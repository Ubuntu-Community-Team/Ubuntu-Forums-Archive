---
title: "Running sudo commands in sessions, what's the best method for me?"
date: 2008-11-11
forum: General Help
---

### Post by Benchamoneh on 2008-11-11
Hi all,

I'm running ubuntu 8.04 on my eee after replacing the useless xandros installation. I've installed the eee-control suite (available [here]("http://greg.geekmind.org/eee-control/")) and when I try to run the daemon using the instructions on the website I get a message about a conflict with another module, namely asus_eee. I know that if I disable the module by typing "sudo rmmod asus_eee" then I can then run the daemon but my problem is that I have to do this each time I use my laptop.

How can I go about entering these two lines at each boot? Is there some other way to remove the asus_eee module from loading at logon? I've tried using sessions but the commands were not executed and I'd prefer to not have to enter my password at each logon.

My linux knowledge is pretty limited as you may have guessed but any help is appreciated. Thanks!

---

### Post by ju2wheels on 2008-11-11
Since your pretty new to Linux, I would recommend following the instructions here [http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly) and using the NiceeePC script to do the hard work for you.

---

