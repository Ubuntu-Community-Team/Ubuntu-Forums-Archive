---
title: "Ubuntu Live USB Drive"
date: 2008-11-03
forum: General Help
---

### Post by Tex786 on 2008-11-03
Hi,

I made a bootable USB drive last night and I do not know how to boot off of my USB drive.

What do i need to do to get booting? How can i use this live usb on other computers say at work?

I have ubuntu 8.04 on the drive as I had it on a CD from ubuntu. I did the USB thing in ubuntu 8.10

Thanks

---

### Post by C.S.Cameron on 2008-11-03
In BIOS select your flash drive as the first hard drive.

---

### Post by conscious on 2008-11-03
I think you should set your USB drive as a boot device in BIOS.

However,
[QUOTE=http://en.wikipedia.org/wiki/Live_USB]Some computers, particularly older ones, may not have a BIOS that supports USB booting. Many which do support USB booting may still be unable to boot the device in question. In these cases a computer can often be "redirected" to boot from a USB device through use of an initial bootable CD or floppy disk.[/QUOTE]

---

### Post by timcredible on 2008-11-03
fwiw, the usb flash drive install works great - i used a 1gb flash drive, and had the 8.10 iso on my hard drive, went through the menus, and in less than 5 minutes, i was booting off a flash drive.  what a nice way to carry around the livecd.  bravo, whoever wrote that code!

---

### Post by chipmaker on 2008-11-05
Hello,

I am a Linux and Ubuntu newbie. I want to make a bootable USB drive and now that 8.10 has an automated function for making that, I tried to do it last night. I created a bootable USB drive after running a LiveCD (made from burning an ISO downloaded from a local server (Switch, if I'm not mistaken). But I think I'm running into some problems when I try to boot from the USB now. This is what happens (I'm running a Dell Latitude D630 laptop):

1. When I power on the laptop, I have to press F12 and select "booting from USB storage device". My USB drive is already plugged in even before I power on.

2. I select "English" from the list of languages.

3. At this point, I am presented with a menu screen and I have the choice of selecting either (1) Try Ubuntu without any change to your computer; or (2) Install Ubuntu.

When I select the first option, I get a screen with ASCII text saying "Loading. Please wait." on top, and some verbage about Ubuntu being free software and having no guarantees, etc. At the bottom of the screen, there seems to be a command line saying "ubuntu@ubuntu:~$". Nothing else happens even if I press ESC. At this point, I have to power the system off.

When I select the second option, I get through to Ubuntu booting up and a screen about partitioning the hard disk. I then press Quit and Ubuntu OS fully loads. At this point, I seem to be a Live Session User.

Is this normal or is something else supposed to happen? Can I just boot in completely into Ubuntu without going through the selections?

---

