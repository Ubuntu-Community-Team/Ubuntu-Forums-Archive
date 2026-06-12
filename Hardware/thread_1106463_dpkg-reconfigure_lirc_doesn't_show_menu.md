---
title: "dpkg-reconfigure lirc doesn't show menu"
date: 2009-03-25
forum: Hardware
---

### Post by drig23 on 2009-03-25
I have a newly installed mythbuntu.  I plugged a serial receiver which had worked with my old MythDora installation.  When I run "sudo dpkg-reconfigure lirc", it never shows me the menu:

[INDENT]drig@tvroom:/etc/apt$ sudo dpkg-reconfigure lirc
 * Reloading kernel event manager...                [ OK ] 
drig@tvroom:/etc/apt$ 
[/INDENT]
I checked all the various logs and there doesn't seem to be anything important.  I did an apt-get remove lirc and then reinstalled.  No help.  I tried running this over ssh with -X specified, without -X, via VNC from the computer's X session, and once logged into locally to X.  Same thing.

Can anyone think of what I'm missing?  The only change between my installation and a standard install is that I also installed xbmc and boxee.

Thanks!
-Dave

---

### Post by wooddealer on 2009-04-04
I have been battling the same problem myself for sometime now.  I recently built a homebrew serial ir receiver, and have been trying to get Mythbuntu 8.10 to work with it, with little success.

No guarantees but try looking at /etc/lirc/hardware.conf
specifically look for the following line at the very bottom

```
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
```

I changed this to "false" and then dpkg-reconfigure did enter an interactive mode.  I still don't have it working yet, but hopefully this will help you.  I discovered this via this thread [HTML]http://ubuntuforums.org/showthread.php?p=6502305[/HTML]

good luck.

---

