---
title: "Ubuntu Installation Freezes Randomly on MSI GE72 2QF Apache Pro 2"
date: 2015-06-28
forum: Hardware
---

### Post by steven-wooding on 2015-06-28
Hi

I am fairly advanced with configuring and setting up Ubuntu and have been an Ubuntu user for about 10 years. So I usually get through problems quite easily. But I cannot seem to get past this problem. The problem is:

When installing or running Ubuntu 14.04.2 the laptop would randomly hang. Sometimes it can run for an hour before it does so. But other times it barely makes it past boot. I have tried the following:
[LIST=1]
[*]Disabled FastBoot
[*]Disabled Intel SpeedStep
[*]Disabled SecureBoot
[*]Enabled UEFI with CSM
[*]Even tried running it in a virtual machine, using VirtualBox and also VMWare workstation on a windows 8.1 host, tried Ubuntu 14.04.2 64 bit and 32 bit also tried Ubuntu 15.04 64 bit. But it simply freezed the entire machine and windows throws an exception saying "MACHINE_CHECK_EXCEPTION". I have disabled various options inside each virtual machine's like VT-x as well as in my BIOS. I disabled 3D acceleration mode.
[*]I added nomodeset into the grub parameters
[*]I added acpi=off into the grub parameters
[/LIST]

I have been struggling for about 4 days now, and it seems like this laptop is allergic to Ubuntu, or possibly any Linux kernel for that matter. It might be because it is a very new generation CPU (i7 5700HQ) that the Linux kernel is not compatible with. The weird thing is that it happens inside an emulator like VMware and VirtualBox where it also crashes the host, as well as when running directly on the hardware.

