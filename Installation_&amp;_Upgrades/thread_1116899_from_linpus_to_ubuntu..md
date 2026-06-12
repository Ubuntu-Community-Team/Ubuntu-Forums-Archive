---
title: "from linpus to ubuntu."
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by luccidity on 2009-04-05
I have an acer aspire 150 notebook. Which had linpus already installed on the full hard drive.
I put xp media centre edition on, but was not happy with that. Then decided to put ubuntu on (full install).
Everything seemed to install ok, but the wireless would not work, neither could i get the wireless light to even show. Put linpus back on and everthing ok with wireless. From what i have read the acer aspire was made especially for linpus.
Could the fact that i had xp on previously affect the wireless.
Should i be ok to put ubuntu back on either full install or partition. I have a 160gb hard drive.

Any help appreciated.

---

### Post by ongun.kanat on 2009-04-05
try Hardware Drivers menu at System->Management
or network icon at the panel.
you can configure your network drive

ubuntu supports lots of hardware but maybe your network drive isn't supported or you must install it manually

---

### Post by albinootje on 2009-04-05
> **luccidity said:**
>  Everything seemed to install ok, but the wireless would not work

I have an Acer Aspire One 110, and I've put Ubuntu Jaunty Beta on it, everything (including wifi) worked out of the box, except for a little tweak needed to make the sdhc card read on the left card-reader (I didn't try the right card-reader actually).

Jaunty rocks! :)

---

### Post by luccidity on 2009-04-05
Thanks to you both for taking the time to reply. I will give ubuntu another go.

I will have another look at this ubuntu jaunty as well.

---

### Post by calvinps on 2009-04-05
Try this:

```
lshw -class network
```

Post your results when you're done

---

### Post by luccidity on 2009-04-06
calvinps, i am not sure what you mean. could you please ellaborate on what to do as i am only a beginner.
Thanks.

---

### Post by albinootje on 2009-04-06
> **luccidity said:**
> calvinps, i am not sure what you mean. could you please ellaborate on what to do as i am only a beginner.
Thanks.

calvinps was asking you to open a terminal 
(->Applications  ->Accessories -> Terminal)
and then post the output of that command here.
You would do that in the "live session" using your Ubuntu cdrom.
If you don't have internet at all during that live session you could pop in an usb-stick.

---

### Post by luccidity on 2009-04-07
Thanks for the reply.

---

### Post by bolucpap on 2009-04-08
albinootje, can you remember what small tweak you performed for the card reader? Thanks in advance for any help you may provide.

---

### Post by albinootje on 2009-04-08
> **bolucpap said:**
> can you remember what small tweak you performed for the card reader? Thanks in advance for any help you may provide.

Sorry that i didn't include that :(

From here : [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
> 
Remark 1: Support for SDHC cards can be enabled with BIOS 3305 and 3309 for kernel 2.6.27 and 2.6.28 via a module parameter. Add "options sdhci debug_quirks=1" (without double quotes) as seperate line to a new file in directory "/etc/modprobe.d" so that the "sdhci" kernel module loads with this module parameter.


---

### Post by teaker1s on 2009-04-10
take a look at this thread, I have been posting on it and it will fix all the common aspire issues
[http://ubuntuforums.org/showthread.php?t=1106155]("http://ubuntuforums.org/showthread.php?t=1106155")

---

