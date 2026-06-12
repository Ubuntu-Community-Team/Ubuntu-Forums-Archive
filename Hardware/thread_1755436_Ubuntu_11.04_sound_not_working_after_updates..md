---
title: "Ubuntu 11.04 sound not working after updates."
date: 2011-05-11
forum: Hardware
---

### Post by spinfx on 2011-05-11
hi there.

i installed ubuntu 11.04 from scratch, formatted the hard drive. all working perfect. installed all software, and still working perfect.

once i did updates, the sound didnt work.

tried this 4 times, with 32 bit and also 64 bit. same result. only once the first set of updates are done, the sound stops working. i am not sure which update causes the problem as there is 135 of them.

if i use grub to load the previous version of linux, sound works again, so i am quiet sure there is a bug somewhere with one or more of the updates.

can anyone help me nut this out ? i am not too technical on ubuntu.

thanks. :popcorn::popcorn:

---

### Post by grahammechanical on 2011-05-11
I have found that sometimes an update will mute the sound. And all I have to do is click the sound icon and work my way through the options making sure nothing has been muted.

Regards.

---

### Post by spinfx on 2011-05-14
hi there.

thanks, but definitely not a mute problem. its almost sounds like a hardware conflict, like in the old days when you had IRQ conflicts in windows etc...

the sounds wants to work, you hear a milisecond of sound, but then stops, some applications will play sound, but very gittery... others will not play at all... 

like i said before this only happens after first update. works perfect if there is no update. 

thanks :)

---

### Post by kostkon on 2011-05-14
Do you have an nvidia sound card. If yes, try configuring your sound again, after applying all the updates.

Select and test all the available profiles and configurations.

---

### Post by spinfx on 2011-06-09
hi everyone.

thanks for trying to help, but none of the solutions worked.

i just updated to kernel 2.6.38.10 and that fixed it. if i go back to 2.6.38.09, the sound does not work. so its obviously something to do with that particular kernel version.

so i guess this is solved, somewhat :)

thanks again :)

---

