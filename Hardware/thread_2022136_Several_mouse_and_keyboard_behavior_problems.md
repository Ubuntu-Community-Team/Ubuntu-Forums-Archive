---
title: "Several mouse and keyboard behavior problems"
date: 2012-07-10
forum: Hardware
---

### Post by paul1149 on 2012-07-10
Hi,

I'm on ubuntu 12.04/gnome, on an older Pentium 4/2.6GHz machine with 1.26GB RAM, and things are running quite smoothly as I'm checking them out. The biggest problem I have right now, though, is the behavior of the keyboard and mouse. 

The first problem can best be described as *momentum* with regard to scrolling and dragging. When I'm in Opera, which doesn't support that neat ad hoc mini scroll bar widget, when I grab the vertical scrollbar and pull downward, the page continues to scroll after I have stopped. This creates a very sloppy, uncertain scroll, and I often have to compensate by moving the mouse upward again. It's like trying to regain control when a car breaks loose on ice. The same thing happens when page scrolling via the keyboard cursor arrows.

Also, if I'm dragging a window using the mouse, the same momentum kicks in. After I stop moving the mouse, the window keeps going, past where I want it to be.

AIUI, this is a distinct issue from acceleration, which is configurable. Accelerated movement should stop when the user stops scrolling.

The second problem is the slowness of the mouse scroll wheel. I'm using a Gateway USB three-button mouse, and each flick of the wheel might scroll a page five lines if I'm lucky. This is extremely tiresome, and forces me to find the scrollbar - and experience the first problem.

The third problem is that the standard Windows context menu key brings up the system Dash menu rather than the focused app's context menu. To access that menu I currently have to use the mouse, which is distracting.

All these problems are adding up. I find them to be a major hindrance to making this a workable system for daily use.

Thanks.

---

### Post by lukeiamyourfather on 2012-07-10
Two things, that hardware is probably better matched with Xubuntu Or Lubuntu which require fewer resources. The other thing is it sounds like no graphics driver is installed which can cause the slowness you are experiencing when scrolling. The keyboard and mouse are working just fine.

---

### Post by navingoradara on 2012-07-10
When I'm in Opera, which doesn't support that neat ad hoc mini scroll  bar widget, when I grab the vertical scrollbar and pull downward, the  page continues to scroll after I have stopped.

---

### Post by sudodus on 2012-07-10
> **lukeiamyourfather said:**
> Two things, that hardware is probably better matched with Xubuntu Or Lubuntu which require fewer resources. The other thing is it sounds like no graphics driver is installed which can cause the slowness you are experiencing when scrolling. The keyboard and mouse are working just fine.
+1

I have seen so many people having similar problems because the new Ubuntu with gnome 3 needs more computing power. So download Xubuntu or Lubuntu and try them. Boot from a CD or USB drive to find out what you like before considering what to install.

