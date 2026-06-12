---
title: "Ubuntu + GSensor Device (LIS331DL|)"
date: 2010-03-04
forum: Hardware
---

### Post by luispsc on 2010-03-04
Hi, all.

Lately I've been trying to build a linux driver to an accelerometer chipset, LIS331DL, embedded to a certain motherboard. System's BIOS has not been updated as to fit current gsensors linux drivers in (communities releases and so). We are positive that the device naturally inputs/outputs info through very specific I/O ports, namely the 0x6C and 0x68 ones. The problem is that I am able to access the device data through those ports in windows, but not in linux. Moreover, there's no real datasheet to help us through. 

Here I have some few questions:

1) Is there, by any sort, a software kit which could possibly help us into diagnosing the motherboard as to provide more info about the device (LIS331DL accelerometer chip)?

2) Provided that there's already a windows driver that's fully functional and easily gets to send/retrieve data to/from the gsensor, under Ubuntu, the management of those same I/O would end into same results? In short, is there any difference between Linux and Windows I/O ports access (logical and addressing shifts perhaps)?

Any help would be much appreciated. Thanx in advance.

---

### Post by luispsc on 2010-03-05
I managed to successfully get access to the gsensor device. Hope any other won't face the problems I had to, but just in case, I will now provide feedback to my own questions:

1) Is there, by any sort, a software kit which could possibly help us
into diagnosing the motherboard as to provide more info about the
device (LIS331DL accelerometer chip)?

Yes. A very good one called ECTOOL. Lookie -> [http://www.coreboot.org/Ectool](http://www.coreboot.org/Ectool)

It probes the EC-RAM memory, which's quite a good start on taking notice of how bits are behaving and, later on, making decisions on that! ;)

2) Provided that there's already a windows driver that's fully
functional and easily gets to send/retrieve data to/from the gsensor,
under linux, the management of those same I/O would end into same
results? In short, is there any difference between Linux and Windows I/
O ports access (logical and addressing shifts perhaps)?

Yes, same results. No difference. The gsensor got to output the same values (three-axial coordinates) as in windows. Hurray!

---

### Post by jsampaio57 on 2010-09-07
> **luispsc said:**
> I managed to successfully get access to the gsensor device. Hope any other won't face the problems I had to, but just in case, I will now provide feedback to my own questions:

1) Is there, by any sort, a software kit which could possibly help us
into diagnosing the motherboard as to provide more info about the
device (LIS331DL accelerometer chip)?

Yes. A very good one called ECTOOL. Lookie -> [http://www.coreboot.org/Ectool](http://www.coreboot.org/Ectool)

It probes the EC-RAM memory, which's quite a good start on taking notice of how bits are behaving and, later on, making decisions on that! ;)

2) Provided that there's already a windows driver that's fully
functional and easily gets to send/retrieve data to/from the gsensor,
under linux, the management of those same I/O would end into same
results? In short, is there any difference between Linux and Windows I/
O ports access (logical and addressing shifts perhaps)?

Yes, same results. No difference. The gsensor got to output the same values (three-axial coordinates) as in windows. Hurray!

I have a Toshiba Satellite Pro T110. It has an 3D accelerometer but I was not able to find any website saying the model of chip used in the T110.

I tried the ECTools. It prints several memory contents, but nothing changes as I rerun after tilting the laptop in different directions. These are only the EC-RAM. The EC IDX RAM is not printed with "-i" option. If I force the print I get all "FF"s.

I think that Toshiba uses a different chip, maybe not ACPI.

Anybody knows?
Cheers...

---

