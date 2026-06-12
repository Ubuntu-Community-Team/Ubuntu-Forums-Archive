---
title: "[SOLVED] CRC error on Wubi..."
date: 2008-12-01
forum: General Help
---

### Post by Jammanuser on 2008-12-01
Hi, i just recently installed ubuntu 8.10 on top of my pre-installed Vista OS, using wubi-installer ([http://www.wubi-installer.org](http://www.wubi-installer.org)), and it was working fine until a couple days ago, when i tried to boot into ubuntu, as before, but received the following error: "crc error" and then on next line "system halted"!!!

Does anyone know what could be the problem????

THANKS in advance!

EDIT: oh, and before anyone suggests it...i've already run a disk check, but it didn't fix the problem!

---

### Post by lisati on 2008-12-01
My first impression is that the copy of Ubuntu on your system has somehow bene scrambled. Something else to check is the usual Windows virus/malware check just in case something nasty has sneaked into your system. Beyond that I'm not sure.....

---

### Post by Jammanuser on 2008-12-01
> **lisati said:**
> My first impression is that the copy of Ubuntu on your system has somehow bene scrambled. Something else to check is the usual Windows virus/malware check just in case something nasty has sneaked into your system. Beyond that I'm not sure.....

thanks for the effort, but i've already run multiple virus/spyware checks, and removed the problems that i found...but Ubuntu's still not booting! 

Looking forward to next comment... :popcorn:

---

### Post by Jammanuser on 2008-12-02
Hi, i just recently installed ubuntu 8.10 on top of my pre-installed Vista OS, using wubi-installer ([http://www.wubi-installer.org](http://www.wubi-installer.org)), and it was working fine until a couple days ago, when i tried to boot into ubuntu, as before, but received the following error: "**crc error**" and then on next line "**system halted**"!!!

Does anyone know what could be the problem????

i've already run a disk check (didn't help!), virus/spyware scans (didn't fix the error), tried other "solutions" that i found after Googling it, such as, resetting the BIOS settings to default, mounting it with Ubuntu Desktop CD, and running a filesystem check (see Wubi Guide), but nothing i've tried so far has fixed this error!!! :( i **really** need my wubi install fixed, as i have some important files on it...that i **can't** recover after mounting the root.disk! for some reason, it wont let me copy them into my Vista OS! :confused:

THANKS in advance!

---

### Post by Jammanuser on 2008-12-02
Hello, i've repeated this question several times because no one has responded with a solution! i dual booted my computer recently with Vista and Ubuntu 8.10, using wubi-installer (not from CD...but from download) to install ubuntu on TOP of my Vista OS! it was working ok there for a while, but then a few days ago, when i tried booting into it as normal, i got a "crc error, system halted" message, and i haven't got past that screen ever since! :( 

of all the 10,000 users on this forum, or so, can NO one answer my question???? :(

Looking forward to any and all replies!

---

### Post by Jammanuser on 2008-12-02
Can **NO** one solve the "**crc error, system halted**" error on booting into ubuntu 8.10???? am i the only one that thinks its a very serious error, and one not to be ignored...which is what i've noticed everyone on this forum so far has done!!! :) 

is there no fix or workaround to this error...its VERY annoying, and is beginning to give me second thoughts on choosing wubi to install ubuntu 8.10...

Looking forward to any and all replies! :guitar:

---

### Post by magmon on 2008-12-02
[http://linuxgazette.net/issue50/tag/24.html](http://linuxgazette.net/issue50/tag/24.html)

This site says it best. From what I've read on the subject, this error is related to ubuntu having issues reading the hard drive. It could be damaged, old, or simply having compatability issues. Did you install using the latest wubi? 8.something?  Google is your friend, see what you can find!

---

### Post by Jammanuser on 2008-12-02
i have a simple question to ask: has ANYONE, ANYONE at all, come up with ANY solution to the "CRC error, system halted" that has been bugging the hell out of me the last few decades?!!! is it just over, when a CRC error hits the works???? if so, then i think that is VERY lame!!! :lolflag: i'm guessing that its probably a very common problem for wubi users, and that i'm not the only one, but it just seems odd that all of ubuntu's BEST have no REAL solutions to offer to this problem!!! 

i've been up and down, and all around on the Internet...even Googled it, but no one, it seems, has any solution to this annoying problem, save to say run a chkrdsk /r scan, which did absolutely NOTHING positive in my case!!! is this a problem that the ubuntu and Wubi people have simply given up on, admitting defeat??? if so, then i think that's really lame...

Looking forward to **any** and all replies!!! :guitar:

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> [http://linuxgazette.net/issue50/tag/24.html](http://linuxgazette.net/issue50/tag/24.html)

This site says it best. From what I've read on the subject, this error is related to ubuntu having issues reading the hard drive. It could be damaged, old, or simply having compatability issues. Did you install using the latest wubi? 8.something?  Google is your friend, see what you can find!

did u not read my above message??? ^^^^^ i **just** stated that i've tried Google already, but got no REAL solutions!!! :(

as for the link...i'll take a look at it, although i have a feeling that it says the one of the same things that i've already covered, and which hasn't solved my problem one OUNCE!!!

EDIT: wait! sorry! i just realized that i mentioned that in a different thread...i apologize!!! and yes, as far as i know, i used the latest Wubi to install! it was only a few days ago! yo!

---

### Post by melojo on 2008-12-02
CRC stands for Cyclic Redundancy Check. This is a data transmission integrity check that is commonly used to determine if transmitted data has been corrupted. CRC verifications are used in BIOS during booting, during data transmission over phone lines and during file reads from assorted media, including hard disks and CD/DVD-ROMS. It can also be used to verify RAM integrity. If you get a CRC error message it normally indicates that the data was corrupted to begin with, or the data was trashed during transmission.

Can you boot a live cd with out any problems?
Also has windows updated itself before this happened?

first thing I would do is to test the ram and update your bios.

---

### Post by magmon on 2008-12-02
Hmm... Do you allow the shutdown/restart process to go, or have you been "power killing" the computer?

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Hmm... Do you allow the shutdown/restart process to go, or have you been "power killing" the computer?

well...i shutdown the CORRECT way every time i'm able to...but sometimes...Vista freezes up, and i have to hard reboot it!!! :) yo! that's probably what caused the crc error in the first place, i know, but that bit of knowledge doesn't help me now...and it didn't help before because the only times that i hard rebooted, like i just said, were the times when Vista froze up, and i couldn't do ****!!! 

Thanks for the replies! 

Cheers! :lolflag:

---

### Post by magmon on 2008-12-02
If vista is bugging you, Im a pro with that lol. Download CCleaner, change your AV to Avira, install online armor, install adaware, and auslogics disk defrag. After all those are up and running, and a scan/fix from all of them has been done, your computer will be running like new!

---

### Post by Jammanuser on 2008-12-02
> **melojo said:**
> CRC stands for Cyclic Redundancy Check. This is a data transmission integrity check that is commonly used to determine if transmitted data has been corrupted. CRC verifications are used in BIOS during booting, during data transmission over phone lines and during file reads from assorted media, including hard disks and CD/DVD-ROMS. It can also be used to verify RAM integrity. If you get a CRC error message it normally indicates that the data was corrupted to begin with, or the data was trashed during transmission.

Can you boot a live cd with out any problems?
Also has windows updated itself before this happened?

first thing I would do is to test the ram and update your bios.

Thanks, melojo, for replying!! :) yes! i **can** boot a live cd without any problems...at least for the time being...i hope it ALWAYS works!!

and not sure what u mean by Windows "updating itself"! :confused: as for updating my BIOS, thanks, but i've already done that! yo! i reset all the settings back to the factory default! 

and about the ram...don't think that would be the problem because my computer is practically brand-new, with 4GBS of memory! i hardly think that's the problem!

Again, thanks for replying, and looking forward to ur NEXT reply!

:lolflag:

---

### Post by prshah on 2008-12-02
> **Jammanuser said:**
> 
received the following error: "crc error" and then on next line "system halted"!!!

Memory error? Oh but then Vista shouldn't run... won't hurt to check it though. Use a live CD, and choose the option to "Test Memory" (or "memtest")

---

### Post by magmon on 2008-12-02
Windows automatic updater. Like, when you shutdown, has it installed/configured updates? Or, has the little blue thing with the windows icon apeared in the bar by your clock?

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> If vista is bugging you, Im a pro with that lol. Download CCleaner, change your AV to Avira, install online armor, install adaware, and auslogics disk defrag. After all those are up and running, and a scan/fix from all of them has been done, your computer will be running like new!

hmm...no offense, but i already **have** ccleaner, and ran a scan with it not too long ago, and removed all my privacy files (thank goodness!!! :)); personally, i prefer AVG Internet Security to Avira, and ran a scan with AVG just recently too, but it found no problems...my favorite anti-spyware is CounterSpy (from sunbeltsoftware.com), which i also used recently and removed the annoying spyware that it found!! :) i'm also running a defrag right this second, by the way!!

HAHAHA!!! so **basically** what i'm saying in response to that, in case u haven't noticed, then, is THANKS but NO THANKS!!!! 

Cheers! :guitar:

EDIT: oh! one more thing! just for the record, CounterSpy came out as #1 in a review, while Adaware came out...u guessed it! LAST!!! HAHAHA!!! sorry...i couldn't resist!

---

### Post by magmon on 2008-12-02
Avira has more than a 10% higher detection that avg. And, adaware is more intuitive and better than counter spy. So, basically what Im saying in responce to that is that I offered the BEST programs, found from 2 years of vista use. Use what you like, but dont ask for help if you dont want the answers.

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Avira has more than a 10% higher detection that avg. And, adaware is more intuitive and better than counter spy. So, basically what Im saying in responce to that is that I offered the BEST programs, found from 2 years of vista use. Use what you like, but dont ask for help if you dont want the answers.

hmm...uhh...if u don't mind me asking, what r ur sources to make such a statement as that???? CounterSpy came out on top in the review that i read! :)

and of course i wanted some answers...otherwise i wouldn't have asked!!! 

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Windows automatic updater. Like, when you shutdown, has it installed/configured updates? Or, has the little blue thing with the windows icon apeared in the bar by your clock?

oh...yeah, sure! :) Windows has installed several updates, not only BEFORE the crc error, but also after!

not sure how this relates to my problem...but yeah!

Looking forward to ur reply...

---

### Post by magmon on 2008-12-02
Lol, w/e. Either way, avira owns your nooby little AVG. But, that is totally unrelated to ubuntu, and if I get into an argument we will both end up banned xD.

---

### Post by Jammanuser on 2008-12-02
> **prshah said:**
> Memory error? Oh but then Vista shouldn't run... won't hurt to check it though. Use a live CD, and choose the option to "Test Memory" (or "memtest")

actually, i've already tried that...the memtest that is! although, i ran it from my wubi install itself, instead of the LiveCD! admittedly, i didn't let it finish, because i didn't have the patience to wait several hours until it got done!

anyway, i'm fairly certain that my RAM'S not the problem...my computer is practically brand-new...how could it be???

Looking forward to ur reply... :guitar:

---

### Post by lisati on 2008-12-02
> **magmon said:**
> Lol, w/e. Either way, avira owns your nooby little AVG. But, that is totally unrelated to ubuntu, and if I get into an argument we will both end up banned xD.

Keep on smiling! I'm sure we can cope with the occasional difference of opinion over preferred apps without it deteriorating into full-scale war!

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Lol, w/e. Either way, avira owns your nooby little AVG. But, that is totally unrelated to ubuntu, and if I get into an argument we will both end up banned xD.

again...where is ur source to back up such a claim, i wonder...?

anyway, personally, regardless of the detection ability of AVG vs Avira, i prefer it because of all the neat little features its jam packed with! lol :guitar:

---

### Post by magmon on 2008-12-02
Heh, unfortunately I have my fathers temper. But I agree, its just the somewhat condesending mannor in which he said that he had stuff that got me. Which, is why I attempted to change the subject lol

You want neat features?! Go for avast! I personally think its odd, but it looks cool xD.

---

### Post by Jammanuser on 2008-12-02
> **lisati said:**
> Keep on smiling! I'm sure we can cope with the occasional difference of opinion over preferred apps without it deteriorating into full-scale war!

agreed! thanks, lisati, for the support...i'll take that to mean u prefer AVG! HAHAHA!!!! :) 

:guitar:

---

### Post by magmon on 2008-12-02
Prefer what you will, when you get a virus and Avira killed it, I doubt you'll be laughing =P. At least install threatfire! Its a really cool behavior sensing AV that works with your current AV.

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Heh, unfortunately I have my fathers temper. But I agree, its just the somewhat condesending mannor in which he said that he had stuff that got me. Which, is why I attempted to change the subject lol

You want neat features?! Go for avast! I personally think its odd, but it looks cool xD.

i wasn't speaking (typing) in a "somewhat condescending manner" (u spelled "manner" wrong, by the way!:))...i was merely commenting on the fact that i already had CCleaner, as well as antivirus/antispyware programs, and have already got all that out of the way! sorry if it appeared that way to u, lol! 

:guitar:

P.S. AVG is still better!

---

### Post by magmon on 2008-12-02
Mehehehe, I never claimed to be able to spell xD

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Prefer what you will, when you get a virus and Avira killed it, I doubt you'll be laughing =P. At least install threatfire! Its a really cool behavior sensing AV that works with your current AV.

incidentally, i think overall Vipre (also from sunbeltsoftware.com) is possibly the BEST AV you'll ever find, detection wise, but take what u will! :)

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Mehehehe, I never claimed to be able to spell xD

that's good! because u sure can't...

:guitar:

---

### Post by magmon on 2008-12-02
Ill have to look at that. But, personally I still like avira. Btw, your a post behind xD

Edit: Bah, you posted as I was typing... And I love how you used "u" in telling me that I cant spell haha

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Ill have to look at that. But, personally I still like avira. Btw, your a post behind xD

Edit: Bah, you posted as I was typing... And I love how you used "u" in telling me that I cant spell haha

hope u do...btw NOW look who's a post behind?

:guitar:

EDIT: "u" is a short form of YOU...people use it all the time, and it doesn't reflect inability to spell, like urs did...

---

### Post by magmon on 2008-12-02
At least I noticed it >.>

---

### Post by 1hunter8 on 2008-12-02
I agree with you!![img]http://links.longhainet.com/haha.jpg[/img]-----------------------------------------------------------------------------------------------------------------------------------Signed Network: Not A Bad Man, A Woman Does Not Love!Recommendation:[Die Casting Mold](http://www.hitop-mould.com/die-casting-mold.asp) / [Stainless Steel Jewelry](http://www.aab-co.com/stainless-steel-jewelry.asp) / [Jewelry Manufacturer](http://www.aab-co.com/jewelry-manufacturer.asp) / [Rubber Casting Molds](http://www.mold-sources.com/products0view251/Rubber-Casting-Molds.html) / [Custom Mold](http://www.mold-sources.com/products0view236/Custom-Mold.html)

---

### Post by lisati on 2008-12-02
> **Jammanuser said:**
> agreed! thanks, lisati, for the support...i'll take that to mean u prefer AVG! HAHAHA!!!! :) 

:guitar:
:)
Kinda going off AVG a bit since support for the Ubuntu-friendly version I've used in the past is said to be on its way out, but discussions on that is probably better suited to a separate thread.

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> At least I noticed it >.>

good thing u did too...wouldn't have known what to do without it! 

:guitar:

---

### Post by magmon on 2008-12-02
Who would have what now o.O?? Anyway, Im off to browse the other forums, ttyl.

---

### Post by Jammanuser on 2008-12-02
> **lisati said:**
> :)
Kinda going off AVG a bit since support for the Ubuntu-friendly version I've used in the past is said to be on its way out, but discussions on that is probably better suited to a separate thread.

ha! i KNEW it! :) ok...cool! i'll say no more on the subject here!

:guitar:

---

### Post by utnubuuser on 2008-12-02
Hey, did I miss something, or is wubi only one way of installing for a dual boot?

I recently installed 8.04 on a acer laptop by resizing the existing windows partitions,(using gparted), making room for ubuntu, (on the right side), then going through a regular install,  
This way, not only is it a nice clean install, but it actually improved the performance of the windows partitions as well.

---

### Post by muniquelareyn on 2008-12-02
[http://linuxgazette.net/issue50/tag/24.html](http://linuxgazette.net/issue50/tag/24.html)

Many says this site works best.Ubuntu has issues reading the hard drive. Damage or compatibility may cause errors. 

 be [ Fitness Good](http://www.gymfitnessexerciseequipment.com/ )

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Who would have what now o.O?? Anyway, Im off to browse the other forums, ttyl.

again, poor English...but i was talking (i mean typing! :)) about the fact that i could have done without ur "useful" advice, referring to the AV programs, of course! (i meant it **sarcastically** of course!)

i'm off as well...

:guitar:

---

### Post by lisati on 2008-12-02
> **Jammanuser said:**
> ha! i KNEW it! :) ok...cool! i'll say no more on the subject here!

:guitar:

How's the search for a solution to the CRC error you've experienced progressing?
I won't suggest the CHKDSK and malware scans again as they've already been mentioned here and elsewhere, I'm beginning to wonder if a fresh install is an option.

---

### Post by Jammanuser on 2008-12-02
> **1hunter8 said:**
> I agree with you!![img]http://links.longhainet.com/haha.jpg[/img]-----------------------------------------------------------------------------------------------------------------------------------Signed Network: Not A Bad Man, A Woman Does Not Love!Recommendation:[Die Casting Mold](http://www.hitop-mould.com/die-casting-mold.asp) / [Stainless Steel Jewelry](http://www.aab-co.com/stainless-steel-jewelry.asp) / [Jewelry Manufacturer](http://www.aab-co.com/jewelry-manufacturer.asp) / [Rubber Casting Molds](http://www.mold-sources.com/products0view251/Rubber-Casting-Molds.html) / [Custom Mold](http://www.mold-sources.com/products0view236/Custom-Mold.html)

thanks for the support! at least i got ONE person that agrees with me that the ubuntu people **really** should come up with a fix or workaround to the crc error while booting!!! :)

now if only we could get a few more...

:guitar:

---

### Post by Jammanuser on 2008-12-02
> **lisati said:**
> How's the search for a solution to the CRC error you've experienced progressing?
I won't suggest the CHKDSK and malware scans again as they've already been mentioned here and elsewhere, I'm beginning to wonder if a fresh install is an option.

well...the fresh install is what i was going to attempt as a LAST resort!!! i was really hoping for someone to have come up with a fix for the error, by now! :(

the search is not going very well...

right now, i'm in the process of trying to figure out how to download 'Tomsrtbt' from [http://www.toms.net/rb/download.html](http://www.toms.net/rb/download.html) 

all the options i've clicked on so far, either did not work, or sent me to a page on which could not be found the app!

Hope i can eventually figure it out... :confused:

---

### Post by Jammanuser on 2008-12-02
> **utnubuuser said:**
> Hey, did I miss something, or is wubi only one way of installing for a dual boot?

I recently installed 8.04 on a acer laptop by resizing the existing windows partitions,(using gparted), making room for ubuntu, (on the right side), then going through a regular install,  
This way, not only is it a nice clean install, but it actually improved the performance of the windows partitions as well.

i'm beginning to think that installing ubuntu on a partition, to begin with, and not even using wubi at all (at least when ur dealing with Windows Vista...as i am!) might be the best option! probably i wouldn't be having this crc error right now if i had done that, instead of using wubi...oh well! :(

at least YOU had enough sense! :guitar:

---

### Post by magmon on 2008-12-02
Lisati, Ive got a question. So many people are reporting this issue, do you know how common it is? Id really love to avoid this, as ubuntu has become my main OS.

---

### Post by magmon on 2008-12-02
Pssh, Im with ya all the way man, if I get hit with this I dont wana be left without ubuntu.

---

### Post by ago on 2008-12-02
that is likely a hardware issue, not much we can do about

---

### Post by ago on 2008-12-02
Could you please refrain from spamming this forum, one thread on a topic is enough.

---

### Post by ghostworkz on 2008-12-02
First off, I have a dual boot system with Vista and have ZERO problems.  I would 1.) check your hardware and 2.) Research how to dual boot Ubuntu and Windows without using Wubi.

---

### Post by Jammanuser on 2008-12-02
> **ago said:**
> that is likely a hardware issue, not much we can do about

i disagree! :popcorn: in this particular instance, at least, i am quite certain that it is not a hardware issue, as my computer is practically brand-new! my problem seems to be Vista-related, as the most likely cause for getting the crc error in the first place was probably doing an improper shutdown, to which, i might add, i had no other choice, because Vista froze up!

but putting aside the reason why i got this error in the first place, i **really** wish someone would come up with a fix or workaround at least to this problem on wubi!!!

):P

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Lisati, Ive got a question. So many people are reporting this issue, do you know how common it is? Id really love to avoid this, as ubuntu has become my main OS.

