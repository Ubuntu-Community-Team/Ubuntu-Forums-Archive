---
title: "[SOLVED] Lirc trouble with Dell Latitude D600 laptop ir port"
date: 2008-06-26
forum: Hardware
---

### Post by AndrewWalker on 2008-06-26
I'm having trouble getting the ir port working on my Dell Latitude D600 laptop. I've enabled it in the BIOS as com2 but the only mention I get in dmesg is this

[   37.732859] irda_init()

there is nothing in devices when I do

cat /proc/bus/input/devices

I've run

 sudo dpkg-reconfigure lirc
 
and selected 

SIR IrDA (built-in IR ports)

but nothing happens.
I've tried restarting lirc manually
sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                                                            [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                                           [ OK ]
fred@Dell-laptop:~$ 

my /etc/lirc/hardware.config is as follows


REMOTE="SIR IrDA (built-in IR ports)"
REMOTE_MODULES="lirc_dev lirc_sir"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/lircd.conf.nova-t"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

the file /usr/share/lirc/remotes/hauppauge/lircd.conf.nova-t is the one for the remote control handset that I want to use and I know the script is correct because I use it on another machine with it's TV card.
I'm running Kubuntu-8.04 but that shouldn't make any real difference.

---

### Post by Meson on 2008-11-06
Have you had any luck with this?  How do you even tell if it's working?  Were you trying to get a remote control going?

---

### Post by AndrewWalker on 2008-11-07
No, I'm still hoping someone will help me!
I found this snippet on the web somewhere, wasn't sure if compiling the lirc_module was necessary and didn't understand what to do with setserial to get it to work at boot up.
-----------------------------------------
io=0x02e8 irq=3
irport and lirc_sir

I've gotton lirc to work on a Dell latitude d600. just set the irda / com
port in the bios, and compile the lirc_module for serial ports (lirc_sir),
and point it to the com port.

I needed to run setserial dev/ttyS1 uart none (i'm using com2, com1 is
ttyS0). works fine with a Sky remote control (i'm in the UK), but the
receiver is in such a poor position on the laptop that it's only useful for
curiosity value.

---

### Post by Meson on 2008-11-07
My main problem right now is that when lirc is starting up, my system freezes.

---

### Post by AndrewWalker on 2008-11-07
Ah, progress at last!
I've sort of got it working. Stop the daemon 
sudo /etc/init.d/lirc stop

Edit /etc/lirc/hardware.conf as follows
REMOTE="SIR IrDA (built-in IR ports)"
REMOTE_MODULES="lirc_dev lirc_sir"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"


editing REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge" to suit your remote, pick it from /usr/share/lirc/remotes

Edit /etc/lirc/lircd.conf as follows
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge
editing it to match the same as your remote like above.
Check that ir is enabled in BIOS using 
dmesg | grep serial
You should get this for the second serial port
serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Then do
sudo setserial /dev/ttyS1 uart none
and
sudo modprobe lirc_sir irq=3 io=0x02f8
finally
sudo lircd -d /dev/lirc0 /etc/lircd.conf --nodaemon
and you should get
lircd(userspace) ready

In another shell try this
sudo mode2 -d /dev/lirc0
and press a few buttons and you should get an output!

Kill that with Ctrl+c and try running
irw

when you press buttons on your ir it should echo the reply in the shell!
All I need to work out now is how to get it to work at boot!
Let me know how you get on, good luck!

---

### Post by Meson on 2008-11-07
You might want to set LOAD_MODULES to true in hardware.conf

---

### Post by AndrewWalker on 2008-11-08
If I do that I get the following when I restart lirc daemon

fred@Dell-laptop:~$ sudo /etc/init.d/lirc start
 * Loading LIRC modules                                                                                                                [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
fred@Dell-laptop:~$

Do I definitely put this?

LOAD_MODULES="true"

What about the setserial option?

---

### Post by Meson on 2008-11-08
I'm still trying to figure out the setserial option.  I'm also trying to figure out how to get the device to be /dev/lirc (not lirc0) with read-write permissions for all users.  Or get it to be lirc0 with rw for all, and a symlink to from lirc to lirc0 (however the symlink disappears when lirc0 disappears).

As for the module part, I did the following:
```

$ sudo echo "options lirc-sir irq=3 io=0x02f8" > /etc/modprobe.d/lirc-sir

```

It doesn't seem to be necessary to add lirc-sir to /etc/modules....

---

### Post by AndrewWalker on 2008-11-08
Just had a look on my Gentoo machine at that file and it had this example highlighted.

#
# For first serial receivers:
#
#options lirc_serial irq=4 io=0x3f8
#options lirc_sir irq=4 io=0x3f8

#
# Detach first serial port from serial-driver.
# Use this when you have your serial-port-driver statically
# compiled into your kernel, or as a module but loaded before
# the lirc-module.
# 
#install lirc_serial setserial /dev/ttyS0 uart none; modprobe --ignore-install lirc_serial
#
#install lirc_sir    setserial /dev/ttyS0 uart none; modprobe --ignore-install lirc_sir


#
# For parallel receivers:
#
#options lirc_parallel irq=7 io=0x3bc


Try this line with ttyS1 instead of TTYS0

install lirc_sir    setserial /dev/ttyS0 uart none; modprobe --ignore-install lirc_sir

(all one line by the way and --ignore-install without spaces)
Haven't tried it myself yet, let me know if it works!
That's why I prefer Gentoo, it usually gives you clues even if it is a steep learning curve!

---

### Post by Meson on 2008-11-08
I added the options and it seems to work:

install lirc_sir setserial /dev/ttyS1 uart none; modprobe --ignore-install lirc_sir irq=3 io=0x02f8

Now to figure out how to get the device to have the proper permissions.

---

### Post by AndrewWalker on 2008-11-09
Well mine is sort of working. If I run irw I usually get the first button pressed ok and sometimes several but eventually it stops responding.
Seems buggy but I don't seem to have any permission issues though.
I only have lircd and lirc0  in /dev so I would check your scripts are
REMOTE_DEVICE="/dev/lirc0" and not REMOTE_DEVICE="/dev/lirc" or something like that. I think lirc0 is only created by udev if the lirc daemon starts correctly, you shouldn't need to manually create the /dev entries or mess around with it's permissions.

---

### Post by Meson on 2008-11-09
Ok, well I'll recap what I've done.  Hopefully I am not leaving anything out (because I did do a lot of tinkering...)  For full discloser, I'm running Intrepid on a Dell Latitide D800

1) In your system BIOS, enable IR and set it to COMM2 (You can also get comm3 and comm4 to work, comm1 will NOT work.

2) Install lirc.  This will also install setserial.  (You can also install lirc-x, I haven't done this yet.):
```
sudo apt-get install lirc
```

2a) Choose: SIR IrDA (built-in IR ports) for your input (I selected none for output.

3) Edit /etc/lirc/hardware.conf as follows:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="SIR IrDA (built-in IR ports)"
REMOTE_MODULES="lirc_dev lirc_sir"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

4) Add this to /etc/lirc/lircd.conf:
```
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge
```

(Just to note, the remote I'm using is actually the Verizon FIOS remote for the HD set-top-box.  However it seems to work fine with these settings.  I plan on tweaking it in the future.)

5) Create/edit /etc/modprobe.d/lirc-sir and add the following line:
```
install lirc_sir setserial /dev/ttyS1 uart none; modprobe --ignore-install lirc_sir irq=3 io=0x02f8
```
(Note that /dev/ttyS1, irq=3, io=0x02f8 are specific to COMM2

6) Restart lirc:
```
sudo /etc/init.d/lirc restart
```

7) If you have the file /etc/rc2.d/S##lirc then lirc should start automatically.

