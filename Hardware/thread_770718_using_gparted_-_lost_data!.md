---
title: "using gparted - lost data!"
date: 2008-04-27
forum: Hardware
---

### Post by miguelitu on 2008-04-27
I was preparing my pc for installing ubuntu 8.04.

I had a 6gb partition that were not using anymore, so in gparted i used copy and then paste in my home partition...

i thought that would just copy the files into the home, but what happened it was it deleted all files i had in my home directory and now its has the files of the 6gb partition...

anyway of recovering it?

i believe no, just wondering... im mostly a basic user, but i believe it should be a more specific warning on that... 

for me copy & past doesn't mean erasing all data of the target partition...

cheers and i would appreciate any help.

---

### Post by pytheas22 on 2008-04-27
You can install some recovery tools to try to get your files back:
```

sudo apt-get install testdisk
```

Then run the program photorec:
```

sudo photorec
```

and tell it to search the partition that currently resides where /home used to be (or the whole drive).  photorec usually does a good job of finding files, although it can't recover their names, only their content, unfortunately.

You can also run testdisk:
```

sudo testdisk
```

to try to fix the partition structure.  testdisk can find partitions that accidentally were overwritten/deleted and attempt to restore them.  I've never used it but it's supposed to be good.  There's another utility called gpart (distinct from gparted) that you could also try if testdisk fails.

Also, keep in mind that if you use testdisk to try to change the partition table of your disk, you risk causing other problems, so make sure you backup important data from all partitions before using testdisk.

---

### Post by miguelitu on 2008-04-27
thanks for the reply!

i´ll work on that now

---

### Post by miguelitu on 2008-04-27
testdisk coulnd retrieve the old partition, and photorec did find some files, but as you said without names

i gave up... i have a backup of the important stuff

just going to lose some time ripping and downloading some stuff.

now i wanna know if the dumb one here is me or the copy & paste in gparted should be more clear, or at least more "alarming" 

thanks again, pytheas22

---

