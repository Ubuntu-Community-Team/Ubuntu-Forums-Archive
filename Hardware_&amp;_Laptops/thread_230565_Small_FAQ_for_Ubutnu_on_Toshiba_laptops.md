---
title: "Small FAQ for Ubutnu on Toshiba laptops"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by riksweeney on 2006-08-06
30 Aug 2006 - Updated sound section

**Disclaimer - I sourced all this information from various places around the internet and I do not claim this to be my own work or take credit for it. I also accept no responsibilty for any damage or loss of data caused by following the instructions in this post, what worked for me might not work for anyone else.**

I had a few problems installing Ubuntu on my Toshiba laptop, so here are the things I did to get it working:

**_Ubuntu freezes during the live CD install_**

Download the Alternative CD instead. It's available from Ubuntu's website. This should install OK.

**_When I boot into Ubuntu, I don't get the login screen, it just goes black_**

You've probably had a Kernel Panic. On my Toshiba Satellite M70 I solved this by doing the following:

When I booted up I pressed escape to get the boot menu. I highlighted the default boot option and choose to modify / edit the current settings. I then selected the kernel line and added

acpi=off

to the end of the line. When I booted into Ubuntu I no longer received a Kernel Panic. If this works for you, edit /boot/grub/menu.lst, locate the kernel line you modified in the boot screen and add

acpi=off

to the end of the line. I believe you need to do this to the

# defoptions=

line aswell so that when you update the kernel you don't get the Kernel Panic again.

**_The XServer isn't working, I've got an ATI card_**

Install the ATI driver by typing the following

sudo apt-get install xorg-driver-fglrx

I then did

sudo dpkg-reconfigure xserver-xorg

to reconfigure my /etc/X11/xorg.conf, but this might not be necessary.

**_It still doesn't work!_**

Edit your /etc/X11/xorg.conf and find the following lines

Section "Device"
        Identifier "(The name of your ATI Card)"

In this section, change the Driver value to

"fglrx"

and give that a try.

**_Nope, that didn't help either!_**

*Have you tried turning it off and on again?*

Try these values aswell.

BusID "PCI:1:0:0"
Option "VideoOverlay" "on"

This is all I had to do to get it working.

**The sound is out of sync in some games**

This mainly affects SDL games and applications such as MAME SDL, SCUMMVM, Frozen Bubble and [Parallel Realities games]("http://www.parallelrealities.co.uk"). I found out the the sound mixing was causing a problem. This solution should work for an Intel ICH6:

Create a file in your Home directory called

.asoundrc

and paste the following into it

pcm.!default {
    type plug
    slave.pcm "dmixer"
}

pcm.dmixer  {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        format s16_LE
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
}
    bindings {
        0 0
        1 1
}
}

I also disabled the Sound System in the System Settings' Sound And Media.

---

### Post by Sethro on 2006-08-06
Thanks this helped!!

---

### Post by DesertFox on 2006-08-07
yah no kidding man i was just about to give up this helped a lot

---

### Post by riksweeney on 2006-08-07
Glad to have been of service!

---

### Post by ieee488 on 2006-08-07
I have an old Toshiba.

Do you any hints on getting PCMCIA card especially modems to work?

---

### Post by riksweeney on 2006-08-30
I made a minor modification to the sound section if anyone's interested

---

