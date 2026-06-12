---
title: "Disk drives checked every boot."
date: 2011-03-19
forum: Hardware
---

### Post by Daminator on 2011-03-19
Hi all,

One of my laptops checks it's drives every boot.

It says
"Your disk drives are being checked for errors. This may take some time"

Sometimes it just checks (and takes a good 10 minutes about it), other times it says that I need to press F to fix things, which also takes about 10 minutes.

This has been happening for a few weeks. Nothing 'seems' to be actually wrong with my drives and updates haven't fixed the problem.

I had this a year or two ago with Ubuntu on this laptop, but then there was either an update that sorted it out or someone found a fix.

Any ideas how to sort things out this time?

Thanks
Damian

---

### Post by wyliecoyoteuk on 2011-03-19
Is your clock OK?
Normally disk checking is every so many days or so many boots.

[[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=859327") may help.

---

### Post by Daminator on 2011-03-19
Clock seems ok to me.

I'd be fine with every 25 boots or so (like my other Ubuntu systems are). Everyboot is not so good. It's the family computer so 10 - 15 minutes to turn on is not great.

Damian

---

### Post by KegHead on 2011-03-19
Hi!

Which Version are you using?

KegHead

---

### Post by dabl on 2011-03-19
Are you using the Ubuntu shutdown menu item to shut it down and power off?  What filesystem format did you use when you installed the system?

If it is running fsck on every boot (and you have not changed the fsck default setting), that is probably because it is detecting filesystem corruption -- not a good thing.  Either there's some problem with the way the system is being shut down, or there's a hard disk drive that is starting to go bad.

---

