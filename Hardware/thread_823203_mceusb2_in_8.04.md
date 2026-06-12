---
title: "mceusb2 in 8.04"
date: 2008-06-09
forum: Hardware
---

### Post by pavon on 2008-06-09
Hi,
I have been trying to setup my MCE Remote in 8.04, using [this HOWTO]("https://help.ubuntu.com/community/InstallLirc/Hardy"). I installed lirc (with apt-get), however when it tried to start lircd for the first time it failed. I checked messages and saw one error. The relevant portion of /var/log/messages is below.

> 
Jun  8 21:56:50 linux kernel: [36066.132535] lirc_dev: IR Remote Control driver registered, major 61
**Jun  8 21:56:50 linux kernel: [36066.139185] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.**
Jun  8 21:56:50 linux kernel: [36066.139764]
Jun  8 21:56:50 linux kernel: [36066.139767] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
Jun  8 21:56:50 linux kernel: [36066.139769] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
Jun  8 21:56:50 linux kernel: [36066.253551] usb 5-1: reset full speed USB device using uhci_hcd and address 2
Jun  8 21:56:50 linux kernel: [36066.399853] lirc_dev: lirc_register_plugin: sample_rate: 0
Jun  8 21:56:50 linux kernel: [36066.403842] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb5:2
Jun  8 21:56:50 linux kernel: [36066.403868] usbcore: registered new interface driver lirc_mceusb2


So I manually restarted it (/etc/init.d/lircd restart), and that didn't have any errors. After that I manually ran the configuration tool, since it didn't happen during installation (dpkg-reconfigure lirc), and selected the Microsoft Media Center remote (newer - Philips). The config file it generated looks good:

> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""


After that I restarted lirc again. lsusb showed that my device was found:

> 
[Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
**Bus 005 Device 002: ID 0471:0815 Philips**
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 004: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000


And lsmod showed that the correct modules were loaded: 

lsmod | grep lirc:
> 
lirc_mceusb2           14852  0
lirc_dev               15860  1 lirc_mceusb2
usbcore               146028  5 lirc_mceusb2,usbhid,ehci_hcd,uhci_hcd


However when I ran irw I wasn't getting anything - the light on the IR receiver flashes, but the data is not getting through.

I found [this posting]("http://www.gossamer-threads.com/lists/mythtv/users/323611") on the mythtv mailing list that looks like someone is having the same problem on mythbuntu 8.04. I checked and I do have the generic kernel, not i386.

Has anyone got this remote working in Hardy? If so, any ideas on what I'm doing wrong? If not, I'll file a bug report.

---

### Post by jmw86069 on 2008-06-22
I found another similar post myself ([here]("http://ubuntuforums.org/showthread.php?t=388728&page=4"))
but it still didn't work. However, I'm more convinced my problem is relatively unique, and here is why:

1) The remote worked GREAT the first time I plugged it in. I ran mythbuntu-lirc-generator and set it up with the new Philips driver. I ran mythTV and it found it, and it ran fine. However, at the time my USB TV tuner didn't work...
2) I plugged in the TV tuner, and BOOM the remote stopped working. Unplugging it didn't help either. I tried various things, and confirmed these two don't live nice together. They were plugged in through a powered USB 2.0 4-port hub... plugged in, so power should be fine. When I press remote buttons, the USB light didn't blink at all.
3) Redid the whole setup so the USB TV tuner and hard drive are on the USB hub, while the USB IR receiver is on its own USB port. Reinstalled drivers (see above post, now I have LIRC version 1.45) and now the TV tuner works, and the little usb IR receiver lights up when I press remote keys. But same symptom, no luck when I run irw.

I have NOT tried it again with only the IR receiver and not the TV tuner plugged in. Will do so shortly. (Kids want me to play Wii first. Wii!!!!)

My questions:
* Do you know if EHCI_HCD is required (USB 2.0) or is UHCI_HCD okay (USB 1.x)? When I switched things around, the TV tuner is on USB 2.0, but now the remote receiver is on USB 1.x. I figured I need faster USB for the TV tuner.
* Do people with problems have multiple USB devices that could be conflicting. Your lsmod doesn't indicate it, but just curious.
* I saw info that LIRC doesn't do well with two remote devices... my TV tuner has an IR receiver, but I don't use it. I also don't see it in dmesg though, so maybe it's being ignored?
* Why is there nothing in /proc/bus/usb?

Thanks everyone for the help!

---

### Post by jmw86069 on 2008-06-22
Whoohoo!!! Success!! Now, to figure out what I did to fix it... :-)

Here are the steps, highlighting where I *think* there were benefits.
1) I unplugged the USB MCE receiver.
2) I typed 'sudo rmmod lirc_mceusb2' to un-load the remote module.
3) I created a file '/etc/modprobe.conf' and added two lines.
```
alias char-major-61 lirc_mceusb2
options lirc_mceusb2 debug=1

```
The first line is supposed to point the character 61 line found in 'dmesg' to the appropriate remote module. The second line causes all the signals received from the remote to be sent to 'dmesg' for review. If it sends nothing, you've got issues I guess.
4) I had no files in /proc/bus/usb at all, so I created them with this command, then made sure the permissions on the lirc sockets were "permissive":
```
sudo mount -t usbfs usbfs /proc/bus/usb
chmod 666 /dev/lircd
chmod 666 /dev/lirc0
```
5) I plugged the MCE into the USB hub where it previously didn't work. It didn't work again, and there was no chatter at all in 'dmesg' nor 'lsmod' nor 'lsusb' etc. Nothin'. (This step was a dead-end obviously.) If you don't have a USB hub issue, just stand up, walk three times in a circle, then sit back down. Essentially the same thing. ;-)
6) I plugged in the MCE back to the USB port where it was originally.
7) I typed 'sudo modprobe lirc_mceusb2' to re-load the remote driver.
8) I ran 'lsmod' and 'lsusb' and 'dmesg' and found the same messages I saw before (e.g. no vendor name in 'lsusb', but the vendor ID and device ID were correct, and the same messages in 'dmesg' etc.)
This time, though, dmesg showed what looked like remote control signals (from the debug=1 statement above) ... so I pressed a few buttons and checked again. MAGIC.
9) I ran 'irw' and this time it worked. GOLD.

No idea, but removing the module, adding the lines to modprobe.conf to reinforce lirc_mceusb2, running the steps to mount USB, and permissiate /dev/lirc* seem helpful. Let me know if these steps help anybody else?

---

### Post by tivolieselet on 2008-07-17
hmm.. tried this one.. but it dont work.. 

I have started a new thread [http://ubuntuforums.org/showthread.php?t=861591&highlight=mce+keyboard](http://ubuntuforums.org/showthread.php?t=861591&highlight=mce+keyboard) :confused:

---

