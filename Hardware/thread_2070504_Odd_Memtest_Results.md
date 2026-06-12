---
title: "Odd Memtest Results"
date: 2012-10-12
forum: Hardware
---

### Post by sonypete on 2012-10-12
I'm currently running 12.10 (Previously 12.04 for a few weeks)
CPU: AMD A8-5600K (New FM2 Trinity APU)

Long Story short, whe I run the built in Memtest86+ that you access form the grub menu, I consistently get 10,0000+ errors by the time I reach 50%.  *BUT* if I boot off a memtest cd or any other live-cd with memtest built in I do not get any errors.

I even tested the same ram in my main gaming rig and get no errors. I took the known-good ram out of the gaming rig and stuck it in my linux box and it would shows errors using hte built in memtest in the grub menu. It would not error out if I booted off a live-cd to test.

Has anyone experienced this anomaly? I cannot find any other posts about anyone else experiencing this issue. This is for a server I'm setting up so a bit worried about these results.

- Pete

P.S. I know the new Beta memtest86+ 5.00b added support for Trinity AMD CPU's but still doesn't explain how the same version (4.20) gives me different results.

---

### Post by afmprog on 2012-10-14
I am running on a Toshiba Satellite L755 with a i5-2450m 2.5GHz processor. I have a multi boot system using Windows 7, Xubuntu 12.04 LTS and Xubuntu 12.10 beta. The grub menu is from the 12.10 beta install.
  Like you I get thousands of errors when I run memtest86 version 4.20 from the grub menu. When I run it from a bootable cd there are no errors. Therefore I assume the developers are having problrms with the /etc/grub.d configuration scripts they are using to generate the grub boot menu.
  All 3 of my operating systems work fine, so if I need to run memtest I will just boot it from my memtest cd.

---

### Post by ahallubuntu on 2012-10-14
The older versions of Memtest may have bugs related to the newer chipsets.

---

### Post by sonypete on 2012-10-17
afmprog,
  Thanks for your scenario description, that makes me feel much better about what i'm seeing.

ahallubuntu,
    Yea, I kind of want to figure out how to load the binaries for the newest version of memtest86+ into grub2 and re-run to see if that eliminates the issue i'm facing.


- Pete

---

### Post by vtornado on 2012-10-26
Note that I just reported probably the same issue on the memtest86+ forums:

[http://forum.canardpc.com/threads/72840-Ubuntu-12.10-build-Memtest-v4.20-fails-on-Sandy-Bridge](http://forum.canardpc.com/threads/72840-Ubuntu-12.10-build-Memtest-v4.20-fails-on-Sandy-Bridge)

> **sonypete said:**
> afmprog,
ahallubuntu,
    Yea, I kind of want to figure out how to load the binaries for the newest version of memtest86+ into grub2 and re-run to see if that eliminates the issue i'm facing.
- Pete

That is easy. Just replace the /boot/memtest86+.bin file with the 5.00b1 bin file. I tried that for the v4.20 bin file downloaded from the memtest86+ site, and it works.

---

