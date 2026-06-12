---
title: "Lenovo W540 Bluetooth adapter"
date: 2014-10-31
forum: Hardware
---

### Post by jurgen32 on 2014-10-31
I have Kubuntu 14.10 installed on my Lenovo W540.
When I tried to enable my bluetooth I received the message that no adapter could be found.

The (graphical) solution was to install Kusers.
Open Kusers (system/kusers) and give your password.
Open your user (jurgen in my case).
Go to 'groups' and tick bluetooth.
Press OK, close all and reboot.

Now bluetooth should be there.

I belief the commandline method is this:
sudo useradd -G {bluetooth} username

So, I already solved my thread but I thought it would be handy for other users as well.

---

