---
title: "Basic info about Suspend2"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by ltmon on 2006-06-05
Hi All,

I'm eagerly awaiting delivery of my new Asus M6VA (aka Z70VA) and have been scouring forums and wikis so I know all the issues I could face when installing Dapper on it's hardware.

I'm pretty happy with most of the information I've gotten, but am still confused about suspend to disk and suspend to RAM.

Can someone answer these basic questions:

- Is suspend2 required to successfully suspend this laptop (ATI x700 video card btw)?
- Is suspend2 compiled into the Dapper kernels by default?
- Will I need to recompile the kernel to get or upgrade suspend2?
- What options do I need to set in xorg.conf to get suspend and resume working correctly?
- Any other hacking around required (e.g. module unloading/loading)?

All the information on this is a bit scattered and confused, and often refers to out of date kernels/distros.  I'm just looking for a basic summary of the state of suspend in Dapper.

TIA,

L.

---

### Post by norman_h on 2006-06-05
Out of the box dapper does not allow acpi to work on my ASUS M6R.  Could be a similar situation to your new lappy.

I had to move two files so that my lappy didn't stall on boot.  The system didn't boot on startup and required a second bootable CD to move the files.

```

sudo mv /etc/rc2.d/S10acpid /etc/rc2.d/S20apmd /etc/

```

---

