---
title: "WoL in intrepid"
date: 2008-11-23
forum: General Help
---

### Post by barkerben on 2008-11-23
Hi,

I am running 8.10, and am having no luck at all getting WoL to work. When using Hardy, there was no problem getting the NIC to stay up at shutdown, but now I am getting nowhere.  Ihave trawled th forums and found various suggestions, but none of them seem to help me in this case. Does anyone have a tried and tested method to enable this functionality?

Cheers,

Ben

---

### Post by ITAndrew on 2008-11-23
WoL is controlled by your systems BIOS and has nothing to do with your OS. Make sure WoL is enabled in your systems BIOS, then attemt to send a magic packet to your system using the <nil> or port 0.

---

### Post by barkerben on 2008-11-23
Thanks - I understand how wol functions. WoL is enabled in the BIOS. However, it is not the case that this is entirely independant of the OS. 

At shutdown it is possible for the OS to override the BIOS settings and, for example, not provide power to the NIC. 

It would appear that this is the case here. As a proof of the above, I can dual boot into windows (though I rarely do). Shutting down from windows leaves the NIC powered, and I am able to WoL.

Ben

---

