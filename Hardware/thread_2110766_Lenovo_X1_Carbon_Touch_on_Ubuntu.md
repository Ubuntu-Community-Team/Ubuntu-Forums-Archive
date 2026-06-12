---
title: "Lenovo X1 Carbon Touch on Ubuntu"
date: 2013-01-31
forum: Hardware
---

### Post by viggonavarsete on 2013-01-31
Hi,

I'm thinking about buying the new Lenovo X1 Carbon Touch laptop, and I want to run Ubuntu on it. Will the touch capabilities of the lap top work "out of the box", or will it ever be able to fix, or should I rather go for the Lenovo X1 Carbon (without touch..)?

[http://www.engadget.com/2013/01/02/lenovo-thinkpad-x1-carbon-touch-review/](http://www.engadget.com/2013/01/02/lenovo-thinkpad-x1-carbon-touch-review/)

Any suggestions?

---

### Post by asayler on 2013-02-09
Hi,

I just got an X1 Carbon Touch and installed Ubuntu 12.10 x64 on it. The touchscreen is recognized out of the box, but doesn't fully function as you might expect. It works is a manner similar to connecting a second mouse to the machine. You can click on things, move the mouse pointer around the screen, drag, etc, but there is no support for multi-touch or touch-specific gestures (drag-to-scroll, pinch-to-zoom, etc).

I haven't played with it much yet, so I don't know if there will be a way to enable a more native touchscreen interface or if the support for touchscreens as something different than a mouse just isn't there yet.

Beside the touchscreen, everything seems to work more or less out of the box (wifi, bluetooth, SD reader, etc). I haven't tested the fingerprint reader yet. The touch-pad works fine for 2-finger gestures (scroll, zoom, etc), but does not seem to recognize 3-finger gestures by default. Again, I haven't tried that hard to fix this yet.

Overall, the X1 carbon Touch seems to work pretty well with Ubuntu 12.10 x64 without any special configuration. I hope more of touch-native support is coming down the pipe soon (and maybe an improved touch-pad driver), but the current state doesn't seem any worse than most early-adopter hardware can be on Linux...

Cheers,
Andy
[www.andysayler.com](www.andysayler.com)

---

### Post by asayler on 2013-02-11
I should also mention that after further exploration, there does seem to be some basic support for multitouch via the touchscreen. Taping a window with three fingers brings up the move/resize Unity context. Tapping the screen with more than 3 fingers seems to activate the Unity dash.

There still doesn't seem to be any support for pinching or scrolling via the touchscreen.

Also, I seem to be getting 3 to 5 hours of battery life depending on the brightness settings, etc.

---

### Post by offgridguy on 2013-02-11
> **asayler said:**
> 

Also, I seem to be getting 3 to 5 hours of battery life depending on the brightness settings, etc.
3-5 hours sounds good to me.:D   Interesting regarding the touch
screen as i have windows 8 on a touch screen laptop and was
wondering how ubuntu would function using touchscreen.

---

### Post by layolayo on 2013-07-09
Just ordered one of these - looking forward to seeing how Raring runs on it.

Have you upgraded and noticed any improvements?

Also, did you go for a full overwrite of the SSD? Any issue with UEFI on this machine? just asking before it arrives...

---

### Post by asayler on 2013-07-09
[SIZE=2]> **layolayo said:**
> 
[FONT=arial]Have you upgraded and noticed any improvements?[/FONT]


[FONT=arial]No major differences in 13.04. It seems they improved the default power settings a bit, upping the battery life to about what I got after lots of manual tweaking in 12.10. A few notes, however:[/FONT]

[FONT=arial]First, Ubuntu still has no standard way to set the default, boot-time screen brightness. I set it to about 50% at boot via my /etc/rc.local script:[/FONT]

```
[FONT=arial]echo 7 > /sys/class/backlight/acpi_video/brightness[/FONT]
```

[FONT=arial]This helps improve power efficiency quite a bit.[/FONT]

[FONT=arial]Second, the new default 13.04 power profile seem to be a little too conservative with respect to the CPU power governor settings. This causes the CPU frequency to fail to properly spin up on heavy workloads, cutting your performance to about 30% of what it could be. I fixed this by switching from the default "ondemand" governor (and it's default parameters) to the "conservative" governor. To accomplish this, I added a "conservative" case to the "$governors" case statement in my /etc/init.d/ondemand script:[/FONT]

[/SIZE]```
[SIZE=2][FONT=arial][COLOR=#000000]case $governors in[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]         *interactive*)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   GOVERNOR="interactive"[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   break[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   ;;[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]           *conservative*)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   GOVERNOR="conservative"[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   break[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   ;;[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]           *ondemand*)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   GOVERNOR="ondemand"[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   break[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   ;;[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]           *)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   exit 0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]                   ;;[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=arial][COLOR=#000000]esac[/COLOR][/FONT][/SIZE]
```[SIZE=2][FONT=arial]

You could probably also fix this by sticking with "ondemand" and just editing the sensitivity settings to get it to spin up at a lower threshold than the default. I also expect this issue will go away in 13.10 when we switch to the 3.10 kernel with it's new Intel p-states driver/governor support.

See [/FONT][/SIZE][https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt](https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt) for more information.[SIZE=2][FONT=arial]

> **layolayo said:**
> 
Also, did you go for a full overwrite of the SSD? Any issue with UEFI on this machine?


Yes, I fully wiped and reformatted my SSD using GPT partitioning and btrfs. I'm using both UEFI and SecureBoot. The Ubuntu 12.10 and Ubuntu 13.04 install CDs should automatically setup both UEFI and SecureBoot as long as you boot the install CD/USB Drive in UEFI mode. Working like a charm for me here.

Overall, it's a great machine and works well with Ubuntu. We still need better awareness for touch events, gestures, and actions, but I think we'll see more of that as the Ubuntu Touch code goes into the mainline and as more users have touchscreen laptops.

Good luck![/FONT][/SIZE]

---

### Post by asayler on 2013-07-09
Also, the touch-pad seems to be a little over-sensitive at times, and I haven't been able to find a way to disable cursor movement when you're clicking. This causes the cursor to jump a bit on each click, making precision selection somewhat difficult. There's likely a driver setting that I could tweak to fix this, but I haven't found it yet...

And I did end up testing the fingerprint reader. It works fine, although I rarely use it.

---

### Post by layolayo on 2013-07-31
Thanks for info asayler - just managed to get logged in again after the security breach.

Also checked with UPS and laptop should arrive in the next few days :) Unfortunately I am in a different country at the moment :(

---

### Post by layolayo on 2013-08-14
Ok got my Lenovo X1 - all is okay (not great), got a lot of lag when scrolling on web pages, running 13.04. Just got used to the touchpad layout - build quality is good, keyboard is nice too. Like that the touchscreen works out the box with 13.04. I tried arch, crunchbang and elementaryOS just to try and fix this screen lag issue - but have ended up back with 13.04 as none of them supported touchscreen (except Arch once initiated, but I'm not that dedicated a Linux user to venture in that black box... yet) ... so is anyone else having these problems. I'm using a celeron 32 bit ACER here at the moment and scrolling is fine on this piece of junk.

---

### Post by layolayo on 2013-08-15
asayler - thanks for the further info regarding conservative settings, I've traced this to using TLP ([http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter/285681#285681](http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter/285681#285681))

hoping this is the area you were setting up also, if you have any further info on getting the best out of the x1 (sounds like you have some good experience both linux/x1) it is much appreciated.

---

