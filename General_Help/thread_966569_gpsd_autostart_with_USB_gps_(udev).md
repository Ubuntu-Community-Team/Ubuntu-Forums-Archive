---
title: "gpsd autostart with USB gps (udev)"
date: 2008-11-01
forum: General Help
---

### Post by jared_c on 2008-11-01
Took me a while to figure out how to accomplish this, here's the instructions on how to get gpsd to autostart when I plug my USB gps into the computer.

First, make sure that the computer is seeing your gps.  Plug in the GPS then type:

dmesg | tail

This tells you what your computer just did with the gps.  Mine shows this:

[ 6155.044088] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 6155.223458] usb 3-2: configuration #1 chosen from 1 choice
[ 6155.435134] usbserial: USB Serial support registered for pl2303
[ 6155.436614] pl2303 3-2:1.0: pl2303 converter detected
[ 6155.452112] usb 3-2: pl2303 converter now attached to ttyUSB3
[ 6155.454457] usbcore: registered new interface driver pl2303
[ 6155.454471] pl2303: Prolific PL2303 USB to serial adaptor driver

My gps is really a serial port gps, and the manufacturer installed a USB-to-serial adapter to make it a USB gps.  It has now been attached to /dev/ttyUSB3.  I can run "gpsd /dev/ttyUSB3" and gpsd will start up.

What I want is for gpsd to start automatically when I plug my gps in.

This is supposed to happen anyway, but gpsd is a little broken, due to both debian and ubuntu modifications.

Now, part of the problem is in /etc/default/gpsd.  Change the line that reads "USBAUTO=false" to "USBAUTO=true"  I know, the file has a big warning at the top that you should only change this file with "dpkg-reconfigure gpsd", but that's currently broken.  Please see [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/8b068eb84b0845dd/fab503e152576f07?lnk=raot](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/8b068eb84b0845dd/fab503e152576f07?lnk=raot)

The rest of the problem is in the udev setup.  Open (back it up first) /lib/udev/gpsd.hotplug.wrapper, and change the line that says 

[ "$START_DAEMON" = "true" ] || exit 0 

to

[ "$START_DAEMON" = "false" ] || exit 0

That's all part of the above google groups link.  

Do you see the line towards the end that says ". /lib/udev/hotplug.functions"?  That file currently does not exist in ubuntu, therefore when this script tries to run that file it fails.  That's where the function "wait_for_file" used later is defined.  Now, we can comment out these three lines:

. /lib/udev/hotplug.functions
wait_for_file /usr/bin/python && \
wait_for_file /var/run && \

by placing a # symbol before them, and that solves the current problem.  However, it also adds a problem, because those lines are there so that gpsd can start when the computer boots, and those lines make gpsd wait until certain files exist before starting up.  A better solution in my mind is providing the missing "hotplug.functions" file.  Where can we get one?  Why, from Debian, of course!  Looking through their files, it looks like etch, lenny, and sid all have hotplug.functions, and the differences between the two are in comments and whitespace only.  I think we should use the latest from sid.  I'm not sure why it's not in Intrepid, but maybe there was a good reason for removing it, or maybe sid was broken and didn't have it when they did the sync.  *shrug*  

Download the udev package from [http://packages.debian.org/sid/i386/udev/download](http://packages.debian.org/sid/i386/udev/download)  Open it in Archive Manager (not the GDebi package installer, we don't want to install it, just pull the hotplug.functions file out of it).  Go into data.tar.gz, . , lib, udev, and there it is, hotplug.functions!  Extract that file only, and copy it to /lib/udev/ where it will do it's job.

That's it, all done.  Now when I plug my gps in gpsd automatically starts.  

Now, if this doesn't work for you, another possible issue could be in one of the files we haven't looked at.  If it's not recognized as a GPS, your problem is probably in /etc/udev/rules.d/50-gpsd.rules  I would compare the output of lsusb and the rules in 50-gpsd.rules, see if it's recognizing it.  You may have to learn some bash scripting, but it's not to difficult.  

If you have a bluetooth GPS I have no idea where to go looking, nor do I know much about real serial gps's.

---

### Post by nixi on 2009-01-16
Woah, thank you very much! :)

