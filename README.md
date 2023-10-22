repro:

```
./autogen.sh
make -j5

sudo apt update
sudo apt install ghostscript

curl -OL https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf
gs -q -dQUIET -dSAFER -dBATCH -dNOPAUSE -dNOPROMPT -dPDFSTOPONERROR -sDEVICE=pdfwrite -sOwnerPassword=secret -sUserPassword=secret -sOutputFile=encrypted.pdf dummy.pdf


./bin/gs -q -dQUIET -dSAFER -dBATCH -dNOPAUSE -dNOPROMPT -sstdout=%stderr -sDEVICE=pdfwrite -SPDFPassword=secret -dPDFSTOPONERROR  -sOutputFile=out.pdf encrypted.pdf
```

bisect: 205d4f51cba82bc7cfa6a64b3d82b77baebf91b4

