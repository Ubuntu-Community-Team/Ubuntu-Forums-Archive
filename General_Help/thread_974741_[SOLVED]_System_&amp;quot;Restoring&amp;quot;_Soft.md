---
title: "[SOLVED] System &amp;quot;Restoring&amp;quot; Software"
date: 2008-11-07
forum: General Help
---

### Post by Yuki_Nagato on 2008-11-07
I am looking for a way to "backup" a computer in such a way that I can break things and then have others fix them for practice.  But this still needs to be a working workstation.

Deep Freeze is similar to what I had in mind, but not exactly.  I want to be able to take a "snapshot" of my hard drive, and then restore that exact snapshot at a later date if need be.  I understand this would half the effective size of my hard drive, but this method would prove the most effective.

It is not really a "backup" program, but a way to quickly restore a computer to a slightly older configuration.  My family members are sick of buying new Kaspersky licenses.

---

### Post by taladan on 2008-11-07
[http://windowsdream.com/ping.html]("http://windowsdream.com/ping.html")

It's like Norton Ghost, but free, and linux based.  Set your system up exactly like you want it, then grab a partimage of it.  Takes roughly 10 minutes to drop the image back to the drive on a fresh install.  The more data you have on the drive, the longer it'll take to drop the image back to the drive.

I use this system at work all the time with images of windows to drop to refurbished school systems and it works like a charm.

Tal

---

### Post by dcstar on 2008-11-08
> **Yuki_Nagato said:**
> I am looking for a way to "backup" a computer in such a way that I can break things and then have others fix them for practice.  But this still needs to be a working workstation.

Deep Freeze is similar to what I had in mind, but not exactly.  I want to be able to take a "snapshot" of my hard drive, and then restore that exact snapshot at a later date if need be.  I understand this would half the effective size of my hard drive, but this method would prove the most effective.

It is not really a "backup" program, but a way to quickly restore a computer to a slightly older configuration.  My family members are sick of buying new Kaspersky licenses.

Install (the free) VMWare server, make VMs of whatever you run and use the "Snapshot" feature to preserve them for rollback.

---

### Post by Yuki_Nagato on 2008-11-19
Both are excellent suggestions.

I am currently using the PING option on my main machine, and am backing up my virtual machines with the snapshots.

Excellent.

---

