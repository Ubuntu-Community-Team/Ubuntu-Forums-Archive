---
title: "How to select and install correct NVIDIA driver bin binary from help.ubuntu.com"
date: 2019-01-05
forum: Hardware
---

### Post by spazz2 on 2019-01-05
How to select and install correct NVIDIA driver bin binary from help.ubuntu.com

Hi All.
I inquired in another thread about installing proprietary NVIDIA graphics drivers.
I was initially trying to do it using the .run file from the NVIDIA website. 

I was told not to do that  by oldos2er , who referred me to this link,
to install these drivers using binaries.
[https://help.ubuntu.com/community/Bi...erHowto/Nvidia](https://help.ubuntu.com/community/Bi...erHowto/Nvidia)

I know this is probably a dumb question, but I am entirely at a loss as to which bin package to download.
I have quickly read through the entire guide , trying to find an answer as to which bin to select,
but cannot find the info.
I have opened every single link at the top of the page, for all the various bins.
Almost all of them mention "Cosmic Cuttlefish" which I am running (ubuntu studio).

As far as I can tell, these only provide info for which OS / ubuntu version to install drivers for -- but not for which gfx card these are for in particular.

I am running
Description:    Ubuntu Studio 18.10
Codename:    cosmic
x86_64

The graphics card is
NVIDIA Corporation G71GL [Quadro FX 1500] (rev a1)

I apologise if this is a painfully obvious question, but I am a bit bewildered .
Would definitely prefer not to install the wrong thing for something like this.
Ta.

=================
_**EDIT :**_
My main problems with the default nouveau driver in Ubuntu and reasons for wanting the official NVIDIA driver over are : 
1) The nvidia card _**fan speed**_ is constantly at maximum speed, and very loud. 
I cannot control the fan speed with the nouveau driver (as far as I know.)
2) If I put the computer to sleep or into hibernate, the display will go to a white / broken signal image, and I cannot bring it back.

Thanks.

---

### Post by mikasu on 2019-01-06
so I guess that you know that you need to use "sh" to run that .run binary... Next is, because I helped someone who had no choice but that to get a proper display in a standard boot, get in failsafe/recovery mode and execute "sh <file-driver-name>.run" and then it should work. The driver should install properly without errors. As opposed to when the OS is working where the driver installation will say "Could not install the driver" or something. If that was your issue. But you can try while the OS is running, if it works for you then good, reboot and then blacklist the nouveau driver and you have your Quadro setup and working. That's just about installation... but I don't know about all the other stuff... I never got my hands on a Quadro, not even a real GTX (I only got a laptop NVIDIA GPU but that gave me some experience with their drivers...). Also, by the way, your link goes nowhere...

---

### Post by mikasu on 2019-01-06
I probably got it wrong... were you looking for which driver version? If so, I would say always go with highiest number. Right now it should be 410 or 415. And use the graphics driver ppa for more up-to-date drivers. The most updated version right now should be the 415 so I believe what you would like to do is "sudo apt install nvidia-driver-415". Then, just a good old classic reboot and cross your fingers you don't have any issues. The "login loop" or "can't login" issue can be fixed by launching a terminal with F7(if I recall correctly) login into the terminal then delete the .ICEAuthority in your home directory (or something similar, it will end with Authority anyway) and login again like you do normally.

---

### Post by CatKiller on 2019-01-06
You don't download the driver from the wiki page; that simply gives instructions.

The automatic driver tool will tell you which is the recommended driver version for the particular card.

In this case, the version you want is 304, since support for that card was dropped from subsequent versions.

---

### Post by Yellow Pasque on 2019-01-06
The Nvidia 304.xx driver is officially EOL and was not included in Ubuntu 18.04. You can find an unofficial version patched to work with Ubuntu 18.xx using this PPA:[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
There's no guarantee the 304.137 driver will continue to function with unofficial patches moving forward. If you intend to run the proprietary driver, you may be better off sticking with Ubuntu 18.04.1 where the kernel and Xserver versions stay stable for the next 4 years.

You could also try the open-source nouveau driver before assuming you need the proprietary 304 one. It does work well on some older Nvidia GPU's. nouveau ran well for me on an 8400GS, which is similar vintage (one gen newer) to your GPU.

---

### Post by mikasu on 2019-01-06
Is this card only for display? Because I don't see why you would use it for any kinds of workloads since it's age... if so, nouveau should do well... if nouveau is terrible for you, then Temüjin and CatKiller got you

---

### Post by deadflowr on 2019-01-06
The complexity of patching the 304 driver for Ubuntu 18.04:
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic]("https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic")
But I would run with the open-source nouveau drivers unless the situation is unbearable (ie, locks up, freezes, tearing, etc)

