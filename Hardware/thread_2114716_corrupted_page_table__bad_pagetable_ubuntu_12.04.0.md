---
title: "corrupted page table / bad pagetable ubuntu 12.04.01 desktop"
date: 2013-02-10
forum: Hardware
---

### Post by drummondislebsd on 2013-02-10
first time ubuntu user, BSD system operator.
 
building up an ubuntu desktop X64 machine. used 12.04.01 LTS X64 version of ubuntu.
 
installed on a freshly "dbaned" 500G hd on an AMD opteron x64 x2, ASUS a8n vm-csm board with 2G of ram. the board has nvidia on board vga, including a dvi output which I've attached to a hd mmonitor.
 
board's bios has a "field" suggesting "some linux programs cannot install with 'on chip' nvidia device (display adapter), which I toggled. Also, worth noting, latest bios for board is installed.
 
FYI... install was smooth. machine operated and upgraded. then the crashes started. FSCK detected nothing. Memtest detected nothing. Now it will not even fully boot to ubuntu.
 
error message displayed as result of booting;
 
corrupted page table at address 7f45a10
PGD (numbers) PUD (numbers) PMD (numbers) PTE (numbers)
bad pagetable 000d [#1] SMP
 
and it continues...
but the "crash" appears to result when software is attempting to "update-apt-xapt"
 
so, i'd like to know if this is a recoverable software issue, a hardware issue, a display issue, a 64bit software issue, or ????
 
i personally suspect the issue is attempting to run the 64 bit software on this older board which has display hardcoded on board? but, that's a less than expert guess.
 
absent direction, i will dban the drive and attempt ubuntu 32bit version. but, it is a shame to let the 64bit dual core's potential go to waste...
 
thanks in advance

---

### Post by drummondislebsd on 2013-02-11
following my hunch, i investigated and downloded a nvidia driver.

i chmod +x the file and executed via ./

the error message is unable to creade a directory /tmp/(nvidia driver).....

it says the file is read only.
 
i am concerned about changing the permission of the directory, should i be concerned?
 
also, there is another folder in /tmp that i suspect is another nvidia driver, that i think is an incorrect driver.

how do i uninstall that?

---

