---
title: "Update Manager Causes freeze *Urgent*"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by NikoK on 2007-07-11
So this just happened as a random occurance and now is happening everytme I try to open up update manager...Apt-get in the terminal works but this doesnt 
 
I will go to update manager and click update, and then the screen fades down a bit and when its singupposed to show the password box it shows a translucent box instead, so i figured it was a one time bug and typed in the password and pressed enter...bringing me to a frozen screen like this

[[IMG]http://img106.imageshack.us/img106/7529/screenshotnk5.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotnk5.png)

---

### Post by bapoumba on 2007-07-11
What is the error message running:
```
:~$ update-manager
```

---

### Post by NikoK on 2007-07-11
It doesnt give one :S But when I click the update icon in the tray it does it...and now I discovered it does it when using the deb package installer too, Its always when starting administrative services....

---

### Post by bapoumba on 2007-07-11
Okay, so I guess that 
```
sudo nano
```
will work (enter CTRL-X to exit nano, a small text editor working in the terminal)
and
```
gksudo gedit

```
will not. Please paste the error message to
```
gksudo -S -d gedit
```

---

### Post by NikoK on 2007-07-11
Well gksudo gedit is working.

Deb package installer still no go same thing with update manager

---

### Post by bapoumba on 2007-07-11
Does **gksudo synaptic** work ?
Without an error message, it's going to be a little difficult to find whats going on...
I'm checking bugs.

Edit: which flavor of Ubuntu are you using ?

---

### Post by NikoK on 2007-07-11
It seems that everything terminal based is working :S

Still cant find an error message, i tried dpkg -i to a deb file but it worked...no errors

---

### Post by bapoumba on 2007-07-11
> **NikoK said:**
> It seems that everything terminal based is working :S

Still cant find an error message, i tried dpkg -i to a deb file but it worked...no errors
Okay, so you're not stuck, you can update/upgrade with aptitude or apt-get.

Which version of ubuntu are you using ?

---

### Post by NikoK on 2007-07-11
Yes I can use apt-get and update via terminal...Im using feisty 7.04 and I just updated to the new kernel 2.6.22....but this was happening before i updated the kernel i hoped the kernel update would fix it.

---

### Post by bapoumba on 2007-07-11
Which theme are you using?

---

### Post by NikoK on 2007-07-11
Im using Beryl with Emerald...scaled-black-mod theme that came with emerald...never had any problems with it as i said this was a random occurance..

---

### Post by bapoumba on 2007-07-11
Okay, I'm browsing through bug reports.
Which locales are you using ?

Edit: you can also check ~/xsession-errors.

---

### Post by NikoK on 2007-07-11
I think im using EN locales..

and with that xsession command i get a no file or directory found message...

---

### Post by bapoumba on 2007-07-11
I'm sorry, ~/.xsession-errors
It's a hidden file in your /home directory.

---

### Post by NikoK on 2007-07-11
Permission denied even with sudo :S

---

### Post by schnupi on 2007-07-11
Hmm i have the exact same problem.. here is my .xsession-error list..its a bit long now..hope it helps...


```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "schnupi"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
Setting IM through im-switch for locale=en_IE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/scim.
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/ubuntu:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.4

Starting SCIM as daemon ...
SCIM has been successfully launched.
Smart Common Input Method 1.4.4

Xlib:  extension "XEVIE" missing on display ":1.0".
Bonobo accessibility support initialized
GTK Accessibility Module initialized
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/5387

(gnome-session:5387): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session:5387): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session:5387): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session:5387): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session:5387): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session:5387): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session:5387): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session:5387): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

GTK Accessibility Module initialized
Bonobo accessibility support initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Bonobo accessibility support initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gnome-panel:5492): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

Initializing gnome-mount extension
GTK Accessibility Module initialized
Unable to open desktop file file:///home/schnupi/Desktop/swiftfox.desktop for panel launcher: No such file or directory
Unable to open desktop file file:///home/schnupi/Desktop/exaile.desktop for panel launcher: No such file or directory
GTK Accessibility Module initialized

(process:5573): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed
GTK Accessibility Module initialized

(nautilus:5497): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

GTK Accessibility Module initialized
Bonobo accessibility support initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(nm-applet:5608): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

Bonobo accessibility support initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(update-notifier:5556): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(update-notifier:5556): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(update-notifier:5556): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(update-notifier:5556): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(update-notifier:5556): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(update-notifier:5556): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(update-notifier:5556): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(update-notifier:5556): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

Backend     : ini
Integration : true
Profile     : default
Adding plugin firepaint (firepaint)
Adding plugin glib (glib)
Adding plugin clone (clone)
Adding plugin extrawm (extrawm)
Adding plugin blur (blur)
Adding plugin animation (animation)
Adding plugin fakeargb (fakeargb)
Adding plugin group (group)
Adding plugin regex (regex)
Adding plugin imgjpeg (imgjpeg)
Adding plugin showdesktop (showdesktop)
Adding plugin bench (bench)
Adding plugin ring (ring)
Adding plugin wall (wall)
Adding plugin addhelper (addhelper)
Adding plugin switcher (switcher)
Adding plugin scaleaddon (scaleaddon)
Adding plugin zoom (zoom)
Adding plugin rotate (rotate)
Adding plugin annotate (annotate)
Adding plugin reflex (reflex)
Adding plugin video (video)
Adding plugin scalefilter (scalefilter)
Adding plugin resize (resize)
Adding core settings (General Options)
Adding plugin cubereflex (cubereflex)
Adding plugin gotovp (gotovp)
Adding plugin place (place)
Adding plugin snow (snow)
Adding plugin resizeinfo (resizeinfo)
Adding plugin GTK Accessibility Module initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized
expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin neg (neg)
Adding plugin trailfocus (trailfocus)
Adding plugin scale (scale)
Adding plugin plane (plane)
Adding plugin crashhandler (crashhandler)
Adding plugin svg (svg)
Adding plugin move (move)
Adding plugin vpswitch (vpswitch)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin inotify (inotify)
Adding plugin opacify (opacify)
Adding plugin snap (snap)
Adding plugin winrules (winrules)
Adding plugin tile (tile)
Adding plugin fs (fs)
Adding plugin splash (splash)
Adding plugin put (put)
Adding plugin png (png)
Adding plugin thumbnail (thumbnail)
Adding plugin fadedesktop (fadedesktop)
Adding plugin mblur (mblur)
Adding plugin cube (cube)
Adding plugin wobbly (wobbly)
Adding plugin fade (fade)
Adding plugin minimize (minimize)
Adding plugin water (water)
Adding plugin text (text)
Initializing core options...done
Initializing imgjpeg options...done
Initializing ring options...done
Initializing zoom options...done
InitialDebug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
GTK Accessibility Module initialized

(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5780): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

Debug: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
Debug: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GTK Panel of SCIM 1.4.4

GTK Accessibility Module initialized

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized

(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-keyring-ask:5829): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)
** Message: <information>	You are now connected to the wireless network 'quologis2'.

GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gnome-system-log:5941): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-system-log:5941): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-system-log:5941): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-system-log:5941): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-system-log:5941): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-system-log:5941): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-system-log:5941): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-system-log:5941): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:5952): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gnome-terminal:6029): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-terminal:6029): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-terminal:6029): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-terminal:6029): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-terminal:6029): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-terminal:6029): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-terminal:6029): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-terminal:6029): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized

(Gecko:6052): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6230): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(yelp:6240): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(yelp:6240): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(yelp:6240): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(yelp:6240): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(yelp:6240): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(yelp:6240): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(yelp:6240): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(yelp:6240): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

** (yelp:6240): WARNING **: No listener with the specified listener id 1

** (yelp:6240): WARNING **: No listener with the specified listener id 2

** (yelp:6240): WARNING **: No listener with the specified listener id 3

** (yelp:6240): WARNING **: No listener with the specified listener id 4

** (yelp:6240): WARNING **: No listener with the specified listener id 5

** (yelp:6240): WARNING **: No listener with the specified listener id 6

** (yelp:6240): WARNING **: No listener with the specified listener id 7

** (yelp:6240): WARNING **: No listener with the specified listener id 8

** (yelp:6240): WARNING **: No listener with the specified listener id 9

** (yelp:6240): WARNING **: No listener with the specified listener id 10

** (yelp:6240): WARNING **: No listener with the specified listener id 11

** (yelp:6240): WARNING **: No listener with the specified listener id 12

** (yelp:6240): WARNING **: No listener with the specified listener id 13

** (yelp:6240): WARNING **: No listener with the specified listener id 14

** (yelp:6240): WARNING **: No listener with the specified listener id 15

** (yelp:6240): WARNING **: No listener with the specified listener id 16

** (yelp:6240): WARNING **: No listener with the specified listener id 17

** (yelp:6240): WARNING **: No listener with the specified listener id 18

** (yelp:6240): WARNING **: No listener with the specified listener id 19

** (yelp:6240): WARNING **: No listener with the specified listener id 20

** (yelp:6240): WARNING **: No listener with the specified listener id 21

** (yelp:6240): WARNING **: No listener with the specified listener id 22

** (yelp:6240): WARNING **: No listener with the specified listener id 23

** (yelp:6240): WARNING **: No listener with the specified listener id 24

** (yelp:6240): WARNING **: No listener with the specified listener id 25

** (yelp:6240): WARNING **: No listener with the specified listener id 26

** (yelp:6240): WARNING **: No listener with the specified listener id 27

** (yelp:6240): WARNING **: No listener with the specified listener id 28

(yelp:6240): GLib-CRITICAL **: g_hash_table_foreach_remove: assertion `hash_table != NULL' failed

(yelp:6240): GLib-CRITICAL **: g_hash_table_size: assertion `hash_table != NULL' failed
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-session-properties:6343): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)
/usr/lib/python2.5/site-packages/AppInstall/common.py:26: GtkWarning: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

  return theme.load_icon(icon, size, flags)

** (gnome-app-install:6635): WARNING **: return value of custom widget handler was not a GtkWidget

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1532: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized

(gksu:6665): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gksu:6665): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gksu:6665): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gksu:6665): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gksu:6665): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gksu:6665): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gksu:6665): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gksu:6665): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(synaptic:6667): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4

GTK Accessibility Module initialized

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(nautilus:5497): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(nautilus:5497): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field



(Gecko:6052): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(Gecko:6052): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

(synaptic:6667): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()
/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()
(synaptic:6667): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field
/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()
/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()


(synaptic:6667): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field

/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()
/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()
/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()

/usr/lib/python2.5/site-packages/AppInstall/PackageWorker.py:107: GtkWarning: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

  gtk.main_iteration()
(synaptic:6667): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(synaptic:6667): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(nm-applet:5608): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

GTK Accessibility Module initialized
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)
/usr/share/exaile/xl/panels.py:227: GtkWarning: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

  gtk.ICON_SIZE_SMALL_TOOLBAR)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

** ERROR **: file orbit-object.c: line 149 (do_unref): assertion failed: (robj->refs < ORBIT_REFCOUNT_MAX && robj->refs > 0)
aborting...

** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.

Plugins 'Update Notifier' version '0.2' loaded successfully
Checking in /home/schnupi/.exaile/plugins for egg plugins
<pkg_resources.Environment object at 0x8b5332c>
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x8b54020>}
Logging in to audioscrobbler
Using multimedia keys from: gnome
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/schnupi/.exaile/saved/playlist0001.m3u
Importing /home/schnupi/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0
Warning: Gstreamer equalizer element not found, please install the latest gst-plugins-bad package
updated plays 1, rating 1
Attempting to submit track Processed Beats from Kasabian by Kasabian to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-11%2021%3A43%3A19&b[0]=Kasabian&a[0]=Kasabian&u=schnupi&m[0]=&t[0]=Processed%20Beats&l[0]=187
2007-07-11 21:43:19: Uploaded 1 tracks successfully
next track was reported as  Reason Is Tre
** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.

ason from Kasabian by Kasabian
updated plays 1, rating 1
Attempting to submit track Test Transmission from Kasabian by Kasabian to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-11%2021%3A46%3A51&b[0]=Kasabian&a[0]=Kasabian&u=schnupi&m[0]=&t[0]=Test%20Transmission&l[0]=235
2007-07-11 21:46:51: Uploaded 1 tracks successfully
next track was reported as  Cutt Off from Kasabian by Kasabian
updated plays 1, rating 1
Attempting to submit track I.D from Kasabian by Kasabian to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-11%2021%3A51%3A13&b[0]=Kasabian&a[0]=Kasabian&u=schnupi&m[0]=&t[0]=I.D&l[0]=287
2007-07-11 21:51:14: Uploaded 1 tracks successfully
next track was reported as  L.S.F from Kasabian by Kasabian
updated plays 1, rating 1
Attempting to submit track Running Battle from Kasabian by Kasabian to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-11%2021%3A55%3A46&b[0]=Kasabian&a[0]=Kasabian&u=schnupi&m[0]=&t[0]=Running%20Battle&l[0]
** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

** (exaile.py:6746): WARNING **: failure: no device event controller found.


** (exaile.py:6746): WARNING **: failure: no device event controller found.


** (exaile.py:6746): WARNING **: failure: no device event controller found.


** (exaile.py:6746): WARNING **: failure: no device event controller found.


** (exaile.py:6746): WARNING **: failure: no device event controller found.


** (exaile.py:6746): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.

GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gcalctool:7722): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gcalctool:7722): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gcalctool:7722): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gcalctool:7722): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gcalctool:7722): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gcalctool:7722): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gcalctool:7722): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gcalctool:7722): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field


(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)
=255
2007-07-11 21:55:46: Uploaded 1 tracks successfully
next track was reported as  Test Transmission from Kasabian by Kasabian
updated plays 1, rating 1
Attempting to submit track Club Foot from Kasabian by Kasabian to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-11%2021%3A59%3A41&b[0]=Kasabian&a[0]=Kasabian&u=schnupi&m[0]=&t[0]=Club%20Foot&l[0]=215
2007-07-11 21:59:41: Uploaded 1 tracks successfully
next track was reported as  Processed Beats from Kasabian by Kasabian
updated plays 1, rating 1
Attempting to submit track Cutt Off from Kasabian by Kasabian to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-11%2022%3A03%3A48&b[0]=Kasabian&a[0]=Kasabian&u=schnupi&m[0]=&t[0]=Cutt%20Off&l[0]=277
2007-07-11 22:03:48: Uploaded 1 tracks successfully
next track was reported as  Butcher Blues from Kasabian by Kasabian
updated plays 1, rating 1
Attempting to submit track L.S.F from Kasabian by Kasabian to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-11%2022%3A07%3A45&b[0]=
(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:5492): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:5533): Wnck-WARNING **: Unhandled action type (nil)

** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.

Kasabian&a[0]=Kasabian&u=schnupi&m[0]=&t[0]=L.S.F&l[0]=197
2007-07-11 22:07:46: Uploaded 1 tracks successfully
next track was reported as  Running Battle from Kasabian by Kasabian
Last active is: 1
Exiting, bye!

** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


** (Gecko:6052): WARNING **: failure: no device event controller found.


...Too much output, ignoring rest...


```

---

### Post by bapoumba on 2007-07-12
Hmm..
May be try to get a backtrace running update-manager and file a bug report?
[https://wiki.ubuntu.com/Backtrace]("https://wiki.ubuntu.com/Backtrace")

---

### Post by Sabrage on 2007-08-21
This happens to me too, I think. When I click the *install updates" button the update manager window goes grey, but nothing happens. This only affects this window, not other programs.

Anyone found a solution? Maybe reinstall Update Manager? (if that is possible :confused:)

---

### Post by skew on 2007-12-16
I have the same issues here as well.    I stumbled upon a **partial fix**.  I discovered that when this happens (which is almost all the time) if I open the system monitor/processes and kill the ** gksu** process the update manager resumes doing what it's doing and finishes the task of checking for updates.  When I notice this occurring I need to do the proceeding very quickly before whole system freezes requiring a ctrl-alt-F3 (shell), login, run top (or in my case htop),  and kill the gksu process. 

 Maybe it's some bug with the gksu but for what it's worth I also have beryl and emerald running like a previous poster here also mentioned.  

I'd sure love to get  permanent fix to this though!

---

