---
title: "no video (at all)"
date: 2012-11-19
forum: Hardware
---

### Post by cdoublejj on 2012-11-19
I get video just fine during install and grub but, after/during boot i have no video at all.

I'm running Lubuntu 12.04 on Panasonic tough book CF-28, CF-28PTJAZQM. I installed off USB, no cd/dvd drive.

---

### Post by dannyboy79 on 2012-11-19
can you hold ctrl-alt and then hit F1. can you then sign in to the tty1 session and tell us what graphics card you have? you can find out by issuing the following command and looking for the vga line.

```
sudo lshw -short
```

---

### Post by cdoublejj on 2012-11-20
Command not found. lspci on the other hand gives me this...

[IMG]http://i.imgur.com/kB5eSl.jpg[/IMG]

Sorry about the weird angle.

---

### Post by cwsnyder on 2012-11-20
If you are in a terminal or other command line, type **xrandr**.

This should tell you what resolution(s) your screen is set for in Ubuntu and what settings Ubuntu believes your Intel 82830M/MG graphics controller supports for your display. Below is the listing from my desktop:```
xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1280x1024      59.9* 
```Note the listing on the first line of the response with the current resolution of 1280x1024.  On the second line note my monitor is called VGA-1.  Your monitor name for Ubuntu should also be listed in a line which looks similar to this.

To change your resolution to 1024x768 from the command line, replace VGA-1 with the response from your computer and use:```
xrandr --output VGA-1 --mode 1024x768
```

---

### Post by cdoublejj on 2012-11-20
it just says command not found.

[IMG]http://i.imgur.com/Qqx65l.jpg[/IMG]

---

### Post by cwsnyder on 2012-11-21
Try the following in a terminal:```
sudo apt-get update
sudo apt-get install x11-xserver-utils
xrandr
```
Instead of taking a picture of the screen, if you are accessing the Internet from the machine, you can copy from the terminal by highlighting what you want to send, right clicking, select copy, then paste here between code /code tags.

---

### Post by cdoublejj on 2012-11-21
I have multiple machines. ATM i don't think the toughbook has internet but, i'll give it a try and if it fails i may try another normal install. i installed this via alternate and alternate never detects network drivers/devices.

I just plugged in a Ethernet adapter will see if that works.

---

### Post by cdoublejj on 2012-11-22
So i ran the command and it' asks me to pu the 12.10 cd in the disc drive, except i have no disk driver. I have been installing from usb via a PLOP boot floppy disk.

So i think i'm gonna try another NON alternative install and allow it to download updates while installing, i expect no video just as before but, i'll try some of the suggested command in the this thread ie xrandr.

---

### Post by cdoublejj on 2012-11-22
[IMG]http://i.imgur.com/9pV5dl.jpg[/IMG]

I'm wondering if the 128mb ram stick install is bad or maybe if the embedded ram is bad or even if the hard drive is bad. Obviously the non alternative installed failed. The alternative gets errors when trying to "install selected software" however i think that is glitch due to the fact i'm installing it off a usb stick where it tries to find the data on the non existent cd/dvd drive. I think that has something to do with LILI not knowing how to properly convert _Alternate_ ISO to USB format.

---

### Post by cdoublejj on 2012-11-23
The embedded RAM failed stress tests. So much for that project.

---

### Post by cdoublejj on 2012-12-05
so i got a working CF-28. i've been doing a little research and am wondering the if the intel 82830m or Intel 830m don't meet the minimum requirement for linux?

---

