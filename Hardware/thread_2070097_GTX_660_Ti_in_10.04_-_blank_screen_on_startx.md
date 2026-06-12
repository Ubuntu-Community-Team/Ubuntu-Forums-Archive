---
title: "GTX 660 Ti in 10.04 - blank screen on startx"
date: 2012-10-12
forum: Hardware
---

### Post by Yokouchi on 2012-10-12
All

I'm using 10.04 64-bit (CAELinux 2011) on a fresh build having a NVIDIA GTX660Ti card.

The standard drivers don't recognize the 660Ti, so i added the Ubuntu-X-swat repo and used apt-get to add nvidia-current drivers (currently 304.xx).

Ubuntu boots, when it gets to X all I get is a blank, black screen.

The only error in logs concerns my mouse.

xorg.conf has no resolutions in it.

It's connected to my TV over HDMI. On non-NVIDIA drivers, I can run X no problem.

apt-get -f doesn't bring up any missing dependencies.

I'm at a loss what to do! Even some pointers as to where to start would be great.

I use three programs in the CAELinux distribution and I'm nearly willing to attempt some notoriously fickle installs in 12.04 and run that (my main PC is 12.04... and going strong!)

---

### Post by BicyclerBoy on 2012-10-12
Do a console login & run
sudo nvidia-xconfig

reboot.
Have a look in /var/log/Xorg.0.log

The nVidia driver install on older *buntus needed manually added blacklist entries, including nouveau nvidiafb vesafb.
The newer drive should have done this check /etc/modprobe.d/*.conf files..

---

### Post by Yokouchi on 2012-10-12
Blacklists are in place.

The log lists:

"(EE) Screen(s) found, but none have a usable configuration"

Hmm. Thoughts? Most of the links I've found suggest it's a lost cause

---

### Post by pqwoerituytrueiwoq on 2012-10-12
use nomodeset in your kernel boot line
also don't expect HDMI sound to work with that card on 10.04
HDMI audio on the 550 ti needs natteys kernel and going higher than maverick breaks virtualbox and i am sure the 660 ti will need something newer than that

```
~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset **video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap"
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
GRUB_GFXMODE=1366x768
GRUB_GFXPAYLOAD_LINUX=1366x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Yokouchi on 2012-10-12
Interesting. Made a few more 'distorted colours' on-screen before going blank/black

Wondering if it doesn't like the screen?

I get this in Xorg.0.log now:

(WW) Oct 12 11:23:06 NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid:
(WW) Oct 12 11:23:06 NVIDIA(GPU-0):     unrecognized EDID Header.

then 

(**) Oct 12 11:23:06 NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
(**) Oct 12 11:23:06 NVIDIA(0):     device DFP-1 (Using EDID frequencies has been enabled on
(**) Oct 12 11:23:06 NVIDIA(0):     all display devices.)

---

### Post by Yokouchi on 2012-10-12
More...

Putting in a custom modeline into xorg.conf didn't do anything.

Did a clean 12.04 install to check if it were a kernel or X-version dependency thing. Same problem.

Checking for proprietary drivers required reveals nothing - it's as if Ubuntu doesn't consider that it's an NVIDIA card.

Swapping HDMI ports on the TV does nothing.

Xorg.0.log certainly picks up the card.

Problem seems concentrated here:

[    21.329] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.329] (**) NVIDIA(0):     device DFP-1 (Using EDID frequencies has been enabled on
[    21.329] (**) NVIDIA(0):     all display devices.)
[    21.329] (==) NVIDIA(0): 
[    21.329] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    21.329] (==) NVIDIA(0):     will be used as the requested mode.
[    21.329] (==) NVIDIA(0): 
[    21.329] (II) NVIDIA(0): Validated MetaModes:
[    21.329] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[    21.329] (II) NVIDIA(0): Virtual screen size determined to be 800 x 600
[    21.368] (WW) NVIDIA(0): Unable to get display device DFP-1's EDID; cannot compute DPI
[    21.368] (WW) NVIDIA(0):     from DFP-1's EDID.
[    21.368] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default

and 

[    21.943] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid:
[    21.943] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.

and

[    21.943] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.943] (**) NVIDIA(0):     device DFP-1 (Using EDID frequencies has been enabled on
[    21.943] (**) NVIDIA(0):     all display devices.)
[    24.655] (WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-1
[    24.655] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.655] (**) NVIDIA(0):     device DFP-1 (Using EDID frequencies has been enabled on
[    24.655] (**) NVIDIA(0):     all display devices.)

---

### Post by Yokouchi on 2012-10-12
Going to try ignore the EDID data (I'm reading this may not be possible with the current NVIDIA drivers) or fake something useful. Will report back.

---

### Post by Yokouchi on 2012-10-12
Fixed! [http://analogbit.com/fix_nvidia_edid](http://analogbit.com/fix_nvidia_edid) helped.

---

