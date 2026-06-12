---
title: "reduce PDF file resolution"
date: 2008-09-08
forum: General Help
---

### Post by bayonetblaha on 2008-09-08
I'm trying to upload some scanned documents in PDF format to google docs, but google docs requires <10MB file size.  How can I reduce the image resolution in these PDF files to lower the size of my files?

---

### Post by annatar on 2008-09-08
'Reprint' the file as a PDF (a built-in function of ubuntu), and find the appropriate options in the print dialog for reducing image resolution 

Also see this thread : [http://ubuntuforums.org/showthread.php?t=681859](http://ubuntuforums.org/showthread.php?t=681859)

---

### Post by mxsteini on 2012-03-16
use ghostscript:
gs -dNOPAUSE -sDEVICE=pdfwrite -r100x100 -q -sOutputFile=reduced.pdf  inputfile.pdf

---

### Post by wombalton on 2012-07-06
add a -c quit to your ghostscript line. this will automaticly close the ghostscript environment. Very useful in shellscripts!

```

gs -dNOPAUSE -sDEVICE=pdfwrite -r100x100 -q -sOutputFile=output.pdf input.pdf -c quit

```

I wrote a little script to make my life easier:
```

#!/bin/bash

#
# pdfimgresreduce
#

if [[ "$1" == "" ]]
then 	echo "usage: pdfimgresreduce input.pdf [output.pdf]"; exit 0
fi
if [[ "$2" == "" ]]
then 	out=$1.red.pdf; echo "outputfile: "$out
else	out=$2
fi

if [[ -f $1 ]]
then	gs -dNOPAUSE -sDEVICE=pdfwrite -r100x100 -q -sOutputFile=$out $1 -c quit
else 	echo $1" not found"; exit 1
fi

```

---

