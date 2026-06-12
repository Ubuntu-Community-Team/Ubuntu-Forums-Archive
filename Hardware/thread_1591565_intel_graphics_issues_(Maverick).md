---
title: "intel graphics issues (Maverick)"
date: 2010-10-09
forum: Hardware
---

### Post by pixnaps on 2010-10-09
Background: I have a Toshiba Satellite A135-S4527 with dual-core processor, 1 gb ram, and Intel 945GM graphics.

Games like Lincity-NG and Eschalon worked on this laptop back in the days of Hardy.  In Lucid, I found that my computer would often crash into low-graphics mode (especially if I tried playing Lincity-NG).  So I upgraded to Maverick RC, which seemed to solve that problem, but introduced others (e.g. the [can't start Lincity-NG]("https://bugs.launchpad.net/ubuntu/+source/libphysfs/+bug/588301/") bug).

Anyway, now I try playing Eschalon Book II, and it runs extremely sluggishly (even when I choose all the lowest graphics options).  I assume the problem is my Intel graphics.

I tried adding the x-swat "X updates" PPA, but it doesn't seem to help. (I'm not sure it updated properly, as two packages were held back: xserver-xorg-video-ati and xserver-xorg-video-radeon.  Do I need those for an Intel graphics card?)

I even tried xorg-edgers, but had to ppapurge it since it caused my computer to crash into low-graphics mode on startup.

Any suggestions?

---

### Post by pixnaps on 2010-10-09
More technical details, in case it helps:
```
$ lsmod |grep video
video                  18712  1 i915
output                  1883  1 video

```
the first lines of output from lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

Let me know if more diagnostic info is required!

---

### Post by pixnaps on 2010-10-10
*bump*

---

### Post by pixnaps on 2010-10-10
*bump*

---

### Post by pihbar on 2010-10-11
You can start ubuntu in recovery mode and then try to troubleshoot with generic video drivers in place. I recommend changing the driver to vesa for the time being, or installing a more recent version of intel drivers. I'm about to do this myself.

---

### Post by james_xxx on 2010-10-12
I have a Dell Inspiron E1505 with the same graphics chipset, and the graphics here seem much more sluggish in Kubuntu 10.10 than in 10.04.

One odd issue is that although the Kwin compositing manager is turned on in System Settings, it is not on when I log in. I have to manually turn it on afterward. Desktop Effects then work, but again, noticeably more sluggishly than was the case in Lucid.

Unless a fix can be found in the next several days, I'll likely be going back to Lucid on this machine.

---

### Post by james_xxx on 2010-10-12
I cannot believe there have not been a lot more posts relating to this issue.

Performance on this laptop since installing Kubuntu 10.10 is just horrible.

Images sometimes do not load correctly in a browser, and graphics are lagging in many other ways.

Pretty awful.

I hope a fix can be found for this.

---

### Post by Marceau on 2010-10-12
I think I may be suffering from the same. It is impossible for me to turn on compositing. I tried with Compiz, and then Metacity, and the latter stays on about 5 seconds on boot and then turns off.

I'm not sure if this may be related, but I get the following error on startup: 

```
modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory
```

This is a fresh install of Maverick UNE on an Asus EEEPC 1000HE with (I believe) Intel 945.

---

### Post by klemperal on 2010-10-13
I'm also running an intel 945 and can't get the desktop effects working.

---

### Post by gregbair on 2010-10-13
The reason you guys are having problems with desktop effects is because Ubuntu decided to go with fbdev drivers on some Intel graphics cards for Maverick.  fbdev does not support GL graphics, which compositing needs.

See:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492/comments/260](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492/comments/260)

---

### Post by klemperal on 2010-10-13
Is there a fix for us then?  Might you know how can we change back to the drivers that worked before?

---

### Post by Calorus on 2010-10-14
Yup this is all kind of bad form, I think - to have a seemingly platform  independent project and then to skew it by preloading it with nVidia  stuff whilst simultaneously moving to less supportive Intel drivers.

Desperate for a solution.

---

### Post by ianmillington on 2010-10-14
Same here - Kwin desktop effects which were passable in Lucid, are now formally disabled as the system is too slow. This happened on upgrade to kubuntu 10.10.

In KDE there is an option to turn off the check that does this but I've not checked it yet.

---

### Post by pixnaps on 2010-10-14
Marking thread as solved -- it turns out my problems were due to Software Sources [assigning me to a bad mirror]("http://ubuntuforums.org/showthread.php?p=9972476"), and hence my system hadn't updated properly.

---

### Post by james_xxx on 2010-10-14
pixnaps,

Dude, if you have the graphics adapter you say you have, your problem is not solved.

There rest of us are using good mirrors, and the problem is still here.

You may be able to get along generally, if you keep desktop effects turned off, otherwise you'll have a large mess on your hands.

I am still hoping that some fixes will appear soon. If that does not happen, I am either switching distros, or going back to 10.04 on this laptop.

---

### Post by ravi.xolve on 2010-10-15
How did you solve it? Please tell that. My laptop is as unusable as a remote dumb terminal.

