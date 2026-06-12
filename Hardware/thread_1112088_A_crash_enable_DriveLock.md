---
title: "A crash enable DriveLock"
date: 2009-03-31
forum: Hardware
---

### Post by Valde_91 on 2009-03-31
Hi!

Yesterday my nx7000 crashed. Something went wrong in my HD, my system still works, but my computer was unusable: nautilus was unable to locate any file in my drive. I had to hard switch-off my laptop holding my power button, because also the gnome power manger was unusable. Then I restarted my laptop, and I was asked for a DriveLock password: but I never enabled this feature on my laptop. This is a encrypting feature of HP/Compaq laptop, that link the access to the HD to a BIOS password.

I press enter three time, than I had the same message of a HD failure.
I restarted again by pressing the power button, all started fine. After 15 minute another HD failure. Another hard switch-off, and another time I was asked for the drivelock password. Restarted 4 times and drivelock password disappear again.
It's possible that an HD failure generate this bug? Or it's an Ubuntu related issue?
I don't want to accidentally lock forever my HD, so any suggestion?

thanks a lot

Valde_91 

Ps: I had to partition on my laptop, and both partition passed the regular disk checking this morning.

---

### Post by Valde_91 on 2009-03-31
Hi! my bug changes a little bit now: sometimes the HD doesn't respond. It's strange because when it's happend a lot of icons, but not all, doesn't appear anymore. For some instead I have an icon with a little red cross. Moreover when this happens the gnome power manger is unable to shutdown the pc. 

I don't know if it's a filesystem error or an hard drive error...
any suggestion?

Valde_91

---

### Post by cariboo on 2009-03-31
I would suggest a couple of things, first boot from the LiveCD and run fsck manually  on your Linux partition. Do do this, open an Applications-->Accessories-->Terminal and type:

```
sudo fsck /dev/sda1
```

Substitue your partition for the one in the command.

The second thing is to go to your hard drives' manufacturers web site and download their diagnostic tools and run them to check your hard drive.

Jim

---

### Post by Valde_91 on 2009-04-01
Thanks cariboo907 for your reply! 
I'll try yours propositions as soon as I change my cd-rom drive. I discovred today that is broken...

bye bye Valde_91

---

### Post by Valde_91 on 2009-04-10
Hi cariboo907!
I've reassembled my pc today. I've done the fsck and the manufacturer test (western digital). Both doesn't have find any error on my drive. 
But when I was reassembling my PC I noticed that the the upper part of the support of the HD was mounted up side down. The support covered a little hole of the HD. Since I remounted the HD the bug is gone.


Thanks for yours suggestions Valde_91

---

