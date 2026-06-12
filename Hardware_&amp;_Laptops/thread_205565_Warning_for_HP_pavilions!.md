---
title: "Warning for HP pavilions!"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by aarbear26 on 2006-06-28
I just bought an HP pavilion dv 5000t.  It has a dualcore CORE Duo processor and and Nvidia GO 7400 w/ 128 RAM.  I specifically got this because the hardware works and i like quickplay.  I understand that certain things don't work in linux, but i'm not too concerned about those.  

I just called tech support to find our if the quickplay would work if i changed the boot sector (like what grub does).  I talked to someone from india the whole time and he didn't seem to have any idea what i was talking about.  Then he warned me that installing another operating system would void my waranty, including the hardware waranty!  He said even if i installed a different version of windows, it would still void the waranty!](*,)

I asked to talk to a supervisor to confirm that and was hung up on while on hold.  I called again and another man tried to explain to me why they would void the warranty, though he didn't make much sense.  So i had to ask him several times before he would transfer me to a supervisor.  What nerve, he tried to argue with me and would not transfer me.:mad:

The supervisor initially said the same thing, then finally conceded that if i did a full recovery of the original OS, they would cover me.  And if it was harddrive failure, i would still be covered as well.  

I like the hardware and so far it's works great. but i must say I am definatly not impresssed with the customer service.

---

### Post by Ptero-4 on 2006-06-28
That's why I don't like those stinky Windoze-lover PC maker companies. The good thing is that at least we got a PC maker that understands the need of using Opensource software and OS's.

---

### Post by tseliot on 2006-06-28
I have an HP portable computer and I use Linux (ONLY). Almost a year ago the battery died as well as the DVD-reader. Then I brought it back to the shop where I had bought it and they installed the Windows version which came with the laptop by default. Then they sent it to HP and it came back with no problems whatsoever.

That's the only thing you can do

---

### Post by doog on 2006-06-28
This is why I installed the ntfsprogs and wrote a couple little scripts to backup/restor the original image.

Here's the Backup script:
```

 #!/bin/bash

if [ -f /mnt/ntfsBackup.img ]; then
  echo
else
  echo Mounting restore Image location
  sudo mount /dev/hda5 /mnt
fi

echo Ready to restore hda1
sudo ntfsclone --save-image --output /mnt/ntfsBackup.img /dev/hda1
```

and the Restore script:
```

#!/bin/bash

if [ -f /mnt/ntfsBackup.img ]; then
  echo
else
  echo Mounting Backup Image location
  sudo mount /dev/hda5 /mnt
fi

echo Ready to Backup hda1
sudo ntfsclone --restore-image --overwrite /dev/hda1 /mnt/ntfsBackup.img
```

When I installed Ubuntu, the orginal partition got crunched down to 10GB.  I've done a backup and restore and it worked. One thing I've not tried is reformating the partition and then restoring. It generated a 6.6GB file that'll fit on a Duallayer DVD for off-device archiving in the event your laptop has to go back to the manufacturer.

Can't wait til OEMs get on the Linux bandwagon with full support. Until then, this is an option when purchasing outside the Linux pre-installed systems.

---

### Post by aarbear26 on 2006-06-28
Thanks for all the positive replies.  it at least makes me feel better about my purchase.  I am also glad that others have experience and it turned out well.

---

### Post by SirShaggy on 2006-06-29
[QUOTE=aarbear26]Thanks for all the positive replies.  it at least makes me feel better about my purchase.  I am also glad that others have experience and it turned out well.[/QUOTE]

If it makes you feel any better, The day I bought my Compaq, I tried the first install of Fedora Core 3 (Beta I think). Anyway, half way through, the hard drive started making really bad sounds, LOUD TOO! I called tech support, the guy laughed and said my warranty is gone, gave me to his supervisor and, well pissed me off.  There was no way to reinstall Windows at this point.
I took their hard drive out, welded a 6" steel cage around it with 3/8 rod, welded on some chain and a steel ball.
It cost me almost $60.00 to mail it with my personal point of view on the matter!
I explained that I didn't need their ball and chain anymore and nobody would ever force me to use Windows again. I also explained that if I got one more crappy manager over the phone, I was going to drop 5 grand to personally find them....I gave his name and the phone number I had been routed to. (Yes I took it personal, I can't write here exactly what he said, women and children most likely present.)
Two weeks to the day, I got an apology from the man and he sent a coupon from HP for a 10 or 15% discount off my next purchase. Yeah right! I set fire to that.
New hard drive was cheap, used it untill the 80GB 7200 RPM Hitachi came out and I swapped them again. Never had any more troubles. Hibernate and suspend work, but the laptop doesnt awake from either! (Not so good)
I bought this because it was cheap and I didn't know if I'd even like a laptop. I learned my lesson, I'll never buy another OEM with an operating system installed. It will cost me more in money, but it cost's much less in aggrevation.

---

