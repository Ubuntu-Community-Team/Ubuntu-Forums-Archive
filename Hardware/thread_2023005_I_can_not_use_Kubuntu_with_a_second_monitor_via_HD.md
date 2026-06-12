---
title: "I can not use Kubuntu with a second monitor via HDMI cable."
date: 2012-07-11
forum: Hardware
---

### Post by NBPX on 2012-07-11
I have a laptop with an ATI Mobility Radeon HD 5470 and would like to use a second monitor, which is actually a TV, via HDMI.

The problem is that the system does not recognize the second monitor. I can not even switch the display between the laptop monitor and TV.

The problem is not with the hardware because I can do this in Windows 7.

To say the truth I managed to send the screen image up to projectors. Only in this case I have problems.

---

### Post by Ubun2to on 2012-07-11
Have you installed the AMD Catalyst Control Center drivers yet?

---

### Post by NBPX on 2012-07-11
Yes. I Can do that with a VGA cable and Catalyst. 

But with the HDMI cable it not works.

The problem with VGA is that I cannot use widescreen.  

My TV/Monitor is a Samsung SyncMaster T240M. In its screen appears a message saying "No signal" when using Kubuntu and HDMI cable.

---

### Post by NBPX on 2012-07-12
xrandr output:

> 
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1920 x 1920
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1366x768       60.0*+
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   1280x600       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   640x480        60.0 +
CRT1 disconnected (normal left inverted right x axis y 

---

### Post by Ubun2to on 2012-07-13
> **NBPX said:**
> Yes. I Can do that with a VGA cable and Catalyst. 

But with the HDMI cable it not works.

The problem with VGA is that I cannot use widescreen.  

My TV/Monitor is a Samsung SyncMaster T240M. In its screen appears a message saying "No signal" when using Kubuntu and HDMI cable.

Go into the Displays settings menu. Not sure how to get to that on KDE, but there should be a display configuration program somewhere in the settings. Make sure the TV is set to On.

---

### Post by rvdli on 2012-07-13
Well, "traditional" Ubuntu with Gnome/Unity works pretty well with secondary monitors and bigger widescreen resolutions.

But my experiences with Kubuntu aren't so good. I needed to create manually a xorg.conf file for it to recognize my work monitor native resolution (1440x900), even when it works fine with Windows or Gnome. 

Don't know if the issue is related to KDE or Kubuntu itself, but that was the only way I could make it work. This computer has an onboard Intel G31 card, btw.

---

### Post by NBPX on 2012-07-13
> **rvdli said:**
> Well, "traditional" Ubuntu with Gnome/Unity works pretty well with secondary monitors and bigger widescreen resolutions.

But my experiences with Kubuntu aren't so good. I needed to create manually a xorg.conf file for it to recognize my work monitor native resolution (1440x900), even when it works fine with Windows or Gnome. 

Don't know if the issue is related to KDE or Kubuntu itself, but that was the only way I could make it work. This computer has an onboard Intel G31 card, btw.
I do not want to leave KDE. The KDE interface is much more beautiful and enjoyable, especially after months of modifying it to stay exactly the way I like it and because it has a few little tricks that make my life easier, for example, open a console the currently open folder, and because I hate Unity.


But now I see I'll have to migrate to Ubuntu.

Can I make the Ubuntu interface more like KDE, at least? Is there a theme similar to Oxygen?

---

### Post by NBPX on 2012-07-13
> **Ubun2to said:**
> Go into the Displays settings menu. Not sure how to get to that on KDE, but there should be a display configuration program somewhere in the settings. Make sure the TV is set to On.

I tried this, but it has nothing on these menus to help me.

To be honest, I can put in widescreen mode, but to do this I need to use a function of the TV that stretches the image horizontally decreasing sharpness. It is not very beautiful to watch ...

---

### Post by Ubun2to on 2012-07-15
> **NBPX said:**
> I do not want to leave KDE. The KDE interface is much more beautiful and enjoyable, especially after months of modifying it to stay exactly the way I like it and because it has a few little tricks that make my life easier, for example, open a console the currently open folder, and because I hate Unity.


But now I see I'll have to migrate to Ubuntu.

Can I make the Ubuntu interface more like KDE, at least? Is there a theme similar to Oxygen?

Simple.
1. Install Ubuntu.
2. Download KDE from the Software Center.
3. Ignore the Unity option, or, get rid of it. To get rid of it...
This gets rid of Unity as well as all of the features included with it.
```
sudo apt-get remove unity unity-2d-places unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications gir1.2-unity-4.0 unity-common indicator-sound indicator-power indicator-appmenu libindicator6 indicator-application evolution-indicator indicator-datetime indicator-messages libnux-1.0-0 nuxtools
```
If you only want to remove Unity and none of the features, do this command, instead:
```
sudo apt-get remove unity unity-2d
```
My source:
[http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm)

---

### Post by NBPX on 2012-07-15
But in this case will not have access to the Unity lenses?

I do not like the Unity, but this feature seems very attractive. I would like it in KDE.


"2. Download KDE from the Software Center."

It's possible to install Unity on Kubuntu to test before? It's hard to revert the changes?

---

### Post by Ubun2to on 2012-07-17
> **NBPX said:**
> But in this case will not have access to the Unity lenses?

I do not like the Unity, but this feature seems very attractive. I would like it in KDE.


"2. Download KDE from the Software Center."

It's possible to install Unity on Kubuntu to test before? It's hard to revert the changes?

You won't get Unity lenses unless you do just this:
```
sudo apt-get remove unity unity-2d
```
But, the Unity lenses are literally useless without Unity itself.

You actually can download Unity on Kubuntu via the Software Center.

---

### Post by NBPX on 2012-11-13
Ok, now I have Ubuntu 12.10 on my notebook, but the problem remains.


But don't using Catalyst because it make the window borders and panels disappear. I'm using x.org driver.

---

