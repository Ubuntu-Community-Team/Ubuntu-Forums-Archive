---
title: "Server Boot Fails at {initramfs}"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by Sct_Plt on 2009-03-27
I got a problem installing 8.10 server.  I installed 8.10 Desktop on sda1, and then Server on sdb1 -two identical 250Gb drives. The Desktop installation is no problem - love it; works great. The server is another matter.

It gets into stage two and then has some problem with kinit. Something about not finding the drive and trying to resume. I can't figure out how to capture the boot log messages. the  dmesg file is empty on the sdb /var/log directory. In fact most all of the logs are empty  on the server partition. I've tried reinstalling the server 3 times with no success; at least I get the same error messages. The boot stalls with initramfs running; I get the {initramfs} prompt on the screen. I wish I could provide better details but without capturing the kernel boot messages it gonna be tough to fix I think.

Any suggestions?

Thanks to all

---

### Post by dandnsmith on 2009-03-27
I hope someone knowledgeable will comment on this one.
I've seen it happen a number of times - recently several with live CDs of various distros.
I hypothesize that something goes wrong with the initrd load (I think I remember reading that this is 'init ram disk'), but cannot fit it into the larger picture, and give up with a sigh when it happens.

I haven't tried cutting out that command from the boot script, as it's a bit difficult with a prepacked liveCD.

---

### Post by Sct_Plt on 2009-03-27
Thanks Derek; downloaded the latest server image 2X and made sure to check the hash - all ok. The initramfs is actually a initial ram file system. Any ideas on capturing boot messages to a file?

Tnx agn!

---

### Post by dandnsmith on 2009-03-30
The best I can offer, since the system isn't running properly when this happens, is screenshots with a digital camera. I used this a number of times when saving the screenshots for a dos-level restore process.

---

### Post by Sct_Plt on 2009-03-31
> **dandnsmith said:**
> The best I can offer, since the system isn't running properly when this happens, is screenshots with a digital camera. I used this a number of times when saving the screenshots for a dos-level restore process.
Thanks Derek...capital idea!

---

