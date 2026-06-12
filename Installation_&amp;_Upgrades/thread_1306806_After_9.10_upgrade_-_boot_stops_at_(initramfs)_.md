---
title: "After 9.10 upgrade - boot stops at (initramfs)_"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by mahaganapati on 2009-10-30
Upgrading from 9.04 to 9.10 I find myself in a situation I can't handle: Rebooting the machine results in nothing but the text 

(initramfs)_ 

 I have done nothing but run the upgrade. I am not particularly linux-savvy, so please bear over with any questions I might have to your suggestions.

Ideas, suggestions (and - ideally a solution) will be much appreciated.

---

### Post by mahaganapati on 2009-10-30
Well, I managed to figure out that I can boot with the 2.6.28-16-generic kernel, but now I have lost all network connections *and* all sound. Sigh. It seems that I have hit all of the most common faults in this update. Anyway:

iwconfig says:

lo no wireless extensions
eth0 no wireless extensions

Status: I can't boot with the 2.6.31-kernel, I have no sound and no wireless connections. Please help! 

Thanks in advance.

---

### Post by mahaganapati on 2009-11-01
Bump. 
I have installed grub2 but no luck so far - I still cant boot 2.6.31. 2.6.28, however, works fine. I just don't get it - the settings in the grub menu are exactly the same for the two kernels (with the obvious difference of the kernel names, of course), but whenever i try the latest one i end up at the "initramfs"-prompt.

---

### Post by hrafninn on 2009-11-01
It looks like you have the same problem that I had.  I had no option but doing a clean install of 9.04 again; see [http://ubuntuforums.org/showthread.php?t=1307780]("http://ubuntuforums.org/showthread.php?t=1307780")

---

### Post by mahaganapati on 2009-11-01
I really hope that won't be necessary. I can't help but think that this is a really small issue that can be solved by changing a few characters in the right config file somewhere. Of course this might not be the case, and either way I wouldn't know where to begin.  
I would really like to hear some more alternatives to reinstalling before I choose that option. Is it possible to remove and reinstall the 2.6.31-kernel?

---

