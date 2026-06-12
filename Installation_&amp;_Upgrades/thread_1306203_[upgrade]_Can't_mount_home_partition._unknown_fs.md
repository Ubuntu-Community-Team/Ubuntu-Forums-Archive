---
title: "[upgrade] Can't mount /home partition. unknown fs"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by m4lte on 2009-10-30
I used to run 9.04 with separate partitions for my system and home folder. Both with ext3 file system. I also had a windows partition.

After I upgraded through the update manager my computer does not boot anymore.

I get the following messages:
mount: unknown filesystem type 'dazukofs'
mountall: mount /home [962] terminated with status 32
mountall: Filesystem could not be mounted: /home
mountall: mount /home [965] terminated with status 32
mountall: Filesystem could not be mounted: /home
init: mountall main process (513) terminated with status 4
Mount of root filesystem failed.
A maintenance shell will now be started.

I tried booting from a 9.04 live CD which was no problem and I couldn't find anything wrong with my home partition.
Any suggestions?


[B]EDIT:
I SOLVED THE PROBLEM BY REMOVING SOME LINES FROM MY /etc/fstab. FOR DETAILS SEE POST #6.[/B]

---

### Post by userdev on 2009-10-30
Exact same problem for me. I'd love some help on this, as well.

---

### Post by userdev on 2009-10-31
Nobody else is experiencing this? I've had a perfectly useful stable setup until this. I'm sure someone else is in the same boat...somewhere.

---

### Post by userdev on 2009-10-31
By way of update, if someone might be able to help with this information:
 
I took out some stuff in my fstab, specifically, it had a line like /home /home dazukofs 0 0 0
 
I stripped it down to /home and the message at bootup is that it is waiting for drives to mount. Of course, waiting doesn't help anything.
 
However, I've managed to get into Ubuntu 9.10, so I think progress is being made, but I'm a little unsure of what to make from my success. Essentially, I get into the maintenance shell and put in the following in root:
 
```
mount -o remount,rw /
```
 
followed by
 
```
 
sudo dpkg --configure -a

```
 
This gets me in, but when I restart, I have to do it again. I'm pretty sure a mod of fstab will finish this off, but I'm not quite experienced enough to know how.

---

### Post by userdev on 2009-10-31
Just tried this again, and all that is required is the remount and I can get into 9.10.
 
Does anyon have extensive fstab expertise? I think that's what I need next.

---

### Post by m4lte on 2009-10-31
I solve the problem.
In the file /etc/fstab I found the following lines which I assume were written there by Avira Anti Virus which I had installed some time ago:

# DazukoFS
# Example of mounting one dir onto dazukofs (directory to be protected by AVIRA Guard)
# /home/shared /home/shared dazukofs
/home /home dazukofs
# ... DazukoFS

I deleted those lines and saved my fstab again. Now my machine runs fine again.

Note: if you're system doesn't boot you can use the maintenance shell and edit your fstab using the command
nano /etc/fstab
before you do changes, you might want to backup your fstab for example by making a copy like this
cp /etc/fstab /etc/fstab.bk


Comment #29 explains that the problem occurs because of a change in how errors in the fstab are treated.
[https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/432620?comments=all](https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/432620?comments=all)

---

### Post by userdev on 2009-10-31
Thanks for the reply!
 
As I mentioned earlier, I had changed
 
/home /home dazukofs 0 0 0 
 
to 
 
/home
 
After reading your reply, I took out the /home and it now works beautifully!
 
Thanks for the help!

---

