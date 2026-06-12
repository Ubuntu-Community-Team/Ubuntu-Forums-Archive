---
title: "Apt-get Lockfile error 21 File is a directory"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by NewbieNik on 2009-07-05
OK, so I updated Jaunty 64bit around 3 weeks ago. Since then I cannot run any apt-get commands even using sudo and su.
Each time I get the error that says:-

E: Could not open lock file /var/lib/dpkg/lock - open (21 Is a directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Looking in the /var/lib/dpkg directory there is indeed a "lock" folder. I have tried renaming, removing and verbally abusing this folder, but each time it is immediately recreated. I have tried killing the update process, but not sure this worked as there was no difference (If someone could pass me the correct method to kill this process, it would be appreciated)

As this affects all apt-get commands I cannot run updates, purges nor forces.

So how do I fix this problem? I REALLY don't want to do another re-install (3rd one on this system)

Thanks in advance.

---

### Post by taurus on 2009-07-05
What groups do you belong to?  Do you belong to group admin?

```
id
```

---

### Post by NewbieNik on 2009-07-05
Yeah, I'm in the sudoers.

Sudo-ing any command is fine, it's just the apt-get commands that fail as it is looking for a "lock" file in the /var/lib/dpkg folder, but can only find a folder...I assume.

As I said in the original post, this happens if I run it with SU so it's affecting the root user too.

---

### Post by taurus on 2009-07-05
Does synaptic work?  I have a lock file in /var/lib/dpkg and don't have any problem using apt-get from a terminal.

```

-rw-r-----  1 root root       0 2009-07-02 17:30 lock

```

---

### Post by NewbieNik on 2009-07-05
Nah, Synaptic fubar'd too!

As I said, there is a lock FOLDER in /var/lib/dpkg, but no lock FILE. I cannot create a file because I cannot remove the folder. I assume this is because the update service is still running. 
Is there a way I can find the PID of the update process and kill it? That way I can try creating a blank file with root only access and run apt or synaptic again.

Thanks for your help so far.

---

### Post by taurus on 2009-07-05
```
ps -A
```

---

### Post by Soul-Sing on 2009-07-05
mostly this is a problem when another package update / installation application is already running.(ad/remove/synaptic/apt-get)

if thats not the case
try: 
```
sudo rm /var/lib/dpkg/lock
```

then should it say something about other lock..

```
sudo rm /var/cache/apt/archives/lock
```

```
sudo apt-get update
```

---

### Post by NewbieNik on 2009-07-05
You my friend, are a star. I had to use the rmdir command for the /var/lib/dpkg/lock, but it's now running sweet. Must have been the cache that was replacing the folder.

Thank you, thank you ,thank you.

How do I close this thread?

> **leoquant said:**
> mostly this is a problem when another package update / installation application is already running.(ad/remove/synaptic/apt-get)

if thats not the case
try: 
```
sudo rm /var/lib/dpkg/lock
```

then should it say something about other lock..

```
sudo rm /var/cache/apt/archives/lock
```

```
sudo apt-get update
```

---

### Post by NewbieNik on 2009-07-05
Ooooh, as an aside, that failed. Told me that /var/lib/dpkg/triggers was not a folder.
It was right, it was a file.

ran:-
sudo rm /var/lib/dpkg/triggers
sudo apt-get update

all working sweet as a sweet thing in a sweet place....sweet

---

