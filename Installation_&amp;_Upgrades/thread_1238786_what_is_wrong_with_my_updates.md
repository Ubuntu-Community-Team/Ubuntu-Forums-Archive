---
title: "what is wrong with my updates?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by clinc on 2009-08-12
For some reason, I am not able to install updates now. 

please help!!!

the system updater error message states:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have changed nothing recently, and I have been able to update this computer successfully since I first installed 9.0.4. 

Any thoughts?

---

### Post by raymondh on 2009-08-12
> **clinc said:**
> For some reason, I am not able to install updates now. 

please help!!!

the system updater error message states:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have changed nothing recently, and I have been able to update this computer successfully since I first installed 9.0.4. 

Any thoughts?

As it says, type in terminal (applications > accessories)

```
sudo dpkg --configure -a

```

Then continue with the update

sudo apt-get update && sudo apt-get upgrade


Your update was interrupted, somehow.

---

### Post by clinc on 2009-08-12
when I type "sudo dpkg --configure -a" it basically freezes the functionality of my computer. All other things happening concurrently all seem to choke. 

What could be making this happen?

---

### Post by raymondh on 2009-08-12
> **clinc said:**
> when I type "sudo dpkg --configure -a" it basically freezes the functionality of my computer. All other things happening concurrently all seem to choke. 

What could be making this happen?

Are you running only the terminal?  Or do you have synaptic and/or add/remove open as well?  Only run one (1) manager.

---

### Post by clinc on 2009-08-12
I am running in terminal. My terminal then states what I believe it is referring to as an open office package and all other functions of my computer freeze. I can still move the mouse around, but I can't access any of my other open windows of applications. I let this run over-night last night, and nothing changed. 

this is really frustrating. It looks as if the installer is going to begin working, since it asks for my password. Then, everything locks up.

---

### Post by raymondh on 2009-08-12
> **clinc said:**
> I am running in terminal. My terminal then states what I believe it is referring to as an open office package and all other functions of my computer freeze. I can still move the mouse around, but I can't access any of my other open windows of applications. I let this run over-night last night, and nothing changed. 

this is really frustrating. It looks as if the installer is going to begin working, since it asks for my password. Then, everything locks up.


Back up your files.

Does it (lock-up) also happen when you just have the terminal .. and all other apps/programs are closed?

What version open office?  I seem to recall a number of posts in the forum about open office and that it *seems* to be better using the 'sun' version.  

Do you want to try to un-install open office and install again?  You can use synaptic for that by marking for removal all open office.  make sure your OO files are backed up elsewhere.

---

