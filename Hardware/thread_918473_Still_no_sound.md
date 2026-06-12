---
title: "Still no sound"
date: 2008-09-13
forum: Hardware
---

### Post by ossinthedesert on 2008-09-13
I've installed Xubuntu 8.04 onto my computer. Upon inspection of the new installation, I noticed there was no sound, but this was expected because I've used Xubuntu onto this computer before. Well anyway, the sound card is a Soundblaster 16, I believe. But I looked at a chip on the card itself and the product number is CT4520. After googling, I read that its a Creative Soundblaster AWE64. The card connects through ISA. IDK if its PNP, but Windows XP detected it just fine. I followed several docs, such as the Sound Troubleshooting guide, along with How to Setup Sound Cards. I've installed and uninstalled ALSA several times, each taking different steps and using different modules. The two are snd-sb16 and snd-sbawe. Neither work. aplay -l shows no playback devices either. Its been four days and I have yet to find a solution. Any help or ideas are appreciated. 

On a side note, I changed the IRQ of the sound card to 5, as following ```
options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5 mpu_port=0x330

``` under /etc/modprobe.d/sound and upon doing so, my network card needs to be reconfigured.

---

### Post by cariboo on 2008-09-13
In a terminal try:

```
cat /proc/interrupts
```

to see if there is an unused irq. That is pretty old hardware, if you are still using an isa card.

Jim

---

### Post by ossinthedesert on 2008-09-14
OK, here's what I got:

```
           CPU0       
  0:      51865    XT-PIC-XT        timer
  1:        153    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          2    XT-PIC-XT      
  4:          2    XT-PIC-XT      
  5:          0    XT-PIC-XT        MPU401 UART
  6:          5    XT-PIC-XT        floppy
  7:          1    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:       9219    XT-PIC-XT        acpi, uhci_hcd:usb1
 11:       1259    XT-PIC-XT        eth0
 14:       9035    XT-PIC-XT        libata
 15:       2727    XT-PIC-XT        libata
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

```

Now what?

---

### Post by JohnnyCanuck on 2008-10-04
Did you get a response on this issue?

---

