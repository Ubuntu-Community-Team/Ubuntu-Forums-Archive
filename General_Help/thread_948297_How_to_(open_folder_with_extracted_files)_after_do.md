---
title: "How to (open folder with extracted files) after download is complete?"
date: 2008-10-15
forum: General Help
---

### Post by ledibri on 2008-10-15
I am using Firefox, and would like to automate download and file usage process as much as possible.

Right now I have only: when I click file link, it is automatically downloaded to "Downloads" folder.

**My wish is to:**
Folder "Downloads" opens after all downloads are finished.
If I was downloading archive file (.zip, .tar.gz), it is automatically extracted and the archive file is deleted.

 Do you know how to do this? That would really make a life easier, since there would be no need to perform the same action with hands.

---

### Post by neilengineer on 2008-10-15
Maybe install FlashGot, a plugin for Firefox.
Then write a shell script to do it.

---

### Post by ledibri on 2008-10-16
> **neilengineer said:**
> 
Then write a shell script to do it.

That's part of problem. I don't know how to write script.

---

### Post by neilengineer on 2008-10-17
Will write you one when free.

---

### Post by neilengineer on 2008-10-17
Should be something like this.
The script assumes that you use "wget" as a download tool and you've already installed flashgot.
Yet, since I don't have internet where I wrote the script, I was unable to test it. Sorry.

How to use it:
Go to flashgot preference, click "add", enter "getit".
Then select the script: getit.sh at the next step.



#!/bin/sh
#Written by Neil Zhao (neilzhao2008@gmail.com) Oct.17,2008

DOWNLOADER_BIN=wget
DOWNLOADER_OPTS=-c
TERMINAL_BIN=/usr/bin/gnome-terminal
DOWNLOAD_DIR=~/Downloads
$TERMINAL_BIN -e "$DOWNLOADER_BIN $DOWNLOADER_OPTS -P $DOWNLOAD_DIR $1"
cd $DOWNLOAD_DIR
for i in `ls $DOWNLOAD_DIR`
do
	if [ `file "$i" |cut -d " " -f 2` = "bzip2" ]
	then
		tar jxvf $i&&rm $i
	elif [ `file "$i" |cut -d " " -f 2` = "gzip" ]
	then
		tar zxvf $i&&rm $i
	elif [ `file "$i" |cut -d " " -f 2` = "Zip" ]
	then
		unzip $i&&rm $i
	fi
done
nautilus $DOWNLOAD_DIR

---

