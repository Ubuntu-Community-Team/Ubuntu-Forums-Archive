---
title: "Udev Rules - reg"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by zoobave on 2007-06-20
hi,

         I am in a situation that, i need to run a program (or Application) whenever an USB device is inserted. So that, i put the following entry in **"/etc/udev/rules.d/01-local.rules"** file.
[B]
SUBSYSTEM=="usb_device", ACTION=="add", ATTRS{manufacturer}=="JetFlash", PROGRAM="/usr/bin/nautilus ", NAME="%c", MODE="0777"[/B]


if i test using then following command, the nautilus starts

**dvm@dvm-desktop:~$ udevtest /sys/class/usb_device/usbdev4.5/ **


parse_file: reading '/etc/udev/rules.d/00- init.rules' as rules file
parse_file: reading '/etc/udev/rules.d/01-local.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/10- myrule.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/25-dmsetup.rules' as rules file
parse_file: reading '/etc/udev/rules.d/25- iftab.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id
.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45- fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libgphoto2.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45- libsane.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-libpisock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60- symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules ' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules ' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90- modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/99-udevmonitor.rules' as rules file
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, if rules
match against subsystem specfic kernel event variables.

main: looking at device '/class/usb_device/usbdev4.5' from subsystem 'usb_device'
[B]run_program: '/usr/bin/nautilus '
run_program: '/usr/bin/nautilus' returned with status 0[/B]
udev_rules_get_name: rule applied, 'usbdev4.5' becomes ''
run_program: 'usb_device_name --export usbdev4.5'
run_program: '/lib/udev/usb_device_name' (stdout) 'USB_BUS=004'
run_program: '/lib/udev/usb_device_name' (stdout) 'USB_DEV=005'
run_program: '/lib/udev/usb_device_name' returned with status 0
run_program: 'check_ptp_camera 06/01/01'
run_program: '/lib/udev/check_ptp_camera' returned with status 1
udev_device_event: device node creation supressed
main: run: 'socket:/org/freedesktop/hal/udev_event'
main: run: 'socket:/org/kernel/udev/monitor'




[B]
but, when i insert the same device, it will not run the program automatically.  How can i modify the above entry to run the nautilus (or any program) automatically?

Is there anything i have to do after the changes to the file?
[/B]
-- 

Regards,

Zoobave A
[http://zoobave.blogspot.com/](http://zoobave.blogspot.com/)

---

