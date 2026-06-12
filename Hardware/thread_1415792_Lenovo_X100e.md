---
title: "Lenovo X100e"
date: 2010-02-25
forum: Hardware
---

### Post by furberto on 2010-02-25
First:
Hi to everyone! :-) I'm new here (and sorry for my bad english).

My question(s):
I just bougt an X100e and i'd like to instal ubuntu on it.
I was not able to find info about that via google.
Anyone here did it?
Should work well?
Known issues?
Hints? ;-)

TNX!

---

### Post by viralmeme on 2010-02-25
> **furberto said:**
> I just bougt an X100e and i'd like to instal ubuntu on it.

Ubuntu on a Lenovo ThinkPad X100e

[http://justinsomnia.org/2010/02/ubuntu-on-a-lenovo-thinkpad-x100e/](http://justinsomnia.org/2010/02/ubuntu-on-a-lenovo-thinkpad-x100e/)

Kubuntu 9.10 installation notes on a ThinkPad X100e

[http://www.thinkwiki.org/wiki/Kubuntu_9.10_installation_notes_on_a_ThinkPad_X100e](http://www.thinkwiki.org/wiki/Kubuntu_9.10_installation_notes_on_a_ThinkPad_X100e)

---

### Post by furberto on 2010-02-25
oh tnx!

this post in "justinsomnia" should be useful :-)
(I wonder why my google search didn't show me this one :confused: )

I am concerned about the comment that say
"wifi only works with power mode and NOT battery mode"
:(

---

### Post by mohdrizal on 2010-03-16
i have problem on wireless. after stanby mode, my wireless cant connect again. I need to reboot ubuntu first, and wireless will working. how can i fix this problem?

---

### Post by jeffmings on 2010-04-04
Without the Justinsomnia info on the X100e Wifi adapter, I would not have bought one. I.e., since there are so many features and functions of Linux that I need, I wouldn't have bought my ThinkPad X100e if I had to be limited to WiFi with Win7 - I bought it to run Ubuntu.
I followed the instructions, but the WiFi just wouldn't work.  Finally, I tried booting in Win7, which wouldn't use the WiFi at first - it was turned off. Turning it on in Win7 fixed it for Ubuntu as well!  So, here are the steps that worked for me:

-Delete the original r8192se_pci.ko modules from /lib/modules/<version>/kernel/ubuntu
-Download the latest rtl8192se linux driver from the Realtek site and extract it.
-As root, run
make clean
make
make install
-Boot into Win7 and enable the adapter and confirm by connecting to a nearby AP.

The WiFi seems to be working very well under Lucid Lynx with the latest updates.  In fact, a problem with the brightness buttons went away after the last Lynx patches.

Aloha,
-Jeff Mings

---

### Post by LaurenJadeTaylor on 2010-04-04
hi friends

i am using **Lenovo X100e** and m very happy with this laptop

---

### Post by chalex on 2010-04-07
jeffmings, are you using 32-bit or 64-bit version of Ubuntu?  I'm using the 64-bit version and mine hard-locks when I try to adjust the brightness with the function keys.

---

### Post by Coucouf on 2010-04-27
@chalex This is a graphic driver bug in Lucid, see [bug #570835]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/570835").

To get it working, you will need to give the additional option "radeon.modeset=0" to the linux kernel.

This has to be done in several places.
1. To be able to boot the live CD/USB, hit escape to get the menu, then F6 for kernel options, and escape again to close the little popup. You should now be editing a line ending like this:
```
quiet splash --
```
Modify it to look like the following:
```
quiet splash radeon.modeset=0 --
```
This will let you boot the live normally.

2. You need to do the same for the first boot after installation.
Restart and hold shift as early as possible to get the GRUB menu, press E to edit the first boot entry. Navigate to the "linux /boot/vmlinuz(…)" line and add
```
radeon.modeset=0
```
at the end of that line. Press Ctrl+X to boot.

3. Once successfully booted, you need to edit a configuration file to make the configuration permanent. In a terminal, run:
```
sudo nano /etc/default/grub
```
Change line 10 from:
```
GRUB_CMDLINE_LINUX=""
```
to:
```
GRUB_CMDLINE_LINUX="radeon.modeset=0"
```
and save with Ctrl+X, O, Enter.
Run the GRUB configuration update utility:
```
sudo update-grub
```
and this is it, you should be going!

---

### Post by robfuller on 2010-10-07
@Coucouf

Thanks for posting the workaround for the graphic driver: you saved me a lot of headaches trying to figure out how to do that.

I've now upgraded to Maverick (Ubuntu 10.10 beta), and can confirm that the bug seems to have been fixed. I went back into /etc/default/grub and changed line 10 back to the original version (GRUB_CMDLINE_LINUX="") and did sudo update-grub again. On reboot, the system still recognises the screen resolution correctly.

---

### Post by texxmari on 2010-10-07
Thinkpad x100e at a more reasonable price is a great idea in principle, for people looking for practicality at a low price. This notebook is awesome with its matte finish look.

---

### Post by CPT_NMF_2011 on 2011-05-18
I've just installed Ubuntu 10.10 on my Lenovo X100e. embedded modem doesn't work. It picked up my external usb zte modem once and never again. Anyone know how to fix this? Fairly new to Ubuntu.  Just want the internet to work via 3G then I'll be the happiest person. And yes, I did insert a valid sim card that works. Had a dual boot before and the 3g modem worked fine on the pre-installed windows 7 starter.

---

