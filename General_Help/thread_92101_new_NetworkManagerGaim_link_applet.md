---
title: "new NetworkManager/Gaim link applet"
date: 2005-11-18
forum: General Help
---

### Post by fergus on 2005-11-18
All,

I got frustrated with gaim never being in sync with my network on my laptop.  Suspend/Resume cycles would leave gaim not knowing what the network was doing.  I assume that eventually Gaim would listen to NetworkManager messages directly,  but until then I wrote a small app that sits between the two and controls gaim when the network comes up and goes away.

The app is simple.  When the network goes away, shutdown gaim.  When the network comes back, startup gaim.  I have my account setup to auto login so everything just works for me.  Its not the most elegant solution but it works until a more official method is established.

Just add it to your gnome session and enjoy.. 

get it here

[http://users.adelphia.net/~fergus420/nm-gaim-dbus.py](http://users.adelphia.net/~fergus420/nm-gaim-dbus.py)

---

### Post by briguy on 2005-11-18
Sounds cool!  I'm going to give 'er a try.

Works like a charm when I suspended.

---

### Post by KSDZ on 2006-04-04
I took the liberty to modify it for Gaim 2.0
Awsome script btw, very good idea!

```

#!/usr/bin/python
#
# nm-gaim-dbus.py - Watch for NetworkManager signals and 
#                   shutdown/startup gaim when appropriate.
#
# Author: Richard Ferguson <gnome@fergusnet.com>
# Modified for Gaim 2.0 dbus connection by Koen Sadza <koen@sadza.nl>
#
# ChangeLog
# -------- --- -------------------------------------------
# 04/04/06 Modified for DBUS connection to gaim (Gaim 2.0)
# 11/18/05 RJF Initial Release
#

import os

import gtk
import dbus
import dbus.glib

#######################################

class GaimControl:
	def __init__(self):
		self.gaim_was_running = 0

	# Launch gaim
	def start_gaim(self):
		if self.gaim_was_running:
			pid = os.fork()
			if pid == 0:
				os.execlp('gaim', 'gaim')

	# Shutdown gaim
	def stop_gaim(self):
 		try:
 			dbus_gaim.GaimCoreQuit()
 			self.gaim_was_running = 1
 		except:
 			res = os.system('gaim-remote quit')
 			if res != 0:
 				self.gaim_was_running = 0
 			else:
 				self.gaim_was_running = 1

	# Network device activated
	def nm_device_active_cb(self,path):
		self.start_gaim()

	# Network device deactivated
	def nm_device_notactive_cb(self,path):
		self.stop_gaim()

#######################################

gc = GaimControl()

# Connect to DBUS for NM
bus = dbus.SystemBus()
nm_proxy_obj = bus.get_object('org.freedesktop.NetworkManager', '/org/freedesktop/NetworkManager')
dbus_nm = dbus.Interface(nm_proxy_obj, 'org.freedesktop.NetworkManager')

# And for Gaim
bus = dbus.SessionBus()
gaim_proxy_obj = bus.get_object('net.sf.gaim.GaimService', '/net/sf/gaim/GaimObject')
dbus_gaim = dbus.Interface(gaim_proxy_obj, 'net.sf.gaim.GaimInterface')

# Listen for NetworkManager signals
dbus_nm.connect_to_signal('DeviceNowActive', gc.nm_device_active_cb)
dbus_nm.connect_to_signal('DeviceNoLongerActive', gc.nm_device_notactive_cb)

# Loop
gtk.main()

```

TO DO:
Find out what the Connect and Disconnect dbus bindings are (if any) so it would be cleaner
Get PyGaim to compile so I can make it a gaim-plugin instead of an external app.

---

### Post by frup on 2006-04-04
while gaim is on topic, is there a way to make it work over a network to IM, i.e if the internet is down networked computer could still have an "account" running?

---

### Post by KSDZ on 2006-04-04
> **frup:**
while gaim is on topic, is there a way to make it work over a network to IM, i.e if the internet is down networked computer could still have an "account" running?
Do you mean you want to be possible to chat on the internal network if the internet is down?

Then you should look into configuring your own Jabber server,
i recommend [ejabberd]("http://ejabberd.jabber.ru"), its in the repos.

---

### Post by frup on 2006-04-04
thanks :D as soon as i posted i realised that was a possible answer (jabber server) just didnt know where to start. hopefully not too hard, will try tomorrow

---

### Post by calgarystevens on 2007-05-12
OK, I'm fairly new to Ubuntu, and never programmed... but I took a stab at doing the same with your script for Wicd and Pidgin... no luck. I would love it if my Pidgin would stay in sync also, as I use it all the time, and on resume it just doesn't update itself. If any of you python masters read this and have time, would you be able to modify the script for use with Wicd and Pidgin? I feel terrible for asking, I feel if I did more research I could make it work, but I think it's over my head. Thanks.

---

### Post by fergus on 2007-05-14
what is Wicd?

---

### Post by calgarystevens on 2007-05-14
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) An alternative to Network Manager that works better with my system, it allows me to use WPA with my router. It also means the script needs to check WiCd's status with dbus, not nm's, which I think I had working, but I couldn't get the Pidgin/Gaim part to work.

---

### Post by sb73542 on 2007-06-22
> **calgarystevens said:**
> OK, I'm fairly new to Ubuntu, and never programmed... but I took a stab at doing the same with your script for Wicd and Pidgin... no luck. I would love it if my Pidgin would stay in sync also, as I use it all the time, and on resume it just doesn't update itself. If any of you python masters read this and have time, would you be able to modify the script for use with Wicd and Pidgin? I feel terrible for asking, I feel if I did more research I could make it work, but I think it's over my head. Thanks.

I would love something like this for Gaim and Wicd too.  Why in the world does Gaim not provide a plugin to check for network status?  Gaim / Pidgin should be the one to check for network connection every few seconds.  It works in Windows perfectly.

---

