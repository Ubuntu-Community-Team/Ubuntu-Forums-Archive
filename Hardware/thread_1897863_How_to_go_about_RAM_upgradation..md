---
title: "How to go about RAM upgradation."
date: 2011-12-20
forum: Hardware
---

### Post by anur.bhargav on 2011-12-20
I'm thinking of upgrading the memory of my desktop (presently 2*1.0GB to 4.0GB).
One, Is there a command or anything to know the Speed,Technology of my memory so that I can buy one with the same specs.

Two, Also recommend the best way to go about the upgrade. 

1. Can I add a 2GB of same Technology and Speed along with the existing 2*1.0GB. If so I will have to install it in DIMM_3 Connector.

2. Shouldn't memory modules always be in 'matched pairs'. Is it ok to go ahead with Option 1.

3. Should I remove the 2*1.0GB of RAM I have and buy a single 4GB RAM.
(This may be a little difficult as 4GB DDR2 RAM's are not easily available)

---

### Post by BC59 on 2011-12-20
All these questions are answered on your manufacturers website. Or at least if you google using as reference the specifications of your computer, you will find the limits and the suggestions of the upgrade you want to do.

---

### Post by prshah on 2011-12-20
> **anur.bhargav said:**
> I'm thinking of upgrading the memory of my desktop (presently 2*1.0GB to 4.0GB).
One, Is there a command or anything to know the Speed,Technology of my memory so that I can buy one with the same specs.

Two, Also recommend the best way to go about the upgrade. 

1. Can I add a 2GB of same Technology and Speed along with the existing 2*1.0GB. If so I will have to install it in DIMM_3 Connector.

2. Shouldn't memory modules always be in 'matched pairs'. Is it ok to go ahead with Option 1.

3. Should I remove the 2*1.0GB of RAM I have and buy a single 4GB RAM.
(This may be a little difficult as 4GB DDR2 RAM's are not easily available)

You can use the memtest86+ option from a live CD to find the details about your RAM. A less readable, but more comprehensive option is to give the below command in the Terminal (Applications-Accessories-Terminal):
```

sudo lshw -C memory
```

(Without sudo, the information is very limited).

Upgrading is a simple process; shutdown cleanly (no hibernation), then open up the system, and replace (or add) your new RAM. Reboot, but avoid loading your OS immediately. Instead, enter the BIOS, and verify the new RAM is correct. Then, boot to a live CD, and run a memtest cycle for about 3-6 hours. If nothing shows up in red, then you are good to boot into your OS. The OS should automatically find and use the new memory without any action required on your part.

The reason for memtest is that if there is any error in the memory or installation, it will be detected in the memtest. There is a small chance of corruption if the OS is loaded with faulty memory.

The latest Ubuntu 32 bit has PAE available automatically when required, otherwise 32bit OS's cannot see/use memory over 3.2GB. if you have a 64 bit OS (recommended) then you need to take no further action.

You can use the terminal command```
free -h
``` to check if your new memory is recognized by the OS.

It is not absolutely required to "match pairs" with DDR2 memory; however, matching pairs will allow supported motherboards to use "Dual Channel" memory access, which adds a small boost (8-10%) ONLY to the memory subsystem access speeds.

Some motherboards don't support Dual Channel at all, some allow mixed Dual Channel, but the majority have automatic switching to Dual Channel when possible (eg when using matched pairs). You can check if Dual Channel is active in the BIOS, memtest, or by checking the lshw output as before.

If your motherboard has more than two DIMM slots, then you have to install the memory in particular physical locations for Dual Channel access. Please consult your manual for information on this.

Your system can switch transparently between Dual Channel and Single Channel at anytime, without any effect on the installed OS (except maybe a negligible loss in speed).

I personally suggest that you use 2 x 2GB; 
a) you get the Dual Channel advantage.
b) If something goes wrong with one memory module in the future, you can continue to use the system on the proper one while the second one is being replaced under warranty/RMA.

While more RAM are Dual Channel capable (when supported by the motherboard), I suggest you consider only premium modules such as Kingston or Corsair (highly recommended).

---

### Post by anur.bhargav on 2011-12-20
> **prshah said:**
> You can use the memtest86+ option from a live CD to find the details about your RAM. A less readable, but more comprehensive option is to give the below command in the Terminal (Applications-Accessories-Terminal):
```

sudo lshw -C memory
```

(Without sudo, the information is very limited).

Upgrading is a simple process; shutdown cleanly (no hibernation), then open up the system, and replace (or add) your new RAM. Reboot, but avoid loading your OS immediately. Instead, enter the BIOS, and verify the new RAM is correct. Then, boot to a live CD, and run a memtest cycle for about 3-6 hours. If nothing shows up in red, then you are good to boot into your OS. The OS should automatically find and use the new memory without any action required on your part.

The reason for memtest is that if there is any error in the memory or installation, it will be detected in the memtest. There is a small chance of corruption if the OS is loaded with faulty memory.

The latest Ubuntu 32 bit has PAE available automatically when required, otherwise 32bit OS's cannot see/use memory over 3.2GB. if you have a 64 bit OS (recommended) then you need to take no further action.

You can use the terminal command```
free -h
``` to check if your new memory is recognized by the OS.

It is not absolutely required to "match pairs" with DDR2 memory; however, matching pairs will allow supported motherboards to use "Dual Channel" memory access, which adds a small boost (8-10%) ONLY to the memory subsystem access speeds.

Some motherboards don't support Dual Channel at all, some allow mixed Dual Channel, but the majority have automatic switching to Dual Channel when possible (eg when using matched pairs). You can check if Dual Channel is active in the BIOS, memtest, or by checking the lshw output as before.

If your motherboard has more than two DIMM slots, then you have to install the memory in particular physical locations for Dual Channel access. Please consult your manual for information on this.

Your system can switch transparently between Dual Channel and Single Channel at anytime, without any effect on the installed OS (except maybe a negligible loss in speed).

I personally suggest that you use 2 x 2GB; 
a) you get the Dual Channel advantage.
b) If something goes wrong with one memory module in the future, you can retain the proper one while the second one is being replaced under warranty/RMA.

While more RAM are Dual Channel capable (when supported by the motherboard), I suggest you consider only premium modules such as Kingston or Corsair (highly recommended).

This is very good information.. Thank you :)

---

### Post by prshah on 2011-12-22
Illustrative result of a small experiment performed in the past. 3 runs with single / dual channel, all hardware remains same.

Dual Channel RAM performance difference: Approx 8% 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209566&stc=1&d=1324579331[/IMG]

---

### Post by gordintoronto on 2011-12-22
Do you need more memory? If you open a Terminal and enter the command top, it will show how much memory is free, and whether your swap partition is being used. If your swap is never used, you don't need more memory.

---

### Post by anur.bhargav on 2012-05-07
> **prshah said:**
> Illustrative result of a small experiment performed in the past. 3 runs with single / dual channel, all hardware remains same.

Dual Channel RAM performance difference: Approx 8% 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209566&stc=1&d=1324579331[/IMG]

Thank you very much for such good information.

---

### Post by anur.bhargav on 2012-05-07
> **gordintoronto said:**
> Do you need more memory? If you open a Terminal and enter the command top, it will show how much memory is free, and whether your swap partition is being used. If your swap is never used, you don't need more memory.

Yes.. Very little swap is used.

---

