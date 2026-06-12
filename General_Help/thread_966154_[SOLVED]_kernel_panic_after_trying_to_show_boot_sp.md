---
title: "[SOLVED] kernel panic after trying to show boot splash screen"
date: 2008-11-01
forum: General Help
---

### Post by gothdaddee on 2008-11-01
Good day to everyone!
i just want to share my experience and how it was solved hoping that it will also help somebody else.

first my problem was that the boot splash screen of my ubuntu isn't showing.  so i searched the forums and found this instructions:

[http://ph.ubuntuforums.com/showpost.php?p=3687398&postcount=20](http://ph.ubuntuforums.com/showpost.php?p=3687398&postcount=20)

when i rebooted, my ubuntu wasn't booting anymore!  it returned the following error:
VFS: Cannot open root device etc,etc,
kernel panic - not syncing: VFS Unable to mount root fs on unknown-block etc, etc.

i had a hunch that this was caused by the last step in the instructions, that is: 

sudo update-initramfs -u -k xxxxxxxxx

so i searched the forums and googled for answers, to no avail.  the answers i find do not solve anything.  i was already preparing my system for a fresh reinstall of ubuntu (and undergo downloading and installing programs all over again!) when i gave googling another shot.  So using the livecd (which was almost ready to fire up the reinstall), i googled and alas! my salvation!  it turns out that that last command was really messed things up for me.  So I'm giving this link to those who might also be helped by this.

[http://www.alterego7.com/2008/02/my-ubuntu-gutsy-wont-boot.html](http://www.alterego7.com/2008/02/my-ubuntu-gutsy-wont-boot.html)

cheers and i hope this will also be helpful to others!

---

