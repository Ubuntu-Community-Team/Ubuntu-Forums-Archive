---
title: "Monitor not detected in Ubuntu 10.10"
date: 2010-10-22
forum: Hardware
---

### Post by wrenchy54110 on 2010-10-22
After installing Ubuntu 10.10 I had problems getting my monitor to its native resolution.  The monitor was not detected and I was getting extremely frustrated.  I combed through these forums and Google searches for days.  I finally figured out the EDID data was from the monitor wasn't being read by the graphics card.  I was able to track it down to a cheap VGA cable that didn't allow the data to transfer.  I replaced it with a newer/higher quality cable and it fixed it.  Perfect. 

I know this probably isn't the fix for all the resolution problems and monitor detection problems out there, but I hope it helps someone else.  

I am fully enjoying my new install now.  

Good Luck....:guitar:

---

### Post by Phil Usher on 2011-01-18
Thanks for posting this.  It helped me work out my own problem.  

My "Monitor not detected" problem was due to my use of a KVM switch.  Using remote desktop I restarted the machine and Ubuntu couldn't detect the monitor because the switch pointed to another machine.  Physically changing the KVM switch to allow connection between the computer and monitor allowed Ubuntu to "see" the monitor.

I expect there is a workaround to my problem by forcing resolutions into the setup but my Linux knowledge isn't up to that challenge.

---

### Post by Fozzy-Bear on 2011-04-06
Hi,

I created this account so I could post and say thank you, this problem has been driving me up the wall for a few days now until I came accross your post and changed the VGA cable, which fixed the problem!!

Thanks for posting this info!

---

### Post by wondu on 2011-08-14
wow! this posting totally saved me a whole bunch of trouble. I have dual monitors and they were both working OK until some time last night when my system stopped detecting the second monitor. I was scratching my head trying to figure out what the problem is but with no success. Then I saw this posting, changed the cable and I'm back in business! Thanks for the post!

---