---

### Post by zagor83 on 2009-02-08
Can somebody help me?

I have Navilock NL-302U GPS receiver, and I don't know how to set
baud rate on 4800 using GPSD

---

### Post by marcin on 2009-05-05
> **zagor83 said:**
> Can somebody help me?

I have Navilock NL-302U GPS receiver, and I don't know how to set
baud rate on 4800 using GPSD

I don't know how gpsd works, but you can see baud rate using:
stty -F /dev/ttyUSB0 (the device be different)
and set it:
sudo stty -F /dev/ttyUSB0 ispeed 4800

---

### Post by synace on 2009-07-14
this is working for me now for first hotplug, but i'd also like to start a custom script that I need for google earth upon hotplug of the device:

echo rw|netcat localhost 2947 > /tmp/gps.dump
gpsbabel -i nmea -f /tmp/gps.dump -o kml -F /tmp/gps.kml

i'd also like to track the pid's of these, and kill them upon unplug.

it appears that the unplug isn't killing gpsd properly currently as well.

debugging in /lib/udev/gpsd.hotplug
```

def hotplug(action, devpath):
    syslog.syslog("ACTION=%s DEVPATH=%s" % (action,devpath))

```
```

Jul 14 16:19:04 synacetablet kernel: [13701.536059] usb 3-1: new full speed USB device using ohci_hcd and address 55
Jul 14 16:19:05 synacetablet kernel: [13701.697968] usb 3-1: configuration #1 chosen from 1 choice
Jul 14 16:19:05 synacetablet kernel: [13701.699161] pl2303 3-1:1.0: pl2303 converter detected
Jul 14 16:19:05 synacetablet kernel: [13701.723267] usb 3-1: pl2303 converter now attached to ttyUSB0
Jul 14 16:19:05 synacetablet gpsd.hotplug: gpsd_control(action=add, arg=/dev/ttyUSB0)
Jul 14 16:19:05 synacetablet gpsd.hotplug: socket /var/run/gpsd.sock doesn't exist
Jul 14 16:19:05 synacetablet gpsd.hotplug: launching gpsd -F /var/run/gpsd.sock
Jul 14 16:19:05 synacetablet NetworkManager: <info>  (ttyUSB0): ignoring due to lack of mobile broadband capabilties 
Jul 14 16:19:27 synacetablet kernel: [13724.390236] usb 3-1: USB disconnect, address 55
Jul 14 16:19:27 synacetablet kernel: [13724.393128] pl2303 3-1:1.0: device disconnected

```
manually killed the gpsd process ( sudo killall -9 gpsd; sudo rm /var/run/gpsd.sock; ), only then does the disconnect & remove fire
```

Jul 14 16:20:30 synacetablet kernel: [13786.795058] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
Jul 14 16:20:30 synacetablet gpsd.hotplug: gpsd_control(action=remove, arg=/dev/ttyUSB0)
Jul 14 16:20:30 synacetablet gpsd.hotplug: gpsd_control(action=remove, arg=/dev/ttyUSB0)
Jul 14 16:20:30 synacetablet gpsd.hotplug: socket /var/run/gpsd.sock creation failure: [Errno 111] Connection refused
Jul 14 16:20:30 synacetablet gpsd.hotplug: can't reach gpsd

```

---

### Post by synace on 2009-07-14
i modified a script for google earth that i found that expected nmea data from the serial port

```

gpspipe -r | gegpsd

```

had to install python-serial: 
```

sudo apt-get install python-serial

```

