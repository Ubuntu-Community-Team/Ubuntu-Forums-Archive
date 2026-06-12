---
title: "pdftk usage question"
date: 2008-09-23
forum: General Help
---

### Post by reader4 on 2008-09-23
Sometimes when the librarians scan papers/books to send me, they get the orientation wrong and all of the even pages need to be rotated 180 degrees.  I can rotate all of those pages using pdftk

```
pdftk in.pdf cat 1-endevenS output out.pdf
```

But how to 'cat' the odd pages back in, properly interleaved? 

Using this just gives me the all the rotated even pages first, then the odd pages:

```
pdftk in.pdf cat 2-endevenS 1-endodd output out.pdf
```

---

### Post by Tillmo on 2009-05-02
Use the following shell script. Save it as pdf-rotate-even and make it executable.

```

#/bin/bash
# script for rotating all even pages of a document

# enough arguments?
if [ $# -ne 2 ]; then
         echo 1>&2 Usage: pdf-rotate-even input.pdf output.pdf
         exit 127
    fi

# generate a temporary directory
TEMPDIR=/tmp/pdf`date +%N`
mkdir $TEMPDIR

# rotate all even pages, keep the odd ones
pdftk $1 cat 1-endodd output $TEMPDIR/odd.pdf
pdftk $1 cat 1-endevenS output $TEMPDIR/even.pdf

# split the files...
pdftk $TEMPDIR/odd.pdf burst output $TEMPDIR/pg%04d_A.pdf
pdftk $TEMPDIR/even.pdf burst output $TEMPDIR/pg%04d_B.pdf

# ... and recombine them, "_A" and "_B" suffixes leading to the correct order
pdftk $TEMPDIR/pg*.pdf cat output $2

# cleanup
rm -r $TEMPDIR

```

---

### Post by fungs on 2009-10-06
Thanks for the script, I had the same problem.

I suggest du use evenD instead of evenS since it will rotate relatively by 180 degrees.

---

### Post by tareko on 2010-09-26
Thank you, the script is very helpful. Here is one small modification that allows you to decide which direction the rotation is:

```

#/bin/bash
# script for rotating all even pages of a document

# enough arguments?
if [ $# -ne 3 ]; then
         echo 1>&2 Usage: pdf-rotate-even <direction> input.pdf output.pdf
         exit 127
    fi

# generate a temporary directory
TEMPDIR=/tmp/pdf`date +%N`
mkdir $TEMPDIR

# rotate all even pages, keep the odd ones
pdftk $2 cat 1-endodd output $TEMPDIR/odd.pdf
pdftk $2 cat 1-endeven$1 output $TEMPDIR/even.pdf

# split the files...
pdftk $TEMPDIR/odd.pdf burst output $TEMPDIR/pg%04d_A.pdf
pdftk $TEMPDIR/even.pdf burst output $TEMPDIR/pg%04d_B.pdf

# ... and recombine them, "_A" and "_B" suffixes leading to the correct order
pdftk $TEMPDIR/pg*.pdf cat output $3

# cleanup
rm -r $TEMPDIR

```

---

### Post by Xime on 2012-01-06
Thanks a lot guys. I had the same kind of problem and it worked like a charm. This is exactly the reason why FOSS rules.

I tweaked the script a little bit further to allow to specify particular rotation angles for odd *and* even pages. In case it might spare a few minutes to people in the same situation as I was, I share it here :

```
#/bin/bash
# script for rotating all even pages of a document

# enough arguments?
if [ $# -ne 4 ]; then
         echo
         echo 1>&2 Usage: bash pdf-rotate-odd-even.sh input.pdf direction_odd direction_even output.pdf
         echo
         exit 127
    fi

# generate a temporary directory
TEMPDIR=/tmp/pdf`date +%N`
mkdir $TEMPDIR

# rotate all even pages, keep the odd ones
pdftk $1 cat 1-endodd$2 output $TEMPDIR/odd.pdf
pdftk $1 cat 1-endeven$3 output $TEMPDIR/even.pdf

# split the files...
pdftk $TEMPDIR/odd.pdf burst output $TEMPDIR/pg%04d_A.pdf
pdftk $TEMPDIR/even.pdf burst output $TEMPDIR/pg%04d_B.pdf

# ... and recombine them, "_A" and "_B" suffixes leading to the correct order
pdftk $TEMPDIR/pg*.pdf cat output $4

# cleanup
rm -r $TEMPDIR
```

---

### Post by mathieud on 2013-05-05
Dear all,

I have successfully used your script and wanted to thank you.

Maybe using the mktemp -d command to create the temporary directory would be better.

---

### Post by oldos2er on 2013-05-05
Old thread closed.

---

