---
title: "Ryzen 7700X graphics support?"
date: 2022-12-06
forum: Hardware
---

### Post by mfleming on 2022-12-06
Hi,

I am trying to use Ubuntu 22.04.1 with the integrated graphics of a Ryzen 7700X. On installation, the only available resolution is 1024x768. I tried downloading and building the latest Radeon drivers from AMD's site but this didn't work. Maybe the 7700X is just too new and there isn't much Linux support yet? If so this would be OK, since I built this machine mostly to run Windows and can always add an Nvidia graphics card if necessary.  But if there is a solution it would be much appreciated.

Thank you,

Matthew Fleming

---

### Post by Autodave on 2022-12-06
I don't know anything about the Radeon, but IF you put nVidia in there, use the 525 driver and NOT the 525 OPEN one.  Assuming that your card will use the newest driver.

---

### Post by #&amp;thj^% on 2022-12-06
> **mfleming said:**
> Hi,

But if there is a solution it would be much appreciated.

Thank you,

Matthew Fleming
It will work but you'll have to add third-party sources or compile what you can:  "The main items to note are needing Linux 5.18 + Mesa 22 / linux-firmware.git" as of this month to make use of the Radeon iGPU under Linux.
Here's a good look at what's possible: [https://www.phoronix.com/review/amd-ryzen7-7700x](https://www.phoronix.com/review/amd-ryzen7-7700x)

---

### Post by TheFu on 2022-12-07
> **mfleming said:**
> Hi,

I am trying to use Ubuntu 22.04.1 with the integrated graphics of a Ryzen 7700X. On installation, the only available resolution is 1024x768. I tried downloading and building the latest Radeon drivers from AMD's site but this didn't work. Maybe the 7700X is just too new and there isn't much Linux support yet? If so this would be OK, since I built this machine mostly to run Windows and can always add an Nvidia graphics card if necessary.  But if there is a solution it would be much appreciated.


I don't know which kernel 22.04.1 comes with. that would be the first thing to be checked. Ensure it includes the AMD iGPU support you want.  If it doesn't,  you might have better luck installing 22.10 for now, then after the 22.04.2 HWE release, dropping back to that release so you get back on an LTS version and aren't trapped into full OS installs every 6 months until 24.04 is released. That's the next LTS - over a year away.

When it comes to GPU drivers, stick with the ones provided by Canonical and in the kernel.  Linux isn't MS-Windows.

That Ryzen 7xxx CPU is the definition of bleeding edge.  You'll need a fairly recent kernel, likely NOT the default ones shipped with any LTS Ubuntu  release, until they get to the minimal level.  You can run one of the "mainline" kernels, just be certain to know it isn't tested by Canonical or patched by them.  Another option is to load a different distro that uses newer kernels.  I've seen some people using 6.0.x kernels and these aren't kernel junkies, so the distro they were running installed that version.

When I was running 18.04 with a Ryzen 5600G, the default kernels didn't include the AMD drivers needed for anything but basic support.  I wasn't prepared for running a newer release, so I installed the "mainline" 5.10.x kernel into 18.04 and ran that for a few months. Once a fresh install was done on that system with 20.04, it had the 5.15.x kernel and all the iGPU magic "just worked" like magic thanks to the linux-image-generic-hwe-20.04 kernel package.

LTT did a comparison of a few Ryzen 5xxx and Ryzen 7xxx series of CPUs that might be useful for people to check out.  [https://youtu.be/_vLq2PjmIx0](https://youtu.be/_vLq2PjmIx0)

---

### Post by mfleming on 2022-12-07
Thanks very much for all this good info. As mentioned, I bought this machine primarily to run Windows. In my business I have a critical server currently running Ubuntu 22.04.1 LTS, and then other machines I use to develop software for the server, also running Ubuntu 22.04.1. It would be nice but is not really necessary for this machine also to be usable for development, but for that it would pretty much have to run the same distro as the server. Given what you all have explained I think I'll leave Linux off it for now. I expect ultimately to repurpose it for more serious stuff, and for that I'll probably want an Nvidia card anyway. Thanks again.

---

### Post by TheFu on 2022-12-07
If you want to run a different OS, the easiest way is to use a virtual machine.  Only gamers bother to dual boot ... them and testers.
Normal people who need multiple OSes, use virtual machines.  Heck, I switch my main desktop to a VM around 2010 and had been using VMs for over a decade before that, mainly for testing different language installations of commercial software.

But since around 2005, servers running on a VM have been the mandated standard at enterprise companies and desktop-on-desktop VMs have become really great across all VM technology since around 2016 (except gaming).  For coding and normal office apps, virtual desktops were deployed inside enterprises since around 2007 for security reasons.  Heck, I deployed VDI servers into an on-shore data center in 2007 that were used by developers half-a-world away.  I found it odd how things that would take 20 people here always seemed to be estimated at 60 people there AND that the average cost of each person was 1/3rd, so effectively, we were paying the same, for less efficiency, language barriers, and middle of the night meetings.  Only upper management believes they can make those numbers work. After 2.5 yrs of trying, the project was cancelled, so it seems they couldn't actually make the numbers work.  I can't say how much money had been spent, but it was more than small nations spend for all their Govt IT in a year.

Anyway, use VMs for servers and when you need desktops running specialized software or even just a little different environment.  VMs decouple the OS and applications from the hardware. I have a few VMs that have been moved between 4 different physical hardware systems over the decades.  Those applications don't know they are running on a hot Ryzen.  To them, it looks like a single core with 1GB of RAM.  If that's all they need, that's all they get.

---

### Post by #&amp;thj^% on 2022-12-07
I had my hands on just the chip a few days ago, and with what I mentioned and the added info from TheFu, it preformed super nice with a little elbow grease.
I sent it to other Devs for their additions for Linux. I'm not sure you'll have to wait any longer than a month or so before Linux Desktops are workable on this little beast.
I have Nvidia Cards that I also used with it and all worked great, and as mentioned the Nvidia 525 driver was the smoothest offering ATM.
Enjoy

---

### Post by mfleming on 2022-12-07
Thanks very much. As mentioned, there's no great rush from my perspective, but your efforts are appreciated. The chip itself seems to work great. I have it in a Gigabyte B650M Aorus Elite AX mobo, and am quite happy with that as well.

---

### Post by Yellow Pasque on 2022-12-07
> **mfleming said:**
> In my business I have a critical server currently running Ubuntu 22.04.1 LTS, and then other machines I use to develop software for the server, also running Ubuntu 22.04.1. It would be nice but is not really necessary for this machine also to be usable for development, but for that it would pretty much have to run the same distro as the server. 

You could use Ubuntu mainline kernels until 22.04.2 releases. It would require more manual intervention than the standard repo kernel, but something like this could help:
[https://www.linuxcapable.com/how-to-install-linux-mainline-kernel-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-linux-mainline-kernel-on-ubuntu-22-04-lts/)

---