8) Rather than using mode2 to test that it's working, add ~/.lircrc to your home directory.  This is the first one it found but there's enough in there to ensure that it works.  I'm sure a lot of tweaking should be done to this:
```
# File: ~/.lircrc
# Remote Control: Pixelview PlayTV MPEG2 PV-M4900 FM.RC
# Author: Paulo Roma
#
###############################################
### xirw for debugging                        #
###############################################

begin
    prog   = xirw
    button = power
    config = power
end

begin
    prog   = xirw
    button = source
    config = source
end

begin
    prog   = xirw
    button = timeshift 
    config = timeshift
end

begin
    prog   = xirw
    button = zoom
    config = zoom
end

begin
    prog   = xirw
    button = mute
    config = mute
end

begin
   prog   = xirw
   button = ch+ 
   config = ch+
end

begin
    prog   = xirw
    button = ch-
    config = ch-
end

begin
    prog   = xirw
    button = vol+
    config = vol+
end

begin
    prog   = xirw
    button = vol-
    config = vol-
end

begin
    prog   = xirw
    button = loop
    config = loop
end

begin
    prog   = xirw
    button = scan
    config = scan
end

begin
    prog   = xirw
    button = snapshot
    config = snapshot
end

begin
    prog   = xirw
    button = bw
    config = bw
end

begin
    prog   = xirw
    button = rec
    config = rec
end

begin
    prog   = xirw
    button = fw
    config = fw
end

begin
    prog   = xirw
    button = stop
    config = stop
end

begin
    prog   = xirw
    button = play
    config = play
end

begin
    prog   = xirw
    button = pause
    config = pause
end

begin
    prog   = xirw
    button = tv
    config = TV
end

begin
    prog   = xirw
    button = fm 
    config = FM
end

begin
    prog   = xirw
    button = +100
    config = X mouse
    mode = mouse
end

begin
    prog   = xirw
    button = 1
    config = 1
end

begin
    prog   = xirw
    button = 2
    config = 2
end

begin
    prog   = xirw
    button = 3
    config = 3
end

begin
    prog   = xirw
    button = 4
    config = 4
end

begin
    prog   = xirw
    button = 5
    config = 5
end

begin
    prog   = xirw
    button = 6
    config = 6
end

begin
    prog   = xirw
    button = 7
    config = 7
end

begin
    prog   = xirw
    button = 8
    config = 8
end

begin
    prog   = xirw
    button = 9
    config = 9
end

begin
    prog   = xirw
    button = 10
    config = 10
end

begin
    prog   = xirw
    button = 0
    config = 0
end

###############################################
### Starts application mode                   #
###############################################

begin
      button = timeshift
      mode   = apprun
end

###############################################
### Selects the application to run            #
###############################################

begin apprun
begin
    prog = irexec
    button = 1
    config = tvtime.sh &
    mode = tvtime
    flags = once
end

begin
    prog = irexec
    button = 2
    config = playtv.sh Globo 0 &
    mode = mplayer
    flags = once
end

begin
    prog = irexec
    button = 3
    config = gnomeradio &
    mode = gnomeradio
    flags = once
end

begin
  prog = irexec
  button = 4
  config = xmms&
  mode = xmms
  flags = once
end

begin
  prog = irexec
  button = 5
  config = xmcd&
  mode = xmcd
  flags = once
end

begin
  prog = irexec
  button = 6
  config = xawtv -c /dev/tvtuner &
  mode = xawtv
  flags = once
end

begin
  prog = irexec
  button = 7
  config = rhythmbox &
  mode = rhythmbox
  flags = once
end

begin
    prog = irexec
    button = 0
    config = irmix &
    mode = irmix
    flags = once
end
end   apprun

###############################################
### tvtime for playing TV                     #
###############################################
#
# This is an example config file for your LIRC remote.  All buttons
# depend on what you have configured in your lircd.conf file.  Please
# refer to this and adjust the labels below accordingly.
#
# tvtime is controlled through a separate program called tvtime-command.
# For a list of commands, see 'man tvtime-command'.  Key events can
# be 'faked' using the command KEY_EVENT, which allows for mapping a
# single remote control button to both a menu mode command and a normal
# mode command.
#
# begin
#    prog = irexec
#    button = DISPLAY
#    config = tvtime-command DISPLAY_INFO
# end

# This section includes two configs, what this does is that it allows
# you to open tvtime and close tvtime with one button.  If your remote
# has seperate buttons for this, then you can break it apart.

# The following defines most of the common buttons found on a remote and
# what commads they would map to inside tvtime.

begin tvtime
begin
    prog = irexec
    button = power
    config = tvtime-command QUIT
    flags = mode
end

begin
    prog = irexec
    button = source
    config = tvtime-command TOGGLE_INPUT
end
begin
    prog = irexec
    button = scan
    config = tvtime-command DISPLAY_INFO
end
begin
    prog = irexec
    button = zoom
    config = tvtime-command TOGGLE_FULLSCREEN
end
# closed caption
begin
    prog = irexec
    button = tv
    config = tvtime-command TOGGLE_CC
end

begin
    prog = irexec
    button = mute
    config = tvtime-command TOGGLE_MUTE
end

begin
    prog = irexec
    button = snapshot
    config = tvtime-command SCREENSHOT
end

begin
    prog = irexec
    button = fm
    config = tvtime-command TOGGLE_AUDIO_MODE
end

# Menu navigation.
begin
    prog = irexec
    button = ch+
    config = tvtime-command UP
end
begin
    prog = irexec
    button = ch-
    config = tvtime-command DOWN
end
begin
    prog = irexec
    button = vol+
    config = tvtime-command RIGHT
    repeat = 6
end
begin
    prog = irexec
    button = vol-
    config = tvtime-command LEFT
    repeat = 6
end

begin
    prog = irexec
    button = loop
    config = tvtime-command CHANNEL_JUMP
end

begin
    prog   = irexec
    button = 1
    config = tvtime-command CHANNEL_1
end
begin
    prog   = irexec
    button = 2
    config = tvtime-command CHANNEL_2
end
begin
    prog   = irexec
    button = 3
    config = tvtime-command CHANNEL_3
end
begin
    prog   = irexec
    button = 4
    config = tvtime-command CHANNEL_4
end
begin
    prog   = irexec
    button = 5
    config = tvtime-command CHANNEL_5
end
begin
    prog   = irexec
    button = 6
    config = tvtime-command CHANNEL_6
end
begin
    prog   = irexec
    button = 7
    config = tvtime-command CHANNEL_7
end
begin
    prog   = irexec
    button = 8
    config = tvtime-command CHANNEL_8
end
begin
    prog   = irexec
    button = 9
    config = tvtime-command CHANNEL_9
end
begin
    prog   = irexec
    button = 0
    config = tvtime-command CHANNEL_0
end
begin
    prog = irexec
    button = play
    config = tvtime-command ENTER
end
end tvtime

###############################################
### MPlayer for videos (avi, dvd, MPEG)       #
###############################################

begin mplayer 
begin
    prog   = mplayer
    button = power
    config = quit
    flags  = mode
end

begin
    prog   = mplayer
    button = vol+
    config = volume 1
    repeat = 3
end

begin
    prog   = mplayer
    button = vol-
    config = volume -1
    repeat = 3
end

begin
    prog   = mplayer
    button = stop
    config = seek 0 1\npause
end

begin
    prog   = mplayer
    button = pause
    config = pause
end

begin
    prog   = mplayer
    button = fw
    config = seek 30
    repeat = 1
end

begin
    prog   = mplayer
    button = bw
    config = seek -30
    repeat = 1
end

begin
    prog   = mplayer
    button = zoom
    config = vo_fullscreen
end

begin
    prog   = mplayer
    button = ch+
    config = tv_step_channel 1
end

begin
    prog   = mplayer
    button = ch-
    config = tv_step_channel -1
end

begin
    prog   = mplayer
    button = 1
    config = tv_set_channel 7
end
begin
    prog   = mplayer
    button = 2
    config = tv_set_channel 1
end
begin
    prog   = mplayer
    button = 3
    config = tv_set_channel 2
end
begin
    prog   = mplayer
    button = 4
    config = tv_set_channel 3
end
begin
    prog   = mplayer
    button = 5
    config = tv_set_channel 4
end
begin
    prog   = mplayer
    button = 6
    config = tv_set_channel 4
end
begin
    prog   = mplayer
    button = 7
    config = tv_set_channel 5
end
begin
    prog   = mplayer
    button = 8
    config = tv_set_channel 6
end
begin
    prog   = mplayer
    button = 9
    config = tv_set_channel 6
end
begin
    prog   = mplayer
    button = 0
    config = tv_set_channel 8
end

begin
    prog   = mplayer
    button = mute
    config = mute
end

#begin
#    prog   = irxevent
#    button = loop
#    config = Key c mplayer
#end
end mplayer

###############################################
### gnomeradio for playing radio              #
###############################################

begin gnomeradio
begin
    prog = gnomeradio
    button = power
    config = QUIT
    flags = mode
end
begin
	prog = gnomeradio
	button = MUTE
	config = mute
end
begin
	prog = gnomeradio
	button = fw
	config = tune up
end
begin
	prog = gnomeradio
	button = bw
	config = tune down
end
begin
	prog = gnomeradio
	button = CH+
	config = preset up
end
begin
	prog = gnomeradio
	button = CH-
	config = preset down
end
begin
	prog = gnomeradio
	button = VOL+
	config = volume up
	repeat = 3	
end
begin
	prog = gnomeradio
	button = VOL-
	config = volume down
	repeat = 3
end
begin
	prog = gnomeradio
	button = 0
	config = preset 0
end
begin
	prog = gnomeradio
	button = 1
	config = preset 1
end
begin
	prog = gnomeradio
	button = 2
	config = preset 2
end
begin
	prog = gnomeradio
	button = 3
	config = preset 3
end
begin
	prog = gnomeradio
	button = 4
	config = preset 4
end
begin
	prog = gnomeradio
	button = 5
	config = preset 5
end
begin
	prog = gnomeradio
	button = 6
	config = preset 6
end
begin
	prog = gnomeradio
	button = 7
	config = preset 7
end
begin
	prog = gnomeradio
	button = 8
	config = preset 8
end
begin
	prog = gnomeradio
	button = 9
	config = preset 9
end
end gnomeradio

###############################################
### irmix - mixer controller                  #
###############################################

begin irmix
begin
    prog   = irexec
    button = power
    config = killall -HUP irmix
    flags  = mode
end

begin
    prog   = irmix
    button = vol-
    repeat = 1
    config = dec 1
end

begin
    prog   = irmix
    button = vol+
    repeat = 1
    config = inc 1
end

begin
    prog   = irmix
    button = zoom
    config = select
end

begin
    prog   = irmix
    button = ch+
    config = nextchannel
end

begin
    prog   = irmix
    button = ch-
    config = prevchannel
end

begin
    prog   = irmix
    button = mute
    config = togglemute
end
end irmix

###############################################
### XMMS for playing mp3                      #
###############################################

begin xmms
begin
    prog   = xmms
    button = power
    config = QUIT
    flags  = mode
end

begin
    prog   = xmms
    button = source
    config = PLAYLIST_CLEAR
end

begin
    prog   = xmms
    button = fm
    config = PLAYLIST_ADD /home/roma/.xmms/xmms.m3u
end

begin
    prog   = xmms
    button = play
    config = PLAY
end

begin
    prog   = xmms
    button = ch+
    config = NEXT
end

begin
    prog   = xmms
    button = ch-
    config = PREV
end

begin
    prog   = xmms
    button = bw
    config = BWD
    repeat = 1
end

begin
    prog   = xmms
    button = fw
    config = FWD
    repeat = 1
end

begin
    prog   = xmms
    button = pause
    config = PAUSE 
end

begin
    prog   = xmms
    button = stop
    config = STOP
end

begin
    prog   = xmms
    button = scan
    config = SHUFFLE
end

begin
    prog   = xmms
    button = loop
    config = REPEAT
end

begin
    prog   = xmms
    button = vol+
    config = VOL_UP 5
    repeat = 2
end

begin
    prog   = xmms
    button = vol-
    config = VOL_DOWN 5
    repeat = 2
end

begin
    prog   = xmms
    button = mute
    config = MUTE
end

begin
    prog = xmms
    button = zoom
    config = BAL_CENTER
end

begin
    prog   = xmms
    button = 1
    config = ONE
end

begin
    prog   = xmms
    button = 2
    config = TWO
end

begin
    prog   = xmms
    button = 3
    config = THREE
end

begin
    prog   = xmms
    button = 4
    config = FOUR
end

begin
    prog   = xmms
    button = 5
    config = FIVE
end

begin
    prog   = xmms
    button = 6
    config = SIX
end

begin
    prog   = xmms
    button = 7
    config = SEVEN
end

begin
    prog   = xmms
    button = 8
    config = EIGHT
end

begin
    prog   = xmms
    button = 9
    config = NINE
end

begin
    prog   = xmms
    button = 0
    config = ZERO
end

begin
    prog   = xmms
    button = snapshot
    config = SETPOS
end
end xmms


###############################################
### XMCD for audio CD's                       #
###############################################

begin xmcd 
begin
    prog = irexec
    button = power
    config = xmcd.sh quit
    flags = mode
end

begin
    prog   = irexec
    button = vol+
    config = xmcd.sh volume 100 
end

begin
    prog   = irexec
    button = vol-
    config = xmcd.sh volume 50
end

begin
    prog   = irexec
    button = play
    config = xmcd.sh play
end

begin
    prog   = irexec
    button = stop
    config = xmcd.sh stop
end

begin
    prog   = irexec
    button = pause
    config = xmcd.sh pause
end

begin
    prog   = irexec
    button = fw
    config = xmcd.sh index next
    repeat = 1
end

begin
    prog   = irexec
    button = rw
    config = xmcd.sh index prev
    repeat = 1
end

begin
    prog   = irexec
    button = ch-
    config = xmcd.sh track prev
end

begin
    prog   = irexec
    button = ch+
    config = xmcd.sh track next
end

begin
    prog   = irexec
    button = loop
    config = xmcd.sh repeat
end

begin
    prog   = irexec
    button = snapshot
    config = xmcd.sh time r-trac
end

begin
    prog   = irexec
    button = 1
    config = xmcd.sh track 1
end

begin
    prog   = irexec
    button = 2
    config = xmcd.sh track 2
end

begin
    prog   = irexec
    button = 3
    config = xmcd.sh track 3
end

begin
    prog   = irexec
    button = 4
    config = xmcd.sh track 4
end

begin
    prog   = irexec
    button = 5
    config = xmcd.sh track 5
end

begin
    prog   = irexec
    button = 6
    config = xmcd.sh track 6
end

begin
    prog   = irexec
    button = 7
    config = xmcd.sh track 7
end

begin
    prog   = irexec
    button = 8
    config = xmcd.sh track 8
end

begin
    prog   = irexec
    button = 9
    config = xmcd.sh track 9
end

begin
    prog   = irexec
    button = 0
    config = xmcd.sh track 10
end
end xmcd

###############################################
### xawtv another TV player                   #
###############################################

begin xawtv
begin 
    prog   = 	irexec
    button = 	power
    config = 	xawtv-remote quit
    flags  =	mode
end
    begin 
    prog   = 	irexec
    button = 	source
    config = 	xawtv-remote setinput next
end
begin
    prog   = 	irexec
    button = 	zoom
    config = 	xawtv-remote fullscreen
end
begin 
    prog   =	irexec
    button =	ch-
    config =	xawtv-remote setstation prev
end
begin
    prog   =	irexec
    button =	ch+
    config =	xawtv-remote setstation next
end
begin
    prog   =	irxevent
    button =	loop
    config =	Key c xawtv
end
begin
    prog   =	irxevent
    button =	scan
    config =	Key ctrl-z xawtv
end
begin
    prog   = irxevent
    button = mute
    config = Key a xawtv
end    
begin
    prog   = irxevent
    button = vol+
    repeat = 3
    config = Key KP_Add xawtv
end
begin
    prog   = irxevent
    button = vol-
    repeat = 3
    config = Key KP_Subtract xawtv
end
begin
    prog   = irexec
    button = 2
    config = xawtv-remote setstation 0
end
begin
    prog   = irexec
    button = 3
    config = xawtv-remote setstation 1
end
begin
    prog   = irexec
    button = 4
    config = xawtv-remote setstation 2
end
begin
    prog   = irexec
    button = 6
    config = xawtv-remote setstation 3
end
begin
    prog   = irexec
    button = 7
    config = xawtv-remote setstation 4
end
begin
    prog   = irexec
    button = 9
    config = xawtv-remote setstation 5
end
begin
    prog   = irexec
    button = 1
    config = xawtv-remote setstation 6
end
begin
    prog   = irexec
    button = 0
    config = xawtv-remote setstation 7
end
begin
    prog   =	irexec
    button =	rec
    config =	xawtv-remote attr next
end
begin
    prog   =	irexec
    button =	fw
    config =	xawtv-remote attr inc
    repeat =    3
end
begin
    prog   =	irexec
    button =	bw
    config =	xawtv-remote attr dec
    repeat =    3
end
begin
    prog   =	irexec
    button =	snapshot
    config =	xawtv-remote msg " `date +%H:%M` "
end
end xawtv

###############################################
### Rhythmbox juke box player 
###############################################

begin rhythmbox
begin
    prog   =    Rhythmbox
    button =    power
    config =    quit
    flags  =    mode
end

begin
    prog = Rhythmbox
    button = play
    config = play
end

begin
    prog = Rhythmbox
    button = pause
    config = pause
end

begin
    prog = Rhythmbox
    button = stop
    config = stop
end

begin
    prog = Rhythmbox
    button = vol+
    config = volume_up
    repeat = 3
end


begin
    prog = Rhythmbox
    button = vol-
    config = volume_down
    repeat = 3
end
begin
    prog = Rhythmbox
    button = ch+
    config = next
end

begin
    prog = RhythmBox
    button = ch-
    config = previous
end

begin
    prog = RhythmBox
    button = mute
    config = mute
end

begin
    prog = RhythmBox
    button = scan
    config = shuffle
end

begin
    prog = RhythmBox
    button = loop
    config = repeat
end

begin
    prog = RhythmBox
    button = fw
    config = seek_forward
end

begin
    prog = RhythmBox
    button = bw
    config = seek_backward
end
end rhythmbox
```

9) Start rhythmbox, enable the lirc plugin.  You should now be able to control your volume...

10) Enjoy!

---

### Post by AndrewWalker on 2008-11-09
Just an small useful bit of info for anyone using MythTV and Ubuntu.
If you install a bit of software called myth-lirc-generator after configuring lirc, it converts all your remote control key binding and generates the .lircrc bits for you.
Thanks for all the help, I'll mark this post as solved now.

---

### Post by Haser on 2009-04-30
Hello, i have a dell studio 1537, I would try this guide but my infrared port is recognized as integrated into the keyboard. how do I enter it correctly parameters in section 5?

---

### Post by Kulgan on 2009-05-25
> Hello, i have a dell studio 1537, I would try this guide but my infrared port is recognized as integrated into the keyboard. how do I enter it correctly parameters in section 5?

Agreed. Haven't installed the BIOS update yet ([http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R199825&formatcnt=1&libid=0&fileid=276805](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R199825&formatcnt=1&libid=0&fileid=276805)) but will do so over the weekend and see if that changes anything. Should also fix the dreadful sound :)

---

