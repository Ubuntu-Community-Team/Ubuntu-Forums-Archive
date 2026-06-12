---
title: "Motorola Moto G (Second Gen) Not recognised"
date: 2014-11-05
forum: Hardware
---

### Post by JayArtist on 2014-11-05
Hi,

This may seem a bit strange, but my new Second Gen (5") Motorla Moto G (should be the same as the older model) isn't being recognised in Ubuntu 14.04. What makes it stranger is that I have another PC with the same version of Ubuntu, with updates, same software etc and it is recognised!

Both machines are freshly installed. The phone was recognised in Win7 before I installed Ubuntu on the machine that wasn't working. I've also tried various USB ports, but nothing.

What is also weird is that if I switch from Media Connection (MTP) to Camera Connection (PTP) on the phone, the phone is recognised in Ubuntu, well at least the camera folder is.

I've seem others having this issue from updating Ubuntu 14.04 and some finding it fine on Kubuntu, but not Ubuntu when they tested.

Is this a bug perhaps? any help would be appreciated.

Jay.

---

### Post by Occasionally Correct on 2014-11-07
What is the output of **lsusb** and the last several lines of output from **dmesg **after plugging it in?

Not sure I'll be able to help, but I do have a workaround that I use on my first gen MotoG (not because my phone isn't recognized, but because I thought it was nerdy and cool). Install [Ftp Server]("https://play.google.com/store/apps/details?id=com.theolivetree.ftpserver&hl=en") on your phone, then use some FTP client on Ubuntu to connect to your phone and download/upload whatever files you need. :)

---

### Post by JayArtist on 2014-11-07
My Moto G is the new model, 2nd gen with an SD card slot. I would have  thought that because it's fresh out this year, it hasn't full support in Ubuntu. Strange that it works on one machine and not the other though. The only thing I did different was run Android Dev Kit manually - but as it wasn't installed, I'd be surprised if any ADT drivers were copied across.

That's a bit of a pain to do. As a basic work around myself, although not ideal, because PTP works (the camera folder), I can copy stuff to that and transfer from there.

---

