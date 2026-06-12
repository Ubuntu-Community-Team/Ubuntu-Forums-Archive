---
title: "Will updating 8.10 to 9.04 remove all of my manually installed packages?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by jikuty on 2009-04-23
Hi.

I was just wondering if using the update feature will remove all of my manually installed packages. For example, I installed programs like Virtualbox and Opera using apt-get... will these programs be preserved upon updating to 9.04? If it's of any help, I do have a separate /home partition.

On a related note, is there a way for me to get a list of all of my manually installed packages? That way, if the update goes badly and I have to start fresh, I could just use the list apt-get all of my packages again and be up and running really quickly. 

Thanks!

---

### Post by ahbart on 2009-04-23
What you can do is to have a look at your repositories. Or in /etc/apt/sources.list or via synaptic - settings - repositories.
Look at lines you have added yourself with Intrepid in it.
Go to/follow this url's and find out if there is a Jaunty directory for that.
There is a virtualbox jaunty package, but there is still no repository for jaunty. The package is here: [link](http://download.virtualbox.org/virtualbox/2.2.0/virtualbox-2.2_2.2.0-45846_Ubuntu_jaunty_i386.deb)

---

