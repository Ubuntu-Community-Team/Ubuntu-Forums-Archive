---
title: "no more garmin gps?"
date: 2009-04-27
forum: Hardware
---

### Post by shane2peru on 2009-04-27
Ok, I wanted to download my tracks from my garmin nuvi 200w to my computer and put them on Google earth.  I was able to connect to my gps in ibex, however I'm not able to connect or even see it on Jaunty.  I don't know if this is  a bug or what any help would greatly be appreciated.  Here is what I have done:

```

lsusb
Bus 001 Device 005: ID 0d49:7310 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c508 Logitech, Inc. Cordless Trackball
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and 
```

cat /etc/modprobe.d/blacklist.conf | grep garmin
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

```

Which according to this web site should be blacklisted: [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)

And the bug refered to by the blacklist file is here:
[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/114565](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/114565)

Any help or information on this would be greatly appreciated!  Thanks

Shane

---

### Post by shane2peru on 2009-04-27
Scratch that, sorry, about that.  I tried a new cable and it was detected.  :)  Basic troubleshooting procedure.

Shane

---

### Post by shane2peru on 2009-04-27
Ok, got connected and cannot get the info off of my garmin here is what I did:

```

gpsbabel -t -r -w -i garmin -f usb: -o gpx -F backup.gpx
Claim interfaced failed: could not claim interface 0: Operation not permitted

```
That isn't good. :)  Any help here would be appreciated.  Thanks!

Shane

---

### Post by rogerdean on 2009-04-28
My Garmin (Vista Cx) is working fine after I did the same things I used to do after Intrepid install...

```
echo 'SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666"' >> /etc/udev/rules.d/51-garmin.rules
```

Reboot

```
gpsbabel -w -t -r -i garmin -f usb: -o kml -F /home/roger/Desktop/gpsdown.kml
```

Hope this helps
Cheers
Roger

---

### Post by shane2peru on 2009-04-29
> **rogerdean said:**
> My Garmin (Vista Cx) is working fine after I did the same things I used to do after Intrepid install...

```
echo 'SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666"' >> /etc/udev/rules.d/51-garmin.rules
```

Reboot

```
gpsbabel -w -t -r -i garmin -f usb: -o kml -F /home/roger/Desktop/gpsdown.kml
```

Hope this helps
Cheers
Roger

Well, it was worth a try.  I'm still getting that odd error message posted in the first post.  Thanks for the thought.  I had a different garmin.rules but I deleted it and then ran your line, rebooted and no good.  Any further thoughts would be greatly appreciated.  

Shane

---

### Post by shane2peru on 2009-04-29
ok, I re-installed since I had installed the Jaunty RC, now I have the regular release of Jaunty amd64.  I tried what you said again and nothing.  Also for further info my Garmin mounts like this:

```

/dev/sdc on /media/GARMIN type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

Perhaps someone can decipher and help me out with that.  Thanks.

Shane

---

### Post by shane2peru on 2009-04-30
Does anyone have any ideas about this?

Shane

---

### Post by pmt on 2009-07-21
Does anyone found a solution? ... same problems at my side :confused:

---

### Post by caseylem on 2009-07-28
Hi,

> 
gpsbabel -t -r -w -i garmin -f usb: -o gpx -F backup.gpx
Claim interfaced failed: could not claim interface 0: Operation not permitted
I had the same problem but solved it completely by recompiling my kernel with the option
CONFIG_SYSFS_DEPRECATED "disabled" and then reboot on the new kernel.

I think that all users having this message with the Garmin are suffering from the same problem : gpsbabel obviously uses a new style of interface that doesn't talk well to old style kernels.

To check restart udev and look for the following output in "dmesg" (at the end): 

deprecated sysfs layout (kernel too old, or CONFIG_SYSFS_DEPRECATED) is unsupported, some udev features may fail

If you see this you have almost solved your problem as in that case recompiling the kernel fixes everything :-)

Of course you also have to put garmin_gps on the blacklist and add the /etc/udev/rules.d/garmin.rules but that is already explained above.

Success,
Casey

---

### Post by pmt on 2009-08-02
Hi Casey,

thanks for the hint. Unfortunatelly, seems to be, my problems have other reasons:

after
sudo /etc/init.d/udev restart

dmesg only say:

udev: starting version 141

Which looks ok for me. Know Warnings or Error messages :-(

---

### Post by Havok_Rocka on 2009-08-09
Ok, could anybody explain the solution to the "Claim interfaced failed: could not claim interface 0: Operation not permitted" - problem in words that an absolute new ubuntu/linux users understands? That would be fantastic! 
Thanks.

---

### Post by michaelayland on 2009-09-03
I am at the very same stage as the previous correspondent it seems that Jaunty is not recognising the USB port the garmin (60CSx) is attached to. I have also tried to by-pass this and go Bluetooth using a GPS Bluetooth Mouse but babbel does not like this either!  Oh botheration.. any help welcomed!

---

### Post by darkazurka on 2010-04-11
> **shane2peru said:**
> Ok, got connected and cannot get the info off of my garmin.<snip>

UPDATE
For Ubuntu 10.10 'Maverick' just follow the instructions(all section instructions!) for the section "Ubuntu --> 
Dapper Drake" at [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html) and it will work! Don't forget to turn on your device while it is connected through usb!

For an OS based on Jaunty Jackalope 9.04, it was enough to follow [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html) do
what the webpage says for dapper drake, except no need to edit /etc/modprobe.d/blacklist because it's already blacklisted in there!

Although(again for 9.04 'Jaunty') I edited /etc/udev/rules.d/51-garmin.rules as in the instructions. Then I rebooted the computer, while my gps device was connected (but without having gone through setup-> interface-> 'USB Mass Storage').

I only needed to transfer waypoints to my computer as a gpx file (using "Gebabbel", a gpsbabel frontend/gui) and I succeeded.

---

### Post by Ticatla on 2011-06-13
> **darkazurka said:**
> UPDATE
For Ubuntu 10.10 'Maverick' just follow the instructions(all section instructions!) for the section "Ubuntu --> 
Dapper Drake" at [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html) and it will work! Don't forget to turn on your device while it is connected through usb!
.

Just a small comment about those instructions: they also work nice in Ubuntu 11.04 after having exactly the same problem. By the way I used gksudo gedit /path/file

See ya!

---

### Post by john_spiral on 2012-01-10
FYI:

I'm using Ubuntu/Lubuntu 11.10 with a Garmin edge 205, the below commands run as root worked a treat!

apt-get install gpsbabel
gpsbabel -r -i gpx -f cyclestreets1472914quietest.gpx -o garmin -F usb:

In the above command cyclestreets1472914quietest.gpx is a file I downloaded from a cycle mapping service.

hope this helps someone.

I guess having a look at [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html) should fix needing to be root.

---

