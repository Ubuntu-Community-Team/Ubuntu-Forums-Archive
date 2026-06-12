---
title: "[SOLVED] no window decorations, blank terminals"
date: 2008-08-14
forum: General Help
---

### Post by os.getlogin on 2008-08-14
I restarted my machine which was running just fine (Hardy) and now no windows have decorations and the terminal comes up as a pure white blank box.  Any ideas?  (and don't give me a command line tip...I can't type anything!)

Thanks,
Nate

---

### Post by Elfy on 2008-08-14
Do you use compiz if so what window decoration manager do you use, if you don't use compiz do Alt+F2 then metacity --replace in the run dialogue, should get the window decoration back.

HAve you recently done/installed something that could have caused it?

---

### Post by os.getlogin on 2008-08-14
> **forestpixie said:**
> Do you use compiz if so what window decoration manager do you use, if you don't use compiz do Alt+F2 then metacity --replace in the run dialogue, should get the window decoration back.

HAve you recently done/installed something that could have caused it?

How do I determine the window decoration manager?

The last thing I did before it bonked was "log out" and it cycled through a bunch of black screens and asked if I wanted to start in safe mode or shutdown.  So I shutdown and I'm here. (well I've tried restarting X, rebooting etc)

---

### Post by Elfy on 2008-08-14
I realise you logged out to cause it - I meant have you installed a new card, started using compiz or something like that. Have you installed emerald to use...

Do you use compiz or not?

---

### Post by os.getlogin on 2008-08-14
Yep, using compiz.  I haven't installed anything new hardware-wise and have not changed anything the with the decorator.


Some more info.  This seems to be the point of failure in /var/log/messages:
> Aug 14 13:29:34 xxxxxxx kernel: [1401266.786897] NVRM: API mismatch: the client has the version 96.43.05, but
Aug 14 13:29:34 xxxxxxx kernel: [1401266.786900] NVRM: this kernel module has the version 169.12.  Please
Aug 14 13:29:34 xxxxxxx kernel: [1401266.786902] NVRM: make sure that this kernel module and all NVIDIA driver
Aug 14 13:29:34 xxxxxxx kernel: [1401266.786903] NVRM: components have the same version.
Aug 14 13:29:39 xxxxxxx kernel: [1401271.849398] NVRM: API mismatch: the client has the version 96.43.05, but
Aug 14 13:29:39 xxxxxxx kernel: [1401271.849401] NVRM: this kernel module has the version 169.12.  Please
Aug 14 13:29:39 xxxxxxx kernel: [1401271.849402] NVRM: make sure that this kernel module and all NVIDIA driver
Aug 14 13:29:39 xxxxxxx kernel: [1401271.849404] NVRM: components have the same version.
Aug 14 13:29:44 xxxxxxx kernel: [1401276.914986] NVRM: API mismatch: the client has the version 96.43.05, but
Aug 14 13:29:44 xxxxxxx kernel: [1401276.914989] NVRM: this kernel module has the version 169.12.  Please
Aug 14 13:29:44 xxxxxxx kernel: [1401276.914990] NVRM: make sure that this kernel module and all NVIDIA driver
Aug 14 13:29:44 xxxxxxx kernel: [1401276.914991] NVRM: components have the same version.
Aug 14 13:30:01 xxxxxxx kernel: [1401294.164247] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 14 13:30:03 xxxxxxx exiting on signal 15
Aug 14 13:30:50 xxxxxxx syslogd 1.5.0#1ubuntu1: restart

So the crash appears nvidia related.

Then later:
> Aug 14 13:36:55 xxxxxxx kernel: [  409.941967] compiz.real[6382]: segfault at 006c656e eip 08055a80 esp bfaeb2b0 error 

---

### Post by PCessna on 2008-08-14
Whenever this happens to me and its not compiz related, I just reboot and im good for another day or two :)

---

### Post by Elfy on 2008-08-14
I found I had to use emerald with compiz to get decorations working with my card, it seems a bit odd that the errors point at different nvidia versions - I know that 96.43.05 is for older cards (I use it) not sure of 169.12

I also had to insert lines in xorg to get the decorations working properly 

> Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    [COLOR="Red"]Option         "AddARGBGLXVisuals" "True"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    [COLOR="#ff0000"]Option         "AddARGBGLXVisuals" "True"[/COLOR]
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    [COLOR="#ff0000"]Option         "AddARGBGLXVisuals" "True"[/COLOR]
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
EndSection

---

### Post by os.getlogin on 2008-08-14
> **forestpixie said:**
> I found I had to use emerald with compiz to get decorations working with my card, it seems a bit odd that the errors point at different nvidia versions - I know that 96.43.05 is for older cards (I use it) not sure of 169.12

I also had to insert lines in xorg to get the decorations working properly

I'm not sure what your fix is doing, but it works!  My windows decorations are back and the terminal looks fine.  No idea what's going on.  I still get compiz errors in the logs, but I'll hold my breath and call it good.

Thanks!

---

### Post by Elfy on 2008-08-14
I meant to add to the post - to get the options added to xorg, Alt+F2 and in the run box

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

but glad all is ok. Not sure either what the command does, other than add the options which are apparently default to off.

Just so you are aware - if when intrepid gets released you're tempted, at the moment older nvidia cards (certainly the 96. drivers don't work) and their drivers are not working with the new xorg at the moment, waiting for nvidia to deal with the driver it seems.

---

### Post by sarmadzhiev on 2008-10-09
Thx this saved my day :-)

---

