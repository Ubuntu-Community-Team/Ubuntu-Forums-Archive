---
title: "Install KDE3.5 on Hardy"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by windyrij on 2009-07-01
I have been running Kubuntu Hardy. I use Kshowmail for checking and deleting email on the server, without downloading it.

Kshowmail can be installed on Kubuntu Hardy, as that uses the KDE3.5 desktop. Presumably, Kshowmail was written for KDE3.5.

I found that Kshowmail will not run properly on Jaunty, which uses KDE4 - when trying to access the server (refresh) you get an error message -
"Could not start process. Unable to create ioslave.
klauncher said: Unknown protocal 'POP3'."

I have just installed Ubuntu Hardy, as I prefer the Gnome desktop. Before anything else, I installed updates., as recommended I do not know if KDE3.5-desktop was there originally, but KDE4-desktop now shows up with Synaptic. No KDE3.5..

I installed Kshowmail from Synaptic in Hardy, but I get the same error message about the ioslave, as with Kubuntu Jaunty.

Am I correct in thinking that KDE 3.5 is the answer. If so, how do  I install KDE3.5-desktop?


Any help would be good. Thanks a lot

windyrij

---

### Post by windyrij on 2009-07-09
PROBLEM SOLVED!

On Ubuntu Hardy, you also need to install kdebase-kio-plugins, version 4:3.5.10.

I discovered this by checking the installed components on Kubuntu Hardy, using Synaptic (Gnome desktop installed as well as KDE), against Ubuntu Hardy.

I have not checked if this works for Jaunty Ubuntu.

Hope this helps someone else!

Kshowmail is really useful - no household should be without one!

windyrij

---

