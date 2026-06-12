---
title: "Touchpad disable button hp dv6t (Lucid)"
date: 2010-04-18
forum: Hardware
---

### Post by doans on 2010-04-18
I have a problem with my HP dv6t laptop after I use the touchpad disable button. After I turn the touchpad disable button on the touchpad is indeed disabled, but the keyboard does not work anymore. I am running Beta2 of Lucid Lynx. This problem is frustrating. This has been a great experience with Lucid on this laptop with the exception of this problem.

I have been looking for a way to "re-enable" the keyboard after pushing this button but with no luck. However it should be noted that the only way I can fix this problem is for ctrl-alt-del and then do a restart.

How can I get the keyboard back after pushing this button? Thanks for any advice on this problem.

---

### Post by doans on 2010-04-24
I have not been able to find any way around this problem. If you click the touchpad disable button then the keyboard does not work again. Have to restart the computer just to get the keyboard back. This is a bummer.

Any ideas anybody?

---

### Post by kenrowe410 on 2010-04-29
+1.  Same problem.  I can't find any other way to re-enable the keyboard, either.

Thanks.

---

### Post by P4man on 2010-04-29
File a bug report on launchpad. I cant see this bug reported there yet and it clearly is one:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by kenrowe410 on 2010-04-29
Bug filed!  

[https://bugs.launchpad.net/ubuntu/+bug/571638.]("https://bugs.launchpad.net/ubuntu/+bug/571638")

---

### Post by lidex on 2010-04-29
This may help:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#touchpad]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#touchpad")

---

### Post by Toddohl on 2010-05-11
From the Ubuntu Software Center try installing the "Pointing devices" (gpointing-device-settings) control Panel -- the description lists it as a successor to GSynaptics -- worked for me.

---

### Post by doans on 2010-05-17
I still have not found a solution to this problem, but I have found a workaround. At least I can get my keyboard to respond again after tapping the touchpad disable button.

I found this thread [http://ubuntuforums.org/showthread.php?t=1478237]("http://ubuntuforums.org/showthread.php?t=1478237") and pressing Ctrl-Alt-F1 and then Ctrl-Alt-F7 gets the keyboard to work again!!

---

### Post by headcheese3 on 2011-04-28
Raagh!!! I have had this problem for a while, instead of not being able to disable I have not been able to enable my touchpad after messing with the touchpad disable button. I have tried turning it on and off again and no results. I am using 10.10 and on a HP Pavilion dv6000

---

### Post by mmiller7 on 2011-05-08
I too would be interested in a solution or workaround for this...I have a HP dv2000t and a HP dv6tQ, both of which would be nice to dual-boot but the touchpad not being able to re-enable is a real showstopper.
 
I treid the xorg.conf thing on the other site but I ran into two problems -- there was no xorg.conf in Lucid (10.04) and when I tried to make one it broke my install.
 
So put me on the list looking for a way to re-enable my touchpad.
 
-Matt
 
 
P.S. I would have just used Natty (11.04) which seems to fix the touchpad on LiveCD but it won't tell me my battery remain (just says "estimating" until it dies) and I read there are known battery & temp issues on Natty.

---

