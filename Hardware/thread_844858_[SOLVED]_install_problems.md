---
title: "[SOLVED] install problems"
date: 2008-06-30
forum: Hardware
---

### Post by beanhead on 2008-06-30
Any help would be appreciated, Ok I made an xubuntu 8.04 alternate iso disc to install into my girlfriends computer and it freezes when installing software packages.After a while it restarts with an os not found when it loads from bios. I know the iso is good and works because I reinstalled xubuntu to double check with my computer. I figured then maybe I would try a puppy 4.0 install tested the iso with my computer worked fine and then with her computer. It loads the kernal needed to acess disc drixes,then fails when "searching for puppy files on computers disc drives" error code sts p_up 400.sfs not found. Dropping out to initial-ramdisk console
/bin/sh:cant' access tty; job control turned off.
then i have a # and a flashing cursor.

Now i believe that it is not finding the files because im using and external cd drive. Also the xubuntu disc gave no error codes just froze and shut down.

also I set the bios to boot cd first. 

Win xp home boots and installs fine then crashes later of course because thats what windows does best.

ok computer specs for problem computer

Dell latitude ls h400 st 

model- pp01s

bios version  A09

dell latitude external cd drive 

hd shows in bios as does cd drive 

thanks for taking a look I would love to mark this solved!

---

### Post by kessaris on 2008-06-30
When I was installing ubuntu, I had to specify the partition scheme by hand (Do not use the GUIDED option).

If you can, please try specifying the partitions manually as follows:

```
/boot  70 megabytes (ext3)
swap   2*your RAM (About 700 megabytes anyway)
/home  around 60% of the space (ext3)
/      the rest of the space. (ext3)
```

On a 60 gig drive and a computer with 512 megs of RAM it would be

```
/boot  70 megabytes
swap   1024 megabytes 
/home  35 gigabytes
/      25 gigabytes
```

It's important to specify them in that order, otherwise you may get conflicts if you add / and then /home.

After you manually create the partitions, you can install ubuntu.

I had to go into the live CD and format the hard drive before running the installer.

Partitioning the drives was by far the hardest part of the installation.  I had a very similar problem where the installation seemed to complete but then it rebooted and nothing happened.

I hope this helps you!

---

### Post by beanhead on 2008-06-30
Thanks for the info but it wasn't a problem with partitioning.
Anyway the lcd screen stopped working all together now so its a trash can computer. Also im a fan of Gparted. So now im ust running pupppy linux and enjoying xubuntu on my computer.:guitar:

---

