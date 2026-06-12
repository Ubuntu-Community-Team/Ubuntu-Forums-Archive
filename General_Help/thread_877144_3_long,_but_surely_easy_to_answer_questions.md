---
title: "3 long, but surely easy to answer questions"
date: 2008-08-01
forum: General Help
---

### Post by schmidtbag on 2008-08-01
I know the background info is long but please read all of it carefully, it is significant.  I appreciate your patience.





For some background information:
     I had an ata 40GB hdd that had ubuntu on it.  It worked fine until I put in this new mobo.  Linux couldn't boot up all the way.  Not even the live CD could read it correctly (except Gparted, but that wasn't going to help), it was classified as an SCSI device.  I'm not really sure why this was, so I installed windows on this separate 160gb sata drive I have.  Windows could read the drive perfectly fine (I have programs that can read ext3)
     Anyways, I split the 160gb into 3 partitions - one was a 40gb fat32, another was ext3, the last was where windows xp was stored.  i thought i could migrate my 40gb hdd but apparently the program can't copy TO ext3, so i just copied everything manually to the fat32 partition.
     I no longer have the 40gb drive in at all - just the 160gb.  I have no use for windows anymore, so now the last partition is changed to a 512mb swap space.

So now to my questions:

1.  How can I copy my Ubuntu stuff from the fat32 partition to the ext3 partition?  I'm running the Ubuntu Live CD but it says I don't have the permission to do so.

2.  After the copy, I want to make the fat32 partition into ext3 (I know how to do that) and then I'll be copying the data back to that.  What I want to know next is how can I make both ext3 partitions combined?

3.  If I copy all the data to the new ext3 filesystem, will it still boot up?



Again, thank you very much for taking the time to answer my questions.  I hope they're simple to answer.  I need some luck.

---

### Post by LowSky on 2008-08-01
When you change significant hardware (like a motherboard) you should really do a clean install
what I suggest is just grabing important files you might have on the drive and start new.

---

### Post by schmidtbag on 2008-08-01
Well thats sort of the problem - I'm trying to copy the files but the Live CD won't let me due to permission issues.  I am aware a clean install is the best choice, but IF everything still works with my previous install then I don't see why I should start over.  Would you still have an answer to my 2nd question?

---

### Post by LowSky on 2008-08-01
use gparted to creat the ext3 partition then copy the data over then delete the fat32 partion. You can make a partion larger by tell ing gpart to extend the size of the partition. It may Corrupt data i don't suggest it. You would be better off just saving you /home folder and reinstalling everything else.

and for #3 no it wont you will need to recreat your MBR use a super grub disc for that.

---

### Post by schmidtbag on 2008-08-01
thanks for the answer to #3, but again, i can't copy ANYTHING.  gparted won't help, i need to be super user but idk how on the live cd.

---

### Post by dentaku65 on 2008-08-01
You can try in this way (for copying files):

First on live cd create your user that is present on ext3 partition
```
sudo useradd -m username
sudo passwd username

```

Then type:
```
su username
```

Then open your Fat32 disk:
```
nautilus /media/<your_fat32_partition>
```
and see if you can copy and paste to your 
/media/<your_ext3_partition>

---

### Post by schmidtbag on 2008-08-01
dentaku, thats exactly what I need, but i made some changes to what you said myself since not all of what you said worked.  i'll post again to mention my current status

---

### Post by schmidtbag on 2008-08-01
OK, so I repartitioned everything, Super GRUB did as much as it could but Ubuntu still doesn't start up, and now I'm just wondering if theres a way I can keep all my installed programs and settings but reinstall the OS itself.

---

### Post by dentaku65 on 2008-08-01
> **schmidtbag said:**
> OK, so I repartitioned everything, Super GRUB did as much as it could but Ubuntu still doesn't start up, and now I'm just wondering if theres a way I can keep all my installed programs and settings but reinstall the OS itself.

I'm not sure to have understood well... but I suggest to copy all the directory /home/<yourname> in an external hard-disk (this saves all your config/setting files, application I think does not matter), then reinstall Ubuntu and applications you want throught synaptic or apt... or, if you are able to boot in Recovery Mode (from grub), maybe you are still able to recover the present installation (for example: installing a previous kernel throught apt...)

---

### Post by schmidtbag on 2008-08-01
well I was hoping I could copy my /usr or /bin folder and entirely replace the old ones.  If I set myself to the correct user and replace them, do you think it will work?

EDIT:
nevermind, didn't work.  i guess i'll just reset everything

---

