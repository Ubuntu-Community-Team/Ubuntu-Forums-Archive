---
title: "need ftp client that supports scheduling and timetabled throttling"
date: 2008-07-22
forum: General Help
---

### Post by garethsimpsonuk on 2008-07-22
ello ppl,

well basically i have a home ubuntu server for files and printing mainly and it's gui free. i also have an xp tower and vista laptop on my desk. i have a ubuntu dedi server in a datacentre which i use for a torrents amongst other things. virgin caps me for a whole week if i download more than 5 gb in a week during peak times. because of this i leave my xp tower running during the night ( off peak times ) downloading. when i do this i have to leave my home server on aswell as that's where the files are transferred to. it's a bit pointless leaving 2 boxes running all the time and defeats the object of me getting a server. i'm gonna install a gui so i can use an ftp client on the server and i'm happy to leave that running all the time syncing with the server. the thing is i need to restrict the speeds between 4 - midnight so i dont go over my allowance. what linux ftp client can do this? i like smartftp for windows for the interface and the scheduling, pausing and 'shutdown after transfers'. i need this sort of thing for ubuntu.

also by switching over to the ubuntu box for transfers am i opening a whole load of doors in terms of integration? i.e. can i sync my ubuntu home server with my ubuntu datacentre server through nautilius? browse remote shares as if local? also any tips people can give for quieing / syncing the files would be great as it's very time consuming.

i know there must be something out there for me nbut i've never used a linux ftp client before. oh and no cli clients - that would be too much!

jeez this was only meant to be a small post!

cheers,
gareth

---

### Post by garethsimpsonuk on 2008-07-24
bump..

---

### Post by Potatoj316 on 2008-07-24
Probably not the best way, or even a possible way to accomplish this.  Maybe you can set up a cron job that severly clipples your transfer rates during peak times.

---

### Post by garethsimpsonuk on 2008-07-24
yea i suppose that culd work. but still what client could i use? what about pausing transfers halfway through? so i culd shutdown and carry on later. i know nothing about it but what about rsync? or something similar. or getting ubuntu to watch a certain directory and when there's new files in there a transfer starts. that way i wouldn't have to cue them up indiviually, just move completed transfers to a subfolder. torrentflux doesn't automatically move transfers to a completed folder which is the biggest flaw with it.

thanks for the reply

---

### Post by Potatoj316 on 2008-07-24
You could create a cron job that would check every so often (maybe like 5 mins or so) and if there were new files it could rsync them.  That might not be the most efficient way to do this though.

There is a terminal ftp client called... ftp (original name)  i dont know if thats what you want or not though.

---

### Post by garethsimpsonuk on 2008-07-24
yea i'd like a graphical one. what's the most respected ftp client for linux? the 1 with the most features?

thanks for ur help

---

### Post by Potatoj316 on 2008-07-24
I really dont know, I usually use fireftp but thats a firefox extension.  Try searching for ftp packages
```
aptitude search ftp
```

---

### Post by garethsimpsonuk on 2008-07-24
well i know of quite a few but i need personal experiences / reviews, rather than having to try them all out myself.

maybe someone else can help?

---

### Post by garethsimpsonuk on 2008-07-28
im still looking guys if any 1 can help, thanks

---

### Post by morningboat on 2008-07-30
The GUI FTP client CrossFTP should meet your requiremnt: [http://www.crossftp.com/](http://www.crossftp.com/)
Or you can write the scripts to do the sync in cron by lftp if you like the command line tools.

---

### Post by Boozkachu on 2008-12-17
You could write a little script to do your ftping and limit/throttle the bandwith with trickle. Then have this scheduled to run as a cron job.

```
sudo apt-get install trickle
```

Cheers.

---

