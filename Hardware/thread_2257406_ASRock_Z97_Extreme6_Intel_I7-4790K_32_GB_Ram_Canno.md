---
title: "ASRock Z97 Extreme6 Intel I7-4790K 32 GB Ram Cannot install ubuntu"
date: 2014-12-19
forum: Hardware
---

### Post by osmanb on 2014-12-19
Hello,
I have built a computer using ASrock z97 extreme 6 mb, and I7-4790K chip with 32 GB ram and GTX-970 video card, and no OS. I had ubuntu 12 LTS running on my old computer and used that 2TB hard disk with  additional  new 480GB SSD, old 250GB SSD. 2 TB drive had the ubuntu distro on it. My idea was to put the latest ubuntu on the 480GB ssd and have a fast parallel computing environment for scientific calculations. Now, the system boots using the old distribution. But have sound issues to which the solution is to put a new linux kernel (3.16 or newer). Now the only linux distributions that boot are : the old one on 2TB hd, and knoppix 7.4.2 from DVD or USB.  All the others (centos, open suse, mint ...) even non ubuntu ones seem to just give me a blank screen.
Knoppix is not a solution for me as it also needs nvidia drivers and don't know how to do that in that environment. I am scared to touch the old 12.04 LTS as it the only working (semi)  os I have. 
1). how can I update the kernel to new one without making the situation worse.
2). same with the nvidia drivers. is threre a possibility to just get a blank screen?
I need the nvidia drivers + cuda to do the work i planned.

I have tried turning off asmedia sata ports but did not seemed to affect anything. 
None of the live DVD linux options except for knoppix works.

Thanks in advance

---

### Post by oldfred on 2014-12-19
Are all your old installs BIOS? Your new motherboard is an UEFI motherboard with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

You will need to use ppa's to add the very newest kernel, support software and video drivers. One of the disadvantages of very new hardware is that the standard packaged distributions take a release or two to catchup and.

My old nVidia card would always boot to black screen unless I used nomodeset. But new UEFI system does boot and nouveau does work. I only get a bit of tearing inside these quick reply posts. But have not tried lots of video yet.

Your nVidia card is very new and in Maxwell family. Those with the first Maxwell 750Ti had/have lots of issues. I normally suggest only installing the nVidia driver from Ubuntu repository, but that driver is too old for your card.

Not sure which ppa is best, any examples showing a specific version to install, need to be changed to use the newest version available in the ppa. 
      
 14.04 drivers for Nvidia GeForce GT 730 desktop board - 
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)
Kernel updater script - also git methods
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)


 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)

Do not install directly form nVidia but this will tell you most current version.

 Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

I would create gpt partition structure on SSD with gparted, add a 300MB efi partition, a 2MB bios_grub partition and a 25GB / (root) partition and install just to that to test if UEFI works better.
With efi partition you can install in UEFI mode and with bios_grub partition you can install in BIOS boot mode, so you can easily test either way.
      
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

My standard suggestion, but I would not worry about /home or rest of SSD for now but just to test installs and getting all drivers install.


 Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
Even though it has a short life, you may want to try 14.10 or even 15.04 as they have newer kernels. I normally like to configure a LTS version as my main working system and install newer versions to test or experiment as they do not have long lives.

---

### Post by osmanb on 2014-12-20
Thanks a lot for the extensive info. From the info on your post and some others, I edited grub to add "nomodeset" after  "splash". This worked for all cases. I created usb installs and was able to edit  /boot/grub/grub.cfg files. Now all distros work in live case. 
I was able to install 14.04 LTS but its kernel a bit old for my MB. Sound , even though worked on the "live" session, in the installed case, a little garbled. I think I'll update the kernel from one of the links you provided. I have been rusty on system tools, used ubuntu without problems for the last 10 years. I also ran 15.04 in live mode. Sound  worked ok. I think I'll partition 250GB SSD into two and put 15.05 on one half and 14.10 on another. Don't yet know which one will be good to work on. 
Question is APT on CD  workable tool to transfer all my sofrware used on 12.x to 14 or 15 (apt-get installed ones)??
Thanks again.

---

### Post by oldfred on 2014-12-20
Unless you chroot into your system, I do not think you can use apt on live installer version to list software.
I actually use rsync to backup /home and run the dpkg commands to get new list of installed apps with every backup.

---

### Post by Yellow Pasque on 2014-12-21
Most likely, you are hitting this sound bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421) 
You don't need an entirely new kernel to fix it; just update the sound modules: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

I guess open-source nouveau chokes on the GTX 970 and will continue to do so until kernel 3.19: [http://www.phoronix.com/scan.php?page=news_item&px=MTg1MjU](http://www.phoronix.com/scan.php?page=news_item&px=MTg1MjU)
At least you found a way to get a usable install and allow installation of the blob driver.

---

### Post by osmanb on 2014-12-23
I was able to improve my graphics by doing
sudo add-apr-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346
all these  after CTRL ALT 2  and doing sudo service gdm stop 
after installs and doing gdm start, now I have great graphics and sound.
But, I also need the CUDA SDK to do build GPU accelerated programs. 
Got CUDA SDK from Nvidia (for Trusty), but cannot install it due to error:
preparing to unpack ...
unpacking ....
setting up ...
gpg: keyblock resource /etc/apt/trusted.gpg.d/xorg-edgers-ppa.gpg: resource limit
failed to add GPGKEY at /var?cuda-repo-6-5-prod/GPGKEY to apt keys.

Is xorg-edgers blacklisting nvidia cuda ? 

Also all the cuda stuff from ubuntu wont install either due to conflict (opencl -> wine ). I don't need wine as I don't have windows OS at all.
But removing wine removes other graphics display management apps that I may need :-(

Maybe I need to give up on 14.04 and try 15.04.
Thanks for all the help.

---

### Post by osmanb on 2015-01-03
I also had a fix for cuda not working:

at least one of the following was missing:
crw-rw-rw- 1 root root 195,   0 Jan  3 10:51 /dev/nvidia0
crw-rw-rw- 1 root root 195, 255 Jan  3 10:51 /dev/nvidiactl
crw-rw-rw- 1 root root 248,   0 Jan  3 10:55 /dev/nvidia-uvm

I think it was /dev/nvidia-uvm. I just run a script that creates them at login. Now everything is working fine with Trusty. No need to go to 15, with which I did not have any success yet. But every day there is a new one to try :-)

---

