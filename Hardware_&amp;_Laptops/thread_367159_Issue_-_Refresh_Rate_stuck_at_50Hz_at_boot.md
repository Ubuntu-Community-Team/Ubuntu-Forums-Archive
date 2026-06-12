---
title: "Issue - Refresh Rate stuck at 50Hz at boot"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by Vivix729 on 2007-02-21
Well, I noticed that my laptop screen defaults to 50Hz upon boot.  I can start nvidia-settings and set it to 60Hz there, but it doesn't stick.  If I do the "Write to X" option, it breaks Beryl.  Actually, even if I only adjust "VertRefresh" line in xorg.conf to 60, it breaks Beryl (doing that doesn't even work, because it STILL defaults to 50Hz). 

Any ideas?

EDIT:  And doing dpkg-reconfigure xserver-xorgconf won't help me, since it doesn't show any widescreen resolutions :(

---

### Post by fearpi on 2007-02-22
I was just going to post *exactly* this problem. I will post my experience here. Unfortunately, I have not found a solution:

I run Beryl. I have a laptop, and I have an NVidia card.

I start up my computer. I go to System -> Preferences - Screen Resolution. The only option for refresh rate is 50 Hz. I go to System -> Preferences -> NVidia Settings. Under "X Server Display Configuration", there are two choices: Auto (selected) and 60 Hz. I select 60 Hz and Apply. When I go back to System -> Preferences -> Screen resolution, the only choice is 63 Hz. When I restart Beryl, there is a noticeable increase in performance.

I reboot. I'm back to square one. "Screen Resolution" refresh is at 50 Hz, and the NVidia Settings refresh is at Auto.

In xorg.conf, under section "Monitor", I have VertRefresh set to 60.0.

---

### Post by Vivix729 on 2007-02-22
> **fearpi said:**
> I was just going to post [i]exactly[i] this problem. I will post my experience here. Unfortunately, I have not found a solution:

I run Beryl. I have a laptop, and I have an NVidia card.

I start up my computer. I go to System -> Preferences - Screen Resolution. The only option for refresh rate is 50 Hz. I go to System -> Preferences -> NVidia Settings. Under "X Server Display Configuration", there are two choices: Auto (selected) and 60 Hz. I select 60 Hz and Apply. When I go back to System -> Preferences -> Screen resolution, the only choice is 63 Hz. When I restart Beryl, there is a noticeable increase in performance.

I reboot. I'm back to square one. "Screen Resolution" refresh is at 50 Hz, and the NVidia Settings refresh is at Auto.

In xorg.conf, under section "Monitor", I have VertRefresh set to 60.0.

This is my EXACT issue.  However, if I set VertRefresh to 60, Beryl is not working right (windows lose their border).

If you find a solution, PLEASE let me know :)

---

### Post by fearpi on 2007-02-22
Let me ask you this: What do you set VertRefresh to if it isn't 60? Because I used to have the problem with no window borders, and I fixed it by doing this:

```

Section "Screen"
...
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "True"
...
EndSection
```

---

### Post by Vivix729 on 2007-02-22
> **fearpi said:**
> Let me ask you this: What do you set VertRefresh to if it isn't 60? Because I used to have the problem with no window borders, and I fixed it by doing this:

```

Section "Screen"
...
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "True"
...
EndSection
```


Ah, I'll try the "TripleBuffer".  The default is 43.0 - 60.0 for VertRefresh.

---

### Post by fearpi on 2007-02-22
I'm throwing in the towel on this one after an hour of tweaking and rebooting. If you want to know my train of thought in case you want to tackle the problem yourself, I was comparing /var/log/Xorg.0.log before and after changing the refresh rate in nvidia-settings. It changes mode to something like "1280x800_60@1280x800+0+0", but when this mode is put in with the other modes in /etc/X11/xorg.conf and the computer rebooted, the xorg log shows that the mode is not valid. Go figure. "1280x800_60" is a valid, mode, but all it seems to do is add a "51 Hz" option in the Screen Resolution box. I tried a couple of others like "1280x800_63" and "1280x800_72" but the xorg log said they were not valid.

---

### Post by fearpi on 2007-02-24
Well, I decided that after a bunch of various problems, I might as well reinstall Ubuntu. I reinstalled the nvidia drivers, but not the latest ones (9746). Instead, I just enabled all of the repositories in /etc/apt/sources.list, and got nvidia-glx through Synaptic. This version is 8776, but seems to work just as well - except that the refresh rate is always set correctly. If you still want to try to fix your problem, I'd try uninstalling your nvidia drivers and then reinstalling them as I have here.

---

### Post by fearpi on 2007-02-24
One more bit of information: I have tried again with the latest NVidia drivers, and after some research I have found that it is not necessarily that the refresh rate is in fact wrong, but that gnome-display-properties is reporting it incorrectly, and so Beryl uses that incorrect value. The trick here is to go into the Beryl settings manager, and under General Options, uncheck Detect Refresh Rate, and then set the Refresh Rate slider to the real refresh rate.

---

