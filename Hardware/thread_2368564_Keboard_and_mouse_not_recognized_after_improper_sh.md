---
title: "Keboard and mouse not recognized after improper shutdown."
date: 2017-08-12
forum: Hardware
---

### Post by nonbeing2 on 2017-08-12
I dual boot Ubuntu Gnome 17.04 and Windows 10, installed to separate  partitions on the same ssd. Ubuntu as my daily driver, windows for games and as a  backup.

Relevant Hardware:
CPU: i5-6500
MB: MSI B150M mortar
8 GB ram
Keyboard: Unicomp Model M ultra classic, usb
Mouse: Logitech M500 corded mouse, usb

So  basically, I've had some issues where for one reason or another, I have  to power down or reset because of ubuntu freezing (this is of course  only after attempting to solve the problem by other means, usually by  waiting, then attempting to kill the process with top on tty3, then using sysrq F, then  REISUB, in that order; I only power down if all of these fail, which is still at least once a week). Sometimes, when  rebooting after doing this, my keyboard and sometimes (but not always)  my mouse will be inactive upon booting. As in they don't even appear to  be receiving power from usb. Unplugging and replugging into the usb port  does not resolve the problem. Usually simply shutting down a few times  (properly if my mouse works, powering down if not) will fix this.  However, it's been resistant to repeated attempts today and in any case I  probably need to fix the root problem what with how frequent this is.

Usually  the keyboard will be inactive during the bios and grub as well, leaving  me unable to do anything but wait for it to boot into ubuntu. This  time, for some reason, the keyboard is working during those stages before it  shuts off once I reach ubuntu, so I can at least boot into windows. Windows recognizes the hardware fine and works with no problems. This suggests it's probably a linux/ubuntu problem rather than hardware/firmware.

Oh, and one more thing since I originally typed this. Yesterday, after the current bout of problems started, I somehow got it to recognize the hardware by replugging them. Used the pc for a while, then shut down **properly*.***Yet when I started up today it was back to not recognizing them and the re-plugging fix is not working. Using other usb ports doesn't work either.

I have not tried booting into safe mode. Partly because I have no ideas as to what I would actually *do* in safe mode once I got there.

Any ideas on what is causing this, how I can fix it, and/or how I can stop it from happening in the future?

TL;DR:
Sometimes  when I have to force-power-down my computer, it will not recognize the  keyboard or mouse after restart. Problem seems to mainly be on ubuntu  but has previously manifested in the bios-splash/grub.

---

### Post by DuckHook on 2017-08-12
[LIST=1]
[*]Are input devices connected directly into USB ports or through intervening devices like a hub or KVM switch?
[*]Have you tried different mice/keyboards?
[*]Have you ever tried reinstalling the OS?
[*]Do things run better on an LTS (16.04)? Try running xenial using a LiveUSB/DVD. Do same problems occur?
[*]What do your logs tell you? Especially syslog? You may need to peruse archived logs too.
[/LIST]
The solution in [this]("https://askubuntu.com/questions/772056/keyboard-stops-working-ubuntu-16-04") link may be useful. The concept of USB suspending improperly is explained in the link.

---

### Post by nonbeing2 on 2017-08-13
1. They are connected directly to the motherboard io panel
3. The OS has been reinstalled several times to deal with unrelated technical issues. The last time would have been this January, I believe. This problem is something I've been noticing for the last couple months, I'd say.
4. 16.04 is incompatible with my PC as it lacks the driver for polaris GPUs.

I will get back to you re: 2 and 4. If safe mode doesn't work, it should be fine to check syslog using windows, right? It would still be there from the last session? Are there any other logs I should check?

**Edit:**
So I started by trying my old mouse and keyboard (generic Dell usb). Plugged in other mouse, didn't work. Plugged in other keyboard, and... it both the mouse and keyboard worked. Plugged my main keyboard back in and it still worked. As I mentioned before, simply re-plugging the hardware, did fix it one other time, it's just that it doesn't fix it all or even most of the time, maybe like 25%.

Anyway, I am posting from the problematic pc right now, so I've saved a copy of the current /var/log/syslog to my home folder. I don't really know how to read it myself, so do you want me to just attach the whole thing? Does it contain any private info other than the name of my pc?

---

### Post by DuckHook on 2017-08-13
There is no easy way to read logs. I've been using Linux for years now and logs are still obscure arcane beasts out of the twelfth dimension. Well, I exaggerate—but only a little. Going through logs does tend to give you some idea of the boot process and an appreciation for the sheer number and complexity of processes that go into a working computing environment, but even gurus find going through them tedious. So, the usual practice is to filter logs through *grep*, looking only for items of interest. In your case, you can look for key words like "warning", "error", "usb", etc. There's some creativity involved in coming up with the terms that may be relevant.

