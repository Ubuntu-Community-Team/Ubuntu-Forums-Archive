---
title: "Nvidia FX 5900 Driver Problems"
date: 2010-01-20
forum: Hardware
---

### Post by kingdogbert on 2010-01-20
Hi all, I just restored my old computer to use as a Linux machine, but I'm having problems with the graphics. System config:

Pentium 4, 1.4Ghz
768MB RAM
Nvidia FX 5900
Ubuntu 9.10

Yesterday, I installed nvidia's [recommended driver](http://www.nvidia.com/object/linux_display_ia32_173.14.22.html). After installing, I rebooted the machine. Everything seems to boot up fine (I get my BIOS splash screen, then Grub, and finally the white Ubuntu loading splash screen), but when the list of usernames should be popping up, the screen goes black. It's not a loss-of-signal problem; the monitor is reporting it's still got a connection. Nothing on the keyboard seems to respond (e.g. Ctrl+Alt+F1 doesn't get me a terminal). Through Grub, I can enter recovery mode and get a terminal, but 'startx' immediately earns me the black screen.

On a side note, the networking is working fine, and my SSH server is starting up, so I do have remote admin capabilities.

My first thought was that xorg.conf was screwed up. However, restoring the old conf file did nothing to help the problem. Now I'm out of ideas. Please help!

---

### Post by kingdogbert on 2010-01-20
So... progress has been made. Through a process of lots of different things, none of which I can remember, I think I've successfully undone the damage of running Nvidia's installer. However, I still don't have a good driver. I enabled the restricted package directory, and now when I open System -> Administration -> Hardware Drivers, two proprietary drivers get listed, version 173 (recommended) and version 96.

I've tried activating both of these drivers. When the computer reboots, I get "Starting Up..." and then a command prompt login that keeps blinking. I can't type anything at all, let alone login. Logging in remotely, I can "service gdm stop", which then allows me to login locally. I overwrite the new xorg.conf with the backup, "service gdm start", and get my GUI login. But now the Nvidia isn't activated.

How do I fix the xorg.conf so that I can run my driver?

---

### Post by kingdogbert on 2010-01-22
Finally got it. Ran uninstall on the nvidia script and envyng and wiped anything from synaptic that had "nvidia" in it. This killed even my basic desktop gui, but oh well. I ran envyng from the command line and finally got everything set up right. If anyone stumbles upon this thread and wants details, post! I keep my subscription on this thread active.

---

