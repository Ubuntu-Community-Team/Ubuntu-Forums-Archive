---
title: "dont understand why tightvnc wont connect..."
date: 2008-10-13
forum: General Help
---

### Post by puppetj on 2008-10-13
hi, ok i have tightvnc viewer on my windows PC, and installed tightvnc server on my Ubuntu pc by synaptic package manager, ran the server by way of
whats explained below under tightvnc, ive tried:  
tightvncserver -nolisten tcp -localhost   (runs but cant connect on my win pc)

i try  tightvncserver -nolisten tcp :1 (i get Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the tightvncserver script.
Couldn't start Xtightvnc process.


Fatal server error:
Server is already active for display 1
	If this server is no longer running, remove /tmp/.X1-lock
	and start again.


Fatal server error:
Server is already active for display 1
	If this server is no longer running, remove /tmp/.X1-lock
	and start again.)


i tried to see if the /etc/vnc.conf was the issue to the last load to start the app but where there and could finf the file, 

so what do i do?

btw i want to access inside the network, not from the internet, thanks




[https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c](https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c)

---

### Post by fragos on 2008-10-13
Your tightvnc client should be able to connect without installing tightvnc server. On the Ubuntu system do System-> Preferences-> Remote Desktop and select sharing "Allow other users to view your desktop". There are other things in that window you will want to set.

---

### Post by puppetj on 2008-10-13
that works with tight viewer for windows??? cuz im trying to view my linux desktop from windows pc using tightvnc viewer. can u tell me how? (because it doesnt work i followed what u said)

ok also i did get tightvnc  to connect to view my Ubuntu desktop and researching now because all it does is display the terminal the everything is grayed out even on a post i seen related to the issue is say to ad the  -geometry "re"zx"rez"  option and i do by my ubuntu rez where those "rezs" are, but no luck

thanks for replying !

---

### Post by Phil Marsh on 2008-10-13
Dear puppetj,
How is your ~/.vnc/xstartup file configured?
You might try my configuration below:

#!/bin/sh

#xrdb $HOME/.Xresources
#xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#exec gnome-session &

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

exec gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# twm &

#############################################################


First of all, I'd just installed tightvnc this last weekend (Oct 11, 2008) and I'd noticed the same problem with the default configuration xstartup file that shipped with Tightvnc: i.e. you get a gray background with no icons and only an x-window. Not too useful at that!
After finding the above xstartup file, my desktop became visible remotely but then I get the error on it:
"There was an error with the GNOME Settings Daemon ......
Everything else seemed fine except for this annoying message that shows up when I first access a newly started vnc window.
Incidently, the above configuration will give you an open xterm window.
If you don't want that try commenting out the line above starting with 
xterm.
I'm sure my logfile tells more about the reason for the errors and it's shown below:
If any one else out there sees this could you kindly give us a clue as how to fix it? I'm kind of a amateur here!

My vnc logfile appears below:



13/10/08 22:30:19 Xvnc version 3.3.tight1.2.9
13/10/08 22:30:19 Copyright (C) 1999 AT&T Laboratories Cambridge.
13/10/08 22:30:19 Copyright (C) 2000-2002 Constantin Kaplinsky.
13/10/08 22:30:19 All Rights Reserved.
13/10/08 22:30:19 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
13/10/08 22:30:19 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
13/10/08 22:30:19 Desktop name 'X' (Sibyl:1)
13/10/08 22:30:19 Protocol version supported 3.3
13/10/08 22:30:19 Listening for VNC connections on TCP port 5901
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring
/home/viking/.vnc/xstartup: 18: vncconfig: not found
SESSION_MANAGER=local/Sibyl:/tmp/.ICE-unix/24936

** (gnome-settings-daemon:24942): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24942): WARNING **: Could not acquire name
1223951420.321822 Session manager: disconnected...

** (gnome-settings-daemon:24944): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24944): WARNING **: Could not acquire name
1223951420.338697 Session manager: disconnected...

** (gnome-settings-daemon:24951): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24951): WARNING **: Could not acquire name
1223951420.355589 Session manager: disconnected...

** (gnome-settings-daemon:24959): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24959): WARNING **: Could not acquire name
1223951420.371694 Session manager: disconnected...

