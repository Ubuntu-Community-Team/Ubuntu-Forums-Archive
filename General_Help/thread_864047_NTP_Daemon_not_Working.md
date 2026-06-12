---
title: "NTP Daemon not Working"
date: 2008-07-19
forum: General Help
---

### Post by icarusfall on 2008-07-19
OK, I've googled this and searched on the forum, but no-one seems to have experienced this exact problem. Basically, my computer's clock drifts away from the current time when it's been on for a few hours. No problem, right? That's exactly what the ntp daemon is supposed to fix. But it doesn't seem to. I've checked and double-checked that the ntp daemon really is running (/etc/init.d/ntp), and I've checked the config file (/etc/ntp.conf), and it does have ntp.ubuntu.com as well as some other local (UK) timeservers listed. But, it just doesn't seem to be doing anything, because the time drifts away from the real time.

Obviously I can manually just run:
sudo /etc/init.d/ntp stop
sudo ntpdate ntp.ubuntu.com
sudo /etc/init.d/ntp start

Every so often to fix the problem, but this doesn't explain why the daemon isn't doing what it's supposed to. I've checked /var/log/syslog for any news of the daemon reporting errors, but nothing.

Does anyone have any suggestions of where I should look?

By the way, I'm running Ubuntu 8.04, and the connection to the internet seems to be fine.

---

### Post by Bachstelze on 2008-07-19
While the daemon is running, run

```
ntpq -p
```

and post the results.

---

### Post by icarusfall on 2008-07-19
OK, thank you. Here is the output from that command:

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 europium.canoni 193.79.237.14    2 u   46   64  377  210.211  438570. 31976.3
 maverick.mcc.ac 192.43.244.18    2 u   44   64  277   34.465  438686. 34384.3
 veracity.mcc.ac 193.62.22.98     2 u   58   64  377   23.540  437787. 31802.2
 ntp2.ja.net     .MSF.            1 u   50   64  377   37.204  438683. 31718.7
```

---

### Post by Bachstelze on 2008-07-19
You have very large values indeed...  Here's mine :

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*ntp1.oma.be     .PPS.            1 u  611 1024  377    7.907    3.656   1.042
+woon.curie.fr   .PPS.            1 u  592 1024  377    6.140    3.260   0.241
+chronos.cru.fr  .GPS.            1 u  616 1024  377   17.720    3.399   1.796
 ntp1-rz.rrze.un .INIT.          16 u   5d 1024    0    0.000    0.000 4000.00

```

