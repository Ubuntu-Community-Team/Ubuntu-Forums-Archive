---
title: "xserver-xgl not working with Radeon X1100 (a/k/a xpress200)"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by swingerman on 2007-12-01
Hello!

I'm having trouble using the Xgl xserver on my laptop.  My card is an ATI Xpress 1100 (a/k/a an xpress200).

Info from lspci -v:

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0367
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 19
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2

Here's the relevant information from my lsmod:

pfeil@hawking:~$ lsmod | grep rade
radeon                125472  2 
drm                    83348  3 radeon
pfeil@hawking:~$ lsmod | grep agp
ati_agp                10124  0 
agpgart                35016  2 drm,ati_agp

I'm running  a fresh install of Ubuntu Gutsy Gibbon (7.10).

When I log in after installing xserver-xgl, it starts to log in and then immediately crashes and kicks me out.  Here's the output from my .xsession-errors.  I'm especially concerned with the failed assertion.  I will attach my xorg.conf ASAP.

<.xsession-errors>
(process:13143): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:13147): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Warning, xpress200 detected.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/hawking:/tmp/.ICE-unix/13140
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
Initializing gnome-mount extension
Initializing nautilus-share extension
Initializing nautilus-open-terminal extension


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...

** (trackerd:13254): WARNING **: Tracker daemon is already running - exiting
Initializing nautilus-image-converter extension
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 29689 1196553600 1196523911
evolution-alarm-notify-Message:  Sat Dec  1 19:00:00 2007

evolution-alarm-notify-Message:  Sat Dec  1 10:45:11 2007

Nautilus-Share-Message: REFRESHING SHARES
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: spawn arg "net"
Nautilus-Share-Message: spawn arg "usershare"
Nautilus-Share-Message: spawn arg "info"
Nautilus-Share-Message: end of spawn args; SPAWNING

Nautilus-Share-Message: returned from spawn: SUCCESS: 
Nautilus-Share-Message: exit code 255
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: usershares are currently disabled

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Xgl: r300_emit.c:403: r300EmitArrays: Assertion `((inputs_bitset)[((_TNL_ATTRIB_COLOR0) / (sizeof (GLuint) * 8))] & (1 << ((_TNL_ATTRIB_COLOR0) % (sizeof (GLuint) * 8))))' failed.
The application 'nautilus' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'vino-session' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gtk-window-decorator' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'bluetooth-applet' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'evolution-alarm-notify' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'nm-applet' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'applet.py' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
X connection to :2.0 broken (explicit kill or server shutdown).
The application 'update-notifier' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
Aborted (core dumped)
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Sat Dec  1 19:00:00 2007
 
The application 'x-session-manager' lost its connection to the display :2.0;
most likely the X server was shut down or you killed/destroyed
the application.
</.xsession-errors>

Thank you very much!

--Jason

---

