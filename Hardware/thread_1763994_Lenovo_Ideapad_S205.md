---
title: "Lenovo Ideapad S205"
date: 2011-05-21
forum: Hardware
---

### Post by friedofraes on 2011-05-21
Hi everyone,

 I just got my new netbook today and wanted to install ubuntu. Well, it didn't work.
To be precise, the installation-process did work, but after restart I'm stuck in the bootscreen..
I also tried to install the netbook-version, but booting this from usb-stick only leeds to a black screen with the line: 

SYSLINUX 3.86 2010-04-01 EBIOS Copyright 1994-2010 H.Peter Anvin et al
_ (-> blinking)

I should also mention, that there is no DOS on it right now, since I bought it from a very nice guy, who apparently deleted it somehow (?).

Please help me!

---

### Post by benedi on 2011-05-26
Hi. 

I guess I had the same problem you have. I don' t exactly know why, but the bootloader grub2 (which is probably the one contained in your ubuntu) is somehow not compatible with the software (I think it has something to do with UEFI or BIOS) of the computer. Anyway booting from a live CD (or USB) and installing the first version of grub fixed the problem in my case. 

Kind regards 


Benedikt

---

### Post by bill_mchale on 2011-05-27
Since both of you appear to have installed ubuntu on the s205, what are your impressions?  Outside of Grub, is the machine essentially functional on bootup?  

--
Bill

---

### Post by ameseisch on 2011-05-27
I have Ubuntu running on my Ideapad s205. It is not without hang-ups. Wifi is a problem in an odd way. apparently it has something to do with with duplicate drivers loading. and then the hardware switch is quirky too. I haven't found a perfect solution but I found a acceptable workaround.

after startup run.

rfkill unblock wifi
rfkill unblock all
sudo modprobe -r acer_wmi

you will have to do it after each startup.

also, sleep and shutdown have issues. looks like it runs into a process that it can't interrupt. I have to hold down the power button to get it to shutdown, and have disabled all automatic sleep functionality.

---

### Post by ameseisch on 2011-06-04
other things not working as I have continued to test it out. 

internal mic,
headphones jack,
sd card reader

I'll try to post back if I get any of these figured out in case anyone else has this same piece of hardware. Hardware wise this laptop is pretty good, so I hope I can get past all these issues.

---

### Post by rwh on 2011-06-13
I've written a blog post that explains step-by-step how I installed Ubuntu 11.04 on the s205 (dual booted with Windows 7).  I'll update it if I can find any solutions to the above issues.

