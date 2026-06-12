---
title: "N110 Sound - Nothing But Crackles"
date: 2009-07-18
forum: Hardware
---

### Post by elewton on 2009-07-18
Good day.
I've been installing Ubuntu on anyone's computer who'll let me.
I installed Ubuntu on my friend's computer and he's loving it.
Everything was working perfectly last night.  We left it copying his files to the hard drive.

This morning, Ubuntu can only make a clicking noise when playing audio.
I created a new account.  It does the same thing.
If I boot using my Ubuntu USB key, the sound works fine.
I've been using the Ubuntu test sound instead of music, to avoid codec issues.
The Laptop is not connected to a network.
It's a little embarrassing, because XP is working perfectly.

dmesg | tail says nothing useful.

Any advice would be much appreciated,
Thank you.

---

### Post by elewton on 2009-07-18
As is often the case, my own post gave my new search terms which led me to the answer.
The PCM mixer volume had switched itself to 0.

I guess this is an ALSA bug?

---

### Post by ibuclaw on 2009-07-19
> **elewton said:**
> As is often the case, my own post gave my new search terms which led me to the answer.
The PCM mixer volume had switched itself to 0.

I guess this is an ALSA bug?

Yes, that is a bug. I can confirm it on my HP Pavillion Laptop as of about a month ago. (I'll try it on my Netbook in a minute).

Just a quick question, does the Mute Button work as expected? Or does it too send the speakers into a Crackle?

If so, I have written a (little known) workaround. [http://ubuntuforums.org/showthread.php?t=1182152](http://ubuntuforums.org/showthread.php?t=1182152)


Regards
Iain

---

