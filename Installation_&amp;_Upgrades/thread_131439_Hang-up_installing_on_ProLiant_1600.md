---
title: "Hang-up installing on ProLiant 1600"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by Swad on 2006-02-16
I am attempting to install Ubuntu Breezy 5.10 on an old Compaq ProLiant 1600 we have.  It uses a Compaq Smart Array 221 controller.  It always hangs up at the exact same place every time.  I have tried a couple boot switches (like noacpi) that don't seem to really change anything.  Here is the last bit of information spit out to me before it hangs up:

```
SCSI subsystem initialized
sym0: <875> rev 0x14 at pci 0000:01:09.0 irq 9
sym0: No NVRAM ID 7, Fast-20, SE, parity checking
sym0: SCSI BUS has been reset
SCSI0 : sym-2.2.0
 0:0:0:0: ABORT operation started.
 0:0:0:0: ABORT operation timed-out.
 0:0:0:0: DEVICE RESET operation started.
 0:0:0:0: DEVICE RESET operation timed out.
 0:0:0:0: BUS RESET operation started.
 0:0:0:0: BUS RESET operation timed out.
 0:0:0:0: HOST RESET operation started.
sym0: SCSI BUS has been reset.
```

That last line is where it stops and it goes no further.  I have let it sit for a while to be sure it wasn't doing something.  I've googled all over and searched where I can think of to try and figure out how I can get this thing working, but to no avail so far.

Can anyone offer any help?

---

### Post by paredown on 2006-02-16
I'm another newbie with more questions than answers, but I thought I remembered seeing (when I was banging around with my trial installs, and looking at the partitioning options) the initial install options server and desktop also included the choices of special setups for RAID--or are you past that point already?
I'm new in town, and I'm not finding the board is particularly responsive...
dean

---

### Post by Swad on 2006-02-17
It really doesn't matter which install you do.  It seems to be I am missing some sort of switch, though, when installing.  I've tried several, but none seem to be the ticket.

---

### Post by paredown on 2006-02-19
I was back looking for my posts & saw this. One thought occurred to me this morning--have you used the Adaptec utility  Control-A at boot (or other?)--and tried disabling parity on the card?
Or trying loading all defaults--F6 on my Adaptec from the menu.
I'm also thinking that Ubuntu/Linux may require Int 13 support, & this might not be enabled...
Dean

---

### Post by Swad on 2006-02-20
I don't believe this machien has any Adaptec hardware in it, but I may be mistaken.  I'm fairly sure it's all compaq (compaq smart array) for RAID and SCSI.

---

