---
title: "network and USB mouse freeze"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by nautilu on 2006-06-05
Ok i just installed a fresh copy of ubuntu dapper on my LG laptop (LE50),
wich has ATI radeon xpress 200m chipset.


after working for few minutes (could be 2, could be 20) my USB mouse stops respondig (even though the touch pad keeps working).
in addition, and i don't know how it's connected, but at the same time i don't have a network connection anymore. can't even ping my second computer on my home net.
to make it work again i have to reboot the system


Not to mention that i still couldn't make my wireless work.

---

### Post by nautilu on 2006-06-05
i just noticed that i don't have anything ATI related installed

insted nvidia-kernel

could it be the problem?

---

### Post by aszoz on 2006-06-05
Have similar problem with Fujitsu-Siemens L1310G, ati radeon xpress 200
  just upgraded to DD, and my usb mouse stops working after some time.
  Everything else is fine;
  Any suggestions?

---

### Post by nautilu on 2006-06-06
> Have similar problem with Fujitsu-Siemens L1310G, ati radeon xpress 200

What kind of Wireless card do you have?

it could be realted  to the fact that there's no drivers for the wireless card, even though the kernel recognize it.
so first thing to do is to make the wireless work with proper drivers.

---

### Post by villelai on 2006-06-06
[QUOTE=aszoz]Have similar problem with Fujitsu-Siemens L1310G, ati radeon xpress 200
  just upgraded to DD, and my usb mouse stops working after some time.
  Everything else is fine;
  Any suggestions?[/QUOTE]

I have same laptop, same distribution and same problem. Without fglrx everything works fine. But when using it, mouse freezes after some time and sometimes even keyboard stops responsing.

- ville

---

### Post by nautilu on 2006-06-06
well i just managed to make my wireless card work flawlessly (with Windows Drivers for my card)
and for [COLOR="Red"]now[/COLOR] don't have any feezing problems. (still don't know how my problem connected to this)

hope it'll stay that way

---

### Post by seanwnz on 2006-06-13
I have this problem too - my mouse stops working at random times, and I have to reboot the computer to get it running again. The touchpad still works fine.

Someone please help :)

My computer:
Toshiba Satellite M70
ATI Express 200m
Dapper

---

### Post by Shinsei on 2006-06-13
This also happens with my installation. If I'm using the fglrx module with the 8.25.18 drivers, all external USB devices shut down within five minutes of starting X. Using the generic 'ati' driver, it works fine. 

Wireless networking, keyboard and Synaptics touchpad all work fine after this happens.

---

### Post by nautilu on 2006-06-14
i reinstalled to Kubuntu 6.06 and none of it ever happened.

no fglrx drivers are used.

That's my only advice.

---

### Post by Eversmann on 2006-06-24
Same problem, same laptop (fujitsu amilo l1310g). Using fglrx (8.24 from ati or 8.25 from ubuntu) sometimes it freezes my external usb mouse with the message from psmouse.c went out of sync.

With no fglrx everything works ok.

Btw, atheros card working with compiled drivers from madwifi.org adding modprobe ath_pci rfkill=0 to enable radio.

---

### Post by saintjohnny on 2006-09-18
Bump...


Hey has anyone had any progress with this?  I'd rather keep the correct drivers for my video card and rought it without a USB mouse.  Thats just better for my uses.  Thanks in advance

---

### Post by lemmis on 2006-10-13
I have the same problem on my Toshiba Satellite with Ati 200m chipset, except that I don't have fglrx installed and it freezes even so. The mouse stops working after a couple of minutes, and the only thing that helps is a reboot.

---

### Post by digitalp1mp on 2006-10-17
Yup same here. Toshiba Satellite with ATI 200. fglrx kills all usb.  Mouse and Thumb drive. :confused: :confused: :confused:

---

### Post by rlozano on 2006-10-18
hiya guys..

