---
title: "Upgrading to Breezy from Hoary"
date: 2005-11-07
forum: General Help
---

### Post by Warren on 2005-11-07
I want to upgrade to Breezy sometime soon, but will I have to do the same procedure as I did to install Hoary?  What I mean is that I want to just overwrite Hoary with Breezy so I won't lose my /home files and the packages I've installed.  Is that possible?

---

### Post by earobinson on 2005-11-07
You are looking for this
[http://www.ubuntuforums.org/showthread.php?t=85986&highlight=dist-upgrade+breezy](http://www.ubuntuforums.org/showthread.php?t=85986&highlight=dist-upgrade+breezy)
or [https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

---

### Post by lorenco on 2005-11-07
Well all you need to backup is /etc and /home (bar anything else you have data in)

Then do a clean install... I found a helpfull tip: Always have two partitions ready for linux , one for the current (in your case Hoary) version and one for new (breezy)

I upgraded doing this without troubles... Then you can copy the /etc/ and /home files (if you want)

---

### Post by earobinson on 2005-11-07
Ya i did more reading, a lot of people say you should do a cleen install.

---

### Post by Mustard on 2005-11-07
Upgrading to breezy is fairly simple and its not necessary that you lose your present user configurations.  Below I have included a wiki guide which will allow you to prepare for that upgrade.

[https://wiki.ubuntu.com/BreezyUpgrade]("https://wiki.ubuntu.com/BreezyUpgrade")

-edit-

Hehehe..one minute there was no reply and by the time I posted I am five posts down.  Sorry for the repeat information.

-edit2-

Looking over the guide above, I would say they wiki entry is a little more comprehensive in its coverage.

---

### Post by earobinson on 2005-11-07
better that than nothing :)

---

### Post by Warren on 2005-11-11
Looks good.  I copied the URL to my reminders file, and I'll give it a good looking-through probably around Thanksgiving when I have some time off from school.  Thanks a lot, everyone.

---

### Post by fei on 2005-11-11
I just got the 5.10 CD today. And looking for docs about how to upgrade from Hoary to Breezy. I have a lot personalized settings. It would take me to too much time to do a clean install. But I know that upgrading is not safe, might cause problem.

It need to read this thread carefully first before taking any action.

---

### Post by Zwack on 2005-11-12
[QUOTE=fei]I just got the 5.10 CD today. And looking for docs about how to upgrade from Hoary to Breezy. I have a lot personalized settings. It would take me to too much time to do a clean install. But I know that upgrading is not safe, might cause problem.[/QUOTE]

I tried two things... Both worked...

1) just put the 5.10 CD in while Hoary is running and select the automatic update option.  It seemed to work, but gave me a slightly different end result than...

2) Backup /home and install from Cd, then restore /home...  Then I had to fix some, now incorrect, personalisations.

I hope that this helps,

Z.

---

