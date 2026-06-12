---
title: "Ubuntu live cd on Mac - copy file to PC - error"
date: 2008-07-24
forum: General Help
---

### Post by srt7300 on 2008-07-24
I cannot copy files from a Mac to a PC using a live Ubuntu disk on the Mac.

I booted a live Ubuntu 8.04 disk on a Mac powerbook (I do have the Ubuntu version for the powerbook). 
I can see all the files in the Mac User directory by doing a "sudo nautilus" command. They were restricted in a regular browser window before that.

In the sudo nautilus window, if I go to a file on the Mac in the User directory, I can open and read that file (in this case, a pdf file).

I am networked to a WindowsXP computer, that has a shared Fat32 partition (no spaces in the partition name or folder names).
From the Ubuntu booted Mac, I can read files and create folders in the shared XP partition.

If I try to click and drag the previously mentioned pdf file from the Mac (nautilus opened window with read ability) to a folder on the XP partition I get a this error:
Error while copying. The file "this.pdf" cannot be handled because you do not have permission to read it.

But I do have permission to read it. I just read it. 

So now I try to copy using the cp command.

sudo cp -r "/media/Macintosh HD/Users/dave/desktop/testfolder" "smb://d3/data2b/dave"
I get the following error:
cp: cannot create directory 'smb://d3/data2b/dave' : no such file or directory

I put quotes around the names because of the space in the Mac name (space put there by Ubuntu, not me).
I want to copy all files and folder under the testfolder, which is where the pdf file is.
The destination folder Dave already exists. I already did some tests to make sure I can read and write to that folder.
I opened the directory in a window and used the Go-Location command and copied the path names to make sure I did not typo anything for both directories.

So even though Ubuntu has confirmed that I have read permission and that the destination directory exists, Ubuntu claims both of these are false.

Any suggestions?

The above attempts are just to see if I can get this process to work. If I can, I will be copying the entire Mac User directory to the Fat32 partition on the PC. This Mac cannot boot by itself. I am trying to rescue the user files off of it.

---

### Post by xxcheesexpuffxx on 2008-08-08
I'm having the exact same issues just with pictures, trying to copy from mac to basically anywhere. Did you have any luck?

---

### Post by ghaiteiro on 2008-09-21
Same issue here. Any luck anybody?

---

### Post by elyjet on 2008-12-12
please, someone?

---

