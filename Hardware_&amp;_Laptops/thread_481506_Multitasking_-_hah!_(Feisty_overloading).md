---
title: "Multitasking - hah! (Feisty overloading)"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by pickarooney on 2007-06-22
For the past three days I've been experiencing odd and frustrating behaviour from my system when it comes to running pretty much any two programs concurrently.
First, I notice the fan getting louder, rising to vacuum-cleaner level, then (if I've time) I can see the CPU usage jump to the high nineties for an individual process, the mouse starts reacting reeeeealllly sloooooowly and finally the whole PC freezes and hangs.
It's happened so far with the following:
Firefox and Skype (1.4 Beta)
Firefox and K3B
Firefox and Amarok (using the replaygain normaliser script on my entire music collection)
Xine and Amarok (running the script again)

It has been quite hot here these last few days, which may partly explain the overheating, but I've never experienced similar problems before. I don't think there's an onboard thermometer that I can monitor with. Any ideas where I might look for a cause and solution?

I don't know if there's a link, but my network connection keeps falling out and had been problematic since the beginning of the week (since I upgraded to Fesity, more or less)

---

### Post by diatribe on 2007-06-22
what are your hardware specs? also top will let you know what processes are using the most cpu/ram

---

### Post by pickarooney on 2007-06-22
AMD 3400XP 64 bit, 1GB DDRAM, nVidia 6200 Turbocache 64/256MB, onboard sound.
In the past I had serious problems with a conflict between the gfx drivers and the chipset, but these were resolved in the nvidia driver released earlier this year. I'm not sure how to tell what version is installed now after upgrading to Feisty.

Top tells me (when the fan is blasting away) variously that firefox is using 97% or mp3gain is using 98% of the CPU, although I didn't check the RAM usage last time.
Right now, the browser is using less than 1% CPU and 12% of my RAM.

---

### Post by pickarooney on 2007-06-28
Can anyone help me out here - I just got another freeze when changing the properties in SMplayer. I couldn't access a shell to check **top** and don't know where else to look. 
This is driving me nuts.

---

### Post by nocturn on 2007-06-28
> **pickarooney said:**
> Can anyone help me out here - I just got another freeze when changing the properties in SMplayer. I couldn't access a shell to check **top** and don't know where else to look. 
This is driving me nuts.

Just a thought, but check out if DMA is turned on on your HD.
sudo hdparm /dev/hda

---

### Post by pickarooney on 2007-06-28
It is, thanks.

---

### Post by pickarooney on 2007-06-28
Before I go reformat, I'd really like to find out if this is a hardware/software/driver issue.
I checked **/var/log/messages** to see the last thing that happened before the system froze, forcing me to switch off at the mains:

```

Jun 28 11:28:58 marklar kernel: [  834.236000] usb 2-4: USB disconnect, address 8
Jun 28 11:55:44 marklar -- MARK --
Jun 28 12:15:44 marklar -- MARK --
Jun 28 12:35:44 marklar -- MARK --
Jun 28 12:55:45 marklar -- MARK --
Jun 28 13:15:48 marklar -- MARK --
Jun 28 13:27:45 marklar kernel: [ 7961.328000] SCSI device sdb: 494848 512-byte hdwr sectors (253 MB)
Jun 28 13:27:46 marklar kernel: [ 7961.340000] sdb: Write Protect is off
Jun 28 13:27:46 marklar kernel: [ 7961.360000] SCSI device sdb: 494848 512-byte hdwr sectors (253 MB)
Jun 28 13:27:46 marklar kernel: [ 7961.368000] sdb: Write Protect is off
Jun 28 13:27:46 marklar kernel: [ 7961.368000]  sdb: sdb1
Jun 28 15:20:33 marklar syslogd 1.4.1#20ubuntu4: restart.

```

**sdb** is my camera's memory card.
Maybe if I had some sort of widget that monitors when the CPU overloads....

---

### Post by pickarooney on 2007-06-29
Just bumping this out of pure frustration with the increasingly regular crashes, in the hope someone might have a tip... :(

---

### Post by John.Michael.Kane on 2007-06-29
Is there anyway of adjusting the amount of memory your video card is caching?

As some of it's capacity comes from available system memory eg: it's taking 256mb from your 1gb of system ram.

---

### Post by pickarooney on 2007-06-29
Not really, it takes whatever it needs, from 0-192MB, but I rarely use anything that requires much GPU power.
I've been testing this evening (5 crashes in an hour :() and the crashes happen like so:
The cursor stops blinking (or images stop moving if I'm watching a video), everything stops, I can move the mouse once - it jumps a few cm - and then everything freezes up. On one occasion, after five minutes it came back alive again, but other times I can leave it for over an hour and nothing moves.
I don't think it's a heating problem - nothing is particularly hot in the system and I left the PC running all day with a liveCD and there was no crash (I'm currently logged in from a LiveCD after 6 crashes in a row, all Ok so far touch wood).
I've also been running** top** constantly and processes haven't been going over 60% when crashes occur.

---

### Post by pickarooney on 2007-07-02
So, both of my IDE hard-drives are apparently hosed - loads of errors mounting and unmounting them on startup and shutdown and tens of thousands of bad sectors/nodes when fscking them. But, even with both these drives unmounted I *still* get frequent freezes. What can I do to stop the rot? New MoBo? New PSU? Two (or three?) new drives? Dump the computer and get a new one?

---

