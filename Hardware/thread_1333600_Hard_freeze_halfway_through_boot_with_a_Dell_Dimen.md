---
title: "Hard freeze halfway through boot with a Dell Dimension 2400"
date: 2009-11-21
forum: Hardware
---

### Post by kc7zzv on 2009-11-21
I have a Dell Dimension 2400.  When I boot Karmic, the system hangs on every boot after mounting the filesystems.  I think it's crashing before GDM starts, but I don't know how to check.  Numlock does not work.  I can't ping it.  I attached my preseed.txt that I use to install.  (I did replace the password hashes)  Looking on the web makes me think that I have an Intel i845GV graphics card.  Linux thinks I have a 830M.

I tried changing the shared memory size like it says here and no effect.
[http://ubuntuforums.org/showthread.php?t=1224560&highlight=dell+2400](http://ubuntuforums.org/showthread.php?t=1224560&highlight=dell+2400)

Here's the strange part:
I press escape while booting, and it fails to mount all the drives.  The I press Ctrl-D and continue tapping escape until gdm starts.  This fixes the problem till next reboot.

I have no clue why it fixes it.  Any advice on how to fix it, or change something to get the same effect?

Are there any logs I could post that would help?  Would setting up a console on a hardware serial-port help?  Would hard-powering it off after it hangs, booting off a live disc, and copying any files help?  Is there a better place to post this?

---

### Post by lucasdeskywalker on 2009-11-22
I am having the same problem, I think.  It gets to the ubuntu logo and then there is a cursor in the left hand corner, some text flashes and then no video.

This PC has booted before.  It is a new install of Ubuntu 9.10.  We are seeing it freeze up and become unresponsive after sitting for a while, when we do get it to boot.

I wonder if its a compatibility problem with the onboard Intel video?

Thanks,

Dave

---

### Post by kc7zzv on 2009-11-22
> **lucasdeskywalker said:**
> I am having the same problem, I think.  It gets to the ubuntu logo and then there is a cursor in the left hand corner, some text flashes and then no video.

This PC has booted before.  It is a new install of Ubuntu 9.10.  We are seeing it freeze up and become unresponsive after sitting for a while, when we do get it to boot.

I wonder if its a compatibility problem with the onboard Intel video?

Thanks,

Dave

Did it work with an older version?

---

