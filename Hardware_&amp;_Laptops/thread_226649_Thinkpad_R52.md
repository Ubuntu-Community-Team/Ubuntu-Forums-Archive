---
title: "Thinkpad R52"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by allegrucci on 2006-07-31
Hi all,

I'm going to buy the above laptop but looking at [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM)
this laptop seems to have some issues with Sleep/suspend to RAM.
Can anyone tell me if those issues are solved in Ubuntu 6.06?
Thank you

---

### Post by timetunnel on 2006-09-12
If you're still interested in an answer: I've got an R52, the one with an ATI graphics card, and Suspend to RAM works fine. Haven't used it very much, so I don't know if there are maybe some USB issues or similar. Hibernate doesn't work at all.

---

### Post by DagMan on 2006-11-01
I use an r52.  Mine with just the shared graphics.
In Dapper and Edgy both suspend works fine.  Hibernate works in Edgy, although it's almost as slow as a full reboot, and I don't remember how it was in Dapper.

In both Dapper and Edgy I had to run alsamixer then alsactl store and then had to put a symlink to the also script in init.d to get sound up properly.

In Dapper I was able to compile a kernel for the pentium-m and then compile the wireless support, drivers, and copy the firmware from what I downloaded.  This did not work in Edgy but I was able to simply compile the kernel and then rename the firmware folder to name of the new kernel and this works fine.  That method will also work for Dapper instead of having to compile the driver and so forth.  As I understand it now, there isn't any real reason to compile new drivers in Dapper.

In Dapper I made a script to chmod the CD/DVD device, to run at startup, and gave it permission to run without a password in the sudoers file.  Without that CD and DVD burning would just simply have to be run with sudo or gksudo is all.  I did this in Edgy too but didn't actually check first to see if it was needed.

In Dapper I had to add ide-cd to /etc/modules in order to play DVD's and I had to comment out all the entries in xorg.conf that weren't the color depth of 24 that I was running already... strange that one.  The DVD's were playing in lower colour before that.  Edgy didn't have either of these problems.

I added, in both Dapper and Edgy, HorzSync and VertRefresh values to get lower screen resolutions than the 1024x768 the install gave me.  I wanted this for a few full screen games.  I don't know if the values are accurate, it was the best info I could find on it and I won't repost it if I'm asked because I don't know what invalid values will do over time.

That, I think, was everything that I did.

Not necisarry that I did, was to define hotkeys to remove and load the module needed for the touchpad.  It's very sensitive and much easier to type with turned off temporarily.

The dial-up modem in my r52 will not work properly.  Video out doesn't work but I haven't tried very hard.  I haven't tried firewire yet.  Ethernet is fine.

---

