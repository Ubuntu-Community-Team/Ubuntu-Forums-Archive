---
title: "Screen dimmed/blank on resume from sleep (xscreensaver issue?)"
date: 2012-03-01
forum: Hardware
---

### Post by Conic on 2012-03-01
Hello.

Every now and then when I resume my Xubuntu netbook (Asus 1215t) from sleep, I have one of two problems. 

In the first situation, I'm presented with a dimmed screen. My computer is fully usable, and the backlight is still on full, but it's as if I'm viewing my entire desktop through a transparent window, such as the terminal emulator. Everything but my cursor is dimmed in this way.
I have also had this problem using Linux Mint with XFCE.
The only way to fix this that I have figured out is to reboot the computer. This can be frustrating.

In the second situation my screen is completely black, but the backlight is still on and the cursor fully bright. I can only move my mouse around in a small square on the screen, going nowhere near any of the edges.


I'm aware that these problems sound vague, I'm currently sleeping and resuming my laptop over and over again in the hopes of reproducing these problems and getting screenshots.

Thanks in advance for the help.

---

### Post by Conic on 2012-03-01
I have successfully reproduced the first issue, it seems to be simply random. I took a screenshot, but I got a picture of a normal desktop. Anyone had a similar problem?

---

### Post by joehill on 2012-06-25
I have the same problem. When the screen initially looks totally black, if I tilt the screen a bit I can see that it's the same problem but 95% black instead of 50% or so. I filed a bug on launchpad but no response yet. Very annoying bug, and I've looked all over and not found any indication of what causes it or how to solve it!

---

### Post by abelian jeff on 2012-07-04
I have this problem too, and it is indeed very frustrating!

Just a note: For the first problem, you can simply log out instead of rebooting, and this fixes the problem.

---

### Post by eddielgarcia on 2012-08-19
Could you post the link to the filed bug on launchpad?  This problem is annoying and I would like to see its status also.

---

### Post by Bucky Ball on 2012-08-20
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1015297?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1015297?comments=all)

Yea, annoying. I have posted here and there on this. My issue, though, is random. Only happens maybe one in ten times when I lift the lid and come out of suspend.

I can see enough to close apps and log out. Then all is fine again. Odd. 

So, yes people, a known bug. Check the Launchpad link at top of this post. For now, this is not fixed. Good luck. ;)

PS: I'm presuming everyone is using Xubuntu or Xfce4 to experience this issue?

---

### Post by northrup on 2012-10-24
If you haven't seen my posts on the bug's entry in Launchpad, here's what I did to work around this problem if it appears.  This is only tested with a Radeon-based card (in my case, an ATI Mobility Radeon HD 4500 series) with the proprietary drivers (and Catalyst Control Center) installed.

[LIST=1]
[*]Open Catalyst Control Center (in Xfce, click on the application menu, then Settings, then Catalyst Control Center.
[*]Navigate to the "Color" section, and in the "Gamma" box, tweak the slider in either direction.
[*]Your screen should pop back to full brightness.  Reset the slider, hit "OK", and enjoy not having to log out to fix the issue.
[/LIST]

Again, this is only tested on my Radeon card; I don't have a laptop with another ATI/AMD card or an Nvidia card to test and attempt to replicate the problem.  If you don't have CCC (i.e. you aren't using proprietary drivers), install Redshift

```

sudo apt-get install redshift gtk-redshift

```

and use Redshift's methods to tweak the gamma.  If you're using an Nvidia card, use nvidia-settings (I'm assuming it has a way of tweaking a gamma setting).

Hope that helps everyone!

---

