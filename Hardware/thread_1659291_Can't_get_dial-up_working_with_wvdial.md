---
title: "Can't get dial-up working with wvdial"
date: 2011-01-03
forum: Hardware
---

### Post by jesse.melhuish on 2011-01-03
I've been looking for a situation similar to mine but have found none.  I figure since dial-up isn't exactly common anymore it may be harder to find a similar occurrence.  Here's the problem: I'm trying to convert my family to Ubuntu, which I can't do unless I can get our dial-up connection working, since all they do is type and use the internet(which is why I think conversion will be easy).  I've gotten as far as getting the modem driver installed and wvconf set up, but now I get some weird errors.  I managed to fix the first problem I was having by changing the configuration username to "user@wmconnect.com" instead of just the user name, but new problem have arisen.  Here's the output as it runs:

--> Modem initialized.
--> Sending: ATDT9851121
--> Waiting for carrier.
ATDT9851121
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
UQKT2 an1.stl10.da.uu.net
Login: 
--> Looks like a login prompt.
--> Sending: <username>@wmconnect.com
<username>@wmconnect.com
Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Mon Jan  3 12:39:13 2011
--> Pid of pppd: 2161
--> Using interface ppp0
--> pppd: (U&#65533;[08]@S&#65533;[08]
--> pppd: (U&#65533;[08]@S&#65533;[08]
--> pppd: (U&#65533;[08]@S&#65533;[08]
--> pppd: (U&#65533;[08]@S&#65533;[08]
--> pppd: (U&#65533;[08]@S&#65533;[08]
--> Disconnecting at Mon Jan  3 12:39:44 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

The password and username are correct before it is asked.  I will be very grateful if anyone can help me, I really want to see my family understand why Ubuntu is so much better than Windows.  Thanks in advance!!

---

