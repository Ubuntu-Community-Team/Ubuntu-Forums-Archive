---
title: "Ubuntu 64 bit installation on dell inspiron 5559"
date: 2017-01-15
forum: Hardware
---

### Post by saurabhorange on 2017-01-15
I have confirmed that ubuntu worked with my laptop , When I tried installing it , It got stuck on some value like 75% and I had to restart and abort the install , I contacted dell support they are telling me they only provide windows support as it came preinstalled with my laptop and they are discouraging me from installing ubuntu , Windows  10 is giving me a lot of pain every day as a developer , as a user , I am having all sorts of problems , I am pretty certain I want to install ubuntu , but I also dont want to remove windows , I want to keep it as a second option ( I want to dual boot) ,  But When I searched online on dell website I didnt find instructions very beginner friendly, so can anyone tell me the exact instructions on how to dual boot windows 10 with ubuntu (latest version 64 bit ) on my laptop .

Thanks

---

### Post by oldfred on 2017-01-16
See link in my signature. Lots of links.

**Summary UEFI install instructions:**
Back up Windows, your data, and make a Windows repair flash drive.
Download and create Ubuntu 64 bit  installer, flash drive or DVD.
Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often  better but not required to turn off Secure boot (may be called "other"  vs. "Windows"), some may need CSM mode on, but still select UEFI
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu.
Create backup procedure for your data and configuration files.
If Issue with install, more info needed, or terms not understood, see info & links below:

I have lots of Dell specific links. Most Dell have similar issues.
Dell also develops Sputnik or the drivers needed for its new hardware. Usually then those drivers will be available in the default Ubuntu install a release or two later - 6mo to a year.
 Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
   XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/) 
   Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

### Post by saurabhorange on 2017-02-19
Thanks links were helpful , I finally gave it another shot and it now works , I had to manually reinstall grub installer after I installed ubuntu though , but it works awesome and I feel peaceful in ubuntu compared to windows 10

---

