---
title: "Warning For Dell Inspiron Users"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by Mr Fat Bat on 2006-05-17
I have a Dell Inspiron 6400.  It "worked" very well until one day for work reasons I changed my BIOS boot sequence to:

1. CD/DVD
2. USB drive
3. Hard Disk

After saving the settings and exiting the BIOS I restarted, the computer pauses about 3/4 of the way through the Dell load screen and then goes to black screen with the message:

> Time-of-day clock stopped 
After a long conversation with the Dell people, and after trying all of their suggestions a technician was sent out to replace my motherboard.  

He came, he fixed, everything booted.. great.

Until.... I changed my boot settings back to the way I needed them... BAM the same error again!

Back on the phone to my friendly Australian Dell Support Agent (in Singapore), they are resolving the issue now.  I will let you know if they find a solution that doesn't involve replacing the motherboard!

I'll post as soon as I know... but until then... Dell Inspiron people, don't change your boot sequence!

---

### Post by Mr Fat Bat on 2006-05-17
UPDATE:

They are sending out ther guy with a new motherboard.  We'll then flash update the BIOS and then change the boot sequence!

I'll keep you posted..... *sigh

---

### Post by mimp on 2006-05-18
If you do a search there's already a thread on this, and it's been reported as a bug in dapper as well. Seems to be a problem with the last few versions of the dapper kernel.

The good news is you can fix the problem simply by removing the coin-cell battery for a few seconds and replacing it again.

The bad news is that if you damage your computer in the process of taking it apart to get at the battery then the damage isn't covered under your warrenty, so if you're paranoid like me you have to wait three days before a dell technician comes along and spends 5 minutes fixing your machine.

Although re-reading your post maybe this is a seperate issue as it appears you never got as far as ubuntu before it broke.

Oh and this is in breezy. mega-odd.

---

### Post by Mr Fat Bat on 2006-05-18
Yeah the Dell boot screen is pausing before the option to hit F2 or F12 even appears, so you can't even get back into the BIOS to change it back.  The Dell man is coming today to replace my motherboard... i'll make him stay around while I change the boot sequence again and if it breaks then I think i'll look around for a laptop that supports letting you boot from CD then USB then HD and not die ;)

---

### Post by Mr Fat Bat on 2006-05-19
Okay all done!

We installed a brand new motherboard and then flashed the bios and all is well.  Now it's back to trying to get that **[COLOR=Red]DAMNED [/COLOR]**[COLOR=Red][COLOR=Black]card reader to work ;)[/COLOR][/COLOR]

---

### Post by vinil on 2006-05-19
i remember that before get the "time-of-day clock stopped" i enter to the bios and change some settings, then i could't boot.

dell replaced my motherboard, and by now is working fine...

i use dapper flight 6.

---

### Post by nischg on 2006-06-07
It's not quite on the subject but I think this could be for interest for you guys:

I am on a Dell 6400 now with Dapper on it. I've managed to solve almost every issue but two things are holding me from saying bye to Win XP. They are described in this post [http://www.ubuntuforums.org/showthread.php?t=190167]("http://www.ubuntuforums.org/showthread.php?t=190167") 

I thought that we could create a guide or how-to for this laptop and Ubuntu with all our problems and solutions so far so we can help each other out. I do not know if a thread on this great forum would be the best or we could make a wiki or something. If someone else is interested in this please contact me. I do have little time but I am willing to do everything I can to help others with an Inspiron. I can offer 24/7 hosting for anything on this subject.

Thanks

---

