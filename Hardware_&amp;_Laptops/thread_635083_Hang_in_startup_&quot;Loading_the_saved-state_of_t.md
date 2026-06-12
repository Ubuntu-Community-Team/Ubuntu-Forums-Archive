---
title: "Hang in startup: &quot;Loading the saved-state of the serial devices&quot;"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by vemon on 2007-12-08
Hi!

My Ubuntu Gutsy randomly hangs in the startup with the "Loading the saved-state of the serial devices" as the last startup msg displayed. Actually it doesn't go straight to the text mode but first stays about 30secs in the splash/progress display with the progress bar freezed.

The problem with debugging this problem is that the hangs are random (about one hang in ten boots). It doesn't sound very tempting to unplug one device, boot 10+ times and do the same again until the faulty/guilty device is found.

I have some doubts about the problem lying either in my PCI DVB card or my self built ir serial receiver.

Please share your knowledge on the subject :)

Here are some similar threads that I've already found:

[http://www.mepis.org/node/806](http://www.mepis.org/node/806)
[http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg07080.html](http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg07080.html)

Attached are my lspci & /proc/cpuinfo (yes, I'm using cpufreq).

---

### Post by dea.dB.ear on 2008-05-29
I have this same problem.

On hardy, with a T60 lenovo....

but every boot, and only using the -rt kernel (the newest, 2.6.24.18,  i think).

everything works fine on the generic kernel.

If i ctrl-alt-del at the hang. I get:

init: rcS (2545) main process killed by term signal
      
init: rc6 (4658) main process killed by term signal  //that smily is an 8 and a paren..............

and it goes to a terminal login and hangs when starting 'cupsd'.

Now, if I press alt-f4 on the first hang, the screen clears and hangs until i press ctrl-alt-del, giving me the above process killed messages, and it goes to terminal login.   When I begin to type a login, the boot continues....   succeeding at reaching the ubuntu login ~1 out of 4 times.

the rest of the time it restarts.

when I do get into the OS it is a little buggy and my comp runs hot.  But all the ubuntu studio software works much better.  I suspect this is pretty normal, but I havent had a chance to play or fix it because this is my only experience with -rt.

As a linux newbie, I have figured out the above through the power of mashing so any help would be great.....

Thanks

UPDATE:  When the boot checks the hard-drive and I skip the check...  everything works fine................  hmmmm........

---

