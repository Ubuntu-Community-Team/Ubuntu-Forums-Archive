---
title: "how to upgrade bios without video?"
date: 2010-02-19
forum: Hardware
---

### Post by steve19137 on 2010-02-19
i was just given a custom pc, and it has a problem: no video. when you boot it, it just beeps. so here are the specs (to the best of my knowledge)

80GB IDE hard drive (no OS i suspect)
floppy drive (standard size, whatever it is)
2GB RAM
Pentium 4 processor (cant remember the speed)
ASRock K7VM2 Motherboard

its the mother board that has all the connections for the back of the computer: video, audio, usb, and every thing else. heres the story. this computer originally had a video card, but it was taken out for some strange reason, and now there is not output. i suspect the the bios in the mother board is still trying to send video through the video card, even though it can send video through itself. so what i need is to get a bootable floppy disc (with dos), put the bios upgrader in it, and run it in DOS (i dont have a choice in that matter). so how can i do that with a USB floppy drive and ubuntu?

---

### Post by JackRock on 2010-02-19
What is the "beep" doing?  Is it a long one, or several short ones, or a long one followed by a few short beeps?  This is the POST, letting you know what's going on.

Does the mobo have its own video port?  If so, are you running any add-on video cards?  If both are true, remove the secondary card, connect the monitor to the mobo's video port so you can start the machine and change BIOS settings.

I seriously doubt flashing your BIOS is going to resolve this problem.  

As for "solving the problem in Ubuntu", you won't.  Ubuntu (or any other OS) isn't yet loaded by that stage, so it wouldn't have any effect yet.  If you have absolutely no video, you will have to resolve the problem in the hardware and/or BIOS.

---

### Post by paulisdead on 2010-02-19
You might be able to get it to use the onboard video again by resetting the CMOS jumper on the motherboard.  If you do that, though, you'll need to go through and reconfigure all the options in the BIOS afterward, since it'll lose all those.  I'm sure you can find the manual on the manufacturer's site that'll tell you where it is.  It's just a jumper probably near the battery on the board.  Alternatively you could pull the battery out for a few minutes and it would accomplish the same thing.

---

### Post by steve19137 on 2010-02-19
> **JackRock said:**
> What is the "beep" doing?  Is it a long one, or several short ones, or a long one followed by a few short beeps?  This is the POST, letting you know what's going on.

Does the mobo have its own video port?  If so, are you running any add-on video cards?  If both are true, remove the secondary card, connect the monitor to the mobo's video port so you can start the machine and change BIOS settings.

I seriously doubt flashing your BIOS is going to resolve this problem.  

As for "solving the problem in Ubuntu", you won't.  Ubuntu (or any other OS) isn't yet loaded by that stage, so it wouldn't have any effect yet.  If you have absolutely no video, you will have to resolve the problem in the hardware and/or BIOS.

the beeps are short and many. my dad did some research, and he said that the beeping is probably telling me that there is no video. the mobo (i like that) have onboard video, but no secondary video card. it used to have a secondary, but now it doesnt.

---

### Post by steve19137 on 2010-02-19
> **paulisdead said:**
> You might be able to get it to use the onboard video again by resetting the CMOS jumper on the motherboard.  If you do that, though, you'll need to go through and reconfigure all the options in the BIOS afterward, since it'll lose all those.  I'm sure you can find the manual on the manufacturer's site that'll tell you where it is.  It's just a jumper probably near the battery on the board.  Alternatively you could pull the battery out for a few minutes and it would accomplish the same thing.

ill probably look for that jumper or battery thing, and see what that does, as it is the easiest option i have.

---

### Post by pirateghost on 2010-02-19
> **paulisdead said:**
> You might be able to get it to use the onboard video again by resetting the CMOS jumper on the motherboard.  If you do that, though, you'll need to go through and reconfigure all the options in the BIOS afterward, since it'll lose all those.  I'm sure you can find the manual on the manufacturer's site that'll tell you where it is.  It's just a jumper probably near the battery on the board.  Alternatively you could pull the battery out for a few minutes and it would accomplish the same thing.

this should be the first place to start.  you should NOT try to flash BIOS if it is not working properly to begin with.

---

### Post by steve19137 on 2010-02-19
would that be the battery and CMOS jumper?

---

### Post by steve19137 on 2010-02-19
> **pirateghost said:**
> this should be the first place to start.  you should NOT try to flash BIOS if it is not working properly to begin with.

resetting would mean pulling it out right? the cable in the pic i took?

---

### Post by steve19137 on 2010-02-19
OMG!!! i did it!!! thanks paulisdead for the tip!!!

---

