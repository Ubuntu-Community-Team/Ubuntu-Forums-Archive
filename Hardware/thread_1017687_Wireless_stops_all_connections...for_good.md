---
title: "Wireless stops all connections...for good"
date: 2008-12-21
forum: Hardware
---

### Post by scoleshill on 2008-12-21
So I've been using Ubuntu for the last 6 months or so, and no problems. The other day I was connected to my network, went away for 5 minutes (no programs or browsers were running), came back and the connection was "cut". I tried to reconnect even after restarting the laptop a few times and now it won't connect to any network, unprotected or otherwise. 

I'm running 8.04 on an Acer 2420 with a centrino chipset. Any help would be much appreciated.

---

### Post by trapgate on 2008-12-21
Sounds like the wireless switch got toggled accidentally:

[http://answers.yahoo.com/question/index?qid=20080209164040AAkvB7Z](http://answers.yahoo.com/question/index?qid=20080209164040AAkvB7Z)

---

### Post by scoleshill on 2008-12-21
I wish it were that simple... the laptop can see and any network I'm in range of and even try to connect to them, but after about 20 seconds of trying to connect it gives up. When I did run windows, the switch completely shut off any wireless capabilities, so it being on or off isn't the problem.

---

### Post by trapgate on 2008-12-21
So the next question is whether this is a configuration problem or there's something wrong with the hardware. I'd suggest booting the Ubuntu LiveCD to see whether the wireless works there.

---

### Post by scoleshill on 2008-12-21
I tried using wireless on Puppy Linux since I didn't have an Ubunutu Live CD on me and had no luck, I still couldn't connect to a wireless network. A hardware problem doesn't make a lot of sense, since the laptop just sat there and nobody touched it.

Is there any type of software I could run to see if the wireless chipset is actually broken?

---

### Post by bdoe on 2008-12-21
I ran into this issue when I updated my WICD installation. I ended up having to revert back to the previous version to get connectivity again.

Try this:

Set your wireless router to unsecured (no WEP, WPA, etc) and then try to connect. I don't advise leaving your network like this for any length of time, but just long enough to determine if you can connect to unsecure networks. If you can connect, then your problem may be with your wpasupplicant driver.

---

### Post by scoleshill on 2008-12-21
I've tried that and it won't connect regardless. I made a live cd of 8.10 and it seems to work now, so I'm just going to try and upgrade from Hardy to Intrepid and hope it works.

---

