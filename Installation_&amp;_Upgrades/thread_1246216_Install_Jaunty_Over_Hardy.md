---
title: "Install Jaunty Over Hardy?"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by rajcan on 2009-08-21
Is this possible? I've got 2 partitions on my hard drive, one for hardy and one for XP. I don't want to create a new partition, but I don't want to delete my hardy partition, so can I just install over it? I just got my Jaunty cd today so I'm wanting to do so.

---

### Post by snowpine on 2009-08-21
Yes you can install Jaunty on your existing Hardy partition. Use the "Manual" option when you get to the Partitioner step of the install. It will delete everything on your Hardy partition, so make sure you've backed up all of your data first. (Also good to back up the data on your Windows partition, just in case you make a mistake.)

---

### Post by rajcan on 2009-08-21
Ok, so do I delete my hardy partion, and then from that create a new partition for jaunty?

---

### Post by dsavi on 2009-08-21
Small correction- It deletes everything but /home. Although I would recommend backing up /home anyway.

---

### Post by snowpine on 2009-08-21
> **rajcan said:**
> Ok, so do I delete my hardy partion, and then from that create a new partition for jaunty?
Yes, that should work fine.

---

### Post by rajcan on 2009-08-21
Ok, I'm gonna try this installation and then I'll post back on it's success.

---

### Post by fishy6969 on 2009-08-21
I'm sure you've already considered this, but how about an upgrade via 'sudo do-release-upgrade -d' and upgrade from hardy -> intrepid, then repeat for intrepid -> jaunty?

Settings inc home folders #SHOULD# be preserved.

---

### Post by rajcan on 2009-08-21
Yeah, I've considered that, but I had a bad experience upgrading from kubuntu 8.10 to 9.04. Now I've heard that that particular kubuntu upgrade has problems, but after my experience I don't want to risk it. Plus with my internet that would take a minimum of 6 hours.

---

### Post by peakshysteria on 2009-08-21
> **fishy6969 said:**
> I'm sure you've already considered this, but how about an upgrade via 'sudo do-release-upgrade -d' and upgrade from hardy -> intrepid, then repeat for intrepid -> jaunty?

Settings inc home folders #SHOULD# be preserved.

I use this method every time. Always worked smooth for us on all our four machines. Going from Hardy it's important to follow The Release schedule as fishy6969 mentions. After that all should be happy days :)

[B][URL="https://help.ubuntu.com/community/UpgradeNotes"]UpgradeNotes
[/URL][/B]
Or you could always download the ISO and install from scratch. Takes about 25 minutes to install once you have the ISO burnt.

---

### Post by rajcan on 2009-08-21
Well a tad late for that. The installation's already started. Plus there wasn't really anything on my ubuntu partition. I'm installing this on the home computer, and my family mostly uses XP. So that's where all of our stuff is, incase this does go wrong we do have a backup, so I'm just praying for the best here.

On top of that my internet is ridiculously slow. It's a step above dial-up and I'm lucky to get 80 Kb/s of download speed.

---

### Post by rajcan on 2009-08-21
Ok, the installation's finished, so here's the results.

It's a success!!!

Installation went smoothly, XP is untouched, and Jaunty is working beautifully. I'm installing updates for it, and then I've got some tweaking to do after that.

---

### Post by snowpine on 2009-08-21
Good luck with Jaunty! I think it is the best Ubuntu release yet. :)

---

### Post by rajcan on 2009-08-21
Well everything works so far except for desktop effects. Apparently my video card is blacklisted and so I can't start compiz. I was running compiz on hardy so jaunty should support it. Isn't there a way to unblacklist your video card?

---

### Post by russu52 on 2009-08-21
> **snowpine said:**
> Yes, that should work fine.

i agree, it should. tried it:)

---

### Post by kaptain0 on 2009-08-21
to save your settings from one installation to another if you're doing a full install instead of an internet upgrade, you had to set your /home to a separate partition. that way whenever you install again, you just reuse the root partition, since that's all that needs to be changed and it doesn't contain your settings.
 
but you'd have had to put home in a separate partition when you installed hardy for that to matter

---

