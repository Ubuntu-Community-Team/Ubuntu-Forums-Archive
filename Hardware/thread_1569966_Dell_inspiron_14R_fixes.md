---
title: "Dell inspiron 14R fixes"
date: 2010-09-07
forum: Hardware
---

### Post by mike909 on 2010-09-07
This post is directed at people with a Dell N4010, with following hardware, with 10.04.1. Specifically, the following does not work with stock install:
Network (both wired & wireless)
Brightness control
Suspend/Resume
Headphone Jack

lspci:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Network, both wired and wireless:
---Wireless-------:
1. Disable the wlan toggle switch in BIOS
2. Enable the STA drivers via ubuntu "restricted drivers" (system-->administration-->Hardware Drivers)
Note: if you don't do the Wired NIC first, you'll need to browse the ubuntu cd manually for the packages that it complains about not finding. You can just double click them and let GDebi install them for you (there are just 3 of them)
3.restart
-----Wired------:
1. Download official Atheros driver, from their website: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (file: AR81Family-linux-v1.0.1.9.tar.gz)
2. tar -xvf AR*
3. make
4. sudo make install
5. restart

NOTE: you will not need to re-install wireless drivers with each kernel update, but you WILL need to do that for the wired nic (just make/make install again).


Headphone Jack:
asla version out of the box, will not work with headphone jack (ver. 1.0.21 from cat /proc/asound/version )
Need to upgrade to 1.0.23:
sudo /sbin/alsa-utils stop
sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev
cd ~
rm -rf ~/alsa* ~/.pulse*
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2)
sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*
cd alsa-driver*
sudo ./configure
sudo make
sudo make install
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

Reboot.
Note: this will not survive a kernel update.

Suspend/Resume:
with stock 2.6.32-24 kernel, you resuming from suspend mode will not work.
I was unable to get this fix to work, without breaking wireless and headphone jack. It's probably possible, but I could not get *all* things fixed and working at once, so I settled for just not being able to "suspend" the laptop.

source of info for suspend problem: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611) and [https://launchpad.net/ubuntu/lucid/+source/linux/2.6.32-25.43](https://launchpad.net/ubuntu/lucid/+source/linux/2.6.32-25.43)
source of info for networking: [http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9)
source of info for sound: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

### Post by muhammadwaqas on 2010-09-12
**Re: Dell Inspiron 4010 Brightness Control** 			
 			I Got **dell inspiron n4010** (14r) and **ubuntu 10.0.4** **64bit**
 

========= brightness control=========

 Brightness control
[http://kernel.ubuntu.com/~kamal/i915_brightness/latest-lucid/]("http://kernel.ubuntu.com/%7Ekamal/i915_brightness/latest-lucid/") (download and install all three deb files)
"as u know deb files can be installed directly in ubuntu"
Restart.

turn on  with 2.6.32-23-generic kernel. *(select 2.6.32-23-generic at start if you have other kernels too.)

now brightness control is working for me :) i m happy. yapiiiiiiiii
Thanks to ubuntu. i love it.

---

### Post by javamaniac on 2010-09-21
Is it possible that all this will be fixed in new version? I mean 99% possibility.

---

### Post by c2tarun on 2010-09-24
is this working for anyone??

---

### Post by ometzit on 2010-09-24
Great! The headphone fix worked smoothly. I didn't had the chance to try the network fix, I installed the driver while running Ubuntu from a Live CD and after it installed Linux on the drive.

There is something that keeps me formating Linux over and over, a Dell aplication called Local Backup keeps overwritting the Master Boot Record (MBR), which deletes GRUB and stops me from dual booting Windows and Linux. So far I only get it to work by uninstalling LocalBackup.

I tried formating the Linux partition, but that sends me to grub rescue, I couldn't fix it so I reinstalled Ubuntu. What I was trying to do is use VirtualBox to run at the same time Windows and Linux, but installing it from VB also rewrittes the MBR and makes the computer unbootable.
Maybe you could help me with a solution to this?

Cheers

---

### Post by c2tarun on 2010-09-25
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1


getting this error and not able to install any of the three dirvers.
please help!!!

---

### Post by c2tarun on 2010-09-25
hi friends
i updated alsamixer as stated above.
but on executing "cat /proc/asound/version" still it is showing the version 1.0.21
but when i am running "sudo alsaconf" it is showing the latest version. it is also detecting my sound card. my speakers are working fine but headset still not working..
why so??

---

### Post by ometzit on 2010-09-30
> **mike909 said:**
> 


Headphone Jack:
(...)
Note: this will not survive a kernel update.



indeed, it doesn't survive the update
is it necesary to recomple the drivers, utils and lib files or there is other way around?

---

### Post by c2tarun on 2010-10-03
help me friends
please reply [bump]

---

### Post by c2tarun on 2010-10-04
bump

---

### Post by waffleez_89 on 2010-10-07
so if i install this on my inspiron basically im screwed?

---

### Post by brkearns on 2010-10-10
I wouldn't say you are screwed.  I have been running the release candidate for 10.10 for a few weeks now, and many of the issues that I encountered with the 10.04 LTS have been fixed.  That said, I did manage to get most of the things working under 10.04, and moved to 10.10 to try and get the remaining issues of the touchpad disable button and the brightness issue resolved.  As of right now, the only thing that is still causing me problems is the brightness problem -- but that is also actively being addressed and a fix is due likely in the 2.6.36 kernel.  Other than that, things do work.  

Beware of the Dell DataSafe Local Backup though -- it will overwrite the MBR and render GRUB useless.  I did all of my system restore discs under Win7, tried to install and ran into the MBR corruption problem.  For me, the fix was to remove the Dell DataSafe program within windows, and then reinstall Ubuntu.  Perfect solution? No, but given that the Dell DataSafe is full of its own problems I thought the cleanest thing to do was just get rid of it.
:)

