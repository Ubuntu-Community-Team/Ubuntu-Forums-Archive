---
title: "HPLIP Does Not Install"
date: 2019-08-15
forum: Hardware
---

### Post by artist-wavenet on 2019-08-15
I am trying to get my HP 4620 printer working under Ubuntu 18.04. To that end I attempted to install:

hplip-3.19.6.run

Which I downloaded from: [https://sourceforge.net/projects/hplip/](https://sourceforge.net/projects/hplip/). The installation fails with this error:

```
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes python-dbus.mainloop.pyqt5'
Please wait, this may take several minutes...
error: A required dependency 'pyqt5 (PyQt 5- Qt interface for Python (for Qt version 4.x))' is still missing.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'pyqt5 (PyQt 5- Qt interface for Python (for Qt version 4.x))' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

```

The steps to resolve this would be greatly appreciated.

I do not see in the lsusb command's output the printer. Is printer's presence in the lsusb command's output dependent on an hplip installation?

---

### Post by artist-wavenet on 2019-08-16
Using information I found at:
[https://itsfoss.com/install-pip-ubuntu/](https://itsfoss.com/install-pip-ubuntu/)
I was able to complete the hplip installation after executing these commands:
```
sudo apt-get install python3-pip
pip3 install pyqt5

```

However the command "hp-plugin -i" got me this error:
```

Plugin installation failed
error: Python gobject/dbus may be not installed
error: Plug-in install failed.

```

But this command sequence worked to install those plugins:
```

sudo aa-disable /usr/share/hplip/plugin.py
hp-plugin -i

```
The source of the above solution is this thread:
[https://bugs.launchpad.net/hplip/+bug/1813768](https://bugs.launchpad.net/hplip/+bug/1813768)

The printer still does not appear in the lsub comand's output. The hplip application still cannot find the printer.

---

### Post by Autodave on 2019-08-16
Why didn't you just use the one in the repositories?  It has always worked for me for networked, cabled, or wireless.

---

### Post by Dennis N on 2019-08-16
Have you tried Settings > Printers, where you can add your printer to the system? There is an automatic search for correct driver which is then installed for you.

---

### Post by artist-wavenet on 2019-08-16
I tried installing hplip in Ubuntu's Software utility. I was unable to add the printer.

Before a printer can be added to a driver utility, must it appear in the output of the lsusb command? I still does not. I suspect something is wrong with the printer. Printer model 4620 E does appear on this list:
[URL="https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index"]https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index
[/URL]
On the printer's label I see model number 4620 e. It does look like it should be supported.

---

### Post by Dennis N on 2019-08-16
> **artist-wavenet said:**
> I tried installing hplip in Ubuntu's Software utility. I was unable to add the printer. Before a printer can be added to a driver utility, must it appear in the output of the lsusb command? I still does not. I suspect either this printer is not supported, or something is wrong with the printer. The printer model 4620 E does appear on this list:
[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)
But from what I can see my printer model does not have an E on the end of it. I do not know what that means.

After opening the printers dialog, did you click the ADD button? Then it does a search for your printer. 

If connected by USB, I would think it should appear in lsusb output. I can't confirm this with my printer, since my HP 6980 is a network printer and is connected to a router.

As to the 'E', searching for 4620 on the HP support page only matches the 4620 E all-in-one, so my guess is it's the same thing.

---

### Post by brian_p on 2019-08-17
It would be useful to see the output of

```
avahi-browse -rt _ipp._tcp
```

---

### Post by artist-wavenet on 2019-08-18
Yes, the Add button was used in an attempt to use the printer. The printer was not found.

I do not get any response to the command: 
```
avahi-browse -rt _ipp._tcp

```
Not even an error.

It is by USB I need to connect to this printer.

---

### Post by brian_p on 2019-08-18
> **artist-wavenet said:**
> 
It is by USB I need to connect to this printer.

Are you completely ruling out using a network connection?

Incidentally, the OfficeJet 4620 E-all-in-one Printer has been supported by HPLIP since version 3.12.6. hplip-3.19.6.run is not likely to magically resolve any issues you are having on Ubuntu 18.04.

---

### Post by Dennis N on 2019-08-18
> **artist-wavenet said:**
> Yes, the Add button was used in an attempt to use the printer. The printer was not found.

I do not get any response to the command: 
```
avahi-browse -rt _ipp._tcp

```
Not even an error.

It is by USB I need to connect to this printer.

Can we assume the printer worked previously with another version of Ubuntu or some other Linux?

If yes to the above, since it's not being detected as a connected USB device, I might try the other USB 2.0 ports on the computer (not USB 3.x). I would also try another cable. It should be detected even without any driver installed, so it shouldn't be an incorrect driver that is the problem. 

Can you try a different printer, just to see if it is detected? If it is, that would suggest the printer itself or its interface being the problem. If not, it might be related to your new installation of 18.04 or steps you might have taken after install.

Do you have another computer? Does the printer work on that? All this to try and isolate the problem.

---

### Post by artist-wavenet on 2019-08-18
I tested the printer and cable on a Windows 7 machine. I was able to use this printer to print on that Windows 7 machine.

On my Ubuntu computer I tested several USB ports and found only the USB3 ports work to communicate with printer, and on these ports it did show up in the lsusb command's output. It appears all USB2 ports are malfunctioning on my Ubuntu computer. These USB2 ports do not work with anything else also, be it keyboard, mouse, or memory stick. I do not know right now if it is a hardware failure, or a driver problem.

Thanks for your help :)

---

