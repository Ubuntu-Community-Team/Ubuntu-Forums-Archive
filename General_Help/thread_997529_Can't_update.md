---
title: "Can't update"
date: 2008-11-29
forum: General Help
---

### Post by k5495 on 2008-11-29
Have had a computer running only linux ubuntu 8.04 for about 4 months and have always been able to download and install updates.

Now I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have tried opening a terminal and typing in dpkg --configure -a

that doesn't work

Any suggestions?

---

### Post by drs305 on 2008-11-29
You must run it with sudo:
```
sudo dpkg --configure -a
```
You will be asked for a password. Type your entire password - you won't see it as you type - and hit ENTER when you have entered it.

---

### Post by k5495 on 2008-11-29
I was able to get the command:

sudo dpkg --configure -a 

to run.  Thanks for that.

The computer then did something that took about 5 minutes.  I don't think it solved the problem.  

I still get the same error message when I try to update.

The red arrow on my toolbar now indicates that have 75 updates available.

Any Ideas??

---

### Post by drs305 on 2008-11-30
> **k5495 said:**
> I was able to get the command:

sudo dpkg --configure -a 

to run.  Thanks for that.

The computer then did something that took about 5 minutes.  I don't think it solved the problem.  

I still get the same error message when I try to update.

The red arrow on my toolbar now indicates that have 75 updates available.

Any Ideas??

Run both of these and report any errors. Let us know if the first command still takes a long time to run:
```

sudo dpkg --configure -a
sudo apt-get update
```

typo fixed, thanks Xiong

---

### Post by Xiong Chiamiov on 2008-11-30
> **drs305 said:**
> Run both of these and report any errors. Let us know if the first command still takes a long time to run:
```

sudo dpkg --configure -a
sudo apt-get udpate
```

s/udpate/update/

Translation: that's update, as I'm sure you'd figure out, but just to be safe.

---

### Post by sosaudio1 on 2008-11-30
sudo dpkg --configure -a
[sudo] password: 
dpkg: unable to open/create status database lockfile: No such file or directory

HELP having the same problem..how do I fix this...I have a thread started in updates but I am losing traction....need to get this fixed..

Thanks
Rich

---

### Post by yBfj3nbmn7 on 2008-11-30
I had the same problem, but your advice solved it, drs305. Thanks!

---

### Post by Tobster on 2008-11-30
I am having the same problem.

But when it is working to update to Ubuntu 8.10

Chick on Synaptic then 
                   *properties (then)
                         *Allow Distribution upgrades (it something along 
                          knows lines but because my Synpatic is like yours 
                          I can't check - I broke mine when I tried to 
                          install an old version of Second Life)

---

