---
title: "Problem with setting frequency on monitor"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by Jonnik on 2005-03-31
Hi. I started my first linux system, Ubuntu and I have little problem. I set frequency that sytem don´t respect. So I only saw the first login for one second not more and then the black screen appears and monitor says over-frequency. 140kHz. It seems to me much. I don´t know any monitor that can use tha psycho frequency. But the interval by using "sudo dkpg-reconfigure xserver-xorg" or "sudoedit etc/X11/xorg.conf" is sets on value 30-71kHz. I don´t know what now with this I can do. Is there any other utility or scripting to eliminate this problem? I have monitor LG Flatron ez T710BH, PC: AMD Sempron2500+@(3100+), 2x256MB dual DDR 400 PQI I think, HDD 80GB-Seagate ATA100 7200rpms, 2MB cache (4 partitions: 1. WinXP(10GB-NTFS),2.Ubuntu(5GB-I can´t remember, it´s that 3th system for linux),3.Win98(2GB-not yet installed-FAT32),4.Data(63GB-FAT32)), ATI Radeon Saphire 9600 128MB, MB ASUSS A7V880, LG CD-RW mechanic 52x32x52x. So I beliave that anybody can helps. I will be glad. I have to do project to school in Linux for sorting some data in .xls file. First I must have workly Linux. I saw Ubuntu for a second, but it seems very good. I am beginner but scripting in shell is realy quick. So only the grafic environment is missing for me this time. Please help. Thanks. LW: You can send me on my e-mail.

---

### Post by Whiffle on 2005-03-31
Hit ctrl + alt +f2 , which will take you to a text login screen.  

login,

run " sudo nano -w /etc/X11/xorg.conf "

Cursor down the page to where it says 
"Section "Monitor"
    Identifier   "blah"
    HorizSync  "blah"
    VertRefresh "blah"
EndSection

Find our the Horizontal and vertical sync info for your monitor and fill it in there.  

Hit f3 to save, ctrl+X to exit. 

Then ctl+alt+f7 to get back to the black screen or wherever, and ctrl+alt+backspace to restart the X server, and it *should* be fixed.

---

### Post by alastair on 2005-03-31
Post the file :

/etc/X11/xorg.conf

A quick google for your monitor shows (possibly) :

Vertical Frequency is 50 to 160Hz
Horizontal Frequency is 30 to 98kHz

From : [http://www.systemsassurance.co.uk/default.asp?shopID=systemsRelated.asp&pn=T710BH](http://www.systemsassurance.co.uk/default.asp?shopID=systemsRelated.asp&pn=T710BH)

(I would normally find the manufacturer spec. - you might want to do this to check!)

---