---

### Post by Yellow Pasque on 2019-01-07
> **deadflowr said:**
> The complexity of patching the 304 driver for Ubuntu 18.04:

I would have thought that the PPA I linked would have taken care of that. If not, then they are not doing their job :\

---

### Post by mikasu on 2019-01-07
I just looked at the PPA on it's launchpad page, they still provide the 304 driver.

Here is the launchpad page (which also explains how to add the ppa) : [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by spazz2 on 2019-01-10
Hi Mikasu. Thanks !
No, I am ignorant and was unaware of everything you just mentioned, but it makes sense.
Still at the very beginning of learning linux command line  !

Yes, I was actually looking for the correct driver version in that list / link I provided -- as it only mentions NVIDIA drivers for Ubuntu versions, nothing to do with what actual graphics cards I require the driver for.

All your other info was really generally useful though , and stuff I didn't know!

My main problems with the default nouveau driver in Ubuntu and reasons for wanting the official NVIDIA driver over are : 
1) The nvidia card fan speed is constantly at maximum speed, and very loud. 
I cannot control the fan speed with the nouveau driver (as far as I know.)
2) If I put the computer to sleep or into hibernate, the display will go to a white / broken signal image, and I cannot bring it back.

PS. I am unsure what you mean about "is it only for display" ?
Or do you mean for improving performance of system generally ?
Yes, it is for display and video editing and just having a better performing system.
I know there are other clever uses of graphics cards, but I'm not doing anything too fancy or clever with it. 
Just the basics that it is for.
**What other "workloads" would you be referring to ?** 

Some good general info you've given me there about .run files and logging directly into terminal on reboot, and about removing a bad install.
Thanks !

---

### Post by spazz2 on 2019-01-10
CatKiller  :
Thanks ! Obviously I did not click through far enough then !
I appreciate you doing my homework for me. 
I have misunderstood what that wiki page was telling me, and what was written by another contributor on these forums.
Thx heaps for clearing that up (:

---

### Post by spazz2 on 2019-01-10
Thanks for the information Temüjin !
That is a bit disappointing that it is EOL.
Is this patch unofficial ?
It appears to be from canonical. 
Or do you mean "not officially from NVIDIA".


I am not committed to the NVIDIA driver if I can make Nouveau work properly for me.
I have edited my reasons for seeking the NVIDIA driver in the Orig Post -- which are :


My main problems with the default nouveau driver in Ubuntu and reasons for wanting the official NVIDIA driver over are : 
1) The nvidia card fan speed is constantly at maximum speed, and very loud. 
I cannot control the fan speed with the nouveau driver (as far as I know.)
2) If I put the computer to sleep or into hibernate, the display will go to a white / broken signal image, and I cannot bring it back.


If I can find either a nouveau GUI or usable terminal commands to control fan speed, throttling, and can put my computer to sleep and make it wake back up without giving me a grey screen of death (which it currently does) then I would be okay with Nouveau. 
I'm in a hot-climate, so being able to put my PC to sleep / hibernate is a very useful thing for a healthy PC. 
Thanks again!

---

### Post by CatKiller on 2019-01-11
> **spazz2 said:**
> What other "workloads" would you be referring to ?

That would be the "other clever uses." It's called GPGPU.

> **spazz2 said:**
> If I can find either a nouveau GUI or usable terminal commands to control fan speed, throttling, and can put my computer to sleep and make it wake back up without giving me a grey screen of death (which it currently does) then I would be okay with Nouveau. 

There's [this]("https://wiki.archlinux.org/index.php/nouveau#Fan_control") on the Arch wiki:

> 
**Fan control**

 If it is implemented for you card you can configure fan control via /sys. 
```
$ find /sys -name pwm1_enable
/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/hwmon/hwmon1/pwm1_enable
$ readlink /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/driver
../../../../bus/pci/drivers/nouveau
```
pwm1_enable can be set to 0, 1 or 2 meaning NONE, MANUAL and AUTO fan control. If set to manual fan control, you can set pwm1 manually, for example to 40 for 40%. 
 **Warning:** Use at your own risk! Don't overheat your card!
 You can also set it by udev rule: 