The specific Laptop model is a GE72 2QF Apache Pro with the added 256 SSD and 16GB Ram. [http://www.msi.com/product/nb/GE72-2QF-Apache-Pro.html#hero-overview](http://www.msi.com/product/nb/GE72-2QF-Apache-Pro.html#hero-overview)

I can't seems to find any articles or forums regarding issues with this model or with the 5th generation i7 processors. Any help would be very very much appreciated.

Thank You










I have got it working now. Here is the solution:

I have got Ubuntu running on my GE72 2QF. It runs very well. Setup was a bit of a problem but other than that Ubuntu runs like a charm now. Everything works. Even hibernation and suspend works 100%. Sometimes it would not pick up my wifi hotspot but then I simply click "Connect to hidden wifi network" and select my hotspot from the list. Then it will connect with no problems. But I am very happy with the installation. Ubuntu runs amazingly fast.


The reason that the installation crashes is because of 2 reasons. One is that the SSD and Ubuntu does not work properly with asynchronous transfers. The other is Intel speed step. I think both cause the same exception. 


I have posted the complete process that I followed to get it set up earlier on in this thread but I will post it again here for convenience. Here it is:


1. You HAVE to install ubuntu 15.04 64bit. Any other version simply does not work. Some people also reported that 14.04.3 64bit works too.
2. In the BIOS you have to disable the following: FastBoot, Intel Speedstep, SecureBoot
3. In the BIOS make sure that UEFI is enabled with CSM
4. When starting the Ubuntu installation you have to add the kernel option "libata.force=noncq". This is a MUST!
5. After the installation do a full update on Ubuntu. Then you can remove the kernel option "libata.force=noncq". Your SSD should perform faster now. But SpeedStep is still a problem. I have to keep it off.
6. I even re-enabled Fastboot and Secure in the BIOS and it still runs fine.


I have tried to install it inside a VM using VirtualBox as well as VMware but I never got it working properly, still freezes now and then. I just run it natively on the hardware.

---

### Post by efflandt on 2015-06-28
Of course if you ask MSI, they will tell you that MSI does not support Linux.

I personally bought an MSI GE60 2OE with Win7 while I still could in Oct 2013, and while it is capable of UEFI, the BIOS version for Win7 defaults to regular BIOS and uses msdos partitions. So it was pretty much mainstream i7-4700MQ with hybrid Intel HD 4600/Nvidia GTX 765M graphics. The only unusually thing I ran into removing its Win7 D: partition and installing Ubuntu 13.10 at that time is that when I put grub2 on sda4 (wanting to leave the mbr untouched) and marked that as the boot partition (removing boot flag from sda2) something kept resetting sda2 boot flag, so I had to resort to installing grub on USB memory stick to boot Linux. That is no longer an issue since I installed 64-bit 14.04 with grub on mSATA SSD and set that (sdb) to be the boot drive. Note that although **nomodeset** is typically used for desktops with Nvidia graphics, I read a post where that did not work for hybrid Intel/Nvidia laptop, so I did not use nomodeset. I am currently using nvidia-331-updates for that from the normal repositories, but I do not know if the GTX 970M needs something newer (xorg-edgers ppa has versions through nvidia-352 package).

But I have not had to deal with Secure Boot or UEFI yet. And not sure if "Exclusive Super RAID 2 with 3 SSD RAID0" might result in some proprietary issues (recently read another post about someone attempting to install Ubuntu on dual Win8 RAID drives). Sometimes when you are cutting edge not everything gets support right away in Linux until someone works that out. For example hybrid graphics were somewhat of a pain in 13.10 because it used bumblebee and optirun needed additional parameters for certain games (never could get primusrun to work). But in 14.04 with nvidia prime the active graphics device can be switched from NVIDIA X Server Settings. So you may want to test a newer Ubuntu version like 15.04 to see if that works any better.

---

### Post by weatherman2 on 2015-06-28
For fun, try a different desktop edition - that is, try Lubuntu instead of Ubuntu.  Maybe it's not a driver issue at all.

And you should re-enable Intel Speedstep if you haven't already.  That lets the CPU slow down when idle to save power and is really important for keeping the laptop cool and saving battery life, etc.

---

### Post by steven-wooding on 2015-06-29
> **weatherman2 said:**
> For fun, try a different desktop edition - that is, try Lubuntu instead of Ubuntu.  Maybe it's not a driver issue at all.

And you should re-enable Intel Speedstep if you haven't already.  That lets the CPU slow down when idle to save power and is really important for keeping the laptop cool and saving battery life, etc.

Ok. I have enabled everything again in the BIOS (SpeedStep, Fastboot, UEFI etc) and installed Lubuntu 14.04 64bit in an VMWare emulator. And it seems to be standing it's ground. I went through the whole installation process and the upgrade process afterwards. Also installed VMWare tools and it is running fine. Haven't crashed yet. So maybe you are right. It's something inside Ubuntu that it not fully compatible with the hardware.

The next step is to run it natively on the hardware without an emulator. I will do that tonight and post the results. But thanks for the help so far.

---

### Post by steven-wooding on 2015-06-29
Lubuntu 14.04 x64 just crashed the laptop from within the VMware emulator. Exactly the same issue as Ubuntu. But it seems to run a bit longer before it crashes. Going to try Lubuntu 15.04 x64 directly on the hardware now.

---

### Post by steven-wooding on 2015-06-29
Seems like I have figured it out. Thanks to efflandt. The SSD was the problem. With the boot grub flag "libata.force=noncq" to fix the SSD issues, and disabling fast boot, secure boot and speed step in the BIOS. And it has to be Ubuntu 15.04 x64 or later. Previous versions just won't work. And after the installation you can run a full update and enable speed step again as well as remove the "libata.force=noncq" flag from grub. Seems to run fine now :p .

---

### Post by maquann on 2015-07-17
I have a very similar computer (MSI GE62 Apache) and seem to be having the same freezing problem when I try to install Ubuntu (I'm dual booting Windows 8.1). Unfortunately this is my first time installing Ubuntu, so I have very little experience in this area.

I have disabled fast boot, secure boot, speedstep in BIOS, and using the 15.04 x64 iso. How do I add the boot grub flag prior to installation? Can I modify it through the Try Ubuntu Without Installing/Install Ubuntu screen? 

Thank you

---

### Post by pesalamone on 2015-08-02
This might help:https://help.ubuntu.com/community/AspireTimeline/Fixes

---

### Post by noobslab on 2015-08-20
Hi Steve,

Well, the computer doesn't have problem. Only you need to boot your Ubuntu using upstart service, as you may or may not know that Ubuntu has switched to systemd. So by default Ubuntu is using it. 

Solution for VM:
Follow this method if you want to use Ubuntu in the VirtualBox or VMware, once you start your Ubuntu VM immediately press **ESC** key to see boot options > **choose advance option** > and boot **Ubuntu with (upstart)**. I am pretty sure it will work for you.
If it does work for you and you want to switch permanently to upstart then you can do it from here [https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart](https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart)

I can't test it on the hardware but you can check the same method on your laptop and don't forget to let us know. It may help others who run into same problem like you do.

Since the core i7 5xxxhq series is newer than 4xxxhq series, so you may have to wait little bit to get everything work properly. Hopefully this issue will be addressed soon.

Umair from **[http://NoobsLab.com](http://NoobsLab.com)**
Don't forget to visit us for Ubuntu related stuff, also checkout our Virtual machines project **[http://osboxes.org](http://osboxes.org)**

Best,

---

### Post by GiulioGx on 2015-08-23
Hi, I intend to buy a MSI GP62 laptop, which has a very similar configuration to the one you bought! It would be very nice of you if you could share some of your experience with your laptop on linux, in particular i would like to know if you have had any other trouble beside the one you told about (is not a problem anymore , is it?). Thank you very much! ;)

---

### Post by kgross on 2015-09-02
I have this same model ge72 2qd apache pro, and I can't get ubuntu installed at all.   The system hangs hard before I can even start the install.     How did you get it installed on yours (trying to install on the hardware rather than via a VM, but that is next)

---

### Post by aaronjeaton on 2015-09-05
Hi,
I have a MSI GE62 2QD Apache Pro and I've had to use Ubuntu 14.04.01 Desktop in order to install Ubuntu. 14.04.02, 14.04.03 and 15.04 freeze randomly and seem to give nouveau error messages during startup.

Hope this helps

---

### Post by gabrarlz on 2015-09-07
I've just bought a ge72 laptop and also struggling to install Ubuntu (adm64) on a VM with virtualbox in a Windows host.
Ubuntu 15 raises bsod on installation
Ubuntu 14.04.3 randomly raises bsod (I installed everything but when I'm programming it crashes):
Gonna try 14.04.1 now

---

### Post by resaypi on 2015-09-07
I have MSI ge72, and I have the same issue of freezing. What is the solution to this?

---

### Post by gabrarlz on 2015-09-07
Also tried Ubuntu 14.04.1 without success. Same BSOD with **MACHINE_CHECK_EXCEPTION**

---

### Post by gabrarlz on 2015-09-07
EDIT: This below did not work

I'm going to try this now: [https://superuser.com/questions/938199/new-computer-cant-run-linux-but-runs-windows-with-no-problems?newreg=3fea057f4dea418d9f001494b63532c4](https://superuser.com/questions/938199/new-computer-cant-run-linux-but-runs-windows-with-no-problems?newreg=3fea057f4dea418d9f001494b63532c4)

[FONT=Helvetica Neue] I seem to be having some luck *fixing* the Linux problems by disabling some features in the BIOS. I haven't seen any crashes since doing so. The changes I made initially (just based on guessing):[/FONT]

[LIST]
[*]Virtualization Technology: Disabled <===== Since I'm using Virtualbox, I'm not disabling it.
[*]Fast Boot: Disabled
[*]SpeedStep: Disabled
[*]PCI Latency Timer: 64 Clocks (was 32)
[/LIST]
[FONT=Helvetica Neue]Based on subsequent testing of variations of these, apparently *both* VT and SS need to be disabled -- but for sure, at least SpeedStep. **Does this make it easier to isolate the crashes as being based on a hardware defect?** ...Or could this possibly be a software problem in Ubuntu/Linux?[/FONT]

---

### Post by gabrarlz on 2015-09-08
Just got another BSOD with those steps above.

---

### Post by steven-wooding on 2015-09-09
OP here

I have got Ubuntu running on my GE72 2QF. It runs very well. Setup was a bit of a problem but other than that Ubuntu runs like a charm now. Everything works. Even hibernation and suspend works 100%. Sometimes it would not pick up my wifi hotspot but then I simply click "Connect to hidden wifi network" and select my hotspot from the list. Then it will connect with no problems. But I am very happy with the installation. Ubuntu runs amazingly fast.

The reason that the installation crashes is because of 2 reasons. One is that the SSD and Ubuntu does not work properly with asynchronous transfers. The other is Intel speed step. I think both cause the same exception. 

I have posted the complete process that I followed to get it set up earlier on in this thread but I will post it again here for convenience. Here it is:

1. You HAVE to install ubuntu 15.04 64bit. Any other version simply does not work.
2. In the BIOS you have to disable the following: FastBoot, Intel Speedstep, SecureBoot
3. In the BIOS make sure that UEFI is enabled with CSM
4. When starting the Ubuntu installation you have to add the kernel option "libata.force=noncq". This is a MUST!
5. After the installation do a full update on Ubuntu. Then you can remove the kernel option "libata.force=noncq". Your SSD should perform faster now. But SpeedStep is still a problem. I have to keep it off.
6. I even re-enabled Fastboot and Secure in the BIOS and it still runs fine.

I have tried to install it inside a VM using VirtualBox as well as VMware but I never got it working properly, still freezes now and then. I just run it natively on the hardware.

---

### Post by resaypi on 2015-09-09
> **steven-wooding said:**
> OP here

I have got Ubuntu running on my GE72 2QF. It runs very well. Setup was a bit of a problem but other than that Ubuntu runs like a charm now. Everything works. Even hibernation and suspend works 100%. Sometimes it would not pick up my wifi hotspot but then I simply click "Connect to hidden wifi network" and select my hotspot from the list. Then it will connect with no problems. But I am very happy with the installation. Ubuntu runs amazingly fast.

The reason that the installation crashes is because of 2 reasons. One is that the SSD and Ubuntu does not work properly with asynchronous transfers. The other is Intel speed step. I think both cause the same exception. 

I have posted the complete process that I followed to get it set up earlier on in this thread but I will post it again here for convenience. Here it is:

1. You HAVE to install ubuntu 15.04 64bit. Any other version simply does not work.
2. In the BIOS you have to disable the following: FastBoot, Intel Speedstep, SecureBoot
3. In the BIOS make sure that UEFI is enabled with CSM
4. When starting the Ubuntu installation you have to add the kernel option "libata.force=noncq". This is a MUST!
5. After the installation do a full update on Ubuntu. Then you can remove the kernel option "libata.force=noncq". Your SSD should perform faster now. But SpeedStep is still a problem. I have to keep it off.
6. I even re-enabled Fastboot and Secure in the BIOS and it still runs fine.

I have tried to install it inside a VM using VirtualBox as well as VMware but I never got it working properly, still freezes now and then. I just run it natively on the hardware.


These steps worked for me for ubuntu 14.04 64 bit. I've been using it for more than a day without freezing so far. If freezing occurs I'll try switching to 15.04. Thanks for the update.

---

### Post by steven-wooding on 2015-09-15
Awesome. I see that 14.04.3 has been released in the beginning of August. And I have tried to install 14.04.2 and failed. So it might be that the Linux kernel that comes with 14.04.3 was already compatible enough to make it past the installation phase.

---

### Post by gabrarlz on 2015-09-22
I'm still trying to make it work with VirtualBox :(

---

### Post by eycheu on 2015-09-28
Does anyone has any idea how to install Ubuntu on MSI GS60 6QE laptop with generation 6 i7 CPU. I got the error that CPU got soft lock.

I have not problem installing Ubuntu 14.04.03 64 bit in VMWare.

---

### Post by fmbrieva on 2015-10-28
I have installed Ubuntu 15.10 on my MSI GE72 2QD Apache Pro with i7-5700HQ and nVidia Geforce GTX960M.

These are the steps:

**1. Update BIOS** for GE72 2QD (This BIOS update Microcode version to 13)
    (Be careful!, you can damage your computer if you have lack of technical expertise)

**2. Install Ubuntu 15.10**

**3. Update Nvidia**:
>      sudo add-apt-repository ppa:graphics-drivers/ppa
     sudo apt-get update
     sudo apt-get install nvidia-352 nvidia-settings

Good Luck!

---

### Post by tibor-sekelj on 2015-12-27
How to update bios on msi GE72 6QD?

current version is 2.17.1254

i own only ubuntu and mac devices.
cant find anywhere Bios update download or instructions.

---

### Post by Vladlenin5000 on 2015-12-27
> **tibor-sekelj said:**
> cant find anywhere Bios update download or instructions.

BIOS as well as drivers updates can usually be found at the manufacturer's website. Have you searched there? It took me just a couple of seconds to find this:
[http://www.msi.com/product/notebook/support/GE72-6QD-Apache-Pro.html#down-bios](http://www.msi.com/product/notebook/support/GE72-6QD-Apache-Pro.html#down-bios)
Instructions are included.

---

### Post by manutheking on 2016-03-03
Hi, 

my GE72 6QD has just arrived and I've just seen the problem, I tried to do what the OP says but it doesn't work, can you explain me how to put the kernel options? I think I'm doing it right but just in case

thanks

---

### Post by benjamindean on 2016-03-25
Hi, everyone. 
Same problem here. MSI GE72 6QD. Here is the story:

1. USB boot failed with "broken bios suspected" message. Updated bios - no luck.
2. Played with boot parameters and got it working with "acpi=off". Installed normally, but this parameter cuts off some hardware communication. Keyboard, mouse, etc.
3. Updated kernel to 4.5. Now a different message about "nouveau".
4. Installed Nvidia drivers, but got a black screen on boot, until "nomodeset" were added to boot parameters. 
5. Got a "Login loop" with that. Installing kernel headers, deleting .Xauthority, etc - no luck.

Is there any way to use Ubuntu on this laptop?

---

### Post by ted_thomas on 2016-03-25
Thanks for this very detailed assist. I too have been using Ubuntu for nearly 10 years, and I've never had any problems with random freezes -- until a few days ago, when I installed UbuntuMATE on an Acer desktop (dual-boot with Windows 7). I have 14.04 running on my current primary E-Machine, and it has never frozen. If you google 'ubuntu 14.04 random freezes' you'll be deluged with posts, and in almost every case, they're attempting to explain it on the basis of something: browser, nvidia driver, you name it. In one post (askubuntu) they led with "Every computer freezes now and then..." That's right: 20 years ago they did (and when you're running Windows, they still do). I'm concerned this issue is not being prioritized by Ubuntu 'HQ'. In my case, the freezes were precipitated within about 20 minutes of starting to setup the machine, using the terminal. Nothing else running, just doing some basic text-file housekeeping chores. The cause of the freeze? I clicked the mouse in one of two terminal windows that were open. That's all, and the thing just stopped, no error, no response of any kind. I sure hope I can verify a fix, because if not, this puts me in the position of no-longer recommending Ubuntu to clients. Thanks to your post, I'm going to check out my top-suspect for the cause: fancy new bios features. Thanks again, but if this is still happening widespread, I think people need to keep the discussion active.

---

### Post by russjar on 2016-06-05
Hi everyone that's having the same issue as me.

I've got an MSI GP62 6QF Notebook and I to am having installation hangs just like everyone else. I've tried all the suggestions and still no joy! I did do something different however. I took an acronis image of Ubuntu 14.04 x64  running on a Dell Inspiron, and restored it on my MSI notebook and it boots in no worries, and seems to run fine but the network modules are missing and so I have no networking whatsoever. So if I could fix the networking issue I'd be on my way happily using my shiny new notebook with Ubuntu installed. 

I worked on this all day yesterday to great frustration. :mad::mad::mad:

In summary

New build = hangs with suggested fixes (see below) not working
Acronis Image Restore = No networking

So if anyone else has managed to get this happening I would be very happy to hear just how you got it working.



> **steven-wooding said:**
> OP here

I have posted the complete process that I followed to get it set up earlier on in this thread but I will post it again here for convenience. Here it is:

1. You HAVE to install ubuntu 15.04 64bit. Any other version simply does not work.
2. In the BIOS you have to disable the following: FastBoot, Intel Speedstep, SecureBoot
3. In the BIOS make sure that UEFI is enabled with CSM
4. When starting the Ubuntu installation you have to add the kernel option "libata.force=noncq". This is a MUST!
5. After the installation do a full update on Ubuntu. Then you can remove the kernel option "libata.force=noncq". Your SSD should perform faster now. But SpeedStep is still a problem. I have to keep it off.
6. I even re-enabled Fastboot and Secure in the BIOS and it still runs fine.

I have tried to install it inside a VM using VirtualBox as well as VMware but I never got it working properly, still freezes now and then. I just run it natively on the hardware.

---

### Post by xnovoa on 2016-07-04
Hi all,

I have instaled Linux Mint 18 (ubuntu 16.4) on a MSI GP72 6QE using this tuto:
[https://forum.ubuntu-fr.org/viewtopic.php?id=1976971](https://forum.ubuntu-fr.org/viewtopic.php?id=1976971)

Now all work for me

---

### Post by russjar on 2016-07-04
> **xnovoa said:**
> Hi all,

I have instaled Linux Mint 18 (ubuntu 16.4) on a MSI GP72 6QE using this tuto:
[https://forum.ubuntu-fr.org/viewtopic.php?id=1976971](https://forum.ubuntu-fr.org/viewtopic.php?id=1976971)

Now all work for me

Hi, 

It's in French, I can't read French. 

Cheers!

---

### Post by resaypi on 2016-09-05
Hi all.

So I changed the following on BIOS, which I've read from this forum:
- UEFI -> Enabled with CSM
- Virtualization Technology -> Disabled
- Fast Boot -> Disabled
- Speed Step -> Disabled
- PCI Latent Time -> 64 Clocks
- Secure Boot -> Disabled

I have GTX970m as GPU. I installed Ubuntu 16.04 without a problem. So far no random freezes.

My problem now is I can't find GTX970m in ubuntu. nvidia-detect returns none and lspci lists:
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5600 (rev 0a)
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)
Which is kind of weird.

So I want to use for my computations. Any fixes?

Best

---

### Post by xnovoa on 2016-10-10
Hi russjar,
Try google traslate:
[https://translate.google.es/translate?sl=fr&tl=en&js=y&prev=_t&hl=es&ie=UTF-8&u=https%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D1976971&edit-text=](https://translate.google.es/translate?sl=fr&tl=en&js=y&prev=_t&hl=es&ie=UTF-8&u=https%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D1976971&edit-text=)

---

