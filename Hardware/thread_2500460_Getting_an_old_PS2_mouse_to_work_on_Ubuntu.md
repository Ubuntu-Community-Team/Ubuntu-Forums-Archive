---
title: "Getting an old PS/2 mouse to work on Ubuntu"
date: 2024-09-02
forum: Hardware
---

### Post by bucephalusstudios on 2024-09-02
Hi everyone, I've got an interesting problem for you today.

I'm on a Ubuntu 22.04.4 LTS machine without those old PS/2 ports and I'm trying to get an old PS/2 mouse and keyboard to work on the machine by using a USB adapter. The reason for this is that I'm an exhibitor at a retro game convention and I'd like to show off a game with some old-looking peripherals.

The vintage PS/2 keyboard I bought off ebay works great, but the PS/2 mouse was not working on start up. Movement and clicking is unresponsive. 

I ran the following commands to diagnose the potential problems:

> sudo dmesg | grep -i mouse
[sudo] password for jeff: 
[    0.502228] mousedev: PS/2 mouse device common for all mice
[    1.640475] input: DLL077C:00 06CB:7E92 Mouse as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-2/i2c-DLL077C:00/0018:06CB:7E92.0001/input/input7
[    1.640679] hid-generic 0018:06CB:7E92.0001: input,hidraw0: I2C HID v1.00 Mouse [DLL077C:00 06CB:7E92] on i2c-DLL077C:00
[    2.308373] input: Barcode Reader  Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.1/0003:13BA:0018.0003/input/input11
[    2.361444] hid-generic 0003:13BA:0018.0003: input,hidraw2: USB HID v1.10 Mouse [Barcode Reader ] on usb-0000:00:14.0-2/input1
[   15.331848] psmouse serio1: Failed to deactivate mouse on isa0060/serio1: -5
[   15.803867] psmouse serio1: Failed to enable mouse on isa0060/serio1
[   20.147896] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
[   20.355851] psmouse serio1: Failed to enable mouse on isa0060/serio1
[   29.667439] input: DLL077C:00 06CB:7E92 Mouse as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-2/i2c-DLL077C:00/0018:06CB:7E92.0001/input/input16
[   29.667706] hid-multitouch 0018:06CB:7E92.0001: input,hidraw0: I2C HID v1.00 Mouse [DLL077C:00 06CB:7E92] on i2c-DLL077C:00


It looks like Ubuntu found the mouse but failed to try to enable it.

> jeff@baryshnikov:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Barcode Reader  Mouse                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; Barcode Reader  Consumer Control            id=14    [slave  pointer  (2)]
&#9116;   &#8627; DLL077C:00 06CB:7E92 Mouse                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; DLL077C:00 06CB:7E92 Touchpad               id=16    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=21    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Barcode Reader                              id=11    [slave  keyboard (3)]
    &#8627; Barcode Reader  System Control              id=13    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=17    [slave  keyboard (3)]
    &#8627; Intel HID 5 button array                    id=18    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=19    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=20    [slave  keyboard (3)]
    &#8627; Barcode Reader  Consumer Control            id=22    [slave  keyboard (3)]


xinput sees the mouse too!

