---
title: "Keyboard not recognised: PS/2 keyboard with PS/2 to USB adaptor on Ubuntu 8.04"
date: 2009-08-15
forum: Hardware
---

### Post by jwyg on 2009-08-15
I'm trying to connect a PS/2 keyboard (Logitech Deluxe 250) to my machine (Dell Latitude D400 running Ubuntu 8.04, Hardy Heron) via the USB port using a 'PS/2 to USB' converter - but am getting no response.

Does anyone have any ideas? Has anyone had problems with a PS/2 keyboard and a PS/2 to USB converter on Ubuntu? Or has anyone done this without problems?

Clues:

[LIST]
[*]The CAPS/NUM/SCROLL lights all light up - so its definitely connected
[*]I've previously connected USB keyboards to the same computer without a hitch (though perhaps on an older version of Ubuntu)
[*]A USB mouse currently functions fine
[*]When the keyboard is plugged in 'lsusb' lists all devices as 0000:0000
[*]When I do 'sudo tail -f /var/log/messages' nothing happens when I unplug and then plug in the keyboard
[*]The keyboard is not recognised when I go into the BIOS menu on system start up
[*]There doesn't look like there is any 'enable legacy USB' option per se on my BIOS menu, but I have checked that other relevant looking options are enabled
[/LIST]
Any advice would be very much appreciated!

---

### Post by nixscripter on 2009-08-15
Have you verified that the keyboard works without the converter?

If so, then also try loading the **psmouse** module explicitly:

```

modprobe -r psmouse
modprobe psmouse proto=imps

```

(Taken from [this thread]("http://ubuntuforums.org/showthread.php?t=1167221"))

---

### Post by jwyg on 2009-08-15
Thanks for your reply, nixscripter!

> **nixscripter said:**
> Have you verified that the keyboard works without the converter?


I haven't tested it - but it is fresh out of the box, so I assume it works!

> **nixscripter said:**
> 
If so, then also try loading the **psmouse** module explicitly:
```

modprobe -r psmouse
modprobe psmouse proto=imps

```(Taken from [this thread]("http://ubuntuforums.org/showthread.php?t=1167221"))

I just tried this and it doesn't enable the PS/2 keyboard, but it does disable the trackpad on my laptop. Oops! Is there any way I can undo this?

---

### Post by freiheit37 on 2009-08-16
Hello there,

I am posting on behalf of JWYG, as he is now locked out of his keyboard (and needs to get back on tonight)! 
He typed in the modprobe psmouse command but upon restarting of his computer got locked out of his keyboard. The keyboard works up until the point that Ubuntu starts loading proper and then it freezes - so no commands can be tyoed in etc. 

Is there a way he can unlock his keyboard from the start up menu? 

Any help would be appreciated..........!

---

### Post by nixscripter on 2009-08-16
Sorry about that. I thought a rostart wold fix it.

Does the keyboard work booted into "Safe mode"? Hit ESC from the boot screen of "3...2...1..." and select the next entry down. You should see all the boot information and get to a shell instead of the GUI login.

---

### Post by jwyg on 2009-08-17
Thanks for your reply! Sending this from an internet cafe...

> **nixscripter said:**
> Sorry about that. I thought a rostart wold fix it.

Does the keyboard work booted into "Safe mode"? Hit ESC from the boot screen of "3...2...1..." and select the next entry down. You should see all the boot information and get to a shell instead of the GUI login.

I can get to a shell prompt via the 'recovery menu' - and the keyboard works there!

Is there anything I can do from this point to re-enable the keyboard in normal boot?

---

### Post by jwyg on 2009-08-17
Hmm.. after [asking around on the #ubuntu channel]("http://irclogs.ubuntu.com/2009/08/17/%23ubuntu.txt") - its been suggested that this may be in fact due to a (coincidental) recent upgrade from 8.04 to 8.10 - rather than related to psmouse!

In any case still looking for a way to re-enable my keyboard and mouse!

---

### Post by jwyg on 2009-08-17
Aha! Normal functionality in built in trackpad and keyboard are back! Managed to restore old xorg.conf settings, which must have been corrupted in upgrade. What a relief! :)

PS/2 keyboard still doesn't work though. Has anyone got one working before with a PS/2 to USB adaptor? :confused:

---

### Post by nixscripter on 2009-08-17
Alright, let's take this a little more slowly.

Just to verify wheter the keyboard is being detected at all, open a Terminal and run this with it unplugged:

```
sudo tail -0lf /var/log/messages
```

It should hang there. That's okay.

Now plug it in. Any messages? (Cntl-C to stop when you are done)

---

### Post by jwyg on 2009-08-18
> **nixscripter said:**
> Alright, let's take this a little more slowly.

Just to verify wheter the keyboard is being detected at all, open a Terminal and run this with it unplugged:

```
sudo tail -0lf /var/log/messages
```It should hang there. That's okay.

Now plug it in. Any messages? (Cntl-C to stop when you are done)

Hmm.. No messages at all. I get messages when I plug in a USB mouse, but none for the keyboard.

---

### Post by nixscripter on 2009-08-19
I would have expected at least "unknown USB device", which makes me suspect it's not the hardware. But since your desire to use this device suggests to me that new hardware is a last resort, there is one more way to check to make absolutely sure. In short, it's to enable USB debug.

That requires recompiling that kernel module, however, which is not trivial. Just to emphasize: this will not affect your kernel directly (and thus your ability to get support), but only one of the loadable modules (which does USB).

If you are up to some serious command line work, start by installing a few packages:

```

sudo apt-get install linux-headers-generic
sudo apt-get build-dep linux-source # this will be about nine key packages

```

Also, pick a directory where you will do the rebuild, and then download the source:

```
cd **my-directory** && apt-get source apt-get source linux-image-$(uname -r)
```

If you want to go on, post again.

---

### Post by jocasee on 2009-09-09
Hello there,

I have this problem as well.  I get a message when USB keyboard is plugged in, but no message when plugging in a PS/2 mouse.  In my job, hotplugging PS/2 keyboard is extremely important, and also still having the option to hotplug USB keyboard.  If you wouldn't mind, please continue your steps, I have run the apt-get's which you have already specified. 

Thanks much for your help,
Kamran Khan

PS:  I am not using a PS/2 to USB converter.  Our systems have PS/2 port, but no messages are showing up on the /var/log/messages when i plug a PS/2 keyboard in.

---

