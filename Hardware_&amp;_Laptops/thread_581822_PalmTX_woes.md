---
title: "PalmTX woes"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Paul_Whelan on 2007-10-19
I had to hard-reset my PalmTX today but wasn't too worried due to the fact that I backup regularly as part of synchronising.

After many attempts I couldn't restore the device using the pilot applet so decided to re-install my apps and re-sync with evolution.

The only problem is that I cannot even install any of my apps.

I have tried dragging and dropping the app onto the pilot applet and that didn't work so I decided to use gpilot-install-file that to see if I get any sort of messages to help diagnose the problem.

Running the command and pressing hotsync on the TX gives the following:

paul@ubuntu-desktop:~/Desktop/palm$ gpilot-install-file --now SecurityPnl_enUS.prc 
gpilotd-Message: Activating object OAFIID:GNOME_Pilot_Daemon

nd nothing else. 

I can see messages on the TX screen saying that it has connected, and that it is synchronising the app but it never ends. 

I should mention that I stopped pilot applet and any related tasks before running gpilot-install-file

I am running an up to date copy of 64bit Feisty.

Any help would be appreciated.

---

