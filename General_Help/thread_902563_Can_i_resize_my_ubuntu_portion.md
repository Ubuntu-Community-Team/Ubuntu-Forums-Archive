---
title: "Can i resize my ubuntu portion?"
date: 2008-08-27
forum: General Help
---

### Post by dragos240 on 2008-08-27
I set up 6 gb for my ubuntu portion, and now i've decided to max it out to 20gb. Any way i can change it? General discussion sent me here since i installed from windows.

---

### Post by moycano on 2008-08-27
Sorry if I didn't answer your question -I'm quite a newbie- but also I'll like to ask how could remove/disable the swap under loopmounted filesystem (wubi/lubi).

On typical setup is as easy as run gpart(/ed, I can't remember and I'm not in my PC right now), made "swapoff", and delete it.

---

### Post by jerome1232 on 2008-08-27
> **moycano said:**
> Sorry if I didn't answer your question -I'm quite a newbie- but also I'll like to ask how could remove/disable the swap under loopmounted filesystem (wubi/lubi).

On typical setup is as easy as run gpart(/ed, I can't remember and I'm not in my PC right now), made "swapoff", and delete it.

You should really start you own thread instead of hijacking his


@dragos did you see the link I sent in your other post,  [http://ubuntuforums.org/showthread.php?t=901715](http://ubuntuforums.org/showthread.php?t=901715)

I think the easiest solution is to migrate out a partition

Did you install alot of programs and fill up /usr or do you have alot of picuters and music filling up /home?

You should be able to use disk usage analyzer to figure out where all your space is going, post a screenshot of it if you want.

You could migrate out /home into it's own 10 GB partition or /usr out to a 4 GB or so depending on your needs and where your getting filled up at.

Feel free to ask more questions if your unsure about something.

---

