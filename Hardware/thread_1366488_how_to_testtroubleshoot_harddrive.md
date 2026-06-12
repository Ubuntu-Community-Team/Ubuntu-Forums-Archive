---
title: "how to test/troubleshoot harddrive"
date: 2009-12-28
forum: Hardware
---

### Post by MichaelBurns on 2009-12-28
Is there a program that I can run in ubuntu 9.04 (off of the live cd) to find out what is wrong with my harddrive?  According to my BIOS, the harddrive is not even connected.  However, I know that it is physically connected, and I can hear it making weird noises on boot up.

---

### Post by cascade9 on 2009-12-28
If your drive doesnt appear in BIOS, then ubuntu (or anything else) wont be able to see it. 

You could try moving IDE channels, or changing from 'master' to 'slave' if it is IDE, or changing the SATA port if it is SATA...or trying a new cable for either SATA or IDE. 

Clicking is a classic sign of a dieing hard drive.

---

### Post by doas777 on 2009-12-28
if the bios won't see it, then somthing is seriously wrong with your drive, cabling, or mobo slot.

all I can tell you is keep rebooting, and hopefully you will get it to come up once outta 10 times. if so, then back your data up fast.

---

### Post by MichaelBurns on 2009-12-28
Yeah, OK, I didn't have much hope for it.  I is not clicking, but I don't know what you mean; I describe the normal noise of the reading and writing as a clicking noise.  Anyway, it is buzzing, with steadily increasing pitch, for about 1/2 a second.  It repeats this a few times, then it's silent for a moment.  This noise cycle repeats over and over.  I do not hear the drive spinning, nor do I hear the "good" clicking sound of the drive reading.

Is it possible that the BIOS cannot see the harddrive if it cannot see the boot sector, but the rest of the drive could be fine?

Is a clean room absolutely necessary to open the harddrive (without damage/loosing data)?

Is it bad to try tapping the drive to maybe dislodge something?

BTW:
I'm sure that it's a problem with the harddrive, rather than mobo or something, because I took it (the harddrive) to a computer shop, and they said that they could not even get the drive to come up on their computer, and they described the same noise that I'm hearing.

---

### Post by cascade9 on 2009-12-28
If it doesnt pop up on another computers BIOS, then its probably dead.

> **MichaelBurns said:**
> Yeah, OK, I didn't have much hope for it.  I is not clicking, but I don't know what you mean; I describe the normal noise of the reading and writing as a clicking noise.  Anyway, it is buzzing, with steadily increasing pitch, for about 1/2 a second.  It repeats this a few times, then it's silent for a moment.  This noise cycle repeats over and over.  I do not hear the drive spinning, nor do I hear the "good" clicking sound of the drive reading.


Is it possible that the BIOS cannot see the harddrive if it cannot see the boot sector, but the rest of the drive could be fine?

That noise is the drive trying to initialise, but failing. Its very very unlikely that you boot sector is dead, but he rest is OK. AFAIK, it only hits the boot sector when it tries to boot, during the  initialise phase its is pretty much just 'testing' itself. Sounds more like you have a drive motor/heads issue. I would guess the 'buzz' is the drive spinning up, but your not getting the 'click' from the stepper motor that controls the heads. 
 
> **MichaelBurns said:**
> Is a clean room absolutely necessary to open the harddrive (without damage/loosing data)?

Is it bad to try tapping the drive to maybe dislodge something?

Well, no you dont NEED a clean room. I've done a platter swap once just on my normal workspace, and lost no data. Its probably not a good idea though. Unless all else fails.  

I would try the freezer trick- 

