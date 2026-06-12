---
title: "Ubuntu 16.04 login loop and errors"
date: 2017-05-22
forum: Hardware
---

### Post by scojopa on 2017-05-22
I have a fresh install of Ubuntu 16.04 / 4.8.0-51-generic
I have been having issues with two external monitors initializing when docking the machine. 
This morning I was unable to login. Entering password just brought me back to login screen. 

I change the permissions on .Xauthority to add the local user account. 

That got me back into the desktop. 

Looking at the logs Can someone help me troubleshoot this? my system is using EFI and is dualboot. 

/dev/sda1 EFI
/dev/sda2 / (ubuntu 16.04)
/dev/sda3 /home (ubuntu 16.04)
/dev/sda4  swap (ubuntu 16.04
/dev/sda5 / (kali)
/dev/sda6 /home (kali)
/dev/sda7 swap (kali)


fstab shows / with errors=remount-ro
```
# / was on /dev/sda2 during installation
UUID=d1f6b5d2-044b-42dd-b9be-73beaa7b431d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
```


dmesg | grep mount shows 
```

[    4.574344] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    4.784198] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    4.898023] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    6.566460] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    7.236606] audit: type=1400 audit(1495451131.544:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/1689/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=744 comm="apparmor_parser"
[   97.094216] audit: type=1400 audit(1495451221.404:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/snap/core/1689/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=1038 comm="apparmor_parser"

```


dmesg | grep failed shows
```

[    0.482153] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
[    5.072296] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[    5.072311] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[    5.076562] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-22.ucode failed with error -2
[    5.282493] thermal thermal_zone3: failed to read out thermal zone (-5)
[  110.747821] vmmon: module verification failed: signature and/or required key missing - tainting kernel
[  264.285108] usb 1-7:1.0: rebind failed: -517
[  264.285116] usb 1-7:1.1: rebind failed: -517
[  264.314269] thermal thermal_zone3: failed to read out thermal zone (-5)
[  265.801546] Bluetooth: hci0: Setting Intel event mask failed (-16)

```
syslog shows

```
May 22 07:31:31 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device/start timed out.
May 22 07:31:31 777 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device.
May 22 07:31:31 777 systemd[1]: Dependency failed for /dev/disk/by-uuid/b3a6a9cb-fb5e-4512-bd87-aac467710e67.
May 22 07:31:31 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.swap: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.swap/start failed with result 'dependency'.
May 22 07:31:31 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device/start failed with result 'timeout'.


```

blkid:
```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/sda1: UUID="E659-68F1" TYPE="vfat" PARTUUID="da06d867-fd8e-4786-b5ea-1bfb650c4e41"
/dev/sda2: UUID="d1f6b5d2-044b-42dd-b9be-73beaa7b431d" TYPE="ext4" PARTUUID="d6ba3047-9ce0-4dfb-9c8b-dcbdacbb32af"
/dev/sda3: UUID="954f4cde-bf7c-42b2-88b7-ac99f6f7044e" TYPE="ext4" PARTUUID="d493d77a-266c-47c8-be0b-bd69cc9621c2"
/dev/sda4: UUID="618fc87d-99a7-4ca3-864a-5b549f65dfb9" TYPE="swap" PARTUUID="208526c7-ba9d-47b3-b692-0f674ce59476"
/dev/sda5: UUID="a48499d1-0fde-4f66-9e20-1b7ff0d373ad" TYPE="ext4" PARTUUID="fb2664e0-e931-456b-a48e-163a13612b7a"
/dev/sda6: UUID="b41cceba-f523-4b80-a88c-da7c6870e0ed" TYPE="ext4" PARTUUID="b6d9fb52-f0cc-43cd-9fe2-f524437e1f96"
/dev/sda7: UUID="1b0f5320-6151-408d-908d-3e8208c36283" TYPE="swap" PARTUUID="af874e70-9880-4ac0-8cb2-f5e3e2c72f4e"

```

cat syslog | grep error
```
May 22 05:43:37 777 systemd-sleep[12509]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
May 22 05:43:37 777 systemd-sleep[12510]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
May 22 06:45:31 777 org.freedesktop.Notifications[1629]: ** (notify-osd:5430): WARNING **: dnd_is_screensaver_active(): Got error "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
May 22 06:45:31 777 systemd-sleep[12509]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
May 22 06:45:31 777 systemd-sleep[12592]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
May 22 06:45:32 777 bluetoothd[853]: gatt-time-server: Input/output error (5)
May 22 06:48:12 777 org.freedesktop.Notifications[1629]: ** (notify-osd:5430): WARNING **: dnd_is_screensaver_active(): Got error "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
May 22 06:48:19 777 systemd-sleep[16346]: /lib/systemd/system-sleep/wpasupplicant failed with error code 254.
Binary file (standard input) matches

```cat syslog | grep failed
```
May 22 05:18:24 777 colord[964]: (colord:964): Cd-WARNING **: failed to get session [pid 12041]: No such device or address
May 22 05:18:53 777 systemd[1]: Dependency failed for /dev/disk/by-uuid/b3a6a9cb-fb5e-4512-bd87-aac467710e67.
May 22 05:18:53 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.swap: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.swap/start failed with result 'dependency'.
May 22 05:18:53 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device/start failed with result 'timeout'.
May 22 05:43:37 777 systemd-sleep[12510]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
May 22 06:45:31 777 kernel: [23744.373418] usb 1-7:1.0: rebind failed: -517
May 22 06:45:31 777 kernel: [23744.373422] usb 1-7:1.1: rebind failed: -517
May 22 06:45:31 777 kernel: [23744.382149] thermal thermal_zone3: failed to read out thermal zone (-5)
May 22 06:45:31 777 systemd-sleep[12592]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
May 22 06:45:31 777 wpa_supplicant[1059]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
May 22 06:45:32 777 kernel: [23746.038286] Bluetooth: hci0: Setting Intel event mask failed (-16)
May 22 06:45:32 777 bluetoothd[853]: Sap driver initialization failed.
May 22 06:45:39 777 colord[964]: (colord:964): Cd-WARNING **: failed to get session [pid 12691]: No such device or address
May 22 06:46:03 777 NetworkManager[891]: <warn>  [1495449963.0823] (cdc-wdm1) failed to enable modem: GDBus.Error:org.freedesktop.libmbim.Error.Status.Failure: Failure
May 22 06:46:56 777 systemd[1]: Dependency failed for /dev/disk/by-uuid/b3a6a9cb-fb5e-4512-bd87-aac467710e67.
May 22 06:46:56 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.swap: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.swap/start failed with result 'dependency'.
May 22 06:46:56 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device/start failed with result 'timeout'.
May 22 06:47:19 777 gnome-session[15885]: pa_context_connect() failed: Connection refused
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_object_notify: assertion 'G_IS_OBJECT (object)' failed
May 22 06:47:19 777 gnome-session[15885]: (process:16086): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
May 22 06:48:19 777 systemd-sleep[16346]: /lib/systemd/system-sleep/wpasupplicant failed with error code 254.
Binary file (standard input) matches

```/var/log$ cat syslog | grep timeout
```
May 22 05:18:53 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device/start failed with result 'timeout'.
May 22 06:45:31 777 kernel: [23743.158130] xhci_hcd 0000:00:14.0: port 8 resume PLC timeout
May 22 06:45:31 777 kernel: [23743.175628] xhci_hcd 0000:00:14.0: port 6 resume PLC timeout
May 22 06:45:31 777 kernel: [23743.192971] xhci_hcd 0000:00:14.0: port 1 resume PLC timeout
May 22 06:45:31 777 org.freedesktop.Notifications[1629]: ** (notify-osd:5430): WARNING **: dnd_is_screensaver_active(): Got error "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
May 22 06:45:34 777 NetworkManager[891]: <info>  [1495449934.6296] dhcp4 (enp0s31f6): activation: beginning transaction (timeout in 45 seconds)
May 22 06:46:56 777 systemd[1]: dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device: Job dev-disk-by\x2duuid-b3a6a9cb\x2dfb5e\x2d4512\x2dbd87\x2daac467710e67.device/start failed with result 'timeout'.
May 22 06:48:12 777 org.freedesktop.Notifications[1629]: ** (notify-osd:5430): WARNING **: dnd_is_screensaver_active(): Got error "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
Binary file (standard input) matches




```

---

### Post by scojopa on 2017-05-22
One thing I noticed was my /swap UUID in fstab was incorrect according to blkid 
I fixed that an improved boot time.

But now seeing a lot of errors relating to gnome
```

gnome-session[2198]: ** (zeitgeist-datahub:2551): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required

```

```

com.canonical.Unity.Scope.Applications[2023]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
May 22 08:46:01 777 com.canonical.Unity.Scope.Applications[2023]: (unity-scope-loader:2992): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed

```


```

gnome-session[2198]: (gnome-software:2407): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

```

```

org.a11y.Bus[2023]: ** (process:2145): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

Thanks,

---

