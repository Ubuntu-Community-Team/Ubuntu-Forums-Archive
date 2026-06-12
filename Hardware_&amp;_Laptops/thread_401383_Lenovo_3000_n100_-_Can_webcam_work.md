---
title: "Lenovo 3000 n100 - Can webcam work?"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by whitefort on 2007-04-04
Hi,

A few weeks ago I got a Lenovo 3000 N100 with Ubuntu pre-installed, and I've been very, very happy with it.

But now I've got to thinking that it would be nice if there was a way to get that little built-in webcame to work, and I was just wondering if anyone's had any success with this?

Thanks!

---

### Post by lusepuster on 2007-05-22
I  havent't had the time to test it yet, but there should be some alpha drivers for the webcam and the fingerprint reader. Your mileage will definitely vary.

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768")

---

### Post by Aleksandersen on 2007-07-08
Quick answer from a guy with the same notebook and problems: **No.** You can work your bottom off, but it will not work no matter what you do.

Apparently the only solution is to a) learn how to program your own drivers or b) donate your machine to some developers who can program drivers. Option a takes forever if you do not know how things work, and option b is not very cost effective.

Alternately you can just wait and put your trust in the commercial work done by Skype to get [webcams to Linux](http://opensource-notebook.com/2007/06/skype-linux-video/).

Try getting an external Logitech QuickCam Pro 4000 instead. Those works every time and they have very good image quality. I use one my self for both Mac OS 10.4 and KUbuntu 7.04.

---

### Post by whitefort on 2007-07-09
Thanks, Alek.

Actually I can live very happily without any webcam at all - I just thought that since there was one built in to the hardware, it might be nice if it worked!

At the risk of changing the subject of this thread, is there a way to change the resolution of the monitor - presumably because it's widescreen, every time I try to alter it I end up with a totally black screen. It would be nice if I could get a *slightly* lower resolution, as my eyesight isn't what it used to be!

---

### Post by Aleksandersen on 2007-07-09
In KUbuntu 7.04: K > System Settings >Monitor and Display, and click Administer Mode, authorize, and finally change your resolution. Works like a charm.

By the way... Search the web for how to disable the camera and fingerprint scanner. They consume power if you do not disable them!

---

### Post by whitefort on 2007-07-09
Hi Again, Alek.

I know you're going to decide that I'm a complete idiot, but I've been through every menu in KDE, and I can't find a single one that relates to screen resolution.

This is Ubuntu 7.04.  I installed it as Gnome, then later added all the KDE stuff so I could boot into KDE.  Perhaps that's why I'm missing something?

I have resolution options in Gnome (which crash the display) but absolutely no way to get at resolution in KDE.  Very strange!

---

### Post by Aleksandersen on 2007-07-09
The application is a mneu item of it's own in the K menu.

Try this command:

sudo systemsettings -caption "%c" %i %m

---

### Post by whitefort on 2007-07-09
Hi Alek.

I have systemsettings, but it doesn't contain any monitor or resolution controls.

When i typed
sudo systemsettings -caption "%c" %i %m

It complained about %i and %m. 
(systemsettings: Unexpected argument '%i'.
)
 When I tried again without them, i got the following:
----------------------------------------------------------

john@Corinth:~$ sudo systemsettings -caption "%c"
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
kdecore (KProcess): WARNING: _attachPty() 11
john@Corinth:~$ MediaManager::slotMediumRemoved: sda1
----------------------------------------------------------------

I've no clue what any of this means, and have to admit that I'm way out of my depth.  I guess I'll just have to make do with the resolution I've got, because when it comes to messing with this complicated stuff, the usual result is that I end up with a wrecked system and having to do a reinstall!

But thanks for trying to help!

John

---

### Post by abhitux on 2007-09-16
I have a different model (Lenovo 3000 Y500 776144Q0 whcih seems to be India specific. Making the webcam work out of the box was a pain in the wrong place. However, extensive Googling and lots of terminal output later i realised there is no set way you could make your webcam work. 

1)It's important to have video4Linux drivers according to some. 

2)Try doing lshw in the terminal. it should show you the output of the hardware installed on your system. Then it would be possible for you to find out the correct driver for your laptop. 

3)Try Easy Cam. It is an automated script which "might" list your camera and install the drivers for you. Mind you, it is still in development and doesnot support your hardware out of box as yet. 

However, I could make Ekiga support my webcam and show me the output. Other softwares like Camorama shows the error output as ;could not connect to video device (/dev/video0) Strangely Camera Monitor shows as my camera being "switched on". I tried to reinstall Camorama but failed to make it work. ](*,)]

I tried using Xaw TV to capture the picture but again it doesnot seem to connect to the device. 

I am at my wits end as to what could be the issue here. The fact that camera works in Ekiga means that the software drivers are alright. Why shouldn't it work in others? 

Please do shed some light on this. This would be much much appreciated!:)Thanks in advance.

---

### Post by rybu on 2007-09-16
Simple question.  Say you find a driver you want to experiment with.  You download it, compile it.  Now you have the driver sitting in a somewhat appropriate place, for example:

/lib/modules/2.6.22-11-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko

How do you create /dev/video0 and link it to the driver, so that Ubuntu knows the driver is ready for use?

sudo modprobe -v uvcvideo

loads the driver but that doesn't associate it with /dev/video0, which is what I would like to do.

---

### Post by pinecone on 2008-05-16
I've got it working.  Found a partial answer here.  Figured out what I had to do to make it actually work, and updated the wiki.  Just scroll down to webcam and follow the directions.

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768#preview](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768#preview)

---

