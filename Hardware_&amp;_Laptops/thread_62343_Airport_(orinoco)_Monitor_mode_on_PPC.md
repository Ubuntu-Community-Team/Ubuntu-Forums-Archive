---
title: "Airport (orinoco) Monitor mode on PPC"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by call3 on 2005-09-04
Hello! having problem on my ibook. I installed ubuntu on my old ibook with airport (not extreme), I needed it for the perpose of wardriving.

And when i installed it i could find the airport  card.
then i found out airport was a "repackt orinoco" (source: [http://www.swieskowski.net/code/wifi.php](http://www.swieskowski.net/code/wifi.php)) and to get it working for wardriving you needed to patch the drivers ([http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html))
And i have no idea how to rebuild the kernal, so i followed the nice guide in the wiki ([https://wiki.ubuntu.com//OrinocoMonitorKismet2005Hoary](https://wiki.ubuntu.com//OrinocoMonitorKismet2005Hoary)) the only thing i had to change was the 386 to powerpc

But when im all done and diden't forget anything in the guide (reinstalld the system when it didn't work the first time just to make sure) But the card can't be found.... 
(even after the "modprobe orinoco" command)
Anyone out here who know any trick to get Airport (orinoco) in to MONITOR mode.

Have a lovley day //calle

---

### Post by rayhaque on 2006-03-10
I would be curious to know if anyone here has compiled the driver successfully on 5.10 ppc.  And if so, what is the catch?

I have downloaded kernel source, headers, etc.  Actually went and did a make oldconfig && make dep && make modules && make.  At that point I was able to get into the Makefile of several piles of source code (patched 13e ver 8/9/etc, a couple different 15's, cvs stuff, etc) and change my KERNEL_SRC variable to reflect the real location (for me /usr/src/linux - a symbolic link).  At that point, I can run a make and build any source code I want -without errors.  It took me a few days of mucking around to get to this point.

But now that I have the compiled orinoco and airport drivers I need, I can't insmod them . When I do, I get "-1 unresolved symbols" errors.

So, has anyone made monitor supportive Orinoco drivers for 5.10 PowerPC?  If so, could we *share* those with you please?  :-)

Thanks!

-Ray Haque

---

### Post by rayhaque on 2006-03-10
Silly idea #2:

Would anyone have patches (for rfmon support) to the orinoco driver that comes with the PPC Ubuntu 5.10?

dmesg | grep orinoco 

[90141.820542] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)

I suppose with a some coding skill, one could pick apart the diff's and try to apply them to the 14'alpha 2 source.  But I have ZERO skill in c programming.  ;-)

-Ray Haque

---

### Post by rayhaque on 2006-03-11
Hey, nevermind.  I'm an idiot.

I was going into the Makefiles and changing the KERNEL_PATH (or KERNEL_SOURCE) to /usr/src/linux.  My stuff would build find at that point.  Yet, I wasn't using the powerpc headers when I did it that way.  Hence, my *** load of Unresolved/Unsolved Symbol messages.

So after installing linux-headers-<kernel version>-powerpc and then re-making things, they compiled without modification to the Makefiles, and they worked just fine.

So, nevermind!  I don't think anyone was paying attention to this anyway.  Since I was adding onto a year old thread.  ;-)

-Ray Haque

---

