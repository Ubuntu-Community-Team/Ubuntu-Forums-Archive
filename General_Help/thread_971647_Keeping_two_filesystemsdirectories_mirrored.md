---
title: "Keeping two filesystems/directories mirrored"
date: 2008-11-05
forum: General Help
---

### Post by mtausig on 2008-11-05
Hy!

I would like to keep two directories (respectively mounted filesystems) in a continuously mirrored state. 
Or in other terms: I am looking for something like a RAID-1 but on a filesystem level.

Does somebody know, if such a thing exists?

cheers
Mathias

---

### Post by fjgaude on 2008-11-06
When you say "continously" you mean within milliseconds of changes to the master?

---

### Post by mtausig on 2008-11-07
More or less, yes. What I want to achieve is kind of a mirroring-RAID, but across two differnet hosts.
For isntance, if I have the directory /important-data on my local harddisk and a NFS volume mounted on /remote, I would like these to directories to be mirrored all the time. 
I am aware, that I could just get a NAS and export it to both servers, but I actually want to avoid acquiring yet another device.

cheers
Mathias

---

### Post by fjgaude on 2008-11-08
The only way I can think of and this will take some digging to understand what is required: **rsync** running with **cron**, and set to update every minute or so. Files will be copied if they have changed, after making both drives identical.

I use **unison** to keep my laptop updated, but only once or twice a day. I don't know cron but do use **grsync** for local and off-line backups, so others will have to help you, or you will have to study up and do it yourself.

Others may know of a better way, but this is my only thought. I can't see how to do software mirror, raid1, over a LAN or WAN.

---

### Post by bodhi.zazen on 2008-11-08
You could mount --bind or link ?

mount --bind /dir1 /dir2
ln -s /dir1 /dir2

Otherwise , +1 for cron + rsync.

---

### Post by fjgaude on 2008-11-08
> **bodhi.zazen said:**
> You could mount --bind or link ?

mount --bind /dir1 /dir2
ln -s /dir1 /dir2

Otherwise , +1 for cron + rsync.

Wound **bind** or **link** make two directories, filesystems identical?

---

### Post by bodhi.zazen on 2008-11-08
> **fjgaude said:**
> Wound **bind** or **link** make two directories, filesystems identical?

no, it keeps 1 copy of a directory and makes it accessible in more then 1 location.

Usually mirroring is used between machines while links or mount bind on a single machine.

I am just wondering, why would you sync two directories on a single machine rather then a link or mount --bind.

I was thinking that a link or mount --bind would be easier and consume less resources then mirroring with rsync / cron.

---

### Post by fjgaude on 2008-11-08
"across two different hosts", so we think of a LAN or WAN situation, eh?

Links and DNS are not what is needed here, I don't think. <smile>

---

### Post by bodhi.zazen on 2008-11-08
Ah, I missed that somehow, I was confused by "something like a RAID-1 but on a filesystem level"

---

### Post by mtausig on 2008-11-10
> **fjgaude said:**
> "across two different hosts", so we think of a LAN or WAN situation, eh?

Links and DNS are not what is needed here, I don't think. <smile>

It should at least be across two different filesystems to make sense.

Well, but obviuosly, there is no real solution apart from manual syncing. Still, thank you for the effort guys.

---

### Post by mtausig on 2008-11-21
If someone else is interested in that matter:
I just found [http://www.drbd.org]("http://www.drbd.org"), which is at least similar to what I wanted.

---

### Post by fjgaude on 2008-11-21
Okay,very interesting; can you tell us what one or two of the DRBD devices cost?

---

### Post by mtausig on 2009-01-08
I didn't com round to trying it yet, but as far as I understand it, it doesn't matter what devices you use. ITs a piece of software, that can be used on any two PCs/server machines.

---

### Post by detroit/zero on 2009-01-08
Not that I'm any sort of expert on anything discussed here, but I would think that some bash scripting making use of the ls, diff and cp commands, along with some creative usage of ssh/scp, would get the job done. you would have to manually execute the script, but you could also set cron to run it once an hour/every 5 mins/every minute. I would also think you could write something in python, or even bash again, to detect when a change to the folder in question has been made and to execute the script then.

Just one thing: Don't ask me to do it. ;)

---

### Post by hyper_ch on 2009-01-08
can't you just mount the directory in one location through sshfs?

---

### Post by mtausig on 2009-01-08
Thanks, but since I have to handle critical data which always has to be consistent, doing something manually/every minute is far from good enough.

---

### Post by mtausig on 2009-01-08
> **hyper_ch said:**
> can't you just mount the directory in one location through sshfs?

That won't help, since I need the filesystem mirrored in different locations.

---

### Post by detroit/zero on 2009-01-09
Somebody mentioned it on page 1, but you may want to go read up on Unison:
[http://www.ubuntugeek.com/unison-file-synchronization-tool.html](http://www.ubuntugeek.com/unison-file-synchronization-tool.html)
Sounds like what you're looking for, and it's highly customizable.

---