Also, the fact that you have no line with a + or * at the beginning does indeed mean that you aren't actually synchronizing to any server. Since you're in UK, try [these](http://www.pool.ntp.org/zone/uk) instead.

---

### Post by icarusfall on 2008-07-19
OK, so I added the lines:
	   server 0.uk.pool.ntp.org
	   server 1.uk.pool.ntp.org
	   server 2.uk.pool.ntp.org
	   server 3.uk.pool.ntp.org
to /etc/ntp.conf

Then I ran
/etc/init.d/ntp restart

And now the output of 
ntpq -p

is

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 ntp.ubuntu.com  193.79.237.14    2 u   58   64    3  313.325  192595. 7037.85
 maverick.mcc.ac 192.43.244.18    2 u   57   64    3  373.282  192739. 7142.96
 veracity.mcc.ac 193.62.22.66     2 u   56   64    3  393.821  192862. 7212.09
 ntp2.ja.net     .MSF.            1 u   54   64    3  229.432  192984. 7170.68
 spork.qfe3.net  212.13.195.4     3 u   51   64    3  175.982  193286. 7132.84
 calx.pulsewidth 195.66.241.3     2 u   53   64    3  217.729  193089. 6839.58
 ntp1.****.org   130.88.200.98    3 u   52   64    3  217.015  193203. 6906.33
 scarlett.lon.re 193.67.79.202    2 u   51   64    3  179.565  193284. 6846.73
```


Sorry, how do I do the formatting the output in the code mark-up, by the way?

Should I be concerned that there still doesn't seem to be a line starting with + or *?

---

### Post by Bachstelze on 2008-07-19
> **icarusfall said:**
> OK, so I added the lines:
	   server 0.uk.pool.ntp.org
	   server 1.uk.pool.ntp.org
	   server 2.uk.pool.ntp.org
	   server 3.uk.pool.ntp.org
to /etc/ntp.conf

Do not just add them, also remove all the other server lines.

> **icarusfall said:**
> Then I ran
/etc/init.d/ntp restart

And now the output of 
ntpq -p

is

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 ntp.ubuntu.com  193.79.237.14    2 u   58   64    3  313.325  192595. 7037.85
 maverick.mcc.ac 192.43.244.18    2 u   57   64    3  373.282  192739. 7142.96
 veracity.mcc.ac 193.62.22.66     2 u   56   64    3  393.821  192862. 7212.09
 ntp2.ja.net     .MSF.            1 u   54   64    3  229.432  192984. 7170.68
 spork.qfe3.net  212.13.195.4     3 u   51   64    3  175.982  193286. 7132.84
 calx.pulsewidth 195.66.241.3     2 u   53   64    3  217.729  193089. 6839.58
 ntp1.****.org   130.88.200.98    3 u   52   64    3  217.015  193203. 6906.33
 scarlett.lon.re 193.67.79.202    2 u   51   64    3  179.565  193284. 6846.73
```

No change... There's really something wrong here. Do you have a proxy or firewall that could be blocking the connection to the servers?


> **icarusfall said:**
> Sorry, how do I do the formatting the output in the code mark-up, by the way?

Wrap your text around [*code] and [*/code] (without the asterisks).

> **icarusfall said:**
> Should I be concerned that there still doesn't seem to be a line starting with + or *?

Yes, because the +'s indicate which servers are selected for synthronization, and the * indicates which server your system is currently synchronizing with. So if you don't have them... you get the idea.

---

### Post by icarusfall on 2008-07-19
OK, well I replaced the lines, and now the output is:
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 0.uk.pool.ntp.o 193.79.237.14    2 u   62   64    1  396.680  285151.   0.001
 1.uk.pool.ntp.o 130.159.196.118  3 u   61   64    1  361.194  285251.   0.001
 2.uk.pool.ntp.o 192.87.106.3     2 u   60   64    1  229.579  285272.   0.001
 3.uk.pool.ntp.o 249.240.53.144   2 u   59   64    1  231.921  285387.   0.001

```

I do have a firewall on my router, but it doesn't have any particularly restrictive settings. Is there a port that needs forwarding or something?

---

### Post by Bachstelze on 2008-07-19
> **icarusfall said:**
> OK, well I replaced the lines, and now the output is:
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 0.uk.pool.ntp.o 193.79.237.14    2 u   62   64    1  396.680  285151.   0.001
 1.uk.pool.ntp.o 130.159.196.118  3 u   61   64    1  361.194  285251.   0.001
 2.uk.pool.ntp.o 192.87.106.3     2 u   60   64    1  229.579  285272.   0.001
 3.uk.pool.ntp.o 249.240.53.144   2 u   59   64    1  231.921  285387.   0.001

```

I do have a firewall on my router, but it doesn't have any particularly restrictive settings. Is there a port that needs forwarding or something?

There shouldn't. Okay, first fix that huge offset, run the daemon again and paste what you get.

```
sudo /etc/init.d/ntp stop
sudo ntpdate 0.uk.pool.ntp.org
sudo /etc/init.d/ntp start
ntpq -p
```

Also, are you by any chance dual-booting with Windows?

---

### Post by icarusfall on 2008-07-20
OK, many apologies for the delay, and thank you very much for taking the time to help me with this. I ran those commands, and the output of ntpq -p is:
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 0.uk.pool.ntp.o 130.88.200.6     3 u    4   64    1   26.848    0.927   0.001
 starbug.netiner 193.62.22.66     2 u    3   64    1   19.539    1.894   0.001
 syrinx-123.yann 209.51.161.238   2 u    2   64    1   20.090   -0.934   0.001
 dns1.rmplc.co.u 131.188.3.221    2 u    1   64    1   23.622    1.022   0.001


```

And, it's not a dual boot, this box only has Ubuntu installed on it.

---

### Post by icarusfall on 2008-07-20
Well, I don't know what happened, but it seems to be working now:
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+ns.integri.net  130.88.200.6     3 u  108  128  377   21.583    1.520 113.065
+noisebox.positi 130.159.196.118  3 u  113  128  377   20.241    0.477 113.828
-cheddar.halon.o 193.0.0.228      2 u   87  128  377   19.728   -2.420 165.888
*z.je            192.87.106.3     2 u   11  128  377   20.061    2.001   1.062

```

Thank you very much indeed for your help.

---

### Post by kg4cna on 2008-07-26
Nevermind fellas....I did a clean install and put everything back and it's working fine now.

---

### Post by mmXmm on 2009-06-02
Hate to necro-post; but, this is exactly what I'm experiencing

My offset jumps greatly with each passing minute... here's a ntpq -p
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 yuma.acns.colos 192.43.244.18    2 u   62   64  377    2.737  -6514.1 4104.41

```If I run:

```

:/etc/init.d$ sudo ./ntp stop
:/etc/init.d$ sudo ntpdate ntp.colostate.edu
:/etc/init.d$ sudo ./ntp start

```This is immediately after:
```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 yuma.acns.colos 192.43.244.18    2 u    3   64    1    1.065  -68.515   0.001

```About a minute later:
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 yuma.acns.colos 192.43.244.18    2 u    6   64    3    1.447  -997.60 929.089

```Here's my syslog output (grep ntp):
```

Jun  2 14:51:29 HHS007 ntpd[5894]: precision = 1.000 usec
Jun  2 14:51:29 HHS007 ntpd[5894]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun  2 14:51:29 HHS007 ntpd[5894]: Listening on interface #1 wildcard, ::#123 Disabled
Jun  2 14:51:29 HHS007 ntpd[5894]: Listening on interface #2 lo, ::1#123 Enabled
Jun  2 14:51:29 HHS007 ntpd[5894]: Listening on interface #3 eth0, fe80::215:5dff:fea5:112e#123 Enabled
Jun  2 14:51:29 HHS007 ntpd[5894]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun  2 14:51:29 HHS007 ntpd[5894]: Listening on interface #5 eth0, 129.82.165.7#123 Enabled
Jun  2 14:51:29 HHS007 ntpd[5894]: kernel time sync status 0040
Jun  2 14:51:29 HHS007 ntpd[5894]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift

```

It seems to me to be very similar to what icarusfall was experiencing; unfortunately, there was never any resolution.

Any ideas?
Thanks!

---

### Post by mmXmm on 2009-06-03
Gave up on ntpd

put a ntpdate in crontab - it sucks; but, if ntpd refuses to work, you do what you can.

---

### Post by ghen on 2009-06-10
From what little I know of how NTPD works, all it does is changes the offset for your system clock. So if your offset keeps getting larger very quickly that means your system clock is really slow. Probably a BIOS or CMOS battery problem.

How often did you set ntpdate to run to keep the time updated?

---

### Post by iaindb on 2011-03-18
another necro-post, but this hasn't been answered and it's high up in google so here goes:

ntpdate via cron is bad for a number of reasons not limited to: it doesn't handle servers with bad time, it doesn't calculate drift, it doesn't have redundancy, and by default it steps, not slews.  This may be ok for you, but not for everyone.

mmXmm: typical reasons for clocks drifting out of sync quickly include bad driftfiles (yours was emtpy), BIOSs, hardware, and kernels - c 2.6.18 had some drifting issues from memory.  Update all of those things and see if it works.  Also check the kernel has the right modules for your clock.

icarusfall: it probably works after you ran ntpdate because ntpd will not do anything if the difference is too big.  When you ran ntpdate you reduced the difference from 200s to a few ms, so ntpd was happy to work with you.

Hope that helps you googlers a bit!

---

### Post by hvengel on 2011-07-05
Your offset was too big and ntp will not work with large offsets.  Once you ran ntpdate and got the offset down low enough ntp was able to do it's job.

---

