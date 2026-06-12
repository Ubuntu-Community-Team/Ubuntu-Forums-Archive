---
title: "GeForce GTX 750"
date: 2014-04-03
forum: Hardware
---

### Post by mentekid on 2014-04-03
Hello,

I've been running Ubuntu on my machine for quite some time, with a cheap-ass graphics card. A few days ago I went out and bought ASUS GeForce GTX 750, and I dual-booted my system.

Windows works fine, but now Ubuntu acts up. I fresh-installed suspecting that maybe the old drivers and the new drivers were conflicting, but that does not solve the problem. What happens is:


[LIST=1]
[*]If I try to boot Ubuntu normally, it displays the Ubuntu logo and the loading dots (in a weirdly low resolution). After playing the login "drum" sound, the screen freezes and nothing helps but hard reboot 
[*]If I try to boot through safe mode, then leave safe mode and go to normal, Ubuntu boots fine 
[*]If I edit the boot order from grub (via e) to remove quiet splash, i get an infinite amount of this error message: 
[/LIST]

```
[   31.52...] nouveau E[(blank space here) PMC][0000:04:00.0] unknown intr 0x44000000     
```

This gets displayed a lot, then freezes and the computer keeps running.

What I've tried:
[LIST=1]
[*]Installing restricted drivers from the software list. Ubuntu said it can't find any 
[*]Both suggestions on this thread: [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649) 
[*]Installing manually this driver: [http://www.nvidia.com/download/driverResults.aspx/73666/en-us](http://www.nvidia.com/download/driverResults.aspx/73666/en-us) 
[/LIST]

Surprisingly, the last step worked the second time (though not the first). Right now, the status is that I can boot into Ubuntu through safe mode, abort safe mode and it works fine, I think even with the proper drivers, because the resolution is fine and it handles transparency and fade effects well.

So how do I make it boot normally from Grub without all this back-channeling?? I feel like I should simply purge nouveau (that's what's been causing the error messages in the splash I think) but I really don't want to risk it since I've spent all night trying to get to where I am...

I've logged my [lshw]("https://dl.dropboxusercontent.com/u/78161923/lshw.txt") and [dmesg]("https://dl.dropboxusercontent.com/u/78161923/dmesg.txt") outputs for your pleasure (too big for forum attachments)

Please help :)

---

### Post by Kris_Spencer on 2014-04-04
I'm jealous of your 750 GTX!!! :-o But I would say that the proprietary drivers are the way to go. I never use Nouveau. Hopefully 14.04 will just work better for you, using kernel 3.13. I can see why you may be worried about purging the Nouveau drivers. I'm assuming that you aren't using a snapshot compatible File System?

---

### Post by mentekid on 2014-04-04
> **Kris_Spencer said:**
> I'm jealous of your 750 GTX!!! :-o But I would say that the proprietary drivers are the way to go. I never use Nouveau. Hopefully 14.04 will just work better for you, using kernel 3.13. I can see why you may be worried about purging the Nouveau drivers. I'm assuming that you aren't using a snapshot compatible File System?


I guess it's one of those "if you're using it you know it" situations, so probably no snapshot compatibility.

---

### Post by Kris_Spencer on 2014-04-05
Sorry, I probably should have just asked if you were using ext4. In which case, it's not snapshot compatible. Using a snapshot, you could give a try to ripping out nouveau worry free. If it broke something really badly, you could roll your system back to the snapshot and pretend that you never did that. I would probably just wait until 14.04 releases and see if working with the 3.13 kernel might help. Sorry that I can't provide anymore info.

---

### Post by mentekid on 2014-04-06
Thanks for your time anyway :)

I'll probably just wait for the new kernel, yeah.

---

### Post by bonzini on 2014-04-23
Running 14.04 on an older Dell Optiplex with a brand new Asus GTX750.

This booted with VESA graphics.  You need to install 334.21 NVIDIA drivers to get the card working properly.

I followed these instructions, more or less - except that I couldn't get a terminal session killing lightdm.  So I booted in recovery mode, checked the file systems (which also mounts them) and ran the script there.

---

### Post by mentekid on 2014-04-24
Update: Yesterday I upgraded to 14.04, and the problem just disappeared. My system still can't find any additional drivers from the menu, but everything works properly.

I guess it was just because of the new gfx card? Thanks to everyone :)

---

