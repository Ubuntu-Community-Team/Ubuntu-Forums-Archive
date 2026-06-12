---
title: "Live-cd and root issues"
date: 2005-11-08
forum: General Help
---

### Post by sexcopter on 2005-11-08
Hi, for one reason or another my list of devices has got a bit messy (see: [http://users.fission.org.uk/~sexcopter/Screenshot-GParted.png](http://users.fission.org.uk/~sexcopter/Screenshot-GParted.png)). I'd like to tidy it up a bit by merging the two linux-swap partitions. When running "normally", I try to fiddle with hda5 it says "Please unmount any logical partitions having a number higher than 5". Fair do's. So I run it under live-cd and this doesn't seem to help, so I try it under "live-expert", where you can specify more details, in particular where the swap is for the live session. It all seems to work fine, except I then can't run gparted; it rejects the root password I give during the setup, and I can't figure why...

So my question is... what am I doing wrong, or is there a better way to clean up the list of devices (other than reformatting :P)?

Thanks in advance,
James.

---

### Post by Samuel on 2005-11-08
well on the live cd you can use sudo, there is no password (not sure if it has a time out but for the first 15 mins or so you definatly have root access)

Run the command '/sbin/swapoff -a' to unmount the swap drives.

make sure you back up anything important because i wiped my installation out using GParted trying to move swap partitions..

---

### Post by sexcopter on 2005-11-09
Ok, thanks for that advice, but I already tried "sudo gparted" and just hit enter at the password prompt and it didn't accept that. However when running the non-expert livecd it doesn't ask for any passwords, so maybe the /sbin/swapoff -a command will let me do all this under a normal live session. I'll try that soon, thanks!

---

### Post by mechanic on 2005-11-09
[QUOTE=sexcopter]So my question is... what am I doing wrong, or is there a better way to clean up the list of devices (other than reformatting :P)?
[/QUOTE]

Hmmm,  two swap partitions and one is labelled hda5! I hesitate to guess how you got there! You could try deleting the hda5 swap partition, hopefully the remaining partitions will relabel themselves sensibly after that, then enlarge the (single) remaining swap partition if necessary. Just a suggestion, when it gets to the 'should I try re-installing' stage anything's worth a try.

m.

---

### Post by sexcopter on 2005-11-09
Hello again, I've done it! It's all sorted now: [http://users.fission.org.uk/~sexcopter/Screenshot-GParted2.png](http://users.fission.org.uk/~sexcopter/Screenshot-GParted2.png)

For the interested reader, here is what I did:
I went into a normal live session, used swapoff -a (thanks to Samuel for this) and could delete hda5. Sure enough hda7 and hda6 became hda6 and hda5 respectively (well predicted mechanic!). So I shifted the free space over to hda5 and voila... all sorted.

Well not quite. It seemed to muck up my grub a bit, and I got an error 17 (whatever that is). So I went back into live, followed the wiki RecoveringUbuntuAfterInstallingWindows and it was ok! A nail-biting moment to say the least (could see the reformat option looming...)

So, thanks again to Samuel and mechanic for saving me half a gig of hdd space :)

A new question on the side now: Is it possible for me to shift some space from hda5 to hda2? It seems in gparted that hda4 is "fixed" in size and can't be changed. It's not a biggie, but hda1 and hda2 could use that extra bit of space!

---

