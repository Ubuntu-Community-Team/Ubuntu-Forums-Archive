---
title: "[SOLVED] After uninstall of gufw message: Enter the password to perform administrativ"
date: 2008-10-03
forum: General Help
---

### Post by abcuser on 2008-10-03
Hi,
on Ubuntu 8.04 Desktop I have installed deb package of "gufw" ( GUI Firewall) from [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

I have tested it and decited to uninstall. So I uninstalled it from Synaptic using "Mark for Complete Removal".

I rebooted computer and login message still exists:
[img]http://shrani.si/f/3M/WS/YZxvM4F/gufw.jpg[/img]

I have checked out and file /usr/share/applications/gufw.desktop does not exist.

Any idea how to remove this login window when login in into Ubuntu.
Thanks,
Abcuser

---

### Post by gaiterin on 2008-10-03
Hi!
Sorry by this issue, you can remove "Firewall Configuration" file in your home/.config/autostart (Gnome).
or more easy, install Gufw, configure to not autostart, and uninstall Gufw.
Best regards.
Marcos Alvarez.

---

### Post by abcuser on 2008-10-05
Marcos,
thanks a lot. It looks like a little bug when gufw is uninstalled.

But I just misunderstood settings from Edit | Preferences | "Autostart with session". I though this autostarts the firewall, but as I see firewall is started after "Firewall enabled" button is pressed in main window. Now I have tested this in depth.

So "Autostart with session" is just a settings to let autostart the GUI of ufw which is just a settings I don't need at boot up - that is probably the case this settings is set to off by default.

Few days ago I just tried to uninstall Gufw because it was annoying to login after reboot. My mistake... But now I will keep this useful tool. I like it.

BTW, it would be nice to also have outgoing traffic control - now only there is only incoming traffic control.
Thanks,
Abcuser

---

### Post by gaiterin on 2008-10-05
Hi abcuser ;)

Yes, you really don't need to autostart Gufw. Gufw is just a settings tool for ufw (the real firewall), and they are split separate.

Think of Gufw as a settings dialog. After you do all of the changes and close it, the settings are still in effect (for example, when you setup a new printer - after you close the setup window, your printer setup still stays!).

So there is no need to add Gufw to auto-start, unless you're going to change your firewall settings very frequently. If you enable the firewall and close Gufw, the firewall will still be enabled, even after a reboot.

Best regards!

---

