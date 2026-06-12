---
title: "[SOLVED] Data Recovery for Ubuntu (Ext2/3)"
date: 2008-10-10
forum: General Help
---

### Post by TheSwede86 on 2008-10-10
Hi!

I am really nearing my 19th nervous breakdown.

The situation is as following:

I reinstalled Ubuntu, carefully placing my files into a USB drive and my /home folder (the exact path was something like /home/ubuntu)

I reinstall ubuntu and carefully chose not to touch anything but the "/" partition leaving the home partition that is on a separate parition untouched.

I enter the fresh Ubuntu with a chilling realisation that ALL MY DOCUMENTS AND EMAILS ARE GONE!

The USB memory didnt mount as normal so I added a line in a file (dont remember its name) and wrote something like "mount /dev/dbs1 mnt/usb1"
and then the USB "magically" appeared.

After that I added all my files, took the USB memory out, checked it that it contained the files and then checked via gparted that it was ca. 150mb full (that was the total amount of files).

I am now running a basic recoveryprogram for EXT2/EXT3 with the help of WINE but the results I get are mostly that it don't seem to find any files at all and therefore I suspect that WINE is not the solution.

I need a SIMPLE GUI based recovery program that will recover files and pref. folders from a deleted and formated partition (in the worst case).

I have tried a little of Autopsy (The Sleuth Kit or something like that), and some other recoveryprograms for Ubuntu/Linux but all seem to be textbased and quite complex.

Do I have to go this way if I am going to have a chance to recover the files or can you recommend a good gui based program? The documents are textdocuments made in gedit (dont know extension), open office documents, pdf docs, email files from thunderbird and 2 videos in MPEG or AVI.

PLEASE help!

Thanks in advance & Best Regards - TheSwede86

Sorry for any bad english and/or wierd statements, I am really desperate and its around 4 a'clock at night here.

---

### Post by Sam on 2008-10-10
The whole partition has gone ? [Try this](http://ubuntuforums.org/showpost.php?p=4160085&postcount=3).

---

### Post by iaculallad on 2008-10-10
Try [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), not a GUI-based app but a good terminal Data Recovery utility.

---

### Post by sokopok on 2008-10-10
If you didn't touch the partition that contains your /home it should still be there. Can you still mount it and check if it's intact.
eg:

mkdir oldhome
sudo mount /dev/sdaX oldhome

then check if your files are still there (make sure to "show hidden files")

---

### Post by TheSwede86 on 2008-10-10
Thank you guys for your fast reply I REALLY appreciate it.

This is the thing, my old Home appeared as it used to (reinstalled Ubuntu a few times) but not with my latest files but with my previous home folder.

So I had 3 partitions, One "/", one "/Home" and one "Swap" but the files in "/Home" was not my current (last) Home but the one before that.

Really wierd.

Anyways running Photorec now with a full recovery of my entire harddrive to an external USB one but do you guys know if it will recover:

[I]PDF
Open Office
Exported mail in Thunderbird (it was one file for "Inbox", one for "Sent" etc. don't sure about the file extension)
MOV/MPEG[/I]

EDIT: Seems to find all but my email files according to the site, they might be in .mbox or might be in .eml

With that said (that I have 3 partitions) is any option viable except the one trying to restore it with data recovery programs?

And if Photorecovery doesn't work is it any idea to send it to a computer store that uses IBAS? Don't know if you guys know about it (or maybe its really wellknown) but it seems to be the mother of all data recovery software.

EDIT:

Sorry need to point a few things, I seem to mix past tense with present:

I have currently now 3 partitions, they are named the following in gparted:
dev/hda5 - "linux-swap"
dev/hda6 - (blank no text)
dev/hda7 - "./"

Shouldn't the middle one be named like "/home" or something like that?

Edit:

Got the files recovered with Photorec and using a USB-stick that I had saved the files to.

---

