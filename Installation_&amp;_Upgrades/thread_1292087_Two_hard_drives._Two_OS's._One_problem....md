---
title: "Two hard drives. Two OS's. One problem..."
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by TonyChaos on 2009-10-15
So I am just getting into the Ubuntu scene after a long wait on my computer to be put together. I want to have Windows XP Pro on my larger drive, being a 500GB, and Ubuntu on my smaller drive, being 320GB.

I tried to figure it out myself, but no no avail. The first time I tried I only allocated 250Mb for Ubuntu after the install. I tried again but this time allocated 120GB for Ubuntu after the installation. I put both the Windows OS and Ubuntu on the same hard drive before I realized I had two drives and could put one on each. I'd like to have a prompt come up asking which OS to load as well.

Is there anyone that can walk me through how to do this? I need Windows on the computer for work, but I want to tinker with Ubuntu.

---

### Post by az on 2009-10-15
Install Windows first.

Then install Ubuntu.  At the partitioning stage, you will be shown different scenarios.  Chose to use the entire disk of the second drive (I'm guessing it will be called /dev/sdb). 

Proceed normally.  It will detect your existing Windows install.  By default, it will install a bootloader on the first hard drive and you will be shown the grub menu every time you boot - you will be able to pick between OSes at boot time.

---

### Post by TonyChaos on 2009-10-15
Thank you! It went without a hitch. The only thing now is that my monitor isn't detected. I can only go up to 800x600 (4.3).

Is there someplace I could go for drivers that would help me out with this?

---

### Post by rob-ward on 2009-10-16
what graphics card are you using?

---

### Post by TonyChaos on 2009-10-16
It's an nVidia GeForce 6150 LE. I tried to download the X-org 173 driver but it keeps telling me that I need to get rid of the other driver used for my monitor and use the Synaptic package manager. I just can't seem to figure out what I need to get rid of...:(

---

### Post by TonyChaos on 2009-10-16
After a bit of tinkering I got it to change resolution now. 

To those of you that are having this problem as well: I had to boot into into safe mode and have it attempt to repair the monitor resolution. It was the last option in safe mode, for those of you who are having problems like I had. It fixed it and my monitor still is unrecognizable, but the resolution can be set higher, which is all I really care about.

---

