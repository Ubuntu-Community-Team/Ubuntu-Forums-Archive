---
title: "Error 17........."
date: 2008-10-18
forum: General Help
---

### Post by Taz. on 2008-10-18
Hey guys, im totaly new to linux.. i know nuthing about it.

All i did: Took the x64 ubuntu latest .ISO installer, boot it from cd and installed it on my external hard drive whic is a 160 gb , and is recognized by my mother board. My CPU is an AMD Turion64 X2.

And i have vista as a main OS on my pc's HDD. Now i try to boot, everything works fine. I get a menu, to boot:

-Boot ubuntu
-Boot the recovery
-Boot the memtest
-boot vista
-and another boot vista only this one works.

When i press boot ubuntu, it says: Error 17: Unable to mount.. sumthing, i forgot what was it..

What can i do? Thanks alot ppl for your help, which is highly appreciated :) Thanks in advanced...

---

### Post by Bucky Ball on 2008-10-18
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

That will explain what is happening. Grub is looking in the wrong place for Ubuntu basically. Your easiest option for the moment would probably be to go to:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

... download the iso, burn a cd and boot from it and there is a good chance it can reconfigure things for you. Once you can get into ubuntu, you can have a bit more of a look around and we can let you know how to delete the dead Vista entry (if super grub disk doesn't do that for you). Good luck and welcome. :)

---

### Post by Taz. on 2008-10-18
> **Bucky Ball said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

That will explain what is happening. Grub is looking in the wrong place for Ubuntu basically. Your easiest option for the moment would probably be to go to:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

... download the iso, burn a cd and boot from it and there is a good chance it can reconfigure things for you. Once you can get into ubuntu, you can have a bit more of a look around and we can let you know how to delete the dead Vista entry (if super grub disk doesn't do that for you). Good luck and welcome. :)

Are you sure about that? Bcse i dont wanna waste a 700 mb cd for 4 mb..

---

### Post by WWSmith36 on 2008-10-18
You can try booting into ubuntu from the grub command line interface.  When you get the grub menu hit ´c´ to get into the CLI.

First first the correct drive/partition that ubuntu is on.

```
grub> find /boot/grub/stage1
```

Should give you output like (hd?, ?)

Now you can hit escape and to get back to the grub menu.
Now this time select ubuntu and hit ¨e¨ to edit.

change root statement to whatever your output was from the find command
root (hd?, ?)
then hit enter and then ´b´ to boot.

When you get into ubuntu open a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

You will need to edit this file so it will boot properly.  Edit the 

# groot=(hd?,?)

and the root statements of your boot menu.

Hope this help

---

### Post by Taz. on 2008-10-18
> **WWSmith36 said:**
> You can try booting into ubuntu from the grub command line interface.  When you get the grub menu hit ´c´ to get into the CLI.

First first the correct drive/partition that ubuntu is on.

```
grub> find /boot/grub/stage1
```

Should give you output like (hd?, ?)

Now you can hit escape and to get back to the grub menu.
Now this time select ubuntu and hit ¨e¨ to edit.

change root statement to whatever your output was from the find command
root (hd?, ?)
then hit enter and then ´b´ to boot.

When you get into ubuntu open a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

You will need to edit this file so it will boot properly.  Edit the 

# groot=(hd?,?)

and the root statements of your boot menu.

Hope this help



thats so complicated, can u go with less words like.... groot? or w.e? Im still begininer its been not even 1 day i know bout linux. Can ya do it like.. Step by Step?

and bout the .ISO thingy? Should i try it?

---

### Post by TeXtonyx on 2008-10-18
There is a floppy version of Super Grub, but I haven't used it.
A few days ago I got an error 17 and used the Super Grub cd in
"help" mode. I followed the directions and it showed grub in
(hd0,4) I believe (grub is installed to the boot partition). So I
booted into Ubuntu and from Super Grub. Then I looked at menu.lst
in /boot/grub and it listed Ubuntu as (hd0,5); I think I messed
with the partitions. I edited menu.lst, sudo gedit /boot/grub/menu.lst
and changed all the (hd0,5) entries to (hd0,4) and it worked.

---

### Post by Bucky Ball on 2008-10-18
> **Taz. said:**
> Are you sure about that? Bcse i dont wanna waste a 700 mb cd for 4 mb..

? That would cost the grand total of about 25c where I come from. Having supergrubdisk on hand is never a waste. I would be surprised if it didn't fix your problem quick and easy. Good luck anyway.

---

### Post by Taz. on 2008-10-18
> **Bucky Ball said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

That will explain what is happening. Grub is looking in the wrong place for Ubuntu basically. Your easiest option for the moment would probably be to go to:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

... download the iso, burn a cd and boot from it and there is a good chance it can reconfigure things for you. Once you can get into ubuntu, you can have a bit more of a look around and we can let you know how to delete the dead Vista entry (if super grub disk doesn't do that for you). Good luck and welcome. :)


Tried it, tried it several times still nuthing. What now please?

---

### Post by caljohnsmith on 2008-10-18
OK, how about booting your Live CD, open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
See if you can get that far, and if not, try and at least post the output of the first "fdisk" command above. :)

---

### Post by Taz. on 2008-10-18
> **caljohnsmith said:**
> OK, how about booting your Live CD, open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
See if you can get that far, and if not, try and at least post the output of the first "fdisk" command above. :)


You dont understand. This is chinese for me. Can you explain in details step by step please?

EDIT: im using vista btw.

---

### Post by caljohnsmith on 2008-10-18
OK, when you boot your Live CD, when you get to the first menu, select the "try Ubuntu without making changes" option. Once you get to the Ubuntu desktop, in the upper-left corner of your screen is an Applications menu, click it and go to Accessories, then select "Terminal". From there you can enter the commands. See if you can get to that point.

---

### Post by Taz. on 2008-10-18
> **caljohnsmith said:**
> OK, when you boot your Live CD, when you get to the first menu, select the "try Ubuntu without making changes" option. Once you get to the Ubuntu desktop, in the upper-left corner of your screen is an Applications menu, click it and go to Accessories, then select "Terminal". From there you can enter the commands. See if you can get to that point.

I got no live cd.. I got ubuntu installed on my external hard drive... Should i do a live cd?

---

### Post by caljohnsmith on 2008-10-18
OK, just to clarify, you originally said:
[QUOTE=Taz.]All i did: Took the x64 ubuntu latest .ISO installer, boot it from cd and installed it on my external hard drive whic is a 160 gb , and is recognized by my mother board. My CPU is an AMD Turion64 X2.
[/QUOTE]
So did you burn the Ubuntu ISO to CD, boot it up, and then use the "install Ubuntu" option? Or did you select the "try Ubuntu without making any changes" option and then use the Ubuntu installer once you got into the Ubuntu desktop? When you get the boot menu on start up, does it say anything about "Grub"? Or does it look like it is a Vista boot menu?

---

### Post by Taz. on 2008-10-18
> **caljohnsmith said:**
> OK, just to clarify, you originally said:

So did you burn the Ubuntu ISO to CD, boot it up, and then use the "install Ubuntu" option? Or did you select the "try Ubuntu without making any changes" option and then use the Ubuntu installer once you got into the Ubuntu desktop? When you get the boot menu on start up, does it say anything about "Grub"? Or does it look like it is a Vista boot menu?


I came to the ubuntu meny and i pressed Install Ubuntu, it formated my extarnal HDD and then installed ubuntu on it. Weird now i cant acces my HDD anymore...

---

### Post by Taz. on 2008-10-18
Ok guys, forget all this, i dont want ubuntu anymore. I wanna unsintall it.. from my extarnal hard drive how? And when i plug my HDD in vista its not showing.. what to do?

---

### Post by Taz. on 2008-10-18
> **caljohnsmith said:**
> OK, when you boot your Live CD, when you get to the first menu, select the "try Ubuntu without making changes" option. Once you get to the Ubuntu desktop, in the upper-left corner of your screen is an Applications menu, click it and go to Accessories, then select "Terminal". From there you can enter the commands. See if you can get to that point.


OK, i got to that point.

---

### Post by caljohnsmith on 2008-10-18
Since you installed Ubuntu under Windows, you should be able to just boot into Vista and use the Add/Remove Programs to remove Ubuntu (or whatever it is called in Vista, I use XP). If you're not interested in Ubuntu any more, there's nothing wrong with removing it. We understand that Linux isn't for everyone.

---

### Post by Taz. on 2008-10-18
> **caljohnsmith said:**
> Since you installed Ubuntu under Windows, you should be able to just boot into Vista and use the Add/Remove Programs to remove Ubuntu (or whatever it is called in Vista, I use XP). If you're not interested in Ubuntu any more, there's nothing wrong with removing it. We understand that Linux isn't for everyone.

1-Ubuntu ROCKS. Ill be using it soon.

2-I managed to get back my HDD to NTFS.

3-I tried it on live CD, but i dont have wireless connection... I have a Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter

Any ideas, and thanks for all :guitar: :arrow: ROCK ON!

---

### Post by melojo on 2008-10-18
I used this thread to get my rtl8180 to work using ndiswrapper and the windows driver.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by Bucky Ball on 2008-10-19
What make is the machine? I couldn't find that in the thread.

---

### Post by Taz. on 2008-10-26
> **Bucky Ball said:**
> What make is the machine? I couldn't find that in the thread.


Toshiba A210

---

### Post by nothingspecial on 2008-12-04
Here`s a solution to your wireless. At the bottom it says it works with your make and model.


[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

---

