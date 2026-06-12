---
title: "Wine behaves irrationally"
date: 2005-11-16
forum: General Help
---

### Post by Troop on 2005-11-16
I know this is really a question for somebody at the WINE site, but i reckon that I can use any help I can get. Obviously, I'm an Ubuntu user - and somewhat unexperienced when it comes to Linux/Unix - so maybe what seems obvious to some of you is hidden in clouds to me.

I've installed Wine from "http://wine.sourceforge.net/apt/ binary/", using the "apt-get install wine"-command, followed by WineTools which i downloaded with my browser and installed using instructions from it's corresponding website. I've run WineTools, and successfully created a fake windows drive. The next recommended step was to install the Arial font through the same program. As the URL it uses seems to be a little "out of date" I manually downloaded the arial32.exe-file which I made the program use. Wine seemed to run it without any complications - and I was thrown into a small Windows installer which seemed to work properly. However, no file is yet to be seen in the font folder of the virtual drive (.../drive_c/windows/fonts/). I thought this is maybe not a problem, as the font is maybe only visible "through wine for the win applications" - so I continued to the next step, which is to install "DCOM98". I have absolutely no idea what that does, but apparently I had to install it in order to have IE6 later on. Once again the installer was launched flawlessly, but it failed to identify my windows system as win98 (which obviously was required for the installation to be completed). So i launched "winecfg" and configured wine so that it should emulate win98 for the dcom.exe file, and tried to run it again. Without success. It still thinks I'm running an NT system. Please help me. I'm stuck!

Pardon my crappy english...

---

### Post by Troop on 2005-11-16
I've solved this using the infamous sidenet installer. No need to worry.

---