u want to avoid it? then my advice is to avoid using wubi period, and instead install ubuntu on a separate partition...which is what i should've done to begin with! if i had only done that...then i would probably not be having this issue right now with the crc error! :guitar:

word to the wise: install ubuntu on a separate partition than Windows...don't trust wubi to do the job for u!

:popcorn:

---

### Post by Jammanuser on 2008-12-02
> **ago said:**
> Could you please refrain from spamming this forum, one thread on a topic is enough.

sorry about all the threads on the same issue, but the reason that i did it was because everyone seemed to ignore my first two threads on the issue, and i figured that if were to post it several times, i was bound to eventually get some answers, if only to tell me not to spam the forum! :p

i apologize...on a different note, is it possible to upgrade wubi to a separate partition, even when not able to get into wubi...maybe using the LiveCD?

Looking forward to ur reply... ):P

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Pssh, Im with ya all the way man, if I get hit with this I dont wana be left without ubuntu.

good...don't make the same mistake that i made! ;) install ubuntu on a separate partition, and i guarantee that u will have a **lot** less problems...at least with ubuntu booting, at least!

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-02
> **ghostworkz said:**
> First off, I have a dual boot system with Vista and have ZERO problems.  I would 1.) check your hardware and 2.) Research how to dual boot Ubuntu and Windows without using Wubi.

