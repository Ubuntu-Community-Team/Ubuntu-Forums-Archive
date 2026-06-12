---
title: "Resetting command-line parameter after shift command"
date: 2008-07-25
forum: General Help
---

### Post by kaibob on 2008-07-25
Post deleted by Kaibob. See the following post.

---

### Post by kaibob on 2008-07-25
I haven't received any responses to this thread, and I've progressed a bit, so I thought I would delete my original posting and try again.

I often have need to add one or more PDF files to a master PDF document. I wrote the shell script quoted below for this purpose, and it works well with one exception. When the name of the added PDF file contain spaces, the script does not work. I experimented with the quoting of variables in the script but couldn't get it to work.

I suspect the problem is that the $filelist variable does not individually quote the file names it contains. Is there some way to do this?

I also tried using $@ in the pdftk command line instead of the $filelist variable, but the previous until/shift loop had emptied $@. Is there some way to reset $@?

As an aside, this script is used with the Nautilus Actions extension which passes the added files to the script as command line arguments. And, the purpose of the until loop (which is not all that necessary) is to prevent me from adding a PDF file to itself. 

I appreciate any help. 

> #!/bin/bash

# Change to working directory.
workdir=$(dirname "$1")
cd "$workdir"

# Get PDF name.
pdfname=$(zenity --file-selection)
if [ -z "$pdfname" ] ; then exit ; fi

# Check input PDF not in target PDF
until [ $# -eq 0 ] ; do 
filelist="$filelist $1"
if [ "$1" = "$pdfname" ] ; then
zenity --error --text "Input PDF same as target PDF! "
fi
shift
done

# Create PDF
pdftk "$pdfname" $filelist cat output .xxx.pdf
mv .xxx.pdf "$pdfname"

---

### Post by geirha on 2008-07-25
You can do something like this, without using shift at all
[php]
for file in "$@"; do
    if [ "$file" == "$pdfname" ]; then
        zenity --error --text "Input PDF same as target PDF!"
        exit 1
    fi
done

pdftk "$pdfname" "$@" cat output .xxx.pdf
[/php]

The $@ is a bit special. Putting the quotes around "$@" makes it handle spaces in filenames. Read about it in the bash manual.

---

### Post by kaibob on 2008-07-25
geirha,

Thanks for the help. I changed my script as you suggested, and it now works fine with files that contain spaces in their names. I'm new to shell scripting and will read about $@ as you suggest.

Thanks again.

kaibob

---

### Post by DGortze380 on 2008-07-25
> **kaibob said:**
> geirha,

Thanks for the help. I changed my script as you suggested, and it now works fine with files that contain spaces in their names. I'm new to shell scripting and will read about $@ as you suggest.

Thanks again.

kaibob

another way to do this would be with awk. use a designated delimiter at the end of each file name and set awk to break at that delimiter.

---

