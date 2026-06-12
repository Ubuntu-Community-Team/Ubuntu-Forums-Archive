---
title: "Plantronics USB device"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by JACIE on 2005-04-22
Hi, reasonably new to Linux/Ubuntu.

I used Skype on Win XP with a Plantronics USB Headset. Since installing Ubuntu this has not worked. It is recognised as a USB device, but there is no audio and the mic is not working.

I have used the Volume Control applet to enable both and to raise the volumes but no improvement.

This isn't very much to go on I know, but any help would be appreciated.

JCIE

---

### Post by magicfab on 2005-04-22
A quick search on Google returned some possible solutions:

[http://ubuntuforums.org/archive/index.php/t-21576.html](http://ubuntuforums.org/archive/index.php/t-21576.html)
[http://www.wombatnation.com/2004/06/skype-on-linux](http://www.wombatnation.com/2004/06/skype-on-linux) (check the comments section)

---

### Post by JACIE on 2005-04-23
[QUOTE=magicfab]A quick search on Google returned some possible solutions:

[http://ubuntuforums.org/archive/index.php/t-21576.html](http://ubuntuforums.org/archive/index.php/t-21576.html)
[http://www.wombatnation.com/2004/06/skype-on-linux](http://www.wombatnation.com/2004/06/skype-on-linux) (check the comments section)[/QUOTE]
 Magicfab,

many thanks for this. I had come across the first page already, however for some reason I have no /etc/modules.conf. The install is a new install of Hoary.

Any ideas why this would be?

Best,

JC

---

### Post by JACIE on 2005-04-24
Finally figured this out, took me a while...

It is fairly basic. Within Skype and xmms there are options for choosing the output device (sound card).

Skype:  File/Options, Hand/Headset. In my case choose /dev/dsp1 as an audio device.

xmms: Ctrl-P, Audio I/O Plugins tab, Output Plugin section, choose ALSA 1.x.x, click configure, choose the relevant audio device (hw:1,0 for me).

Can't find the setting for Rythmbox, but maybe a command line switch.

Anyway, hope this helps someone.

JC

---

