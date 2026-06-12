---
title: "networking"
date: 2008-11-15
forum: General Help
---

### Post by Bigneil on 2008-11-15
My desk top and my laptop are connected to a Bt HomeHub wireless modem router. they are connected directly into it with Ethernet in the two avilable ethernet slots, but they don't seem to be able to see each. i would like to copy files from one pc to the other.  

Both computers are running Ubuntu gutsy  installed within the last 48 hours.

Any one out there willing to point a NOOB in the right direction??

---

### Post by Chris Musampa on 2008-11-15
Its really easy.

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by Bigneil on 2008-11-15
Ta Chriss:)

---

### Post by Bigneil on 2008-11-15
Ok i know it is probably easy when you know how, but, that sounds a bit complicated to a beginner. i copied    sudo apt-get install nfs-kernel-server nfs-common portmap

Into the terminal and off it went and installed or chaged settings, but it hasn't made any difference that i can see. 

I will have another look at it in the morning with a fresh mind, But could you answer one wee question before i go?

Do i do this to both computers?

---

### Post by fragos on 2008-11-15
I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. This scheme works with any mix of 8.04 and 8.10. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

### Post by Bigneil on 2008-11-16
Thankyou for taking the time to point me in the right direction.:)

i havn't quite got it just yet though, im going to study a bit then come back to your posts and re read them.

---

