---
title: "List Folder and File names in separate index file"
date: 2008-07-20
forum: General Help
---

### Post by letmein on 2008-07-20
Hi,
I am looking for a program/script that i can use to list all the folders and file names and ideally their attributes or not (type, size, last modified) into a spreadsheet or other type of file, and have hyperlinks to the source files.

Im basically looking to export all my folder and file names into one index file, that can be used to access files directly instead of searching, any thing available?

---

### Post by lswb on 2008-07-20
Something like this?

```


#!/bin/bash

ShowTitle()
{

STEXT=$( grep -h -i -B4 "</title>" "${1}" )

unset INTITLE
HOLDIFS=$IFS
IFS="$IFS<>"
shopt -s nocasematch
for word in $STEXT ; do

	if [[ "${word}" == "/title" ]] ; then break; fi

	if ! [ $INTITLE ] ; then
		if [[ "${word}" == "title" ]] ; then 
			INTITLE=1
			continue
		fi
	else echo -n "$word "
	fi
	
done
shopt -u nocasematch

# If no title was found:
if ! [ $INTITLE ] ; then echo " (Untitled HTML)" ; fi

IFS=$HOLDIFS
}

INDEX="index.html.building"
DOCDIR=""
SUBTITLE=""
EXT=""
NUMFILES=0

# Begin:

[ $# -gt 0 ] && [ -d $1 ] && cd $1

DOCDIR=`pwd`

echo "Creating $DOCDIR/index.html"

[ -e index.html ] && mv index.html index.html.old

exec 6>&1
exec>"$INDEX"


echo "<html>" 
echo "<head><title>Local Documentation: $DOCDIR</title></head>"
echo "<h1>$DOCDIR</h1>"
echo "<h2>Listing produced `date +\"%B %d %Y\"`</h2>"


#Not handling upper case filename.EXT yet.

for filename in *.htm *.html *.pdf *.txt ; do
	if [ -f "${filename}" ] ; then
	echo ${filename} >&6
	(( NUMFILES++ ))

	case ${filename} in

		*.htm)
		EXT=".htm"
		SUBTITLE="  $( ShowTitle "${filename}" )"
		;;
		
		*.html)
		EXT=".html"
		SUBTITLE="  $( ShowTitle "${filename}" )"
		;;

		*.pdf)
		EXT=".pdf"
		SUBTITLE="  (PDF)"
		;;

		*.txt)
		EXT=".txt"
		SUBTITLE="  (Text)"
		;;

	esac	

	echo -n "<a href=\"file://${DOCDIR}/${filename}\">$( basename "${filename}" "${EXT}" )</a> ${SUBTITLE}"
	echo "<br><br>"

	fi
done

echo "</html>"

exec 1>&6 6>&-
mv "${INDEX}" "index.html"

echo "
$NUMFILES links listed in index.html
"


```

---

### Post by letmein on 2008-07-20
Well, im not a programmer but I want to test this out...where do i specify the directories/files i would like to reference, and how do i run this script?

---

### Post by lswb on 2008-07-20
Copy the text to a file and give it a name, lets say you call it hindex.

Then 

chmod +x hindex

to make it executable

type 

./hindex 
or
./hindex directoryname

It will scan the current directory (or directoryname if specified) for any html, pdf, or text files (based on file extension) and create a very basic list in a file named "index.html" in the same directory which you can then open with a web browser. If there is already a file named index.html in that directory it will save it first with the name "index.html.old"

If you move hindex to a directory in your path you will be able to run it without 
the ./ (or the complete path) preceding the command.

This script does not do exactly what you asked for but may give you some ideas for writing one that does just what you want.

---

### Post by letmein on 2008-07-20
It did do just that, idea wise that is, many thanks!

I also found a program (windows based) that accomplishes the above with countless other settings eg. attributes, size, date created etc...

[http://www.karenware.com/newsletters/2000/2000-06-12.asp](http://www.karenware.com/newsletters/2000/2000-06-12.asp)

---

