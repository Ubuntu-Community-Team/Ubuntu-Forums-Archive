---
title: "setting up IrDA"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by neoTheCat on 2006-03-18
hello.

i really, really tried lookig this up everywhere, but i can not get my IrDA working.  after i plug it in. dmesg gives me:

[FONT="Courier New"]
[4330315.815000] usb 1-1: USB disconnect, address 4
[4330319.742000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[4330319.861000] SigmaTel STIr4200 IRDA/USB found at address 5, Vendor: 66f, Product: 4200
[4330319.863000] drivers/net/irda/stir4200.c: IrDA: Registered SigmaTel device irda0
[/FONT]

and my  /etc/default/irda-utils:
[FONT="Courier New"]
ENABLE="true"
DISCOVERY="true"
DEVICE="irda0"
DONGLE="none"
SETSERIAL=""
[/FONT]

but when i try to sync my palm pilot via /dev/ircomm0, it got halfway, it got disconnected, and now i can't sync again.  when i do an "irdadump", i get:

[FONT="Courier New"]
16:16:46.943103 xid:cmd ffffffff < 53287dd0 S=6 s=0 (14)
16:16:47.032164 xid:cmd ffffffff < 53287dd0 S=6 s=1 (14)
16:16:47.123345 xid:cmd ffffffff < 53287dd0 S=6 s=2 (14)
16:16:47.123370 xid:rsp 492783da > 53287dd0 S=6 s=2 akira hint=0400 [ Computer ] (21)
16:16:47.272336 xid:cmd ffffffff < 53287dd0 S=6 s=3 (14)
16:16:47.362400 xid:cmd ffffffff < 53287dd0 S=6 s=4 (14)
16:16:47.452465 xid:cmd ffffffff < 53287dd0 S=6 s=5 (14)
16:16:47.551536 xid:cmd ffffffff < 53287dd0 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23)
[/FONT]

it seems like nothing i do gets the connection again, no matter how many times i restart irda-utils, plug unplug the irda device...

any ideas, hints, or anything online i missed reading?

thank you,
-=- neothecat

---

