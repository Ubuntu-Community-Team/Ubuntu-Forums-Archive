---
title: "VIA 82C686A soundcard -&gt; full duplex?  Okay with Ekiga?"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by ts2000 on 2006-03-18
Running Dapper - When trying to connect Ekiga cannot connect to my sound device - although it is detected in the configuration.

+ I get dial beeps which gives me hope this thing will run!
- Don't get sound when connecting to sip:500@ekiga.net which is the test connection.
- Cannot move volume controls for mic or volume when connected.
- When I connect occassionally get a dialogue box saying ekiga can't connect to sound device and asks the question about the device being capable of full duplex.

So this is the question... is the VIA82C686A/B a full duplex sound device?

---

### Post by ts2000 on 2006-03-18
I got the sound working by doing:

supertramp@ubuntu:~$ekiga -d 4

debugging mode... impossible to follow the sequence of events but sound worked, however, no microphone.  

Skype works fine.  So this is intrigue.

---

