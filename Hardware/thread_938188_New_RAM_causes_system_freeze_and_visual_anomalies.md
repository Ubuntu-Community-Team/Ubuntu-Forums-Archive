---
title: "New RAM causes system freeze and visual anomalies"
date: 2008-10-04
forum: Hardware
---

### Post by GregoryMA on 2008-10-04
I just install more RAM in my laptop.  The new RAM is recognized and seems to be working correctly.  Except without notice it will freeze.  When this happens there are short vertical lines on the monitor.  Often purple or green.  Is there something I need to configure to get this to work properly?

Thanks in advance, Greg.

---

### Post by cariboo on 2008-10-04
Run memtest for 3-4 hours, to see if you get any errors.

Jim

---

### Post by GregoryMA on 2008-10-05
I ran it for 4 or 5 hours and it came up with no errors.

---

### Post by cariboo on 2008-10-05
The only other thing I can suggest, is becuase the ram is shared with the video adapter, you may want to reinstall your video drivers.

Jim

---

### Post by Kevbert on 2008-10-05
Is the memory the same type as the original ? Mix and match is not a good idea.  If, in terminal, you enter 
```
free -m 
```
what do you get ? Is the total value close to the amount of memory you now have installed ?

---

### Post by GregoryMA on 2008-10-05
It is close to how much I added.  I had two sticks of 256 in.  I replaced the first one with 1 gig.  free -m showed I have about a gig in there.  

I will take out the 256 stick and see if that fixes it.

---

### Post by GregoryMA on 2008-10-05
I guess I was wrong.  When I took the 256 stick out (so that I just had the 1 gig stick) there was 877mg's but when the 1 gig stick was in with the 256 stick there was 1.1gig's  

So with only the one new stick in (1 gig) I still have the problems.  I just had the whole thing freeze up.

Can I conclude that the RAM is messed up, or is it a software problem?

---

### Post by Kevbert on 2008-10-05
Unless the manual says you can install different sizes of memory you shouldn't use 256Mb + 1Gb, but what is more important is the memory type and speed which should be the same.  It's possible that some of the RAM could be used as shared memory with the video card.  
The memory sticks are probably fine as you've run memtest for a few hours.
I think probably your real problem is more likely due to the programs that you are running.  If it's running, try stopping compiz, as that's quite memory hungry.  You can do that temporarily with [[COLOR="Red"]compiz-switch[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Switch"). Also using terminal try
```
top
```
as this will display what is running and taking memory resources.

---

### Post by GregoryMA on 2008-10-05
I don't have compiz on my computer.  

I ran top.  The only things using up memory were xorg (10.9%) and firefox (16.3%).  (note that I put the two 256's back in because I was tired of it freezing.)  I have been monitoring the memory load quite frequentely during all of this via Gnome System Monitor.  When I had the 1 gig stick in it was stable at around 35 or 40%.

I checked the speed and type of both the old and new RAM.  They are both 333mHz and DDR.

---

### Post by Kevbert on 2008-10-06
Good. It may be worth checking that you haven't upset the display card (assuming it's not on-board the mobo) when you installed the memory sticks. Just check it's seated correctly.  
The other thing you can take a look at is the logs in the /var/log directory to see if any errors are shown there.

---

### Post by GregoryMA on 2008-10-07
The display card is okay.

Is there any specific file I should be looking at in /var/log?  It has quite a lot of stuff in there.  Or should I just snoop around till I find something.

---

### Post by Kevbert on 2008-10-07
Probably the best logs to take a look at are the kern.log and syslog files.
What I suggest you do is to put all the memory in and get the problem.  Then turn off the PC and remove the offending memory. Reboot and check these files to see if you get any errors (someone else may need to help with the actual errors as I'm quite new to this). If these two logfiles are very short and show no errors you may need to look at kern.0.log and syslog.0 as they will be the previously generated logfiles.

---

### Post by GregoryMA on 2008-10-07
The display card is okay.  I will root around in /var/log sometime in the next couple days when I have a bit of time to do it.

---

### Post by GregoryMA on 2008-10-09
It just happened twice.  Both times the last thing logged in syslog was this.

Oct  9 22:59:05 gregory-laptop kernel: [15183.744680] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.

Both times I was on this webpage simply moving the mouse.

---

### Post by GregoryMA on 2008-10-09
It just happened twice.  Both times the last thing logged in syslog was this.

Oct  9 22:59:05 gregory-laptop kernel: [15183.744680] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.

Both times I was on this webpage simply moving the mouse.

---

### Post by GregoryMA on 2008-10-09
A third time.  Also while using the touchpad to scroll. But the same error didn't show up this time.  Here are the last few lines from syslog before it froze.

Oct  9 23:18:39 gregory-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct  9 23:18:39 gregory-laptop ntpdate[5909]: no servers can be used, exiting
Oct  9 23:18:40 gregory-laptop avahi-daemon[4793]: Registering new address record for fe80::290:4bff:fef9:2aec on wlan0.*.
Oct  9 23:18:49 gregory-laptop kernel: [  108.482800] wlan0: no IPv6 routers present

---

