---
title: "Unstable"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by ben3005 on 2009-08-13
im curently dual booting vista and ubuntu, 
vista is working fine (a rarity i know)
however ubuntu is very unstable, it crashes within five minutes of booting up,
im new to ubuntu so have n idea why
any ideas?

---

### Post by lisati on 2009-08-13
What sort of computer are you running it on? What kind of specs?

---

### Post by ben3005 on 2009-08-13
2 x 120 gb maxtor hard drives
1 gb of RAM 
amd athlon 64processor 3200+ 2.2ghz

---

### Post by ronparent on 2009-08-13
What do you mean by crashing? ie rebooting or freezing?

---

### Post by ben3005 on 2009-08-14
it freezes,  it completely locks up, and becomes unresponsive so i have to reset my pc

---

### Post by ronparent on 2009-08-14
Try booting from the live cd. Hit f6 after the language selection screen and use the spacebar to deselect apic and lapic. Continue to boot on the 1st menu choice - to run wihtout installing. If you can run for any length of time - 1hr or more - without freezing, then the installed system will also with apic and lapic disabled. You can reinstall from the live session and those options will be disabled automatically or you can notate the kernel loading line as admin by adding a noapic,nolapic option to the loading instructions.

---

### Post by ben3005 on 2009-08-15
many thanks for that, ive done what you said and now it seems to be working fine, thanks for the help :KS

---

