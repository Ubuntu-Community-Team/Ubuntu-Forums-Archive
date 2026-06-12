---
title: "How is Support for Non-Wacom Tablets"
date: 2009-10-25
forum: Hardware
---

### Post by hocmin on 2009-10-25
My Wacom Bamboo Fun died on me and I'm wondering how support is for non-wacom tablets; Genius and Adesso in particular.  Anyone have first-hand experience working with one in Ubuntu?  Any documentation?

Thanks

---

### Post by Visible Spirit on 2009-11-06
**Hi all,**


I'm wondering the same thing. I was going to start my own thread on this subject and then ran across this thread via a forum tag search.

I have an [Adesso Cyber Tablet 12000]("http://www.adesso.com/index.php/en/home/tablets/159-cybertablet-12000") graphics tablet and would like to know if there's any Linux drivers and/or software support for this model? I've installed Xournal which somewhat works with my tablet, but the stylus cursor isn't stable nor am I able to calibrate the tablet to the screen area. I've also tried using it in GIMP to no avail with the same result/problem. I'd really like to use this tablet on Linux if it's possible.

If no one has or is working on a solution, is there anyone out there willing to tackle this project?

I'll gladly upload the software/driver CD that came with it if someone wants to work up a stable solution. On the CD is factory support for MS-Windows 2k-XP(Vista?) and Mac OSX OS's, so I would think there's a solution for Linux. Or you can download the .zip file with new drivers from the page linked above for MS-Windows 2k-7 and Mac OSX-(update -- you must now register membership to access Adesso website downloads as of March 2010). My offer to upload driver(s) from disc still stands -- PM me?. I'm not a programmer and haven't a clue how one would go about this. Any takers?

Anyone have any suggestions, ideas, or leads to a solution or a work in progress?

*Any* help would be greatly appreciated.


[B]Thanks,
Visible Spirit[/B]

OS = Ubuntu Studio v8.04 LTS

---

### Post by tudor117 on 2009-11-06
Hi have a Genius G-Pen F610. It works ok in Karmic.
I had to patch the wacom driver to get it to work though. In Jaunty it was fine.
Also, there are two extra buttons on the stylus but they both do the same thing regardless of config. Other than that, it's great.

---

### Post by Visible Spirit on 2010-03-21
**Bump.**

Still looking for a solution. Please read post above.


Thanks,
Visible Spirit

---

### Post by tudor117 on 2010-03-21
This is from quite some time ago. ;)
Anyways, from what I understood about tablets, here are some tips. First, tablets are made by major companies (wacom, waltop, wizardpen, etc) then rebranded into something else. For example the tablet I have is branded as a Genius; but the base is a Waltop.
The best way would be to figure out what brand your tablet is. Most of them have some kind of driver for linux. Try doing *lsusb* or maybe even better *lsusb -v*.
Aha also do *xinput list*.

---

### Post by Visible Spirit on 2010-03-21
Hi tudor117,


Thanks for the input. Much appreciated! I'll check into this and see what I can come up with. ;)


Regards,
Visible Spirit

---

