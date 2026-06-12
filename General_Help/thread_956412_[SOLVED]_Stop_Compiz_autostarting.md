---
title: "[SOLVED] Stop Compiz autostarting"
date: 2008-10-23
forum: General Help
---

### Post by Krydahl on 2008-10-23
Does anyone know how to do this?

I can't see anything that's starting compiz in ~/.config/autostart or /etc/xdg/autostart. Anyone know where the instruction to start compiz is hiding?

---

### Post by MaxIBoy on 2008-10-23
```
sudo apt-get install fusion-icon
```

After that, find the "sessions" dialog in the "system" menu, uncheck "compiz."

Fusion-icon can be dragged to a panel or the desktop. It will appear in the taskbar, and you will be able to use it to turn compiz on and off at will.

---

### Post by Krydahl on 2008-10-23
Hi, thanks for the reply.

It's not turning compiz on and off that's puzzling me, it's the fact that there isn't an entry in sessions - nor in any of the commandline places I'd look for an autostart instruction, so I'm confused over how it's starting.

---

### Post by MaxIBoy on 2008-10-23
Well, the only thing I can think of is to create a new entry under the session, with the following command:
```
sleep 5 && killall compiz && metacity --replace
```
That might work.

---

### Post by Krydahl on 2008-10-23
Yuk!

Yes, it probably would, but it's hardly elegant.

I guess I can install your icon and turn it off after boot (or do it manually from the command line), it just seems odd that I can't see what's starting it. Thanks for your suggestions though.

---

### Post by Therion on 2008-10-23
Open a Terminal and navigate to ~/.config/autostart and see if there is a compiz desktop file. 

If there is the following command should do the trick:```
rm ~/.config/autostart/*compiz*
```

---

### Post by Krydahl on 2008-10-23
Nope, that's where I looked first. There's also nothing in /etc/xdg/autostart, which is the other place these things can be started from that I know of.

---

### Post by MaxIBoy on 2008-10-23
> **Krydahl said:**
> Yuk!

Yes, it probably would, but it's hardly elegant.

I guess I can install your icon and turn it off after boot (or do it manually from the command line), it just seems odd that I can't see what's starting it. Thanks for your suggestions though.
Born to kludge! :)


If you set fusion-icon to start automatically, and make sure it's set to metacity before you shut off, that would work too.

---

### Post by Krydahl on 2008-10-24
I asked because I was about to install XFCE and wanted to be sure it wasn't going to try to run compiz when I started an XFCE session. I've now done this and it doesn't seem to be trying to start compiz, so it's not a big worry. If I start switching between gnome and Xfce a lot I might install the fusion icon. Till then, I shan't worry about it since it's not causing a problem. 

Thanks for the input.

---

### Post by MaxIBoy on 2008-10-24
All right. Glad I could help.

---

