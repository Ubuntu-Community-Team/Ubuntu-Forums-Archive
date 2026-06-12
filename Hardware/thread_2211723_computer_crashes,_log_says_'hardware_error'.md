---
title: "computer crashes, log says 'hardware error'"
date: 2014-03-17
forum: Hardware
---

### Post by jaarvidsen on 2014-03-17
in the last week or so my self built machine has started  crashing hard, its happened about 4 times. it was built last summer and  no changes has been made to it or bios since, and its run flawlessly  until about a week ago.

  
 kernel log says:

 ----------
 Mar 17 10:59:36 enceladus kernel: [    6.034574] MCE: In-kernel MCE decoding enabled.
Mar 17 10:59:36 enceladus kernel: [    6.034578] [Hardware Error]: MC1 Error: Microcode Patch Buffer.
Mar 17 10:59:36 enceladus kernel: [    6.034597] [Hardware Error]: Error Status: System Fatal error.
Mar 17 10:59:36 enceladus kernel: [    6.034613] [Hardware Error]: CPU:3  (15:2:0) MC1_STATUS[-|UE|-|PCC|AddrV|-|-]: 0xb600000000100153
Mar 17 10:59:36 enceladus kernel: [    6.034639] [Hardware Error]: MC1_ADDR: 0x0000000000000007
Mar 17 10:59:36 enceladus kernel: [    6.034652] [Hardware Error]: cache level: L3/GEN, tx: INSN, mem-tx: IRD
Mar 17 10:59:36 enceladus kernel: [    6.036330] EDAC MC: Ver: 3.0.0
Mar 17 10:59:36 enceladus kernel: [    6.037553] AMD64 EDAC driver v3.4.0
Mar 17 10:59:36 enceladus kernel: [    6.037575] EDAC amd64: DRAM ECC disabled.
Mar 17 10:59:36 enceladus kernel: [    6.037584] EDAC amd64: ECC  disabled in the BIOS or no ECC capability, module will not load.
 Mar 17 10:59:36 enceladus kernel: [    6.037584]  Either enable ECC  checking or force module loading by setting 'ecc_enable_override'.
 ----------
im not sure if the last 2 lines there are related to the crashes but ECC is enabled and has always been enabled in bios

 

  
 any clues what might be wrong? i mean can ram for example that has worked flawlessly for a year suddenly become faulty?
so far this has not happened in windows and i spend a few hours there daily gaming

  
 my hardware is about like this
 asus sabertooth 990fx motherboard
 amd 8350 8 core cpu (4.5 ghz  overclock, does never go above 50 C  even under stress tests - the problem is deffo not cpu overheating - it  would have been at around 30C for each crash)
 16 gb corsair ram of some sort
nvidia gtx670

 64 bit kubuntu 13.10/win7 64bit dual boot

---

### Post by ajgreeny on 2014-03-17
What graphic card, or do you use the cpu graphics chip.

References I have seen to ECC seem to be related to graphics chips most often, but I admit I know little of this.

---

### Post by jaarvidsen on 2014-03-17
im using a gigabyte nvidia gtx 670

---

### Post by Yellow Pasque on 2014-03-18
Don't worry about the EDAC/ECC messages (unless you actually have ECC RAM). They're common on modern kernels and I even have them in my dmesg...

> any clues what might be wrong? i mean can ram for example that has worked flawlessly for a year suddenly become faulty?
Yes, RAM goes faulty, and depending on how the OS manages it, you may only be hitting the bad part with Linux. I've seen some reports of that on these forums before (and it's probably more likely with a large amount of RAM). So run memtest to rule that out.

This looks suspicious...
```
Mar 17 10:59:36 enceladus kernel: [ 6.034578] [Hardware Error]: MC1 Error: Microcode Patch Buffer.
Mar 17 10:59:36 enceladus kernel: [ 6.034597] [Hardware Error]: Error Status: System Fatal error.
Mar 17 10:59:36 enceladus kernel: [ 6.034613] [Hardware Error]: CPU:3 (15:2:0) MC1_STATUS[-|UE|-|PCC|AddrV|-|-]: 0xb600000000100153
Mar 17 10:59:36 enceladus kernel: [ 6.034639] [Hardware Error]: MC1_ADDR: 0x0000000000000007
Mar 17 10:59:36 enceladus kernel: [ 6.034652] [Hardware Error]: cache level: L3/GEN, tx: INSN, mem-tx: IRD
```

I would try booting into an older kernel if you have one installed. Also, I'm wondering if you have amd64-microcode package installed?

---

### Post by jaarvidsen on 2014-03-18
thanks for reply
no i dont have amd64-microcode installed
not sure what u mean by actual ecc ram, anyway ecc is enabled in bios and my dmesg says its not
[    6.185048] EDAC amd64: DRAM ECC disabled.
[    6.185057] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    6.185057]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.

it might well be that this started happening after a recent kernel update, ill see if i can boot into an older one

---

### Post by Yellow Pasque on 2014-03-18
The RAM itself needs to support ECC (not just BIOS). If you don't know what ECC RAM is, then you probably don't have it.. [http://en.wikipedia.org/wiki/ECC_memory](http://en.wikipedia.org/wiki/ECC_memory)

---

### Post by jaarvidsen on 2014-03-18
seems you're right, i found my mem sticks online and it says non-ecc. i guess that means i can disable ecc in bios ?
currently running an older kernel 3.11.0-17 - might take days to see if any crashes occur though

---

### Post by Yellow Pasque on 2014-03-18
Run memtest.

---

### Post by jaarvidsen on 2014-03-18
ok, i dont have thte opportunity now to run memtest properly over a longer period, i just briefly ran it for some minutes, no errors found, but what i found strange that it said that it was ddr2 320 mhz 1-3-3-3 memory while it really is ddr3 1600mhz 1-9-9-9 (the latter being from memory might be wrong) - says both in bios and on POST or is that just memtest testing the ram in different modes? or is that even possible. this was running the built in memtest that appears in grub

sudo dmidecode --type 17 confirms ddr3/1600

---

### Post by jaarvidsen on 2014-03-18
great now i had a crash in windows too, screen went completely white, machine still runs but completely unresponsive, had to do a hard reboot, went back looked in some logs but the only think i found was something about unexpected shutdown which i guess was me pressing the reset button. hard to say if this is related or just a 'normal' windows crash

---

### Post by jaarvidsen on 2014-03-18
ok, seems the white screen crash in windows is common with the newest nvidia drivers, i dont think its related, it didnt feel the same way, the linux crash is like one sec im doing smt the next im at POST. the windows one didnt reboot, it just lingered

also ran memtest for an hour and a half, and reached 100% - i guess that means i ran the whole test once? anyway, no errors found. 

no crashes with the old kernel that ive been running half the day yet either, but too early to tell

---

### Post by jaarvidsen on 2014-03-25
well a week on an older kernel now (3.11.0-17 instead of 3.11.0-18) has resulted in zero crashes so i guess it must have been a kernel problem...knowing my luck though it will crash just after i hit the post button

---

