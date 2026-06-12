---
title: "System seems to have completely died"
date: 2008-09-06
forum: General Help
---

### Post by rahaydenuk on 2008-09-06
Hi,

I went out last night with my computer left on as normal, got back and it had totally frozen with the monitors on standby so I couldn't see what was going on. So I rebooted and it seemed OK, checked syslog and it spoke of a general protection fault caused by spamassassin (which runs via cron every three minutes as my email is fetched). I can't put the details here because I am currently unable to access my system.

I left it on and went to bed and this morning it had frozen again. Rebooted and this time it tried to fsck. This was finding tonnes of "deleted inodes with zero dtime" and apparently fixing them, but fsck got to about 4% and then died with a "trap invalid opcode". It told me to run fsck manually from a maintenance shell, which I did and basically the same thing happened.

I now can't get into my system and I have absolutely no idea what the hell is going on. I changed nothing in the last 10 days, I have been very busy at work this week and have literally only been using my home machine to browse the web, check emails etc., certainly no new software has been installed or upgraded. This has never happened before. I really need to use this machine as soon as possible so any help most gratefully appreciated!

Thanks,

Richard.

---

### Post by Bliepo32 on 2008-09-06
Well, it seems that your harddrive has been damaged. You could try to run the live cd, back-up the essential files, reformat the thing, and hope the damage wasn't permanent.

By the way, are you using a beta version of spamassassin? Or any other beta products? Because they might have caused the computer to freeze.

---

### Post by rahaydenuk on 2008-09-06
OK I just tried to boot from a live CD and while it was loading, I've got what appears to be a kernel panic emanating from sysenter_past_esp, sys_read, unionfs_read, vfs_read, shmem_file_read etc. I cannot see the whole thing as it goes off the end of the screen.

Please someone help!

---

### Post by rahaydenuk on 2008-09-06
OK I got it to boot using a different live CD, tried to run e2fsck on the main disk and it found inodes with zero dtime again, but then the whole system just hung with no error messages or anything a short way into the fsck. The mouse has gone, doesn't respond to keystrokes etc. Had to reboot.

At a total loss here!!

---

### Post by rahaydenuk on 2008-09-06
OK, just ran memtest86 and got 80,000+ errors within the space of about 5 minutes, so I presume it's not the hard disk after all, and the corruption was just caused by bad memory.

Just doing trial and error now to find out which of my 4 x 1Gb sticks it is.

Only had them for about a year though, how common is it that memory catastrophically fails like this?

---

### Post by Bliepo32 on 2008-09-06
It depends. Overclocking for example will increase the risk. Unstable power supply's will do so as well. And some brands are quite worthless.

---

### Post by cooke77 on 2008-09-06
Aquick way...to find out which RAM module has died on you....is to pull ALL them out!
Then, just re-install them.
One at a time. (You stated that you 4 Gig of RAM........ONE is all you will need, to boot your computer.)
Reboot, after every RAM has been exchanged. 
And, proven itself..to be workable.
If it doesn't 'Boot'...that's the 'offending RAM'.

---

