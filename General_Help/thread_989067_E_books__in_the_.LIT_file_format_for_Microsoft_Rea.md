---
title: "E books  in the .LIT file format for Microsoft Reader"
date: 2008-11-21
forum: General Help
---

### Post by jon555 on 2008-11-21
How do you read .lit books in ubuntu?

---

### Post by everthonvaladao on 2009-02-10
The .lit files are Microsoft Reader proprietary ebook files, but you can convert them to HTML with clit ([_ConvertLit_]("http://www.convertlit.com/download.php")). 

To install clit from source, follow [_this tutorial_]("http://ubuntuliving.blogspot.com/2007/02/converting-lit-files-in-ubuntu.html") (or just download [_this_]("http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb") and [_this_]("http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/clit_1.8-1_i386.deb") .deb compiled versions and double-click them to install).

After installing it, you can use [_this script_]("http://ubuntuforums.org/attachment.php?attachmentid=30912&d=1177590357") that convert the .lit to .html and open it with firefox browser. At the browser, you can "print" them as PDF or just save the HTML, if you want.

I've made this script to install everything and also create an lit2pdf script to make things easier:

> 
    #install clit
    cd /tmp
    wget -c [http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb](http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb)
    wget -c [http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/clit_1.8-1_i386.deb](http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/clit_1.8-1_i386.deb)
    sudo dpkg -i libtommath_0.37-1_i386.deb clit_1.8-1_i386.deb
    wget -O cleanlit.sh -c [http://ubuntuforums.org/attachment.php?attachmentid=30912&d=1177590357](http://ubuntuforums.org/attachment.php?attachmentid=30912&d=1177590357)
    #install litreader script
    chmod +x /tmp/cleanlit.sh
    sudo mv /tmp/cleanlit.sh /usr/local/bin/litreader
    #install lit2pdf script
    sudo apt-get install htmldoc
    echo '
    echo "[Stage 1] converting $1 to HTML..."
    HTML_DIR=`litreader "$1" | grep Exploded | sed -e "s/Exploded .* into //g" -e "s/\.$//g" -e "s/\"//g"`
    echo "HTMLs saved to $HTML_DIR"
    BOOK_TITLE=`basename "$1" .lit`
    sed -i -e "s/<title>New Page 1<\/title>/<title>$BOOK_TITLE<\/title>/g" ${HTML_DIR}*.htm
    echo "[Stage 2] converting the HTML to PDF..."
    #htmldoc -t html -f "$1.html" --book --no-toc --no-title ${HTML_DIR}*.htm
    htmldoc -t pdf13 -f "$1.pdf" --webpage --no-toc --no-title ${HTML_DIR}*.htm
    echo "PDF saved to $1.pdf"
    evince "$1.pdf"
    '> /usr/bin/local/lit2pdf
    chmod +x /usr/local/bin/lit2pdf


Then you can associate your .lit files with litreader and create an nautilus-actions entry to convert an .lit file to .pdf.

source: [_http://mobilevs.blogspot.com_]("http://mobilevs.blogspot.com/2009/02/lit2pdf-convert-microsoft-reader-lit.html")

[]'s

---

### Post by mb_webguy on 2009-02-10
Microsoft Reader also apparently works well under Wine...

---

