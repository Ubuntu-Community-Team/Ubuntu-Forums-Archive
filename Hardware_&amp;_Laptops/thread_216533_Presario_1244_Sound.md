---
title: "Presario 1244 Sound"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by Quadzilla63 on 2006-07-15
I recently upgraded my Compaq Presario 1244 from Breezy to Dapper and have been plagued with sound problems.  When I initially installed Breezy the sound never worked.  I believed it to be a problem with the fact that the install was interupted prior to being finished and restarted at a later date.  I thought when I upgraded to Dapper, all the problems would have been solved, but no such luck.

Anyone have any recommendations as to how to solve the sound issue?

D.

---

### Post by javaJake on 2006-07-15
I will not be able to help you on this issue. However, posting information about your sound card would be useful, and will make it more likely that you'll get help from someone else.

The most important things you can get are the model name and the USBID.

---

### Post by smontano7 on 2007-12-20
Hi folks,

I'm currently setting up Xubuntu 7.10 on a Compaq Presario 1244 with an ES1869 audio chipset and cannot get the audio to work.  Here is the audio card info straight from the bios screen:

* Base I/O address: 220-22F
* Interrupt: IRQ5
* DMA Channel: DMA1
* DMA Channel: DMA0
* FM I/O address: 388-38B
* MPU I/O address: 330-331

So far I have tried editing the /etc/modules file to include the following which allowed a volume icon to appear on the upper right of the Xubuntu GUI.  However there was no sound device available to choose.  Here is my /etc/modules file so far.  The first three lines were present before I did any editing.

loop
lp
fuse
snd-esl8xx enable=1 isapnp=0 port=0x220 mpu_port=0x330 fm_port=0x388 irq=5 dma1=0 dma2=1

Any help would be greatly appreciated.  Thanks!

Steve

---

