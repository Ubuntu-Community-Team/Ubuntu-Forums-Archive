---
title: "Problem to setup external monitor with Ubuntu 9.10 on a Lenovo Ideapad S10"
date: 2009-12-04
forum: Hardware
---

### Post by kernel_script on 2009-12-04
Hello folks,

I'm having a hard time trying to set up my LG W2252TQ external monitor with Ubuntu 9.10 on my Lenovo Ideapad S10 Laptop. No luck, the monitor is recognised, but only the lowest resolution is available. How can I fix that? There is a way to make Ubuntu recognise the resolution properly? I want to mirror my Laptop onto the external monitor, to use my laptop as a traditional case computer, like a Mac Mini or a Dell Zino for example. What I want is to use only the external monitor, not the Laptop's, and use the external monitor max resolution, which is 1680x1050, which, doesn't work, it only gets the lowest resolution of the Laptop.

Please help. 

Thanks in advance for taking the time to read this and trying to help.

---

### Post by Perturbed Penguin on 2009-12-04
Hey there, this issue is unfortunately a common and unfixed one. See this thread:
[http://ubuntuforums.org/showthread.php?t=1305919](http://ubuntuforums.org/showthread.php?t=1305919)

*** You can probably get your external to work if you switch to Metacity rather than Compiz before connecting your external. Just in case you do not know how to do this here is what you need to do:

open up the run dialog by using alt+f2 and enter:
metacity --replace

this will switch you temporarily to the Metacity window manager, to switch back(only do this once you are done using your external) use this command:
compiz --replace

To make things easier, at least until there is a legitimate fix for this bug, you can add a custom application launcher to the menubar and enter these commands(as seperate launchers) as the run command for your launcher that way you can easily switch between the two when needed just by clicking on the launchers. ...You can also just install compiz fusion icon from the repos to get something similar to this.

Hope this helps, let me know if you have any questions other than "when will there be a fix for this". lol ;)

... as a side note, nice 'top, I've got a white S10 as well... works SO well with UNR 9.10 even with a bunch of Compiz effects turned on!!

---

### Post by kernel_script on 2009-12-04
Thank you very much for the help Perturbed Penguin : )

Well, I already knew about the **metacity --replace** command, but not it's use with such situation, thanks for the help.

Unfortunately, it didn't work, and I realised that my previous description lacks a key description piece: I want to mirror my Laptop onto the external monitor, to use my laptop as a traditional case computer, like a Mac Mini or a Dell Zino for example. Sorry about that, I should've said it earlier : / So, I'm still not able to assign the correct external monitor resolution, the only options is the lowest resolution.

Yeah! S10 is awesome! Mine is a black one : ) It even run some nice 3D games, like Warsow for example, really cool.

---

### Post by Perturbed Penguin on 2009-12-08
Ah, I am not familiar with what you mean by a traditional case comp, a Mac Mini or Dell Zino, lol, but if I understand you correctly you are looking to have the external adopt the exact native netbook resolution... in our case 1024x600? If this is what you are looking to do I think the problem you are running into is that the external monitor's resolution is incompatible with the netbook's native resolution, because of this you cannot physically mirror the two screens without dropping to the next highest laptop res that is compatible with both screens. This is the one advantage CRTs have over LCDs they don't have set pixels so they can adopt pretty much whatever they need to even if it looks awkward or stretched but LCDs have no such leeway. There is likely some external LCD screen out there that would be compatible with a 1024x600 resolution netbook screen but most are not(most are compatible with the similar 1024x800 but this won't work for this purpose) and therefore with most externals the system has to drop to the painfully low, but reliable 800x600 res. You probably already know this but I thought I'd let you know just in case. I suppose it is possible that your setup is dropping the res even lower to like 480x640 if your external is not compatible with an 800x600 res but I've never heard of such a thing happening. If you decide not to mirror, the screens don't have to be compatable and you can use the full res of the external or the full res of the internal. 

Is this what you are trying to do or did this answer any of your questions? Are you perhaps trying not to mirror but rather to use both screens as some sort of combined display where you can, for example, drag a window from the laptops screen to the external? Anyways let me know if this was any use to you.

---

### Post by kernel_script on 2009-12-08
No, that's not it, unfornunately : /
But thanks for trying to help man!

What I want is to use only the external monitor, not the Laptop's, and use the external monitor max resolution, which is 1680x1050, which, doesn't work, it only gets the lowest resolution of the Laptop.

My S10 has a mas res of 1024x576, the lowest I don't remember right now.

Sorry, I don't know how to explain very well : /

---

### Post by Perturbed Penguin on 2009-12-09
I don't give up very easily lol...
So you must be using the European version then? Anyways now I understand what you are getting at. So after refreshing the display list when you open the display settings window and even when you set the laptops screen to be off and redetect displays the external monitor still isn't detected at its full resolution?

I know with past Ubuntu versions I have had similar, if not the same problems, getting externals to be detected with their full resolution but that, for me, hasn't been a problem with Karmic, so if this is the case I don't know that I can help! :( If so... good luck, I'll be sure to post anything I come across that seems relevant!

btw, you are explaining fine, I am simply oftentimes incompetent. ;)

---

### Post by kernel_script on 2009-12-09
> **Perturbed Penguin said:**
> Anyways now I understand what you are getting at. So after refreshing the display list when you open the display settings window and even when you set the laptops screen to be off and redetect displays the external monitor still isn't detected at its full resolution?
Exactly!

No problem man, thank you very much for taking the time and trying to help :)

---

### Post by cprise on 2009-12-23
This worked for me:

[http://en.opensuse.org/Multiple_Screens_Using_XRandR](http://en.opensuse.org/Multiple_Screens_Using_XRandR)

Put your display into mirror mode first. Then executing a command like "xrandr --auto --output VGA-0 --mode 1680x1050" will push both displays to the higher mode (and if higher then your laptop's screen, you will see a partial display there but a full display on the external).

The page also tells you which GUI utilities for Gnome and KDE accomplish the same thing.

---

### Post by kernel_script on 2009-12-23
Thanks cprise, but unfortunately that didn't work :( I tried a lot, no luck, I could get a higher res, but not the native one (which would be the max res).

---

### Post by romanos.tsomos on 2010-05-06
Hi, I am aware this comes quite late, 
but I had had the exact problem 
(laptop with max res 1024x768 + external monitor connected, only wanting to use the external one, and not getting higher resolution)
and was JUST able to find the solution!

..quite "stupid" one actually.. :
I went into the Ubuntu Software Center, typed in "resolution", and then installed the "Resolution Switcher".

After having started it (its in Applications > Accessories) a small icon appeared on the taskbar. Clicking it allows you to change the resolution!

At last..
hope that helps

---

### Post by kernel_script on 2010-05-06
@romanos.tsomos
Hi, thanks for the help, unfortunately it didn't work. But I could finally make it work manually with the help of a forum post from here on Ubuntu Forums:

[http://www.uluga.ubuntuforums.org/showthread.php?p=9240037](http://www.uluga.ubuntuforums.org/showthread.php?p=9240037)

I adapted some of the configs and solved the problem as follows:

```
:~$ cvt 1680 1050 60
# etc etc etc (parameters I don't remember/have right now)
Modeline "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

:~$ xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

:~$ xrandr --addmode VGA1 1680x1050
```

VGA1 been my external monitor.

---

