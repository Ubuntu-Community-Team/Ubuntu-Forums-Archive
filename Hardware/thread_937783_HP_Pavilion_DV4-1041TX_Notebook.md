---
title: "HP Pavilion DV4-1041TX Notebook"
date: 2008-10-04
forum: Hardware
---

### Post by hvlugger on 2008-10-04
I have tried to install Ubuntu Beta on this machine and get as far as a login screen, but my USB mouse is not recognised, the keyboard is not able to enter text. I can however CTRL-ALT-F1 and login, enter text and kill X and startx, but I am back in the same position. I am also gettng many error messages on boot. Any other DV4 installers out there?


I have had more attempts with Beta, but result still the same, no keyboard, no mouse. I also get this message very early in boot:

ACPI: GPE Storm detected, disable EC GPE


Update, installed Ubuntu 8.04 Hardy and:

Hardy installed, I now have graphics working, sound a big problem but thanks to a post by Jorge_C which was a big help, have it sorted now. Had to add the 'pci=noacpi' kernel option to /boot/grub/menu.lst and that fixed sound looping on boot. Could not get front jacks working and plugging in a headset didn't stop sound from speakers, nor did any sound come out of them to headset. Fixed that by editing line for 'snd-hda-intel' at bottom of /etc/modprobe.d/alsa-base - to this:

options snd-hda-intel model=laptop probe_mask=1

. . and rebooting. I got this from the helpful page at:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)


My webcam was easy to set up, loaded the module for this webcam which is marked HP webcam:

sudo modprobe -v uvcvideo

. . and this made /dev/video0 appear. Checked with ls /dev/video* then ran webcam with:

mplayer tv:// -tv device=/dev/video0:driver=v4l2:width=640:height=480 -vf mirror

. . note, your image may vary from this size, this is correct size for my webcam.

USB mouse working fine, sound now working well, video working, I have two USB TV devices controlled by a Bash script of my own making, both work very well using VLC. Realtek LAN device is working well. Intel wireless device NOT working, but I understand this is fixed in Intrepid. I feel there were some problems with Beta that may well vanish soon. I could boot with 8.04 live CD so this guided me to install.


Update:

Wireless still not working, and Realtek Gigabit flaky in performance, but altered settings in Vista that may have been altering the chip. I have had trouble with the screen coming up much too bright to use, as well as probably draining battery more quickly. Looked for a brightness alteration and set this up in /etc/rc.local to dim it down:

echo 70 > /proc/acpi/video/EVGA/LCD/brightness 

. . this works very well. Until Intrepid comes out I will stick with this.

---

