---
title: "Samba does not start after upgrade to 8.04"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by jimq on 2008-12-11
I had samba running for quite some time under 7.04.  I recently upgraded my 7.04 to 7.1 and immediately to 8.04 LTS.  I cannot get samba to start.  I have tried to reload samba, samba-common, smbfs.  I deleted and purged them from the system and reloaded them from scratch.

Whenever I execute "/etc/init.d/samba start" it starts the processes (they show up in ps -fe) but the /etc/init.d/samba takes forever to return and when it does finally return, samba doesn't work.  I found a similar post to the forum, but no solution was posted. ([http://ubuntuforums.org/showthread.php?t=925827):confused:](http://ubuntuforums.org/showthread.php?t=925827):confused:)

---

### Post by lykwydchykyn on 2008-12-11
Try the following:

- run "testparm" and see if there are errors in your config

- check /var/log/syslog for errors related to samba

- check in /var/log/samba/ for errors

---

### Post by jimq on 2008-12-11
[COLOR="Blue"]testparm[/COLOR] is clean

[COLOR="Blue"]log.nmbd shows :[/COLOR]
2008/12/11 10:56:52, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/12/11 11:02:34, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server FILESERVER is now a local master browser for workgroup BROWNBOOTS on subnet 192.168.0.41
  
  *****

  Copyright Andrew Tridgell and the Samba Team 1992-2008
[COLOR="Blue"]
log.smbd shows:[/COLOR]
008/12/11 11:02:00, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008



[COLOR="Blue"]syslog[/COLOR] doesn't report anything.

---

### Post by lykwydchykyn on 2008-12-11
If you issue /etc/init.d/samba stop, are there still smbd or nmbd processes active?

---

### Post by jimq on 2008-12-11
In order to start samba  and keep working in the same window, I submit /etc/init.d/samba start in the background.

If that command (samba start) is still running (which it does for about 5-10 minutes) when I run samba stop, it does NOT kill the smbd and nmbd processes.  

If the samba start command completed, then samba start kills smbd and nmbd processes.

---

### Post by lykwydchykyn on 2008-12-11
Try killing all your samba processes, then run this:
```

smbd --debug-level=3

```

See what kind of output that gives you.

---

### Post by jimq on 2008-12-12
syslog and messages displayed nothing.  there was no output from the command.

---

### Post by lykwydchykyn on 2008-12-12
Well, you can try progressively higher bug levels until you get some output.  I really don't know what else to suggest.

---

### Post by jimq on 2008-12-12
Close this one for good!!

I removed samba completely from the system.  I upgraded from 8.04 to 8.10 and re-installed samba:

apt-get install samba-common
apt-get install samba

It works!  Life is good again!

Thanks for your help!!!!  I do appreciate that you took the time.

Thank you,

---

