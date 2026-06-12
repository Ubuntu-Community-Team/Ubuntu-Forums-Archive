---
title: "Apt-get upgrade message and no obvious help on website"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by taryneast on 2006-01-05
Hi, I know, the topic is probably ambiguous - apologies.

this is not a "is there any help on upgrading" question... it's more a potential upgrade to the GUI (should this go in as a bug?).

So picture this - I'm using synaptic and as I close the app it prompts me to upgrade to breezy by going to [www.ubuntulinux.org](www.ubuntulinux.org)

I go to the above link and immediately start looking for the big red message saying "upgrading from hoary to breezy"... which isn't there. I go to the downloads page and only find info on downloading new versions of breezy...  It's not until I trawl these fora that I find myself some useful links for this information...

So my point?

Would it be possible to add a link on the ubuntu homepage (or even the download page) for upgrading form one version to another? Especially given that the message is clearly indicating that this is where a person has to go to find this information...


Cheers,
Taryn
[who may, of course, have simply missed such a link - in which case, maybe it just isn't prominent enough... ?]

---

### Post by Zelut on 2006-01-05
I think you are right.  I don't remember seeing any links for upgrading other than downloading the latest copy & installing that way.  That is most likely what they are referring to...

If you would like to simply upgrade your current version to the later you can do it with the following commands at the prompt:

sudo apt-get update
sudo apt-get dist-upgrade

That will move you from Hoary to Breezy but it occasionally leads to some issues.  I'd suggest backing up your /home and doing a fresh install if you're set on upgrading.

---

