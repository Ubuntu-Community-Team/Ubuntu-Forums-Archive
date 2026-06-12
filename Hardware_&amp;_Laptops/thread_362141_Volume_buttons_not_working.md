---
title: "Volume buttons not working"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by psi36 on 2007-02-15
The volume buttons (mute, down, up) and the special keys like fn + f3 for Suspend or fn + f8 for battery status on my Compaq nx7400 laptop only sporadically work.

Sometimes they work and do until the next reboot, but most of the time the don't.

I'm running Ubunutu 6.10 the 32 bit version now, when I use the 64 bit version I don't have this problem.

Anyone know what ould cause this and/or have a solution?

---

### Post by dlehman on 2007-02-15
well on my full keyboard I can set the special keys with the system > preferences > keyboard shortcuts, and there is an app in the repo call fnfx you may want to look at it and search the repo I believe there is a similar app also nut sure what it is call though 

good luck

---

### Post by psi36 on 2007-02-15
Problem is that, in keyboard shortcuts, when I try to asign a new key to volume up and i press the volume up button on my laptop, nothing happens. My system doesn't seem to know it's even pressed.  For the mute button the same problem, altough the button does light up after I press it.
And as said: sometimes it does work, but only untill reboot and for no apperent reason.

---

### Post by psi36 on 2007-04-12
Actually: the volume buttons only worked a few times just after I installed Ubuntu. They haven't worked since then.

I have the 64 bit version of Ubuntu on another partition and if I boot that, they do work. Problem is that I'm having major suspend problems with 64 bit Ubuntu, so I can't use it.

So the volume buttons should be able to work, only I have no idea how to make them work...

---

### Post by tanguyr on 2007-05-09
> **psi36 said:**
> Actually: the volume buttons only worked a few times just after I installed Ubuntu. They haven't worked since then.

I have the 64 bit version of Ubuntu on another partition and if I boot that, they do work. Problem is that I'm having major suspend problems with 64 bit Ubuntu, so I can't use it.

So the volume buttons should be able to work, only I have no idea how to make them work...

Hello/Dag/Bonjour,

On the non-functioning install (32 bit), you haven't by any chance installed XGL? I ask because i can get my laptop volume buttons to work just fine under a "normal"x server, but not under XGL.

Try this: open a terminal and type:

```
tail -f /var/log/acpid
```

And then type a few special laptop keys. Do you see any text scrolling in the window?

Regs,
/t

---

### Post by psi36 on 2007-05-09
This is what I get:```
~$ tail -f /var/log/acpid
[Wed May  9 20:30:31 2007] action exited with status 0
[Wed May  9 20:30:31 2007] completed event "button/lid C237 00000080 00000005"
[Thu May 10 00:12:37 2007] received event "button/lid C237 00000080 00000006"
[Thu May 10 00:12:37 2007] notifying client 4596[108:108]
[Thu May 10 00:12:37 2007] notifying client 4745[0:0]
[Thu May 10 00:12:37 2007] executing action "/etc/acpi/lid.sh"
[Thu May 10 00:12:37 2007] BEGIN HANDLER MESSAGES
[Thu May 10 00:12:37 2007] END HANDLER MESSAGES
[Thu May 10 00:12:37 2007] action exited with status 0
[Thu May 10 00:12:37 2007] completed event "button/lid C237 00000080 00000006"


```Nothing changes when I press the laptop buttons like volume plus or min or mute.

---

### Post by tanguyr on 2007-05-10
and, just to confirm, you have/haven't installed XGL?

The fact that your /var/log/acpid file doesn't change when you hit these buttons means that your computer doesn't "see" it when they are punched (as opposed to seeing it but not handling it correctly). It is strange that this sometimes works - i would expect it to always work or never work (but, i must warn you, i am far from being an expert).

Can you try booting into 64 bit mode and doing the same test? The idea being to see if you get a reaction from this log when it does work.

---

### Post by psi36 on 2007-05-12
The package xserver-xgl isn't installed.

The problem is that for the moment I cannot boot into 64 bit mode as I have problem after trying to upgrade it to 7.04. It now just boots into BusyBox --> [http://ubuntuforums.org/showthread.php?t=441290](http://ubuntuforums.org/showthread.php?t=441290)

---

### Post by psi36 on 2007-06-24
Updated to Feisty today and now the volume buttons seam to be working after every restart!
I only restated twice, but it worked the two times and before it only worked once every times or even less. So I guess the problem is solved.

---

