---
title: "input/output error, kernel panic not syncing"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by J1Dopeman on 2006-01-20
I started the upgrade from hoary to breezy last night and ran into some errors.  I'm new to ubuntu and linux, so bear with me.  You can skip a few lines if you just want to know the problem, but here is what I did to cause it incase that helps.  So I began with the apt-get dist-upgrade and it downloaded all of the packages and was setting them up but at some point dpkg started getting a lot of errors uncompressing things and it stopped.  I restarted the system and it loaded the new kernel but couldn't load the gui.  I tried "sudo dpkg -configure -a" because I read that somewhere and it started reconfiguring things again, until it started to error out with something like 'dpkg ext3-fs error read-only filesystem'.  I rebooted and tried it again and it completed and said that it couldn't configure about 13 or so packages.  I saw that one of them was ubuntu-base, which I figure is bad.  I didn't know what to do so I tried to run the dist-upgrade again but it told me I should fix things first, and gave me a command to try, I cannot remember it exactly.  It was something like fpkg -all maybe, not sure.  Anyway, it started configuring and then the read only error started again.  I rebooted and now I have the kernel panic - not syncing!  The two errors immediately before that are:

/sbin/init: 428: cannot create /dev/null: input/output error
/sbin/init: 429: cannot open dev/console: input output error

And that's it.  System is dead.  I am running the 2.6.10-6-386 kernel and tried the recovery one as well.  It says my filesystem type is ext2fs.  I only have the old hoary 5.04 cd, not the 5.10 one.  Should I reinstall and attempt another upgrade, or does anybody know how I might fix this?  Any help is much appreciated, thanks.

---

### Post by J1Dopeman on 2006-01-20
Oh yeah, and I use grub.

---

