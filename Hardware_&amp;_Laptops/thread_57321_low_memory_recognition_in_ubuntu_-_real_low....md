---
title: "low memory recognition in ubuntu - real low..."
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by recklessray on 2005-08-16
hi, ive got a p42800 with 1 gig of ram installed. in my 'system monitor' program, it confidently tells me i have a grand total of 377.8 megs of ram to play with, of which 160 is used. how can this be when i have 1 gig installed? ive read others have had a problem with only having 8oo or so megs used out of a gig and have had to 'change the kernal' to fix it.. any ideas please - 

many thanks :)

---

### Post by tseliot on 2005-08-16
The default kernel should support up to 900MB RAM, so your problem is a little weird. You can try to install a different kernel optimised for pentiums: open Synaptic (or Kynaptic) and look for linux-image-2.6.10-5-686 and linux-headers-2.6.10-5-686 (just put the word "linux" in the search field) click on them and select "mark for installation" and then press the "Apply" button. DON'T REMOVE your current kernel.

After it has finished close Synaptic and restart your computer.
Your computer will boot using the new kernel whic has a higher memory support. Then verifiy if all your RAM is recognised.

If anthing went wrong (I don't know a reason for which it would) you could switch back to your kernel: while booting your computer and press "ESC" repeatedly until GRUB menu appears and you can choose kernel 2.6.10  for [COLOR=Red]i386[/COLOR] (i.e. your previous kernel) again (using your keyboard arrows). Once you enter Ubuntu open Synaptic and remove the undesired kernel in the same way you installed it (it's a matter of mouse clicks). And reboot.

---

### Post by recklessray on 2005-08-16
hey, thanks for that. im a newbee but it all sounds good to me! ill give that a go and reply with the results.
all the best :)

---

### Post by recklessray on 2005-08-16
hi there, well i installed the new kernal and rebooted. the pc seemed to boot up much more quickly than before. however the memory is still 377.6 in the system monitor... any more thoughts / help most gratefully recieved :)

---

