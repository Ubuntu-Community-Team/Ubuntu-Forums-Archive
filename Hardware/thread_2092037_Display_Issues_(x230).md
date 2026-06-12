---
title: "Display Issues (x230)"
date: 2012-12-06
forum: Hardware
---

### Post by nhkim on 2012-12-06
I tried searching for solutions and could not find one to my specific problem, so if this issue has been brought up before and solved, I apologize. 

I'm trying to run xubuntu or voyager or some other xfce desktop on my Thinkpad x230 and ran into a slight problem. 

My display does a little "flicker" every time there is movement on screen. I first noticed it while watching a video, but it's more noticeable when I drag a window across the screen. It does this wavy flicker as if the display is not catching up with the actual movement of whatever is on screen. I don't have the same issue on Windows 8, so I'm guessing it is an issue with the Ubuntu variant.

I have tried updating drivers and, although I don't know how to update kernel, I know I'm running 3.5. I've tried it with Xubuntu and Voyager. I will be trying it with Manjaro and Ubuntu to see if the problem is just on Ubuntu variants, xfce, or linux in general. 

Any help would be much appreciated.

---

### Post by gordintoronto on 2012-12-06
More info might help. What is your video adapter? (Run this command in Terminal: lspci
then find the line which includes "vga".)

Did you install an "additional driver"?

The X230 is a high-powered machine, I'm surprised you chose Xubuntu.

To get the complete kernel version, open Terminal and type the command: uname -a

---

### Post by nhkim on 2012-12-07
> **gordintoronto said:**
> More info might help. What is your video adapter? (Run this command in Terminal: lspci
then find the line which includes "vga".)

Did you install an "additional driver"?

The X230 is a high-powered machine, I'm surprised you chose Xubuntu.

To get the complete kernel version, open Terminal and type the command: uname -a

I will do that in the morning as I am currently running Windows 8. Unless you're just talking about the graphics card, in which case, I have intel 4000hd.

I did, however, run all the updates and upgrades from terminal after I installed xubuntu. I didn't see any "additional driver" options. 

Also, what's wrong with Xubuntu? 

Should I be considering something else?

---

### Post by nhkim on 2012-12-07
Wanted to add that the problem did not occur in Fedora (gnome3).

---

### Post by QIII on 2012-12-07
You won't see any additional driver offered because the Intel driver is rolled into the kernel by default.

And there is nothing wrong with Xubuntu.  There may be some misperceptions that it is somehow "inferior" because it is light and often recommended for low spec machines.  I use it because I like it personally.

Don't know that I have any particular words of wisdom about the flicker.

---

### Post by nhkim on 2012-12-07
> **QIII said:**
> You won't see any additional driver offered because the Intel driver is rolled into the kernel by default.

And there is nothing wrong with Xubuntu.  There may be some misperceptions that it is somehow "inferior" because it is light and often recommended for low spec machines.  I use it because I like it personally.

Don't know that I have any particular words of wisdom about the flicker.

I like Xubuntu over the regular Ubuntu too. Besides, I'm running a very small (128) ssd, and need all the space I can get...

As for the problem. I think it is something to do with xfce. I ran Fedora Gnome and everything was fine, but when I loaded up Fedora with xfce, I got the flicker. I'm trying to run regular Ubuntu to see if it's the same. I hope it's fixable. I like xfce the best so far.

---

### Post by gordintoronto on 2012-12-07
I agree that there's nothing wrong with Xubuntu. My main system currently dual-boots Xubuntu 12.10 and Linux Mint 13. (I mostly use Mint.)

I think you could install gnome-desktop-environment, then select Gnome at logon, to see if that solves the problem.

---

### Post by nhkim on 2012-12-08
VGA: Intel Corp 3rd gen core processor Graphics controller (rev 09).

Kernel 3.5.0-19 generic

__________________________________

I've also tried regular Ubuntu, xubuntu with Gnome classic, Xubuntu with Cinnamon. None of these DE have the flickering problem. I think something is off with the xfce. Is there something I could do to fix it? I really prefer xfce over all the ones I've tried so far :/

---

### Post by linrunner on 2012-12-08
Hi,

please show your driver parameters and kernel boot options:
```
sudo grep '.*' /sys/module/i915/parameters/*
cat /proc/cmdline
```

---

