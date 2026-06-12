---
title: "Executing sudo script without login"
date: 2008-09-27
forum: General Help
---

### Post by quic on 2008-09-27
Ubuntu 8.04

I have written a script in order to start up my Xbox360 controller driver when run.  However, I cannot fully automate this script since I have to type in my password in order for the "sudo" lines to execute.  I have tried amending the 'etc/sudoers' file to make an exception, however without any success.

I have added all of the following lines to the end of sudoers without any luck!

(xbmc is my username)

xbmc ALL=NOPASSWD: /home/xbmc/tmp/xboxdrv-linux-0.2/

xbmc ALL=NOPASSWD: /home/xbmc/tmp/xboxdrv-linux-0.2/*

xbmc ALL=NOPASSWD: /home/xbmc/tmp/xboxdrv-linux-0.2/controller

xbmc ALL=NOPASSWD: /home/xbmc/tmp/xboxdrv-linux-0.2/controller.sh

If I completly turn off sudo passwords with:

xbmc ALL=NOPASSWD: ALL

then it works FINE! however then ANY sudo script can be run on my system without the password.

If anyone knows the syntax to make an exception to the password rule, please reply as I wish to run this code...

```
cd ~/tmp/xboxdrv-linux-0.2
sudo ./xboxdrv --wid 0 -l 2 --dpad-as-button --deadzone 12000
```

In the end of all of this I wish the sudo script to be called on startup so the controller driver loads and the controller works without any input.

---

### Post by sisco311 on 2008-09-27
You don't need to edit the sudoers file.
Put your command in the /etc/rc.local file.
The script is executed at boot time as root.
Make sure the file is executeble:
```
sudo chmod +x /etc/rc.local
```

---

### Post by quic on 2008-09-27
Thanks for responding so quickly...:)

This is what I have now got in my rc.local file:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
cd /home/xbmc/tmp/xboxdrv-linux-0.2
sudo ./xboxdrv --wid 0 -l 2 --dpad-as-button --deadzone 12000
exit 0

```

I think it is working, however as soon as the 'exit 0' line is run the script stops executing and the driver no longer works....does this sound right? or should the 'sudo ./xboxdrv --wid 0 -l 2 --dpad-as-button --deadzone 12000' keep running even after the rc.local exits?

---

### Post by sisco311 on 2008-09-27
try:
> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/home/xbmc/tmp/xboxdrv-linux-0.2/xboxdrv --wid 0 -l 2 --dpad-as-button --deadzone 12000 &
exit 0

---

