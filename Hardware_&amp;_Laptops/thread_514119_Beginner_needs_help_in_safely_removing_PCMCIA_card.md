---
title: "Beginner needs help in safely removing PCMCIA card"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by dreaswar on 2007-07-31
hi,

i run ubuntu 7.04 on a laptop (32 bit). i use a wireless adapter a Dlink DWL G 630.

i also have a PCMCIA card USB 2.0 adapter which i use for external DVD writing.

How do i

1)safely switch off my net connection,

2)safely eject the PCMCIA net card and

3)insert the USB adapter.

4)After writing the DVD i want my net card back on and connection enabled.

i dont want to spoil my net connection because i had lot of diffculty wth tis card and had to finally use ndiswrapper to get connection enabled, so i dont want to lose anything by just taking out the card te wrong way.

i read on some post that there is a command called "pccardctl"

how to go about it safely??

i am a new bie.... so any command line.. please be clear and dont assume i know...

thanks...

---

### Post by overdrank on 2007-08-01
> **dreaswar said:**
> hi,

i run ubuntu 7.04 on a laptop (32 bit). i use a wireless adapter a Dlink DWL G 630.

i also have a PCMCIA card USB 2.0 adapter which i use for external DVD writing.

How do i

1)safely switch off my net connection,

2)safely eject the PCMCIA net card and

3)insert the USB adapter.

4)After writing the DVD i want my net card back on and connection enabled.

i dont want to spoil my net connection because i had lot of diffculty wth tis card and had to finally use ndiswrapper to get connection enabled, so i dont want to lose anything by just taking out the card te wrong way.

i read on some post that there is a command called "pccardctl"

how to go about it safely??

i am a new bie.... so any command line.. please be clear and dont assume i know...

thanks...

HI if you have not found a answer to you issues maybe this will help.
If you were to right click on the network icon on the upper task bar and disable your wireless connection this will allow you to safely remove your wireless card.
Then to eject your usb adapter you can just unmount from your desktop or you home folder. Then when you reinsert the wireless card feisty should recognize the  device and connect to the internet. I have a wireless card on one laptop with feisty ndiswrapper and this works fine to eject the card and reconnect to the network. Hope this helps and good luck. :KS

---

