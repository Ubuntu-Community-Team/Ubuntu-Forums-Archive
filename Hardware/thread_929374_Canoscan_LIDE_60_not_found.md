---
title: "Canoscan LIDE 60 not found"
date: 2008-09-24
forum: Hardware
---

### Post by wyth on 2008-09-24
I've used a Canoscan LIDE 60 with no issues for I don't know how many versions of Ubuntu, until now.  For some reason, Xsane will not find it on my desktop (No Device Found), and after the latest updates, I can't find it on my laptop, either.

The scanner is connected via a usb plug.  When I run lsusb, it the device shows up with the ID 04a9:221c Canon, Inc. (as it should).  It also shows up with cat /proc/bus/usb/devices, so the device is definitely being recognized.  

However, sane-find scanner finds nothing (same when done as root), and the command scanimage -L gives me nothing on the desktop, and just my camera on the laptop (same when done as root).  

Everything is fine with /etc/sane.d/dll.conf and /etc/sane.d/genesys.conf.  The device uses genesys.

Running sane-find-scanner should at least show a usb device.  This means I have to go into windows to use my scanner, and I'm teaching now and need my scanner a lot.  Not cool.  I know the device still works, though, because it works fine in windows.  I'm completely baffled at this point.  

Any ideas?

---

### Post by justsomedude on 2008-09-25
> **wyth said:**
> Any ideas?

Maybe. I have the same scanner, but I don't use Ubuntu, so I'm not sure.

But I do remember I ran into the same problem some month ago, not sure how I solved it though...

Could be a groups issue, please post the ouput of:

```
groups
```

(not as root!)

---

### Post by wyth on 2008-09-25
Howdy,

I'm familiar with groups, and was part of scanner.  But here's the output, just in case:

```
joe adm dialout cdrom floppy audio dip video plugdev users scanner fuse lpadmin admin netdev powerdev sambashare vboxusers hamachi gwen usbfs
```

---

### Post by justsomedude on 2008-09-25
Yes, the scanner group was the thing I was looking for.

I'm not entirely sure how Ubuntu handles udev rules. Have a look into /etc/udev/rules.d. There should be a file called xx-sane.rules somewhere. Mine is called 53-sane.rules.

Open the file, do a text search for "lide", and find the line for your scanner. I've changed mine to this:

```
# Canon CanoScan LiDE 60
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="221c", MODE="0660", GROUP="scanner", ENV{libsane_matched}="yes"
```

MODE should be 0660 or 0666, you have to edit the file as root and log out (maybe even reboot) for the changes to take effect.

Hope this helps. :)

---

### Post by wyth on 2008-09-26
Now that's interesting.  I don't have a sane.rules, but I have libsane.rules on the laptop, and the LiDE 60 line is missing the ENV{libsane_matched}="yes" line.  I don't have anything with sane in the desktop's rules.d.  Going to try adding that and will report back.

---

### Post by wyth on 2008-09-26
Nope, no joy. I added that ENV{libsane_matched}="yes" to 45-libsane.rules, and that didn't take.  The line in 45-libsane.rules, by the way, is ```
# Canon CanoScan LiDE 60
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="221c", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
```

So I tried adding a 53-sane.rules file, with the 45-libsane.rules headers and your line, no luck -- the device still isn't found.  The one difference between your line and the one in 45-libsane.rules is MODE="0660" vs. MODE="0660." I tried it both ways in 53-sane.rules, but nope, no luck.

What I'm confused by is why this worked before, and what has changed.  I don't know if this will be back in 8.10, but I could really use my scanner.

(I also filed a bug, [#274249]("https://bugs.launchpad.net/ubuntu/+bug/274249"))

---

### Post by justsomedude on 2008-09-26
Hmm, okay. I don't think it's important how the file is called. If Ubuntu uses 45-libsane.rules, we should try that.

Try this:

If you have created 53-sane.rules, delete it.

Edit 45-libsane.rules, the important part is MODE="". Change it from MODE="0664" to MODE="0660", save it and reboot, it is possible this file is read at boot time.

Does this help?

---

### Post by wyth on 2008-09-26
Nope, no good, but I appreciate the suggestion.  I tried it with both modes -- not that I'm all that sure what those modes are for.  I just know sane-find-scanner can't even tell there's a scanner plugged in on the usb, even though lsusb and cat /proc/bus/usb/devices show it's present.

Blargh... I don't like booting into windows just to scan a document.

---

### Post by justsomedude on 2008-09-26
Ok. One last attempt:

I'm currently on a Hardy Heron Live CD. 

- I was able to recreate your problem.

- I was able to get xsane running. Try this:

1. Delete the Lide 60 entry from whatever file it is in in /etc/udev/rules.d (there is no sane.rules file on the Live CD). Do this as root of course, and backup the file before doing that.

2. Create a sane.rules file with a low number (low means it's read first).

```
sudo gedit /etc/udev/rules.d/04-sane.rules
```

If you already have a file starting with "04" in /etc/udev/rules.d, choose a different low number.

3. Paste the following code in there and save it:

```
# Canon CanoScan LiDE 60
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="221c", MODE="0660", GROUP="scanner", ENV{libsane_matched}="yes"
```

4. Reload udev:
```

sudo udevcontrol reload_rules
```

5. Unplug your scanner and plug it back in.

6. Start xsane

```
xsane
```


Worked here, I hope it works for you, too. :)

If not, I'm running out of ideas. :confused: If it doesn't work, what happens when you start xsane as root?

```
sudo xsane
```

Good luck!

---

### Post by wyth on 2008-09-26
That was a brilliant attempt -- really you've gone way beyond the call of duty here, thank you.  

It still doesn't pick up the scanner, but sometimes the math can be fantastic even when the solution doesn't work.

---

