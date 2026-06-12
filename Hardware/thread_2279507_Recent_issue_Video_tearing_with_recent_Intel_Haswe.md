---
title: "Recent issue: Video tearing with recent Intel Haswell chip / Asus mobo: Solved?"
date: 2015-05-23
forum: Hardware
---

### Post by AFriendlyNerd on 2015-05-23
Hi

Recently I began to notice video tearing when using Kodi(xbmc). I thought it was a Kodi problem until I noticed it in VLC, only less pronounced.

Reading around, I found a fix for it (I think):

```
[COLOR=#333333][FONT=Roboto]!!!First install mesa utilitis if u dont have it!![/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]--------------Terminal------------------[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]*-----------[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]sudo apt-get install mesa-utils[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]----------------------------------------[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]*-------------[/FONT][/COLOR]

[COLOR=#333333][FONT=Roboto]To see what mesa and opengl version u have[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]--------------Terminal------------------[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]*---------[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]glxinfo | grep OpenGL[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]----------------------------------------[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]*----------[/FONT][/COLOR]

[COLOR=#333333][FONT=Roboto]Now to solve the video tearing [/FONT][/COLOR]

[COLOR=#333333][FONT=Roboto]-------------Terminal----------------[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]sudo mkdir /etc/X11/xorg.conf.d/[/FONT][/COLOR]


[COLOR=#333333][FONT=Roboto]echo -e 'Section "Device"\n Identifier "Intel Graphics"\n Driver "Intel"\n Option "AccelMethod" "sna"\n Option "TearFree" "true"\nEndSection' | sudo tee /etc/X11/xorg.conf.d/20-intel.conf[/FONT][/COLOR]

[COLOR=#333333][FONT=Roboto]sudo reboot[/FONT][/COLOR]




[COLOR=#333333][FONT=Roboto]----------------------------------------[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]*----------------[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]*"sudo reboot" will restart the pc!!!![/FONT][/COLOR]


[COLOR=#333333][FONT=Roboto]To revert back to the default acceleration method , just delete the file you created.[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]----------------------------Terminal----[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]*----------------------------------[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]sudo rm /etc/X11/xorg.conf.d/20-intel.conf[/FONT][/COLOR]

[COLOR=#333333][FONT=Roboto]sudo reboot[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]----------------------------------------[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]*---------------------------------------[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]*"sudo reboot" will restart the pc!!!![/FONT][/COLOR]
```

It appears to be resolved, but is there any drawback to this? Feels wrong going back to using a config file that is essentially deprecated, and there is a hint of performance issues here: [https://wiki.archlinux.org/index.php/Intel_graphics#Tear-free_video](https://wiki.archlinux.org/index.php/Intel_graphics#Tear-free_video) , although I'm not using this machine for games, only media playback.

I thought I would seek the guidance of the smartest guys in the room! Thank you for reading.

---

### Post by AFriendlyNerd on 2015-05-24
I've been informed that this fix introduces "triple buffering". Anyone have better advice?

---

