---
title: "How does mouse detection work during boot?"
date: 2008-06-26
forum: Hardware
---

### Post by j.daniel on 2008-06-26
Hello,

  A hopefully simple question: How does Ubuntu detect and determine which protocols to use when communicating with the mouse?

  As far as I understand the communication protocols are not identical between - for instance Microsoft and Logitech mice - when it comes to scroll wheel, 3rd mouse button etc.

  Since I have an issue with this, I am wondering:

 1 - When is this detection taking place?
 2 - How can I override which protocol is used?

  My problem is described in another of my threads, but basically I have a KVM switch between the mouse and the computer and everything works OK if I have the switch set to the Ubuntu computer when I power it up. If I don't, when I use the scroll-wheel upwards, I always get a right mouse button event triggered at the end of the scroll.

  So, my theory is that the mouse detection works OK when the computer communicates with the mouse directly during boot (i.e. the KVM switch is set to the Ubuntu computer), but not if the KVM switch emulates the mouse. 

  It is not enough to restart the display manager, so I am not sure that the solution lies in xorg. Or perhaps xorg is started earlier than that?

  Anyway. Anyone have ideas?

Cheers
/ Daniel

---

### Post by j.daniel on 2008-07-07
...bump...

---

### Post by listener on 2008-08-15
Hope you won't mind me bumping here.  I have a logitech (510 I think) and KVM switch.  Much the same config as you, but my wheel and scroll buttons weren't working at all.  I was pretty sure the wheel had worked at one time. 

It ***is *** using the KVM to switch machines which triggers the mouse wheel failing, but in my case if the Ubuntu machine sleeps, it seems to be resetting the mouse.  I am getting some textual error report which goes by very quickly, not sure if it is related.

So I've found that if I put the Ubuntu to sleep, then bring it back, it seems to reset something about the mouse.  This sounds like the same general idea you have.  Thought I'd throw in my info in case it helps.  I've tried several of the other resolutions, such as imwheel, locomo, editing xorg.conf, none seemed to have any good effect.

Thanks

---

