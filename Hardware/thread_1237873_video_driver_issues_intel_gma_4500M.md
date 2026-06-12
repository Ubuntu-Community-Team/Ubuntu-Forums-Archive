---
title: "video driver issues intel gma 4500M"
date: 2009-08-11
forum: Hardware
---

### Post by bdormaier on 2009-08-11
Hi, I am attempting to have a running version of ubuntu on my new laptop, a Lenovo U350.

While I have been able to find a lot of help, or stumble my way into a number of things to be setup for my laptop, I cannot seem to figure out how to address my driver issue.

The driver on the laptop is an intel gma 4500m.  I've tried changing the driver in xorg.conf to intel from vesa, but that results in me just getting a blank screen on restart.  This is primarily an issue because my laptop is a widescreen and vesa only gives me the options of 1024x768 or 800x600.  The resolution should be something more along the lines of 1366x768.

Any help is appreciated!

---

### Post by bdormaier on 2009-08-12
bump.

---

### Post by bdormaier on 2009-08-13
bump.

---

### Post by applemacmad on 2009-08-13
Try following [this]("http://ubuntuforums.org/showthread.php?t=1130582") guide through to part B (Safe/Optimal), the newer graphics drivers might help. Also, stick with intel, not vesa.

Other than graphics, how is the U350 in Linux? I'm thinking of getting one myself :)

---

### Post by bdormaier on 2009-08-13
aside from the video driver issues, it has run well in linux, much better performance than in Vista.  Though if you are a dual booter, it's nice that it qualifies for a free upgrade to 7.

As far as Ubuntu though, it has run well, (though I haven't done anything graphics intensive yet... figured not even worth it to try until I can switch off of vesa.

I'll take a shot at the instructions you sent and see how it goes.

---

### Post by bdormaier on 2009-09-27
To finish this up, I never found a solution in 9.04, but have been running the 9.10 alphas, which appear to have fixed the graphics driver issues. Still have a couple things that I'm trying to fix but I must say that anyone with a U350 really should consider Ubuntu as it is much more responsive than vista on the machine.

---

### Post by highfructose327 on 2009-11-26
bdormaier how is the support for the gma 4500m in karmic now? I am looking at a netbook with the 4500m
thanks

---

### Post by mrebanza on 2010-01-11
must say gma 4500m support is great in Ubuntu 9.10 Karmic . . . I have no complaints, compiz runs smooth . . . despktop effects, youtube in HD all flawless, Im on a toshiba satolit with the Intel® Graphics Media Accelerator 4500M . . . If your not using Ubuntu Karmic 9.10 than UPGRADE (or better yet do a fresh install) . . . By that netbook and Ubuntu it! You'll be glad you did!

:popcorn:

A little speed test... Like I said I am now running a Toshiba Satellite I bought myself for Christmas . . . Before this I was using an Acer Aspire One (also with the Intel GMA 450)

So I got my new Toshiba Satellite home...It came loaded with Windows 7, 3GB DDR3 Ram and a 360GB Hard drive... The Acer Aspire One is load with Ubuntu 9.10 Karmic, 1GB DDR2 Ram and a 120 GB Hard Drive.

So i decide to run a boot test... The Win7 took over 60 seconds to boot to the desktop while Ubuntu loads in just 23 seconds!!! 

Its crazy how much fast Karmic is than seven! 

Ubuntu 9.10 can turn any netbook into a speed demon ! ! !

---

### Post by vel_vasta on 2010-05-18
ok, nice one, but... I changed my laptop in a new one two days ago. So, I've put inside Kubuntu 10.04, but my Asus seems so slow...
Its graphic device is the Intel you mentioned above.
the GPU is
```
[COLOR=#000000][FONT=Arial][COLOR=#E0DEDB]Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)[/COLOR][/FONT][/COLOR]
```
Should I downgrade to the 9.10 :(
Thanks a lot
Enrico
[COLOR=#000000][FONT=Arial][COLOR=#E0DEDB][/COLOR][/FONT][/COLOR]

---

### Post by marquinos on 2010-12-30
This works perfect for my laptop ACER TM 5735 Graphic card T4500M, with Ubuntu 10.10 64 bits:
[http://ubuntuforums.org/showpost.php?p=10112062&postcount=6](http://ubuntuforums.org/showpost.php?p=10112062&postcount=6)
Best regards.

---

### Post by denied on 2011-01-03
Man after setting up my moms new Toshiba C660-D123 laptop with ati graphics card and getting some miss configures in brightness and all that she eventually got tired of all the problems.

Now i called the store and its possible to switch the computer or get the money back. Problem is for 350 euro you dont get a decent laptop with nvidia drivers. Found a few HP but not out in the store only web stores.

So im fearing i'll have to do another 3 day marathon to get the damned Intel Gma 4500M to work as she likes. I eventually solved most of my problems by installing OpenSUSE with the acpi option of, but then there are so many problems with toshiba and linux.

I see the topic is up to date and most of you have this damned problem, but is there any solution to it ? I remember when i tried to change the ubuntu load cd configures and wrote acpi=o (was going to write off) but then the screen just started to flicker like there was no tomorrow. Very weird since i hadnt even pressed enter yet...

---

### Post by lithopsian on 2011-01-04
The latest xorg Intel drivers are much more stable and perform better too.  You should find things much easier if you are on 10.04 or ideally 10.10.  I've heard some people still struggle with kernel modesetting ...

---

