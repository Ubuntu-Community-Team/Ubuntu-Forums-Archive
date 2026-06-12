---
title: "need to install nvidia drivers, but has gone wrong before"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Cerafem on 2009-10-23
I have Ubuntu installed to my computer, which contains a GeForce GTS 250.  I have tried to install drivers previously, a while back (through the Administration->Hardware Drivers) but upon reboot, it won't boot to any kind of GUI, telling me that x server couldn't find any screens (i think, it was awhile back).  So anyway, I got onto NVIDIA's site, and told me to download the .run file, then read stuff on how to install it.

the installation tutorial, on step 6:
[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-06.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-06.html)

a related link it sent me to:
[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/appendix-i.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/appendix-i.html)

And basically, I don't want to mess up this again (and have the only way to use linux be to remove my graphics card and use integrated graphics), and I don't want to spend more hours trying to find out how to properly install this, having to figure out a bunch of in between steps, possibly screwing up my system.  Could you guys help?  I am good with computers (this build was put together by me), and have some programming experience, but not too much linux experience (I come from Windows XP).

Oh, and I am using 9.04, and have installed all other updates, I believe.

---

### Post by Paul41 on 2009-10-23
I have never installed the drivers from downloading them so I can't help you there. If you have the same problem with losing your GUI again run this:

```
sudo dpkg-reconfigure xserver-xorg
```

It will take you through several screens to reset your xserver. On most of the options you can chose the default.

---

### Post by Cerafem on 2009-10-23
Well, the gui doesn't even start, I can login, but on a black screen with white text.  Would this still work?

---

### Post by Fire_Chief on 2009-10-23
Tried using Envy-ng for the install?
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Paul41 on 2009-10-23
> **Cerafem said:**
> Well, the gui doesn't even start, I can login, but on a black screen with white text.  Would this still work?

Yes, it still works. It is all run from the command line.  Worst case you can use recovery mode. You boot to it from grub and you get a terminal screen with root privileges.

---

### Post by Cerafem on 2009-10-23
installing EnvyNG now...

how would I boot from grub?

---

### Post by CharlesA on 2009-10-23
> **Fire_Chief said:**
> Tried using Envy-ng for the install?
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

This is what I ended up using to get my 9400GS working. It's nice and simple to use. :)

---

### Post by Paul41 on 2009-10-23
When you first turn your computer on (or restart it) grub boots your system. Depending on how you have things set up you will either see the grub menu (I'm guessing you don't) or you will get a quick message about grub telling you how to show it. Once you get to the menu recovery mode will be one of your options.

---

### Post by Cerafem on 2009-10-23
Yeah, there was nothing of that sort, it just tried to start, quit, then it would let me login and stuff, but it was always on a black screen with white text.

an example, has nothing to do with this, but should show what I am talking about:
[http://2.bp.blogspot.com/_GY7CglwXFAQ/SC9Lo0PJGcI/AAAAAAAABaA/hP4iLh4_qro/s400/222.JPG](http://2.bp.blogspot.com/_GY7CglwXFAQ/SC9Lo0PJGcI/AAAAAAAABaA/hP4iLh4_qro/s400/222.JPG)

---

### Post by Paul41 on 2009-10-23
Press the escape key after you computer loads the bios. [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by Cerafem on 2009-10-23
ok, I installed EnvyNG, but when I run, it asks for my password, I give it, then I don't hear from it again.

---

### Post by Paul41 on 2009-10-23
> **Cerafem said:**
> ok, I installed EnvyNG, but when I run, it asks for my password, I give it, then I don't hear from it again.

What happens if you start EnvyNG from the terminal and then run it. Do any errors show up in the terminal?

---

### Post by Cerafem on 2009-10-23
sorry, I was reading more about Envy, it says some stuff about adding repositories, but I need the location...

but this is what shows up:


```
alex@alex-desktop:~$ sudo envyng -t
Traceback (most recent call last):
  File "interface.py", line 428, in <module>
    a = Interface()
  File "interface.py", line 126, in __init__
    self.abstract = abstraction.Abstraction(progress, True)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 39, in __init__
    self.driverDetails = self.hardware.selectDriver()
  File "/usr/lib/python2.6/dist-packages/Envy/detection.py", line 320, in selectDriver
    compatibleDrivers.setdefault('fglrx', []).append('xorg-driver-' + choice)
TypeError: cannot concatenate 'str' and 'int' objects
alex@alex-desktop:~$
```

---

### Post by Cerafem on 2009-10-23
Well thanks for the help guys, I will get back on later tomorrow, unfortunately I have other things that I have to go do.  Feel free to post more solutions in my absence though. :)

---

### Post by Cerafem on 2009-10-24
All right, I am back.  What can I do now?          :confused:

---

### Post by Cerafem on 2009-10-24
OK, no one has responded for a little while.  I will just recap.

I need graphics drivers for Ubuntu 9.04, card is XFX GeForce GTS 250.

I tried to use EnvyNG like others suggested, but the site says something about enabling the repositories, which it does not tell me where they are.  When I run it, I give it my password, then it doesn't do anything else.  While running from the terminal, It gives me this error at the end (a full version of what the terminal says is a couple posts up):
```

TypeError: cannot concatenate 'str' and 'int' objects
```, which sounds like python cannot run it because it perhaps needs to typecast, or (very unlikely) has a bug.

I have very little experience here, and need others to help me.

---

### Post by Paul41 on 2009-10-24
See if this helps any.

[https://help.ubuntu.com/community/NvidiaManual#Installation%20with%20Envy/EnvyNG](https://help.ubuntu.com/community/NvidiaManual#Installation%20with%20Envy/EnvyNG)

---

### Post by Cerafem on 2009-10-24
it never makes it to that screen.

also, if I follow this:

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

will it work?

---

### Post by Cerafem on 2009-10-24
OK, thanks for the help, it seems that in jaunty, the problem I previously encountered no longer applies.  Hardware Drivers installed it and after a reboot, it works fine.  If I wasted your time, sorry, but I didn't want to have the same problem again.

---

