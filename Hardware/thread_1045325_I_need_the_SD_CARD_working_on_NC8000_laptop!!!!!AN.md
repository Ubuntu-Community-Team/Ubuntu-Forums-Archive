---
title: "I need the SD CARD working on NC8000 laptop!!!!!ANYONE??"
date: 2009-01-20
forum: Hardware
---

### Post by DocTorQue on 2009-01-20
Please,

Folks...what is the matter with you all...some kind a linux support...

I have HP Compaq NC8000 Laptop.The SD-CARD reader dont work...i have tried something to get it work and i screw up the intire system...had to reinstall ubuntu (8.10)

Now im not touching it unless someone has a solution that works 100%.

AND im not a linux programer to do it by foot. It would be nice that someone gives me a good tutorial for beginner.

Thank you...

---

### Post by stchman on 2009-01-20
> **DocTorQue said:**
> Please,

Folks...what is the matter with you all...some kind a linux support...

I have HP Compaq NC8000 Laptop.The SD-CARD reader dont work...i have tried something to get it work and i screw up the intire system...had to reinstall ubuntu (8.10)

Now im not touching it unless someone has a solution that works 100%.

AND im not a linux programer to do it by foot. It would be nice that someone gives me a good tutorial for beginner.

Thank you...

Does this laptop have an SD/xD card slot?  Are you using just SD cards or are you trying to read xD cards?  I know that most laptop Ubuntu's kernel does not support xD cards used in the multi slots.

There is always the USB to SD/xD card readers.  They can be had on ebay for under $8 and they work with all kinds of cards.

Give us an lspci output in this thread.

---

### Post by russu52 on 2009-01-20
hello and thanks for this thread. i have an acer aspire 5720 running on ubuntu 8.10. the multi card slot reads sdhc, but doesn't recognise the xd card.

---

### Post by timcredible on 2009-01-20
well, since you asked so nice......

---

### Post by mtbsoft on 2009-01-20
> **DocTorQue said:**
> Folks...what is the matter with you all...some kind a linux support...
With an attitude like that, you're going to make loads of friends here!  Please remember that all the other forum users are volunteers, giving up their own time to help both the grateful and the ungrateful.

Might I respectfully suggest you read [this]("http://linux.oneandoneis2.org/LNW.htm") article, item 3a seems rather appropriate...

---

### Post by sedawk on 2009-01-20
Start your computer without the SD card.
Clear the kernel message buffer using "sudo dmesg -c" on command line.
Now insert the SD card and wait 10 seconds.
Post the (new) output of "dmesg" here.

Normally you should see that the SD card is mapped to some
SCSI device files, e.g. to /dev/sdc and /dev/sdc1.
It should also mount automatically at /media/<some_name>.

---

### Post by Lutherian on 2009-04-12
Hi Sedawk

Whilst other's might chastise you for using exclamation marks and the "manner in which you ask the question", I understand that you are simply expressing your frustration - so let it out, you're not alone :)

What the heck, I'll have a go at it as well

YES - MY DAMN SD CARD DOESN'T WORK EITHER !!!!!!! I'M AS MAD AS HELL!!!
{Kicking the trash can now}

phew, I feel better already.

Also tried chmods, etc, etc - swapped SD cards, tested on different OS.
(Works fine on Windows BTW) Bottom line is right now ubuntu doesn't let you write to SD card sometimes.

I've been search this topic for a while now (2 weeks), and I don't seem to be getting/finding any staight answers - just the same questions.

One guy even posted on his blog that he used high pressure air to clean out the contacts! go figure.
Hang in there - If I find something more meaningful than 

"type dsadad -sd d- -c -p -blah -blah less>>output-diagnostic-test-file-email-to-forum.txt"

I'll let you know - if you find something, let me know.

Good luck.

---

### Post by Lutherian on 2009-04-12
Oops! LOL - Didn't scroll all the way to top, sorry, I should be directing this to DocTorQue - not SedAwk. (sigh... brain upgrades?)

---

