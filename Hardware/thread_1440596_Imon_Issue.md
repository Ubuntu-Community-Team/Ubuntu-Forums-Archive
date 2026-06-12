---
title: "Imon Issue"
date: 2010-03-27
forum: Hardware
---

### Post by eric_pwb on 2010-03-27
Hi,

I am having a problem getting my antec veris elite (Imon) vfd to work correctly under ubuntu karmic.

my dmesg output shows that the lirc_imon is seeing the device, but I cannot echo to it, even as root, I get a broken pipe error. It is connected to my asus p7h55-m pro mobo.
When I have lcdproc running, my dmesg output shows send packet failed errors.

I tried connecting it to my macbook pro 5,5 under karmic and it works without a hitch.

Any Ideas?

---

### Post by mal205 on 2010-03-29
Try working through this: [http://ubuntuforums.org/showthread.php?p=9044098#post9044098]("http://ubuntuforums.org/showthread.php?p=9044098#post9044098")

---

### Post by eric_pwb on 2010-03-29
Tried it, actually the vfd version linked from it, and I end up with:

 lsmod | grep lirc
lirc_imon              25872  1 
lirc_dev               10804  3 lirc_imon

dmesg

[30737.796824] lirc_imon: send_packet: packet tx failed (-32)
[30737.796829] lirc_imon: vfd_write: send packet failed for packet #3
[30737.921695] lirc_imon: send_packet: packet tx failed (-32)
[30737.921700] lirc_imon: vfd_write: send packet failed for packet #3
[30738.045828] lirc_imon: send_packet: packet tx failed (-32)
[30738.045833] lirc_imon: vfd_write: send packet failed for packet #1
[30738.171682] lirc_imon: send_packet: packet tx failed (-32)
[30738.171687] lirc_imon: vfd_write: send packet failed for packet #3
[30738.546289] lirc_imon: send_packet: packet tx failed (-32)
[30738.546294] lirc_imon: vfd_write: send packet failed for packet #2
[30738.795583] lirc_imon: send_packet: packet tx failed (-32)
[30738.795588] lirc_imon: vfd_write: send packet failed for packet #1
[30739.046335] lirc_imon: send_packet: packet tx failed (-32)
[30739.046339] lirc_imon: vfd_write: send packet failed for packet #2
[30739.171715] lirc_imon: send_packet: packet tx failed (-32)
[30739.171720] lirc_imon: vfd_write: send packet failed for packet #3
[30739.298462] lirc_imon: send_packet: packet tx failed (-32)
[30739.298467] lirc_imon: vfd_write: send packet failed for packet #5
[30739.546716] lirc_imon: send_packet: packet tx failed (-32)
[30739.546721] lirc_imon: vfd_write: send packet failed for packet #3
[30739.796845] lirc_imon: send_packet: packet tx failed (-32)
[30739.796850] lirc_imon: vfd_write: send packet failed for packet #3
[30740.421852] lirc_imon: send_packet: packet tx failed (-32)
[30740.421857] lirc_imon: vfd_write: send packet failed for packet #3
[30740.849480] display port closed


LCDd:

LCDd version 0.5.3 starting
Built on Oct 14 2009, protocol version 0.3, API version 0.5
Using Configuration File: /etc/LCDd.conf
Set report level to 5, output to stderr
LCDd 0.5.3, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2009 William Ferrell, Scott Scriven
                        and many other contributors

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software Foundation,
Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imon", filename="/usr/lib/lcdproc/imon.so")
imon: using Device /dev/lcd0
imon: init() done
Key "Escape" is now reserved exclusively by client [-1]
Key "Enter" is now reserved shared by client [-1]
Key "Up" is now reserved shared by client [-1]
Key "Down" is now reserved shared by client [-1]
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_switch: switched to screen [_server_screen]
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
screenlist_process()
screenlist_switch(s=[_server_screen])
^CServer shutting down on SIGINT
Key "Escape" reserved exclusively by client [-1] and is now released
Key "Enter" reserved shared by client [-1] and is now released
Key "Up" reserved shared by client [-1] and is now released
Key "Down" reserved shared by client [-1] and is now released
screenlist_shutdown()
Exiting.


For the most part the display remains blank, on the occasion on a reboot the display will show a few garbled characters.

---

### Post by eric_pwb on 2010-03-29
Solved:  Check this thread: [http://ubuntuforums.org/showthread.php?p=9044967&mode=threaded#post9044967]("http://ubuntuforums.org/showthread.php?p=9044967&mode=threaded#post9044967")

---

