---
title: "adding a new ext3 partition to / partition..."
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-05-29
i hav Ubuntu 8.10..working with LiveCD option now...i used Gparted to resize a partition n created some unallocated space next to my '/' (root) partition...then formatted it to ext3...my '/' also ext3...

now i want to merge these two partition to increase the size of my /home partition..

BTW,while installin 8.10 i didnt give a separate mount point for /home..
wat should i do now to increase my /home partition size?

---

### Post by merlinus on 2009-05-29
Info on creating /home here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by vpnm_87 on 2009-05-29
i followed the link u gave me to create separate /home partition...everything went well..but when i gave

find . -depth -print0 | cpio --null --sparse -pvd /new/

cpio: ./valliappan/.thumbnails/normal/b46aa61f412b8df5c10461864f718a35.png: Cannot stat: Permission denied

i used even 

sudo find . -depth -print0 | cpio --null --sparse -pvd /new/

but same error...

I am using LiveCD now..

---

### Post by drs305 on 2009-05-29
My guess is that you have one or more files owned by root in your /home directory and that is why it is not allowing you access to this file.

You would have to put "sudo" after the pipe as well - before cpio, but don't do that. Better to change the owner of that specific folder to yourself to make sure you don't mess up too many permissions.

So try this, assuming valliappan is your username:
```

sudo chown -R valliappan: ./valliappan/.thumbnails/normal/

```

Then try the command again.

---

### Post by vpnm_87 on 2009-05-29
when i gave the command u suggested i got this error

chown: invalid spec: `valliappan:'

my user name is 'valliappan'..any command to check my username?or any other solution?

BTW,i took backup of all my important files..i just want to create a separate /home partition of 14 GB without messing up my root file system..else i have to install all updates from the beginning..

---

### Post by drs305 on 2009-05-29
I was assuming that ./valliappan/.thumbnails/normal/ is in your HOME folder and that your username is "valliappan".
I missed that you were in the LiveCD. 

Run the command from the normal boot process - the LiveCd doesn't know who you are. You can also try this so you don't have to be in a specific folder:
```

sudo chown -R valliappan:valliappan $HOME/.thumbnails/normal/

```

I've got to go but I'll try to come back with some other options or see how you have gotten along tomorrow.

**Added:** If you want to stay in the livecd, you might try moving the thumbnail folder into a system partition and worry about it after you have completed moving $HOME and are back after a normal boot. You could move the folder now with the command below:
```

sudo mv ./valliappan/.thumbnails/normal /root/Desktop

```
If this works (the only folder with permission problems) don't forget to move it back to $HOME later (and probably change the permissions as well).

---

