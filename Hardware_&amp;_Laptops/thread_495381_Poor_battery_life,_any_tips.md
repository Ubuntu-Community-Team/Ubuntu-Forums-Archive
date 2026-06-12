---
title: "Poor battery life, any tips?"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by Bazirker on 2007-07-08
My battery life on my notebook in Ubuntu is much worse than it is in Windows XP, and it makes me sad (especially since I only get 100 minutes or so in XP)...does anyone have general tips for how to improve battery life?  I've already got the CPU frequency selector going and it helps, but it still isn't enough.  I guess what I'm looking for are some sort of extended options for power management or some other utility for tweaking power consumption.

There should be a "Hardware and Laptops" sticky with links to some 'mandatory' things that need to happen on notebooks versus desktops...things like installing the CPU frequency selector, setting up touchpads (defining scroll areas, etc), and power management tips (if they actually exist)...I might have to get on that  :)

---

### Post by madmetal on 2007-07-09
since your laptop has intel cpu give a look here
[http://www.linuxpowertop.org/](http://www.linuxpowertop.org/) 
for further powersaving tips you should look what processes work more and use more system resources and find a way to make them run better..
ie. on my old laptop flash animations were killing my cpu so i added adblock+filters so i firefox needs less resources..
opera is lighter than firefox , abiword is lighter than openoffice etc..

---

### Post by Bazirker on 2007-07-10
PowerTOP looks pretty cool, but using Gutsy's kernel or compiling a custom kernel is a requirement to use it, and I can't be fussed.  Come October, I'm gonna remember PowerTOP...

So...aside from obvious stuff like using your computer less (more/bigger processes = less battery), how can I tweak hardware to make it burn less battery?  For example, most laptop manufacturers have an included power utility for XP with different power profiles to control not only backlight and clock speed but also hard drive activity or GPU performance.  Is there anything like that currently available, or is that something perhaps coming in a future release of Ubuntu?  Can those things be quickly and easily changed when going from AC to battery and back?

---

### Post by NikoC on 2007-07-10
Perhaps this might be a good tip, it worked for me:
[http://samwel.tk/laptop_mode/packages/ubuntu]("http://samwel.tk/laptop_mode/packages/ubuntu")

---

### Post by ntetreau on 2007-07-19
Follow the first post of my howto ([http://ubuntuforums.org/showthread.php?t=419772](http://ubuntuforums.org/showthread.php?t=419772)) to turn laptop-mode and yuo can go a step further to enable powersaving on your wifi card (intel only).

Nic

---