### Post by OldZack on 2006-06-29
It's just about reached the stage these days when it's far quicker and often cheaper to just order up a new hard-drive (whatever) and put in yourself than struggle through a warranty claim!:-\"

---

### Post by trent dillman on 2006-06-30
Here's my two cents: 

Yes, it's bad when a representative of a company is rude, thus portraying a bad image. But let us not forget that HP (or any other OEM) has trained their tech support to all use the OS that shipped with that machine, and they may have special diagnostic software to test these machines (or they have a hidden account or back door that allows them access to the OS that ships with the computer, or both).

Let's be honest, folks: Windows is currently the so-called "standard."

---

### Post by nrwilk on 2006-07-22
Strange.  I'm looking at buying an HP laptop, and this post worried me.  So, I called up a sales rep.  He didn't know, but he put me on hold while he asked his manager.  His manager said that the warranty is not voided by deleting XP.  But, they did say that in order to send it in to be fixed under warranty, XP would have to be installed.  So, basically you have to reinstall XP on it if you're going to send it in.

I wasn't quite satisfied with the answer, so I also sent them an email asking the same questions.  That way if they give me trouble with it after I buy the laptop I can throw their email response at them, and demand some service.  Assuming that the response is that the warranty is not voided by installing another OS.

I will post their response when I get it.  They claim to respond within 2 business days.  So, that means tuesday July 25, I guess.

So, maybe it's better than we thought.

---

### Post by arthur on 2006-07-22
When my Pavilion was collected for repair, the HDD was not there, as I had pulled it out.
No comments, no complaints from HP.
And, amazingly, it was collected in Spain (not even Madrid or Barcelona), sent to the UK, and returned back to Spain within 48 hours.

Wow!
Just my two cents ;)

---

### Post by BKK on 2006-07-23
I Just got a new HP pavilion. DApper works well, There are some drivers listed in device manager as unknown....my guess is the 3954bg intel centrino or the memory card reader...possibly bluetooth...Dont know enough about linux yet anyways. I dual boot this machine with the XP home that was preinstalled. Main complaint is that I had to create my own backup discs, the notebook shipped with ZERO discs!!

---

### Post by nrwilk on 2006-07-23
> **nrwilk said:**
> I will post their response when I get it.

I promised their response, here it is.

> I understand from your mail that you want to know whether using a different OS will void the notebook's warranty and is it necessary to back up the recovery partition before deleting it.

Noah, regarding your query about removing the Windows XP and installing 
a different OS, such as Linux, please let me clarify that HP does not 
recommend using any other OS than the one pre-installed in the notebook.


The reason behind this is we do not have drivers compatible to other OS 
and installing another OS will probably result into a driver conflict. 
In that case, we will not be in a position to assist you as no drivers 
will be available, and hence the warranty will be considered as void.

However, the hardware will be covered under warranty regardless of the 
operating system you use.

Noah, regarding the query about creating a backup of the recovery 
partition before deleting it, please let me explain that a recovery 
partition does not only have the OS settings. It also contains the 
drivers and pre-installed applications or softwares for the notebook. 

For the above reason, HP does not recommend to delete the recovery 
partition. However, if you want to delete the partition, please create 
the recovery CDs or DVDs as a backup so that the drivers or the 
softwares can be recovered when there is a conflict of them. 

I have to say that a lot of that is confusing.  The warranty is considered void, but the hardware will still be covered under warranty?  What does that mean?  I wasn't aware of any warranty on these machines OTHER than a hardware warranty.  Also, what is this "driver conflict" of which he speaks?  Maybe he assumes I'll be dual-booting?

What does everyone else think of this letter?  Good?  Bad?


