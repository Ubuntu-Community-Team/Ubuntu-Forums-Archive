---
title: "Windows Fat32 Read/Write"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by linedpaper on 2007-01-31
This might be more of a question for some sort of window's forum, but they all suck so if you know...

I have a fat32 partition that is supposed to be a share partition for me to be able to read/write between ubuntu and windows.  The problem is that anything I write into this partition via unbuntu does not appear in there in my windows install until I rescan the partition via chkdsk or something of that nature.  Anybody else run into this problem, and if so how can i fix it?

---

### Post by Stochastic on 2007-02-01
hmm sounds like you've run into a bug with your windows - mine didn't have any issues with that back when I still had windows.  I'd give microsoft a call and ask them why your version of windows can't see files on your fat32 partition until you rescan your hard drive.  The files obviously exist there, other operating systems can see them, but windows can't.

---

### Post by linedpaper on 2007-02-01
it worked when i ran fedora and gentoo on this same laptop.  hmm strange.   i really do just want to trash windows, but i can't seem to get away from it as i'm still in school and all of the "programs" i need that come with the books are windows only.  i've never been able to get any of them to work via wine :(

---

### Post by Stochastic on 2007-02-01
Well I don't know what to tell you.  I'm not  an expert on filesystems but if the file is able to be accessed by ubuntu then it's clearly written to that hard drive.  Windows should at least be able to see files located on the hard drive.

As for  the programs at school, I'd start asking the profs about that - maybe they'll look for books/programs that work on multiple platforms or are web-based (possibly they'll even mention it to the publishers next time they talk).  Tell them that you run Linux because its principles are based on open learning and sharing of ideas.  Tell them that you're a broke student that can't afford to buy a windows disk just for their class (that may be a lie but hey, it's a plausible case).  If they're unable to budge, then let them know you'll have to borrow a roommate's computer so it'll be a real pain in the ***.  I really don't understand why more universities don't adopt a Linux platform.

---

