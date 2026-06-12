---
title: "Ubuntu Error 18 | Help"
date: 2009-12-09
forum: Hardware
---

### Post by SametAras on 2009-12-09
[FONT=Courier New]Hello,

I'am old computer installed in Ubuntu. And in hdd very important datas available. When I turn on the my computer gives the following error:

[/FONT]```
GRUP Loading stage1.5.

GRUP Loading, please wait...

(waiting 1 minute) and;

Error 18
```[FONT=Courier New]

Please, how to my hdd on error fix ?


Sincerely;
Aras, Samet.
[/FONT]

---

### Post by Fafler on 2009-12-09
[http://http://wiki.linuxquestions.org/wiki/GRUB#Error_18]("http://http//wiki.linuxquestions.org/wiki/GRUB#Error_18")

The easiest thing, if you only need need the data, is to download a Live CD like Knoppix, boot it and move the data to another location.

If you want to use the machine with Ubuntu, you need to reinstall (BACKUP DATA FIRST!) and make a small (100 mb) partition as the first partition on the disk and use it as /boot

---

### Post by SametAras on 2009-12-09
[FONT=Courier New]Hello,

Thank you for your interest. I'am dowloading "**KNOPPIX-ADRIANE_V6.2CD-2009-11-18-EN.iso**" to "**ftp.linux.org.tr**".

I have new harddisk. Ubuntu will install it. But I need to recover my old data from disc. Knoppix will install the old harddisk. Can I transfer datas from here?


[/FONT] [FONT=Courier New]Sincerely;
Aras, Samet.
[/FONT]

---

### Post by Fafler on 2009-12-09
You don't need to install Knoppix. It boot and runs entirely from the CD.

So you have two harddrives? One with a Ubuntu installation that wont boot and a new empty one?

The easiest thing would actually be to put the new drive in the PC and install Ubuntu on it. After you have a working Ubuntu installation on the new drive, turn of the PC, connect the old drive to a second SATA/IDE/etc. channel and boot with both drives connected. Now the old drive should show up on your desktop and you can copy the files you need to the new drive.

---

### Post by SametAras on 2009-12-09
[FONT=Courier New]Hello,

I can't connect to the computer two harddisk. Actually harddisk opened. But GRUP not loading. Now gives the following error:
```

GRUP Loading stage1.5.



GRUP loading, please wait...
Error 16


```

Onetime gives the error 18.

[/FONT][FONT=Courier New]Sincerely;
Aras, Samet.
[/FONT]

---

