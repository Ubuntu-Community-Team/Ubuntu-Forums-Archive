---
title: "Acer Travelmate 4740Z does not boot"
date: 2011-01-01
forum: Hardware
---

### Post by FBARRENA on 2011-01-01
I have this brand new Acer Travelmate 4740Z-4310. First tried Ubuntu 10.10 from the CD and worked perfect. Then installed it on the hard drive and the computer doesn't boot. 
When turned on it displays a lot of text lines. Then stops and displays a command line asking for username and password. At this point you can login, but if you type startx the screen goes black. 
If you don't type anything, the computer continues doing some processing, then displays another set of text lines and finally does the same as if you typed startx, and just goes black. 

Some of the final text lines displayed before asking for username are this: 
[11.365979] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
At this point ask you for username, then if you don't login, displays this:

i915: gave up waiting for init of module intel_agp.
i915: Unknown symbol intel_agp_enabled (err-16)
i915: gave up waiting for init of module intel_agp.
i915: Unknown symbol intel_max_stolen (err-16)

I have 7 computers with Ubuntu and all of them work smoothly (2 Dell Inspiron, 2 Acer One, 2 desktops home built, 1 Asus K52). Don't know what is wrong with this one. I reinstalled 3 times and it goes the same. Please help!

Francisco Barrena.

---

### Post by pr3smac on 2011-01-03
I have the exact same problem! Have you found any fixes?

I am trying to put Ubuntu on a Dell Inspiron N4010

---

### Post by FBARRENA on 2011-01-03
Hi, 

I tried with Ubuntu 9.04 and it installs but with no network support. I tried with Ubuntu 10.04 and it doesn't even recognize it as an installable disk. 

There is no response from the forum and the problem seems to be complex and hardware-related, so as this notebook came with linpus (awful), I just purchased a Windows 7 Starter licence. I will install it and will get rid of the machine. Maybe I'll try with another brand. 

It's a shame. Ubuntu is the best OS to me. I really like it. 

Regards, 

Francisco.

---

### Post by FBARRENA on 2011-01-19
To whom may run into the same problem: 

I sold the Travelmate and bought a Lenovo Y450 for about the same price. It is running very well on Ubuntu 10.10 and it is nicer. 

Some problems to suspend, I will address that later.

---

### Post by hnavag73 on 2011-02-03
yesterday I bought an Acer Travelmate 4740Z-4310.

At the first boot I experienced the same issue (after login & startx), and I had to shutdown the cpu with the power button (1 brief touch only) and it offered a menu for a short time before shutting down.

On the second boot, at grub I chose the recovery mode with low graphics and let the update manager installed updates. After this the computer has been working flawlessly, wifi, video, sound, etc.

Hope this helps someone.
Héctor Navarro

---

