---
title: "It's a RAM issue."
date: 2010-04-19
forum: Hardware
---

### Post by Zexter on 2010-04-19
So I have been combing the forums and google for ubuntu ram problems. Though, what I have found is slightly different than my problem.

I'm just coming back to nix from windows 7. (mainly because im an android user. getting into deving for android, and thought itd be appropriate)

I just noticed that ubuntu tells me i only have 3.9g of ram available. So i naturally booted into bios to check. Well, it's also saying I only have 4g of ram. 

The problem is. thats untrue. i have 6g of ram installed. when i was running windows 7 64bit. bios and win showed me as having 6g of ram. now my box is lieing to me, lol.

how do i unleash my hidden 2g of ram?

---

### Post by dabl on 2010-04-19
Linux takes its cue from BIOS on things like memory, drives, etc.  You need to figure out why and how BIOS got reset (Hint: Linux didn't do it.)  There may be some issue with one of your memory modules, or a piece of lint in the connector on the motherboard, or some other hardware issue.

---

### Post by Zexter on 2010-04-19
really? thats one hell of a cowinkydink!

i literally had 6g of ram one day. installed nix. then had 4g.
i'll take er apart and give er a good cleaning.

---

### Post by Zexter on 2010-04-19
so here's the verdict, and now im really confused.

so i couldnt figure out why i dont have 6g. took the ram out. looked at it. sure enough i have 2x 2g sticks. so the question now is. why did i think i had 6g? and why was windows telling me i had 6g? lol. i swear i dont do drugs.

---

### Post by tgalati4 on 2010-04-19
Some memory can be either single or dual data rate (ddr) meaning that addresses are stored on both up and down strokes of the memory clock.  It's possible that one pair of your memory can be read as 4 GB with ddr so that you really have 6 GB available.  

It's up to the BIOS to enumerate your memory.  Try moving them around and keep similar pairs matched to your color-coded memory sockets.  If your sockets aren't color-coded, then look for a motherboard guide.  You get the best performance by keeping similar memory sticks in their respective slots.

Run memtest and write down the memory speeds and amounts and compare with your slot arrangement.  Move them and re-run the test.  Keep the configuration that gives you the greatest capacity and speed.

---

### Post by dabl on 2010-04-21
> **Zexter said:**
> 

 so the question now is. why did i think i had 6g? 



Well, I think we can safely categorize this as a PEBCAC issue.  :lolflag:

---

### Post by Yellow Pasque on 2010-04-21
> **Zexter said:**
> i swear i dont do drugs.
I highly recommend them :lolflag:

---

