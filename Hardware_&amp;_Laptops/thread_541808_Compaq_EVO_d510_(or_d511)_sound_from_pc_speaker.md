---
title: "Compaq EVO d510 (or d511) sound from pc speaker"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by Error403 on 2007-09-03
Hi, I'm using a Compaq Evo d510 or d511, I don't remember, as a pvr on my tv and the sound comes out by both the pc speaker and the tv's speakers.  When I mute or shut down the TV, the sound still plays through the pc itself.

Is there a way to disable the PC speaker from there?  Thanks!

---

### Post by angryfirelord on 2007-09-03
Is the sound source coming from the tv or coming from the computer? How are the audio cables configured?

---

### Post by Error403 on 2007-09-03
It comes from both: I plugged a audio jack to rca cable from the sound card to the sound inputs of the TV, but the sound still comes out from the pc.

I saw that behaviour somewhere else when I booted ubuntu on a Dell and the booting sound disturbed people so I just plugged in my ipod earphones so the sound would go through them and no one would hear it, but the internal pc speaker made the same sound.

Any ideas?  Thanks!

---

### Post by angryfirelord on 2007-09-03
I think I'm getting myself confused. When you say "internal pc speaker", do you mean the 2 speakers that are built in front of the laptop, or the tiny pc speaker built into the motherboard? (that's the one that makes all the beeping when you go into the BIOS & hit a wrong key)

---

### Post by Error403 on 2007-09-03
Er, it's not a laptop, it's a small form factor box like [this one]("http://h18000.www1.hp.com/products/quickspecs/11349_div/11349_OV1_SSF.gif"). Found [here]("http://h18000.www1.hp.com/products/quickspecs/11349_div/11349_div.HTML"). 

There is no apparent speaker in front of it, but it seems that the sound comes from the "tiny speaker on the motherboard" like you say.  :)

---

### Post by angryfirelord on 2007-09-03
Strange that it would do something like that. Try:

[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/]("http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/")

-disabling it from the BIOS
-look for jumpers on the motherboard that could disable it
-look for cables that can be easily be removed that connect to the speaker

---

### Post by Error403 on 2007-09-03
I was thinking about doing that as soon as I have a minute.  I might simply drive a pair of cutters through the pc speaker's wires.

Thanks anyway!

---

### Post by angryfirelord on 2007-09-03
> **Error403 said:**
> I was thinking about doing that as soon as I have a minute.  I might simply drive a pair of cutters through the pc speaker's wires.

Thanks anyway!
Don't do that unless you're absolutely sure that blacklisting & looking through the BIOS doesn't give results.

---

### Post by Error403 on 2007-09-28
Hey, I fixed it! You have to remove the power supply module and there lies the pc speaker wire. However, the pc speaker is not removable (to make breathing space) because it is an integral part of that fixture that helps lift up the drives module.

There, no more sound from the box!

---

