---
title: "HP Pavilion dv9000/9700 + amd64 + atheros wireless workaround"
date: 2008-06-10
forum: Hardware
---

### Post by beornharris on 2008-06-10
So after hours (and HOURS) of playing....I have a workaround that consistently seems to work to get my wireless to work!  I hope this helps out the other poor buggers that have struggled with this.

1) Install the ndiswrapper solution as posted in MANY other forums and threads
2) switch the hard switch (front left) to OFF (to the left)
3) open a terminal and run the following:
   $ sudo modprobe -r ndiswrapper
   $ sudo modprobe ndiswrapper
   $ sudo /etc/init.d/networking restart
4) Switch the hard switch ON
5) wait 15-30 seconds
6) ALWAYS use the "connect to other wireless networks" option.  It seems to remember the settings so all is good.  Leave Wireless Interface on Roaming.

Thats it.  Pain in the rear, but it seems to work every time.  Personally, I am opting for ripping out the Atheros mini PCI card, and throwing in an Intel (since it only costs about $40AUD...hope THAT works!) but this seems to have done it for now.  I read a thread somewhere that suggested the module loading order of ndiswrapper might affect it working...maybe some of the wireless boffins can shed some light on why this works.

Note that the wireless light still shows orange (not blue) but everything worked for me.  Hope this helps some of you.


Good luck :o)

---

### Post by beornharris on 2008-06-11
I forgot to note that after waiting 15-30 seconds a password box (keyring) appears.  I am unsure of the significance of this (and maybe the boffins can answer...?) but is this maybe why it isnt active on boot?  an authentication issue?  I am not quite sure what the authentication is for.

---

### Post by beornharris on 2008-06-13
So I got my new intel wireless card.....
I should have done more research (if I had known what to look for!)
It turns out that HP have included a PCI card white list in the BIOS, so that ONLY the (very) small range of cards that HP approve (sell?) will be recognised at all.
My advice: dont buy HP.  I think this behaviour is completely unethical.
There are hacks for the BIOS to either bypass the whitelist check, or to change the IDs of the allowed PCI cards...but you risk bricking your machine...so it looks like I live with the ndiswrapper workaround mentioned here.

---

