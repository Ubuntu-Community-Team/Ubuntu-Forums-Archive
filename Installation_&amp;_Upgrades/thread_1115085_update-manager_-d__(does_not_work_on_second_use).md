---
title: "update-manager -d  (does not work on second use)"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by cpbl on 2009-04-03
I ran update-manager -d from 8.10 to install 9.04beta.  After partly downloading the files, I interrupted the process. It had not started any installs, and subsequent normal updates seem to be working properly for 8.10 still.

However, now when I try 
update-manager -d
again, I get no mention of 9.04.

Anyone know what do I need to reset? Is this a bug?
(The downloading of update files should really be more separable from starting to install them).

Thanks!

Chris

---

### Post by cariboo on 2009-04-03
You probably won't  get any results, as the /etc/apt/sources.list has been change to download from the Jaunty repositories  already. Open a termianl and type:

```
sudo apt-get install -f
```

to see if the upgrade will continue, if that doesn't work in the same terminal type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Jim

---

### Post by NoobBiscUiT on 2009-04-03
neither of those commands worked for me.

did they shut down the sources for a 9.04 distribution upgrade?

---

### Post by Pasdar on 2009-04-03
Not available anymore it seems.

---

### Post by Jellyffs on 2009-04-03
Same here...

---

### Post by karlr42 on 2009-04-03
This was discussed on the ubuntu-devel mailing list:
> Message: 3
Date: Fri, 3 Apr 2009 11:59:00 +0200
From: Michael Vogt <michael.vogt@ubuntu.com>
Subject: Upgrades from intrepid to jaunty temporally disabled
To: Ubuntu Devel <ubuntu-devel@lists.ubuntu.com>
Message-ID: <20090403095900.GC19398@tas>
Content-Type: text/plain; charset=us-ascii

Hi,

I disabled the upgrades from intrepid to jaunty via the release
upgrader temporarlly. The rational is bug #354228 that hits everybody
doing a release upgrade.

The problem is that when python2.6-minimal gets install the rtinstall
scripts get run. Those scripts are designed to byte-compile files for
the new python runtime just installed (used by python-support and
python-central, among others). There was a bug that prevents those
scripts from being run (and some python modules were not available for
python2.6 because of this bug).

This bug got fixed yesterday. But the fix trigger the bug mentioned
above in python-central (#354228) and it affects every upgrade from
intrepid to jaunty. The fix is being worked on and the upgrade should
be available again by the end of the day.

Cheers,
 Michael

---

### Post by NoobBiscUiT on 2009-04-03
ok cool, that's what i like to hear.

---

### Post by NoobBiscUiT on 2009-04-03
It's working now!

woo!

thanks guys

---

### Post by euriconeto on 2009-04-04
Hi Everyone,

I'm a very new ubuntu user and would like to receive some (very detailed) help on how to upgrade my 8.10 as this seems to be the only way for me to be able to use my mobile broadband (since with 8.10 my USB modem ZTE627 don't work).

Anyone with patience available for the task? I would really appreciate that as I can't wait 2 weeks to have access... 

Thanx
Eurico

---

### Post by Pasdar on 2009-04-04
> **euriconeto said:**
> Hi Everyone,

I'm a very new ubuntu user and would like to receive some (very detailed) help on how to upgrade my 8.10 as this seems to be the only way for me to be able to use my mobile broadband (since with 8.10 my USB modem ZTE627 don't work).

Anyone with patience available for the task? I would really appreciate that as I can't wait 2 weeks to have access... 

Thanx
Eurico

Press ALT+ F2 and a run screen will start, then type this in it: update-manager -d

A new windows will jump up and at the top you click "UPGRADE".

---

