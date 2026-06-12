---
title: "Command lshw gave half memory-size."
date: 2017-12-05
forum: Hardware
---

### Post by Azyx on 2017-12-05
sudo lshw gave this info about memory. Total 5966MiB are correkt but the slots have double so big DDR2-DIMM modules.

```
*-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: [COLOR=#ff0000]5966MiB[/COLOR]
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: C&#65533;
             size: [COLOR=#ff0000]512MiB[/COLOR]
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: C&#65533;
             size: [COLOR=#ff0000]1GiB[/COLOR]
             width: 64 bits
        *-bank:2
             description: DIMM Synchronous
             physical id: 2
             slot: C&#65533;
             size: [COLOR=#ff0000]512MiB[/COLOR]
             width: 64 bits
        *-bank:3
             description: DIMM Synchronous
             physical id: 3
             slot: C&#65533;
             size: [COLOR=#ff0000]1GiB[/COLOR]
             width: 64 bits
     *-pci
```

/Cheers

---

### Post by ajgreeny on 2017-12-05
What does the command ***free -mw*** show as output?

---

### Post by Azyx on 2017-12-05
Same as installed 5966, hw also gave that as summary of memory.
-------------------------------------
sudo free -mw
[sudo] password for a: 
              total        used        free      shared     buffers       cache   available
Mem:           5966        2436        2105         164         222        1201        3082
Swap:          3904           0        3904
Azyx@Datorn:~$ 
___________________________

---

### Post by ajgreeny on 2017-12-05
You do not need to use sudo for that free command, but should run it as your normal user, though I think the output would be the same.

---

### Post by Azyx on 2017-12-05
Yes it get the same results.

lshw as a user, don't get DIMM-slots just total memory.

Very strange. I have also tested hwinfo and inxi whith same results as lshw

---

### Post by Yellow Pasque on 2017-12-05
Does dmidecode give the same results?
```
sudo dmidecode -t memory
```

What system or motherboard do you have?

---

### Post by tripp98 on 2017-12-24
What does it say in bios?

---

