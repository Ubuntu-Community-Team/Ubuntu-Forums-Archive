---
title: "Pidgin crashes after upgrade to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by AN@S on 2009-04-25
Hello, 

After I upgraded from 8.10 to 9.04, Pidgin crashes after 10 seconds of being started, I tried to run it from the command line and I got this message:

> Pidgin 2.5.3 has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

I tried reinstallation but still the same problem. Anyone having the same problem or knew the solution?

---

### Post by rippon on 2009-04-27
Most likely caused by a plugin.

Try installing libnotify.

```
sudo apt-get install libnotify-bin
```

---

### Post by AN@S on 2009-04-27
> **rippon said:**
> Most likely caused by a plugin.

Try installing libnotify.

```
sudo apt-get install libnotify-bin
```

Hi,

I've installed libnotify-bin but still have the same error. Is there a way to deactivate plugins without starting Pidgin?

:confused:

---

### Post by Bios Element on 2009-04-27
Yeah, Rename your /home/<username>/.purple folder to "purple" and it'll name a new config. That should work.

---

### Post by jonobr on 2009-05-07
Bios Element

THanks for this post, 
I ahd the same problem post upgrade, and confirm that when I did that move as you suggested, it worked great.

Also, for anyone reviewing this post, after the move your previous accounts settings are in ~/purple/accounts.xml

Thanks
.

---

### Post by bonevg on 2009-07-06
Well it keeps crashing
ICQ and MSN accounts.. Seems with ICQ only it works - when I add the MSN account it is fine.
And when I message one of the contacts it just dies.

[SOLUTION]
After checking the /var/log/messages I've found this:
```
Jul  6 15:27:04 gbonevpc kernel: [18633.628619] pidgin[18066]: segfault at b3462a50 ip b3462a50 sp b3f1b33c error 4 in libasound.so.2.0.0[b3473000+c3000]
```

Try to setup all settings to use alsa in "System > Preferences > Sound"

If you get similar error like this:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

Then use this in your home dir:
```
rm -f .asoundrc*
```

GL every1 :)

---

### Post by os56k on 2009-07-23
I suggest to download the latest version of pidgin from [http://pidgin.im/](http://pidgin.im/) and it may solve the problem.

---

### Post by xjgnsdof on 2009-08-07
> **Bios Element said:**
> Yeah, Rename your /home/<username>/.purple folder to "purple" and it'll name a new config. That should work.

This worked for me in 64-bit 9.04 Ubuntu.

---

