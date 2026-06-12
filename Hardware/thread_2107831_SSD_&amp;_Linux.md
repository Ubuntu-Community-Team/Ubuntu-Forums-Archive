---
title: "SSD &amp; Linux"
date: 2013-01-22
forum: Hardware
---

### Post by bman on 2013-01-22
So it's going to be that time soon to upgrade. Going to be building top of the line which includes an SSD for my main OS. Might even have just that one SSD, and have a server somewhere else for all my other stuff.

I know this has been asked before, I just wanted to make sure the answer is directly to my situation.

Any problems with installing any version of Ubuntu or other Linux onto an SSD? Are all the benefits there with Linux? Anything extra I have to do when installing it/after installing?

Anything else I might need to know. 

Also, this will be my first time using an SSD.

---

### Post by offgridguy on 2013-01-22
Someone else asking a similar question here.

[http://ubuntuforums.org/showthread.php?t=2107019](http://ubuntuforums.org/showthread.php?t=2107019)

To reiterate what i said there, i treat my SSD just like any HDD,  I don't know if that is 
recommended or not, but so far no problems.  If there are special considerations i would
like to know myself, as i haven't heard of any.:p

---

### Post by natesymer on 2013-01-22
You have to add the discard option to your fstab if you have a non-sandforce drive. See [here]("http://askubuntu.com/questions/18903/how-to-enable-trim"). Additionally, I have heard that the Crucial M4 has built-in garbage collection...

Anyhow, the idea is to be a little write conservative. Moving a file around on a single partition is not a write, moving it between partitions IS. Just try not to do too many writes. I think MLC can take 750TB of data (16GB/day for 100 years) written to them before they become readonly due to lack of write ability.

Also, if you have enough RAM (>16GB) you can decrease your swappiness value to increase the life of your SSD.

I personally have an Ubuntu machine running dual SSDs. One is an OCZ Vertex 4 with the discard enabled, while the other is an OWC Mercury Electra 3G. The OWC drive holds all of my personal stuff, and it is also where I point netatalk to for my AFP volume for my family's macs.

Anyway, welcome to the SSD crowd!!!

---

