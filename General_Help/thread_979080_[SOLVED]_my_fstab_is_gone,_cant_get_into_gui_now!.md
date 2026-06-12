---
title: "[SOLVED] my fstab is gone, cant get into gui now!"
date: 2008-11-11
forum: General Help
---

### Post by severean0 on 2008-11-11
S0rry, this is a bit 0f a tricky 0ne. Im really stuck and have searched the f0rums f0r an answer.
Im running 8.10 0n an inspir0n lapt0p.
I was trying t0 get my wind0ws partiti0n t0 m0unt aut0matically, f0ll0wing instructi0ns in :
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
But I seem t0 have messed up my Fstab because when I restarted, ubuntu w0uldn't l0ad, s0 n0w im in the Live CD searching f0r help. I created a backup 0f Fstab, which I can see fr0m here but I can't save it 0ver the 0riginal versi0n which I screwed up ! 
N0vice s0rry!
Any help greatly appreciated.

---

### Post by severean0 on 2008-11-12
bump. d0es any0ne kn0w h0w t0 edit files in \etc 0f an0ther partiti0n when l0gged 0n t0 the live CD? It says I d0n't have permissi0n, s0 is there any way 0f m0unting the partiti0n as r00t user 0r whatever?

---

### Post by geirha on 2008-11-12
Hit alt+f2 and run ```
gksu nautilus
``` which will give you a nautilus window run as root. It should have the needed privileges to replace the broken /etc/fstab with the backup.

---

### Post by severean0 on 2008-11-12
S0rry. That w0n't w0rk because I'm l0gged in t0 the live CD. My n0rmal ubuntu partiti0n w0n't l0ad, presumably because 0f having screwed up fstab. I guess I either need t0 find a way 0f editing Fstab back t0 the backed up versi0n fr0m the live CD, 0r s0meh0w getting my n0rmal ubuntu user acc0unt t0 l0ad. This is what it l00ks like at the m0ment when I b00t the c0mputer:
"C0uld n0t start the X Server due t0 s0me internal err0r. PLease c0ntact y0ur system administrat0r, 0r check y0ur sysl0g t0 diagn0se. In the mean time this display will be disabled, PLease restart GDM when the pr0blem is c0rrected."
 
THen i've g0t the c0mmand pr0mpt:
"lapt0p l0gin:"


any ideas?

---

### Post by geirha on 2008-11-12
> **severean0 said:**
> S0rry. That w0n't w0rk because I'm l0gged in t0 the live CD. My n0rmal ubuntu partiti0n w0n't l0ad, presumably because 0f having screwed up fstab.

«Won't load», do you mean you are unable to mount it from the live CD? 

> **severean0 said:**
> 
I guess I either need t0 find a way 0f editing Fstab back t0 the backed up versi0n fr0m the live CD, 0r s0meh0w getting my n0rmal ubuntu user acc0unt t0 l0ad. This is what it l00ks like at the m0ment when I b00t the c0mputer:
"C0uld n0t start the X Server due t0 s0me internal err0r. PLease c0ntact y0ur system administrat0r, 0r check y0ur sysl0g t0 diagn0se. In the mean time this display will be disabled, PLease restart GDM when the pr0blem is c0rrected."
 
THen i've g0t the c0mmand pr0mpt:
"lapt0p l0gin:"


any ideas?

Are you able to login at the console (command prompt)?  If so, you could copy the backup with something like:
```
sudo cp /path/to/fstab_backup /etc/fstab
```
Then run ```
sudo mount -a
``` to see if there are any errors mounting.

---

### Post by severean0 on 2008-11-12
> «Won't load», do you mean you are unable to mount it from the live CD? 


Sorry, I meant to say I can't load my normal ubuntu system, as I get the error message I mentioned before. If I load the Live CD, I can mount my normal system's partition, but just can't edit the fstab file because I don't have permission. 

> Are you able to login at the console (command prompt)? If so, you could copy the backup with something like:

