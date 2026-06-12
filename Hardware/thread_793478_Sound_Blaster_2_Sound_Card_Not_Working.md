---
title: "Sound Blaster 2 Sound Card Not Working"
date: 2008-05-13
forum: Hardware
---

### Post by ARam1024 on 2008-05-13
I've found a lot of posts in different forums about similar issues, and I've tried their suggestions, but I still can't get this to work.  I also tried the [ALSA website]("http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1#Audigy_2_Platinum_EX"), but it instructs you to modify /etc/modules.conf, which I discovered Ubuntu does not have.

Computer Specs:
Asus A7N8X-Deluxe motherboard (nforce 2 chipset)
integrated nforce audio (won't work in Ubuntu or Windows XP)
AMD Athlon XP 2700+
1.5 gb DDR PC3200 RAM
Asus AH2600PRO 512mb (AGP card from ATI)

I'm running Kubuntu 8.04 with KDE4.  I just loaded the OS yesterday, so it's pretty fresh.  I know that this sound card was working in Kubuntu 7.04 with KDE 3.5, but I've had several OSs on there since (XP, Vista, Kubutu 7.10)

Helpful info:

cat /proc/asound/cards
0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650E at irq 16
 1 [default        ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.0-2, full s
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd3010000 irq 11
 3 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

the USB-Audio is an external sound card I'm using temporarily.  The HDMI output is on the graphics card.

If anyone has any advice or could direct me to helpful thread, I'd be very appreciative

---

### Post by kessaris on 2008-07-02
I'm having the same or a similar issue!

Turns out ubuntu has diverged from the regular established procedures of configuring the ALSA hardware..

I have no idea how we're supposed to add new audio hardware!!

Sorry I couldn't be of any help,

but if you found out anything since then, I'd love to know!

---

### Post by ARam1024 on 2008-07-02
thanks for the info.  A moth got into my desktop and wreaked havok.  I'll try again with the drivers after the autopsy.

---

