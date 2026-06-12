---
title: "Upgrade Direct From Intrepid to Karmic?"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by klausner on 2009-11-06
Is there a way to upgrade directly from 8.10 to 9.10, skipping Jaunty? Other than doing a new install? 

Update Manager offers to let me go to 9.04, but I'd rather skip Jaunty to avoid all the Intel video issues reported. Karmic supposedly has these fixed, and testing the Karmic Live CD shows impressive performance improvements.

Tried just installing the 2.6.31 kernel, but it won't boot. Have also seen suggestions to change my repositories to point to the Karmic files, and then do updates, but there don't seem to be any reports if this actually works.

So is there a way to skip Jaunty?

---

### Post by tommcd on 2009-11-06
Skipping versions is not recommended when doing dist-upgrades. You should upgrade in sequence, i.e., 8.10 > 9.04 > 9.10. In addition, it is recommended that you have all the updates before upgrading to the next version. 
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
I think it would be faster and easier, to just do a clean install of Karmic. This would also be the best way to avoid problems during the upgrade.

---

### Post by klausner on 2009-11-06
> **tommcd said:**
> Skipping versions is not recommended when doing dist-upgrades. 

Yet the [changelog]("https://launchpad.net/ubuntu/+source/update-manager/1:0.126/+changelog") for update-manager on Launchpad indicates that the functionality was added to go directly from Hardy to Karmic. I just don't know *how* to invoke this.

---

### Post by woodnymph on 2009-11-06
on a related note, a similar question ..

i am running 8.04 LTS heron and wanting to upgrade.  if i wait for the next LTS 'lynx', will i be able to do a direct upgrade - LTS to LTS -, skipping all the intermediate releases?  or will i still have to do either the sequential upgrades or the fresh install?  trying to decide to deal with karmic now or wait til spring .. thanks

---

### Post by tommcd on 2009-11-07
> **woodnymph said:**
> 
i am running 8.04 LTS heron and wanting to upgrade.  if i wait for the next LTS 'lynx', will i be able to do a direct upgrade - LTS to LTS -, skipping all the intermediate releases?  or will i still have to do either the sequential upgrades or the fresh install?
When Lucid Lynx 10.04 comes out you should be able to upgrade directly from Hardy LTS to Lucid LTS. Upgrading directly from Dapper 6.06 LTS to Hardy LTS was supported:
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)
 So I would think that upgrading from Hardy LTS to Lucid LTS should be supported also.

---

### Post by tommcd on 2009-11-07
> **klausner said:**
> Yet the [changelog]("https://launchpad.net/ubuntu/+source/update-manager/1:0.126/+changelog") for update-manager on Launchpad indicates that the functionality was added to go directly from Hardy to Karmic. I just don't know *how* to invoke this.
I did not follow the changelogs. I was going by the release notes and what is recommended on the links I posted.
Also, you said you are running 8.10, and not Hardy 8.04.
If upgrade manager only offers you to go to 9.04, then the only way to upgrade would be in sequence. At least that is the only way that seems to be officially supported.

---

### Post by klausner on 2009-11-20
[QUOTE=tommcd;8263482If upgrade manager only offers you to go to 9.04, then the only way to upgrade would be in sequence. At least that is the only way that seems to be officially supported.[/QUOTE]

Is there an unofficial way that's known to work?

---

### Post by snowpine on 2009-11-20
> **klausner said:**
> Yet the [changelog]("https://launchpad.net/ubuntu/+source/update-manager/1:0.126/+changelog") for update-manager on Launchpad indicates that the functionality was added to go directly from Hardy to Karmic. I just don't know *how* to invoke this.

I believe this was done for testing the upcoming Hardy->Lucid LTS migration. 

You asked for an UNOFFICIAL method. Perhaps you could edit your /etc/apt/sources.list and change all "intrepid" to "karmic"? I used this method once to go from gutsy to hardy. Who knows if it would work for intrepid->karmic?

---

### Post by klausner on 2009-11-20
> **snowpine said:**
> I believe this was done for testing the upcoming Hardy->Lucid LTS migration. 

You asked for an UNOFFICIAL method. Perhaps you could edit your /etc/apt/sources.list and change all "intrepid" to "karmic"? I used this method once to go from gutsy to hardy. Who knows if it would work for intrepid->karmic?

I've seen that suggested elsewhere, but no seems to have reported if it actually works.

---

### Post by tommcd on 2009-11-21
> **klausner said:**
> I've seen that suggested elsewhere, but no seems to have reported if it actually works.
This is why I did not want to suggest this. As Snowpipe said: "Who knows if it would work for intrepid->karmic?"

So this is unsupported and would be something you do at your own risk. I would think a clean install of 9.10 would be the way to go here, rather than trying to sort out the ptoblems that would likely develop after an upgrade done like this, but it is your system.

---

