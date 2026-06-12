---
title: "kernel vga=0x31a doesn't work anymore in ibex"
date: 2008-12-01
forum: Hardware
---

### Post by PoolSnoopy on 2008-12-01
after upgrading to ibex the kernel parameter vga=0x31a doesn't work anymore. when booting the kernel says that the mode is not supported and that I can scan for valid codes or press space and so on.
what changed since hardy concerning the framebuffer console?
graphics card is a nvidia geforce fx Go5600 with 128MB RAM. but it worked before dating back to dapper.

thanx a lot in advance for any help

---

### Post by PoolSnoopy on 2008-12-02
it seems that this could be a nvidia only problem: I tried the same thing in a vmware and it worked like it always did: perfect.
anyone else with a nvidia card who could try to change the resolution of the text console with vga=0x0317 or whatever suits you?

---

