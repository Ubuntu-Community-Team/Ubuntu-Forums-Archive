---
title: "Ipod Shuffle won't work on Ubuntu 10.10"
date: 2011-02-20
forum: Hardware
---

### Post by Acheron3 on 2011-02-20
Hi, 
I own an Ipod Shuffle (first generation) and it worked ok on Ubuntu till I upgraded from 10.04 to 10.10.
When I installed Ubuntu 10.10 it was detected by Rhythmbox but I wasn't able to update it. I've tried lots of programs (gtkpod, floola, hipo...) but nothing seems to work for me.
I tried to reinstall all the packages related to ipod in Synatptic (I just made a search for the key "ipod") and I probably deleted something I shouldn't because since then Rhytmbox has stop detecting it.
Is it possible to make this ipod work with Ubuntu 10.10? What Ubuntu packages do you need to work with an ipod?

Thank you ;-)

Cheers

---

### Post by darkmire on 2011-02-20
> **Acheron3 said:**
> Hi, 
I own an Ipod Shuffle (first generation) and it worked ok on Ubuntu till I upgraded from 10.04 to 10.10.
When I installed Ubuntu 10.10 it was detected by Rhythmbox but I wasn't able to update it. I've tried lots of programs (gtkpod, floola, hipo...) but nothing seems to work for me.
I tried to reinstall all the packages related to ipod in Synatptic (I just made a search for the key "ipod") and I probably deleted something I shouldn't because since then Rhytmbox has stop detecting it.
Is it possible to make this ipod work with Ubuntu 10.10? What Ubuntu packages do you need to work with an ipod?

Thank you ;-)

Cheers

I've got one of these and had the same kinds of problem.  As I don't use iTunes decided to use it as an mp3 player by just transferring the sound files over to root directory the shuffle.  They will then work quite happily on any linux media playing package.   However, if you do this the shuffle won't work off the computer without running a python script called rebuild_db  which rebuilds the shuffle's internal database so it will read the files you transferred, otherwise they are invisible to the shuffle.  The only issue is that rebuild_db has to be run each time you add or remove files from the shuffle.   [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/) gives you details.

---

### Post by Acheron3 on 2011-02-21
It works! Thanks!!:popcorn:

---

