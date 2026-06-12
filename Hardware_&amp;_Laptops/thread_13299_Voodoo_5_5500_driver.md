---
title: "Voodoo 5 5500 driver"
date: 2005-01-30
forum: Hardware &amp; Laptops
---

### Post by gizmospc on 2005-01-30
I am looking for a driver for my old 3dfx Voodoo 5 5500 agp card that will accelarate the graphics on Ubuntu.  The card was automatically detacted during installation, however I've noticed that there seems to be no accelaration of 3d graphics.  I've searched far and wide and so far no luck with this issue.  Any help with this would be cool.  :confused:

---

### Post by markuman on 2005-06-30
[QUOTE=gizmospc]I am looking for a driver for my old 3dfx Voodoo 5 5500 agp card that will accelarate the graphics on Ubuntu.  The card was automatically detacted during installation, however I've noticed that there seems to be no accelaration of 3d graphics.  I've searched far and wide and so far no luck with this issue.  Any help with this would be cool.  :confused:[/QUOTE]


hi, nice to meet 3dfx fans ;-)

i got this card to. for the first. SLI don´ t work. Glide developer said the problem is by xorg, but they said, the problem is by Glide....(i try to find the mistake and hope to fix it)
so both chips will do the same and so at the moment the voodoo 5 has not 100% power. with both chips it will be have much more performance.

for installing 3D support for 3Dfx card, just install Glide library

```
apt-get install libglide3
```

now you have to ReLink your librarys with

```
 sudo ldconfig
```

ready. that was all.

Note: check glxgears before installing Glide3 install and after to see the different!


###EDIT###

oh, i see you've find out it alone ... [http://ubuntuforums.org/showthread.php?t=14428&highlight=3dfx](http://ubuntuforums.org/showthread.php?t=14428&highlight=3dfx)

---

