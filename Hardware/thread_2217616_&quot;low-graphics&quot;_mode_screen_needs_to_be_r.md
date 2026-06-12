---
title: "&quot;low-graphics&quot; mode screen needs to be rethought"
date: 2014-04-18
forum: Hardware
---

### Post by hellslinger on 2014-04-18
I'm not sure if this issue is specific to Ubuntu or is an Xorg thing. However, being that it is release time for 14.04 and Ubuntu has made great strides in usability, I thought I'd leave this message here. 

In the past few days, I have installed 14.04 on 4 different machines. Every machine that I have upgraded has started up into "low-graphics" mode, regardless of what video card/driver the machine has. Two of the machines have been Intel i915 and the other two are nvidia (both nouveau and binary produce the same results).

On the intel machine, I had to install fresh after formatting for lightdm to startup correctly. 

Even after installing nvidia-current on the other two, after nouveau would not allow progress beyond "low-graphics", the low-graphics warning still comes up. This is after I am able to stop lightdm, start i3 or another desktop environment from the command line with everything working correctly. I'm even able to see the NVIDIA logo show up before the window manager loads and OpenGL acceleration works, etc. 

According to this post: [http://askubuntu.com/questions/239149/the-system-is-running-in-low-graphics-mode-i-get-this-message-when-i-boot-my-u]("http://askubuntu.com/questions/239149/the-system-is-running-in-low-graphics-mode-i-get-this-message-when-i-boot-my-u") the presence of /etc/X11/xorg.conf.failsafe is enough to cause "low-graphics" to appear.

I have encountered low graphics mode over the years, sometimes for good reason, and lately, for apparently no good reason. Here's what I've noticed that puzzles me:

- The only useful output accessible from this screen is Xorg log and errors by clicking "Troubleshoot". However, if in the case that there isn't anything wrong, there is no helpful output.
- The first option, continue in low graphics mode for one session (or something like that), has never worked for me. Not even once. Why bother?
- The option to reconfigure has not once worked for me either. I have tried both options, the only result is the window reappears with exactly the same options. If something is failing to cause this window to reappear, shouldn't we see an error message or something?
- Exit to console login has only worked once. I have tried it every time.

Surely I'm not the only person to notice that this message is a _frustrating_ buffet of false hope. There is nothing more irritating than a bunch of menus and options that do nothing, produce no output, yet claim to do what you need. The names are misleading. "Troubleshooting" the option is not the same thing as "view logs" but THAT is what it does and NOTHING more.

If the "low-graphics" warning was replaced by a simple text file that gave the user instructions on how to get the right drivers installed or provided a way to stop lightdm and drop down to a console that actually worked, it would be a huge improvement. 

Finally, locking lightdm's bootup by the existence of /etc/X11/xorg.conf.failsafe, and not telling anyone, is madness. xorg.conf.failsafe implied (at least to me) that there is a fallback file in case things don't work, but I wouldn't expect that its existence means it will block lightdm forever until it is gone. I'm a fairly experienced user, but how is anyone supposed to guess that this is how it works? I apt-get purged lightdm and this file remained. There has to be a better way to signal lightdm than this...

---

### Post by grahammechanical on 2014-04-18
I have had the same experience but not lately and I have been running Trusty Tahr for all of it development cycle. There can be problems with kernels and Xserver upgrades that result in a "low graphics mode" and I agree with you it is completely useless.

Something else that is completely useless, is Recovery mode>FailsafeX. That is completely broken as far as I am concerned. There is one bright hope - MIR. It will replace Xserver, LighDM and Compiz. Someone will then have review Recovery mode. FailsafeX will have to go because the Xserver will not longer be there.

The Ubuntu developers have very busy with Ubuntu phone and tablet code writing and testing. During the next development cycle (26 weeks) they will work on converging the phone/tablet code on the desktop code. It is during the next 6 to 12 months that something will have to be done about Recovery mode.

Regards.

---

### Post by hellslinger on 2014-04-18
Thanks for the reply, graham. I am looking forward to MIR. 

I was able to fix the problem. Dumb me, I didn't realize there is a /var/log/lightdm/ log for lightdm. It was looking for unity-system-compositor from some old config files. apt-get purge unity-system-compositor took care of that and then it booted. It was very strange that the remnants of this package were present on all of these old systems. Perhaps the developers can add a check somewhere in a script to fix this problem.

Unity 7 with nouveau and nvidia is very, very fast and responsive, faster than it has ever been. Compliments to the Unity team.

---

### Post by lucas-bertolotti on 2014-04-19
Is there an official solution for this problem?

---

### Post by grahammechanical on 2014-04-19
> **lucas-bertolotti said:**
> Is there an official solution for this problem?

What problem specifically?

There can be many reasons that we get "low resolution mode." In the case of the OP it was due to a conflict with some old configuration files. I do not think that unity-system-compositor is installed by default. It is connected with Xmir/Mir. Months ago it was possible to test Xmir on Ubuntu. Doing that will bring in unity-system-compositor. At the time it was hoped that Xmir would be set up by default in 14.04 but that idea was dropped. If we wish to test on 14.04 a Unity 8 preview session then we need to specifically install it. That will bring in unity-system-compositor. I have it installed but it does not affect LightDM on my system.

In my case I got low resolution mode due to a mismatch in an upgrade to both the Linux kernel and the Xserver during my testing of Trusty Tahr. I also experiment with FailsafeX. So, I know it is broken. No need to fix it as X will be gone within 6 to 12 months.

Regards.

---

### Post by lucas-bertolotti on 2014-04-19
I tried a lot of methods to solve this issue, to no avail, last thing I found was this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132), but I was wondering if Canonical didn't post an official method for solving this "low-graphics" screen (after all 14.04 is a LTS release).

---

### Post by lucas-bertolotti on 2014-04-21
So any news from the front? One thing I noticed searching the web for answers is that multiple problems seems to associated with this same screen, meaning that there's no general solution for this issue.

---

