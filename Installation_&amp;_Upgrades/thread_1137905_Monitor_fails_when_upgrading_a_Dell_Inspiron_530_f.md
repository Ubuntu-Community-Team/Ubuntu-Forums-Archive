---
title: "Monitor fails when upgrading a Dell Inspiron 530 from 8.04 -&gt; 8.10 -&gt; 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by perchance on 2009-04-26
I upgraded my TwinView dual monitor 8.04 Dell Inspiron to 8.10 and then up to 9.04. As when I previously tried to hit 8.10, I found that positioning was off in Ibex. I detailed this in a previous post here: [http://ubuntuforums.org/showthread.php?t=1110383](http://ubuntuforums.org/showthread.php?t=1110383)

When I reached 9.04, I found that the monitor wouldn't load at all with my monitor config and I was hit with a login prompt at the command line on boot and then the following popup:

```
Ubuntu is running low-graphics mode

...

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ** Aborting ***
(EE) Screen(s) found, but none have a usable configuration
```

Is there anything I can do to remedy this? 

I can hack around a little in low-graphics mode, but I really am far from an expert. I thought I'd try to upgrade and post my results just so, if nothing else, get some feedback logged up here. 

My life isn't over if this doesn't square, I can reformat with 8.04 -- but I would really love to stick with 9.04 if I can make it work.

Thanks.

UPDATE

I just got the following in my terminal after trying to rewrite my xorg.conf

```
ben@dell-desktop:~$ sudo nvidia-xconfig
[sudo] password for ben: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

And now the restart is going more poorly. It halts with a popup that says:

```
The greeter application appears to be crashing. Attempting to use a different one.
```

---

