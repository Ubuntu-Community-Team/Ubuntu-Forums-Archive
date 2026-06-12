---
title: "Hard Drive HElp PLease"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by enzodad on 2009-05-28
Hello. I been useing vista for a few months now due to software i am not able to use with ubuntu. I love ubuntu though and am switching back. BUT in vist i use my 150gbs HDD as primary installation ect and i have a secnd HDD120gbs that is used as /d but as more storage they arent in raid nor combined. The second harddrive is just mass storage lol. I would like the same setup in ubuntu, one hd as extra storage. When i clicked install it gave me option to select install for any one of the drives but i am not sure how to set up one as install one as storage can anyone give me  artards guide thanks :):KS

---

### Post by lindsay7 on 2009-05-28
You can use your home directory as storage if you set it up that way. Do the manual install option. If your current second hard drive is just a data drive now. I would repartition it using the live Gparted program which you can download (go to the Gparted web site) as an ISO image and burn it to a cd. It will boot from your cd drive and you can shrink you current partition and set up two new partitions. One of the new ones should be set up as the / mount point and the other as /home. check the box to format as ext 3 or ext 4 and the Ubuntu install disk will do the rest. Be sure not to check the format box for the existing data partition that you already have.

---

### Post by IsmAvatar on 2009-05-28
You will want to resize the Vista partition. But before you do this, make sure that you have defragged Vista, so that everything is in one clump on the hard-drive, so that when you do resize, you don't overwrite anything that was outlying.
It's kind of like cropping (resizing) a photo (analogy to Windows) so that you can fit another picture (linux) next to it in a page in a picture album (analogy to Hard Drive).

---

### Post by enzodad on 2009-05-28
Thanks ill give it a shot ill actuly be ditching vista .. using ubuntu  from now on

---

