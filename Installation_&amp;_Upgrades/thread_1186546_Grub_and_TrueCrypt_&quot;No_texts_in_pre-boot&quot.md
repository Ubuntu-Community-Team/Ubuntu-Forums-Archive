---
title: "Grub and TrueCrypt &quot;No texts in pre-boot&quot; option"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Piotrex on 2009-06-13
Hello,
I have a problem with dual booting Ubuntu and Windows XP encrypted with TrueCrypt and residing on the same hdd when TrueCrypt's "Do not show any texts in the pre-boot authentication screen" option is active.
Theoretically this should effectively hide truecrypt's boot menu showing only user defined text in the screen without any key echo. Very welcome function as it allows me to make my winxp installation invisible at first glance.

I'm following standard procedure:
1. WinXP installation
2. Ubuntu with Grub installation.
3. WinXP truecrypt encryption.
4. Copying truecrypts mbr under ubutu live cd enviroment to file
6. Reinstalling Grub to mbr and redefining menu.lst with appropriate chainload

And it works! Works without a problem and allows me to boot Ubuntu or encrypted windows.

The strange thing comes when I want to enable aformentioned truecrypt's "Do not show any texts in the pre-boot authentication screen" option. 

After doing this and once again:
1. Copying mbr changed by truecrypt to file
2. Reinstalling Grub to mbr and redefining menu.lst
nothing changes! 

I mean truecrypt menu appearing as always. No hiding!
And yes, this option works as it should if... if not called with Grub. If truecrypt's bootloader resides in mbr I get blankscreen (or my text as I should) but if exactly the same mbr is placed in a file and loaded with Grub I get the standard truecrypt menu!!!
Honestly this behaviour leaves me thinking that I'm NOT understanding the whole boot-thing AT ALL. 
How is it even possible? If I compare two mbrs dumped to files, one without "Do not show any texts..." and one with "Do not show any texts..." enabled the changes are clearly visible and in the second case you can see where the user defined text is placed within mbr. But when I load these two files with grub's chainload mechanism both acting the same!!
Why??

Any help will be appreciated.

---

### Post by blubbmade on 2012-11-18
Hey, already found an answer?
same problem...

---

### Post by Old_Grey_Wolf on 2012-11-18
Old thread. Closed.

---

