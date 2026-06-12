---
title: "Updates: Linux/UNIX on Acer Aspire 4530 with 9100m chipset"
date: 2008-08-27
forum: Hardware
---

### Post by Caveira2099 on 2008-08-27
Hi folks!

I am working on to figure out how to make a linux instalation on my Acer Aspire 4530 with nVidia 9100m chipset. So far, my experience is:

1) Every linux distro I've tried doesn't even boot... Checking on the startup log messages I could figure out that the main reason for the failure is when the system tries to load SATA and USB modules.

2) I tried OpenSolaris 2008.5 and it booted nicely! Of course it didn't have the latest nvidia drivers, and for this reason many features were not loaded. But I got the system up and running!

Considering that the solaris kernel included is older than the linux kernels I've tried,
 my first conclusion is that there can be some driver lack, but also there's some tricks to be done in the boot scripts. I am currently involved with Scientific Linux, but if I can make it work under SL, other newer distros like Ubuntu will surely follow on.

If there's anyone out there willing to give a try with OpenSolaris, please let us know.

Cheers,

---

### Post by kreyz on 2008-08-28
> **Caveira2099 said:**
> Hi folks!

I am working on to figure out how to make a linux instalation on my Acer Aspire 4530 with nVidia 9100m chipset. So far, my experience is:

1) Every linux distro I've tried doesn't even boot... Checking on the startup log messages I could figure out that the main reason for the failure is when the system tries to load SATA and USB modules.

2) I tried OpenSolaris 2008.5 and it booted nicely! Of course it didn't have the latest nvidia drivers, and for this reason many features were not loaded. But I got the system up and running!

Considering that the solaris kernel included is older than the linux kernels I've tried,
 my first conclusion is that there can be some driver lack, but also there's some tricks to be done in the boot scripts. I am currently involved with Scientific Linux, but if I can make it work under SL, other newer distros like Ubuntu will surely follow on.

If there's anyone out there willing to give a try with OpenSolaris, please let us know.

Cheers,

Actually I'm using Ubuntu Ultimate 1.8 32 bit in Acer 4530, it's going fine.. except for one more glitch, I still can't make the sound to work.. so it become a silent lappie.. :)

---

### Post by Caveira2099 on 2008-08-28
Hmm interesting... Ubuntu 8.04 didn't boot here... I'll check that.

By the way, can you post which is the nForce/nVidia driver version you use?

---

### Post by kreyz on 2008-08-28
> **Caveira2099 said:**
> Hmm interesting... Ubuntu 8.04 didn't boot here... I'll check that.

By the way, can you post which is the nForce/nVidia driver version you use?

Did you tried using F6 and type "all_generic_ide floppy=off irqpoll" at the start screen?
I'm using the latest version, 173.14.12 and it's working fine...

---

### Post by Caveira2099 on 2008-08-28
Dude, I really don't know exactly what is going on... In the specific case of ubuntu, it gives me a kernel panic during the boot (screen brightness goes down and the caps lock led starts blinking...).

I have just tried your suggestion and still no go. I am trying Ubuntu 8.04 AMD64 live cd.

Other distros, the same... I am still lost, but I hope to find something in the next couple of days. My acer is 4530-5267.

---

### Post by Caveira2099 on 2008-08-31
Ok, time for updates.

I tried Ultimate 1.9 with and without these boot parameters and still no go. I won't boot.

Actually, no distro I have tried boots. All of them are hanging while loading the sata modules.

Maybe it's a (lack of) driver problem or something else I don't know.

Please, any help here is welcome! Or I'll try to switch to solaris.....

---

### Post by gootoo on 2008-09-02
Same issue my one.
Some body said after some days the there are many solutions, for this laptop too new.

---

### Post by major_alliance on 2008-09-03
i have try those solutions mention all over the internet regarding this one,

so far there is one distro that can boot properly aspire 4530

which is Mandriva one 2008 but i just install it for fun and the only draw back is the driver for display, not yet available during that time mean early  august.

