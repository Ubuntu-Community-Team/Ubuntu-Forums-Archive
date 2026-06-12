---
title: "Toshiba NB505 won't hibernate or sleep w/11.04"
date: 2011-04-30
forum: Hardware
---

### Post by odysseus2k7 on 2011-04-30
I recently updated both my netbooks, a Toshiba NB305-400 and Toshiba NB505-500.  The upgrades went fine, but now neither will recover from hibernate or sleep.  Is anyone else having this problem?  What's the solution?  I'd like to be able to have full functionality again.

odysseus2k7

---

### Post by odysseus2k7 on 2011-05-01
> **odysseus2k7 said:**
> I recently updated both my netbooks, a Toshiba NB305-400 and Toshiba NB505-500.  The upgrades went fine, but now neither will recover from hibernate or sleep.  Is anyone else having this problem?  What's the solution?  I'd like to be able to have full functionality again.

odysseus2k7

Correction: Sleep mode works perfectly.  It comes right to life at the password screen, where 10.10 basically restarted the system and brought up the grub.  I never liked Hibernate anyway.  So far, no complaints about Natty.

---

### Post by egbutter on 2011-05-11
On upgrade to 11.04 natty, I am having the same problem with my Toshiba R705 (Portege) -- sleep works fine, hibernate is freezing on the black screen, then shuts off before it saves the state to the hard disk.  

Here [http://ubuntuforums.org/showthread.php?t=1382481&highlight=toshiba+natty+hibernate](http://ubuntuforums.org/showthread.php?t=1382481&highlight=toshiba+natty+hibernate) NB305 suggested that the Intel GMA 3150 might be the problem, but that does not seem right to me.  I had no such problems on maverick.  I also do not understand danielus means when s/he writes that s2disk works (is this a solution I should try? how?) 

Does anybody know what part of the hardware would no longer be interfacing correctly to cause this behavior?  If I can get some high-level advice, I am more than happy to dig in and figure out what is going on.  

Thanks for your help,

---

### Post by dagoss on 2011-05-17
I'm having a similar problem with a Portege r705.

In 10.10, suspend worked perfectly; since upgrading to 11.04 suspend sometimes works, sometimes doesn't. Sometimes I get a black screen, sometimes I type my password and nothing happens. I can't CTRL+ALT+F2 to get to a terminal, just freezes without any error message.

Not really sure how to debug this problem.

It occurred while using Unity, Gnome 2, and Gnome 3 (installed via PPA).

---

### Post by Reg71 on 2011-08-15
I am actually very close to buying one of the nb505s from bestbuy.  the tablet craze has made them very affordable and I am tired of the full sized laptop.  I want the portability.  Is this the only trouble ? I am oka with just running 10.04 on it.  I am using it now for my HTPC and it seems fine.

---

### Post by Reg71 on 2011-09-02
I find that if I choose hibernate, it doesn't work right.  If I just close the cover or let it blank from timeout, then it brings up the password prompt and goes right back where I was.  I ended up with the nb505 and am completely happy with it.  I got 11.04 working easier than any other ubuntu install I have ever tried.

---

