---
title: "Ubuntu 5.10 GUI down"
date: 2005-11-21
forum: General Help
---

### Post by skalsky on 2005-11-21
Hi.. i'm new to linux and Ubuntu, and tried to activate the Nvidia drivers for GeForce2 Pro by following already a lot of posts on different forums, but haven't succeeded in configuring direct rendering.. finally found a thread about a ready solution in ubuntu menu->system->help then i think the last choice.. and access the solution from "hardware" link on the left. The soution said to create a new file nvidia_dont remember the rest.. .and to insert the lines indicated by help. And so I did.. then it told me to restart gnome.. and so I did. But gnome did not restart.. instead I got the terminal. I tried to run the same command as before (gedit to the nvidia_something file that I created) to remove the file.. but couldn't access it. i rebooted the system but I get the ubuntu loading screen, and then the terminal appears asking me to login. GUI does not start.. how can I fix this error? Anybody have an idea? Thanks in advance..

Skalsky

---

### Post by skalsky on 2005-11-22
Well.. I've managed to get to the problem and to fix it by myself.. but just in case...

1. The problem was with the file "NVIDIA-settings.desktop" located in "/usr/share/applications". I deleted the file from the terminal.

2. Because the system still did not start the "X server" I restored the backed up "xorg.conf" file.

3. GUI starts :)


Oh yeah... sorry for posting a stupid newbie problem like this on the forum.. I didn't mean to waste your time ;)

Cheers!

Skalsky

---

