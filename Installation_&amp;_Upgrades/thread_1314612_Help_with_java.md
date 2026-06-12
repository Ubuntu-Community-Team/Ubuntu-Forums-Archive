---
title: "Help with java"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by duthieamber on 2009-11-04
Hi I am trying to download and install Java for Ubuntu 9.10 and am having alot of trouble could someone please give me step by step instructions on how to do this? 
               Thanks,
                  Amber

---

### Post by 73ckn797 on 2009-11-04
You can get it via Applications/Ubuntu Software Center/Other. Look for "Ubuntu restricted extras". It is so much easier that way.

---

### Post by duthieamber on 2009-11-04
It says waiting for other software managers to quit . what does that mean?

---

### Post by issih on 2009-11-04
It means you have something else open that accesses the ubuntu repositories...either synaptic package manager, a terminal runnign apt-get or the update manager are the usual suspects.

Close those, then try again

Hope that helps

---

### Post by duthieamber on 2009-11-04
but none of those are open... I'm so confused

---

### Post by issih on 2009-11-04
Well, if in doubt I'd log out and back in again as the simplest possible fix...and if thats not it reboot.

I could tell you to look at the process table and try to find the rogue synaptic process or whatever it is, but this is a million times easier.

---

### Post by duthieamber on 2009-11-04
restarted the computer and i am still getting that message ... please help

---

### Post by issih on 2009-11-04
Hmmn, it seems that the new software centre does a poor job of reporting error messages:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/464020](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/464020)

That bug listing implies that it is the fairly common issue of the repos getting into a bit of a mess.

Normally this error is reported along with its solution which hopefully is:

```
sudo dpkg --configure -a
```

Open a terminal window (Applications->Accessories->terminal)

and enter that line and hit enter (you can paste with the mouse)

You will then be asked for your login password, type it and hit enter (nothing will be echoed to the screem)

Hopefully that should fix it,

---

### Post by 73ckn797 on 2009-11-04
> **duthieamber said:**
> restarted the computer and i am still getting that message ... please help

Can you find it in Synaptic Package Manager? For Java, look for sun-java6-jre and sun-java6-plugin.

issih's solution will likely work.

---

### Post by duthieamber on 2009-11-04
now when i do it im getting an error message saying Package Operation Failed
The installation or removal of a software package failed. then in the box it says E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch): 


And when i opened Synaptic it says i have a broken package....???

---

### Post by issih on 2009-11-04
Have you run the command I suggested? 

here is the gui solution to broken packages, open synaptic and then:

[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

Alternatively run the following in a terminal:

```
sudo apt-get install --fix-missing
```

Hope that finally gets you up and running

---

### Post by laidback82 on 2009-11-04
hi there! I am having the exact same problem as the OP. Issih seems to have sorted it but.... this is a really stupid question....

I used Issih's last command prompt suggestion, the Terminal suggested I try something else, which I did... I now can't seem to accept the EULA thingy. It's the Sun disclaimer with <ok> at the end. I've scrolled down to the bottom and hit return, to no avail. How do I accept it?

Stupid, I know!

SORRY! JUST FOUND OUT HOW TO DO IT! I feel very small right now.

---

### Post by 73ckn797 on 2009-11-04
> **laidback82 said:**
> SORRY! JUST FOUND OUT HOW TO DO IT! I feel very small right now.

Don't feel bad. We all have those things happen. It is a learning process.

---

### Post by duthieamber on 2009-11-05
Thanks everybody i got it fixed!!

---

