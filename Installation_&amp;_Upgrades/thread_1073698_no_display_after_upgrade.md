---
title: "no display after upgrade"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by hockman5 on 2009-02-18
Well I searched for some help on this and didn't come up with anything. I know I have had this problem in the past but I don't remember how to correct it.
Last night I upgraded from 8.04 to 8.10. When the system boots up, there is no graphical display. The power light on the monitor actually goes into sleep mode.(from a green light to an orange light)  I can hear the sound of the xserver finishing up and asking for a login. I can actually type the username and password and it plays the music that it plays when you log in. But the screen is still in sleep mode and my only way out is Ctrl-Alt-F1 to terminal mode. What is the command to reconfigure the xserver and to have it repoll hardware devices (keyboard, mouse, etc.) Keep in mind I can only do this from a terminal.

---

### Post by insineratehymn on 2009-02-18
sudo dpkg-reconfigure xserver-xorg

---

### Post by cariboo on 2009-02-18
Make sure your update have completed. Start in recovery mode and at the prompt type:

```
dhclient eth0
```

To get network connectivity, then tyoe:

```
apt-get install -f
```

to install any dependencies that didn't install. Next type:

```
apt-get update && apt-get dist-upgrade
```

this should complete your upgrade.

Jim

---

### Post by hockman5 on 2009-02-18
> **insineratehymn said:**
> sudo dpkg-reconfigure xserver-xorg

OK I tried that and I get the same effect. There was no option to select graphics or monitor options, just keyboard and mouse. I guess I need something more thorough.

---

### Post by avtolle on 2009-02-18
That command, in 8.10, does exactly what you found, due to the change in the xorg app used in 8.10. 

When you were in 8.04, did you have desktop effects, a/k/a compiz, enabled? If so, you need to disable them (or remove compiz as it is an upgraded installation from the command line). 

From the command line, have you tried xfix (I believe that is the correct command) to see if it might fix things enough to get you into even a low graphic environment desktop?

---

### Post by hockman5 on 2009-02-18
> **avtolle said:**
> That command, in 8.10, does exactly what you found, due to the change in the xorg app used in 8.10. 

When you were in 8.04, did you have desktop effects, a/k/a compiz, enabled? If so, you need to disable them (or remove compiz as it is an upgraded installation from the command line). 

From the command line, have you tried xfix (I believe that is the correct command) to see if it might fix things enough to get you into even a low graphic environment desktop?

I tried xfix and it didn't help.
Yes, in 8.04, I had desktop effects (compiz) enabled and running, so you are saying I should try to remove that package and then try again? My problem is I can't even see the log in screen so I would think that compiz isn't even running at that point anyway. Wouldn't that eliminate compiz being the problem?

My upgrade did complete successfully.

---

### Post by hockman5 on 2009-02-19
I do have two graphics cards, one is board mounted and disabled in bios, the other is a PCI Radeon HD2400 Pro card. I really need to get my Ubuntu up and running again, I am stuck in WinDos until then.

---

### Post by hockman5 on 2009-02-19
OK I got it working.... Here is what I did.
Downloaded the radeonhd driver from
[http://packages.ubuntu.com/intrepid/xserver-xorg-video-radeonhd](http://packages.ubuntu.com/intrepid/xserver-xorg-video-radeonhd) to an accessible location for ubuntu.
installed the driver with dpkg -i command
hit ctrl-alt-F7 to get back to blank screen
hit Ctrl-Alt-Backspace to restart Xserver.
Everything works fine now.
So if you happen to have an ATI Radeon HD2400 adapter, thats what you do.

---

### Post by hockman5 on 2009-07-27
I guess ubuntu updated to a new level again and my graphics are no longer working..... again.  I tried what I did before but that doesn't work now. Has anyone came up with a solution for this?

---

### Post by hockman5 on 2009-08-18
Is the answer to never update or upgrade ubuntu? I can't believe there isn't a solution to this problem.

---

### Post by markbuntu on 2009-08-18
If you were using the proprietary fglrx driver before you updated it is still in your system and causing problems. You need to remove/purge it.

Always remember to remove any drivers not from the repos before upgrading. In the case of proprietary driver like fglrx or nvidia you need to remove them regardless of where they came from before upgrading.

---

### Post by hockman5 on 2009-08-19
Thanks for the info, but how do I remove the old drivers?

---

