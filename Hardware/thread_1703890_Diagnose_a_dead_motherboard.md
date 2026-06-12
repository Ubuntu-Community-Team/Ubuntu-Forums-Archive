---
title: "Diagnose a dead motherboard"
date: 2011-03-09
forum: Hardware
---

### Post by nl4m on 2011-03-09
I have a laptop that does not turn on. When I plug in the power cable only the battery light comes on. I push the power button but the computer never turns on... I want to find out what the problem is. How do I test to see if the Motherboard is defective, or if it's the CPU that is defective? The ram I've tested  by putting it in another computer. I just need to know how to test the motherboard and the CPU to see which one is defective, how do I do that? PLEASE HELP!!!!!

---

### Post by Yellow Pasque on 2011-03-10
Theoretically, you would try the CPU in another system with the same socket and/or use a different CPU for the mobo in question. Of course, that's not always feasible, so you may have to take it to a repair shop.

Keep in mind that it could be the battery or power supply circuitry (which I guess is part of the mobo).

---

### Post by tgalati4 on 2011-03-10
Pull the battery.  Try to boot on wall power alone.

---

### Post by nl4m on 2011-03-10
I tried to boot without the battery it does not help. I let the battery charge and booted from the battery alone, it does not help. The computer wont turn on. I tried booting without the ram, does not help. The power cable is not an original, but there is still power going through the computer.

So the only way to test the CPU is to replace it, or try it on another system? If the CPU fails then that's the problem. If it passes than is must be the motherboard? Can it be a bad HDD drive that's preventing the machine from powering up?

What's the "power supply circuitry"? Does that mean I'd have to replace the motherboard, or only a part of it?

---

### Post by tgalati4 on 2011-03-10
It could be the power brick.  Try another one.

---

### Post by Grenage on 2011-03-10
> **nl4m said:**
> Can it be a bad HDD drive that's preventing the machine from powering up?

No, a HD isn't required to boot a machine; you'd leave that unplugged while testing.

Probability of failure is usually PSU > Motherboard > CPU.  I've never actually seen a stock-clocked CPU fail, but it does happen.

---

### Post by nl4m on 2011-03-10
It's a laptop. Isn't the power supply build into the computer? If the power supply went bed the motherboard would need to be replaced, on a laptop, right?

If it's the CPU that's the problem, wont at least the power light turn on? The whole laptop is dead, excluding the battery light.

---

### Post by Grenage on 2011-03-10
> **nl4m said:**
> It's a laptop. Isn't the power supply build into the computer? If the power supply went bed the motherboard would need to be replaced, on a laptop, right?

They are usually external on laptops.

> **nl4m said:**
> If it's the CPU that's the problem, wont at least the power light turn on? The whole laptop is dead, excluding the battery light.

I would personally expect more than just a battery light if it was the CPU, so I'd lean towards motherboard or PSU.  Unless you have some kit to test the PSU output, or a spare motherboard/cpu, you're a bit stuck.

---

### Post by nl4m on 2011-03-10
By PSU you mean the AC/Power cable? There's a normal 19v flowing through it.
I've read on the net that some motherboards beep when the CPU is bad, other motherboards don't... This varies by model?

---

### Post by cascade9 on 2011-03-11
Yep, that varies by model and the error as well. 

> **Grenage said:**
> They are usually external on laptops.

Yeah, true. But there is still a power conversion going on (12v to 5v/3.3v or, similar).I agree, power supply, (or conversion)  is probably not the problem though. 

@ nl4m- try holding down the power button for a while, a long while. Up to 60 secodns. Sometimes that forces the CMOS to clear, and has given new life to laptops in the same situation as yours. 

The CMOS should clear with 10-20 seconds, but holding it down longer wont hurt.

---

### Post by nl4m on 2011-03-11
^^^ I tried it... Now the battery light comes on for a few seconds and  then shuts off, no matter what I press the light remains off... 

I wish I knew how to tell whats defective in a computer... I have  another computer where the lights come on, the fans stays off, there is  no HDD activity, and the screen never turns on.... also motherboard?

---

### Post by Niedzwiedz on 2011-03-11
This can turn into mass confusion. Lot of different ideas and many will work.
First, unplug your AC adapter. Remove the rechargeable battery and then remove your CMOS backup battery/batteries some may have more than one. Push the power button and hold for a few seconds, most people may say 15 seconds, may see an LED flicker on/off.
Second, you need a volt meter, plug the AC adapter into the wall and see if your getting the voltage output that the Specification label say; be something like;
input: 110-240 VAC
output: 19 VDC or whatever.
You can try checking the rechargeable battery, but, do not ask me what pin do what. I would look to see what the  battery volts are, may be 12 VDC Then assume a pin to one side is ground and look for that voltage from the battery. If, you have the Ground backwards then you see -12 VDC instead of 12 VDC which means it is good. YOUR volts may be different, so, read the labels.
If, the AC adapter looking good, and not need replaced, and the battery not charged (regardless of what lights show), then it the board inside that control the voltages and where they go. Here you will need to open up the Laptop and use the volt meter again.
IF, the AC adapter and the rechargeable battery look good and you thought to check the CMOS batteries just to be sure they 3 VDC?
Then it probably the MOBO, but, no promise. As stated, try the CPU in another known working board, OR, try a known working CPU in your board.

---

### Post by PRC09 on 2011-03-12
Not sure about the cmos battery or swapping the cpu from a laptop but the last one I tried to do this with had to be completely disassembled just to access those components.If you wish to do this go to the manufacturers website look for the service manual and the disassembly instructions and about 50 small screws and 3 or 4 broken plastic tabs later you will be ready to start........

---

