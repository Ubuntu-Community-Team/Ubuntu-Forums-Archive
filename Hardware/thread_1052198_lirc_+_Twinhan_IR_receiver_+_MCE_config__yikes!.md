---
title: "lirc + Twinhan IR receiver + MCE config:  yikes!"
date: 2009-01-27
forum: Hardware
---

### Post by dishbert on 2009-01-27
I'm trying to get a remote to work with Mythtv.  I have a Twinhan sat TV card with a USB remote:

chris@PC-Linux:~$ lsusb

Bus 001 Device 003: ID 6253:0100 TwinHan Technology Co., Ltd Ir reciver f. remote control
Bus 001 Device 001: ID 0000:0000

Since Twinhan was not listed under USB or TV devices when I set up lirc, I selected the MCE remote, thinking my Harmony 880 would work if I programmed it to emulate the MCE. (I never get this far though).

Configuring lirc this way results in:

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

and

/etc/lirc/lircd.conf

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

and /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb exists and looks fine (first couple of lines):

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4

And SOME of the buttons on the Twinhan remote work fine:  the numbers, select (Enter), exit.  But none of the others work as expected.  "Guide" brings up the channel editor, for instance.

There is no lirc0 in /dev, only lircd.
irw doesn't work:  first attempt gets no responce, second attempt gets "Connection refused".

Changing a working key "0" in home/.lircrc to something else that should work:

begin
   prog = mythtv
   button = Zero
   config = m
end

Does nothing.

Starting mythfrontend gives a couple of hints:

2009-01-27 11:29:57.427 Could not open settings file /home/chris/.mythtv/config.xml for writing

and 

mythtv: could not connect to socket
mythtv: Connection refused
2009-01-27 11:29:58.120 lirc_init failed for mythtv, see preceding messages

And in fact there is no config.xml:

[email]chris@PC-Linux:~/.mythtv[/email]$ ls
themecache

I'm at my wits end.

---

### Post by dishbert on 2009-01-28
I found this on Linuxquestions.org under the title:

"irw kills the lirc daemon - troubleshooting advice?

'It seems that udev is creating a device at /dev/lirc0, but the irw is looking for /dev/lirc (no number afterwards).
I started up the lircd daemon, and created a symbolic link which redirected /dev/lirc to /dev/lirc0."


I'd give this a try, but /dev has no lirc0 in it, and I don't know how to set up a sym link in lircd.

---

