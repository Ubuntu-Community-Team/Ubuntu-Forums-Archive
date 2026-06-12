---
title: "[SOLVED] Scroll wheel only scroll down in vmware"
date: 2008-11-05
forum: General Help
---

### Post by StebQC on 2008-11-05
I just installed Intrepid Ibex in a virtual machine using VMWare Server. The problem is that the mouse wheel can scroll down but not up and it is very annoying.

I have the same problem as this thread but now it is closed without an answer ([http://ubuntuforums.org/showthread.php?t=957276](http://ubuntuforums.org/showthread.php?t=957276))

For your information, xev send button 5 on both direction. My xorg.conf is:

```
Section "InputDevice"
  Driver "vmmouse"
  Identifier "VMware Mouse"
  Option "Buttons" "5"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "IMPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Emulate3Buttons" "true"
EndSection
```

Thanks in advance,
StebQC

---

### Post by Yashiro on 2008-11-05
Comment it all out and reboot?

---

### Post by StebQC on 2008-11-05
> **Yashiro said:**
> Comment it all out and reboot?

No effet. I tried to comment some part, change the ZAxisMapping option to "6 7" with no effect either.

Any other ideas ?

---

### Post by Yashiro on 2008-11-05
If wheelup and wheeldown both return button 5 then there's not alot you can do.

Under Hardy I'd use Btnx or Xbindkeys and Xmodmap. Intrepid is a different beast though and many of the old fixes no longer work.

Does you rmouse wheel work OK on your normal desktop?

---

### Post by StebQC on 2008-11-05
The mouse wheel work perfectly on windows. And it use to work correctly on hardy but when I upgraded to intrepid, the problem started. I reinstall with a clean machine and the same thing happened.

Is it possible that the problem is from the vmmouse driver loaded in xorg.conf ? If so, is it possible to test with the driver from hardy ?

---

### Post by Yashiro on 2008-11-05
Have you tried commenting out the entire section, not just parts of it?

Section "InputDevice"
  Driver "vmmouse"
  Identifier "VMware Mouse"
  Option "Buttons" "5"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "IMPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Emulate3Buttons" "true"
EndSection

---

### Post by StebQC on 2008-11-06
> **Yashiro said:**
> Have you tried commenting out the entire section, not just parts of it?

Yes I have tried that also.

---

### Post by Dil Bert on 2008-11-08
I had the exact same problem. To make matters worse this was not the only problem I had. 

The VMWare window would also "shrink" (did not stay full screen) when it lost focus. Furthermore when the mouse moved over the minimized VMWare bar at the top I would get 2 mouse cursors.

I figured all these problems had something to do with the mouse driver, so I googled for "Ubuntu 8.10 and VMWare mouse driver".

I came accross this link:
[https://edge.launchpad.net/ubuntu/intrepid/i386/xserver-xorg-input-vmmouse/1:12.5.1-1ubuntu5.1]("https://edge.launchpad.net/ubuntu/intrepid/i386/xserver-xorg-input-vmmouse/1:12.5.1-1ubuntu5.1")

Installing the .deb package solved all problems, including the scrolling up.

Hope this helps...

---

### Post by Yashiro on 2008-11-08
Nice find. :)

---

### Post by StebQC on 2008-11-10
> **Dil Bert said:**
> I came accross this link:
[https://edge.launchpad.net/ubuntu/intrepid/i386/xserver-xorg-input-vmmouse/1:12.5.1-1ubuntu5.1]("https://edge.launchpad.net/ubuntu/intrepid/i386/xserver-xorg-input-vmmouse/1:12.5.1-1ubuntu5.1")

Installing the .deb package solved all problems, including the scrolling up.

Hope this helps...

Yes, that was it. Thanks

---

### Post by dcstar on 2008-11-15
> **Dil Bert said:**
> 
........
I came accross this link:
[https://edge.launchpad.net/ubuntu/intrepid/i386/xserver-xorg-input-vmmouse/1:12.5.1-1ubuntu5.1]("https://edge.launchpad.net/ubuntu/intrepid/i386/xserver-xorg-input-vmmouse/1:12.5.1-1ubuntu5.1")

Installing the .deb package solved all problems, including the scrolling up.

Hope this helps...

I notice that this package version in now in the repositories and appears on the upgrade list, but a good get anyhow!

---

