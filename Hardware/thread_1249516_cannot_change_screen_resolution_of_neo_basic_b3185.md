---
title: "cannot change screen resolution of neo basic b3185"
date: 2009-08-25
forum: Hardware
---

### Post by abatek on 2009-08-25
[Neo Basic B3185]("http://www.neo.com.ph/products_basic_b3185.aspx")

Graphics: SiS Mirage 3+

only available resolution : 800x600
refresh rate : 61 Hz

Ubuntu 8.10 - Intrepid


apology if this was already posted and solved.

anyone help please

---

### Post by Yellow Pasque on 2009-08-25
[http://launchpadlibrarian.net/24820246/xorg-driver-sis671_0.9.tar.gz](http://launchpadlibrarian.net/24820246/xorg-driver-sis671_0.9.tar.gz)

```
gksudo gedit /etc/X11/xorg.conf
```
Then make sure you add this line (or modify the existing 'Driver' line) in the 'Device' section:
```
Driver   "sis671"
```

---

### Post by abatek on 2009-08-26
Thanks Temujin but I still need further instructions.

I clicked on the link and opened the file xorg-driver-sis671_0.9.tar.gz

then extracted all files and all were saved on Home Folder

I modified and added the Driver "sis671" as shown below

```
Section "Device"
	Identifier	"Configured Video Device"
       Driver          "sis671"
EndSection
```

then save the file, re-started

but reported with error messages

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "sis671" (module does not exist, 0)

(EE) No drivers available


Did I saved the extracted files in the wrong directory? The suggested/default location was Home Folder so I just click OK.


Thanks again for your time.

---

### Post by dumblebee100 on 2009-08-26
> **abatek said:**
> Thanks Temujin but I still need further instructions.

I clicked on the link and opened the file xorg-driver-sis671_0.9.tar.gz

then extracted all files and all were saved on Home Folder

I modified and added the Driver "sis671" as shown below

```
Section "Device"
	Identifier	"Configured Video Device"
       Driver          "sis671"
EndSection
```

then save the file, re-started

but reported with error messages

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "sis671" (module does not exist, 0)

(EE) No drivers available


Did I saved the extracted files in the wrong directory? The suggested/default location was Home Folder so I just click OK.


Thanks again for your time.

I never did a driver installation from tar.gz archives but I think that drivers are not loaded from /home directory 

I think they should be in /usr directory and may be in inner folders ..since Im not sure about this I would recommend you to install it from synaptic 

then do the same procedure ....adding sis driver in xorg.conf

---

### Post by abatek on 2009-08-27
Thanks dumblebee100 I used Synaptic Package Manager and after locating the xorg-driver-sis671-0.9 via the search function

I marked both files for upgrades then click Apply
when it was completed I edited the xorg.conf and restart

but same error that Ubuntu is running in low graphics mode

as a note, I tried to troubleshoot the error by
- reviewing the xserver log fie
- review the startup errors
- edit configuration file (I only view this and changed nothing)
- archive configuration and logs (can be located at /var/log/failsafeX-backup-090826233004.tar)

so I go back and restarted in low graphics mode

I am really lost, am I not?

Thanks guys for your patience.

---

### Post by abatek on 2009-08-27
Since I am not sure what else to do, I edited the device section and changed from,

Driver "sis671"

to

Driver "sis"

and now the error message is only one, (I am not sure if that is good or bad direction)

(EE) No drivers available.

the other error message no longer appear but still 800x600 the only screen resolution.

What else do I need to do/check?

Thanks again.

---

### Post by Yellow Pasque on 2009-08-27
My apologies; I thought I linked you to a .deb file. There are some .deb's posted in this bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/301958](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/301958)
Unfortunately, the one posted for Intrepid/8.10 doesn't have 2D acceleration. The one for Jaunty does, but I'm not sure if it will work for you.

---

### Post by dumblebee100 on 2009-08-27
> **abatek said:**
> Thanks dumblebee100 I used Synaptic Package Manager and after locating the xorg-driver-sis671-0.9 via the search function

I marked both files for upgrades then click Apply
when it was completed I edited the xorg.conf and restart

but same error that Ubuntu is running in low graphics mode

as a note, I tried to troubleshoot the error by
- reviewing the xserver log fie
- review the startup errors
- edit configuration file (I only view this and changed nothing)
- archive configuration and logs (can be located at /var/log/failsafeX-backup-090826233004.tar)

so I go back and restarted in low graphics mode

I am really lost, am I not?

Thanks guys for your patience.

I told you to follow above procedure ..not just adding sis ...instead I meant sis671

anyways its not working for u ..so I searched for and got a link which might be useful for u 
[http://ubuntuforums.org/showthread.php?t=958967]("http://ubuntuforums.org/showthread.php?t=958967")

---

### Post by abatek on 2009-08-27
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/301958/comments/5](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/301958/comments/5)

works like a charm as they say ...


```
#5   	 bgerlich  wrote on 2008-12-16:

    * xserver-video-sis671_ubuntu8.10-1_i386.deb (286.9 KiB, application/x-debian-package)

For convenience I have prepared a debian package with sisimedia driver patched by fedora forum's user "bahamot" to work with xserver 1.5.x.

I have made a few very minor changes so that the driver would seem more seamless, namely - buggy 2D acceleration is now disabled by default. I have also included a pciid file, so that the card is detected automatically. Just install the deb and restart your xserver.

Remember to remove any driver names and such from xorg conf manualy or by typing sudo dpkg-reconfigure -phigh xserver-xorg in terminal.

```

VERY BIG THANKS guys, it is now set to 1280x800 as it should be.

And along the way I learned how to "install a deb file, lol

Now twice happy, madwifi lets me connect wireless and now i386.deb sets the correct screen resolution.

---

### Post by abatek on 2009-08-27
@dumblebee100

regarding the changing from "sis671" to "sis" and then back again to "sis671" was just an experiment, since I am lost and ever since been doing the trial and error method and hoped i get lucky but no it didn't work

yes had also read that and this but did not work

SiS 771/671 Mirage 3 Video Drivers!?!?

[http://ubuntuforums.org/showthread.php?t=958967&page=2](http://ubuntuforums.org/showthread.php?t=958967&page=2)

anyway, really thank you for helping me out, Ubuntu is now more fun than before

---

### Post by Yellow Pasque on 2009-08-27
is your issue solved or not?

---

### Post by abatek on 2009-08-27
additional comments:

I was able to set resolution to 1280x800 from 800x600

but if I set it back to any other lower resolution (1024x768, 800x600, 640x480) I cannot set it back to 1280x800

Then if I set to 1024x768, I cannot re-set to other settings.
After a re-start it defaulted to 1280x800.

Not sure if that is a bug or a limitation.

---

### Post by abatek on 2009-08-27
> **Temüjin said:**
> is your issue solved or not?

well as far as thread and the title suggest, it is now SOLVED

thank you guys for helping me on my problem

i will now search for similar problem and subscribed to them for my new problem -- probably a side effect of the 'upgrade'

after the Ubuntu splash screen and before the login screen

[B]appears a very bright one inch wide vertical strip in the middle of the screen
[/B]
it was not there before the 'upgrade'

just to check if it is setting-specific only

i tested for 1280x800, 1024x768 and even at 800x600, and did it for 3 times, it always appear

so will check if there is already a similar problem reported

again thank you guys

---

