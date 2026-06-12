---
title: "Mouse Keeps Disconnecting - How To Reconnect?"
date: 2010-07-19
forum: Hardware
---

### Post by Andysan on 2010-07-19
Hi all,

I'm running Ubuntu 10.04 on my desktop and have a Gigabyte GM-M6880 wired USB mouse.  As is commonplace with these mouses they occasionally disconnect and have to be unplugged and plugged back in to continue working.  Under XP this was no problem and under Windows 7 I never have to do this as it seems to manage it itself (I guess).

Under Ubuntu however when I take the mouse out and put it back in it doesnt redetect it.  Is there any key combination or command I can run to redetect the mouse?  Currently I have to either do a Ctrl + Alt + Backspace to resart X or power off and on which is obviously a bit more of a pain.

The problem is definitely with the mouse and not with Ubuntu as such as I've used the mouse with numerous operating systems on many different machines and always had the same problem.  The obvious answer is just to buy a new mouse, but the GM-M6880 is a very nice mouse for the money and similar spec mouses tend to cost £50 instead of the £10 I paid for this one.

Thanks & regards!

---

### Post by ajgreeny on 2010-07-19
> As is commonplace with these mouses they occasionally disconnect and  have to be unplugged and plugged back in to continue working.
What makes you say this?  I don't have a usb mouse for my main machine personally, it's ps2, but on many machines I use, I have usb mice and never see any sort of problem with it stopping.

Are you sure the mouse is really OK, or that your usb port is OK?  Try a different port for it, or if it is connected through a hub, do it direct instead.

---

### Post by Andysan on 2010-07-19
> **ajgreeny said:**
> What makes you say this?  I don't have a usb mouse for my main machine personally, it's ps2, but on many machines I use, I have usb mice and never see any sort of problem with it stopping.

Are you sure the mouse is really OK, or that your usb port is OK?  Try a different port for it, or if it is connected through a hub, do it direct instead.

Sorry, I meant "mice", not "mouses" :)

The disconnection problem is with the mouse itself, not my USB port or OS as it happens on any machine I use it on.  I usually just unplug it and plug it back in and it carries on working fine.

My problem is that with Ubuntu 10.04 when the mouse plays up as it occasionally does, unplugging it and plugging it back in does not fix the issue (regardless of the USB port used), as it has done on other machines/OS'es.

I was reading [this]("http://ubuntuforums.org/showthread.php?t=420537&highlight=detect+camera") ans was wondering if the following command would psuccessfully probe for USB devices? 

```
sudo modprobe -r ehci_hcd
```

When it next plays up I will give it a try and report back.

Cheers!

---

### Post by ajgreeny on 2010-07-19
Sorry, no experience of any of this so can't help further, but your comment:-
> The disconnection problem is with the mouse itself, not my USB port or  OS as it happens on any machine I use it on.  I usually just unplug it  and plug it back in and it carries on working fine.
suggests to me that the mouse is faulty.

---

### Post by Andysan on 2010-07-19
> **ajgreeny said:**
> Sorry, no experience of any of this so can't help further, but your comment:-

suggests to me that the mouse is faulty.

Hi,

No probs, thanks for your time.  It is definitely a problem with the mouse yes, as indicated by many of [these ]("http://www.play.com/PC/PCs/4-/7976590/Gigabyte-GM-M6880-Gaming-Laser-USB-Mouse-Black/ProductReviews.html")reviews where others have the same problem.  I'm just trying to find a way to work around it as its a relatively niche problem and a pretty decent mouse besides.

Will update this post if my meddling works.

---

