---
title: "Computer Auto Shuts Off Within A Few Seconds Of Starting"
date: 2017-01-11
forum: Hardware
---

### Post by ThePowerpuffGirls on 2017-01-11
My best friend had given me her husbands old computer. It works, but keeps shutting off.
I switched power supplies and it worked for a little while and started doing it again. I put the power supply  that I had temporally in it, in the computer I'm using now and it works without any issues.
I took apart everything and put it all back. I've updated the BIOS.
I had it working long enough to install Ubuntu when I swapped out the power supply. I have the old one back in it. I cleaned the dust from the case, the fans. I took out the CPU, which was caked with paste so much that it stuck to the heat sink and wiped it all off, and applied new paste.
I configured the BIOS to AHCI,
I made sure all the RAM installed was 800MHz.
I can't figure it out.

Motherboard: ASUS M2N SLI Delux
RAM: 4GB DDR2 800MHz (2 sticks)
Processor: AMD Athlon X2 64 5600+
Graphic Card: Nvidia GeForce G310 512MB
Drives:
Seagate 250GB (7200RPM), Silicon Power 120GB SSD. I did have a KingSpec 60GB SSD, but upgraded because it was too slow.

---

### Post by ThePowerpuffGirls on 2017-01-13
Update: I've changed the case, took everything apart and back together again, and it still does it. Has anyone any idea what is causing it?

---

### Post by geeksmith on 2017-01-13
If it's getting past the POST, then this is probably related to heat or a bad motherboard. Is the BIOS doing a full memory check? Does it shut down if you stop it in the BIOS, or just if you boot the OS? What about a live Ubuntu DVD or USB stick?

Have you detached all external devices? Even keyboard, mouse, monitor? And internal cards/components that aren't essential for boot?

---

### Post by #&amp;thj^% on 2017-01-13
Don't kill the messenger but this just looks and acts like Bad or faulty Hardware.
Ninjed by GeekSmith:)

---

### Post by ThePowerpuffGirls on 2017-01-13
I had it working a short while ago, and installed Ubuntu on an SSD. All hardware seems to work OK.
The weird thing is that when it is started, it seems to stay started until shut restart or shut down. It's like we have to wait some time before turning it on to get it to stay on. It's one of the weirdest things I've seen.

When I got it, it had a lot of dust, but I cleaned the heat sink, it's like it was when it was bought. It's a mystery as to what it is, exactly, and how it is caused. Someone said bad ram, and another said it could be the RAM.

Update: I got it working, and it's only been about 10 minutes since it was last working. I'm running a RAM test through memtest86 v5.01

It says 'RAM: 401 MHz (DDR2-803)'
I have the BIOS set for 800MHz, I thought that is what is was. I'm confused.

---

### Post by Yellow Pasque on 2017-01-14
Bad CMOS battery?

---

### Post by ThePowerpuffGirls on 2017-01-14
The settings are staying the same, however the one it originally had in it, was bad because every time I unplugged it, everything was clear.
Could a bad CMOS save everything but still cause it?

I've checked the RAM, 4 passes, 0 fails.

What about the processor? That is pretty much the only thing I didn't check yet. I've been using the same one since I got it.
I don't think I have another AM2 processor, just an AM3.

---

### Post by Yellow Pasque on 2017-01-15
In general, I think I would try disabling all unused features in the BIOS (floppy drive, 2nd LAN port, esata controller, etc.)

> What about the processor? That is pretty much the only thing I didn't check yet.
It's hard to remove all doubt without a spare. If you're confident you installed the heatsink correctly and you've been monitoring temps to assure no overheating, you may want to try bumping the CPU voltage a bit. I have my doubts it will help, but it's worth a try. I've worked with a bunch of Athlon 64/X2 chips, and I don't think I encountered one that didn't run solid at stock voltage. In fact, they could usually pass stress tests with less than stock voltage, especially the awesome Orleans/Brisbane cores. So I wouldn't worry too much about overheating an AM2 chip with modest voltage bumps, even with a stock heatsink.

I guess you could also try bumping the voltage on the nForce chipset, but I would be very cautious about that. Those chips ran **HOT**, even on mobos with a heat pipe setup like yours. I hope you have a good exhaust fan on your case to move air over the heatsink. Maybe scaling the HT down to 4x would be a better idea.

> Could a bad CMOS save everything but still cause it?
I've seen bad CMOS batteries/chips do weird things. I'm actually experiencing what I suspect to be a dying battery on my AM3 system (built in 2008 IIRC) right now. It doesn't want to cold boot with full RAM speed. It will refuse to get past POST until rebooted a few times, and then it informs me that it scaled back my RAM speed (DDR3-1333 to DDR3-800). I enter the BIOS and set it back to 1333, reboot, and then it will run fine for weeks/months if I don't turn it off. Like you, I get no errors with memtest, and all of the BIOS settings (including date/time) are always retained. *shrug*

---

### Post by ThePowerpuffGirls on 2017-01-25
I believe the issue could be a faulty motherboard, as each time I test it, it gets more and more problems and I'm unable to install Ubuntu without crashes during installation, and now it says the USBs are faulty or something.
You never know, could be the a bad CMOS or maybe both.

Thank you for your input and your help. :)

---

### Post by mörgæs on 2017-01-26
Are you able to install a text-only system and is it stable?

---