### Post by nhkim on 2012-12-10
```
/sys/module/i915/parameters/enable_hangcheck:Y
/sys/module/i915/parameters/fbpercrtc:0
/sys/module/i915/parameters/i915_enable_fbc:-1
/sys/module/i915/parameters/i915_enable_ppgtt:-1
/sys/module/i915/parameters/i915_enable_rc6:-1
/sys/module/i915/parameters/invert_brightness:0
/sys/module/i915/parameters/lvds_channel_mode:0
/sys/module/i915/parameters/lvds_downclock:0
/sys/module/i915/parameters/lvds_use_ssc:-1
/sys/module/i915/parameters/modeset:-1
/sys/module/i915/parameters/panel_ignore_lid:0
/sys/module/i915/parameters/powersave:1
/sys/module/i915/parameters/reset:Y
/sys/module/i915/parameters/semaphores:-1
/sys/module/i915/parameters/vbt_sdvo_panel_type:-1

``````
BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic root=UUID=bdb1f797-3bf6-4242-bd3f-edcc12d12caf ro quiet splash vt.handoff=7
```

---

### Post by nhkim on 2012-12-10
Some more notes: 

The problem did not occur in regular Ubuntu. It also did not flicker when I ran Gnome and Cinnamon on Xubuntu. However, I got the flickers again when I ran Kubuntu. The flickers were less noticeable in KDE than xfce.

---

### Post by Pjotr123 on 2012-12-10
What Xubuntu version are you using? 12.04 LTS or 12.10?

---

### Post by nhkim on 2012-12-10
> **Pjotr123 said:**
> What Xubuntu version are you using? 12.04 LTS or 12.10?

12.10

But I'm getting the problem with xfce. The same problem exists in Fedora with xfce.

---

### Post by linrunner on 2012-12-10
> **nhkim said:**
> [code]/sys/module/i915/parameters/lvds_downclock:0
Parameters are fine. I thought lvds_downclock might be the problem, but it's off (default).

---

### Post by Yellow Pasque on 2012-12-10
Have you tried turning the compositor on/off (in the Window Manager Tweaks section of xfce's settings)? It seems to be a known issue with intel/xfce: [http://old.nabble.com/Tearing-VSync-in-xfwm4-compositor-due-to-XRender-tt32553406.html#a32553406](http://old.nabble.com/Tearing-VSync-in-xfwm4-compositor-due-to-XRender-tt32553406.html#a32553406)

xfce/xfwm (with compositing on) and KDE/Kwin (without OpenGL enabled) use Xrender, which lacks vsync, hence the tearing.

---

### Post by nhkim on 2012-12-10
> **Temüjin said:**
> Have you tried turning the compositor on/off (in the Window Manager Tweaks section of xfce's settings)? It seems to be a known issue with intel/xfce: [http://old.nabble.com/Tearing-VSync-in-xfwm4-compositor-due-to-XRender-tt32553406.html#a32553406](http://old.nabble.com/Tearing-VSync-in-xfwm4-compositor-due-to-XRender-tt32553406.html#a32553406)

xfce/xfwm (with compositing on) and KDE/Kwin (without OpenGL enabled) use Xrender, which lacks vsync, hence the tearing.

Tried it... didn't solve the problem. 

I think it makes it a little better, but it's very marginal. Enabled or not, the tearing is still there and really noticeable.

---

### Post by nhkim on 2012-12-10
> **Temüjin said:**
> Have you tried turning the compositor on/off (in the Window Manager Tweaks section of xfce's settings)? It seems to be a known issue with intel/xfce: [http://old.nabble.com/Tearing-VSync-in-xfwm4-compositor-due-to-XRender-tt32553406.html#a32553406](http://old.nabble.com/Tearing-VSync-in-xfwm4-compositor-due-to-XRender-tt32553406.html#a32553406)

xfce/xfwm (with compositing on) and KDE/Kwin (without OpenGL enabled) use Xrender, which lacks vsync, hence the tearing.

I believe I found the solution!
[http://www.webupd8.org/2012/10/xfce-sync-to-vblank-support-for-xfwm.html](http://www.webupd8.org/2012/10/xfce-sync-to-vblank-support-for-xfwm.html)

I Googled "xfce screen tearing" instead of "display flickers" and was able to find that. So far, it seems to work pretty damn well. 

Thanks everyone for the help.

---

