---
title: "Login no longer works."
date: 2008-10-29
forum: General Help
---

### Post by NeuB27 on 2008-10-29
I recently downloaded some sound drivers for my motherboard from the ASUS website that were stated as being for Linux, after trying to install them, and their failing, I now cannot log into Ubuntu. Whenever I try to, I am immediately logged out, the error states that linsound.so.2 cannot be found in usr/bin/seahorse-agent. I'm not sure what that means. I tried to start in recovery mode, and none of the options there helped. Is there any way to undo the changes that were made to the system, and get back to a functioning environment? Thanks in advance for any help.

---

### Post by wolfen69 on 2008-10-29
try ```
sudo apt-get install gdm
```

---

### Post by NeuB27 on 2008-10-29
I can only access the root prompt, and I use a wireless card to access the internet. The root prompt, from when you start in recovery mode, doesn't start the nmapplet to set up the network, is there a way to connect without that, using only the limited things loaded in recovery mode? I've checked at the root prompt and the ndiswrapper stuff is still setup, but ifconfig doesn't list anything but local area connection. Or is there some way to use nonetdebs to accomplish the apt-get install gdm?

---

