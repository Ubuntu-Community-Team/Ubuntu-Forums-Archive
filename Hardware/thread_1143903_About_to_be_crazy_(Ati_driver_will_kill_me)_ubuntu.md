---
title: "About to be crazy (Ati driver will kill me) ubuntu 9.04"
date: 2009-04-30
forum: Hardware
---

### Post by dangerman2 on 2009-04-30
[CENTER][FONT=Georgia][SIZE=4][COLOR=Purple]My ati driver about to kill me soon
[/COLOR][/SIZE][/FONT]

[SIZE=4][COLOR=Indigo]the problem is :
when i Download any version of _ati driver 9.4 or 9.3 even 9.2 & 9.1_
& after installation complete
when i type _aticonfig --initial or even aticonfig_
give me this:
_No supported adapter detected_
& after restart my screen stop working & hung

this problem happened with ubuntu 9.04 & 8.10 & suse 11 & mandriva 2009
my card :_ ati x1250 on board_
now iam using _ubuntu 9.04_

Heeeeeeeelp me please
ati will kill me soooooon
](*,):frown:](*,)
[/COLOR][/SIZE][/CENTER]

---

### Post by krazyd on 2009-04-30
Your card is only supported by the open-source driver, not the one you can download from AMD's website.

Are you having issues with the built-in graphics?

---

### Post by StuartN on 2009-04-30
> **dangerman2 said:**
> Heeeeeeeelp me please
ati will kill me soooooon

Try deleting the entire fglrx driver installation and reinstalling the open source ATI driver as described here: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Let us know if it works.

---

### Post by dangerman2 on 2009-05-06
[CENTER][B][I][FONT=Georgia][SIZE=5][COLOR=Purple]it didnt work for me

when i finished setup & install mesa
 i didn't find any thing new in xorg.conf

like wroten in this page
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

any one can help me about the method of install that opensource driver please

reall ati is so boring ........... help please
[/COLOR][/SIZE][/FONT][/I][/B][/CENTER]

---

### Post by crom.osec on 2009-05-06
Hello,

I have installed drivers for ati radeon on my kubuntu 9.04 so I may be able to help you. 

I've noticed that there is a driver for your card at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Check at Linux x86 Integrated/Motherboard

If you need help on installing it, let me know (if I'm still here I'll try to help you).

---

### Post by barretr on 2009-10-05
Try [downgrading]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue") your xserver.

---

