---
title: "Exturnal Wireless Adapter"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by krs_hasukie on 2008-02-08
I work at best buy so i am going to pick up a wireless Card for my labtop... Witch one will work for the latest version of Xubuntu?
my inturnal one does not work and i am goiing threw hell to get it to work i rather just buy a new one lol
but this one will be exturnal... My laptop is a dv6000 seris of hps and people are everywere talking about how it does not work....
so yea...
exturnal wireless Card witch one sould i get?

---

### Post by neurostu on 2008-02-08
Here is a list [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

of usb cards that are known to work with NDISwrapper.

Hope this helps

---

### Post by nzruss on 2008-02-08
I have an dv6000 also, and managed to get the wireless to work fine. 

type "sudo lshw -C network" into terminal to determine the actual chipset.  Then check out my post here:

[http://ubuntuforums.org/showpost.php?p=4290847&postcount=13]("http://ubuntuforums.org/showpost.php?p=4290847&postcount=13")

---

### Post by krs_hasukie on 2008-02-09
Um like is there somthing that like will work right out of the box i am really retarded when it comes to this stuff... and for the guy who had the dv6000 seris i will try what you did i most likly will fail lol but i will try
Edit:
yea there is not way i just read ndiswrapper That thing is like insane lol i don't know how people use it I don't know how to get it to work O_O;;;
heh 
but yea i would realy like to know if anything will work out the box if not i am proably screwed. I was reading that the spint cards do but than i have to sign up for service heh...

---

### Post by neurostu on 2008-02-09
So NDISWrapper is the linux driver for WIFI, if you goto that list it lists _all_ wifi adapters that work out of the box. Pick two or three usb sticks and look them up on the list and if they are on the list then they will work.

---

### Post by nzruss on 2008-02-11
> **neurostu said:**
> So NDISWrapper is the linux driver for WIFI, if you goto that list it lists _all_ wifi adapters that work out of the box. Pick two or three usb sticks and look them up on the list and if they are on the list then they will work.

Not really. Ndiswrapper is a piece of software that translates the Windows driver to use with Linux. That list provides known windows drivers that work with ndiswrapper.

I'd suggest you check out [this link]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53"): 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Which is a list of supported wireless cards that work 'out of the box' in Ubuntu.

---

