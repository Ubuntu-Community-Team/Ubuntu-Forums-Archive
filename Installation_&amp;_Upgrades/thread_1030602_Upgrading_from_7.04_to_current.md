---
title: "Upgrading from 7.04 to current"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by hockman5 on 2009-01-04
I am trying to upgrade from  7.04 without having to do a new install from CD. I have used the help site that suggest adding new repository addressed to my update manager but I still receive errors saying that the repository no longer exists or does not conatin the files. Is there any other way to do the upgrade?

---

### Post by cariboo on 2009-01-04
The preffered method, is to update from 7.04-->7.10-->8.04-->8.10, to update from one version to the next use in a terminal:

```
sudo update-manager -c
```

THis will check to see if you can update. You will have to do this for every version you update to.

Jim

---

### Post by hockman5 on 2009-01-04
my problem is more complex than that. The update manager says there is an update available to 7.10 yet the files are no longer available from the repositories. The upgrade help page list some additional repositories to add to my sources list, though when I do that, it says that they do not exist either. I confirmed this by going to those address and the files are not there as listed.
There must be someone else out there who has had this problem and resolved it somehow. Anyone???

---

### Post by hockman5 on 2009-01-04
Well I guess one flaw in the Ubuntu distro's is upgrading. I see lots of people having this same problem but from different releases. I wouldn't mind having to go through the steps of coming from 7.04 to 7.10 to 8.04 . etc. And it would be so simple of the repositories just kept the files where they are or moved them to an archive location that is correctly stated in the upgrade documentations. Oh well, I guess it is a new install for me. Haven't decided on 8.04 or 8.10 though.

---

### Post by abn91c on 2009-01-04
download the 7.10 live cd and add to the repositories, the installation will be slower, then go to 8.04.8.10 like the other poster suggested.

---

### Post by hockman5 on 2009-01-04
> **abn91c said:**
> download the 7.10 live cd and add to the repositories, the installation will be slower, then go to 8.04.8.10 like the other poster suggested.

You mean fresh install 7.10? Why not just install 8.x then?
Does the live CD run without install on a Ubuntu system?

---

### Post by abn91c on 2009-01-04
> **hockman5 said:**
> You mean fresh install 7.10? Why not just install 8.x then?
Does the live CD run without install on a Ubuntu system?
no in synaptic, you can add a cdrom as a repository for  upgrades, go to the repositories section>third party updates>add cdrom
follow this guide [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by hockman5 on 2009-01-04
> **abn91c said:**
> no in synaptic, you can add a cdrom as a repository for  upgrades, go to the repositories section>third party updates>add cdrom
follow this guide [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

I will give that a whirl.....thanks

---

