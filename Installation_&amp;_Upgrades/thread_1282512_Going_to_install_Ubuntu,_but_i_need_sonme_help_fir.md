---
title: "Going to install Ubuntu, but i need sonme help first."
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Onforty on 2009-10-04
Hey guys, i am a 13 year old computer geek. My parents both work with computer and i growed up with computers. Since i was 8 i have always been interested in Linux/Unix machines and programming. Finally after 3 years i decided to take the jump, so now i sit 19:09 Danish time, ready to put that Ubuntu disc into my drive and rebooting. I did that terrible mistake to re-install and format my hard disk. Atleast i got a backup now.
I got my graphics card up and run thanks to my father, but my sound driver is missing. 
 
 
However i need to know about some things:
 
1. Is gcc included?
2. I installed Windows Xp first,
now, how do i make Ubuntu co exist with our dear old buggy bloaty windows?
3. Does Steam run on Ubuntu by Wine?
4. Will it run on my computer?
5. Is it compatible with soundblaster?
 
Specs:
 
Amd Sempron Processor 3000+ 1.81 Ghz
2 GB Ram.
ATI Saphire X1650PRO
Logitech and Microsoft pheriphals
I bought it 5 years ago.
 
 
Ps. My pc once broke down on a virus. My hard-disk jumped from 320 GB to 90 GB then to 79GB. How do i fix it?
 
Respond a fast as you can.
 
With a nice warm salute,
David aka Onforty, DarkWing, whatever..

---

### Post by howefield on 2009-10-04
> **Onforty said:**
>  
1. Is gcc included?
2. I installed Windows Xp first,
now, how do i make Ubuntu co exist with our dear old buggy bloaty windows?
3. Does Steam run on Ubuntu by Wine?
4. Will it run on my computer?
5. Is it compatible with soundblaster?

1. Yes.
2. During the installation process, you will have the opportunity to resize your windows partition to make room for Ubuntu. Read very carefully each screen/step before committing the disk to changes. 
3. Yes.
4. Boot up with the live cd, if it all works, you should be ok.
5. Yes.

With the live cd booted, open a terminal and type

```
fdisk -l
```

and post the output here, it will help in answering your last question regarding your hard disk.

---

### Post by Onforty on 2009-10-07
Alright mister. Gotta reboot,

---

### Post by Mark Phelps on 2009-10-07
Since you're using an ATI x1650 card, you won't be able to install restricted drivers, which means you won't get 3D hardware acceleration.  Don't know, but I wouldn't be surprised if that prevented installing or using Steam.

And, before you ask, NO, you can not use Wine to install device drivers.  So, even though there may be an ATI driver for your card in MS windows, you can't use that in Ubuntu or Wine.

---

### Post by ritche on 2009-10-07
Hi, did you get ubuntu installed after? I'm new to this as well, and made the jump to install the 9.04 version on my machine. 

I'm not sure what happened, but now, when the computer starts, it just goes to the Grub command line. Did I miss something? Everything seemed to install fine booting from the CD and walking through installation steps, but then it rebooted and I get this Grub command line screen now. Am I supposed to edit a kernel or a config file to boot to Ubuntu? I can't seem to find anything online about it. Everyone else seems to be booting to Ubuntu after that.

---

### Post by ikisham on 2009-10-07
ritche, you should open a new thread to ask your question.
GRUB is the bootloader. Through its window you can choose which operating system to boot if you have more than one and edit the boot options if you need to troubleshoot something.
Ubuntu will boot automatically after a countdown or you just select its entry and press <Enter>.
If you want to know how to edit GRUB's menu so it doesn't show up at the boot time, please open another thread so it doesn't mix with this one.

---

### Post by Onforty on 2009-10-07
Oh (Poo releated word)!
That means i cant brag to my nerd friend that i runned HL2 on Ubuntu :|
Well, theres one Con. And there might be a thousand cons, maybe even a million.
And only one pro: Everything is free, and you can edit the spagetthi code laying behind it, maybe another one: You can use nearly "any" hardware, just not a ATI card. Maybe another one: You dont have to get Visual Studio, you got GCC. But what is 3 Vs a Million? Who wins? The Pro's or Cons? I think as a very careful and scared virus suffering windows user that its the cons that wins.

Also, fdisk sounds like "format disk", i got paranoid and skipped that.

