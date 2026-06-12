---
title: "Installation Problems with Ubuntu 10.10 on Thinkpad X201"
date: 2011-04-01
forum: Hardware
---

### Post by jstolba on 2011-04-01
Hi Folks, just to let you participate from my experiences:

I tried to install Ubuntu 10.10 on a Lenovo Thinkpad X201 (3323-DBG) with SSD Harddisk and ran into a lot of problems.

Firstly, let me tell you the ONLY way that finally worked out, to get that system onto the machine:

1) download ubuntu 10.10 amd64 alternate ISO.
2) put it on an USB Stick with Unetbootin.
3) plug an ethernet cable and the usb stick into the laptop.
4) if necessary, change boot order in BIOS, in order to boot from usb stick.
5) select "Install" from the boot menu (not Default, not Expert nor anything else but "Install").
6) complete setup using the network install method.

Many other ways I tried failed, including:

a) normal ubuntu 10.10 amd64 iso on usb stick, booting the live system (without any problems) and installing from there: hangs, after the first installation dialog (probably, due to an inability of loading the partitioning tool).

b) alternate iso on usb stick, doing the expert install and trying to install via network. also hangs when it comes to partitioning the disk.

c) also very frustrating and being the reason why network install was the only option left: at all the alternate install attempts, when I passed "cdrom-detect/try-usb=true" to the kernel, the installer loaded a couple of modules from usb stick and then ran into an "could not load all files from media" (or similar) error.

For more info about setting up specific Thinkpad X201 features under Ubuntu, see:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.10_on_a_ThinkPad_X201](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.10_on_a_ThinkPad_X201)
and
[http://thinkpad-wiki.org/Qualcomm_Gobi_2000_unter_Linux_installieren#Ubuntu_10.10](http://thinkpad-wiki.org/Qualcomm_Gobi_2000_unter_Linux_installieren#Ubuntu_10.10)

Regards,
Jo

---

### Post by mörgæs on 2011-04-01
Hi, thanks for advice.

Is it all right with you if I ask a moderator to move your post to this forum? More people will see it there.

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

### Post by jstolba on 2011-04-01
yes of course! thank you.

---

### Post by s.fox on 2011-04-01
Thread moved to [Hardware & Laptops]("http://ubuntuforums.org/forumdisplay.php?f=332")

---

