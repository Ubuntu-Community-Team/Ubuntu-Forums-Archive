---
title: "Script to report total folder sizes"
date: 2008-11-11
forum: General Help
---

### Post by Ohmu on 2008-11-11
Ever wanted to do: 
[INDENT][FONT="Courier New"]spud@spud-laptop:~$ **dsize**
4G 	 . 
3G 	 Movies
115M 	 .cache 
3M 	 .thumbnails 
1M 	 Code
560K 	 .gnome2 
46K 	 .purple 
[/FONT][/INDENT]

I often need to know which folders are eating up all my HDD space. So I spent the day pestering the lovely people on irc.freenode.net, and ended up with this bash script:

Just save it as [FONT="Courier New"]**dsize**[/FONT], do [FONT="Courier New"]**chmod u+x dsize**[/FONT], and mv it into some folder bash will find ([FONT="Courier New"]**echo $PATH**[/FONT]) 

Well, I'm a noob in linux, I don't know a good place to stick this - please tell me!

If you wana get it recursing (see below), please go ahead!

Enjoy!

Ohmu

```

#!/bin/bash

# DirectorySize : Lists the size of folder and all subfolders, in decreasing order
# Ohmu (sunfish7@gmail.com) 11 Nov 08

# Thankyou to
#    irc.freenode.net#linux
#    irc.freenode.net#awk
#    http://awk.freeshell.org/FormatFileSizes
#
# Example use:
#
# spud@spud-laptop:~$ ./dsize
# 4 G 	 	 . 
# 3 G 	 	 .local 
# 115 M 	 .cache 
# 3 M 	 	 .thumbnails 
# 1 M 	 	 .fr-6Q0eny 
# 560 K 	 .gnome2 
# 46 K 	 	 .purple 
#
# TODO:
#   Make it operate on a param (eg dsize /tmp)
#   Make it recursive.  So that if any folder reports more 
#     than (say) 1Meg, we go into that folder and rinse&repeat
#  eg
# $./dsize -depth 0 (infinite) -granularity 1M
# 4 G             . 
#    3 G 	  .local 
#       2.9G      .local/fish
#       3M        .local/pudding
# etc
# anyone interested? :)  I'm done for now!  RSI'd out!
# Ohmu

# Get the byte usage for each subfolder, including .
#   Need some tricky syntax to get the .MyFolder folders
#   Try 'echo {a,b}c' then 'echo {,.}*'
#   [!.] takes out . and ..
#   We want . so we have to put it in manually
# Sort, largest first
# The awk script replaces eg 4784 with 4K
#

du -s {,.}[!.]* . \
 | sort -rn \
 | awk '
	BEGIN {
		u[0]="K"
		u[1]="M"
		u[2]="G"
	}
	{
		# Get filesize and filename from paramlist
		# cannot use $1 and $2 as filename may contain spaces

		size=$1			# grab the number
		sub(/^[^\t]+\t+/, "")   # Remove it from param list, and following spaces
		name=$0			# what is left is the name

		for (i=3; i>=0; --i) 
		{
			if ( size > 1024 ^i)
			{
				# can sub %d with eg %.2f instead for 2dp precision
				printf "%d%s \t %s \n",  (size / 1024^i), u[i], name
				next
			}
		}
	}' \
 | more
```

---

### Post by jpeddicord on 2008-11-13
Moved to General Help; is a script and not directly a tutorial.

And a tip: the -h parameter to du shows human-readable sizes instead of having to do calculations on the numbers.

---

### Post by Ohmu on 2008-11-13
using -h means it can no longer be sorted by decreasing size (eg 2K 3M 4K).  That's why I posted a workaround.  I'll update the post at the new location.

Thanks.

Ohmu

---

