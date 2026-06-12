---
title: "nVidia, the 8800, and the black boot screen..."
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by thinkbox on 2007-05-03
I understand that there are loads of forum posts in regards to this. I have been using linux for about 2 days(downloaded my first copy on Monday), so I admit that I'm a newbie at it, however my full-time job is hardware/software diagnosis for a local computer shop on the windows platform, so I have some fair grasp of how linux is likely to treat some of the hardware and/or drivers from the get-go. 

Well, of all the posts I have come across I haven't seen anybody with a solid solution that works across the board. However, I have discovered something that I'm hoping will help some of the real software geniuses help the rest of us linux-newbies figure this nvidia problem out.

If I log into the failsafe terminal(esc at GRUB, alternate kernel boot), run telinit 3, and then provide my standard user credentials my 8800GTS comes up with full 3d acceleration and no(thus far) noticeable issues. That's right, I can run WoW, Counter-Strike, Beryl, Emerald, etc. And this is with the nVidia supplied drivers, letting them compile their own kernel, etc.. However, a simple reboot seems to consistantly go to the black screen and never successfully boot into the graphical interface, and trying to select an alternate console(ctrl-alt-F1) is completely unresponsive. The only explanation I can think of is something not initializing properly in the standard boot, something conflicting with what SHOULD be initializing, or perhaps something not happening in the proper order...?

Anyway, that's may frail input to a common problem. Any response would be appreciated. Also, I would like to know if this redneck work-around works for other 7/8 series nVidia users out there. I do have a lot of hardware at my disposal, and I tried several different motherboards/processors/etc on the AMD64 platform with the same video card, and same results, same work-around.

---

### Post by kvonb on 2007-05-03
Sounds like it might be trying to load the "nv" module as well as the compiled module.

Try editing your restricted-modules file and disabling it:

```
 sudo vi /etc/default/linux-restricted-modules-common
```

...then add:

```
DISABLED_MODULES="nv"
```


That should do the trick :)

---

### Post by thinkbox on 2007-05-03
Thanks for your reply.

Well, that makes sense... Unfortunately, I already have the linux-restricted-modules-common edited as per your instructions.

I have double checked it, and the 'nv' module is still set in the disabled list. The system is still doing the same. Any other startup items that may be conflicting?

---

### Post by kvonb on 2007-05-03
[SIZE=-1]Did you do this lot:

[/SIZE]```
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
```

That might help :)

---

### Post by thinkbox on 2007-05-03
I definately get where you're coming from... I'll give it a shot when I get home. My only concern about it is that I really like, and do utilise the nvidia-settings control panel, which does come with the nvidia supplied driver set. Perhaps I'll remove the nvidia-* stuff from init.d first and see how that works(correct me if I'm not grasping the concept here). I'm sure I didn't install the nvidia-glx/nvidia-glx-new apt packages, however I'll double check and --purge them.

I'll post my process and results later on.

---

### Post by kvonb on 2007-05-03
> **thinkbox said:**
> I definately get where you're coming from... I'll give it a shot when I get home. My only concern about it is that I really like, and do utilise the nvidia-settings control panel, which does come with the nvidia supplied driver set. Perhaps I'll remove the nvidia-* stuff from init.d first and see how that works(correct me if I'm not grasping the concept here). I'm sure I didn't install the nvidia-glx/nvidia-glx-new apt packages, however I'll double check and --purge them.

I'll post my process and results later on.

The nvidia-glx stuff I mentioned is just the old default driver junk, it's just a "clean up" thing.  Although you might want to re-run the installer again once you've done that lot.

You should end up with the proper Nvidia settings app :).

---

### Post by thinkbox on 2007-05-04
Well, it seems that I'm out of luck lol. It still isn't being cooperative. Perhaps I should just give and go back to the 32-bit version, which might work better. It's just frustrating because I know it will work, as I use it everyday aver logging in to the single user shell, and runnint telinit 2/3.

---

### Post by BobCFC on 2007-06-11
I have an 8800gts.  The 100.14.09 driver works great and I use Beryl and Nexuiz on max settings, but it has trouble with the splash screen.  To get it running try pressing e to edit GRUB menu and on kernel params line change **splash** to **nosplash**.   Then press ESC and b to boot.

If it works for you it can be made persistent by changing the GRUB config file in /boot/grub/menu.lst 

You may also want to add **vga=795** which will start the console in 1280x1024x32 mode.

---

