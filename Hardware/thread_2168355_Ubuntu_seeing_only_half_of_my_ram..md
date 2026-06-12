---
title: "Ubuntu seeing only half of my ram."
date: 2013-08-17
forum: Hardware
---

### Post by Panderz on 2013-08-17
I have 16 GB of ram installed, but Ubuntu is only detecting half of that.
The command free shows as well that only 8 GB are installed and system settings>details shows that as well.
My bios is detecting all 16 GB and in Windows it says 16 GB (7.96 usable)
Any thoughts?
Coud there be a bios setting that I need to change?

---

### Post by Bucky Ball on 2013-08-17
> **Panderz said:**
> ... in Windows it says 16 GB (7.96 usable)
Any thoughts?


Yes. Windows is telling you exactly the same thing Ubuntu is. Ubuntu appears to be ignoring the one that isn't working. You only have 8Gb of usable RAM. In Ubuntu, run this in a terminal:

```
free -m
```

What's the output?

If the RAM has just been put in, take it out and reseat it. To find which one is playing up, take one out, boot up. If there's problems, put the RAM back, take the next out, etc., until you find the odd one ...

The BIOS might say there's something in the slot and what, but not necessarily that it is working. Sometimes rubbing the connectors on the new RAM with a regular pencil eraser can get them behaving. Sounds crazy, but trust me ... just don't go berserk. :twisted: ;)

---

### Post by Yellow Pasque on 2013-08-17
Since the BIOS detects the stick, I think it's more likely to be a memory mapping/addressing issue or chipset limitation rather than a bad stick. Can you also give output of dmidecode?:
```
sudo apt-get install dmidecode
sudo dmidecode
```

---

### Post by Vladlenin5000 on 2013-08-18
Indeed it most likely is a chipset limitation. I would start with that. What is your motherboard's brand/model(+revision)?

---

### Post by Panderz on 2013-09-10
Sorry to everyone who replied to my thread, I forgot that I had made this. I never got it fully figured out, but I did find out that if I lowered by ram speed to 1066 (I think that's what it is), both operating systems detect all of my ram. 
I never got it working at 1600 MHz though.

---

### Post by 1clue on 2013-09-10
Figure out the model of your motherboard.  Go to the manufacturer website and see the maximum amount of RAM.

I've seen this sort of thing before and had more than one answer.  Here are the answers I've had, or have heard of:
[LIST=1]
[*]Motherboard does not support more than xx RAM.  Nothing you can do about it.
[*]Bad memory stick.  Already covered in this thread.  Extremely unlikely that you would have more than one bad in the same instant without a catastrophic power spike.
[*]Board failure.  For example, if you installed it badly and broke a socket.  Again, I doubt this because you almost certainly don't have 8g sticks and it's unlikely you broke more than one socket.
[*]BIOS problem.  Look for an upgrade.
[*]Operating system failure.  Unlikely because it's recognizing 8g.  Some Windows systems allow more than 4 but Linux will either register slightly less than 4, or however much you have.
[/LIST]

My opinion is it's number 1.

---

### Post by Bucky Ball on 2013-09-10
Maybe check the maximum RAM speed it will handle, as well as max amount. If it's finding it at 1066 but not at 1600 it seems logical. But then, I would have thought it wouldn't have seen any rather than half. Maybe an anomaly ...

---

### Post by Panderz on 2013-09-10
My motherboard is a gigabyte 990fxa-ud5. I'm pretty sure it supports up to 32 GB of ram. I already had updated my bios as per the suggestion of someone on a different forum. I think it might be a bad ram stick, my computer will not POST with one of the sticks, I'm not sure which one it is at the moment though. The dimms are all good, checked with my brother's ram sticks to make sure.

---

### Post by Panderz on 2013-09-10
The motherboard is also rated for up to 2000 MHz ram.

---

### Post by 1clue on 2013-09-10
Ya it's 32g max on the board.  Actually looks kinda nice.

Take your memory out and look for bent pins or cracks in the sockets, or any other damage.  Or crud stuck in the sockets.  Try that eraser trick on the stick contacts too.  Look for detached pads on the memory while you're doing the eraser thing.

I thought we were done with one stick knocking out a whole bank of sockets, you're using 4g sticks right?

---

### Post by Panderz on 2013-09-11
I'm using 2x8GB sticks. Sorry, probably should've mentioned that.

---

### Post by Panderz on 2013-09-11
It's just when I use a certain one by itself that it doesn't POST. If I use the 2 sticks together (2x8GB), they work in any configuration and are recognized as long as the speed is 1066 MH.

---

### Post by 1clue on 2013-09-11
OK take the one that doesn't post out, boot your system completely.  Does it still work?

If you have another compatible stick, even in another size, put that in the empty slot.  Does it work?  What amount of RAM do you get?

---

