---
title: "WUBI Install Cant Boot into Ubuntu after install....."
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by eluman75 on 2009-03-25
I have for about a week now been trying to get UBUNTU working on my Vista 64 bit machine after a WUBI install. I have uninstalled and reinstalled it about 20 different times. Each time it is the same result. When i reboot...it isnt there as a choice in the windows boot manager. So i did research on forums and got EASYBcd. Added Wubi under linux via NEOGRUB. That adds a NTS file to my windows folder. Anyways I reboot afterwards and ubuntu is there now as a choice but it doesnt boot into it. It flashes some text and goes to a command prompt i.e. grub. What do i need to do to get the correct boot entry in my windows files?


Ok i reinstalled Ubuntu for the 21st time and this is what is in eastBCD:

There is one entry in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

So i went to add/remove entires...clicked on linux tab....chose type WUBI...named it Ubuntu and clicked add entry.  Now easyBCD has this:

There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu
BCD ID:  {309ba0e1-1407-11de-b601-002243a1c513}
Drive:  C:\
Bootloader Path:  \NST\NeoGrub.mbr

replaced the menu.lst in the NST folder with the one in the ubuntu folder.....got into Ubuntu....it finished the install.....then rebooted after it was done and cant get back into ubuntu....i get a lot of text on my screen and then a grub command prompt.  I get the following now when i try to boot to Ubuntu:

Warning: Unrecognized partition table for drive 80.  Please rebuild it using a Microsoft-compatible FDISK tool (err=26).  Current C/H/S=16383/16/63

Error 19:  Cannot mount selected partition

Press any key to continue...

After i press a key it takes me to GRUB4DOS

What am i doing wrong?  is the Boot Enrty incorrect?

---

### Post by eluman75 on 2009-03-25
Sweet.....No reply...appreciate the help...everyone.

---

### Post by theozzlives on 2009-03-25
why don't you re-size your Vista partition and install the normal way?

---

### Post by eluman75 on 2009-03-25
> **theozzlives said:**
> why don't you re-size your Vista partition and install the normal way?

the first time i tried that....i had to reinstall windows completely b/c i couldnt boot into ubuntu or windows

---

### Post by sailthesea on 2009-03-25
It looks like you've tried to do a bit of both here With Wubi you shouldn't have to do any partitioning just defrag to make a good blank gap at the back of your drive then install totally within windows

---

### Post by eluman75 on 2009-03-25
> **sailthesea said:**
> It looks like you've tried to do a bit of both here With Wubi you shouldn't have to do any partitioning just defrag to make a good blank gap at the back of your drive then install totally within windows

did that but as posted in orginal post there is no boot entry for ubuntu afterwards and then the above problems happen.

---

### Post by sailthesea on 2009-03-25
You could try making a Livecd and booting into that to check things out
But you should probably go into vista and use fdisk to erase the partitions before you try again I don't use vista at all but I think you can only alter the partitions successfully from within 
 Once you get rid of the faulty stuff start over I'm sure MS make it difficult to run/install Linux on occupied machines Check the tuts, version, compatabilty etc and try other sources as its easy to go down the wrong path
Good Luck !

edit: EasyBCD doesn't look like something I'd go with in your situation

---

