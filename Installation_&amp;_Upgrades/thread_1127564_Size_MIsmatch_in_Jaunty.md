---
title: "Size MIsmatch in Jaunty"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by Ralex1098 on 2009-04-16
So, I turned on my Dell Mini 9 and decided to run update manager in my jaunty beta. I run the update and get 306 Mb of upgrades. I let it do its thing and get a myriad of "failed to fetch" based on "size mismatches". Anyone encounter this before in Jaunty beta?

I have 106 Mb of updating left to do.

---

### Post by cariboo on 2009-04-16
I would suggest you change to a different download server. Go to System-->Administration-->Software Sources and in the download from dropdown select other.

Jim

---

### Post by Ralex1098 on 2009-04-17
Worked perfectly. Thanks!

---

### Post by KarthikH on 2009-07-20
It worked for me after a change in server, but them it started failing with the same 'size mismatch' error when I tried to download something else.
It seems to be a generic problem and is not fixed by change of servers.

anyone else has any ideas?

--KH

---

### Post by wesc on 2009-09-11
I started running into the "Size Mismatch" errors after I started running DansGuardian on my firewall machine.  It, of course, makes perfect sense because what DG delivers is not what apt was expecting because of some pretty non-obvious (file content and file name) rules within DG.  It also, of course, wasn't obvious to me at first due to the time that elapsed between the two events (I slept several times in between them).

In my case, I just added site exceptions for debian.org, ubuntu.org, etc. so that these sites don't get filtered, but I'm betting another/better solution would be to point at ftp servers instead of http servers for my packages...  Any comments/opinions on that?

---

