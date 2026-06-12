---
title: "Extra Hard Drive &amp; Mouse Problems"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by bikerdude on 2005-09-03
Ok just a fare warning I am very new to Linux so bare with me..
Right now my computer has 3 Hard Drives in it 6gig(Swap Bay), 120gig, 120gig all Western Digitals. When I am using WinXP via Swap Bay I had to install a Dinamic Drive Overlay for Windows to be able to see the 2nds 120gig at it's full capacity.

Now when I am on Ubuntu I can see the first 120gig but not the 2nd..
They're all formated on FAT32 full capacities with no partitions..

So what can I do to make this 2nd 120gig mount properly?

I used the code in the Ubuntu Guide. Here is what I am putting in the Terminal window and the error I get

"How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write?"
******@ubuntu:~$ sudo mount /dev/hdd1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Now regarding my mouse it's a Logitech MX510 and for some odd reason the 2 buttons on the side dont' work on Ubuntu but in WinXP they work like going forward or backwards in Webpages or Explorer.

So if anyone can offer some advice on these 2 issue it would be great

---

### Post by dbrine on 2005-09-04
try using this guide. I am really new, for the most part, too. But this worked great for me.


[http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/)

---

### Post by bikerdude on 2005-09-04
Thanks **dbrine** but it's not the mounting part that I can't figureout. It's the part where I can't see the stuff on my Hard Drive for some odd reason and thats it's formated in Fat32 just like the other one..

But thanks again for this link to another guide that I will deffenitely look at.

So if anyone here still has any sugestions to my problem pls let me know. Thanks in advance.. I think I will look at loading Grub via a Diskette.. I heard someone mentioning this some where so this way I can possibly load the Western Digital DDO loader for it to see the HD at it's full capacity.

---

### Post by dbrine on 2005-09-04
When I was having a million problems formating, partitioning and mouinting my hdd's I got the same errors. I had to repartion, format, etc. However I copied all the data, 100gb, to another pc prior to installation in linux environment. One think i didn't know about fat32. Is it is can only be partitioned and formatted to 32gb. I know with sound wierd but supposely this is true. I did a search on google for fat32 formatting and cae across it. I ended up formatting my new hdd with linux (83).

---

