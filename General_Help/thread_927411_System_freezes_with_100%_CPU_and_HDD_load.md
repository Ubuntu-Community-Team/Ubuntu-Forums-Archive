---
title: "System freezes with 100% CPU and HDD load"
date: 2008-09-22
forum: General Help
---

### Post by alecz20 on 2008-09-22
This happens occasionally on my laptop with Hardy, but every time on the Desktop with Ubuntustudio 8.04.1

Steps:
2) Let computer run (playing music, or downloading via torrents) for several hours
3) Come back and notice the system not responding, the HDD light steady ON, and the last frame of the CPU load graph at 100% (kernel load, not user)

System description:
HP Pavilion a1740
Dlink AirPLus G520 (Atheros, AR5212/AR5213)
Nvidia 7300 GT (with latest drivers from nvidia - not the ones supplied with the distro)
Echoaudio GINA 3G audio card
Realtime kernel 2.6.24-19

The last message to appear (several times) in syslog is:
```

[32630, 801539] wifi0: rx FIFO overrun; resetting

```

Line 57 in the syslog.
Line 5070 in messages.
I have also attached the logfiles

**[SIZE="5"]UPDATE:[/SIZE]**

On Vista is was giving blue screens and resets. From the Live CD there were no problems, we tried HDD on different machine, same issue.

Concluded it was the HDD. New HDD works fine for now. We still have to figure out what to do with old 320GB hdd.

On the Laptop its a different issue: memory leak on aMule due to internet connection drop.

---

### Post by willca on 2008-09-23
I had this similar but not totally the same on a laptop. Same thing looked like about wireless being culprit. Apparently, it was the HD.

So what I did was to boot off livecd and do fsck on HD.

---

### Post by alecz20 on 2008-09-25
The system did a routine HDD check. The problem still happens, but the HDD light was not on.

I think the system freezes only when idle for a few minutes. I have disabled desktop effects. 

Looking through the log again, I found other messages:

in /var/log/messages:
```

pulseaudio[6242]: alsa-util.c: Cannot find fallback mixer control "Mic".

```
and some "-MARK-" messages

I will try with jack not running, and see what happens.

Generally, if I let the computer running alone, I find it frozen, so I can't leave it to download anything :(

EDIT:
Same symptoms while watching a movie and having JACK closed.

I also checked the logs, and there isn't anything but the "-MARK-" message.

I have ran out of inspiration... **how do I get to the bottom of the problem?**

---

### Post by alecz20 on 2008-09-26
I have also attached dmesg output. Maybe someone can figure it out, I don't know what to look for.

P.S.: I tried editing the last post with the attachment, but it didn't work, so I had to make a new one.

---

### Post by alecz20 on 2008-09-29
I managed to get a glimpse at the System Monitor Window when the system froze.

Audacious was running with JACK, but no music was playing, the usage was 29%

Pulseaudio was running at 39% (for no apparent reason). I think the freeze is related to pulse-audio.

I still hope someone can give more pointers to troubleshoot these freezes!

---

