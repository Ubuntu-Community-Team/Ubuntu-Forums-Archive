---
title: "Sound stops working"
date: 2008-11-10
forum: General Help
---

### Post by Chewie8 on 2008-11-10
Hi all,
   I recently upgraded from Hardy Heron to Intrepid Ibex, and I've run into a little problem.  If I let my computer sit for a day or so without using it, it will not emit any sound.  Music, movies, or system sounds do not work.  If I restart my computer, than the sound instantly works again.  I have not had a great deal of time to narrow down the problem anymore.  Thanks for your help!

---

### Post by Chewie8 on 2008-11-10
Is there anyone that can help me?

---

### Post by ubun_two on 2008-11-10
> **Chewie8 said:**
> Is there anyone that can help me?

You might want to wait more than 35 minutes...:-D

I haven't had the problem you are having, but the pulseaudio in Intrepid/Hardy is known to be problematic, and it could be causing the issue.

You should look at the log when this happens and see if there is any error message.  That might help narrowing down the problem.

If it is the pulseaudio that's causing the issue, you might consider uninstalling it to use ALSA instead.

---

### Post by rudy.elgato on 2008-11-10
Several people have reported losing sound after resuming from a suspend/hibernate.  If this is what's happening to you, have a look at [http://ubuntuforums.org/showthread.php?t=965340]("http://ubuntuforums.org/showthread.php?t=965340").

Good luck...

---

