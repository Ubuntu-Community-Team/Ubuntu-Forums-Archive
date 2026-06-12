---
title: "screen won't resume after it goes blank"
date: 2008-05-11
forum: Hardware
---

### Post by jellylogix on 2008-05-11
i have a HP dv6000 laptop with Ubuntu 8.04 installed. Its also dual booted with Vista, but ubuntu works "fine" on its own.

The problem that i am having is that when my screen saver goes on I CAN resume when i wiggle the mouse (as it should)... but if i wait longer, then eventually the screen will go blank (like its sleeping or something)... anyways when i try wiggling the mouse, i hear no difference in the hard drive activity or the computer itself trying to do something. I even tried hitting keys on the keyboard, but nothing seems to work on getting this to resume out of its "trance"... any suggestions?

The way i have been "fixing it" is by simply holding down the power button until it hard shuts down.

---

### Post by pro003 on 2008-05-11
did you checked "lock screen when screensaver is active" ?

---

### Post by jellylogix on 2008-05-11
no its not checked... but i can't even see if anything is physically locked... its just not responding or something

---

### Post by jeromio on 2008-05-13
I have this same problem on a Compaq v6000. This system worked fine in 7.04. In 8.04, if the screen goes to "sleep", it never comes back. The back light is on though. Just stays blank. I installed SSH, so I can log in to it remotely. The last entry in Xorg.0.log is SetGrabKeysstate - disabled.

I noted that the screen saver was running, killing that didn't help me. Looks like Xorg died? But why would the system not drop back to the prompt?

I am running the proprietary Nvidia graphics driver - same one I used on this system for 7.04.

---

### Post by llama320 on 2008-05-13
I had the same problem. First of all, can you access your virtual terminals (ctrl-alt-F#)?

If you get just a blank screen where your virtual terminals should be, then it's probably a problem with the nvidia driver (assuming your HP is using nvidia)

Now, I'm also assuming you're using nvidia-glx-new as the driver right now. If you don't care about compiz working, then nvidia-glx will probably remedy this problem.

To get compiz working, though, what I had to do was manually install nvidia driver 100.14.23..it's kind of old but it works

here's the thread I made for this problem, hope it helps
[http://ubuntuforums.org/showthread.php?t=780996](http://ubuntuforums.org/showthread.php?t=780996)

---

### Post by jeromio on 2008-05-13
> **llama320 said:**
> I had the same problem. First of all, can you access your virtual terminals (ctrl-alt-F#)?YEs! Except I didn't have any other sessions active. But hitting ctrl-alt-f6 lit up the screen with the screen saver. Very odd. I read the thread you referenced> 
[http://ubuntuforums.org/showthread.php?t=780996](http://ubuntuforums.org/showthread.php?t=780996)but I'm not sure what this has to do with it? I do have the latest nvidia proprietary driver.

But, at least I have a work-around. Thank you.

---

