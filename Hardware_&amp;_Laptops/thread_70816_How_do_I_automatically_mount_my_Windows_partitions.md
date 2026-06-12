---
title: "How do I automatically mount my Windows partitions?"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by LinuxConvert on 2005-10-01
Hi everyone,

I'm new to Ubuntu and so far its been great but i still have a couple of problems which I haven't been able to solve...

1) My Windows partitions do not automatically mount themselves... I have to manually mount them every time I reboot my PC which is a real pain, as I dual boot with windows, and most of my documents are stored in a FAT32 partition so they can be shared between Windows and Linux... Any ideas how to make it automatic everytime I reboot?

2) Anoher problem I have is that my session doesn't really restore itself every time I reboot (for example, GAIM doesn't automatically come back on when I reboot, etc) Any suggestions?

In case this helps, I always log in as root because I got tired of having restricted access to everything all the time... I know its less safe, but I feel the convenience makes up for that...

Sorry if my questions seem really newbie-like, but I'm rather new to Linux and I'd appreciate any help I can get... Thanks in advance!

LC

---

### Post by juantxorena on 2005-10-01
1) You must change the /etc/fstab archive, which contains info about differents partitions and mounting points.
You must add some lines like
```
/dev/hda1       /media/C:     ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/D:    ntfs    nls=utf8,umask=0222 0       0

```
Obviously, you must change them to your needs.

2) I don't know :p

---

### Post by aysiu on 2005-10-01
[QUOTE=LinuxConvert]
2) Anoher problem I have is that my session doesn't really restore itself every time I reboot (for example, GAIM doesn't automatically come back on when I reboot, etc) Any suggestions?[/quote] System > Preferences > Sessions. Isn't there some option about saving sessions every time?

> 
In case this helps, I always log in as root because I got tired of having restricted access to everything all the time... I know its less safe, but I feel the convenience makes up for that... Just curious, what's this "everything all the time" that you need access to? The only times I need root access are when I'm installing software or changing a system configuration file--not that often.

Have you considered just creating a "browse as root" launcher? Just right-click on the panel, select "Add to Panel," "Custom Application Launcher" and put for the command *gksudo nautilus*.

---

### Post by LinuxConvert on 2005-10-01
Hi guys,

Thanks for the quick replies. I'm amazed at how fast that was... lol!

1) I've tried changing the fstab file, hope it works... Thanks for that...

2) Thanks, found it... Don't know how I missed it :P

Well, I only JUST installed Ubuntu and its been taking some time to get everything to work right, so thats why I need root access for so many things... lol

Another question, Ubuntu detects my Windows network computers, but I can't seem to get it to detect any shared folders except Shared Documents... Anyone know how to work around that, besides typing in the exact directory I want in Nautilus?

Thanks again

LC

---

### Post by aysiu on 2005-10-01
[QUOTE=LinuxConvert]
Well, I only JUST installed Ubuntu and its been taking some time to get everything to work right, so thats why I need root access for so many things... lol[/quote] Use the custom launcher I described. First of all, once you get everything set up, you will rarely need root privileges, so it's safer to generally use user. Secondly, it's far more convenient to gain root privileges temporarily by clicking a launcher and typing in your password than to log out, log back in as root, log out as root, then log back in as user.

> 
Another question, Ubuntu detects my Windows network computers, but I can't seem to get it to detect any shared folders except Shared Documents... Anyone know how to work around that, besides typing in the exact directory I want in Nautilus? Sounds as if it might be something on the Windows end of things in terms of what they're willing to share. If not, can't you bookmark a folder you've manually typed in?

---

### Post by LinuxConvert on 2005-10-01
[QUOTE=aysiu]Use the custom launcher I described. First of all, once you get everything set up, you will rarely need root privileges, so it's safer to generally use user. Secondly, it's far more convenient to gain root privileges temporarily by clicking a launcher and typing in your password than to log out, log back in as root, log out as root, then log back in as user.
Sounds as if it might be something on the Windows end of things in terms of what they're willing to share. If not, can't you bookmark a folder you've manually typed in?[/QUOTE]

I think I will do that, thanks for the suggestion... As for the sharing thing, the folder is already shared, but I can't seem to see it using Nautilus, unless I type in the destination... I guess bookmarking it is a good idea, I'll probably do that... Thanks again!

LC

---