One happy thought:
It looks like that the ATI card is supported anyway, things are clearer than Windows, no flickering, no strechted things, the close animation is 3d and runs smooth. But that might just be the fact that Ubuntu has a nicer GUI than Dirtywindows DeadSmiley. Well, i posted this in a Ubuntu Live CD Session, was ******* happy with that it runned, but then a sad tired franctic face froze on me when i heard that i couldnt run Steam. A dream of a perfect operating system crushed there.

Well, happy Ubuntu'ing, and thanks for the warning.
So that was all, wait no: Give me more than 5 pros differing from the ones i posted, and i might decide to install Ubuntu.

I wasent trolling, i hate trolls, they should burn in hell.

Onforty.

Edit: Forgot to tell that i run Steam on MS Windows, without installing any driver for running Steam games, ofcourse i had to install a driver for the card itself. But wouldnt Ubuntu recognise my card, and do 3D accelleration anyway? Also i know that you cant install drivers trough Wine, as that makes no sense...

---

### Post by Bartender on 2009-10-07
I feel a little awkward talking to such an intelligent 13 year old kid.  It's kind of unnerving.  I don't expect you to understand that, Onforty, it's just that an old guy like me tends to think to himself, "Was I this smart at 13?" and when you realize probably not it's a bit intimidating.

If I may make a suggestion.  Keep XP.  I think for right now it's the only avenue that makes sense.  But don't use it for anything that you don't have to.  Back up your personal data, wipe the drive clean (hopefully that will solve the "shrinking HDD phenomenon") install XP to a primary partition, install Ubuntu and swap (and a shared NTFS partition if you want) as logical partitions inside an extended partition.

Load XP up with a good free firewall like Comodo or Zone Alarm, antivirus, three or four spyware apps, and DON'T GO CRUISING THE NET ANY MORE THAN NECESSARY WITH XP.

Boot into Ubuntu for email, web browsing, etc.  This way you can play your games and get a chance to learn what can and cannot be done in Ubuntu.  I get the feeling there's a push to make games Linux-compatible.  Maybe by the time you're 14 or 15 you can dump Windows altogether.

---

### Post by Onforty on 2009-10-07
Oh thanks for the advice Bartender. (If i spelled that incorrectly, sorry.)
You really putted my nerves down again, your idea is perfect.
Well, Wine's list of App's running with it shows up with: Half-Life 2.

Though i am a smart young boy, i am not perfect. Example: I suffer Schizo (Very weak, and only very light person mess-up.), i only have one friend, i have to take pills, i am so god-damn high that i bump to the ceiling (Or how it spelled) when i am in old houses.. alot more. Just like Linux! I got some Pro's and some Cons's.

---

### Post by raymondh on 2009-10-07
> **Onforty said:**
> Oh thanks for the advice Bartender. (If i spelled that incorrectly, sorry.)
You really putted my nerves down again, your idea is perfect.
Well, Wine's list of App's running with it shows up with: Half-Life 2.

Though i am a smart young boy, i am not perfect. Example: I suffer Schizo (Very weak, and only very light person mess-up.), i only have one friend, i have to take pills, i am so god-damn high that i bump to the ceiling (Or how it spelled) when i am in old houses.. alot more. Just like Linux! I got some Pro's and some Cons's.

As an add-on tip:

1.  If you're going to take space from windows to do a dual-boot ... defrag windows first.  2x if you have the time.
2.  in step 4 of the installer, you'll have an option to choose "side-by-side".  When you do so, remember to use the slider (below) to allocate partition sizes or you'll end up with a 2.5GB ubuntu install which is not enough for the first update.

Have fun and happy ubuntu-ing :)

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

Regards,

---

### Post by Onforty on 2009-10-09
Im going Ubuntu today or tomorrow.
Im happy that BYOND runs in Linux, that allows me to chat with Windows friends, while playing around with Ubuntu.

Also, book recommendations:

Moving to Ubuntu Linux (The author of "Cooking with Linux" made it)
Jon Erricsons "Hacking" (Teaches alot about Linux and C and stuff.

Ps. Kirk Hammet FTW :guitar:

---

### Post by Onforty on 2009-10-12
Been away in some time, now I finally installed Ubuntu.
One FDISK -1 is coming up!
Ps. Will a 30 GB partition do the job??

---

### Post by raymondh on 2009-10-12
> **Onforty said:**
> Been away in some time, now I finally installed Ubuntu.
One FDISK -1 is coming up!
Ps. Will a 30 GB partition do the job??

30GB is OK.  Just remember that when you save personal data/media ... you only have 30GB.  Have you thought/considered separating your /home from root?

Regards,

---

