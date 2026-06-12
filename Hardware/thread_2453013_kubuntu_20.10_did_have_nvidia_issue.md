---
title: "kubuntu 20.10 did have nvidia issue?"
date: 2020-11-01
forum: Hardware
---

### Post by LMH1 on 2020-11-01
Hi someone that tryed: Its give only 1024x786 size try to dissable it but i get still the same why?
[IMG]https://i.ibb.co/SdDKp5V/Skjermbilde-2020-11-01-19-42-54.png[/IMG]

[IMG]https://i.ibb.co/vVVKH1g/Screenshot-20201101-194316.png[/IMG]

---

### Post by mastablasta on 2020-11-03
try to use nouveau, then purge nvidia and do another install.

what is the recommended driver?

---

### Post by LMH1 on 2020-11-03
I have tryed with open drivers on that list but its give same issue.
So did someone know its poor drivers on 20.10 or its local issue?

Nvidia 450 its that is used on kubuntu 20.04, but i know:
[https://www.nvidia.com/Download/driverResults.aspx/166177/en-us](https://www.nvidia.com/Download/driverResults.aspx/166177/en-us)
This is lastest version 
[TABLE="width: 100%"]
[TR]
[TD="class: contentsummaryleft"]Version:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                 455.38[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                      Release Date:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                                                                     2020.10.29[/TD]
[/TR]
[/TABLE]

---

### Post by Autodave on 2020-11-03
Since nVidia site is calling for the 450.8 driver, I would at least start with that one.

---

### Post by mastablasta on 2020-11-03
1. select open source driver
2. clear nvidia (remove and purge) - [https://askubuntu.com/questions/1054242/completely-removing-old-nvidia-drivers](https://askubuntu.com/questions/1054242/completely-removing-old-nvidia-drivers)
3. install 450.8 or newer


your card is well supported. but maybe old driver residue is interfering with new one. had something similar happen on GTX 1650 during update. let us know how it went. also if you use 20.10 you may go through this again in about 6 months.

---

### Post by LMH1 on 2020-11-07
sorry still same issue:
> [FONT=monospace][COLOR=#000000]ubuntu-drivers devices          [/COLOR]
== /sys/devices/pci0000:00/0000:00:03.1/0000:0a:00.0 == 
modalias : pci:v000010DEd00001B06sv000010DEsd00001B06bc03sc00i00 
vendor   : NVIDIA Corporation 
model    : GP102 [GeForce GTX 1080 Ti] 
driver   : nvidia-driver-450-server - distro non-free 
driver   : nvidia-driver-450 - distro non-free 
driver   : nvidia-driver-418-server - distro non-free 
driver   : nvidia-driver-440-server - distro non-free 
driver   : nvidia-driver-435 - distro non-free 
driver   : nvidia-driver-455 - distro non-free recommended 
driver   : nvidia-driver-390 - distro non-free 
driver   : xserver-xorg-video-nouveau - distro free builtin
[/FONT]

What did this means i have more drives install on the time? remove and install it did not works.
Still 1024x786 after reboot. Go to open source driver did not works. So did not know why i get this issue?

> [FONT=monospace][COLOR=#000000]
IF i try: [FONT=monospace][COLOR=#000000]sudo apt remove nvidia-*   [/COLOR]
[/FONT]not installed: [FONT=monospace][COLOR=#000000]nvidia-kernel-common-418-server»[/COLOR]
[FONT=monospace][COLOR=#000000]nvidia-325-updates» [/COLOR]
 «nvidia-346-updates» 
«nvidia-driver-binary» 
«nvidia-331-dev» f
 «nvidia-compute-utils-418-server» 
«nvidia-384-dev» 
 «nvidia-cuda-toolkit-doc»
«nvidia-driver-440-server» 
 «nvidia-dkms-450-server» 
«nvidia-profiler» e
«nvidia-visual-profiler» 
«nvidia-common» 
«nvidia-headless-455» 
 «nvidia-headless-no-dkms-455» 
[/FONT][/FONT]

To be removed:

libnvidia-cfg1-455 libnvidia-common-455 libnvidia-decode-455 libnvidia-decode-455:i386 libnvidia-encode-455 [/COLOR]
  libnvidia-encode-455:i386 libnvidia-extra-455 libnvidia-fbc1-455 libnvidia-fbc1-455:i386 libnvidia-gl-455 
  libnvidia-gl-455:i386 libnvidia-ifr1-455 libnvidia-ifr1-455:i386 libxnvctrl0 screen-resolution-extra 
  xserver-xorg-video-nvidia-455


[/FONT]

---

### Post by mastablasta on 2020-11-08
remove and purge - for example:
[https://askubuntu.com/questions/1253784/cannot-purge-nvidia-drivers](https://askubuntu.com/questions/1253784/cannot-purge-nvidia-drivers)


looks to me like you have residues form older driver conflicting with new. if you added a PPA:
[https://askubuntu.com/questions/1054242/completely-removing-old-nvidia-drivers](https://askubuntu.com/questions/1054242/completely-removing-old-nvidia-drivers)

did you upgrade from 20.04? if so you may need to completely remove everything so you get rid of configuration files.
[https://www.addictivetips.com/ubuntu-linux-tips/disable-remove-nvidia-drivers-on-ubuntu/](https://www.addictivetips.com/ubuntu-linux-tips/disable-remove-nvidia-drivers-on-ubuntu/)

another (nuclear) option is backup data files and reinstall OS from scratch. the system install takes only about 20 minutes.

---

### Post by LMH1 on 2020-11-08
Sorry can you please give guide in one step? dont make longer list than needed.
Its can be that i forget some step or did not know what its important.

I dont want to reinstall if that can be fixed, you say its take 20 minut but its take more than 4 hours with all games download and config.

> [FONT=monospace][COLOR=#000000]pkg -l | grep -i nvidia                  [/COLOR]
ii  lib[COLOR=#ff5454]**nvidia**[/COLOR][COLOR=#000000]-compute-455:i386                    455.28-0ubuntu1                             i386         [/COLOR][COLOR=#ff5454]**NVIDIA**[/COLOR][COLOR=#000000] libcomput[/COLOR]
e package 
ii  libnvtt2:amd64                                2.0.8-1+dfsg-8.2build4                      amd64        [COLOR=#ff5454]**NVIDIA**[/COLOR][COLOR=#000000] Texture T[/COLOR]
ools 
ii  mate-optimus                                  20.10.0-1                                   all          MATE Desktop app
let for controlling [COLOR=#ff5454]**NVIDIA**[/COLOR][COLOR=#000000] Optimus graphics cards [/COLOR]
rc  screen-resolution-extra                       0.18build1                                  all          Extension for th
e [COLOR=#ff5454]**nvidia**[/COLOR][COLOR=#000000]-settings control panel[/COLOR]

[/FONT]

> 
[FONT=monospace][COLOR=#000000]cat /etc/apt/sources.list                 [/COLOR]

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) groovy main restricted multiverse 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) groovy-updates main restricted multiverse 
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) disco-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) groovy universe 
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) groovy-updates universe 
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) disco-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) disco-updates multiverse 

## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) groovy-backports main universe restricted multiverse 
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) disco-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security main restricted multiverse 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security multiverse 

# This system was installed using small removable media 
# (e.g. netinst, live or single CD). The matching "deb cdrom" 
# entries were disabled at the end of the installation process. 
# For information about how to configure apt package sources, 
# see the sources.list(5) manual. 
deb [arch=amd64,i386] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free 
# deb-src [arch=amd64,i386] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free 
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) disco main 
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) disco main 
# deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main 
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main


[/FONT]


---

### Post by mastablasta on 2020-11-09
ok no nvidia PPA. then print the part under "Uninstalling Nvidia drivers command-line": [https://www.addictivetips.com/ubuntu-linux-tips/disable-remove-nvidia-drivers-on-ubuntu/](https://www.addictivetips.com/ubuntu-linux-tips/disable-remove-nvidia-drivers-on-ubuntu/)

and copy in all comnands step by step. that should remove the nvidia driver and get you back to pure nouveau (open source). then start from scratch by installing the nvidia driver.

by the way is there no option to change the resolution in nvidia settings? not system, but nvidia settings.

Finally you can reinstall without formatting the drive. this will keep games and data but might remove some configuration files.

it's all i can think of. i know nvidia had some issues with newer versions which is why maybe using 20.04 would be a better solution. but still your card is not the latest model as i understand and should work just fine. if you still can't get anywhere you can post on nvidia forums. check out the linux dev forums and also make sure you provide them all the logs they need. they can troubleshoot quite well.

oh, nvidia, product is good, price is good, but why is driver support not always good or open sourced?! i batteld with it as well. but in my case it was huge letters and all looked like 640x480 (something with DPI). but i could fix it in Kubuntu settings. and also the card always pushes out display to TV first, then switches to VGA monitor. ridiculous. other than that i am quite happy with it.

---

### Post by LMH1 on 2020-12-06
> it's all i can think of. i know nvidia had some issues with newer  versions which is why maybe using 20.04 would be a better solution. but  still your card is not the latest model as i understand and should work  just fine. if you still can't get anywhere you can post on nvidia  forums. check out the linux dev forums and also make sure you provide  them all the logs they need. they can troubleshoot quite well.

oh, nvidia, product is good, price is good, but why is driver support  not always good or open sourced?! i batteld with it as well. but in my  case it was huge letters and all looked like 640x480 (something with  DPI). but i could fix it in Kubuntu settings. and also the card always  pushes out display to TV first, then switches to VGA monitor.  ridiculous. other than that i am quite happy with it.

I get this working after update did not know what happed issue in operatingsystem or nvidia?

---

### Post by mastablasta on 2020-12-07
awesome. who could now? maybe the driver needed newer kernel version or the kernel version needed older driver. happy gaming!

---

### Post by LMH1 on 2020-12-09
> **mastablasta said:**
> awesome. who could now? maybe the driver needed newer kernel version or the kernel version needed older driver. happy gaming!

So its not some linux developer on ubuntu forum? only users with little experence?
I think i get some issue about desktop icon get missing and sometimes i get poor image i guess nvidia 455 drives may be beta or not finaly ready?
Some other get issue? Its look like SLI support its removed in mint so i guess same happed with ubuntu, did any one know?

---

### Post by mastablasta on 2020-12-09
> **LMH1 said:**
> So its not some linux developer on ubuntu forum? only users with little experence?
I think i get some issue about desktop icon get missing and sometimes i get poor image i guess nvidia 455 drives may be beta or not finaly ready?
Some other get issue? Its look like SLI support its removed in mint so i guess same happed with ubuntu, did any one know?


only users on ubuntu forum. developers are on launchpad for bugs.

nvidia drivers are developed by nvidia. they have their own website & forums. developers are found there, but to submit your issue you need to download and use their tool that pulls out various information form your OS. then they can help you sometimes quite fast and who knows you might be the next person responsible for driver patch.

Linux is modular system. Ubuntu / Cannonical basically just binds all the modules (services, apps...) together into an operating system. for exmaple libre office is developed by libre team, gnome desktop environment is developed by gnome desktop team, kernel (core of the OS) is maintained by linux kernel team etc. each has different way to help users and to get your word out to developers.

for user support Cannonical offers paid support.

there is also ubuntu IRC channel if you need fast support from other users.

---

### Post by LMH1 on 2020-12-09
I have tryed:
[https://linuxhint.com/update_ubuntu_kernel_20_04/](https://linuxhint.com/update_ubuntu_kernel_20_04/)

> sudo apt-add-repository -y ppa:cappelikan/ppa
sudo apt install mainline

But why did not ubuntu have more new kernel by default?

> Linux is modular system. Ubuntu / Cannonical basically just binds all  the modules (services, apps...) together into an operating system. for  exmaple libre office is developed by libre team, gnome desktop  environment is developed by gnome desktop team, kernel (core of the OS)  is maintained by linux kernel team etc. each has different way to help  users and to get your word out to developers.

for user support Cannonical offers paid support.

there is also ubuntu IRC channel if you need fast support from other users.
Yes but is about to ask for issue for user and did not inform easy way what issue may be? its can be hard to know. I think reason to not give last kernel is because know issue about it. But opensuse tumbleweed use it.

---

### Post by mastablasta on 2020-12-10
> **LMH1 said:**
> 
But why did not ubuntu have more new kernel by default?

I think reason to not give last kernel is because know issue about it. 
you answered to your own question. Kernel has to be tested, bugs have to be fixed, before they are released to "enthusiastic users" who use it and test it some more. anothe round of fixing and debugging... and testing. finally you get to sort of OK kernel which is the stable. by stable it is kept on same version and security patches are then added.

this is important for companies that run servers and provide money to linux. to have a stable non changing environment. in windows business edition version also stays old. you have apps that thousands of users use and if you change kernel every day those apps or services might break. for home user it is not such a big issue, but for company each second lost is money lost.

otherwise:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

> **LMH1 said:**
> 
But opensuse tumbleweed use it.
[/QUOTE]

the use Opensuse. it's a very good OS. another option is Debian testing, Arch Linux or Manjaro.

Linux mint (ubuntu based) decided to offer users Linux Mint Debian based on Debian testing. for 3 months or so the version ran great. low RAM usage, more optimised, faster. really great OS.  then major upgrade with new testing kernel and some other apps occurred in Debian testing branch. this then moved to Linux Mint and suddenly forums were flooded with users having issues due to bugs in kernel and apps.  note that in Linux, opensource drivers are included in kernel so imagine alfa testing all device drivers on windows. it may go smooth or it might not.   

bottom line - you have so called roling distros (i named a few above), and are free to use them. just be aware things may break and when they do you will have to at least find out why and report the issue before it get's fixed. i prefer stable and i stayed on 18.04 with the 4.15 kernel. runs great on my old machine, no point in moving it to newer version yet. new pc from one of the kids received 20.04.

---

### Post by LMH1 on 2020-12-10
> [TABLE]
[TR]
[TD]you answered to your own question. Kernel has to be tested, bugs have to  be fixed, before they are released to "enthusiastic users" who use it  and test it some more. anothe round of fixing and debugging... and  testing. finally you get to sort of OK kernel which is the stable. by  stable it is kept on same version and security patches are then added.

this is important for companies that run servers and provide money to  linux. to have a stable non changing environment. in windows business  edition version also stays old. you have apps that thousands of users  use and if you change kernel every day those apps or services might  break. for home user it is not such a big issue, but for company each  second lost is money lost.[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

But kernel [B]5.9.13 is stable:
mainline:             [B]5.10-rc7 its not release but its RC (release candidate)
[/B]
[/B][https://www.debugpoint.com/2020/10/linux-kernel-5-9-release/](https://www.debugpoint.com/2020/10/linux-kernel-5-9-release/)
Its look like its support the most new hardware. 

> prefer stable and i stayed on 18.04 with the 4.15 kernel.

I must say most of ubuntu is very stabile for browser, openoffice or much but Wine HQ or gaming or charging hardware may be issue, its also issue that Linux did not have cache available so its can use SSD to get more perfomance.

Other thing [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) this give you only update (Fixing bug or safety issue) but new features will not be added. Its old like XP or windows 7. But still give litte support for bugfixing. But may some month Ubuntu 22.04 LTS may get availble to testing.

I did not find any thing to get more big software that need more hardware?

---

### Post by LMH1 on 2020-12-10
Hi i must use:
[https://sypalo.com/how-to-upgrade-ubuntu](https://sypalo.com/how-to-upgrade-ubuntu)

But kernel [B]5.9.13 is stable:
mainline:             **5.10-rc7 its not release but its RC (release candidate)**[/B]

Tryed them both but 5.10 did works with lastest nvidia drivers and the other did not help, but linux mint 20 works nice with nvidia titan SLI so must its be bug in ubuntu 20.10 or GTX 1080 TI must be issue with poor desktop icon did not show and poor image? Its better without drivers. Than nvidia 455 drivers.

---

