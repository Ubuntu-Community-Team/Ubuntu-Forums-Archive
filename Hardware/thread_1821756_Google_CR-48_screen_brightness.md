---
title: "Google CR-48 screen brightness"
date: 2011-08-09
forum: Hardware
---

### Post by kerc on 2011-08-09
Hey guys, this is a pretty awesome forum.
 
I recently installed Kubuntu on my CR-48, and everything works perfectly, except screen brightness. It seems to be stuck around 65% or so. I'd like to either 1) set the brightness permanently to 100%, or 2) be able to set up keys for controlling brightness.
 
I noticed that the slider in the power management panel is always all the way down to the left. I set it (with no changes on screen), close the panel, and when I reopen it, it's back to the left.
 
Xbacklight doesn't work (something about no outputs having backlight properties, and setpci does nothing.
 
I'm at a loss...I'm a recent convert to Ubuntu and I'm in love with it so far! I wanna keep loving it. :P
 
Thanks!

---

### Post by Toz on 2011-08-09
Don't know if you've noticed, but there is a whole thread here devoted to the CR-48 (see: [http://ubuntuforums.org/showthread.php?t=1651290]("http://ubuntuforums.org/showthread.php?t=1651290")) and specifically post #31 ([http://ubuntuforums.org/showpost.php?p=10282278&postcount=31]("http://ubuntuforums.org/showpost.php?p=10282278&postcount=31")) that talks about a python script to change brightness levels. 

In addition, there is a thread at the arch linux forums that talks about brightness on the CR-48. See post #28 at: [https://bbs.archlinux.org/viewtopic.php?pid=873122]("https://bbs.archlinux.org/viewtopic.php?pid=873122").

Let us know how you make out.

---

### Post by kerc on 2011-08-09
I'll check those out. Thanks! I'll keep you posted on my results.

---

### Post by kerry_s on 2011-08-09
install "keytouch" & use this:

```

<keyboard>
  <file-info>
    <syntax-version>1.2</syntax-version>
    <last-change format="%d-%m-%Y">22-03-2011</last-change>
    <author></author>
  </file-info>
  <keyboard-info>
    <keyboard-name>
      <manufacturer>Google</manufacturer>
      <model>Cr-48</model>
    </keyboard-name>
  </keyboard-info>
  <key-list>
    <key>
      <name>Back-F1</name>
      <scancode>59</scancode>
      <keycode>BACK</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>Forward-F2</name>
      <scancode>60</scancode>
      <keycode>FORWARD</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>Refresh-F3</name>
      <scancode>61</scancode>
      <keycode>REFRESH</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>BrightDown-F6</name>
      <scancode>64</scancode>
      <keycode>BRIGHTNESSDOWN</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>BrightUp-F7</name>
      <scancode>65</scancode>
      <keycode>BRIGHTNESSUP</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>VolumeMute-F8</name>
      <scancode>66</scancode>
      <keycode>MUTE</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>VolumeDown-F9</name>
      <scancode>67</scancode>
      <keycode>VOLUMEDOWN</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>VolumeUp-F10</name>
      <scancode>68</scancode>
      <keycode>VOLUMEUP</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>Search Key</name>
      <scancode>219</scancode>
      <keycode>SEARCH</keycode>
      <default-action action-type="plugin">
        <plugin-name>WWW Browser</plugin-name>
        <plugin-function>Search</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Full_Screen-F4</name>
      <scancode>62</scancode>
      <keycode>STOP</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>NextWindow-F5</name>
      <scancode>63</scancode>
      <keycode>AGAIN</keycode>
      <default-action></default-action>
    </key>
  </key-list>
</keyboard>


```

---

### Post by kerc on 2011-08-09
Where would I place that XML data? Sorry, I'm a total n00b. :confused: ):P
 
> **kerry_s said:**
> install "keytouch" & use this:
 
```

<keyboard>
  <file-info>
    <syntax-version>1.2</syntax-version>
    <last-change format="%d-%m-%Y">22-03-2011</last-change>
    <author></author>
  </file-info>
  <keyboard-info>
    <keyboard-name>
      <manufacturer>Google</manufacturer>
      <model>Cr-48</model>
    </keyboard-name>
  </keyboard-info>
  <key-list>
    <key>
      <name>Back-F1</name>
      <scancode>59</scancode>
      <keycode>BACK</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>Forward-F2</name>
      <scancode>60</scancode>
      <keycode>FORWARD</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>Refresh-F3</name>
      <scancode>61</scancode>
      <keycode>REFRESH</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>BrightDown-F6</name>
      <scancode>64</scancode>
      <keycode>BRIGHTNESSDOWN</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>BrightUp-F7</name>
      <scancode>65</scancode>
      <keycode>BRIGHTNESSUP</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>VolumeMute-F8</name>
      <scancode>66</scancode>
      <keycode>MUTE</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>VolumeDown-F9</name>
      <scancode>67</scancode>
      <keycode>VOLUMEDOWN</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>VolumeUp-F10</name>
      <scancode>68</scancode>
      <keycode>VOLUMEUP</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>Search Key</name>
      <scancode>219</scancode>
      <keycode>SEARCH</keycode>
      <default-action action-type="plugin">
        <plugin-name>WWW Browser</plugin-name>
        <plugin-function>Search</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Full_Screen-F4</name>
      <scancode>62</scancode>
      <keycode>STOP</keycode>
      <default-action></default-action>
    </key>
    <key>
      <name>NextWindow-F5</name>
      <scancode>63</scancode>
      <keycode>AGAIN</keycode>
      <default-action></default-action>
    </key>
  </key-list>
</keyboard>
 

```

---

### Post by kerry_s on 2011-08-09
Create a file & paste that in an save. 
Open keytouch & look for add or install, then point it to the file. 
Sorry, it's been a long time since I saw my cr-48. Can't remember enough to be specific.

---

### Post by kerc on 2011-08-09
I'll try keytouch when I get home tonight. The Python script doesn't work because it's calling xbacklight, which isn't working.
 
More geeking out tonight. My wife will kill me. :)
 
> **kerry_s said:**
> Create a file & paste that in an save. 
Open keytouch & look for add or install, then point it to the file. 
Sorry, it's been a long time since I saw my cr-48. Can't remember enough to be specific.

---

### Post by kerc on 2011-08-09
Update: Nothing works. I has a sad.

---

### Post by Toz on 2011-08-09
Does the following return anything?
```
cat /proc/acpi/video/OVGA/DD02/brightness
```

If not, how about:
```
ls -l /proc/acpi/video/
```

---

### Post by kerc on 2011-08-09
> **Toz said:**
> Does the following return anything?
```
cat /proc/acpi/video/OVGA/DD02/brightness
```

If not, how about:
```
ls -l /proc/acpi/video/
```

```

user@cr-48-ubuntu:~$ cat /proc/acpi/video/OVGA/DD02/brightness
cat: /proc/acpi/video/OVGA/DD02/brightness: No such file or directory
user@cr-48-ubuntu:~$ ls -l /proc/acpi/video
ls: cannot access /proc/acpi/video: No such file or directory
user@cr-48-ubuntu:~$ 

```

By the way, I switched for now to Gnome...

---

### Post by Toz on 2011-08-09
Are you booting with any special kernel parameters?
```
cat /etc/default/grub
```

---

### Post by kerc on 2011-08-10
> **Toz said:**
> Are you booting with any special kernel parameters?
```
cat /etc/default/grub
```

```


user@cr-48-ubuntu:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Toz on 2011-08-10
You seem to be using the **acpi_osi=** paramater. Was it to solve a specific problem? I think its affecting your ability to use xbacklight and the other methods of dimming/brightening the screen.

---

### Post by kerc on 2011-08-10
> **Toz said:**
> You seem to be using the **acpi_osi=** paramater. Was it to solve a specific problem? I think its affecting your ability to use xbacklight and the other methods of dimming/brightening the screen.
 
It was to solve this particular problem. Xbacklight didn't work before either...

---

### Post by Toz on 2011-08-10
Have you tried the other usual suspects:
[LIST=0]
[*]acpi_osi=Linux
[*]acpi_backlight=vendor
[*]acpi_osi=\"Linux\"
[*]acpi_osi=Linux acpi_backlight=vendor
[/LIST]

Also, can you try booting without that parameter and then seeing if **/proc/acpi/video/OVGA/DD02/brightness** exists. Reference link: [https://bbs.archlinux.org/viewtopic.php?pid=869028#p869028]("https://bbs.archlinux.org/viewtopic.php?pid=869028#p869028")

---

### Post by bem202 on 2011-12-29
The "Keytouch" solution worked for me. Thanks :)

---

