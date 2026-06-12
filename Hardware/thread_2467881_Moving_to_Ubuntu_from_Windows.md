---
title: "Moving to Ubuntu from Windows"
date: 2021-10-11
forum: Hardware
---

### Post by acm2021 on 2021-10-11
Hi,

After many years of windows (too many), I've decided to move my PC to Linux.

Main uses will be programming, gaming (with steamplay and some retro like dosbox, emulators, etc), some virtualization if possible and general use, like browsing, movies, office, etc.
I would like to get some feedback from more experienced users whether if my currently hardware setup would face some incompatibility/not supported problems and some replacement software I may need.

I made some research and I can see that some brands do not officially support linux, like razer for example, but they may work out of the box or have some other software.
I'm also thinking on using Ubuntu, but please feel free to suggest other distro, if you think it will be better.

Thank you in advance for your help.

Hardware
```
ATX Gigabyte Z390 Aorus Master
Intel Core i7-9700K Octa-Core 3.6GHz c/ Turbo 4.9GHz 12MB Skt1151
Water Cooler CPU Corsair Hydro Series H115i PRO RGB
Seasonic PRIME Ultra 850W Gold Full Modular
RAM G.SKILL Trident Z RGB 16GB (2x8GB) DDR4-3000MHz CL16
Samsung SSD EVI 1B
NVIDIA GeForce RTX 2060
Monitor DELL U2515H (Dual)
Razer Deathadder V2
Redgradon keyboard - moving soon to a razer one
xbox gamepad (wired)
Headset Razer Blackshark V2 X 7.1
```

Software
```
nvidia software (geForce experience?)
water cooler software (iCue?)
Gigabyte stuff for the motherboard (rgb fusion, etc)
Razer software (7.1, synapse, chroma, etc)
Office (I think libreoffice should be a good replacement?)
Virtualization windows 10 (virtualbox?)
```

---

### Post by tea for one on 2021-10-11
Are you familiar with Try Ubuntu in a live session?

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

Exploring a live Ubuntu session using your own hardware should help to answer some of your questions.

---

### Post by acm2021 on 2021-10-11
> **tea for one said:**
> Are you familiar with Try Ubuntu in a live session?

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

Exploring a live Ubuntu session using your own hardware should help to answer some of your questions.

I was not.

I'll give it a go. 

Thank you.

---

### Post by TheFu on 2021-10-11
Spend 5 minutes and create a bootable Ubuntu USB Flash install drive.  When it boots, choose the "Try Ubuntu" choice and play with it for an hour. See what works and what doesn't.  It won't write to any connected storage, unless you specifically access that storage and write to it.

That will be much more authoritative than anyone here trying to answer questions could do.

In short, try it out.

BTW, you'll want to ensure the firmware on the SSD is current. Some Samsung SSDs have issues, though I'd not seen it with my SATA Samsung, I will be building a new box this week and have a Samsung NVMe that you'll bet I flash with current firmware before installing.

The Try Ubuntu won't let you use nvidia proprietary drivers, but the F/LOSS drivers should be fine for testing out everything else. If you decide to go with some official flavor of Ubuntu (xubuntu/kubuntu/Lubuntu/Ubuntu-Mate/ or one of the others, then post install you can have the OS install the proprietary drivers for all known hardware using 
**sudo ubuntu-drivers autoinstall**
In Ubuntu, never get software directly from nvidia. Always stick with the version provided through Ubuntu's tools. IF you don't, you'll learn more about incompatibilities than you really wish to know.  I have a 1030 GT and have been buying nvidia GPUs for about 20 yrs.

For virtualization, there are many choices.  Virtualbox is good for a first use, but you'll want a better, lighter, hypervisor in a few months probably.  There are a number of tools to make that easy and the interfaces are very similar to what Virtualbox provides, so it won't be a huge change for more capable, more stable, lighter, but faster, hypervisors.  We each have a different need for 

You can forget the RGB software btw. None of that works under Linux.
You can forget about most specialized driver tools as well. Those are only made for MS-Windows. In linux, we can control driver settings, but often that means toggling things without using a GUI.
No clue about water cooling software. I've been using the stock coolers provided with the CPU for a decade. They work fine.
Whether MS-Office and LibreOffice are good enough or not is personal.  Download LibreOffice for Windows and try it out now. See if it is fine or not.

Gigabyte is known for being hostile towards Linux, so don't expect much support, if any, from them.

