---
title: "My Resume Script. I need help!"
date: 2009-11-04
forum: Hardware
---

### Post by outleradam on 2009-11-04
This is my resume script to restart the remote control which I use on my media center. It works, but I need to automate it. I need help on sending a LIRC command in memory to a null device, or to clear the LIRC command in memory. I have to do this manually right now. The device works with this script, but it has to be done manually from a terminal. 
 
```
sudo rmmod lirc_atiusb
sudo modprobe lirc_atiusb  'restart the drivers
sudo /etc/init.d/lirc restart 'restart LIRC
IRW  'dump the waiting "close" command to IRW
```
 
I had to run IRW to dump the CLOSE command out of the remote daemon because it's holding onto it until it gets a port to unload it. If I initiate the last line of code (below) before running IRW, it sends the command close(which is also my resume button on my remote) to my program which then initiates the suspend script all over agin.
 
 
hit ctrl-C to stop the process - This is the part I need help on
 
 
```
sudo curl "http://127.0.0.1:8080/xbmcCmds/xbmcHttp?command=ExecBuiltIn&parameter=LIRC.Start"
```
 
 
How can I automate running IRW, or something, to dump the contents of the LIRC memory and then close it before I connect LIRC to my program?

---

### Post by outleradam on 2009-11-04
ref this thread [http://xbmc.org/forum/showthread.php?t=60823](http://xbmc.org/forum/showthread.php?t=60823)
 
 
A guy came up with this to port the command out of memory then terminate the process
```
irw & sleep 1; killall irw
```
 
Surely there is a better way to dump this command out of memory before starting the program which uses the remote control.

---

