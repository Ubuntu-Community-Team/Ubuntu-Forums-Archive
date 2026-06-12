---
title: "Black boxes after install 9.04 on my AAO"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by ADDJ on 2009-04-29
Hi guys this si my first post, im Antonio David from Seville [Spain] and i have a big problem

im studing at the university operating sistems careers and i need my laptop :P

ok, the problem:

i was using ubuntu 8.10 and all perfect[ ubuntu is the best] but when i updated and later , clean intall ubuntu 9.04 , with my user i have a problem, when i log with it , where i pass the pointer puts in black! if i push on applications, a black box... if i push alt+F , black boxes... All the same!!! but from error tester terminal, i added a user, and when i log with it, ubun tu 9.04 works fine !!

how i can solve this?

Please help me guys.

********************************EDITTTTTTTTTTTTTTTTTTTT***************************


Here are the XORGSESSSION ERROR


/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=es_ES.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-fmPszk/socket
SSH_AUTH_SOCK=/tmp/keyring-fmPszk/socket.ssh
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
I/O warning : failed to load external entity "/home/addj69/.compiz/session/1036a80a12cb44a8ad124101926364691300000049220022"
** (gnome-panel:5135): DEBUG: Adding applet 0.
** (gnome-panel:5135): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:5135): DEBUG: Adding applet 1.
** (gnome-panel:5135): DEBUG: Adding applet 2.
** (gnome-panel:5135): DEBUG: Adding applet 3.
** (gnome-panel:5135): DEBUG: Adding applet 4.
** (gnome-panel:5135): DEBUG: Adding applet 5.
** (gnome-panel:5135): DEBUG: Adding applet 6.
** (gnome-panel:5135): DEBUG: Adding applet 7.
** Message: <info>  No keyring secrets found for ConexiÃ³n inalÃ¡mbrica 1/802-11-wireless-security; asking user.

** (gnome-panel:5135): DEBUG: Adding applet 8.
** (gnome-panel:5135): DEBUG: Adding applet 9.
** (gnome-panel:5135): DEBUG: Adding applet 10.

(gnome-panel:5135): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:5135): DEBUG: Adding applet 11.

** (nautilus:5136): WARNING **: Unable to add monitor: No soportado
Nautilus-Share-Message: Called "net usershare info" but it failed: La Â«red compartidaÂ» devolviÃ³ el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero Ã³ directorio
Please ask your system administrator to enable user sharing.

[B]/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
** (nm-applet:5144): DEBUG: applet_common_device_state_changed
** (nm-applet:5144): DEBUG: old state indicates that this was not a disconnect 0[/B]
** (nm-applet:5144): DEBUG: applet_common_device_state_changed
Starting gtk-window-decorator
** (nm-applet:5144): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 30304 1241049600 1241019296
evolution-alarm-notify-Message:  Thu Apr 30 02:00:00 2009

evolution-alarm-notify-Message:  Wed Apr 29 17:34:56 2009

** (nm-applet:5144): DEBUG: applet_common_device_state_changed
** (nm-applet:5144): DEBUG: applet_common_device_state_changed
** (nm-applet:5144): DEBUG: applet_common_device_state_changed
** (nm-applet:5144): DEBUG: applet_common_device_state_changed
** (nm-applet:5144): DEBUG: foo_client_state_changed_cb
** (update-notifier:5141): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
*************************************************************************************


Some help pleasE? i put in [   b  ]  possible error


REALLY THANKS !

---

### Post by ADDJ on 2009-04-29
bump

---

### Post by ADDJ on 2009-04-29
Xorg error session says errors adding appllets 10 with glade interface, and applet 11,and dont add 12 and 13

---

### Post by ADDJ on 2009-04-29
My own solved...

log in terminal session 

gnome-panel

and activate EXTRA in appearance.... voilá

---

