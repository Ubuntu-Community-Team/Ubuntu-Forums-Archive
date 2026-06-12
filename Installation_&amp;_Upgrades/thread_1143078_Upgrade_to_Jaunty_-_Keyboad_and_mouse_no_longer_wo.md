---
title: "Upgrade to Jaunty - Keyboad and mouse no longer work"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by PaulM1985 on 2009-04-29
Hello

I have upgraded to Jaunty and after shutting down, restarting and logging in, the bar with Applications, Places, System etc loaded but were blank.

Since the Off button also hadn't loaded, I didn't know how to turn it off other than pressing the physical off button on my computer.

After rebooting again, the computer started scanning the disk and errored.  I am unsure of the correct wording of the error, something about line not being long enough.  The prompt recommended running fcsk to rescan and fix the problems. I ran this and accepted any changes.

Now the computer boots up and gets to the enter username screen, but the cursor doesn't move when I move the mouse and the keyboard is also unresponsive.

Any help or advice would be much appreciated.

Paul

---

### Post by PaulM1985 on 2009-04-30
Anyone have any ideas of why this is happening.  It seems to be a fairly common problem without any real solution.  I am able to access bios but all USB stuff is enabled.  It seems that as soon as I try to run the OS the keyboard and mouse are disabled.  

Any ideas of how to fix this other than put Hardy back on.

Paul

---

### Post by stakh on 2009-04-30
Just to mention that I have exactly the same problem after an upgrade from kubuntu hardy->jaunty. No mouse or keyboard on the kde, but I could type during the login, and can use the keyboard on the tty consoles.

It gets worse than that, if I try to do a fresh install, the keyboard works but the touchpad STILL does not work. Never had that...

---

### Post by PaulM1985 on 2009-04-30
Hi Guys

I think I have a solution, but I don't think it will be too popular, but it has worked for me.

Basically, I have downloaded and written the disk for Jaunty and done a full format of my hard disk and installed.  My graphics card does not seem to have installed perfectly, but my keyboard and mouse now work and so my computer is at least functional.  I took a full backup of my computer before updating, so formatting my disk wasn't a problem for me, but I guess it will be a problem for at least some people.  Additionally, I had another computer available (which I had not performed the upgrade on) that I was able to create the disk with.

I hope this helps some people out there.  I was able to start my computer in command line, so maybe if you have not backed up your info, you could mount a hard disk if you have one available.  You may be able to do this when you run the install disk for Jaunty, and backup any information then.

I hope this helps some people out there, but I know it is by no means an ideal solution.

Paul

---

### Post by stakh on 2009-04-30
Glad it worked for you. As for me, that's not really an option, as I only have my laptop at home, and my backup hard-drive is in another contry. I'm actually using my laptop with a combination of screen+w3m+vim. It's ok for mail, forums, but defenitely not ok for watching DVDs...

There MUST be a solution to this issue, besides formating the whole darn thing

---

### Post by lekksi on 2009-05-02
> **stakh said:**
> Just to mention that I have exactly the same problem after an upgrade from kubuntu hardy->jaunty. No mouse or keyboard on the kde, but I could type during the login, and can use the keyboard on the tty consoles.


I had the same problem after upgrading from Hardy to Jaunty on my older laptop (Acer Travelmate 3210): The keyboard and touchpad were dead. Luckily I had my usb mouse still working and could open keyboard settings.

I found this workaround that got the keyboard working again (after reboot): I changed my keyboard model setting from "Acer Laptop" to "Generic 105-key..."
(System -> Preferences -> Keyboard -> Layout tab -> Keyboard model)

No luck with the touchpad yet.

---

### Post by lekksi on 2009-05-02
I found [a fix]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33") that worked for me: 

In terminal:
> modprobe -r psmouse
modprobe psmouse proto=imps

To make this permanent:
> add: options psmouse proto=imps
to: gedit /etc/modprobe.d/options

This fixed the dead keyboard aswell.

---

### Post by chrisinspace on 2009-05-02
> **lekksi said:**
> I found [a fix]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33") that worked for me: 

In terminal:


To make this permanent:

Any idea what this config change does?

---

### Post by zalamkhis on 2009-05-03
Hi,

I have a Dell vostro 1310 with the same problem about touchpad/keyboard and i found my solution following what the user Didius Falco says here: [http://ubuntuforums.org/showthread.php?t=1137797](http://ubuntuforums.org/showthread.php?t=1137797) (a modify of the file menu.lst)

---

### Post by lekksi on 2009-05-03
> **chrisinspace said:**
> Any idea what this config change does?

```
modprobe -r psmouse
modprobe psmouse proto=imps
```
The first line removes psmouse module from kernel and the second one adds it (with parameters proto=imps). More information on [modprobe.]("http://en.wikipedia.org/wiki/Modprobe")

Typing
```
modinfo psmouse
```
into terminal gives you information about the psmouse module. The line with proto is bolded.
```
filename:       /lib/modules/2.6.24-19-generic/kernel/drivers/input/mouse/psmouse.ko
license:        GPL
description:    PS/2 mouse driver
author:         Vojtech Pavlik <vojtech@suse.cz>
srcversion:     81A9B9E9F4F2BA00DE12050
alias:          serio:ty05pr*id*ex*
alias:          serio:ty01pr*id*ex*
depends:        
vermagic:       2.6.24-19-generic SMP mod_unload 
**parm:           proto:Highest protocol extension to probe (bare, imps, exps, any). Useful for KVM switches. (proto_abbrev)**
parm:           resolution:Resolution, in dpi. (uint)
parm:           rate:Report rate, in reports per second. (uint)
parm:           smartscroll:Logitech Smartscroll autorepeat, 1 = enabled (default), 0 = disabled. (bool)
parm:           resetafter:Reset device after so many bad packets (0 = never). (uint)
parm:           resync_time:How long can mouse stay idle before forcing resync (in seconds, 0 = never). (uint)
```

The config option changes the highest psmouse driver protocol extension to probe. I'm not sure what that means in practice. :)
I guess it sets the "level" of the protocol. In other words: does the mouse have just basic functions or some extra functionality. But that is just a guess. :confused:

I found some information on [this page.]("http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml")

---

### Post by chrisinspace on 2009-05-11
> **zalamkhis said:**
> Hi,

I have a Dell vostro 1310 with the same problem about touchpad/keyboard and i found my solution following what the user Didius Falco says here: [http://ubuntuforums.org/showthread.php?t=1137797](http://ubuntuforums.org/showthread.php?t=1137797) (a modify of the file menu.lst)

Thanks, zalamkhis.  This worked perfectly.  I haven't seen the problem since I made the change.

---

