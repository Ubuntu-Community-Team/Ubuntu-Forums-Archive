---
title: "New install to an Nvidia Ion, Random Crashing"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by spiffydudex on 2009-08-13
I have a new installation of Ubuntu 9.04 desktop edition, with the intention of making a streaming media server for my home theater. Immediately I ran into some issues. During the installation if I let it sit till it ran the screen saver, the computer would restart. So I thought well, that could easily be the video drivers, so I sat there juggling the mouse every 5 minutes. After install completed, I installed the Nvidia Ion drivers from the Nvidia website. Rebooted, still had issues with the screen saver rebooting the computer, so I disabled it. Every so often I still get a random reboot. Not entirely sure what could be the cause. 

I checked the syslog and there wasn't any real error posted. This is just one incident of many.
```

Aug 13 11:53:06 xbmc kernel: [   91.811019] wlan0: disassociating by local choice (reason=3)
Aug 13 11:53:11 xbmc kernel: [   96.816782] wlan0: deauthenticated
Aug 13 12:00:01 xbmc /USR/SBIN/CRON[3679]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 13 12:00:01 xbmc /USR/SBIN/CRON[3680]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 13 12:00:53 xbmc syslogd 1.5.0#5ubuntu3: restart.
Aug 13 12:00:53 xbmc kernel: Inspecting /boot/System.map-2.6.28-14-generic

```As you can see The only thing that went on before the crash was my wireless card disconnecting. Pretty normal. I ran a memtest for an hour or so(enough for 1 full pass) and it came back clean. Is there anything I could be missing or anything I can try to root out the problem? 

I work on Ubuntu servers, this area of Ubuntu is not my forte, Help Please.

Thanks
Andy

Hardware: 
Zotac IONITX D-E Atom 330 Dual core
2 Gig OCZ memory
160 Gig HDD

---

