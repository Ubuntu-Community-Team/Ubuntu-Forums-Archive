---
title: "updates: 2.6.32-24-generic: driver issues"
date: 2010-08-31
forum: Hardware
---

### Post by ekeyser on 2010-08-31
I'm posting this to get more information on an issue I had today. I installed the recent updates (today) which included linux-image-2.6.32-24-generic kernel.

On reboot I had no sound, power management, Bluetooth funkiness, etc.

I rebooted into the 2.6.32-23 kernel and problems went away.

Hopefully this helps someone else.

If you've had this issue go ahead and reply.

My appologies if this isn't the correct forum to post to.

I can submit a bug somewhere (launchpad?) but figured I'd do some due diligence beforehand to figure out exactly if this is a bug or if I've configured something incorrectly.

Feel free to ask questions or require more info.

---

### Post by Dave158 on 2010-08-31
What type of computer/laptop are you using?

---

### Post by ekeyser on 2010-08-31
I'm using a Thinkpad Z60m.

Funny thing, and this is most likely user error, but after working on this a bit today I can now boot into 32-24 with no problems with any of the previously mentioned items.

The only thing I did was install and uninstall xtightvncviewer (unrelated reasons). I doubt if that had any effect on the state of my machine.

Aside from that I tried to set the default boot image in grub2. I'm not as familiar with grub2 as I was with grub so maybe I issued a weird chain of commands. Bottom line was that I thought I had the 32-23 kernel as default and was disappointed when 32-24 boot up. But then was pleasantly surprised when all the hardware was working like normal. Go figure.

Again, probably user error but I could swear that when 32-24 was running there were hardware issues, but when 32-23 was running I was golden.

Maybe if I have some extra time I'll go through the boot logs but frankly I doubt that's going to happen.

---

### Post by a.daniel on 2010-09-20
My sound problems were fixed by following the advice in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519)

> 
Actually, this appears to be a bug with permissions, I had to add myself  to the audio group.  I'm not sure what's causing it, but it doesn't  appear to be kernel related.


---