[http://ubuntuforums.org/showthread.php?t=1362667&highlight=freezer+trick](http://ubuntuforums.org/showthread.php?t=1362667&highlight=freezer+trick) 

Not permanent, and doesnt always work, but its worth a go if only to recover data. If I am right and its a stepper motor problem, it wont help at all. 

Tapping shouldn't help at all, but if the freezer trick doesnt work, maybe try it. Then platter swapping.

---

### Post by MichaelBurns on 2009-12-29
Cascade, thanks for the link to that other thread!  I am nervous to do any of these things, but I think that at least my harddrive has a date with some rice in the freezer tonight.  I am extremely nervous to open up the harddrive in my "workspace", but you and others have indicated that this is a workable solution, so I might try (assuming all liability, of course).  I am pessimistic of the freezer trick; it seems to be a solution for an overheating harddrive.  We'll see.

There is a cleanroom in Austin that specializes in harddrive data recovery, but they charge upwards of $100's.  I was thinking of rigging up a plastic storage box with holes for a vacuum cleaner hose attachment, input filter, and two gloves, as a makeshift "cleanbox" (instead of clean room).  Maybe I should just mount the vacuum cleaner hose a foot or so above my "workspace" and consider it good enough.  Anyone else have a better suggestion (if it comes to that)?  What's a good and cheap way to determine the amount of dust in the box?  How big of a problem is moisture?

---

### Post by cascade9 on 2009-12-30
NP on the linkage ;) 

Nah, its not just for heat issues. I've had it help with heat (as you can see from that thread) but is has helped on non-heat issues, probably far more often than heat. I've seen a lot of debate on hardware forums as to *why* it helps, I've never seen a hard answer. 

As for dust, moisture etc- hard drives have an 'air hole'. They are not sealed units. Its best to avoid getting any dust or water in there, but unless you do it in a very dusty room, or drop any sweat into the drive, you should be fine. Damage to the platters from fingerprints, oil on your fingers or how delicate the drive parts are is a much bigger problem.

---

