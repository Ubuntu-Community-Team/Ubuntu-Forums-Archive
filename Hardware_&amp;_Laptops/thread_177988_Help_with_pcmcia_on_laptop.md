---
title: "Help with pcmcia on laptop"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by narcus on 2006-05-17
Hello,
I've been trying for hours now to get my Memory Stick Pro Duo card working and I hope someone will be able to help me out a bit. I'm running Dapper Flight7 now, but have also tried earlier on Breezy (actually thats why I upgraded, hoping for better pcmcia support)

When I stick my card in the slot, I see in syslog:
May 17 15:15:24 localhost kernel: [4296609.658000] pccard: PCMCIA card inserted into slot 0
May 17 15:15:24 localhost kernel: [4296609.658000] pcmcia: registering new device pcmcia0.0

It is also now listed in Device Manager as "Bay2Controller", under "RL5c476 II", under "82801 Mobile PCI Bridge".

"$ pccardctl info" shows me:
PRODID_1="RICOH"
PRODID_2="Bay2Controller"
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=254
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

The relevant line from $ lspci I think is:
0000:02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)

But it's not showing up in /dev (I think as sda1 is common), so I don't know how to mount it from here ](*,) 

Let me know if there's anything else I can do to provide more info.

---

### Post by narcus on 2006-05-22
OK, I guess the answer to my problem just is "your device is not supported" then...

---

### Post by perryjones on 2006-05-24
I am confused because you said " But it's not showing up in /dev (I think as sda1 is common)" That would be a drive label not a pc card label. Is this just a wireless pc card? You can't mount anything but a drive. Look closer at the drivers being used and see if you can find an update or fix for your particular card.

---

### Post by perryjones on 2006-05-24
PS .... You may have to tweak the kernel or the driver a little look for help specific to your card and linux version.

---

### Post by snipe122 on 2006-05-25
](*,)  I think he talks about a memory card adapter (MSD<-> PCMCIA) and not about a WiFi-Card :mrgreen: 

but about the problem I cant tell you anything. I just know that my internal cardreader doesnt work either. Ubuntu (dapper as well) has problems especially with internal card readers. Dont know how it is with pcmcia adapters cause theyre not very common at all... I would suggest to buy a usb-cardreader for € 10, they work great.

greetz
snipe

---

### Post by narcus on 2006-05-26
Hi, thanks for replying. Yeah, it's not a wifi-card, but a Memory Stick Duo (for my Sony Ericsson W810i) into a little adapter card and then in my MS/SD/MMC internal card reader. Well, I guess it was a bit too much to hope for...apart from that Ubuntu works great on my laptop :KS 

Anyway, I've been sniffing around some more for info, and it seems the culprit is the Ricoh RL5c476 II bridge; I read someone saying that it doesn't use the standard interfaces so a proprietary linux driver may be needed, which obviously the producer can't be bothered with. 

Guess I could poke around in the kernel modules, but I'm using this computer for my daily work so I can't risk to much damage. I do manage anyway, as the phone came with a USB cable as well, I just wanted it so badly to work :rolleyes:

---

