---
title: "Replace CD player with CD-writer in Ubuntu?"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by web1b on 2007-06-27
I installed Ubuntu 6.06 Desktop on a Dell desktop PC with a plain CD-ROM.
I now want to replace the drive with a CD writer.
What does it take to have it recognize the CD writer and install burning software?

Would it be easier to just format and reinstall Ubuntu from scratch and have it "autodetect" it?

I also have Vista running in VMWare player.  Should the Vista guest pick up the change or does that OS need to be reinstalled also?

---

### Post by elsaturnino on 2007-06-27
My guess is that you can probably just install it and try to get it working without having to reinstall ubuntu. Worst case scenario, it's too much of a pain and you just reinstall ubuntu anyway. As for the VMWare problem, I think it will be ok as long as ubuntu recognizes the new drive. Again, if you have the drive you might as well install it and see how it goes.

---

### Post by Tachyon_ on 2007-06-27
> Would it be easier to just format and reinstall Ubuntu from scratch and have it "autodetect" it?
The easiest option would be to plug it in and it will most likely work. Linux will detect the hardware during the boot, so it's likely that reinstalling will not help. Anyway, just plug it in and try . If it doesn't work, and you you'd like to try reinstalling, it's not more trouble as you have the drive in place.

> **web1b said:**
> IWhat does it take to have it recognize the CD writer and install burning software?
Please reboot first, there is not a single occasion where I had to reinstall becouse of a hardware change. If it doesn't work after reboot, repost. You can find lot's of burning software from synaptic. It's the Settings-Administration-Synaptics Package manager, search for "burning". You'll find software such as brasero or k3b.

> I also have Vista running in VMWare player.  Should the Vista guest pick up the change or does that OS need to be reinstalled also? 

Vista would most likely also pick up the change, but I'm not sure how well burning is implemented trought vmware. If it doesn't, I'd say vmware is to blame.

---

### Post by trak87 on 2007-06-27
Reinstalling is overkill. Just install the new cd drive and if you have any problems post it in a new thread. Linux should handle it fine. I think Windows should handle it fine too.

---

