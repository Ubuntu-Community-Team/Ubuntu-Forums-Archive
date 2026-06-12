---
title: "Laptop hardware: What to upgrade?"
date: 2010-03-06
forum: Hardware
---

### Post by OzVegan on 2010-03-06
I upgraded my wife's laptop from a crappily running openSUSE 11.0 to Ubuntu Netbook 9.10 (Karmic).

It runs much better and the layout is perfect for a non-IT person. I have one issue that I need to solve:

The graphics repainting is clunky/slow. For example, scrolling down a page like the System tab is jerky and moves about three clunks at a time.
Changing tabs takes about 2 to 3 seconds to refresh the image and shows about three faded transitions until the page is painted/loaded.

I'm thinking it might be the graphics card... But I don't know. This is the laptop's hardware:

[LIST]
[*]Memory 1.8 GB
[*]Intel(R) Celeron(R) CPU 550 @ 2.00 GHz
[/LIST]
Software:

[LIST]
[*]9.10 Netbook
[*]Kernel Linux 2.6.31-20-generic
[/LIST]
The monitor shows the memory at:
18.5% average: 347.9 mb
No swapping at all.

CPU
average of 38% with peaks of 80 to 100% on occasion.

Graphics Card:
VGA compatible controllerVIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] 

Benchmark info:
CPU Blowfish
This Machine    1995 MHz    16.776
Intel(R) Celeron(R) M processor 1.50GHz    (null)    26.1876862
PowerPC 740/750 (280.00MHz)    (null)    172.816713

CPU Cryptohash
This Machine    1995 MHz    79.351

CPU Fibonacci
This Machine    1995 MHz    5.972
Intel(R) Celeron(R) M processor 1.50GHz    (null)    8.1375674
PowerPC 740/750 (280.00MHz)    (null)    58.07682

CPU N-Queens
This Machine    1995 MHz    11.419

FPU FFT
This Machine    1995 MHz    11.753

FPU Raytracing
This Machine    1995 MHz    22.802
Intel(R) Celeron(R) M processor 1.50GHz    (null)    40.8816714
PowerPC 740/750 (280.00MHz)    (null)    161.312647

Anyone know what I should do? Is it the graphics card or the CPU? Is memory not being utilised properly? :???:

---

### Post by 2hot6ft2 on 2010-03-06
Check in
System > Administration > Hardware Drivers
to see if there's a proprietary driver for its graphics card.

---

### Post by OzVegan on 2010-03-07
No drivers except for the modem.

So you think a graphics card upgrade is the answer?

---

### Post by OzVegan on 2010-03-07
I was scouring the forum and someone mentioned that if there is a graphics card slot you could plug in an NVIDIA card and it should be picked up automatically. Maybe that's the answer.

---

