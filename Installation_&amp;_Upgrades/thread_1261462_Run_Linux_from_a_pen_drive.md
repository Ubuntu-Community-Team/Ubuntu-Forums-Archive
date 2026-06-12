---
title: "Run Linux from a pen drive"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by n4th4n on 2009-09-08
ive been using linux for a good few months now, and i went from ubuntu to linux mint in the last few days. I want to be able to run linux mint 7 from a pen drive. ive seen a tutorial on how to make a USB live linux from Windows(WIndows can burn in hell) but i want to be able to make a pen drive linux FROM linux. can anyone help? If so, thanks in advance. :)

---

### Post by ElSlunko on 2009-09-08
You can use Unetbootin to create the bootable installation for Ubuntu and many other distros :

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'm not too sure if I understood your intent 100%. Do you wish to install from a pen to another pen? Or the same pen? Or install to a regular HDD?

---

### Post by n4th4n on 2009-09-08
> **ElSlunko said:**
> You can use Unetbootin to create the bootable installation for Ubuntu and many other distros :

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'm not too sure if I understood your intent 100%. Do you wish to install from a pen to another pen? Or the same pen? Or install to a regular HDD?


i wish it for it to be a portable desktop i can take on my flash drive

---

### Post by ElSlunko on 2009-09-08
Then you have 2 options. Well 3, but I think the last one may not work since I haven't done it myself.

You can burn the ISO of the distro you want, restart your PC loading the Live CD, and when you choose what drive to install to choose the USB stick! Easy as that.

If you have 2 pens, you can use unetbootin on 1 to create the installer and use the 2nd pen to install TO when choosing the destination drive.

Finally, if you only have 1 pen and don't wish to burn a CD, I believe you can make 2 partitions on your pen drive & direct unetbootin to 1 of the partitions and install to the 2nd partition. However, I dont know if A.) That will work, and B.) If it will have boot loading issues. I suppose you could delete the installation partition and expand the Operating System partition and it may work.

---

### Post by n4th4n on 2009-09-08
> **ElSlunko said:**
> Then you have 2 options. Well 3, but I think the last one may not work since I haven't done it myself.

You can burn the ISO of the distro you want, restart your PC loading the Live CD, and when you choose what drive to install to choose the USB stick! Easy as that.

If you have 2 pens, you can use unetbootin on 1 to create the installer and use the 2nd pen to install TO when choosing the destination drive.

Finally, if you only have 1 pen and don't wish to burn a CD, I believe you can make 2 partitions on your pen drive & direct unetbootin to 1 of the partitions and install to the 2nd partition. However, I dont know if A.) That will work, and B.) If it will have boot loading issues. I suppose you could delete the installation partition and expand the Operating System partition and it may work.


thanks, it seems so obvious now haha

thanks muchly

---

### Post by ElSlunko on 2009-09-08
No problem! Be sure to come back and let us know what method you used and how it worked out.

---

