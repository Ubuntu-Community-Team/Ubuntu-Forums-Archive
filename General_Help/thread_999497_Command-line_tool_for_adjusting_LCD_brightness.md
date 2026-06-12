---
title: "Command-line tool for adjusting LCD brightness"
date: 2008-12-01
forum: General Help
---

### Post by wirawan0 on 2008-12-01
It came to my attention that the new (Intrepid Ibex) gnome-power-manager GUI (executable = gnome-power-preferences) has a cool facility to set display brightness; from the source code it seems that this can be done in two ways: via HALD or xrandr.

I wonder if somebody has written a command line tool to do the same thing (i.e. to increase/decrease display brightness). I am thinking of this tool as a way to work around Dell's woe with Intrepid or Hardy when we adjust the brightness via Fn+Up/Fn+Down.

Wirawan

---

### Post by loomsen on 2008-12-01
You need to have i2c, acpi or any support by your video device driver enabled in your kernel configuration.

For me, I have it in:

> 
[color=blue]docter[/proc][/color] cd acpi/video/VGA/LCD/
[color=blue]docter[/proc/acpi/video/VGA/LCD][/color] ls
brightness  EDID  info  state
[color=blue]docter[/proc/acpi/video/VGA/LCD][/color] cat brightness 
levels:  70 40 0 10 20 30 40 50 60 70
current: 70
[color=blue]docter[/proc/acpi/video/VGA/LCD][/color]


The files in /proc, if you didn't get to know yet, are a virtual layer providing a platform for you to interact with your hardware.

That's what the "Kernel alive" message is about (you might have noticed). Your kernel actually is alive, you can interact with your hardware using the /proc interface (other than in Win for instance where any hardware is enabled with predefined options, and where most hardware has to be restarted to change options)

So in my case, this cmd for instance would darken my screen:
> 
[color=blue]docter[/proc/acpi/video/VGA/LCD][/color] sudo -i
[color=blue]root@dhcppc0:~#[/color] cd /proc/acpi/video/VGA/LCD/
[color=blue]root@dhcppc0:/proc/acpi/video/VGA/LCD#[/color] cat brightness 
levels:  70 40 0 10 20 30 40 50 60 70
current: 70
[color=blue]root@dhcppc0:/proc/acpi/video/VGA/LCD#[/color] echo 50 > brightness
[color=blue]root@dhcppc0:/proc/acpi/video/VGA/LCD#[/color] cat brightness 
levels:  70 40 0 10 20 30 40 50 60 70
current: 50
[color=blue]root@dhcppc0:/proc/acpi/video/VGA/LCD#[/color] 


*edit*
As the "files" listed in /proc are pretty PC-specific, you might have to search for the equal file on your system. Try a combination of acpi/ic2 and brightness or so. Most likely you'll find something appropriate under /proc

---

### Post by wirawan0 on 2008-12-29
Too bad my /proc/acpi tree doesn't have VGA subdir in it. It only has video/, but here's the content: (hardware: Dell Lattitude D600)

```

/proc/acpi $ tree video/
video/
`-- VID
    |-- CRT
    |   |-- EDID
    |   |-- brightness
    |   |-- info
    |   `-- state
    |-- CRT2
    |   |-- EDID
    |   |-- brightness
    |   |-- info
    |   `-- state
    |-- DOS
    |-- DVI
    |   |-- EDID
    |   |-- brightness
    |   |-- info
    |   `-- state
    |-- LCD
    |   |-- EDID
    |   |-- brightness
    |   |-- info
    |   `-- state
    |-- POST
    |-- POST_info
    |-- ROM
    |-- TV
    |   |-- EDID
    |   |-- brightness
    |   |-- info
    |   `-- state
    `-- info

```
And alas, the brightness is not supported. Never mind though. We could probably use dbus-send to do it, by talking to HAL. This is just an idea; maybe someone else would pick it up.

Wirawan

---

### Post by imwithid on 2009-06-26
I can set the brightness level through the driver in Windows but nothing in Ubuntu (including the Brightness Applet) works. I am using a desktop and not a laptop which is why those directories do not exist in my filetree.

When the computer is inactive for several minutes, the screen dims gradually. How can it be locked into one of those gradient dim levels?

---

### Post by gwydionwaters on 2009-09-21
system > preferences > power management
set the display brightness there, have you tried this way before? it doesn't seem to work for me but i am using a ppc so a lot of things are a pain.

---

### Post by imwithid on 2009-10-14
The power management that is displayed on my desktop is quite rudimentary. I would put it oafishly as such:

Ubuntu Power Management = Sucks

I could make do without all the special effects that have been thrown in over the last few releases.

Searching through the folders in the file system is rather brutal as well if you search for VGA, power or other similar terms gives you hundreds of results, 95% being shortcuts.

---

### Post by Cruxic on 2009-10-31
If you have a laptop with Intel graphics and you're using Karmic (9.10) the [xbacklight]("http://cgit.freedesktop.org/xorg/app/xbacklight/") command should work (install the "xbacklight" package with Synaptic).  [Apparently]("https://wiki.ubuntu.com/Halsectomy") this works with the open-source nvidia drivers too.

---

