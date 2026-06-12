---
title: "Stupid move via upgrade to 9.04 to 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by dodgerwv on 2009-11-01
Can't boot back into 9.10 after upgrading.  Used the Live CD to boot and all of my data is fine.  Yes, I fully admit my idiocy for not backing up prior to the upgrade.  

How can access my documents, pictures, and music from the Live CD to back them up in order to perform a fresh install or should I try to fix the boot loader?  I'm guessing the easiest option for a relative newbie would be to do the fresh install?

---

### Post by dodgerwv on 2009-11-01
Here's the error message that I get trying to boot:

init sreadahead main process (2578) terminated with status1
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2579) terminated with status1
General error mounting filesystems
A maintainance shell will now be started
CONTROL-D will terminate this shell and re-try
root@ dell-desktop:~#

Computer freezes at this point.  It's a Dell Inspiron 530 if that matters.  Thanks in advance for any help!

---

### Post by dodgerwv on 2009-11-01
I've decided to go with a clean install.  Any thoughts on how to use the Live CD to get my files?  I can get to them, but don't have permissions.  What do I need to do?

---

### Post by Fr33d0m on 2009-11-01
If you run gksudo nautilus, you'll have root privileges to copy the files off onto some other media.  You may have to change ownership after you move them back onto the computer, if so use chown, it'll be much faster.

At least you still have your data, I backed mine up but the backup app did a horrid job and I lost lots.

---

### Post by dodgerwv on 2009-11-01
Can't get that to work.  Tried the Knoppix live CD to no avail.  I can find my stuff, just can't change the permissions or mount the files to move most of them.

---

### Post by Fr33d0m on 2009-11-02
I don't think Knoppix is going to help any more than an Ubuntu CD so lets stick with that for clarity.  

gksudo nautilus didn't work how?  Did you get a nautilus window or did it give you some other error?  If I remember correctly you don't give an actual password if you are using the live CD.

Or did you have problems when you tried to move to some other media?

---

### Post by fela on 2009-11-02
You're not an idiot for not backing up your data, actually. The chance that there'd be an upgrade bug that clobbers all your data is teeny. The most likely way of clobbering your data is human error; ie reformatting. As you found out, getting your data back is a piece of cake with a livecd. Just copy it all to an external harddrive or something. Use root if you have to.

---

### Post by NHElnath on 2009-11-02
I seem to have just about the same problem (and the same mistake of not backing up my data).  At this point I'll be thrilled just to get the data back and do a clean install from CD.

---

### Post by dodgerwv on 2009-11-02
My computer is one of the Dell that was already loaded with Ubuntu.  Is this why I'm having trouble with the permissions.  I can get into the files with Nautilus, but I'm denied moving the files due to not having ownership of the file.  How do I handle this through root.  I've used Ubuntu for two-plus years, but haven't had to do a lot through the terminal.

---

### Post by Fr33d0m on 2009-11-03
Just booted to CD to check my memory.

If you look in System-Administration you'll see disk utility which will show all the volumes and will allow you to mount them.  Give them easy to use mount names like disk1 and disk2 and use the small icon on the top left of the window (looks like a disk with a green arrow next to it).  That should mount the drives.

What I forgot besides that is that the permissions are retained as user id's.  You'll have to change to the directory where the files are and then sudo chown -hR root:root *.*

You should then be able to cp, mv, or gksudo nautilus and copy or move them.  You'll likely have to chown them to your new profile name once you get your system rebuilt.

---

### Post by hariks0 on 2009-11-03
> **dodgerwv said:**
> My computer is one of the Dell that was already loaded with Ubuntu.  Is this why I'm having trouble with the permissions.  I can get into the files with Nautilus, but I'm denied moving the files due to not having ownership of the file.  How do I handle this through root.  I've used Ubuntu for two-plus years, but haven't had to do a lot through the terminal.

Type 'sudo nautilus' in a terminal. you will get a root nautilus after you enter your password.

---

