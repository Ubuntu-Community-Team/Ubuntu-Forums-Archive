---
title: "New to this. cant find out how to access ubuntu now that i installed it"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by HPspectre3 on 2009-10-10
hi i just burned 9.04 ubuntu and installed a 20 GB disk on my windows xp machine. ive looked on my desktop, my computer, start menu and putting the disc in my cd drive and turning my pc on without booting from cd and doing it with booting from cd, when i do that i can only do the basic options without installing it on my computer. i went through the instalation process with windows up and chose to use 20 GB of my hard drive. i see a folder called UBUNTU in my C/: root and thats it. it is 20.2 GB in size but i see no way to use it as an application. now that ive created space on my hard drive, how do i use it?
thanks

---

### Post by e_torano on 2009-10-10
Hm. Did you choose to use Grub as your bootloader or are you using the default windows one? If you're using the windows one, check the file c:/boot.ini and see if there's any mention of Ubuntu in it.

---

### Post by HPspectre3 on 2009-10-10
lol im not sure. i clicked on the middle choice. and went with the default choices i think. also, i searched my intire computer with windows search thing, i have no boot.ini

---

### Post by e_torano on 2009-10-10
Hm. Not sure what the middle option is because I haven't done a full ubuntu install from a disc in a while.

I'd guess that it's the windows bootloader though - grub would display ubuntu.

Sorry I can't be of more help atm D:

---

### Post by HPspectre3 on 2009-10-10
um well can u at leased tell me what grub is? lol maby i can search for answers from there.
thanks

---

### Post by e_torano on 2009-10-10
Grub is the bootloader which comes with Ubuntu. Since ubuntu 9.10, grub 2.0 has been in use.

Check out this page for details:

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

---

### Post by HPspectre3 on 2009-10-10
ok is there any command in command prompt that i can activate this bootloader? my CMD is a bit screwed up. i dont think its activated at startup.
thanks.

---

### Post by HPspectre3 on 2009-10-10
also, i dont know if this is ok but there is nothing in my C:/ubuntu\disks\boot\grub\ directory. i reistalled it and nothing. on my computer my cmd does not work propery and i often need to put in comands on some things that run automaticly.

---

### Post by Bartender on 2009-10-10
> **HPspectre3 said:**
> i see a folder called UBUNTU in my C/: root and thats it. 

Doesn't this mean you used wubi to place it inside the Windows partition?  Wubi is not the same thing as installing Ubuntu to its own partition...

---

### Post by SkyNet2029 on 2009-10-10
At boot up, you should now have an option to boot into ubuntu. provided you used wubi. It sounds like you did though...

---

### Post by presence1960 on 2009-10-10
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Bartender on 2009-10-10
presence1960 -
What does that boot info script utility report if it's a wubi install?  I haven't messed with wubi.  I understand that it's installed within Windows - does GRUB also install to the Windows MBR in a wubi setup?

---

### Post by presence1960 on 2009-10-10
> **Bartender said:**
> presence1960 -
What does that boot info script utility report if it's a wubi install?  I haven't messed with wubi.  I understand that it's installed within Windows - does GRUB also install to the Windows MBR in a wubi setup?

The script reports even in a wubi setup, it does not restrict it's reporting to linux, will report on any OS. It will report disk & partition info, MBR & bootloader info, in the case of windows will report boot.ini. In boot.ini in a wubi install you will see the line for Ubuntu. It will also report the menu.lst for ubuntu which BTW presents a GRUB menu after you choose Ubuntu from the windows boot loader.

I haven't used wubi since the beginning or middle of the summer. I installed it just so I could see how it works and increase my knowledge. While using it I used Windows daily also without defragmenting the NTFS partition and it did indeed suffer performance slowdown due to windows NTFS fragmentation- just as the documentation says it will. Even though wubi is not meant to be a permanent solution I wanted to become at least vaguely familiar with it since a lot of newbies wind up trying it.

---

### Post by HPspectre3 on 2009-10-10
```
alright i hope i do and did all this right
```

---

### Post by presence1960 on 2009-10-11
> **HPspectre3 said:**
> ```
alright i hope i do and did all this right
```

```
================================ sda1/boot.ini: ================================

[boot loader]

[COLOR="Red"]timeout=1[/COLOR]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu" 
```

You have your timeout set to 1 second, therefore you are missing the option to choose Windows or Ubuntu. You need to edit your boot.ini file. I believe you can do that through control panel > System in XP.

---

### Post by presence1960 on 2009-10-11
OK, I booted into XP. here is how to adjust the timeout.

Control Panel > System > Advanced tab > Startup & Recovery "Settings" button > check Time to display list of Operating Systems and then set time in seconds. This will determine how long the menu to choose windows or Ubuntu will be displayed. At one second you really have no time to see it let alone choose.

If you like Ubuntu after trying it, I would recommend partitioning your disk and installing Ubuntu to it's own partition. Wubi is not meant to be a permanent solution, just a test drive for those unwilling to partition their disk until they decide they really like Ubuntu. 

Here are some links on wubi:

[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

### Post by HPspectre3 on 2009-10-11
dude [presence1960]("http://ubuntuforums.org/member.php?u=657448"). thank you so much this is frickin great and you are the s***!
its working now and i couldnt be happyer :guitar:

---

### Post by presence1960 on 2009-10-11
> **HPspectre3 said:**
> dude [presence1960]("http://ubuntuforums.org/member.php?u=657448"). thank you so much this is frickin great and you are the s***!
its working now and i couldnt be happyer :guitar:

Glad you got it working. Enjoy Ubuntu.

---

