---
title: "touchpad problem at random: psmouse serio2: synaptics: Unable to initialize device."
date: 2020-03-12
forum: Hardware
---

### Post by Claus7 on 2020-03-12
Hello,

after upgrading to ubuntu 19.10 half of the time I'm getting this error under logs:
*Message* psmouse serio2: synaptics: Unable to initialize device. 
*Kernel device* +serio:serio2
*Priority* 3

The thing is that this is a common issue after also upgrading to 20.04. I'm aware that other users were affected by this issue, yet in my case, this is not happening in every boot, yet it happens at random.

I always have control of my touchpad, yet in case this error appears, my touchpad is less responsive and I cannot use double finger scrolling or 3 fingers middle click. 

When this error happens, I reboot, and then things are working as normal. Do you have any idea why this happens at random?

Regards!

---

### Post by Claus7 on 2020-03-26
Hello,

I removed the lightdm window manager and installed gdm, and issue temporarily seemed to get resolved. With the latest updates though, problem persisted. Now, issuing the command:
dmesg | grep -i psmouse

I get the output:

> [    1.809059] psmouse serio2: synaptics: queried max coordinates: x [..5718], y [..4908]
[    1.925690] psmouse serio2: synaptics: queried min coordinates: x [1238..], y [956..]
[    1.925695] psmouse serio2: synaptics: Your touchpad (PNP: SYN1221 PNP0f13) says it can support a different bus. If i2c-hid and hid-rmi are not used, you might want to try setting psmouse.synaptics_intertouch to 1 and report this to [email]linux-input@vger.kernel.org[/email].
[    2.037713] psmouse serio2: synaptics: Unable to initialize device.

Needs to investigate further...

edit: according to this: [https://forum.manjaro.org/t/touchpad-has-an-identity-crisis/77353/15](https://forum.manjaro.org/t/touchpad-has-an-identity-crisis/77353/15), synaptics seems to be obsolete, so I removed it. I rebooted and the output of the previous command is:
> [    1.807119] psmouse serio2: synaptics: queried max coordinates: x [..5718], y [..4908]
[    1.924876] psmouse serio2: synaptics: queried min coordinates: x [1238..], y [956..]
[    1.924881] psmouse serio2: synaptics: Your touchpad (PNP: SYN1221 PNP0f13) says it can support a different bus. If i2c-hid and hid-rmi are not used, you might want to try setting psmouse.synaptics_intertouch to 1 and report this to [email]linux-input@vger.kernel.org[/email].
[    2.069950] psmouse serio2: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2b1, caps: 0xf00223/0x840300/0x26800/0x0, board id: 3175, fw id: 2330500

The same message for different bus is still there, even if now psmouse is understood.

edit2:
1) I re-installed xserver-xorg-input-synaptics, as I saw that this is not affecting anything
2) typed: sudo gedit /etc/default/grub
and changed the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash psmouse.synaptics_intertouch=1"

do NOT remove quiet splash, unless you would like your login screen to be full of message lines
3) updated grub with the command: sudo update-grub
4) rebooted

Now the output of the command: dmesg | grep -i psmouse, is:

> [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-20-generic root=UUID=f38a8643-a1ca-4cf2-81b7-847ab291bc39 ro quiet splash psmouse.synaptics_intertouch=1 vt.handoff=7
[    0.031869] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-20-generic root=UUID=f38a8643-a1ca-4cf2-81b7-847ab291bc39 ro quiet splash psmouse.synaptics_intertouch=1 vt.handoff=7
[    1.798411] psmouse serio2: synaptics: queried max coordinates: x [..5718], y [..4908]
[    1.915046] psmouse serio2: synaptics: queried min coordinates: x [1238..], y [956..]
[    1.915048] psmouse serio2: synaptics: Trying to set up SMBus access

which seems to be much better. Time will tell how it will behave.

Regards!

---

### Post by Claus7 on 2020-04-28
Hello,

upgrading to focal and reverting grub to normal did not eliminate the random problem with touchpad.
The commands:
echo -n "reconnect" | sudo tee /sys/bus/serio/devices/serio2/drvctl
synclient TapButton3=2

make the touchpad functional again, and enable the 3 finger middle click respectively, without the need for reboot.

Regards!

---

### Post by Claus7 on 2020-05-06
Hello,

even if it seems to be a kernel issue, I uninstalled xserver-xorg-input-synaptics, in case there was a conflict with xserver-xorg-input-libinput package. The kernel used was 5.4.0-28-generic. All but the latest boot caused the problem anew, until upgraded to the latest kernel at the time 5.4.0-29-generic.

I have not installed xserver-xorg-input-evdev, which seems to be a package related to touchpad.

Time will tell with the latest kernel.

Regards!

---