Code:
sudo cp /path/to/fstab_backup /etc/fstabThen run 
Code:
sudo mount -ato see if there are any errors mounting. 

If by that you mean when GRUB loads, select Ubuntu recovery mode, yes I can access the command prompt from there I think, I will try it out later.

---

### Post by geirha on 2008-11-12
> **severean0 said:**
> Sorry, I meant to say I can't load my normal ubuntu system, as I get the error message I mentioned before. If I load the Live CD, I can mount my normal system's partition, but just can't edit the fstab file because I don't have permission. 


Then running "gksu nautilus" in the live session should give you permissions to replace /etc/fstab.

---

### Post by severean0 on 2008-11-12
Yep that worked, thank you very much f0r y0ur help. D0 y0u happen t0 kn0w the best way t0 c0nfigure an ntfs partiti0n t0 m0unt aut0matically at startup?

---

### Post by geirha on 2008-11-12
I'd go for an entry like this in /etc/fstab
```
UUID=*abcd1234* /media/*mount-point* ntfs-3g defaults,uid=*yourusername*,gid=admin,dmask=002,fmask=113 0 0
```

To find the UUID, run ```
sudo blkid
``` the mount-point you choose must be created first ```
sudo mkdir /media/*mount-point*
``` and of course replace *yourusername* with your username.

The above line will make it automatically mount on boot, and it will be writeable to *yourusername* and members of the admin group, and only readable to everyone else.

When you've added the line, run ```
sudo mount -a
``` which will attempt to mount all entries in fstab that would be automatically mounted on boot. If it mounts your ntfs-partition with no errors, you shouldn't get any surprises during next boot.

---

### Post by Jakey_TheSnake on 2008-11-12
Provided the NTFS partition is shut down correctly, it should mount automatically. Mine did anyway. 

Otherwise you can use the terminal to force mount it using "sudo mount -t -ntfs-3g /dev/sda1 /media/disk -o force" or something similar, it's in the details section if you expand the error message anyhow.

---

### Post by severean0 on 2008-11-12
> I'd go for an entry like this in /etc/fstab
Code:

UUID=abcd1234 /media/mount-point ntfs-3g defaults,uid=yourusername,gid=admin,dmask=002,fmask=113 0 0



is this line 0f c0de in additi0n t0, 0r instead 0f the line that exists f0r that pariti0n already in fstab? 

> the mount-point you choose must be created first
Code:

sudo mkdir /media/mount-point




What p0int sh0uld I ch00se as the m0unt p0int 0n the wind0ws drive? If I just wanted t0 use the r00t 0f that partiti0n (Which in wind0ws w0uld be C:\), h0w w0uld I d0 that? D0 I navigate there in the terminal and then run mkdir /media/mount-point?

---

### Post by geirha on 2008-11-12
Modify your existing line to look like the one I gave you.

As for the mount point; let's take an analog to windows. In windows, when you mount a filesystem, the mount point is a letter. C: for the first one, and other file systems get mounted to D:, E:, F: etc. In ubuntu, the ubuntu partition is mounted as / (linux's C: you could say) and all other partitions are mounted on directories inside /, so if you call your mount point /media/windows for example, then after mounting, you should see the contents of C: in windows under /media/windows. E.g. /media/windows/WINDOWS corresponding to C:\WINDOWS ...

You don't need to navigate anywhere in the terminal. Just open a terminal and type for example: ```
sudo mkdir /media/windows
``` The path starts with a / which means its an absolute path. The command will do exactly the same no matter which directory you are standing in.

---

### Post by severean0 on 2008-11-12
Thanks f0r the explanati0n - makes a l0t m0re sense n0w. It's w0rking fine n0w. pr0blem s0lved, many thanks !

---

### Post by -Zeus- on 2008-11-12
so, i just had to ask:  is there something wrong with your 'o' key?  cause it is really annoying to have to take 2x as long to read your post to try to help you.

---

