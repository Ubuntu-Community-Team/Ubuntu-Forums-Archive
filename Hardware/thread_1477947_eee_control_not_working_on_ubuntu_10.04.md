---
title: "eee control not working on ubuntu 10.04"
date: 2010-05-09
forum: Hardware
---

### Post by pathwork on 2010-05-09
Hi,

I recently upgraded my eee 1005HA to ubuntu 10.04.  Eee control stopped working even if I reinstalled it.  I get the message "Error while communicating with eee-control deamon!"


Warnings I get when installing eee-control:
/usr/bin/eee-control-setup.sh: 115: /etc/init.d/hotkey-setup: not found
Loading modules...
update-rc.d: warning: eee-control stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (S 0 1 6)
 * Starting Eee PC hardware control eee-control-daemon                          Cannot access ACPI control files!
Make sure the modules eeepc_acpi (or eeepc_laptop) are loaded.

Any ideas?

---

### Post by firehawk_1989 on 2010-05-10
I'm having the same problem, yet to find a solution.

---

### Post by sfabel on 2010-05-12
Same thing here. When trying to restart it from the terminal, I get this output:
```

$ sudo /etc/init.d/eee-control restart
 * Restarting Eee PC hardware control eee-control-daemon
Cannot access ACPI control files!
Make sure the modules eeepc_acpi (or eeepc_laptop) are loaded.

```
So I tried to load the modules:
```

$ sudo modprobe eeepc_acpi
FATAL: Module eeepc_acpi not found.
$ sudo modprobe eeepc_laptop
FATAL: Error inserting eeepc_laptop (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/eeepc-laptop.ko): No such device

```

This is starting to annoy me...

Stephan

---

### Post by olayak on 2010-05-16
i actually found that with 10.04 on my eee 1005hab, i no longer need eee control!
are you sure you still need/want it?

---

### Post by firehawk_1989 on 2010-05-16
> **olayak said:**
> i actually found that with 10.04 on my eee 1005hab, i no longer need eee control!
are you sure you still need/want it?

How come you don't need eee control? I have an eee 1005hab also. My upgrade didn't go to smoothly. Maybe I'll have to give 10.04 a try from a fresh install without eee control.

---

### Post by sfabel on 2010-05-17
Ok I figured it out.

You have to change the following line in your /etc/default/grub:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

to

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

```

then reboot. This did it for me at least. Now all the hotkeys are working, I can switch between cpu speeds, etc.

Cheers,
Stephan

---

### Post by firehawk_1989 on 2010-05-20
> **sfabel said:**
> Ok I figured it out.

You have to change the following line in your /etc/default/grub:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

to

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

```

then reboot. This did it for me at least. Now all the hotkeys are working, I can switch between cpu speeds, etc.

Cheers,
Stephan

Hmm I read somewhere else about this fix. I don't seem to have a /etc/default/grub file on my system. Would it work if I created this file and put that line in?

---

### Post by sfabel on 2010-05-20
> **firehawk_1989 said:**
> Hmm I read somewhere else about this fix. I don't seem to have a /etc/default/grub file on my system. Would it work if I created this file and put that line in?

I don't know about that, you should have that file if you use grub. However, as far as I can tell, there should be a default file located at

/usr/share/grub/default/grub

- maybe that helps.

Stephan

---

### Post by Gato Verde on 2010-05-23
I have the same problem.  I found the file /etc/default/grub but can't seem to edit it.  The permissions tab under properties says it can only be edited by root.  I didn't have a root user so I created one but I still can't modify the file...Howzit done?

---

### Post by sfabel on 2010-05-23
OK, here are the step-by-step instructions (this assumes your eeecontrol is installed):

