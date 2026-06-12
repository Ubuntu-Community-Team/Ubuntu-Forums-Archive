---
title: "kubuntu's boot sequence stuck.."
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by chikko on 2007-07-24
hey guys.
yesterday night i was playing scorched3d when all of a sudden the system got stuck and the display showed the kubuntu logo (same as when you try to shut down your system - but the progress bar wasn't moving what-so-ever).
anyway, i waited about a minute and when nothing seemed to happen i pressed the power button and the computer shut down.
this morning i tried to power it up, and the boot sequence seemed to be fine, but when the progress bar reaches 100% it suddenly shows me the same logo but with an empty progress bar (just like last night!) and there is no movement even when i wait a long time..
i discovered that if i hit the shift key along with some other key (one of those: "zxcvbnm,./" - i panicked - okay??:)) i can try and log-in console style - so now i can browse around my files and such, but i don't really know what to do next..

i'm keeping on thinking it's just a problem with the hibernation - that all i need to do is cancel the last saved image of my system (maybe when it stuck and i hit the power button - which is also the button for hibernation - the system saved the image) but i don't really know how to handle it from the console, without the GUI..

help..?
thanks! :)

---

### Post by pbcartwright on 2007-07-24
the text-login console you can get to by using CTRL-ALT-F1, so linux is up and running in text mode, this is good.
what happens when you login and run sudo gdm ( for gnome) or sudo kdm (for KDE) ?
this should bring up the gui login and start your window manager. IF you installed the system with a separate /home ( recommended) you can always reload linux and everything will still be working. I reload different flavors of linus and still have all my mail & everything else working.
let us know what happens when you run gdm/kdm..

---

