---
title: "When ever I try to Install New Software Or Updates I Get This Message.."
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by GummyBearCrisis on 2009-06-27
[IMG]file:///home/linux/Pictures/What%2520Does%2520This%2520Mean.png[/IMG]I always get the same message for anything that I have to install.

 I used to get a message that told me I had to close any other installer application but there wasn't any other one open.

Can anyone help me out?

Response to 'philcamlin':
I do that but then I get This;
linux@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for linux: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0067' near line 12:
 missing package name
linux@ubuntu:~$

---

### Post by philcamlin on 2009-06-27
go to terminal and run 

sudo dpkg --configure -a 

:popcorn::popcorn:

---

### Post by drs305 on 2009-06-27
It means it wants you to run this command:
```

sudo dpkg --configure -a

```
To clear up an installation. You can look at "man dpkg" to read what it does.

---

### Post by GummyBearCrisis on 2009-06-27
I do that but then all of this shows up. :(


linux@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for linux: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0067' near line 12:
 missing package name
linux@ubuntu:~$

---

### Post by drs305 on 2009-06-27
> **GummyBearCrisis said:**
> I do that but then all of this shows up. :(

OK. It may look like you aren't making progress but you are! When you ran the "sudo dpkg --configure -a" command it allowed APT (the installer) to progress to the next stage.

When it got there, it found some errors in the next set of files - in this case in "/var/lib/dpkg/updates/0067". You could inspect this file but you may not understand it (nor may many of us) or there could be a lot of other files with errors.

So, we will go to that folder, rename the file so it isn't looked at, and see if that was the only problem:
```

sudo mv /var/lib/dpkg/updates/0067 /var/lib/dpkg/updates/0067.bad
sudo apt-get update && sudo apt-get upgrade  # update the package list and upgrade existing packages.

```

See if you get any more errors. If you get more errors for other files in "updates", you may want to rename the entire "updates" folder with this command:
```

sudo mv /var/lib/dpkg/updates /var/lib/dpkg/updates.bad
sudo apt-get update && sudo apt-get upgrade 

```

---

