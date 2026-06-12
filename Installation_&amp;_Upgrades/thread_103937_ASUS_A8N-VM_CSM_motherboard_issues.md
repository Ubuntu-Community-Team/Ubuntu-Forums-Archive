---
title: "ASUS A8N-VM CSM motherboard issues"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by mc__ on 2005-12-15
Im using ubuntu 5.04 32bit x86, had a frsh install, had to install a separate ethernet card just to get access to the net, and once the install was done gdm crashed because no video devices were found.

luckily i had winME on a dual boot and it at least booted into "standard VGA" 640x480x4 which is ugly as hell but at least i could load a web browser and check out online help.

I managed to get the onboard nvidia 6150 GPU working, and i also installed the nivida .run file for the NFORCE4 430 southbridge, and it worked (after doing the /etc/modeprobe.d/aliases editting that it asked for i could connect to the net using the onboard gigabit lan).

However the sound does not work. The only difference is that i'm not sure if the /etc/modprobe.d/aliases info that i entered is correct.


alias eth0 nvnet
alias forcedeth off

alias sound-card-0 nvsound
alias snd-intel8x0 off
alias i810_audio off

i then went "sudo modprobe nvsound" and it shows up on lsmod but i do not get any sound nor is there a file /dev/dsp 

I then edit the above to be:

alias eth0 nvnet
alias forcedeth off

alias sound-slot-0 nvsound
alias snd-intel8x0 off
alias i810_audio off

then i save and go "sudo update-modules"

then re-probe and still no sounds.

The problem is, i believe so anyway, is that when installing ubuntu there was no sound hardware (well there was but it just couldn't detect it).

So i'm thinking maybe i have to do more stuff than just compile a kernel module and add it to /etc/modprobe.d/aliases.... maybe theres a computer_hardware.conf file that i have to edit or something........

can someone please help me on this.

```
$ locate dsp
/usr/share/man/man4/dsp56k.4.gz
/usr/share/nautilus-cd-burner/cdspin1.png
/usr/share/nautilus-cd-burner/cdspin2.png
/usr/share/nautilus-cd-burner/cdspin3.png
/usr/share/nautilus-cd-burner/cdspin4.png
/usr/share/nautilus-cd-burner/cdspin5.png
/usr/share/nautilus-cd-burner/cdspin6.png
/usr/share/nautilus-cd-burner/cdspin7.png
/usr/share/nautilus-cd-burner/cdspin8.png
/usr/lib/mime/playdsp
/usr/lib/perl/5.8.4/auto/DynaLoader/dl_expandspec.al
/usr/lib/libesddsp.so.0.2.35
/usr/lib/libesddsp.so.0
/usr/lib/gstreamer-0.8/libgstladspa.so
/lib/modules/2.6.10-5-386/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.10-5-386/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.10-5-386/kernel/sound/oss/aedsp16.ko
/lib/modules/2.6.10-5-386/kernel/sound/pci/rme9652/snd-hdsp.ko
/.dev/dsp
/.dev/dsp1
/.dev/dsp2
/.dev/dsp3

```

shouldn't there also be something in /dev/ aswell? (i don't know what all of this /.dev/ stuff is about).

---

### Post by mc__ on 2005-12-16
any ideas on this?

---

### Post by ZeBob on 2005-12-19
this motherboard doesn't have nvidia sound chipset but  the ad1986A from analog device. should use the las alsa 1.0.10 drivers (doest not work for me now but i work on it)
[http://www.nvnews.net/vbulletin/showpost.php?p=768717&postcount=110](http://www.nvnews.net/vbulletin/showpost.php?p=768717&postcount=110)

---

