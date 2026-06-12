---
title: "Mounting USB devices - which drivers do I need?"
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by steffen on 2005-01-23
Anyone know what I need to mount USB devices (Flash and HD based) onto my computer.

Everywhere I see that people have managed with sudo mount /dev/sda or sda1 or sdc or sdb1 og sdb or sda2, etc. with -t, vfat, -0, umask=000, etc.

However, every time I attempt to mount either my Canon Digital Ixus or my Creative Jukebox Nomad or Creative Jukebox Zen, I receive error that /dev/sd* don't exist.

How can I set this up?

I know my USB is working, because I'm able to sync my Palm through ttyUSB0

Which drivers do I need to download to have this working?

---

### Post by hardcandy on 2005-01-23
When you hook them up, do they show in device manager?

---

### Post by steffen on 2005-01-23
Both of them do.

I also installed 'usbview', and as soon as I connect them, they show up.

However, I can't find them anywhere in filemanager, or sda-stuff.

---

### Post by steffen on 2005-01-23
Hi!

I was a bit quick in my posting here. I was struggling for hours yesterday in connecting my mp3 players. I never managed to get gnomad2 to recognize them.

When I attached my camera today, I assumed I would have the same problem. But after having installed GTKAM, it automatically detected my camera, and imported my pictures. Great!

If anyone know how to get gnomad2 to work in the same way, or mounting those mp3 players, I appreciate it. I attach them, they are detected, but my system can't find them.

There seems to be a good guide for it here: [http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article)

The only thing I haven't done is to do the > cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox 

...I think

But if I do, I get an error that directory nomadjukebox don't exist. Of course it doesn't, but I don't understand where I should copy it from...

...any suggestion appreciated!

---

### Post by steffen on 2005-01-23
I have libnjb, libusb, and all the other libraries installed. However, I don't have any directory called libnj, which apparently I should...

---

### Post by jakeslife on 2005-01-23
I plugged in my Digital Camera and it recognized it just fine, along with my friends MP3 player.

---

### Post by steffen on 2005-01-23
Here is what I have attempted to do, since simply installing libnjb didn't work:

1) Installed libusb and libusb-dev

2) Fetched the latest CVS from [http://sourceforge.net/project/showfiles.php?group_id=32528](http://sourceforge.net/project/showfiles.php?group_id=32528)

3) ./configure && make && sudo make install && sudo ldconfig

4) I then had to do some weird stuff to get this to work.
I didn't get > sudo cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox to work, because apparently I didn't have permissions, even with sudo, to edit usb.usermap. As well, there was no usb.usermap. So what I did was to > sudo cp /usr/share/doc/hotplug/examples/usb.usermap /etc/hotplug/usb/usb.usermap then > sudo gedit /etc/hotplug/usb/usb.usermap, then open libnjb-2.0/nomad.usermap with gedit as well, and copy the whole thing over to usb.usermap. Then save.

5) cp nomadjukebox /etc/hotplug/usb/ worked fine. However, I had to cd /etc/hotplug/usb to be able to sudo chmod a+x nomadjukebox

Then I restarted my computer. But when I fire up Gnomad2, I still get error message that no jukebox was found on the USB bus... :(

---

### Post by steffen on 2005-01-23
My Canon digital camera shows up immediately, both in device manager and in usbview.

The mp3 player, however, doesn't show up at all, anywhere. I managed to have it show up in device manager yesterday at one point, but don't know why it disappeared again...

---

### Post by hardcandy on 2005-01-23
USB issues
----------

Some users experience problems with USB communication. There are some
hardware USB controllers which is problematic. This might be caused
by either electrical properties of the bus, or by badly programmed 
drivers in the host kernel.

nForce 2 motherboards are known to be problematic.
You don't have one of these do you. Also, if you have one, maybe try a powered usb hub, sometimes they will work a little better.

---

### Post by steffen on 2005-01-24
Don't know if my IBM Thinkpad T40 has a nForce2 motherboard.

I actually removed the custom libnjb now, and re-installed the debian linjb (older version). Don't know if that had anything to do with it, but after a couple of reboots, I now suddenly see the Jukebox in the usbview.

But still, gnomad2 doesn't detect it, and I'm not able to mount it...

---

### Post by diebels on 2005-02-23
:smile: **Just got my zen micro recognized by gnomad2.** What you need is libnjb and gnomad2. Tried some packages, but I guess they where to old. Now I have libnjb-cvs-today and gnomad2 2.6.3 running. Removed the old packages, installed libnjb from cvs and compiled gnomad2_2.6.3 from source. Need to "sudo gnomad2" for it to recognice the player, but that's a minor problem permissions problem to fix later.

Gnomad2 says my firmware revision is 1.1.3

---

### Post by diebels on 2005-02-23
By the way, for the micro to be mounted as a block device it must be activated in the menus on the player. Block device storage is seperate from the music, steals a size you define from music storage capasity, and can not be played. Not sure if that's the case with your players.

---

### Post by diebels on 2005-02-23
You just have to love this player. Damn small, great sound and smart menus. Hope it get's at least universe/multiverse support in hoary.

---

