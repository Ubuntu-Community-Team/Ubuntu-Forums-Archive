---
title: "Synaptics Touchpad Error -- Freezes"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by dutchman25 on 2006-08-22
I have a Pavilion dv5000 with a Synaptics Touchpad.  The touchpad is making my laptop almost unusable, because it periodically freezes other input devices (including a USB-connected mouse).  I do not believe it has anything to do with the synaptics driver, because I've tried every different one I could get my hands on.  I also don't think it's the xorg.conf settings, because I've tried a variety of those as well.  Here's the dmesg output:

[ 1630.640786] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 1630.641513] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1630.645618] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 1630.652547] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 1630.653133] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1630.657459] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 1630.663074] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 1630.663607] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1630.667338] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[repeats at different intervals]

Can anyone help me solve this problem????

---

### Post by tecteun on 2006-10-22
same problem over here... trying to solve it :cool:

---

### Post by jcb666 on 2006-10-22
Interesting.  Same problem here with a Synaptics touchpad.  Only appeared when I upgraded to edgy.  Everything is fine in 6.06.

---

### Post by tecteun on 2006-10-23
> **jcb666 said:**
> Interesting.  Same problem here with a Synaptics touchpad.  Only appeared when I upgraded to edgy.  Everything is fine in 6.06.

I confirm this bug, it wasn't there in Dapper.

---

### Post by Greguti on 2006-10-23
Got the bug too. 

I managed to "fix" it by commenting the line *InputDevice "Synaptics"* in my */etc/X11/xorg.conf*, so that when I restart X (Ctrl+Alt+Backspace), the touchpad is handled as a simple mouse. The touchpad is then far less usable, because I have to click on the buttons below it and the double-tapping don't work. 

I hope the bug will be fixed quite soon! I use Edgy on my Asus S6J laptop and my usb mouse is not always in my pocket :)

Regards

Greg

---

### Post by jcb666 on 2006-10-23
I tried all sorts of X configuration of input devices.  Didn't fix my problem.  

I suspected the problem is with xorg version or kernel 2.16.xx input device.

I replicated the bug on gentoo with a 2.6.16 kernel & earlier xorg, so I strongly susepct the 2.6.16.xx kernel.

Went back to the /dev/psaux interface, diabling everything else in the kernel.  Worked fine.

---

### Post by alohre on 2006-10-24
I can confirm this on an Aopen 1556 (not quite sure about the correct model number, it's a half build from aopen, leaving the choise of CPU, wifi and some other components to the company that sells them). It has a synaptics touchpad and spits out the lost sync error in dmesg. I have tried adding proto=imps and proto=bare after the psmouse module in /etc/modules (search for proto=imps in google to see some of the threads about this). Maybe some of you may have more luck with this than I had. btw: this error started after  upgrading from dapper to edgy, I had no problems with this in dapper.

---

### Post by rushdy on 2006-10-27
I too have this problem on an Aspire 1522. Lost sync in dmesg and pointer freezes. Also caused by updating to Edgy from Dapper.

---

### Post by alohre on 2006-10-29
Adding acpi=off in the menu.lst for the running kernel solved the problem for me. Seem to be a kernel bug.

---

### Post by tecteun on 2006-11-05
> *knocking on wood*
I believe I found the cure:

adding :
```
usbhid
uhci-hcd
ehci-hcd

```
to /etc/modules fixes the random locking of the touchpad

at least: i never noticed choppy mouse since i added this....
so this is yet to be proven

thats not true :S, sorry

---

### Post by Greguti on 2006-11-05
Modification of the /etc/modules file is not working for me. Can you show us your /etc/X11/xorg.conf file please?

Regards

Greguti

---

### Post by tecteun on 2006-11-05
Sorry, too i posted too soon, after a reboot it happens again ](*,)

---

### Post by madelephant on 2006-11-05
Editing /etc/X11/xorg.conf fixed the bug for me for now at least.  Let you know if it acts up again.

[I]
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
#       InputDevice     "Synaptics Touchpad"
[/I]

Commented out the *InputDevice     "Synaptics Touchpad"* line.

---

### Post by Greguti on 2006-11-06
Yep, but commenting *Input Device "Synaptic Touchpad"* in /etc/X11/xorg.conf just makes your touchpad recognisable as a simple mouse, so that some important features disappear (scrolling with your digit on the touchpad for example).

So it is not a solution, it's just a workaround, while we wait for an official patch to Edgy :-(

Regards

Greg

---

### Post by Greguti on 2006-11-10
Hi all,

FYI, I did a totally fresh installation on my computer yesterday. Installed Dapper Drake, then proceeded to the upgrade to Edgy right after it. My Synaptics Touchpad works fine now (at least, for now!).

Regards

Greg

