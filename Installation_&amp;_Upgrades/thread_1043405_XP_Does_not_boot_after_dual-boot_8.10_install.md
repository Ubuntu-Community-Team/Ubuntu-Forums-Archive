---
title: "XP Does not boot after dual-boot 8.10 install"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by futureal2032 on 2009-01-18
hi,
i installed Ubuntu 8.10 from a USB drive

well i booted as a Live Ubuntu from my USB drive and then Installed it on my hard disk.

after that ..i can boot into Ubuntu and do everything without any hassles..i can't boot into XP.

i checked and my XP installation is in /dev/sdb1 partition

my grub lists this

[COLOR="Blue"]# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/COLOR]

[B]but i am not able to boot in XP
it gives me "Missing NTLDR" error[/B]

I need to solve this urgently ..as my mom has to use XP for her work

help appreciated.

---

### Post by sovietdoughnut on 2009-01-18
do you have an xp disk you could boot from? if so, boot into and select repair an installation. whatever the problem is, the repair option  should fix it. upon reboot you'll find that your computer  boots right into windows but now you can't access linux. you'll need to boot from an ubuntu disk and reinstall grub and hope that it autoconfigures correctly this time. 

i'm sure the gurus on here could help you edit your menu.lst file to get it to load xp, but i've never had much luck messing around with that myself.

---

### Post by logos34 on 2009-01-18
follow this:

[http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)

afterward, restore grub from ubuntu live cd (see link in my signature)

---

### Post by breakerr on 2009-01-18
Just my two cents in here:

All I can say is that your Windows Xp is there....dont get desperate and fustrated by formatting/deleting your Windows OS. Maybe by doing what I just did to fix my boot priority you can solve something: [http://ubuntuforums.org/showthread.php?t=1043031](http://ubuntuforums.org/showthread.php?t=1043031) make the right question in google and it might help you too. Best of luck.

---

### Post by caljohnsmith on 2009-01-18
So is Ubuntu on the sda drive and Windows on your sdb drive? In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by futureal2032 on 2009-01-19
> **caljohnsmith said:**
> So is Ubuntu on the sda drive and Windows on your sdb drive? In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.


Thank you for ur suggestion. I downloaded the script and created the "Results.txt" too..but..

well but meanwhile i had created supergrub and fixntldr disks..
so i thought beofore posting the contents of the file ..i should try those disks..
so i did following..
1. I booted the pc with "fixntldr" boot cd..
and my win dows booted fine.
2. Then i restarted windows and booted using the "Supergrub" boot disk.. and again it boots my windows fine..
so i was happy..since its not the first time i have installed ubuntu and toyed with Grub... i decided i will check the "SuperGrub" entry for "Windows" and copy it to my grub menu.lst.
3. i checked and the Supergrub entry is
[COLOR="RoyalBlue"]rootnovery (hd0,0)
chainloader+1 
boot[/COLOR]
4. so i decided i would now copy this above entry to my existing grub.. so i restarted the pc...
**and now it directly boots in WIndows XP. My "Grub" has disappeared.**
since this was the first time i hav used "FIxntldr" or "SuperGrub"

**now i have my windows back..but don't know how to get grub back.**

[B]So I want to know.. i know i can install Grub from Live CD or Live Session from USB...but if i do that will i face the same problem of booting windows again?

or can i install Grub again using the "SuperGrub" cd?

[/B]

---

### Post by futureal2032 on 2009-01-19
Hi thanks everyone,
i have solved the problem..

i just booted from my Live USB
did the following steps..

grub> find /grub/stage1

# It showed me (hd1,9)

grub> root (hd1,9)

grub> setup (hd1)

grub> quit

then i edited the menu.lst..and replaced the default entries for windows (generated automatically by Ubuntu) with the following

rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1


Bingo!... it worked...
i guess the 0riginal problem was occuring due to grub getting installed at hd0 instead of hd1... and the default entries that ubuntu created.. i guess those default entries were what is called "live swap" entries.

anyways..all's well that ends well. Thank You.

---

