---
title: "toshiba sound"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by c_walkin on 2005-04-23
hey there,
after trying different things to get sound on my laptop to F*^$ing work ive hit a wall....
somebody please tell me how to configure my sound on this thing,,

ps using kubuntu

toshiba satellite a60
ati raedon 9000
intel 3.06ghz
 ](*,)

---

### Post by az on 2005-04-23
What does lspci tell you?
I know that some audigy2 sond cards need a newer alsa driver to work.  If this is the case you should add to the existing bug report.

If this is not the case, did the sound work in another distribution?  

Either way, this needs to be reported as a bug, since sound should always work out of the box.  That is, unless you did something wierd or obvious...

If you cannot find an obvious solution from another user on this thead, end it by posting your bug report link.

---

### Post by crazybill on 2005-04-24
Hmm. I as going to convert my Toshiba Satellite to Ubuntu ... but maybe I will work to see how this turns out.

---

### Post by punkinside on 2005-05-01
I got my sound working on an A70 with the instructions here: 

[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsToshiba](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsToshiba)

its pretty easy, and sometimes the sounds kinda overlap each other but now I can listen to some music which was all I wanted! Lets hope that they fix this with Breezy lots of folks with toshiba laptops have been complaining about sound.

---

### Post by lucus on 2005-05-01
i am one of those toshiba complainers  so i salute your efforts!!!
mine was an old toshiba tecra
i did modprobe to fix it.

modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530

you might try something similar... yours (i'd imagine) isn't the opl3sa2 card... but give this little piece a try with the right info inserted and cross your fingers!

---

