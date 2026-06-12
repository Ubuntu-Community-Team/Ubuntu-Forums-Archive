---
title: "Cannot run lcd4linux anymore after fresh install!"
date: 2008-11-30
forum: General Help
---

### Post by l1nuxb0x on 2008-11-30
I have been running ubuntu since around 6.04 with lcd4linux, everything was configured and working perfect. I've upgraded over the years to 8.04 without ever doing a format/reinstall until recently.

A few days ago I thought I'd try the 64 bit edition and I didn't save a copy of my lcd4linux.conf file, now I can't get the sucker to work.

I am using a palm zire 72 using palmorb to emulate a matrixorbital lcd

On startup the palm is set as 
> Bus 001 Device 003: ID 0830:0061 Palm, Inc. Lifedrive / Treo 650/680 / Tunsten E2/T5/TX / Zire 21/31/72 / Z22

I found it at /dev/bus/usb/001/003 and pointed to it in the lcd4linux.conf file
however I get an error when trying to run it
> alex@alex-desktop:/dev/bus/usb/001$ sudo lcd4linux -Fvvq
Version 0.10.1-RC2-796 starting
plugin_cfg.c: Variable minute = '60000' (60000)
plugin_cfg.c: Variable tack = '100' (100)
plugin_cfg.c: Variable tick = '500' (500)
[KVV] Using station 89
[KVV] Using default port 80
[KVV] Using default refresh interval of 60 seconds
[KVV] Default abbreviation setting: off
lcd4linux.c: initializing driver MatrixOrbital
MatrixOrbital: $Rev: 773 $
MatrixOrbital: using model 'LK204-25'
MatrixOrbital: using port '/dev/bus/usb/001/003' at 19200 baud
MatrixOrbital: tcgetattr(/dev/bus/usb/001/003) failed: Inappropriate ioctl for device

Now I used gnome-pilot settings and got it working by selecting "usb:" as the port, but that doesn't really tell me specifically where it points

With my old install, back when lcd4linux worked, I remember pointing it to a ttyUSB001, or similar, but that isn't used in the new install it seems...

I think the problem is where I'm pointing it to, all my other usb devices were installed when I installed ubuntu and they all work perfect (the mouse even uses all it's buttons!). So what replaces ttyusb001,2,3,etc on the new version?

Is it the 64-bit deal that is holding me back?

Here is the bits of my lcd4linux.conf file that had to be changed
> Display LK204 {
    Driver 'MatrixOrbital'
    Model 'LK204-25'
    Port '/dev/bus/usb/001/003'
#   Port '/dev/tts/0'
    Speed 19200
    Contrast 256/2
}
> Display 'LK204'
#Display 'MI240'
#Display 'CW12232'
#Display 'HD44780-20x4'
#Display 'SC1602D'
#Display 'LCM-162'
#Display 'CF631'
#Display 'CF632'
#Display 'CF633'
#Display 'Curses'
#Display 'M50530-24x8'
#Display 'CT20x4'
#Display 'T6963-240x64'
#Display 'XWindow'
#Display 'USBLCD'
#Display 'BWCT'
#Display 'Image'
#Display 'Pertelian'

#Layout  'Default'
#Layout 'L16x2'
#Layout 'L20x2'
Layout 'Test'


Variables {
   tick 500
   tack 100
   minute 60000
}

Does anyone have any hints or suggestions?

---

### Post by l1nuxb0x on 2008-11-30
Strangely enough, my ubuntu froze tonight, and on reboot it refused to startx! I logged in by command line and typed 'startx' and it came up with a gray screen and an X pointer but nothing else happened. I've been using windows the rest of the night...

So, late night bump

---

### Post by l1nuxb0x on 2008-11-30
No new thoughts? I'm gonna play some zombie mod cs:S anyone wanna join?

---

### Post by l1nuxb0x on 2008-12-01
Alright well I couldn't salvage my 64 bit system, and I formatted and installed 32 bit ubuntu, 8.10, aaaannnd same situation. My old install before the 64 bit must have carried over the /dev/ttyUSB001 but the new install doesn't sooo don't know what to do

---

### Post by l1nuxb0x on 2008-12-01
I switched to the sample conf file that comes with the ubuntu version of lcd4linux, but I'm still getting the same error

Also I get an error that says 'could not connect to port 6600, is mpd started?'. That's paraphrased, btw.

I looked up mpd and it's a 'Music Player Daemon' which is completely unrelated, isn't it? Why should that matter? Anyway I ignore it when it comes up.

---

### Post by peterthewolf on 2008-12-06
Do not know if of help but I will not move my main PC from feisty as I need to run lcdproc to a palm pilot. On fiesty it runs with no problem but from 7,10 all ubuntu versions are broken so that no valid /dev is generated for the palm usb. There are many posts on launchpad but such a basic fault does not effect enough people for it to attract attention.

---

### Post by l1nuxb0x on 2008-12-07
ahhhh, that does help

and it's weird, because it worked for me in 8.10 but that was because it had been installed since 6.04 and everything else around it was updated

when I reinstalled this last time, I formatted first. I felt I had to to avoid any conflicts with the 64bit install.

So it seems to me it's still possible to do, but I don't know how to do such a thing so I'm really at the mercy of the developers/code writers

thanks for bringing that to my attention peter!

---

### Post by peterthewolf on 2008-12-08
Lcdproc would not work for me on 8.10 but following 'sudo modprobe visor' all was well.

---

### Post by l1nuxb0x on 2008-12-08
cool, I'll give that a try, but where did you link the palm to in /dev?

---

### Post by peterthewolf on 2008-12-08
In gnome pilot I linked to /dev/pilot

---

### Post by l1nuxb0x on 2008-12-11
you're the man peter, after modprobe visor it linked my palm to /dev/ttyUSB1 like on the old system and after some changing to the /etc/lcd4linux.conf it is working!

Thanks so much!

---

### Post by markitoxs on 2009-10-25
just for the info, modprobe visor reboots the palm tx continuously if attached (karmic koala)

---

