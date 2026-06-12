---
title: "Missing startup and shutdown screens"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Another Monkey on 2009-04-24
A strange issue.  After upgrading from 8.10 to 9.04, I no longer see any splash screens with the progress bar. during stratup or shutdown.

I actually thought the PC had crashed the first time I went to shut down.

Anyone any ideas how to resolve this?  I can't figure out what is missing/wrong.

I've had a few issues during the upgrade (8.10 Intrepid was stable and working), not sure if this is related.

---

### Post by trpnblies7 on 2009-04-24
I'm having the same problem. I'd love to know what's causing this.

---

### Post by drs305 on 2009-04-24
Do you still have the "splash" option on the kernel line of /boot/grub/menu.lst ?
Something like this:
> kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5540da112-541e-4f0e-b1e7-d8db9962d7c5 ro **splash** quiet 

You can add it if it isn't there by opening menu.lst for editing:
```
gksudo gedit /boot/grub/menu.lst
```
Take a look at the bottom entries for the sections starting with "title". Make sure the "splash" option is there.

Another way to check would be to interrupt grub during boot by hitting the ESC key as it counts down. Move the cursor to the desired option, hit E, then move to the kernel line and hit E again to see if "splash" is on the line. If it isn't, you can type it in and ESC and B to boot. If you see the progress bar you will still have to edit menu.lst to make the change permanent.

If "quiet" is listed, running these commands may reset it:
```
sudo apt-get install --reinstall usplash
sudo update-initramfs -k all -u
 
```

---

### Post by Partyboi2 on 2009-04-24
deleted

---

### Post by Another Monkey on 2009-04-24
I have "splash", but it is in the order "quiet splash" rather than "splash quiet".  I tried swapping them to see if that made any different, and apart from seem a "Starting up" and "Loading" message, there was no splash.

Could it be a missing file?  How do I find out what splash it is trying to load?
Is there a log file I should look at?  (Linux newb here, I'd need to know the location as well).

---

### Post by drs305 on 2009-04-24
> **Another Monkey said:**
> Could it be a missing file?  How do I find out what splash it is trying to load?  (Linux newb here, I'd need to know the location as well).

This command reloads it. If the file(s) exist it should give you a name to select:
```
sudo update-alternatives --config usplash-artwork.so
```

That file is in /usr/lib/usplash

---

### Post by Another Monkey on 2009-04-24
Thanks dsr305, I tried that.  No joy.

The output was:
```
There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/usplash/usplash-theme-ubuntu.so
          2    /usr/lib/usplash/usplash-theme-xubuntu.so
```

I got to a VT and tried this "sudo usplash -c -v >/tmp/usplash.log 2>&1", the result of which was an empty log file.  For fun I tried it again from a normal terminal and got:
```
usplash: can't get console font: Invalid argument
```

I am not sure that that is relevant though.

What's weird is I have Jaunty RC in a VirtualBox image on another machine (also upgraded from 8.10) and it works fine.

Are the logs or files I should try and compare between the two?

---

### Post by Another Monkey on 2009-04-24
could it be intel graphics related?  (Same as the lack of compiz support in Jaunty?)

When I added "vga=795" to the Grub menu.lst, i got a complaint and it only offered a very few choice (80cols X 40rows, 640 X 480; all crude).

I am just thinking that if usplash can't get the correct resolution, it doesn't display; but then I would have expected to see an error in the logs.

I have a Intel Corporation 82865G Integrated Graphics Controller (rev 02), and there appear to be some bugs with it in Jaunty.

---

### Post by Another Monkey on 2009-04-24
Well, that fixed it.  Seems with was the video buffer (is that the same as the frame buffer?)

Anyhoo; I rebooted, went into the BIOS and had a good root about for any video options.  The only thing I could find was about the buffer size.  1mb or 8mb.  So I changed the setting from 1mb **to** 8mb and voilá; I have a splash screens.

No idea *why* Jaunty insists on having a much bigger buffer - anyone any ideas?  Is this expected or is it a bug?  Intrepid was perfectly happy with 1mb.

That's one problem down, now to work out why Samba is goosed.  Hmmm....

---

### Post by trpnblies7 on 2009-04-25
I fixed mine. Turned out the problem was that I still had usplash-smooth installed, but that isn't currently supported in Jaunty, so it was causing some kind of conflict. I got rid of that, reinstalled usplash and usplash-ubuntu-theme for the heck of it, and everything is back to normal.

---