Hit Alt+F2 or start a terminal and enter this:
```
gksu gedit /etc/default/grub
```
(enter your password). Then find
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```
Just to be on the safe side, run
```
sudo update-grub
```
After that (not sure if it is necessary but it won't hurt either). And reboot.

If you like to test this first without changing the file (maybe you have a different bootloader?) append the [FONT="Courier New"]acpi_osi=Linux[/FONT] to your boot command manually first and see how it works. If you don't have this file, I am not sure what you need to do, it should be there if you use Grub as a Bootmanager under Ubuntu. If it is not there, take a look at the Ubuntu docs on how to install Grub or Grub2 or just try creating the file with the above string inside instead of "changing" the file.

Note also that this is probably temporary and might be different in future versions of Ubuntu and/or eeecontrol. That's just from experience.

HTH,
Stephan

---

### Post by landymann on 2010-05-24
So is every one using a ubunutu 10.04 version of eee control? I am still using this version [http://danamlund.dk/eee-control/eee-control.html](http://danamlund.dk/eee-control/eee-control.html)

---

### Post by sfabel on 2010-05-24
> **landymann said:**
> So is every one using a ubunutu 10.04 version of eee control? I am still using this version [http://danamlund.dk/eee-control/eee-control.html](http://danamlund.dk/eee-control/eee-control.html)

org-mode: NICE :)

I am using the one from the PPA.

Cheers,
Stephan

---

### Post by landymann on 2010-05-24
Thanks, I don't think that was around when the RC was released!

---

### Post by bierce on 2010-12-05
On an Asus eeepc, I am unable to run the eee control utility will under 10.10.  The symptoms are the same as reported for 10.04, but the fix reported [in this other thread]("https://bbs.archlinux.org/viewtopic.php?id=87316") (setting acpi_osi=Linux in /etc/default/grub, followed by sudo update-grub) does not work.

Anyone know if the kernel option changed?  Or if this is a fresh bug?

Any clues gratefully received.

(EDIT: Never mind.  The PC is not an eeepc, but an Atom netbook by another maker.)

---

### Post by landymann on 2010-12-06
I know it's the wrong hardware, but I'm not sure, mine seems to be working in 10.10 after upgrading from 10.04 although it doesn't seem quite as slick as before. Depending on what you are trying to do I use the CPU Frequency monitor on the panel to scale the power, but that doesn't solve the APCI problems.

David

---

### Post by Blimpsgo90 on 2010-12-06
Hi,

I have a Asus 1005HA running Ubuntu 10.04 lts Netbook Edition, running
Kernel 2.6.32-26-generic.

I recently installed eee-control using a old deb package, 0.9.4, and it
worked well.

I then checked and found the newest version and installed 0.9.6 using
the deb package.  It now tells me "error commucationg with
eee-control-daemon! make sure it is running".

I have attempted to uninstall it and revert to 0.9.4, but when
attempting to uninstall using the package manger, I get this error:

E: eee-control: subprocess installed pre-removal script returned error
exit status 1


How would I go about fixing this?

Thanks

---

### Post by landymann on 2010-12-06
I would presume the fact that it says sub process installed means that eee-control-daemon is installed, when you select to uninstall it with synaptic it should give you the option for a complete uninstall (can't remeber the phraseing and currently on a uni box with XP). However first try running eee-control-daemon from teminal and then running eee control as you were, and have a look to see what the result is.
 
Hope that helps 
 
David

---

### Post by landymann on 2010-12-06
[http://danamlund.dk/eee-control/eee-control.html](http://danamlund.dk/eee-control/eee-control.html) Here is somemore info on eee control and it looks like development has finished on it.

---

### Post by Blimpsgo90 on 2010-12-06
> **landymann said:**
> I would presume the fact that it says sub process installed means that eee-control-daemon is installed, when you select to uninstall it with synaptic it should give you the option for a complete uninstall (can't remeber the phraseing and currently on a uni box with XP). However first try running eee-control-daemon from teminal and then running eee control as you were, and have a look to see what the result is.
 
Hope that helps 
 
David

Starting eee-control-daemon seems to do nothing.

And complete uninstall gives me the same error.

---

### Post by Blimpsgo90 on 2010-12-06
> **landymann said:**
> [http://danamlund.dk/eee-control/eee-control.html](http://danamlund.dk/eee-control/eee-control.html) Here is somemore info on eee control and it looks like development has finished on it.



no idea what that site is, I thought this was the main development site:
[http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/)

---

### Post by landymann on 2010-12-06
Yep I think your right, it's a site I was useing at one point with a modified .deb file so it would work on Lucid and 9.10 before the correct versions were released.

---

### Post by landymann on 2010-12-06
> **Blimpsgo90 said:**
> Starting eee-control-daemon seems to do nothing.

And complete uninstall gives me the same error.

I've just had a check of my eee PC and I've set it up so it launches eee-control-tray at startup so you could try that. Other than that I have no other ideas.

David

---

