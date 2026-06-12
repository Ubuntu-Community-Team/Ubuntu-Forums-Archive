---
title: "partition &quot;root file&quot;not found"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2009-04-24
I had to do a fresh install of 8.10/vista dual boot because my keybord stopped working(only in ubuntu).I need the keyboard to work to upgrade to Jaunty so i thought fresh install of 8.10 would be quick fix.From live cd i got to partition page and picked 'guided'and it partitioned to
dev/sda1 NTFS   276444MB 
dev/sda6 ext3    112118MB   34881used
dev/sda5 swap     4795MB
dev/sda2 NTFS     6718MB     5779used

now when i hit forward a pop up window tells me 'no root file is defined please correct partition menu'and takes me back to above page.I remember something about a '/' to be put in somewhere in past installs (i think its called a 'mount point') but i dont know how or where to put it.There are little boxes in a 'format'  colloum but i cant seem to use them. When i click a box the whole line gets highlited and im at a loss from there.Does that make sense to anyone that can take me to the next step cause now im afraid to do anything like hit 'quit' or 'back' in case i lose everything

---

### Post by drs305 on 2009-04-24
In the partitioning section, if you select to manually select the partitions, you would highlight sda6, which looks like the partition on which you want to install ubuntu. On the right side there will be some options. Normal users select ext3 as the format. There is also a "Use as" box that you have to click on and you would select " / ". That is the root partition. 

Here are a couple of installation guides. They are for 8.04 but still apply. The second one shows pictures of what you will see for manually selecting the partitions.

[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

[URL="http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml"]
_http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml_[/URL]

---

### Post by jesse c on 2009-04-24
thanks for reply drs305.My problem was that i had started the partition as a 'guided' install so the process was not like the tutorials but they did give me enough clues as to risk going forward.For the record i used your advice to assume sda6 was what i needing to mess with,so i highlited it and then hit the 'edit partition'bar which brought up a whole list of stuff (format types i guess,things like fat32,fat 16 and more i cant remember now) so i clicked on "ext3 journaled file system' and crossed my fingers and hit 'ok' which brought back the partition list with the little box on the format coloum checked now and i was now able to put the'/' on the line and when i hit 'forward' everything seems to be going ok.

---

