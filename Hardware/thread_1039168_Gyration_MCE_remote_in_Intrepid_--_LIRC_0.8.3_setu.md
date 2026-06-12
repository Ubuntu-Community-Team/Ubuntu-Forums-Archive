---
title: "Gyration MCE remote in Intrepid -- LIRC 0.8.3 setup"
date: 2009-01-14
forum: Hardware
---

### Post by cbaker on 2009-01-14
i have the Gyration MCE remote (GYR3101) which ran fine under Gutsy and Hardy using the evrouter package.  when i upgraded to Intrepid (clean install), this solution stopped working.  

i was finally able to get this remote working again using the LIRC package.  here's how:

first, LIRC was griping about "can't get exclusive access to events comming from `/dev/input/event2' interface".  some googling turned up that i had to add 3 lines to my /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi
```

$ cat /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
[B]     <match key="info.product" contains_ncase="Gyration RF Technology Receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>[/B]
  </device>
</deviceinfo>

```

which i grabbed from the pertainent section from lshal
```

$lshal
...
udi = '/org/freedesktop/Hal/devices/temp/19'
  info.ignore = true  (bool)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0'  (string)
  info.product = 'Ignored Device'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ignored-device'  (string)
  info.vendor = 'Gyration, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/001/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/usb1/1-2'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration = 'USB Receiver'  (string)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 544  (0x220)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/usb1/1-2'  (string)
  usb_device.max_power = 98  (0x62)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = '**Gyration RF Technology Receiver**'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Gyration, Inc.'  (string)
  usb_device.vendor_id = 3094  (0xc16)  (int)
  usb_device.version = 1.1 (1.1) (double)
...

```

that was really the key (maybe superm1 knows why).  after that i just a standard LIRC setup.  

i'm running lirc-0.8.3-0ubuntu2
```

$ lircd --version
lircd 0.8.3

```

here's my hardware.conf
```

$ cat /etc/lirc/hardware.conf 
# /etc/lirc/hardware.conf

#
#Chosen Remote Control
REMOTE="gyration"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd"
REMOTE_LIRCD_CONF=""
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
START_LIRCMD="false"

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

```

and my lircd.conf
```

$ cat /etc/lirc/lircd.conf
#
# lircd.conf 
#    for Gyration MCE remote
# 
begin remote

 name     gyration
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x8001
 gap          135997
 toggle_bit_mask 0x0

      begin codes
#         Power                    0x0074 wrong
         Stop                     0x00A6
         Record                   0x00A7
         Pause                    0x0077
         Rewind                   0x00A8
         Play                     0x00CF
         FastForward              0x00D0
         SkipBack                 0x00A5
         SkipForward              0x00A3
#         LiveTV                   0x0025 wrong
         Up                       0x0067
         Guide                    0x016A
         Left                     0x0069
         Enter                    0x001C
         Right                    0x006A
         Back                     0x009E
         Down                     0x006C
         Info                     0x0082
         VolUp                    0x0073
#         Windows                  0x0066 wrong
         ChanUp                   0x0192
         VolDown                  0x0072
         Mute                     0x0071
         ChanDown                 0x0193
#         Pictures                 0x00E2 wrong
#         TV                       0x016E wrong
#         Music                    0x0187 wrong
#         Video                    0x0189 wrong
         One                      0x0002
         Two                      0x0003
         Three                    0x0004
         Four                     0x0005
         Five                     0x0006
         Six                      0x0007
         Seven                    0x0008
         Eight                    0x0009
         Nine                     0x000A
         StarHash                 0x002A  # Star = 0x2a and 0x08
         Zero                     0x000B
#         Hash                     0x002A  # Hash = 0x2a and 0x03
         Clear                    0x0001
#         Enter                    0x001C  # same as OK
#         SetupMenu                no code
#         Last                     no code
#         Connect                  no code
#         Input                    no code
#         DVDMenu                  0x0029 wrong
     end codes

end remote

```

and the mythtv section from my ~/.lircrc
```

$ cat ~/.lircrc
begin
    remote = gyration
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Rewind
    config = J
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = FastForward
    config = U
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = SkipBack
    config = Home
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = SkipForward
    config = End
    repeat = 0
    delay = 0
end

#begin
#    remote = gyration
#    prog = mythtv
#    button = LiveTV
#    config = C
#    repeat = 0
#    delay = 0
#end

begin
    remote = gyration
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Guide
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Enter
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Info
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

#begin
#    remote = gyration
#    prog = mythtv
#    button = Windows
#    config = firefox&
#    repeat = 0
#    delay = 0
#end

begin
    remote = gyration
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

#begin
#    remote = gyration
#    prog = mythtv
#    button = Pictures
#    config = ?????
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = gyration
#    prog = mythtv
#    button = TV
#    config = ?????
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = gyration
#    prog = mythtv
#    button = Music
#    config = ?????
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = gyration
#    prog = mythtv
#    button = Video
#    config = ?????
#    repeat = 0
#    delay = 0
#end

begin
    remote = gyration
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

#begin
#    remote = gyration
#    prog = mythtv
#    button = StarHash
#    config = ?????
#    repeat = 0
#    delay = 0
#end

begin
    remote = gyration
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Clear
    config = Escape
    repeat = 0
    delay = 0
end

# Enter sends same code as OK

# Setup menu (no code)

# Last (no code)

# Connect (no code)

# Input (no code)

#begin
#    remote = gyration
#    prog = mythtv
#    button = DVDMenu
#    config = O
#    repeat = 0
#    delay = 0
#end

```

hopefully someone else finds this info useful for fixing their remote.  also, if anyone figures out the buttons that i don't have working, let me know.  i copied all the key codes from my .evrouterrc because i couldn't get irrecord to work.

---

### Post by williammanda on 2009-01-26
What was your previous setup? Please state some details, what you liked, what is different between the two setups, etc... Does your gyro mouse function still work? It doesn't for mine.
Thanks

---

### Post by williammanda on 2009-01-27
Here is more detailed information on my problem:

[http://ubuntuforums.org/showthread.php?p=6604959#post6604959](http://ubuntuforums.org/showthread.php?p=6604959#post6604959)

Thanks

---

### Post by cbaker on 2009-02-14
> **williammanda said:**
> What was your previous setup? Please state some details, what you liked, what is different between the two setups, etc... Does your gyro mouse function still work? It doesn't for mine.
Thanks

i used the evrouter package previously (hardy).  it worked fine until intrepid, and i don't know why.  my mouse doesn't work right now, but it did work a few weeks ago.  i dropped it pretty good, so i'm not sure if i broke it or if some configuration broke.

look here for info on the evrouter setup:
[http://ubuntuforums.org/showthread.php?t=479897&page=4](http://ubuntuforums.org/showthread.php?t=479897&page=4)

---

