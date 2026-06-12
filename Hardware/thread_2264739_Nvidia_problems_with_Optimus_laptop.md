---
title: "Nvidia problems with Optimus laptop"
date: 2015-02-09
forum: Hardware
---

### Post by pcolbeck on 2015-02-09
Hi

I have an IBM W540 laptop with Nvidia Optimus garphics.
I have done a fesh install of 14.10 and updated everything. With nouveau drivers it works fine. If however I use the Nvidia binary drivers it doesnt, Unity wont load and I just get a blank desktop, cant even right click.

I did

sudo apt-get install nvidia-331 nvidia-settings nvidia-prime

Then rebooted.

/usr/lib/nux/unity_support_test -p

reports that GLX is miisng and not available on the system.

Any ideas ?

Thanks

---

### Post by pcolbeck on 2015-02-09
Just found the problem.

To get a visible desktop during installaton I had selected "nomodeset" and teh installation had added that to teh boot options as well.
Removed nomodeset from grub and it all works fine now.

---

