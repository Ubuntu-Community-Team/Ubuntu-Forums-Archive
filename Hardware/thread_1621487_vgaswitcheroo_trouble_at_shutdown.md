---
title: "vgaswitcheroo: trouble at shutdown"
date: 2010-11-14
forum: Hardware
---

### Post by adpads on 2010-11-14
Hi - Is anyone else having the same problem with vga_switcheroo at shutdown, on laptops with switchable graphics?

Under maverick with the 2.6.35-22 kernel, I am using the vga_switcheroo module to select the internal intel graphics card, and power off the discrete radeon GPU on my Acer TimelineX 3820 TG.

On shutdown, I get a million repetitions of the following two errors streaming down the screen:

> kernel: [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB3C (len 62, WS 0, PS 0) @ 0xCB58
kernel: [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting

I guess this is because drm can't talk to the GPU which is powered off. But if I try to power on the discrete graphics card (echo ON > /sys/kernel/debug/vgaswitcheroo/switch), then I immediately get a black screen. 

Has anyone got a solution to this (i.e. a way to switch the discrete card back on at shutdown?)

---

### Post by adpads on 2010-11-15
I found a stopgap solution, for anyone finding this thread with the same issue, but I am not going to mark the thread as solved in case someone else has an even cleverer way of doing it.

I have been using /etc/rc.local to issue commands to vgaswitcheroo to select the card.

After some fiddling around with these over many reboots, I discovered that they had not been working reliably.

Overall vgaswitcheroo is not always working reliably for me, either from the command line, or with the switch built into the "ubuntu control center," or with the scripts found on [this page]("http://asusm51ta-with-linux.blogspot.com/2010/05/07052010-fedora-13-beta-kernel-2.html"), After many attempts, I discovered that when I could get my computer to switch to the radeon card at all (one in 10 tries probably), the card does not support 3D rendering and I can't run compiz or compositing. This reinforced my sense that for now what I really want to do is just power it off.

The best way I came up with to do this is to include a line at the end of my now quite lengthy /etc/rc.local which removes the radeon module 60 seconds after boot. So my /etc/rc.local now looks something like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo chmod a+w /sys/kernel/debug/vgaswitcheroo/switch
sudo echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
sleep 60; sudo modprobe -r radeon
exit 0

```

The first line changes permissions on the switch to allow users to operate it. The second selects the intel card; the third cuts power to the unused card. I am at a loss to explain why I had to put 'sudo' before those commands, which ought in theory to be running as root.
The last command removes the radeon module after a 60-second delay.

At shutdown I get a few unintelligible messages from vgaswitcheroo, but they don't repeat endlessly down the screen and it saves some time.

However, my boot is still really slow - about 1.5 minutes. I think there may be some trouble there too also related to this issue, but I haven't had time to look into that yet.

Please share your thoughts on these issues people, as I hope this will help all of this get smoother in future releases.

---

### Post by Ace_NoOne on 2010-11-15
Thanks for posting this! I'll give it a try and report back (will probably take a few days to get a reliable impression).

> **adpads said:**
> 
sleep 60; sudo modprobe -r radeon
[...]
However, my boot is still really slow - about 1.5 minutes.

I'm not an expert, but won't that *sleep* there delay startup? I doubt *rc.local* is executed asynchronously.

---

### Post by adpads on 2010-11-15
> **Ace_NoOne said:**
> I'm not an expert, but won't that *sleep* there delay startup? I doubt *rc.local* is executed asynchronously.

I'm getting a usable desktop, and then the radeon module (and consequently also vgaswitcheroo) are getting shut off about a minute after. In fact, the reason I had to put that delay in is that the unused GPU isn't getting powered off right away, but only a few seconds after boot, which is why the radeon module wasn't removing successfully.
Hope that works for you!

---

### Post by adpads on 2010-11-22
Update on this, for what it's worth:

I was having some problems with the above setup, including having my system freeze up completely sometimes when the radeon module is removed, forcing a restart at the loss of all my work, and some sloppy screen redraws which occasionally makes things illegible.

I have shortened my /etc/rc.local, in the hopes of cutting down the cruft and speeding up my boot. I am now only running three commands: echo OFF, to turn off the radeon card, a power-saving script I use, and sleeep 60; modprobe -r radeon, to remove the module.
The script doesn't always seem to be running to completion, and sometimes the radeon module is not removed, but I am no longer getting any errors at shutdown. Not sure why, but I will post again if I figure out why not.

---

### Post by Ace_NoOne on 2010-11-23
I've been using your (original) *rc.local* on my 3820TG for about a week now, quite successfully: I haven't encountered any of the issues you describe (yet?), and it has significantly increased battery life (~4 hours instead of barely 3).

Thanks for sharing!

**UPDATE:** There is one issue after all: When the machine is idle for a while, it sometimes(?) doesn't wake up anymore. I thought the first time was a fluke, but it happened again just now.

---

### Post by jocko on 2010-11-27
I've tried this on my Acer TimelineX 3820TG, and it works with some exceptions:

The radeon module takes a very long time to unload (running modprobe -r radeon in a terminal just seems to hang for several minutes). Once it finally unloads it ither freezes the computer, or it will refuse to come back from sleep if I leave it.

If I prevent the radeon module from loading (by adding "blacklist radeon" to /etc/modprobe.d/blacklist.conf) everything works out fine, but a few minutes after boot the radeon card is powered on and at the same time the /sys/kernel/debug/vgaswitcheroo/switch file disappears, bringing power consumption up from 11-15W to almost 30W on idle...

So I simply let the radeon module stay loaded and ignore the error messages on shutdown...

---

### Post by mino.sk on 2011-02-08
I solved this problem by blacklisting radeon. Yes, vgaswitcheroo doesn't work since there's only one graphic card but never mind - you can power off the ATI card using this script - [http://ubuntuforums.org/showpost.php?p=9446283&postcount=65](http://ubuntuforums.org/showpost.php?p=9446283&postcount=65).
I have done it that way and everything works flawlessly.

PS: You really need to *blacklist* radeon...
modprobe -r radeon DOESN'T WORK - I tried it so many times... in /etc/init.d/rc.local, after startup...

---

