---
title: "After installing Ubuntu XP wont boot: missing ntldr"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by futureal2032 on 2009-08-24
Hi,
I had some prob with dual boot and grub recently..which i have posted elsewhere and i managed to solve the problem.

Now my GRUB loads fine..and my XP was working fine before dual boot..
but now when i select XP from the GRUB list... 
it gives me Missing NTLDR error 

well..thing is NTLDR is there and i know that my XP and everything is fine..

My GRUB conf for XP in menu.lst is showing like this,

title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Can anyone pls help..its a little urgent

---

### Post by stlsaint on 2009-08-24
how do you know that xp is fine if you cant boot into it? ntldr is a system file in xp...have you tried doing a system recovery thru xp cd...boot.ini files may be bad! also if you have the time you can reload xp to mbr than readd grub!

---

### Post by Mark Phelps on 2009-08-25
Looks like you have two hard drives (presence of the map command).  One thing you could try is disconnecting the Ubuntu drive and booting from the XP drive.  Unless you installed GRUB to the MBR of the XP drive, it should boot OK.  That will at least confirm that your XP install still works.

---

### Post by presence1960 on 2009-08-25
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

