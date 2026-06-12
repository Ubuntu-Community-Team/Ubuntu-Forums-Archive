---
title: "Running Ubuntu off Intel Graphics Card"
date: 2014-01-16
forum: Hardware
---

### Post by arnold_layne2 on 2014-01-16
My Laptop has dual graphics cards, an AMD 6770 and an Intel HD3000. The AMD card has developed a fault, and as a result I'm running Windows with the AMD card disabled and installed drivers for the Intel card. It runs flawlessly as long as I don't expect high graphics performance out of it.

I want a similar setup with Ubuntu since most my work is in Ubuntu. But I'm not able to do it. 

If I boot Ubuntu normally, I get this:

[IMG]http://i.imgur.com/txdej1k.jpg?1?6520[/IMG]


Now if I boot Ubuntu with 'nomodeset' in it's options, I don't get this error, but instead Ubuntu starts in 'Software Rendering Mode'.


TL;DR: 2 Graphics cards, AMD is faulty, need to run Ubuntu off my Intel card. How?

---

### Post by buzzingrobot on 2014-01-16
Have you disabled the Radeon in the BIOS? And, potentially, removed the Radeon driver?

The Intel drivers are in the kernel.  If Intel video is enabled, and the Radeon is not, you should be 
OK.

---

### Post by arnold_layne2 on 2014-01-17
There's no option to disable the AMD card in my BIOS unfortunately. 

How do I remove the AMD drivers and/or disable the AMD? I'm sorry but I'm kind of a noob when it comes to this, I'd appreciate if you can guide me a bit.

---

### Post by Bucky Ball on 2014-01-17
Why not take the dead card out of the machine altogether???

---

### Post by buzzingrobot on 2014-01-17
> **arnold_layne2 said:**
> 

How do I remove the AMD drivers and/or disable the AMD? I'm sorry but I'm kind of a noob when it comes to this, I'd appreciate if you can guide me a bit.

Depends on how you installed the drivers. If via the Software Center, return there and find the same drivers.  You should see a "Remove" option where you saw "Install" earlier. Ditto other tools like Synaptic, although their GUI's are different. If you installed via "Additional Drivers", go back and use it to remove the driver.

If you used apt-get, then "sudo apt-get remove --purge  <name-of-driver-package>" will do the trick, and also delete the now unneccesary configuration files created to support the driver. 

I don't know how to disable the Radeon if the BIOS offers no option.

---

### Post by Mark Phelps on 2014-01-17
You have what is known as a Hybrid Graphics PC in which two different video chips are at work and they switch back and forth automatically. There is generally no way to disable either in the BIOS as that would defeat the purpose of having two chips.

You may be able to find something that works for you in the linked thread: [http://ubuntuforums.org/showthread.php?t=1930450]("http://ubuntuforums.org/showthread.php?t=1930450")

---

### Post by arnold_layne2 on 2014-01-17
> **Bucky Ball said:**
> Why not take the dead card out of the machine altogether???
It's a hybrid graphics laptop, the AMD card apparently cannot be taken out without messing the motherboard.

> **buzzingrobot said:**
> Depends on how you installed the drivers. If via the Software Center, return there and find the same drivers.  You should see a "Remove" option where you saw "Install" earlier. Ditto other tools like Synaptic, although their GUI's are different. If you installed via "Additional Drivers", go back and use it to remove the driver.

If you used apt-get, then "sudo apt-get remove --purge  <name-of-driver-package>" will do the trick, and also delete the now unneccesary configuration files created to support the driver. 

I don't know how to disable the Radeon if the BIOS offers no option.

See I didn't install any drivers, I just installed Ubuntu, it's using whatever default drivers it uses. No modifications.

> **Mark Phelps said:**
> You have what is known as a Hybrid Graphics PC in which two different video chips are at work and they switch back and forth automatically. There is generally no way to disable either in the BIOS as that would defeat the purpose of having two chips.

You may be able to find something that works for you in the linked thread: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

See that thread is about making the Hybrid graphics work. I don't care about Hybrid graphics. I just need a working Ubuntu installation running off my Intel card somehow, I don't want anything to do with the AMD card.

I have this thing setup in Windows working perfectly, I'm sure there must be a way to do that in Linux!


EDIT: Do you think something like this would work? [http://ubuntuforums.org/showthread.php?t=1807422](http://ubuntuforums.org/showthread.php?t=1807422). Blacklisting the AMD card?

---

### Post by buzzingrobot on 2014-01-17
Ubuntu *does not* install any proprietary drivers by default.  Only a user can install them.  If you did not install proprietary AMD drivers, they are not installed or in use.

It's possible you are using the open-source AMD driver, if the installer detected that defective card.  If "Additional Drivers" lists available drivers, then it is detected. (The driver currently in use will be indicated.) If Additional Drivers lists nothing, then the AMD is not detected.

Blacklisting?  Yes, I would try that.


BTW, "nomodeset" is typically used to allow at least some kind of working display until an appropriate driver is installed. Or, in your case, apparently, until a defective card can be hidden. (Unity requires 3D. Nomodeset delivers 2D.  Hence, the "Software Rendering..." message.  It's emulating 3D because it found no 3D capability.)

---

### Post by arnold_layne2 on 2014-01-18
> **buzzingrobot said:**
> Ubuntu *does not* install any proprietary drivers by default.  Only a user can install them.  If you did not install proprietary AMD drivers, they are not installed or in use.

It's possible you are using the open-source AMD driver, if the installer detected that defective card.  If "Additional Drivers" lists available drivers, then it is detected. (The driver currently in use will be indicated.) If Additional Drivers lists nothing, then the AMD is not detected.

Blacklisting?  Yes, I would try that.


BTW, "nomodeset" is typically used to allow at least some kind of working display until an appropriate driver is installed. Or, in your case, apparently, until a defective card can be hidden. (Unity requires 3D. Nomodeset delivers 2D.  Hence, the "Software Rendering..." message.  It's emulating 3D because it found no 3D capability.)

Hmm adding blacklist radeon to blacklist.conf doesn't seem to work. It does nothing, essentially. Any clue?

---

### Post by buzzingrobot on 2014-01-18
Well no, no clues to go on, really.

 If you have not installed any proprietary Radeon drivers, and if Additional Drivers does not show the open source Radeon driver in use, then you are almost certainly running on the Intel.  

Perhaps the fault to the Radeon is the roadblock. Someone with expertise in how the kernel detects GPU's and, in the case of dual card machines, decides which one to use, needs, I think, to respond. I.e., if it is detecting the Radeon, as those boot messages indicate, then the fact that it is malfunctioning could prevent its use while causing the kernel to ignore the Intel. (Long shot: Can Windows physically disable the Radeon, as opposed to simply ignoring it? If Windows can turn off the card, and it stays turned off over a reboot into Linux, then that might be useful.)

---

### Post by Yellow Pasque on 2014-01-18
Blacklisting should work. You may need to run this to get the change to take effect:
```
sudo depmod -a
```

---

