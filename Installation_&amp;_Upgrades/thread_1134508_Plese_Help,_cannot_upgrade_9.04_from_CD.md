---
title: "Plese Help, cannot upgrade 9.04 from CD"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by JMacGill on 2009-04-23
I am running Ubuntu 8.10 amd64 on a Sony Vaio VGN-FW290. I attempted to do the upgrade to 9.04 today using Synaptic but the files are downloading so slowly that it said it would take 9-12 hours (it fluctuates). 

I don't want to wait that long so i fallowed the instructions here ([http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")) and used the built in bittorrent client to download the alternate CD (9.04 amd64)

I mounted the image and started the install just fine using gksu "sh /cdrom/cdromupgrade"Durring the install, it asks if I want to include the latest updates from the internet. It says if I answer 'no' the network is not used at all. I select 'No' and then when it's at the "Getting new packages" stage, it instantly finds about 970 packages and then it procedes to start downloading the rest (about 180) off the internet, and still says it will take about 3-6 hours.

If I turn off the internet it blazes through the "Getting new packages" stage and then says that it failed to get all the packages. I can also see that it's looking at a website for the packages even though I select 'No' when it asks if I want to use the network. After this, it cancels the update.

Why is it still going online (or trying to) to find packages even when I've told it not to?  How can I get it to just use the CD for the upgrade?  I just want to get 9.04 installed, I can update the packages later.

---

### Post by trpnblies7 on 2009-04-23
I'm having the same exact problem. I'd love to know how to fix this.

---

### Post by dcwood on 2009-04-23
Ditto on the problem here. I think it blases through the first few files as they were previously downloaded before I abandoned that approch in favor of using the upgrade CD.

I wonder if it has something to do with the fact that the upgrade was first attempted through the upgrade manager before using the CD - Just a wild guess.

---

### Post by por100pre1 on 2009-04-23
Today is not a good day for upgrading, not even with CDs. Please wait a couple of days before trying again.

---

### Post by wirechief on 2009-04-23
The only way i know of updating would be with Ubuntu cd/dvd 's I think
they have special coding and require the user to make a option to install
software from the cd in the synaptic installer. If you downloaded a .iso
it is used for installing to a un-used partition not for getting files.

---

### Post by barney385 on 2009-04-23
You're suppose to use the alternate cd for upgrading...

---

### Post by projecthikari on 2009-04-23
I got a similar problem... After 3 hours, it went *boop!* sorry, can't do it.
Heavy sigh for me.
I used the update manager, though.

---

### Post by Stavro on 2009-04-23
I don’t mean to hijack anyone’s thread, but I believe this question is somehow related. Does anyone know if it's possible to install 9.04 over an existing 7.04 installation using the standard liveCD and retaining the existing file system (ext3).

The machine is fairly modern, with one 80GB fixed disk and GRUB to handle loading XP.

---

### Post by Slim Odds on 2009-04-23
> **Stavro said:**
> I don’t mean to hijack anyone’s thread, .... Then start a new tread.....

You can use the same partitions, but you'll need to reinstall.

That's why it's a really good idea to keep a separate partition for /home

---

### Post by Slim Odds on 2009-04-23
The the original poster and others with this issue.

The alternate install CD still has to have limited number of packages. So if you have a system to which you've added lots of packages, the only way to update those is to go to the Internet.

One thing about a system wide update like this is that lots of things need to match. So there may just be no way around some Internet access during the upgrade.

---

### Post by bwpopper on 2009-04-23
Seems I remember reading that you do have to use the alternate disc for upgrades, and I'm fairly certain that the only way to go from 7.10 to 9.04 is to incrementally go version to version.  Probably a good idea to do as suggested and keep /home separate from the rest of the OS.  Wish I had thought of that earlier, but it's nothing a quick backup can't fix.

---

### Post by Slim Odds on 2009-04-23
> **bwpopper said:**
> Seems I remember reading that you do have to use the alternate disc for upgrades, and I'm fairly certain that the only way to go from 7.10 to 9.04 is to incrementally go version to version.

Yes, the only big jump that you can do is from LTS to LTS.

---

### Post by DJ_Cripple on 2010-04-30
Nice one Slim Odds - sounds like a good explanation.

---

