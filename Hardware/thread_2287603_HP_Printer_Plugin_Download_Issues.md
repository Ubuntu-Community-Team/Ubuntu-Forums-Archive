---
title: "HP Printer Plugin Download Issues?"
date: 2015-07-20
forum: Hardware
---

### Post by neltnerb on 2015-07-20
I have a HP LaserJet P1102w which worked great in Ubuntu of all versions for a long time. On my latest system, running Ubuntu 15.04, I removed the printer (unnecessarily) from the printer list, and can't get it to reinstall.

I tried for the more complete tool to try to debug, using hp-plugin and hp-doctor, but it is failing to download the plugin from the hplip website. As best I can tell from manually testing the address in my web browser, the sourceforge page hosting the plugin is down. I am curious if anyone else is having the same issue -- it has been doing this for the last week at least, since I started trying. I was hoping it would just come back up, but I don't know what to do.

hp-doctor gives me this:

```

error: Failed to connect to HPLIP site. Error code = 8
error: Failed to download http://hplip.sourceforge.net/hplip_web.conf.

```

followed by asking if I want to download and disable smart install (which makes perfect sense), but it fails to do so due to presumably the same inability to download the hplip_web.conf file.

I tried using locate to find the file on my computer, but it doesn't seem to have been included by any obvious Ubuntu packages. If someone could point me at a package I can install to get the conf file and manually install the plugin that would probably also solve the issue.

It could also just be that I'm tethering to the internet through my cell phone and that for some reason my connection that way is unable to connect to sourceforge, so if someone else can just try to wget [http://hplip.sourceforge.net/hplip_web.conf](http://hplip.sourceforge.net/hplip_web.conf) and let me know if it's just my connection that would be great...

---

### Post by dino99 on 2015-07-21
why trying to download from hp site ? Try the suggestions below:

[http://askubuntu.com/questions/575547/how-can-i-install-hp-laserjet-p1102w-on-ubuntu](http://askubuntu.com/questions/575547/how-can-i-install-hp-laserjet-p1102w-on-ubuntu)

---

### Post by Vladlenin5000 on 2015-07-21
post #2
+1

And no, the problem isn't on your side. If you opened the link you're trying to download from (or any other from SF) you'd notice this message:

> The sourceforge.net website is temporarily in static offline mode.
Only a very limited set of project pages are available until the main website returns to service.

---

### Post by neltnerb on 2015-07-21
Okay, thanks for the sanity check.

The linked page just does what I did (I suppose I did apt-get purge and then apt-get install instead), except they didn't fail because when it tries to download the proprietary plugin it had a valid link. Looks like I'll just have to wait until sourceforge works again.

---

