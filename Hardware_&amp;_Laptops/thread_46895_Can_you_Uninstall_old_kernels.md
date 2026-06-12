---
title: "Can you Uninstall old kernels?"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by jc3835 on 2005-07-06
Since I've installed Ubuntu (386), I've added a 686 kernel and two newer 2.6.12 kernels. I've got 4 kernels in total. How can I clean up the 2 or 3 I never use? Some of them don't even work, and I guess those are the ones I'm most interested in uninstalling.
I've searched the forums thinking someone else might have asked, but no luck finding anything.
I KNOW how to comment them out of GRUB, but I want rid of them completely.

Thanks.

JC

---

### Post by varunus on 2005-07-06
If they're ubuntu packages, you can always just uninstall them with synaptic.  If they're custom kernels, I think you can delete the modules and the vmlinuz file.  Make sure you don't delete the wrong kernel, and that the new ones completely work.   :)  I've screwed up a Slackware system by deleting the wrong set of modules...

---

