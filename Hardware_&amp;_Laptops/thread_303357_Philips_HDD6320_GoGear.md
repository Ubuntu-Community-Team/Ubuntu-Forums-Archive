---
title: "Philips HDD6320 GoGear"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by slakkie on 2006-11-20
Hello all,

I just bought a Philips HDD6320/00 Gogear MP3 player.
When I came home I noticed that I could not mount the player. The system does recognize the player:

```

udi = '/org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M'  (string)
  linux.subsystem = 'usb'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.is_self_powered = false  (bool)
  usb_device.version_bcd = 512  (0x200)  (int)
  usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.serial = '           65932942M'  (string)
  usb_device.linux.device_number = 12  (0xc)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 1  (0x1)  (int)
  info.product = 'Philips HDD63XX GoGear'  (string)
  usb_device.product = 'Philips HDD63XX GoGear'  (string)
  info.vendor = 'Philips'  (string)
  usb_device.vendor = 'Philips'  (string)
  usb_device.product_id = 331  (0x14b)  (int)
  usb_device.vendor_id = 1137  (0x471)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb3/3-3'  (string)
  info.linux.driver = 'usb'  (string)
  info.bus = 'usb_device'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:1d.7/usb3/3-3'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb3/3-3'  (string)

```

Does anyone know how to mount this device?

