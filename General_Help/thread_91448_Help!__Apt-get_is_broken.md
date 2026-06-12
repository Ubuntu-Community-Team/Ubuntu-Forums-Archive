---
title: "Help!  Apt-get is broken"
date: 2005-11-17
forum: General Help
---

### Post by jblaty on 2005-11-17
I ran clamav with the delete option on /var.  It appears that it found that clam found every file to be infected with a virus, because it wiped out a bunch before I could stop it.  I am going to be getting rid of clamav after I fix this issue...

Anyway, I'm doing a "apt-get -f dist-upgrade" to see if I can restore anything that was lost in the clamscan.  Nothing is in the trash bin.  The response I'm getting is:

Reading package lists... Error!
E:  Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E:  The package lists or status file could not be parsed or opened.

So basically, I can't apt-get anything.

I don't know what else is broken in /var, because I don't know what clam destroyed.

Can anybody help get me out of this mess?  It concerns me that an AV scanner is so destructive.

Thanks,
Joe

---

### Post by Lambert on 2005-11-17
sudo apt-get update

I believe all you did was delete the cache of what packages are availble that apt-get reads from.

---

### Post by jblaty on 2005-11-17
[QUOTE=Lambert]sudo apt-get update

I believe all you did was delete the cache of what packages are availble that apt-get reads from.[/QUOTE]

Tried that.
Apt-get did a few "Gets"...then "Hits"....
Then it failed again with the same messages, above.

---

### Post by Lambert on 2005-11-17
sudo dpkg-reconfigure -phigh apt

This should reconfigure apt and set up any thing that was deleted by accident

---

### Post by jblaty on 2005-11-17
[QUOTE=Lambert]sudo dpkg-reconfigure -phigh apt

This should reconfigure apt and set up any thing that was deleted by accident[/QUOTE]

(sudo to root)

dpkg-reconfigure -phigh apt

dpkg-query: failed to open package info file '/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: apt is not installed

---

### Post by Lambert on 2005-11-17
There may be a way to fix this but you'll have to wait until the right person reads this.

dpkg is what maintains the packages on the system and with this not working you'll probably have to reinstall though. Do you have a separate partition for your /home directory and are all your files saved there? If so then you can reinstall, set that partition to mount as your /home partition but do not format. Or just backup all your important stuff and do a clean install.

---

### Post by jblaty on 2005-11-17
[QUOTE=Lambert]There may be a way to fix this but you'll have to wait until the right person reads this.

dpkg is what maintains the packages on the system and with this not working you'll probably have to reinstall though. Do you have a separate partition for your /home directory and are all your files saved there? If so then you can reinstall, set that partition to mount as your /home partition but do not format. Or just backup all your important stuff and do a clean install.[/QUOTE]

OK, I will wait a bit.

Also, I'm very hesitant to do a reinstall on this system, because I've done quite a bit of custom configuration (Samba and Xmail).  I want to make sure that I understand how to do that reinstall without wiping out my custom configurations, before I embark on a task like that.

I have not been backing up the image of this system, unfortunately.  I don't know of a tool that I can install on Ubuntu that will image the O/S partitions to a compressed backup file (either DVD-R, network or local drive, etc.).  If anyone has suggestions, I would love to hear them.

If you can suggest a way/link to safely perform this reinstall, I would appreciate it.

In any case, thanks for your help.

---

### Post by Lambert on 2005-11-17
One last thought, not sure if this will work but you could give it a try.

Map out your /var directory
Pop in an ubuntu live cd(if you have one handy), compare that /var directory to yours
Mount your drive and copy the missing pieces to your hard drive (try to limit it to just the missing directories)
sudo cp -R /var/<path>  /mnt/<path_to_hda_/var/<path>

Keep track of what you copy noting the -r is recursive, it will copy anything in that directory and the directories below it.

Log back in; do apt-get update. If that doesn't work then try the dpkg-reconfigure command and see if you get any results.

This may not work but as long as you keep record of what you copy so you can undo; it shouldn't harm anything.

---

### Post by jblaty on 2005-11-17
[QUOTE=Lambert]One last thought, not sure if this will work but you could give it a try.

Map out your /var directory
Pop in an ubuntu live cd(if you have one handy), compare that /var directory to yours
Mount your drive and copy the missing pieces to your hard drive (try to limit it to just the missing directories)
sudo cp -R /var/<path>  /mnt/<path_to_hda_/var/<path>

Keep track of what you copy noting the -r is recursive, it will copy anything in that directory and the directories below it.

Log back in; do apt-get update. If that doesn't work then try the dpkg-reconfigure command and see if you get any results.

This may not work but as long as you keep record of what you copy so you can undo; it shouldn't harm anything.[/QUOTE]

I'm having trouble finding the /var path on the LiveCD...

---

### Post by jblaty on 2005-11-18
Any ideas on where /var is on the LiveCD?

---

### Post by jblaty on 2005-11-18
OK, I booted with the LiveCD, mounted the hard drive, and copied the /var directory on the LiveCD to the hard drive /var.  Then I ran a dpkg-reconfigure -phigh apt

I found that I can run apt-get now, as well as synaptic package manager.  However, all of my installed packages aren't recognized.  For example, I know that the clam daemon is installed and running, yet does not show up as installed.  If I do a apt-get remove on any of the installed packages, it just says "not installed."

Is there any way to dynamically rebuild the list of installed packages?

---

### Post by Lambert on 2005-11-19
Not sure if you got an answer yet or solved this but I ran across this in my reading.

**6.3.4 Recover package selection data**

 If /var/lib/dpkg/status becomes corrupt for any reason, the Debian system loses package selection data and suffers severely. Look for the old /var/lib/dpkg/status file at /var/lib/dpkg/status-old or /var/backups/dpkg.status.*. 
Keeping /var/backups/ in a separate partition may be a good idea since this directory contains lots of important system data. 
  If no old /var/lib/dpkg/status file is available, you can still recover information from directories in /usr/share/doc/.  

      # ls /usr/share/doc | \
       grep -v [A-Z] | \
       grep -v '^texmf$' | \
       grep -v '^debian$' | \
       awk '{print $1 " install"}' | \
       dpkg --set-selections
     # dselect --expert # reinstall system, de-select as needed

---

### Post by macluvjay on 2006-11-29
I'm having the same problem as the original post.Here's what I've done so far:

```

aeonos@fluxbuntu:~$ cd /var/lib/dpkg
aeonos@fluxbuntu:/var/lib/dpkg$ ls
alternatives  diversions      info  methods  statoverride      status-old
cmethopt      diversions-old  lock  parts    statoverride-old  updates
aeonos@fluxbuntu:/var/lib/dpkg$ sudo cp status-old status
aeonos@fluxbuntu:/var/lib/dpkg$ sudo touch status

```

Now I get:
```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

I'll keep looking.  Maybe we will eventually find a solution to this problem :)

---

### Post by nsleiman on 2006-12-13
well i was facing same problem and i solved it, steps i did:
1-
gunzip dpkg.status.0.gz located in /var/backups and save it under `status` in /var/lib/dpkg/
2-
you might need to create the `available` file in also `/var/lib/dpkg/` this can be done by typing: `touch available` (or `sudo touch available`) 

after these 2 steps try to `dpkg -i package.deb` (or sudo ..).

Regards

---

### Post by Riscos on 2007-01-03
> **Lambert said:**
> sudo dpkg-reconfigure -phigh apt

This should reconfigure apt and set up any thing that was deleted by accident

Lambert saved my life!!!!!!!!!!!!!!!!

this command I'm going to frame "sudo dpkg-reconfigure -phigh apt"

---

