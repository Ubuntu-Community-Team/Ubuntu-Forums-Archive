---
title: "Gigabyte T1028M Issues with Touchpad and Touchscreen"
date: 2009-08-03
forum: Hardware
---

### Post by Legolover64 on 2009-08-03
Hey guys!

I have a Gigabyte T1028M tablet netbook. I love it. It shipped with XP, however, and for a guy who's used to SSHing into his machines, this would not work. I have had OS X running on it for a while, but I was not very pleased with the hardware incompatibility, so last night I installed Kubuntu 9.04.

Unfortunately, the mouse does not work. I know it is a multitouch mouse, and a place where I was reading stated it was made by elantech. I searched around on the Ubuntu forums, and none of the resources helped me. I have sudo apt-get update'd and sudo apt-get upgrade'd to the newest versions of everything in the repositories, so I should have the newest stuff (right?).

Anyways, I'm looking for help getting the touchpad (made by potentially Elantech) and the touchscreen (made by eGalax) working under Kubuntu. Does anyone have any ideas? The mouse currently does not work at all, however the touchscreen does allow me to click, but not move the mouse.

Furthermore, how can I check if the webcam is working, if the computer can sleep properly, and if other features of it work? Any easy way?

Thanks in advance!

---

### Post by Favux on 2009-08-03
Hi Legolover64,

I think eGalax has linux drivers.  Also I believe the evtouch driver works for it.  Check Synaptic Package Manager to see if evtouch is installed.

For the webcam you could try installing Cheese through Synaptic.

---

### Post by Legolover64 on 2009-08-03
Thank you for the reply!

I installed evtouch, but randomly (less than 5 minutes after the display manager loads) the entire computer locks up! I can't move the mouse (with the touchscreen) or type anything.

Unfortunately, the trackpad also still does not work. Does anyone have any ideas about how to fix it?

EDIT: Also, for the eGalax drivers, how do I know if the touchscreen is hooked in via RS232, PS/2 or USB? I need this to be able to install it.

---

### Post by Doktor.Wahnsinn on 2009-08-04
Hi Leglover64,

i check some fixes from the 902 out, the touchpad one works with my t1028x fine:


open /boot/grub/menu.lst as root

go to the line begins with '# kopt=root=UID=123123123123... ro ' and put after this 'i8042.noloop=1'


save and rebuilt with 'sudo update-grub '

reboot and the touchpad works fine.

I also checked out some fix-ideas for the touchscreen. The Penmount doesnt work, it crashes like you said randomly after a few minutes.

The Ubuntu Setup installs touchpad drivers nearly good, the right mouse-click isnt avaiable, and not so fast as with the reinstalled penmount driver it crashes, too.

Maybe it is an special problem for the  variant of the 1028 with hd-resolution..?

I hope this helps a little, maybe someone has a resolution for the touchpad problem.

Best regardes,

Doktor Wahnsinn

---

### Post by Legolover64 on 2009-08-05
> **Doktor.Wahnsinn said:**
> Hi Leglover64,

i check some fixes from the 902 out, the touchpad one works with my t1028x fine:


open /boot/grub/menu.lst as root

go to the line begins with '# kopt=root=UID=123123123123... ro ' and put after this 'i8042.noloop=1'


save and rebuilt with 'sudo update-grub '

reboot and the touchpad works fine.

I also checked out some fix-ideas for the touchscreen. The Penmount doesnt work, it crashes like you said randomly after a few minutes.

The Ubuntu Setup installs touchpad drivers nearly good, the right mouse-click isnt avaiable, and not so fast as with the reinstalled penmount driver it crashes, too.

Maybe it is an special problem for the  variant of the 1028 with hd-resolution..?

I hope this helps a little, maybe someone has a resolution for the touchpad problem.

Best regardes,

Doktor Wahnsinn

Thank you so much for your advice!

I now have the trackpad working.

However, I now have problems with the wifi. How do I get it to work? Also, how do I get the sleep and ACPI to work? How does i work on the T1028X?

Thanks again!

---

