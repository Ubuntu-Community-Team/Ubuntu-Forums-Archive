---
title: "ubuntu 11.10 dual monitor"
date: 2011-10-15
forum: Hardware
---

### Post by dohomi on 2011-10-15
Hi there, 

I upgraded to Ubuntu 11.10 few time ago on my Lenovo T410 with Nvidia graphics. I have a docking station with 2x 24'', and running on Ubuntu 11.04 everything was great. But since the upgrade to Oneiric Ocelot the Nvidia configuration breaks down all the time, if I try to activate my both screens with twin view. The monitors get displayed but after choosing one the desktop freezes...

Does anybody now how getting it run? Under "Display" in the settings the monitors doesnt get recognized.

Thanks for any help!

Greetings Dominic

---

### Post by ggx123qwe on 2011-10-15
> **dohomi said:**
> Hi there, 

I upgraded to Ubuntu 11.10 few time ago on my Lenovo T410 with Nvidia graphics. I have a docking station with 2x 24'', and running on Ubuntu 11.04 everything was great. But since the upgrade to Oneiric Ocelot the Nvidia configuration breaks down all the time, if I try to activate my both screens with twin view. The monitors get displayed but after choosing one the desktop freezes...

Does anybody now how getting it run? Under "Display" in the settings the monitors doesnt get recognized.

Thanks for any help!

Greetings Dominic

Same problems are being reported all over the place. It seems 11.10 breaks everything in terms of dual support. Very immature.....

I guess we have to wait...

---

### Post by dohomi on 2011-10-15
Hello,

thanks for your answer, I could get it run with following solution:

1. enable 1 external display and disable LEN in one step!
2. save to xorg.conf and quit.
open nvidia again
1. enable 2. external display 
2. save to xorg.conf
Now both are running. So the problem seems to pop up, when laptop and an external should work together, but external with external seems fine for now.
Cheers Dominic

---

### Post by tkoopa on 2011-10-17
Same problem here ( Quadro FX 2800M on a Precision M6500 )

At work I have a 23" and a 19" monitors plugged into the dock in DVI. 
At home I have just 19" plugged into the dock in DVI. 

At home I just can't get it to run the external monitor, but at work I can at least get the 23" + the laptop together. 

Still this is huge nuisance, it had been working flawlessly in 10.04 and 11.04. 

But does this have to be reported to Ubuntu or Nvidia ?

---

### Post by ggx123qwe on 2011-10-19
This post saved my life....pesky little bug in 11.10

Now I have no problems running 11.10 with multi monitor. I DID NOT use the 11.9 Catalyst (Post Release), but the 'ATI/AMD proprietary FGLRX graphics driver'

more info on 

[http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx](http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx)

---

### Post by tkoopa on 2011-10-21
I managed to get my two monitors working by disabling the laptop monitor in nvidia-settings ( not just setting display off in twinview). Still an ugly regression though.

---

### Post by denisk on 2011-10-23
I wasn't able to setup dual monitors for a while with oneiric. I have nvidia card, and whenever I hit 'apply' in nvidia-settings, displays would break (colorful trash would appear) and I needed to reboot. What I did was hitting "save to x configuration file', after running
```
sudo nvidia-xconfig
```
and unchecking "merge with existing file" option. Monitors work fine now, just the top bar on the main display works awkward - menus disappear immediately after I release mouse button. I can use the other menu bar however, not a showstopper for me.

---

### Post by tkoopa on 2011-10-24
My problem is that it's a laptop that I use in two different work setups, so I can't save permanently to xorg.conf

---

