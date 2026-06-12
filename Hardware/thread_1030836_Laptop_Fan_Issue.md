---
title: "Laptop Fan Issue"
date: 2009-01-04
forum: Hardware
---

### Post by semi_fiction on 2009-01-04
Hi! I recently installed Ubuntu 8.10 (Intrepid) on my Toshiba Satellite L305-S5891. I got everything set up and working. I looked around some forums and discovered I must install the HP Omnibook kernel module for the fan to work properly. I installed the module and correctly enabled and added it to my /etc/modules file with the ectype=11 argument. The fan works now, but it always stays in the state it was when I boot the computer up. That means I have to boot the computer up, let the cpu heat up for a second, then reboot it so the fan kicks on at POST and stays at that speed for the Ubuntu session. Also, if I put the computer in suspend mode, when I resume it, the fan is off again.

Any ideas to make it so my fan responds correctly to cpu temperatures like it does in Vista(ick)?

---

### Post by semi_fiction on 2009-01-05
bump

---

### Post by semi_fiction on 2009-01-12
Nobody???

---

### Post by emustrangler on 2009-01-12
Can't help, but I'm having what sounds like the exact same problem with the same model Toshiba, so I can confirm at least that it isn't just you.

There were a couple modules that looked like they allow for manual fan control, so I was going to try and use them to write a script to turn on the fan when the temp reaches a certain point.  I'll post again to let you know how it goes.

Having to boot twice to use Ubuntu is getting annoying.

---

### Post by swinky on 2009-01-26
I have the same laptop and the fan works just fine with the omnibook module loaded. It will speed up or slow down as needed and everything. Honestly, the fan maintaining whatever speed it had during the boot sequence sounds like what my laptop was doing before I got the module installed. So I am wondering if maybe the omnibook module is not loading correctly? 

You can find out if the module has been loaded correctly and typing into the console:
```
lsmod | grep omnibook
```
If omnibook is loaded then it should list it. If no results come up, then something is causing the module not to load on boot.

If the omnibook module is NOT loaded, try loading it manually:
```
sudo modprobe omnibook ectype=11
```
On my laptop, if I don't have the module already running, the fan will suddenly kick on as soon as I load it like that. The omnibook module is also what allows the use of the function keys, such as brightness, to work within Ubuntu, so try changing the brightness with those keys. If the brightness doesn't change, the module isn't working correctly, even if it is loaded.

---

### Post by semi_fiction on 2009-01-27
Thanks for the idea, but I remember being able to change the brightness with the Fn keys just fine. I have since overwritten Ubuntu with openSUSE and all is well now. :)

---

### Post by emustrangler on 2009-01-27
Yea, its definitely a problem with how the omnibook is being loaded.  I used 'lsmod |grep omnibook' and it wasn't detected.  I reinstalled it and then reloaded it using:

sudo depmod -a
sudo modprobe omnibook

and it appeared to work (could use brightness adjust keys, temperature stayed under 40C).  Rebooted and ran lsmod again, and it didn't list omnibook, but I can still use brightness adjust!!

Added omnibook to /etc/modules.  I'll see what happens when I reboot....

ETA:  Eh, rebooted, omnibook shows up on lsmod now, but can't adjust brightness.  Weirdness.

ETA:  OK, still not sure what was going on earlier where it worked sometimes even when the module wasn't loaded, but part of the problem was that I didn't add the ectype option when I added the module to /etc/modules.  However adding the line 'options omnibook ectype=11' to /etc/modprobe.d/options seems make it load on reboot and the adjust brightness and temp control function normally.  In anycase, I'm excited about not having to boot twice everytime I want to use Ubuntu :)  Thanks for help, **Swinky**

---

### Post by swinky on 2009-01-28
You are very welcome! The omnibook module can be a really picky thing to work with. Oddly enough, when I installed the 8.10 beta, everything worked out of the box *without* the omnibook module, but newer kernel versions require installing the module. I don't know what is enabled in the beta that makes it work. I wish I knew, because the omnibook module will actually make my computer turn itself on after I shut it down sometimes (so I am actually using the kernel that came with the beta.) I hear it is an issue with *some* laptops of this model, but not all.

---

### Post by emustrangler on 2009-02-03
Heh, well your post helped me figure out why my battery is dead whenever I comeback to the machine :(  Guess I'm having the laptop turning itself on problem as well.  Very HAL.

---

### Post by swinky on 2009-02-03
Unfortunately, I don't know why the omnibook module starts the machine back up, or why some computers experience it and others don't. I don't know enough about the module itself to fix it, but I do know that it is the cause. I've tried messing with BIOS options, updating the BIOS, and even blindly stumbled around different numbers to use in the ectype= option, with no luck. 

Somehow, though, the 8.10 beta kernel manages the fan and uses the hotkeys and everything just fine without the omnibook module, meaning that all that works without my computer turning itself on. I've been trying to figure out what the difference is between each kernel, but so far have only deduced that there is no extra module that is being loaded in the old kernel that lets it work. Maybe it is something in the kernel itself, or some other option I am missing entirely. If I ever manage to figure it out, I'll be sure to mention it here.

---

### Post by semi_fiction on 2009-07-12
Hey, bringing this thread back from the dead. Got my fan working fine in 9.04, all I had to do was add this to /boot/grub/menu.lst under the Ubuntu option:
```
acpi_osi="Linux"
```

And to Swinky, if you're the same swinky that wrote this blog [http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html]("http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html"), thanks because that's what helped me!

---

### Post by swinky on 2009-07-13
> And to Swinky, if you're the same swinky that wrote this blog [http://swinky-linuxblog.blogspot.com...lite-l305.html](http://swinky-linuxblog.blogspot.com...lite-l305.html), thanks because that's what helped me! 

I am in fact the author of that article. I'm glad to hear that it helped you out! The hardware on some of these laptops is pretty tricky, just figured I would pass along the knowledge I gained. It took me quite a while to figure it all out, but now Ubuntu is working great on my Satellite L305. :D

---

