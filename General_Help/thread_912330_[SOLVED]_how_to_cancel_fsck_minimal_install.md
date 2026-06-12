---
title: "[SOLVED] how to cancel fsck minimal install"
date: 2008-09-06
forum: General Help
---

### Post by derrick81787 on 2008-09-06
Hello everyone,

In a default Ubuntu install, when fsck runs at boot time, you have the option to cancel it by hitting the esc key.  However, I've installed the minimal system and built up from there, and for some reason, I don't have that feature.

Basically, I'm wondering if there is anything I can do to get that feature.  Is there a package I can install, or a config file I can change, or something?

Any help would be appreciated.

Thanks,
Derrick

---

### Post by forger on 2008-09-06
You are advised to **do the fsck scan** your files, it's like Windows "scandisk"/"chkdsk" feature that cleans up problems with files/folders after a failure or improper shutdown.

To change the frequency of the fsck checks:
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by derrick81787 on 2008-09-06
> **forger said:**
> You are advised to **do the fsck scan** your files, it's like Windows "scandisk"/"chkdsk" feature that cleans up problems with files/folders after a failure or improper shutdown.

To change the frequency of the fsck checks:
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

Well, I know that, and most of the time I will.  It's just that every once in a while, fsck has really bad timing.  That's the whole reason the ability to postpone the check until next boot was introduced in Hardy (or maybe Gutsy, I don't remember).

Either way, this isn't that big of a deal.  I just know that it's what happens in the default install, and I was trying to configure my system that way, too.

- Derrick

---

### Post by forger on 2008-09-06
hm.. in that case, probably something's wrong with the ubuntu usplash theme, you might consider filing a bug report about it at [http://bugs.launchpad.net/ubuntu](http://bugs.launchpad.net/ubuntu)

---

### Post by derrick81787 on 2008-09-06
> **forger said:**
> hm.. in that case, probably something's wrong with the ubuntu usplash theme, you might consider filing a bug report about it at [http://bugs.launchpad.net/ubuntu](http://bugs.launchpad.net/ubuntu)

So it's something in the spash screen and not in the bootup process itself?  If so, that's the problem, then because I don't have a splash theme installed.  I guess that's something I should've made clear in my first post...

---

### Post by drs305 on 2008-09-06
You mentioned fsck and bad timing. If what you are looking for is a way to manage *when* fsck runs, there is an app called 'autofsck' which will allow you to tweak when fsck is run (such as on shutdown instead of on boot).

tune2fs can set how often the fsck checks are run (# of boots, # of days, etc).

Running "sudo touch /forcefsck" in the root directory will cause an fsck check to be run on the next boot.

---

### Post by derrick81787 on 2008-09-06
> **drs305 said:**
> You mentioned fsck and bad timing. If what you are looking for is a way to manage *when* fsck runs, there is an app called 'autofsck' which will allow you to tweak when fsck is run (such as on shutdown instead of on boot).

tune2fs can set how often the fsck checks are run (# of boots, # of days, etc).

Running "sudo touch /forcefsck" in the root directory will cause an fsck check to be run on the next boot.

What's the name of the package that contains autofsck?  "aptitude search autofsck" doesn't have any results, and "aptitude search fsck" doesn't seem to return anything relevant except "showfsck" which I don't think is what I'm looking for.  Having fsck run at shutdown would be better, in my opinion, because I wouldn't have to wait for the check to run whenever I'm just wanting to start up real quick and do something.  How could I make it run on shutdown?

Thanks,
Derrick

---

### Post by drs305 on 2008-09-06
derrick81787,

It's in my synaptic but apparently because I installed an external .deb package.

Here is the ubuntu wiki link for autofsck, which contains the installation instructions and link to the deb download:
[https://wiki.ubuntu.com/AutoFsck]("https://wiki.ubuntu.com/AutoFsck")

I use it often and am very satisfied with its performance. There is a note in the wiki on how to correct the problem if it tries to run on every shutdown.

---

### Post by forger on 2008-09-07
> **derrick81787 said:**
> So it's something in the spash screen and not in the bootup process itself?  If so, that's the problem, then because I don't have a splash theme installed.  I guess that's something I should've made clear in my first post...

Yes, I think that the Esc for fsck is connected with the usplash. To get the usplash back you have to install it along with its dependencies:
```
sudo apt-get install usplash-theme-ubuntu
```

---

### Post by derrick81787 on 2008-09-08
> **forger said:**
> Yes, I think that the Esc for fsck is connected with the usplash. To get the usplash back you have to install it along with its dependencies:
```
sudo apt-get install usplash-theme-ubuntu
```

Alright, I'll look into that.  Thanks a lot to everyone who helped out.

- Derrick

---

### Post by spacedoubtman on 2008-10-05
I get the same problem. It would be great to be able to cancel (or delay) the check sometimes. I'm sure I used to be able to use ctrl+c

I looked and have usplash installed - is there anything I can do to configure it?

---

