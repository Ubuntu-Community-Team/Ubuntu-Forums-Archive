---
title: "Recover from a clicking hard drive?"
date: 2014-02-02
forum: Hardware
---

### Post by gordon33 on 2014-02-02
Hello All

I want to learn a little and possibly recover information from the hard drive.

I have a Hard Drive model WD1600BEVT -60ZCT1 that is just clicking about as load as a mechanical watch.  The clicking is the only life noticed from this Hard Drive even when connected with a PC USB to IDE/SATA Converter Cable Set.  I want to learn a little and possibly recover from the hard drive.

I came across an 8 step video ( [http://www.youtube.com/watch?v=bZxEz6hRblM](http://www.youtube.com/watch?v=bZxEz6hRblM) ) that talked about replacing the Controller Board to fix the Hard Drive.  Step 5 talks about a Firmware Transfer = Controller Board BIOS swap needed on the replacement Controller Board.

What test can be made to narrow down the problem with the Hard Drive?
If it is the Hard Drive's Controller Board Is the  Firmware Transfer necessary?
Would it be a better idea to buy a complete Hard Drive rather then just a Controller Board?
Should the sound of Hard Drive's Disk spinning  be heard?

Symptoms from my Hard Drive
No Spin. "Clicking sound".(click of death) and wasn't dropped. 
Hard drive does not spin up. Just sound of a short, quiet tickling sound can be heard. 

Gordon33

---

### Post by Bashing-om on 2014-02-02
gordon33; Hi !

Quick way to isolate to the hard disk ->
Install the hard disk in another box and see what happens. (no intermediary components then )

If that disk is not spinning in the case.... ummm, best know what you are doing when you pop open that case !
Hard drives are an exact science.

[INDENT]just 1 way 
[INDENT][INDENT]to start skinning
[INDENT][INDENT][INDENT]that cat
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by CharlesA on 2014-02-02
A clicking hard drive usually means it has had a head crash, which means your data is gone unless you want to pay a ton to a data recovery specialist.

The DR company would  put the platters from the current drive in a new drive and see if they can recover your data. This is done in a clean room because any bit of dirt or dust can make things worse.

In any case, it is expensive, which is why it is a good idea to keep backups of any data you consider valuable.

Replacing the board on the bottom of the drive isn't going to help you access your data.

---

### Post by gordon33 on 2014-02-02
Hello Bashing-om, and  Charles A

Bashing-om  I did find the Hard drive was dead when I checked it out with the test cable (PC USB to IDE/SATA Converter Cable Set).

Charles A  I did not want to spend a lot of $$$ to recover any thing on the Hard Drive.  I figured if the Hard Drive is dead its a good one to learn on.   I DO have back ups of most of what is on the Hard Drive.  Its a chance to learn some thing.  Doesen't the board at the bottom have something to do with the disk spinning?  

If any one knows of a web site that teaches about hard drive recovery / repair Please let me know.

Gordon 33

---

### Post by CharlesA on 2014-02-02
> **gordon33 said:**
> 
Charles A  I did not want to spend a lot of $$$ to recover any thing on the Hard Drive.  I figured if the Hard Drive is dead its a good one to learn on.   I DO have back ups of most of what is on the Hard Drive.  Its a chance to learn some thing.  Doesen't the board at the bottom have something to do with the disk spinning?  

If any one knows of a web site that teaches about hard drive recovery / repair Please let me know.

Gordon 33

No, that's just the interface board.

See here:
[http://www.hardwaresecrets.com/article/177](http://www.hardwaresecrets.com/article/177)

It's a bit old (2005), but it should give you a general idea of what each part of the drive does.

---

### Post by tgalati4 on 2014-02-02
If the platter is stuck due to a sticky bearing, you can sometime get the platters spinning by holding the drive in your hand and twisting rapidly with your wrist.  Once the drive is spinning, then you have a chance of recovery.  Otherwise the magnets make good refrigerator magnets.  The control board has the motor drive circuitry, but 90% of the platter spin failures are due to a sticky bearing.  Changing the board won't help with that.

If you open the drive and you gently get the platters to spin and reassemble, then you might have a chance.  It's interesting to watch a disk drive in action.

---

### Post by varunendra on 2014-02-02
> **gordon33 said:**
> If it is the Hard Drive's Controller Board Is the  Firmware Transfer necessary?
Absolutely necessary. Even if you get the board from the same lot of hard disks, the BIOS would most probably be different. It is not done intentionally, just the way it happens.

The circuit board does have the motor control IC as well, which is the most vulnerable IC since a lot of current passes through it making it really hot. In that case, replacing the board may solve the spinning problem too.

All of this is in addition to what has already been said, including the suggestion about refrigerator magnets. :P

---

### Post by gordon33 on 2014-02-02
Hello Charles A, tgalati4, and Varundra

Thank you for all the replys.  

[http://www.hardwaresecrets.com/article/177](http://www.hardwaresecrets.com/article/177) porvided a lot of information.

No luck with the twist to get things spinning.  

Unless there is a way to get the Firmware transfered my self will I have to find a supplyer who takes care of that for a new Hard Drive or Controller Board.  I have had the hard drive pluged in for 10 to 20 minits and it is still cold.  Does that mean the Motor Controler IC is not doing its thing?

Gordon33

---

### Post by varunendra on 2014-02-03
> **gordon33 said:**
> Unless there is a way to get the Firmware transfered my self will I have to find a supplyer who takes care of that for a new Hard Drive or Controller Board.
In most SATA drives, it is an 8-pin IC (about 3x4 mm size, with 4 pins on one side, four on the opposite). I didn't follow the link, but replacing the firmware means replacing this chip. Without a good quality soldering iron/paste and some good experience with soldering kit, it is almost impossible for a first timer *(you will either damage the IC by overheating it, or damage the print which it is sold to)*. I know because I have done that, quite painfully, but somehow successfully *(even succeeded in getting a replacement under warranty after recovering the data on the drive, the guys doing initial checking before accepting the drive couldn't realize that the chip was replaced ;)).*

> I have had the hard drive pluged in for 10 to 20 minits and it is still cold.  Does that mean the Motor Controler IC is not doing its thing?
It won't heat up if it has nothing to do. If the drive fails to initialize for 'Any' reason, there IS nothing to do.

---

### Post by gordon33 on 2014-02-03
Hello varunendra

Thank you for the reply.  I might as well take this Hard drive apart and see what happens.  If nothing else i will have new refrigerator magnets.

Gordon33

---

### Post by varunendra on 2014-02-04
> **gordon33 said:**
> I might as well take this Hard drive apart and see what happens.  If nothing else i will have new refrigerator magnets.

My [s]deepest cond..[/s] I mean.. best wishes, Good luck ! :P

Do not forget to post screenshots for us. :D

---

### Post by andyfied on 2014-02-04
Hello

Your heads are damaged. Don't worry about the PCB too much.  They only thing you will get out of this drive is the learning  experience so I hope you enjoy it!

WRT the comment about experts  taking the platters out and putting them in a new shell, it's probably not  necessary. If the platters are not spinning then the head is more likely to be stuck to them than a seized motor, but it could be possible. Seized motors tend to beep (but not always).

I cannot recommend you open it if you want your data back, but if you do then try to find some videos on releasing heads, don't just yank it off.

Good luck :)

---

### Post by oldfred on 2014-02-04
Did you try freezer?
 The old freezer trick to get drive cold and see if it will start. Or a tap with a rubber hammer. Both are to resolve the issue where the lubrication has dried up or failed and drive is sticking and motor is not strong enough to start it. If it gets going then it may start once.

I saw one user years ago that purchased another drive of same type and removed platters from old drive to install in new drive. Without clean room new drive will not last long, and it was just to get data from old drive.
But new drives have data tracks so precisely written, close together that each drive is software tuned to precise alignment, so just moving platter may not work without precise software alignment that only the professionals have.

---

