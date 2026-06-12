---
title: "Dell e6400 wandering touchpad - workaround"
date: 2008-12-31
forum: Hardware
---

### Post by slinkp on 2008-12-31
**Experimental: Fixing The Horrible Dell E6400 Wandering Touchpad On Ubuntu 8.10 (Intrepid Ibex)**

Tired of your pointer flying randomly across the screen and clicking random crap?  Wondering about the spew of "... psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1" in your dmesg? Tired of scrolling being broken?

Here's how I have mine working - mostly. There still seem to be intermittent problems, but not as often as before.

This fix should be regarded as experimental; I wrote this up with the hope that others might find it useful and improve it, but of course there is NO WARRANTY. YMMV.

The wandering problem turns out to be poor support for this weird model of ALPS touchpad in the psmouse.c driver code.  There is a patch, which probably still needs work, and it hasn't been released in any version of Linux yet as of 2008/12/30 ... not even linux 2.6.28.  Below is one way to get the patch installed. There's probably a better way.

**Things I had already tried:**

* Upgrading to linux-image-2.6.27-11.22-generic kernel from intrepid-proposed, as per [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/270643](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/270643)

  This fixes the broken scrolling, but only until the next round of glitchy pointer freakout, which will cause the touchpad to revert to acting like a generic mouse. 

