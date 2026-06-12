---
title: "usb keyboard unresponsive after a couple of minutes"
date: 2008-08-08
forum: Hardware
---

### Post by OliverN on 2008-08-08
[COLOR="Blue"][EDIT: Some regular update has solved this problem. I don't know why it ever occurred and I guess I never will][/COLOR]

Every time I boot up my computer, a few minutes will pass until my usb keyboard becomes unresponsive.

Up until that point it will sometimes 'lock' on a certain key, writing it over and over until I press the delete key. It will also occasionally miss keystrokes.

This is a pretty standard keyboard. An Enermax Aurora. It's connected to my msi k9a2 platinum mobo. Never had problems in Vista.

What's up with that?

---

### Post by ARhere on 2008-08-08
Debugging steps.

1. Test the keyboard on another computer, both Vista and Ubuntu alike.
2. Test the problem PC with another keyboard, must be USB as well.

Keyboards take a pounding.  Just because it worked in the past with Vista is circumstantial.  Test and write back with more detail.

-AR

---

### Post by OliverN on 2008-08-08
> **ARhere said:**
> Debugging steps.

1. Test the keyboard on another computer, both Vista and Ubuntu alike.
2. Test the problem PC with another keyboard, must be USB as well.

Keyboards take a pounding.  Just because it worked in the past with Vista is circumstantial.  Test and write back with more detail.

-AR

Thanks for your reply.
1. Well, I have tested the keyboard with another pc, a Dell Inspiron 6400 in Ubuntu Feisty and Windows XP. No problems there. I don't have access to another Vista/Hardy pc.

2. The PC I'm on right now dual boots a fresh Hardy install and Vista Ultimate. I have no problems using this keyboard, which is quite new, in Vista.

I don't think there's anything wrong with my keyboard or my usb ports, really. Couldn't this be an issue in Hardy somehow?

---

### Post by ARhere on 2008-08-08
> **OliverN said:**
> Thanks for your reply.
1. Well, I have tested the keyboard with another pc, a Dell Inspiron 6400 in Ubuntu Feisty and Windows XP. No problems there. I don't have access to another Vista/Hardy pc.
That is good enough to say the keyboard is fine.

> 
2. The PC I'm on right now dual boots a fresh Hardy install and Vista Ultimate. I have no problems using this keyboard, which is quite new, in Vista.
Have you tried plugging another USB keyboard into the PC where the trouble was occurring?  That needs to be the next thing you do.  If you plug in another USB keyboard and the same behavior occurs, then that narrows it down a bit.  If it really only does it with Ubuntu and not Vista, I will be confused.  

Just to be sure, in Vista change the repeat key rate to max speed. *In XP I think it is under Control Panel-->keyboard, the app where you set how long you press a key down so it starts repeating.*  If you do that and the same behavior occurs in Vista as well, then it is a hardware/firmware problem that you just could not see in Vista.

Do that, and try another USB keyboard in the PC and let us know.

-AR

---

### Post by OliverN on 2008-08-12
> 
Have you tried plugging another USB keyboard into the PC where the trouble was occurring?

I'm sorry, I wasn't reading your post right. I have bought myself another cheap usb keyboard, and this one gives me no trouble. Neither in Vista nor Ubuntu. I tried the old and newly bought keyboards in Fedora also, and it's the same: The old (Enermax) malfunctions, but the new, cheap one doesn't.

> 
Just to be sure, in Vista change the repeat key rate to max speed. *In XP I think it is under Control Panel-->keyboard, the app where you set how long you press a key down so it starts repeating.*  If you do that and the same behavior occurs in Vista as well, then it is a hardware/firmware problem that you just could not see in Vista.

The behaviour did *not* occur in Vista.

I have to mention that I never had problems with my keyboard outside of OSs.
So... I guess the Linux distros are having trouble with my keyboard (or vice versa) for some reason? If there's nothing to be done, then I guess I can live with switching keyboards.

---

