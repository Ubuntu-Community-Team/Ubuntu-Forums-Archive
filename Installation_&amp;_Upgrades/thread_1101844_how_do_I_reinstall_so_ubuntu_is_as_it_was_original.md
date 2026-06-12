---
title: "how do I reinstall so ubuntu is as it was original"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by drmi115 on 2009-03-20
OK.  I am new at this.  I messed up my sound on my 8.10 installation.  I need to reinstall as it was originally (when it worked!)  I inserted installation stick (on a Samsung nc10) and start ubuntu from it.  I choose to install, and get to partitioning.  When I choose manual, I just get a graphic of my disk as it is currently, and below it is a graphic with the whole disk dedicated to ubuntu.  I want to save my windows partition, and I want to format the ubuntu partitions so I don't revert to the mess I have now.  I don't see anything on the screen to help me chose a particular partition, delete it, resize it, or add a partition.  There must be some way, but it is not apparent.  Can someone help a newcomer?  I have done some searches of the database, but I apparently not asking the right questions.

---

### Post by blue13130 on 2009-03-20
On that screen there should be a option that says "manual" which will then take you to another screen where you can assign your partitions and say which ones to format and which ones to keep as is.

---

### Post by drmi115 on 2009-03-20
All I see is the two graphics I mention when I check the manual button.  Do I click on the forward button?  I don't want the whole drive ubuntu.

---

### Post by Lunx on 2009-03-20
The first graphic you see is actually a slider, you can move it back and forth to get the size you want for each partion, ie. slide it to the right to increase the size of the Windows partion.

---

### Post by drmi115 on 2009-03-20
The slider is on the guided partitioning.  I cannot access any partition via the slider except the one called dev/sda5.  When I click manual partitioning, I don't see anything except the after graphic that says 100%.  I don't want to click forward there until I know that I will not destroy my windows partition.  There is no slider when I click the manual radio button.  There must be something I do.

---

### Post by blue13130 on 2009-03-20
Select Manual then Forward.  It will not delete your partitions and will progress to the next screen which allows you to edit your partitions.  Beware the screen you progress to can delete your partitions if you are not careful

---

### Post by cariboo on 2009-03-20
When you get to the partitioning section, select **manual**, you should be presented with a screen similar to the screenshot. Highlight the partition you want to change and you will see the **Edit Partition** and **Delete Partition** buttons become enabled, all you really have to do is to mark the partitions to be formatted and continue to the next step.

Jim

---

### Post by Lunx on 2009-03-20
> **drmi115 said:**
> The slider is on the guided partitioning.  I cannot access any partition via the slider except the one called dev/sda5.  When I click manual partitioning, I don't see anything except the after graphic that says 100%.  I don't want to click forward there until I know that I will not destroy my windows partition.  There is no slider when I click the manual radio button.  There must be something I do.

Sorry, my mistake for not reading closely enough first time. Not sure how to help there, I only have Ubuntu on this box now and when I did first install with dual boot, I used the slider option. Have you read through the chapter on installation in the *[Pocket Guide]("http://www.ubuntupocketguide.com/")*?

---

### Post by drmi115 on 2009-03-20
OK. I formatted the partition where ubuntu had been.  Now, how do I designate that partition as the root?  What do I choose in the "Choose as" drop down box.  I see use as FAT 32, EXT3 journaling file system, Ext2 file system, several other journaling systems, swap area, and do not use.  How do I designate it as root?

---

### Post by drmi115 on 2009-03-20
I am installing on a laptop (Samsung nc10).  Should I choose Ext2 file system in "use as" drop down list?  Then should I choose /root as the "mount point"?

---

