---
title: "Terminal screen not refreshing properly"
date: 2008-11-22
forum: General Help
---

### Post by supergrover1981 on 2008-11-22
Hi gang,

Just moved to a new laptop & a fresh Intrepid (64-bit) install, and I'm having a bit of a problem.

In the terminal - most noticably when using vim, the screen often doesn't refresh properly.

What I mean is, when I scroll down, often many lines will display the same (unscrolled) lines until edited, when it becomes clear there's something else there afterall.

I didn't have problems on my old PC - ran x386 8.10 on the old one, running AMD64 on the new.

Anyone run into this before? Any suggested solutions?

Cheers,
       - JB

---

### Post by Dr Small on 2008-11-22
Do you mean in a Virtual Terminal, or gnome-terminal/xterm ?

---

### Post by supergrover1981 on 2008-11-22
Hi Dr Small (great name), cheers for the response.

Gnome terminal 2.24.1.1. :-)

---

### Post by Dr Small on 2008-11-23
> **supergrover1981 said:**
> Hi Dr Small (great name), cheers for the response.

Gnome terminal 2.24.1.1. :-)
Please try with xterm to see if the problem persists. If it does, the problem could be deeper. If not, then you may need to try reinstalling gnome-terminal.

---

### Post by mem on 2008-11-24
I have noticed the same behavior running Intrepid 64 bit.

I do not believe this problem is limited to the terminal. I run Wing IDE as my python editor of choice and have noticed the same behavior in that app. I believe it uses GTK. Gnome-terminal does it, it becomes really apparent using something like irssi or vim.

I moved from 8.04 32 bit to a fresh install of 8.10 64 bit.

Not sure if it matters but i'm running the latest nvidia drives from the repos (177 i believe) on a 8600 (laptop - dell vostro 1500).

---

### Post by supergrover1981 on 2008-11-24
Mem - yep, further investigation shows the same problem here: first noticed it in vIM, but other windows have the problem also.

I'm also running the 177 NVIDIA drivers. Might be time to rollback to 173 by the looks of things...

---

### Post by supergrover1981 on 2008-11-24
Hi Dr Small,

After 5 minutes in xTerm I can't notice any problems, but it's inconsistent anyhow, so possibly just haven't caught it yet. Will let you know if I catch it in xTerm. :-)

---

### Post by supergrover1981 on 2008-11-25
Just a quick follow-up: I've reverted to Nvidia 173 drivers - after 30 mins in vIM, the problem *seems* to be resolved.

---

