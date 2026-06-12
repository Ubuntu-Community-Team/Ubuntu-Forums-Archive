---
title: "Touchpad on Laptop won't work."
date: 2014-07-24
forum: Hardware
---

### Post by jballer0602 on 2014-07-24
My touchpad on my Asus K55N-DB81 will not work after a fresh install of Ubuntu 14.04. It was working during the installation, but after the reboot it wasn't working. When I plug in an external mouse it works perfectly fine.

---

### Post by WinEunuchs2Unix on 2014-07-24
On my Toshiba Laptop running gedit /var/log/Xorg.0.log reveals the following:

```

[    14.187] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    14.187] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    14.187] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    14.187] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    14.187] (II) LoadModule: "synaptics"
[    14.188] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    14.201] (II) Module synaptics: vendor="X.Org Foundation"

```

Does yours show the same or does it have error messages?

NOTE: run the terminal with <CTRL>+<ALT>+T in order to run the gedit command above.  To close the terminal type exit at the prompt.

Ironically on my Laptop the Touchpad works perfectly and the wireless mouse is less than perfect.

---

### Post by jballer0602 on 2014-07-24
I just did that, and there isn't even a driver or anything that says "touchpad". I don't even think the driver is installed! :( How could this happen on a fresh boot??

---

### Post by jballer0602 on 2014-07-24
Ive even ran the USB boot stick to freshly install it multiple times before, and the touchpad worked the first few times of the installation, now it doesn't. Anybody know how I can get the driver or something.

---

### Post by jeremy31 on 2014-07-25
See if ```
sudo modprobe psmouse
```
gets the touchpad working

---

### Post by jballer0602 on 2014-07-25
No, it still didn't work :\

---

### Post by jballer0602 on 2014-07-25
I installed the synaptics package, but there still is no "synaptics touchpad" when doing the " xinput list " command

---

### Post by jeremy31 on 2014-07-25
Plug in a mouse and then enter ```
dmesg | tail
``` and ```
cat /var/log/Xorg.0.log | tail
```

There should be a clue somewhere

---

### Post by jballer0602 on 2014-07-26
Hey, Thanks alot for the Effort. I just decided to use an External USB mouse. Touchpad just doesn't seem to work. But thanks anyway!

---

### Post by jeremy31 on 2014-07-26
Don't be surprised if an update brings the touchpad back

---

### Post by jballer0602 on 2014-07-26
Could it have something to do with the graphics card?

---

### Post by WinEunuchs2Unix on 2014-07-26
Have you looked at the output from dmesg for error messages about the graphics card, mouse or anything else?  You can also gedit the files /var/log/kernel.log and /var/log/Xorg.log to look for error messages.

You can post them here using the "Go Advanced" option and selecting the pound sign, aka "hash tag" symbol that looks like "#" and paste the screen output between the code tags.  I'm not great in deciphering error messages but I can probably help you spot them.

---

### Post by kurt18947 on 2014-07-26
I'm using Ubuntu-Gnome but can you find something like a "mouse and touchpad" in a hardware or settings app?  I'm wondering if for some reason the touchpad is disabled and not showing up.

---

### Post by WinEunuchs2Unix on 2014-07-26
The Gnome desktop is a different animal than the Unity desktop.  For example here are hundreds of issues on Gnome Mice: [http://gnome-look.org/?xcontentmode=36](http://gnome-look.org/?xcontentmode=36)

---

### Post by jballer0602 on 2014-07-26
Well, I've installed Kubuntu now, and the problem still persists. Should I follow through or is it different?

It just seems like even though the Synaptics is installed it won't enable or something.

Take a look at my Xinput List (Kubuntu 14.04) 

Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical gaming mouse                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical gaming mouse                  id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; USB Optical gaming mouse                  id=10   [slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                        id=12   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=13   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]

Im using an external gaming mouse right now as a derivative. But as you can see, No Synaptics driver?

---

### Post by jeremy31 on 2014-07-26
> **jballer0602 said:**
> Well, I've installed Kubuntu now, and the problem still persists. Should I follow through or is it different?

It just seems like even though the Synaptics is installed it won't enable or something.

Take a look at my Xinput List (Kubuntu 14.04) 

Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical gaming mouse                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical gaming mouse                  id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; USB Optical gaming mouse                  id=10   [slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                        id=12   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=13   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]

Im using an external gaming mouse right now as a derivative. But as you can see, No Synaptics driver?

You could install pastebinit and upload a couple files that might help
```
sudo apt-get install pastebinit
```
```
pastebinit /var/log/dmesg
```
```
pastebinit /var/log/Xorg.0.log
```
 and just copy/paste the URL's from the last two commands in your next post.  I had a similar event happen installing a different linux on a Toshiba Satellite so I used a mouse for a while and before I could figure out what went wrong, the touchpad was working again

---

### Post by jballer0602 on 2014-07-26
[http://paste.ubuntu.com/7869399/](http://paste.ubuntu.com/7869399/)

---

### Post by jballer0602 on 2014-07-27
Bump?

---

### Post by jeremy31 on 2014-07-27
> **jballer0602 said:**
> Bump?

Nothing in Xorg log, how about the /var/log/dmesg and /var/log/kern.log

---

### Post by WinEunuchs2Unix on 2014-07-27
> **jeremy31 said:**
> Nothing in Xorg log, how about the /var/log/dmesg and /var/log/kern.log

Agreed.

EDIT: Contents of /var/log/udev might also shine some light on the problem

---

### Post by jballer0602 on 2014-07-27
I get Permission denied when trying to access any of those commands even when im root

jerome@jerome-K55N:~$ /var/log/dmesg
bash: /var/log/dmesg: Permission denied
jerome@jerome-K55N:~$ sudo /var/log/dmesg
[sudo] password for jerome: 
sudo: /var/log/dmesg: command not found
jerome@jerome-K55N:~$ /var/log/kern.log
bash: /var/log/kern.log: Permission denied
jerome@jerome-K55N:~$ sudo su
root@jerome-K55N:/home/jerome# /var/log/kern.log
bash: /var/log/kern.log: Permission denied
root@jerome-K55N:/home/jerome# /var/log/udev 
bash: /var/log/udev: Permission denied
root@jerome-K55N:/home/jerome# /var/log/dmesg
bash: /var/log/dmesg: Permission denied
root@jerome-K55N:/home/jerome#

---

### Post by WinEunuchs2Unix on 2014-07-27
You are typing the file name, ie "/var/log/dmesg" as if it were a command.  The terminal format is <command> <file_name>.  The <command> can be "sudo gedit" or "cat" or "pastebinit" as you used last time.  The <file_name> will be "/var/log/dmesg" or "/var/log/udev", etc.

To let us see your dmesg 
```
pastebinit /var/log/dmesg
```

then attach the output to a message like you did with the Xorg.0.log file output previously.

Repeat the process for "pastebinit /var/log/kern.log" and "pastebinit /var/log/udev".

Remember earlier I said my mouse was "less than perfect" well today I ran boot-repair because Windows wouldn't load and now the mouse in Ubuntu is great.  This affirms Jermey's post of how and update might make the touchpad work again.
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by jballer0602 on 2014-07-27
Ohh, Ok thanks for telling me that : )

Well here are the links

/var/log/dmesg
[http://paste.ubuntu.com/7880576/](http://paste.ubuntu.com/7880576/)

/var/log/kern.log
[http://paste.ubuntu.com/7880588/](http://paste.ubuntu.com/7880588/)

/var/log/udev
[http://paste.ubuntu.com/7880590/](http://paste.ubuntu.com/7880590/)

---

### Post by WinEunuchs2Unix on 2014-07-27
Your ASUS and i8042 chipset have a lot of dissussion at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1323346:](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1323346:)

================
[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][Hans de Goede (j-w-r-degoede)]("https://launchpad.net/~j-w-r-degoede") wrote on 2014-06-23:[/TD]
[TD="class: bug-comment-index"][#19]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1323346/comments/19")[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]Hi,
Fixing this is non trivial, supporting these new touchpads likely needs a signicant amount of work (for details see[https://bugzilla.redhat.com/show_bug.cgi?id=1110011](https://bugzilla.redhat.com/show_bug.cgi?id=1110011) ).
In the mean time, I can provide a workaround which should make the touchpad work in ps/2 mouse emulation mode (so no 2 finger scrolling, etc.), and stop it from interfering with an external mouse.
Sounds good? Try booting with "psmouse.proto=bare" on the kernel cmdline.
See: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) for how to add a parameter to the kernel commandline.
Regards,
Hans
[/FONT]
[/FONT][/COLOR]
-----------------------------

I looked at the redhat bug report discussion referenced in the above post and it is quite extensive back and force between the user and a linux programmer.

---

### Post by jballer0602 on 2014-07-28
Hmmmm, It used to work perfect when first installing Ubuntu 14.04. I guess I should just use the emulator for now?
when checking the touchpad in input devices where you can find the mouse sensitivity. It says "synaptics driver is not installed (or is not used)"

---

### Post by jeremy31 on 2014-07-28
It did work, post terminal results from ```
cat /etc/default/grub
```

---

### Post by jballer0602 on 2014-07-28
Ok here it is

root@jerome-K55N:/home/jerome# cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
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

If you didn't know already, I'm running kubuntu, so I'm not sure if much is different between Gnome and KDE

---

### Post by jeremy31 on 2014-07-28
> **jballer0602 said:**
> Ok here it is

root@jerome-K55N:/home/jerome# cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
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

If you didn't know already, I'm running kubuntu, so I'm not sure if much is different between Gnome and KDE

If you get a grub menu at boot select advanced options for Ubuntu or previous versions and select the one with the lowest numbered kernel which is likely to be 3.13.0-24 and press enter and see if the touchpad works after as this could always be a regression with the later kernel

---

### Post by jballer0602 on 2014-07-29
Hey, I've just decided to use the external mouse from now on, I've gotten used to it anyway. Thanks A LOT for the support, you guys are great :). If an update brings it back, well it will be even better!

---

### Post by jeremy31 on 2014-07-29
> **jballer0602 said:**
> Hey, I've just decided to use the external mouse from now on, I've gotten used to it anyway. Thanks A LOT for the support, you guys are great :). If an update brings it back, well it will be even better!

File a bug report to get the ball moving

---

### Post by WinEunuchs2Unix on 2014-07-29
A little confusion above the OP meant the touchpad worked when installing Ubuntu BEFORE grub was created to boot from hdd.  To the best of my understanding there never was any previous version to revert to other than the live boot CD.

I think there are already a couple of bug reports filed already and a work around is already posted until the real patch comes out.  As posted above the work around was Kernel command line [COLOR=#333333][FONT=monospace]"psmouse.proto=bare"[/FONT][/COLOR]

---

