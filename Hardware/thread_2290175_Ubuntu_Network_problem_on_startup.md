---
title: "Ubuntu Network problem on startup"
date: 2015-08-10
forum: Hardware
---

### Post by Andrew_McCann on 2015-08-10
I have been running an ubuntu server for a while now without issue. We recently lost our internet connection for weeks so had to try to get  the server to work with a 4G mobile Broadband usb dongle. Now that our  internet connection has been established again I have removed all traces  of the USB dongle.
  Since then, every time the server is restarted I have no network connection and the only way to invoke this is by using:
  sudo service network-manager restart
  So any ideas how I can fix this?
  The server is on a UPS and if during the night we lose power and the  system does need to go down gracefully then I'd like it all to come back  up without any manual intervention.

---

### Post by dino99 on 2015-08-10
you did not give detail about the ubuntu version to get  more precise answer; but watch at possible broken links into /etc/rc?.d/ and erase them if any

---

### Post by Andrew_McCann on 2015-08-10
Version - Ububtu 12.04.05 LTS Linux 3.5.0-54-generic i686e, thanks for the broken links idea but i'm new to all this so I need the answer in really basic descriptive terms if possible please. I know of etc but not rc?.d and erase what exactly? Thanks for helping :-)

---

### Post by weatherman2 on 2015-08-10
OK - so you're using Ubuntu 12.04.5 desktop edition (which has a Gui, not server edition which has only a terminal), right?  Had you not mentioned Network Manager I would have assumed you were using the server edition, which does not use Network Manager at all unless you install it.

We can't be sure what you changed in the process of setting up and then removing the USB dongle.  But you can try editing connections in network manager and make sure your wired(?) connection is set to "connect automatically."  But you're saying that even if you manually try to connect to your network at startup, nothing happens?  If not, what happens?

Or, try deleting your connection in Network Manager and creating a new one.

You could also try removing and re-installing Network Manager.

---

### Post by Andrew_McCann on 2015-08-14
Yes weatherman2 you're correct and sorry I wasn't more descriptive. I use the terminal within the Gnome Gui. When I look in connection in the gui there is nothing until I restart the network manager then the wired connections appear and that's it. I did notice that on startup (before the gui gets going) I get the 'starting' black and white screen which starts with the /dev/mapper/Rhino11-root: clean file info stuff which then lists the services it's starting and stopping (network device security, starting SMB/CIFS File Server, Userspace bootsplash, save udev log etc etc...) then after CUPS printing spooler/server it sits there 'waiting for network configuration...' then again for 60 more seconds.... then the gui boots and I have to run the restart NM stuff. I hope this helps???

---

### Post by Andrew_McCann on 2015-08-14
Also...in Terminal when I do restart network-manager restart I get 'Stop: Unknown Instance:' and then NM running process 3629' if this helps?

---

### Post by Andrew_McCann on 2015-08-18
Does anyone have any ideas on this please?

---

