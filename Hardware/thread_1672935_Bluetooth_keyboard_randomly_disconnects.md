---
title: "Bluetooth keyboard randomly disconnects"
date: 2011-01-21
forum: Hardware
---

### Post by N00b-un-2 on 2011-01-21
this has been an ongoing problem literally since I purchased the keyboard well over a year and a half ago.  It is a ["Logitech Mediaboard Pro", model Y-X5A77]("http://www.logitech.com/en-gb/441/3616").  It is a bluetooth keyboard with a built in track pad like you would find on a laptop.  I use it with an HTPC running Lucid Gnome 32 bit desktop. I have it connected to my television, and if not for the connectivity issues it would be the ideal solution.  Perhaps my issues arise from the fact that it is intended to be a Playstation 3 peripheral.
What happens is the keyboard will stop working for a minute or two randomly and without warning and then it will resume on it's own.  I've tried using the default bluetooth manager, blueman, and the KDE bluetooth manager, all with identical results.  I've noticed the same exact behavior on multiple versions of Ubuntu as well as Linux Mint, on both the 64 and 32 bit versions going back as far as 9.10.
Typically, setting up the device is as straight forward as it gets.  I follow the setup wizard, type in the randomly generated PIN and then it connects without any problems.  Interestingly enough, this problem does not persist on the current versions of openSUSE or Fedora, so it seems the problem is with Ubuntu's bluetooth stack.

---

### Post by N00b-un-2 on 2011-01-25
solved the problem through trial and error.  What worked for me was to uninstall the default bluetooth manager, then install the packages *bluez-compat* and *blueman*

I don't know if this step is necessary, but I disconnected the keyboard from the computer and then closed the blueman applet.  Then in the terminal I entered typed

```
hcitool scan
```

I had to hit the reset button on the keyboard while the scan was going on.  Eventually it located my keyboard so I copied the bluetooth address that it reported and pasted it into the following command

```
sudo hidd connect xx:xx:xx:xx:xx:xx
```

* Interesting note!  it was surprising to me that it didn't ask for a pin, but the bluetooth applet and blueman both do.

at which point the keyboard was connected to the computer.  However, after any period of inactivity, the keyboard would 'go to sleep' and disconnect from the computer.  At which point it can be reconnected by typing

```
sudo hidd --search
```

but I was looking for a more permanent solution.  After establishing a connection with the keyboard via terminal, I opened blueman and then paired the keyboard as normal (which was much faster than it usually takes) making sure to mark the keyboard as 'trusted'.

It's been nearly two days and it has yet to drop the keyboard again, but I wonder if it will survive through a reboot.  My guess is no, but if I have to enter a single command into the terminal after a reboot, i think I can handle that.

---

### Post by N00b-un-2 on 2011-01-25
I stand corrected.  The keyboard still disconnected eventually and then after a reboot I was unable to pair the keyboard again using blueman.  ](*,)

---

