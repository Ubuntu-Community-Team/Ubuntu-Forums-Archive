---
title: "How do you disable little pc speaker?"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Konopa on 2009-08-02
How do i turn that little pc speaker off inside the case that gives warnings?

OS: Mandriva- Gnome 2009

---

### Post by OscarFoxtrot on 2009-08-02
Open PC box. Find wires going to speaker, they should go to a pair of pins on the motherboard labelled SPKR. Disconnect the wires from the motherboard.

If you have the manual for the motherboard this help you find the relevant connection.

---

### Post by running_rabbit07 on 2009-08-02
Do not do that!  Really?

> **t4thfavor said:**
> Inside of the sound preferences there is sometimes a mixer for system beep. I have in the past shut it off(muted) and the beeping stoped. Though I do believe there are boards that do not have this capability.
  &
> **damis648 said:**
> Open a terminal and type the following:
```
sudo rmmod pcspkr
sudo su -c "echo 'blacklist pcspkr' >> /etc/modprobe.d/blacklist.conf"
```(Yes, the sudo su -c is weird, but sudo does not accept '>>' directly)

These worked for me on a thread I previously made. Don't open your PC and risk ESD damage just for a few beeps.

That advice was given in this[ thread]("http://ubuntuforums.org/showthread.php?t=1224408").

---

### Post by dagrump on 2009-08-02
Disconnecting the speaker, Shouldn't risk ESD if you aren't a total putz, I just switched my hard drive light connecter earlier & the box was on. 
I wouldn't advise adding or removing hardware under power, disconnecting a small plug from a mobo is pretty safe. Touch a metal part of the case before you touch anything else, I rest my arm against something if possible.

---

### Post by Chemical Imbalance on 2009-08-02
> **running_rabbit07 said:**
> Do not do that!  Really?

These worked for me on a thread I previously made. Don't open your PC and risk ESD damage just for a few beeps.


You've never assembled your own desktop then?

You simply ground yourself.

I agree though that a software fix is safer for someone who doesn't know what they are doing.

---

### Post by running_rabbit07 on 2009-08-02
> **dagrump said:**
> Disconnecting the speaker, Shouldn't risk ESD if you aren't a total putz, I just switched my hard drive light connecter earlier & the box was on. 
I wouldn't advise adding or removing hardware under power, disconnecting a small plug from a mobo is pretty safe. Touch a metal part of the case before you touch anything else, I rest my arm against something if possible.

I haven't had any problems working inside my box, but the OP's problem is much easier fixed via software adjustments.

---

### Post by running_rabbit07 on 2009-08-02
> **Chemical Imbalance said:**
> You've never assembled your own desktop then?

You simply ground yourself.

I agree though that a software fix is safer for someone who doesn't know what they are doing.

True, amazingly I know two people who have tried to build there own and fried the motherboard before they ever got to install an OS. Sadly one of them was A+ certified. I've changed RAM in two of my machines but that is as far as I have needed to go so far. I do plan on building my next system though.

---

### Post by dagrump on 2009-08-02
I guess that I also don't consider that they aren't qualified to open the box. Some of the posters might not have any system build in their background. Or in my case just breaking stuff.

---

### Post by running_rabbit07 on 2009-08-02
> **dagrump said:**
> I guess that I also don't consider that they aren't qualified to open the box. Some of the posters might not have any system build in their background. Or in my case just breaking stuff.

After reading your sig, I have a hard time imagining Clint Eastwood in his latest movie playing with a laptop on his porch instead of reading a paper.

---

### Post by dagrump on 2009-08-02
Nope I'm out there with loud power tools. Dremels get kinda loud cutting and grinding on stuff. The sawz-all isn't real quiet either.
****
Yeah, I am old enough that I buy the newspaper. Old habits die hard.

---

