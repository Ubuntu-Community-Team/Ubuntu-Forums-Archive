---
title: "[SOLVED] Ubuntu Fails To Boot"
date: 2008-09-12
forum: General Help
---

### Post by Virtua-Touch on 2008-09-12
This morning, I tried to boot into Ubuntu. I've installed Ubuntu correctly using Wubi, and this is what I get when booting up:
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```

It's almost like CMD or Terminal but at the boot-up screen. I don't know what happened. I used Ubuntu last night fine, and the only thing I did was use firefox.

---

### Post by broken tibula on 2008-09-12
I don't know what's wrong, but I'm having the same issue.  Just posted about it in another thread--I sort of broke my computer, have been trying to fix it all day, and then I rebooted and was like, "Are you kidding me?  What did I do *now?*.  

At least I know I'm not alone!

(BusyBox is a shell, which is kind of like the nuts-and-bolts part of Linux.  And the fact that I know this is utterly useless, because I don't know how to do anything in it.)

Is this happening to anyone else?  Or better yet, does someone out there know why this is happening and how we can fix it?

---

### Post by Virtua-Touch on 2008-09-12
I really do not want to install again. (even though it takes me 5 minutes to install; me = fast computer :})

---

### Post by broken tibula on 2008-09-12
I don't mind re-installing (although I think that might be what I end up doing--I'm not patient enough to wait for some benevolent, intelligent person to post to solution), but I don't want to re-tweak all my features.  I had it down the way I liked it.  

Anyway.  This thread is my current source of math-homework procrastination, and I should probably get off of here and get on my homework.  Please help us!

---

### Post by Virtua-Touch on 2008-09-12
I'm gonna try a few things. I'll keep you posted if I get it to work. If not, I'll just reinstall. It's only 5 minutes of my time.

[EDIT] Right now, I am in Ubuntu. For some reason, I got an error stating something about the partition not being correct, and I had to fix it with Windows, but it booted anyway.

---

### Post by broken tibula on 2008-09-12
Wait, you got a GUI up on Ubuntu?  How'd you do that?

---

### Post by Virtua-Touch on 2008-09-12
No idea. I just booted into it and it never came up with that crap. Although, I did get a Windows Partition table 83 error, but I guess that's normal. I did, however, try running this command in CMD in C:\ and C:\ubuntu. I got an error both times, but it might've fixed it. 
```
chkdsk /r
```

Also, make sure that you've shut down Windows properly. If you haven't, try rebooting regularly. (Start >> Shutdown)

---

### Post by broken tibula on 2008-09-12
Thanks!  I got on, but it's an absolute nightmare from what was wrong earlier.  I'm just going to reinstall.

---

### Post by Virtua-Touch on 2008-09-12
What was wrong with it?

---

### Post by duface on 2008-09-14
I am getting the same problem, I end up with (initramfs)

I've tried reinstalling several times. Tried chkdsk /r. I don't know if I'm doing the grub4dos correctly, what I put in isn't there when I reboot.

I tried the workarounds, I got different numbers when it quits but the message is the same JFS: nTxBlock=8088, nTxBlock=64707

Does the JFS mean anything?

---

### Post by Virtua-Touch on 2008-09-16
As of my knowledge, I have no idea why this happens. I've gotten mine to work.

---

### Post by zotrules on 2008-09-28
wow... only people who have problems. no solutions whatsoever, anywhere.
ubuntu forums appear to be frequented only by people who don't know, who are stuck somewhere, who are having problems... no experts whatsoever?!?
where's the people who know????

---

### Post by zotrules on 2008-09-28
[solved]??? my ***!

---

### Post by sandbird on 2008-09-28
> **duface said:**
> I am getting the same problem, I end up with (initramfs)

I've tried reinstalling several times. Tried chkdsk /r. I don't know if I'm doing the grub4dos correctly, what I put in isn't there when I reboot.

I tried the workarounds, I got different numbers when it quits but the message is the same JFS: nTxBlock=8088, nTxBlock=64707

Does the JFS mean anything?

Yes! Linux doesn't support SATA disks like Windows. That's our problem.

---

### Post by DFizz on 2008-09-28
I booted to windows and it ran the checkdisk. Once that finished I rebooted and started up ubuntu just fine.

---

### Post by ago on 2008-09-29
There are several reasons why Ubuntu may fail to boot merging them all in one thread is pretty much useless. 

The common issues are:

1. Ntfs is corrupted, this usually happens because of a hard reboot after linux-side installation and can normally be recovered running chkdsk /r. In some cases chkdsk /r might remove some files, so you have to make sure /ubuntu/disks/root.disk is available. 

2. Unsupported setup. If you have a (software) raid or encrypted disk you cannot use Wubi. If you are using the wrong ISO (alternate or DVD) you cannot run Wubi. This result in the user being unable to run the linux-side installation.

3. Other unsupported hardware. Some hardware is not well compatible. But unlike the above this can usually be resolved using special kernel parameters such as noacpi. The specific parameter to use depends on the hardware you have.

4. Unsupported video. It's not really a boot issue, people though sometimes confuse it with the above since they end up with a black screen or command line interface. This is resolved by booting in rescue mode or safe graphic mode and installing the appropriate drivers or changing the configuration.


For anything else you need to boot in verbose mode (press esc at boot) and post the detailed error log (/casper.log at first boot).

---

