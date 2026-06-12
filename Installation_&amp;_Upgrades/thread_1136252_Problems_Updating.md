---
title: "Problems Updating"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by accooper on 2009-04-24
Am I the only one have a problem upgrading?  I have tried several times and nothing happens and then it will download like dial-up.  I am on a cable connection.  My net meter says I'm pumping out some high numbers.  Is it just because the Ubuntu site is swamped?

:guitar:

Andrew

---

### Post by Partyboi2 on 2009-04-24
When a new release comes out the servers get busy so you will probably noticed speed reductions for awhile.

---

### Post by pytheas22 on 2009-04-24
Yes, the Ubuntu servers are just overwhelmed right now and will probably remain that way for a few days.  You might have better luck if you go to System>Administration>Software Sources and choose a different download mirror.

If you're adventurous, you can also try [using apt-p2p to do the upgrade]("http://www.ubuntugeek.com/how-to-use-apt-p2p-for-faster-upgrades-from-ubuntu-intrepid-810-to-jaunty-904.html").  It downloads the files over the p2p network rather than from a server, which would probably be much faster.  But it's aimed at more advanced users.

---

### Post by doas777 on 2009-04-24
I've been through this before, so I usually start the download before heading off to work on release day. I usually do clean installs (seperate home partitions are the best) so I don't have to wait hours and hours. 
last time i tried a distro upgrade online, it took about 23 hours to download the necessary files.

---

### Post by Garrovick on 2009-04-24
I went back to 8.10 and destroyed my 9.04 CD.

I don't have the experience to trouble shoot or post a valid problem description.

The ISO downloaded,and 9.04 seemed to install "normally". But I have things missing, and am getting misdirected or bad errors. Like telling me directories do not exist, while I'm looking at them in another window and telling me that it can't find drives that don't even exist any way. Like drives "G" one time and "H" another.  I have one hard drive and one optical drive.

Think it's when it froze for several minutes at 82% scanning mirrors, that should have clued me in, that some things are missing.

Now that I reverted, every thing is back to normal. Darn, and to think, yesterday I thought all was good.

---

### Post by pytheas22 on 2009-04-24
> I went back to 8.10 and destroyed my 9.04 CD.

I don't have the experience to trouble shoot or post a valid problem description.

The ISO downloaded,and 9.04 seemed to install "normally". But I have things missing, and am getting misdirected or bad errors. Like telling me directories do not exist, while I'm looking at them in another window and telling me that it can't find drives that don't even exist any way. Like drives "G" one time and "H" another. I have one hard drive and one optical drive.

Think it's when it froze for several minutes at 82% scanning mirrors, that should have clued me in, that some things are missing.

Now that I reverted, every thing is back to normal. Darn, and to think, yesterday I thought all was good.

It sounds like you had an unclean upgrade.  I've never had good luck in the past trying to update online--something always ended up broken.  I think it's a better approach just to do a clean install of the new release.  If you keep /home on a separate partition, you can do it without losing any of your personal files or settings.

---

### Post by Tiger658 on 2009-04-25
I am experiencing REALLY slow download times for updates, and new packages (To the tune of 45kB/sec as opposed to 1mb/sec before installing 9.04). Should this also be attributed to the swamped servers? If so, how long do you think until they speed back up?

---

### Post by Partyboi2 on 2009-04-25
> **Tiger658 said:**
> I am experiencing REALLY slow download times for updates, and new packages (To the tune of 45kB/sec as opposed to 1mb/sec before installing 9.04). Should this also be attributed to the swamped servers? If so, how long do you think until they speed back up?
Yes updating from the servers will be slower, give it a week and it should be a lot better.

---

### Post by Tiger658 on 2009-04-25
Ok, thanks. It kinda scared me at first.

---

