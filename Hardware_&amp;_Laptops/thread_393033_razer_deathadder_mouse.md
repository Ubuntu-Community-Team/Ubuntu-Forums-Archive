---
title: "razer deathadder mouse"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by uric on 2007-03-25
Hi

I wonder if it would be possible to turn off the lights on my Razer Deathadder mouse? It is possible with the windows firmware, but it doesnt save the settings in the mouse, so the light go back on when I start up ubuntu.

I run ubuntu edgy, and these are my settings in xorg.conf, buttons, mousewheel, everything works great, execept for those annoying lights on the mouse wheel and body. 

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer Deathadder"
    Option         "Vendor" "Razer"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Resolution" "1800"
    Option         "SampleRate" "1000Hz"
EndSection
```

Thanks in advance!

---

### Post by PrivatePickle on 2007-06-03
[http://www.bu3sch.de/deathadder.php]("http://www.bu3sch.de/deathadder.php")

I installed deathaddercfg-004 but have yet to figure out how to use it.  If you have any luck please let me know.  

It still takes me a while to do anything thats not point and click or basic command line.

---

### Post by miceagol on 2007-07-19
> **PrivatePickle said:**
> [http://www.bu3sch.de/deathadder.php]("http://www.bu3sch.de/deathadder.php")

I installed deathaddercfg-004 but have yet to figure out how to use it.  If you have any luck please let me know.  

It still takes me a while to do anything thats not point and click or basic command line.

I'm in the same boat as you. Very easy to install, but I've got no idea on how to use the utility. Do you understand the example rules file udev-deathadder.rules?

```

# Configure the Razer DeathAdder mouse
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="1532", SYSFS{idProduct
}=="0007", RUN+="/usr/local/bin/deathaddercfg --no-rebind -C"
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="1532", SYSFS{idProduct
}=="0003", RUN+="/usr/local/bin/deathaddercfg --no-rebind -t krait -C"

```

I'll contact the developer for instructions...

---

### Post by miceagol on 2007-07-19
Btw, have you tried to add profiles to the mouse in Windows (if you have it)? You can save 5 profiles inside the mouse with the Windows utility. By pressing the button underneath the mouse, you browse through the profiles. This feature should be OS-independent, but you have to use Windows to save the actual profiles into the mouse. I'll try it later on.

---

### Post by PrivatePickle on 2007-07-21
I made several profiles in windows but pushing the profile button in Linux doesn't seem to do anything.  I still can't figure out how to use deathaddercfg.  Have you tried contacting the developer yet?  If not I will give it a shot.

---

### Post by miceagol on 2007-07-23
> **PrivatePickle said:**
> I made several profiles in windows but pushing the profile button in Linux doesn't seem to do anything.  I still can't figure out how to use deathaddercfg.  Have you tried contacting the developer yet?  If not I will give it a shot.

It's sad that even the profile thing doesn't work. I'll try it myself anyway in case it works for me. I just have to try it before I try contacting the developer. Tell me if you reached him before me. Just got the Deathadder, so haven't had time to test it in Windows yet. ;) 

Before I bought the Deathadder I read [this review]("http://www.hardware.no/tester/input/3_x_razer/35617") (Norwegian), which said that it was possible to use the profile button in Linux. If I can't get it to work, I'll send an e-mail to the author and ask him what he did.

Anyway, I love this mouse. It's really pleasant in the hand with the soft rubber surface, and its design is very appealing, especially the blue pulsating logo. :D

---

### Post by PrivatePickle on 2007-07-25
I just sent an email to the developer so we'll see what he says.  I followed everything that was in the readme including adding the udev rules and copied the example config file to /etc/deathadder.cfg.  When I change entries in the config it doesn't change anything even with a reboot.  I have tried searching google on using udev but nothing makes sense to me.

I had the razer diamondback before this one and wasn't sure I would like the design change but it has been great.  Even if I can't get the configuration tool to work this mouse is awsome.

---

### Post by miceagol on 2007-07-26
> **PrivatePickle said:**
> I just sent an email to the developer so we'll see what he says.

Great! :)

But beleive it or not, my Deathadder was destroyed after I tried installing the 1.07 drivers in Windows Vista (64 bit). It worked well in Ubuntu 7.04 (32 bit) and Windows XP (32 bit), but now it's totally dead in both these OS's too. :cry:

It's the first time I've experienced hardware being destroyed when installing drivers. Thought that only could happen when installing firmware. Anyway, I'll contact the dealer to get a replacement tomorrow, but I can't do any more testing for a while.

---

### Post by Prefix100 on 2008-05-27
Any word on this?

Im trying it now, and cant get it to work.

---

