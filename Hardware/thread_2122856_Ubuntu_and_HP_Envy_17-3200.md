---
title: "Ubuntu and HP Envy 17-3200"
date: 2013-03-06
forum: Hardware
---

### Post by jwhirl06 on 2013-03-06
So I've got a HP Envy 17t-3200 CTO. The specs are as follows:

Intel Core i7 3610QM 
16GB Corsair Vengeance 1600MHZ DDR3
AMD Radeon HD 7850M 1GB | Intel HD Graphics

I was wondering a few things, firstly, I have had absolutely no success following the guides as far as getting my hybrid graphics working. Ivybridge Mobile works great out of the box, until I follow through with the guides to get the hybrid setup working then it just boots me to Low Graphics Mode and I cannot fix it after that point. How do I blacklist the ATI card so Ubuntu never tries to install it or load the modules for it?

Secondly, I have a fancy synaptics clickpad on this, everything works great except using it to click and moving the mouse, the cursor will jump an inch or two after I move it, and also move up or down when I try to click something. Is there a better driver or some settings I can put in the config files for it?

Any help would be greatly appreciated. Thanks!

---

### Post by Mark Phelps on 2013-03-08
Sorry, but Switchable Graphics is not supported well in Linux.  Those machines come with drivers (for MS Windows, of course) supplied by the machine vendors.  Linux drivers are not available.  If you try to install drivers from AMD, they won't work.

The link below is old, but it has some suggestions:

[http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html]("http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html")

---

