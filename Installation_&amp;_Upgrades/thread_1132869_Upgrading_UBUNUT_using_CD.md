---
title: "Upgrading UBUNUT using CD?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by ravi_buz on 2009-04-22
I have ubuntu 8.04 installed and i have ubuntu 8.10 in a cd , Can i upgrade my ubuntu using the CD instead of downloading the update

---

### Post by leonardo_neo on 2009-04-22
> **ravi_buz said:**
> I have ubuntu 8.04 installed and i have ubuntu 8.10 in a cd , Can i upgrade my ubuntu using the CD instead of downloading the update

If you have a separate /home partition, then you can do a fresh install, and documents in your /home folders will remain intact.

---

### Post by slakkie on 2009-04-22
You could use the following approach, but that requires the alternate CD and not the live cd people normally have.

[https://help.ubuntu.com/community/IntrepidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/IntrepidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

Good luck. I think upgrading via do-release-upgrade works better, because you will need to upgrade your machine straight after the initial upgrade via CD. Upgrading via apt does not require an additional upgrade.

---

### Post by slakkie on 2009-04-22
> **leonardo_neo said:**
> If you have a separate /home partition, then you can do a fresh install, and documents in your /home folders will remain intact.

This is not really an answer to his/her question, now is it?

---

### Post by leonardo_neo on 2009-04-22
> **slakkie said:**
> This is not really an answer to his/her question, now is it?

Suggesting the best possible solution should be the approach. If you wish to stick to what is asked by the questioner '***strictly***', then suggestion of using "alternate CD" also doesn't qualify that criteria.

Anyway, very less information was given in the question, and I suggested the best possible I could with all my goodwills.

---

### Post by cubeist on 2009-04-22
I think you can put the cd in the drive, then open software sources (in the system/admin menu) and add the cd to the sources, then run the update manager and you should have the option to upgrade to a new release.

I have never tried this, but I have seen other posts similar to this method.

---

