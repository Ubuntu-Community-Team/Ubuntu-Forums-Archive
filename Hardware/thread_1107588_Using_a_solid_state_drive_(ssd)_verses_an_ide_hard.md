---
title: "Using a solid state drive (ssd) verses an ide hard drive (hdd)"
date: 2009-03-26
forum: Hardware
---

### Post by Snow Keld on 2009-03-26
I'm looking to buy the Ace aspire one.

i know solid state drives are faster, but i also know about write times and life span being low on solid state drive.

i've found info on how to decrease write times to expand the life of the ssd, this is not the information i'm looking for, although when i found out about the write times and life span issues it was saddening because i was thinking that a swap file on a ssd would be sweet cuz it would be fast :(



ok, my real question here is about performance, after i dont have a swap file or put the swap somewhere else like an SD card (if thats possible). using an ext 2 filesystem, have the hard drive mount with 'noatime' option, temp files to ram and have them save to the ssd at shutdown, and whatever else i find to lessen the number or writes.

the technical /home partition would be on the SD card, and i would be putting all major files (music and movies) on an external hard drive.



after i get the ssd drive to this point, how does it compare to a regular hard drive in performance?

i'm asking about this because with it being more cost effective for me to buy the aspire version with a regular hard drive, because i wont have to buy an external drive.

this is more about what peoples opinions are, and other viewpoints, esp about the SD card and the fact that (i'm pretty sure) the ssd in the aspire is replaceable.



am i better off buying the regular version or the ssd version?

how noticeable is the performance difference?


_________

i've gotten conflicting viewpoints on this so far, the ssd was highly praised by a friend (who knows nothing of linux) for its speed and reliability, but never mentioned the lifespan problem, today i got a conflicting view from another friend who taught me a great deal about linux, and different disto's mentioned the lifespan problem and that i could find many issues with the ssd, he can be very close minded from new ideas though, he's very stuck in his way of doing things, especially with software, using primarily knoppix and bashing graphical interfaces saying that the command line is 100x better, which might be true, but still... idk, i know hes very smart and when i says that i decided to research it further than i already have, i found how to reduce write times but i want the opinion of people who have already put ubuntu on solid state drives and if the performance was considerably better than an ide or if i should just go for an ide hard drive.


oh, and i small Q, how much of a difference does it make on battery life (say its rated for 2.5h for an ide, how much of an improvement to a ssd?

---

### Post by kerry_s on 2009-03-26
i went for the ssd, i ordered the dell mini 9, can't wait to get it. :P

i didn't get a regular hard drive, cause i didn't want the noise, the extra heat and i have plenty of external drives already.
8 gigs is plenty enough for me, i always use a custom install anyways, my current install hasn't even reached 2 gigs yet.

---

### Post by Snow Keld on 2009-03-26
thank you for the input.
i have up lots of space but i'll be putting my media files elsewhere and i wont eat up more than 6 gigs with OS and programs.





has anyone already messed with this yet?

or the eee pc, cuz that comes with a solid state as well, although i know theres is not replaceable.

---

### Post by Snow Keld on 2009-03-28
not be pushy but i would like some opinions from people who have encountered this already.


i came to ask here cuz i trust you guys when it comes to my computer.

if you would please just give me your thoughts on performance difference between the diff types of hard drives.. and if you think its worth it :D

---

### Post by pewterbot9 on 2009-03-30
SSD's are very appealing to geeks and techs, because they are bleeding edge. But in doing some research, I learned that the standard hard drives in netbooks are highly durable. There is also the questionable quality of these SD cards, especially the affordable ones!

IMO, SSD's are not yet quite ready to be used as one's main hard drives. Assuming you'll want to upgrade a year or two after your present netbook purchase, I'd say by the time you're ready to upgrade, the SSD's will also be up to snuff.

But for now, please do yourself a big favor, and go the standard hard drive way. My Asus netbook runs very quietly, drive-wise and fan-wise...don't even notice 'em.

The Acer Aspire 1 is a fine machine, but FYI: among all netbooks, the Asus runs coolest re. drive, fan, and wifi. Most durable, most reliable. Great keyboard BTW.

---

### Post by bobwyajnr on 2009-03-30
This by a long way the best article on the state of SSD performance at present:
[http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=1]("The SSD Anthology: Understanding SSDs and New Drives from OCZ")

You will see if you have the money for the best (Intel X-M or X-E) it's a no-brainer. The OCZ vertex offers a budget MLC alternative (with it's improved firmware) - hardware comptability is more of an issue than with the Intel drives. Other Flash MLC SSDs have very bad random write stuttering problems - so don't touch!!

Bob

---

### Post by happyhamster on 2009-03-30
Reason I have been using an ssd for a short while now (root partition) is the exact same article bobwyajnr linked to. It's a 30GB OCZ Vertex ssd, and I must say that it performs splendidly. It decreased boot times (Grub menu to GDM login screen) with ~10 seconds, offers much more "snappy" behaviour of the desktop as a whole (GIMP, Open Office Writer starting in a mere second), and the pc is eerily quiet all of a sudden.

But you get used to that after a few days... :)

So, what I mean to say is that the improvements are great but not necessarily earth-shattering, because modern systems are very fast already. If you have some applications that are bottle-necked by random-writes/reads, then you will notice a *major* improvement though.

So, YMMV. (You Mileage May Vary.) I assume *going back* to a regular drive will be much more noticeable though.

On the subject of duration: the predicted lifetime of a current ssd is already on par with (or exceeds) regular drives, when some care is taken to randomize writes and not keep the drive almost filled up.

---

### Post by slyde on 2009-03-31
I think youd be better in this case with the hdd, mostly due to price and storage space, I have an external expressvcard ssd, I dont believe its the same thing but I did notice that its faster than usb, I'm using it to dual boot ubuntu on an ideapad s10 along side the factory install of win xp home and ubuntu seems faster on here than windows but I only have 8Gb of space, Personally Id go for the normal hd, but then again I guess it depends on the use of the laptop. I suppose solid state would be better for someone who moves around a lot but then again I do and have never had any issues with any of the laptops I've ever owned.

---

### Post by thefirstone on 2009-03-31
I haven't done research as to speed but I have a Asus 1000HA with 160gb hdd and I installed and run Ubuntu from a 8gb SD Card. The Hdd serves as storage and I also boot to WinXP which is installed on the hdd. Ubuntu requires a small partition for swap so I assigned that to the hdd as well. Asus 1000HA allows you to boot from a SD card as if it were a hard drive. Everything runs fine, boot time is fast, silent and plenty of space for a nice install. I installed another version of Ubuntu on another 8gb SD card so I just swap cards to use the other LinuxOS.

---

### Post by bobwyajnr on 2009-03-31
> **thefirstone said:**
> I haven't done research as to speed but I have a Asus 1000HA with 160gb hdd and I installed and run Ubuntu from a 8gb SD Card. The Hdd serves as storage and I also boot to WinXP which is installed on the hdd. Ubuntu requires a small partition for swap so I assigned that to the hdd as well. ...

You could mount the /var path on a seperate partition on the regular harddisk as this folder is used to store regularly updated files (log files, etc.) Random rewrites to small files is not so good for regular flash cards...

I think there are also kernel switches (??) to indicate that Linux is stored on a medium that should be rewritten as little as possible (log files, etc. are cached in RAM) e.g. NAND flash.

Bob

---

### Post by Snow Keld on 2009-03-31
thank you all for your input.

i think i'm leaning toward the ssd right now, simply because it is that much faster, and if i do need to replace it then i can, replacements are not overly expensive given that the first one wont burn out for over a year (which it should last at least 3 years anyway).

i'd probably upgrade for the extra space long before i ever even had problems with the original.




@ thefirstone, you said you put ubuntu on an SD card? when you did that was the SD card in the laptop and you just did a normal CD install and it recognized the SD card was there and allowed you to partition it?
if it is that easy then that would be a bit more of a reason to get the ssd version. (just make the separate /home partition on the SD card)




and after thinking on it for awhile, i think the modding to ubuntu to not kill a ssd as fast is a bit over the top, i'd i just use an ext2 filesystem and no swap on the ssd then i think it would be fine, considering that i'd probably buy a new one before it dies anyway.




oh, and one more question, does ubuntu have any problems with using external hard drives? and would it make any sense to use one for my movie and music files?

---

### Post by thefirstone on 2009-03-31
The reason I got the hdd was for the space,160gb.I want to be able to carry a lot of music and video around. I plan on upgrading to a 500gb hdd soon. I have XP in th main partition (25gb) and the rest of the hard drive is mainly a large partition for data storage. At first I was going to make another partition on the hdd for Ubuntu as I do with most my other PCs but I noticed that the BIOS in my eeepc alowed me to boot from a SD Card. I installed Ubuntu from a USB Pen Drive and during the install I selected the SD Card as the drive for root(\).The SD Card must be inserted in the card reader before starting up the PC. I didn't want to take up space on the SD Card for swap partition so I first made a small partition on the hdd and then assigned it for swap during the Ubuntu install. I also didn't want to partition the SD Card into two partitions(I,ve never tried that).When I want to boot from the SD Card I enter BIOS and assign the SD Card as primary boot drive. To boot from Windows XP I assign the hdd as primary boot drive. 
 External drives have worked fine with Ubuntu for me except for Seagate FreeAgent which have a feature that disconnects the drive during idle and wasn't friendly with Ubuntu.There's a workaround for it but I recommend avoiding Seagate FreeAgent. 
Hope the info is useful. Have fun.

---

### Post by RockDoctor on 2009-04-02
> **thefirstone said:**
> ...At first I was going to make another partition on the hdd for Ubuntu as I do with most my other PCs but I noticed that the BIOS in my eeepc alowed me to boot from a SD Card....
If only the old Acer Aspire Ones could be made do this...

---

