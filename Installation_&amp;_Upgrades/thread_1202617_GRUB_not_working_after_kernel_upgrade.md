---
title: "GRUB not working after kernel upgrade"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-07-02
I just downloaded the update for the 2.26.24-24 kernel.  A window appeared asking if I wanted to keep my installed menu.lst or use the package maintainer's version.  I chose package maintainer's version.  I rebooted and I always get the grub prompt.

I followed the directions for restoring grub and here are the commands I issue and their outputs:
```

grub> find /boot/grub/stage1
  (hd0,1)

grub> root (hd0,1)

grub> setup (hd0)
  Checking if "/boot/grub/stage1" exists... yes
  Checking if "/boot/grub/stage2" exists... yes
  Checking if "/boot/grub/e2fs_stage1_5" exists... yes
  Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded. succeeded
  Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub>

```

Per instructions I type "quit" but I get an: Error 27: Unrecognized command.  I type reboot and after a reboot I am brought to the same grub prompt.

I tried using:
```

setup (hd0,1)

```
Which I know I don't want b/c I want to use my MBR but I tried it anyway and I had the same problem.  Also, the output was:
```

grub> setup (hd0)
  Checking if "/boot/grub/stage1" exists... yes
  Checking if "/boot/grub/stage2" exists... yes
  Checking if "/boot/grub/e2fs_stage1_5" exists... yes
  Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
  Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
  Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub>

```

I would like to avoid using the LiveCD method as this problem should be resolvable right from the command prompt.  I appreciate your help.

---

### Post by merlinus on 2009-07-02
What partition is ubuntu on?  Do you have more than one hdd?

---

### Post by MaindotC on 2009-07-02
Just 1 hdd.  I don't know how to find parition information without a live cd or booting into the o/s.  I can tell you this:  I have / and /home on separate partitions per the psychocats recommendation.  I read about the condition w/ restoring grub if you have /boot on a separate partition, but I just have the whole / filesystem on it's own partition.

---

### Post by merlinus on 2009-07-02
```
sudo fdisk -l
df -h

```

---

### Post by MaindotC on 2009-07-02
Can't run those commands in grub and can't boot into recovery mode.  Alright, look I'll boot into the livecd but this is absolutely unnacceptable.  Hold on.

---

### Post by merlinus on 2009-07-02
Absolutely unacceptable?  You did choose to override your own menu.lst with someone else's, eh?

Use gparted on the live cd to view your partitions, as df -h will only work if you are running ubuntu, not booting from the cd.

You can also take and post a screenshot.

---

### Post by MaindotC on 2009-07-02
I rebooted w/ the LiveCD and clicked the "Try Ubuntu without making any changes to your machine" and the Ubuntu logo w/ the status bar flowing back and forth came up, but it wouldn't get any further than that.  After about 5 mins I rebooted, and now GRUB is recognized.  I think this was a hardware, bios, or other electrical error because I believe I was CLEARLY entering the grub commands properly.  Thanks for your help in any event.

---

### Post by MaindotC on 2009-07-02
I chose to overwrite the menu.lst because the last time I chose "keep the installed menu.lst" and my grub was bricked.  That was on my "let's upgrade to Jaunty" journey that ended with an unsupported video card.  Hey listen - I have two machines here.  The 64-bit hardy was the one that I was prompted to install a new menu.lst whereas the 32-bit machine WASN'T so explain that mr. "You did choose to override your own menu.lst with someone else's, eh?" from a kernel upgrade that came from Canonical!

The fact that I was entering the commands properly and I couldn't resolve the issue from the command prompt is unacceptable.  As you can see, what I was doing was correct, and it was (most likely) my hardware that was screwing me over.

---

### Post by merlinus on 2009-07-02
Glad it is working, and if ubuntu is on sda2, then you did enter the grub commands correctly.

You expect consistency from computers?  See it as an adventure rather than a hassle.

:lolflag:

---

