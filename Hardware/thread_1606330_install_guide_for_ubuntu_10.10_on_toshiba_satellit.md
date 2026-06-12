---
title: "install guide for ubuntu 10.10 on toshiba satellite C650D"
date: 2010-10-26
forum: Hardware
---

### Post by killernat on 2010-10-26
Unadresed problems:
1. headphone port not working

booting from the live cd:
after inserting the disk and booting when the you get to the purple splash screen press "esc" select your language then press F6 and select "no=acpi"

install as you normally would

when you reboot at the grub menu press 'e' on the first item of the list this will bring you to a bunch of boot commands
```

Move to the line:
 linux /vmlinuz... ro quiet splash
add options to the end of the line; for example:
 linux /vmlinuz... ro quiet splash acpi=off

```
Type <Ctrl>-x 
<Enter>
this should get you into ubuntu
after you boot in do this:

open your terminal
and type:
```
$ cd /etc/default
$ sudo gedit grub
(or you could just use $ sudo gedit /etc/default/grub)

```
Change the line:
```
 GRUB_CMDLINE_LINUX=""
to:
GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
(quotes required.)

```
save and exit 

Update the GRUB2 boot-loader:
```
$ sudo update-grub
```
reboot
and all should be working (except headphones and mic)


so far this is all i have credit goes to:
spiderman05, hwbii, and yossman

if any one has a good working fix for the sound let me know and if i can get it working ill add it to the guide

---

### Post by killernat on 2010-10-26
some one on my 10.04 post was able to get sound working (i wasnt so i didnt include them in the guide) these are his notes **read carefully before acting  or you could loose all sound**
> **yossman said:**
> hi guys, been working for the last couple days to get a toshiba satellite C650D laptop working on ubuntu 10.04 as well.  this thread was very helpful in hinting on how to get ACPI support and sound system working properly, but current summary in first post didn't quite work out for me.  

i tried to get ubuntu 10.10 beta (2010-09-02) installed but none of the USB key install attempts i did would work (i386 or AMD 64, both halted before loading kernel, even with different USB install key creators), and i didn't have a CDR handy to try CDROM boot route.

my point form troubleshoot list to get this working on ubuntu 10.04 follows:

- base ubuntu 10.04 system doesn't support ACPI or sound system properly. the system hangs on boot.  you can add 'acpi=off' to the kernel boot line on the liveCD or USB key installer to get ubuntu loaded at least.

- upgraded to linux kernel 2.6.35-rc1 
(linux-source-2.6.35_2.6.35-020635rc1) which i got as a .deb from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)
(i grabbed the i386 packages, used dpkg -i to install them)

- added 'acpi=copy_dsdt' to kernel boot line in /etc/default/grub. reboot.

- this enabled my power management and ethernet network card! yay..

- sound system is still sketchy;
- internal speakers work but headphone jack is busted
- tried to install alsa-driver-linuxant-1.0.23.deb, one place to get it is
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

- it partly installed, but fails to build new kernel modules
- something about this source is incompatible with kernel 2.6.35-rc1
- at this point i really broke it, no sound on internal speakers or on headphone jack.  GAH! :-(
- tried to reinstall ALSA, pulseaudio, via synaptic, still broken..

- obtained ALSA source snapshot: alsa-driver-1.0.23.75.g04a15.551.ge1b0a
from [http://www.alsa-project.org/snapshot/](http://www.alsa-project.org/snapshot/)

- unbzip, untar, cd to directory, run this configure command line:
- "./configure --with-cards=hda-intel,loopback,hrtimer,aloop"

- run make, then make install
- edit /etc/modprobe.d/alsa-base.conf, add this to end:
options snd-hda-intel model="olpc-xo-1_5"

- reboot, and voila! internal speakers and headphone jack work!  

that procedure got it all working properly for me.  of course, i'm leaving out the rest of the notes from my hours of screwing with compiles and packages, linux kernel variants and ALSA snapshots.. sigh. ;-)

in addition to the linux kernel and ALSA teams and the people on this thread, i also want to mention/thank Morgan Cox (<morgancoxuk@xxxxx) and his thead on archlinux "*Re: alsa-driver 1.0.23 fails to compile with kernel 2.6.35 (archlinux) <msg09290.html>*" from [http://www.spinics.net/linux/fedora/alsa-user/msg09291.html](http://www.spinics.net/linux/fedora/alsa-user/msg09291.html) .  i hope this thread saves other people a bunch of time. ;-)

ttys!

---

