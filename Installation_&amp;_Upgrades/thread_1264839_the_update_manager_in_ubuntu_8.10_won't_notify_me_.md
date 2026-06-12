---
title: "the update manager in ubuntu 8.10 won't notify me to upgrade to 9.04"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by justo222 on 2009-09-12
i installed ubuntu 8.10 (from a downloaded CD) onto 2 computers.  the install on the laptop told me that the system was not up-to-date.  i installed the updates, rebooted, and it then told me that there was a newer version of ubuntu available (v. 9.04).  so far, so good!!  in the "update manager", i was then able to do the upgrade and now have ubuntu 9.04 on the laptop.

i then started up my desktop which had v.8.10 installed a number of months ago (from the same CD).  i went online and installed all the updates for it, rebooted, and it did not tell me about the 9.04 upgrade.  i then compared the installs between the laptop and the desktop, and all settings/repositories etc... in the "synaptic package manager" are identical between the 2 computers.

does anybody know what i can do to get my desktop to tell me about the 9.04 upgrade?  i suppose i could download the upgrade, burn a CD and do the manual install as is mentioned on the website, but that's not the point.

j

---

### Post by snowpine on 2009-09-12
From the terminal (applications-accessories-terminal):

```
sudo do-release-upgrade
```

---

### Post by justo222 on 2009-09-12
> **snowpine said:**
> From the terminal (applications-accessories-terminal):

```
sudo do-release-upgrade
```

thanks snowpine.  i'm running this now, and it appears to be upgrading my install to v.9.04, however, this doesn't seem to be answering my question.  my question was how do i get the "update manager" to notify me when there is a new version of ubuntu available?  the "update manager" seems to work properly on my laptop install but not on my desktop install.  both have had their initial install from the same CD and neither are networked together.

any help on how to fix this would be greatly appreciated.  i will definitely keep snowpine's terminal commandline suggestion as a future backup.

j

---