[Installing Ubuntu on the lenovo ideapad S205](http://helms-deep.cable.nu/~rwh/blog/?p=177)

---

### Post by bill_mchale on 2011-06-14
> **rwh said:**
> I've written a blog post that explains step-by-step how I installed Ubuntu 11.04 on the s205 (dual booted with Windows 7).  I'll update it if I can find any solutions to the above issues.

[Installing Ubuntu on the lenovo ideapad S205](http://helms-deep.cable.nu/~rwh/blog/?p=177)

I will attest to the method that rwh has posted.  It got my s205 running with ubuntu.  You have to be careful to keep your partitions straight, otherwise, you will be back to square one.

Also, to anyone who has gotten the s205 up and running, have you noticed slow wireless?  I did some tests yesterday and I download speeds were about **_20 times_** faster in windows than they were in linux.  Is it something in the configuration?  Or is there a driver I should be using?

Thanks, 
Bill

---

### Post by steve7777777 on 2011-06-19
removed.

---

### Post by sioban on 2011-06-23
Hi, 

I've just bought a Lenovo S205 and I'm playing with it under ubuntu 11.04.

I've followed RWH blog post about how to install Grub Legacy (Thanks BTW) and a comment inside this blog on which module I have to blacklist to make Wifi works.

So far so good, I still have some problems :
- Wifi is slow, I verified it using iperf, the max I can get is 40 kb/s, on my other Laptop on the same wifi under ubuntu 10.04 I can reach an average 24 Mbp/s.
- Hibernate / Suspend does not work, I highly suspect GRUB and options to be the problem, as I can use the suspend function on the Ubuntu USB installer (I needed it to unfreeze a OCZ Vertex 2 SSD drive to update it).
- SDCard does not work at all (no info at all about it...)

I've still have not tested MIC, Webcam, HDMI, jack connection and double screen.

Bluetooth is perfectly working with my iPhone for sharing connection (haven't tested USB sharing yet) ^^

BTW a thing not directly related to Linux but I wanted to update the BIOS of netbook. Lenovo is only providing Windows utilities. I think this is not right for a company that sell non OS netbook to only provide support under Windows (not even DOS !)... 
I've tried using UBCD4Win but got an error "Please Connect Battery".

---

### Post by bill_mchale on 2011-06-24
> **sioban said:**
> Hi, 

I've just bought a Lenovo S205 and I'm playing with it under ubuntu 11.04.

I've followed RWH blog post about how to install Grub Legacy (Thanks BTW) and a comment inside this blog on which module I have to blacklist to make Wifi works.

So far so good, I still have some problems :
- Wifi is slow, I verified it using iperf, the max I can get is 40 kb/s, on my other Laptop on the same wifi under ubuntu 10.04 I can reach an average 24 Mbp/s.
- Hibernate / Suspend does not work, I highly suspect GRUB and options to be the problem, as I can use the suspend function on the Ubuntu USB installer (I needed it to unfreeze a OCZ Vertex 2 SSD drive to update it).
- SDCard does not work at all (no info at all about it...)

I've still have not tested MIC, Webcam, HDMI, jack connection and double screen.

Bluetooth is perfectly working with my iPhone for sharing connection (haven't tested USB sharing yet) ^^

BTW a thing not directly related to Linux but I wanted to update the BIOS of netbook. Lenovo is only providing Windows utilities. I think this is not right for a company that sell non OS netbook to only provide support under Windows (not even DOS !)... 
I've tried using UBCD4Win but got an error "Please Connect Battery".

Hi, in my experience, the webcam should work, the microphone doesn't.  I haven't tested the other stuff because it is not very important to me.  Suspend and hibernate definitely work for me and I was also using RWH's blog post to set everything up.

As for wireless, what I normally get is a short burst of high performance (if I am reading it right 100 KB/s) then it settles down to around 10-15 KB/s.  Its almost like it is some sort of power saving mode.  Does your other laptop have the same wifi card as the s205?  

--
Bill

---

### Post by sioban on 2011-06-25
nope, it's an Intel 3945ABG

---

### Post by sioban on 2011-06-26
i've found this on a german forum : 

> Under 11:04 there are problems with the kernel and the drivers used here.  Test driver for the following boot option:   ```
echo "options ath9k nohwcrypt = 1" | sudo tee / etc/modprobe.d/ath9k.conf 
```  Driver unload / reload or restart. 
  Otherwise it is recommended to install a newer kernel.  Try it with a [mainline kernel]("http://translate.googleusercontent.com/translate_c?hl=en&prev=/search%3Fq%3Dubuntu%2Blenovo%2Bs205%2Bwifi%2Bslow%26hl%3Dfr%26client%3Dubuntu%26hs%3Dpo5%26channel%3Dfs%26prmd%3Divnsfd&rurl=translate.google.com&sl=de&twu=1&u=http://wiki.ubuntuusers.de/Mainline-Kernel&usg=ALkJrhhXwPXSY4Rnu4BDU21a3FhKLJxgwQ") from 11.10 (06.02.39-rc5) / [mainline kernel archive]("http://translate.googleusercontent.com/translate_c?hl=en&prev=/search%3Fq%3Dubuntu%2Blenovo%2Bs205%2Bwifi%2Bslow%26hl%3Dfr%26client%3Dubuntu%26hs%3Dpo5%26channel%3Dfs%26prmd%3Divnsfd&rurl=translate.google.com&sl=de&twu=1&u=http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/&usg=ALkJrhgV8LBPXlmKu3hqqsHYfyja0hPG9w") 
  [http://kernel.ubuntu.com/ ~ kernel-ppa  9-rc5-oneiric /]("http://translate.googleusercontent.com/translate_c?hl=en&prev=/search%3Fq%3Dubuntu%2Blenovo%2Bs205%2Bwifi%2Bslow%26hl%3Dfr%26client%3Dubuntu%26hs%3Dpo5%26channel%3Dfs%26prmd%3Divnsfd&rurl=translate.google.com&sl=de&twu=1&u=http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-rc5-oneiric/&usg=ALkJrhiTXGULl_MzB1G8WNLDEjrkYAzbWQ") 
  Here the following packages are required: 
  linux-image-2.6.39-020639rc5-generic_2.6.39-020639rc5.201105041556_i386.deb 
  linux-headers-6.2.39-020639rc5_2.6.39-020639rc5.201105041556_all.deb 
  linux-headers-6.2.39-020639rc5-generic_2.6.39-020639rc5.201105041556_i386.deb 


> [http://translate.google.com/translate?hl=en&prev=/search%3Fq%3Dubuntu%2Blenovo%2Bs205%2Bwifi%2Bslow%26hl%3Dfr%26client%3Dubuntu%26hs%3Dpo5%26channel%3Dfs%26prmd%3Divnsfd&rurl=translate.google.com&sl=de&u=http://forum.ubuntuusers.de/topic/kein-wlan-atheros-ar9285-ubuntu-11-/#post-2985882](http://translate.google.com/translate?hl=en&prev=/search%3Fq%3Dubuntu%2Blenovo%2Bs205%2Bwifi%2Bslow%26hl%3Dfr%26client%3Dubuntu%26hs%3Dpo5%26channel%3Dfs%26prmd%3Divnsfd&rurl=translate.google.com&sl=de&u=http://forum.ubuntuusers.de/topic/kein-wlan-atheros-ar9285-ubuntu-11-/#post-2985882)

---

### Post by kr00lplatinum on 2011-06-28
Hello everyone, I too am a IdeaPad S205 owner. I wanted to put Ubuntu on the machine and dual boot Windows 7. I created the Recovery DVDs and wanted to test them out before installing Ubuntu. I set the bios boot order to seek my USB DVD Rom first. However, when the USB DVD Rob is plugged into the S205 and I hit the power button, it locks up on the Lenovo Boot Screen. 

I have tried to hit F12 button (Fn+F11) to get to the boot order screen but it still locks up!

Anyone have any suggestions? I could install Ubuntu using a USB Drive however, that won't fix this problem. 

Also, updating the bios did not help the situation.

---

### Post by sioban on 2011-07-03
I've found a solution for the slow Wifi problem without having to install a 2.6.39-RC driver.

Just install backport modules :

```
sudo apt-get install linux-backports-modules-headers-natty-generic-pae linux-backports-modules-net-natty-generic-pae
```You can safely remove -pae extension if you use less than 3Go memory.

I've also found a way to upgrade the BIOS :
- download the windows binary files from Lenovo support site
- extract the files on a linux workstation using cabextract utilities
- copy at least .bin, SCT.BAT, pflash.exe and ACDC.exe on a bootable DOS USB key
- Boot on it
- flash ;)

---

### Post by bill_mchale on 2011-07-05
> **sioban said:**
> I've found a solution for the slow Wifi problem without having to install a 2.6.39-RC driver.

Just install backport modules :

```
sudo apt-get install linux-backports-modules-headers-natty-generic-pae linux-backports-modules-net-natty-generic-pae
```You can safely remove -pae extension if you use less than 3Go memory.

I've also found a way to upgrade the BIOS :
- download the windows binary files from Lenovo support site
- extract the files on a linux workstation using cabextract utilities
- copy at least .bin, SCT.BAT, pflash.exe and ACDC.exe on a bootable DOS USB key
- Boot on it
- flash ;)

So I tried this solution... And every time I get the following errors:

E: Unable to locate package linux-backports-modules-headers-natty-generic-pae
E: Unable to locate package linux-backports-modules-net-natty-generic-pae

Is there another step I am missing here?

--
Bill

---

### Post by sioban on 2011-07-06
Arg.
Can you try without -pae ?

My SSD just died yesterday, so I can't check anymore on my system if these modules came from a ppa or from a official repository :(

---

### Post by Nonsteeler on 2011-07-20
I am way out of depth with this shiny new machine. Basically I'd like the s205 as a dual boot computer, hence my scenario is identical to rmh's.

At the moment however I am in the unfortunate position that neither Win7 nor Ubuntu is working, ie neither OS is booting from the hard rive. I followed rwh's recipe as posted here: [http://helms-deep.cable.nu/~rwh/blog/?p=177](http://helms-deep.cable.nu/~rwh/blog/?p=177)

However I can't install grub1 on the ext2 partition, as the **terminal announces
```

root@ubuntu:/# grub-install /dev/sda6
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda6: Not found or not a block device.
```

A bit earlier I get

```
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: unable to resolve 'UUID=2417ea1f-f985-4a6b-93a3-0770ac61c158'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
findfs: unable to resolve 'UUID=dcb7f025-1008-4e57-86bf-2e15daa23b79'
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 
```

Problem is I don't how to 'validate /etc/fstab'...

I guess something is wrong with the partitions ... I'd be happy to get back at least Win7.  Any useful input greatly appricaited as I'm lost here/not used to a Linux machine playing-up *that* seriously.

EDIT:
fdisk -l gives me:
```
root@ubuntu:/# fdisk -l
cannot open /proc/partitions
```

---

### Post by rwh on 2011-07-20
Hi Nonsteeler,

Yes, it looks like your partitions aren't set up the same way that mine ended up.  All is not yet lost, however!  Could you try running:

```
fdisk /dev/sda
```

Then press "p" to print the partition table and post the output here?  Also post the contents of your /etc/fstab file.

If worse comes to worst, you can always restore to factory state by pressing the little orange button "OneKey Recovery Restore".  From the hardware maintenance manual:

> The IdeaPad S205 computers come with pre-installed OneKey Rescue System. In order to save application files and the initial backed up files of the system, the hard disk in a Lenovo computer includes a hidden partition when it is shipped. If you need to restore the system to the point of your first boot up, just enter Lenovo OneKey Rescue System and run Restore to factory default. For details of OneKey Rescue System, see the User Guide for OneKey Rescue System. 

Note: This will delete all the new data on the system partition (C drive), which is not recoverable. Make sure to back up your critical data before you perform this action

From memory, you use a pen to press the tiny recessed orange button with a "back" arrow next to it up in the top left or top right of the computer (don't have it with me right now).

Cheers,

Rob

---

### Post by Nonsteeler on 2011-07-20
Rob, thanks for pointing to the onekeyrecovery option. I will try this. And then give ubuntu a 2nd try - a bit more prepared ... or wait for a newer kernel/ubuntu  version. Although I would quite fancy an ubuntu *derivative *running with lxde on this machine soon-ish -  ... I will gauge my options/the situation after restoring Win7...

---

### Post by infernosoft on 2011-08-13
Has anyone figured out how to get the internal mic working yet?

---

### Post by sioban on 2011-08-13
This ppa is useful for the internal Jack, maybe it'll help for the mic : 

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa")
 sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

---

### Post by infernosoft on 2011-08-13
> **sioban said:**
> This ppa is useful for the internal Jack, maybe it'll help for the mic : 

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa")
 sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

So, I added the PPA to my repo list and did an update. Now, I think I need to install some of the packages within the PPA repo, right? If so, which ones? And if not, what do I need to do now?

Sorry I'm a little new to Ubuntu (have been using Fedora for over a year now and just decided to move to Ubuntu).

---

### Post by sioban on 2011-08-14
I think that a "sudo apt-get upgrade" should do the job.
It's just updated versions of already installed packages.

---

### Post by Baen on 2011-08-29
I've tried to install ubuntu using rwh's guide, but it didn't work. I think I've followed it quite closely and got no error messages, aside from the fact that sudo apt-get update didn't work. I installed grub with synaptic, update-grub, grub-install \dev\sda7 (I have root at 6 and boot at 7) and update-grub again just for the heck of it. :)

I used EasyBCD to fix the W7 bootloader, and everything seemed peachy, but Ubuntu still won't boot. Just get the black screen.

Any ideas where I've gone wrong?

I know that's not much info to go on, but I'm not sure what you need to know. I've tried googling it, but no luck, so it seems I'm stuck with a shiney, useless netbook.

---

### Post by dwpbike on 2011-09-05
> **sioban said:**
> This ppa is useful for the internal Jack, maybe it'll help for the mic : 

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa")
 sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

i owe you a beer.  i just assumed my hp touchsmart, which is neither, was deaf (it has visible injury from multiple drops by previous owners).  not a must have feature, so i let it slide.  now i may attempt google chat.  tanks

---

### Post by midnightkz on 2011-10-02
*delete (no need for asking, found an answer myself)

---

### Post by sioban on 2011-11-22
Hi !

I've just tried to read a HD 1080p video under ubuntu but with no sucess (too slow).
I think I may have a problem with the drivers.

Awaited perfs are : ATI Radeon HD 6310 (Catalyst), frame=13 262, fps=2 652
and I got frame=3300, fps=644

direct rendering is activated !

Any idea ?

---

### Post by vikos on 2011-11-26
Finally 
I made It. All Hardware works! :D

Sound card, WebCam, CardReader, suspend, BT, WLAN. Everything.
Video out.. Two Monitor. (Via D-sub and HDMI...) 
I can't test the HDMI's sound...I haven't any device that use HDMI to sound input... 

The only litle thing is: 
The Wifi  no alwasy works at first time. On a WPA2 networks with special chars in password.. can't connect at first. But can on second!!! So it connects!... 

I'll wirte a 'long how to'.


Cheers!

Ps.: Can play 1080P MKV !

---

### Post by sioban on 2011-11-26
> **vikos said:**
> I'll wirte a 'long how to'.

Interested.

> **vikos said:**
> Ps.: Can play 1080P MKV !

Interested too.
In 11.04 or 11.10 ?

---

### Post by vikos on 2011-11-27
> **sioban said:**
> in 11.04 or 11.10 ?
11.10...

---

### Post by sioban on 2011-11-27
I was afraid of going on 11.10 as it was hard to make 11.04 wifi works at full speed...

Maybe I'll give a try.

---

### Post by Ti_p_it on 2011-12-01
Here the lucazades answer #10 for wireless problems seems to work for me: [http://ubuntuforums.org/showthread.php?p=11296524](http://ubuntuforums.org/showthread.php?p=11296524) in Xubuntu 11.10.

---

### Post by pafarthing on 2011-12-11
I'm just curious, as I am looking seriously at the S205: It's not the ideal solution, but given the problems people have reported with this laptop, has anyone tried using Wubi to install Ubuntu, and if so, has it avoided the difficulties?

It's a pity there are so many reports of problems as Ubuntu runs flawlessly on my Lenovo 3000-G530.

Thanks.

---

### Post by indistinguishible on 2011-12-28
> **vikos said:**
> Finally 
I made It. All Hardware works! :D

Sound card, WebCam, CardReader, suspend, BT, WLAN. Everything.
Video out.. Two Monitor. (Via D-sub and HDMI...) 
I can't test the HDMI's sound...I haven't any device that use HDMI to sound input... 

The only litle thing is: 
The Wifi  no alwasy works at first time. On a WPA2 networks with special chars in password.. can't connect at first. But can on second!!! So it connects!... 

I'll wirte a 'long how to'.


Cheers!

Ps.: Can play 1080P MKV !

We are waiting for this HOWTO. I have a lot of problems with my Ubuntu. Wi-Fi, Webcam and sound are OK, but internal microphon, card reader and 2 of 3 USB ports don't work.

Vikos, help us!

---

### Post by vikos on 2012-01-11
SO...
I'm back...

At first: I have to fix myself. You cannot make work pure linux install.

I think the problem is the grubs uEFI image. Ony ! only Windows 7 64Bit has good EFI image.
So use Wubi install. I hope this problem will fix in the future!!!

I've spent thousands of hours to make work pure linux installation (dual install too!), but i cant.

However the Wubi install can preform very well.

I works on linux 7-9 hours a day.. but I need to use windows at home... :(
Lenovo is my only PC...
I hope 12.04 will work perfectly out of the box.:)
--------------------------------
So... on wubi install:

Touchpad, BT, suspend, 3d acceleration (mesa driver), HDMI/ VGA (dual screen too!) works out of the box.

Wireless:
The driver is in the installed system. On 11.04 use rt2860STA on 11.10 use  rt2800pci kernel module. 
They are not the same. Officially the 2860sta contains the 309x driver.. but it's moved to 2800pci in kernel 3.0+!!!!

11.04 kernel module blacklist:
# Lenovo S205 fix
blacklist acer_wmi
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib

11.10 blacklist:
# Lenovo S205 fix
blacklist acer_wmi
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib




1080P video playing:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29)
Use this wiki to install fglrx driver...
Follow the Hardware Acceleration part too.

I used VLC player. You can change the video decoder device in the setting. Use the GPU.

Dual screen >> acceleration works only on primary screen (hardware limitations). If the playing sluggish.. Use the other screen or switch back to one screen mode.
(The problem there is under Widows too!!!).

I've read there can be some problem with acceleration and compiz.
I cant confirm this because I used Xubunut. 

USB on the right / Card reader:
The card reader uses wrong driver and it blocks the usb ports on right side.
Follow this instructions to install the driver:
[http://www.worldofnubcraft.com/1700/enable-realtek-usb-2-0-card-reader-on-ubuntu/](http://www.worldofnubcraft.com/1700/enable-realtek-usb-2-0-card-reader-on-ubuntu/)


Suspend on pure install:
There's possible to suspend because the previous version of fedora can. 

Finally:
I'm only enthusiastic ubuntu user not a pro linux guru... so everything in this help originate from lot of google searchs!

---

### Post by p0bailey on 2012-01-19
I've recently purchased a Lenovo Ideapad 205 and without big hassles I was
able to install  Xubuntu 11.10 64bit alternate edition. Everything is working
out of the box, except the internal microphone and the two USB ports on the 
right side. There's any workaround for this issues?

Best,
Phillip

---

### Post by loudness on 2012-01-22
> **p0bailey said:**
> Everything is working
out of the box, except the internal microphone and the two USB ports on the 
right side. There's any workaround for this issues?

Best,
Phillip

For the internal mic, see [http://ubuntuforums.org/showthread.php?t=1732074](http://ubuntuforums.org/showthread.php?t=1732074)

For USB, follow the instruction in the previous post (Vikos), but remove the line
#define GET_CARD_STATUS_USING_EPC
from rts51x_chip.h before running make.

Cheers,
Rob

---

### Post by Shtodan on 2012-01-30
Hi im a bit noob in linux, i have wireless problem on my s205 with 3090 ralink, so if i dont do commands these 3 commands i cant use wireless. is there some fix for that to work normal?
i use 11.10..ty and cheers

---

### Post by Shtodan on 2012-01-31
Hi i solved my "wireless disable" issue, so ill write here and maybe helps some1
ALT+F2 and run to edit blacklists  [B]gksu gedit /etc/modprobe.d/blacklist.conf  
[/B]I removed all related to ralink (which is my wifi) and added
line **blacklist acer_wmi  **
then just save and exit
That's it! Hope  it helps some1!
cheers

---

### Post by ameseisch on 2012-04-28
old solution stopped working for me with 12.04, but deep in a bug report I found new way. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659)

"At least for the IdeaPad S205 model 1038 there is a quite weird workaround:

After installation there is a mysterious "ubuntu" entry in the boot order that must not be at the top. So go to your "BIOS" with F2 and change the boot order so the hardisk comes before "ubuntu" entry. Seems like a buggy EFI/BIOS implementation.

Kudos goes to the german guys at http://forum.ubuntuusers.de/topic/wlan-karte-ralink-rt3090-lenovo-ideapad-s205-l/"

---

