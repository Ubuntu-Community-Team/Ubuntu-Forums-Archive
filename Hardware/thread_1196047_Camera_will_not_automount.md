---
title: "Camera will not automount"
date: 2009-06-24
forum: Hardware
---

### Post by txtinman on 2009-06-24
I use GNOME, but recently tried KDE for a while. I didn't like and came back to GNOME. After removing KDE my Nikon D50 will no longer auto-mount. It worked fine before. I checked the camera settings and they are still as before. The camera is setup as a mass storage device. If I put the SD card into a USB card reader the card is auto-mounted as it should be. If I try to mount the camera manually, I'm told I do not have permission to mount the device.

Any help is appreciated.

Mike White

My last post has the fix.

---

### Post by txtinman on 2009-06-26
Bump

---

### Post by jerrrys on 2009-06-26
here's one thing to try.  go to Synaptic Package Manager and reinstall 'gnome-volume-manager'...

---

### Post by txtinman on 2009-06-28
> **jerrrys said:**
> here's one thing to try.  go to Synaptic Package Manager and reinstall 'gnome-volume-manager'...

I checked that out. I found that gnome-volume-manager was not installed on my computer. I installed it, but still no joy. I just don't understand why the camera won't mount but if I put the card into a simple card reader it mounts just fine. I wonder if there could be some problem with the camera itself? It seems to operate just fine other than not being mounted by the computer.

Mike White

---

### Post by jerrrys on 2009-06-29
plug in your camera, turn it on and enter  **lsusb  **in terminal.  that should bring up your camera.

---

### Post by txtinman on 2009-06-29
> **jerrrys said:**
> plug in your camera, turn it on and enter  **lsusb  **in terminal.  that should bring up your camera.
Here is the result. It does show the camera, but the camera still does not show in Nautilus. When I click on the computer tab in Nautilus the camera should show as a mass storage device like it used to.

```
mike@mike-desktop:~$ lsusb
Bus 001 Device 100: ID 04b0:0409 Nikon Corp. D50 digital camera
```

---

### Post by jerrrys on 2009-06-29
well, that tells me that your camera is not the problem. are you running 9.04?

look in File System>Media.  a camera should show as a "Disk" folder.  if such a folder exist without the camera being plugged in, then that folder needs to be deleted.

---

### Post by txtinman on 2009-06-29
> **jerrrys said:**
> well, that tells me that your camera is not the problem. are you running 9.04?

look in File System>Media.  a camera should show as a "Disk" folder.  if such a folder exist without the camera being plugged in, then that folder needs to be deleted.
The only things showing there are my cdrom drives. And yes I am running 9.04.

---

### Post by jerrrys on 2009-06-29
ok, been doing some more digging.  this seems to be good reading

[http://www.uluga.ubuntuforums.org/showthread.php?t=1003745](http://www.uluga.ubuntuforums.org/showthread.php?t=1003745)

and #2 here

[http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html](http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html)

and about permissions

[ATTACH]119311[/ATTACH]

fstab needs to be researched, but its 1:30 here and time to say goodnight...

---

### Post by dozch on 2009-06-29
Have you tried changing the USB mode on the camera? You can choose between 'Mass Storage' and 'PTP'. I've got mine on PTP and that mounts ok.

In the camera menu, go to the spanner icon and scroll down to 'USB'.

---

### Post by jerrrys on 2009-06-29
good point dozch...

---

### Post by txtinman on 2009-06-29
This is the link that helped: [http://www.ubuntugeek.com/some-of-kn...rkarounds.html](http://www.ubuntugeek.com/some-of-kn...rkarounds.html)

```

2) Camera doesn’t mount when connected and switched on in Ubuntu 9.04(Jaunty)

Bug Details

Camera doesn’t mount when connected and switched on in Ubuntu 9.04(Jaunty)

Workaround

Quick fix:

Run the command from your terminal

    sudo killall gvfs-gphoto2-volume-monitor

then connect the camera.

Long-term fix:

Prevent the process from starting Using the following command

    sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
```

Thanks to jerrys for the help.

Mike White

---

### Post by jerrrys on 2009-06-29
glad to hear that...

---

