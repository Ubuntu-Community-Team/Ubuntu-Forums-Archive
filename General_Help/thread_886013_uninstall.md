---
title: "uninstall"
date: 2008-08-10
forum: General Help
---

### Post by jorj82 on 2008-08-10
How do I uninstall Ubuntu?  The pc I put it on has no internet connection, so I can't download the packages I need to play my games.

---

### Post by atoponce on 2008-08-10
Are you looking to install something instead?  Windows or some other version of GNU/Linux?  Does the computer dual-boot?  What are we looking at here?

---

### Post by jorj82 on 2008-08-10
I have what I need to install something else, I just need to wipe the hard drive.  I tried to dual-boot when I installed Ubuntu but my drive wouldn't take it for some reason, so now I guess I have to reformat or something but I can't figure out how to do it.

---

### Post by Zimmer on 2008-08-10
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

or

[http://ubuntuforums.org/showthread.php?t=113630&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=113630&highlight=dual+boot)

May provide you with the answer...

---

### Post by jorj82 on 2008-08-10
OK, now I'm confused again.  I don't think I have the MBR in the Windows partition because I couldn't partition my drive, the whole drive is the only partition and that's where Ubuntu is.  I guess I'm a dumb troll for not reading enough before switching.

---

### Post by Zimmer on 2008-08-10
> **jorj82 said:**
> I have what I need to install something else, I just need to wipe the hard drive.  I tried to dual-boot when I installed Ubuntu but my drive wouldn't take it for some reason, so now I guess I have to reformat or something but I can't figure out how to do it.

So, give us a clue, what are you going to install?
If it is XP then
 Windows XP 'Recovery Console'
Just put in your Windows XP install CD, and boot into the Windows XP Recovery Console and use the so-called 'FIXMBR' command. Follow prompts to format and so on.. should work ok.

---

### Post by jorj82 on 2008-08-10
> **Zimmer said:**
> So, give us a clue, what are you going to install?


Windows 2000 SP4.  Its what came with the pc.

---

### Post by atoponce on 2008-08-11
I am not clear if Windows is installed on the machine, or not.  If so, I would follow Zimmer's suggestion.  If not, I would pull up a terminal in Ubuntu, and type the following with the W2K disk in the drive:

```
dd if=/dev/zero of=/dev/sda bs=446 count=1; reboot
```

---