this seems to be a problem with the buil-in ATI driver of Ubuntu. It's not the mouse that is actually dying. if you will look further into it, it is the USB that is actually dying. anything you insert in the USB port after your mouse stops moving will not be functional anymore. if you plug-off your mouse then plug-in again, notice that the optical light will not turn-on anymore.

here's my 2 cents suggestion/solution:

1. for those in dapper, things with built-in ubunt ATI driver seems to work fine. don't upgrade to fglrx anymore. for those who have upgraded to fglrx, revert back to your old ATI driver. 

2. for those in edgy, upgrade your ATI driver to binary ATI drive fglrx. this should solve the problem.

in both cases, before you do anything else, please see your xorg.conf for verification.

hope this helps....

---

### Post by digitalp1mp on 2006-10-18
Well i found that using the "noapic" or "nolapic" option usb wont freeze and the fglrx driver works fine. BUT now my network wont work. Computer sees the card eth0 but dhcp fails to grab an address. Wont work with static entry either. This is getting annoying.:mad:

---

### Post by digitalp1mp on 2006-10-18
ok got it. add "noapic" AND "irqpoll" <---if network wont work.

Everything working :D

---

### Post by poseydon on 2006-10-30
The same problem for me on edgy, after a while my mouse freezing but the touchpad still working, i have a Toshiba satellite laptop and with dapper i have no problems.

---

### Post by samurai1200 on 2006-11-08
It couldn't be an ATI thing... I am having the exact same problem with my computer (Nvidia 590 chipset). Regardless, i have no specialized drivers installed.  Mouse seems to freeze up only when i let it sit for an amount of time... as long as I keep moving it at least once every couple of minutes, it stays "alive".

Some massive searching around this forum reveals... nothing. The device logs say nothing, and nobody has found a fix except for:

```
sudo modprobe -r usbhid
sudo modprobe usbhid
```

but i have not tried this yet. every time my mouse freezes, i don't happen to have a terminal window open...
unplugging and re-plugging the mouse's usb cable doesnt work, whether or not i switch usb ports.

I have "noapic" running by default, its the only way the kernel will load with my processor (athlon x2... i believe its due to some timing issue).

Here is an old thread of some folks having the same problem, over a year ago:

[http://www.ubuntuforums.org/showthread.php?t=28173&highlight=mouse+freeze](http://www.ubuntuforums.org/showthread.php?t=28173&highlight=mouse+freeze)

no fix, though. ](*,)

I'm about ready to format and install Dapper Drake to see if that is the problem. Anyone know much about the difference in kernels for Dapper Drake vs Edgy Eft?

---

### Post by g1nsu on 2006-11-09
Just to add some more info to the thread.
I am having the same problem with the USB [optical] mouse freeze on a desktop machine. It works fine as long as I am active. Once it sits for a while, it freezes and requires a reboot. 

I have tried without success:
1. noapic on boot options
2. irqpoll on boot options -freezes machine on boot
3. added Option "DisableIRQ" to my video cards in xorg.conf
4. disabled legacy USB in the bios

Kubuntu edgy - with kernel update from a couple of days ago
AMD64
nvidia 590 chipset

Anyone using a USB optical mouse with success?

---

### Post by samurai1200 on 2006-11-10
There are many people using USB mice with success, I'm sure. The problem is our USB controllers. For some reason, the VIA chipset and the NForce (maybe just 590) chipset are causing this problem, or at least this is what it seems like.

I am also on an NForce 590 (Asus M2N32-SLI Deluxe WIFI)

---

### Post by saintjohnny on 2006-11-10
Just out of curiosity, is anyone having these problems on desktops?  I'm having the problem on a laptop with an ATI card.  It seems like its laptop with ATI specific.

---

### Post by samurai1200 on 2006-11-14
Uh, me. See my above post. Nvidia mobo and Nvidia video card.

---