---

### Post by enigma_0Z on 2006-11-16
I think I have found the solution.

/etc/modules in edgy contains the following:

```

lp
psmouse
sbp2
sr_mod

```

Comment these and reboot. This should fix the problem. I believe that some modules (perhaps deps for lp?) were getting loaded before psmouse and causing irq/acpi problems.

My config for reference:

```

#lp
#psmouse
#sbp2
#sr_mod

ndiswrapper

```

I'm on a HP dv6000z w/ AMD sempron. I think I am going to try switching back to ubuntu-64... maybe.

---

### Post by enigma_0Z on 2006-11-16
> **Greguti said:**
> Hi all,

FYI, I did a totally fresh installation on my computer yesterday. Installed Dapper Drake, then proceeded to the upgrade to Edgy right after it. My Synaptics Touchpad works fine now (at least, for now!).

Regards

Greg

What kernel are you running? I did the same thing, and if I run the 2.6.15 kernel, I get the same out of sync errors, but the driver re-syncs properly and there's no lockup. After a while of running, the touchpad is stable.

---

### Post by Greguti on 2006-11-16
Hi,

finally my re-installation of Ubuntu didn't fix it. The second time I rebooted my computer, the touchpad did freeze again...

I found a workaround, it works for me each time I try it:

First, I installed qsynaptics, then each time I open my gnome session, I launch it, and I have to manually play with its configuration panels, like for example "enable/disable" radio box on and off, etc. Then I select "Apply", then suddenly the touchpad drivers operates well and stays here...

I have to navigate trought the interface of qsynaptics with keyboard shortcuts (tab, alt-tab, space, enter, arrow keys) before I press "apply".

Didn' try the workaround by enigma_OZ yet. I'll soon try it and tell you.

Regards

Greg

---

### Post by enigma_0Z on 2006-11-16
I tried your solution, did not work. I think that I was running edgy with the 2.6.15 kernel... I am downloading the vanilla 2.6.18 kernel to see if it makes a difference.

Oh yeah, and the /etc/modules thing did not work.

-- EDIT --

OK, completely CLEAN install of edgy (installed to new partition, new home dir, everything) from the DESKTOP CD, no problem now. I am installing some necessary software (firefox, build-essential, as well as updates from everywhere but universe, multiverse, and backports), slowly to see if something specific causes a screwup.

---

### Post by kikkum on 2007-01-02
Have this problem as well on my Acer Aspire 1501LMi since my Dapper to Edgy upgrade. Is there any know solution yet?

---

### Post by kikkum on 2007-01-02
I just found out it only happens in Gnome.

---

### Post by bouddidje on 2007-01-15
same same
```
Jan 15 21:10:21 bouddidje-portable kernel: [17187544.740000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Jan 15 21:10:21 bouddidje-portable kernel: [17187544.740000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jan 15 21:10:21 bouddidje-portable kernel: [17187544.752000] psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
Jan 15 21:12:17 bouddidje-portable kernel: [17187660.748000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jan 15 21:12:17 bouddidje-portable kernel: [17187660.752000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jan 15 21:12:17 bouddidje-portable kernel: [17187660.756000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jan 15 21:12:17 bouddidje-portable last message repeated 2 times
```

So fortunetely it's not a big bug, but sometimes you think you have click and in fact not, 
or you click delete :( instead of something else because you've moved the mouse...

---

### Post by mattds on 2007-01-24
This happens in KDE as well as Gnome.  It seems the bug has been confirmed on Launchpad and has a medium rating.  Is it possible to get the rating upped to high?  Is it something like the more people that report the issue the higher the rating?  

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/46074](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/46074)

---

### Post by kikkum on 2007-01-25
When I said it only happened in Gnome, I meant it didn't happen in XFCE, don't have KDE installed here. Anyway, hope they fix it.

---

### Post by dutchman25 on 2007-01-27
I finally got my Broadcom 4319 card working with ndiswrapper 1.33.  I used the 64-bit windows driver, and the touchpad error has disappeared and all is well.

---

### Post by spangemonkee on 2007-02-02
this happens on my Dell Inspiron 4000 with Dapper. Can't get wireless to work on Edgy. Restarting the mouse module works for me.

sudo modprobe -r psmouse
sudo modprobe psmouse

---

### Post by mattds on 2007-03-09
folks, I found that adding the line below to /etc/modprobe.d/options cleared up the issue for me.  There might be other proto options that work.

options psmouse proto=imps

Hope that helps.

---

### Post by Cannaregio on 2007-03-24
> folks, I found that adding the line below to /etc/modprobe.d/options cleared up the issue for me. There might be other proto options that work.

options psmouse proto=imps

Hope that helps

Thanks a lot mattds, it solved my touchpad problems - after updating to edgy on a Siemens Amilo S

