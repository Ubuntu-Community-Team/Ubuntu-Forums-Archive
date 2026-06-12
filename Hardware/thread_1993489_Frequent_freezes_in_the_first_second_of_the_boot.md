---
title: "Frequent freezes in the first second of the boot"
date: 2012-06-02
forum: Hardware
---

### Post by Photon89 on 2012-06-02
Hello community,

it's my first post here and as usual it's starting with a problem. Though I'm new to this forums, I've used Ubuntu for several years and now it's even running on the machines of my parents. In fact, the machine of my mother is what is causing the problem.

It started several months ago when I bought a "new" second-hand PC (Asrock-939 Dual-SATA motherboard, AMD Athlon 3700+ CPU) to replace the old socket A system that my mother was running before. I copied the Maverick install from the old PC to the new one and for about a month the system ran fine.

But then it was March 2012 and the support for Maverick was about to end, so I decided to update to Oneiric, since Pricise had not been released yet. I created a new partition and made a clean Oneiric install parallel to the old Maverick install (which turned out to be a good idea). For some weeks it ran fine but some day the problem appeared for the first time: It just stuck while booting and didn't react to anything. Using the fallback Grub entry I saw that it was stuck about 0.2 seconds after boot without a real error (see picture: [http://dl.dropbox.com/u/1507406/CIMG2938.JPG](http://dl.dropbox.com/u/1507406/CIMG2938.JPG)).

This problem began to appear more and more frequently and soon just about 1 of 10 boots succeeded. I decided to update to Precise which has been released by that time, but this didn't make any difference. First I thought, that it's a hardware problem, but this couldn't be the case since the old Maverick installation booted fine in 10 of 10 cases. 

So I made another partition and started to experiment. I tried several versions of Ubuntu beginning from Lucid and also some other distros and here's the result: It seems as if only Ubuntus with a 3.x kernel were affected by this problem. Maverick had a 2.6.x kernel and booted fine. Oneiric and Precise had 3.x kernels and had the boot problem. Lucid had the most interesting result: With its "native" 2.6.x kernel it booted fine, but with the backported 3.x kernel it failed to boot.

So I suspected that it's a kernel problem and tried some other distros. Mint 13 hat the same problem - not surprising as it heavily based on Ubuntu. But Open Suse surprised me: It had a 3.2.x kernel and still booted fine - at least I haven't observed a single freeze after about ten boots.

So it's Ubuntu's 3.x kernels that cause the problem. I'll try Debian to find out, whether it's some Ubuntu stuff that is causing the problem or already Debians kernels show this behaviour. But in any case: How do I further investigate the problem? Besides of the screenshot linked above I have absolutely no log output, since no logs are saved in the first quarter of the second of the boot. So I can't really report this as a bug. How do I get useful information about this problem?

Thanks in advance,
Photon

---

### Post by Photon89 on 2012-06-03
*bump* The issue is still unsolved. :)

---

