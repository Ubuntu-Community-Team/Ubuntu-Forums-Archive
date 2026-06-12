---
title: "Dapper (6.06 LTS) Boots w/ 1GB of memory -- but not 2GB"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by heykev on 2007-04-14
When I run my PC with 1GB of memory, Dapper runs fine.  When I install a second GB, Dapper fails to boot.

Changing the Grub option from "quiet splash" to "verbose" reveals that the boot process stops at:

     "Begin: Running /scripts/local-top ..."

but I don't know what that means or what to do about it.

If I return to 1GB, the problem vanishes and Dapper boots just fine.

I'm working with two 1GB memory modules.  I think the memory itself is OK because:
1) It's new.
2) Dapper will boot with either 1GB module, but not with both.

I suspected a problem with the motherboard, but:
1) I ran the motherboard's start-up memory test without error.
2) From the Grub menu I ran the Ubuntu memory test without error.
3) I booted into Windows XP without error.
All three acknowledge the full 2GB.

Any ideas?  Are there other ways to diagnose this problem?

---

### Post by Chappy7777 on 2007-04-14
I could be firing blanks here, but I'll take a stab at this one. I need more beans anyhow, [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif) 
:D 

I suggest also that you give us some details about your system. Make, cpu, etc. My wife is running a P3-1Gig Compaq. I bought her some more sdram to beef up the thing, only to get a
beep beep beep from the RAM beeper. A message came up on the screen saying that her machine will not take more than 512mgs of RAM. I am thinking this may be your problem. 

Did you ever have 2 Gigs of RAM in that machine and have it work with XP or another OS?

It's frustrating w/my wife's machine because the easiest place to upgrade is RAM, and she can't.

I am looking for a used P3 w/1Gig CPU or more. I am presently running Dapper on an old P2 that I overclocked to 500mhz. It has 768mgs SDRAM, but it is still way too slow. Tho since I am a noob at Linux, I can use the time I spend waiting for my PC to draw windows to read my book,
"Ubuntu for Non Geeks" which has made all the difference in my Linux experience.

God bless,
Chap

---

### Post by heykev on 2007-04-14
Thanks, Chap, for the response.  I suspect that you're right about the motherboard/memory compatibility, but I've satisfied all the board's memory specifications.  What I fear is that I'm within specs but that there is "bug" with the board or bios.  This board is a few years old and I already have the last bios update issued.

And like I said in the original post, the 2GB configuration only creates a problem for Ubuntu -- not for the bios self-check, not for the Ubuntu memtest, and not for Windows XP.

Any other thoughts?

FYI, the board is a Abit KG7-RAID.  The memory modules are both 1GB DDR400 PC3200 Unbuffered Non-ECC.  The memory is a recent purchase.  Here's a link to the [Crucial Tech page]("http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=84CFC8B6A5CA7304").

---

### Post by Chappy7777 on 2007-04-14
No, sorry. If you can get 2gigs of RAM to work w/XP, then I have no idea what Ubuntu could do to your system that would affect this. I think you are correct and the problem is w/your BIOS. It has to be. Hopefully someone much older in Ubuntu time will help you/

God bless,
Chappy

---

