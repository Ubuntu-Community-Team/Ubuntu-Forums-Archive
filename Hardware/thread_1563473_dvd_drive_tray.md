---
title: "dvd drive tray"
date: 2010-08-29
forum: Hardware
---

### Post by venturosa on 2010-08-29
My Pioneer DVD drive works perfectly except when I go to eject a disc the tray opens and then immediately closes again. I have to be quick to grab hold of it to take the disc out.
This did not happen before upgrading to Karmic (now running Lucid). This doesn't happen with my other drive, an LG. Also the Pioneer drive ejects properly with windows.
I have seen this reported before but have never found a solution for it. It's obviously a software issue, so there must be one.
Any help greatly appreciated.

---

### Post by varunendra on 2010-08-30
If this is really software-related, I've no idea. Because it has been very frequent with samsung (older now) drives and it always was a drive's hardware problem- with windows, linux,.. whatever.

Dirty tray with extra friction combined with a loose belt caused incomplete ejection of the tray which thus couldn't reach the **stop** **switch** at the opening end. Therefore, after motor's ejection mode timeout, the cd tray returned back automatically. The remedy was typical Indian type: to wind a cotton thread around the tray-ejection pulleys and fix it with some rubber-based adhesive. This provided a better grip to the ejection belt thus helping full ejection of the tray.

However, as you said, if the drive is still fine with windows & the problem occurs only with ubuntu, then it maybe a different one. You may check whether the tray is completely ejected or not. If not, then you may try the above workaround or get a new belt if you can.

If not sure, please confirm these:

[LIST=1]
[*]Is the drive still okay with windows everytime you switch to it?
[*]When this happens, does the tray come out completely before returning back?
[/LIST]

---

### Post by venturosa on 2010-08-30
Thanks for replying.
Yes the drive does always work properly with windows, fully ejecting the tray. It does fully eject with Ubuntu but flies straight back in again. It's only a year old and works perfectly in every other way.

---

### Post by varunendra on 2010-08-30
Hmm.... looks like [this]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/546373") bug then. Unfortunately, it seems there's no fix released for it yet. :( 
(however, there's a better yet still irritating workaround as suggested in post #19 of the above bug-report page.) You may add your case as another confirmation there.

---

### Post by venturosa on 2010-08-30
Thanks for pointing me in the right direction.
I added the line "dev.cdrom.autoclose = 0" to /etc/sysctl.conf as suggested in the "bugs" page and rebooted.  My dvd drive now performs perfectly.

---

### Post by varunendra on 2010-08-30
Ah.. typo on my part, I'm editing it to make #19.

Glad it worked for you. However, aren't you having the "no automount" problem as he complained about?

---

### Post by venturosa on 2010-09-01
I choose not to have my dvd drives etc. automount so have no problems. It's easy enough to right click and select mount.
In case you're wondering why;  The main reason is I occasionally use packet-writing on cd's/dvd's and need to use a different mount point for this (at least that's the only way I can get it to work).

---

### Post by amr-maro on 2010-09-02
I have the same [COLOR=DeepSkyBlue][problem]("http://ubuntuforums.org/showthread.php?t=1565575&highlight=dvd+tray+problem")[/COLOR] but with some other complications.

---

### Post by amr-maro on 2010-09-03
That solution didn't work for me. The [problem]("http://ubuntuforums.org/showthread.php?t=1565575") still exists.

---

