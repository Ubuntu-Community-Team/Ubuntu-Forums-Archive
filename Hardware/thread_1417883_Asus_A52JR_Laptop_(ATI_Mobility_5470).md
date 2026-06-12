---
title: "Asus A52JR Laptop (ATI Mobility 5470)"
date: 2010-02-27
forum: Hardware
---

### Post by blackbinary on 2010-02-27
I have a laptop with an ATI Radeon Mobility 5470 graphics card.
It seems Ubuntu does not recognize the card. jockey-gtk does not recognize any usable restricted drivers, it seems to be stuck with a veerrry slow vesa, making the install unusable. 

I just wanted some help confirming that it is because the card is so new. The point I'm at now, i suspect I'll have to wait for AMD/ATI to release the next linux driver (10.3) which would include support for my card. 

Has anyone had luck getting even simple 2D Acceleration working with these Mobility 5000 series cards, using other drivers? 
I tried radeon and radeonhd with no luck, but i suppose there is a chance I have set them up wrong.

Thanks, and i appreciate the help.

---

### Post by knuby on 2010-02-28
I have the same laptop ASUS K52J with Kubuntu 9.10, and now I am also looking for a solution of the same problem! I tried this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), ATI installer works without errors/crashes, but in fact the driver could not be installed, ```
~$ fglrxinfo
Segmentation fault
~$ aticonfig --initial
aticonfig: No supported adapters detected
```A little offtopic: I have just installed ethernet on this laptop, and it was not simple, [http://ubuntuforums.org/showthread.php?t=1402076](http://ubuntuforums.org/showthread.php?t=1402076) was a solution.

---

### Post by blackbinary on 2010-02-28
Yes, i also tried compiling the binary driver from ATI.

If you notice, their most recent driver for linux (10.2) does not actually support the Mobility HD 5000 series, only the desktop HD 5000 series. I am pretty sure 10.3 will have this support. That is why when you try to install ATI's drivers, it says there is no hardware that the drivers can use, because it doesn't support them. 

One other thing, your fglrxinfo seg faulted, you have to restart your computer before you can use that command, then no segfault. 

As for ethernet, i did not know it was such a hassle. I almost exclusively (or exclusively haha) use the wirless, which works fine (However, there is a strange bug, that after connecting to my wireless through ubuntu, rebooting and going into win7, win7 thinks my wireless adapter is 'disabled'. And i have to renable it every time)

Anyways, it looks like we're waiting for Catalyst 10.3, unless someone else has the answers...

---

### Post by knuby on 2010-02-28
Yes, it seems that the ATI Mobility Radeon HD 5400s are unsupported yet.
Please post when you have it figured out or new Catalyst has been released.

---

### Post by blackbinary on 2010-02-28
Will do.

---

### Post by sleepitoff on 2010-03-01
First, make sure you have 'unsupported updates' and 'prereleased updates' checked in Synaptic's repository preferences. 

Then, just run the 10.2 catalyst and you'll be on your way. (directions listed at  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) just substitute the catalyst number. ) 

Kubuntu doesn't work (freeze on log-in), so you'll be stuck to Gnome, and always have a watermark in the bottom right hand stating "AMD Unsupported Hardware," but other than that, everything will work OKAY.

---

### Post by knuby on 2010-03-03
sleepitoff: Thank you! Now I am using Gnome, and ATI Catalyst works fine there!

---

### Post by Yellow Pasque on 2010-03-03
> I tried radeon and radeonhd with no luck, but i suppose there is a chance I have set them up wrong.
Hopefully, 2D acceleration will come soon with the open-source drivers. Once the first rc of the 2.6.34 kernel is out, you can use that and the xorg-edgers PPA to get mode-setting support (i.e. full resolution).

---

### Post by blackbinary on 2010-03-04
Just booted into Linux and it recognized there was something new to install, and voila it works (with watermark)

Now the only question is why the heck my internet is so slow (wireless).

---

### Post by sleepitoff on 2010-03-05
Yeah, for some reason network-manager didn't work very well on my  ASUS laptop (k52jr) and it would disconnect every few minutes, the fix I found is to use wicd instead of network-manager (sudo apt-get install wicd , or look in synaptic for wicd) No more disconnections, so I'd try that if I were you. 

Also, for the watermark, make this a script and run it: > #!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6
}'); do
 echo found $x
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

^Found that script on the phoronix.com forums and it works !

---

### Post by Kurotowa on 2010-03-06
Working here too, many thanks ! That watermark was becoming sooo annoying ^_^

---

### Post by blackbinary on 2010-03-07
I have tried wicd, and it hangs at the stage where it is obtaining an IP address. Also, the wireless in the A52JR can be 3 different kinds (or perhaps thats just for A52J), is yours Atheros?

---

### Post by sleepitoff on 2010-03-21
Yeah, Atheros, but I was having problem with my signal being so weak for some reason so I further investigated the problem and found out you have to install karmic backports for it to properly work, and after doing this, everything is perfect. 

sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install linux-backports-modules-karmic 
reboot 

Also, I want to say, tonight I downloaded and installed the daily build of Lucid Lynx and was pleasantly surprised and very, very happy to see that right off the bat, I booted into the correct resolution, KDE is running fine, and no problems with multiple monitors or anything display related! How nice is that!? No messing around with ATI's catalyst, and with the 5470, we know this is a pain.

---

### Post by blackbinary on 2010-03-26
Thanks for that sleepitoff. It is a bit sad though, the drivers are only available for ubuntu 10.04 development. ATI gave them the drivers ahead of time, for any other distro that wants latest Xorg support, we have to wait till Catalyst 10.4

---

### Post by xycris on 2010-11-15
has anyone tried the new catalyst 10.10 on ubuntu 10.10 with the 5470 hd?

---