### Post by Ohmu on 2008-12-11
OK after a fiddle, it supports lots of juicy stuff.
I've split the awk script into a separate file, so gedit colors it nicely.
Rename the awk script dsize_awk.  Or, you may want to recombine them (here's why: [http://wooledge.org:8000/BashFAQ/028](http://wooledge.org:8000/BashFAQ/028) Notice my fugly workaround: AWKFILE="/usr/bin/dsize_awk"

Enjoy ... & send me a thanks if it helps you (boost my UF karma :p )

Love n light

Sam

```
#!/bin/bash

# THANKS TO:
#    irc.freenode.net#linux
#    irc.freenode.net#awk
#    http://wooledge.org:8000/BashFAQ/035 for handling commandline args
#    ${DIR%/}/ explained at: http://wooledge.org:8000/BashFAQ/073

AWKFILE="/usr/bin/dsize_awk"
RECURSE="NO"
MINSIZE="512K"
LINES="20"

show_help()
{
	echo 'dsizer - Get Directory Size (Recursable)'
	echo '   Tool for showing sizes of contained directories'
	echo '   Useful for flushing out the garbage when your HDD is hitting 99%'
	echo '   First bash script by spud (yay) sunfish7@gmail.com Dec 08'
	echo ''
	echo 'USAGE: dsizer [OPTION]... [PATH]'
	echo 'OPTIONS:'
	echo '   -h -? --help      for help'
	echo '   -r --recurse      to recurse. Default:'$RECURSE
	echo '   -n --lines    x   to show only x lines (use -0 to show all). Default:'$LINES
	echo '   -m --minsize  4K  only reports dirs > 4K.  Can use 6.7g 800M etc. Default:'$MINSIZE
}


while [[ $1 == -* ]]; do
	case "$1" in
		-h|--help|-\?) show_help; exit 0;;
		-r|--recurse) RECURSE="YES"; shift;;
		-m|--minsize) MINSIZE=$2; shift 2;;
		-n|--lines) LINES=$2; shift 2;;
		-*) echo "invalid option: $1"; show_help; exit 1;;
	esac
done

# if DIR was specified, make sure it finishes with a / (add one if necessary)
DIR=$1
if [[ "$DIR" ]] 
	then DIR=${DIR%/}/
fi

if [[ "$RECURSE" == "YES" ]]
	then DU_PARAMS='-c '$DIR'*/'
	else DU_PARAMS='-s '$DIR'*/ '$DIR'.'
fi

# ensures * reports dir's beginning with .
shopt -s dotglob

echo 'whirr...'
du $DU_PARAMS $DIR \
 | sort -rn \
 | awk -v minsize="$MINSIZE"  -f $AWKFILE \
 | head -n $LINES

exit 0

```

and dsize_awk:

```
#!/usr/bin/awk -f

# - Typical line from du might be
# 	14816	chords/
#
# - The awk script replaces eg 4784 with 4K, and filters
# 	lines where the bytecount < $MINSIZE
#
# - Run this script with '-v minsize="$MINSIZE"' where $MINSIZE=4K, 3.7g, etc
#
# - Script based on:
#	http://awk.freeshell.org/FormatFileSizes

BEGIN {
	u[0]="K"
	u[1]="M"
	u[2]="G"
}
{
	# Get filesize and filename from paramlist
	# cannot use $1 and $2 as filename may contain spaces
	size=$1			# grab the number
	sub(/^[^\t]+\t+/, "")   # Remove it from param list, and following spaces
	dirname=$0		# what is left is the name

	minK = Convert_xK_to_x(minsize)
	if (size < minK)
		exit

	for (i=3; i>=0; --i) 
		if (size > 1024^i)
		{
			# can sub %d with eg %.2f instead for 2dp precision
			printf "%d%s \t %s \n",  (size / 1024^i), u[i], dirname
			next
		}
}

# takes eg 4K or 6.5m and outputs 4, or w/e 6.5Megs is in k
function Convert_xK_to_x(x)
{
	s_in = x

	letter = substr(s_in, length(s_in), 1)

	num = s_in
	sub("K", "", num)

	for (i=0; i<=2; i++) 
		if (toupper(letter)==u[i])
			num*=1024^i

	s_out = num
	return s_out
}
```

---

### Post by qpieus on 2008-12-11
For a different approach, here's a one-liner du command, human readable, with directories sorted by increasing size.```
du -k --max-depth=1 | sort -n | cut -f2 | xargs -d '\n' du -sh
```

I use this in a KDE servicemenu, so I can simply right click on a file in a directory and a terminal will open and list the subdirectories by size. You should be able to easily do the same thing with a nautilus script too.

---

### Post by stickman77 on 2009-03-09
find /path_to_search -maxdepth 2 -mindepth 1 -type d -exec du -sk {} \;

set the max and min depth you want to search... might be useful to someone

---