/usr/local/bin/gegpsd
```

#!/usr/bin/python

# Copyright (C) 2007 by Jaroslaw Zachwieja <grok!warwick.ac.uk>
# Copyright (C) 2008 by TJ <linux!tjworld.net>
# modified 2009 by synace to use stdin for use with gpspipe
# Published under the terms of GNU General Public License v2 or later.
# License text available at http://www.gnu.org/licenses/licenses.html#GPL

import serial
import string
import sys
import getopt

def main():
	# defaults
	file = '/dev/shm/gps.kml'

	print "Serving data from stdin to %s" % (file)

	latitude = 0
	longitude = 0
	speed = 0
	heading_in = 0
	altitude = 0
	range = 1000
	tilt = 30

	while 1:
		line = sys.stdin.readline()

		datablock = line.split(',') 

		if line[0:6] == '$GPRMC':
			latitude_in = string.atof(datablock[3])
			longitude_in = string.atof(datablock[5])
			try:

				altitude = string.atof(datablock[8])
			except ValueError:
				# use last good value
				altitude = altitude
			speed_in = string.atof(datablock[7])

			try:
				heading_in = string.atof(datablock[8])
			except ValueError:
				# use last good value
				heading_in = heading_in
			if datablock[4] == 'S':
				latitude_in = -latitude_in
			if datablock[6] == 'W':
				longitude_in = -longitude_in

			latitude_degrees = int(latitude_in/100)
			latitude_minutes = latitude_in - latitude_degrees*100

			longitude_degrees = int(longitude_in/100)
			longitude_minutes = longitude_in - longitude_degrees*100

			latitude = latitude_degrees + (latitude_minutes/60)
			longitude = longitude_degrees + (longitude_minutes/60)

			speed = int(speed_in * 1.852)
			range = ( ( speed / 100  ) * 350 ) + 650
			tilt = ( ( speed / 120 ) * 43 ) + 30
			heading = heading_in

			if speed < 10:
				range = 200
				tilt = 30
				heading = 0

			output = """<?xml version="1.0" encoding="UTF-8"?>
	<kml xmlns="http://earth.google.com/kml/2.0">
		<Placemark>
			<name>%s km/h</name>
			<description>^</description>
			<LookAt>
				<longitude>%s</longitude>
				<latitude>%s</latitude>
				<range>%s</range>
				<tilt>%s</tilt>
				<heading>%s</heading>
			</LookAt>
			<Point>
				<coordinates>%s,%s,%s</coordinates>
			</Point>
		</Placemark>
	</kml>""" % (speed,longitude,latitude,range,tilt,heading,longitude,latitude,altitude)

			f=open(file, 'w')
			f.write(output)
			f.close()


if __name__ == "__main__":
	main()

```

since the kml file is written every second or so, i put it on ramdisk.


i also modified /lib/udev/gpsd.hotplug
```

    elif action == 'add':
        gpsdcmd = "gpsd -F " + CONTROL_SOCKET
        syslog.syslog("launching %s" % gpsdcmd)
        os.system(gpsdcmd)

        # by synace: patch to add a kml file for google earth into /dev/shm/gps.kml
        googlecmd = "gpspipe -r | gegpsd"
        os.system(googlecmd)

        connect = gpsd_control_connect()

```

and /lib/udev/gpsd.hotplug.wrapper
```

# wait for /usr & /var & /dev/shm to be mounted
wait_for_file /usr/bin/python && \
wait_for_file /var/run && \
wait_for_file /dev/shm && \
  exec /lib/udev/gpsd.hotplug "$ACTION" "$DEVNAME"

```

this doesn't seem to wait though.. it either starts before /dev/shm is there (or my GPS is taking too long to start streaming data).. any thoughts??

---

### Post by synace on 2009-07-14
also, you need to load up a kml that will load the dynamic one & reload.

```

<?xml version="1.0" encoding="UTF-8"?>
<kml xmlns="http://earth.google.com/kml/2.1">
<NetworkLink>
	<name>GPS</name>
	<flyToView>1</flyToView>
	<Url>
		<href>/dev/shm/gps.kml</href>
		<refreshMode>onInterval</refreshMode>
		<refreshInterval>1</refreshInterval>
	</Url>
</NetworkLink>
</kml>

```

i also since disable the hotplug. it's still not quite working properly.

---

