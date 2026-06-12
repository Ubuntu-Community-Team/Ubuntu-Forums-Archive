---
title: "Can't upgrade from Hardy - no upgrade available?"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by J2R on 2009-08-17
I'm trying to move what was a Kubuntu Gutsy installation step by step up to Jaunty. I managed to upgrade via Adept to Hardy, and most things are working pretty well. The next step is Intrepid, but I'm not having much luck. 

The recommended Kubuntu way is to use the Version Upgrade button in Adept, but when I try to do this, I get as far as where it says to click Finish to close Adept and launch the Distribution Upgrade tool to upgrade to 8.10. I click Finish and that closes the dialog, but Adept does not close, and no Distribution Upgrade tool appears.

So, I thought I'd try using the dist-upgrade approach from the command line. I do sudo apt-get update, then sudo apt-get dist-upgrade and this is what I get:

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Huh? Why no new version?

What should I do next?

---

### Post by dstew on 2009-08-17
In order for dist-upgrade to work, you need to have the repositories for the next distribution in your /etc/apt/sources.list. See [this page]("https://help.ubuntu.com/community/Repositories/CommandLine") for information on how to do this.

---

### Post by ptn107 on 2009-08-17
Edit /etc/update-manager/release-upgrades and change 'Prompt=lts' to 'Prompt=normal'.  Then try update manager again.

---

### Post by J2R on 2009-08-17
> **ptn107 said:**
> Edit /etc/update-manager/release-upgrades and change 'Prompt=lts' to 'Prompt=normal'.  Then try update manager again.

I tried this and then repeated both attempted upgrade methods, but still no joy. (update-manager itself is not present in Kubuntu, and I believe Adept fulfils the same function).

---

### Post by J2R on 2009-08-17
> **dstew said:**
> In order for dist-upgrade to work, you need to have the repositories for the next distribution in your /etc/apt/sources.list. See [this page]("https://help.ubuntu.com/community/Repositories/CommandLine") for information on how to do this.

Is it safe to simply replace all instances of 'hardy' with 'intrepid' in sources.list, then? I know I've done this kind of thing before, but my understanding was that the 'proper' distribution upgrade procedures do this automatically, and with perhaps a little more intelligence (adding new repositories, removing obsolete ones, etc).

---

### Post by dstew on 2009-08-17
Yes, I think replacing intrepid with hardy is the way to go. That is my best guess. I haven't done this "by hand" upgrading, only using the update manager in the past, so I don't know for sure. But looking at how apt-get dist-upgrade works, it looks like you need the hardy repositories in the sources.list file.

---

### Post by mcduck on 2009-08-17
"sudo apt-get dist-upgrade" has nothing to do with upgrading to next distribution version. It updates *current* distribution version. Aöthough I agree that the command might sound like it was for upgrading to new releases.. :)

- "apt-get upgrade" upgrades installed packages, and adds new packages if required. This is similar to the upgrade done with the Update Manager.

- "apt-get dist-upgrade" upgrades installed packages, and is able to both add and/or remove packages if required. Updating through Synaptic Package Manager works in the same way.

The command to upgrade to next distribution version is "**sudo do-release-upgrade**"

(well, editing your sources.lst to use repositories for the new release and *after that* running "sudo apt-get dist-upgrade work, at least to some level, but using "do-release-upgrade" is the recommended way.)

edit: [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by J2R on 2009-08-18
Thanks very much for that. It was a stupid misunderstanding on my part.sudo do-release-upgrade did in fact do the job (although I also changed 'hardy' to 'intrepid' in sources.list, perhaps unnecessarily). The version upgrade completed fine. I have immediately set about doing the next step, to Jaunty, and this time Adept is letting me do it.

---

