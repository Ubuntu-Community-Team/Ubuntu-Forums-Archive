---
title: "Calling GRUB experts!  Help!"
date: 2008-11-12
forum: General Help
---

### Post by PRMan on 2008-11-12
I have a Dell 400SC Server (2.4 Hyperthread) machine that still runs great.  I have Windows on it and I have been dual-booting Feisty Fawn, although I now have another Linux server with Hardy so I don't use that drive anymore.

I come home from a business trip and the machine won't boot:

GRUB Error 17

I disconnect the Ubuntu drive and I get:

Disk Error

I boot with the Intrepid Live CD and everything works great.  I can mount both drives no problem and I back everything up.

Now, this machine was going to go to the kids and other than the fact that hard drives are not bootable, it seems fine.

I even tried putting Windows XP SP3 on a newer SATA drive and it loaded all the way up but after booting, I get:

Disk Error

So, it seems like USB and CD will boot but hard drives will not.

Can't I install GRUB on a USB key and then use that to boot and chainload Windows?  If so, what do I put on the USB stick to do that?

Thanks.

(I know the machine is 5 years old, but it still seems fast with XP and my wife just agreed to let me buy another PC, so I am not going to get away with buying 2 more.  I have a machine from my business going back to HP on lease, so I NEED to make this work.  :))

---

### Post by Ryadt on 2008-11-12
To reinstall grub. Boot in the livecd and open the terminal.
Do
```

sudo grub

``````
find /boot/grub/stage1

``````

root (hdx,x)
```Replace x by the output of the second code.
Then
```
setup (hd0)
``````
quit
```And reboot.

---

### Post by PRMan on 2008-11-12
> **Ryadt said:**
> To reinstall grub. Boot in the livecd and open the terminal.
Do
```

sudo grub

``````
find /boot/grub/stage1

``````

root (hdx,x)
```Replace x by the output of the second code.
Then
```
setup (hd0)
``````
quit
```And reboot.

I did that.  That doesn't work.  Neither does doing the corresponding FIXMBR / FIXBOOT or even an XP INSTALL on the Windows or a blank drive.

There is something wrong with the hardware so that the computer won't boot, but the drives are just fine otherwise.

How do I make a USB that will boot the hard disk Windows partition?

---

