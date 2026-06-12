---
title: "Nvidia driver install issue"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by Da.Rabbi on 2009-07-05
I'm haven a great deal of problems installing my video driver everytime I go to install I get the message (see picture)

I tried to change the permission for the file 
chmod +rwx and nothing happens

can someone please let me know what I have done wrong.

P.S I am a newbie leaving Micro$hit for ever

---

### Post by Da.Rabbi on 2009-07-05
-rwxrwxrwx  1 administrator root          20141927 2009-07-05 09:52 NVIDIA-Linux-x86-173.14.20-pkg1.run

I have all the permissions to run the file

---

### Post by merlinus on 2009-07-05
Did you try System/Administration/Hardware Drivers to see if one is listed there?

---

### Post by overdrank on 2009-07-05
Hi and you will have to exit x
```
sudo /etc/init.d/gdm stop

```
And to install the driver
```
sudo sh NVIDIA-Linux-x86_64-185.19-pkg2.run
``` replace with the name of the driver you downloaded.
Edit and as merlinus pointed out the other option :)

---

### Post by Da.Rabbi on 2009-07-05
Thank You both so much both info was helpful, I have now managed to get it working.:p

---

