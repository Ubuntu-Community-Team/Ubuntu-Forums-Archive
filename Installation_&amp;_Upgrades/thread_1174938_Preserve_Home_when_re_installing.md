---
title: "Preserve Home when re installing?"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2009-05-31
This facility seems to have been suggested, approved, and implemented, apparently for 8.04 an dI guess later versions.

[https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-preserve-home](https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-preserve-home)

Can someone please (confirm and) summarise this works - do I have to choose the manual partitioning during the install for example, or is there some particular item or choice to click upon?

tia

---

### Post by merlinus on 2009-05-31
Do you have an existing /home partition?  If so, then yes, select manual at the partitioning screen.  Find your /home partition, select use but do not format.

Then select the partition where you want to install the root filesystem.

---

### Post by Linteg on 2009-05-31
If you choose manual partitioning and select the same mount points as before (**do not format the drive/partition!**) /home will still be there but /bin /etc /usr and so on will be deleted.

---

### Post by zika on 2009-05-31
> **Linteg said:**
> If you choose manual partitioning and select the same mount points as before (**do not format the drive/partition!**) /home will still be there but /bin /etc /usr and so on will be deleted.
Am I getting this right: even though I (still) do not have separate /home partition I can preserve it in re-install by ... what ... choosing manual (as I always do) and preventing from formatting the existing Ubuntu partition ...?

---

### Post by merlinus on 2009-05-31
No, plain and simple.  If your /home directory is on the same partition as /, it will be gone, because when installing a new version you have to format the / partition.

You can move your /home directory to a new partition, however, by following these steps:

[http://www.go2linux.org/how-to-move-home-directory-to-another-partition]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by zika on 2009-05-31
> **merlinus said:**
> No, plain and simple.  If your /home directory is on the same partition as /, it will be gone, because when installing a new version you have to format the / partition.
You can move your /home directory to a new partition, however, by following these steps:
[http://www.go2linux.org/how-to-move-home-directory-to-another-partition]("http://www.psychocats.net/ubuntu/separatehome")
Thank You, I know that but I kind of misread (obviously) that post and I wanted to clear that.

---

### Post by Linteg on 2009-05-31
The spec ***is*** implemented.

---

### Post by zika on 2009-06-01
> **Linteg said:**
> The spec ***is*** implemented.
/home is not mentioned. So is it preserved?

---

### Post by merlinus on 2009-06-01
Thanks, Linteg.  Live and learn....

---

### Post by VastOne on 2009-06-01
> **zika said:**
> /home is not mentioned. So is it preserved?

Is /home on a separate partition? If it is you can preserve it, if it is not you cannot. Unless of course you have it backed up elsewhere

---

### Post by Linteg on 2009-06-01
> **zika said:**
> /home is not mentioned. So is it preserved?
According to the full spec, at least /home, /srv and /root are preserved, see [https://wiki.ubuntu.com/UbiquityPreserveHome](https://wiki.ubuntu.com/UbiquityPreserveHome)

I just tried it on a Virtualbox install of Ubuntu, files in /home, /root, and /srv were preserved.

---

### Post by zika on 2009-06-01
> **Linteg said:**
> According to the full spec, at least /home, /srv and /root are preserved, see [https://wiki.ubuntu.com/UbiquityPreserveHome](https://wiki.ubuntu.com/UbiquityPreserveHome)

I just tried it on a Virtualbox install of Ubuntu, files in /home, /root, and /srv were preserved.
Cool! That is good news... It makes me hard to wait for a good time to update to Karmic ... :) It also makes hacking Jaunty less dangerous ... :)

---

