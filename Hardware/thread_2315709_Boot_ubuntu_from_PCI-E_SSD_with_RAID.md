---
title: "Boot ubuntu from PCI-E SSD with RAID"
date: 2016-03-01
forum: Hardware
---

### Post by harrispartyof3 on 2016-03-01
I have a very complex proposal for my ubuntu server setup. I'm using a motherboard with eight SATA ports, a normal PCI-E x16 slot (currently occupied by a graphics card so the rig will boot) and two PCI-E x 1 slots. The case I'm using has eight HDD mounting locations. The intention is to install all eight HDD with RAID 6 (one HDD as a hot spare). Now that's all fine and dandy but with the os on the RAID array the HDD will never go into standby due to disk access and such for normal log operations. My thought was to put the os on two separate drives with RAID 1 (it would be silly to have the media safely RAIDed and the os vulnerable) but with all eight HDD slots populated there wont be any more SATA ports for the two OS drives. So my solution was to use two PCI-E to mSATA adapter and have the two PCI-E x 1 slots populated with these in RAID 1 to hold the os. I'm not concerned with any possible performance boost from using PCI-E for storage, simply the intention of keeping the HDD's in standby until media needs to be accessed since seven HDD's all furiously reading data uses a decent amount of energy.  

 
 
 So now for the tricky bit: how likely is it that I will be able to boot from PCI-E cards? And if that is even possible will I be able to have two separate cards in RAID 1?
 
 
 I poked around and couldn't find any insight on the PCI boot much less PCI RAID. Thanks in advance for any help.

---

### Post by houstonbofh on 2016-03-02
If you get a well supported card that just presents as 2 SATA ports, you should be able to boot from it, and use Linux for mirroring.  (Also use Linux for the RAID, not the fakeRAID on the motherboard.)  Hardware RAID is asking for trouble.

Another option (depending on what you need the server for) is just installing nas4free.  It can boot from a thumb drive, and the config can be backed up easily to another thumb drive.

---

### Post by harrispartyof3 on 2016-03-02
How do I determine if a card is well supported? Is that based on the manufacturer or chipset on the card or a combination? I looked into nas4free but I like the expandability of using Ubuntu since I plan to keep adding to this server over the next several years as I figre stuff out. I figured out a backup solution using cron jobs and rsync to an offsite box so I'm not too worried about ease of backing up anymore as this solution works pretty well. Is my best bet just ordering PCI cards and testing them and returning them if they don't work? Sounds like a simple but costly way of doing it..

---

### Post by him610 on 2016-03-02
[QUOTE]How do I determine if a card is well supported?[/QUOTE

Have you ever heard of the phrase "due diligence?"  What one needs to be aware of is that all of these cards are manufactured to industry standards. One manufacturer's card _should_ work as well as its competitor's model. That said, technology does not stand still; it marches on, continually improving. What you seem to be referring to is reliability, availability, and maintainability (RAM.) Mean Time Between Failures (MTBF) is another term that comes to mind. When comparing the physical and performance characteristics of different models, be sure to compare similar characteristics, and try not to get taken in by marketing spiel.

Max Sequential Read 
Max Sequential Write 
4KB Random Read 
4KB Random Write 

Go to each manufacturer's site for each particular model you are considering; study and compare the published specifications. Find out the RAM characteristics of each device being considered. Do your research and comparisons before you buy, then buy the best candidate you can afford. If you plan on testing them in someway, develop you test plan and procedures ahead of time so you do not waste any time once you have your selected card on hand. Good luck.

---

### Post by harrispartyof3 on 2016-03-02
I had that mindset when I was getting graphics cards for my most recent desktop and that ended up burning me since now the computer locks up whenever the GPU gets any kind of reasonable load. I suppose I can email each manufacturer for info on if their cards have been tested or not. That is probably what I will do, thanks for the thought!

---

### Post by houstonbofh on 2016-03-02
> **harrispartyof3 said:**
> How do I determine if a card is well supported? Is that based on the manufacturer or chipset on the card or a combination?
Yes.  The chip-set generally, but some manufactures mess with it for unknown reasons.
> **harrispartyof3 said:**
> I looked into nas4free but I like the expandability of using Ubuntu since I plan to keep adding to this server over the next several years as I figre stuff out. I figured out a backup solution using cron jobs and rsync to an offsite box so I'm not too worried about ease of backing up anymore as this solution works pretty well.
Nas4free is Unix and is quite expandable, but not as easy to customize, so whatever works for you.
> **harrispartyof3 said:**
> Is my best bet just ordering PCI cards and testing them and returning them if they don't work? Sounds like a simple but costly way of doing it..
Or, let someone else do it. :)  Linux is actually much better at support then FreeBSD or Solaris, so if it is on this list, you are good.
[http://blog.zorinaq.com/?e=10](http://blog.zorinaq.com/?e=10)

---

### Post by gordintoronto on 2016-03-03
Then again, simply booting from a flash drive sounds simpler and cheaper. And it's easy to have a perfect backup.

---

### Post by harrispartyof3 on 2016-03-04
The flashdrive idea is very tempting but I'm going to give this a shot mostly because having a flashrive sticking out of the back is going to do a number on my OCD, having a couple cards inside with the SSDs mounted to them all neat and tidy like would look aesthetically better, cant believe i just committed to an extra $60 in the name of aesthetics I'll let you guys know how this all went after I get the cards (hopefully) installed, probably wont be until next month though. Thanks for all the help fellas!

---

### Post by harrispartyof3 on 2016-04-26
Finally got the hardware in, two no-name PCIE sata/msata adapter and two sandisk 64G msata drive and installed Ubuntu server 16.04 on them in RAID 1. aside from some confusing unrelated install errors (some conflict between grub2 and gpt partition tables) all works beautifully. Total cost for the setup was $100 and I love the clean look it leaves.

I know someone's wondering, no there's no noticeable performance boost at all, but from my experience (4 computers to-date) Ubuntu's boot doesn't seem impacted by a ssd, ubuntu seems to have its loading pretty well streamlined so the bottleneck appears to be waiting for motherboard components to connect and configure (network cards, drives, etc)

Thanks everyone for the help, I appreciate the guidance.

---

