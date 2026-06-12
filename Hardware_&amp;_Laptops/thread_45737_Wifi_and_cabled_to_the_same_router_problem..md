---
title: "Wifi and cabled to the same router problem."
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by Chivan on 2005-07-01
Ok, I have a problem. Two actually. I've installed my broadcom wifi card with a litle help from the Broadcom HOWTO on this forum. It is functioning perfectly now, WEP and everything. But since i've got my card working I've ran into another problem. My built in network adapter and my wifi card are connected to the same router, so i can't turn them on both at the same time. Now all i want to now is how to make my computer turn off one of the card and the other on when needed. So if the lan cable is disconnected i want the wifi card to come on-line and the other one to come on-line en visa versa. Can anyone help me to accomplish this? 

On to my next problem :). If the wifi card is not active when the computer shuts down the ndiswrapper module won't load at boot, although i ran sudo ndiswrapper -m. “ modprobe config already contains alias directive”. I would appreciate any help you can offer, Thanks.

---

### Post by intangible on 2005-07-01
Did you know about the **System->Administration->Networking** option?  You just change which device to use as your gateway.  

Here's a howto on how to automate the process: [thread]43766[/thread]

---

### Post by Chivan on 2005-07-01
I now of the default gateway option, it is simply not working. When i activate both my wireless an cabled network interfaces networking freezes. So most of the time i just deactivate my wireless card but when i reboot the next problem comes up, the ndiswrapper module isn't loaded. I have reallu no idea how to fix this.

---

### Post by intangible on 2005-07-01
There is a way to make stuff load whenever your interface is brought up by putting a script in **/etc/network/if-up.d/**

This seems to be a point in the right direction: [http://www.linuxforums.org/forum/topic-23329.html](http://www.linuxforums.org/forum/topic-23329.html)

---

