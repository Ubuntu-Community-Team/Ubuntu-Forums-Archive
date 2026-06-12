---
title: "Black screen after adding a GTX-1060"
date: 2017-07-03
forum: Hardware
---

### Post by Luft on 2017-07-03
I have a PC with hard drive caddy that allows me to swap my main drive.  I have one Windows drive for gaming and a Ubuntu 16.04 for everything else.

I took my PC in with the Windows drive in and had a Geforce GTX 1060 put in.  The windows drive works great but now when I put in the Ubuntu 16.04 drive the screen is black.  How can I configure Ubuntu 16.04 to use the new GPU without even being able to see the screen?

Thanks.

---

### Post by Bashing-om on 2017-07-04
Luft; Hello -

Boot with the nomodeset boot parameter from grub;
Remove the old graphic's driver ;
install the new nvidia driver ( 375 ) : [http://www.nvidia.com/download/driverResults.aspx/118290/en-us](http://www.nvidia.com/download/driverResults.aspx/118290/en-us) from the software respository.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by efflandt on 2017-07-04
I had a problem with original 16.04 (only on my Dell XPS 8100 from 2010) in which upon reboot (warm or cold from totally off) the screen would remain totally blank (no BIOS splash screen or grub menu or plymouth) until an OS did graphics (either Ubuntu gui login or Win7 depending upon what booted by default). It was as though 16.04 left graphics in a state when it shut down where no text would display until something did graphics. And it happened whether using GTX 750 Ti or GTX 1060 with various nvidia drivers.

That did NOT happen on any other computer. 64-bit 16.04 worked fine on an old Dell 1.66 GHz dual core laptop with legacy ATI X1300 mobile graphics, other laptops, old Optiplex dual core Pentium, or 32-bit 16.04 on very old Dell Dimension 4700 single core Pentium with hyperthreading that cannot even do 64-bit or SpeedStep and worked fine when I tried my GTX 550 Ti in it (other than graphics being slow in PCIe 1.0 slot).

I am currently running 64-bit 16.10 on the Dell XPS 8100 with nvidia-381 package from graphics-drivers ppa (use Ubuntu packages, not .run file from nvidia.com) which works fine from SSD, as does 14.04 still on my hard drive. I probably should try 16.04.2 or whatever is current LTS version to see if it still has the problem because I think support for 16.10 ends soon. I recently upgraded this 7 yr old PC from i5 650 to i7 870 and from 8 GB 1066 RAM to 16 GB 1333. Using tmpfs for /tmp and no swap I am actually using that RAM for drive caching while Steam gaming.```
~$ free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        1.4G        3.4G        618M         10G         13G
Swap:            0B          0B          0B
```

---

### Post by Luft on 2017-07-04
How do I boot with the nomodeset boot parameter from grub? I never get the chance to interact.  It just goes to a black screen.

---

### Post by Bashing-om on 2017-07-04
Luft;

> **Luft said:**
> How do I boot with the nomodeset boot parameter from grub? I never get the chance to interact.  It just goes to a black screen.

Well. legacy or EFI system ?

Legacy :
As soon as the bios screen clears depress and hold a shift key -> grub menu
Here with the latest kernel selected press the 'e' key for edit mode -> boot parameters screen

arrow down to the line starting with linux and across to quiet splash - replace quiet splash with nomodeset
key combo ctl+x to continue the boot process ( will now see the boot messages ).

If this is a EFI system it is the escape key that grub looks for . Spam the escape key as soon as the firmware screen clears - is but a 3 second window of opportunity .

With nomodeset set; can you now boot to the GUI ? - degraded graphics at this point is OK - we will fix .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