Example:```
egrep -i 'warning|error|fatal|usb' /var/log/syslog
```
If you want to post your syslog, please post your output between [noparse]```
 and 
```[/noparse] tags for manageability. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Your logs might have some private info, like your NIC MAC address, WAN address, etc that you may wish to anonymize prior to posting. You will have to parse the logs to detect if such info exists and where it might be. Once again, *grep* will help, but there is no easy way to excise such info except to manually search through your logs for them.

Should you successfully boot to an environment with working peripherals, also post the output of:```
lsusb
``````
sudo lshw -C bus
``````
sudo lshw -C input
``````
xinput --list
```

Last, but not least, have you explored the solutions in my previous link?

---

### Post by nonbeing2 on 2017-08-15
First of all, here's what I got from searching my syslog (from my current session, which had the same problem as usual, solved by plugging in a different device temporarily) with the command you provided. Note that I was also experimenting with **solution 2** from the provided link, so that could be the source of some of these lines:

```
Aug 15 00:27:56 pc-name gnome-shell[2035]: Received error from DBus search provider org.gnome.Photos.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 15 00:28:34 pc-name kernel: [  498.492669] usb 1-9: USB disconnect, device number 9
Aug 15 00:28:40 pc-name gnome-shell[2035]: JS WARNING: [resource:///org/gnome/shell/ui/panel.js 342]: reference to undefined property this.menu.actionGroup
Aug 15 00:29:01 pc-name gnome-shell[2035]: Received error from DBus search provider org.gnome.Photos.desktop during GetResultMetas: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'org.gnome.Shell.SearchProvider2' on object at path /org/gnome/Photos/SearchProvider
Aug 15 00:30:05 pc-name kernel: [  588.692048] usb 1-9: new full-speed USB device number 10 using xhci_hcd
Aug 15 00:30:05 pc-name kernel: [  588.834620] usb 1-9: New USB device found, idVendor=17f6, idProduct=0822
Aug 15 00:30:05 pc-name kernel: [  588.834624] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 15 00:30:05 pc-name kernel: [  588.834627] usb 1-9: Product: Ruffian6_x Kbrd v3_xx
Aug 15 00:30:05 pc-name kernel: [  588.834629] usb 1-9: Manufacturer: Unicomp Inc
Aug 15 00:30:05 pc-name kernel: [  588.839089] input: Unicomp Inc Ruffian6_x Kbrd v3_xx as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:17F6:0822.0005/input/input23
Aug 15 00:30:05 pc-name mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9"
Aug 15 00:30:05 pc-name kernel: [  588.896368] hid-generic 0003:17F6:0822.0005: input,hidraw1: USB HID v1.11 Keyboard [Unicomp Inc Ruffian6_x Kbrd v3_xx] on usb-0000:00:14.0-9/input0
Aug 15 00:30:05 pc-name /usr/lib/gdm3/gdm-x-session[1829]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:17F6:0822.0005/input/input23/event17"
Aug 15 00:30:12 pc-name gnome-shell[2035]: JS WARNING: [resource:///org/gnome/shell/ui/keyboard.js 573]: reference to undefined property actor.extended_key
Aug 15 00:30:13 pc-name gnome-shell[2035]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.148 was not provided by any .service files
Aug 15 00:36:43 pc-name org.gnome.Shell.desktop[1219]: Window manager warning: Failed to set power save mode for output HDMI-1: Permission denied
Aug 15 00:36:43 pc-name gsd-sharing[2181]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Aug 15 00:36:43 pc-name gnome-shell[2035]: JS WARNING: [/home/username/.local/share/gnome-shell/extensions/gTile@vibou/hotkeys.js 47]: assignment to undeclared variable key
Aug 15 00:36:46 pc-name systemd-sleep[5214]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Aug 15 00:36:46 pc-name systemd-sleep[5215]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Aug 15 00:36:58 pc-name systemd-sleep[5214]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Aug 15 00:36:58 pc-name systemd-sleep[5309]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Aug 15 00:36:58 pc-name kernel: [  993.943185] usb 1-1: new full-speed USB device number 11 using xhci_hcd
Aug 15 00:37:03 pc-name kernel: [  999.251280] usb 1-1: device descriptor read/64, error -110
Aug 15 00:37:03 pc-name org.gnome.Shell.desktop[1219]: Window manager warning: Failed to set power save mode for output HDMI-1: Permission denied
Aug 15 00:37:08 pc-name gsd-sharing[2181]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Aug 15 00:37:08 pc-name gnome-shell[2035]: JS WARNING: [resource:///org/gnome/shell/gdm/util.js 331]: reference to undefined property this._preemptingService
Aug 15 00:37:19 pc-name kernel: [ 1014.863303] usb 1-1: device descriptor read/64, error -110
Aug 15 00:37:19 pc-name kernel: [ 1015.091293] usb 1-1: new full-speed USB device number 12 using xhci_hcd
Aug 15 00:37:24 pc-name kernel: [ 1020.239462] usb 1-1: device descriptor read/64, error -110
Aug 15 00:37:40 pc-name kernel: [ 1035.855544] usb 1-1: device descriptor read/64, error -110
Aug 15 00:37:40 pc-name kernel: [ 1036.083401] usb 1-1: new full-speed USB device number 13 using xhci_hcd
Aug 15 00:37:46 pc-name kernel: [ 1041.319474] usb 1-1: Device not responding to setup address.
Aug 15 00:37:46 pc-name kernel: [ 1041.527438] usb 1-1: device not accepting address 13, error -71
Aug 15 00:37:46 pc-name kernel: [ 1041.647387] usb 1-1: new full-speed USB device number 14 using xhci_hcd
Aug 15 00:37:51 pc-name kernel: [ 1046.951535] usb 1-1: Device not responding to setup address.
Aug 15 00:37:51 pc-name kernel: [ 1047.159465] usb 1-1: device not accepting address 14, error -71
Aug 15 00:37:51 pc-name kernel: [ 1047.159504] usb usb1-port1: unable to enumerate USB device
Aug 15 00:37:55 pc-name gnome-shell[2035]: JS WARNING: [resource:///org/gnome/shell/misc/history.js 72]: reference to undefined property this._historyIndex[this._history.length]
Aug 15 00:38:05 pc-name gnome-shell[2035]: JS WARNING: [resource:///org/gnome/shell/ui/modalDialog.js 311]: reference to undefined property global.gdk_screen
Aug 15 00:38:09 pc-name org.gnome.Shell.desktop[2035]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c00061 (rc.local ()
Aug 15 00:38:28 pc-name nautilus[5708]: Failed to register client: GDBus.Error:org.gnome.SessionManager.AlreadyRegistered: Unable to register client
Aug 15 00:38:28 pc-name xdg-document-portal[5718]:    unique: 6, error: -2 (No such file or directory), outsize: 16
Aug 15 00:38:28 pc-name xdg-document-portal[5718]:    unique: 7, error: -2 (No such file or directory), outsize: 16

```

