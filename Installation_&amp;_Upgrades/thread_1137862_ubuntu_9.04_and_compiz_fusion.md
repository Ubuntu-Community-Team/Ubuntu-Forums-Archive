---
title: "ubuntu 9.04 and compiz fusion"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by kadaj6 on 2009-04-26
is compiz fusion installed on 9.04?

is compiz fusion better on 8.10 or 9.04?

how do i install compiz fusion?

ubuntu 8.10 or 9.04 wich one is better?

please answer this question thankyou

---

### Post by organicanagram on 2009-04-26
1. Not from a clean install of jaunty. 
2. It seems to run smoother on 8.10, but I'm using an intel GMA x3100 graphics card, so I had to enable a workaround to get compiz fusion to work (they blacklisted the x3100)
3. In a terminal, type sudo apt-get install compizconfig-settings-manager
4. 8.10 will be maintained long term, whereas 9.04 will not (but 9.10 is coming out on 9/10, see the pattern?). 9.04 has a quicker startup time and everything indexes faster. I only just started using it, but so far I don't see much of a difference.

---

### Post by kadaj6 on 2009-04-26
well i asked all this question because im about to make a pc  with dual graphic card (SLI) and was wandering if it was better to instal vista or ubuntu and, if i was to install ubuntu witch one should i get?...

thank you a lot for the answers ^^

---

### Post by kadaj6 on 2009-04-26
anyone?

---

### Post by kadaj6 on 2009-04-26
?

---

### Post by linux newb on 2009-04-26
I would suggest kubuntu 8.10. Kubuntu is alot easier on the eyes if you know what i mean. these guys are right, that it is also alot smoother. Now i see you are interested in windows and linux. heres a couple things you can do. 

1. setup a dualboot system, runnning linux and windows with an os selection at boot up. [http://www.freesoftwaremagazine.com/articles/dual_boot_kubuntu](http://www.freesoftwaremagazine.com/articles/dual_boot_kubuntu). that guide should show you how to do this

2. install linux, then install microstoft inside of it. this is done quite simply if you are not very familiar with the command line and dont want to be. basically you install kubuntu, then on the kubuntu installation, you want to install virtual box.[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), then within the virtual machine, you can install any operating system you want, and  as well as multiple operating systems. i hope this helps you, oh and about compiz, go into your restricted hardware drivers and enable video driver 180, then go to aplications/system/desktop effects, and check off the one where its says "youll need sunglasses", then go to applications/system/package manager. search "compiz" without quotes, and install all of the compiz packages except for the unsupported plugins, these you will not need.

---

### Post by linux newb on 2009-04-26
> **linux newb said:**
> I would suggest kubuntu 8.10. Kubuntu is alot easier on the eyes if you know what i mean. these guys are right, that it is also alot smoother. Now i see you are interested in windows and linux. heres a couple things you can do. 

1. setup a dualboot system, runnning linux and windows with an os selection at boot up. [http://www.freesoftwaremagazine.com/articles/dual_boot_kubuntu](http://www.freesoftwaremagazine.com/articles/dual_boot_kubuntu). that guide should show you how to do this

2. install linux, then install microstoft inside of it. this is done quite simply if you are not very familiar with the command line and dont want to be. basically you install kubuntu, then on the kubuntu installation, you want to install virtual box.[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), then within the virtual machine, you can install any operating system you want, and  as well as multiple operating systems. i hope this helps you, oh and about compiz, go into your restricted hardware drivers and enable video driver 180, then go to aplications/system/desktop effects, and check off the one where its says "youll need sunglasses", then go to applications/system/package manager. search "compiz" without quotes, and install all of the compiz packages except for the unsupported plugins, these you will not need.
kubuntu 9.04 just came out so i would wait before upgrading to it fer at least a couple months, there are a couple buggs with it unallowing desktop effects to be enabled.

---