### Post by denisk on 2011-10-25
> **tkoopa said:**
> My problem is that it's a laptop that I use in two different work setups, so I can't save permanently to xorg.conf
The problem seems to be Ubuntu/Unity-specific: I installed Kubuntu 11.10 on the same machine, and dual monitor configuration works just fine there (except the fact that it is wiped out after each logout, but this is an old bug and shouldn't be too big of a problem for you since you have to switch between different configurations anyway).
Go for Kubuntu, KDE is so much better then Unity, honestly...

---

### Post by arch0njw on 2011-11-20
> **tkoopa said:**
> I managed to get my two monitors working by disabling the laptop monitor in nvidia-settings ( not just setting display off in twinview). Still an ugly regression though.

First:  Same on Kubuntu.

Second:  Thank you for that tip.  It worked for me.

Third:  Yuck!  Yucky yuck yuck!!!  This was seamless in 11.04!  What happened, Team Kubuntu / Team KDE?!

---

### Post by rocky_raccoon on 2011-11-29
I use an ATI Mobility Radeon HD 6370 with proprietary drivers in Ubuntu 11.10 64 and I can't get it to detect an external monitor through HDMI. Not with the catalyst software nor with the "Displays" utility. Everything else seems fine. I'd appreciate your suggestions.

---

### Post by denisk on 2011-11-30
@[rocky_raccoon]("http://ubuntuforums.org/member.php?u=464817"): can you at least see your second monitor in ATI catalyst? If you can, chances are that it can be made workable.

---

### Post by rocky_raccoon on 2011-12-03
No, I can't see it, at least not anymore (although I think it never detected it properly). Here is the whole story:

I connected my laptop and my sony bravia tv monitor with an hdmi cable. I went to catalyst and it showed and external display, though it looked very strange, I couldn't configure a proper resolution. Anyway I set it up for a clone display and catalyst told me to reboot. I thought it was weird, but I did it anyway and X failed to start. I spent hours trying to fix that and the only solution I found was to delete xorg.conf file in order for the system to generate a new one. I succeeded loading X again but now catalyst centre doesn't detect the external monitor (not even a strange one). I've tried reinstalling the drivers, running *aticonfig--initial=dual-head* and other variants. Not sure if I'm looking in the right place, but if run,  say, ```
aticonfig --desktop-setup=clone
```, I get a massage claiming ```
--dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!
```

No idea what that means. I only know this whole issue is not hardware related in anyway because it works perfectly in (cover your ears) Windows 7. Thanks for the help.

---

### Post by denisk on 2011-12-06
I wish I could suggest you something useful here. This tutorial have helped me setup dual monitor plenty of times when all 'standard' approaches had failed:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Let us know if you find it useful

---

### Post by rocky_raccoon on 2011-12-17
Thanks for the info, but I do not think it can help me. It states that it only applies for versions prior to 11.04. I can't run the command *gnome-display-properties*, for example. I'll take look to the rest of the document anyway, thanks again. I might start a new thread on this, since my problem is detecting any external monitor at all and not quite setting up a dual monitor array.

---

### Post by baizon on 2011-12-17
What's working for me is... i hope this helps.
```

sudo aticonfig --initial=dual-head --screen-layout=right
Restart X Server.
sudo aticonfig --xinerama=on

```
Then i get Dual-Screen Display. My Catalyst version is 11.11.

---

### Post by tkoopa on 2012-01-04
Pro-tip: because Unity crashes every time I enable the monitors, I have a shell script on my desktop that I click and "run in terminal" with ```
#!/bin/bash
unity --replace
``` to restart Unity

---

### Post by Cookieh on 2012-01-04
Get Compiz Advanced Settings... Solved my problem...

---

### Post by rocky_raccoon on 2012-01-04
> sudo aticonfig --initial=dual-head --screen-layout=right
Restart X Server.
sudo aticonfig --xinerama=on

Doesn't work for me, my display is not detected at all, I have tried *--initial, --initial=dual-head* and *--initial adapter=all* and the closest I've been to having my monitor detected is failing to start X at all.

---

### Post by rocky_raccoon on 2012-01-04
> Get Compiz Advanced Settings... Solved my problem...
Compiz advanced settings? Is that different from Compiz settings manager. Can you explain?

---

### Post by lmihaila on 2012-01-10
On a Nvidia Quadro 160m powered laptop I solved this problem by installing gtk2-engines-pixbuf
The operation is described here [http://forums.techarena.in/operating-systems/1447603.htm](http://forums.techarena.in/operating-systems/1447603.htm) and, for now, that topic still fits into one page.
Although you cannot dock/undock with the OS started. Was this possible in 11.04?

---

### Post by jvdurme on 2012-02-11
Basically, dual screen setup in *buntu 11.10 is faulty. It won't detect your primary screen. It will always put panels on the leftmost screen. If that's your physical setup, you're fine. If you want the panels/launcher on the rightmost screen, you're screwed.
The xrandr --primary command will never stick. I have an ATI card fyi.
For Unity 11.10 there is a fix in Daniels ppa:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/742544](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/742544)

In Ubuntu 12.04, Unity has a workaround. It puts the launcher on both screens and it's easy to configure the screen layout (left, right, ...). Unfortunately, you cannot choose the screen that displays the launcher. It will always be on both screens. 
Kubuntu 12.04 does not accept the primary setting neither in their fancy display setup menu. One workaround here is to make a new panel on the external screen. But keep in mind that the panel on the laptop screen and external screen are not the same. Each change to one of both panels, will not be transferred to the other panel.

Xubuntu 12.04 is the only ubuntu based distro that handles dual screens well. But you will have to script a little to get it working permanently. Each xfce panel can be attributed to a screen separately from the panel config menu or from the command line:

```
xfconf-query -c xfce4-panel -p /panels/panel-0/output-name -s <NAME OF OUTPUT SCREEN>
```

I also made a python script that runs xrandr on each login and sees if an external monitor is connected or not. And then has the panel(s) located appropriately. If you're interested in that script, let me know.

Hope this info is useful.

---

