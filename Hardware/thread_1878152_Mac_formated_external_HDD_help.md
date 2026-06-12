---
title: "Mac formated external HDD help"
date: 2011-11-09
forum: Hardware
---

### Post by spitnllama on 2011-11-09
I just installed Ubuntu 11.10 on my HP pavilion dm4 laptop and I love it. My last computer was a imac 27" and i backed up all my data on a 2TB external hard drive.The things is that i don't have the mac any more but i have all the data on the external. When i try to open the main folder on the external ( it has a gray x on the corner of it) i get a message that tells me i don't have permission to open this folder. I have looked every were for a guide to walk me through to opening my external but with no success plz help?

---

### Post by coffeecat on 2011-11-09
There are two problems.

1 - MacOS supports the same system of Unix permissions as Ubuntu, but the UID of your Mac files is (probably) 501, whereas the UID of your Ubuntu account would be 1000 if the first created account. You would also have a different GID (group ID) between Ubuntu and the Mac files. The "other" permission in your Mac files is probably 0, i.e. no access for other users. 

2 - Your Mac external drive is almost certainly formatted with the journalled version of HFS+ which can be mounted read-only in Ubuntu which means you cannot change the permissions in Ubuntu. (You can mount it read-write with a force option but I wouldn't advise that.)

There are several workarounds.

In Ubuntu, you could open a root nautilus with:

```
gksu nautilus
```

Navigate to the external Mac drive and you will be able to access and copy anything. The disadvantage is that after copying to Ubuntu, the files will be owned either by root or by UID=501 - I can't remember which - and you will need root privileges to change the ownership. Easily done, and post back if you need help with that.

Or - do you have access to another Mac? You can change all the "other" permissions recursively in the Mac GUI, or you can run "sudo chmod -R 777...." in a Mac terminal. That will give you full read-only access to all your files as an ordinary user in Ubuntu. Again, post back if you need help with either of those.

Or - you can disable the journal in MacOS which would make the drive read-write in Ubuntu, but I wouldn't recommend that until you've copied your files.

---

### Post by spitnllama on 2011-11-11
Thnx coffeecat when i access the extenal drive the way of gksu nautilus all my files but one come up as plain text documents.

---

### Post by coffeecat on 2011-11-11
What happens after you copy them to your Ubuntu drive?

**EDIT**: a thought. When you backed up your files from the iMac, did you use a simple drag-drop copy or did you use special backup software?

---

### Post by spitnllama on 2011-11-11
When i coped the files to ubuntu they are the same as they appear on the external blank document files. When i backed up my data. I used the time machine function that the mac offered at the time it seamed to be the hassle free approach. Oh i forgot to mention that there one small group of files that i could open that were normal, but the bulk of the data is all blank document files.

---

### Post by coffeecat on 2011-11-11
Yes - I wondered if it was Time Machine. I must admit the only experience I have of Time Machine is dismissing the Time Machine prompt whenever I plugged a USB drive into my Mac Mini. From what I remember of TM is that it does incremental backups. It's possible that the normal files are the originals and all the seeming text ones are incrementals that can only be unscrambled or put back together with Time Machine. Tbh, that's only a theory - I'm not sure.

You've intrigued me now, so I'm going to do a bit of searching around to see if this might be the case. In the meantime, do you have access to another Mac?

**EDIT**: if I'm reading this Wikipedia article correctly, my theory is sort of half-right:

[http://en.wikipedia.org/wiki/Time_Machine_%28Mac_OS%29](http://en.wikipedia.org/wiki/Time_Machine_%28Mac_OS%29)

Sorry - beyond reconstructing your archived files with another Mac, I really don't know how you could do this.

---

### Post by spitnllama on 2011-11-11
unfortunately i don't have any one right now that has a mac. I just moved overseas for a bit and every one over here have acer laptops but i will ask around. thnx coffeecat for your help to understand this cuz all the guides that i read were for the external HDD that apple sells that have wifi [http://www.omgubuntu.co.uk/2010/11/connecting-to-your-apple-time-capsule-in-ubuntu/](http://www.omgubuntu.co.uk/2010/11/connecting-to-your-apple-time-capsule-in-ubuntu/) but they didn't work.

---

### Post by coffeecat on 2011-11-11
If I understand that link (it's not that clear) I think that's a way of reading your Time Machine backup files from Ubuntu, but via a running Mac which you connect to over the network. What you need is a way of reading the TM files directly in Ubuntu. I found this:

[http://hints.macworld.com/article.php?story=20080623213342356](http://hints.macworld.com/article.php?story=20080623213342356)

See if that helps to find your files.

---