hmm...i wonder how long u have had the dual boot...

again, it is most **certainly** not my hardware that's the issue here...and concerning doing research...i'm doing that right now...here, as well as other places! yo!

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-02
say...has someone moved all my threads on the same subject into this one? it seems that i'm seeing here my postings on different threads...

:guitar:

---

### Post by Jammanuser on 2008-12-02
> **muniquelareyn said:**
> [http://linuxgazette.net/issue50/tag/24.html](http://linuxgazette.net/issue50/tag/24.html)

Many says this site works best.Ubuntu has issues reading the hard drive. Damage or compatibility may cause errors. 

 be [ Fitness Good](http://www.gymfitnessexerciseequipment.com/ )

say...u wouldn't happen to know, would u, how to download Tom's Root/Boot from the link mentioned in that page?

i've been having trouble finding the place to download from!

Looking forward to ur reply... :lolflag:

EDIT: never mind...i finally found where to download from! thanks for **not** answering... :D

---

### Post by Jammanuser on 2008-12-03
Man...Tom's Root/Boot is WAY outdated!!! it was made for either Windows 97 or GNU/Linux! neither of which OS i have...and i sure as hell ain't going to downgrade to Windows 97 from Vista! ;) shiiiit...if VISTA sucks this much, i can't even imagine how sucky 97 must have been/be!!!  

so it appears there's nothing in terms of options for me then...other than to reinstall wubi! :(

---

### Post by Jammanuser on 2008-12-03
Bump...its appears that this is now an empty forum...

*Waiting for more answers* ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-04
ANYONE???? ):P