As a new Linux user, I think your expectations and Windows-centric background may be a problem for your happiness.  Expect little, then be happy when things work.
Also, as a new user, learn that newer isn't better.  You should load a 20.04 version of *buntu.  That is an LTS.  When 22.04 LTS is released in late April, run it under a VM for 6 months before deciding if you want to upgrade from 20.04 to it. I'm just now migrating my 18.04 (a prior LTS) to 20.04 as they fix some important bugs in it.  

***_New is the enemy of stable._***

If you plan to buy hardware, look up the Linux support, in depth, before buying.  You'll find that randomly buying stuff will end in disappointment and returns.  Even if the box says "Linux Supported" on the outside in huge letters, you don't know if that support is current or from 4 yrs ago.  I got burned with this buying a HW-RAID card - yes, it provided drivers for a 3 yr old kernel, but not any new kernel. When buying add-on PCIe devices, you'll want to read the fine print and learn about the actual chips used inside.  Don't expect any driver disk or even a driver download from the vendor.

Oh, and hope you don't learn the hard way about realtek ethernet and wifi issues. Hopefully, everything will "just work", but don't be surprised if some strange LAN chip isn't supported automatically.  I go out of my way to get Intel GigE NICs in all my systems, because the drivers are excellent and "just work."  Saving $10 and getting a lesser NIC that has problems (Marvell, Realtek) just isn't worth my frustration.  When it comes to wifi, there are many more challenges - so I've heard.  I don't use wifi on computers at home. Even my laptop that doesn't have a built-in NIC uses a USB3-to-GigE converter to avoid using wifi.  The wifi works, but it isn't fast and we all know that no wifi is actually secure, right?

---

### Post by TheFu on 2021-10-11
> **acm2021 said:**
> I was not.

I'll give it a go. 

Thank you.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview) has a guide for Windows.  There are links in it for MacOS and Linux.  

With any Unix, it is basically a 
```
sudo cp {/path/to/ubuntu.iso} /dev/{whole device name, not partition}
```
This command can work for ANY Unix-like OS. No special tool(s) needed, like most of the "how-to" guides suggest.  Oddly, it doesn't appear that Windows knows how to copy bits from A--->B unmolested, so for that OS, a tool is needed - rufus and etcher are popular.  Or just follow the instructions in the link above.

---

### Post by acm2021 on 2021-10-12
Ok so first impressions.

Is live session persistent? I've rebooted and lost all previous configuration meh. Anyway..

Everything seemed to work OTB, but I had a couple of problems.

 Could only get sound to work from the front panel where I have my headset connected, back panel with columns had no sound. Even if disconnected the headset, no sound at all.
Tested Minecraft because of the gpu and while using the correct gpu, I had low framerates. tried to mess with nvidia drivers but they do not work correctly in live session (nvidia app window was always empty). Perhaps the low fps was because of being played from the usb, not sure about it.
Installed steam (had a weird font problem that I solved), and installed duke nukem 3d to try and get something out of it, but couldn't Have to try again.

Will try again today to check if I can get things to work better.

Thank you for the help

---

### Post by tea for one on 2021-10-12
Live Ubuntu sessions are very informative, are they not? ;)
Many Windows users have never experienced this because it is not possible to Try Windows in a similar way. 

Live session is generally not persistent (depending on the utility used).
However, if you use the Windows application Rufus, there is an option for persistence.
Please see image attached.

Also, there is a very good application for Ubuntu called [COLOR="#0000FF"]mkusb[/COLOR]
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Sound problems are tricky to solve but the first thing to do is install [COLOR="#0000FF"]pulseaudio[/COLOR] and [COLOR="#0000FF"]pavucontrol[/COLOR]
This will give you more options for sound.

---

### Post by yancek on 2021-10-12
>  Is live session persistent? 

I'm not aware of any Linux iso being persistent on download.  You can use software such as those suggested in post 7 above to make an iso installed to a USB persistent.  I don't think persistence will allow changing any system files such as fstab.  At least, that has been my experience.  For Ubuntu, I would recommend mkusb but that's my personal opinion based on my experience.,  I'd read the information on the mkusb site to see if it fits your needs.

---

### Post by TheFu on 2021-10-12
> **acm2021 said:**
> Ok so first impressions.

Is live session persistent? I've rebooted and lost all previous configuration meh. Anyway..

Everything seemed to work OTB, but I had a couple of problems.

 Could only get sound to work from the front panel where I have my headset connected, back panel with columns had no sound. Even if disconnected the headset, no sound at all.