### Post by Doktor.Wahnsinn on 2009-08-05
Hi LegoLover64,

try this: Put your t1028 during the setup via hardwire lan to your dhcp router,which is online.

The setup checks than additional the possible hardware matches with an internet source up.

I have working wifi,acpi - means standby/suspend mode. In suspend mode the wifi doesnt wake upd the hardkey also is dead ,but in standby it does run, thats is ok for me; all works with the normal ubuntu network image.

greetings,

Doktor Wahnsinn

---

### Post by Legolover64 on 2009-08-05
Thanks for the idea. I will try that.

I am distressed that my wifi is not working. I feel as though it's possible that the switch was turned "off" before I installed ubuntu. Is there any way to turn this on without reinstalling windows?

---

### Post by Doktor.Wahnsinn on 2009-08-05
Hi,
this is not important for wifi installation, its just a hardkey put throught the keyboard chip. If it not works, its another problem.

as i said, check setup with online status.

greetings,

Doktor Wahnsinn

---

### Post by Legolover64 on 2009-08-06
Doktor Wahnsinn,

Do you have any ways of getting the touchscreen to work? Beyond the evtouch/nonfunctional eGalax drivers, what do you recommend? Is there any way to get evtouch to not crash?

My WiFi is also definitely not working, I do not know why. I had the computer plugged in while installing... any ideas?

Also, is there any way to configure the button on the side of the computer to rotate the screen so the computer can be used in portrait mode?

---

### Post by Doktor.Wahnsinn on 2009-08-10
Hi,

as i said, my touchpad works fine after installation with the ubuntu network image. maybe its another device in the 1028m than in the 1028x.

i try to get infomrmations about the used hardware.

the same to your wifi problem. it works 'out of the box' fine, with a better connection quality and speed than on xp.

i checked the button not out until now, it gives no action , nether to the editor or any other effect.

i use an equal button on my athena, would be nice, if it works in the same way.

meanwhile you can go to panell,add to panel and choose the screen icon .

after this, it appears at the top panel and with mouseclick left you can choose rotation now directly.

if you have something new, post it, i'll too.

best regardes,

Doktor Wahnsinn

---

### Post by Legolover64 on 2009-08-13
Thanks so much for your help Doktor Wahnsinn!

I have another question. I tried again with evtouch, after I reinstalled with a network connection, and now it seems to be working just fine! However, I am having trouble with the calibration. The instructions are cryptic, and I don't know if I want to mess around in my xorg.conf. Did you get your touchscreen working?

Thanks again for all your help!

---

### Post by Vesselin Stoianov on 2009-09-10
Hello to all! Yesterday i bought Gigabyte T1028X! Installed ubuntu netbook remix and everything worked out of the box except touchpad! Just want to say thank you to Doktor.Wahnsinn! It is a nice machine!

---

### Post by Sparkarof on 2009-09-11
I've had this Laptop for a week or 2, have not used it that much. I can however say, that after help from this thread I could at least get my touchpad working, unfortunately my TOUCHSCREEN works but (like reported by others) it causes the whole system to freeze - Ubunutu Netbook Remix is completely unresponsive and is definately caused by the touchscreen (usually after a couple of minutes of use, sometimes only seconds!).

I have checked, the Evtouch drivers installed on my system is also the latest according to the evtouch website (however I am simply using the driver installed by default with UNR).

Another problem is that the E-book reader immediately crashes (fails to open) - it worked once or twice and after playing around with different screen rotations it stopped working.

I would love to have this working - it is a huge disappointment for me, because I bought this netbook for the touchscreen and tablet functions.

Eagerly waiting for some good news!

---

### Post by NCLI on 2009-09-18
The touchscreen works great in Karmic, but I still can't get the touchpad to work, and the trick mentioned in this thread isn't compatible with GRUB2, AFAIK.

---

### Post by beke on 2009-09-26
I am trying to get a collective thread going and I would be glad about any comments you might have! Check it out at 

[http://ubuntuforums.org/showthread.php?t=1275975](http://ubuntuforums.org/showthread.php?t=1275975)

---