### Post by saintjohnny on 2006-11-15
> **samurai1200 said:**
> Uh, me. See my above post. Nvidia mobo and Nvidia video card.
ok correction 99% of the ppl having this problem have ATI and more importantly a **laptop**.  

(I saw your thread but your problem seems to be different in that you can "keep it alive" by moving your mouse.)

---

### Post by mooz on 2006-11-15
I have the same problem with an ASUS L5D (nVidia chipset and nVidia Graphic card) since I installed Edy Eft. Theese are rows of my lspci relative to USB controller:

00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)


I'm using nVidia propetary drivers and wl_apsta.o for my Broadcom 4306 wireless chipset (that doesn't work at all when mouse freezes); I experienced the same problem other times... but I didn't understand how I got things work the other times! Pheraps whit a kernel update/recompilation it will work?

I noticed this thing: 

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

The numbers are the same of the USB controller, is it the same for all people having this problem?

---

### Post by saintjohnny on 2006-11-15
Interesting...

The fact that us ATI people can solve the problem by NOT using the fglrx driver, proves that its ATI driver related.  So there may be a handful of different but similar usb mouse problems floating around?  Very confusing and I just about give up.  :-?

---

### Post by tailon on 2006-11-24
Hi guys / gals 

i had the same problem with my mouse freezing , i went into the bios and turned of support for USB Legacy devices . haven't had a problem since 

hope that helps

---

### Post by masukomi on 2007-02-10
Disabling the legacy USB support in the BIOS solved the problem for me too. Thanks.

---

### Post by Galactix on 2007-04-19
I can confirm this, turning off USB Legacy fixes USB hang-ups. 

However, now I have no keyboard in Grub... (no windows -> no games = more spare time) so not much of a problem. 

But still, this indicates there is something wrong in the USB Legacy support.

Should we file a Bugreport for this? It seems to me Legacy USB is flawed un at least Ubuntu, not sure about other distributions.

Reference: lspci:
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)

First I thought it was my Logitech G15 messing things up, no problem any more.

---

