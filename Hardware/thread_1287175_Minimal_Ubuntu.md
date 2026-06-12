---
title: "Minimal Ubuntu"
date: 2009-10-09
forum: Hardware
---

### Post by Spigon on 2009-10-09
I hate how Ubuntu is at the moment. Like most people I would like to be able to customize thier distros but also have ease of use. Meaning I would like to have no extra packaged and to be able to install my own file manager, windows manager, boot manager, and ect. However the only options I know of that allows the user to do this is installing ubuntu server edition or the minimal cd. Both of which however does require internet to set up. So my question is, is there anyway to wipe the desktop editions configuration to allow me to set ubuntu up the way I want; while keeping my ability to go wifi and my nvidia graphic driver. Thanks for any and all help that may follow.

---

### Post by slakkie on 2009-10-09
Sure, remove packages you don't want and keep an eye open with what you remove so you don't remove important system files.

---

### Post by mikewhatever on 2009-10-09
Use an alternate cd, hit f4 at the menu screen and select minimal installation. You will, however, need internet connection after thhe minimal system is installed, cause there are tons of window managers and it's impractical to put them all on cd.

I don't think wiping the desktop is a good idea, though removing some packages should be ok.

---

### Post by wojox on 2009-10-09
You don't have an Ethernet cable you could plug into temporarily ?

---

### Post by Spigon on 2009-10-09
Ya I do but the problem no cd that make minimal ubuntu easy supports wifi connections.

---

### Post by kerry_s on 2009-10-09
> **Spigon said:**
> Ya I do but the problem no cd that make minimal ubuntu easy supports wifi connections.

really? it doesn't give you a option to select the device after "detect network devices" stage?
is your wifi supported by the kernel or do you have to grab firmware?

i haven't done a ubuntu minimal in a while, but i was going to do one sometime next week. in the past the ubuntu used the same cli installer as debian, with a few changes to make it ubuntu. now i'm not sure if i should bother. :(

when i did my debian custom install(net install) over wireless, i just select it, the next window asks for the name, then it asks for the password.

---

### Post by Dark_Stang on 2009-10-09
> **Spigon said:**
> Ya I do but the problem no cd that make minimal ubuntu easy supports wifi connections.

So after you get your GUI going and synaptic installed, just install a network manager. I start with Ubuntu minimal and I'm running on a laptop. I just installed network-manager on top of gnome-core.

---

### Post by Spigon on 2009-10-09
Yea but the whole network-manager installed with gnome core defeats my purpose. I don't want gnome anything lol. I just want a ubuntu that has icewm, slim log-in manager, xfe/pcman/thunar file manager (still choosing), and swiftweseal with my nvidia driver and wifi access.

---

### Post by ikisham on 2009-10-09
Maybe you could try Wicd? It's in the repos (wicd).

---

### Post by Dark_Stang on 2009-10-09
Okay, so install a different network manager. Wicd Network Manager has no gnome reliance, so that might do what you want. Search google, your repositories, or sourceforge for others.

---

### Post by Spigon on 2009-10-09
I tried that, I may have messed up but could you tell me how to get it to start up and where it is at. I installed it from the repos and restarted my computer but couldn't find it afterwatds.

---

### Post by P1umb3r on 2009-10-09
> **Spigon said:**
> Yea but the whole network-manager installed with gnome core defeats my purpose. I don't want gnome anything lol. I just want a ubuntu that has icewm, slim log-in manager, xfe/pcman/thunar file manager (still choosing), and swiftweseal with my nvidia driver and wifi access.

This tutorial has almost exactly what you want.  It does require a net install though.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Spigon on 2009-10-09
> **P1umb3r said:**
> This tutorial has almost exactly what you want.  It does require a net install though.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

That doesn't help at all, I already knew how to do all that it just the wifi I need. No point in doing all this if i can't go online.

---

### Post by Dark_Stang on 2009-10-09
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
I don't use wicd, but most network managers are similar. Check out their website for more info.

---

### Post by kerry_s on 2009-10-09
you can manually do the wifi you know.

[B]sudo iwconfig wlan0 essid your-router-name
sudo dhclient wlan0[/B]

you might have to do:
**sudo ifup wlan0**

replace wlan0 with your connection, use "sudo iwconfig" to show status of wireless devices.

you can try it now if you want.

i always have to do it manually till i get the gui installed after i do a base install.

---

### Post by jeremyswalker on 2009-10-09
> **kerry_s said:**
> you can manually do the wifi you know.

[B]sudo iwconfig wlan0 essid your-router-name
sudo dhclient wlan0[/B]

you might have to do:
**sudo ifup wlan0**

replace wlan0 with your connection, use "sudo iwconfig" to show status of wireless devices.

you can try it now if you want.

i always have to do it manually till i get the gui installed after i do a base install.

Manual way is always an option. However, if your network is secured, it's not quite as straightforward as you show.

---

### Post by Spigon on 2009-10-10
Thanks I'll try some of these stuff when I get back to my dads house. But just in case if anyone else have anymore solutions that would be great.

---

### Post by ikisham on 2009-10-10
To launch the Wicd GUI run
```
wicd-client -n
```

[http://wicd.sourceforge.net/moinmoin/FAQ](http://wicd.sourceforge.net/moinmoin/FAQ)

If you're using IceWM, create a file named *startup* at ~/.icewm if you want to launch it at startup time
```
#!/bin/bash

sleep 2 && wicd-client &
```
right click on it, select properties and give the permission to be executed.
(the sleep 2 is for it to let the taskbar open before it docks on the tray and the last '&' is for it to remain running)

---

