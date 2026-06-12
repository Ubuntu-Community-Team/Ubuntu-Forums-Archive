---
title: "RAID Installation"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by soorjithp on 2009-04-13
Dear All

I have to install Ubuntu server in a machine - HP ML370 G5 Tower server E5420. Its storage controller is HP smart array P400/512MB BBWC Controller (RAID 1+0). Pls let me know how can I configure and install the RAID in Ubuntu.

Thanks & Regards
Soorjith P

---

### Post by linuxuser21 on 2009-04-13
I have the same machine (g4 though).  I can't get it to detect my 3rd hard drive at all.  You should just be able to install and they'll be right there.  I mounted one as / and the other as /home so I can keep all my music & stuff on one away from the system files..

---

### Post by NoReflex on 2009-04-13
If your system has a RAID controller then in Ubuntu you should see a single drive and the RAID configuration should be done independent of the operating system (much like BIOS).
Does you system have a RAID configuration utility (there should be some prompts during boot up).

Best wishes,
NoReflex

---

### Post by ronparent on 2009-04-13
Just a general comment. I am using a raid0 system - two hrd drives in a stripped array. I did originally configure them through a raid configuration utility which has a prompt during bootup. During an initial install of winXP I had to insert the reference to a driver for the raid controller as the first step of the install. This will not happen with the standard ubuntu install disk, however. What you will see during partitioning are two unallocated drives. In order to install to the array, once created in bios, you need to use the alternate cd which does contain software which will allow you to see the array. Look up the how to install on a raid drive which will guide the install. I'm sorry I'm not more specific but I don't have the references at hand right now.

---

### Post by ronparent on 2009-04-14
Having done some research, the following reference can walk you through installing on a 'fake' raid using dmraid:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

This is the a preferred way to go if you need to access windows partition(s) from ubuntu. Otherwise you will have to read the install with software raid using mdadm.

---

