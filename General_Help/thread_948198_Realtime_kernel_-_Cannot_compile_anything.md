---
title: "Realtime kernel - Cannot compile anything"
date: 2008-10-15
forum: General Help
---

### Post by _godbout_ on 2008-10-15
Hi there!

I used to had Ubuntu 8.04 on my laptop, everything was running perfectly. Then I removed it to fully use it for audio production and installed Ubuntu Studio. Now, I can't make my wireless works and neither install the nvidia drivers. Each time I try to compile, I've got this message telling me that the blablabla.../build is missing. 
I've tried to install the linux-source, development, headers, I can't make it.

Any help?

Thanks,

---

### Post by _godbout_ on 2008-10-15
I've destroyed my installation. Nothing is working correctly, neither the video nor the wireless. Amazing. Hardy worked pretty well. Seems that this Studio is catastrophic.

---

### Post by jespdj on 2008-10-15
To be able to compile software you need to install the package **build-essential**.

---

### Post by _godbout_ on 2008-10-22
The build-essential package was installed already, but the linux-headers for the realtime kernel not. Thanks for the tip anyway!
I've compiled the madwifi patched drivers, seems to work. But I've got problems with the nvidia drivers and my touchpad, the xorg file seems to be completely rubbish...

This version is very shitty. The 32bits works better than the 64bits, but still, impossible to have a common nvidia card working? And the touchpad? I worked on it for a week now, has never been so painful and rubbish.

Why does the synaptic disappears from the Studio xorg.conf? Everything worked fine in Hardy :-/

---

