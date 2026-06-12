---
title: "Severe problem with Jaunty upgrade/install and rieserfs"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Wintersdark on 2009-04-28
The setting:

A dell Optiplex gx280 with sata seagate 7200.11 500gb drive, originally functioned as my fileserver running FreeNAS off a USB stick.  The 500gb drive was partitioned as reiserfs.  I was playing movies/tv shows off this with my laptop, but it was inconvenient to connect my laptop directly to my tv.

So, I resized the reiserfs partition to 450gb; and created a 38gb ext3 partition and 4gb linuxswap partition, then installed ubuntu 8.10 to the ext3 partition.

Everything worked great - I shared the 450gb partition over my local network with samba, connected the Ubuntu box to my HDTV, and all was wonderful.

In a fit of nerdy glee, however, I just had to try out Jaunty.  So, using the update manager, I upgraded to 9.04.  Jaunty installed nicely, and rebooted.  Ubuntu startup screen appears, all goes smoothly until "* Reading files needed for boot"; followed by endlessly repeating I/O errors. 

I've swapped OS's on a variety of systems a number of times over the years, so I figured rather than fight with this, I'd just reformat the ext3 partition to ext4 and try a clean install of Jaunty.  Jaunty installed wonderfully, started up perfectly.  Wow!  Ext4 is *fast*.  I updated, did all the setup stuff, mounted my reiserfs partition, got samba running, browsed around on my notebook to ensure it was connected properly, and danced with more nerdy glee...

... Prematurely.  Turns out, when (back on the ubuntu pc) I attempted to play a video file, the video player (gecko, mplayer, and vlc tried) would begin playing just fine, then crash after playing 3-10 seconds.  After crashing, no file operations would work whatsoever in Ubuntu - even those unrelated to the reiserfs partition.  Shutdowns/restarts in this state dropped to console and reported a slew of I/O errors as well.

This behavior persisted over several re-installs of jaunty.  Basically, once any volume of data was transfered from/to the reiserfs partition, Jaunty would become extremely unstable and suffer endless I/O errors (specific errors varied depending on what exactly I was trying to do, but that they were I/O errors relating to /dev/sda was the common thread).

I'm now trying to reinstall Intrepid, so see if this corrects the problem, as this worked fine before.  I'd REALLY like to go back to Jaunty, though, because quite frankly it's wonderful.  

Can anyone offer any advice?  

ps: I do not have a sufficiently large drive to transfer files off the reiserfs partition and reformat it with a newer filesystem, unfortunately, and tools to effectively manipulate reiserfs partitions are few and far between.  I *REALLY* don't want to lose the contents of said partition either.

---

### Post by Wintersdark on 2009-04-28
Well.  That's that.  Seems my harddrive entirely failed during the upgrade.  Maybe just bad luck, I'm not sure, but it was fine earlier in the day and sporting 2 million+ bad blocks now; and probably more.  

~cries~

---

### Post by wpshooter on 2009-04-28
Have you downloaded & ran the Seagate diagnostics software on this hard drive ?

---

### Post by Wintersdark on 2009-04-28
I have a cd with the software, but it's Windows based. My other two pc's are laptops, with no way of connecting the drive, and it is the only fixed drive in the system it's in.  The problems on the drive appear to be worsening with use, too. 

I'm fairly sure Jaunty wasn't the cause, I had some odd behavior prior to the upgrade, particularly on video playback, but didn't make the connection till today. 

I've wanted to rebuild my htpc for some time - it's in a SFF case with veery little room for hardware, so I figure i'll just build a new system, get a couple new drives, and see if I can recover anything then.

---

