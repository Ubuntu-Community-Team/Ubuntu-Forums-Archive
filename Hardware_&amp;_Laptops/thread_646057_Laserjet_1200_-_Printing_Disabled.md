---
title: "Laserjet 1200 - Printing Disabled"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by secular on 2007-12-20
I've looked at a few similar problems posted in other threads, but I haven't found one with a solution to my problem.

I have an HP Laserjet 1200 that's worked well in Linux for a couple of years now. 

Since installing Gutsy, it's been disabled at random. Sometimes it's disabled after rebooting. Sometimes it's disabled after printing one item. 

To enable it, I go to System, Administration, Printing. Once there, I click on the Policies tab and select Enabled. Sometimes this allows me to print a few times in various applications, but then it becomes disabled later.

I have CUPS installed, and I've re-installed both it and the printer a couple of times.

Any help here would be appreciated.

---

### Post by The Cog on 2008-01-25
Happens to me too, and I've seen other posts complaining of the same thing. Mine's an HP Deskjet-1280. All the others I've read are HP too. Hmmm.

Is there a way to give a user rights to re-enable the printer without giving them full admin rights to mess up everything?

UPDATE:
Yes, you can allow users to enable printers by adding them to the lpadmin group. But there seems to be a bug in the users and groups management GUI, so the only reliable way to do this seems to be from the command line.

---

### Post by secular on 2008-02-03
> **The Cog said:**
> Happens to me too, and I've seen other posts complaining of the same thing. Mine's an HP Deskjet-1280. All the others I've read are HP too. Hmmm.

Is there a way to give a user rights to re-enable the printer without giving them full admin rights to mess up everything?

UPDATE:
Yes, you can allow users to enable printers by adding them to the lpadmin group. But there seems to be a bug in the users and groups management GUI, so the only reliable way to do this seems to be from the command line.

I'm the only user on this machine, but I don't need to do anything as root to re-enable it. I just do as I say in my original post.

Since I posted first on this, I've seen at least one CUPS update listed, and I've done that. My problem remains, though.

Thanks for your input.

---

