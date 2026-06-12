---
title: "power management"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by nwadams on 2007-05-07
what program is the best for power management on a laptop?

thanks

---

### Post by DagMan on 2007-05-07
It depends if the laptop is old or newerish and you also need to be sure that there is kernel support for your laptop.  On Ubuntu, and generally speaking, the default programs that get installed are the best for handling things if there's support for it.  There needs to be kernel support for changing the speed of the processor for example, before a program handling it is worthwhile.

It's a specific question you're asking though.  It'd be better if you made a thread, or looked for an existing one, that relates to the laptop in question keeping in mind though that one of the same model might have a core duo in one case and a pentium m in another or one may have  nvidia graphics while another has intel integrated.  The processor throttling is the only thing that sticks out as needing to think about with power management but I might be wrong.

---

### Post by nwadams on 2007-05-07
thanks, ya my toshiba sattelite A100 supports cpu throttling, i was looking for one that handeled that as well as screen brightness

---

### Post by DagMan on 2007-05-15
I have a satellite a100 and I was able to get the brightness working by applying a bios update from their website.  You'de have to be very sure you got the one for your a100 though as there's more than one type and it would still be no garuntee to work in your particular case.  
It was a pain to apply for me because I had to move data to make room for a windows install to run the update.  I had to also update windows first.
It doesn't run great whatsover from the fn keys and I used xbindkeys and xbindkeys-config along with a script I gave root priveleges in the sudoers file.

---

