---
title: "Trouble with Laptop Display - Dell XPS M1530 - Nvidia 8400M GS"
date: 2012-05-05
forum: Hardware
---

### Post by stev067 on 2012-05-05
I recently built a new desktop PC, and decided to install Ubuntu 12.04 64-bit on my old laptop. I've had older versions of Ubuntu installed on it before, years ago. During boot, my laptop display shows the purple screen with ubuntu logo perfectly. But when it gets to the desktop, my laptop screen goes white and stays that way. My desktop will show perfectly on my external display if I plug that in.
So I went into the display settings, and the only available resolution for my laptop display is 800x600 or something like that. The screen is 1280x800. To the best of my knowledge, I have the latest nvidia driver installed. I've run updates for a few days hoping it would get fixed, but maybe there is something I can do to fix it. Does anyone know how to help me troubleshoot this?

---

### Post by kc1di on 2012-05-05
There is indeed a problem with the Nvidia drivers in 12.04. here's the work around for now.  This may or may not be the problem with your's.

Go to system system settings >additional drivers if nvidia propitiatory drive is installed uninstall it.  reboot and see it your monitor will work. 

This thread gives a description of the problem. [http://ubuntuforums.org/showthread.php?t=1971463]("http://ubuntuforums.org/showthread.php?t=1971463")

---

### Post by stev067 on 2012-05-05
Thanks for the response! I stumbled upon this in a recent thread, and it seems to have fixed the problem:

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

---

### Post by kc1di on 2012-05-05
> **stev067 said:**
> Thanks for the response! I stumbled upon this in a recent thread, and it seems to have fixed the problem:

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

Glad you got it :)

---