lsusb:
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 17f6:0822 Unicomp, Inc 
Bus 001 Device 006: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

sudo lshw -C bus:
```
  *-core                    
       description: Motherboard
       product: B150M MORTAR (MS-7972)
       vendor: MSI
       physical id: 0
       version: 2.0
       serial: G616180755
       slot: Default string
  *-usb
       description: USB controller
       product: Sunrise Point-H USB 3.0 xHCI Controller
       vendor: Intel Corporation
       physical id: 14
       bus info: pci@0000:00:14.0
       version: 31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi xhci bus_master cap_list
       configuration: driver=xhci_hcd latency=0
       resources: irq:122 memory:dff10000-dff1ffff
     *-usbhost:0
          product: xHCI Host Controller
          vendor: Linux 4.10.0-32-generic xhci-hcd
          physical id: 0
          bus info: usb@1
          logical name: usb1
          version: 4.10
          capabilities: usb-2.00
          configuration: driver=hub slots=12 speed=480Mbit/s
     *-usbhost:1
          product: xHCI Host Controller
          vendor: Linux 4.10.0-32-generic xhci-hcd
          physical id: 1
          bus info: usb@2
          logical name: usb2
          version: 4.10
          capabilities: usb-3.00
          configuration: driver=hub slots=6 speed=5000Mbit/s
  *-serial UNCLAIMED
       description: SMBus
       product: Sunrise Point-H SMBus
       vendor: Intel Corporation
       physical id: 1f.4
       bus info: pci@0000:00:1f.4
       version: 31
       width: 64 bits
       clock: 33MHz
       configuration: latency=0
       resources: memory:dff2a000-dff2a0ff ioport:f000(size=32)


```

sudo lshw -C input:
```
 *-usb:0                   
       description: Mouse
       product: USB Laser Mouse
       vendor: Logitech
       physical id: 4
       bus info: usb@1:4
       version: 56.01
       capabilities: usb-2.00
       configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
  *-usb:1
       description: Keyboard
       product: Ruffian6_x Kbrd v3_xx
       vendor: Unicomp Inc
       physical id: 9
       bus info: usb@1:9
       version: 3.45
       capabilities: usb-2.00
       configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
```

xinput --list:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Unicomp Inc Ruffian6_x Kbrd v3_xx           id=10    [slave  keyboard (3)]


```

Now, as for the link. I started to go through with solution #2. When I reached the stage of editing /etc/rc.local, I noticed that no such file existed. A search on this revealed that this file is apparently not used by default since the switch to systemd. If I create the file by copypasting in the text from the post, will it still work? Or will I need to go through additional steps?

---

