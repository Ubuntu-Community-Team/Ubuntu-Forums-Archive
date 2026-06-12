---
title: "Help with installing Kubutu"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by EdZ on 2006-01-21
I am currently dual booting w2k and Kanotix. I would like to install Kubutu over the Kanotix partition, and give Kubutu a try. I've tried the install routine a number of times but the section on partitioning is a little confusing to me and don't want to take the chance of messing up what is already working. Any help with the would be appreciated.

---

### Post by matthewv on 2006-01-21
You will need to find the Kanotix partitions, erase them and replace them with then allow ubuntu to use the free space on the drive. There will most likely be 1 partition, of type ntfs, another of type swap, and then 1 or more of type ext3 or reiserfs. Delete the ext3 or reiserfs partitions, and then allow the partitioner to use the free space. Warning: this will erase all data from your current Kanotix partitions.

---

### Post by EdZ on 2006-01-21
Matt, 

Thank you for your quick reply and help. I tried again with a little more courage and lots of risk. I&#8217;m now able to dual boot w2k/Kubutu.   


EdZ 
South Central PA

---

