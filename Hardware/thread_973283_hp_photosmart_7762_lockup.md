---
title: "hp photosmart 7762 lockup"
date: 2008-11-06
forum: Hardware
---

### Post by tomkatt on 2008-11-06
In Hardy my hp photosmart 7762 frequently locks up after printing one or two jobs. I often get an error message saying 'paper jam' but there is no jam. Powering off and on always wakes up the printer again. No problems when using my Windows partition.

---

### Post by Tim Watson on 2008-11-06
I seem to remember the same problem reported by someone some time ago. If you're dual booting, does it work OK under Windows XP (just checking - I assume that's what you mean by 'Windows partition')?

Tim.

---

### Post by Tim Watson on 2008-11-06
I found the thread:

[http://ubuntuforums.org/showthread.php?t=872551](http://ubuntuforums.org/showthread.php?t=872551)

Several people have the same problem with the 7260 model. Someone on that thread posted to the following launchpad thread:

[https://answers.launchpad.net/hplip/+question/38687](https://answers.launchpad.net/hplip/+question/38687)

but that question expired because the information that the printer worked under Windows wasn't supplied  - it looks like someone thought it might be a hardware problem but your problem suggests that it isn't.

If anyone has any further information or similar problems to show that this is a significant issue then that would be very useful to know about.

Sorry I can't be of more help,

Tim.

---

### Post by tomkatt on 2008-11-07
Yes it works under windows. Is suggestion to update hplip worth trying? How do I find which version I have? tomkatt

---

### Post by Tim Watson on 2008-11-07
Updating hplip will probably not help. If you installed it using apt-get at the commandline, or synaptic package manager from the System->Administration menu then you will have the latest package - I wouldn't advise grabbing a later version from the hplip site unless you're quite comfortable with building and installing software. 

If no-one else in these forums has any suggestions then you might try contacting the hplip developers directly and asking for advice.

All the best,

Tim.

---

### Post by pedrogfrancisco on 2010-02-01
See workaround at: [https://answers.launchpad.net/hplip/+question/98527](https://answers.launchpad.net/hplip/+question/98527)

---

