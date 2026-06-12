---
title: "&quot;Cannot install 'edubuntu-desktop'"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by out-of-hand on 2009-06-27
hi , i downloaded Ubuntu 9.04 and got it working, did all my necessary updates and then i wanted to test EDUBUNTU.
so i downloaded the ISO , made it a image on a cd , inserted it into my cd rom . Ubuntu sees its a add on m and wants to install the files.

so it opens Add/ Remove prog...

i select Educational desktop for ubuntu. and as i click it m i get this error
:confused:

This application conflicts with other installed software. To install 'edubuntu-desktop' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

im confused at this error , i went on irc chat ,. spoke to someone there , they suggested i report a bug..

can anyone please assist me ?
im fairly new to Linux

many thanks
Out-Of_hand

---

### Post by starcraft.man on 2009-06-27
Odd.

You didn't have to download the ISO btw. The meta-package is available in the default repos. 

Ok, open a terminal (Applications > Accessories > Terminal) and then type in the following and return:

```
sudo aptitude install edubuntu-desktop
```

If it returns the same error, please copy and paste it here and I'll see what the trouble is. On a vanilla install it shouldn't give trouble, doesn't on either of my boxes.

Oh and push q to stop the installation if you don't want to remove the packages.

---

