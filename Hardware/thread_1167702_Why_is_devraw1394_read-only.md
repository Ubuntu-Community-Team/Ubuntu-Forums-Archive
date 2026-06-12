---
title: "Why is /dev/raw1394 read-only??"
date: 2009-05-23
forum: Hardware
---

### Post by gilgongo on 2009-05-23
I'm using Jaunty, and have used the last four major Ubuntu releases, and each time it's been the same when I want to capture video from my FireWire camcorder:

1. Install Kino

2. Run Kino, hit "capture" tab

3. See Kino complain about /dev/raw1394.

4. Scream

5. sudo chmod 777 /dev/raw1394

WHY???? WHY????

So - I've had it. I'm going to start a campaign:

"Make /dev/raw1394 writable by default"

I'm going to post to the developer mailing lists. I'm going to petition Mark Shuttleworth, I'm going to do WHATEVER IT TAKES to change this.

With issues like this, it's no wonder Ubuntu hasn't seen the take-up people expect.

---

### Post by WA_Garrett on 2009-05-24
It's things like that that make me realize that the only way you can create a video in Linux is if you're a massive geek with ample time on your hands. :( 

I would like to join your campaign, please provide those details.

---

### Post by stenella on 2009-05-25
I just ran into this too when I hooked up our camera to download footage... So how do I get it to capture the footage? I'm new to this and pretty new to Linux, and I really, really don't want to have to go into Vista to capture video. I'll join.
Fraser

---

### Post by WA_Garrett on 2009-05-25
> **stenella said:**
> I just ran into this too when I hooked up our camera to download footage... So how do I get it to capture the footage? I'm new to this and pretty new to Linux, and I really, really don't want to have to go into Vista to capture video. I'll join.
Fraser

I have found there are a few ways to capture video from a DV camera, all of them involve the command line is some way though. 

One way is to connect your camera and open the terminal and use the following command. 
> dvgrab
That command starts playing the video in your camera and records to your hard drive when it encounters a new clip. 

If you're trying to use kino another thing you could do is open kino as a super user through the terminal using the command
> sudo open kino
and then type your administrative password, that would allow you to have access to raw1394 file under dev

or you could just change the permissions of the raw 1394 file under dev by going up to the root of you drive system in your terminal and by typing in the terminal 
> sudo chmod 777 /dev/raw1394

Unfortunately you will have to do that every time you turn your computer on and want to capture video.

---

### Post by gilgongo on 2009-06-01
You may also be able to put chmod 777 /dev/raw1394 into the system startup scripts (eg the file /etc/rc.local) so it changes the permissions on boot.

---

