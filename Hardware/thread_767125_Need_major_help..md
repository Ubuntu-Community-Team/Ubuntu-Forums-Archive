---
title: "Need major help."
date: 2008-04-25
forum: Hardware
---

### Post by Linux Loser on 2008-04-25
Ok well right after the GRUB menu comes up and counts down from 3 this pops up.

> Starting up...
[13.187548] ACPI: EC: acpi_ec_wait timeout, status=0, expect_event=1
[13.187600] ACPI: EC: read timeout, command=128

I completely formatted my hard drive and did a clean install of ubuntu and it still pops up.

The only way for me to load up my computer is to press esc during the grub menu countdown and load recovery mode> normal boot.

Please help if you can.

---

### Post by Linux Loser on 2008-04-25
:(

---

### Post by SnakeHips on 2008-04-25
I cant help you specifically but YOU can help others to help you more by including the following

what hardware are you running- laptop/desktop?

what version of ubuntu? 32bit/64bit?

livecd / alternate ?

anyhow ,to get the ball rolling ,when you boot in "recovery mode" does it load and work correctly ?

---

### Post by SnakeHips on 2008-04-25
From my limited knowledge of such things it does'nt sound like you have any hardware probs......more likely a software config error. i think ACPI is connected with power/saving and hibernating and *if* this is the point [Quote Starting up....] when booting ,that it "hangs" ,then boot is just waiting around to be told it's ok to continue...
Maybe it's making a call on a driver or awaiting a correct value to be returned from the hardware.

It might also be a setting in your BIOS needs to be changed......actually the more i think about it.....formatting the disk would only leave the BIOS settings which got picked up when you re-installed?.......could anything have changed the  BIOS settings?

Sorry i cant give you a load of linux stuff to do ,still teaching myself ,hope some of this helps.

---