-jammanuser

;)

---

### Post by Jammanuser on 2008-12-06
Bump. :D

-jammanuser

;)

---

### Post by prshah on 2008-12-07
> **Jammanuser said:**
> Bump...its appears that this is now an empty forum...

> **Jammanuser said:**
> ANYONE????

> **Jammanuser said:**
> Bump

I think by now it's pretty clear that no one has answers to your problem. Maybe you should either wait a while for more answers or reinstall your wubi installation, or look at [LVPM]("http://lubi.sourceforge.net/lvpm.html") to try to convert your wubi installation to a dedicated installation (if possible).

In either case, I suggest you stop bumping and/or creating new threads on a topic no one can currently seem to answer.

If you feel the forum has been of no help to you, don't complain here. Most people will call that "troll"ing behavior.

---

### Post by Jammanuser on 2008-12-07
> **prshah said:**
> I think by now it's pretty clear that no one has answers to your problem. Maybe you should either wait a while for more answers or reinstall your wubi installation, or look at [LVPM]("http://lubi.sourceforge.net/lvpm.html") to try to convert your wubi installation to a dedicated installation (if possible).

In either case, I suggest you stop bumping and/or creating new threads on a topic no one can currently seem to answer.

If you feel the forum has been of no help to you, don't complain here. Most people will call that "troll"ing behavior.

sorry...didn't mean to troll! :( as for reinstalling Wubi...i'm doing that right this instant! ;)

Cheers! :D

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-08
Whoopee! :D :D :D

My problem has been solved! 

To see what I did to fix it, see this thread: [http://ubuntuforums.org/showthread.php?t=1004180](http://ubuntuforums.org/showthread.php?t=1004180)

I hope that everyone else who has the same damn "crc error" will also fix it, using the info that i describe in my other thread! ;)

Cheers! :D

-jammanuser

):P

---