* Adding i8042.nomux=1 to kernel parameters. This didn't help me at all.
  Found in threads for other Dell laptops, eg. [http://ubuntuforums.org/showthread.php?t=808164&highlight=dell+alps+touchpad](http://ubuntuforums.org/showthread.php?t=808164&highlight=dell+alps+touchpad)


**[SIZE="2"]What worked for me[/SIZE]**

**Caveats:**

* It takes a long time to build the kernel.[1]

* Not all problems are solved; eg. the touchpad has on a few occasions completely stopped working and I don't know a fix at this time except to reboot.

* The kernel patch is not widely tested and probably needs more work; I've only been running it myself for less than a week so far.  So there's some risk here.  YMMV.

* I'm not using the binary nvidia driver.  (I had it working with kernel 2.6.27-9 but that broke when I upgraded to 2.6.27-11; I haven't bothered to investigate because I don't really need 3D.)

* I had to disable Xen virtualization support, because the kernel build barfed on it, as noted below. Again, not a problem for me.

**Step-by-step instructions:**

* Be sure hal starts before gdm; otherwise your pointer might sometimes fail to work at all. You can do this like so:
 ```

 $ sudo update-rc.d -f gdm remove
 $ sudo update-rc.d gdm defaults 25

```

* Fetch the kernel sources, according to docs at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

* Patch the kernel with the patch here: [http://www.gossamer-threads.com/lists/engine?do=post_attachment;postatt_id=32187;list=linux](http://www.gossamer-threads.com/lists/engine?do=post_attachment;postatt_id=32187;list=linux)

  (... discussion of that patch in this linux kernel mailing list thread: [http://www.gossamer-threads.com/lists/linux/kernel/991762](http://www.gossamer-threads.com/lists/linux/kernel/991762) )

* Copy your old kernel config - mine was at /boot/config-2.6.27-11-generic. Just copy it to .config in your source tree.

* Modify the .config to avoid a compile error. Disable Xen virtualization by changing this line:

```
    CONFIG_XEN=y
```

  to this:
 ```

    CONFIG_XEN=n
```

  You might want to turn off kernel debugging while you're at it; it makes the built kernel and especially the modules really, really huge. I forgot to do that.
  
  I was tempted to also turn off some of the zillions of unnecessary drivers to speed up compilation, but when I tried that, kpkg complained loudly[2], so I gave up on that idea.


* Build the kernel as per [https://help.ubuntu.com/community/Kernel/Compile#Build%20the%20kernel%20(when%20source%20is%20from%20git%20repository,%20or%20from%20apt-get%20source)](https://help.ubuntu.com/community/Kernel/Compile#Build%20the%20kernel%20(when%20source%20is%20from%20git%20repository,%20or%20from%20apt-get%20source))
  
  You don't need to build the linux-ubuntu-modules package for Intrepid.  And do NOT run "make-kpkg clean", it removes the debian/ directory and you'll have to start over.


* Install the kernel, as per [https://help.ubuntu.com/community/Kernel/Compile#Install%20the%20new%20kernel](https://help.ubuntu.com/community/Kernel/Compile#Install%20the%20new%20kernel)

  This step will fail the first time you try it, while trying to deal with the Nvidia binary drivers. Don't worry. When you see an error like this:

  "run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20"

  ... you just force reinstallation of the nvidia-common package:

```

   sudo apt-get purge nvidia-common
   # The kernel binary package will automatically restart at this point, and should succeed now.
   sudo apt-get install nvidia-common

```

* Check /boot/grub/menu.lst, edit as necessary to add your new kernel.

* Reboot and see if everything works!

**Disabling the Touchstick**

If, like me, you hate hate HATE the touchstick and only use the touchpad, once you have the above working, you can disable it. In Gnome, you can go to System -> Preferences -> Session, click the Add button, and enter this info:

   Name: Disable TouchStick
   Command: xinput set-int-prop "DualPoint Stick" "Device Enabled" 32 0
   Comment: I hate it, that's why.

(If you're not using Gnome, put that same command wherever you normally put commands to run when X starts.)

This unfortunately does not seem to be permanent; if I leave the laptop on for a while and come back to it later, there's a good chance the touchstick will have mysteriously re-enabled itself. On two other occasions, I have had both the touchpad and the touchstick become completely frozen - the pointer won't move at all.  I've tried reloading the psmouse module, and restarting hal, but neither of those helps; right now I don't know a solution other than reboot.


[1] The recommended kernel compilation procedure on ubuntu is really really time-consuming, and seems to be broken currently wrt. the Xen stuff as noted above. I have never had so much trouble compiling a kernel on any system since I first started using exclusively linux 10 years ago. I am a complete Ubuntu noob, so presumably I'm doing something totally wrong. Next time I'll try downloading vanilla sources and see if I have better luck with the old-school vanilla methods.)
 
[2] At that point I was experimenting with "the old-fashioned debian way" as per [https://help.ubuntu.com/community/Kernel/Compile#Alternate Build Method: The Old-Fashioned Debian Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate Build Method: The Old-Fashioned Debian Way)

---

### Post by kadawer on 2009-01-06
hi.
i really appreciate your posting, otherwise i would not have found this patch. although the patch doesn't fix every problem with the touchpad/trackpoint, it really solves the tedious button locking after concurrently using touchpad and trackpoint (which happens a lot if you use the trackpointer and rest your hand/thumb on the touchpad). the mouse pointer still gets desynchronized, but now its only bothersome and not anymore unusable.

please inform us, if you find any other improvements on this matter.

---

### Post by slinkp on 2009-01-06
Thanks! I intend to keep updating this post as long as I have problems, until it's fixed for good.  I just added an update about a problem I still have: occasionally the pointer freezes completely. It's only happened maybe 2 times since my original post a week ago.  Not as maddening as the wandering pointer problem, but still annoying.

Who'd have thought a little touchpad could cause so much anguish.

---

### Post by kadawer on 2009-02-01
hi, i noticed that it isn't necessary to build the whole kernel. you can just compile the psmouse module with the kernel-headers installed.
just create a makefile in the right directory (kernel/drivers/input/mouse) of the kernel sourcecode and copy the builded psmouse.ko to your /lib/modules/$(shell uname -r)/drivers/inout/mouse directory.

```

#
# Makefile for the mouse drivers.
#

# Each configuration option enables a list of files.

obj-$(CONFIG_MOUSE_AMIGA)	+= amimouse.o
obj-$(CONFIG_MOUSE_APPLETOUCH)	+= appletouch.o
obj-$(CONFIG_MOUSE_BCM5974)	+= bcm5974.o
obj-$(CONFIG_MOUSE_ATARI)	+= atarimouse.o
obj-$(CONFIG_MOUSE_RISCPC)	+= rpcmouse.o
obj-$(CONFIG_MOUSE_INPORT)	+= inport.o
obj-$(CONFIG_MOUSE_LOGIBM)	+= logibm.o
obj-$(CONFIG_MOUSE_PC110PAD)	+= pc110pad.o
obj-$(CONFIG_MOUSE_PS2)		+= psmouse.o
obj-$(CONFIG_MOUSE_SERIAL)	+= sermouse.o
obj-$(CONFIG_MOUSE_HIL)		+= hil_ptr.o
obj-$(CONFIG_MOUSE_VSXXXAA)	+= vsxxxaa.o
obj-$(CONFIG_MOUSE_GPIO)	+= gpio_mouse.o

psmouse-objs := psmouse-base.o synaptics.o

psmouse-$(CONFIG_MOUSE_PS2_ALPS)	+= alps.o
psmouse-$(CONFIG_MOUSE_PS2_LOGIPS2PP)	+= logips2pp.o
psmouse-$(CONFIG_MOUSE_PS2_LIFEBOOK)	+= lifebook.o
psmouse-$(CONFIG_MOUSE_PS2_TRACKPOINT)	+= trackpoint.o
psmouse-$(CONFIG_MOUSE_PS2_TOUCHKIT)	+= touchkit_ps2.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

---

### Post by dg0yt on 2009-03-26
I was not satisfied with any of the solutions proposed on the web, but I found another workaround:

Edit (as root) /etc/modprobe.d/options and add:

```

options psmouse proto=bare

```

After the next reboot (or after reload module psmouse), the kernel driver won't test if the hardware is some sort of touchpad, but instead treat it as a generic mouse. In this mode, both the stick and the touchpad are working without strange effects. 

Caveats: You cannot set any touchpad options. You loose the scrolling feature.

I found this solution when a analyzed why sometimes everything suddenly started working like it should. After a number of errors, the kernel driver decided to treat the touchpad/stick as a generic mouse.

Good luck!

---

### Post by nexxus07 on 2009-03-27
Hooray, that works. This was my first patch so it took me a while to find out the right steps from the description of kadawer.

Here is my step by step

**Install Kernel Sources. **
I used git for this:
[https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)

in short 
```

  sudo apt-get install git-core
  git clone --reference linux-2.6/ git://kernel.ubuntu.com/ubuntu/ubuntu-jaunty.git

```

Kind of ridiculous to have 700MB just to make a mouse driver but well.

**apply patch **
copy the .diff file above in the directory of the kernel sources (ubuntu-jaunty/drivers/input/mouse) and:

```
patch < alps.diff
```

**Make psmouse.ko**

There is already a Makefile in the directory 
I just added the two lines at the bottom
```

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean


```

and run 

```
make
```

then as specified by kadawer copy the psmouse.ko into /lib/modules/$(shell uname -r)/drivers/inout/mouse directory and reboot.

---

### Post by hyl4me on 2009-03-28
I tried the whole night.  I couldn't pass the **make** command.  nexxus07, can you show me step by step starting from get build-essential and such.  Thank you

---

### Post by kadawer on 2009-03-29
make sure that you have installed **build-essential** package and that you changed into the right directory (ubuntu-jaunty/drivers/input/mouse if you followed the steps).

it is not necessary to reboot, just unload the module and load it again
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

or modify the Makefile furthermore by adding a new make target:
```

psmouse:
	modprobe -r psmouse
	cp psmouse.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/mouse/
	modprobe psmouse

```

now you can type **make** as mentioned and then **sudo make psmouse** to automatically copy and load the new module.
you could merge the two commands in the Makefile, but this is not usual.

---

### Post by undoIT on 2009-05-15
Is there any way to reload the touchpad driver without have to restart X or reboot?

---

### Post by Strazhce on 2009-07-28
Hi.

I have Dell E6500. I've followed suggestions of Nexuss - git clone, modify Makefile build psmouse.ko, install in into modules, rmmod/modprobe and it didn't fix touchpad/trackpoint to work correctly. 
The thing is - I have a bit different issue here. If I use trackpoint/touchpad and touchpad buttons, mouse "locks" on certain window (e.g. Firefox). When I alt-tab to konsole and click it (e.g. with USB mouse), click goes to firefox. If I switch desktops and start clicking left/right mouse buttons like mad, it some times looses lock. But then it regains it again...

Any similiar exprience? Any ideas?

Thx.
Strazhce

---

### Post by robobart on 2009-07-31
Hi, I have a dell e4300 - same problem

Please keep this post going until we get it completely fixed :)

---

### Post by Strazhce on 2009-08-18
Well, it just started working. Don't know why. Today my Dell got its top cover replaced together with touchpad. But also last time I've upgraded my system fully to Karmic Development. Know I'm downloading more (400 MB) of updates, so maybe next time I boot, it will stop working again :)

---

### Post by undoIT on 2009-08-18
> **Strazhce said:**
> Well, it just started working. Don't know why. Today my Dell got its top cover replaced together with touchpad. But also last time I've upgraded my system fully to Karmic Development. Know I'm downloading more (400 MB) of updates, so maybe next time I boot, it will stop working again :)

Please keep us updated. Also, is it possible to check if you have a Synaptic touchpad now (instead of the Alps)?

---

### Post by Strazhce on 2009-08-18
Ok, today is 18.8.2009. Now  I have current Karmic with KDE 4.3. All works ok (basic click, right edge scrolling, tap and hold for dragging)

[LIST]
[*]Unhacked kernel linux-image-2.6.31-6-generic (i.e. I haven't applied a patch suggested in forums).
[*]cat /proc/bus/input/devices reports AlpsPS/2 ALPS DualPoint TouchPad, which is probably correct (it is touchpad + stick).
[*]tpconfig still reports Synaptics touchpad, it reported synaptics touchpad before as well.
[*]HAL: /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi is unmodified.
[*]xorg.conf contains
[/LIST]
> Section "Module"
        Load "synaptics"
EndSectionWindows use Alps driver, so I suppose it is still Alps.

I don't understand, what has changed :-( I guess I should have checked out linux vs. touchpad on E6500 before tech guy has replaced it (the reason was something totally unconnected to touchpad).

Strazhce

---

### Post by undoIT on 2009-08-18
> **Strazhce said:**
> Ok, today is 18.8.2009. Now  I have current Karmic with KDE 4.3. All works ok (basic click, right edge scrolling, tap and hold for dragging)

[LIST]
[*]Unhacked kernel linux-image-2.6.31-6-generic (i.e. I haven't applied a patch suggested in forums).
[*]cat /proc/bus/input/devices reports AlpsPS/2 ALPS DualPoint TouchPad, which is probably correct (it is touchpad + stick).
[*]tpconfig still reports Synaptics touchpad, it reported synaptics touchpad before as well.
[*]HAL: /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi is unmodified.
[*]xorg.conf contains
[/LIST]
Windows use Alps driver, so I suppose it is still Alps.

I don't understand, what has changed :-( I guess I should have checked out linux vs. touchpad on E6500 before tech guy has replaced it (the reason was something totally unconnected to touchpad).

Strazhce

Sounds like the Alps driver has been fixed, which is very good news. The problem with the touchpad jumping around and the functionality getting disabled / acceleration being set low after some use is a bugger. Can't wait for 9.10 if this is the case!

---

### Post by bregnernice on 2009-08-31
I just made a clean install of karmic to counter these problems (random clicking, left/right buttons, making folders) making my cpu sometimes useless and driving me insane. Unfortunately the issues remain in karmic and im eagerly awaiting a fix.

---

### Post by Strazhce on 2009-08-31
> **bregnernice said:**
> I just made a clean install of karmic to counter these problems (random clicking, left/right buttons, making folders) making my cpu sometimes useless and driving me insane. Unfortunately the issues remain in karmic and im eagerly awaiting a fix.
IMO my touchpad was replaced by some other ALPS model. I don't have any other explanation, why it would magically work.

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

### Post by charles.figura on 2009-11-05
I just got a Dell E6400, and 'xinput list' indicates that Karmic recognizes both the AlpsPS/2 DualPoint Touchpad AND the DualPoint Stick.

Most of the time it works well, but there is some skipping around with the stick (which I use most of the time) and the left stick button (the button above the touchpad) fails to register (or so it seems).  I have a hunch that much of the pointer skipping I experience occurs when I'm dragging and using that button.

Has anyone else observed this particular skipping behavior?  I'm trying to figure out whether this might indicate a hardware problem in the button.

Thanks!

---

### Post by erik.osterholm on 2009-11-06
What do you mean by "skipping around?"  Does the pointer move around in a seemingly random fashion, and so fast that it apparently just jumps to a new location that may not even be the direction you meant to go?

That's the exact problem that this thread is detailing and that no one seems to have solved to any satisfaction.  It seems to happen if you're using either the stick or the stick's buttons while the pad or the pad's buttons are also being used, or vice versa.  Note that it may be unintentional use, due to your palms accidentally brushing the pad or your fingers brushing the stick while you're typing.

---

### Post by charles.figura on 2009-11-06
> **erik.osterholm said:**
> What do you mean by "skipping around?"  Does the pointer move around in a seemingly random fashion, and so fast that it apparently just jumps to a new location that may not even be the direction you meant to go?

...
Note that it may be unintentional use, due to your palms accidentally brushing the pad or your fingers brushing the stick while you're typing.

Generally, I see a lot of screwey jumping back to the beginning of the page when I try to drag a scroll bar down, or the pointer keeps jumping to right of screen when I try to drag.  I don't think it's a function of brushing the pad, since I almost *never* use the pad - I've been experiencing this problem (for the most part) with the pointy stick.

---

### Post by lbjay on 2009-11-14
> **charles.figura said:**
> Generally, I see a lot of screwey jumping back to the beginning of the page when I try to drag a scroll bar down, or the pointer keeps jumping to right of screen when I try to drag.  I don't think it's a function of brushing the pad, since I almost *never* use the pad - I've been experiencing this problem (for the most part) with the pointy stick.

I am having the exact same issue on a Latitude e4300. Any action that requires clicking/holding while moving the pointer stick (i.e., dragging an item or scrollbar) causes the mouse pointer to jump up and to the right. I'm having the behavior in both Jaunty & Karmic.

---

### Post by undoIT on 2009-11-14
> **lbjay said:**
> I am having the exact same issue on a Latitude e4300. Any action that requires clicking/holding while moving the pointer stick (i.e., dragging an item or scrollbar) causes the mouse pointer to jump up and to the right. I'm having the behavior in both Jaunty & Karmic.

Probably what is happening is that the knuckle of your thumb is brushing the touchpad while using the tracking stick. I have noticed that this happens occasionally when I am dragging and dropping using the tracking stick and it is because my thumb is touching the touchpad. If I'm careful not to let that happen, then drag and drop works fine. In my opinion, this is a design flaw with the Latitude E series, because there is no recess between the buttons for the tracking stick and the top of the touchpad.

Perhaps there is a way to use syndaemon to disable the touchpad while using the tracking stick (although it may only be possible to disable touchpad while using the keyboard and I'm not sure if syndaemon works with Alps touchpads, but it is worth looking into).

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by vikjon0 on 2009-11-15
> Edit (as root) /etc/modprobe.d/options and add:

Code:

options psmouse proto=bare



This seem to solve the problem for me (on karmic!)

The downside is that the touchpad stays enabled. I did not expect that and there seem to be no way to disable it now...

---

### Post by charles.figura on 2009-11-15
There's been a nice discussion over on launchpad regarding this issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296610](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296610)

There's a set of kernel patches (that patch the psmouse.ko module) in comments 120-122.  I've been running them for a couple days now with great success -
1.  No more 'jumping' cursor
2.  No more sticking LH button
3.  Much more reliable scrolling action on the touchpad edge.

I don't know when the patches are going to work their way out to a proper package (there's still testing going on), but if you're not afraid of patching your kernel, you can get this problem fixed.

If you're running the stock 2.6.31-15-generic-pae ubuntu kernel, you can use the patched module I've attached.

To test it out, save the attached module somewhere handy & unzip it, and do the following:
$ sudo rmmod psmouse        (all pointer activity will go away)
$ sudo insmod psmouse.ko

If everything is happy, you can copy that module to:
/lib/modules/2.6.31-15-generic-pae/kernel/drivers/input/mouse/psmouse.ko
and you should be ready to go.  The new module will be automatically loaded when you reboot.

If you get an error on the insmod, you're probably NOT running the PAE kernel (which is the kernel variant to deal with 4+GB ram).  You could install the PAE kernel and go back through the above (there's no problem if you have less than 4GB on your machine) or compile the patch against your kernel.

-Charlie

---