the other one other than Mandriva that did successful install and run is OpenSuSe 11 but you need to switch between AHCI and IDE mode in order to sucessfully to boot into it but later i find it failed to boot and enter a kernel panic due.

i'm also waiting to get a hand into the final version of Intrepid Ibex which might have resolved the kernel panic isssues.

since this is a laptop using Nvidia Chipsets and Gforce 9series which maybe too new before nvidia release the driver for linux users.

---

### Post by Caveira2099 on 2008-09-03
Hi all,

Dogmeat has given precious findings: [http://ubuntuforums.org/showthread.php?p=5722249#post5722249](http://ubuntuforums.org/showthread.php?p=5722249#post5722249)

Follow that thread for news on this laptop.

Cheers

---

### Post by gootoo on 2008-09-23
SuSE 11 can work with this ACER model.
Display card works fine.
Enable SATA please add kernel parameter pci=nomsi, then can boot and install.

Also have question with Ubuntu installation.
I want install 64bit Ubuntu710 for my CAx software NX5. but till now still cannot start.

---

### Post by 3rag0n on 2008-10-07
> **gootoo said:**
> SuSE 11 can work with this ACER model.
Display card works fine.
Enable SATA please add kernel parameter pci=nomsi, then can boot and install.

Also have question with Ubuntu installation.
I want install 64bit Ubuntu710 for my CAx software NX5. but till now still cannot start.

Why do you want to install 7.10 ?
I use Hardy 8.04 on the same laptop and it works awesome ( but still has no sound).

So far, i have tried the following distros on this machine :
OpenSuSe 11.0
Ubuntu 8.04 Hardy
Mandriva 2008.one

And all run well, except for the common sound problem.

I believe that this sound problem (and wireless too ) will be solved if you update the kernel to 2.6.27 version.

Or wait for the soon-to-come Intrepid Ibex ( 8.10 ). It has this latest kernel. And if you cant wait, it's beta is available.

---

### Post by cid_leonhart on 2008-10-08
> **kreyz said:**
> Did you tried using F6 and type "all_generic_ide floppy=off irqpoll" at the start screen?
I'm using the latest version, 173.14.12 and it's working fine...

i'm following your suggestion to add "all_generic_ide floppy=off irqpoll" in boot option, and the installation progress complete.

the problem is after installation. after grub loading, it's stop booting the OS when detecting sata... how should i fix this... any one can help??

*sorry if my english so bad

---

### Post by gootoo on 2008-10-24
> **3rag0n said:**
> Why do you want to install 7.10 ?
I use Hardy 8.04 on the same laptop and it works awesome ( but still has no sound).

So far, i have tried the following distros on this machine :
OpenSuSe 11.0
Ubuntu 8.04 Hardy
Mandriva 2008.one

And all run well, except for the common sound problem.

I believe that this sound problem (and wireless too ) will be solved if you update the kernel to 2.6.27 version.

Or wait for the soon-to-come Intrepid Ibex ( 8.10 ). It has this latest kernel. And if you cant wait, it's beta is available.

are the above distros 64bit? if yes, it is kind if you can post your boot parameters.

64bit ubuntu810 RC can not boot PC my side.
THank you.

---

### Post by cid_leonhart on 2008-11-05
Just downloaded Interpid Ibex (x86 64) Final Release, but still can't boot live cd... cdrom led is flashing but no response! Do i have to use 32bit version of this release on this laptop...

---

### Post by 3rag0n on 2008-11-09
uh-oh.
I tried the latest and greatest ( :( ??? ) intrepid ibex (64-bit) on my 4530 and when i select "try ubuntu", the orange progress indicator stops at a point which is 1/5th of the full length.

Upon selecting "install ubuntu", the laptop starts beeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee:confused:ping like mad. Like its about to die. And I'm not sure whether the sound's coming only from the speakers... It's like a system beep(?).

Havent tried wubi for this yet.

---

### Post by Caveira2099 on 2008-11-09
Hi 3rag0n, you should follow this thread instead: [http://ubuntuforums.org/showthread.php?p=5722249#post5722249](http://ubuntuforums.org/showthread.php?p=5722249#post5722249)

I've found that for the moment, only mandriva 2009 and opensuse 11.1 beta4 run well on this laptop. You should try them as well.

The blinking and sounds are normal, they're just a hint of a kernel panic during the boot process.

Cheers,

---

### Post by cid_leonhart on 2008-11-09
Just install the 32bit version.... now it's working fine VGA, Sound, Wireless (ndiswrapper), everything except Audio Front Panel...

I already use the usual way to fix it but the internal speaker not muted and the headphone don't seems to sound anything...

```

# sudo apt-get install linux-backports-modules-2.6.27-7-generic
# sudo tee -a /etc/modprobe.d/alsa-base | echo "option snd-hda-intel mode=acer"
# sudo init 6


```

late on I found up that this laptop using snd-hda-nvidia... thanks before...

---

### Post by 3rag0n on 2008-11-14
> **Caveira2099 said:**
> Hi 3rag0n, you should follow this thread instead: [http://ubuntuforums.org/showthread.php?p=5722249#post5722249](http://ubuntuforums.org/showthread.php?p=5722249#post5722249)

I've found that for the moment, only mandriva 2009 and opensuse 11.1 beta4 run well on this laptop. You should try them as well.

The blinking and sounds are normal, they're just a hint of a kernel panic during the boot process.

Cheers,

Yeah right.... mdv 2009.0 works great outta the box...(32 bit)
Using it now... removed vista.. (which was P!r/\t3d anyway)... [every1 in india has a "n0n-genu!ne" vista "exp3rience", no one is foolish enough to buy vindoze which costs a fortune]

I guess i'll try openSuse 11.1 since u say it works (64-bit, right?)
I want to stop using mandriva and install opensuse 11.1 because the One edition is not available as amd64 and ive always loved suse anyway..
thanks for the info friend!

---

### Post by LashSilence83 on 2008-11-28
I just got a AS4530 and installed 32 bit intrepid. Through some truly frustrating trial and error sessions, I found that running the 32 bit xp driver through ndiswrapper seems to be the easiest way to get wireless working. The remaining issues I'm having are the webcam and suspend/hibernate. I'm basically just trying to connect with others who have this laptop and are running linux on it. Sorry if I should have started a new thread for this... wasn't sure what to do.

---

### Post by aravind_svu on 2009-03-29
Good news guys,
     I have successfuly installed a 64-bit version of linux on my ACER ASPIRE 4530 with AMD Athlon X2, NVIDIA GEFORCE 9100M G

We all know that Ubuntu Intrepid Ibex 8.10 32-bit boots on this machine, with most of the drivers out of box. But Ubuntu 8.10 64-bit couldn't even boot.

Then I tried Jaunty Jackalope 64-bit PC Install/Live Ubuntu 9.04 DVD from the following link
[http://cdimage.ubuntu.com/dvd/current/]("http://cdimage.ubuntu.com/dvd/current/")

It works great, with everything out of box. However with my installation the package manager did not receive the uploads automatically, so I had to open the pacakage manager and click on reload. After doing this, opening system-> administration -> hardware devices would show up the required drivers. 

All the drivers including, card reader, bluetooth, WLAN, volume wheel, sound etc works alright. For graphics I installed NVIDIA Proprietary driver, but you can get open driver 177 & 180 versions via the package manager.


I am a novice with Linux and installing linux had been bothering me ever since I got this laptop (Aug 2008). Now finally I got a 64-bit linux with out of box support. Cheers :guitar:

---

### Post by LashSilence83 on 2009-03-30
aravind_svu , 

how did you do that? As soon as I read your post, I downloaded and burned the image but none of the options at the boot menu produce anything but a system halt after a lot of squashfs errors. I even ran through several attempts with various boot options and still nothing. What am I doing wrong?

---

### Post by aravind_svu on 2009-04-01
> **LashSilence83 said:**
> aravind_svu , 

how did you do that? As soon as I read your post, I downloaded and burned the image but none of the options at the boot menu produce anything but a system halt after a lot of squashfs errors. I even ran through several attempts with various boot options and still nothing. What am I doing wrong?

Thats strange. I am a novice when it comes to Linux.. So you can pretty much understand what I could have done anything techie there..

All I did was to download Ubuntu 9.04 AMD64 (Jaunty Jackalope) from the link I mentioned in my original post. It was 4.3GB DVD image. I burnt it onto DVD RW disk and boot from it. Heres my computer configuration

ACER ASPIRE 4530
AMD Athlon 64 X2 Dual core processor
NVIDIA GEFORCE 9100M Graphics (512 MB)
SATA 160GB HDD set in SATA Mode as AHCI in BIOS
 This is the result of lcpci on my laptop

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation Device 0ad5 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:15.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9100M G (rev a2)
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)



I just listed it because some of the ACER ASPIRE 4530 are AMD Turion version and I dont know their configuration.


Just to mention, Please do a disk check, because sometimes the disk could be problemic. When I tried to install UBuntu 8.10 32-bit at first I never could get it boot. I wasted a lot of time only to find that my disk has problem. Then I got a new DVD RW disk and burnt the image at 4x and this time I was able to run the live cd session successfuly, which I couldnt do before. I am sure if I tried I would have been able to install on my harddisk as well. But UBuntu 8.10 64-bit version couldn't even boot. Then I tried Ubuntu 9.04 jaunty jackalope. It worked excellent out of the box.

Always do the disk check.

I even have my laptop with dual boot option
1. WIndows VISTA 32 (such a waste of money :cry:)
2. Ubuntu 9.10 64 bit (created three partitions out of the free space I kept for one fine-day when I would be able to install Linux ever since I baught this laptop, The partitions are swap, /boot & '/' while installing)


Although the following are the issues I am currently facing

1. I cant play audio through Headphones. 
2. Openoffice.org do not have a 64-bit installation binary yet (but Ubuntu 9.04 comes wth preinstalled openoffice.
3. NVIDIA proprietary drivers gave a bit of problem. I had to reinstall it to fix. It happened couple of times, but its pretty stable. I just used the NVIDIA installer instead of nasty methods described in internet, which only advanced users can understand. They are worth a try though.
4. Suspend could never resume. Whole system crashes, when you suspend  your computer session (by closing the lid).

If you are getting errors like Memory I/O read/write errors, while you are trying to boot, it probably means that your media is not proper. Try checking the disk, from the ubuntu boot menu.

Hope this info helps. Again I am a beginner with the wonderful world of linux, so I might not have been able to sound too technical. My Appologies.

Cheers

---

### Post by 3rag0n on 2009-04-08
> **aravind_svu said:**
> Good news guys,
     I have successfuly installed a 64-bit version of linux on my ACER ASPIRE 4530 with AMD Athlon X2, NVIDIA GEFORCE 9100M G

We all know that Ubuntu Intrepid Ibex 8.10 32-bit boots on this machine, with most of the drivers out of box. But Ubuntu 8.10 64-bit couldn't even boot.

Then I tried Jaunty Jackalope 64-bit PC Install/Live Ubuntu 9.04 DVD from the following link
[http://cdimage.ubuntu.com/dvd/current/]("http://cdimage.ubuntu.com/dvd/current/")

It works great, with everything out of box. However with my installation the package manager did not receive the uploads automatically, so I had to open the pacakage manager and click on reload. After doing this, opening system-> administration -> hardware devices would show up the required drivers. 

All the drivers including, card reader, bluetooth, WLAN, volume wheel, sound etc works alright. For graphics I installed NVIDIA Proprietary driver, but you can get open driver 177 & 180 versions via the package manager.


I am a novice with Linux and installing linux had been bothering me ever since I got this laptop (Aug 2008). Now finally I got a 64-bit linux with out of box support. Cheers :guitar:



Hi aravind... thanks fr the info... btw can u tell me about the headphone problem thats been plaguing intrepid users on this lappie.... does the headphone work properly in jaunty now???

Also... try openSuSe 11.1 64-bit.. not a bad one.. superb polish.

---