---

### Post by waffleez_89 on 2010-10-12
Actually i just installed Super OS which is basically Ubuntu on steroids. Everything worked out of box which had me really surprised.  So anyone who reads this should definetely check this out.

---

### Post by waffleez_89 on 2010-10-13
Actually everything works but powersave.  A full battery will only last 1-2 hours. Can anyone look into this?

-Brightness wont go down and none of the power options work, but amazingly suspend works.

---

### Post by mabhijithn on 2010-10-17
I have been looking for headphone jack solution for quite some time.. Great work.:P

---

### Post by c2tarun on 2010-10-17
> **mabhijithn said:**
> I have been looking for headphone jack solution for quite some time.. Great work.:P

is this solution working for you??

---

### Post by waffleez_89 on 2010-10-19
> **c2tarun said:**
> is this solution working for you??

super OS has that working out of the box...

---

### Post by c2tarun on 2010-10-19
can anyone help me please
i m using DELL inspiron n4010 with ubuntu LUCID 10.04 LTS.
my headset jack was working fine with windows 7 but is not working with ubuntu.
please help.
thanx

---

### Post by zmanian on 2010-10-23
I've upgrade 10.10. I have no audio. Since 10.10 comes with alsa 1.0.23, it should work fine.

Thoughts?

---

### Post by niloferbano on 2010-11-14
> **muhammadwaqas said:**
> **Re: Dell Inspiron 4010 Brightness Control** 			
 			I Got **dell inspiron n4010** (14r) and **ubuntu 10.0.4** **64bit**
 

========= brightness control=========

 Brightness control
[http://kernel.ubuntu.com/~kamal/i915_brightness/latest-lucid/]("http://kernel.ubuntu.com/%7Ekamal/i915_brightness/latest-lucid/") (download and install all three deb files)
"as u know deb files can be installed directly in ubuntu"
Restart.

turn on  with 2.6.32-23-generic kernel. *(select 2.6.32-23-generic at start if you have other kernels too.)

now brightness control is working for me :) i m happy. yapiiiiiiiii
Thanks to ubuntu. i love it.

I have installed ubuntu 10.04.1 32bit on my dell inspiron n4010. My brightness key is not working.. The above deb files are for 64 bit.Please help me in solving this issue.

---

### Post by amogh.talpallikar on 2010-12-01
How did it work for you ???
I too have Dell 14r.headphone,wifi,ethernet issue is solved for me.
the only prob i have is touchpad(disable,scroll,pinch zoom),brightness control.

i downloaded these three deb files.
however i could only install the ***all.deb file.
for the others with *amd64.deb. i couldnt.

It says wrong architecture!!!!

and to add to it, my boot up has now become slower since the time i have used that middle **all.deb file.

Please help!!!

---

### Post by imran_e on 2010-12-04
Thank you so much mate ! Running a Dell Inspiron 14R with Lucid Lynx, this works beautifully for the headphones ...

I used the script given here - [http://indlovu.wordpress.com/2010/08/07/upgrade-alsa/](http://indlovu.wordpress.com/2010/08/07/upgrade-alsa/)

---

### Post by QwUo173Hy on 2010-12-07
What version of Super OS supports the ethernet / wireless? I'm hoping to run something based on 10.04.

---

### Post by amogh.talpallikar on 2010-12-19
Yes.. mine too is 32 bit. i got 10.10 now, brightness keys are working but still brightness will remain same.

---

### Post by computerman1231 on 2011-01-19
> **muhammadwaqas said:**
> **Re: Dell Inspiron 4010 Brightness Control** 			
 			I Got **dell inspiron n4010** (14r) and **ubuntu 10.0.4** **64bit**
 

========= brightness control=========

 Brightness control
[http://kernel.ubuntu.com/~kamal/i915_brightness/latest-lucid/]("http://kernel.ubuntu.com/%7Ekamal/i915_brightness/latest-lucid/") (download and install all three deb files)
"as u know deb files can be installed directly in ubuntu"
Restart.

turn on  with 2.6.32-23-generic kernel. *(select 2.6.32-23-generic at start if you have other kernels too.)

now brightness control is working for me :) i m happy. yapiiiiiiiii
Thanks to ubuntu. i love it.
But the first and the third .deb files given in the link are of amd 64 architecture and my Dell Inspiron n4010 has intel core i3 processor. So, when I tried to install the first and third files, the archive manager showed an error "Wrong architecture." How did this work for you? Did you have amd processor? Please I am really frustrated with this brightness issue.

---

