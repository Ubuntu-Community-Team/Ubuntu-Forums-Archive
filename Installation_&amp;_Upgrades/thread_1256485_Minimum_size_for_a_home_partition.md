---
title: "Minimum size for a home partition"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by cheway on 2009-09-02
Hi guys,

I recently ran into some serious problems using Jaunty, and wondered if the size of my home partition was to blame...

I had 8 gigs for /, and 2 gigs for /home, both inside an extended partition. Is this likely to cause me problems? What is the minimum size that the /home partition can be?

---

### Post by ronparent on 2009-09-02
The size of the /home partition depends on how you plan using Ubuntu. 2 Gb is probably on the light side except for casual use with little software installed and few downloads. Even then 4Gb for /home would probably be more realistic. In my case I need 40 to 60Gb for picture files, but, I also need access to those same files from windows and would not keep them in home. Same for internet downloads (other than linux software packages). I currently find 4 Gb adequate but could expand that drastically if the need arose.

That said, unless /home is filled, that may not be your problem.

---

### Post by cheway on 2009-09-02
Thanks for the reply.

I should have mentioned - I have a separate partition for my data; video, music, etc. My home partition is literally just for my dot files. Does a small /home partition fill up with "other stuff", causing problems later down the line?

---

### Post by raymondh on 2009-09-02
My usual practice is to create a separate /home on installs larger than 30GB.  Below that, I just keep it within root.

/Home also contains config files and settings ... which may grow depending on what you install and how you work your system.  

Can I present a different perspective?   There is a common error (on a side-by-side install) where the operator disregards the slider and ends up with a 2.5GB root.  The 2.5GB root is not enough even for the first/initial update.

---

### Post by amsum on 2009-09-02
> **cheway said:**
> Thanks for the reply.

I should have mentioned - I have a separate partition for my data; video, music, etc. My home partition is literally just for my dot files. Does a small /home partition fill up with "other stuff", causing problems later down the line?

If the Home partition fill-up exceeds the limit, you will see some of the "Menu" items (like System, Preference, etc) missing. This is a sign that your Home partition has exceeded the storage quota and still your system is working just because of SWAP partition. 

The moment you free up HOME memory, it will come to normal.

---

### Post by miklcct on 2009-09-03
If you want to, you can share your /home partition between OSes and hosts:
e.g.
```

# /etc/fstab
/dev/sda1 / ext4 defaults 0 1 # ubuntu
/dev/sda2 /mnt/windows ntfs defaults 0 2 # windows
/dev/sda3 /home ext4 defaults 0 2 # home
/dev/sda4 none swap defaults 0 0 # swap
# some other stuffs below

```

---

### Post by louieb on 2009-09-03
> **cheway said:**
> I should have mentioned - I have a separate partition for my data; video, music, etc. My home partition is literally just for my dot files. Does a small /home partition fill up with "other stuff", causing problems later down the line?

I have a separate data partition too. Like you my home folder  is mostly .something files. After a year and a half of running Hardy the home folder is using  less that a  GB - over half of that Thunderbird email and Firefox stuff. 

lol one day I'll get those profiles move to the data partition too.

---

### Post by cheway on 2009-09-03
Thanks for the replies guys.

Yes, my .something files were only at the 400 meg mark, and with a 2 gig home partition I thought this would be OK. However, I wondered if the /home folder needs to contain any temporary files that may be considerably larger? Like when burning DVDs for example?

I have recently just installed intrepid again (thought I had hardware issues, so went back to an OS that I knew worked) and I have a combined / and /home in a 10 gig partition. I am going to put jaunty back on this evening, but don't know whether to seperate / and /home like I had before, or keep them combined.

My data paritition is a seperate hard disk - is it possible to create a mirror of my /home partition in a predetermined location on my data hard disk? Perhaps on startup?

---

### Post by amsum on 2009-09-03
It is always a good practice to have ROOT and HOME partitions separate. The advantage is if you want to have clean install of OS tomorrow, you will find your system setting intact.

I am not sure of your other 2 queries though...

---

### Post by cheway on 2009-09-04
> **amsum said:**
> It is always a good practice to have ROOT and HOME partitions separate. The advantage is if you want to have clean install of OS tomorrow, you will find your system setting intact.

I am not sure of your other 2 queries though...

I understand that, but I don't really want to faf around with extended partitions (can this cause problems?), plus I only have a 10 gig space to put both / and /home - if I combine them, it will give both folders more space (basically, I'm just worried that too small a home partition is what caused me such catastrophic problems before). I can then always rsync the /home folder to another location on my data drive.

---

### Post by louieb on 2009-09-04
> **cheway said:**
> I wondered if the /home folder needs to contain any temporary files that may be considerably larger? Like when burning DVDs for example?
IIRC /tmp is what most programs use for temporary storage and  it gets emptied during shutdown.

> ...extended partitions (can this cause problems?)I have not had a problem at all - Linux works well with them

---

