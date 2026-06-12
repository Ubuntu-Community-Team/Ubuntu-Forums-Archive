---
title: "Scared to accept updates"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by alexcckll on 2009-07-30
Hi folks, 

I'm on preinstalled Ubuntu 8.04LTS - updated to 8.04.3.

I am holding off - because I notice that there is a new kernel - 2.6.24-24.57.

After all the hassles I had with 2.6.24-24.53 until -24.55 came down - where it left my machine in an unbootable state - so I had to roll back to -23.

I posted this when it happened - [http://ubuntuforums.org/showthread.php?t=1176896](http://ubuntuforums.org/showthread.php?t=1176896) and also called my vendor.

I asked them to check - and the updates after that batch were OK - so I accepted them... and and was then able to run happily..

BUT - I am terrified of taking on any more updates... as there are far too many regressions.. to Hardy!

Have other Thinkpad R61i users gone OK with the latest kernel updates?

---

### Post by aysiu on 2009-07-30
I think the simple solution is to back up your current installation.

That way if the update somehow breaks things, you can easily go back to the way things were.

You can use Remastersys or PartImage or even CloneZilla.

---

### Post by alexcckll on 2009-07-30
> **aysiu said:**
> I think the simple solution is to back up your current installation.

That way if the update somehow breaks things, you can easily go back to the way things were.

You can use Remastersys or PartImage or even CloneZilla.
Issue is, though... why should an end-user have to go through a backup process before accepting security updates?  surely it's up to release management to avoid regressions?

PLEASE - stability first...

---

### Post by aysiu on 2009-07-30
> **alexcckll said:**
> Issue is, though... why should an end-user have to go through a backup process before accepting security updates?  surely it's up to release management to avoid regressions?

PLEASE - stability first...
I didn't say the update would break anything.

You were the one who was worried about it. I'm saying if you're worried about it, back up before you do the update. If you're not worried about it, then just install the update.

Why should an end user *have to* go through the backup process? Well, an end user *doesn't* **have to** go through the backup process. Only end users who are afraid of updates breaking things should go through the backup process.

---

### Post by cmarvel on 2009-07-30
I have the same Thinkpad, which, until a few days ago, was running 8.04 like a champ.  Then I tried to upgrade to 9.04.  Jackalope took a tiny chunk of my big ubuntu partition and created a brand new operating system which because of its size could not even load post-release updates.  GRUB could not detect the Windows XP system that I had running alongside ubuntu.  I spent untold hours working with Partition Magic trying to recover but finally gave up.  Today the computer is in the shop waiting a total hard disk partition and formatting job followed by installation of a new copy of Windows XP.

I wish you luck.  Or better, wish you all the enjoyment that you can savor with 8.04.  Because I loved running Intrepid for its speed and reliability.

I do wonder why ubuntu developers have caved in to media pressure to issue new releases every six months.  Am I missing something here?  Why not every seven months?  Or every three and a half?  Or every seventeen weeks and three days?  When this artificial pressure results in the relia bility issues I confronted earlier this week, how can the cause of linux advance.

Okay, I'm off my soap box now.

---

### Post by aysiu on 2009-07-30
> **cmarvel said:**
> 
I do wonder why ubuntu developers have caved in to media pressure to issue new releases every six months. There isn't any media pressure. The six-month release schedule is something Mark Shuttleworth decided in from the very beginning before Warty Warthog (Ubuntu 4.10) was even released. It's to sync up with the Gnome releases.

---

### Post by presence1960 on 2009-07-30
> **cmarvel said:**
>   Today the computer is in the shop waiting a total hard disk partition and formatting job followed by installation of a new copy of Windows XP.



I feel for what happened to you. But it is a shame you are paying someone to do something you probably can do yourself. I never partitioned prior to Linux and with the help in here I learned to partition using the Ubuntu Live CD's gparted and the Gparted Live CD. I hadn't a clue what to do because I only used windows prior. But the knowledgeable people here broke it down to me and gave me some links to check out. The rest is history.

Maybe you feel now that you couldn't format & partition your hard disk to reinstall windows. That's cool but I know that you can do it with some help. In time, Rome was not built in a day.

P.S. you should back up regularly anyway because of a fiend we know as murphy's law. If you have the space you should also back up your root partition as asyiu said. Take no chances when it comes to your data.

---

### Post by Katalog on 2009-07-30
> **presence1960 said:**
> 
P.S. you should back up regularly anyway because of a fiend we know as murphy's law. If you have the space you should also back up your root partition as asyiu said. Take no chances when it comes to your data.

That's true of any OS, be it Windows, Mac OS, Ubuntu, etc. If your data really means that much to you, you're going to protect it just like you would any other valuable item. I have a recurring event in my Evolution calendar to remind me to do incremental backups of my home folder every two weeks. Point being that you never know what's going to happen, whether it be a bad system update, flood, fire, robbery, etc. The only thing sure in this life (besides death) is that you can always expect the unexpected. All you can do is plan for it and hope for the best.

---

### Post by lisati on 2009-07-30
> **alexcckll said:**
> Issue is, though... why should an end-user have to go through a backup process before accepting security updates?  surely it's up to release management to avoid regressions?

PLEASE - stability first...

The primary reason for making backups is not because "something bad is *definitely going to happen*" but "something bad *could happen*", whether it's a program update not quite working as anticipated, a fire in your home destroying your computer, or someone accidentally deleting your data - all things that you don't plan on having happen, but which would be a major nuisance if you hadn't taken steps to make sure your files are safe and recoverable.

---

### Post by alexcckll on 2009-08-06
For the record, I accepted the security updates last night... all is fine..

Over upGRADES... I called my vendor (Linux Emporium) and they suggets that if I was to upgrade eventually (to the new LTS)... I would be best wiping the machine and installing from scratch...

Or buy a new computer.

If I went with the second option.. means *they* would get it working.. 

(I'm running a preinstalled machine)

---

