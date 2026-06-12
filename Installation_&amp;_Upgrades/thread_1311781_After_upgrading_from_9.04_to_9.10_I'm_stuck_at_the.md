---
title: "After upgrading from 9.04 to 9.10 I'm stuck at the kboot screen"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by webster922 on 2009-11-02
On my ps3, I had 9.04 installed. I burned the alternate install disc (ppc architecture) to upgrade to 9.10. The disc was recognized and I clicked 'Run Upgrade'. After maybe two hours the upgrade process was over but now I'm stuck at the kboot screen and haven't used 9.10 once. The kboot screen says this:
[INDENT]mount: mounting none on /dev/pts failed
/init: /init: 923: dropbear: not found
Ubuntu PS3 KBoot Loader

No default root fs was found, or one was found and it didn't contain a message= config file.

If no rootfs was found, you can enter the shell here with 'sh'. Exiting will return you to this prompt. In the shell you can mount your rootfs as /mnt/root

[/INDENT]I enter shell and then type help but none of the given commands seem useful. And I have tried to reinstall 9.10 on the ps3's 10 gb partition with no luck. Hopefully someone knows what this means and what to do. Any help is appreciated.

---

### Post by joepcremers on 2009-11-03
I think this has to do with the partition format. See [http://joepcremers.nl/wordpress/?p=1595]("http://joepcremers.nl/wordpress/?p=1595") for a tutorial..

---

### Post by Jayfox on 2009-11-21
I can't get it to change from ext4 to ext3, it keeps saying that i have no root defined

---

### Post by webster922 on 2009-11-23
Well I finally gave up on the Ubuntu partition and wanted that partition gone. But the PS3 wouldn't format over it so I took it out and formatted it on my computer. Bad idea. Now my PS3 can't load the system software and it won't restore the software as it doesn't recognize the disk. So I would recommend to not take your hard drive out of your PS3.

---

### Post by a7j_72 on 2009-11-23
"turn on ps3 press x to restore on 0 % quikly pull out hdd. then wait may take up to an hour a message will come up to formate hdd. put hdd back in and press yes to format this process worked with in secounds for me but can take longer. it does work but you will lose all saved stuff but online stats will still be on the system. good luck hope it works for u to"

I dont own a ps3 or have ever fixed 1... I simply read this on another ps3 forum.
good luck.
I hope this might be of some help.

---

### Post by webster922 on 2009-12-01
Well that didn't work considering the fact that I couldn't even get to the system's gui, but I sent it in for service. Thanks for the replies.

---

