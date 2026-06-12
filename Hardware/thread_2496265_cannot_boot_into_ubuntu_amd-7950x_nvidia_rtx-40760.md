---
title: "cannot boot into ubuntu amd-7950x nvidia rtx-40760 ti super msi x670e tomahawk"
date: 2024-03-20
forum: Hardware
---

### Post by RobertLos on 2024-03-20
Guys,
Build myself a new computer with the specs in the title. 128 GB RAM. Works fine on windows but booting into Ubuntu (i only use ubuntu since 2005 so just a beginner) hangs when it tries to load the gdm session. I am able to go into recovery mode.
I run the latest kernel 6.5 and nivida driver-550.
What can be wrong and what are the steps to resolve this.

I attach an except of my journalctl log that shows the error.
mrt 21 00:03:36 robert-rlccs rtkit-daemon[1417]: Successfully made thread 1451 of process 1406 owned by '128' RT at priority 20.
mrt 21 00:03:36 robert-rlccs rtkit-daemon[1417]: Supervising 4 threads of 3 processes of 1 users.
mrt 21 00:03:36 robert-rlccs audit[1409]: AVC apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/21184/usr/lib/snapd/snap-confine" pid=1409 comm="snap-confine" capability=12  capname="net_admin"
mrt 21 00:03:36 robert-rlccs audit[1409]: AVC apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/21184/usr/lib/snapd/snap-confine" pid=1409 comm="snap-confine" capability=38  capname="perfmon"
mrt 21 00:03:36 robert-rlccs kernel: kauditd_printk_skb: 42 callbacks suppressed
mrt 21 00:03:36 robert-rlccs kernel: audit: type=1400 audit(1710975816.927:56): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/21184/usr/lib/snapd/snap-confine" pid=1409 comm="snap-confine" capability=12  capname="net_admin"
mrt 21 00:03:36 robert-rlccs kernel: audit: type=1400 audit(1710975816.927:57): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/21184/usr/lib/snapd/snap-confine" pid=1409 comm="snap-confine" capability=38  capname="perfmon"
mrt 21 00:03:36 robert-rlccs systemd[1]: tmp-snap.rootfs_yVQswv.mount: Deactivated successfully.
mrt 21 00:03:36 robert-rlccs gnome-session[1440]: gnome-session-binary[1440]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
mrt 21 00:03:36 robert-rlccs gnome-session[1440]: gnome-session-binary[1440]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
mrt 21 00:03:36 robert-rlccs gnome-session-binary[1440]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
mrt 21 00:03:36 robert-rlccs gnome-session-binary[1440]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
mrt 21 00:03:37 robert-rlccs gnome-shell[1464]: Running GNOME Shell (using mutter 42.9) as a Wayland display server
mrt 21 00:03:37 robert-rlccs gnome-shell[1464]: Device '/dev/dri/card0' prefers shadow buffer
mrt 21 00:03:37 robert-rlccs gnome-shell[1464]: Added device '/dev/dri/card0' (amdgpu) using atomic mode setting.
mrt 21 00:03:37 robert-rlccs org.gnome.Shell.desktop[1464]: Failed to setup: No GPUs with outputs found
mrt 21 00:03:37 robert-rlccs gnome-session[1440]: gnome-session-binary[1440]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
mrt 21 00:03:37 robert-rlccs gnome-session-binary[1440]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-wayland-session[1439]: dbus-daemon[1439]: [session uid=128 pid=1439] Activating service name='ca.desrt.dconf' requested by ':1.2' (uid=128 pid=1440 comm="/usr/libexec/gnome-session-binary --autostart /usr" label="unconfined")
mrt 21 00:03:37 robert-rlccs gnome-session-binary[1440]: Unrecoverable failure in required component org.gnome.Shell.desktop
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-wayland-session[1439]: dbus-daemon[1439]: [session uid=128 pid=1439] Successfully activated service 'ca.desrt.dconf'
mrt 21 00:03:37 robert-rlccs gdm-launch-environment][1394]: pam_unix(gdm-launch-environment:session): session closed for user gdm
mrt 21 00:03:37 robert-rlccs gdm-launch-environment][1394]: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: GdmDisplay: Session never registered, failing
mrt 21 00:03:37 robert-rlccs systemd[1]: session-c1.scope: Deactivated successfully.
mrt 21 00:03:37 robert-rlccs systemd-logind[988]: Session c1 logged out. Waiting for processes to exit.
mrt 21 00:03:37 robert-rlccs systemd-logind[988]: Removed session c1.
mrt 21 00:03:37 robert-rlccs gdm3[1486]: /sbin/prime-switch: 22: /usr/bin/gpu-manager: not found
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: Child process -1415 was already dead.
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: GdmDisplay: Session never registered, failing
mrt 21 00:03:37 robert-rlccs gdm3[1491]: /sbin/prime-switch: 22: /usr/bin/gpu-manager: not found
mrt 21 00:03:37 robert-rlccs snapd-desktop-integration.snapd-desktop-integration[1409]: Sorry, home directories outside of /home needs configuration.
mrt 21 00:03:37 robert-rlccs snapd-desktop-integration.snapd-desktop-integration[1409]: See [https://forum.snapcraft.io/t/11209](https://forum.snapcraft.io/t/11209) for details.
mrt 21 00:03:37 robert-rlccs systemd[1399]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Main process exited, code=exited, status=1/FAILURE
mrt 21 00:03:37 robert-rlccs systemd[1399]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Failed with result 'exit-code'.
mrt 21 00:03:37 robert-rlccs gdm3[1504]: /sbin/prime-switch: 22: /usr/bin/gpu-manager: not found
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: Child process -1415 was already dead.
mrt 21 00:03:37 robert-rlccs gdm-launch-environment][1488]: pam_unix(gdm-launch-environment:session): session opened for user gdm(uid=128) by (uid=0)
mrt 21 00:03:37 robert-rlccs systemd-logind[988]: New session c2 of user gdm.
mrt 21 00:03:37 robert-rlccs rtkit-daemon[1417]: Supervising 4 threads of 3 processes of 1 users.
mrt 21 00:03:37 robert-rlccs systemd[1]: Started Session c2 of User gdm.
mrt 21 00:03:37 robert-rlccs rtkit-daemon[1417]: Successfully made thread 1508 of process 1408 owned by '128' RT at priority 5.
mrt 21 00:03:37 robert-rlccs rtkit-daemon[1417]: Supervising 5 threads of 3 processes of 1 users.
mrt 21 00:03:37 robert-rlccs systemd[1399]: Started Sound Service.
mrt 21 00:03:37 robert-rlccs systemd[1399]: Reached target Main User Target.
mrt 21 00:03:37 robert-rlccs systemd[1399]: Startup finished in 404ms.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (--) Log file renamed from "/var/lib/gdm3/.local/share/xorg/Xorg.pid-1512.log" to "/var/lib/gdm3/.local/share/xorg/Xorg.0.log"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: X.Org X Server 1.21.1.4
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: X Protocol Version 11, Revision 0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: Current Operating System: Linux robert-rlccs 6.5.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Mar 12 10:22:43 UTC 2 x86_64
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-26-generic root=UUID=fa05fc37-e8d4-4877-a1ee-779cbb4aed7c ro nosplash
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: xorg-server 2:21.1.4-2ubuntu1.7~22.04.8 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: Current version of pixman: 0.40.0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         to make sure that you have the latest version.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: Markers: (--) probed, (**) from config file, (==) default setting,
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         (++) from command line, (!!) notice, (II) informational,
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Log file: "/var/lib/gdm3/.local/share/xorg/Xorg.0.log", Time: Thu Mar 21 00:03:37 2024
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Using system config directory "/usr/share/X11/xorg.conf.d"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) No Layout section.  Using the first Screen section.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) No screen section available. Using defaults.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (**) |-->Screen "Default Screen Section" (0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (**) |   |-->Monitor "<default monitor>"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) No monitor specified for screen "Default Screen Section".
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Using a default monitor configuration.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Automatically adding devices
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Automatically enabling devices
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Automatically adding GPU devices
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Automatically binding GPU devices
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Max clients allowed: 256, resource mask: 0x1fffff
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Entry deleted from font path.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Entry deleted from font path.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Entry deleted from font path.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Entry deleted from font path.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Entry deleted from font path.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) FontPath set to:
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         /usr/share/fonts/X11/misc,
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         /usr/share/fonts/X11/Type1,
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         built-ins
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) ModulePath set to "/usr/lib/xorg/modules"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) The server relies on udev to provide the list of input devices.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         If no devices become available, reconfigure udev or disable AutoAddDevices.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Loader magic: 0x5bcda1155020
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Module ABI versions:
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         X.Org ANSI C Emulation: 0.4
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         X.Org Video Driver: 25.2
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         X.Org XInput driver : 24.4
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         X.Org Server Extension : 10.0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (++) using VT number 1
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) systemd-logind: took control of session /org/freedesktop/login1/session/c2
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) xfree86: Adding drm device (/dev/dri/card0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Platform probe for /sys/devices/pci0000:00/0000:00:08.1/0000:16:00.0/drm/card0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 14 paused 0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (--) PCI:*(1@0:0:0) 10de:2705:1771:10de rev 161, Mem @ 0xf4000000/16777216, 0xf800000000/17179869184, 0xfc00000000/33554432, I/O @ 0x0000f000/128, BIOS @ 0x????????/524288
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (--) PCI: (22@0:0:0) 1002:164e:1462:7e12 rev 193, Mem @ 0xfc10000000/268435456, 0xfc20000000/2097152, 0xf5e00000/524288, I/O @ 0x0000d000/256
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "glx"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Module glx: vendor="X.Org Foundation"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         compiled for 1.21.1.4, module version = 1.0.0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         ABI class: X.Org Server Extension, version 10.0
mrt 21 00:03:37 robert-rlccs kernel: usb 3-2: reset high-speed USB device number 2 using xhci_hcd
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched ati as autoconfigured driver 0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched nouveau as autoconfigured driver 1
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched modesetting as autoconfigured driver 2
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched fbdev as autoconfigured driver 3
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched vesa as autoconfigured driver 4
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Assigned the driver to the xf86ConfigLayout
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "ati"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module ati
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "ati" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "nouveau"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module nouveau
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "nouveau" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "modesetting"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Module modesetting: vendor="X.Org Foundation"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         compiled for 1.21.1.4, module version = 1.21.1
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Module class: X.Org Video Driver
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         ABI class: X.Org Video Driver, version 25.2
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "fbdev"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module fbdev
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "fbdev" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "vesa"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module vesa
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "vesa" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched ati as autoconfigured driver 0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched nouveau as autoconfigured driver 1
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched modesetting as autoconfigured driver 2
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched fbdev as autoconfigured driver 3
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Matched vesa as autoconfigured driver 4
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (==) Assigned the driver to the xf86ConfigLayout
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "ati"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module ati
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "ati" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "nouveau"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module nouveau
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "nouveau" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "modesetting"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Module modesetting: vendor="X.Org Foundation"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         compiled for 1.21.1.4, module version = 1.21.1
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         Module class: X.Org Video Driver
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:         ABI class: X.Org Video Driver, version 25.2
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) UnloadModule: "modesetting"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Unloading modesetting
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) Failed to load module "modesetting" (already loaded, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "fbdev"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module fbdev
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "fbdev" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) LoadModule: "vesa"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Warning, couldn't open module vesa
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Failed to load module "vesa" (module does not exist, 0)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) modesetting: Driver for Modesetting Kernel Drivers: kms
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) Falling back to old probe method for modesetting
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) modeset(1): using default device
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) modeset(G0): using drv /dev/dri/card0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Screen 0 deleted because of no matching config section.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (II) UnloadModule: "modesetting"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: Fatal server error:
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: Please consult the The X.Org Foundation support
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:          at [http://wiki.x.org](http://wiki.x.org)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]:  for help.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Please also check the log file at "/var/lib/gdm3/.local/share/xorg/Xorg.0.log" for additional information.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE)
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1512]: (EE) Server terminated with error (1). Closing log file.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1509]: Unable to run X server
mrt 21 00:03:37 robert-rlccs gdm-launch-environment][1488]: pam_unix(gdm-launch-environment:session): session closed for user gdm
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: GdmDisplay: Session never registered, failing
mrt 21 00:03:37 robert-rlccs gdm-launch-environment][1488]: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
mrt 21 00:03:37 robert-rlccs systemd[1]: session-c2.scope: Deactivated successfully.
mrt 21 00:03:37 robert-rlccs systemd-logind[988]: Session c2 logged out. Waiting for processes to exit.
mrt 21 00:03:37 robert-rlccs systemd-logind[988]: Removed session c2.
mrt 21 00:03:37 robert-rlccs gdm3[1515]: /sbin/prime-switch: 22: /usr/bin/gpu-manager: not found
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: Child process -1509 was already dead.
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: GdmDisplay: Session never registered, failing
mrt 21 00:03:37 robert-rlccs gdm3[1520]: /sbin/prime-switch: 22: /usr/bin/gpu-manager: not found
mrt 21 00:03:37 robert-rlccs gdm3[1525]: /sbin/prime-switch: 22: /usr/bin/gpu-manager: not found
mrt 21 00:03:37 robert-rlccs gdm3[1109]: Gdm: Child process -1509 was already dead.
mrt 21 00:03:37 robert-rlccs gdm-launch-environment][1517]: pam_unix(gdm-launch-environment:session): session opened for user gdm(uid=128) by (uid=0)
mrt 21 00:03:37 robert-rlccs systemd-logind[988]: New session c3 of user gdm.
mrt 21 00:03:37 robert-rlccs systemd[1]: Started Session c3 of User gdm.
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1530]: (--) Log file renamed from "/var/lib/gdm3/.local/share/xorg/Xorg.pid-1530.log" to "/var/lib/gdm3/.local/share/xorg/Xorg.0.log"
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1530]: X.Org X Server 1.21.1.4
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1530]: X Protocol Version 11, Revision 0
mrt 21 00:03:37 robert-rlccs /usr/libexec/gdm-x-session[1530]: Current Operating System: Linux robert-rlccs 6.5.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Mar 12 10:22:43 UTC 2 x86_64

---

