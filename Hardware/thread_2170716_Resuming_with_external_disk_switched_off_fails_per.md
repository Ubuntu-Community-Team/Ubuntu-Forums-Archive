---
title: "Resuming with external disk switched off fails permanently"
date: 2013-08-27
forum: Hardware
---

### Post by belgianfries on 2013-08-27
I have an exteral eSATA disk connected to a Lenovo L420 notebook, which I use only for data. The system (13.04, 3.8.0-29-generic) boots from the internal disk.
Now the system goes to standby while the external disk is mounted. Then I switch off the external disk.
When the system now resumes, and I forgot to switch on the external disk, resume fails permanently, even if I switch on the external disk and wait.
The system then needs to be force-stopped and restarted.

Isn't this behaviour unexpected? If the system cannot resume with the external disk basically missing, I'd expect it to wait until it becomes available, and then resume normally, instead of failing permanently.

---

### Post by tgalati4 on 2013-08-27
You have a valid concern, but look at it this way.  How would Linux behave if you disconnected your internal hard disk during a session?  Would it freeze completely?  Would it wait for a long time for you to reconnect it?  Linux expects perfect hardware.

When you power off your external drive and your notebook resumes, a mounted filesystem is now mysteriously gone.  Linux does not tolerate file systems that disappear without kernel involvement.  What are the errors shown in *dmesg* or /var/log?

You would need to add an unmount command to your suspend script, then a remount command in your resume script.

Why do you need to power off your external disk after suspend?  Does the disk not go to sleep as well?  Does it keep spinning or does it park the heads and go to idle?

---

