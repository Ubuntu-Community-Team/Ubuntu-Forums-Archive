---
title: "Joystick still acts as mouse after xserver-xorg-input-evdev update"
date: 2008-11-14
forum: Hardware
---

### Post by Dodongo Dislikes Smoke on 2008-11-14
I got the updated version of xserver-xorg-input-evdev, the 0ubuntu6 version, a couple days back, yet my joystick still moves the mouse cursor around, and is not recognized by any games.  I got rid of jscal and those other configuration programs too, as suggested at [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done).

I'm running the x86 version of Intrepid.  In some of the posts about the issue I dug up, it was suggested this was a amd64 issue only.  Was the fix exclusive to that architecture?  If not, what am I doing wrong?

---

### Post by wgrant on 2008-11-15
Have you removed xserver-xorg-input-joystick? -joystick will turn joysticks into mice regardless of what evdev thinks.

---

### Post by Dodongo Dislikes Smoke on 2008-11-15
I forgot to mention that I had gotten rid of that too.  I was sure that was going to be the fix too, when I first read that tip.

---

### Post by Dodongo Dislikes Smoke on 2008-11-18
Running dpkg-reconfigure on xserver-xorg-input-evdev didn't get me anywhere either.  Is this just plain old unsolved despite what the above linked wiki page claims?

---

### Post by Dodongo Dislikes Smoke on 2008-11-25
Adding 

Section "ServerFlags"
 Option "AutoAddDevices" "False"
EndSection

to my xorg.conf makes my joysticks work as they should, but I'm concerned about additional loss of functionality because of this.  I'd like to see the fix added to the amd64 version of evdev ported to the x86 version.

---

### Post by bzoomer16 on 2008-12-23
> **Dodongo Dislikes Smoke said:**
> 
I'm running the x86 version of Intrepid.  In some of the posts about the issue I dug up, it was suggested this was a amd64 issue only.  Was the fix exclusive to that architecture?  If not, what am I doing wrong?

I'm on Intrepid AMD64, and this is a problem for me. I have a Logitech RumblePad 2 and it works great as a mouse (I would have killed for this functionality out-of-the-box with Windows...) but it won't work as a joystick.

The jscalibrator program sees both analog sticks responding to the changes in position and buttons work, but it's kind of depressing... What's the recommended course of action? I've tried doing the dpkg-reconfigure xserver-xorg-input-evdev and removed the xserver-xorg-input-joystick package, but nothing's changed. :(

---

### Post by cybergrunt on 2009-01-14
I'm running Intrepid on a Dell Latitude and I've tried all the 'fixes' out there and I'm still getting this with my Sidewinder Game Pad Pro. On a mission...

---

### Post by windsurfer49 on 2009-02-09
I use the Saitek X45 with Ubuntu 8.1 Intrepid Ibex.

It would not work until I did the following.

1) Used Synaptic package manager to install xserver-xorg-input-evdev version 1:2.0.99+git20080912-Oubuntu6

2) Modified file:///usr/share/hal/fdi/policy/20thirdparty/10-x11-joystick.fdi as below:

Added following. Note 1) the input.x11_driver type is 'evdev' rather than 'joystick' which the other joysticks in the file have. Note 2) It really does need "Saitek Saitek X45" as shown below. I found this by creating the hal diff files mentioned elsewhere.

<!-- Saitek X45 -->
â&#710;&#8217;<match key="info.product" contains="Saitek Saitek X45">
<merge key="input.x11_driver" type="string">evdev</merge>
</match>

I then had some joystick calibration problems, which I fixed with jscalibrator. This was probably my own fault for having played with it at an earlier date.

It now works fine. Maybe you could try playing with this area of the joystick.fdi file.

---

