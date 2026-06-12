---
title: "[SOLVED] PC is DEAD, WONT TURN ON"
date: 2009-01-01
forum: Hardware
---

### Post by NickArgyle on 2009-01-01
Ok, heres what's up. I had an old HD from a computer that got fried a couple of years ago. I set it to slave and connected it to my desktop. When I booted I was stuck at "verifying dmi pool data." I decided I should reset the CMOS, so pulled out the batter, waited 30 seconds, and plugged it back in. Now, upon booting, I just get a bios beep, then nothing happens. No monitor, nothing. It starts to boot, beeps, then dies.

From what I can tell the Beep sequence is either 3-1-1 or 2-1-1, though I'm not certain. It is a long beep and two short beeps. If I am right about the beeps then it is either "Bit 0; This data bit on the first RAM IC has failed.  Replace the IC if possible," or "Slave DMA register failure. The DMA controller has failed.   Replace the controller if possible."

I used an antistatic wrist strap, so I don't know what could have gone wrong here. I have tried resetting ram, unplugging HDs, using different IDE cables, but I get nothing. 

Does anyone have any idea what's going on here? PLEASE HELP!

---

### Post by my_key on 2009-01-01
Check the manual that came with your motherboard. It should explain the beep sequence. I can't help you with it, because these beep sequences differ from manufacturer to manufacturer. Post here if you figure out what the beeps mean.

PS. The battery on modern systems is only for the clock. It doesn't reset the BIOS any longer. To reset your bios, you also need to refer to your mother board's manual. Usually it's a jumper you need to set, or a contact you need to short while pressing the power button of your computer.

---

### Post by oilchangeguy on 2009-01-01
> **my_key said:**
> Check the manual that came with your motherboard. It should explain the beep sequence. I can't help you with it, because these beep sequences differ from manufacturer to manufacturer. Post here if you figure out what the beeps mean.

PS. The battery on modern systems is only for the clock. It doesn't reset the BIOS any longer. To reset your bios, you also need to refer to your mother board's manual. Usually it's a jumper you need to set, or a contact you need to short while pressing the power button of your computer.

not correct, about the mobo battery. pull it, let it sit for at least 30 min. your bios is back to the default settings. and that annoying bios password is gone (if there was one).

---

### Post by damis648 on 2009-01-01
Well I doubt it was any sort of static damage as long as you had the same potential as the PC. I would say that maybe that dead drive maybe had a short that caused some damage?

---

### Post by NickArgyle on 2009-01-01
> **damis648 said:**
> Well I doubt it was any sort of static damage as long as you had the same potential as the PC. I would say that maybe that dead drive maybe had a short that caused some damage?

I am worried that is the problem.

I will leave the battery out for a while and see if it makes a difference. I only had it out for 30 secs.

---

### Post by oilchangeguy on 2009-01-01
> **NickArgyle said:**
> Ok, heres what's up. I had an old HD from a computer that got fried a couple of years ago. I set it to slave and connected it to my desktop. When I booted I was stuck at "verifying dmi pool data." I decided I should reset the CMOS, so pulled out the batter, waited 30 seconds, and plugged it back in. Now, upon booting, I just get a bios beep, then nothing happens. No monitor, nothing. It starts to boot, beeps, then dies.

From what I can tell the Beep sequence is either 3-1-1 or 2-1-1, though I'm not certain. It is a long beep and two short beeps. If I am right about the beeps then it is either "Bit 0; This data bit on the first RAM IC has failed.  Replace the IC if possible," or "Slave DMA register failure. The DMA controller has failed.   Replace the controller if possible."

I used an antistatic wrist strap, so I don't know what could have gone wrong here. I have tried resetting ram, unplugging HDs, using different IDE cables, but I get nothing. 

Does anyone have any idea what's going on here? PLEASE HELP!

unplug everything but the keyboard, one stick of ram, and the video card. and see what happens.

---

### Post by NickArgyle on 2009-01-01
Ok, so I reset the CMOS again and the PC is booting. However, the HD still won't load. It's stuck "verifying DMI pool data" again. There is a lot about this online so I am going to look around for an answer. I am thinking the best thing to do is put in a cd and error check the hd or rebuild the master boot menu.

---

### Post by kspncr on 2009-01-01
It sounds like that hard drive is gone for good then. If it were me, I wouldn't risk letting it cause any more problems.

---

### Post by NickArgyle on 2009-01-01
Yes, I am afraid I wont be attempting to recover that HD again. 

Anyhow, I reinstalled the OS and the computer is up and running fine. Thanks to everyone for the help.

---

