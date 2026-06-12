---
title: "No signal to monitor after hardware upgrade"
date: 2017-08-31
forum: Hardware
---

### Post by invektiv on 2017-08-31
**I solved it! Solution is at the bottom.**

I just upgraded my motherboard, CPU and RAM, but now when I start the computer the monitor says there's no signal. The fans are running and the power-LED is lit, but there's no signal to the monitor.

I don't know what to do. It's driving me crazy. I thought maybe you could help me out.

What I've done so far is:
- I've checked the power cords from the PSU (the 4-pin and the 24-pin), and they are securely attached
- I've checked that the CPU-fan and all chassis-fans are connected to the motherboard
- I've cleared the CMOS
- I've switched the RAM from one slot to the other
- I've tried a different video card
- I've tried the integral graphic card via a VGA contact at the motherboard (both with a video card in place and with it taken out)
- I've disconnected the power cord and pushed in the start button for a minute
- I've checked on Asus website that the memory stick is supported

Do you have any ideas?

My setup is: Corsair 750W PSU, i7-7700K CPU (with NH-L9x65 CPU-fan), Geforce GT 1030 video card, Asus B250M-K motherboard and Crucial DDR4 2400MHZ 8GB RAM

What I did after my initial post was this:
- I ordered a POST-speaker for the motherboard (have yet to receive it)
- I had my motherboard and processor checked (and they worked fine)

**Finally i tried a different RAM-stick and now I have signal to the monitor :)**

---

### Post by him610 on 2017-09-02
Don't know if this will help or not. A friend of mine had a similar problem with a similar system. He tried many of the same remedies that you have tried with no success.

It turned out to be the cpu heatsink appearing as if were misaligned, and the friend being a 'neatnik.' Whenever an attempt was made to visually align the cpu cooler the system would not boot. Whenever the cpu cooler appeared to be misaligned, it booted. Evidently when he attempted to align the cpu cooler, it ever so slightly twisted the some of the cpu contacts into non-connection.

Some motherboards (MSI) have diagnostic LEDs on the board itself. One more thing, if you have one of those tiny speakers connected to the PC Speaker contacts, the Beep codes may help diagnose the problem.

---

### Post by jglen4902 on 2017-09-03
> **invektiv said:**
> I just upgraded my motherboard, CPU and RAM, but now when I start the computer the monitor says there's no signal. The fans are running and the power-LED is lit, but there's no signal to the monitor.

I don't know what to do. It's driving me crazy. I thought maybe you could help me out.

What I've done so far is:
- I've checked the power cords from the PSU (the 4-pin and the 24-pin), and they are securely attached
- I've checked that the CPU-fan and all chassis-fans are connected to the motherboard
- I've cleared the CMOS I think
- I've switched the RAM from one slot to the other
- I've tried a different video card
- I've tried the integral graphic card via a VGA contact at the motherboard (both with a video card in place and with it taken out)
- I've disconnected the power cord and pushed in the start button for a minute
- I've checked on Asus website that the memory stick is supported

Do you have any ideas?

My setup is: Corsair 750W PSU, i7-7700K CPU (with NH-L9x65 CPU-fan), Geforce GT 1030 video card, Asus B250M-K motherboard and Crucial DDR4 2400MHZ 8GB RAM
After changing your hardware, did you reinstall Ubuntu?

---

### Post by Yellow Pasque on 2017-09-04
[https://www.asus.com/us/Motherboards/PRIME-B250M-K/HelpDesk_CPU/](https://www.asus.com/us/Motherboards/PRIME-B250M-K/HelpDesk_CPU/)
Supposedly, you need at least BIOS 0302 for the 7700k to work.

> After changing your hardware, did you reinstall Ubuntu? 
You should still get a video signal before the OS boots (POST Screen and/or mobo maker's logo).

---

### Post by invektiv on 2017-09-11
Thanks for your input guys! I'm very happy to have signal now :)

---

