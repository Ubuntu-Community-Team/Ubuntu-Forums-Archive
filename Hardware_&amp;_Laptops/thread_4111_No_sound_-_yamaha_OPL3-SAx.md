---
title: "No sound - yamaha OPL3-SAx"
date: 2004-11-12
forum: Hardware &amp; Laptops
---

### Post by bikeboy on 2004-11-12
I'm a complete noob and Warty (might be a preview release) is my 1st dip into linux/unix.
I have seen somewhere that my sound card is supported by the kernel but so far it's the only thing that doesn't work.

I don't know how to install the drivers or anything like that so any help would be greatly appreciated.

I have established that I need isapnp installed but when I run "./configure", it fails so I can't do "make". Any ideas???

thanks

---

### Post by Fred_og_ro on 2004-11-12
Hi bikeboy
Welcome to UbuntuLinux

I followed the instructions given here:
[http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html)

Step by step.

I edited two configuration files. "/etc/modules.conf" and "/etc/modules".
To edit I used the program "vi" that is available in the terminal window. To start a terminal window, right-click on your desktop and you'll get an meny where the first item should be to start a terminal.

"vi" is a fast program that is ideal to edit configuration files, but it can be confusing and frustrating to newbies. Since you will be editing configuration files, please take precautions like making a backup copy of the file first. Key commands in "vi" are: "i" for inserting text, "ctrl-c" to stop inserting text, and ":x" and enter to save and exit "vi". The command ":q!" will exit without saving.


1. Edit the configuration file /etc/modules.conf as an administrator. 
One way of doing this is by typing "sudo vi /etc/modules.conf" in a terminal window. You'll be asked to enter your password to continue. 
Add the following lines:

# ALSA Configuration.
alias snd-card-0 snd-opl3sa2

# some stuff for the OSS drivers
alias char-major-14 snd-pcm-oss
alias sound-slot-0 snd-card-0

# aliases for sound card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

3. You also need to edit the configuration file /etc/modules
Here you will again need to be an administrator. Using the same technique as given above, type "sudo vi /etc/modules" into a terminal window.

The following is a one long row. Type it all in as one long row.
Note. Make sure the information in this line is what it says in your bios (if you have that information).

snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 
port=0x538 sb_port=0x220 wss_port=0x530

4. At this point I rebooted. This shouldn't really be necessary....

5. Once you're back into your desktop you can right-click the sound icon and select the mixer. If it starts then your golden. Be sure to set the volume up if there is no sound.

Good luck

Fred_og_ro <- means peace_and_quiet ;)

---

### Post by bikeboy on 2004-11-12
Thanks mate that worked perfectly. Great to have this kind of support.
It will probably help a lot of other people too.

Thanks again

---

