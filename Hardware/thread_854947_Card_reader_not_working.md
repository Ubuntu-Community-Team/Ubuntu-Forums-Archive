---
title: "Card reader not working"
date: 2008-07-10
forum: Hardware
---

### Post by idrake88 on 2008-07-10
I have a Dell inspiron 9400 running ubuntu hardy The card reader will not read my memory stick

I have found threads on this problem, but they were old and the information in there could not solve my problem,

After running 

 lspci | grep Ricoh

The output is

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


I am uncertain as to what to type next, i have gotten various error outputs when trying other methods, any help would be great, Thank you

---

### Post by sergiom99 on 2008-07-10
Hi.
There's no kernel support yet for Sony MS cards.
Developers have to code the drivers or something like that.

---

### Post by idrake88 on 2008-07-10
Thanks,

So your  saying i am basically out of luck for my memory stick?

---

### Post by silkstone on 2008-07-10
Sorry I don't have a solution, but I can read Sony MS no problem at all with an external reader on Hardy - I've just tried it again to be sure!

---

### Post by idrake88 on 2008-07-10
Alright well thanks for the tip it is good to know external card readers work.

---

### Post by silkstone on 2008-07-10
Does anything at all happen when you insert the card?

If you look at /var/log/kern.log it should record every time you insert a card, and tell you what it thinks it is.

When I tried a Sony Memory Stick before my last post here, this is what it wrote to the log...

```
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.951990] sd 4:0:0:2: [sde] 1947648 512-byte hardware sectors (997 MB)
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.954861] sd 4:0:0:2: [sde] Write Protect is off
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.954866] sd 4:0:0:2: [sde] Mode Sense: 03 00 00 00
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.954870] sd 4:0:0:2: [sde] Assuming drive cache: write through
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.962975] sd 4:0:0:2: [sde] 1947648 512-byte hardware sectors (997 MB)
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.965847] sd 4:0:0:2: [sde] Write Protect is off
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.965852] sd 4:0:0:2: [sde] Mode Sense: 03 00 00 00
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.965855] sd 4:0:0:2: [sde] Assuming drive cache: write through
Jul 10 15:16:26 silkstone-desktop2 kernel: [20947.965860]  sde: sde1
```

---

### Post by idrake88 on 2008-07-10
Nothing at all happens when the card is inserted, i checked the /var/log/kern.log and nothing changed when the card was insterted

---

### Post by silkstone on 2008-07-10
Does it work with other types of card (in other slots)?

---

### Post by idrake88 on 2008-07-10
it has worked with SD cards, unfortunately i do not have one with me anyone so i cannot give you the /var/log/kern.log or any other read outs

---

### Post by silkstone on 2008-07-10
If it works with cards in other slots, it could possibly be a hardware issue.

Don't take offence at this, but are you sure you're inserting the card the right way up. :) With some card readers you have to insert MS cards upside down!

---

### Post by idrake88 on 2008-07-10
There is just the one slot, both SD and memory stick go in the same slot. 

No offense taken, i actually tried it both ways in case i was doing it wrong, although i have had this laptop for 2 years, ran xp and vista, just switched to ubuntu, but yes i have used it before so i know the orientation lol.

---

### Post by sergiom99 on 2008-07-10
My Ricoh built-in 5-1 card reader only works with SD cards. I cannot make it work with MS cards. Its b/c the kernel drivers I told you.

But everything works OOB (i've been told) with USB multi-card readers.

---

### Post by idrake88 on 2008-07-10
Alrighty good to know thanks, i understood it was not written in the kernal i was just not sure if there was a code or something i could copy over to make it work. I am very new to ubuntu so i was unsure. Thank you for your answer

---

### Post by sergiom99 on 2008-07-10
no prob, glad it helped.

---

### Post by sirwhiteout on 2008-07-10
Same problem here.

I found instructions on [http://ubuntuforums.org/showthread.php?t=636867]("http://ubuntuforums.org/showthread.php?t=636867"), but still only SD cards work. I found the same behavior on every Ricoh card reader thread I got from the first two pages of Google. It seems this is a chronic problem.

---

### Post by silkstone on 2008-07-10
OK, well for some reason it seems that internal readers don't recognise Sony MS and external ones do. I've now tried two external readers and both work with MS.

That's a nuisance but I can recommend the Hama 35-in-1 reader that Amazon (UK) sell for £3.40. Sorry it's not an ideal fix but at least it will work.

---

### Post by sirwhiteout on 2008-07-10
Could there be a way to use the Windows driver, like with ndiswrapper?

---

