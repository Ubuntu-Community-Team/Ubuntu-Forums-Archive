---
title: "384MB RAM fitted, only 128MB recognised"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by MartinJ on 2006-03-30
This is on an IBM Aptiva 2140-L46, built in 1998 I think.

The machine originally shipped with 32MB ram, I now have three 128MB modules to install.  Maximum memory for this system is 384MB, according to the IBM maintenance manual.

I have tested each module in each of the three slots, every combination with either one, two or three of them installed.  No matter what, the maximum ram reported by the BIOS is always 128mb.  Starting a live cd is also painfully slow so I'm assuming that nothing else can recognise it.

If I can manage to get more memory recognised I'll be able to properly use this system for an ubuntu install.

Don't know what make of motherboard it is, this number was on it: 
11507L5057ZJ154L4461DQ FRU07L5058 804

I'm not optimistic about getting this fixed, just thought I'd try anyway...  Any ideas?

---

### Post by Swab on 2006-03-30
What type of memory did you have originally, and what type have you put in now?   Perhaps it's the wrong speed?  I had a machine that would only accept PC100 and not PC133.. strange I know.

---

### Post by MartinJ on 2006-03-30
Old: pc66

New: pc66, all with identical part/batch numbers

---

### Post by Old Jimma on 2006-03-31
I am having the same difficulty. It is my understanding that if you must specify to Ubuntu how much memory you have, but I don't know exactly how to do that, yet. I have > 1Gb memory in 3 memory sticks, and Ubuntu is only seeing the 1st 128K... the 1st memory stick.

I'll post a reply with a solution as soon as I get one... my Ubuntu manual arrives on April 8 (Amazon), but my Linux buddies Joe and Harvey might know.

Please be patient. In searching the forums, I've seen alot of posts like this, so you are not alone... and there is a solution.

Best regards,
Phil Smith
Duluth, Ga

---

### Post by Old Jimma on 2006-03-31
*<Deleted>*


*[size=1]Double post*[/size]

---

### Post by Old Jimma on 2006-03-31
Hi:

Have a look at: 

[http://ubuntuforums.org/showthread.php?t=40668&highlight=recognize+memory](http://ubuntuforums.org/showthread.php?t=40668&highlight=recognize+memory)

I tried it, and am not sure it worked or not!  :-)

I used synaptic to find the linux image-686 then let synaptic download and install.

Phil Smith
Duluth, GA

---

### Post by mips on 2006-03-31
[QUOTE=Phil Smith]I am having the same difficulty. It is my understanding that if you must specify to Ubuntu how much memory you have, but I don't know exactly how to do that, yet. I have > 1Gb memory in 3 memory sticks, and Ubuntu is only seeing the 1st 128K... the 1st memory stick.
[/QUOTE]

This problem is not related to ubuntu w.r.t. the OPs post. He mentions that the **BIOS** only recognises 128MB. Ubuntu is not going to see anything more than what the BIOS sees. This issue is hardware related.

The issue you are referring to is where the i386 kernel does not see memory above 800-900MB which is way above 128 or even 384MB.

Could I suggest to the OP to check his BIOS settings and possibly upgrade the BIOS to the latest version. There is not much support wise on on the IBM website so you might have to give them a call but then again I don't even know if they will stiff offer supoort for a machine of that age.

Found some Aptiva related stuff here [http://home.att.net/~wymette/bookmrks.htm](http://home.att.net/~wymette/bookmrks.htm)
[http://www.resoo.org/docs/_hardware/th99/m/I-L/34787.htm](http://www.resoo.org/docs/_hardware/th99/m/I-L/34787.htm)

---

### Post by az on 2006-03-31
[QUOTE=MartinJ]This is on an IBM Aptiva 2140-L46, built in 1998 I think.

The machine originally shipped with 32MB ram, I now have three 128MB modules to install.  Maximum memory for this system is 384MB, according to the IBM maintenance manual.

[/QUOTE]

I had the same problem once, too.  It was on an older machine.

I had the wrong manual (I actually looked on the sticker inside the case, which gave me the correct information) as opposed to a pdf file I found on the net.

The maximun ram was 128 megs for that machine, so regardless of how I placed the sticks, I it would only see 96 or 128 megs of ram.

---

### Post by MartinJ on 2006-03-31
Some good advice and links there, thanks guys.

Busy at the moment but will get stuck into it over the weekend.

/Martin

---

### Post by NetMatrix on 2006-03-31
If the bios only sees 128 and the manual is correct and 384 is possible, perhaps a bios update is the answer.  Check the IBM site to see if there is a new bios flash utility.

---

