---
title: "Bluetooth hangs when trying to enable"
date: 2011-02-28
forum: Hardware
---

### Post by IBUA on 2011-02-28
I've just bought a small Bluetooth USB Dongle.

I've been trying to get it to work. Ubuntu detects it exists, but when trying to enable it, I get various warning messages (different ones per attempt).

When I try to enable the dongle via the standard Ubuntu Bluetooth manager, when I press 'Turn On Bluetooth', the button goes grey and does nothing. 

Sometimes it just reverts back to 'Turn On Bluetooth'; Sometimes  I get 'Connection to BlueZ failed; Bluez daemon is not running, blueman-manager cannot continue.'.

After looking around the internet and these forums, I tried using the 'Blueman' Bluetooth manager, but still no luck, and I either get the above message, or 'Failed to set Bluetooth power' with 'Error Reported: Connection timed out'.

Can anyone suggest anything to try and get it to work?!

Thank you!

---

### Post by Kirboosy on 2011-02-28
Have you tried installing the following packages?


"bluetooth"
"bluez"
"bluez-utils"


Also check your "Startup Applications" to make sure that Blueooth Manager is starting.

---

### Post by IBUA on 2011-02-28
> **Caboose885 said:**
> Have you tried installing the following packages?


"bluetooth"
"bluez"
"bluez-utils"


Also check your "Startup Applications" to make sure that Blueooth Manager is starting.

Hi Caboose885, thanks for the quick reply!

bluetooth and bluez-utils packages weren't insalled, installed them but same problem as before.

Bluetooth Manager isn't in the startup applications, but the 'Blueman Applet' is if that makes a difference?

Thanks!

EDIT: If any help this is the result from 'lsusb' command in terminal

> Bus 006 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

---

### Post by Kirboosy on 2011-02-28
After you installed the packages did you logout and log back in? Or you might have to restart the machine...I'm not sure.

I think it should still work with Blueman.

---

### Post by IBUA on 2011-02-28
> **Caboose885 said:**
> After you installed the packages did you logout and log back in? Or you might have to restart the machine...I'm not sure.

I think it should still work with Blueman.

Yep, restarted (just to make sure). Still doesn't work.

Something i've just found from [URL="https://help.ubuntu.com/community/BluetoothSetup"]https://help.ubuntu.com/community/BluetoothSetup
[/URL]

At the 'Manual Discovery section' when I try the command ```
sudo /etc/init.d/bluez-utils restart
```

I get

```
sudo: /etc/init.d/bluez-utils: command not found
```

although I have already installed bluez-utils

Also when I do 
```
hcitool dev
```

I get 'Device:' but with no key or anything?

---

### Post by Kirboosy on 2011-02-28
That guide is outdated. > This document applies to Ubuntu 8.10 (Hardy Heron) and earlier versions of Ubuntu that come with Bluez3. Ubuntu 9.04 (Jaunty Jackalope) and later versions come with Bluez4, which is completely different. There currently exists no well-documented way to use Bluez4 to connect using non-GUI tools. It's possible that installation of the "bluez-compat" package will allow this documentation to work. Look at /usr/share/doc/bluez/examples for possible pointers. I also do not have /etc/init.d/bluez-utils....

Lets try making a new startup program. 

Name: Bluetooth Manager
Command: bluetooth-applet
Comment: Bluetooth Manager applet

Logout and log back in and see if that fixes anything

---

### Post by IBUA on 2011-02-28
> **Caboose885 said:**
> That guide is outdated.  I also do not have /etc/init.d/bluez-utils....

Lets try making a new startup program. 

Name: Bluetooth Manager
Command: bluetooth-applet
Comment: Bluetooth Manager applet

Logout and log back in and see if that fixes anything

No go :(

Still comes up with the warning message of:

> Failed to set Bluetooth power
The error reported is: Connection timed out

on the Bluetooth Manager applet (although the bluetooth icon is in the gnome panel now)

EDIT: Although now Blueman worked for a bout 5 seconds then died?!

---

### Post by Kirboosy on 2011-02-28
Hmm that is weird...have you verified that the dongle is actually working properly? (maybe plug it in to another computer)

I just recently added [bluetooth]("http://www.dealextreme.com/p/super-mini-bluetooth-2-0-adapter-dongle-vista-compatible-11866") to my desktop and it worked no problem. Also it was an ultra cheap dongle....

Seems like you have hit this [bug]("https://bugs.launchpad.net/blueman/+bug/496733")

---

### Post by IBUA on 2011-02-28
> **Caboose885 said:**
> Hmm that is weird...have you verified that the dongle is actually working properly? (maybe plug it in to another computer)

I just recently added [bluetooth]("http://www.dealextreme.com/p/super-mini-bluetooth-2-0-adapter-dongle-vista-compatible-11866") to my desktop and it worked no problem. Also it was an ultra cheap dongle....

No, I shall do in a second.
Ironically, I was looking at that one, but chose this one as that one got loads of bad reviews on Amazon.co.uk!

---

### Post by Kirboosy on 2011-02-28
Open terminal
- Type in sudo gedit /etc/bluetooth/main.conf without the quotes
- Change the value of RememberPowered from true to false
- Save the document and reboot




Found that on the bug page. Maybe it will fix your problem :)

---

### Post by IBUA on 2011-02-28
> **Caboose885 said:**
> Open terminal
- Type in sudo gedit /etc/bluetooth/main.conf without the quotes
- Change the value of RememberPowered from true to false
- Save the document and reboot




Found that on the bug page. Maybe it will fix your problem :)

Still no go :(. And now the warning messages just freeze and won't go away. Bah.

I tried it on my friends Laptop which is the same make and type as mine but running windows 7. It connected and it said the driver installed successfully but under the windows device manager said it wasn't working properly. I might try for a few more days and if not, send it back.

Thank  you for all your help!

---

### Post by Kirboosy on 2011-02-28
Ok. Glad you sorta figured it out. I hope when the new one comes in everything goes smoothly for you. If not, you know where to find me. ;)

---

