---
title: "help for buy a new pc"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by tanozfood on 2008-02-23
Hello,
the vendor proposed me piece of hardware and I am looking if there are problems
with linux in general and ubuntu in particular. The offer is to buy a motherboard
with integrated graphic chipset, disabilitate it, and add a separated graphic card:

- motherboard : mb asus m2v-mx se k8m890 k8-am2 ht2000 2DDRII vga + pci e
- svga galaxy nvidia pci-e 8500 gt 256 mb ddr2 128bit hdtv dvi

Now, I think that nvidia cards should not give problems (even if driver is proprietary),
but the motherboard mount a via chipset and I do not know if this configuration can
give me some problem..
Any suggestions? Does anyone have tried something of this two?
Thanks,
               tano

---

### Post by gdzsi on 2008-02-23
i don't think i'd buy a motherboard with integrated video card and then not use it...
i think it should work though, even K8M890 has a linux driver, but as far as i know it has no 3D support.

you shouldn't worry about nvidia cards.

---

### Post by Yellow Pasque on 2008-02-23
I would avoid VIA chipsets if possible. They have poor drivers and the VT8237A South Bridge is inferior to nVidia's chipsets and even AMD/ATI SB600. Also, VIA's chipset division will soon stop designing mainstream chipsets and focus on VIA's own CPU's/platforms, so don't expect a dedicated effort on providing good, updated drivers.

---

