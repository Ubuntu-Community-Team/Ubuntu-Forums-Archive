---
title: "Which Linux folders are the least/most volatile? For an almost-read-only system"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by MikeClub on 2008-12-15
I'm looking to create a Xubuntu-based HTPC which boots from a USB drive. I'll actually have two internal USB drives that I want to use for the OS: one which contains mostly static data and one which contains more volatile data (i.e. will have more frequent writes). This is because flash memory degrades upon each write operation. I'm using SLC flash memory, so it should be better, but I still want to be more robust here. I see this splitting as having two benefits: 1) I'll only have to replace one drive upon failure and 2) My more important system files should be more insulated from such a failure.

So, my basic question is this: Which directories should I mount on the second, more expendable USB drive? I don't know enough about Linux, but I can guess that /tmp, /var, and /usr are decent candidates.

Please chime in if you have other ideas; thanks.

---

### Post by kerry_s on 2008-12-15
how much memory is it going to have?

you can mount /tmp in ram(tmpfs) which is what i do. you can also do /var/log but you'll get errors at the start of every boot for the missing files/folders, i recommend just disabling as many logs as you can in /etc/syslog.conf or removing syslog from the install, which is what i did.

your ~(home) is actually the most active part of the system, so if you must, put root(/) on 1 and home(~) on the other.

```
none            /tmp            tmpfs   noatime,nodiratime,defaults,size=128M  0      0
```

my /var/log looks like this:

---

### Post by MikeClub on 2008-12-15
I forgot to mention that; ~ is definitely going on the second one. And I'm doing noatime on everything.

The system has 4GB of RAM.

The tmpfs is a good idea; I forgot you could so easily do that.

So do you recommend just /var/log in a more volatile space (either RAM or the second stick) and not just /var altogether?

I would like the idea of removing all logs, but I don't think I can do that. I'm also going to use this as a download bot, and I'll want to connect to it via SSH, FTP, and even with SMB shares. So I'm going to want a half-decent intrusion detection program like fail2ban, which monitors log files. And so I'll have to look into ways to streamline my logging. I'll look at that script and hunt down some guides on how to do that. Thanks.

Still, any other opinions are appreciated.

---

### Post by kerry_s on 2008-12-16
> So do you recommend just /var/log in a more volatile space (either RAM or the second stick) and not just /var altogether?


i'm not sure i understand.
you have 2 sticks, 1 will have /home(~), the other will have root(/), so /var will be there, it doesn't make since to split that up into different partions, cause you want it wearing equally for the whole stick, not sections of the stick.
like i said you can put that in ram if you want, but it will have to be created again on each boot, so nothing in there will be saved, it's lost and created on each boot.
if you want you can go ahead and try it, to see what i mean. just delete the line to go back to how it was before.

```
none            /var/log            tmpfs   noatime,nodiratime,defaults,size=10M  0      0
``` 

in your case if you want to selectively keep some logs it can be done in /etc/syslog.conf just comment out the 1's you don't want, a lot of the log files are the same if you look into them they'll have the same info as other log files. 

also you should think about going custom instead of xubuntu. with a custom install you just install what you need/want, also desktops run a lot behind them, a window manager is a better option and gives you more control over whats running.

---

### Post by sdennie on 2008-12-16
You may want to have a look at this thread if you are worried about excessive writes: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998") and this one might be useful too: [http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive).

I actually mount a number of things in my home directory as tmpfs and write the changes back to disk every 10 minutes with cron (I do it for power savings though).  That's an extreme method but, it does prevent poorly behaved apps from writing to your disk constantly (I'm looking at you Firefox).

---

### Post by kerry_s on 2008-12-16
> **vor said:**
> You may want to have a look at this thread if you are worried about excessive writes: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998") and this one might be useful too: [http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive).

I actually mount a number of things in my home directory as tmpfs and write the changes back to disk every 10 minutes with cron (I do it for power savings though).  That's an extreme method but, it does prevent poorly behaved apps from writing to your disk constantly (I'm looking at you Firefox).

you should have used ext2, not good to use a journaling file system when your trying to save writes.
have you moved your firefox cache to /tmp?

---

### Post by sdennie on 2008-12-16
> **kerry_s said:**
> you should have used ext2, not good to use a journaling file system when your trying to save writes.
have you moved your firefox cache to /tmp?

I thought about doing that but, it's easy enough to modify the journal commit time.  Looking back and knowing how stable the machine is, ext2 probably would have been a better choice, yes.  I have a normal hard drive and so setting the journal commit time and dirty page writeback time to the same time period works fairly well in my case (I'm just trying to keep the disks in standby).

As for the firefox issue, I actually mount all of ~/.mozilla as tmpfs (with disk storage coming back to encfs via cron every 10 minutes) because every time you navigate to a new page in FF3 (at least in Hardy and presumably in Intrepid) it does an fsync and forcefully brings the disks out of standby.  Every single time you open a page.  The bug report for that annoying behavior can be found here: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009).  I just verified it earlier today and it still exists in Hardy.

---

### Post by MikeClub on 2008-12-16
> **kerry_s said:**
> i'm not sure i understand.
you have 2 sticks, 1 will have /home(~), the other will have root(/), so /var will be there, it doesn't make since to split that up into different partions, cause you want it wearing equally for the whole stick, not sections of the stick.

Well, I expect the sticks have wear leveling, and I don't presume to know exactly how that works, so I'll just treat the sticks as one unit and not worry about the different sections of them.

vor, those are some great suggestions - thanks. I can even use them on the large hard drives I'm going to have in there.

I think I have it pretty much figured out. I'm going to..

 * Mount tmp and var/tmp in RAM
 * Mount ~ on the second stick
 * Mount /usr/local on the second stick
 * Mount /var/log in RAM, as long as it only gives me warnings and not true errors on boot (i.e. it doesn't prevent me from booting). I'm pretty sure I don't care if the logs don't persist between boots. Else I'll put it on the second stick.
 * Mount everything with noatime
 * Set dirty page writeback to some number of minutes for my HDDs
 * Limit the number of logs which are kept

I'm also going to use XFS for my hard drive partitions that serve up large videos. I may install MythTV sometime in the distant future, and so I looked at its install guides, and XFS is recommended. It seems like the advice works for any setup which handles large files like a media center. I'll see about setting the journal commit time to the same period as dirty page writeback.

And I'll just stick with Xubuntu, also trying to limit the number of services it runs, because 1) I don't want to spend a lot of time learning about the kernel to get this project going and 2) I want to use Screenlets; I don't know how that will work with a more minimalist environment, and 3) I think I'll have more than enough CPU cycles & RAM to throw at this thing, especially after the above optimizations.

You guys have been a great help. Thanks! Let me know if there are any problems with my proposal or if anyone can think of anything else.

---

### Post by sdennie on 2008-12-16
That seems reasonable to me.  It's at least a good start that can be tweaked as you see what actual disk usage looks like after using the machine for a while.

---

