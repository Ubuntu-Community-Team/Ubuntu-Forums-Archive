---
title: "Ubuntu reports many bad sectors but vendor's tools don't"
date: 2010-02-03
forum: Hardware
---

### Post by rbaleksandar on 2010-02-03
Hi, guys :)

  A couple of days ago I started receiving warnings from Ubuntu that there are many bad sectors every time I attach my external hard drive (WD Studio Edition 1TB). Since I have such problem for the very first time (believe it or not, but I'm very tidy when it comes to my computer :D). I read that formatting the drive might solve the problem. But there are two things that bother me:

**1)** Right now I'm migrating (fully) to Ubuntu from Windows. I'm making a backup of my data on the Windows partition in order to wipe it out. So reformatting my hard drive is not a good idea. I still have about 200GB free space, but it'll be a long process to take the content of one partition (there are 5 on the external) put in a backup-partition, then format the first one and return the content there. LOL

**2)** Under Windows I used the chkdsk - no problems found. I downloaded Liveguard Diagnostic Tool (or whatever the name was) from the official site of WD - no problems found. I used a couple of other tools - still no problems found.

  I'm running the self-test right now to see what exactly's "wrong" with my WD drive. For now I see two warnings inside the table of the Palimpsest Disk Utility under Ubuntu:

**1)**Reallocated Sector Count - Warning!
Normilized: 199
Worst: 199
Threshold: 140
Value: 1 sector
**2)**Current Pending Sector Count - Warning!
Normilized: 200
Worst: 200
Threshold: 0
Value 81 sectors

All: 82 bad sectors

  I'm reading now about these things but I still can't understand how so many tools (about 5-6) don't report problems? :o It still has a guarantee (bougth it a few months ago and guarantee is 2 years) but I really don't like the idea of replacing it and/or losing all the data I have.

Any advice is really appreciated!
Cheers,
rbaleksandar

---

### Post by mörgæs on 2010-02-04
You have done the right thing. If Palimpsest (which has a known bug) reports bad sectors, then test again with other tools, preferably from the hard drive vendor, and trust the latter.

In your case, I wouldn't worry for my data. A backup is aways good, of course, but your system does not seem to be in danger.

---

### Post by rbaleksandar on 2010-02-04
Thanks for the reply! :)

  And is it important to mention that yesterday Palimpsest couldn't complete (today I haven't tried but I doubt it'll be any different from yesterday) the self-test(s)? There are three options. Neither of them finished. The progress bar shows about 90% and that's it. I waited about 30-40 minutes for the tests to complete, which according to Plaimpsest should have taken less than 10, and about an hour and 20 minutes for the extended test (or whatever the name is).

---

