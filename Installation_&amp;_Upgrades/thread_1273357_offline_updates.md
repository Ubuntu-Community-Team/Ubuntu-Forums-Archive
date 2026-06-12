---
title: "offline updates"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by 45acp on 2009-09-23
I have a computer running Jaunty that I want to update. I downloaded the updates with Keryx from a windows system. When I installed them using dpkg I had to force the install due to dependencies and one new package breaking an installed one . This broke X and I had to reinstall from a backup image. I tried the "add downloaded packages" in synaptic but the downloaded packages are grayed out. Is there an easy way to update offline? 

I have search the forums but I haven't come up with anything satisfactory

Thanks

---

### Post by scragar on 2009-09-23
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by EXCiD3 on 2009-09-23
It's best if you use the local repo script for Keryx. Instead of forcing install which might break things, it takes what Keryx downloaded and installs them via apt, instead of straight dpkg.

Give it some time and Keryx 1.0 will be able to install properly without any problems. If anyone is a Python developer and wants to help, hit me up!

---

### Post by 45acp on 2009-09-23
> It's best if you use the local repo script for Keryx.

Thanks for the replies everyone. EXCiD3 I am not sure what script you are referring to. Could you elaborate a little for a noob?

---

### Post by EXCiD3 on 2009-09-23
It's called LocalRepo-Add.py and it should be included in the download in the doc folder. You can use this to create a repository and then apt-get install the applications from there as it will turn your flash drive into a local repository and you won't have packages breaking anymore. This also means that some things might fail to install because Keryx's current version is not 100% the same as apt-get dependency calculation just yet.

---

### Post by 45acp on 2009-09-23
Thanks for the reply. I'll try that.

---

### Post by peterthinking on 2009-09-23
This looks promising...

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

peterthinking

---

### Post by wojox on 2009-09-23
+1 APTonCD 

Great app.

---

