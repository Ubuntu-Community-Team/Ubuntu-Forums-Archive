---
title: "xircom PCMCIA card &amp; ZyDAS Zd1211b wireless usb problems"
date: 2006-08-19
forum: Hardware &amp; Laptops
---

### Post by Marc Higgins on 2006-08-19
I am having trouble getting networking on my old laptop.

It is a 150mhz mmx with 64mg ram (Samsung S600) running stock standard xubuntu 6.06, kernel 2.6.15-26-386

There are 2 ways we should be able to connect to the internet on this machine but neither are working for me at the moment

Unicorn USB WL54G wireless adapter (Chipset is ZyDAS Zd1211b) this is the preferred method but as a back up plan I have some Xircom PS-CEM-28 combo 10BaseT Ethernet 28.8kbs/33.6kbs fax modem PCMCIA cards that i have had working in the past on this machine.

Unicorn USB WL54G wireless adapter
(Chipset is ZyDAS Zd1211b)

lsusb shows

Bus 001 Device 005: ID 0ace:1215 ZyDas
Bus 001 Devide 001: IS 0000:0000

so it sees it OK

I have done modprobe zd1211 & I can see it in then in lsmod (but this disappears with a reboot)

lsmod |grep zd
zd1211 206624 0
usbcore 130692 3 zd1211,usbhid,uhci_hcd

iwconfig shows

lo no wireless extensions

there is nothing obvious in dmsg

At this point i found this thread & though woo hoo!

[http://www.ubuntuforums.org/showthre...ghlight=Zd1211](http://www.ubuntuforums.org/showthre...ghlight=Zd1211)

sudo modprobe -r zd1211
sudo apt-get remove wpasupplicant

sudo apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev wireless-tools libssl-dev

& things start to come unstuck form me on this howto here;

we don't have a web connection yet so I cant find get the other repositories so there is no kernel-package libncurses5-dev libqt3-mt-dev libssl-dev :-({|= 

unname -r
2.6.15-26-386

sudo apt-get install linux-headers-2.6.15-26 linux-headers-2.6.15-26-386 linux-source-2.6.15

again no network connection means no linux-source

so thats about as far as i can go unless i can get some kind of a web connection & access to the repositories

so I turned to the xirom (the backup plan)

Xircom PS-CEM-28 combo 10BaseT Ethernet 28.8kbs/33.6kbs fax modem PCMCIA card.

This was working beautifully on this laptop under sarge around 1 year ago guessing kernel 2.2, I remember i had to do a modprobe but cant be 100% sure I have the right module

modprobe xirc2ps_cs seems to do nothing

cardctl status shows

Socket0:
5V 16-bit PC Card
funtion 0: [ready]
Socket 1:
no card

So the pcmcia slot sees something.

for good measure I also installed tried modprobe xircom_tulip_cb but this made no difference.

Have a PCMCIA compact flash adapter & when I put that in as well i get

Socket0:
5V 16-bit PC Card
funtion 0: [ready]
Socket 1:
3.3V 16-bit PC Card
funtion 0:[read]

So I am guessing the PCMCIA slot is working fine

Help me please, I am going out of my brain here ](*,)

---

