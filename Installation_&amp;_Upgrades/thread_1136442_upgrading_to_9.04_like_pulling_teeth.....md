---
title: "upgrading to 9.04 like pulling teeth...."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2009-04-25
is it me, or are the servers getting hit hard ? tried the upgrade and it comes to a crawl @ Getting new packages....

---

### Post by lisati on 2009-04-25
Perhaps the server you are using is busy, it is possible to use others.

I had a tooth pulled recently (a filling fell off and there wasn't enough of the tooth left to be worth saving). I feel sorry for the dentist, she was a tiny wee thing, and seemed to be having a tough time of it.

---

### Post by bngguy on 2009-04-25
> **zero7404 said:**
> is it me, or are the servers getting hit hard ? tried the upgrade and it comes to a crawl @ Getting new packages....

first find the best mirror server, this could be done by :

System --> Administration --> Software Sources then select Other from the Download from: menu item.

then try to do the upgrade

---

### Post by bngguy on 2009-04-25
delete

---

### Post by zero7404 on 2009-04-25
thanks for the advice....
when i go and make it search for the best server to pull files from, it suggests one, and i click Choose Server....

after i say ok, in the previous window the Download from still says Main server....

perhaps it didn't take after choosing the suggested server ?

---

### Post by bngguy on 2009-04-25
> **zero7404 said:**
> thanks for the advice....
when i go and make it search for the best server to pull files from, it suggests one, and i click Choose Server....

after i say ok, in the previous window the Download from still says Main server....

perhaps it didn't take after choosing the suggested server ?

you could manually choose a server, try mirrors.us.kernel.org, i got good speed from this mirror.

---

### Post by pparks1 on 2009-04-25
Yes, the servers are heavily utilized with everybody downloading the new release.  Personally, I always start with a fresh install and I grabbed my ISO from the torrent servers.  Had in in about 20 minutes on day 1.   Haven't done a ton of installing yet, as I'm waiting for update servers to settle down, but all-in-all...this seems like a genuinely solid release.

---

### Post by lisati on 2009-04-25
> **pparks1 said:**
> Yes, the servers are heavily utilized with everybody downloading the new release.  Personally, I always start with a fresh install and I grabbed my ISO from the torrent servers.  Had in in about 20 minutes on day 1.   Haven't done a ton of installing yet, as I'm waiting for update servers to settle down, but all-in-all...this seems like a genuinely solid release.

Even Shipit is showing a "please try later" message.....

---

### Post by zero7404 on 2009-04-25
> **pparks1 said:**
> Yes, the servers are heavily utilized with everybody downloading the new release.  Personally, I always start with a fresh install and I grabbed my ISO from the torrent servers.  Had in in about 20 minutes on day 1.   Haven't done a ton of installing yet, as I'm waiting for update servers to settle down, but all-in-all...this seems like a genuinely solid release.

this is my next move....i tried 3 different servers so far i get sporadic download estimates (3 days/18 hrs/1 hr, etc...)....

it's good practice for me do do another clean install, because i eventually plan to migrate to linux, so far i've been messing with it on/off for about 7 months...still not completely comfortable with using it as a platform, not enough has gone wrong or i've had to fix something yet...so if something did get screwed up badly, i wouldn't know how to recover without losing data...(if this makes sense). so i don't trust in myself at this point to use it as a sole pc platform.

---

### Post by zero7404 on 2009-04-25
after a fresh install from disc, i am not amused with 9.04. as a matter of fact, it is less stable and more problematic than 8.10 running on the exact same hardware with the exact same packages installed.

i chose to use ext4 file system after completely removing the old ext3 partition.

i will probably go back to 8.10 (right now, after 2 cycles of installing 9.04, these problems i'm experiencing, not really in the mood to go thru it again)...

---

### Post by lbravo on 2009-04-26
Total misery... I think I have fried my Dell XPS1730 with the 9.04 upgrade.

8.01 worked almost perfectly, but the lure of a new version was strong.  So I began the upgrade, which took an entire day of start and stop downloading.

Now, when I boot, it goes to grub and after selecting 9.04, I get nothing.  If I select the last Ubuntu release on my grub list, I do get the ubuntu logo.  Then it dies.  Black screen of death, cursor blinking in upper left corner.

So now I'm stuck booting to Windows until (if) I get a solution.  I can't see my linux drive in Windows, and I can't seem to mount a drive from the BusyBox junk I get if I run restore mode.

I would like to simply be able to access my original /home directory and copy it, then install 8.01 again and be happy.  How can I do this?

Thanks in advance.

---

### Post by zero7404 on 2009-04-26
lbravo, i think that 9.04 has some bugs...
that is a really strange notion, because it was released and that usually implies that all the work that went into the previous release was incorporated into the new release...

apparently there must be some new code in 9.04 that gets heartburn with higher end hardware like in the m1730....

i put 8.10 back onto my system and grabbed the latest nvidia restricted 180 (i also used this driver with 9.04), and everything works fine, so i doubt it's the nvidia driver....

---

### Post by pbpersson on 2009-04-26
That brings up a comment I wanted to make.

Many people here are hoping that Ubuntu will take over the entire planet and I'm all for that......but they need to really work on the server infrastructure.

Imagine how slow the servers would be if we had ten times more people attempting to get Jaunty.  :o

---

### Post by zero7404 on 2009-04-28
what is the difference between a Default Upgrade and a Smart Upgrade ?

---

### Post by husunzi on 2009-05-17
> **zero7404 said:**
> thanks for the advice....
when i go and make it search for the best server to pull files from, it suggests one, and i click Choose Server....

after i say ok, in the previous window the Download from still says Main server....

perhaps it didn't take after choosing the suggested server ?

I was wondering the same thing. I've also tried many times to choose different servers from "Software Sources" (with & without using "choose best server"), & each time, no matter which server I select, once I click "choose server" & the window closes it still says "main server," as if nothing has changed. And, afterwards, whenever I fail to download updates (& lately every attempt to download updates - including upgrading to 9.04 - fails), the server listed in the "could not download the upgrades" window is the same one I've been using for several months (mirrors.shlug.org), rather than whichever new server I tried to select. 

Can anyone confirm whether our attempts to select new servers are working? If not, is there another way to select a different server?

At the same time, however, having read other people's complaints about 9.04 in this thread, maybe we shouldn't upgrade after all. I for one cannot afford to lose my system right now. (I made the mistake of installing ubuntu on my entire hard drive - only later did I realize ubuntu can't do lots of things I need to do, or does them only with difficulty, & I don't know of any way to install windows on just part of the drive once ubuntu is already installed.) 

Ibravo, did you ever figure out how to recover your system?

Has anyone else encountered the same problem as Ibravo?

Once I have already started installing 9.04 & failed to install it completely, is there anyway to uninstall it (recover 8.10) & then resume making periodic security updates to 8.10? (This is assuming we figure out how to change the download server, or shlug starts working properly again.)

Thanks from a noob ):P

---

