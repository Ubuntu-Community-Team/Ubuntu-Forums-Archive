---
title: "Error in updating from Update Manager"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by rawlins02 on 2009-05-06
Running 7.10 Gutsy Gibon.

Attempted to do updates with Update Manager. Got this error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-16-generic_2.6.22-16.62_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-16-generic_2.6.22-16.62_i386.deb)

I can get to the directory linux-source-2.6.22/ in web browser, but the file is not found.

I want to also ask about the tab at top of Update Manager that says 'New distribution  release '8.04 LTS' is available. I'm curious about whether this implies that this new OS can be installed by clicking the 'Upgrade' button while current OS is running. I don't recall ever seeing that notice in Update Manager.  My apologies if I'm not making sense....

Mike

---

### Post by zvacet on 2009-05-06
> I want to also ask about the tab at top of Update Manager that says 'New distribution release '8.04 LTS' is available. I'm curious about whether this implies that this new OS can be installed by clicking the 'Upgrade' button while current OS is running.

Yes,exactly that.You can upgrade to sable version and I will recommend you to do that because Gutsy is not supported anymore and that is reason you can not get security updates.

---

### Post by rawlins02 on 2009-05-07
Thanks for the reply zvacet.  

Do you know of any potential pitfalls with doing this upgrade?  And, is this a *NEW* means to do OS installs, that is, while an existing OS is running? Sorry, but I use my machine for work and would be in a bind if everything did not work properly right off the bat, or else with minimal tweaking.  

Thanks for the additional info.

Mike

---

### Post by bapoumba on 2009-05-07
Gutsy has reached end of life, and the repos have been moved: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

You need to change your sources.list ;)

Upgrading would be better, as gutsy is not supported any longer and you do not get security updates.

---

### Post by Lindhardsen on 2009-05-07
My server is also stuck on Gutsy, what do I have to change in order to upgrade to an supported version?

apt-get dist-upgrade also fails, as it does not see the repositories anymore. What do I need to add, in order for apt to work for an upgrade? a sample file would be appreciated ;-)

---

### Post by rawlins02 on 2009-05-07
I understand that I need to update/upgrade.  Been meaning to do so for a while now.  But I'll probably have to wait, as it's most convenient to do so in a month or so, after I've inventory all the software I've installed, backed up my files, saved the Windows OS on the other partition, researched what I need to do after installing a new hard drive (eg. how to partition the new disk), and cleared my desk of some work.  Like I said, I've been procrastinating....

---

### Post by Therion on 2009-05-07
> **Lindhardsen said:**
> My server is also stuck on Gutsy, what do I have to change in order to upgrade to an supported version?

apt-get dist-upgrade also fails, as it does not see the repositories anymore. What do I need to add, in order for apt to work for an upgrade? a sample file would be appreciated ;-)
If you want to upgrade your distro simply go to:

System/Administration/Software Sources, Updates tab

And using the menu down at the bottom change the release notifications menu to "Normal Releases".  
Re-run the update manager and you'll get the notification about version 8.04 being available.

Illustrative Picture:  [http://www.refolder.com/wp-content/uploads/2009/01/top5-ubuntu-02.png](http://www.refolder.com/wp-content/uploads/2009/01/top5-ubuntu-02.png)

---

### Post by Lindhardsen on 2009-05-07
Thanks a lot!

Is there any way to do this from the console?

---

### Post by bapoumba on 2009-05-08
You need to remove third party repos and packages if you installed any. Only keep ubuntu repos.

Then change your sources.list and replace gutsy with dapper, then ```
sudo apt-get update
sudo apt-get dist-upgrade
```

Sometimes, the dist-upgrade has to be run several times in a row.

---