I did find an implementation of opengogear ( [http://opengogear.sarovar.org/](http://opengogear.sarovar.org/) ) so I can copy/import MP3's to the player, yet I have to mount it first.

I will post the output of [https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices) later today.

```
uname -a
Linux eniac.euronet.nl 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

```

TIA,

Wesley

---

### Post by slakkie on 2006-11-21
I got somewhere.. 

mtp-detect detects the player, and the following page got me a lot further:

[http://tricky.vanstaveren.us/Projects/Open_Source/Banshee/MTP](http://tricky.vanstaveren.us/Projects/Open_Source/Banshee/MTP)

I have to install a whole bunch of packages in order to resolve depencies, but at least I'm getting somewhere :)

---

### Post by slakkie on 2006-11-21
Almost there.. 

Everything is compiled from the sources (as described in the howto), I did not retreive banshee from cvs (due to a missing file). I downloaded the 0.11.2 tarball.

```

banshee --version     
Banshee 0.11.2

banshee --debug                                       
** Running Banshee in Debug Mode **
Warning: [11/21/2006 1:22:30 PM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed
Debug: [11/21/2006 1:22:32 PM] (Loading audio profiles) - /usr/local/share/banshee/audio-profiles
Debug: [11/21/2006 1:22:33 PM] (Default player engine) - GStreamer 0.10
Debug: [11/21/2006 1:22:33 PM] (Audio CD Core Initialised) - 
Building initial DAAP database from local library...
Starting DAAP Server
Setting MusicBrainz proxy to [www.musicbrainz.org:80](www.musicbrainz.org:80)
** Scheduler: Job scheduled (Banshee.Plugins.MetadataSearch.MetadataSearchPlugin+ScanLibraryJob, Normal)
** Scheduler: execution thread created
** Scheduler: Job started (Banshee.Plugins.MetadataSearch.MetadataSearchPlugin+ScanLibraryJob)
** Scheduler: Job ended (Banshee.Plugins.MetadataSearch.MetadataSearchPlugin+ScanLibraryJob)
** Scheduler: execution thread destroyed, no more jobs scheduled
Debug: [11/21/2006 1:22:52 PM] (MTP: device found: vendor=1137, prod=331) - 
Debug: [11/21/2006 1:22:52 PM] (MTP: device was found in database, but libgphoto2 failed to detect it.  Waiting for it to come alive.  GPhotoDeviceID == -1, # found = 0) - 

And this is working.. 

gphoto2 -L
There is no file in folder '/'.                                                
There are 3 files in folder '/store_00010001'.
There is no file in folder '/store_00010001/Camera'.
There is no file in folder '/store_00010001/Music'.
There is no file in folder '/store_00010001/Music/Sample'.
There are 5 files in folder '/store_00010001/Music/Sample/Sample1'.
There are 4 files in folder '/store_00010001/Music/Sample/Sample2'.
There are 4 files in folder '/store_00010001/Music/Sample/Sample3'.
There is no file in folder '/store_00010001/Pictures'.
There are 6 files in folder '/store_00010001/Pictures/sample images'.
There is no file in folder '/store_00010001/Playlists'.
There is no file in folder '/store_00010001/Recordings'.
There is no file in folder '/store_00010001/Recordings/FMRecordings'.
There is no file in folder '/store_00010001/Recordings/LineinRecordings'.
There is no file in folder '/store_00010001/Recordings/VoiceRecordings'.
There is no file in folder '/store_00010001/_System'.
There is 1 file in folder '/store_00010001/support'.
There are 18 files in folder '/store_00010001/support/sample images'.
There is no file in folder '/store_00010001/tmp'.

```

So far.. so.. frustrating ;)

---

### Post by slakkie on 2006-12-12
Removed libgphoto from the Ubuntu packages to get a clean system (free of deps).
```

dpkg -P --force-all libgphoto2-2 libgphoto2-2-dev libgphoto2-port0

```

Making libgphoto from the sources:
```

cd $HOME/mtp/new/libgphoto2-2.3.0
./configure
make && sudo make install

```

Notes from tricky (the MTP developer for banshee - see the link in one of the previous posts for the official HOWTO):
```

cd packaging/generic/print-camera-list
./print-camera-list hal-fdi > 10-libgphoto2.fdi
mv 10-libgphoto2.fdi /usr/share/hal/fdi/information/10freedesktop/

```

Now we restart the hal daemon (108 is the uid of the hal user, grep hal /etc/passwd to get your correct uid).
```

$ ps -ef | grep hal | grep ^108 | awk '{print $2}' | xargs sudo kill -9   
$ sudo /usr/sbin/hald

```

Check if HAL can detect the device:
```

$ hal-find-by-capability --capability "camera"
/org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0

$ hal-device /org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0
udi = '/org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0'  (string)
  camera.libgphoto2.support = true  (bool)
  camera.libgphoto2.name = 'Philipps HDD6320 2'  (string)
  portable_audio_player.output_formats = { 'audio/mpeg' } (string list)
  portable_audio_player.type = 'mtp'  (string)
  portable_audio_player.access_method = 'user'  (string)
  info.capabilities = { 'camera', 'portable_audio_player' } (string list)
  info.category = 'portable_audio_player'  (string)
  linux.subsystem = 'usb'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  info.product = 'USB Vendor Specific Interface'  (string)
  usb.interface.protocol = 255  (0xff)  (int)
  usb.interface.subclass = 255  (0xff)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb3/3-4/3-4:128.0'  (string)
  usb.num_configurations = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor_id = 1137  (0x471)  (int)
  usb.product_id = 331  (0x14b)  (int)
  usb.vendor = 'Philips'  (string)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.device_revision_bcd = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.linux.device_number = 44  (0x2c)  (int)
  usb.serial = '           65932942M'  (string)
  usb.speed_bcd = 294912  (0x48000)  (int)
  usb.version_bcd = 512  (0x200)  (int)
  usb.is_self_powered = false  (bool)
  usb.can_wake_up = false  (bool)
  usb.bus_number = 3  (0x3)  (int)
  info.bus = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:1d.7/usb3/3-4/3-4:128.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb3/3-4/3-4:128.0'  (string)


```
See [http://pastebin.ca/276364](http://pastebin.ca/276364) for similair output.

Continue with libgphoto-sharp
```

$ cd $HOME/mtp/new/libgphoto-sharp
$ ./configure
$ make && sudo make install

```

Check if the libgphoto installs went OK by installing gphoto:
```

$ cd $HOME/mtp/new/gphoto
$ make && sudo make install

```

And test it.. 
```

$ gphoto2 -l

There is 1 folder in folder '/'.                                               
 - store_00010001
There are 8 folders in folder '/store_00010001'.
 - Camera
 - Music
 - Pictures
 - Playlists
 - Recordings
 - _System
 - support
 - tmp
[snip, more output, no need to display]

```

Get banshee from the cvs tree
```

$ cd $HOME/mtp/new/
$ cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P banshee
$ cd banshee
$ ./autogen.sh --enable-mtp --disable-docs # I want to disable docs, otherwise install monodocs
$ ./configure --enable-mtp # same options as autogen (this is only needed if you downloaded the banshee sources in a tarball).
$ make && sudo make install

```

Lets check and see if we can banshee with my HDD6320!
```

$ banshee
Warning: [12/12/2006 4:20:34 PM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed
Debug: [12/12/2006 4:20:35 PM] (Loading audio profiles) - /usr/local/share/banshee/audio-profiles
Debug: [12/12/2006 4:20:37 PM] (Default player engine) - GStreamer 0.10
Debug: [12/12/2006 4:20:37 PM] (Audio CD Core Initialised) - 
Debug: [12/12/2006 4:20:37 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0
Debug: [12/12/2006 4:20:37 PM] (MTP: Starting initialization) - product_id=331, vendor_id=1137, type=mtp, name=Philipps HDD6320 2
Debug: [12/12/2006 4:20:38 PM] (MTP: device found) - vendor=1137, prod=331
Debug: [12/12/2006 4:20:38 PM] (MTP: found a device that's not what we're looking for; perhaps a camera?) - vendor=1137, prod=331
Debug: [12/12/2006 4:20:38 PM] (MTP: device was found in database, but libgphoto2 failed to detect it. Waiting for it to come alive.  GPhotoDeviceID == -1, # found = 0) - 
Debug: [12/12/2006 4:20:38 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0
Debug: [12/12/2006 4:21:10 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0
Debug: [12/12/2006 4:21:10 PM] (MTP: Starting initialization) - product_id=331, vendor_id=1137, type=mtp, name=Philipps HDD6320 2
Debug: [12/12/2006 4:21:10 PM] (MTP: device found) - vendor=1137, prod=331
Debug: [12/12/2006 4:21:10 PM] (MTP: device was found in database, but libgphoto2 failed to detect it. Waiting for it to come alive.  GPhotoDeviceID == -1, # found = 0) - 
Debug: [12/12/2006 4:21:10 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/usb_device_471_14b____________65932942M_if0


```

BLIEB.. still the same issue..

---

### Post by glittalogik on 2007-03-06
Hey Slakkie, any luck with this yet? I'm about to have a crack at it, and noticed that you hadn't made any mention of checking the player firmware - apparently if you're using earlier than 2.4 then it will cause USB endpoint issues. You can check firmware on the player in (IIRC) Settings --> Information.

You can get the latest firmware by downloading the Philips Device/Firmware Manager v5.2 from [http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?ctn=HDD6320/00](http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?ctn=HDD6320/00)
 - you'll need to run that on a WinXP SP1 or later machine.

---

### Post by Silenz on 2007-03-17
on
[http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=ENG&cat=MP3_PLAYERS_CA&sct=HDD_AUDIO_JUKEBOX_SU&session=20070317133926_82.83.71.15&grp=PORTABLE_ENTERTAINMENT_GR&ctn=HDD6320/00&mid=Link_Software&hlt=Link_Software](http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=ENG&cat=MP3_PLAYERS_CA&sct=HDD_AUDIO_JUKEBOX_SU&session=20070317133926_82.83.71.15&grp=PORTABLE_ENTERTAINMENT_GR&ctn=HDD6320/00&mid=Link_Software&hlt=Link_Software)
i just can find firmware V 2.1
there is no 2.4... but i remember there was a firmware update.. bu where can i get it...

amarok freezes  on connection with the gogear 6320/05

---

### Post by glittalogik on 2007-05-14
As above:
> You can get the latest firmware by downloading the Philips Device/Firmware Manager v5.2 from [http://www.p4c.philips.com/cgi-bin/d...ctn=HDD6320/00](http://www.p4c.philips.com/cgi-bin/d...ctn=HDD6320/00)
- you'll need to run that on a WinXP SP1 or later machine.

You can't get 2.4 on its own, but it's included with the full device manager package.

---

