---
title: "Built in mic not working on Acer Aspire D255"
date: 2010-11-24
forum: Hardware
---

### Post by NinjaFOBs on 2010-11-24
I got an Acer Aspire D255 netbook and have Ubuntu 10.10 desktop installed on it. I was trying to record the screen with XVidCap screen recorder, but it won't record sound. If I record sound with the Sound Recorder app it works fine, but all other apps that record sound don't work. Hope some one can help me out.

---

### Post by cgallaty on 2010-12-08
I just had to set this up in Ubuntu 10.10 (Netbook Remix) on a D255. 

First get pavucontrol from the Ubuntu Software Center (or apt-get install if you roll that way) 

Launch it, then go to the Input Devices tab and hit the little lock icon, then drop one of the two channels to 0 ('Front Right') worked for me.

You should be able to see your levels right away.

---

### Post by Nath4n on 2010-12-12
> **cgallaty said:**
> I just had to set this up in Ubuntu 10.10 (Netbook Remix) on a D255. 

First get pavucontrol from the Ubuntu Software Center (or apt-get install if you roll that way) 

Launch it, then go to the Input Devices tab and hit the little lock icon, then drop one of the two channels to 0 ('Front Right') worked for me.

You should be able to see your levels right away.


Thank you!  I have a d255 I just sudo apt-get install pavucontrol and my mic works now.  Thanks a lot.

---