### Post by MichaelBurns on 2009-12-30
The first date with the rice in the freezer was unsuccessful.  They're on the second date right now.  We'll see if the harddrive gets any love this time.  The first time, I booted up with the live cd, and I had ata errors (that apparently refer to my harddrive, because I don't get them when it is removed).  This time, I will try to boot from the harddrive itself.

If this doesn't work, I was thinking to try booting from the live cd and then hotplugging the harddrive.  Is that a bad idea?

> **cascade9 said:**
> As for dust, moisture etc- hard drives have an 'air hole'. They are not sealed units.That's interesting, and encouraging.  I will need a pair of latex gloves and a clean desk - no problem.  I don't understand, then, why this data recovery outfit wants to charge so much.  Am I in for a surprise, thinking that it is a simple matter of opening, fixing, closing?

---

### Post by cascade9 on 2009-12-31
Hottplugging should be fine with a SATA disc. Dont try it with an IDE disc. If its SATA, I would try hotplugging it before trying to boot it (its possible that booting will just stuff it up more)

As for how easy it is...depends. Drives tend to use odd fasteners (torq fittings are most common). They can be fiddly to work on. It shouldnt be so bad, but its not as easy as, say, installing a CPU. 

LOL, the 'drive recovery' guys charge a lot because- 
1- they can.
2- its not _that_ easy.
3- people who spend any real amount of money on data recovery are NOT going to be happy to get a phonecall back saying 'sorry, failed, lost your data'. So they need to know what they are doing.
4- they tend to use a new drive for every data recovery job, so your looking at the drive cost as well.
5- experience, connections and educated guesses are expensive. The data recovery guys need to know and guess things, before every drive model leaves the shelves. How many drives they should stock for future use, the interactions between different drive models (e.g. ST-xxxx-xxxx uses platter xxxx, ST-xxx-zzz uses platter xxxx, drive ST-xxyy-xxzz use the odd platter xyxz). Its one thing to be lucky and have a compatible drive hanging around, or being able to source one, but its very different to make a business out of it.

---

### Post by MichaelBurns on 2010-01-13
[i]EDIT:  Of course, it is the nature of such things that I should realize a neglected and viable alternative to the platter swap after already exposing my platters.  For anyone thinking about doing this, **FIRST TRY SWAPPING THE CONTROL BOARD _BEFORE EXPOSING THE PLATTERS_!**  This is an extremely trivial procedure, at least on all three of the laptop harddrives that I have; it just amounts to a few screws and a small, board-soldered connector.  If you've come to the point of a platter swap, then you will have a sacrificial drive laying around anyway.  You can use the control board from that, with virtually no risk of damage.

There are three storage devices that enter into either procedure:
- the old, nonfunctioning harddrive:  hdd1, with platter p1 and control board cb1
- the new, sacrificial harddrive for swapping, which apparently must be identical to hdd1:  hdd2, with platter p2 and control board cb2
- another storage device for immediate backup:  hdd3, don't mess with it
(Note:  your OS will NOT refer to these storage devices in this way.  As far as I know, the OS reference is unpredictable, so I will stick with "hdd1", "hdd2", and "hdd3" rather than trying to sound like an OS.)

1.  Prepare hdd3 to receive the data transfer.  I'm guessing that this entails physically connecting hdd3 to the computer as an external storage device and logically mounting partitions, if possible.  (Note:  your OS will only refer to this drive as "hdd3" by coincidence.  Most likely, it will be called something else, e.g. "hdb1", "sda5", etc.)

2.  Connect hdd2 to your computer to make sure that it even works properly.

3(fail).  If your computer does not operate hdd2 properly, then you might (definitely?) have a motherboard problem.  Anyway, obviously neither a platter swap nor a control board swap will help at this point.

3(succeed).  If your computer indeed operates hdd2 properly, then shut down the computer, remove hdd2, and put cb2 in place of cb1 in hdd1.  Plug hdd1 (with cb2) into the computer and try it out.

4(succeed).  If hdd1 (with cb2) now works, then you will have two pristine platters (p1 and p2) safely sealed away, and you may safely use hdd1 (with cb2) with no increased risk of (i.e. inevitable) dust damage.  Also, you will have pride in knowing that you have actually repaired a harddrive (even if it was a gross hack).  Now, flagellate yourself with a shredded IDE cable for not backing up whatever important, irreplaceable data it was that you didn't back up, and immediately back it up NOW to hdd3! (regardless of the fact that hdd1 with cb2 should be reliable).  **CONGRATULATIONS!  YOU SUCCEEDED!**

4(fail).  If the control board swap does not fix the problem, no harm done.  Now I suppose you could proceed with the platter swap (after returning cb2 to hdd2).  The first step that I suggest is to open hdd1 to expose p1.

5(damage).  If p1 itself is scratched (or otherwise obviously damaged), immediately replace the cover, and consider how valuable is the data in terms of dollars and risk to privacy, confounded by the fact that it still may not be recovered (with increased likelihood after exposing p1 in your dusty house).  Then, research the data recovery specialists in your area.

5(pristine).  If p1 looks pristine, open up hdd2, and replace p2 with p1.  Immediately put hdd2 (with p1) back together, plug it into the computer, and back up the data to hdd3.  At this point, p1 is literally damaged by every operation of hdd2, because the head is dragging the invisible dust that inevitably accumulated accross its surface.  (For modern harddrives, the spacing between the head and platter surface is likely to be at least an order of magnitude smaller than human perception.  To me, it looks as though the head is actually resting on the platter, but it is not (supposed to).)  I suppose that neither hdd1 nor hdd2 are useful as storage devices ever again.  You cannot afford any extra reads, and you may not even get all of your data back (e.g. because the head may even become damaged beyond usefulness due to all of the dust that collides with it at 1000's of rpm).[/i]

------------------------------------------------------------------------

I got impatient and just opened up my harddrive without being sufficiently prepared.  In particular, I don't yet have a sacrificial drive to swap.  I just wanted to see if there was anything "obviously" wrong in there (as if I would know).  Of course, my minimal preparations did at least include:
- latex gloves,
- esd strap,
- and a tight hat.
I hope that my above suggestions made painfully obvious the fact that this was a really REALLY stupid thing to do, primarily because I don't yet have the sacrificial nor backup drives.

I laid the drive on aluminum foil (which I assumed would help to prevent esd, or maybe I just killed it ...).  I had vacuumed the whole area:  table-top, chairs, carpet around the area.  I should have also vacuumed the ceiling, but I didn't think of it.  Then, the vacuum cleaner broke (I think the motor shorted out; what a great time for that to happen).  The drive is laying on the aluminum foil in a clear plastic tub.  As I stared at the pristine mirrored surface, to my horror a blemish (spec of dust?) appeared right before my eyes.  Before I could do anything, another appeared.  Dear god! (and damn cats, get off my table!)  I quickly replaced the cover (loosely, with only four of the screws), and laid another piece of aluminum foil over it (so that it now rests sandwiched between two pieces of aluminum foil) for dust/esd protection (or burial, I suppose).

For the curious-minded, this is a **Toshiba mk1234gsx hdd2d31 b zk01 s**.  There are **six screws** around the edge of the case, four at the corners and two on the sides.  They are **all torx** (that six-pointed star-shaped fit), **size T5**.  Unfortunately, the case would not come off upon removal of these screws.  So, I decided to peel back the label.  Sure enough, there is an ***obscurely located seventh screw*** (also T5) ***hidden under the label*** - an ominous, forboding, final warning from Toshiba (after ignoring "Do not disassemble or modify," and "Do not remove any labels.").  I felt like I had removed the seventh seal from the book of judgement or something.

Anyway, I have one question:

Is it safe to use one of those spray-can dusters on the platter's surface?  I shopped around to find the nonflamable kind (I presume that is chemically inert).  I found and purchased Memorex-brand "AirDuster".  Some of the more unsettling warnings on the spray can include:
- Always test in an inconspicuous area before general use. (not very incouraging)
- Do not allow chemicals to puddle. (problably just an evaporative cooling issue)
- Never use on camera mirrors. (a warning that I missed at the store, and would have been a deal-breaker)

Given that I have probably already ruined my harddrive, I don't suppose that it matters, except that the guy at the DiscountElectronics store gave me the name of an operation (Flashback Data) who does data recovery for cheap.  Anyone ever heard of them?

*EDIT:  replaced the word "foil" with "aluminum foil", since some non-Americans refer to static plastic wrap as "foil".  Using static plastic wrap would indeed be a bad idea.*

---

### Post by MichaelBurns on 2010-01-13
Sorry for the extra post.  I just wanted to call to your attention that my previous post has been dramatically ammended.

---

### Post by cascade9 on 2010-01-13
> **MichaelBurns said:**
>  I had vacuumed the whole area:  table-top, chairs, carpet around the area.  I should have also vacuumed the ceiling, but I didn't think of it.  Then, the vacuum cleaner broke (I think the motor shorted out; what a great time for that to happen).  

Yay verily, I say unto you, this was a sign! A  portent of great disaster! Let not your own ego lead you to catastrophe. 

> **MichaelBurns said:**
> They are **all torx** (that six-pointed star-shaped fit), **size T5**. Unfortunately, the case would not come off upon removal of these screws. So, I decided to peel back the label. Sure enough, there is an ***obscurely located seventh screw*** (also T5) ***hidden under the label*** - an ominous, forboding, final warning from Toshiba (after ignoring "Do not disassemble or modify," and "Do not remove any labels."). I felt like I had removed the seventh seal from the book of judgement or something. 

The drive is laying on the aluminum foil in a clear plastic tub.  As I stared at the pristine mirrored surface, to my horror a blemish (spec of dust?) appeared right before my eyes.  Before I could do anything, another appeared.  Dear god! (and damn cats, get off my table!)  I quickly replaced the cover (loosely, with only four of the screws), and laid another piece of aluminum foil over it (so that it now rests sandwiched between two pieces of aluminum foil) for dust/esd protection (or burial, I suppose).

And the seal was broken, the prophesied great disaster! And the blemish appeared, and the gods were avenged by weeping, mourning and beating  on the breast of the unbeliever. Hark ye, desolate is the data of those who are blind, or who refuse to see the signs of the gods of electronics, mighty and wrathful. 

> **MichaelBurns said:**
> *EDIT: replaced the word "foil" with "aluminum foil", since some non-Americans refer to static plastic wrap as "foil". Using static plastic wrap would indeed be a bad idea.*

Funny enough, here everyone knows what 'foil' means. But its slang for the smallest common unit in which weed (cannabis) is sold. 

No, I'm not on any. At the moment. Or yesterday. Or tomorrow. Maybe the day after? :mrgreen:

> **MichaelBurns said:**
> Is it safe to use one of those spray-can dusters on the platter's surface?  I shopped around to find the nonflamable kind (I presume that is chemically inert).  I found and purchased Memorex-brand "AirDuster".  Some of the more unsettling warnings on the spray can include:
- Always test in an inconspicuous area before general use. (not very incouraging)
- Do not allow chemicals to puddle. (problably just an evaporative cooling issue)
- Never use on camera mirrors. (a warning that I missed at the store, and would have been a deal-breaker)

Given that I have probably already ruined my harddrive, I don't suppose that it matters, except that the guy at the DiscountElectronics store gave me the name of an operation (Flashback Data) who does data recovery for cheap.  Anyone ever heard of them? 

Seriously, while vacuuming seems like a good idea, it tends to stir up lots of dust. Unless you have one of those 'hypo-allergic' filters. Its probably not that bad an idea, but I would leave a room for several hours after vacuuming before doing this kind of operation. 

A 'can of air' might well help. They put those 'always test in an inconspicuous area' warnings on things because they contain hydrocarbons, and they can do funny things to dyes, etc. Shouldnt affect a drive platter though. The camera mirror warning is because they can 'spit' liquid 'air'. Thats kind of cold (like, 'wow, be careful, it can give your frostbite cold') and that could crack a glass camera mirror. 

BTW, its best to get teh kind of air cans made for electronic equipment as they can create a static charge unless the right kind of compounds are used. A static charge on those nice, sensitive magnetic platters could lead to data loss. 

There is always an element of risk in anything like this.If your planning on taking the drive to Flashback Data (who I havent heard of BTW, but they are in the US and I'm not) then I would just leave it. 

You don't want to make things worse. :(

---

### Post by IcarusR on 2010-01-13
I seriously doubt that you will be able to 'repair' your hard drive by disassembling it.
Do not expect any data recovery firm to even try to recover data from it once you have opened the drive !!

Lesson to be learned from this kidds is back up all important data !!
When I did my computer engineer training we were told that fast moving items (hard drives) & high voltage items (monitors) fail first & most. 
This proved to be correct.

---

### Post by MichaelBurns on 2010-01-13
Well, I just got off the phone with Flashback, and the lady told me that, since I exposed the platters, I am looking realistically at upwards of a grand $$$ to enlist their services.  God, I am kicking myself so much over my damn rashness.  My data is certainly not worth even a fraction of that.

I will clean the work area as best I can, remove the cover again, give the internals a good (but delicate) air spray, close it back up, and then store it away until I get ahold of hdd's 2 and 3.  Then, I will try a control board swap, with the understanding that I still can't spare an extra read since I have exposed the platters.  It's a gamble, because, if I do indeed need to do a platter swap, I will have scraped that much more dust across the surfaces in my control board swap attempt.  But, after beholding the paranatural precision of the interior, I have absolutely zero confidence that I can accomplish a successful platter swap, so I will only do that for a sense of completeness after the control board swap fails.

At least I learned that there are some really strong magnets in there, so that will make for some fun experimentation.  And those platters are so beautiful, I'm sure that I can find some artful purpose for them.

---

