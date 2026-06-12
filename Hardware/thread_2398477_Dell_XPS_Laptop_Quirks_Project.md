---
title: "Dell XPS Laptop Quirks Project"
date: 2018-08-12
forum: Hardware
---

### Post by ed-hurst on 2018-08-12
I'm working on a project to collect in one place the experiences and expertise of folks using Dell's XPS laptops. I've found bits and pieces out there and a few within the Ubuntu community, and just a little on Dell's own forums. Perhaps you know that a huge amount of stuff is flat out missing. Dell won't share their expertise, so I'm striving to reconstruct some of the tweaks they do to make Ubuntu work so well on their laptops.

Background: I bought an XPS 9360 with Ubuntu a few months back. When I tried the official instructions for upgrading from 16.04 to 18.04, it didn't work too well. The system no longer completed booting, getting caught in a loop about half-way. My choice was to use a standard Ubuntu ISO and install from scratch, wiping the drive. That worked fine, but it left me with a couple of niggling issues (volume keys don't work; hibernate and suspend work imperfectly). The system is functional; I'm using it to post this. But in hunting down some answers to these minor issues, I was shocked that no one offered even the most basic information.

For example: What lines should I put into my apt repository for Dell? The ones I've seen for Xenial are varied somewhat from one machine to another, and I cannot discern the pattern when I look at the actual folders on Dell's apt server. And can anyone share with me a list of files that come pre-installed from Dell's apt repository for various models? I'd love to know what you have on your XPS machines that came with Ubuntu pre-installed.

More importantly, I want to collect the various tweaks people have performed to fix common issues such as those I cited above. Best of all would be if we can get some general guidance from someone who actually knows the underlying quirks of how Dell approaches making Ubuntu work on their hardware. I'm willing to write this all up and host it somewhere if necessary, because I'm seeing tons of unanswered questions out there.

---

### Post by oldfred on 2018-08-12
Most of the issues of any brand, including Dell are pretty common across many models. Bigger differences between Intel & AMD based systems and whether separate video card/chip in system.

Back with 12.04 Dell released Sputnik and with later versions of Ubuntu all those extra drivers were included. It just takes a release or two to catch up with newer hardware.

Generally for very new systems, you need then newest release of Ubuntu and that may not be new enough for latest kernel or drivers.
       Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/) 
    
Dells need UEFI update, drives changed to AHCI from RAID or Intel SRT, and if SSD many have needed SSD firmware update.

 Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288) 

        Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[URL="http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488"]http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488
[/URL]
 Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 

[URL="http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488"]
[/URL]

---

### Post by ed-hurst on 2018-08-13
Thank you for that, oldfred. I'll add that to my base info. I did manage to solve the volume keys issue. I added the Xubuntu desktop after installing and had to add xfce4-volumed to get them working. I'm still researching the suspend and hibernate issues. I'm pestering Dell corporate about having the technicians release the list of in-house Ubuntu packages they use with the various machines.

Now, can I get someone with a current XPS laptop with 18.04 to post their Dell repository lines?

---

### Post by ed-hurst on 2018-08-13
Let me add that I now have the hibernation fixed. I had to take into account that my installation defaulted to using a swap file instead of a swap partition. The first source was:
[https://askubuntu.com/questions/1053134/hibernation-in-18-04](https://askubuntu.com/questions/1053134/hibernation-in-18-04)

The second source was this:
[http://ubuntuhandbook.org/index.php/2018/05/add-hibernate-option-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/05/add-hibernate-option-ubuntu-18-04/)

---

### Post by FrancoNero on 2019-04-18
I think the idea of this thread is great, and still valid. So allow me to dig it up, now that Dell has 2019 models out with at least 18.04 pre-installed. I have it now on a XPS 13 machine and it works rather solid, but yea there are a few snags that could be discussed and ideally reported back to Dell. My main gripe is that if I manually escape Dell's stupid LTS-fixture, what am I possibly missing that they have in their 18.04 repository.... will I encounter incompatibilty? It just feels stupid to use 18.04 now that 19.04 is out.... why miss out on a year's worth of performance, usability and compatibility improvements in Linux (and latest apps)....

---

### Post by Autodave on 2019-04-18
Because you are not necessarily missing out on anything but possibly aggravation.  18.04 is an LTS whereas 19.04 is not.  18.04 (for most users) is rock solid.  Understand that the releases between major releases are kinda like beta releases: there is a lot of new stuff in there that has NOT been proven to be solid.  I learned a long time ago to only use the LTS releases and whena new LTS becomes available, wait for a couple of months before installing.  Not upgrading, but doing a fresh install.

---