I posted similar problem: [http://ubuntuforums.org/showthread.php?t=1595818](http://ubuntuforums.org/showthread.php?t=1595818)

---

### Post by pixnaps on 2010-10-15
There may be other intel graphics issues that aren't solved.  But the games I was concerned about (in my original post) are now playable, since I changed my software sources mirror to the standard US server, and got all the updates.

---

### Post by kingmanowar on 2010-10-15
I have the same kind of issues on my eeePC 1000h. Glxgears is really jerky, however if I keep moving the mouse cursor while running it, it's getting faster and smoother and gets sync with the screen at 60fps. As soon as I released the mouse the framerate drops and glxgears is getting jerky again.

On lucid I had a score of about 1500 on glx gears. It dropped to 200-250 on maverick. I am not new to ubuntu, I have been using it since Dapper on different computers. I know that glxgears is not a benchmark....I don't care much much about the score...but it should be at least smooth. I used top to see if any process was overloading the cpu. Direct rendering is enabled according to glx info. I am not sure what to try.

I went back to lucid for now. I also have issues with my wifi card but it is a known problem and easy to fix.

If anyone is running maverick on a eeePC 1000h without any issue, I would be glad to know it.

Thanks

Eric

---

### Post by james_xxx on 2010-10-16
OK, here is what worked for me..

See post #93 by ahanssen: 

[http://ubuntuforums.org/showthread.php?t=1592245&page=10]("http://ubuntuforums.org/showthread.php?t=1592245&page=10")

Installing this kernel has resolved 90%+ of the problems I was experiencing with Maverick and my mobile Intel graphics adapter.

I stumbled across this just in the nick of time, as I was planning to start working on reverting back to Lucid at some point this evening.

Hope this helps someone else!

---

### Post by mtrivs on 2010-10-18
> **kingmanowar said:**
> I have the same kind of issues on my eeePC 1000h. Glxgears is really jerky, however if I keep moving the mouse cursor while running it, it's getting faster and smoother and gets sync with the screen at 60fps. As soon as I released the mouse the framerate drops and glxgears is getting jerky again.

On lucid I had a score of about 1500 on glx gears. It dropped to 200-250 on maverick. I am not new to ubuntu, I have been using it since Dapper on different computers. I know that glxgears is not a benchmark....I don't care much much about the score...but it should be at least smooth. I used top to see if any process was overloading the cpu. Direct rendering is enabled according to glx info. I am not sure what to try.

I went back to lucid for now. I also have issues with my wifi card but it is a known problem and easy to fix.

If anyone is running maverick on a eeePC 1000h without any issue, I would be glad to know it.

Thanks

Eric
I too have a 1000he (I believe it is the same exact thing as the 1000h) and experienced the mouse phenomenon. I saw that when I moved the mouse the gears did seem a lot less "jerky".  

Has anyone tried the fix?

---

### Post by kingmanowar on 2010-10-20
I tested the 2.6.36 kernels but it did not improve the issue with glxgears and 'mousecursor'
I will try to investigate more on that, switching back to lucid is not the solution. Any help is welcome of course.

---

### Post by klemperal on 2010-10-20
I tried the suggested kernel as well as the latest kernel that showed up in updates and I can't get desktop effects working in either one.

---

### Post by kingmanowar on 2010-10-21
I have tested the kernel 2.6.36RC7 on my eeePC 1000H and it does not improve the jerkiness of glxgears. glxgears is running smooth again and in sync with the monitor if we move

I did the same test with Ubuntu Mint 10RC and Fedora 14 beta and I have the same issues. It is certainly an issue with the Kernel/Xorg/Intel driver i915 and not only ubuntu.

---

### Post by klemperal on 2010-10-21
Why is this thread marked as solved?

---

### Post by james_xxx on 2010-10-21
Marking this thread as solved was OP's decision.

Did not make any sense to me, either.

He claims he just had issues with how his repos were configured, and got that fixed. However, if he is using one of these mobile Intel graphics adapters, his problem did not get solved.

By the way, the 2.6.36 kernel was released today. I installed this kernel on my laptop, booted up using that kernel, only to find that it didn't improve anything with regards to my Intel graphics issues.

---

### Post by kingmanowar on 2010-10-21
I am not sure if you have noticed, but the kernel 2.6.35 has been officially back ported to lucid. I have installed it and everything is fine. Now I am wondering if the issue is only related to the kernel.

---

### Post by drodiger on 2010-12-09
I think there is a problem with kernel and intel drivers. I have all sorts of problems with my laptop with Intel Graphic card. For example, it didn't detected some of the projectors. I resolved this with this tip: [https://wiki.ubuntu.com/X/KernelModeSetting/]("https://wiki.ubuntu.com/X/KernelModeSetting/").
But I still have problems, that my screen is blank when booting starts. What I do is I restart (Ctrl-Alt-Del) several times, until I get the screen. Sometimes I need to boot only once, and sometimes even 7-8 times.

When I finally get to login into X, if I connect external monitor, it is not detected and then I run xrandr -q, and it gets detected, but then I have blank screen on my laptops LCD. But X thinks that my laptop monitor is fine, since I can move windows from external monitor to laptop monitor...

This is why I still wait on following [bugs]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453") to be resolved.

My 2c

---

### Post by mitchellcipriano on 2010-12-18
I also have the same problem on a ThinkPad. Has anyone found a solution?

---

### Post by u b u n t u k u on 2010-12-29
Fixed the issue with latest xserver-xorg-video-intel from glasen ppa :cool:, read here: [http://ubuntuku.org/10/how-to-fix-intel-graphics-issues-in-kubuntu-maverick/](http://ubuntuku.org/10/how-to-fix-intel-graphics-issues-in-kubuntu-maverick/)

---

### Post by crazy ivan on 2011-02-07
Issues with i945GM here as well (compiz crashes when turning a connected screen to higher resolution).

Found out that this is an issue related to the [limited capacities of my card]("http://ubuntuforums.org/showthread.php?t=1683179").

---

