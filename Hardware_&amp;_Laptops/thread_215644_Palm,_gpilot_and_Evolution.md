---
title: "Palm, gpilot and Evolution"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by dangermouse28 on 2006-07-14
Ok - I give up!

Syncing my Zire 71 under 5.10 was easy and reliable. Syncing under 6.01 is impossible. It's not just the USB connection which is at fault. I've spent several days configuring the IrDA port on my laptop and it connects the Zire and the laptop once every 20 tries or so. When it does connect, it appears to transfer the data but nothing appears on the Zire.

Is this ever going to get solved? For anyone who uses and relies on their PDA, being able to sync and restore when necessary is absolutely vital. (and yes my PDA crashed a week ago and yes, because of the state of the Evolution, gpilot, Palm link, I've lost the lot :evil: )

I once read a comment by a developer on a different bulletin board that he wrote apps for his own use and if they didn't work for others he didn't give a s**t. I'm beginning to think this same mentality applies here. :(

---

### Post by Paerez on 2006-07-14
I can use JPilot consistently, but I experience similar results in evolution & gnome-pilot. If you really need the pilot stuff, use jpilot for the time being. I have a Z22, so you should see similar results. Good luck.

---

### Post by Paerez on 2006-07-16
Got it!!!

OK guys I think I figured it out. My method gives me 100% success rate with evolution.

Open up evolution and plug in your palm (order doesn't matter). Then open "synchronization options" in the "edit" menu.

If the sync menu doesn't open, run:
```

# killall -9 gpilotd
# killall -9 gpilotd-control-applet

```

In the devices tab make sure you have a device that syncs over USB using "/dev/ttyUSB1".

Now make sure to leave sync options open, and hit sync on your palm. Thats it!

I figured out that you have to have sync options open, not just evolution. When only evolution is open, mine hangs at "Identifying User" on my palm's screen.

NOTE: You wont get any status on ubuntu, only the palm screen says the progress.

Good luck all!

btw this is my Zire 22.

---

### Post by dangermouse28 on 2006-07-17
Thanks

I'll have a go at this and let you know if it works!

---

### Post by baronKarza on 2006-09-14
Hi, I followed the suggestions of Paerez and dangermouse28 by I still can't connect. After more than 50 attemps only one time it sync (and the sad thing is that I don't know what I did to make it works).
Does someone know if there any bug in 2.6.15 kernel or udev (I'm using Dapper).
Thx in advance.

---

### Post by Paerez on 2006-09-14
I actually can't get it to work anymore. I have been using jpilot.

---

### Post by rplantz on 2006-09-21
I ran gpilotd from the command line. It pauses and says that it's "Watching Cradle."

I plugged in my Palm Pilot m100 and hit the sync button. Amongst the messages, I got one saying that the directory /home/bob/MyPilot could not be found. So I created the directory.

I then killed gpilotd.

Whenever I want to sync, I make sure that gpilotd is not running, then I start it from the command line. Now when I hit the sync button on the Palm, it syncs just fine.

After the sync, I have to end gpilotd with a ctrl-c.

There must be a better way, but at least this works (for me).

---

### Post by rkh on 2006-11-02
Success! Here's what worked with my Z22:

under device options in synchronization options in Evolution 2.8.1 (Edgy)
use ttyUSB1
set timeout to 40
set speed to the slowest option (9600)

hit the synch button on the palm then activate gnome pilot. 

I hope that this helps.

---

### Post by rkh on 2006-11-06
I did a bit more poking around after having some more trouble. The damn thing wouldn't sync-again-so, after multiple tries I checked out System Monitor -System>Administration- and discovered that I had about six instances of gpilotd-control-applet running.

 I killed everything having to do with Gpilot and, on a hunch, checked out what conduits were activated. I really only needed calendar, todo, and addresses, but I had a lot of other stuff running as well. So, keeping System Monitor around -just to keep tabs on what was happening in the background- I unchecked everything except addresses-it worked. I added calendar and it worked, I added todo and it worked.

So, to summarize what has worked for me:
  Set the connection speed slow.
  Check to see what your USB settings are.
  Check System Monitor to make sure that you don't have multiple instances   of anything running.
  Make sure that you have only those conduits that you actually want to use activated.

---

### Post by Feenix3k on 2007-03-27
I had to dump gnome pilot. Went to jpilot, if I just sink and not back up it works fine if you push the sync butten on the palm (I have an E2) then the JPalm sync button. I dont know about the other palms ,but the E2 hold memery if it goes dead from the internal battery

---

### Post by Watonga on 2007-04-14
Paerez's solution worked perfectly for me. Thanks Paerez!

---

### Post by bouncingmolar on 2007-10-13
If i've already synced with evolution using gpilot, what do you have to do to switch to jpilot. will i get double ups of all my data in evolution?

---