An alternative is to install 'only' the desktops into your present installed system (but it will be a system with some double versions of software (one lighter added to the Ubuntu heavy software for several purposes). For example

```
sudo apt-get install lubuntu-desktop
``` or simpler 
```
sudo apt-get install lxde
```

---

### Post by paul1149 on 2012-07-10
> **lukeiamyourfather said:**
> Two things, that hardware is probably better matched with Xubuntu Or Lubuntu which require fewer resources. The other thing is it sounds like no graphics driver is installed which can cause the slowness you are experiencing when scrolling. The keyboard and mouse are working just fine.

Thanks, everyone. This makes sense. I'm seeing a lot of wait time on opening apps, even nautilus.

Checking System monitor now, I'm idling at under 10% cpu, .9 of 1.7GB RAM, and .3 of 1.2GB swap used, with only opera open. That doesn't seem bad.

I'm over at Intel, [looking at drivers]("http://www.intel.com/p/en_US/support/detect/dsktpboards") for the D865GLC board. They do offer some linux drivers, for Red Hat and Novell mostly. Would something like that do here?

---

### Post by lukeiamyourfather on 2012-07-10
> **paul1149 said:**
> Thanks, everyone. This makes sense. I'm seeing a lot of wait time on opening apps, even nautilus.

Checking System monitor now, I'm idling at under 10% cpu, .9 of 1.7GB RAM, and .3 of 1.2GB swap used, with only opera open. That doesn't seem bad.

I'm over at Intel, [looking at drivers]("http://www.intel.com/p/en_US/support/detect/dsktpboards") for the D865GLC board. They do offer some linux drivers, for Red Hat and Novell mostly. Would something like that do here?

There should be a graphics driver in the repositories for Intel video chipsets but I don't have it in front of me to check. Hopefully someone else can chime in on that.

Since the system is using swap that means it completely ran out of memory at some point since booting. Not a good sign, I'd seriously consider Xubuntu or Lubuntu.

---

### Post by paul1149 on 2012-07-10
Ok, Thanks again.

A couple of updates. I turned off opera's smooth scroll, and it's a little better. But the momentum thing is still present when I drag windows across the desktop.

Then, twice today so far Unity has gone missing on me for no apparent reason. It's still there, as is evidenced by info bubbles when I hover in the right places, and I can click on the right blank spaces and make things happen. Rebooting brings it back.

Here is the status quo before I did anything:

[INDENT][COLOR="DarkRed"] sudo lshw -C video
[sudo] password for paul: 
  *-display               
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0000000-f7ffffff memory:ffa80000-ffafffff ioport:ec00(size=8)[/COLOR][/INDENT]

Then [this]("http://askubuntu.com/questions/84786/where-can-i-download-intel-hd-vga-driver-for-my-dell-inspiron-n5010") very helpful thread showed me how to install intel updates. I'm going to reboot right now. Will post back.

---

### Post by paul1149 on 2012-07-10
No change whatsoever in the video properties readout. I guess I need to start looking into the lightweight alternatives to ubuntu, and whether to implement them as sudodus suggested. Any further thoughts would be welcome.

Before I post that, let me add some observations. Even with opera's smooth scrolling turned back on, the momentum problem seems to be absent, either with the mouse or the cursor keys. Windows dragged across the desktop by mouse also do not override their intended destination any longer. I still am getting slow wheel scrolling, though. The driver in the above sudo readout still says i915, but the performance is better.

---

### Post by paul1149 on 2012-07-11
A small update. Despite that sudo graphics readout, the graphics driver update seemed to have been doing something during installation, and the system seems better now. I've had no new Unity crashes. The dragging/scrolling momentum problem is a lot better, if not perfect. The slow wheel scrolling persists, and is a bit worse in Opera than in FF, unfortunately for me.

Swap file usage is down to zero. I just ran the Checkbox system checker tool, and the swap sits at 1MB used, of 1.2GB.

The lack of application context menu key was solved by me finding the correct key. I didn't realize the backup keyboard I'm using has two windows keys on the right side, unlike my main keyboard.

So I'm better off than I was. I'm looking into Lubuntu, which looks intriguing. If I could only get the mouse to scroll faster, I'd say I'm comfortably ensconced in ubuntu.

Thanks for all the help here. I'll be referring to this thread if there are further problems or I want to try that lubuntu command.

---

### Post by sudodus on 2012-07-11
You are making progress :KS

Maybe you will finally manage to get Ubuntu to run nicely in your computer. Otherwise, it costs very little to download and test Xubuntu and Lubuntu live (booted from CD or USB without installing). At least if you have a reasonably fast internet connection ;-)

---

### Post by paul1149 on 2012-07-11
> **sudodus said:**
> 
```
sudo apt-get install lubuntu-desktop
``` or simpler 
```
sudo apt-get install lxde
```

sudodus,

I've been testing unity now for several days, and while I like the concept I don't like the implementation. Essentially, there is not enough configurability. So I decided to try gnome 3, but that didn't grab me either. I came back here to refer to your post, and decided to give lxde a try, and it looks excellent. It may be simple, but it covers the functional bases beautifully, and it's surprisingly configurable.

I am getting some duplication of autoruns, so I need to find where they are stored.

For the record, even in this light environment the scroll speed still is only a few lines per stroke, which is extremely slow. So resources doesn't look to be the issue. But the momentum problem is totally gone.

I may try out the lubuntu environment as well, though it's a hefty download.

Thanks for these suggestions,
p.

---

### Post by paul1149 on 2012-07-12
I now have tried the full lubuntu shell, and I found lxde to be much faster, and didn't see much feature difference between them. So I'm back on lxde, and think it's really nice. 

The biggest problem now is that the debian package manager is non-functional. I wanted to uninstall lubuntu.

[COLOR="Red"]Edit: Ok, I found the synaptic package manager, so no problem now. Thanks again.[/COLOR]

---

