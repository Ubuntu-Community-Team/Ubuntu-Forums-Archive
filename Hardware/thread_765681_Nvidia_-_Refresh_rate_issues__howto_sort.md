---
title: "Nvidia - Refresh rate issues : howto sort"
date: 2008-04-24
forum: Hardware
---

### Post by interzoneuk on 2008-04-24
Hi.

I have just installed Ubuntu 8.04.

I have to say its better than the previous versions (however I wish KDE was the main desktop...:KS)

I had an issue getting the correct refresh rates after installing the nvidia driver, but have sorted it using the nvidia-settings tool.

Here is how I fixed the refresh rate for me...

---------------------------------------------------

(it is a really good idea to backup /etc/X11/xorg.conf first)..

I used the restricted driver to install nvidia driver (on geforce 8500)

My monitor has a max resolution of 2048 x 1536 and after installing the nvidia-new driver (and rebooting) it went to the max resolution.

I used the gnome -> preferences -> screen resolution menu to change the resolution to 1600x1200 - however the refresh rate options were odd - I could choose a range of 51-58 Hz - I should be able to get 85 Hz on my monitor..

I then installed the nvidia-settings package using the commands:-

[SIZE="2"][I]
sudo apt-get update
sudo apt-get install nvidia-settings[/I][/SIZE]

Then launch it using

*[SIZE="2"]sudo nvidia-settings[/SIZE]*

click on X Server Display Configuration

- choose your correct resolution and refresh rath
- click apply

If all is O.K (i.e the correct refresh rate) then click 'Save to X configuration File' and write over /etc/X11/xorg.conf

(note - it should backup your original xorg conf file to /etc/X11/xorg.conf.backup )

---

