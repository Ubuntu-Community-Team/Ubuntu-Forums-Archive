---
title: "Effect of force mount on hard disk"
date: 2008-09-19
forum: General Help
---

### Post by chitresh4u on 2008-09-19
In case of an unclean shutdown (specially with NTFS & dual boot), I get a message saying :

[I]$LogFile indicates unclean shutdown (0, 0)
....
Mount is denied because NTFS is marked to be in use.
...
.... you can use the 'force' option for your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdf1 /mnt/external/ -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdf1 /mnt/external/ ntfs-3g defaults,force 0 0[/I]


I have encountered this a lot of time and used force mount to use the drive. But each time the statement "use the 'force' option for your own responsibility" make me feel bad about what I am doing.

What are the effects of force mount on the hard disk. As far as I know it resets the LogFile. Does it have any other actions? Does it harm the hard-disk physically(in terms of reducing the lifespan of HDD or creating bad sectors etc)?

I am not sure if there is any thread regarding this. I tried to find but ended without any luck.

---

### Post by bodhi.zazen on 2008-09-19
From the man page :

> **force**
Force mount even if errors occurred. Use this option only if you know what are you doing and don’t cry about data loss.you need to "force" the mount because the file system is corrupt. The problem is there are no open source tools to fix it, so you have to use windows.

Although you may be able to force the mount without any problem, the man page is telling you data loss may occur.

---

### Post by -Zeus- on 2008-09-19
the probable issue is that windows was not shut down cleanly.

---

### Post by stickmangumby on 2008-09-19
Hi chitresh4u,

Forcing a mount will reset the logfile completely. It won't physically harm the drive or reduce its lifetime or anything. However, if you were in the middle of writing to the drive, clearing the logfile may cause dataloss (its possible that incomplete writes could be completed based on information in the logfile, but I'm not sure - don't know enough about NTFS).

If you boot into Windows after an unclean shutdown, let it do its thing, then reboot into Ubuntu, does this message not appear? I'd imagine Windows runs chkdisk or something like that to clean up after the unclean shutdown.

Also, it's pretty important to shut down properly. Are you having problems doing this? Is your computer hanging at shutdown or anything?

edit - beaten to the punch! Damn slow typing...

---

### Post by chitresh4u on 2008-09-19
> **stickmangumby said:**
> 
Also, it's pretty important to shut down properly. Are you having problems doing this? Is your computer hanging at shutdown or anything?


Yeah I do understand that proper shutdown is important. Actually I have a malfunctioning UPS, which sometimes do not provide enough backup for proper shutdown. I will get th UPS fixed as soon as possible.

Thanks

---