### Post by Galactix on 2007-05-11
Elsewhere on this forum (can't seem to find where, sorry) I found someone with a similar problem concerning a USB external harddrive. 

He reported having solved his problem by adding the following lines to the boot options in /boot/grub/menu.lst:

acpi=force irqpoll

(that would be right after the 'ro quiet splash' of your kernel description).

This way we can leave Legacy USB on in BIOS so we have USB keyboard support in grub which is always nice. 

Seen as there have been no replies to this thread for two weeks I assume this problem resolved?

---

### Post by dbzeroone on 2007-06-23
I (well, my gf) is using a Toshiba Satellite A-105 and the disable legacy USB thing worked perfectly! THANK YOU ALL!!!

EDIT: I take that back. It worked for about 10 minutes, which is a 500% improvement, but not perfect :(

---

### Post by DarthDie on 2007-06-25
Any updates with this? Does acpi=force irqpoll  fix this problem? I am currently using latest ubuntu version, with a Sony Vaio Desktop, with a Logitech G7 mouse...and after my computer has been idle for a little bit (not sure how long) my mouse will lock up....any updates on this?

---

### Post by toutatis on 2007-07-11
Symptom: My USB mouse froze after a random (5-20 minutes) time. More predictive was the mouse freeze after using the "power off" button in the upper right. Not only the mouse was dead but no USB ports were working anymore. Only booting solved this.
Platform: Toshiba Satellite Pro A100 , Feisty 7.04, ATI fglrx driver 

> **Galactix said:**
> ...
He reported having solved his problem by adding the following lines to the boot options in /boot/grub/menu.lst:

acpi=force irqpoll

(that would be right after the 'ro quiet splash' of your kernel description).

This way we can leave Legacy USB on in BIOS so we have USB keyboard support in grub which is always nice. 



This really worked for me. I'm already working an hour without a freezing mouse. :)
**BTW: Disabling Legacy USB didn't work for me!**

I had some problems changing /boot/grub/menu.lst. My changes kept disappearing everytime I booted  :confused::confused:
[Could be my lack of experience with Ubuntu or my Wubi install, but this is really annoying.
On [ the BootOptions page (permanent changes)]("https://help.ubuntu.com/community/BootOptions#head-ad7f18d198436d5a503cd6056d57b0db62819cf8") I found a way to solve this:

> 
Once you know you need to boot with a special option on your installed system, you'll have to edit the file /boot/grub/menu.lst to make the boot option permanent.

To to this please do the following:

```
sudo nano /boot/grub/menu.lst
```

Add the option to the line that starts with "# kopt=". Then run

```
sudo update-grub
```

to have the menu entries updated.

NB! If you instead edit the menu entries directly, your changes will magically disappear the next time update-grub is run, for instance when system packages are updated. 


This line in my menu.lst is now:
```
# kopt=find=/wubi/boot/linux ro **acpi=force irqpoll**
```

After update-grub the kernel-lines in my menu.lst are modified into:
```
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro **acpi=force irqpoll** quiet splash
```




Roel

---

### Post by progvb on 2007-11-12
I have a problem with my mouse, after 5 or 10 minutes it freeze but the keyboard continue responding and i have to reboot the PC for mouse freeze off.

I have an ATI RADEON x1600 (Driver fglrx), motherboard ASUS P5N32 SLI.

What can i do with that??? :(:(

help me.

reply me please. 

[email]elprogramadorfox@gmail.com[/email]

---

### Post by Fraterius on 2007-12-02
Ok here's the deal if you have an nvidia GPU the conclusion is that there is no driver conflict, I had some problems in finding USB legacy in my bios, the cause is very simple it's not there :). In my bios this function is divided in two and both of them suppose to be disabled.

1) USB mouse support
2) USB KB/storage support

If we will do that, there will be no more USB freeze issue ;).

---

### Post by Psyphre on 2007-12-23
> **Galactix said:**
> Elsewhere on this forum (can't seem to find where, sorry) I found someone with a similar problem concerning a USB external harddrive. 

He reported having solved his problem by adding the following lines to the boot options in /boot/grub/menu.lst:

acpi=force irqpoll

(that would be right after the 'ro quiet splash' of your kernel description).

This way we can leave Legacy USB on in BIOS so we have USB keyboard support in grub which is always nice. 

Seen as there have been no replies to this thread for two weeks I assume this problem resolved?

Im not quite sure where I put "acpi=force irqpoll"

Here is my menu.lst:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bd0b7391-608d-40ec-8a7a-3dd3847eb0a8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

Do i literally put it after "ro quiet splash"? Like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bd0b7391-608d-40ec-8a7a-3dd3847eb0a8 ro quiet splash **acpi=force irqpoll**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

---

### Post by hjalle on 2008-02-09
I have also mouse and keyboard freeze. **Only** when using **Torrent client**. 
Freeze application in my PC
Bittorrent
Ktorrent
(I haven't tested any other client yet)

My Ubuntu computer is connected to internet through a another computer, wireless.

---

### Post by Zakron on 2008-04-30
My system is a desktop with the identical problem. After installing ATI drivers, my usb mouse (both logitech and microsoft mouses) would freeze a minute into using ubuntu after entering the login details.  If the ATI Drivers were not installed, then the mouse did not have any problems.

My computer is a Intel Core 2 Duo, 2GB RAM, ATI 1900XT, nVidia Nforce5 chipset.

I can confirm that the problem has been solved after entering the bios by pressing 'del' or 'f2' as soon as the computer is powered on, and setting the menu item "enable USB legacy support" to 'disabled'.  I also had enable USB which I left enabled (obviously) and enable USB 2.0 (which If not enabled leaves the system with old USB 1.1 support only).

100% confirmed as problem solved for my particular configuration based on the 'ATI and USB mouse freeze conflict' discussed here.

---