```
$ cat /etc/udev/rules.d/50-nouveau-hwmon.rules
ACTION=="add", SUBSYSTEM=="hwmon", DRIVERS=="nouveau", ATTR{pwm1_enable}="2"
```


I don't know anything about suspend.

I'd imagine you'll be fine with the proprietary 304 driver from the PPA for the lifespan of 18.04. After that, who knows?

The situation with Nvidia is awkward. Their driver has been feature-identical with their Windows driver for a long time, essentially by making it the same as the Windows driver. That means that it does entirely its own thing, which isn't the same thing as everyone else is doing. The nouveau driver (which is reverse-engineered by volunteers) has always been a long way behind because most users are well-served by the proprietary driver and Nvidia are officially disinterested in open source drivers. They could make things a lot easier for the nouveau project, but they don't.

By contrast, Ati, as was, had a proprietary driver that wasn't that great, so there was a lot more momentum behind making an open source driver that worked well. Recently AMD have broadly embraced that driver and development is progressing well. Intel's driver has always been open source, and performs as well as they can make it.

That card isn't supported at all on Windows 10, for example. Nvidia would really prefer that you bought a new card.

---

### Post by mikasu on 2019-01-11
Hey Spazz2,
What I meant by "is it for display?" is pretty self explanatory, just to offload the task of displaying to a graphics card. I know some old GPUs can still do video editing, since those softwares rarely care about the age of the GPU, it should be okay to accelerate video rendering. The other workloads would be such as 3D rendering and gaming. This GPU, I doubt it will be strong enough for these tasks. Good luck with your driver installation!

---

### Post by spazz2 on 2019-02-16
[FONT=georgia]Hi all. [/FONT]
[FONT=georgia]I just wanted to thank you all very much for your responses. [/FONT]
[FONT=georgia]I'm sorry for my super late reply. [/FONT]
[FONT=georgia]I've tried a couple of solutions , which haven't worked, but I might have tried them incorrectly.[/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia]I will get back to you all later with details and outcomes of more attempts based on what you've all said, so I hope the thread remains open.[/FONT]

[FONT=georgia]I'm fresh out of time to spend hours(!) messing around at the moment though,[/FONT]
[FONT=georgia]with LOTS of tech college stuff to do -- study is heating up, and I'm behind.[/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia]**_I would also be open to any suggestions or articles about graphics cards which are very Ubuntu friendly / Linux friendly in general ?._** -- 
AMD Radeon ??
Intel?? 
As suggested ^^^
I'm certainly very unhappy with NVidia , and won't be purchasing any more products with their rubbish built in if I can avoid it (might be difficult, but anyway).[/FONT]
[FONT=georgia]
[/FONT]
[FONT=georgia][U][B]Temujin : 
[/B][/U]
I think I tried the correct PPA you linked, and it didn't seem to work after reboot. [/FONT]
[FONT=georgia]I may done it incorrectly, or not selected the correct thing. [/FONT]
[FONT=georgia]Will give it another go later.[/FONT]
[FONT=georgia]
=================
[/FONT]
[U][B][FONT=georgia]Catkiller :[/FONT]
[/B][/U][FONT=georgia]Thankfully, I did not pay for this particular card. [/FONT]
[FONT=georgia]It was donated by a friend at work.[/FONT]
[FONT=georgia]Given that I am slowly making the move to Linux on all my machines, there is no way I would ever purchase an NVIDIA card again (I have in the past), and would be very wary of any laptop that contains them --[/FONT]
[FONT=georgia]and would be dissuading people from buying such a product.[/FONT]
[FONT=georgia]This process and lack of compatibility is just crazy and gets a bit nightmarish ! I can't stand companies like that.
[/FONT]
[FONT=georgia]======================
[/FONT]
[U][B][FONT=georgia]Deadflowr --[/FONT]
[/B][/U][FONT=georgia]I will have a go later at the adufray patch article you linked me. [/FONT]
[FONT=georgia]Every time I think something will take 5 minutes , it takes me like 2+ hours (sometimes with no result).[/FONT][FONT=georgia]
[/FONT]
[FONT=georgia]Yeah, the nouveau driver is sadly a bit unbearable, as the fan speed is constantly maxed-out , which is very annoying to me -- also, not being able to put the computer to sleep and wake it up in a way that the gfx card switches back on) is bad news in my hot occasionally very humid climate.[/FONT]
[FONT=georgia]I mean, it works okay if you don't mind the fan buzzing at a bazillion rpm , and not putting your computer to sleep when it's raging hot (having to do full poweroff instead).[/FONT]