** (gnome-settings-daemon:24960): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24960): WARNING **: Could not acquire name
1223951420.388516 Session manager: disconnected...

** (gnome-settings-daemon:24961): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24961): WARNING **: Could not acquire name
1223951420.405467 Session manager: disconnected...

** (gnome-settings-daemon:24962): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24962): WARNING **: Could not acquire name
1223951420.422633 Session manager: disconnected...

** (gnome-settings-daemon:24966): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24966): WARNING **: Could not acquire name
1223951420.438483 Session manager: disconnected...

** (gnome-settings-daemon:24967): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24967): WARNING **: Could not acquire name
1223951420.453807 Session manager: disconnected...

** (gnome-settings-daemon:24968): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24968): WARNING **: Could not acquire name
1223951420.469317 Session manager: disconnected...

** (gnome-settings-daemon:24969): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:24969): WARNING **: Could not acquire name
1223951420.485809 Session manager: disconnected...

** (gnome-session:24936): CRITICAL **: dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-session:24936): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
Checking for Xgl: Xlib:  extension "XVideo" missing on display ":1.0".
xvinfo: No X-Video Extension on :1.0
not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Initializing nautilus-share extension
seahorse nautilus module initialized
Detected PCI ID for VGA: 01:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/viking/.metacity/sessions/default0.ms: Failed to open file '/home/viking/.metacity/sessions/default0.ms': No such file or directory
Window manager warning: Log level 32: could not find XKB extension.
ERROR: trackerd already running on your session dbus - exiting...
Failure: Module initalization failed
evolution-alarm-notify-Message: Setting timeout for 77380 1224028800 1223951420
evolution-alarm-notify-Message:  Tue Oct 14 20:00:00 2008

evolution-alarm-notify-Message:  Mon Oct 13 22:30:20 2008


(evolution-alarm-notify:25014): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...

** (nautilus:24973): WARNING **: Unable to add monitor: Not supported
  PID TTY          TIME CMD
18622 ?        00:00:17 pulseaudio

13/10/08 22:33:39 Got connection from client 192.168.1.60
13/10/08 22:33:42 Protocol version 3.3
13/10/08 22:33:48 Full-control authentication passed by 192.168.1.60
13/10/08 22:33:48 Pixel format for client 192.168.1.60:
13/10/08 22:33:48   8 bpp, depth 6
13/10/08 22:33:48   true colour: max r 3 g 3 b 3, shift r 4 g 2 b 0
13/10/08 22:33:48 Enabling full-color cursor updates for client 192.168.1.60
13/10/08 22:33:48 rfbProcessClientNormalMessage: ignoring unknown encoding -223
13/10/08 22:33:48 rfbProcessClientNormalMessage: ignoring unknown encoding 16
13/10/08 22:33:48 Using hextile encoding for client 192.168.1.60
13/10/08 22:33:48 Pixel format for client 192.168.1.60:
13/10/08 22:33:48   32 bpp, depth 24, little endian
13/10/08 22:33:48   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
13/10/08 22:33:48   no translation needed
13/10/08 22:33:48 Enabling full-color cursor updates for client 192.168.1.60
13/10/08 22:33:48 rfbProcessClientNormalMessage: ignoring unknown encoding -223
13/10/08 22:33:48 Using hextile encoding for client 192.168.1.60
13/10/08 22:33:48 rfbProcessClientNormalMessage: ignoring unknown encoding 16

---

### Post by fragos on 2008-10-13
I gave up on Windows almost 10 years ago. I have used another Ubuntu box with xtightvncviewer 1.2.9-22 installed and from a Nokia N810 with VNC Viewer 0.6. If it helps, here's the tightvnc website [http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html).

---

### Post by puppetj on 2008-10-14
I figured it out :
[http://manvspc.com/smf/index.php?topic=160.0]("http://manvspc.com/smf/index.php?topic=160.0")


as for giving up on windows, that sux i have way to much to give up on it now, but i always like to use any other os, ubuntu, beos, osx, etc...  but thanks anyway!

---

### Post by fragos on 2008-10-14
The best tool for each of us is the one we can and do use. Windows, Mac or Linux isn't all that important as long as we get the job done.

---

