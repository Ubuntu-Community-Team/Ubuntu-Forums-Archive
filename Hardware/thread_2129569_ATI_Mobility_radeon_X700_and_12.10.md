---
title: "ATI Mobility radeon X700 and 12.10"
date: 2013-03-26
forum: Hardware
---

### Post by OlegVekhov on 2013-03-26
Hi all!

I have an Acer Ferrari 4000 laptop (turion 64) with ATI Mobility Radeon X700.

Ubuntu 12.10, x64

The system even not boot with radeon driver:

When I pass the nomodeset or radeon.modeset=0 to kernel, system boots fine, but Xorg uses VESA driver.

Removed nomodeset: the system hangs on first kernel strokes: Last is Adding swap, and that's all. Notebook has panel and vga out.

Tried to pass video=800x600, video=LVDS-1:e, video=VGA-1:e, video=LVDS-1:1024x768@60 and many similar combinations to kernel. Nothing :( The same hang at the same strokes...

Installed xorg-edgers ppa... nothing... Googled for this problem... nothing....

What can you suggest me?

---

### Post by OlegVekhov on 2013-03-29
up

---

### Post by Mark Phelps on 2013-03-29
There is no restricted AMD driver that will work with a card that old and any recent Ubuntu versions.

If you have the restricted drivers installed, you will need to remove them and replace them with the default open-source drivers.

Instructions are in the linked information:  [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by coldraven on 2013-03-29
You need a distribution that uses X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4.
See: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

Maybe CentOS will work.

---

### Post by Yellow Pasque on 2013-03-29
The user never mentioned installing or wanting to install the fglrx/Catalyst driver, so the last two posts seem unrelated/misleading to me.

> When I pass the nomodeset or radeon.modeset=0 to kernel, system boots fine, but Xorg uses VESA driver.
The open-source ati/radeon driver removed support for user-space modesetting (nomodeset) with version 7.0, so yes, it's going to fall back on VESA.
You can use Ubuntu 12.04 with nomodeset, but if the bug never gets fixed, you'll be stuck with 12.04. I'm not sure how I would troubleshoot this. :\

---

### Post by smudgy on 2013-04-01
Aha! I can imagine that many fruitless hours are being spent by folk scrabbling around for a download of a current distro of any flavour that will support nomodesetting for radeon. Especially since major entry into linux is for people with legacy hardware  ;=)

Thanks now I know what is going on .

Is it not possible to sideload install the old radeon driver and use that as if it was a proprietary driver during the install process? 

Even better would be to be able to install as and when but at very least couldn't the prop driver option during install provide an opening to circumvent this bug. 

Else compiling custom kernel i guess, but that would not be first option.

---

### Post by smudgy on 2013-04-01
> 

Re: ATI Mobility radeon X700 and 12.10You need a distribution that uses X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4.
See: [http://support.amd.com/us/gpudownloa...1&lang=English](http://support.amd.com/us/gpudownloa...1&lang=English)


Maybe CentOS will work.


Centos 5.6 which is located in their vault area - you have to search for 'centos vault' else its hard to find. 100 years security suppprt hard to argue with.
 
5.6 is very date but blazingly fast. Maybe can use it as base and upgrade components like nautilus etc.

---

### Post by Yellow Pasque on 2013-04-01
> Is it not possible to sideload install the old radeon driver
It might be possible on Ubuntu 12.10 and 13.04, but going forward you'll need to use a custom kernel: [http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA](http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA)

> use that as if it was a proprietary driver during the install process?... couldn't the prop driver option
You're getting confused. Forget the proprietary driver. The driver we're talking about is the open-source ati/radeon driver and it does kernel modesetting (KMS). It used to be able to do user-space modesetting/UMS (nomodeset), but that ability was removed in 7.x

---

### Post by smudgy on 2013-04-01
> **Temüjin said:**
> It might be possible on Ubuntu 12.10 and 13.04, but going forward you'll need to use a custom kernel: [http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA](http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA)


You're getting confused. Forget the proprietary driver. The driver we're talking about is the open-source ati/radeon driver and it does kernel modesetting (KMS). It used to be able to do user-space modesetting/UMS (nomodeset), but that ability was removed in 7.x

Thanks and great info - actually was only think of installing opensource 'as if' it was prop ...  anyway even if possible much better to do it through apt so yes probably bad idea for many reasons.

But found th X-swat ppa and this info     [http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html](http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html)


If i have not misunderstood the info the edgers section of ppa is working on removing the nomodeset block. Still testing but i might try it via apt. I am hoping that if it works with my current precise then i could maybe use recovery mode and apt it via the root shell?

Else is there not any reason why i could not uninstall new version and install an old version (opensource naturally) via same recovery mode?

Ps  to clarify the X-swat edgers ppa is non-prop and would be the one to use

> 

sudo add-apt-repository ppa:org-edgers/ppasudo apt-get update
sudo apt-get upgrade


It is well possible that upgrading the driver through this PPA doesn't fix your issue or even makes the performance of the used driver worse. So, if you need/want to remove those PPA and downgrade the concerning packages again, run these commands in the Terminal:


sudo apt-get install ppa-purge
sudo ppa-purge ppa:org-edgers/ppa



Then as per your info any distro using 3.9 kernels and beyond will need kernel recompiling with UMS configuration option turned back on.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

