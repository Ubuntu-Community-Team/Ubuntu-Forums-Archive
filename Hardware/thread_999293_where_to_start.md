---
title: "where to start?"
date: 2008-12-01
forum: Hardware
---

### Post by curiouscustomer on 2008-12-01
yes. i don't know where to start looking for drivers. linux compatible drivers. presumably, maybe i could search for drivers if i could get an internet connection, but i need Ubuntu to recognize my pcmcia card.

dell inspiron 7000, 312 Mib ram, pentium 2 processor and an 8 gig hard drive. ubuntu 8.1 

thanks if you can point me in the right direction.

---

### Post by sergiom99 on 2008-12-01
post the output of this commands typed in a console shell>
lspci
lsusb

That will tell us your hardware specs and then we could try to help you to find the right drivers if needed.

---

### Post by curiouscustomer on 2008-12-02
sorry where do i type this command?

---

### Post by curiouscustomer on 2008-12-02
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

so is it possible to get a pcmcia card that will work 'out of the box' cause installing WifiDocsDriverNdiswrapper may be beyond my comprehension.

thanks again if you can help.

---

### Post by curiouscustomer on 2008-12-02
do you think i should just install windows 98? i am so confused.

---

### Post by curiouscustomer on 2008-12-02
looks like i will have to pay for support. athough i don't know where to find someone to pay. i installed ndiswrapper, but that was no help. then i have this roswill adapter that claims to have linux drivers on the install cd and their website. clicking on the linux driver folder only leads to more confusion unfortunately. i am going to pull some of my hair out now, i will get back to you later.

---

### Post by sergiom99 on 2008-12-02
please post the output of:
lspcmcia

with your card on, of course.

---