Tested Minecraft because of the gpu and while using the correct gpu, I had low framerates. tried to mess with nvidia drivers but they do not work correctly in live session (nvidia app window was always empty). Perhaps the low fps was because of being played from the usb, not sure about it.
Installed steam (had a weird font problem that I solved), and installed duke nukem 3d to try and get something out of it, but couldn't Have to try again.

Will try again today to check if I can get things to work better.

Thank you for the help

I think your experience is typical.  Most things work, but a few do not - not without a little tweaking.  nvidia drivers aren't installed as part of a live session. Most driver-level stuff doesn't actually need a reboot, but GPU drivers do ... and with a non-persistent OS, even if you say to install the drivers, they cannot be used until there is a reboot ... but it isn't persistent, so the drivers would need to be installed again.  Forget about the GPU until you actually do an install. It isn't worth your time.

People don't choose Linux for gaming. If that is your goal. Stay with Windows.  For almost anything else, it is a fine platform and for server development and deployment, it is THE only platform.

Moving from Windows to Linux can be very painful. About 80% of what you've learned in Windows just doesn't apply and will get you into massive trouble under Linux.  Things may "appeal" to be similar, but they are not. Under the covers, they are architect-ed in a very different way. The smoothest transitions happen when someone begins using the same software they will use on Linux on Windows for a few months first.  Then they migrate into a virtual machine install of Linux while still running Windows and slowly use Windows less and less, while using the Linux VM more and more.  The VM presents fake hardware to the OS and the hypervisor presents the most well-supported hardware there is to the guest VM - linux in your case.  Run that for a few months - at least.  I ran that way for a few years even after I'd been administrating Unix and Linux systems for over a decade.  The Linux desktop is a different animal.  Learn to use the hundreds of tiny tools in all Unix systems to create exactly what you want when they are chained together. This is very different from the Windows-way of thinking where people look for another function to an existing tool.  This link tries to explain the difference: [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

Eventually, you'll find booting Windows, then booting the VM a hassle. That's when you'll know it is time to wipe Windows and boot directly into Linux as the main OS.  You can put Windows into a VM for emergency use or for programs that refuse to run under Linux.  I'm down to about 3 tools that will never run in Linux and replacements just aren't there.  I've replaced about 20 often used programs and happily use the Linux or cross-platform versions.  I first started using StarOffice in 1995, for example.  StarOffice is what OpenOffice and LibreOffice started as.  In fact, you can look at the real program names "soffice" - staroffice.

If you don't have time for a measured migration and a willing to live with the pain - there will be pain, frustration - months of it - then just install the distro you think best and pull out your thesaurus so more lively words can become replacements for the words you'd normally use.  Heck, try to get a thesaurus working on Linux that isn't a website. Linux has built-in spell checkers.  Most Linux "desktop" users don't know this.  It would do them good to learn about aspell and ispell and how those tools work.

There are some great tools that handle multi-booting AND persistence.  I can't recall the name now, but in my LUG (Linux Users Group). Found it ... [https://www.ventoy.net/](https://www.ventoy.net/) .  Adding a new distro is as simple as dropping the ISO file in a specific directory.  [https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html) has a step-by-step guide. I've not used it, but a number of people who I respect do.  

For me, flash storage is really only for physical installs or physical system emergencies which just don't happen all that often.  About once a year or every other year is it.  Even when swapping systems (MB and CPU), I tend to just move storage into the new equipment and go from there.  
My NAS box originally started out as a mediacenter with a single 4TB HDD on an AMD E-350 APU (400 passmarks). Now it has ~32TB connected and has a completely different MB, CPU (Pentium G3258), and case.  Either today or later this week, it will be moved to a Ryzen 5000 MB+CPU.  The OS has been upgraded over all these years, not reinstalled from scratch.  It has an internal and external disk array. The extra-wide case is from 1999.  Going from 2000 passmarks to 20K passmarks will be nice. No added power use and I get to retire a different 11 yr old core i5 system too, so saving 130W will be nice. I should see that in the monthly power bills. My system count expands and contracts over the years multiple times. I'm trying to get to 2 main systems (failover) and 1 laptop. The new Ryzen will match a 3 yr old ryzen nicely, though it is ~50% faster.

Of course, these won't see Windows ... except inside a VM. The Windows VM won't know when it gets moved since to it, nothing will have changed. The VM hardware won't change.

---