> sudo journalctl -xe
&#9617;&#9617; Subject: A start job for unit UNIT has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit UNIT has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 629.
Aug 30 15:30:01 baryshnikov CRON[6191]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Aug 30 15:30:01 baryshnikov CRON[6192]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Aug 30 15:30:01 baryshnikov CRON[6191]: pam_unix(cron:session): session closed for user root
Aug 30 15:30:06 baryshnikov systemd[1]: Started Run anacron jobs.
&#9617;&#9617; Subject: A start job for unit anacron.service has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit anacron.service has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 2376.
Aug 30 15:30:06 baryshnikov anacron[6205]: Anacron 2.3 started on 2024-08-30
Aug 30 15:30:06 baryshnikov anacron[6205]: Normal exit (0 jobs run)
Aug 30 15:30:06 baryshnikov systemd[1]: anacron.service: Deactivated successfully.
&#9617;&#9617; Subject: Unit succeeded
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit anacron.service has successfully entered the 'dead' state.
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: (EE) event6  - DLL077C:00 06CB:7E92 Touchpad: kernel bug: Touch jump detected and discarded.
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: See [https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html](https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html) for details
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: (EE) event6  - DLL077C:00 06CB:7E92 Touchpad: kernel bug: Touch jump detected and discarded.
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: See [https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html](https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html) for details
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: (EE) event6  - DLL077C:00 06CB:7E92 Touchpad: kernel bug: Touch jump detected and discarded.
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: See [https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html](https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html) for details
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: (EE) event6  - DLL077C:00 06CB:7E92 Touchpad: kernel bug: Touch jump detected and discarded.
Aug 30 15:30:14 baryshnikov /usr/libexec/gdm-x-session[3365]: See [https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html](https://wayland.freedesktop.org/libinput/doc/1.20.0/touchpad-jumping-cursors.html) for details
Aug 30 15:30:36 baryshnikov sudo[6221]:     jeff : TTY=pts/0 ; PWD=/home/jeff ; USER=root ; COMMAND=/usr/sbin/modprobe psmouse
Aug 30 15:30:36 baryshnikov sudo[6221]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
Aug 30 15:30:36 baryshnikov sudo[6221]: pam_unix(sudo:session): session closed for user root
Aug 30 15:31:29 baryshnikov sudo[6241]:     jeff : TTY=pts/0 ; PWD=/home/jeff ; USER=root ; COMMAND=/usr/bin/tail -f /var/log/syslog
Aug 30 15:31:29 baryshnikov sudo[6241]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
Aug 30 15:31:43 baryshnikov gnome-shell[3544]: Can't update stage views actor <unnamed>[<MetaWindowGroup>:0x5fbf461ba360] is on because it needs an allocation.
Aug 30 15:31:43 baryshnikov gnome-shell[3544]: Can't update stage views actor <unnamed>[<MetaWindowActorX11>:0x5fbf47fcdb00] is on because it needs an allocation.
Aug 30 15:31:43 baryshnikov gnome-shell[3544]: Can't update stage views actor <unnamed>[<MetaSurfaceActorX11>:0x5fbf47fd0de0] is on because it needs an allocation.
Aug 30 15:31:58 baryshnikov sudo[6241]: pam_unix(sudo:session): session closed for user root
Aug 30 15:32:21 baryshnikov sudo[6274]:     jeff : TTY=pts/0 ; PWD=/home/jeff ; USER=root ; COMMAND=/usr/bin/journalctl -xe
Aug 30 15:32:21 baryshnikov sudo[6274]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
Aug 30 15:32:28 baryshnikov sudo[6274]: pam_unix(sudo:session): session closed for user root
Aug 30 15:32:36 baryshnikov sudo[6277]:     jeff : TTY=pts/0 ; PWD=/home/jeff ; USER=root ; COMMAND=/usr/bin/journalctl -xe
Aug 30 15:32:36 baryshnikov sudo[6277]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
Aug 30 15:32:37 baryshnikov sudo[6277]: pam_unix(sudo:session): session closed for user root
Aug 30 15:32:47 baryshnikov sudo[6282]:     jeff : TTY=pts/0 ; PWD=/home/jeff ; USER=root ; COMMAND=/usr/bin/journalctl -xe
Aug 30 15:32:47 baryshnikov sudo[6282]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)


The logs look like they haven't picked up any errors relevant to the PS/2 mouse.

After I ran these commands, I tried the mouse with the adapter out on my Windows PC and it too was unable to pick up the mouse. 

Wondering if it was a hardware issue, I opened up the electronics of the mouse, but did not seem to find anything visibly broken. It's just an old mouse it seems.

At this point, my question to you all is what path should I take forward? Should I bite the bullet and buy another PS/2 mouse, or is there a path for possibly getting this old thing to work?

Thank you very much for your time :)

---

### Post by TheFu on 2024-09-03
I tried for months to get my old PS/2 keyboard (IBM 101m) and mouse (older Logitech) to work.  Bought 3 different PS2-to-USB adapters.  I'd been using a "Y" adapter for over a decade to connect 4 computers to a KVM switch and those all worked.  After being forced to change the KVM switch out (no more VGA outputs from 2 of the main computers), I was forced to HDMI and an HDMI switch with USB ports for keyboard and mice.  Anyway, it never worked.  I miss my IBM 101M keyboard feel.  None of the others I've had since then are even close to the same feel.

I was using a free USB mouse from a client's stash for awhile, but that mouse was much too light and would move around when nobody touched it.  In June, I finally found a used USB mouse for $2.50 at a Good-Will store that was heavier.  I still have a serial mouse from the 1990s that stopped working when Win98 was released.  That was one of many disappointments caused by both OS vendors and hardware vendors.  With Linux, we have to be much more careful which hardware we choose.

Wish I had better news or that I was as stubborn as you.

---

### Post by bucephalusstudios on 2024-09-03
Sorry to hear that you couldn't get your peripherals working either :(

I think my adapter's good because my PS/2 keyboard works fine through it. I'll wait around a bit to see if anyone has solutions to getting an ancient mouse to work lol. If nothing comes up though, I think I may just try buying another mouse.

---

### Post by TheFu on 2024-09-03
> **bucephalusstudios said:**
> Sorry to hear that you couldn't get your peripherals working either :(

I think my adapter's good because my PS/2 keyboard works fine through it. I'll wait around a bit to see if anyone has solutions to getting an ancient mouse to work lol. If nothing comes up though, I think I may just try buying another mouse.

I decided it was the adapter, not the mouse, that was the problem in my situation.

Good luck.

---

### Post by bucephalusstudios on 2024-10-14
I determined that the old mouse was broken. I bought another old PS/2 mouth that worked like a charm.

Now closing this thread :)

---

