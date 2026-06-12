---
title: "driver updates"
date: 2008-09-25
forum: Hardware
---

### Post by Doby on 2008-09-25
Hey I need help, how do I update my drivers on ubuntu 8.04.  I have a hp pavilion dv2000.  I really want to know if there is a driver update for my video card, and my network cards.  Any help would be much appriated.

---

### Post by pytheas22 on 2008-09-25
Generally it's not a good idea to update drivers manually; it's better for various reasons to wait for the updates to be pushed out via Ubuntu updates.  If you're having serious problems with your video or wireless devices, however, it's probably worth it to update their drivers manually (video may be tough to do manually, but wireless should be easier)--but don't do it if things are working fine but you feel like you should have the very latest version of everything; in that case you'll probably create more problems for yourself than you'll solve.

Do you know which drivers you're using?  If not, please post the output of:
```

lspci -nn
lsusb
```

---

### Post by Doby on 2008-11-18
Good point.  I really just want my nvidia geforce 6150 driver.  I can't use dual monitors right now, and i don't have restricted drivers either.  I am running hardy for now, but might upgrade to intrepid this weekend and see if the dual monitors will work.  

I have a hp pavilion dv2000 if that helps.

---

### Post by pytheas22 on 2008-11-18
Have you tried configuring dual monitors using the nvidia-settings utility?  To launch it, run:
```

sudo nvidia-settings
```

Otherwise, you may well have better luck with Intrepid, since it will use a more recent version of the nvidia driver.  You could also use envy to install the nvidia drivers, as I think it will install more updated ones than those available in the Ubuntu repositories.  See [this thread]("http://ubuntuforums.org/showthread.php?t=57368") for details (note that some of the information there is outdated; in particular, xorg.conf no longer really matters in Hardy, and not at all in Intrepid).

---

