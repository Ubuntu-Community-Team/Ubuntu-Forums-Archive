---
title: "Is my hdd failing?"
date: 2011-11-16
forum: Hardware
---

### Post by Sylos on 2011-11-16
Hello all.

I recently bought a Dell Inspiron Laptop from ebay second hand - no os installed but with a 500g HDD. Having installed ubuntu on it I noticed a high pitched whinning noise coming from it when the OS has booted - doesnt do it when just in the BIOS. I began to suspect the HDD as it had taken around 7 hours to wipe using DBAN and had returned around 21 errors. This in mind I decided to try and run some diagnostics.

I installed Smartmontools and run a quick self test on it and the results came back saying I had 90% read errors and stated that the drive life is 505 hours.

I have read some posts in forums saying smart means nothing really and not to worry but I cant help feeling that I am on the verge of a failure. 

im just wondering if someone with more experience could offer some advice. 

Thanks

---

### Post by dandnsmith on 2011-11-16
With those symptoms and results, I'd get any valued data off quickly, and indulge in a new HDD. Figures like drive life are often guesswork, based on some evidence, but lacking a real life experience - individual cases can do almost anything.
It might be work looking to see what the dell warranty says about the HDD - no use going to the manufacturer (as I found out with a dell desktop recently) as the components are bought in under a deal which leaves the warranty period to the PC manufacturer/seller.

---

### Post by TedinOz on 2011-11-16
Someone pointed me to this a while ago. Even though Dell isn't featured you may get a clue from other machine sounds. I don't know if it's of any value but may be of interest to you.

[http://datacent.com/hard_drive_sounds.php](http://datacent.com/hard_drive_sounds.php)

Seems a back-up is imperative in any event.

Cheers :)

---

### Post by Sylos on 2011-11-17
Thanks for the replies people.

I have only just bought this laptop so all there is on it is the OS. Its a christamas present for my girlfriend  (who never backs info up) hence Im worried about failure at a future date once she starts using it. I shall try some more smart tests but  it appears the HDD is likely knackered from the evidence so far.

Pretty annoying really - a good deal is looking less and lees good. And having looked at the technical details it turns out I have to take it apart and damn near build it from scratch again to fit a new HDD. Fun!

I've never done this with a laptop before. The HDD has an interposer that fits onto it. I assume these fit onto any sata drive and make it fit wahtever odd form the motherboard wants. Is that right? I dont wanna make another mistaken purchase. :(

Cheers

---

### Post by Grenage on 2011-11-17
It's probably a 2.5" SATA drive, but without seeing the drive or the model, we can't be sure.  I'm surprised that you have to delve too deeply; every laptop I've replaced the drive in has been accessible via a hatch on the base.

---

### Post by |{urse on 2011-11-17
yeah if dban says its dying then it is, i have a "anything over 4 errors is trash" policy lol sorry to hear that but glad to see a dban user ^^

---

### Post by Sylos on 2011-11-17
UPDATE:

Just installed GSmartControl and tried using it to do a full extended test. It said it would take 2 hours 38 min then finished in 5 sec saying read failure. Am I to assume that this also indicates death or a failure of SMART?


As far as delving deeply is concerned - yeah I knew DELL are bad for making upgrades nearly impossible to the average user - I got drawn in by a nice looking price.

Are there any other linux tools I can use to verify that the disk is bad? (clutches at straws)

---

### Post by Sylos on 2011-11-17
FURTHER UPDATE:

Any attempt to test using GSmart results in only 10% completed with read errors and a response of 500 ish hours til death. Interestingly the health status is still PASSED on the main screen though - rather odd!

Its an odd feeling to be told how many hours til anticipated cessation of life. I hope the HDD cant see the result - poor thing would be really panicked. ;)

Below is the log output of the last few test attempts

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%       507         14673955
# 2  Short offline       Completed: read failure       90%       507         14673955
# 3  Extended offline    Completed: read failure       90%       506         14673955
# 4  Extended offline    Completed: read failure       90%       506         14673955
# 5  Extended offline    Completed: read failure       90%       506         14673955
# 6  Short offline       Completed: read failure       90%       506         14673952
# 7  Extended offline    Completed: read failure       90%       506         14673955
# 8  Extended offline    Completed: read failure       90%       506         14673955
# 9  Short offline       Completed: read failure       90%       505         14673955
#10  Extended offline    Completed: read failure       90%       505         14673955
#11  Extended offline    Completed: read failure       90%       505         14673952
#12  Extended offline    Completed: read failure       90%       505         14673955
#13  Short offline       Completed: read failure       90%       505         14673955
#14  Short offline       Completed: read failure       90%       505         14673952
#15  Short offline       Completed: read failure       90%       503         14673980
#16  Short offline       Completed without error       00%         0         -


```

Seems fairly consistent in terms of where the first errors are. Not sure if that means anything really. Shame it wont continue the test.

---

### Post by IcarusR on 2011-11-17
> And having looked at the technical details it turns out I have to take it apart and damn near build it from scratch again to fit a new HDD. Fun!

Thats strange, all modern laptops & netbooks I've seen are easy to replace HDD, normally under a cover held on with a couple of screws.

Exactly what model is it ?

You could try talking to the ebay seller. Was it described accurately ?

---

### Post by Sylos on 2011-11-17
Hello icarus. The model is n5010. I checked on dells website and it shows that the RAM, Keyboard and hand rest all have to be removed to get access - a total pain in the ***.

The unit was being sold as refurbished so I am going to contact the seller. what i dont want is to end having to send the whole thing back to them and them not fix it. From initial impression it looks like they just take it back and refund - not repair. That would be bad for me as it was sold sans power adapter and battery which I have bought afterwards. cant see them being useful without the laptop.

Gonna download the ultimate boot cd and run some other checks off that hopefully first. Following that it will be time to do the returns dance.

Cheers

---

### Post by |{urse on 2011-11-17
haha, I always love it when it's not me (for once) that has to disassemble a whole laptop just to add ram or replace a hard drive or something. just a bit of schadenfreude, I agree it's ridiculous to have to go through all that.

A bit of advice, don't do it unless you have found the appropriate disassembly manual on google for your model. Also make sure to keep every screw you remove sitting on a white sheet of paper or something so you can categorize them and ultimately remember where the heck they go when you re-assemble..

---

### Post by Sylos on 2011-11-18
thanks for the advice. I have found a manual and a helpful you tube vid for it. and i forgot to mention the optical drive has to come out too. :D

still, first step is the ebay seller. Maybe they will do the dirty work for me (crosses fingers).

---

### Post by Sylos on 2011-11-24
Just to get closure for the thread heres how the story ends....

Seller takes back laptop - acknowledges drive faulty - decides not gonna replace it under warranty - refunds money without informing me of this intent.

I now have separately purchased accessories for a laptop I dont own. I feel a formal complaint comming on.....

---

