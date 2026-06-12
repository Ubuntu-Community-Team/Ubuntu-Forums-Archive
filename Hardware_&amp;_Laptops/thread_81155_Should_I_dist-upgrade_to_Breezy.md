---
title: "Should I dist-upgrade to Breezy?"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by vayu on 2005-10-23
I have a Dell 6000.  I don't have the time to tweak a fresh install to get everyhing back that I have on it now with Hoary.  I'm interested in hearing dist-upgrade stories.  Success and/or failures....

---

### Post by kelsey23 on 2005-10-23
No!!! Don't do sudo apt-get dist-upgrade! That's what I did, and now my Ubuntu installation is terrible. Clean install is your best bet.

---

### Post by aysiu on 2005-10-23
Dist-upgrade could very well work, but I'd advise a clean install as well. If you are planning to upgrade every six months, you may want to create a separate /home partition to save your data and settings from being affected by the upgrade.

---

### Post by gruepig on 2005-10-24
Just curious ... Why would you recommend a clean install over a dist-upgrade?  I've dist-upgraded Debian many times and Ubuntu once and it's so nice not to have to reinstall; is there something I've missed out on by not doing clean installs?

---

### Post by jorgen_s on 2005-10-24
I have dist-upgraded with apt-get once in Debian and now once with Ubuntu. Both times it felt like I only had a half new system and I still had big parts the old one left. apt-get reported that a lot of packeges were held back, didn't find any good info of how to fix things and last time the new gnome features was missing etc. I am sure you could manually fix things but a clean install is better I think.

---

### Post by jarturoar on 2005-10-24
I did a dist-upgrade for my laptop and my amd64, if you know what you're doing there should now be any major problem, the idea is to be sure to update the metapackages, ubuntu-base, ubuntu-desktop, there may be  a few old backs but you can specify to update then.

My advice for a newbie fresh-install, my friends did that, i started playing with backports in debian woody so a lot of dead debian installations gave me to courage to fight the monster and learn to do it right ;)

---

### Post by jeb0921 on 2005-10-24
I,ve done a dist upgrade on four different machines now.  The first two were with apt, the second two using the ubuntu cd for breezy install.  The cd upgrade was the smoothest and fastest.  Although all of the upgrades had no problems at all when done.

I thought it was kinda nice putting the cd into the drive and having a window pop up asking me what I wanted to do.

---

### Post by ecobuntu on 2005-10-24
what's the point of running a debian based distribution if you can't just do apt-get dist-upgrade?  obviously this needs to be worked out.  you can definitely do this in debian without a problem.

---

### Post by gorkhal on 2005-10-24
hey..i dist upgraded too..on my compaq presario...and whoa...one nightmare after another some of my icons went missing...font rendering went absolutely nuts....i thought ohh god breezy screwed my system..but a clean install put such unholy thoughts to rest....a clean install though would entail more work...its still worth it :D

---

### Post by fannymites on 2005-10-25
I dist-upgraded 6 weeks before breezy went official.  There was a lot to upgrade since I had kde, gnome and xfce all installed.  Went like clockwork.  No probs at all.

---

### Post by bryan986 on 2005-10-25
If you have all your data backed up (which you should), why not try a dist-upgrade, and if it goes bonkers, then do a clean install instead?

---

### Post by Jarz Corp on 2005-11-03
I have tried the Ubuntu dist-upgrade from Hoary to Breezy on several machines now.

What ever U do dont go that way, U will waste way to much time fiddling with it afterwards trying to solve depend... issues.

It seems Ubuntu still has quite a bit of way to go until it will be ready for end users, which is a hassle for me as I have introduced it to a lot of those.

Personally I have moved to Suse where the forums never get close to Ubuntu standards but where the OS itself is rock solid and never makes me waste my time fiddling with all kinds of c..., I am on a 64bit machine so I have really learned this the painfull way.

Sorry this turned into a rant: Let me make it short. Dont dist-upgrade it can't be done on ubuntu unless U have just installed hoary and not touched anything at all.

---

### Post by doclivingston on 2005-11-03
I've dist-upgrade'd several machines, some straight Hoary to Breezy, others a reasonable modified Hoary to Breezy, some with the Colony CDs - and they all worked.

---