@BKK, maybe you could answer some of my questions here :-k:):
[http://ubuntuforums.org/showthread.php?t=220981](http://ubuntuforums.org/showthread.php?t=220981)

---

### Post by mips on 2006-07-24
What I don't get is that HP sells some of it's laptops without Windows, FreeDOS only to allow people to install Linux.

Does the above mean they won't honour the warranty if I send it back with FreeDOS or Linux as it has no window on it ?

---

### Post by nrwilk on 2006-07-24
> **mips said:**
> What I don't get is that HP sells some of it's laptops without Windows, FreeDOS only to allow people to install Linux.

Does the above mean they won't honour the warranty if I send it back with FreeDOS or Linux as it has no window on it ?

It's true.  I'd assume that they warranty those machines as long as you keep FreeDOS on them.  They did say in their email to me that they "HP does not recommend using any other OS than the one pre-installed in the notebook."


Anyway, I've come up with a not-so-desirable, but nonetheless acceptable solution to the issue.  I'm going to get the laptop with the smallest hard drive they offer and (with the money saved from not upgrading the drive through HP) also get another 2.5" SATA drive and swap them as soon as I get the machine.  If I ever need to send the machine in for service, I'll stick the original drive back in it.  They'll never even know it was out.

I do have a question, though.  Is it possible to boot XP from an external USB drive?  If so, I'll get one so that I can use the XP drive if I ever really need to without putting it back into the laptop.  I know that I can boot OS X from an external drive, but I don't know whether I can with XP.

---

### Post by mips on 2006-07-25
> **nrwilk said:**
> It's true.  I'd assume that they warranty those machines as long as you keep FreeDOS on them.  They did say in their email to me that they "HP does not recommend using any other OS than the one pre-installed in the notebook."


Anyway, I've come up with a not-so-desirable, but nonetheless acceptable solution to the issue.  I'm going to get the laptop with the smallest hard drive they offer and (with the money saved from not upgrading the drive through HP) also get another 2.5" SATA drive and swap them as soon as I get the machine.  If I ever need to send the machine in for service, I'll stick the original drive back in it.  They'll never even know it was out.


I would recommend the Hitachi Travelstar drives for laptops.

---

### Post by Tycho C on 2006-07-25
If there's one thing I noticed working in a computer repair shop doing RMAs and Warranty calls, if you're gonna buy a laptop, get a BUSINESS laptop!!!

Most of the calls I make for them there are no questions asked.  I personaly have an HP Compaq nc4000.  Business laptop with a 3 year warranty.  I just called them yesterday about getting new hindges. No questions asked they overnighted the new ones and they are waiting for me at home right now.  (gave me a tracking number and all)  They offered to replace them or I could do it myself.  I asked them it it would void my hardware warranty and he said "nope."  

When you buy a laptop, don't go cheap.  In the end it will only cost you money, frustartion, or both.

:D

---

### Post by nrwilk on 2006-07-25
> **mips said:**
> I would recommend the Hitachi Travelstar drives for laptops.
Cool.  That's the model I was looking at getting.  Thanks! :)

What about my question about booting XP from a usb drive?

---

### Post by mips on 2006-07-25
> **nrwilk said:**
> 
What about my question about booting XP from a usb drive?

Dunno, maybe someone else can answer that or google **Boot XP from USB drive**

Found these:
[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)
[http://www.tomshardware.com/2005/09/09/windows_in_your_pocket/](http://www.tomshardware.com/2005/09/09/windows_in_your_pocket/)

---

### Post by cracker on 2006-07-25
It's really quite simple. HP's warranty guarantees software support. If you remove their software, they can't support it, and void the software support warranty. However, in the event of hardware failure, you are still covered. You have to remember that Linux users are generally more knowledgable about computers overall, and HP's (and other OEMs') typical tech support calls are from the kind of people who don't have the computer plugged in. For this reason, they have to be very defensive.

---

### Post by nrwilk on 2006-07-26
> **cracker said:**
> It's really quite simple. HP's warranty guarantees software support. If you remove their software, they can't support it, and void the software support warranty. However, in the event of hardware failure, you are still covered. You have to remember that Linux users are generally more knowledgable about computers overall, and HP's (and other OEMs') typical tech support calls are from the kind of people who don't have the computer plugged in. For this reason, they have to be very defensive.

Right.  This is what we had concluded.

But, a rep DID tell me over the phone that they would not be able to make repairs if it was sent in without XP.

---

### Post by Sal Z on 2006-07-27
I had some clarification from a HP representative when I bought my Pavilion 5165ea : The policies regarding the warranty change between regions.
I don't know about USA, but actually in Europe ( I bought mine in Italy) the warranty covers the hardware for one year , 6 months for the software, but they are independent from each other, so there are no problem using ubuntu on a HP laptop! if you don't care about software warranty , of course... ;)

---

### Post by bluenova on 2006-07-27
I don't understand this. I work for HP selling warranty extensions and recovery media on their machines for the UK/IRE market. The warranty only covers for Hardware not software. You only get 90 days of software cover with the machine after that it is only hardware. I can understand them not being able to provide tech support as the Indian agents are only trained to support Windows, but I don't see how it effects a unit repair, especially as the HDD is always formatted and the recovery ran every time a machine goes in for repair anyway.

These are the only reasons that HP will not perform a repair:

> HP is not obliged to provide services under this Warranty Extension due to (a) improper use; (b) operation outside of the published specifications for the Product; (c) inadequate site conditions or maintenance by Customer; (d) use of media and supplies not approved by the manufacturer or use of other products; (e) work performed by non-HP personnel without HP's authorization; (f) faulty connections or surges on the electrical or telephone network; or (g) natural disasters or other causes beyond HP's reasonable control.

Perhaps what they are talking about comes under (b) but I wouldn't have thought so.

If you want I'll check it out with tech support and find out the situation.

---

### Post by nrwilk on 2006-07-29
@ bluenova - Thanks for the clarification.

I just really wanted to be sure that my hardware would be covered.  That's all I care about really.  I don't need any software support.  My software support is these forums. :D

As long as I can run Kubuntu and be assured that all my hardware is under warranty, I'm happy. :)

---

### Post by welders4linux on 2006-08-06
Title is a little misleading, I had to drop in since I have a pavilion.

Have had ZERO problems......as with all machines If the thing dies during warranty just re-install the virus that it came with.  :-$ 

cheers

---

