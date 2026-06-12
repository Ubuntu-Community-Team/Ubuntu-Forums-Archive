---
title: "synaptics hardware problem during ubuntu installation"
date: 2013-03-11
forum: Hardware
---

### Post by kiritisai on 2013-03-11
I have installed ubuntu 10.04 in my laptop using the windows installer downloaded from the site. But after installation , the screen is functioning a bit differently and its displaying , " unable to query synaptics hardware ". but all my windows drivers are installed properly and I rechecked them once again. After ubuntu 10.04 is opened, im unable to use wired or wireless network connection. Please help me with this.

---

### Post by ibjsb4 on 2013-03-11
Instead of investing time in repair I would suggest you install 12.04.  10.04 reaches end of life next month.

---

### Post by kiritisai on 2013-03-11
But when im trying to use the windows installer for 12.04 , Im getting the following error message 

could not retrieve disk images file
for more info refer.
appdata\local\temp\wubi-12.04-rev272.log 

Does this mean there is some problem with windows??

---

### Post by ibjsb4 on 2013-03-12
I have never used wubi, but I did find this in another thread.

                                                   **[Re: Unable to install ubuntu in windows with wubi]("http://ubuntuforums.org/showthread.php?t=2064219")**
[INDENT]                             > What's happening is:
1. running wubi.exe from a mounted or extracted ISO CD image
2. wubi.exe doesn't detect the ISO and goes to the net to download the image
3. the ISO is old (12.04 instead of 12.04.1) which means that wubi.exe is old and the url's don't exist anymore
4. wubi fails to find the the download.

It's not magic. It's not pretty. It's wubi.

If you do not get any other replies to this thread, you may want to start another thread with wubi in the title.
[/INDENT]

---

