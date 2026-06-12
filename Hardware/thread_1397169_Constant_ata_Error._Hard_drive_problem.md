---
title: "Constant ata Error. Hard drive problem?"
date: 2010-02-02
forum: Hardware
---

### Post by Zeniff on 2010-02-02
Hi~

I've been getting this error continuously for as long as I can tell. I may have had it before upgrading to Karmic, but not sure.

It happens every few seconds.

The last one from dmesg (they are always exactly the same as far as I can tell):
```

[11752.144071] ata3.00: qc timeout (cmd 0xa0)
[11752.144112] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[11752.144122] ata3.00: irq_stat 0x40000001
[11752.144147] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[11752.144151]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[11752.144154]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[11752.144163] ata3.00: status: { DRDY ERR }
[11752.144178] ata3: hard resetting link
[11752.628060] ata3: softreset failed (device not ready)
[11752.628073] ata3: applying SB600 PMP SRST workaround and retrying
[11752.792065] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[11752.806957] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[11752.822474] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[11752.822487] ata3.00: configured for PIO0
[11752.824540] ata3: EH complete

```
I think I recall it used to have an ata1 error also, but I'm not sure.

I think it's a HDD error, but I really don't know. I don't know what ata means, either.

Palimpsest Disk Utility says the disk is healthy. Also, I just completed a SMART Extended self-test from there with no errors.

This shows up in every tty and makes it nearly impossible to use a tty because it outputs the error every few seconds.

Only have one hard drive, which came with this Acer Aspire 5515 laptop (got in summer, 2009, as refurbished). Using Ubuntu 9.10 with dual-boot to Vista.

Besides the continual error messages, I haven't noticed anything affected by this. But, then again, I've had it maybe since first using Linux, so it could be causing things that I don't know are related, I guess.

I hope someone can help... Thank you very much and have a great day! ^_^

---

### Post by sh4rkbyt3 on 2010-02-09
Not sure if this applies to your issue or not but I recently had an ata 4: SRST failed error.

I'm a complete nube to Ubuntu so please bare with me.

I downloaded BackTrack 4 from a torrent and then burned the .iso image to disk. Upon starting up BT4 from the disk I then chose to run "Live CD" mode from the selection menu. Everything seemed to start ok as far as I could tell but then I had the bt#root command or something like that appear. I couldn't figure out how to get out of it so I simply did a hard shutdown (power button) BIG MISTAKE!

When I tried to restart my computer I continued to only get an "ata 4: SRST failed" error message. I then tried to use several disk wipe utilities from a few of my tool CD's which wouldn't touch the drive.
This morning I got online with my netbook and read a few ideas, one worked!

I simply restarted the computer with the same (most likely corrupt) Backtrack 4 burned disc, waited for the prompt and simply typed in "reboot". I couldn't remove the CD so I let it shutdown and restart but before it could read the BT4 disc, I ejected it.

Now I'm back to my original Windows 7 RC1 OS. :)

I don't know if you can apply this to Ubuntu or not but I figure BT4 is Ubuntu based so it might work?

---

### Post by benbloom on 2010-02-09
I have the EXACT same problem on my Acer 5515! must be a hardware specific  bug.
[here's the link to the bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/519471") I submitted when I got a more severe crash which I suspect may be related

---

