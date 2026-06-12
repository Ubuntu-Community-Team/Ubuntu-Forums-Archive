---
title: "Changing screem modes -&gt; crashes"
date: 2008-11-20
forum: Hardware
---

### Post by ScottHW on 2008-11-20
I've been working with a Gateway M275 Tablet laptop w/ Hardy (and recording my results in [_*another thread*_]("http://ubuntuforums.org/showthread.php?p=6194659")).  I have some sort of array of graphics problems;

I get hangs and need hard reboot (inconsistently) when:
[LIST]
[*]Switching to use tty virtual terminals
[*]Suspend/Standby the system
[*]Shutting down
[*]Switching LCD/CRT display
[*]Restarting GDM
[/LIST]

I don't quite know how to go about tracking down my problems any more than this.  I have looked around extensively, and read launchpad bug reports and i810 conflict reports, etc.

How do I find the specifics on my system to move forward and fix these problems?  tracebacks (not entirely sure how to do this...) ? 

I can attach Xorg.conf, Xorg.0.log, lspic, dmesg, or any other logs or pertinent info if it would help.

---

### Post by ScottHW on 2008-11-20
Here are the bug reports I've found, albeit some old, with similar symptoms:
[indent] **laptop hangs when switching video mode**
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101)

**[855GM] system hang during suspend/resume**
[https://bugs.freedesktop.org/show_bug.cgi?id=11432](https://bugs.freedesktop.org/show_bug.cgi?id=11432)

**System freeze after pressing ctrl-alt-bs.**
[https://bugs.freedesktop.org/show_bug.cgi?id=10809](https://bugs.freedesktop.org/show_bug.cgi?id=10809)

**xserver crashes when rotating display and compiz enabled**
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/294309](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/294309)[/indent]
Can anyone tell me how I can determine if I'm effected by the same problems?  Some of those threads are old...

---

### Post by ScottHW on 2008-11-20
Could anyone who has more Ubuntu beans explain to I how to go about trying to diagnose this?

tracebacks?  Which logs to look at?  How I might need to modify my Xorg.conf file?

---

### Post by ScottHW on 2008-11-21
I checked that I have the most recent BIOS (48.04.01)

Any ideas?  Little help?

---

### Post by ScottHW on 2008-11-21
Neither of the sites listed above, bugs.freedesktop nor bugs.launchpad have ANY reports dealing specifically with M275.

Can anyone help me?  At least help me get started???

Please???

---

### Post by ScottHW on 2008-11-21
Well, with no help, and not even a single response from anyone on the forums, I read some useful stuff on other forums that has helped me "solve" this problem.

From this older bug report (about several *other* laptop models), there is a suggestion I'd seen before:
[_https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101_](_https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101_)
[indent] What you need to do is:
edit /etc/X11/xorg.conf
and add into the video card section:
Option "ForceEnablePipeA" "true" [/indent]

I took it to mean this:
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"ForceEnablePipeA" "true"
...
...
End Section
```
Anyway, that *does* work.  But, since I haven't actually figured out *why* this works, or what specific problem(s) it addresses/solves/works-around, I'm not really thrilled with it.

Also, while I can't find the link now, I know I've read in other bug reports that this will cause increased power usage, an unfavorable side-effect on a laptop.

Also, I do not yet know how this might effect actual performance of the video-out VGA.  I may report more later, but there don't seem to be many interested readers here on Ubuntuforums...

---

### Post by MGaddict2000 on 2008-12-22
You do have interested readers, unfortunatly we seem to have less experience then you. The oddest thing I'm noticing here is you have a short snippet of your xorg.conf here and the section your showing has

...
...
End Section

which tells me you have more info there. I have nothing listed in that section besides 

	Identifier	"Configured Video Device"
	Option		"ForceEnablePipeA" "true"

Do you have a driver listed or something? I'm having trouble with wacomcpl telling me I need a driver. I'm probably going to post on your other thread this problem if I don't find it when I finish getting though that thread. But thanks a lot for this, its really helping somebody.

---

