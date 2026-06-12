---
title: "noob here"
date: 2008-07-15
forum: General Help
---

### Post by mahollowspe on 2008-07-15
so I have just started to install Ubuntu and I'm trying to keep my xp installed but nothing that I have read has helped so far. I have made a new partition but when installing ubuntu it only gives me the option to install over xp and not use the other partition. 

do I need to resize my xp partition? how is that done? 
is there a tutorial I can read?

Thanks

---

### Post by mikewhatever on 2008-07-15
There are lots of guides:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/Installation#Standard%20installation](https://help.ubuntu.com/community/Installation#Standard%20installation)

If you've already made the partitions you need for Ubuntu, the manual partitioning option is for you.

---

### Post by iaculallad on 2008-07-15
Make sure that you have (1) available partition besides xp and instead of taking the default (taking the whole disk), select manual editing of your disk's partition table.

---

### Post by mahollowspe on 2008-07-16
so I am in the try out of ubuntu and as the guide says I need to select the *guided-resize partition* to dual boot with windows. but I don't have that option all I have is
1. guided-entire disk
2. Manual

when I click manual then click froward when I try to use the partition I made it says no file root system defined please correct this from the partitioning menu.


 I don't think the partition I made is as big as I need it....so how do I make it bigger/resize windows. I would love a step by step guide on how to resize widows. I'm guessing I use partition editor right. but I don't want to just play around with it for fear of doing damage

BTW I have XP installed.

Thanks so much for your help

---

### Post by enchesss on 2008-07-16
Can you please give more information regarding the sizes of the drives and partitions that the installer/partitioner is showing you. Also include any other details. e.g how big is/should the drive be.

---

### Post by mahollowspe on 2008-07-16
I have one 80 gig drive. when I go to manual the new partition I made in partition editor is only 32MB... too small I know. so I guess I need to make it bigger but how.

I hope that answers your question

---

### Post by Elfy on 2008-07-16
Have you defragged your xp a couple of times? I would do that and try again.

---

### Post by mahollowspe on 2008-07-16
I have about 25 gigs free so why would I need to do defrag again? do I need to resize windows because I have not done that because it will not let me drag the size smaller in partition editor.

---

### Post by enchesss on 2008-07-16
Can you please be much clearer about the sizes of your partitions. You say that there is a 32 megab partition with 25 Gb free?

I would highly recommend buying a second HD. It would be well worth the investment if you are having these confusing issues. You can reinstall and play around in a much safer environment.

Or if you want to go with just one drive then do a guided aprtition and leave about 20gb for windows and install Ubuntu on the rest.

---

### Post by Elfy on 2008-07-16
There  is a partition editor in the system admin menu - you can use that to make yourself partitions.

Then use the manual option to install into the partitions you have made.

---

### Post by ubunutgoz on 2008-07-16
As an aside, did you consider installing Ubuntu using WUBI.  It takes care of partitions etc by iteslf and creates a dual boot menu when booting.  

Its installed as a Windows .exe file, and can just as easily be de-installed from XP's control apnel.

Just a though!

Alan

---

### Post by mahollowspe on 2008-07-16
so 
I have one partition that is 80gig with 25gig free
I just made a new partition in the partition editor but can not make it bigger than 32mb for some reason. I have not resized windows as it says to do in some of the guides because it wont go below 80 gigs..I have tried in the resize option. I guess its telling me it can't shrink?

Thanks again for all the help

edit: thanks Alan I will try that!

---

### Post by anotherdisciple on 2008-07-16
Well.. Turning off System Restore in XP may help a bunch. The Restore points are put toward the end of the partition... making it near impossible to shrink that partition.

So try this. Turn of System Restore, defrag once or twice, resize the partition, Install Ubuntu, and then if you really want to... turn system restore back on.

---

### Post by Elfy on 2008-07-16
> **anotherdisciple said:**
> Well.. Turning off System Restore in XP may help a bunch. The Restore points are put toward the end of the partition... making it near impossible to shrink that partition.

+1

Might also be worth turning off the pagefile before you defrag assuming you have a suitable amount of RAM.

---

### Post by mahollowspe on 2008-07-16
thanks for the tips but after turning off restore points I still can't shrink partition 1?

I rely want to install linux but If I keep having this problem I may just give up:(

Thanks

edit: just found this program:
[http://www.acronis.com/enterprise/products/diskdirectorsuite/](http://www.acronis.com/enterprise/products/diskdirectorsuite/)
may give it a try

---

### Post by mahollowspe on 2008-07-16
so I just found my problem I have:
4KB in bad Sectors when doing a CHKDSK
this prevents me from doing a second partition because of chance of data loss.
from what I have read 4KB is not bad... no one that I have read has been able to create a new partition with bad sectors.

but unless it gets more bad than it is I have nothing to worry about but still I can not fix this issue that I know of so I guess Linux will have to wait until I get and new HDD.

thanks again to everyone that helped:)
I'm not giving up just still looking for a solution.
I may end up installing Ubuntu on my external. is that recommended

Thanks

---

### Post by enchesss on 2008-07-16
If you do that it will alsways need to be plugged in to boot into windows as well

---

### Post by mahollowspe on 2008-07-16
so I guess I have two options.
one is to get another HDD and the other is to take a leap and go ubuntu only with no window.
:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by enchesss on 2008-07-16
From what you just said - you do not seem to have anything important on the windows installation?
If this is right then you can try to do a new installation of both.

If you need the windows that you have then just get another disk. They are fairly cheap now and you could even get away with an old 6Gb for a while until you are more confident.

If you do a new windows installation (whcih may iron out any errors) do a proper NTFS format but install it on the whole drive.

DO NOT MAKE ANOTHER PARTITION WHEN INSTALLING WINDOWS (it is easier to do this when you are installing ubuntu after you have let windows format your drive - do not do a quick format)

When windows is installed then install ubuntu and do a guided partition using all available space but try to leave about 10Gb for windows.

Hope it works

If you are keen - then just get rid of windows and use ubuntu.

---

### Post by mikewhatever on 2008-07-17
> **enchesss said:**
> If you do that it will alsways need to be plugged in to boot into windows as well

Not if GRUB is installed to the MBR of the external HDD.

---