---

### Post by enigma_0Z on 2007-03-27
> **mattds said:**
> folks, I found that adding the line below to /etc/modprobe.d/options cleared up the issue for me.  There might be other proto options that work.

options psmouse proto=imps

Hope that helps.

Uhh... doesn't that remove all of the nifty synaptics stuff such as the multi-finger taps, scrollbar and what not?

---

### Post by mattds on 2007-03-27
I can still tap to click, my pad doesn't have a scroll bar so that doesn't really apply to me.  You can try it and see what happens.

In a perfect world it would just work.  Personally, I'll take less functionality to maintain stability.  :)

---

### Post by trd ku kaman on 2007-04-03
I found a solution that works for my Acer 1522wlmi with synaptics touchpad and  edgy installation on it.

Just add following line to /etc/modprobe.d/options

option psmouse resetafter=0 

I've made a diff on psmouse sources between dapper and edgy kernel sources. 
By setting this parameter the edgy's driver acts like that in dapper, i think. 

You must reboot the system or reload the psmouse driver with modprobe to make the change effective.  

In edgy version after 5 errors the driver issues a reconnect request that freezes the pointer for some seconds.  
This parameter bypass the reconnection process and continue. The driver still prints messages on /var/log/messages when bytes are lost, but i don't notice the mouse freeze behaviour.

After the change in /var/log/messages (or dmesg output) you MUST not see 
"psmouse.c: issuing reconnect request "
between "lost sync at byte" messages.

Hope that helps (this is my first message to the forum...)

:)

---

### Post by viergeame on 2007-04-06
I have tried every suggestion on this thread and still no luck.  There are a few things I have noticed about this bug, on my system anyway.  It happens most in kde.  I also use xfce and gnome.  It seems to happen least in gnome and fairly often in xfce, but less than in kde.  Has anyone else noticed anything similar to that?
Something else I almost forgot to add... All the things on here that people say disable the tap function of the touchpad dont affect mine.  Someone suggested that maybe for some reason my touchpad is thinking that its a wacom tablet.  I'm not sure how that would happen, but I think I'm going to look into that too.

---

### Post by enigma_0Z on 2007-04-09
Well, that seemed to work. I'll be testing it out some more.

EDIT:

OK. Proto=icmp solved the problem at the expense of having two and three finger taps stop working. Hrmmmm I am not having as much of a problem with feisty

---

### Post by trd ku kaman on 2007-04-26
My previus solution was wrong, especially for Feisty.

I found another solution that works on my Acer 1522 wlmi.

I've modified /boot/grub/menu.lst putting 

  i8042.nomux=1 

on the kernel  line.

I've googled around and i found that there's  a problem between the 8042 chip and acpi causing lost packets of data between synaptics touchpad and the chip or the keyboard and the chip.

On Feisty the problem was even worse than Edgy including also keyboard auto repetitions very often.

Now my touchpad runs without problems.

Bye

---

### Post by pjb515 on 2007-07-20
Adding i8042.nomux=1 to the kernel line worked for me too. I have Ubuntu 7.04 on an Itronix Gobook II laptop, synaptics touchpad. Double tap still works fine (This touchpad dowsn't scroll, though, in case you're wondering. It's old.)
Thanks for the fix, I'm a brand new linux user that was going crazy!

---

### Post by tehtrk on 2007-07-22
> **trd ku kaman said:**
> My previus solution was wrong, especially for Feisty.

I found another solution that works on my Acer 1522 wlmi.

I've modified /boot/grub/menu.lst putting 

  i8042.nomux=1 

on the kernel  line.

I've googled around and i found that there's  a problem between the 8042 chip and acpi causing lost packets of data between synaptics touchpad and the chip or the keyboard and the chip.

On Feisty the problem was even worse than Edgy including also keyboard auto repetitions very often.

Now my touchpad runs without problems.

Bye

Seems to work for me, as well. I also changed the psmouse protocol to imps as suggested earlier. As it is working well with both imps and nomux=1, I will leave them as is unless I see the skipping problem reappear

Thanks kaman

---

### Post by Yaywalter on 2008-04-13
> **trd ku kaman said:**
> My previus solution was wrong, especially for Feisty.

I found another solution that works on my Acer 1522 wlmi.

I've modified /boot/grub/menu.lst putting 

  i8042.nomux=1 

on the kernel  line.

I've googled around and i found that there's  a problem between the 8042 chip and acpi causing lost packets of data between synaptics touchpad and the chip or the keyboard and the chip.

On Feisty the problem was even worse than Edgy including also keyboard auto repetitions very often.

Now my touchpad runs without problems.

Bye

Alright, I'm kind of a Linux noob... where exactly do I put that line in that file?

---

