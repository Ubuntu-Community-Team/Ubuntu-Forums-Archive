---
title: "HDAPS on 2.6.22"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by likpok on 2007-07-31
I'm having trouble getting the disk parking with HDAPS working under 2.6.22.

I can get the required modules installed (i.e. tp_smapi and hdaps ), and both working (to a degree, hdaps-gl works, as does the power management in tp_smapi).

Unfortunatly, the one part that doesn't work is also the most useful, the actual parking mechanism. It fails, because the /sys/block/sda/queue/protect file is missing. There is supposedly a kernel patch for it, but when I try to apply it, compile, install, and boot, the kernel fails to recognize my disk. I get dropped to an initramfs shell.

This fails when both when i specify the disk by UUID *and* when i specify it by device node (/dev/sda?).

The patch i'm using is for a previous kernel version (2.6.20 maybe?) but *supposedly* it should work with later versions. The patching program exits with no errors, and the kernel is hand-configured.

---

### Post by airbornespent on 2007-08-10
Follow [theses instructions]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Disk_Protection") and insert your kernel version where appropriate. I followed them for 2.6.20 on my t42p. Be sure to also reinstall the tp_smapi modules.

When I (as root, will not work with sudo): ```
echo 1 > /sys/block/sda/queue/protect
``` the gnome-hdaps-applet shows my disk as paused and I tested this while copying files (which stopped copying as long as I kept issuing the command over and over), so those instructions work.
I'm only having problems with the hdapsd daemon not parking the disk for me in response to shock, so test whether everything works with the echo command above.

EDIT: I got the hdapsd working! There is a note on the thinkwiki page I linked to above that mentions using gcc-3.4 to compile hdapsd, I ignored it at first but then I checked synaptic. You must install gcc-3.4 then when compiling hdapsd use:```
gcc-3.4 -o hdapsd hdapsd-*.c
sudo cp hdapsd /usr/local/sbin/
```

At this point you can run the command "hdapsd" to see the options, ex. "hdapsd -d sda -s 15" 

Now I simply need to figure out where is te best place to start the daemon on startup. rc.local is one place, but I'd personally like it to start ASAP after boot, which means as close to when the tp_smapi modules are loaded as possible.

---

### Post by likpok on 2007-08-17
My main problem is that the patched kernel would fail to boot, while an unpatched kernel booted fine. However, the point is moot now, because I can't get a custom kernel to boot at all under 64 bit.

---

