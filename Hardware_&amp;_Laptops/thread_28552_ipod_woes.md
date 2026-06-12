---
title: "ipod woes"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by ishkabob on 2005-04-20
I think that this post is valid because I have been combing the internet for about a week now trying to figure out how to do this.
I have a 3rd Gen, firewire, 40gig Ipod, and Hoary.
Originally when I installed Ubuntu, I could plug my iPod in, and Ubuntu would automatically recognize it and mount it.  I would then use the command "sudo eject /dev/sda2" to eject it.  However, if I would eject it, and then try and plug it back in, ubuntu would route it to /dev/sdb2.  Now, when I plug the ipod in, nothing happens.  It just charges.  This happened once before, and reinstalling the hal packages seemed to fix the problem.  I tried it again...no such luck.  I would really like to know what is going on here as I am a beginner and am trying to learn how to use Linux effectively.

Also, ever since I started using my iPod with linux, it has been doing crazy things apart from the computer.  Like not displaying anything on the screen while its playing, and hanging between menus.

Any help is much appreciated

---

### Post by jeb0921 on 2005-04-20
Yeah, I am having the same problems.  I'm running Breezy here, but my ipod, a 4th generations usb/firewire does the same thing.  I read somewere on the forums that there was a problem with hal.  Whatever it is, I hope it is fixed soon. I keep trying to get rid of winbloze, but then something like this happens and I have to boot into the unwanted one to access my ipod.
 :roll:

---

### Post by ishkabob on 2005-04-20
I've gotten one step further......i think.  I was able to get my iPod talking to my computer again by not rebooting, but shutting down completely and then rebooting.  I messed around with modeprobe a little before that, but that didnt' do anything.  One thing I think I have discovered is that you should "sudo eject /dev/sda".  I have been doing this since the iPod is working again and I haven't had any problems with it bumpng over to /dev/sdb.  I guess this makes sense because it should eject the sda and all of its partitions.  I could be totally wrong but it makes sense to me.

Let me know if anyone has any other discoveries

---

### Post by AsteriskNix on 2005-04-20
Do NOT reboot with the ipod attached.

4th gen here and I had my PC try to boot to the ipod and it trashed the filesystem on the ipod and I had to format it to get it to run under windows or warty.

I haven't tried to plug it in yet in hoary. Waiting for a better iTunes replacement than gtkpod.

---

