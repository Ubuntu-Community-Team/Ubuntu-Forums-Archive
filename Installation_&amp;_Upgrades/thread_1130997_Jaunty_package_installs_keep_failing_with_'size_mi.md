---
title: "Jaunty package installs keep failing with 'size mismatch'"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by Tyconic on 2009-04-20
Hi guys,

Just wondering if anyone's having the same (extremely aggravating) problem. Some things install fine but others just plain fail. Among the things I'm unable to install are gstreamer ffmpeg plugins and Java, both sun and openjdk versions!

Thanks,

---

### Post by Tyconic on 2009-04-20
I should clarify the error I'm getting. Here's what happens when I try installing gstreamer ffmpeg plugin:

```

$ sudo apt-get install gstreamer0.10-ffmpeg
...
Fetched 2707kB in 5s (503kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.12-1_amd64.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by KarthikH on 2009-07-20
I have the same problem and it doesn't work if you merely change the servers.
BTW.. @Tyconic: did you try this on an office machine with a firewall/proxy. I suspect it to be a proxy issue.. but then I couldn't solve it with that either.. maybe I'm doing something wrong..

any ideas guys?
--KH

---

### Post by Tyconic on 2009-07-22
KarthikH, this might be a weird question, but are you still running the alpha or beta? If so you might try upgrading to the release build. I believe this is what did it for me.

---

### Post by wesc on 2009-09-11
I started running into the "Size Mismatch" errors after I started running DansGuardian on my firewall machine.  It, of course, makes perfect sense because what DG delivers is not what apt was expecting because of some pretty non-obvious (file content and file name) rules within DG.  It also, of course, wasn't obvious to me at first due to the time that elapsed between the two events (I slept several times in between them).

In my case, I just added site exceptions for debian.org, ubuntu.org, etc. so that these sites don't get filtered, but I'm betting another/better solution would be to point at ftp servers instead of http servers for my packages...  Any comments/opinions on that?

---

