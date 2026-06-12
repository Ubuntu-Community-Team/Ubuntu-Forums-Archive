---
title: "ReConfig proprietary inputs on Sony UX180p UMPC?"
date: 2009-08-20
forum: Hardware
---

### Post by CyyberSpaceCowboy on 2009-08-20
I've installed MoonOS (Ubuntu with Enlightenment desktop)on a Sony UX-180p UMPC (512Mb RAM, 1.2 Core Solo, 30Gb drive).  I love the distro, but I need help getting as many of the proprietary peripherals working as possible. 

My first usability hurdle is the built in J Stick pointing device. Down pressure on the stick is interpreted as mouse button 1 (thankfully, there are two dedicated mouse buttons and a scroll button). The mouse one function on the J Stick is useless (you can't click anything without the mouse skittering away) and unless I use a very light touch, anything the cursor passes over gets clicked or selected (for some reason, MoonOS seems less sensitive than Fedora).

Mouse Settings and Mouse Bindings don't show the J Stick button 1 separately from the dedicated mouse 1 button. Sony had a Windows app that let me customize inputs, including disabling the mouse 1 function on the J pointer.

I've not found a lot in general about Linux on the UX series. I know this is not a trivial question, but where would I start looking to disable mouse clicks on the pointer? I'm guessing there is a way to track inputs in a terminal window and modify a config file to ignore that input.  I also thought of extracting the input config utility from the recovery disk and trying to run it in WINE.  Since I imagine the Sony util modifies the Windows registry, I doubt it would have any effect under Linux.

---

