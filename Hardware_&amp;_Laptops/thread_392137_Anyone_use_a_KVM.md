---
title: "Anyone use a KVM?"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by newbie22 on 2007-03-24
Do they work well?  Any problems at all?

Does it require to be plugged into the wall or does it consume the power of a computer?

Compatible with Linux?

I can understand how it shares the keyboard and mouse with 2 computers.  But how does it share the video too?  Is there a slot for a video card in the KVM or something?

---

### Post by jakev383 on 2007-03-24
> **newbie22 said:**
> Do they work well?  Any problems at all?

Does it require to be plugged into the wall or does it consume the power of a computer?

Compatible with Linux?

I can understand how it shares the keyboard and mouse with 2 computers.  But how does it share the video too?  Is there a slot for a video card in the KVM or something?
I use it for my Linux servers. It allows (my version at least) 8 of my servers to share 1 mouse, keyboard, and monitor. To change to the firewall, hit button 1. To change to the DNS server, hit button 2, etc. Works rather well, and the KVM uses the power provided by the PC's to power itself but requires 110V for the flat panel I use to manage them.
Forgot: it plugs into the standard PS/2 and VGA plugs of the computers. No special cards needed.
Hope that helps.

---

### Post by newbie22 on 2007-03-24
Thanks for replying so fast!  I have further questions.

Which computer would it consume power from?  Do I have to set up an alpha-computer?  And this alpha computer must be on in order to use the KVM?  In otherwords, if alpha-computer is off, I would not be able to use the KVM on the other computer(s)?

I have a 250 watts that uses 115V, would that be sufficient to use a KVM? If not, what is the minimum watts?

So the KVM plugs into the PS/2 of one of my computers.  How does the rest of the computer(s) connect to the KVM?  Does the KVM have wires to connect to the other computer(s) or does the other computer(s) have to be connected to the alpha-computer in some otherway?

Also, I only have onboard video, does that mean I would not get video in the KVM?  The other computer(s) will be stuck in text mode?  Or the KVM would not work because it is missing the video?

---

### Post by jakev383 on 2007-03-24
> **newbie22 said:**
> Thanks for replying so fast!  I have further questions.

Which computer would it consume power from?  Do I have to set up an alpha-computer?  And this alpha computer must be on in order to use the KVM?  In otherwords, if alpha-computer is off, I would not be able to use the KVM on the other computer(s)?

I have a 250 watts that uses 115V, would that be sufficient to use a KVM? If not, what is the minimum watts?

So the KVM plugs into the PS/2 of one of my computers.  How does the rest of the computer(s) connect to the KVM?  Does the KVM have wires to connect to the other computer(s) or does the other computer(s) have to be connected to the alpha-computer in some otherway?

Also, I only have onboard video, does that mean I would not get video in the KVM?  The other computer(s) will be stuck in text mode?  Or the KVM would not work because it is missing the video?

It grabs power from the active computer. And it only grabs enough from the PS/2 ports to fire up the electronics. The monitor is usually external so it plugs into power by itself.
The KVM will have a bunch of plugs. Each set of 3 will be labeled for "1", "2", "3", etc. You will also have one set called "master" which will be where you plug in the keyboard, mouse, and monitor you want to use. In the plugs for "1" you would run the cables to your first computer (Keyboard, Video, Mouse, which is what KVM stands for). Same for block "2". Each computer you want to switch will plug into the KVM, which will then allow you to change from each computer to the shared keyboard, mouse, and video.
The KVM plugs into your video just like a monitor, so it doesn't matter what video card you have.

---

### Post by newbie22 on 2007-03-24
You mean the "video" is the monitor?  The KVM plugs into the PS/2 (mouse and keyboard) and monitor sockets of one of my computer?

If that is so, then that means I can share not only my keyboard and mouse, but also my monitor?!

---

### Post by jakev383 on 2007-03-24
> **newbie22 said:**
> You mean the "video" is the monitor?  The KVM plugs into the PS/2 (mouse and keyboard) and monitor sockets of one of my computer?

If that is so, then that means I can share not only my keyboard and mouse, but also my monitor?!

Correct. In my setup, I have 8 computers that use 1 keyboard, 1 mouse, and 1 monitor between them all. That's what the KVM was designed to do, instead of having to have 8 keyboards, 8 mice, and 8 monitors.

---

### Post by bobpur on 2007-03-24
This is something you need to research a little bit.
Some KVM switches will do more harm than good. By that I mean poor picture quality, poor keyboard & mouse response and, if you get one that supports audio, poor sound quality. I think most of these problems come from excess cable length more than anything else. Also, the extra connection points that are added.

---

### Post by newbie22 on 2007-03-24
WOW!!!  Amazing!!!

Only if I knew about the KVM a year back, I could have saved plenty on external hardware.


One major thing I am worried about: You know how sometimes the computer freezes the mouse and keyboard?  If it happens to one computer, will it happen to all plugged into the KVM?

Oh, another thing, will it work work if 1 computer is Linux and the other is Windows?

Which brings me to another queston: The drivers.  Is there any specific brand of KVM I should stay away from that does not support Linux?

---

### Post by jakev383 on 2007-03-24
> **newbie22 said:**
> WOW!!!  Amazing!!!

Only if I knew about the KVM a year back, I could have saved plenty on external hardware.


One major thing I am worried about: You know how sometimes the computer freezes the mouse and keyboard?  If it happens to one computer, will it happen to all plugged into the KVM?

Oh, another thing, will it work work if 1 computer is Linux and the other is Windows?

Which brings me to another queston: The drivers.  Is there any specific brand of KVM I should stay away from that does not support Linux?

No drivers needed. Works with Windows and Linux. Usually shows up as whatever keyboard/mouse/monitor you have plugged into it.
And no, if 1 computer locks up just hit the button for another computer and all will be well.

---

### Post by newbie22 on 2007-03-25
Thank you so much, jakev383!  You have been very helpful.

---

### Post by jakev383 on 2007-03-25
> **newbie22 said:**
> Thank you so much, jakev383!  You have been very helpful.
No problem. Good luck!

---

### Post by mrreality13 on 2007-03-25
I have a belkin KVM all I do is hit the "scroll lock" twice then my up OR down arrow to switch towers its prolly my favorite piece of hardware--lol 

[http://www.microcenter.com/single_product_results.phtml?product_id=0201629](http://www.microcenter.com/single_product_results.phtml?product_id=0201629)

i have had this for like a year now:guitar:

---

### Post by pneaveill on 2007-03-26
I also have a belkin KVM and I love it.  One word of warning that was given to me:  -- If you are installing a fresh distro on that KVM computer, leave it in that screen, don't switch screens, as it will say and do evil things to you.

---

