---
title: "Trackpad not working after 14.04.1 update: Lenovo Yoga 11s"
date: 2014-07-31
forum: Hardware
---

### Post by adamsablich on 2014-07-31
Just reformatted my machine, Lenovo Yoga 11s. 
Tried to install with the 14.04.1 ISO, and realized the touchpad wasn't working, so I went back and used my original 14.04 ISO. 
Worked fine, until I did an apt-get update/upgrade.

Now, this happens, and it's reproducible every boot:
1) Boot the machine. Cursor appears before login, then disappears when login screen populates.
2) Log in. Cursor appears, then disappears before desktop populates.
3) During that time, touchpad is completely unresponsive - no buttons or movement work.
now, the weird part:
4) Suspend the laptop (close lid)
5) Resume laptop (open lid) - Touchpad works normally, like nothing was wrong. Until a reboot, then this process repeats.

The only thing I notice in Xorg.log is this:
[B](**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

[/B]I assume it's somehow recognizing the touchpad twice and disabling it the second time, but I don't know why.

I did also read the DebuggingTouchPad Ubuntu Writeup, but it doesn't actually suggest what I do once I've collected the data. As far as I can tell, my machine is recognizing the mouse just fine, but somehow disabling it just before login.

Any advice would be helpful. Thanks!

---

### Post by adamsablich on 2014-07-31
Additional note - USB mouse always works fine. It's only the touchpad that experiences this issue, and only since the 14.04.1 updates.

---

### Post by adamsablich on 2014-07-31
Fixed.

Realized that my brightness control keys weren't working (and neither were brightness settings under system settings). Researched this, and followed the directions from this post:

[http://askubuntu.com/questions/262003/how-do-i-get-brightness-working-on-a-lenovo-ideapad-yoga](http://askubuntu.com/questions/262003/how-do-i-get-brightness-working-on-a-lenovo-ideapad-yoga)

changing this in grub: [FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=vendor**"
and adding "[/FONT][COLOR=#333333][FONT=UbuntuRegular]*blacklist ideapad_laptop*"  to */*[/FONT][/COLOR][I][COLOR=#333333][FONT=UbuntuRegular]etc/modprobe.d/blacklist.conf 

[/FONT][/COLOR][/I][COLOR=#333333][FONT=UbuntuRegular]Apparently blackisting ideapad_laptop also turns off whatever was making the touchpad not function. All fixed now.[/FONT][/COLOR]

---

### Post by adamsablich on 2014-07-31
Goddamn it. 
But that also disables the ability to scroll chrome's browser using the touchscreen.
Get your **** together, Lenovo. I just want to use Ubuntu the way Shuttleworth intended.

---

### Post by adamsablich on 2014-08-01
Also fixed. 

Add [FONT=Ubuntu Mono]google-chrome --touch-devices=10

to the chrome launcher in /usr/share/applications, and this allows touch in chrome again.

Hooray workarounds.[/FONT]

---

### Post by moboticdes on 2014-12-28
Same problem after an update of Linux Mint 17 Cinnamon.

What I did was


[LIST=1]
[*]Add the acpi_backlight=vendor to the grub default command line by doing the following: 
[/LIST]
    
sudo gedit /etc/default/grub
  You will find this line in the new opened window:

  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
  
Change it to:

  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
  
Save and close the window. Then do the following:


[LIST=1]
[*]Run the update-grub command
[*]blacklist the ideapad_laptop by adding "blacklist ideapad_laptop" to your /etc/modprobe.d/blacklist.conf file.
[*]Reboot
[/LIST]

---

