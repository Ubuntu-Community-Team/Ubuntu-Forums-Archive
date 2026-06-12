---
title: "Touchpad Settings Will Not Keep"
date: 2012-06-02
forum: Hardware
---

### Post by raptir on 2012-06-02
I'm running Ubuntu 12.04 on an HP dm1-4170us. While I was running Xubuntu, I had no trouble getting my synaptics touchpad settings to stick. I edited /usr/share/X11/xorg.conf.d/50-synaptics.conf with the settings I wanted (specifically setting tapbutton2=2 and tapbutton3=3) and saved the copy as 60-synaptics.conf in /etc/X11/xorg.conf.d. Now that I have switched to Ubuntu, this is not working. Does anyone have any experience with making the settings permanent in Ubuntu? I have tried the following:

[LIST]
[*]Renaming the Identifier in my custom settings file to make sure it was loading properly. fgrep InputClass /var/log/Xorg.0.log confirmed that it was loading my configuration file after everything except the "touchpad ignore duplicates" device, but my settings were not sticking.
[*]Adding terminal commands to /etc/rc.local to set the options directly in synclient.
[*]Creating a new script with the line "synclient tapbutton2=2 tapbutton3=3" and adding this to the Unity Startup Applications
[*]Editing /usr/share/X11/xorg.conf.d/50-synaptics.conf directly to include the options I wanted
[/LIST]

I know that the first and last methods worked for me in Xubuntu but are not working in Ubuntu. My best guess is that something with Unity/Gnome is resetting the touchpad settings after all of my config files/scripts are loaded. I'd greatly appreciate any help, and let me know if I can provide some more information.

EDIT: I found a solution but I am currently out and posting from my phone. I'll post it here for others later.

---

### Post by raptir on 2012-06-03
Alright, it seems the problem was that the Gnome touchpad settings were overriding the settings I defined in the config file, even ones that cannot be set through the gnome tocuhpad settings. The workaround is to disable the gnome mouse settings plugin.

[LIST=1]
[*]Install dconf-editor through your favorite package manager (*sudo apt-get install dconf-editor* from the terminal)
[*]Launch dconf-editor
[*]Navigate the tree to org.gnome.settings-daemon.plugins.mouse and uncheck the *Active* box
[/LIST]

The only problem with the workaround is that no settings you configure in System Settings -> Mouse and Touchpad will not be effective, so you have to make any changes you want by editing /usr/share/X11/xorg.conf.d/50-synaptics.conf.

EDIT: Also, since marking the thread SOLVED removed the [Ubuntu] tag, please note that this problem only occurs when running Gnome/Unity in Ubuntu. This should not occur in KDE, XFCE, Lxde, etc...

---

