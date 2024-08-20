```
# 直接对eggnog注释的out.emapper.annotations进行处理
# go-basic.obo下载网址http://purl.obolibrary.org/obo/go/go-basic.obo
sed '/^##/d' out.emapper.annotations | sed 's/#//'  | awk -F'\t' '{print $1"\t"$10}' | awk -F'\t' '{if ($2 != "-") {split($2, go, ","); for (i in go) print $1 "\t" go[i]}}' | tail +2 > self_out.emapper.annotations.GO.txt

sed '/^##/d' out.emapper.annotations | sed 's/#//'  | awk -F'\t' '{print $1"\t"$8}' | tail +2 > self_out.emapper.annotations.description.txt

sed '/^##/d' out.emapper.annotations | sed 's/#//'  | awk -F'\t' '{print $1"\t"$11}' | awk -F'\t' '{if ($2 != "-") {split($2, KEGG_EC, ","); for (i in KEGG_EC) print $1 "\t" KEGG_EC[i]}}' | tail +2 > self_out.emapper.annotations.KEGG_EC.txt

sed '/^##/d' out.emapper.annotations | sed 's/#//'  | awk -F'\t' '{print $1"\t"$12}' | awk -F'\t' '{if ($2 != "-") {split($2, ko, ","); for (i in ko) print $1 "\t" ko[i]}}' | tail +2 | sed 's/ko://g' > self_out.emapper.annotations.KEGG_Knum.txt

sed '/^##/d' out.emapper.annotations | sed 's/#//'  | awk -F'\t' '{print $1"\t"$13}' | awk -F'\t' '{if ($2 != "-") {split($2, KEGG_Pathway, ","); for (i in KEGG_Pathway) print $1 "\t" KEGG_Pathway[i]}}' | tail +2 > self_out.emapper.annotations.KEGG_Pathway.txt

sed '/^##/d' out.emapper.annotations | sed 's/#//'  | awk -F'\t' '{print $1"\t"$21}' | awk -F'\t' '{if ($2 != "-") {split($2, PFAMs, ","); for (i in PFAMs) print $1 "\t" PFAMs[i]}}' | tail +2 > self_out.emapper.annotations.pfam.domain.txt

```

