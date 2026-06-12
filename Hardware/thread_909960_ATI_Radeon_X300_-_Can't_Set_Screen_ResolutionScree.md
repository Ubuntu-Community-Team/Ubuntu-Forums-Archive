---
title: "ATI Radeon X300 - Can't Set Screen Resolution/Screen Lag"
date: 2008-09-04
forum: Hardware
---

### Post by treecheetahdolo on 2008-09-04
**PROBLEM SOLVED**
[COLOR="Red"]**ATI Radeon X300 Video Card**[/COLOR]
[U]
**[COLOR="Red"]THE PROBLEM[/COLOR]**[/U]
[COLOR="Indigo"]**Can't Set Screen Resolution/Screen Lag**[/COLOR]

[COLOR="Red"]**fglrx**[/COLOR] and [COLOR="Red"]**Xserver-xgl**[/COLOR] are [COLOR="Red"]**installed**[/COLOR].

I cant Set My screen Resolution and the desktop lags.

Also I've gotten a white screen when enabling Compiz Fusion and Effects on my desktop. I fixed the "White Screen" Problem by uninstalling the ATI Driver I installed from ATI's Site that was for my Hardware. Becuase its main support was another Distro.


I have not a clue what the problem is, all the correct drivers from Synaptic Package Manager are installed for my video card.

[U]
**[COLOR="Red"]THE SOLUTION[/COLOR]**[/U]
[COLOR="Red"]**Uninstall**[/COLOR] [COLOR="Red"]**fglrx**[/COLOR] and [COLOR="Red"]**Xserver-xgl**[/COLOR].
System>Administration>Synaptic Package Manager
Click search icon, look for the 2 packages and mark for uninstall.
[B]
Note:Read Next 2 posts[/B]

[U]
[COLOR="Red"]**Treecheetahdolo's Computer Specifications**[/COLOR][/U]
[B]Motherboard: Intel D915PBL
Video Card: ATI Radeon X300
Memory: 2GB DDR2 RAM
Processor: Intel Pentium 4 2.8GHz HT Enabled
Moniter: Gateway EV700[/B]

---

### Post by treecheetahdolo on 2008-09-04
So far ive isolated the problem.
I'm Able to change the resolution by using
                                     sudo gedit /etc/X11/xorg.conf

As far as the screen lag its only happens when i enable the "ATI accellerated graphics driver" under System>Administration>Hardware Drivers.

My Main concern is the screen lag now.
 Note:When I freshly installed Ubuntu Hardy i didn't have this problem, only when trying to install Video Card Drivers to get My screen resolution Correct.

---

### Post by treecheetahdolo on 2008-09-04
I'm Attempting to Remove xserver-xgl from Synaptic becuase its listed here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) that its not needed for my card.

After Reboot
I uninstalled xserver-xgl and fglrx. And guess what, no lag what so ever. Also now i can set my screen resolution from System>Preferences>Screen Resolution

Only Problem is my Desktop Screen is misaligned with my Moniter. But some tinkering on my moniter settings solves that problem easily. I enabled Visual Effects and it works like a Charm.

**PROBLEM SOLVED!**

---

