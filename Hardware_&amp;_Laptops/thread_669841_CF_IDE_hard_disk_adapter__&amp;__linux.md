---
title: "CF IDE hard disk adapter  &amp;  linux"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by morepowerr on 2008-01-16
I have used  Toshiba Satellite Laptop i picked up for a 400 bucks from friend how get a newer laptop.  I have it running gutsy on the factory hard disk.  

 What I would like to do is replace the  factory hard disk with a  Dual CF IDE hard disk adapter. Link = [http://www.shopaddonics.com/itemdesc.asp?ic=AD44MIDE2CF](http://www.shopaddonics.com/itemdesc.asp?ic=AD44MIDE2CF) . And 1 or 2  A-DATA 16GB Compact Flash  Card. Link = [http://www.newegg.com/Product/Product.aspx?Item=N82E16820211170](http://www.newegg.com/Product/Product.aspx?Item=N82E16820211170) .

  But 2 thing have me worrying.

  1. Will linux be able to see all 16gb of the CF card. 
  2. Has any one tried this before.  Can linux spalit it up in to 3 drives like on a normal hard disk. 
      ( Aka root,/home & swap)

---

### Post by cryptocoryne on 2008-01-19
YMMV on x86 hardware, but I tried using a 16GB CF card in a CF to IDE adaptor in an old Lombard (PPC G3) powerbook and it was very flakey.  Most linux distributions, including Ubuntu,  would not even install and when I finally got Debian Etch installed, things seemed fine until the system froze with all sorts of I/O errors in the logs. Usually things worked for a day or two and then went downhill rapidly when "Lost Interrupt" errors started appearing in the logs.

Panther ran w/o errors and freezing using the same card, but was a bit slow.  I tested the adaptor using several different brands of CF card and one microdrive and got the same result every time: linux froze, Panther worked but disk I/O was slow.

Googling a lot produced some voodoo boot parameters(noapic, ide=nodma, etc) that people claimed would help, but nothing worked for me. 

This problem may be specific to PPC linux. No one seems to care about it and I'm not smart enough to write/debug IDE modules myself. So I gave up and went back to using the old, noisy 10GB hard disk.

---

### Post by mikesfx on 2008-01-22
I'm actually experimenting with booting linux off of a CF card now.

I'm using the AD44MIDE2CF, the Addonics 2 CF card adapter. It seems to work but I am having some issues either with the card I chose (Sandisk Extreme III 2GB) or the bios of my Dell latitude L400.

Basically I was able to install Ubuntu 7.10 Server in command-line only mode to the CF card but it would not boot, giving me a Grub "stage 1.5read error".

What I did then was install another, older CF card (a Lexar 16MB) into the first slot of the Addonics adapter. Before putting it back into my laptop I installed "Super Grub Disk" to the Lexar and then put it into the laptop with the Lexar as CF1 and the Sandisk as CF2.

I was only able to intermittently boot the linux install on the Sandisk, and in order to do so I had to use the Super Grub Disk's "Live Swap" feature, as the Dell's BIOS wasn't assigning the Sandisk the right drive number. It was giving the SANDISK hd0,0 /dev/sda but grub had been installed with the device map pointing to HD1,0 /dev/sdb. By using Easy Live Swap on SGD, I was able to point grub in the right direction and boot off of the Sandisk.

I used it fine during one session and then the next session the Sandisk wouldn't but up again. It was being detected intermittently and sometimes trying to access it would cause the laptop to reboot. I am thinking that maybe the Sandisk Extreme III isn't compatible with either the Addonics board or perhaps it is the wrong type of card, as I read somewhere that the CF card can either emulate a removable device or a fixed disk depending on the model of the card.

But as for the questions you asked above:

1) Linux should be able to see the 16GB, as it treats a CF card like a normal hard drive (especially through the adaptor), but as a side note I wouldn't waste my money on a HUGE CF card like that until you've tried on a smaller one and seen if it works. I've had to reinstall 3 times on the CF card and these things have limited amount of times you can write to them. Try a 4GB card of similar make and model to the one you are looking at so you can make your mistakes on the test one rather than the larger more expensive CF card so you can save money. (That's just my opinion)

2) As you can probably see from my long story I have tried this and it *can* work but I'm not sure how reliably. Again, my test results seem to be marred by the intermittent issues I am having. You can certainly repartition the CF card like a normal disk. To minimize writes to the CF card to make it last longer, some partitions should either be mounted on other media (like another, less expensive CF than the one you are using for your root partition), hence the good choice in buying the addonics with 2 CF slots.

Good luck and I hope this info helps you in the future.

-Mike

EDIT #1)

I just looked again at the 16GB CF card you wanted to use, and I think it may be able to work better than the card I had bought, the Extreme III. This is because A) someone is already using it w/ Puppy Linux as stated by one reviewer, and B) It seems to be a little bit slower and that may increase compatibility. 

If you do go ahead with this, I'd be interested to see how it works out for you.

---

