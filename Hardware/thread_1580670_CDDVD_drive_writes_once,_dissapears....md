---
title: "CD/DVD drive writes once, dissapears..."
date: 2010-09-23
forum: Hardware
---

### Post by masam on 2010-09-23
so, i have recently (reinstalled) my Ubuntu box from 9.10 to 10.04(fresh install)
i have noticed that as long as it was freshly rebooted, i can burn a dvd/cdr.
however, after time passes, i cant access it(the eject button doesnt work; Places doesnt display it; it shows up in "computer", but cant do anything with it)

my dmesg is showing this error, and i dont know if it is hardware or software based:

```
[ 2150.988041] ata2.00: qc timeout (cmd 0xa0)
[ 2150.988056] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2150.988064] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 2150.988079] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 2150.988081]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2150.988085] ata2.00: status: { DRDY ERR }
[ 2150.988110] ata2: soft resetting link
[ 2151.168262] ata2.00: configured for UDMA/66
[ 2154.699993] ata2: EH complete
[ 2176.944072] ata2.00: qc timeout (cmd 0xa0)
[ 2176.944091] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2176.944101] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 2176.944122] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 2176.944125]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2176.944131] ata2.00: status: { DRDY ERR }
[ 2176.944166] ata2: soft resetting link
[ 2177.124296] ata2.00: configured for UDMA/66
[ 2177.401533] ata2: EH complete
[ 2187.813043] ata2.00: qc timeout (cmd 0xa0)
[ 2187.813058] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2187.813065] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 2187.813080] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 2187.813082]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2187.813086] ata2.00: status: { DRDY ERR }
[ 2187.813112] ata2: soft resetting link
[ 2192.968059] ata2.00: qc timeout (cmd 0xa1)
[ 2192.968074] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 2192.968081] ata2.00: revalidation failed (errno=-5)
[ 2198.008032] ata2: link is slow to respond, please be patient (ready=0)
[ 2202.992032] ata2: device not ready (errno=-16), forcing hardreset
[ 2202.992045] ata2: soft resetting link
[ 2208.193050] ata2: link is slow to respond, please be patient (ready=0)
[ 2213.012028] ata2: SRST failed (errno=-16)
[ 2213.012042] ata2: soft resetting link
[ 2218.208044] ata2: link is slow to respond, please be patient (ready=0)
[ 2223.028032] ata2: SRST failed (errno=-16)
[ 2223.028047] ata2: soft resetting link
[ 2228.224030] ata2: link is slow to respond, please be patient (ready=0)
[ 2258.032025] ata2: SRST failed (errno=-16)
[ 2258.032040] ata2: soft resetting link
[ 2263.068036] ata2: SRST failed (errno=-16)
[ 2263.068044] ata2: reset failed, giving up
[ 2263.068049] ata2.00: disabled
[ 2268.120029] ata2: link is slow to respond, please be patient (ready=0)
[ 2273.112062] ata2: device not ready (errno=-16), forcing hardreset
[ 2273.112079] ata2: soft resetting link
[ 2278.312053] ata2: link is slow to respond, please be patient (ready=0)
[ 2283.128044] ata2: SRST failed (errno=-16)
[ 2283.128057] ata2: soft resetting link
[ 2288.328026] ata2: link is slow to respond, please be patient (ready=0)
[ 2293.148031] ata2: SRST failed (errno=-16)
[ 2293.148045] ata2: soft resetting link
[ 2298.348037] ata2: link is slow to respond, please be patient (ready=0)
[ 2328.176043] ata2: SRST failed (errno=-16)
[ 2328.176059] ata2: soft resetting link
[ 2333.208048] ata2: SRST failed (errno=-16)
[ 2333.208056] ata2: reset failed, giving up
[ 2333.208079] ata2: EH complete
```

like i said, i am able to burn a DVD/CDR as long as it is a fresh boot.
any thoughts on this one?

---

### Post by kdjohn on 2010-09-23
I am having the same issue.  I also have a couple of hard drives in the system and the main drive stays working but the second drive becomes locked just like the cd/dvd drive.  Shows up in the directory but can't access any files on the second drive.  Happens after the system has been sitting for a while and seems to be random.  Did not have any problems with 9.10.  Only showed up with the upgrade to 10.04.  Did a fresh install twice and still have the same problem.

---

### Post by kdjohn on 2010-09-28
I solved my issue.  The drives were IDE and the manufaturer of my computer had strapped both drives as master.  Set one to master and one to slave and all is well.  Been running stable for 3 1/2 days now.

---

### Post by alan145 on 2010-09-28
I have such same problem before, at the end, I have to install a new CD drive

---

