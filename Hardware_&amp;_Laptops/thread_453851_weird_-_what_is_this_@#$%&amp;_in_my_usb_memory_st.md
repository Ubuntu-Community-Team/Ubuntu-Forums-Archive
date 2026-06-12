---
title: "weird - what is this @#$%&amp; in my usb memory stick?"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by Korrontean on 2007-05-24
I've purchased a 2GB Kingston memory stick today. When I plugged it to my laptop, this is what apparently is inside. See screenshot attached.

When plugged to a Windows computer, there's nothing. The memory stick seems to be empty.

Anyone has any idea???

I'm doing this just for curiousity ;), I thought it was a shame to format without knowing a little more about it.

:D:D:D

---

### Post by Korrontean on 2007-05-24
As no one answered yet, I've created a poll. :)

:KSI WANT TO BELIEVE:KS

---

### Post by psusi on 2007-05-24
It looks like the stick has two partitions on it, one named USB DISK and the other KINGSTON.  The KINGSTON one probably is marked as hidden so windows doesn't show it, but linux does, and because your system is set up to use a foreign language, it is probably misinterpreting the names of the files as special characters instead of plain ASCII.  

This is purely a guess though.  What does sudo fdisk -l show?

---

### Post by Korrontean on 2007-05-24
Thank you for the guess, Psusi!

1) This is the output:

Disk /dev/sdb: 2034 MB, 2034237440 bytes
26 heads, 25 sectors/track, 6112 cylinders
Units = cylinders of 650 * 512 = 332800 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6113     1986436    6  FAT16

2) My system is in English.

3) The "USB drive" was another memory stick plugged to my laptop. Mine has "KINGSTON" as its name.

Why should there be any files in my memory stick if I bought it today and it comes from a sealed box??? :-k:-k:-k

---

### Post by Korrontean on 2007-05-24
By the way, when I click on properties, it says:

> Contents: 9 items, totalling 6.6 GB

Someone must know.............................................

:KSTHE TRUTH IS OUT THERE:KS

---

### Post by psusi on 2007-05-24
Weird.... try repairing it... sudo fsck -t vfat /dev/sdb1

---

### Post by reacocard on 2007-05-24
Is this one of those U3 drives? If so, that's what you're seeing: the U3 partition.

---

### Post by ryanVickers on 2007-05-24
Oh dear, that is quite terrifying :)

I think it may be a language problem, or, hmm.  very strange.  Just format it as a linux file system and file a complaint saying it defies thel aws of technology and physics (all the files add up to a bit too much to fit in 2Gb :))

---

### Post by aidanr on 2007-05-24
[fake maybe?]("http://reviews.ebay.co.uk/Beware-of-FAKE-1GB-2GB-4GB-8GB-USB-Flash-Drives-on-eBay_W0QQugidZ10000000000953346")

> It has also been reported that many strange files/folders will appear and you cannot delete them.

---

### Post by deadlydeathcone on 2007-05-24
What a horrible poll, it's obviously made of magic. I mean, what's there to discuss?

I suggest plugging it into as many Windows PCs as you can find so that they, too, can be magical. :KS

---

### Post by siglost on 2007-05-25
Poll is great.  Matrix wins in my book 3-4.

Probably garbage that was posted and not erased in testing.  Might have been:
Garbage left over from the first user, referb.  Might have been:
Garbage left over from defective return user.  Might have been:
You bought a defective item resold by the manufacturer.  Might have been:
Gamma inpressions left by alien life trying to fudge our solar reception.  Might have been:
Magnetic interference caused by the 1000 monkeys next door simultaneously hitting the X key on their IBM Selectrix Typewriters.  Might have been:
Someone who hates you running their soldering iron through a USB drive "voodoo drive".  Might have been:
We are all responding to some residual thought in the universe made up by your mind.  Might have been:
The alcohol.  Might have been:
You are all responding to some residual thought in my made up universe somewhere in my synaptic membrane.  Might have been:
The Knights Templar current day map to the holy grail.  Might have been:
E.T.'s home phone number.  Might have been:
You forgot that you opened it, put shhtufff on it, then passed out and found it the next day.  Might have been:
Kingstons complete intellectual property golden chest.  Might have been:
A lepricons map to the end of the rainbow.  Might have been:
God telling you the day you were going to die.  BUT IS IN FACT:

The KEYS TO ZION!  You moron!  Put it away before an agent greps this shhisastic!!!  Do you realize you are about to be usurped like a villiage idiot, and the whole theme of the Matrix has to start all over?!  I for one am tired of sleeping in a bathtub full of embriotic fluid, trying to scratch that node on the back of my neck in the middle of blissful sleep!  Jesus de Mayo!  Do you want Bill Gates to be like Emperor of the World?  Do you realize how popular he is in this version?!  Can you see little girls running around with windose on their toenails singing, "Windose, Windose, Win.ClipArt, How will Bill Gates win thy Hearts".  GET IT OFF THE NET BOY!

-d

---

### Post by swudee on 2007-05-25
Hmmm  I wonder what it would look like if you had support for Korean language on your system. It looks what I get in Thunderbird when I get E-mail in Thai. I haven't managed to get Thunderbird to auto detect Thai.

---

### Post by Korrontean on 2007-05-25
Thanks for all the feedback! =D>Even if the mistery is not solved yet.

1) reacocard: it's not a U3. It's a regular Kingston DataTraveler 2GB.

2) ryanVickers: sure it goes against laws of physics... it counts up to 6.6 GB. :-s

3) aidanr: I don't think it's a fake... it came in an original Kingston package and I bought it from a reliable store.

4) deadlydeathcone: I should have added "magic" to the answers in the poll. sorry :roll:

5) siglots: it's scary. I tried to see if there was a pattern on the DATES the files were modified last. I saw

[INDENT]a) the date of the battle of Iwo-Jima in February 16,1945

b) December 16, 1966. The date of the approval (by the United Nations) of the International Covenant on Economic, Social and Cultural Rights and the International Covenant on Civil and Political Rights, two of the most important Human Rights documents. By the way, Human Rights is my professional field.

c) Nothing very interesting happened in January 14, 1996. Well, Sampaio was appointed president of Portugal.

d) I haven't found any prophecy/omen for the date January 18, 2020. Maybe it is the date of my death, maybe it's the date when these weird files will get active and DESTROY/SAVE the world. Who knows.[/INDENT]
I'm thinking of trying to delete the files, or formatting the USB drive. I'm not sure yet... maybe I could ask money for them to be saved, like this son of a ***** that was asking for money not to kill and eat his pet rabbit.

Thanks again for your posts: clever, clean and funny =D>=D>=D>

---

### Post by Korrontean on 2007-05-25
Swudee: I'm installing Korean language support. I'll let you know the result ;)

---

### Post by Enverex on 2007-05-25
Just open GParted, delete the partitions, make a new single partiton and format it. It's probably never been formatted properly or with something dodgy.

---

### Post by ryanVickers on 2007-05-25
just noticed something else, it's mounted twice; once as KINGSTON, once as USB Drive or something.  just one more reason for it to probably be defective.

Maybe if you stick it in lots of windows pc's, they'll get infected and burst into flames :p!

---

### Post by Korrontean on 2007-08-08
UPDATE: Had I seen Transformes (the movie) a few months ago, I'd have known... it was clearly a message from the robots in Mars.:lolflag:

---

