---
title: "Impossible to set up my graphic card"
date: 2016-12-18
forum: Hardware
---

### Post by pierro91 on 2016-12-18
Hi,
it's for about 3 days i'm trying to install my graphic card on my ASUS G552VW-DM475T which as an intel core I7-6700HQ (+intel grpahic 520) and a NVIDIA GeForce GTX 960M. To start my laptop i have to edit grub option and turn "acpi=off". Without this i have a black screen. The last thing i have tried is this russian procedure : [http://help.ubuntu.ru/wiki/bumblebee-xenial](http://help.ubuntu.ru/wiki/bumblebee-xenial)
It seems that i have to use bumblebee because of "nvidia optimus" which switchs intelgraphic or nvidia, depend of the laptop use for battery saving.

When i start i have the following error message : "bbswitch : canno't find ACPI handle for VGA device" maybe because i turn off acpi but i need to turn off because when i boot withtout i have a blackscreen (maybe the laptop use graphic card ouptput and the screen use intel graphic something like this)

and i have an other error message 
```
[  159.935096] wlp2s0: send auth to f0:82:61:dc:cf:6a (try 1/3)
[  159.941072] wlp2s0: authenticated
[  159.945473] wlp2s0: associate with f0:82:61:dc:cf:6a (try 1/3)
[  159.952418] wlp2s0: RX AssocResp from f0:82:61:dc:cf:6a (capab=0x431 status=0 aid=3)
[  243.279331] wlp2s0: associated
[  243.289148] wlp2s0: Limiting TX power to 23 (23 - 0) dBm as advertised by f0:82:61:dc:cf:6b
```

So... if someone has something to suggest....
Thanks for reading me

---

### Post by ajgreeny on 2016-12-18
Try using the boot option **nomodeset** rather than **acpi=off** to see if that gets you a GUI from which you can install the nvidia driver needed.

I am not really aware of how good (or bad) bumblebee is now, so I can not help you deal with that in any way, I'm afraid.

---

### Post by pierro91 on 2016-12-18
Only access to the tty but its nice for me to use nomodeset instead of acpi=off, no more VGA error, thanks
I tried "startx" and i have this error in the log file : "UnloadModule : "libinput", don't know if it's usefull

---

### Post by ajgreeny on 2016-12-18
The command **startx** no longer works as Ubuntu has moved from upstart to systemd.

From the cli you may need to run command ```
sudo systemctl start lightdm.service
```as shown at [http://askubuntu.com/questions/804957/startx-as-a-user-fails](http://askubuntu.com/questions/804957/startx-as-a-user-fails)

---

### Post by pierro91 on 2016-12-18
when i cat /proc/acpi/bbswitch it says that my GC is on so its OK for this

and here ligthdm logs after trying to start it, nothing to help :(

```
[+0.44s] DEBUG: Seat seat0: Session authenticated, running command
[+0.44s] DEBUG: Session pid=3814: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/pantheon-greeter
[+0.44s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+0.44s] DEBUG: Session pid=3814: Logging to /var/log/lightdm/seat0-greeter.log
[+0.48s] DEBUG: Activating VT 7
[+0.48s] DEBUG: Activating login1 session c23
[+0.48s] DEBUG: Seat seat0 changes active session to c23
[+0.48s] DEBUG: Session c23 is already active
[+0.86s] DEBUG: Greeter closed communication channel
[+0.86s] DEBUG: Session pid=3814: Exited with return value 0
[+0.86s] DEBUG: Seat seat0: Session stopped
[+0.86s] DEBUG: Seat seat0: Stopping; failed to start a greeter
[+0.86s] DEBUG: Seat seat0: Stopping
[+0.86s] DEBUG: Seat seat0: Stopping display server
[+0.86s] DEBUG: Sending signal 15 to process 3803
[+1.04s] DEBUG: Process 3803 exited with return value 0
[+1.04s] DEBUG: DisplayServer x-0: X server stopped
[+1.04s] DEBUG: Releasing VT 7
[+1.04s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+1.04s] DEBUG: Seat seat0: Display server stopped
[+1.04s] DEBUG: Seat seat0: Stopped
[+1.04s] DEBUG: Required seat has stopped
[+1.04s] DEBUG: Stopping display manager
[+1.04s] DEBUG: Display manager stopped
[+1.04s] DEBUG: Stopping daemon
[+1.04s] DEBUG: Exiting with return value 1
```

---

### Post by pierro91 on 2016-12-20
I tried on an other ubuntu platform and someone gaves me the solution here : [http://askubuntu.com/questions/862665/module-nvidia-361-is-not-found](http://askubuntu.com/questions/862665/module-nvidia-361-is-not-found)
Thanks to the community !

---

