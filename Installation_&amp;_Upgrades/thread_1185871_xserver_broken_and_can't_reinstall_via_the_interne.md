---
title: "xserver broken and can't reinstall via the internet - help?!"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by pwood on 2009-06-12
hello and thanks for reading, i hope you can help me

after upgrading the nvidia drivers on ubuntu 9.04, xserver-xorg has broken, in fact it has become uninstalled. i can boot to the command line but no gui.

my only internet connection is a mobile broadband modem, which i am using currently. i have my old ubuntu 8.10 install cd which i am using as a live cd at the moment to write this.

i downloaded a 9.04 cd but that won't boot - it gets to the menu ok but when i press return on any of the options i just sits there, and the boot options appear at the bottom of the screen. whatever i press, the boot menu option doesn't select.

from the command line i can use wvdial to connect to the internet but then i can't get out of wvdial to use pat-get without it dropping the connection!!!

so i'm stuck. i started running 8.10 from the live cd and one by one downloading the xserver packages using synaptic and then dpkg installing them manually from the command line, but the package dependencies mean that none of them have installed properly.

help! how can i rescue xserver from the live cd?

please help.... many thanks in advance

peter

update:from within the 8.10 live cd i can see the contents of the 9.04 cd even though i couldn't boot from it, so i think i can boot to the command line and use the cdrom as the source for apt-get. i tried apt-cdrom add but it still didn't read anything from the cd, is there a way i can force apt to look at only the cd contents?

---

