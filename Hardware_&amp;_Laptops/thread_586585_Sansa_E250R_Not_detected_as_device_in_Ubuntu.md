---
title: "Sansa E250R: Not detected as device in Ubuntu"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by dab on 2007-10-22
Hi,

 I've spent the last few days interacting with this Sansa E200R that I bought a few weeks ago -- and interacting with a new camera -- only to realize how most of the engineers of these machines do not plan on having their hardware connected to a linux machine. Thankfully, with my SD card reader, my MicroSD adapter, and RockBox's read and write permissions to the little card, I've been able to get a whole lot done.
 The first thing I screwed up with RockBox was to turn off the LCD display using Sleep (After Backlight Off): Always. -- Took forever to get past that problem. 

 But I'm digressing (which I'll continue to do, because it's 6:00 in the morning and I'm off to work at 8:00, and insomnia has taken all of my candor~~apologies).

 My Sansa E250 with Rhapsody (a product that originally attempted to digitally manage my rights?) works beautifully with RockBox. I was already mad that they crammed 1.68GB of .rax files on to the player with out my consent and that their recorder recorded in lossless .wav files. But then I realized that my OS isn't supported by the people at SanDisk (or at least it seems that way).
 After a few hours spent on getting RockBox installed (just days before the standard installer came out, which helps boost my nerdy self confidence a smidgen) with my boss' XP computer, I begin realizing just how much I would have been screwed with the original OS anyway. 
 "I don't have XP at home..." I wonder... "Is this thing going to play nicely with the computer at home?" I was sure that linux would work nicely with linux. But I'm sure that the problem, now, is not a software issue within the player.
 Anyway, to make a long story short: I connected this player to my computer and it's not detected in /dev/usb (nor in /media) by the standard rockbox utility / installer. It really seems like the documentation, faqs, wikis, etc, have been aimed at the majority of the people who use the internet (that is, people who have a copy of windows running).
 I loaded the old firmware (the 5.5mb original firmware, OF.mi4?) via recovery mode which gave me the tiny 16mb partition -- detected by linux -- and gave me a tiny idea that my linux might finally begin to work with the old firmware. 
 Alas, connecting Samsa with the old firmware yielded no 3.82 gb drive. Connecting Samsa with better firmware yields no 3.82 gb drive. Before any one asks, I'm misspelling on purpose: the little video on the sansa reminds me of Gregor Samsa, from Kafka's The Metamorphosis. Samsa is a great name for this black liquid-metal and plastic encased piece of poor nerds' dream.

 Anyway, if I could get any information on where this topic was already covered, or where exactly in the manual I can RTFM, it would be appreciated. Perhaps it's even new subject matter, hopefully not inappropriate to this particular forum, and warrants unique response. And if there isn't any response, that's cool--I'd gotten used to that a long time ago--I'll just keep plugging away.

 More information about my hardware and software:
 From Rockbox:
Rockbox Info
Version: r15073-071010

Buffer: 28.552MB
Battery: 26% 1h 20m
Int: 1.74GB/3.71GB (the .rax files are taking up 1.68GB of my space)
mSD: 980MB/982MB (attempts to excise these diabolical files via microSD have failed, ah! I want to develop and customize the RockBox, and I don't have access to the machine, so sad...)

 From Ubuntu Linux 7.10:
  "Ubuntu 7.10
                - the Gutsy Gibbon - released in October 2007" -- said the documentation page.
 Hmm... I wonder if there's other information I can give you, that I can't think of at the moment because my thought process is riddled with insomnia?

 Anyway, thanks for reading,

 Dominick

---

### Post by breakerr on 2007-11-09
Sorry to reply for nothing since Im in the same boat with you *sniff* I just started googling about it....wish me luck and if you get any info let me know, Ill do the same back for you if I get some luck.

**so far this is the best I had found**: [http://ubuntuforums.org/showthread.php?t=312196](http://ubuntuforums.org/showthread.php?t=312196)

---

### Post by spencedaman on 2008-01-28
I have the same problom except slightly diffrent my sansa c240 has an option in it to auto detct itself and ubuntu recoginizes it as a media device but ubuntu dosent recognize my sansa e250r as a media device any sugestions?

---

### Post by Titus A Duxass on 2008-02-07
My e250 works okay with ubuntu (but not with SuSE 10.3).
Do the following:

[COLOR="Red"]With the player DISCONNECTED[/COLOR]

go to: settings => USB Mode => scroll to MSC and press the centre button.

Now connect the player you should see the e250 appear plus any install micro SD cards.

The other mode (MTP ) will only function with Windows Media Player.

---

