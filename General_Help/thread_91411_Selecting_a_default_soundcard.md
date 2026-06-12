---
title: "Selecting a default soundcard"
date: 2005-11-17
forum: General Help
---

### Post by ksenos on 2005-11-17
As this is my first post on ubuntu forums, I greet everyone in the ubuntu community.

Got some issues with my two sound card, an ATI IXP onboard and a pci SBLive. The ATI IXP is selected as the default sound card although I'd like to SBLive to be it. Although I have selected from the gnome utility in Preferences that the SBLive should be the default some minor stuff do not work correclty. For example, the sound control keyboard shortcuts seem to control the ATI IXP. 

Perhaps it is really easy to fix, but I'd like to know what ways there are to select what card will be the default. I am thinking that if I load the module for the SBLive first (by writing the module name in the /etc/modules file) it will be selected as card 0. Any other ideas? Thanks a lot :D.

Kostas

-------------EDITED--------------

So putting the module of the SBLive in the /etc/modules file, did what I wanted. Now the SBLive is Card 0 and the ATI IXP is Card 1. Cheers :D

---