[U][B][FONT=georgia]I won't purchase any NVIDIA products in future 
(if avoidable).[/FONT][/B][/U]

---

### Post by CatKiller on 2019-02-16
> **spazz2 said:**
> Thankfully, I did not pay for this particular card. 
It was donated by a friend at work.
Given that I am slowly making the move to Linux on all my machines, there is no way I would ever purchase an NVIDIA card again (I have in the past), and would be very wary of any laptop that contains them --
and would be dissuading people from buying such a product.
This process and lack of compatibility is just crazy and gets a bit nightmarish ! I can't stand companies like that.


For the use case of someone who uses the latest graphics cards and then upgrades to something newer and shinier when it gets long in the tooth, Nvidia's approach is more-or-less fine. Their Linux driver supports cards from the time they're released, and for longer than their Windows driver does. The card you're interested in *is* 13 years old. The only problem from the user's perspective is that they're doing their own thing to keep it feature-equivalent with their Windows driver, which means that things they haven't got round to, like Kernel Mode Setting and Wayland, don't really work.

I'm excited by AMD's graphics driver work, and hopefully when it's time for me to upgrade they'll have made graphics cards that can keep up and graphics drivers that perform as well as they can. They're heading in that direction, but weren't quite there yet for my uses the last time I upgraded.

I'd only ever use integrated graphics in a laptop. Mixed graphics are a nightmare, whichever OS you're using. Till now, that's meant Intel, but AMD's APU work is promising.

Lots of people *do* take a stand on principle against Nvidia because of their lack of support for Nouveau, so you aren't alone in that. I'm not one of them, but I understand the position.

---

### Post by MartyBuntu on 2019-02-17
> **CatKiller said:**
> 

I'm excited by AMD's graphics driver work, and hopefully when it's time for me to upgrade they'll have made graphics cards that can keep up and graphics drivers that perform as well as they can.

Remember AMD/ATI's pledge to share their source code and work closely with the Linux Foundation to give users the best quality Linux graphical experience available?

That was over 10 years ago. I'm still waiting.

---

### Post by janeku2 on 2019-02-21
Hello,
I would like to continue this conversation with my Nvidia drivers problem. Maybe I am missing something but I just can't find something related with proper installing of Nvidia drivers on Ubuntu 18,04.2 ,
I recently bought HP 8440p with GT218 card on it (NVS3100) and I just can't instal these drifvers offered by System. Nouveau works good but kust before login screen my screen turns off and no login screen is displayed at all. I have to wake up my screen with FN+F9 or FN+F10 (screen brightness) so it could display login screen (nomodeset and acpi off in GRUB during boot shows that display works good and login screen appear but in lower resolution). I suppose something get wrong during boot sequence but I can't figure out.
Before this, I tried to install Nvidia driver (340.107) through system offered Sofware/Updates solution but my screen just keeped going blank after NVDIA's logo. Is there any good instruction or manual how to properly install these drivers in Ubuntu 18.04 ?
Any link and suggestion are welcome.
Regards,

---

### Post by Yellow Pasque on 2019-02-21
> **janeku2 said:**
> I recently bought HP 8440p with GT218 card on it (NVS3100) and I just can't install these drivers offered by System.

Your situation is very different than the OP's. The OP has an older card only supported by 304.xx drivers, which are now EOL.
It sounds like you are installing the drivers correctly, but they are not working. Start your own thread if you haven't already.

---

### Post by janeku2 on 2019-02-24
Yes I have already started,but looks like ono one is interested to help :(
There are two threads one in Hardware and other one in Installation&Upgrades 
[https://ubuntuforums.org/showthread.php?t=2412326](https://ubuntuforums.org/showthread.php?t=2412326)
[https://ubuntuforums.org/showthread.php?t=2412306](https://ubuntuforums.org/showthread.php?t=2412306)

---

