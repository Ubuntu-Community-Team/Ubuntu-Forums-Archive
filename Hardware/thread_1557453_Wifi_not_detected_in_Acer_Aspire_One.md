---
title: "Wifi not detected in Acer Aspire One"
date: 2010-08-20
forum: Hardware
---

### Post by ZequeZ on 2010-08-20
Hello,
I installed Ubuntu Netbook to my AAO a couple of days ago, the problem is that I didn't have wifi at the moment, now I'm within a wifi network, but the card just don't work, the led is turned off and there is not switch to turn it on...

Any clue? How can I check the exact wifi card that I have?

Thanks ^^

EDIT: Nevermind about the card model "lspci | grep -i wireles" and it is a "RaLink RT3090", im installing some drivers right now, I'll update the post if them work :P

EDIT2: Didn't work :(

Help?

EDIT3: Please? Pleeeeeeeeeeease? I may die for this :(

EDIT4: Seriously I'm nearly desperate, I've tried ndiswrapper and the driver is not supported... Please help me! Please! I'll even try to compile the kernel if it's necessarie Q.Q

EDIT5: Just give me a handdd I'm lost hereee pleaaaaaaaaaaaaaaseeeeeeeeeeeeeeeeeee.. Pleeeeeeeeeaaaaaaaaaaaaaseeeeeeeeeeeeeeeeeeeeeeeee *Cry*

EDIT6: No one have an Acer Aspire One?

EDIT7: Oh! This is just great, I followed [this guide ]("https://help.ubuntu.com/community/AspireOne/AO751h#Fixing%20Wireless%20Led%20%28AO751h%29")to supposedly fix the wireless led not turning on bug, and now Ubuntu don't even detect the wlan0 when I type ifconfig. Pleaseeeeeeeeeee don't make me thisss Q.Q 

Sorry for my poor english :(


EDIT8: OMFG!!! AFTER 5 HOURS I DID IT!! I DID IT!!!! YEEEEEEEEEEEEESSSSSSSSSSSSSSSSSSSSSS WIFIIIIIIIIIIIIIII xDDDDDDD. Well, really I don't know the time when I fixed it, but I ran "modprobe -l | grep 3090" and I found the driver was there, so I started to try things with modprobe so I finally typed "modprobe rt3090sta" and it worked!!!

BTW: Before that I followed like 500 guides and installed like 500 differents drivers, so I don't really know what did it xDD.

---

### Post by ZequeZ on 2010-08-21
Greaate.. Before the last system update it's broken again, why Ubuntu hate me?

lol it's working again xD. I unloaded ndirwrapper module and loaded the other module and I think was that xD.

---

