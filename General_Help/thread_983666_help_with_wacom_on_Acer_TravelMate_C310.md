---
title: "help with wacom on Acer TravelMate C310"
date: 2008-11-15
forum: General Help
---

### Post by DouglasAWh on 2008-11-15
I've got an Acer TravelMate C310 that I'd like to get the tablet pen working.  I'm a little confused by the instructions at 

[https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)

Am I supposed to comment out the serial stuff or leave it in?  Some places make it sound like serial and LCD are similar.

The TravelMate C310 has an nVidia NV43 [GeForce Go 6200/6400].

Thanks for the help!

---

### Post by joshaude on 2008-12-14
I feel your pain, I have a travelmate c314 and I was able to get wacom working somewhat with feisty fawn, but now I can't get anything going.

---

### Post by Favux on 2008-12-17
Hi DouglasAWh and joshaude,

I'm assuming you have a wacom tablet?  Is it a serial or usb connection?  Us TX2000 and TX2500 users are lucky enough to have a tutorial that let's us get linuxwacom installed.  You might want to take a look at it, it is at:

   [http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")

This may help give you ideas.  It may even work for you.  But with Intrepid there is another problem.  Intrepid introduces HAL, and the HAL fdi file for wacom only supports a stylus.  If you have other stuff, like eraser or touch, it won't support it.  So you have to revert back to xorg.conf.  But installing linuxwacom on Intrpid won't build a configured xorg.conf.  So you need to use a xorg.conf from Hardy or earlier.  Or figure out what should be in there piece by piece.

Good luck.

---

### Post by DouglasAWh on 2008-12-17
> **Favux said:**
> Is it a serial or usb connection?  

Whatever the connection on a LCD laptop is...

---

### Post by Favux on 2008-12-17
Hi DouglasAWh,

Not the LCD, the digitizer (tablet) built into the LCD.  Wacom's were serial but they've recently introduced some USB tablets, and tablet pc's.  The reason I ask is that linuxwacom even more recently has added USB support to its linuxwacom driver.  Since the wacom in the TX2000 and TX2500 is USB, we had some problems initially.  Although now that they are at v. 0.8.2 (their latest driver at their site, not the repository) it seems less of an issue.

The problem was the driver in the Ubuntu repository was pre-USB support until recently.  Now I think it is in the early USB support version (still buggy and incomplete support).  So we were using the development branch of the driver to get our tablets working.  If your tablet is USB and you're trying to use the repository driver that could be one of your problems.

---

### Post by DouglasAWh on 2008-12-17
> **Favux said:**
> Hi DouglasAWh,

Not the LCD, the digitizer (tablet) built into the LCD.  Wacom's were serial but they've recently introduced some USB tablets, and tablet pc's.  The reason I ask is that linuxwacom even more recently has added USB support to its linuxwacom driver.  Since the wacom in the TX2000 and TX2500 is USB, we had some problems initially.  Although now that they are at v. 0.8.2 (their latest driver at their site, not the repository) it seems less of an issue.

The problem was the driver in the Ubuntu repository was pre-USB support until recently.  Now I think it is in the early USB support version (still buggy and incomplete support).  So we were using the development branch of the driver to get our tablets working.  If your tablet is USB and you're trying to use the repository driver that could be one of your problems.

So how do I find out which I should be using, serial versus USB?  It's not plugged into a jack, it's just my monitor.  I was following instructions from the link I provided in the first post.  I'll take a look at the .8.2 driver and see what I can make happen.

---

### Post by DouglasAWh on 2008-12-17
upon further review, it must be serial since this laptop is a few years old.

---

### Post by Favux on 2008-12-17
Hi DouglasAWh,

If you don't have the spec.s in the info that came with the laptop I guess you will have to Google it.  The serial or USB connection is internal in the laptop.  You are probably right about it being serial.  But at least you now see why I was asking.  And you may want to check out the tutorial I mentioned.  Between the wiki you referenced (which actually looks reasonably up to date) and it you may get a better idea of what your xorg.conf needs to look like.

Good luck.

---

### Post by DouglasAWh on 2008-12-17
```

user@5686:~/Desktop/linuxwacom-0.8.2/prebuilt$ sudo ./install
Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
wacom_drv.so installed under /usr/lib/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
Installed under /usr/local/bin

Installing wacomcpl......
Installed under /usr/local/bin


You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver.


```

The line "You need to compile", is that an indication it did not work correctly.  I'm using the latest 8.10 kernel.

---

### Post by Favux on 2008-12-17
Alright, you think you have a serial wacom tablet.  I would suggest you follow gali98's tutorial that I referenced.  Copy and paste the commands, don't type them.  Just substitute 0.8.2 for 0.8.1-6 in the instructions.  You'll still have trouble when your done because the xorg.conf most likely won't be properly configured.  But between the wiki and the tutorial's discussion of the xorg.conf you should be able to piece it together.

Luck

---

### Post by DouglasAWh on 2008-12-17
At the moment, this means nothing to me...

```

wacdump v0.7.4                                                                  

MODEL=Unknown                           ROM=1.0-0
CLS=USB  VNDR=Unknown  DEV=Unknown  SUB=UNKNOWN




  BUTTON=+00000 (+00000 .. +00000)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=
     BT8=                BT9=               BT10=               BT11=
    BT12=               BT13=               BT14=               BT15=
    BT16=               BT17=               BT18=               BT19=
    BT20=               BT21=               BT22=               BT23=    



```

---

### Post by DouglasAWh on 2008-12-17
Still clueless

```

user@5686:~/Desktop/linuxwacom-0.8.2/prebuilt/32$ sudo ./wacdump /dev/ttyS0
22:08:08.533 WARN: Discarding 38
22:08:08.534 WARN: Discarding C3
22:08:08.534 WARN: Discarding 8C
22:08:08.534 WARN: Discarding 17
22:08:08.534 WARN: Discarding C3
22:08:08.534 WARN: Discarding 08
22:08:08.534 WARN: Discarding F5
22:08:08.565 WARN: Discarding 38
22:08:08.565 WARN: Discarding C3
22:08:08.565 WARN: Discarding 8C
22:08:08.565 WARN: Discarding 17
22:08:08.565 WARN: Discarding C3
22:08:08.565 WARN: Discarding 08
22:08:08.565 WARN: Discarding F5
22:08:08.601 WARN: Discarding 98
22:08:08.601 WARN: Discarding C3
22:08:08.601 WARN: Discarding 8C
22:08:08.601 WARN: Discarding 17
22:08:08.601 WARN: Discarding C3
22:08:08.602 WARN: Discarding 08
22:08:08.602 WARN: Discarding F5
22:08:08.693 WARN: Discarding 38
22:08:08.693 WARN: Discarding C3
22:08:08.693 WARN: Discarding 8C
22:08:08.693 WARN: Discarding 17
22:08:08.693 WARN: Discarding C3
22:08:08.693 WARN: Discarding 08
22:08:08.694 WARN: Discarding F5
22:08:08.213 WARN: Discarding 98
22:08:08.213 WARN: Discarding C3
22:08:08.213 WARN: Discarding 8C
22:08:08.213 WARN: Discarding 17
22:08:08.213 WARN: Discarding C3
22:08:08.213 WARN: Discarding 08
22:08:08.214 WARN: Discarding F5
22:08:08.285 WARN: Discarding 38
22:08:08.285 WARN: Discarding C3
22:08:08.285 WARN: Discarding 8C
22:08:08.285 WARN: Discarding 17
22:08:08.285 WARN: Discarding C3
22:08:08.285 WARN: Discarding 08
22:08:08.286 WARN: Discarding F5
22:08:08.317 WARN: Discarding 98
22:08:08.317 WARN: Discarding C3
22:08:08.317 WARN: Discarding 8C
22:08:08.317 WARN: Discarding 17
22:08:08.317 WARN: Discarding C3
22:08:08.317 WARN: Discarding 08
22:08:08.318 WARN: Discarding F5
WacomOpenTablet: Connection timed out


```

This is way more effort than should be necessary.  Come on Acer, make some Linux drivers for your tablet.  Giving up again. I have better things to do.

---

### Post by Favux on 2008-12-17
I agree, from that it's not clear it's a wacom tablet.  And I don't think I'd assume CLS=USB means that it, whatever it is, is a USB tablet.  I think you need to nail down your TravelMate spec.s before embarking on any more driver installation adventures.

---

### Post by Favux on 2008-12-18
Hi again DouglasAWh,

I did a little research and it is not clear to me what your tablet is.  The Acer site seems very shy about speccing the tablet.  I did find one review where it was described as "serial wacom tablet emulation"!  The pen is described as a Wacom pen or alternatively a Digital pen.  So it's possible it is a Wacom clone emulating a Wacom serial tablet.  Perhaps this explains some of the difficulty with the linuxwacom driver.

But other folks have **reported success**.  I think you can use the linuxwacom driver in the repository through Synaptics, which simplifies things.  Basically it looks like you have to configure your xorg.conf and the serial.conf files, which shouldn't take that long.

On the forum there is one thread, which you visited:

   [http://ubuntuforums.org/showthread.php?t=219004]("http://ubuntuforums.org/showthread.php?t=219004")

It looks like maybe he made one error in his post.  The solution is on a link in that thread:

   [http://wiki.ubuntu-it.org/Hardware/Notebook/AcerTravelmateC310]("http://wiki.ubuntu-it.org/Hardware/Notebook/AcerTravelmateC310")

because there he adds to the file /etc/serial.conf :
```
#Stylus pen
/dev/ttyS0 port 0x06f8 irq 6 uart 16550A

```
Unfortunately the post is in Italian, so maybe you didn't pay much attention to it.  It actually looks pretty clear to me the steps you need to take but if you get stuck you could translate the Italian at Google.

This Italian link probably came from the tuxmobile site:

   [http://tuxmobil.org/tablet_unix.html]("http://tuxmobil.org/tablet_unix.html")

At that site there are several other HOW TO's for C300's, etc..  There is a HOW TO for a C300 which seems relevant at:

   [http://ubuntuforums.org/showthread.php?t=232250]("http://ubuntuforums.org/showthread.php?t=232250")

Another "success" story:

   [https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelmateC311XMi]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelmateC311XMi")

In short this seems doable.  It looks like a 1 to 3 hour project.

Hope this is helpful.

---

### Post by DouglasAWh on 2008-12-18
Thanks Favux!  I'm not sure when I'll have an hour or three to spare, but when I do I'll give this a shot.  Perhaps tomorrow.  We are supposed to have "thunder snow" here for seriously.

---

