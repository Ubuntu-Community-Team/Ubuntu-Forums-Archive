---
title: "Don't Have the Hardware to Support Unity"
date: 2011-09-15
forum: Hardware
---

### Post by Ozzy720 on 2011-09-15
Okay, so I'm relatively new to this kind of stuff.  I saw a friend using it and was very interested.  I installed it the same way he did (First I tried the Windows Installer) from the website, but, when I install Ubuntu 11.04, it says my laptop doesn't have the hardware to support Unity.

Then I tried to run it via booting from a Flash Drive.  Installed everything, made it bootable, and restarted my computer.  Unfortunately when I went to boot from my usb, it wouldn't work and said it couldn't find some file.

I have an HP Pavillion dv7 with Windows 7 Home 64-bit, with an AMD 1.9 Quad Core processor, 1.5GB dual graphics video card (ATI Radeon 6620G+ATI Radeon 6750M.  Also, a 1.5TB HDD and 8GB of RAM.

Any ideas on why this isn't working? :/

---

### Post by varunendra on 2011-09-16
To make the usb flash drive bootable, try [unetbootin]("http://unetbootin.sourceforge.net/"). The native live usb creator in natty has been very frequently reported to cause such problems.

For Unity support, installing proprietary drivers from ATI (if they exist for Linux) should work.

---

### Post by BicyclerBoy on 2011-09-16
Possibly problems with AMD version of 'optimus' graphics.
Your AMD CPU is a Llano A8 fusion APU ??

Check out: Ironhide, Bumblebee vga-switcharoo.
Catalyst AMD proprietary driver

A solution may be disabling the APU 6620G GPU in BIOS & then later using the Catalyst driver.
Good reading here:
[http://www.phoronix.com/scan.php?page=article&item=amd_llano_graphics&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_llano_graphics&num=1)

---

### Post by maul9999 on 2011-09-16
It is possible problem is your ATI video card, due to unsupport GLopen (Ubuntu need one to running).  Lunix only work better is Intel Video and Geforce.  Don't get GTX 4X0!  It have problem GLopen.  Here video card what i know it would be work better.  9600 GT (I used it which work great), GTX 2X0, GTX 5X0, and Intel Video from Intel i3 and i5.

---

### Post by varunendra on 2011-09-17
Ozzy720,

I am posting your question that you asked me via PM, and my reply here so that more people like you may get benefited:
[QUOTE=Ozzy720 (via PM)]In my post, you said to install the ATI proprietary driver for ATI  cards.  I've seen other people say this, but, I'm not sure how it works  with two operating systems, I've never don't this before.

Would I have to boot with Ubuntu and then uninstall the current Video  driver I have and install the open-source one while running Ubuntu?  Or  can I do that while running windows?

Or can I just install it using Ubuntu and have both drivers?

Any help would be lovely :)[/QUOTE]
Drivers are nothing but tiny piece of software that tell the OS how to use a particular hardware. Like any other software, they are either embedded, or installed on top of the Operating System. As such, they are OS dependent, are different for different OS installations, and thus do not interfere with each other. If there are multiple Operating Systems installed on a system, each of them will need its own separate set of drivers for the system hardware. Which means:

[LIST]
[*][COLOR=Navy]If, by "current Video Driver" you mean the one you have in Windows, then you **don't have to** uninstall it. It has nothing to do with Ubuntu or any other OS installed in parallel to existing Windows on which it is installed.[/COLOR]
[/LIST]

[LIST]
[*][COLOR=Navy]Ubuntu will need its own driver for the ATI Radeon graphics and it has nothing to do with windows or any driver existing in windows.[/COLOR]
[/LIST]

[LIST]
[*][COLOR=Navy]Since it has to be installed on Ubuntu (in case the default one doesn't work for you), you have to be in Ubuntu while doing so. You can not do it while being in windows, because you can not install a driver in one OS while being in another.[/COLOR]
[/LIST]

[LIST]
[*][COLOR=Navy]As such, it is obvious now that you will install it using Ubuntu, and will have both (the ubuntu one and the windows one - in their respective partitions).[/COLOR] Now something more you should know:-
[/LIST]

[LIST]
[*]Usually, Ubuntu automatically picks up an "**fglrx**" driver for ATI graphics, which is already embedded in the kernel and thus does not need to be installed separately. As soon as you boot ubuntu, it will be loaded automatically in the background. The command to get a list of driver modules which are currently loaded for your hardware is: ```
lsmod
```
[/LIST]

[LIST]
[*]If this default "fglrx" driver is found unable to handle the graphics properly, then either you have to install a more suitable driver (most often proprietary) if available, or will have to compromise with reduced performance of the existing driver until a suitable one is released.
[/LIST]

[LIST]
[*]Whenever a known and tested more suitable proprietary driver is available for a particular graphics adapter, it is made available through the repositories and can be easily installed via "Additional Drivers" application in Ubuntu (found under "System Settings" in Natty).
[/LIST]

[LIST]
[*]If no suitable driver is found even in the "Additional Drivers" recommendation box, or the suggested one is buggy and causes problems, only then you need to proceed for manual steps to search and install one manually. This is the first case where complexity steps in for new users (not once you get used to it).
[/LIST]
Now as per the article that BicyclerBoy linked above ([http://www.phoronix.com/scan.php?page=article&item=amd_llano_graphics&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_llano_graphics&num=1)), it seems that Natty should be able to handle the 6620G graphics - with a catalyst driver if not with the default fglrx. Here's the community guide about how to install a catalyst driver manually: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If you face problems with graphics after installation, start a new thread with relevant topic and put your question there with as much details about your problem as possible.

For this one, we would really appreciate if you share with us how you solved your problem (marking it as [solved] means you did solve it - right?:)). That helps us and others to know exactly what may solve a similar problem.

If you still have any doubts, please ask in this or a new thread (if the question is irrelevant to this topic) and we'll be more than happy to help if we could.

---

### Post by Ozzy720 on 2011-09-17
Yeah, I guess I shouldn't have marked it as SOLVED.  I still have a few questions.

> Possibly problems with AMD version of 'optimus' graphics.
Your AMD CPU is a Llano A8 fusion APU ??

Umm, I'm not entirely sure.  But, it is an A8 processor, yes.  It has the Onboard Video card which is the 6620, and then a dedicated video card which is the 6750.  And with Crossfire (which apparently they can do, even though they're in different 100's series) it makes up the 1.5GB video memory.  So I'm not sure which one is the primary video card.  This is my first experience with dual graphics.

----

I'll try installing the drivers via Ubuntu and get back to you on if it works.  If it does, I'll put it back as SOLVED.  Sorry bout that confusion.

---

### Post by BicyclerBoy on 2011-09-17
When it come to video drivers in Linux everyone is confused most of the time.
[Varunendra]("http://ubuntuforums.org/member.php?u=1043629") has described/explained things very well.

I'm not so sure about crossfire working in Linux with APU...
The APU/GPU is more than just dual graphics..it is about sharing an output render buffer, power management, dynamic switching.

But at least your APU & discrete GPU are not competing companies.

Remember the APU graphics are about low power/battery life.
The discrete GPU will decimate it.

---

### Post by maul9999 on 2011-09-17
> **Ozzy720 said:**
> Yeah, I guess I shouldn't have marked it as SOLVED.  I still have a few questions.



Umm, I'm not entirely sure.  But, it is an A8 processor, yes.  It has the Onboard Video card which is the 6620, and then a dedicated video card which is the 6750.  And with Crossfire (which apparently they can do, even though they're in different 100's series) it makes up the 1.5GB video memory.  So I'm not sure which one is the primary video card.  This is my first experience with dual graphics.

----

I'll try installing the drivers via Ubuntu and get back to you on if it works.  If it does, I'll put it back as SOLVED.  Sorry bout that confusion.

It is not crossfire that you have 6620 and 6750, it is called Dual Graphic.

---

### Post by Ozzy720 on 2011-09-17
> It is not crossfire that you have 6620 and 6750, it is called Dual Graphic.

It's not?  Well the internet says "The Hybrid CrossFireX is a technology allowing the IGP, or Integrated Graphics Processor, and the discrete GPU, or Graphics Processing Unit, to form a CrossFire setup to enhance the system capability..."

[s]And plus, why would they sell a laptop with Crossfire capability, and not actually have it doing anything?  I have the option to turn it on/off, and it was on to begin with.  So I figured it was that^ since this computer recognizes both an Integrated and Discrete video card (512MB and 1GB respectively) as being installed.[/s]

EDIT:  Hmm, I did some more research into it, and it says that only 7 and 8 chipsets can use the Hybrid Crossfire, but mine is a 6620 so I guess that doesn't make any sense.  So, if it's not Crossfire, what are Dual Graphics good for?  Does it just split up the graphical workload automatically so my system doesn't have to work as hard?  Are there any other benefits to this Dual Graphics thing?  Or would it be better to just get a laptop with a better processor and just a 1GB dedicated vcard?  I bought this mostly for AutoCAD and games like Starcraft and WoW.

---

### Post by Ozzy720 on 2011-09-17
Hey guys!  I'm posting this via Ubuntu.  Which means I got everything up and running smoothly thanks to your help.

All I did was go to run the Additional Drivers program and it searched and found an update to the driver I was using so I downloaded and installed it and everything is running smooth.

Now, before I mark this as solved, I had one more question.

While booting up Ubuntu, on my screen a few lines pop up that say

BAD LUN (0:1) then followed by some numbers and multiple BAD LINE (#:#)'s.  Any ideas on what that's all about?

---

### Post by varunendra on 2011-09-17
> **Ozzy720 said:**
> Hey guys!  I'm posting this via Ubuntu.  Which means I got everything up and running smoothly thanks to your help.

All I did was go to run the Additional Drivers program and it searched and found an update to the driver I was using so I downloaded and installed it and everything is running smooth.

Now, before I mark this as solved, I had one more question.

While booting up Ubuntu, on my screen a few lines pop up that say

BAD LUN (0:1) then followed by some numbers and multiple BAD LINE (#:#)'s.  Any ideas on what that's all about?
Nice to hear that!

I've no idea about the error message you mentioned, maybe the complete message could make some more sense.

Anyway, I'd like to know one thing - how did you install? Did unetbootin work for you or is it a WUBI install? Or a standard LiveCD installation?

And one thing I'd like to suggest. It's not relevant...., but I don't know why I feel the urge to say this - have a look at [remastersys]("http://www.geekconnection.org/remastersys/"). You can make a live backup of your system (a live DVD iso). In case an update or something breaks the system, you can restore it from that DVD. Not that I'm doubtful about your system's stability, but nevertheless, a handy backup is always a good thing to have, even better if it is a 'live dvd'! And oh, for natty, you may need to manually download its [.deb]("http://www.geekconnection.org/remastersys/repository/karmic/") package to install.

I'll get back to my hole now, hope someone can explain the error message you got.

---

### Post by maul9999 on 2011-09-18
> **Ozzy720 said:**
> It's not?  Well the internet says "The Hybrid CrossFireX is a technology allowing the IGP, or Integrated Graphics Processor, and the discrete GPU, or Graphics Processing Unit, to form a CrossFire setup to enhance the system capability..."

[s]And plus, why would they sell a laptop with Crossfire capability, and not actually have it doing anything?  I have the option to turn it on/off, and it was on to begin with.  So I figured it was that^ since this computer recognizes both an Integrated and Discrete video card (512MB and 1GB respectively) as being installed.[/s]

EDIT:  Hmm, I did some more research into it, and it says that only 7 and 8 chipsets can use the Hybrid Crossfire, but mine is a 6620 so I guess that doesn't make any sense.  So, if it's not Crossfire, what are Dual Graphics good for?  Does it just split up the graphical workload automatically so my system doesn't have to work as hard?  Are there any other benefits to this Dual Graphics thing?  Or would it be better to just get a laptop with a better processor and just a 1GB dedicated vcard?  I bought this mostly for AutoCAD and games like Starcraft and WoW.

Chipset is not video card, it is motherboard.  6620 is mid-end video card.  

It like Hybrid yes, but it didn't mean to call Crossfire every if it is on Dual Graphics.  Wiki is all wrong, I don't believe it and neither you should.  CrossFire is pair up with same GPU.  With Dual Graphics will boost up your PCIE video card or dedicated video card.  Which mean Dual graphics will make it fastest than what normally speed is dedicated video card or PCIE.  "utilizing the processing power of both discrete and integrated graphics processors" Gigabytes website.  

If computer have Dual Graphics and other computer don't have Dual Graphics.  Which is fastest video card?  Computer with Dual Graphics.

---

