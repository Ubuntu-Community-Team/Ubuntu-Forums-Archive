---
title: "Linux (terminal ubuntu) on T5545"
date: 2014-01-09
forum: Hardware
---

### Post by vidar-vidnes on 2014-01-09
Hi

I just wondered if it was possible to flash a t5545 thin client terminal with some lihgtweight minimalistic variant of ubuntu?. Prefferably one without a windows manager, terminal only so to say... Okay, mayby this was a silly question and that these clients are not capable of doing such things but what I need is  basically a standalone device which could run a lightweight  database or two, and maybe a git server, if I am lucky. 

these clients have 1GHz professor and 512MB Flash and 512MB Ram (64 reserved for video), which should be plenty for linux to run if you do not need useless stuff like unity and such.

They have pr. today a linux variant running called thinpro, but it seems not possible to root these and have fun with them. 



Breg
Vidar

---

### Post by adrian89 on 2014-01-10
You could install ubuntu-server if you want database on it. It is quite light, I have it on machine with 1.9Ghz proc, 1Gb of ram. Otherwise you could try installing from a alternate cd image which has an installer similar to windows xp(text based), and after that when you boot in the machine switch to terminal mode Alt+F1....Alt+F2 and then modify grub to boot only to terminal.

---

### Post by vidar-vidnes on 2014-01-22
Hi

I have been fideling around a bit and did some tests with LUBUNTU. The live CD boots well when i set boot option VGA=771 (due to limitations on the built in graphic card) but I am not able to install due to the requirement of having 1.8GB HDD, Which is a litle bit more than the 512MB i have available on the t5545. I tried to install LUBUNTU on a 4GB usb stick using unetbootin. I get the bootloader (grub i guess) and it starts booting but fails after a few seconds restarting the t5545. I don't know if it is some error unetbootin introduses or not, but I have had problems with bootable USB stick's before when using unetbootin. Any information on this anyone?

Question is, are there any distroes that will accept 512MB HDD somehow? I guess even for LUBUNTU there is a lot of space wasted to things i do not need. I did not find the alternate download anymore, has it been deprecated? I guess the alternate do not include all the graphical applications like abiword and such which only wastes space on a device that is ment to be run via terminal.

My plans for the t5545 is to run a mysql database server, a lightweight webserver, ftp and ssh server to remotly manage the device. Nothing fancy and only for internal usage.

Oh, by the way, Initially i said there where 512MB RAM, but it turns out to be 1GB which is nice.

---

### Post by mastablasta on 2014-01-22
try slitaz, tiny core, maybe puppy ( i think that one takes 200 soemthign MB not sure how good it does as server).

1 GB HDd - try ubutnu mini iso (i.e.e net install) and see if oyu can get away with it: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
how to: 

_[COLOR=#810081][http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)[/COLOR]_
[URL="http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html"]http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html
[/URL]
with no x.org etc you might get away with it.

though i would probably try out slitaz: [http://doc.slitaz.org/en:handbook:webserver](http://doc.slitaz.org/en:handbook:webserver)
it will leave you more room on disk

---

### Post by vidar-vidnes on 2014-01-22
Since I have had some experience with Slitaz earlier I went for that option. The base version boots fine and I get to terminal and everything is working except I cant get the network up and running. Working on that. However, I am not able to load live or gtkonly. The graphic board seems to be unsupported since the boot process halts just before I think it should switch to the windowmanager. I tried by altering boot options with VGA=771 which was the option that did the trick for LUBUNTU, but that did not help. I am not very fgamiliar with such boot options so there might be an option to make it work, so if someone know where I should look, I can do the looking. 

For now I might let it be with what I have achieved  so far with base version (And maybe I should swich to slitaz forum since this is not an ubuntu topic anymore ;) )

Now task is to get ethernet (DHCP) running and then to install slitaz permanently to my T5545. 
Yes I know i must use gparted and add grub manually first

---

