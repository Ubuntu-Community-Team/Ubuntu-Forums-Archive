---
title: "ata errors"
date: 2009-06-02
forum: Hardware
---

### Post by EddievV on 2009-06-02
Hello all, 

In 2007 I installed Ubuntu 7.10 on a new computer with a P5KC motherboard and a WD Caviar SE16 of 500 GB. After some time I noticed in recovery mode that a lot of error message were put on the display. They basically look like this:

[    6.936053] ata2: SATA link down (SStatus 0 SControl 300)
[    6.936065] ata2: EH complete
[    7.373133] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[    7.373139] ata2: irq_stat 0x00000040, connection status changed
[    7.373144] ata2: SError: { DevExch }
[    7.373153] ata2: hard resetting link
[    8.096032] ata2: SATA link down (SStatus 0 SControl 300)
[    8.096041] ata2: EH complete
[    8.618350] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[    8.618355] ata2: irq_stat 0x00000040, connection status changed
[    8.618360] ata2: SError: { DevExch }
[    8.618368] ata2: hard resetting link
[    9.340058] ata2: SATA link down (SStatus 0 SControl 300)
[    9.340065] ata2: EH complete

I blamed the harddisk but during serious testing at the shop nothing was found. So I decided to install Ubuntu Studio 8.10 on a new harddisk, this time a Samsung 640 GB. The same errors appeared but at a much lower rate.

Recently I upgraded to Ubuntu 9.04, the errors keep coming. I can prevent them from coming to the screen by typing 'dmesg -n1'. However, I use a program, ecasound, that sends audio files to a DAC in real time. This program jumps occasionally too early to the next song and sometimes my PC is completely stuck and can only be shut down with the off-button. Other users of this program do not have these nasty effects. 

So I have a feeling that these ATA interrupts mess up my real time program. Can anyone give me a clue of what is going on here and if there is a way to fix it?


Kind regards,
Eddie

---

