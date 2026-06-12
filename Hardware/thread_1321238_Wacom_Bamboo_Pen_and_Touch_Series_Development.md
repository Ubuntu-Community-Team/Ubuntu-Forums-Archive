---
title: "Wacom Bamboo Pen and Touch Series Development"
date: 2009-11-09
forum: Hardware
---

### Post by Ayuthia on 2009-11-09
This thread is the development thread for the Wacom Bamboo Pen and Touch series tablets (0xd1, 0xd2, 0xd3, and 0xd4 devices).  0.8.6-1 was released a while back and that should get your device working in Karmic.

If you are using Lucid, please try the instructions on this [post]("http://ubuntuforums.org/showpost.php?p=9119518&postcount=782").

We are going to try a different approach on getting the driver installed.  To make sure that you have all the development tools:
```
sudo apt-get update
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get install libhal-dev libxrandr-dev
sudo apt-get build-dep xserver-xorg-input-wacom
```
Do the following if you are NOT using Karmic:
```

sudo apt-get purge wacom-tools xserver-xorg-input-wacom

```
If you are using Karmic also include the following:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h

```

We are going to use 0.8.6-1 for testing:
**Option A**
For now I have archived this version because of a recent release so you can download it [here]("http://linuxfans.keryxproject.org/packages/wacom/archive/linuxwacom-0.8.6-1.tar.bz2").
Unpack the source:
```

tar -xvjf linuxwacom-0.8.6-1.tar.bz2
cd linuxwacom-0.8.6-1

```

Compile and install:
```
make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.30/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
```

For those using TwinView" (Thank you, [alpharesearch]("http://ubuntuforums.org/showpost.php?p=9031388&postcount=989")!)
```

make clean
make distclean
./configure --enable-wacom --prefix=/usr --enable-quirk-tablet-rescale
make
sudo make install
sudo cp src/2.6.30/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a

```
Make sure that you also set the Horizontal setting to zero.  See the bottom of this post for more info.

To reload the module:
```
sudo modprobe -r wacom
sudo modprobe wacom
```
NOTE: The 'make clean' and 'make distclean' will produce an error message if you have not done a ./configure before.  This is because the source has never been compiled yet and the Makefiles have not been created yet (the Makefile gets built with the ./configure command).  Therefore there is nothing to clean up.

If wacomcpl is not working with your device, please try copying over the file from /usr/local/bin:
```
sudo cp /usr/local/bin/wacomcpl /usr/bin
```
Thanks portets for that [information]("http://ubuntuforums.org/showpost.php?p=8949263&postcount=937")!

**Some helpful xsetwacom commands**
**NOTE: It looks like in 0.8.6-1 the device name might be used instead of touch.  You will need to check with xsetwacom list to find the actual device name.  See [post 870]("http://ubuntuforums.org/showpost.php?p=8819587&postcount=870") for more detail.**
To find the list of recognized devices:
```
xsetwacom list
```
To set your touch so that it works like a mouse touchpad:
```

xsetwacom set touch Mode Relative

```
To set the resolution of your touch (Example is for the medium sized tablet -- the small is X=480 Y=320):
```

xsetwacom set touch bottomx 740
xsetwacom set touch bottomy 500

```
To turn the touch on/off:
```

xsetwacom set touch Touch off
xsetwacom set touch Touch on

```

For the TwinView dual screen to work, this also needs to be added to 10-linuxwacom.fdi:
```

<merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
<merge key="input.x11_options.ScreenNo" type="string">0</merge>

```
If there are any corrections that need to be made, please let me know.

I am not if there are still some adjustments needed for the .fdi files.  Please refer to this [post]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

---

### Post by kgingeri on 2009-11-09
Ayuthia, we have discovered that maybe the purge isn't right.  At least not for version 0.8.4-3 and Karminc.  You may want to update the instructions above?
EDIT: I will test it with 0.8.5-1 and Karmic now

EDIT: do you want to mention that the line...
> sudo cp src/2.6.28/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
...is very kernel version specific (i.e. 2.6.28, Jaunty)? I am on Karmic and therefore use 2.8.31 currently.

I am proceeding from here.
Thx!!

EDIT: yeah again ;)  A time saver for patching all the files would be...
```
for FILE in *.patch; do patch -p1 < $FILE; done
```  :)

---

### Post by Ayuthia on 2009-11-09
> **kgingeri said:**
> Ayuthia, we have discovered that maybe the purge isn't right.  At least not for version 0.8.4-3.  You may want to update the instructions above - at least for Karmic?

EDIT: do you want to mention that the line...
...is very kernel version specific (i.e. 2.6.28, Jaunty)? I am on Karmic and therefore use 2.8.31 currently.

I am proceeding from here.
Thx!!

I am under the impression that 0.8.5-1 does not produce a 2.6.31 directory anymore.  If it does, please let me know and I will correct the post.

I went ahead and updated the purge commands.  Do we know why it is causing problems?  My concern is that we might be missing something in the newer source that is not getting installed.

---

### Post by kgingeri on 2009-11-09
> **Ayuthia said:**
> Do we know why it is causing problems?  My concern is that we might be missing something in the newer source that is not getting installed.

No I really don't - sorry.  Dnprossi discovered it.  I'll keep an eye open for any hints.
I've done some edits to my first response also.

Another thing I discovered is that you cannot do a 'make clean' and 'make distclean' until at least one .configure  ;)

---

### Post by kgingeri on 2009-11-09
Ok got a compile error:
```
In file included from ./xf86Wacom.h:25,
                 from ./wcmConfig.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
./wcmConfig.c:629: error: expected '}' before '{' token
make[2]: *** [wcmConfig.o] Error 1
make[2]: Leaving directory `/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/xdrv'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src'
make: *** [all-recursive] Error 1
```

Looks like you forgot comma's in the structure assignments starting at line 629.

---

### Post by Ayuthia on 2009-11-09
> **kgingeri said:**
> No I really don't - sorry.  Dnprossi discovered it.  I'll keep an eye open for any hints.
I've done some edits to my first response also.

Another thing I discovered is that you cannot do a 'make clean' and 'make distclean' until at least one .configure  ;)

You are correct about the make clean/distclean commands.  I have updated the post to mention that.  It is one of those things that I run into quite often when I chain the commands together and break out while the system is doing the ./configure (and then run the chain of commands again).  

Thanks!

---

### Post by kgingeri on 2009-11-09
Oops - another problem...
```
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c: In function 'wacom_bamboo_pt_irq':
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c:169: error: 'PATCH' undeclared (first use in this function)
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c:169: error: (Each undeclared identifier is reported only once
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c:169: error: for each function it appears in.)
make[4]: *** [/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.o] Error 1
make[3]: *** [_module_/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src'
make: *** [all-recursive] Error 1
```

Do you want me to PM these to you instead?

It does appear like I only have a 2.6.28 directory - you are right there. :)

EDIT: is PATCH suppose to be a pre-compile directive for patch number? got thru make by define PATCH as  '#define PATCH 1' in wacom_wac.c

---

### Post by Ayuthia on 2009-11-09
> **kgingeri said:**
> Oops - another problem...
```
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c: In function 'wacom_bamboo_pt_irq':
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c:169: error: 'PATCH' undeclared (first use in this function)
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c:169: error: (Each undeclared identifier is reported only once
/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.c:169: error: for each function it appears in.)
make[4]: *** [/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28/wacom_wac.o] Error 1
make[3]: *** [_module_/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src/2.6.28'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/KGSD-8G/Downloads/Sys/Wacom/linuxwacom-0.8.5-1/src'
make: *** [all-recursive] Error 1
```

Do you want me to PM these to you instead?

It does appear like I only have a 2.6.28 directory - you are right there. :)

EDIT: is PATCH suppose to be a pre-compile directive for patch number? got thru make by define PATCH as  '#define PATCH 1' in wacom_wac.c
Either way is fine.  You are correct.  The magic number should be 9.  I will update the patch tarball.

EDIT: It is now updated and compiled clean -- also had to fix wcmConfig.c (left out a few commas)

---

### Post by kgingeri on 2009-11-10
Ok Ayuthia, all is working normal - at least stylus and buttons.  I will see if eraser is and if I can collect touch data.

BTW another minor correction in post #1...
> The new experimental stuff is that I have added the .fdi and udev rules as a patch. So when the source is installed (in the sudo make install command above) they should automatically go to the correct place. The files are labled as 10-linuxwacom.fdi (It is Favux's modified version--test3) and should go to /usr/share/hal/fdi/policy.

should be /usr/share/hal/fdi/policy/[COLOR="Navy"]20thirdparty/[/COLOR]

> There is also a 60-wacom.rules file in src/util but it does not look like it is automatically installed (I could be wrong about this) that has the devices listed. You can try to copy that to /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules:
```
sudo cp src/util/60-wacom.rules /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
```

This is my observation - yes.  The by-path links show up, but no sym-links until you copy in the rules files.  The tablet does work with only the by-path, but I still like the more human-readable sym-links.

Oh 3 more things...

1) after copying in the rules file, I unplugged and replugged and no tablet recognition - looks like a reboot? I'll test.

2) I've noticed something interesting about the mouse pointer jumping when you lift the stylus. In the upper left corner the mouse jumps very little (always the same angle BTW), but in the lower right it jumps at least 3 x's further.  I've attached a diagram to explain.

3) the mouse and stylus cursor seemed very jittery, more then normal. If I recall, someone else mentioned this in the other thread.  I'll see if it is the same after a reboot with the rules file in place.

---

### Post by kgingeri on 2009-11-10
No touch info in dmesg at all.

I can't seem to do a xidump on any device?  Here is what I get...
```
crw-r----- 1 root root 13, 36 Nov 10 00:28 mouse4
crw-r----- 1 root root 13, 37 Nov  9 23:58 mouse5
lrwxrwxrwx 1 root root      6 Nov 10 00:28 tablet-wacom-bamboo-pen_touch-stylus -> event9
lrwxrwxrwx 1 root root      7 Nov 10 00:28 tablet-wacom-bamboo-pen_touch-touch -> event10
lrwxrwxrwx 1 root root      6 Nov 10 00:28 wacom -> event9
lrwxrwxrwx 1 root root      7 Nov 10 00:28 wacom-touch -> event10

root@kgulnb:/home/karl/Downloads/Sys/Wacom/linuxwacom-0.8.5-1# xidump /dev/input/wacom-touch 
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/wacom-touch'
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/wacom-touch'
Unable to find input device '/dev/input/wacom-touch'

root@kgulnb:/home/karl/Downloads/Sys/Wacom/linuxwacom-0.8.5-1# xidump /dev/input/wacom       
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/wacom'
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/wacom'
Unable to find input device '/dev/input/wacom'

root@kgulnb:/home/karl/Downloads/Sys/Wacom/linuxwacom-0.8.5-1# xidump /dev/input/tablet-wacom-bamboo-pen_touch-touch 
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/tablet-wacom-bamboo-pen_touch-touch'
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/tablet-wacom-bamboo-pen_touch-touch'
Unable to find input device '/dev/input/tablet-wacom-bamboo-pen_touch-touch'

root@kgulnb:/home/karl/Downloads/Sys/Wacom/linuxwacom-0.8.5-1# xidump /dev/input/tablet-wacom-bamboo-pen_touch-stylus 
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/tablet-wacom-bamboo-pen_touch-stylus'
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '/dev/input/tablet-wacom-bamboo-pen_touch-stylus'
Unable to find input device '/dev/input/tablet-wacom-bamboo-pen_touch-stylus'
```

Am I missing something?  What else can I look for?

EDIT: BTW unplugging and replugging is not working - no tablet after replugging  :(
No reboot necessary but I have to reload wacom with modprobe to get it active again.

EDIT: wacomcpl is working - tho 'touch' is blank - not coded yet likely? Do note the 2 'pad's tho in the attached image.

EDIT: also, setting buttons on the tablet has no effect - I expect we haven't got near this yet, code wise.

---

### Post by Ayuthia on 2009-11-10
> **kgingeri said:**
> 2) I've noticed something interesting about the mouse pointer jumping when you lift the stylus. In the upper left corner the mouse jumps very little (always the same angle BTW), but in the lower right it jumps at least 3 x's further.  I've attached a diagram to explain.


I think that sounds right.  Since the tablet resolution is different than the screen, the driver has to scale the coordinates.  So for simplicity if the X resolution is 100 for the tablet and 300 for the screen, when X is at 0 for the tablet the screen would reflect 0.  When X is at 1the screen would reflect 3.  And when X is at 97, the screen would reflect 291 (97/100 = 291/300).  So for the last example, you will see that the tablet is 3 points away from the bottom right hand corner but the screen is 9 points away.  But when the tablet was 1 point away from the top left hand corner, the screen was only 3 points.

I am not for sure if my explanation makes sense or not.

---

### Post by Ayuthia on 2009-11-10
> **kgingeri said:**
> 

Am I missing something?  What else can I look for?

EDIT: BTW unplugging and replugging is not working - no tablet after replugging  :(
No reboot necessary but I have to reload wacom with modprobe to get it active again.

EDIT: wacomcpl is working - tho 'touch' is blank - not coded yet likely? Do note the 2 'pad's tho in the attached image.

EDIT: also, setting buttons on the tablet has no effect - I expect we haven't got near this yet, code wise.

I might be wrong about this, but I don't think that xidump will report anything because the wacom_drv.so has captured the event so xidump can't see it.  Does wacdump now work or does it segfault?

As for the plugging/unplugging, I will have to check into this one.  I am trying to figure out if that is something that the new driver is running into problems or if there is something else needed in the code.  I recall seeing a post from Favux about having to load the wacom module manually for his tablet (different device but the same source code).  Is there any messages in dmesg when you disconnect/reconnect?

---

### Post by kgingeri on 2009-11-10
> **Ayuthia said:**
> I might be wrong about this, but I don't think that xidump will report anything because the wacom_drv.so has captured the event so xidump can't see it.  Does wacdump now work or does it segfault?

Yeah, Favux explained that to me re wacom_drv.so but I figured **_x_**idump is part of X therefore should see data.  Must be wrong on that.

No luck with wacdump either - still segfaults.

Your explaination re the cursor jump makes good sense, I'd think that it could be coded in tho - to account for display mismatch.  This is a small 1024x600 netbook display.  Looks like wcmCommon.c in xdrv handles this stuff.

Think i'm retiring for the evening. Back at tomorrow night hopefully. :)

---

### Post by kgingeri on 2009-11-10
One more thing Ayuthia... Seems as tho only a part of the features structure is being used.  I noticed touch variables...
```
struct wacom_features {
        char *name;
        int pktlen;
        int x_max;
        int y_max;
        int pressure_max;
        int distance_max;
        int type;
        int touch_x_res;
        int touch_y_res;
        int touch_x_max;
        int touch_y_max;
        unsigned char unit;
        unsigned char unitExpo;   
};
```

I also plugged in dummy data...
```
        { "Wacom Intuos2 6x8",        WACOM_PKGLEN_INTUOS,    20320, 16240, 1023, 31, INTUOS },
    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT, 1024, 512, 1024, 512, 32, 32 },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-460
```
(can't find ANY specs anywhere, box or Wacom's site, re touch resolution for CTH-460)

A re-make went fine but no data from you debug statements yet.
Any who, off to get some shut-eye.  Later.

---

### Post by Favux on 2009-11-10
Hi,

You can use wacdump before X starts.  Once X starts wacom_drv.so grabs the input and wacdump can't get to it.  You can use xidump but wacomcpl can interfere with it.

---

### Post by dnprossi on 2009-11-10
Hi to all and Thanks for new thread!!!

Ubuntu Karmic **Desktop** - on acer aspire 5920g
I have installed 0.8.5-1

Have not purged wacom-tools xorg-server.....
Not using udev nor xorg
when installing 0.8.5-1 fdi did not get copied to directories had to do it manually. used test3 fdi by Favuk...

Stylus - OK
Buttons - OK
Eraser - OK
Nothing from touch nor tablet buttons
wacomcpl OK
contains: touch - empty settings
          eraser - with 4 settings buttons
          stylus - with 4 settings buttons
          pad - not there!!!

Plugging/Unplugging - OK!!

Gimp - Pressure Eraser - OK!!
MyPaint - Pressure Eraser Tilt - OK!!
Blender - Pressure - OK!!

Ubuntu Karmic **Remix** - on acer aspire 5920g
Have same problems as kgingeri's problems in other [thread]("http://ubuntuforums.org/showthread.php?t=1290251") and need udev

fdi and udev files auto-copied correctly by install

Ubuntu Karmic **Remix** - on acer aspire one
Have same problems as kgingeri's problems in other [thread]("http://ubuntuforums.org/showthread.php?t=1290251") and need udev

fdi and udev files auto-copied correctly by install

Something is missing in Remix that Desktop has or maybe also different pc drivers

UPDATE!!
Removed Karmic Remix on Aspire one
Installed Karmic Desktop and 0.8.5-1 wacom drivers no purge
fdi and udev installed automatically. rebooted
Working as on acer aspire 5920g
removed udev - rebooted
Still working as above...

Something wrong with remix dist???

---

### Post by dnprossi on 2009-11-10
EDIT!!!
Confirm above after another very long test on different machines!!!

REDIT!!!
Updated Ubuntu Desktop karmic to 2.6.31-15 generic
reinstalled completely just to see if 0.8.5-1 worked and it does as above...

---

### Post by Ayuthia on 2009-11-10
> **kgingeri said:**
> One more thing Ayuthia... Seems as tho only a part of the features structure is being used.  I noticed touch variables...
```
struct wacom_features {
        char *name;
        int pktlen;
        int x_max;
        int y_max;
        int pressure_max;
        int distance_max;
        int type;
        int touch_x_res;
        int touch_y_res;
        int touch_x_max;
        int touch_y_max;
        unsigned char unit;
        unsigned char unitExpo;   
};
```

I also plugged in dummy data...
```
        { "Wacom Intuos2 6x8",        WACOM_PKGLEN_INTUOS,    20320, 16240, 1023, 31, INTUOS },
    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT, 1024, 512, 1024, 512, 32, 32 },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-460
```
(can't find ANY specs anywhere, box or Wacom's site, re touch resolution for CTH-460)

A re-make went fine but no data from you debug statements yet.
Any who, off to get some shut-eye.  Later.

Is the wacom kernel module loaded?  If so, I will need to double-check that I am pointing the device to the right wacom option.  They are just print statements that should have been triggered once the module is loaded.

I will look into the touch portion once we know that we are getting debug data in both /var/log/messages (or dmesg) and /var/log/Xorg.0.log.  I just want to be sure that we are where we left off in the previous version (0.8.4-3).

---

### Post by Ayuthia on 2009-11-10
> **kgingeri said:**
> Yeah, Favux explained that to me re wacom_drv.so but I figured **_x_**idump is part of X therefore should see data.  Must be wrong on that.

No luck with wacdump either - still segfaults.

Your explaination re the cursor jump makes good sense, I'd think that it could be coded in tho - to account for display mismatch.  This is a small 1024x600 netbook display.  Looks like wcmCommon.c in xdrv handles this stuff.

Think i'm retiring for the evening. Back at tomorrow night hopefully. :)

The jump is happening because of the 0x80 data is not reporting any X,Y coordinates but we are still using it because it seems to be needed for the eraser switch.  Once we figure out the significance of the 0x80 data we can either code in the X,Y coordinates to help it out or figure out another way to get the eraser to switch without using the 0x80 data.

You get to have your choice of tablets to use and you have a netbook?  You have all the fun toys!  We will need to figure out how to calculate the touch resolution.  Right now I am borrowing the TabletPC version, but it might be too big.  But before we do that, we need to be able to pick up the information in kernel module.

---

### Post by ehfortin on 2009-11-10
> **Ayuthia said:**
> Is the wacom kernel module loaded?  If so, I will need to double-check that I am pointing the device to the right wacom option.  They are just print statements that should have been triggered once the module is loaded.

I will look into the touch portion once we know that we are getting debug data in both /var/log/messages (or dmesg) and /var/log/Xorg.0.log.  I just want to be sure that we are where we left off in the previous version (0.8.4-3).

Hi there,

I had this issue at first try. I had to specifically do a "rmmod wacom" before doing the "modprobe wacom" again. It's like if the "modproble -r wacom" didn't do the job. I think it is because I already had the wacom.ko loaded in the kernel. modprobe -r would remove a module but not unload it from memory. At least, that's my understanding.

I have not rebooted yet but I have the tablet working just as before. Still have no touch logging. I'll create a new log set so that you can see what xorg and messages are reporting.

Should post this a little bit later.

ehfortin

---

### Post by sylaulove on 2009-11-10
I'm sorry to double-post, but I'm not sure to know which of the thread is still active, if one of them is not visited anymore.  Here is the content of the first, still applicable:

I plan to buy this tablet soon, and I'd like to use it on Ubuntu (my reason here).

I NEED the pen function, since I'm a student, to take notes in my courses. The touch function is optional for me, but I'd like to use it to the max of it's capabilities.

If the pen works well, I could participate in the development under Ubuntu while I take notes, so I will have plenty of time to give feedback and test.

I'm not very good in developement of driver, in fact, I don't know anything on this, but I'd like to learn.

I'm running Karmic on inspiron 1501, and I plan to buy this since mid-december.

So my question is: Is the pen reliable?

---

### Post by marek_online on 2009-11-10
Hi sylaulove,

From what I can tell, if you're using a desktop version of Ubuntu then the pen should work reliably in Karmic at least (I've had reliable pen and eraser function on three different kernels now - 2.6.28-15-generic in Jaunty and 2.6.31-14-generic and 2.6.31-15-generic in Karmic). From dnprossi's post above, the Karmic Netbook Remix seems to have problems though.

I suspect if you follow Ayuthia's installation instructions in the first post here, I think you should be good to go.

---

### Post by HarM_triade on 2009-11-10
Hello all and Ayuthia and favux in particular,

Have been trying to understand what actualy is happening with my bamboo.

Checking the wcm2 patches I noticed that they point to 2.6.28 kernel. Can't "diff" anything when I compare the 2.6.31 patched and unpatched 0.8.4-3 modules.
I don't know how to compare binaries so, my question is:

How come the 2.6.31 modules work only after being patched?
Where's the trick that makes 'em work as they apparently do?

Good luck,
HarM

---

### Post by Ayuthia on 2009-11-10
> **marek_online said:**
> 
I suspect if you follow Ayuthia's installation instructions in the first post here, I think you should be good to go.
I think you might want to use the instructions in [post 541]("http://ubuntuforums.org/showpost.php?p=8262965&postcount=541") on the other thread.  This one is that is going to be under development quite a bit and may have versions where something might not work.  The other thread is the one we are currently using for those who want to use the pen with the tablet.

So to answer your question, both threads will be active.  I do plan on moving the other thread to another name because the instructions are not in the first post but right now I want to make sure that this new version starts off where the other one left off.

---

### Post by Ayuthia on 2009-11-10
When someone has a chance, can they test out the touch without it being configured in the 10-linuxwacom.fdi file?  I want to see if the evdev or some other driver grabs it and responds to touch.  It will help us determine where we need to initiate the touch.

---

### Post by HarM_triade on 2009-11-10
> **Ayuthia said:**
> When someone has a chance, can they test out the touch without it being configured in the 10-linuxwacom.fdi file?  I want to see if the evdev or some other driver grabs it and responds to touch.  It will help us determine where we need to initiate the touch.

Can you be more specific, i.e. follow all the instructions and remove the fdi_patch itself or comment out lines or what?

I've got some free space left for (xtra) clean installs to test on.
Just say the word. :D
 
Good luck,
HarM

---

### Post by Ayuthia on 2009-11-10
> **HarM_triade said:**
> Hello all and Ayuthia and favux in particular,

Have been trying to understand what actualy is happening with my bamboo.

Checking the wcm2 patches I noticed that they point to 2.6.28 kernel. Can't "diff" anything when I compare the 2.6.31 patched and unpatched 0.8.4-3 modules.
I don't know how to compare binaries so, my question is:

How come the 2.6.31 modules work only after being patched?
Where's the trick that makes 'em work as they apparently do?

Good luck,
HarM

You can only do a "diff" on the source code, not on the binaries.  If you take a look at the Makefile in the 2.6.31 directory, you will find that file will copy the source from the 2.6.28 and 2.6.27 folders and place them in the 2.6.31 directory.  So when we apply the patches to the 2.6.28 directory it will also affect the 2.6.31 directory.

So why do the patches make the device work?  The kernel module looks up the model number of your device and checks to see if it is defined.  This is done in wacom_wac.c.  You will find that wacom_init_input_dev helps define what will be reported to X for the particular device.  Then wacom_wac_irq will parse through the data that is coming from the device and then send it over to X with the appropriate wacom_report_* function.  At the end of the source code, you will see the list of devices defined there.  The devices that we are working on over here are the ones listed with BAMBOO_PT.

Once the items are compiled in the 2.6.X directory, the wacom.ko file is created.  This is the kernel module that reports the data to the X driver.  In theory, the wacom.ko kernel module can report things to evdev also.  However, the wacom.ko module may not report things in the correct order for the evdev module so you can end up with erratic behavior.  This is why we have the wacom X module (the source code in the src/xdrv directory) wacom_drv.so.

I hope that I answered your question.  If not, hopefully it was helpful to someone.  Anyone can feel free to add/correct this information.

---

### Post by Ayuthia on 2009-11-10
> **HarM_triade said:**
> Can you be more specific, i.e. follow all the instructions and remove the fdi_patch itself or comment out lines or what?

I've got some free space left for (xtra) clean installs to test on.
Just say the word. :D
 
Good luck,
HarM

I am just looking for the touch lines to be commented out of the .fdi file.  I am thinking that we can still use the .fdi file and the touch portion will hopefully will be grabbed by another X driver instead of the wacom one:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

    <!-- Wacom Bamboo Pen & Touch (models CTT-460 CTL-460 CTH-460,461,660) -->
<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
    <merge key="input.x11_options.DebugLevel" type="string">12</merge>
    <merge key="input.x11_options.CommonDBG" type="string">12</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">pad</append>
<!--
      <append key="wacom.types" type="strlist">touch</append>
-->
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
  <device>
<!--
    <match key="input.x11_options.Type" contains="touch">
      <merge key="info.product" type="string">touch</merge>
    </match>
-->
  </device>
</deviceinfo>

```
If the wacom_drv.so still grabs the touch portion, then we might need to remove the TOUCH_ID portion out of the code for the devices.

---

### Post by HarM_triade on 2009-11-10
> **Ayuthia said:**
> I am just looking for the touch lines to be commented out of the .fdi file.  I am thinking that we can still use the .fdi file and the touch portion will hopefully will be grabbed by another X driver instead of the wacom one.

Ok, will do, but not before Thursday afternoon. I didn't bring my bamboo home and my "ancient" serial tablet never had touch..... and on top, this is a 64 bit Desktop. :P

What driver are you hoping for .... the synaptic?

Good luck,
HarM

---

### Post by Ayuthia on 2009-11-10
> **HarM_triade said:**
> Ok, will do, but not before Thursday afternoon. I didn't bring my bamboo home and my "ancient" serial tablet never had touch..... and on top, this is a 64 bit Desktop. :P

What driver are you hoping for .... the synaptic?

Good luck,
HarM

Actually, I don't really have a preference on which driver takes it as long as the touch works.  If it works, then we can get that source and see what it is doing to make the touch talk.

---

### Post by GolemdX on 2009-11-10
Personally, touch isn't high priority.

This thread was only created approximately 2 hours after I got my Bamboo, and so far it's been *functioning* great with the patches.

I too, have the problem with the resolution of the screen/tablet and the mouse not being in the right position once the pen loses 'focus', but I understand that's normal for now.

My real question is, how/can I switch the tablet to the equivalent of 'left handed mode'? I have to hold the tablet the opposite side around, which leads to my hand pressing and smudging the buttons when I'm at the side. The only differencees (that I know of) is that the tablet's pen area is rotated 180 degrees, and the order of the buttons on the tablet are reversed. Not too bad, but it's nicer to have the tablet the other way around so my hand won't get slowed down by the shiny surface.

---

### Post by Favux on 2009-11-10
Hi GolemdX,

Add to the .fdi:
```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```

But since this is a testing thread if you can try disabled touch like Ayuthia asked that would be good.  And report the Xorg.0.log and var/log/messages and lshal etc.

---

### Post by GolemdX on 2009-11-10
Thanks. I also just noticed pen pressure isn't working for me in GIMP or InkScape (dunno about anywhere else).

EDIT: Just tried repatching... not sure if this was here before the edit, but I get

```
patch: **** malformed patch at line 75:  </deviceinfo>
```

EDIT2: The edit didn't seem to work. Did I do something wrong?

---

### Post by ehfortin on 2009-11-10
> **Ayuthia said:**
> Actually, I don't really have a preference on which driver takes it as long as the touch works.  If it works, then we can get that source and see what it is doing to make the touch talk.

As promised, here are my logs.  This is after a clean reboot. At first, the wacom driver was not loaded. Maybe you will see something in xorg.results as the tablet probably registered as something else. Then, I've loaded the wacom driver (you will see this in both logs) and try to move the pointer with the stylus (which worked fine) and then, I tried just about anything in touch mode (buttons and touch basically).

Both mode of the tablet are registering to the same ID I would think (0xd3 for my tablet). I don't see how they can be managed apart as I have to discriminate on ID.

BTW, even if I loaded without the wacom driver, the tablet was not working neither with the stylus or touch. No reaction whatsoever so... if a driver picked up the touch mode, it was not a driver that was managing the pointer as nothing was moving.

I'll let you analyse the logs and if you think you are seeing something, we will try to see how we can get to a reproducible result for test purpose and logging (by adding more log details in the proper .fdi file).

ehfortin

---

### Post by kgingeri on 2009-11-10
Back at it for a bit tonight.  I think Karmic Remix has Alzheimers!  ;) Dnprossi is right.  

Everything was fine the other night.  Tonight I started up my netbook (Acer Aspire One also) and the tablet worked only for a few minutes.  I had to reload wacom several times until it finally behaved properly and permanently!  So same as I reported in some of my last posts in the other thread.  I'm wondering about the rmmod - may try that.  I hadn't been using it.  Anyway, don't let this interfere with other more important development - I'm not concerned about it for now.

OK, I will see if I can get evdev to see any touch data, with your mods Ayuthia...

EDIT:
I noticed I had 2 fdi files - 10-wacom.log and 10-linuxzwacom.fdi - maybe that'smy spuratic issue?!  Diff on both turn up one blank line.  Maybe the 'make instal' created the old style file and I dind't notice?

---

### Post by kgingeri on 2009-11-11
Ayuthia, I could not get touch data, no how. Could we just print the packet stream (9 bytes) in binary as it comes from the tablet?  This might tell us that there is at least something getting picked up from touch?

*BTW, the manual clearly states that touch is disabled if the stylus or eraser are within proximity.*

That's it for me tonight. later all.
...actually I will post my xorg log and lshal results after commenting the fdi...

See two text files attached.

Night all.

---

### Post by dnprossi on 2009-11-11
Hi Ayuthia,

I have tested un-commented and commented "touch".

EDIT!!!! This happened with empty fdi (dont know why!!!) Added xorg.log
when commented stylus is recognized from tip and back (cursor movement) but no functionality from pressure, tip click, nor buttons. no touch  

EDIT!!!! Stylus buttons tip-click etc continue working with commented fdi no touch

wacomcpl shows touch when un-commented - hides touch when commented.
there is no log activity from touch (commented un-commented)

messages log syslog reach incredible sizes real fast when using tablet 1.1 gb... Wow!!! had to erase them and restart to see anything. viewer crashes with those sizes...

**[COLOR="Red"]EDIT[/COLOR] answered [here]("http://ubuntuforums.org/showthread.php?t=1290251&page=62")!!**
How do i get rid of tablet logging in messages, syslog etc while not testing???? I commented
```

<merge key="input.x11_options.DebugLevel" type="string">12</merge>
<merge key="input.x11_options.CommonDBG" type="string">12</merge>

```
but logs are still filled with 
```

reporting as pen
[wacom-9]: X=13418 Y=7550 pressure: 0 d6: 0 d7: 0
[wacom-9] data:  0:2 1:f0 2:69 3:34 4:73 5:1d 6:0 7:0

```

Ubuntu Karmic Desktop - 2.6.31-15-generic
Bamboo Fun S Pen & Touch - CTH-461/S

---

### Post by Ayuthia on 2009-11-11
> **kgingeri said:**
> Ayuthia, I could not get touch data, no how. Could we just print the packet stream (9 bytes) in binary as it comes from the tablet?  This might tell us that there is at least something getting picked up from touch?

*BTW, the manual clearly states that touch is disabled if the stylus or eraser are within proximity.*

That's it for me tonight. later all.
...actually I will post my xorg log and lshal results after commenting the fdi...

See two text files attached.

Night all.

The only place that I have been able to grab the packet data is from the wacom kernel module and that is where I have placed the debug statements.  Do you know of another place?

---

### Post by Lucretia9 on 2009-11-11
> **GolemdX said:**
> Personally, touch isn't high priority.


For me, it is a priority. I need to get touch going so I can get away from the mouse as it causes me pains to use it now. Possible CTS.

Luke.

---

### Post by sylaulove on 2009-11-11
I'll let you know when I have it
Thx

---

### Post by marek_online on 2009-11-11
> **Favux said:**
> Hi GolemdX,

Add to the .fdi:
```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```But since this is a testing thread if you can try disabled touch like Ayuthia asked that would be good.  And report the Xorg.0.log and var/log/messages and lshal etc.

Had meant to ask about that actually. Thanks GolemdX and Favux.

More generally, I've tried commenting out the touch lines from the fdi. I've no response to touch at all, and nothing appearing in /var/log/messages. I've attached a set of logs, but I don't think there anything there really.

xinput is listing Wacom Bamboo P&T, which it doesn't when the touch lines are present in the fdi,  but that's the height of it really.

Cheers.

---

### Post by Favux on 2009-11-11
Hi marek_online,

If touch works with the current .fdi then you may need to add the line to the touch section too.

---

### Post by Ayuthia on 2009-11-11
Based on the information gathered here, it looks like we will need to look at the kernel to make it happen.  TheguywholikesLINUX was able to get some touch data (or at least some data that was not related to the pen) to appear.

So at this time, we can put the touch information back into the .fdi file.  I will be releasing another patch soon that will try to initialize another variable for the touch.

---

### Post by Ayuthia on 2009-11-11
I have created a new patch (but forgot to update the revision number--sorry!).  This one has a new init parameter for the touch to see if it does anything.  It will use the original .fdi that is currently patched.

I am also going to test out a new patch for the touch.  This one comes from Pierre Chambart who submitted it to the linuxwacom site.  If it does work for all the devices, I will let them know.

Please test the patch (it is in the first post) and submit the Xorg.0.log and the /var/log/messages so we can see what is happening.  Thank you!

---

### Post by GolemdX on 2009-11-11
Man, I must be bad at this. What I did was add that line inside the fdi.patch file, applied the patch, recompiled, and nothing happened.

Sorry if I'm slowing you down :(. What can I do to help?

EDIT: I'll test the new patch :D.

---

### Post by Ayuthia on 2009-11-11
> **GolemdX said:**
> Man, I must be bad at this. What I did was add that line inside the fdi.patch file, applied the patch, recompiled, and nothing happened.

Sorry if I'm slowing you down :(. What can I do to help?

EDIT: I'll test the new patch :D.

At this point, you should only need to use the patches to make it work.  You will also need to copy the 60-wacom.rules like the first post mentions also.  Anyone-if this information is incorrect, please let me know.

Thanks for helping!

---

### Post by GolemdX on 2009-11-11
The new patch fixed the cursor position for me, it stays where it should!

Also, I was talking about switching the tablet to left-handed mode (rotating it 180 degrees).

---

### Post by Ayuthia on 2009-11-11
> **GolemdX said:**
> The new patch fixed the cursor position for me, it stays where it should!

Also, I was talking about switching the tablet to left-handed mode (rotating it 180 degrees).

Oops.  Sorry about that.  You might try and edit /usr/share/hal/fdi/policy/10-linuxwacom.fdi and add the line there after you do the 'sudo make install'.  If you applied the patch after you made your change, it must have wiped out your change.

---

### Post by GolemdX on 2009-11-11
Eugh... I just ran the command

```
sudo cp src/util/60-wacom.rules /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
```

because I hadn't before and now it's not working. I'll try the process again.

EDIT: Did another sudo make install. It's still not working. Also, there is no /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules on my system, after that.

---

### Post by Ayuthia on 2009-11-11
> **GolemdX said:**
> Eugh... I just ran the command

```
sudo cp src/util/60-wacom.rules /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
```

because I hadn't before and now it's not working. I'll try the process again.

EDIT: Did another sudo make install. It's still not working. Also, there is no /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules on my system, after that.

You might try copying the file over there again.  Confirm that /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules is there and then restart.

---

### Post by GolemdX on 2009-11-11
Yep, that fixed it, I should have tried that first...

Also, I accidentally said that 40-xserver-xorg-input-wacom.rules doesn't exist, when I meant to say that /usr/share/hal/fdi/policy/10-linuxwacom.fdi doesn't exist. Copied the wrong thing.

---

### Post by kgingeri on 2009-11-11
> **Ayuthia said:**
> The only place that I have been able to grab the packet data is from the wacom kernel module and that is where I have placed the debug statements.  Do you know of another place?

No - thats definitely right.  What I meant is a more condensed report of the full packet (no masking bits - just hex) - say if the packet has changed since last report, then print it in the logs.  My thinking is that if there is any data changes then we'll see it with only touching the tablet.  Do you know what I mean?

EDIT: unless that's just too disruptive to the process right now. I haven't tried your new patch yet.  Doing so now...  :)

---

### Post by kgingeri on 2009-11-11
As mentioned previously the pen lifting issue is gone - cursor stays in place now  :D

I've attached my Xorg.o.log - nothing shows at all when I issue a...
```
# tail -f /var/log/Xorg.0.log
```
...and touch the tablet - or any of the tablet buttons (there are 4 on the CTH-460).  Lot of data with stylus as you will see.

---

### Post by Ayuthia on 2009-11-11
> **kgingeri said:**
> No - thats definitely right.  What I meant is a more condensed report of the full packet (no masking bits - just hex) - say if the packet has changed since last report, then print it in the logs.  My thinking is that if there is any data changes then we'll see it with only touching the tablet.  Do you know what I mean?

EDIT: unless that's just too disruptive to the process right now. I haven't tried your new patch yet.  Doing so now...  :)

I will see what we can do about that.  As for disrupting the process, I think that the other person's patch has solved the pen portion so we should now be only focusing on the touch.

Of course, we still need some confirmation on other devices besides the 0xd4 (that is the one you are using right?).  GolemdX, which device do you have?

---

### Post by kgingeri on 2009-11-11
> **Ayuthia said:**
> ...
Of course, we still need some confirmation on other devices besides the 0xd4 (that is the one you are using right?).  GolemdX, which device do you have?

I have a 0xd4 (pen only, at work, so not testable unless I bring it home) and a 0xd1 (pen & touch + 4 tablet buttons) here at home - where I am testing etc.  I don't recall seeing the pen problem on the 0xd4 but it may have been there.

I agree tho, let's continue with touch.  Buttons can wait until after that.

Now, I may have an issue with my 0xd1.  I decided I should be sure touch works, so I installed it with updated drivers on my Macbook and I get NO TOUCH there either.  OSX fully supports it (tablet buttons work fine, an there are all kinds of settings for touch in sys preferences). A quick google didn't turn up much, as far as others having issues goes.  I'm wondering if I have a dud!?  I'll have to call Wacom support (sent an email already) to trouble-shoot that before I'm any use for further testing I'm afraid! :(

I'll let you know when I have a working touch tablet for sure.

EDIT: just had a thought... I'll try installing it in my Windose VM - in Fusion on my Mac  ;)

---

### Post by dnprossi on 2009-11-12
Installed latest patches on Ubuntu Karmic Desktop **without udev** rules.
**0xd2** tablet.

All work as with previous patches, pen lifting issue is gone.

**No log changes for touch.**

The fdi and udev are not automatically copied have to do it manually. When testing on **Ubuntu Karmic Remix**, they were copied but last part of the fdi was missing. (probably thats why kgingeri had problems).

---

### Post by marek_online on 2009-11-12
Using the new patch, with a 0xd1.

Nothing from touch in /var/log/messages, but touch is mentioned in Xorg.0.log. I've attached a somewhat truncated Xorg.0.log along with other outputs (the full file is too big to attach, and just has more of the stylus messages that fill the end of the attached).

More problematic though, is that the eraser is no longer being recognised properly. I can draw with pressure in the GIMP, but switching to eraser doesn't change the drawing tool - it's being treated as the stylus. this happens in xournal also.

Sorry to be the bearer of bad news here. Something to do with the cursor position fix maybe?

---

### Post by GolemdX on 2009-11-12
Where can I find which device I have? This thread was made approximately 2 hours after I bought the tablet, so it's probably the latest version. I don't have it with me right now, but once I'm back I can test it again.

EDIT: Oh, and where are these logs I might be able to post? ...and how do I enable pressure in GIMP or InkScape?

---

### Post by marek_online on 2009-11-12
> Where can I find which device I have? This thread was made approximately 2 hours after I bought the tablet, so it's probably the latest version. I don't have it with me right now, but once I'm back I can test it again.Wacom released five different tablets at the same time.  To find out which one you have, run:
```
lsusb |grep Wacom
```The output will look something like this:
```
Bus 006 Device 002: ID 056a:00d1 Wacom Co., Ltd
```So my device is the 00d1 - the Pen & Touch variant. There's also version for just pen, just touch, fun pen & touch, and I think another one too.

> EDIT: Oh, and where are these logs I might be able to post? ...and how do I enable pressure in GIMP or InkScape?     The logs are /var/log/messages and /var/log/Xorg.0.log

The others will be able to tell you better, but the output to "lshal" and "xinput --list" seem to be useful sometimes too. It's mainly those two log files though, which can get quite big, so you may need to zip them to attach them to posts.

As for pressure - I'm not sure about InkScape, but in the GIMP, you need to configure your extended input devices.
Edit > Preferences > Input Devices > Configure Extended Input Devices 
Set stylus and eraser to "screen".

---

### Post by ehfortin on 2009-11-12
> **kgingeri said:**
> 
Now, I may have an issue with my 0xd1.  I decided I should be sure touch works, so I installed it with updated drivers on my Macbook and I get NO TOUCH there either.  OSX fully supports it (tablet buttons work fine, an there are all kinds of settings for touch in sys preferences). A quick google didn't turn up much, as far as others having issues goes.  I'm wondering if I have a dud!?  I'll have to call Wacom support (sent an email already) to trouble-shoot that before I'm any use for further testing I'm afraid! :(

I'll let you know when I have a working touch tablet for sure.

EDIT: just had a thought... I'll try installing it in my Windose VM - in Fusion on my Mac  ;)
Hi kgingeri,

On Windows, I have to "activate" touch. This is done by pressing the upper-left button. Then I have a large "Touch On" or "Touch Off" appearing on my display. Maybe it is the same on the Mac?

I doubt this is a hardware switch as I can change the definition of the button to something else in the drivers (always on Windows). However, I'm always trying it when doing the touch testing on Linux, just in case. I try touch, press the button, try touch again, press the button again and try touch a last time. This way I'm sure I've tested all conditions.

Hope this help.

ehfortin

---

### Post by rebecca2525 on 2009-11-12
Hi there!

Got me a brand new CTH-611 (works like a charm under Vista) and want to join testing. I'm using Debian Testing, actually, but normally Ubuntu and Debian are similar enough.

My first problem is that I can't find a download for linuxwacom-0.8.5-1, only for 0.8.5-3. The direct link in the first post doesn't work either. I can try to check out the 0.8.5-1 version from cvs though.

---

### Post by dnprossi on 2009-11-12
> 
More problematic though, is that the eraser is no longer being recognised properly. I can draw with pressure in the GIMP, but switching to eraser doesn't change the drawing tool - it's being treated as the stylus. this happens in xournal also


Confirm eraser functionality not there anymore on gimp, mypaint. Same stylus functionality for tip and top(eraser).

---

### Post by Ayuthia on 2009-11-12
> **rebecca2525 said:**
> Hi there!

Got me a brand new CTH-611 (works like a charm under Vista) and want to join testing. I'm using Debian Testing, actually, but normally Ubuntu and Debian are similar enough.

My first problem is that I can't find a download for linuxwacom-0.8.5-1, only for 0.8.5-3. The direct link in the first post doesn't work either. I can try to check out the 0.8.5-1 version from cvs though.
Welcome to the forums!  I hope that it was not too hard to find this post.  I saw your message in the linuxwacom-discuss mailing list, but for some reason, I am unable to reply to that group.

I am going to be building the patches for 0.8.5-3 in a little bit.  The linuxwacom site doesn't always keep their previous releases.

If you want to start patching with the 0.8.5-1 while I am making the patches for 0.8.5-3, you can download the source over [here]("http://linuxfans.keryxproject.org/packages/wacom/archive/linuxwacom-0.8.5-1.tar.bz2").

---

### Post by Ayuthia on 2009-11-12
> **dnprossi said:**
> Confirm eraser functionality not there anymore on gimp, mypaint. Same stylus functionality for tip and top(eraser).

Ok.  What I think I will do is build the next set of patches to contain only the changes that Pierre Chambart made.  His patches were for the 0xD2.

If they work with just those patches applied, we will build the next set of patches from there.

---

### Post by kgingeri on 2009-11-12
> **ehfortin said:**
> Hi kgingeri,

On Windows, I have to "activate" touch. This is done by pressing the upper-left button. Then I have a large "Touch On" or "Touch Off" appearing on my display. Maybe it is the same on the Mac?

I doubt this is a hardware switch as I can change the definition of the button to something else in the drivers (always on Windows). However, I'm always trying it when doing the touch testing on Linux, just in case. I try touch, press the button, try touch again, press the button again and try touch a last time. This way I'm sure I've tested all conditions.

Hope this help.

ehfortin

Thx Ehfortin, yeah Mac is the same but it makes no difference.  Button does trigger a pop-up msg re touch on/off tho.

I can't configure inside a Fusion Windows VM either as VMware treats the mouse differently from other USB devices  :(  A call to Wacom is required.

---

### Post by kgingeri on 2009-11-12
> **dnprossi said:**
> ...

The fdi and udev are not automatically copied have to do it manually. When testing on **Ubuntu Karmic Remix**, they were copied but last part of the fdi was missing. (probably thats why kgingeri had problems).

Thanks for the heads-up on this one Dnprossi!

EDIT: BTW I seem to been having hot-plug issues also - need several modprobe's and unplug replug - haven't recognized a pattern yet.  Haven't been able to check eraser - not sure I triedd it last time.

---

### Post by Favux on 2009-11-12
Hi everyone,

Probably a good thing to go to 0.8.5-3.  0.8.5-1 had a bug in some of the new code, maybe in the "Validate tool type before adding it. Use struct input_id and struct input_absinfo in wcmUSB.c. - for kernel cross version compatibility support."  Anyway 0.8.5-3 fixed it and now Gimp recognizes my eraser as different from my stylus tip again.  It sounds like some of you may have been having the same problem.

---

### Post by Ayuthia on 2009-11-12
> **dnprossi said:**
> 

The fdi and udev are not automatically copied have to do it manually. When testing on **Ubuntu Karmic Remix**, they were copied but last part of the fdi was missing. (probably thats why kgingeri had problems).

The fdi is not being installed automatically into /usr/share/hal/fdi/policy/20thirdparty?  The makefile script in src/util appears to say that it will do it.

---

### Post by dnprossi on 2009-11-12
> **Ayuthia said:**
> The fdi is not being installed automatically into /usr/share/hal/fdi/policy/20thirdparty?  The makefile script in src/util appears to say that it will do it.

On ubuntu desktop karmic with latest updates when installed patches this morning there was no 10-linuxwacom.fdi in the /usr/share/hal/fdi/policy/20thirdparty. Could not figure out why. I will reinstall and see if I can spot issue. Same for udev file nothing there.
 I'll try now...

[COLOR="Red"]EDIT!!![/COLOR]
If I reinstall from my batch file the fdi and udev are not copied.
If I reinstall in terminal one line at a time it does create /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi file and the lib/udev/rules.d/40-xserver-xorg-input-wacom.rules correctly.
Don't know why!!!

The auto-installed fdi will disable stylus pressure I cut and paste from your post [#28]("http://ubuntuforums.org/showpost.php?p=8289576&postcount=28") reboot and pen pressure is back.

I removed lib/udev/rules.d/40-xserver-xorg-input-wacom.rules everything works the same.

---

### Post by Ayuthia on 2009-11-12
As Favux stated earlier, 0.8.5-3 is now out.  This means that 0.8.5-1 is no longer available from their site.  I have updated the patch to only contain changes from Pierre Chambert.

Please test and see if the pen and eraser work.  If this works, we will move this over to the stable post and then start our work with the touch.

The patches are in the first post and the instructions have been updated to reflect the change.

---

### Post by rebecca2525 on 2009-11-12
> **Ayuthia said:**
> I saw your message in the linuxwacom-discuss mailing list, but for some reason, I am unable to reply to that group.
It seems you are not the only one.

> If you want to start patching with the 0.8.5-1 while I am making the patches for 0.8.5-3, you can download the source over [here]("http://linuxfans.keryxproject.org/packages/wacom/archive/linuxwacom-0.8.5-1.tar.bz2").Thanks a lot, this is a great help!

Just in case other Debian users are reading this, I had a small issue compiling the wacom driver [which I solved]("http://sourceforge.net/mailarchive/message.php?msg_name=20091111230322.6fbe7e18%40zam559"). Also, it isn't possible to remove the xserver-xorg-input-wacom due to dependencies (basically, xorg depends on it...), so as a temporary "solution", I moved all the files that package installs to a backup directory.

Compile and install went fine (had to copy the udev rule and the fdi file manually), and after a reboot (with the tablet plugged in), the pen function works!\\:D/ I tried it in MyPaint, and I have pressure sensitivity, the upper pen button works as right mouse click and the lower pen button can be used to scroll the canvas when the pen hovers over the tablet, which is exactly the same behaviour as in Vista. Can't say anything about the eraser since that didn't work in MyPaint in Vista either, so I guess that's MyPaint's problem. Will do some further testing later.

EDIT: I just saw the new patch, my above applies to the older patch I downloaded a few hours ago. Will test the new one later.

---

### Post by Ayuthia on 2009-11-12
> **rebecca2525 said:**
> It seems you are not the only one.

Thanks a lot, this is a great help!

Just in case other Debian users are reading this, I had a small issue compiling the wacom driver [which I solved]("http://sourceforge.net/mailarchive/message.php?msg_name=20091111230322.6fbe7e18%40zam559"). Also, it isn't possible to remove the xserver-xorg-input-wacom due to dependencies (basically, xorg depends on it...), so as a temporary "solution", I moved all the files that package installs to a backup directory.

Compile and install went fine (had to copy the udev rule and the fdi file manually), and after a reboot (with the tablet plugged in), the pen function works!\\:D/ I tried it in MyPaint, and I have pressure sensitivity, the upper pen button works as right mouse click and the lower pen button can be used to scroll the canvas when the pen hovers over the tablet, which is exactly the same behaviour as in Vista. Can't say anything about the eraser since that didn't work in MyPaint in Vista either, so I guess that's MyPaint's problem. Will do some further testing later.

EDIT: I just saw the new patch, my above applies to the older patch I downloaded a few hours ago. Will test the new one later.

That is great to hear!  There is someone who sent me a PM that was trying to install it in Debian so I forwarded your instructions.  

Can you let us know which model tablet you have?  I just want to see if we can confirm that all the Bamboo Pen and Touch versions work with this change.

---

### Post by dnprossi on 2009-11-12
Ayuthia,

about wacom-tools xserver-xorg-input-wacom purging you should see these links on previous post...

[#564]("http://ubuntuforums.org/showpost.php?p=8265799&postcount=564")
[#566]("http://ubuntuforums.org/showpost.php?p=8265946&postcount=566")
[#579]("http://ubuntuforums.org/showpost.php?p=8270211&postcount=579")

Installing 0.8.5-3 patch: error
```
patch -p1 < wcmConfig.c.patch
bash: wcmConfig.c.patch: No such file or directory

```

Nothing working... No tablet...

---

### Post by rebecca2525 on 2009-11-12
My model is a CTH-661, lsusb reports it as [I]ID 056a:00d3 Wacom Co., Ltd

[/I]Selecting stuff (like text) while dragging the pen on the tablet also works, as does dragging selected stuff around. Single clicks via tapping with the pen on the tablet work too.
Going to test the new driver+patch now.

---

### Post by rebecca2525 on 2009-11-12
> **dnprossi said:**
> about wacom-tools xserver-xorg-input-wacom purging you should see these links on previous post...

Yeah, same problem as on Debian (xserver-xorg depends on xserver-xorg-input-all which depends on xserver-xorg-input-wacom). The files I removed manually will be back as soon as there's an update for xserver-xorg-input-wacom... In the threads you linked people said removing xserver-xorg-input-wacom isn't necessary.

---

### Post by Favux on 2009-11-12
Has anyone tried just purging wacom-tools in Karmic?  That would at least reduce the risk of a conflict.

---

### Post by dnprossi on 2009-11-12
> **rebecca2525 said:**
> Yeah, same problem as on Debian (xserver-xorg depends on xserver-xorg-input-all which depends on xserver-xorg-input-wacom). The files I removed manually will be back as soon as there's an update for xserver-xorg-input-wacom... In the threads you linked people said removing xserver-xorg-input-wacom isn't necessary.

Purging will get rid of too many dependencies making the install unstable so i tried not to purge anything and when installing patches these overwrite all needed files. Plus this way i also got rid of lib/udev/rules.d/40-xserver-xorg-input-wacom.rules.

wacom-tools can be purged!! I don't but can be...

---

### Post by Ayuthia on 2009-11-12
> **dnprossi said:**
> Ayuthia,

about wacom-tools xserver-xorg-input-wacom purging you should see these links on previous post...

[#564]("http://ubuntuforums.org/showpost.php?p=8265799&postcount=564")
[#566]("http://ubuntuforums.org/showpost.php?p=8265946&postcount=566")
[#579]("http://ubuntuforums.org/showpost.php?p=8270211&postcount=579")

Installing 0.8.5-3 patch: error
```
patch -p1 < wcmConfig.c.patch
bash: wcmConfig.c.patch: No such file or directory

```

Nothing working... No tablet...

It should have been fdi.patch instead of wcmConfig.c.patch.  I was not able to find anything to change in that source this time.  Hopefully the issue with no tablet is because the .fdi file was not updated.

---

### Post by rebecca2525 on 2009-11-12
```
patch -p1 < fdi.patch
patching file src/util/10-linuxwacom.fdi
Reversed (or previously applied) patch detected!  Assume -R? [n] 
```

---

### Post by dnprossi on 2009-11-12
> **Ayuthia said:**
> It should have been fdi.patch instead of wcmConfig.c.patch.  I was not able to find anything to change in that source this time.  Hopefully the issue with no tablet is because the .fdi file was not updated.

you have "patch -p1 < fdi.patch" twice in instructions 1st line and last of patches.

Nothing working. No tablet at all.

Went back to 0.8.5-1 works
reinstalled 0.8.5-3 nothing.

xorg.0.log detects tablet but no functionality.

fdi is updated...

---

### Post by rebecca2525 on 2009-11-12
> **dnprossi said:**
> you have "patch -p1 < fdi.patch" twice in instructions 1st line and last of patches.

D'oh, I could have seen that myself...

I installed the new patch, unplugged/replugged/rmmod'ed/modprobe'd, and all works like before. Is there an easy way to check if I am using the latest patch and not by accident the old one? Output in some logfiles or so?

Otherwise, double-clicking does work too, but the eraser functions as pressure-sensitive stylus in Gimp, MyPaint and xournal. Does anyone know if these applications are supposed to recognise the eraser as an eraser? I could check that in Vista, but probably not before saturday.

---

### Post by dnprossi on 2009-11-12
Eraser should work automatically in mypaint. in gimp you will have to turn your pen and select eraser from tool box so that it is assigned to stylus eraser.

I can't get anything to work. I'll have to try again.

---

### Post by marek_online on 2009-11-12
> **dnprossi said:**
> Eraser should work automatically in mypaint. in gimp you will have to turn your pen and select eraser from tool box so that it is assigned to stylus eraser.

I can't get anything to work. I'll have to try again.

I'm getting the same nothing. Have recompiled a couple of times to no avail.

---

### Post by Ayuthia on 2009-11-12
> **rebecca2525 said:**
> D'oh, I could have seen that myself...

I installed the new patch, unplugged/replugged/rmmod'ed/modprobe'd, and all works like before. Is there an easy way to check if I am using the latest patch and not by accident the old one? Output in some logfiles or so?

Otherwise, double-clicking does work too, but the eraser functions as pressure-sensitive stylus in Gimp, MyPaint and xournal. Does anyone know if these applications are supposed to recognise the eraser as an eraser? I could check that in Vista, but probably not before saturday.

You can check in /var/log/messages and once you start using the pen, there should be messages in there with [wacom-10] data: 

If it shows [wacom-9], you are using the older version.

---

### Post by Ayuthia on 2009-11-12
> **marek_online said:**
> I'm getting the same nothing. Have recompiled a couple of times to no avail.

Can you and dnprossi both edit src/2.6.28/wacom_wac.c?  Go to line 924 where the code looks like:
```
void wacom_init_input_dev(struct input_dev *input_dev, struct wacom_wac *wacom_wac)
{
        switch (wacom_wac->features->type) {
                case WACOM_MO:
                        input_dev_mo(input_dev, wacom_wac);
                case WACOM_G4:
                        input_dev_g4(input_dev, wacom_wac);
                        /* fall through */
                case BAMBOO_PT:
                case GRAPHIRE:
                        input_dev_g(input_dev, wacom_wac);
                        break;

```
and change it to look like:
```
void wacom_init_input_dev(struct input_dev *input_dev, struct wacom_wac *wacom_wac)
{
        switch (wacom_wac->features->type) {
                case BAMBOO_PT:
                case WACOM_MO:
                        input_dev_mo(input_dev, wacom_wac);
                case WACOM_G4:
                        input_dev_g4(input_dev, wacom_wac);
                        /* fall through */
                case GRAPHIRE:
                        input_dev_g(input_dev, wacom_wac);
                        break;

```

Pierre Chambert's change has the devices starting at input_dev_g instead of input_dev_mo.  There is also some other code changes in 0.8.5-3 that removed some lines here.

So once those changes are made, you can recompile the code.  If that works, I will make the updates for everyone to test again.  If it does not work, please post the /var/log/messages log so that we can see if the wacom kernel module is loaded properly.

EDIT: If you are not comfortable with making the change yourself, let me know.  I can make the update also.  I am trying to reduce the number of changes if this does not make the device work.

---

### Post by Ayuthia on 2009-11-12
> **rebecca2525 said:**
> D'oh, I could have seen that myself...


Sorry.  I should have been paying closer attention.

I have updated the post and have removed the wacom.h.patch also.  It was an empty patch so it does not really do anything.

---

### Post by rebecca2525 on 2009-11-12
Booted into Vista and tried MyPaint 0.7.1 again. There, the eraser works as a stylus as well. I wanted to install Gimp, too, but I couln't reach sourceforge. I'm starting to believe it's IE's fault, but that will have to wait until saturday. I would like to know if I can get the eraser working in Vista to make sure it's not a hardware problem.

Now that I booted Linux again, I'm having the same nothingness as others, so I guess I was still using the old version before. Trying the patch for the patch right now...

---

### Post by dnprossi on 2009-11-12
Ayuthia,

Before changing source i discovered that pen works sporadically when plug/unplug.

see my messages.log towards end i plugged unplugged.

tried also after changing code, same happens.

reading the log pen seems to have worked for a while.

---

### Post by rebecca2525 on 2009-11-12
I changed the source (and this time, I rebooted after the install), and I have the same problem as dnprossi. When I plug the tablet in and use the pen, I get a few lines in /var/log/messages, then nothing more until the next plug out/in.

```
Nov 12 23:33:15 zam559 kernel: [  359.748070] usb 6-1: new full speed USB device using uhci_hcd and address 4
Nov 12 23:33:15 zam559 kernel: [  359.911999] usb 6-1: New USB device found, idVendor=056a, idProduct=00d3
Nov 12 23:33:15 zam559 kernel: [  359.912025] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 12 23:33:15 zam559 kernel: [  359.912031] usb 6-1: Product: CTH-661
Nov 12 23:33:15 zam559 kernel: [  359.912035] usb 6-1: Manufacturer: Wacom Co.,Ltd.
Nov 12 23:33:15 zam559 kernel: [  359.912210] usb 6-1: configuration #1 chosen from 1 choice
Nov 12 23:33:15 zam559 kernel: [  359.915270] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input19
Nov 12 23:33:15 zam559 kernel: [  359.927384] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input20
Nov 12 23:33:15 zam559 kernel: [  359.969911] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 23:33:15 zam559 kernel: [  359.973917] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 23:33:15 zam559 kernel: [  360.021896] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 23:33:15 zam559 kernel: [  360.025892] [wacom-10] data:  0:2 1:f0 2:64 3:21 4:3c 5:21 6:0 7:0
Nov 12 23:33:15 zam559 kernel: [  360.033896] [wacom-10] data:  0:2 1:f1 2:5e 3:21 4:3c 5:21 6:b7 7:1
Nov 12 23:33:15 zam559 kernel: [  360.061876] [wacom-10] data:  0:2 1:f1 2:60 3:21 4:36 5:21 6:c1 7:1
Nov 12 23:33:15 zam559 kernel: [  360.093858] [wacom-10] data:  0:2 1:f1 2:62 3:21 4:35 5:21 6:95 7:1
Nov 12 23:33:15 zam559 kernel: [  360.097864] [wacom-10] data:  0:2 1:f1 2:6d 3:21 4:36 5:21 6:91 7:1
```I don't see any reaction of the pointer, though, maybe it stops working too soon for me to see anything.

---

### Post by Ayuthia on 2009-11-12
I just had some time to review Pierre Chambert's code and found out that there is no coding for the eraser.  I am going to add it.

However, the first issue appears to be with the connection of the device.  Does /var/log/messages always report a "must rebind"?

---

### Post by marek_online on 2009-11-12
Even less success here. After making the edit, I still get no response from the tablet at all.  /var/log/messages has this:

```
Nov 12 22:59:08 Childers kernel: [  155.376610] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input14
```

But xinput --list --short is this:
```
"Virtual core pointer"  id=0    [XPointer]
"Virtual core keyboard" id=1    [XKeyboard]
"Sleep Button"  id=2    [XExtensionKeyboard]
"Video Bus"     id=3    [XExtensionKeyboard]
"Power Button"  id=4    [XExtensionKeyboard]
"AT Translated Set 2 keyboard"  id=5    [XExtensionKeyboard]
"DELL DELL USB Keyboard"        id=6    [XExtensionKeyboard]
"Foxlink Webcam"        id=7    [XExtensionKeyboard]
"Macintosh mouse button emulation"      id=8    [XExtensionPointer]
"ImExPS/2 Generic Explorer Mouse"       id=9    [XExtensionPointer]
"Logitech Optical USB Mouse"    id=10   [XExtensionPointer]
"Wacom Bamboo P&T 4x5"  id=11   [XExtensionPointer]
```

No stylus or eraser mentioned.

---

### Post by dnprossi on 2009-11-12
> **Ayuthia said:**
> I just had some time to review Pierre Chambert's code and found out that there is no coding for the eraser.  I am going to add it.

However, the first issue appears to be with the connection of the device.  Does /var/log/messages always report a "must rebind"?

On each connect in messages "must rebind" is reported.

following is from xorg.0.log at each recconnect.

```

(II) config/hal: removing device Wacom Bamboo Craft
(II) Wacom Bamboo Craft: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Wacom Bamboo Craft
(**) Wacom Bamboo Craft: always reports core events
(**) Wacom Bamboo Craft: Device: "/dev/input/event9"
(II) Wacom Bamboo Craft: Found 10 mouse buttons
(II) Wacom Bamboo Craft: Found scroll wheel(s)
(II) Wacom Bamboo Craft: Found x and y absolute axes
(II) Wacom Bamboo Craft: Found absolute touchpad
(II) Wacom Bamboo Craft: Configuring as touchpad
(**) Wacom Bamboo Craft: YAxisMapping: buttons 4 and 5
(**) Wacom Bamboo Craft: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Wacom Bamboo Craft" (type: TOUCHPAD)
(**) Wacom Bamboo Craft: (accel) keeping acceleration scheme 1
(**) Wacom Bamboo Craft: (accel) filter chain progression: 2.00
(**) Wacom Bamboo Craft: (accel) filter stage 0: 20.00 ms
(**) Wacom Bamboo Craft: (accel) set acceleration profile 0
(II) Wacom Bamboo Craft: initialized for absolute axes.
(II) config/hal: Adding input device eraser
(EE) PreInit returned NULL for "eraser"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device pad
(EE) PreInit returned NULL for "pad"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device touch
(EE) PreInit returned NULL for "touch"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device stylus
(EE) PreInit returned NULL for "stylus"
(EE) config/hal: NewInputDeviceRequest failed (8)

```

Sorry all, in italy its late. I'll be back in morning.
cheers!

---

### Post by kgingeri on 2009-11-12
I have hardware issues. My tablet does not have touch on my son's Vista machine either!  Bummer!!  Back to the store for another one.  :(

Thx Marek_online. I really like 'xinput --list --short'.  Really needa read man pages more often! ;)

Haven't tried 5-3 with your code change Ayuthia. I'll do that now and report back with an EDIT in this post.

EDIT: posted below instead

---

### Post by Ayuthia on 2009-11-12
kgingeri - Sorry to catch you while testing but I wanted to send out a patch before I head out for a meeting.

I have updated the patch files.  Can we try it without the fdi.patch for this one and see if we can get any connection with the tablet?  If you can't then add the fdi.patch and recompile.

I have added the eraser and I also added some debug statements.  I think that we are running into the 0x80 code issues again where the pen loses contact.

The patches are found at the first post.

---

### Post by kgingeri on 2009-11-12
> **Ayuthia said:**
> kgingeri - Sorry to catch you while testing but I wanted to send out a patch before I head out for a meeting.

I have updated the patch files.  Can we try it without the fdi.patch for this one and see if we can get any connection with the tablet?  If you can't then add the fdi.patch and recompile.

I have added the eraser and I also added some debug statements.  I think that we are running into the 0x80 code issues again where the pen loses contact.

The patches are found at the first post.

No prob.  I did test thought and gather results so for what they are worth, they are attached  ;)

I'll redo - without the fdi.patch  :)

EDIT/UPDATE:  Same results.  Did not patch the 10-linuxwacom.fdi file and removed the previous before my 'make install'.  Did get the unpatched one in /usr/share/... but still nothing in Xorg.0.log - tablet is dead, nothing  :(

---

### Post by Ayuthia on 2009-11-12
Can someone try testing out the patch in the first post again?  I incorporated the int variables together because I ran into issues with that format in other kernel modules.  I have also commented out the data information for the time being just to make sure it is not causing the crash.

---

### Post by kgingeri on 2009-11-12
Will do Ayuthia.

I also just returned from the store with a tablet that has touch!  :D
It was definitely a hardware issue as it works fine on my Mac.

Ah - back in the game to win  ;)

EDIT/UPDATE:  Ok this is what I am getting in Xorg.0.log...

```
(II) Wacom Bamboo P&T 4x5: initialized for absolute axes.
(II) config/hal: Adding input device eraser
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-3 $
(EE) PreInit returned NULL for "eraser"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device pad
(EE) PreInit returned NULL for "pad"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device touch
(EE) PreInit returned NULL for "touch"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device stylus
(EE) PreInit returned NULL for "stylus"
(EE) config/hal: NewInputDeviceRequest failed (8)
```

I did patch and install the 10-linuxwacom.fdi this time, right?

Oh - I didn't actually reboot.  I will try that and report back.

EDIT: Ok reboot didn't help.  Here's wacom in /proc/bus/input/devices
```
I: Bus=0003 Vendor=056a Product=00d1 Version=0106
N: Name="Wacom Bamboo P&T 4x5"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input11
U: Uniq=
H: Handlers=mouse4 event11 
B: EV=f
B: KEY=1c43 0 70000 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 3000003

I: Bus=0003 Vendor=056a Product=00d1 Version=0106
N: Name="Wacom Bamboo P&T 4x5"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input12
U: Uniq=
H: Handlers=mouse5 event12 
B: EV=f
B: KEY=1c43 0 70000 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 3000003
```

Xorg.0.log had this Wacom info:
```
(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-3 $
(EE) PreInit returned NULL for "stylus"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device touch
(EE) PreInit returned NULL for "touch"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device pad
(EE) PreInit returned NULL for "pad"
(EE) config/hal: NewInputDeviceRequest failed (8)
...
(II) config/hal: Adding input device Wacom Bamboo P&T 4x5
(**) Wacom Bamboo P&T 4x5: always reports core events
(**) Wacom Bamboo P&T 4x5: Device: "/dev/input/event12"
(II) Wacom Bamboo P&T 4x5: Found 3 mouse buttons
(II) Wacom Bamboo P&T 4x5: Found scroll wheel(s)
(II) Wacom Bamboo P&T 4x5: Found x and y absolute axes
(II) Wacom Bamboo P&T 4x5: Found absolute touchpad
(II) Wacom Bamboo P&T 4x5: Configuring as touchpad
(**) Wacom Bamboo P&T 4x5: YAxisMapping: buttons 4 and 5
(**) Wacom Bamboo P&T 4x5: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Wacom Bamboo P&T 4x5" (type: TOUCHPAD)
(**) Wacom Bamboo P&T 4x5: (accel) keeping acceleration scheme 1
(**) Wacom Bamboo P&T 4x5: (accel) filter chain progression: 2.00
(**) Wacom Bamboo P&T 4x5: (accel) filter stage 0: 20.00 ms
(**) Wacom Bamboo P&T 4x5: (accel) set acceleration profile 0
(II) Wacom Bamboo P&T 4x5: initialized for absolute axes.
```

Interesting how it configures a 'absolute touchpad' but then adds a device also - maybe the first is the stylus touchpad?

---

### Post by Ayuthia on 2009-11-12
> **kgingeri said:**
> Will do Ayuthia.

I also just returned from the store with a tablet that has touch!  :D
It was definitely a hardware issue as it works fine on my Mac.

Ah - back in the game to win  ;)

EDIT/UPDATE:  Ok this is what I am getting in Xorg.0.log...

```
(II) Wacom Bamboo P&T 4x5: initialized for absolute axes.
(II) config/hal: Adding input device eraser
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-3 $
(EE) PreInit returned NULL for "eraser"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device pad
(EE) PreInit returned NULL for "pad"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device touch
(EE) PreInit returned NULL for "touch"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device stylus
(EE) PreInit returned NULL for "stylus"
(EE) config/hal: NewInputDeviceRequest failed (8)
```

I did patch and install the 10-linuxwacom.fdi this time, right?

Oh - I didn't actually reboot.  I will try that and report back.

That was a quick replacement!  Can you see if the wacom kernel module is not repeatedly trying to reload in /var/log/messages?  Thanks.

---

### Post by kgingeri on 2009-11-12
> **Ayuthia said:**
> That was a quick replacement!  Can you see if the wacom kernel module is not repeatedly trying to reload in /var/log/messages?  Thanks.

Ha - I'm getting good at this  ;)
I get this from dmesg...
```
dmesg|tail -30
[   21.407768] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   23.307773] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   23.315772] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   23.351772] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   23.359770] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   24.143773] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   24.147770] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   24.155771] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
[   26.316203] CPU0 attaching NULL sched-domain.
[   26.316218] CPU1 attaching NULL sched-domain.
[   26.337179] CPU0 attaching sched-domain:
[   26.337191]  domain 0: span 0-1 level SIBLING
[   26.337200]   groups: 0 1
[   26.337218] CPU1 attaching sched-domain:
[   26.337226]  domain 0: span 0-1 level SIBLING
[   26.337234]   groups: 1 0
[   52.444798] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[   53.394555] wlan0: authenticate with AP 08:10:74:12:83:7c
[   53.398819] wlan0: authenticated
[   53.398832] wlan0: associate with AP 08:10:74:12:83:7c
[   53.401595] wlan0: RX AssocResp from 08:10:74:12:83:7c (capab=0x411 status=0 aid=2)
[   53.401607] wlan0: associated
[   53.405417] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   63.860030] wlan0: no IPv6 routers present
[   80.008154] usb 2-2: USB disconnect, address 3
[   87.192098] usb 2-2: new low speed USB device using uhci_hcd and address 4
[   87.374868] usb 2-2: configuration #1 chosen from 1 choice
[   87.411193] input: Microsoft Compact Optical Mouse 500 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input16
[   87.411404] generic-usb 0003:045E:0737.0005: input,hidraw0: USB HID v1.11 Mouse [Microsoft Compact Optical Mouse 500] on usb-0000:00:1d.0-2/input0
[  139.398668] ath5k phy0: unsupported jumbo
```

EDIT: BTW when I replace, I wipe both linuxwacom and wcm_patch directories untar and apply patches etc.  I didn't remove fdi or udev files and I did patch everything.

---

### Post by kgingeri on 2009-11-12
Ayuthia, the whole section with [Wacom-10] is this...
```
Nov 12 21:49:09 kgulnb kernel: [    8.767876] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input15
Nov 12 21:49:11 kgulnb kernel: [   10.724141] ppdev: user-space parallel port driver
Nov 12 21:49:21 kgulnb kernel: [   21.395753] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:21 kgulnb kernel: [   21.403775] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:21 kgulnb kernel: [   21.407768] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:23 kgulnb kernel: [   23.307773] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:23 kgulnb kernel: [   23.315772] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:23 kgulnb kernel: [   23.351772] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:23 kgulnb kernel: [   23.359770] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:24 kgulnb kernel: [   24.143773] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:24 kgulnb kernel: [   24.147770] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:24 kgulnb kernel: [   24.155771] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0
Nov 12 21:49:53 kgulnb kernel: [   52.444798] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
```

Left other lines for context purposes.

EDIT:  Hey I like that packet format :D

---

### Post by Ayuthia on 2009-11-12
> **kgingeri said:**
> Ha - I'm getting good at this  ;)
I get this from dmesg...
```
dmesg|tail -30
[   21.407768] [wacom-10] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0

```

EDIT: BTW when I replace, I wipe both linuxwacom and wcm_patch directories untar and apply patches etc.  I didn't remove fdi or udev files and I did patch everything.

Can you try the newer patch?  We have been running into problems with version 10 where the kernel module kept reloading.

---

### Post by kgingeri on 2009-11-12
Just a note to everyone about touch on the CTH-460 tablet.  If touch is working the white LED get brighter as you touch (this didn't happen on my dud tablet).  Also a reminder that if the stylus is turning the LED red, touch will have NO effect.  The stylus over-rides touch internally.

---

### Post by kgingeri on 2009-11-12
> **Ayuthia said:**
> Can you try the newer patch?  We have been running into problems with version 10 where the kernel module kept reloading.

Not sure I know what you mean.  I downloaded from post #1 just before recompiling and testing?

EDIT: file info is '3314 Nov 12 21:38 wcm_patch.0.8.5-3.tar.bz' - I will try again...

---

### Post by Ayuthia on 2009-11-12
> **kgingeri said:**
> Not sure I know what you mean.  I downloaded from post #1 just before recompiling and testing?

Post #1 should have wacom_wac.c showing
#define PATCH 12

From your /var/log/messages, it is showing [wacom-10] instead of [wacom-12].

By the way, when you say that the pen overrides the touch, does that mean that if you start with the touch in Linux it might report until you switch over to the pen?  I was also noticing that in earlier posts it sounds like there is a button to turn on the touch.  Is that correct?

---

### Post by kgingeri on 2009-11-12
> **Ayuthia said:**
> Post #1 should have wacom_wac.c showing
#define PATCH 12

From your /var/log/messages, it is showing [wacom-10] instead of [wacom-12].

By the way, when you say that the pen overrides the touch, does that mean that if you start with the touch in Linux it might report until you switch over to the pen?  I was also noticing that in earlier posts it sounds like there is a button to turn on the touch.  Is that correct?

Ok - I just re-downloaded from post #1 and I am getting PATCH 10!  Wait a second... My bad, duh!  I had another tab open with that post sitting in it from a while ago and was downloading from it - an old link!!! :redface:
EDIT: [COLOR="Red"]BEWARE! I have Firefox set to reload prev tabs but it must use cached data, cuz even after a reboot I was downloading from an old link[/COLOR]

OK - will do it right this time!

Yes, if you are using touch and then use the stylus, the stylus will over ride touch.  This is a hardware feature I believe, so if you rest your hand on the pad and then use the stylus your hand doesn't interfere.

On the tablet a button can be assigned to turn touch on an off.  On my Mac and I expect Windows, you can assign that function to any one of the 4 buttons - so it is software driven.

---

### Post by kgingeri on 2009-11-12
Ok, got the right driver.  Here's what Xorg and messages has:
```
Nov 12 22:06:01 kgulnb kernel: [ 1020.871206] ath5k phy0: unsupported jumbo
Nov 12 22:37:25 kgulnb kernel: [ 2904.776079] usbcore: deregistering interface driver wacom
Nov 12 22:37:26 kgulnb kernel: [ 2905.857059] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input17
Nov 12 22:37:26 kgulnb kernel: [ 2905.881351] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input18
Nov 12 22:37:26 kgulnb kernel: [ 2905.886688] usbcore: registered new interface driver wacom
Nov 12 22:37:26 kgulnb kernel: [ 2905.886703] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
Nov 12 22:37:26 kgulnb logger: device input17 is bound to the driver
Nov 12 22:37:26 kgulnb logger: must rebind
Nov 12 22:37:26 kgulnb logger: device input18 is bound to the driver
Nov 12 22:37:26 kgulnb logger: must rebind
```

Note the times 22:37...

Xorg.0.log shows about the same as before.
EDIT: Will try a reboot now too.

UPDATE: After reboot - I have this in Xorg.0.log:
```
(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-3 $
(EE) PreInit returned NULL for "stylus"
(EE) config/hal: NewInputDeviceRequest failed (8)
...
(II) config/hal: Adding input device Wacom Bamboo P&T 4x5
(**) Wacom Bamboo P&T 4x5: always reports core events
(**) Wacom Bamboo P&T 4x5: Device: "/dev/input/event12"
(II) Wacom Bamboo P&T 4x5: Found 3 mouse buttons
(II) Wacom Bamboo P&T 4x5: Found scroll wheel(s)
(II) Wacom Bamboo P&T 4x5: Found x and y absolute axes
(II) Wacom Bamboo P&T 4x5: Found absolute touchpad
(II) Wacom Bamboo P&T 4x5: Configuring as touchpad
(**) Wacom Bamboo P&T 4x5: YAxisMapping: buttons 4 and 5
(**) Wacom Bamboo P&T 4x5: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Wacom Bamboo P&T 4x5" (type: TOUCHPAD)
(**) Wacom Bamboo P&T 4x5: (accel) keeping acceleration scheme 1
(**) Wacom Bamboo P&T 4x5: (accel) filter chain progression: 2.00
(**) Wacom Bamboo P&T 4x5: (accel) filter stage 0: 20.00 ms
(**) Wacom Bamboo P&T 4x5: (accel) set acceleration profile 0
(II) Wacom Bamboo P&T 4x5: initialized for absolute axes.

```

Messages has:
```
Nov 12 22:46:01 kgulnb kernel: [    6.825451] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input11
Nov 12 22:46:01 kgulnb kernel: [    6.834993] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input12
Nov 12 22:46:01 kgulnb kernel: [    6.845535] usbcore: registered new interface driver wacom
Nov 12 22:46:01 kgulnb kernel: [    6.845549] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
```

No debug data from Xorg.0.log tho

EDIT: xinput has this tho!
```
# xinput --list --short
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
"Acer Crystal Eye webcam"	id=3	[XExtensionKeyboard]
"Sleep Button"	id=4	[XExtensionKeyboard]
"Power Button"	id=5	[XExtensionKeyboard]
"Video Bus"	id=6	[XExtensionKeyboard]
"Power Button"	id=7	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=8	[XExtensionPointer]
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
"Microsoft Compact Optical Mouse 500"	id=10	[XExtensionPointer]
[COLOR="Red"]"Wacom Bamboo P&T 4x5"	id=11	[XExtensionPointer][/COLOR]
```

---

### Post by Ayuthia on 2009-11-12
> **kgingeri said:**
> Ok, got the right driver.  Here's what Xorg and messages has:
```
Nov 12 22:06:01 kgulnb kernel: [ 1020.871206] ath5k phy0: unsupported jumbo
Nov 12 22:37:25 kgulnb kernel: [ 2904.776079] usbcore: deregistering interface driver wacom
Nov 12 22:37:26 kgulnb kernel: [ 2905.857059] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input17
Nov 12 22:37:26 kgulnb kernel: [ 2905.881351] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input18
Nov 12 22:37:26 kgulnb kernel: [ 2905.886688] usbcore: registered new interface driver wacom
Nov 12 22:37:26 kgulnb kernel: [ 2905.886703] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
Nov 12 22:37:26 kgulnb logger: device input17 is bound to the driver
Nov 12 22:37:26 kgulnb logger: must rebind
Nov 12 22:37:26 kgulnb logger: device input18 is bound to the driver
Nov 12 22:37:26 kgulnb logger: must rebind
```

Note the times 22:37...

Xorg.0.log shows about the same as before.
EDIT: Will try a reboot now too.

UPDATE: After reboot - I have this in Xorg.0.log:
```
(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-3 $
(EE) PreInit returned NULL for "stylus"
(EE) config/hal: NewInputDeviceRequest failed (8)
...
(II) config/hal: Adding input device Wacom Bamboo P&T 4x5
(**) Wacom Bamboo P&T 4x5: always reports core events
(**) Wacom Bamboo P&T 4x5: Device: "/dev/input/event12"
(II) Wacom Bamboo P&T 4x5: Found 3 mouse buttons
(II) Wacom Bamboo P&T 4x5: Found scroll wheel(s)
(II) Wacom Bamboo P&T 4x5: Found x and y absolute axes
(II) Wacom Bamboo P&T 4x5: Found absolute touchpad
(II) Wacom Bamboo P&T 4x5: Configuring as touchpad
(**) Wacom Bamboo P&T 4x5: YAxisMapping: buttons 4 and 5
(**) Wacom Bamboo P&T 4x5: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Wacom Bamboo P&T 4x5" (type: TOUCHPAD)
(**) Wacom Bamboo P&T 4x5: (accel) keeping acceleration scheme 1
(**) Wacom Bamboo P&T 4x5: (accel) filter chain progression: 2.00
(**) Wacom Bamboo P&T 4x5: (accel) filter stage 0: 20.00 ms
(**) Wacom Bamboo P&T 4x5: (accel) set acceleration profile 0
(II) Wacom Bamboo P&T 4x5: initialized for absolute axes.

```

Messages has:
```
Nov 12 22:46:01 kgulnb kernel: [    6.825451] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input11
Nov 12 22:46:01 kgulnb kernel: [    6.834993] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input12
Nov 12 22:46:01 kgulnb kernel: [    6.845535] usbcore: registered new interface driver wacom
Nov 12 22:46:01 kgulnb kernel: [    6.845549] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
```

No debug data from Xorg.0.log tho

EDIT: xinput has this tho!
```
# xinput --list --short
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
"Acer Crystal Eye webcam"	id=3	[XExtensionKeyboard]
"Sleep Button"	id=4	[XExtensionKeyboard]
"Power Button"	id=5	[XExtensionKeyboard]
"Video Bus"	id=6	[XExtensionKeyboard]
"Power Button"	id=7	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=8	[XExtensionPointer]
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
"Microsoft Compact Optical Mouse 500"	id=10	[XExtensionPointer]
[COLOR="Red"]"Wacom Bamboo P&T 4x5"	id=11	[XExtensionPointer][/COLOR]
```

Is the pen responding with the evdev driver?  If so, then I can start looking at the X portion to see why it is not getting assigned properly.  By any chance do you know if hal-setup-wacom is getting installed?

---

### Post by kgingeri on 2009-11-12
> **Ayuthia said:**
> Is the pen responding with the evdev driver?  If so, then I can start looking at the X portion to see why it is not getting assigned properly.  By any chance do you know if hal-setup-wacom is getting installed?

No Ayuthia, no pen response.  How do I tell if hal-setup-wacom is getting installed - I have no clue.
EDIT: tried manually
```
# /usr/lib/hal/hal-setup-wacom
hal-setup-wacom: Failed to get UDI
```

I noticed that you are calling wacom_bamboo_pen_irq() instead of wacom_bamboo_pt_irq() in wacom_wac.c - is that on purpose?

---

### Post by Ayuthia on 2009-11-12
> **kgingeri said:**
> No Ayuthia, no pen response.  How do I tell if hal-setup-wacom is getting installed - I have no clue.

I noticed that you are calling wacom_bamboo_pen_irq() instead of wacom_bamboo_pt_irq() in wacom_wac.c - is that on purpose?

It is what Pierre Chambert called it and I have not changed it yet.  I was wanting to test out the code to see if it worked better than what we had and it seemed to be fine for 0.8.5-1 then when we moved to 0.8.5-3 it no longer worked.  I then started reviewing the code and found that it is pretty much what we have submitted except he did not use the 0x80 code (which we found has cause the stylus to not work) and then I noticed that there was no coding for the eraser.

As for hal-setup-wacom, it should be able to be found in /usr/lib/hal or /usr/libexec/hal.  Can you check the dates if you have both?  I am noticing that the most recent copy that I have is in /usr/libexec/hal, but the rest of the other hal data seems to be in /usr/lib/hal.

---

### Post by kgingeri on 2009-11-12
> **Ayuthia said:**
> It is what Pierre Chambert called it and I have not changed it yet.  I was wanting to test out the code to see if it worked better than what we had and it seemed to be fine for 0.8.5-1 then when we moved to 0.8.5-3 it no longer worked.  I then started reviewing the code and found that it is pretty much what we have submitted except he did not use the 0x80 code (which we found has cause the stylus to not work) and then I noticed that there was no coding for the eraser.

Ah, ok - I figured likely.  EDIT: I did try reinstating your _pt_ function but I get no response either.

> As for hal-setup-wacom, it should be able to be found in /usr/lib/hal or /usr/libexec/hal.  Can you check the dates if you have both?  I am noticing that the most recent copy that I have is in /usr/libexec/hal, but the rest of the other hal data seems to be in /usr/lib/hal.

```
# ls -l `locate hal-setup-wacom`
-rwxr-xr-x 1 root root  9632 Oct 14 19:05 /usr/lib/hal/hal-setup-wacom
-rwxr-xr-x 1 root root 16782 Nov 12 23:25 /usr/libexec/hal-setup-wacom
-rwxr-xr-x 1 root root 16782 Nov  7 00:27 /usr/local/libexec/hal-setup-wacom
```

Should I delete some - sym-link?

---

### Post by Ayuthia on 2009-11-13
> **kgingeri said:**
> Ah, ok - I figured likely.  EDIT: I did try reinstating your _pt_ function but I get no response either.



```
# ls -l `locate hal-setup-wacom`
-rwxr-xr-x 1 root root  9632 Oct 14 19:05 /usr/lib/hal/hal-setup-wacom
-rwxr-xr-x 1 root root 16782 Nov 12 23:25 /usr/libexec/hal-setup-wacom
-rwxr-xr-x 1 root root 16782 Nov  7 00:27 /usr/local/libexec/hal-setup-wacom
```

Should I delete some - sym-link?

I am thinking that the /usr/libexec/hal-setup-wacom is supposed to be in /usr/lib/hal.  You might want to make a backup of the one in /usr/lib/hal and symlink it to the one in /usr/libexec.  As for the one in /usr/local/libexec, I would either move it out or remove it.  I am thinking that might have come from an install where the --prefix was not used.

I am hoping that it will help it work, but I am thinking that there is something that we are missing in the 2.6.28 directory that is causing the kernel module to not stay bound.

---

### Post by Ayuthia on 2009-11-13
I was looking at this [link]("http://ubuntuforums.org/showthread.php?t=977708") and I see that there was a similar problem like this a while back and people had to reload the kernel module.  Have you tried this?

EDIT: I think this [bug]("http://bugs.gentoo.org/209263") explains the issue.  From what I can tell, the /lib/udev/check-driver is not installed (EDIT2: I guess the file is there on my system--forgot to update the locate database).  From Jaunty, I am finding this in that file:
```
#!/bin/sh
#

#logger check_driver called with: $1 - $2 - $3 -

wanted=$1
devpath=$2
bustype=$3

device=$(readlink /sys/$devpath/device)
device=${device##*/}
driver=$(readlink /sys/$devpath/device/driver)
driver=${driver##*/}

logger device $device is bound to the $driver driver

if [ "$driver" != "$wanted" ]; then
    logger must rebind
    echo -n "$device" > /sys/$devpath/device/driver/unbind
    echo -n "$device" > /sys/bus/$bustype/drivers/$wanted/bind
else
    logger no need to rebind
fi

```

---

### Post by kgingeri on 2009-11-13
> **Ayuthia said:**
> I was looking at this [link]("http://ubuntuforums.org/showthread.php?t=977708") and I see that there was a similar problem like this a while back and people had to reload the kernel module.  Have you tried this?

Ok, not getting any joy here at all Ayuthia.  I have tried reloading wacom - to no avail.

BTW This is what I did with hal-setup-wacom and then rebooted...
```
# ls -l `locate hal-setup-wacom `
lrwxrwxrwx 1 root root    28 Nov 13 00:17 /usr/lib/hal/hal-setup-wacom -> /usr/libexec/hal-setup-wacom
-rwxr-xr-x 1 root root 16782 Nov 13 00:24 /usr/libexec/hal-setup-wacom
```

> EDIT: I think this [bug]("http://bugs.gentoo.org/209263") explains the issue.  From what I can tell, the /lib/udev/check-driver is not installed (EDIT2: I guess the file is there on my system--forgot to update the locate database).  From Jaunty, I am finding this in that file:
...

I do not have stylus or any action from the tablet, at all.  I'll check out the above.  Funny, I went looking for xorg.conf in /etc/X11 and I don't have one - not even with updated locate!! I can't restart X as UNR comes with Option DontZap enabled.  I'll check out how to put it into the fdi file maybe.  I will also try rebooting and plugging in after - I've always left the tablet connected.  

I'll keep trying what I can but even the old 0.8.5-1 wacom.ko doesn't work now?  I may have forgotten to do a 'make install' - I'll try that again too.

EDIT: Oh, and I do have /lib/udev/check_driver - and it's the same as yours in Jaunty.
EDIT: Think I'm turning in for the night - I'll catch up tomorrow again

---

### Post by Ayuthia on 2009-11-13
> **kgingeri said:**
> 
I do not have stylus or any action from the tablet, at all.  I'll check out the above.  Funny, I went looking for xorg.conf in /etc/X11 and I don't have one - not even with updated locate!! I can't restart X as UNR comes with Option DontZap enabled.  I'll check out how to put it into the fdi file maybe.  I will also try rebooting and plugging in after - I've always left the tablet connected.  

You will need to modify /usr/share/hal/fdi/policy/10osvendor/10-x11-input.fdi and update the "input.keys" section to look like:
```

    <match key="info.capabilities" contains="input.keys">
      <!-- If we're using Linux, we use evdev by default (falling back to
           keyboard otherwise). -->
      <merge key="input.x11_driver" type="string">keyboard</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name"
             string="Linux">
        <merge key="input.xkb.options" type="string">terminate:ctrl_alt_bksp</merge>
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
    </match>

```

I am debating about going back to 0.8.4-3 where we know that it is stable.  If we are not able to get this going in 0.8.5-3, I will start creating patches for both until we are able to get some progress with the 0.8.5-X version.  

Please let me know your thoughts on this.

---

### Post by kgingeri on 2009-11-13
> **Ayuthia said:**
> You will need to modify /usr/share/hal/fdi/policy/10osvendor/10-x11-input.fdi and update the "input.keys" section to look like:
```

    <match key="info.capabilities" contains="input.keys">
      <!-- If we're using Linux, we use evdev by default (falling back to
           keyboard otherwise). -->
      <merge key="input.x11_driver" type="string">keyboard</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name"
             string="Linux">
        <merge key="input.xkb.options" type="string">terminate:ctrl_alt_bksp</merge>
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
    </match>

```

Well I think the key binding is ok, it's a matter of something like:
```
<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
        <merge key="input.x11_options.DebugLevel" type="string">12</merge>
        <merge key="input.x11_options.CommonDBG" type="string">12</merge>
        [COLOR="Red"]<merge key="input.x11_options.DontZap" type="boolean">off</merge>[/COLOR]
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">pad</append>
          <append key="wacom.types" type="strlist">touch</append>
      </match>
    </match>
  </device>
 ...
 
``` - not sure tho.

> I am debating about going back to 0.8.4-3 where we know that it is stable.  If we are not able to get this going in 0.8.5-3, I will start creating patches for both until we are able to get some progress with the 0.8.5-X version.

Yeah, it seems very strange we can't get anything.  I rebuilt for 0.8.5-1 and I have a stylus (evdev) which means no selection, stylus buttons etc.

Now that I have a working touch pad, I can be of more assistance.  :)

ALso, I noticed in one the links to a thread you gave, some xsetwacom command that might be useful for setting the tablet buttons - once we get that far... sample is...
```
# Button <  set to + (Zoom in)
xsetwacom set pad Button1 "core key +"
# Button FN1  set to - (Zoom out)
xsetwacom set pad Button2 "core key -"
# Button > to Ctrl Z (undo)
xsetwacom set pad Button3 "core key ctrl y"
# Button FN2 to Ctrl Y (redo)
xsetwacom set pad Button4 "core key ctrl z"
```

Ok, I'm done for the day... or yesterday now, I guess  ;)

EDIT: Oops, forgot to mention - no touch data seen in dmesg with version 0.8.5-1.  I'll try 0.8.4-3 later today (after some sleep) and see if I see any.

---

### Post by dnprossi on 2009-11-13
Good Morning Ayuthia, 
I went through all posts i missed last night and tried all. Also reinstalling kernel but nothing except for many:
```

(II) config/hal: Adding input device Wacom Bamboo Craft cursor
(EE) PreInit returned NULL for "Wacom Bamboo Craft cursor"
(EE) config/hal: NewInputDeviceRequest failed (8)

```
in xorg.log that were not there in 0.8.5-3 first patches.

> **Ayuthia said:**
> 
I am debating about going back to 0.8.4-3 where we know that it is stable.  If we are not able to get this going in 0.8.5-3, I will start creating patches for both until we are able to get some progress with the 0.8.5-X version.  

Please let me know your thoughts on this.

0.8.5-1 was only missing eraser functionality rest seemed to be fine why not continue from there?? Why do you think of going back to 0.8.4-3??

I reinstalled 0.8.5-1 and [COLOR="Red"]if done correctly[/COLOR] + reboot:

**0.8.5-1** in MyPaint:                           
Stylus: **OK**
Stylus Buttons: **OK**
Tilting: **OK**
Eraser: **[COLOR="Red"]NONE[/COLOR]**
Touch: **[COLOR="Red"]NONE[/COLOR]**
Touch Buttons: **[COLOR="Red"]NONE[/COLOR]**

**0.8.4-3** in MyPaint:
Stylus: **OK**
Stylus Buttons: **OK**
Tilting: **OK**
Eraser: **OK**
Touch: **[COLOR="Red"]NONE[/COLOR]**
Touch Buttons: **[COLOR="Red"]NONE[/COLOR]**

Other issue is to check the [COLOR="Red"]auto-created fdi[/COLOR] that does give issues like **no pressure** in gimp and others. Pasting the test fdi **pressure is back**.

Thanks for your great work,
cheers....

---

### Post by rebecca2525 on 2009-11-13
> 0.8.5-1 was only missing eraser functionality rest seemed to be fine why not continue from there?? Why do you think of going back to 0.8.4-3??I agree, except for the eraser I had all pen functionality with 0.8.5-1.

> Tilting: **OK**This might be a stupid question, but what do you mean by that?

---

### Post by dnprossi on 2009-11-13
> **rebecca2525 said:**
> 
This might be a stupid question, but what do you mean by that?

:) Hi Rebecca2525,
Some applications like git-downloaded MyPaint have stylus tilt input to which different paint functions are assigned. Eg. select a solid brush start painting with pen up-right then tilt and pen will start smudging..

Nifty!!!

---

### Post by rebecca2525 on 2009-11-13
> **dnprossi said:**
> :) Hi Rebecca2525,
Some applications like git-downloaded MyPaint have stylus tilt input to which different paint functions are assigned. Eg. select a solid brush start painting with pen up-right then tilt and pen will start smudging..
Wow, I will have to look out for that.

---

### Post by Ayuthia on 2009-11-13
We can try going from 0.8.5-1.  I have no problem with that.  One concern is that 0.8.5-X is shifting enough that we lose stability at times so we might not have a good patch to submit.  However, I am sure that it is easier to patch to the newer 0.8.5-X version once ours is ready.  

I will update the first post later today to reflect the change back to 0.8.5-1 for now.  Since 0.8.5-1 is no longer available, I will keep a copy of it at [linuxfans.keryxproject.org]("http://linuxfans.keryxproject.org/packages/wacom/archive/linuxwacom-0.8.5-1.tar.bz2").

So the next release today will be reverting back to 0.8.5.-1 and I will add the eraser back to the code also.

---

### Post by dnprossi on 2009-11-13
> **Ayuthia said:**
> We can try going from 0.8.5-1.  I have no problem with that.  One concern is that 0.8.5-X is shifting enough that we lose stability at times so we might not have a good patch to submit.  However, I am sure that it is easier to patch to the newer 0.8.5-X version once ours is ready.  

Ayuthia, hope you did not consider my above message as an imposition it just was a thought. I really don't know about loosing stability things, so it's all up to you. By a user point of view the 0.8.5-1 patch is doing a good job but really do not know if it is the best solution on your side.

> 
I will update the first post later today to reflect the change back to 0.8.5-1 for now.  Since 0.8.5-1 is no longer available, I will keep a copy of it at [linuxfans.keryxproject.org]("http://linuxfans.keryxproject.org/packages/wacom/archive/linuxwacom-0.8.5-1.tar.bz2").

So the next release today will be reverting back to 0.8.5.-1 and I will add the eraser back to the code also.


what ever decision you make... Ready for testing...:)

---

### Post by kgingeri on 2009-11-13
Ayuthia, not sure which is best.  My only thought may be if we do stick to 0.8.5-1 then maybe we are closer to getting it working in 0.8.5-3.  However, just getting it working and understanding the code and functionality also has merit.  Like Dnprossi, I'm with you which ever way you decide.  You're d'man! ;)

---

### Post by Ayuthia on 2009-11-13
I have no preference one way or the other so we are going to go back to 0.8.5-1.  I have updated the first post so that it goes back to the previous version.  It does add the eraser functionality so let us know if the eraser works and also if the stylus falls out of contact and does not come back (unless you put the pen on the pad and remove it twice).

I have also placed a pre-patched source file at linuxfans.keryxproject.org.  The information for the package is also in the first post.  Please let me know if the instructions get too confusing.  Feel free to use either version since they should be the same.

Like the other times, please post the Xorg.0.log and /var/log/messages file.  It will help me see what is happening.  Thanks!

---

### Post by marek_online on 2009-11-13
Thanks Ayuthia.

I have stylus back, but the same problem as before as regard the eraser - it's just picked up as the stylus.

Logs attached.

---

### Post by Ayuthia on 2009-11-13
> **marek_online said:**
> Thanks Ayuthia.

I have stylus back, but the same problem as before as regard the eraser - it's just picked up as the stylus.

Logs attached.

I just looked at your logs and it is showing that you are using version 10.  We should be at 13 now.

Are you using the patches in the first post or the pre-patch source?

---

### Post by dnprossi on 2009-11-13
**Tadaaa!!!**

Ayuthia, all works like a charm.

I had to change **fdi** with the one on post [#28]("http://ubuntuforums.org/showpost.php?p=8289576&postcount=28") **to get pressure to work** for 0xd2 and removed /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules

0.8.5-1 in MyPaint, GIMP:
Stylus: **OK**
Stylus Buttons:**OK**
MyPaint Tilting: **OK**
Eraser: [COLOR="Red"]**OK**[/COLOR] 
Touch: **NONE**
Touch Buttons: **NONE**

Plug/Unplug: [COLOR="Red"]**OK**[/COLOR]

---

### Post by ehfortin on 2009-11-13
> **kgingeri said:**
> 
On the tablet a button can be assigned to turn touch on an off.  On my Mac and I expect Windows, you can assign that function to any one of the 4 buttons - so it is software driven.

Yurk... I'm the one that talked about the turn on/turn off feature and I didn't get it then. While rereading your post, I just realized that maybe the reason we don't get any data from touch is because the damn feature is off by default... So for the model that was touch only (no pen), it would always be on which would explain why we had somebody that had it working for some time at beginning (at least, if I recall correctly).

Yes the on/off feature can be mapped to any button on the tablet but we don't know if it is on or off once initialized by the driver. Maybe the Windows/Mac driver is initializing it as on but... if the hardware is in idle mode by default (which would make sense to be the pen mode as it's what Wacom was doing first), we may be looking for data that we won't see coming until we figure how to activate the feature.

It's just a thought. Is there anyway to get access to the information directly from Wacom? I was under the impression they were involved in the linux wacom project so if there is some specific information needed, they should pass it on to help.

What do you think? Is it possible that's the situation we are getting into?


ehfortin

---

### Post by ehfortin on 2009-11-13
> **dnprossi said:**
> **Tadaaa!!!**

Ayuthia, all works like a charm.

I had to change **fdi** with the one on post [#28]("http://ubuntuforums.org/showpost.php?p=8289576&postcount=28") **to get pressure to work** for 0xd2 and removed /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules

0.8.5-1 in MyPaint, GIMP:
Stylus: **OK**
Stylus Buttons:**OK**
MyPaint Tilting: **OK**
Eraser: [COLOR=Red]**OK**[/COLOR] 
Touch: **NONE**
Touch Buttons: **NONE**

That's with 0.8.5-1, right? I know that's what is beside "in MyPaint, GIMP" but as it may be a cut&paste from the previous email, I just want to make sure it is not on 0.8.5-3 as I'm heading to build the most recent working solution.

Thanks.

ehfortin

---

### Post by dnprossi on 2009-11-13
Hi ehfortin,

Yes it is 0.8.5-1 with the new patches on post #1...
I used the ones I already had and downloaded new patches but Ayuthia prepatched 0.8.5-1 on his linuxfans.keryxproject.org download.


Also: **Plug/Unplug: [COLOR="Red"]OK[/COLOR]**

---

### Post by rebecca2525 on 2009-11-13
Works, with eraser! 

**0.8.5.1 patch 13, model CTH-661 (ID 056a:00d3)**

STYLUS

Pressure sensitivity: OK
Buttons (2): OK
Select/Drag with stylus down: OK
Single/double tap: OK
Pan with hovering stylus and lower button: OK
Tilt: ? (have no app that supports it yet)


ERASER

Pressure sensitivity: OK
Buttons (2): OK
Select/Drag with stylus down: OK
Single/double tap: OK
Pan with hovering stylus and lower button: OK
Tilt: ? (have no app that supports it yet)


TOUCH

no


TABLET BUTTONS

no


PLUG/UNPLUG

OK



=D>

---

### Post by marek_online on 2009-11-13
> I just looked at your logs and it is showing that you are using version 10.  We should be at 13 now.

Are you using the patches in the first post or the pre-patch source? 	

I was using the pre-patch source. Used linuxwacom-0.8.5-1  and the patches in the first post and I have stylus and eraser working with pressure again.

Excellent!

---

### Post by rebecca2525 on 2009-11-13
I'm using the pre-patched source, and have patch 13 as it should be; so it's not a problem of the pre-patched source.

---

### Post by kgingeri on 2009-11-13
> **ehfortin said:**
> Yurk... I'm the one that talked about the turn on/turn off feature and I didn't get it then. While rereading your post, I just realized that maybe the reason we don't get any data from touch is because the damn feature is off by default... So for the model that was touch only (no pen), it would always be on which would explain why we had somebody that had it working for some time at beginning (at least, if I recall correctly).

Yes the on/off feature can be mapped to any button on the tablet but we don't know if it is on or off once initialized by the driver. Maybe the Windows/Mac driver is initializing it as on but... if the hardware is in idle mode by default (which would make sense to be the pen mode as it's what Wacom was doing first), we may be looking for data that we won't see coming until we figure how to activate the feature.

It's just a thought. Is there anyway to get access to the information directly from Wacom? I was under the impression they were involved in the linux wacom project so if there is some specific information needed, they should pass it on to help.

What do you think? Is it possible that's the situation we are getting into?


ehfortin

Good think'n Ehfortin!!  You could be onto something there.  Someone should look back at posts to see if it was a touch-only tablet!  (come on... I am at work still ya know, and shouldn't looking at this ;)

I'll try to dig around on my Mac and see if I can find any log or other info that might help.  Touch IS ON by default.

I seem to recall there is a way to determine the xsetwacom commands - man page maybe?  It may not support touch tho?  :(

---

### Post by rebecca2525 on 2009-11-13
But the LEDs on the tablet blink as if everything is working allright. Just saying, dunno if that means anything.

I can always boot into Vista and look for anything that might be of help. I'm a bit of a Windows noob, though, so if anyone has any suggestions where to look...

EDIT: xsetwacom has no man page, but seems to be aware of touch:

> $ xsetwacom list dev
eraser     eraser
touch     touch
stylus     stylusEDIT 2: playing around with xsetwacom...
> $ xsetwacom list param | grep -i touch
Touch            - Turns on/off Touch events (default is enable/on). 
Gesture          - Turns on/off Touch Gesture (default is enable/on). 
Capacity         - Touch sensitivity level (default is 3, -1 for none capacitive tools). 
$ xsetwacom get touch Touch
0
$ xsetwacom set touch Touch 1
$ xsetwacom get touch Touch
1Nothing in /var/log/messages though about the touch, regardless what value I set with xsetwacom. xorg log shows:
> xf86WcmChangeControl: dev touch set 0x9 to 0x1
xf86WcmChangeControl: dev touch set 0x9 to 0x0You can use "on" (=1) and "off" (=0)as values, too

---

### Post by Ayuthia on 2009-11-13
> **kgingeri said:**
> Good think'n Ehfortin!!  You could be onto something there.  Someone should look back at posts to see if it was a touch-only tablet!  (come on... I am at work still ya know, and shouldn't looking at this ;)

I'll try to dig around on my Mac and see if I can find any log or other info that might help.  Touch IS ON by default.

I seem to recall there is a way to determine the xsetwacom commands - man page maybe?  It may not support touch tho?  :(

Come on and play!!!  I am sure that you won't get caught!  :p

I don't recall having anyone that had a Bamboo Touch in here so far.

Does the Mac have /dev/input/eventX to view the output?  My guess that it does not.  If someone has a USB sniffer in Windows we would be able to see what is being sent over to the device.

I have asked Ping about how to turn on the touch data but it seems that Wacom is not ready to release that information yet.

---

### Post by kgingeri on 2009-11-13
> **rebecca2525 said:**
> But the LEDs on the tablet blink as if everything is working allright. Just saying, dunno if that means anything.
Yup always do - whether enabled or not
> EDIT: xsetwacom has no man page, but seems to be aware of touch:

EDIT 2: playing around with xsetwacom...
Nothing in /var/log/messages though about the touch, regardless what value I set with xsetwacom. xorg log shows:
You can use "on" and "off" as values, too

So have you tried touch after:
```
$ xsetwacom set touch Touch 1
```

> xf86WcmChangeControl: dev touch set 0x9 to 0x1

0x1 = true = on
0x0 = false = off

...so try touch after you see "dev touch set 0x9 to 0x1" in Xorg.0.log!! :)

---

### Post by rebecca2525 on 2009-11-13
> **kgingeri said:**
> ...so try touch after you see "dev touch set 0x9 to 0x1" in Xorg.0.log!! :)
Yeah, tried that, no reaction in /var/log/messages :(
 
USB sniffer... *googles*
 
EDIT: It's late over here, will continue tomorrow.

---

### Post by dnprossi on 2009-11-13
Ok I was on windows trying to get data from tablet...

Here are three short text files one with activating the touch and the other deactivating it and one with movement.

Device monitoring studio... Totally unclear for me hope they are for you...

I'll try more apps...

EDIT!! to start/stop touch on windows I had to press (having tablet buttons on left) the topmost button...

---

### Post by Ayuthia on 2009-11-13
> **dnprossi said:**
> Ok I was on windows trying to get data from tablet...

Here are three short text files one with activating the touch and the other deactivating it and one with movement.

Device monitoring studio... Totally unclear for me hope they are for you...

I'll try more apps...

EDIT!! to start/stop touch on windows I had to press (having tablet buttons on left) the topmost button...

Well, the good news is that the moving data looks like what TheguywholikesLINUX has reported in Linux before.  I want to say that he did not get the .fdi file working correctly when he reported the data so it might have been possible that the evdev driver triggered something.

When we receive the 0x80 data (the pen is not in range), is your palm on the pad?  I am guessing that the 0x80 is for the palm.  When the finger is on the pad, it will report 0x81 (once we figure out how to grab the touch data).

Is that possible?

The information for the button seems like it is missing something.  I will need to think about it.

---

### Post by dnprossi on 2009-11-13
> **Ayuthia said:**
> 
When we receive the 0x80 data (the pen is not in range), is your palm on the pad?  I am guessing that the 0x80 is for the palm.  When the finger is on the pad, it will report 0x81 (once we figure out how to grab the touch data).


I get the following in windows:
0x82 = finger or palm on pad
0x81 = pen tip

not getting 0x80

[COLOR="Red"]EDIT!![/COLOR]
sending more info before sleep!!!

This is data dumped from USBlyzer - seems more complete

That's it for now... i'll be back tomorrow...
cheers!!

---

### Post by ehfortin on 2009-11-13
Hi,

I was looking at the most recent version of the linuxwacom driver directly from CVS (which has been updated a few hours ago). It seems that Ping is in the middle of major transformation. I wanted to see if I was able to port our modification to this code but... some of the structure we are using are not even there in the new version. I'm under the impression the code is being cleaned up and generic functions are replacing multiple specific functions which add a lot of validation here and there.

Otherwise said, it will be a major part of fun to get our changes back in the source. I would think that Ping will be the best placed to "convert" our code to the new structure as we probably recreate/reuse stuff that was already existing in some form before.

I would say we are stuck with 0.8.5-1 for now (which work pretty well on the stylus part with the most recent patch as everybody reported already). Maybe that working part should be transmitted to Ping so he at least give his feedback on the best way to integrate this in latest source and our work should concentrate in making the touch part talking (don't know if we could use menace to achieve our goal? ;) )

Let the game continue :)

ehfortin

---

### Post by kgingeri on 2009-11-13
Ayuthia, did you notice that finger data from Dnprossi's data had a length of **_20_** as opposed to 9!!!  Our structure definitions are for 9 ...

wacom_wac.c has...
```
#define WACOM_PKGLEN_BBFUN       9
...
    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-460
    { "Wacom Bamboo Craft",       WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-461/S
    { "Wacom Bamboo P&T 6x8",     WACOM_PKGLEN_BBFUN,     21648, 13530, 1023, 63, BAMBOO_PT }, // CTH-661
```

...remeber the structure def from wacom_wac.h is...
```
struct wacom_features {
        char *name;
        int pktlen;
        int x_max;
        int y_max;
        int pressure_max;
        int distance_max;
        int type;
        int touch_x_res;
        int touch_y_res;
        int touch_x_max;
        int touch_y_max;
        unsigned char unit;
        unsigned char unitExpo;
};
```

Could our problem be we are cutting off data?!

---

### Post by kgingeri on 2009-11-13
[SIZE="6"][COLOR="DarkGreen"]WHA-HOOOOO!  Looky this![/COLOR][/SIZE]
The blank line is after lifting my sylus and the next lines are finger!!

```
tail -f /var/log/messages
Nov 13 22:53:50 kgulnb kernel: [80010.950321] [wacom-13] data:  0:2 1:0 2:ff 3:81 4:b8 5:1 6:31 7:81 8:c2 9:1 10:30 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80010.974322] [wacom-13] data:  0:2 1:0 2:ff 3:81 4:b9 5:1 6:30 7:81 8:c2 9:1 10:30 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80010.990316] [wacom-13] data:  0:2 1:0 2:ff 3:81 4:b9 5:1 6:31 7:81 8:c2 9:1 10:30 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80011.014310] [wacom-13] data:  0:2 1:0 2:ff 3:81 4:c5 5:1 6:31 7:81 8:c3 9:1 10:30 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80011.034313] [wacom-13] data:  0:2 1:0 2:ff 3:81 4:cc 5:1 6:31 7:81 8:c5 9:1 10:31 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80011.054316] [wacom-13] data:  0:2 1:0 2:ff 3:81 4:cd 5:1 6:32 7:81 8:c9 9:1 10:32 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80011.074318] [wacom-13] data:  0:2 1:0 2:ff 3:81 4:ce 5:1 6:32 7:81 8:cb 9:1 10:32 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80011.094315] [wacom-13] data:  0:2 1:0 2:e0 3:81 4:d8 5:1 6:32 7:81 8:ce 9:1 10:32 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80011.110311] [wacom-13] data:  0:2 1:0 2:b9 3:81 4:d9 5:1 6:33 7:81 8:d1 9:1 10:33 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:53:50 kgulnb kernel: [80011.134316] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

Nov 13 22:54:30 kgulnb kernel: [80051.118327] [wacom-13] data:  0:2 1:0 2:8f 3:81 4:20 5:0 6:89 7:81 8:1f 9:0 10:86 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:30 kgulnb kernel: [80051.138315] [wacom-13] data:  0:2 1:0 2:a3 3:81 4:20 5:0 6:86 7:81 8:1f 9:0 10:84 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:30 kgulnb kernel: [80051.158320] [wacom-13] data:  0:2 1:0 2:a9 3:81 4:20 5:0 6:86 7:81 8:1f 9:0 10:83 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:30 kgulnb kernel: [80051.178325] [wacom-13] data:  0:2 1:0 2:a9 3:81 4:20 5:0 6:85 7:81 8:1e 9:0 10:82 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:30 kgulnb kernel: [80051.198320] [wacom-13] data:  0:2 1:0 2:ab 3:81 4:20 5:0 6:83 7:81 8:1e 9:0 10:81 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:30 kgulnb kernel: [80051.218321] [wacom-13] data:  0:2 1:0 2:ab 3:81 4:1f 5:0 6:7f 7:81 8:1e 9:0 10:7d 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:30 kgulnb kernel: [80051.234322] [wacom-13] data:  0:2 1:0 2:af 3:81 4:1f 5:0 6:7c 7:81 8:1e 9:0 10:7a 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.258320] [wacom-13] data:  0:2 1:0 2:bc 3:81 4:1e 5:0 6:75 7:81 8:1d 9:0 10:73 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.274318] [wacom-13] data:  0:2 1:0 2:c1 3:81 4:1e 5:0 6:71 7:81 8:1d 9:0 10:6e 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.298318] [wacom-13] data:  0:2 1:0 2:c0 3:81 4:1d 5:0 6:69 7:81 8:1c 9:0 10:67 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.314314] [wacom-13] data:  0:2 1:0 2:c1 3:81 4:1c 5:0 6:62 7:81 8:1b 9:0 10:5f 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.338316] [wacom-13] data:  0:2 1:0 2:ca 3:81 4:1c 5:0 6:5a 7:81 8:1b 9:0 10:59 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.354322] [wacom-13] data:  0:2 1:0 2:c0 3:81 4:1a 5:0 6:55 7:81 8:1a 9:0 10:53 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.374311] [wacom-13] data:  0:2 1:0 2:d7 3:81 4:19 5:0 6:49 7:81 8:18 9:0 10:47 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.394315] [wacom-13] data:  0:2 1:0 2:d4 3:81 4:17 5:0 6:43 7:81 8:17 9:0 10:42 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.414323] [wacom-13] data:  0:2 1:0 2:cb 3:81 4:15 5:0 6:39 7:81 8:13 9:0 10:36 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.434322] [wacom-13] data:  0:2 1:0 2:d1 3:81 4:15 5:0 6:33 7:81 8:13 9:0 10:31 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.454320] [wacom-13] data:  0:2 1:0 2:ce 3:81 4:13 5:0 6:2c 7:81 8:11 9:0 10:2b 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.474325] [wacom-13] data:  0:2 1:0 2:cf 3:81 4:11 5:0 6:2a 7:81 8:f 9:0 10:29 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.494320] [wacom-13] data:  0:2 1:0 2:e0 3:81 4:e 5:0 6:27 7:81 8:c 9:0 10:27 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.510318] [wacom-13] data:  0:2 1:0 2:e3 3:81 4:c 5:0 6:27 7:81 8:a 9:0 10:27 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.534318] [wacom-13] data:  0:2 1:0 2:f7 3:81 4:5 5:0 6:2a 7:81 8:4 9:0 10:28 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.550315] [wacom-13] data:  0:2 1:0 2:eb 3:80 4:fe 5:0 6:2d 7:80 8:fb 9:0 10:2b 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.574323] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:f5 5:0 6:31 7:80 8:f3 9:0 10:2f 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.590323] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:ed 5:0 6:34 7:80 8:ed 9:0 10:32 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.614318] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:e4 5:0 6:3f 7:80 8:e3 9:0 10:3e 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.630326] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:e0 5:0 6:43 7:80 8:df 9:0 10:41 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.650323] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:da 5:0 6:4a 7:80 8:da 9:0 10:47 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.670318] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:d8 5:0 6:4e 7:80 8:d8 9:0 10:4e 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.690321] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:d6 5:0 6:54 7:80 8:d4 9:0 10:53 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.710317] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:d6 5:0 6:56 7:80 8:d6 9:0 10:55 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.730323] [wacom-13] data:  0:2 1:0 2:fb 3:80 4:d8 5:0 6:59 7:80 8:d5 9:0 10:57 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.750314] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:d9 5:0 6:5c 7:80 8:d9 9:0 10:5a 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.770315] [wacom-13] data:  0:2 1:0 2:ff 3:80 4:dd 5:0 6:62 7:80 8:dc 9:0 10:62 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.786316] [wacom-13] data:  0:2 1:0 2:ed 3:80 4:e0 5:0 6:64 7:80 8:df 9:0 10:65 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.810316] [wacom-13] data:  0:2 1:0 2:ed 3:80 4:e7 5:0 6:6b 7:80 8:e5 9:0 10:69 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.826317] [wacom-13] data:  0:2 1:0 2:e2 3:80 4:ec 5:0 6:6d 7:80 8:e9 9:0 10:6b 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.850315] [wacom-13] data:  0:2 1:0 2:d3 3:80 4:f1 5:0 6:71 7:80 8:f1 9:0 10:6f 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.866318] [wacom-13] data:  0:2 1:0 2:d6 3:80 4:f8 5:0 6:73 7:80 8:f6 9:0 10:70 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.890322] [wacom-13] data:  0:2 1:0 2:d1 3:80 4:ff 5:0 6:73 7:80 8:fd 9:0 10:71 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.906316] [wacom-13] data:  0:2 1:0 2:c9 3:81 4:1 5:0 6:74 7:80 8:fe 9:0 10:71 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 22:54:31 kgulnb kernel: [80051.926325] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

```

I haven't looked close yet, but I had to post it right away.
I changed the buffer length to 20! and recompiled.

EDIT: ok, I'll settle down a bit and do more testing because X is not responding to my stylus - even tho I got this data.  Hope it's not false hope!!

Well even if the data is bogus, here is three finger taps - center, upper right and lower left.  My stylus is a yard away! (I pressed enter between each)
```
# tail -f /var/log/messages
Nov 13 23:01:18 kgulnb kernel: [80458.414369] [wacom-13] data:  0:2 1:0 2:5b 3:81 4:9 5:0 6:7b 7:81 8:4 9:0 10:76 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:18 kgulnb kernel: [80458.434365] [wacom-13] data:  0:2 1:0 2:88 3:81 4:8 5:0 6:79 7:81 8:7 9:0 10:76 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:18 kgulnb kernel: [80458.450367] [wacom-13] data:  0:2 1:0 2:97 3:81 4:8 5:0 6:79 7:81 8:7 9:0 10:76 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:18 kgulnb kernel: [80458.474375] [wacom-13] data:  0:2 1:0 2:95 3:81 4:8 5:0 6:79 7:81 8:7 9:0 10:75 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:18 kgulnb kernel: [80458.490373] [wacom-13] data:  0:2 1:0 2:8e 3:81 4:7 5:0 6:7a 7:81 8:7 9:0 10:75 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 23:01:18 kgulnb kernel: [80458.514369] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

Nov 13 23:01:25 kgulnb kernel: [80465.482369] [wacom-13] data:  0:2 1:0 2:4a 3:81 4:e0 5:0 6:16 7:81 8:e0 9:0 10:11 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:25 kgulnb kernel: [80465.498352] [wacom-13] data:  0:2 1:0 2:5c 3:81 4:e0 5:0 6:15 7:81 8:e0 9:0 10:15 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:25 kgulnb kernel: [80465.522371] [wacom-13] data:  0:2 1:0 2:5b 3:81 4:e0 5:0 6:17 7:81 8:e0 9:0 10:16 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:25 kgulnb kernel: [80465.538386] [wacom-13] data:  0:2 1:0 2:50 3:81 4:e0 5:0 6:1a 7:81 8:e0 9:0 10:18 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 23:01:25 kgulnb kernel: [80465.562376] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

Nov 13 23:01:27 kgulnb kernel: [80467.782374] [wacom-13] data:  0:2 1:0 2:46 3:80 4:0 5:1 6:2b 7:80 8:0 9:1 10:28 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:27 kgulnb kernel: [80467.798355] [wacom-13] data:  0:2 1:0 2:76 3:80 4:0 5:1 6:2a 7:80 8:0 9:1 10:28 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:27 kgulnb kernel: [80467.822368] [wacom-13] data:  0:2 1:0 2:6d 3:80 4:0 5:1 6:29 7:80 8:0 9:1 10:28 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0
Nov 13 23:01:27 kgulnb kernel: [80467.838369] [wacom-13] data:  0:2 1:0 2:45 3:80 4:0 5:1 6:2c 7:80 8:0 9:1 10:2a 11:0 12:0 13:0 14:0 15:0 16:80 17:11 18:0
Nov 13 23:01:27 kgulnb kernel: [80467.862371] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

```

---

### Post by kgingeri on 2009-11-13
Here are the 4 buttons also (with buffer length set to 20)!!!
```
Nov 13 23:06:13 kgulnb kernel: [80754.234408] [wacom-13] data:  0:2 1:1 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0
Nov 13 23:06:14 kgulnb kernel: [80754.518406] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

Nov 13 23:06:20 kgulnb kernel: [80760.338393] [wacom-13] data:  0:2 1:2 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0
Nov 13 23:06:20 kgulnb kernel: [80760.490408] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

Nov 13 23:06:22 kgulnb kernel: [80762.814411] [wacom-13] data:  0:2 1:4 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0
Nov 13 23:06:22 kgulnb kernel: [80762.990408] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0

Nov 13 23:06:25 kgulnb kernel: [80765.574407] [wacom-13] data:  0:2 1:8 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0
Nov 13 23:06:25 kgulnb kernel: [80765.726398] [wacom-13] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0
```

EDIT: Ha, simple - second byte bit positions 0,1,2 and 3 - all other values 0

EDIT: Weird - I am not getting stylus data now - hmmmmm :confused:
EDIT Only get data from stylus once after replugging, after that nothing.

---

### Post by kgingeri on 2009-11-13
Wow, everyone must actually be taking time for a social life around here.  I feel like a lonely geek ;)  :D

EDIT:Ok, so while I had a bit of time and am waiting for excitment re my find, I finally wrote a rebuild script.  Copy the code below into your favorite editor and save it as RebuildWacom (or whatever) and then issue a
"chmod a+x RebuildWacom" to make it executable.  Then issue "./RebuildWacom" to run it...
EDIT: or download the attached file

```
#!/bin/sh
#	RebuildWacom --- Wacom Tablet remake
#
# For an up to date copy, visit http://ubuntuforums.org/showpost.php?p=8313047&postcount=145
#
export SVER=$(ls -1d linuxwacom*bz2 | awk 'END {print substr($0,12,7)}')
export PVER=$(ls -1d wcm_patch*bz2 | awk 'END {print substr($0,19,2)}')
#
clear
echo -n "
Linux Wacom Testing Builder

Enter linuxwacom version or press enter for [$SVER]: "; read VER
if test "$VER" != "" ; then SVER=$VER; fi
#
echo -n "Enter patch level or press enter for [$PVER]: "; read VER
if test "$VER" != "" ; then PVER=$VER; fi
#
echo -n "
This script is set to rebuild for:
  LinuxWacom version: linuxwacom-$SVER
   Wcm_patch version: wcm_patch-$SVER-$PVER

"
#
export SRC_DIR=linuxwacom-$SVER
export SRC_TAR=$SRC_DIR.tar.bz2
export PCH_DIR=wcm_patch-$SVER
export PCH_TAR=$PCH_DIR-$PVER.tar.bz2
#
if ! test -f $SRC_TAR; then
  echo "
	ERROR! Source archive not found!
	       You must be in the directory containing $SRC_TAR and $PCH_TAR!
"
  exit
fi
echo -n "Press [Enter] to rebuild LinuxWacom -or- used Ctrl+C to quit! "; read DMY
echo "Removing existing source...
"
#
rm -rf ./$PCH_DIR/ ./$SRC_DIR/
echo -n "
Done - press [Enter] for next step: "; read DMY
#
echo "Unarchiving a fresh copyi of source...
"
tar xvjf ./$SRC_TAR
tar xvjf ./$PCH_TAR
echo -n "
Done - press [Enter] for next step: "; read DMY
#
echo "Patching...
"
cp $PCH_DIR/*.patch ./$SRC_DIR
cd $SRC_DIR
for FILE in *.patch; do patch -p1 <$FILE; done
echo -n "
Done - press [Enter] for next step: "; read DMY
#
echo "Doing configurations...
"
if test -f Makefile ; then
  make clean
  make distclean
fi
./configure --enable-wacom --prefix=/usr
echo -n "
Done - press [Enter] for next step: "; read DMY
#
echo "Compiling (watch for stopped errors)...
"
make
echo -n "
Done - press [Enter] for next step: "; read DMY
#
echo "Installing (watch for stopped errors)...
"
sudo make install
echo -n "
Done - press [Enter] for next step: "; read DMY
#
echo "Installing/updating kernel modules (should be no output)...
"
sudo cp src/2.6.28/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
sudo modprobe -r wacom
sudo modprobe wacom
echo -n "
Done - press [Enter] for next step: "; read DMY
#
echo "Copying Udev file in place (should be no output)...
"
sudo cp src/util/60-wacom.rules /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
#
echo "
All done. Copy in any special 10-linuxwacom.fdi files /usr/share/hal/fdi/policy/20thirdparty/ 
sand then you MUST reboot to test properly.
"
```

Oh yeah, it does actually work - I use it  ;)

---

### Post by Favux on 2009-11-14
Hi kgingeri,

Nonsense.  I had my social life and have been back home for an hour!  They're just passed out.

So can you separate the buffer length to 9 for the stylus/eraser and 20 for the pad and touch in the code?

Ha!  Gali98 wrote a python script to download and compile linuxwacom and Ping posted it.

---

### Post by Ayuthia on 2009-11-14
> **kgingeri said:**
> Wow, everyone must actually be taking time for a social life around here.  I feel like a lonely geek ;)  :D

I was actually catching up on some shows for the week.  Nothing better than recording shows with MythTV.

So you are now no longer able to get the stylus to work?  It sounds like we need to figure out how to "flip" that switch.  It could be possible that whatever was used last (and working) is what is retained in the next session.  Do you recall if you used the touch last on your Mac?

As for the record length, I saw the same information as you did.  I am thinking that we might need to somehow split the two so that we can handle the data properly.

I think that we may also have someone that has a Bamboo Touch so we might be able to grab some of the kernel data from that device and build the code around that information.  That would then leave us with figuring out how to switch between the two.

The touch data is supposed to be coming from the other event so it might not be that bad.

---

### Post by kgingeri on 2009-11-14
Aaahhh - I'm not alone after all  ;)

Yeah, Ayuthia, Favux just posted before you wondering about seperating the buffer length per device.  I wonder if it is necessary OR if some of the data IS the length (that's the way a lot of protocols work!)

I don't really think the button on/off is effecting us yet.  Xsetwacom implies that it is ON by default and until we can turn it OFF, we'll have data.  The device has no way of saving state - I know - I took my other one apart, in case I could see something obvious and fix it :D (which I couldn't) 

I've been looking at the data to to see if I can decipher anything data wise and nothing jumps out at me. So I don't know.

As for my stylus; I have no idea what's happening.  I am not sure I have ever had 0.8.5-1 seeing my stylus on Karmic UNR yet!!  I still have a copy of 0.8.5-1 I tried and I downloaded yours also [COLOR="DimGray"](tar files where a different size!)[/COLOR] but neither give me stylus.  I am leaving the udev file in place tho I know dnprossi likes to blow it away?  [COLOR="DimGray"]EDIT: Nope sorry I was looking at your prepatched tar file vs unpatched.  I guess I over-wrote my previous.  I still have it backed up tho too[/COLOR]
Any suggestions?!  

EDIT: You know, I not following my own advise and rebooting.  Think I'll do that right now and see if it helps.  It hasn't in the past tho.

---

### Post by kgingeri on 2009-11-14
> **Favux said:**
> Ha!  Gali98 wrote a python script to download and compile linuxwacom and Ping posted it.

Ha Favux, yeah mine assumes you've downloaded and installed all prerequisites so it's only a rebuild.  

As for social life, I'm glad some have their priorities right :p

---

### Post by Ayuthia on 2009-11-14
> **kgingeri said:**
> Aaahhh - I'm not alone after all  ;)

Yeah, Ayuthia, Favux just posted before you wondering about seperating the buffer length per device.  I wonder if it is necessary OR if some of the data IS the length (that's the way a lot of protocols work!)

I don't really think the button on/off is effecting us yet.  Xsetwacom implies that it is ON by default and until we can turn it OFF, we'll have data.  The device has no way of saving state - I know - I took my other one apart, in case I could see something obvious and fix it :D (which I couldn't) 

I've been looking at the data to to see if I can decipher anything data wise and nothing jumps out at me. So I don't know.

As for my stylus; I have no idea what's happening.  I am not sure I have ever had 0.8.5-1 seeing my stylus on Karmic UNR yet!!  I still have a copy of 0.8.5-1 I tried and I downloaded yours also [COLOR="DimGray"](tar files where a different size!)[/COLOR] but neither give me stylus.  I am leaving the udev file in place tho I know dnprossi likes to blow it away?  [COLOR="DimGray"]EDIT: Nope sorry I was looking at your prepatched tar file vs unpatched.  I guess I over-wrote my previous.  I still have it backed up tho too[/COLOR]
Any suggestions?!  

EDIT: You know, I not following my own advise and rebooting.  Think I'll do that right now and see if it helps.  It hasn't in the past tho.

Have you taken a look at /var/log/Xorg.0.log to see which event the device is connecting?

EDIT: By the way, the data that you posted for the finger--is that just one finger or multiple?

---

### Post by kgingeri on 2009-11-14
> **Ayuthia said:**
> ...
I think that we may also have someone that has a Bamboo Touch so we might be able to grab some of the kernel data from that device and build the code around that information.  That would then leave us with figuring out how to switch between the two.

The touch data is supposed to be coming from the other event so it might not be that bad.

Yup a Touch-only device would certainly help - I think I've got enough for now tho :lol:  (not that I think you were implying anything)

Ok, more seriously - Your right - it should be coming from the other event.  What about other tablets?  Maybe we should look thru existing code for how that's handled, or are these tablet unique that way?

BTW:  I am not getting touch either anymore!!  I should have saved that last rebuild!!!  I'll see if I can revert.

---

### Post by kgingeri on 2009-11-14
> **Ayuthia said:**
> Have you taken a look at /var/log/Xorg.0.log to see which event the device is connecting?

EDIT: By the way, the data that you posted for the finger--is that just one finger or multiple?

I'll look into messages - in fact I'll safeguard a copy!

Just one finger. and very quick taps - no dragging or other jestures.

---

### Post by kgingeri on 2009-11-14
Ok, I think you guys were already ahead on me on this one.

First, let me say that rebooting between builds IS DEFINITELY NECESSARY!
All worked fine after a reboot. Stylus wise and dmesg data.

Second, I again modified packet length to 20 and sure enough, I get data logging in dmesg (or /var/log/messages)!  :D  Of course I then do not get stylus action or data logging with this mod.  It is either one or the other.

Soooo... what's the next step?!

I think I may go dig into code for a while - well, until I fall asleep a least :)

BTW, a big thanks to Dnprossi for the effort to install a USB sniffer and for that data!

EDIT: here's the Xorg info Ayuthia, with the buffer @ 20 and touch data.  Not sure it's what your looking for?
```
Nov 14 01:05:58 kgulnb kernel: [    6.915200] udev: starting version 147
Nov 14 01:05:58 kgulnb kernel: [    7.152869] lp: driver loaded but no devices found
Nov 14 01:05:58 kgulnb kernel: [    7.166178] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input11
Nov 14 01:05:58 kgulnb kernel: [    7.176157] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input12
Nov 14 01:05:58 kgulnb kernel: [    7.181872] usbcore: registered new interface driver wacom
Nov 14 01:05:58 kgulnb kernel: [    7.181885] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
```
I'll also do some gesture stuff and post it here too...

---

### Post by Favux on 2009-11-14
```
First, let me say that rebooting between builds IS DEFINITELY NECESSARY!
```
Yanking my hair out in frustrated exasperation.  "They just don't listen!"

So what CPU does your netbook have?

---

### Post by Ayuthia on 2009-11-14
> **kgingeri said:**
> Yup a Touch-only device would certainly help - I think I've got enough for now tho :lol:  (not that I think you were implying anything)

Ok, more seriously - Your right - it should be coming from the other event.  What about other tablets?  Maybe we should look thru existing code for how that's handled, or are these tablet unique that way?

BTW:  I am not getting touch either anymore!!  I should have saved that last rebuild!!!  I'll see if I can revert.

The TabletPC's are probably the closest to these things because they do have a stylus and touch.  The part I am not for sure about is if they report from two different events.  Favux might know the answer to this.

By the way, which one has the greater distance, the X or the Y coordinate?  I had a thought about the X and Y coordinate, but your center sample does not match my theory.

It could also be that 0x80 and 0x81 are finger counters.  These are all just guesses.

---

### Post by kgingeri on 2009-11-14
> **Favux said:**
> ```
First, let me say that rebooting between builds IS DEFINITELY NECESSARY!
```
Yanking my hair out in frustrated exasperation.  "They just don't listen!"

So what CPU does your netbook have?

So sorry Favux - didn't mean to cause baldness!!  :lol:
I know, lazy mostly, and I thought the mod commands would be enough  ;)

It's an Intel Atom 1.6 Ghz - Acer One Aspire, model ZG6

---

### Post by Favux on 2009-11-14
Hi Ayuthia and kgingeri,

Yes the TX2000 and TX2500 report touch on a separate event from the stylus.  As near as I've been able to tell the Bamboo P & T's are constructed the same way.  A digitizer and a touch screen sandwiched together.  The only difference I've seen so far, is unlike the tablet pc's, the touch screen is apparently a physically different size from the digitizer on the P & T's.

---

### Post by Moophius on 2009-11-14
Per [Ayuthia]("http://ubuntuforums.org/member.php?u=286983")'s request, as I have a bamboo touch, I am posting my Messages log and my Xorg.0.log

---

### Post by kgingeri on 2009-11-14
> **Ayuthia said:**
> The TabletPC's are probably the closest to these things because they do have a stylus and touch.  The part I am not for sure about is if they report from two different events.  Favux might know the answer to this.

By the way, which one has the greater distance, the X or the Y coordinate?  I had a thought about the X and Y coordinate, but your center sample does not match my theory.

It could also be that 0x80 and 0x81 are finger counters.  These are all just guesses.

Actually that center tap may not have been center.  I was more careful with the corner taps so don't use that first data.  I'll redo center and all corners and post it here also.

I've attached a gesture data file.  Have a look...

EDIT: Weird, my txt file won't upload this time.  Anyway it did as a gzip file.  I have labeled the data groups.
EDIT: and new and careful tap data.

---

### Post by Ayuthia on 2009-11-14
> **kgingeri said:**
> So sorry Favux - didn't mean to cause baldness!!  :lol:
I know, lazy mostly, and I thought the mod commands would be enough  ;)

It's an Intel Atom 1.6 Ghz - Acer One Aspire, model ZG6

For my N-Trig device, I usually kill X, do the modprobe commands, and then start X again.  The modprobe commands alone have always left my touchscreen unresponsive.

I am thinking that we should try to continue with the touch.  It might help to see how the one finger touch differs from two.  Can you also do one finger for each corner?  We might be able to get a better idea of how the coordinates are laid out.  I am thinking that the X,Y coordinates are not very big for these tablets (X < 256 Y < 512) so they only need three bytes to hold the data.

As for me, I am heading for bed.  I just wish there was a way for us to grab the data through /dev.  The N-Trig ones are able to get it through /dev/hidrawX.  I have a couple of python scripts that help me read the data instead of reading logs.

---

### Post by Ayuthia on 2009-11-14
> **Moophius said:**
> Per [Ayuthia]("http://ubuntuforums.org/member.php?u=286983")'s request, as I have a bamboo touch, I am posting my Messages log and my Xorg.0.log

Welcome to the group!

I just realized that your device might not be defined yet.  Can you provide the lsusb result for us?  Once we get that, we can add the device to the source so that your device will be recognized.

---

### Post by kgingeri on 2009-11-14
> **Ayuthia said:**
> For my N-Trig device, I usually kill X, do the modprobe commands, and then start X again.  The modprobe commands alone have always left my touchscreen unresponsive.

I am thinking that we should try to continue with the touch.  It might help to see how the one finger touch differs from two.  Can you also do one finger for each corner?  We might be able to get a better idea of how the coordinates are laid out.  I am thinking that the X,Y coordinates are not very big for these tablets (X < 256 Y < 512) so they only need three bytes to hold the data.

As for me, I am heading for bed.  I just wish there was a way for us to grab the data through /dev.  The N-Trig ones are able to get it through /dev/hidrawX.  I have a couple of python scripts that help me read the data instead of reading logs.

Agreed. Scripts for dev nodes would be great!
See my previous post to yours for gesture and tap data - I did it before reading this post - files are [here #159]("http://ubuntuforums.org/showpost.php?p=8313434&postcount=159")

---

### Post by kgingeri on 2009-11-14
> **Moophius said:**
> Per [Ayuthia]("http://ubuntuforums.org/member.php?u=286983")'s request, as I have a bamboo touch, I am posting my Messages log and my Xorg.0.log

Yes - Welcome Moophius!  Hang in there with us and we'll see if we can't get touch working soon!!

I sure do like how it works on my Mac  ;)

EDIT: Yeah, as Ayuthia asked, do an lsusb command and get us the output.  Your logs show that the device is not recognized.

---

### Post by Ayuthia on 2009-11-14
> **kgingeri said:**
> Actually that center tap may not have been center.  I was more careful with the corner taps so don't use that first data.  I'll redo center and all corners and post it here also.

I've attached a gesture data file.  Have a look...

EDIT: Weird, my txt file won't upload this time.  Anyway it did as a gzip file.  I have labeled the data groups.
EDIT: and new and careful tap data.

The center tap is always the one that throws me off!

Upper left:
```
3:80 4:0 5:0 6:6
```
X=0x0 (0) Y=0x6 (6)

Upper right:
```
3:81 4:e0 5:0 6:c
```
X=0xe0 (224)  Y=0xc (12)

Lower left:
```
3:80 4:0 5:1 6:39
```
X=0x0 (0) Y=0x139 (313)

Lower right:
```
3:81 4:e0 5:1 6:3f
```
X=0xe0 (224) Y=0x13f (319)

All of that makes it seem like we have found the corner coordinates where X max is at 224 and Y max is around 320.

Then you produce the center data:
```
3:80 4:e4 5:0 6:b3
```
X=0xe4 (228 )  Y=0xb3 (179)
The Y result is reasonable, but the X value would end up higher at the center?  That does not sound right.

What happens if you drag your finger from the upper left to the lower right?  Try to drag a straight line!  :lol:

By any chance, do you know why you are missing the 20th byte?  I was reading your gestures and I am trying to figure out if 80 and 81 are separate fingers or not.
(I am really heading to bed now...)

---

### Post by kgingeri on 2009-11-14
> **Ayuthia said:**
> 
...
What happens if you drag your finger from the upper left to the lower right?  Try to drag a straight line!  :lol:

By any chance, do you know why you are missing the 20th byte?  I was reading your gestures and I am trying to figure out if 80 and 81 are separate fingers or not.
(I am really heading to bed now...)

Ok, here it is Ayuthia (hope you did get to bed tho ;))

EDIT: Oops forgot to answer your other question.  No, I have no idea why there is only 19! My code change is:
```
    { "Wacom Intuos2 6x8",        WACOM_PKGLEN_INTUOS,    20320, 16240, 1023, 31, INTUOS },
    { "Wacom Bamboo P&T 4x5",                     20,     14732, 9144, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-460
```
I could try making it larger? -or- is your index init and test ok? - "...<var.pktlen" rather than "...<=var.pktlen"?  I haven't cecked your code.
Ok sac time for me as well - tomorrow again.

---

### Post by dnprossi on 2009-11-14
WOW!!!! Can't believe that my dumps have started all this!!!\\:D/

Ayuthia, kgingery **Good work!!** 
 
Have some other info for you!

When I switch off touch in windows data is still dumped and passed from tablet through usb. Touch is not disabled, somehow **software switched** not to receive data from touch. This is confirmed by tablet led that continues signaling when pressing or moving finger on it...

touch area is smaller than stylus area..
I have added top-left, bottom-right, center tappings txt files...

---

### Post by neapolitan on 2009-11-14
Thanks for the great work you guys!  I'm running Debian sid and still have a problem with the patched, compiled, and installed 0.8.5-1 linuxwacom drivers on (custom) kernel 2.6.28.8 (but problem is constant between all kernels.)  I used Ayuthia's latest patch which applies cleanly, and install goes without any issues.  On reboot, the module is installed ok if tab is connected at boot, or if I subsequently connect the tablet, dmesg reports:

```
[  356.440508] input: Wacom Bamboo Pen 4x5 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input13
[  356.458501] input: Wacom Bamboo Pen 4x5 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input14
[  356.464419] usbcore: registered new interface driver wacom
[  356.464426] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
```However, going to /dev/input, the new devices appear as:
```

ls /dev/input
by-id  by-path  js0  mice  mouse0  mouse1  mouse2

```with mouse1 and mouse2 being new since the plug.  I'm running a thinkpad T43p, so the touchstick is on mouse0.

Reading through the wacom project docs, there is a page here:
[http://linuxwacom.sourceforge.net/index.php/howto/mouse1](http://linuxwacom.sourceforge.net/index.php/howto/mouse1)

that seems to frown on using the mixer device "mice."  I went through my xorg.conf, and removed all references to /dev/mice, and "hardcoded" the inputdevice for the touchstick as:

```

Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse0"
    Driver      "mouse"
    Option "Protocol"    "Auto"
    Option "Device"      "/dev/input/mouse0"
    Option "ZAxisMapping"       "4 5"
    Option "ButtonMapping"      "1 9 3 4 5"
```However, it still seems to detect the wacom tablet as a mouse, and it does nothing with X.  If I dump the /dev/mouse1 or /dev/mouse2 devices, it seems to recognize the pad as a mouse (dragging in a specific direction on the pad produces reproducible characters, etc.)

Any help is greatly appreciated!!

---

### Post by Moophius on 2009-11-14
> **kgingeri said:**
> Yes - Welcome Moophius!  Hang in there with us and we'll see if we can't get touch working soon!!

I sure do like how it works on my Mac  ;)

EDIT: Yeah, as Ayuthia asked, do an lsusb command and get us the output.  Your logs show that the device is not recognized.

Thanks for the warm welcome :D

When I do the lsusb command it does recognize my wacom as attached:

> Bus 008 Device 002: ID 056a:00d0 Wacom Co., Ltdit still remains unresponsive however /sigh

Additionally, when I run some of the commands I'm not sure if they are properly fetching the information, for example, the first set of commands provide this error:
> W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

I am still new to ubuntu and am trying to familiarize myself with how it operates, yet this remains greek to me for the time being

---

### Post by Ayuthia on 2009-11-14
> **kgingeri said:**
> Ok, here it is Ayuthia (hope you did get to bed tho ;))

EDIT: Oops forgot to answer your other question.  No, I have no idea why there is only 19! My code change is:
```
    { "Wacom Intuos2 6x8",        WACOM_PKGLEN_INTUOS,    20320, 16240, 1023, 31, INTUOS },
    { "Wacom Bamboo P&T 4x5",                     20,     14732, 9144, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBFUN,     14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-460
```
I could try making it larger? -or- is your index init and test ok? - "...<var.pktlen" rather than "...<=var.pktlen"?  I haven't cecked your code.
Ok sac time for me as well - tomorrow again.

Ok.  I think we have it figured out now.  Field 3 is also need.  The data is shared with the 0x80.
Upper left:
```
3:80 4:0 5:0 6:6
```
X=0x0 (0) Y=0x6 (6)

Upper right:
```
3:81 4:e0 5:0 6:c
```
X=0x1e0 (480)  Y=0xc (12)

Lower left:
```
3:80 4:0 5:1 6:39
```
X=0x0 (0) Y=0x139 (313)

Lower right:
```
3:81 4:e0 5:1 6:3f
```
X=0x1e0 (480) Y=0x13f (319)

Center:
```
3:80 4:e4 5:0 6:b3
```
X=0xe4 (228 )  Y=0xb3 (179)

With all the data provided, we can confirm that the max X is 480 and Y is 320.  If you take a look at dnprossi's attachment, there is a file called usbproperties.txt and you will find the logical maximums for X and Y listed as 480 and 320.

I will need to review the two-finger data a little more to see if we can figure out how two fingers are reported.  It looks like the same finger data can be reported in the same data packet.  It looks like the second finger data starts at field 12 though.

---

### Post by Ayuthia on 2009-11-14
> **Moophius said:**
> Thanks for the warm welcome :D

When I do the lsusb command it does recognize my wacom as attached:

it still remains unresponsive however /sigh

Additionally, when I run some of the commands I'm not sure if they are properly fetching the information, for example, the first set of commands provide this error:


I am still new to ubuntu and am trying to familiarize myself with how it operates, yet this remains greek to me for the time being

I will try to update the patch today so that your device is added.  You just confirmed that we have not seen this device yet.  In future posts, you will see me sometimes calling your device the 0xd0.

It also looks like we have enough to get one finger touch to start working.

---

### Post by Ayuthia on 2009-11-14
> **neapolitan said:**
> Thanks for the great work you guys!  I'm running Debian sid and still have a problem with the patched, compiled, and installed 0.8.5-1 linuxwacom drivers on (custom) kernel 2.6.28.8 (but problem is constant between all kernels.)  I used Ayuthia's latest patch which applies cleanly, and install goes without any issues.  On reboot, the module is installed ok if tab is connected at boot, or if I subsequently connect the tablet, dmesg reports:

```
[  356.440508] input: Wacom Bamboo Pen 4x5 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input13
[  356.458501] input: Wacom Bamboo Pen 4x5 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input14
[  356.464419] usbcore: registered new interface driver wacom
[  356.464426] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
```However, going to /dev/input, the new devices appear as:
```

ls /dev/input
by-id  by-path  js0  mice  mouse0  mouse1  mouse2

```with mouse1 and mouse2 being new since the plug.  I'm running a thinkpad T43p, so the touchstick is on mouse0.

Reading through the wacom project docs, there is a page here:
[http://linuxwacom.sourceforge.net/index.php/howto/mouse1](http://linuxwacom.sourceforge.net/index.php/howto/mouse1)

that seems to frown on using the mixer device "mice."  I went through my xorg.conf, and removed all references to /dev/mice, and "hardcoded" the inputdevice for the touchstick as:

```

Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse0"
    Driver      "mouse"
    Option "Protocol"    "Auto"
    Option "Device"      "/dev/input/mouse0"
    Option "ZAxisMapping"       "4 5"
    Option "ButtonMapping"      "1 9 3 4 5"
```However, it still seems to detect the wacom tablet as a mouse, and it does nothing with X.  If I dump the /dev/mouse1 or /dev/mouse2 devices, it seems to recognize the pad as a mouse (dragging in a specific direction on the pad produces reproducible characters, etc.)

Any help is greatly appreciated!!

Did you install the udev rules?  Since we are currently using .fdi to define the device, can you also provide the results for your device from lshal?  Thanks!

Since you don't have an event assigned, it could mean that X did not find your device.  Can you let us know which tablet you have (lsusb)?

---

### Post by Ayuthia on 2009-11-14
> **Moophius said:**
> Thanks for the warm welcome :D

When I do the lsusb command it does recognize my wacom as attached:

it still remains unresponsive however /sigh

Additionally, when I run some of the commands I'm not sure if they are properly fetching the information, for example, the first set of commands provide this error: > W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


I am still new to ubuntu and am trying to familiarize myself with how it operates, yet this remains greek to me for the time being

This message is most likely happening because you do not have the LiveCd in your drive.  If you do not want to use it, you can go into Synaptic and turn of the CD portion.  You can try this [guide]("https://help.ubuntu.com/community/Repositories/Ubuntu").

I usually use Kubuntu so I am not too familiar around Ubuntu, but I think that Software Sources is still there.

---

### Post by neapolitan on 2009-11-14
> **Ayuthia said:**
> Did you install the udev rules? Since we are currently using .fdi to define the device, can you also provide the results for your device from lshal? Thanks!

Since you don't have an event assigned, it could mean that X did not find your device. Can you let us know which tablet you have (lsusb)?

Thanks so much.

Udev rules are installed, but I will check on this (is it now installed from the patch?)

lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 056a:00d4 Wacom Co., Ltd
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 002: ID 0a5c:201e Broadcom Corp. IBM Integrated Bluetooth IV
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```and lshal:
```


udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'CTL-460'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/003/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 262  (0x106)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2'  (string)
  usb_device.max_power = 98  (0x62)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'CTL-460'  (string)
  usb_device.product_id = 212  (0xd4)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_if1'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 262  (0x106)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 212  (0xd4)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_if0'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 262  (0x106)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 212  (0xd4)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_usbraw'  (string)
  linux.device_file = '/dev/usbdev3.3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/usb_device/usbdev3.3'  (string)
  usbraw.device = '/dev/usbdev3.3'  (string)

```This is all of the 56a/d4 references in lshal.

I have the CTL460 (Bamboo pen only) device.

The udev rules I have is downloaded from the git site:
```
wget -O 40-xserver-xorg-input-wacom.rules "http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=e110b046292d6aff63b489c9b1aecec25d470cdb"
```and placed in /lib/udev/rules.d (I did not place it in /etc/udev/rules.d).

I tried rebooting and reinserting, and still detected as a mouse device.  Interestingly enough, the /dev/input/mice is still always visible when the Bamboo pad is not plugged in and the wacom driver removed.

```
/lib/udev/rules.d# ls /dev/input
by-path  js0  mice  mouse0

```

---

### Post by Ayuthia on 2009-11-14
The patches does not install the rules for you.  We have been doing the following:
```
sudo cp src/util/60-wacom.rules /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
```
However, it does not seem that you are getting any input entries either so it could be possible that the kernel module is not happy with something. 

Out of curiosity, do you have a /dev/usbraw file?  Also, do you get any data when you do:
```
sudo hexdump /dev/usbdev3.3
```Press control-c to end the application.

Since you are using Debian, you might try compiling it like rebecca2525 does from this [link]("https://sourceforge.net/mailarchive/message.php?msg_name=20091111230322.6fbe7e18%40zam559").  However, you are using the 2.6.28 kernel so you should not need the extra steps.  It just looks like the kernel module is not recognizing your device.

The mouse0/mice information is most likely pointing to another device.  You might be able to see what device it is connecting to through /dev/input/by-path.

---

### Post by rebecca2525 on 2009-11-14
My problem on Debian testing (with kernel 2.6.30-2-amd64) was that *configure --enable-wacom* always said there was no support for kernel modules, and thus make wouldn't create a *wacom.ko*. Once I fixed that like in the link above, everything worked fine for me. Remember to copy some files manually:

> cp src/2.6.28/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
cp src/util/60-wacom.rules /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
cp src/util/10-linuxwacom.fdi /usr/share/hal/fdi/policy/20thirdparty


Btw, I just used the tablet for real and drew my first image in MyPaint. Works great!

---

### Post by Ayuthia on 2009-11-14
Does anyone else have a record like this in lshal:
```

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d4_noserial_usbraw'  (string)
  linux.device_file = '/dev/usbdev3.3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/usb_device/usbdev3.3'  (string)
  usbraw.device = '/dev/usbdev3.3'  (string)

```

This might be the location where you can see the data without having to read the messages log.  If you do have it, can you check and see if you can read the data from either xxd or hexdump:
```
sudo hexdump /dev/usbdev3.3
sudo xxd /dev/usbdev3.3
```Control-C to get out of the application.  The 3.3 might be a different number for everyone.  

If you do get data out of it, can you provide a sample set for us?  We can then create a python script to read the data a little more nicely.

---

### Post by rebecca2525 on 2009-11-14
```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_d3_noserial_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d3_noserial'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d3_noserial_usbraw'  (string)
  linux.device_file = '/dev/usbdev6.3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/usb_device/usbdev6.3'  (string)
  usbraw.device = '/dev/usbdev6.3'  (string)
``````

$ xxd /dev/usbdev6.3
0000000: 1201 0002 0000 0040 6a05 d300 0601 0102  .......@j.......
0000010: 0001 0902 3b00 0201 0080 3109 0400 0001  ....;.....1.....
0000020: 0301 0200 0921 0001 0001 22b0 0007 0581  .....!....".....
0000030: 0309 0004 0904 0100 0103 0000 0009 2100  ..............!.
0000040: 0100 0122 4b00 0705 8203 4000 04         ..."K.....@..
```It stops by itself after these few lines without me pressing Ctrl-C, and it's always the same output...

---

### Post by Ayuthia on 2009-11-14
> **rebecca2525 said:**
> ```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_d3_noserial_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d3_noserial'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d3_noserial_usbraw'  (string)
  linux.device_file = '/dev/usbdev6.3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/usb_device/usbdev6.3'  (string)
  usbraw.device = '/dev/usbdev6.3'  (string)
``````

$ xxd /dev/usbdev6.3
0000000: 1201 0002 0000 0040 6a05 d300 0601 0102  .......@j.......
0000010: 0001 0902 3b00 0201 0080 3109 0400 0001  ....;.....1.....
0000020: 0301 0200 0921 0001 0001 22b0 0007 0581  .....!....".....
0000030: 0309 0004 0904 0100 0103 0000 0009 2100  ..............!.
0000040: 0100 0122 4b00 0705 8203 4000 04         ..."K.....@..
```It stops by itself after these few lines without me pressing Ctrl-C, and it's always the same output...

Ok.  So that must be some hardware information.  Is there a /dev/usbraw file of any sort?

---

### Post by rebecca2525 on 2009-11-14
No.
```
$ ls /dev/usb*
/dev/usbdev1.1       /dev/usbdev3.1       /dev/usbdev4.2_ep81  /dev/usbdev6.3_ep81  /dev/usbmon1
/dev/usbdev1.1_ep00  /dev/usbdev3.1_ep00  /dev/usbdev5.1       /dev/usbdev6.3_ep82  /dev/usbmon2
/dev/usbdev1.1_ep81  /dev/usbdev3.1_ep81  /dev/usbdev5.1_ep00  /dev/usbdev7.1       /dev/usbmon3
/dev/usbdev1.3       /dev/usbdev4.1       /dev/usbdev5.1_ep81  /dev/usbdev7.1_ep00  /dev/usbmon4
/dev/usbdev1.3_ep00  /dev/usbdev4.1_ep00  /dev/usbdev6.1       /dev/usbdev7.1_ep81  /dev/usbmon5
/dev/usbdev1.3_ep83  /dev/usbdev4.1_ep81  /dev/usbdev6.1_ep00  /dev/usbdev8.1       /dev/usbmon6
/dev/usbdev2.1       /dev/usbdev4.2       /dev/usbdev6.1_ep81  /dev/usbdev8.1_ep00  /dev/usbmon7
/dev/usbdev2.1_ep00  /dev/usbdev4.2_ep00  /dev/usbdev6.3       /dev/usbdev8.1_ep81  /dev/usbmon8
/dev/usbdev2.1_ep81  /dev/usbdev4.2_ep02  /dev/usbdev6.3_ep00  /dev/usbmon0
```EDIT:
*find /dev/ -iname "*raw*"  *finds nothing and* find /dev/ -iname "*usb*"*  [finds this]("http://paste.pocoo.org/show/150629/").

---

### Post by Ayuthia on 2009-11-14
I guess that is trying to tell us that it is not there :(

Thanks for checking this!

---

### Post by neapolitan on 2009-11-14
> **rebecca2525 said:**
> My problem on Debian testing (with kernel 2.6.30-2-amd64) was that *configure --enable-wacom* always said there was no support for kernel modules, and thus make wouldn't create a *wacom.ko*. Once I fixed that like in the link above, everything worked fine for me. Remember to copy some files manually:




Btw, I just used the tablet for real and drew my first image in MyPaint. Works great!

Thanks rebecca and ayuthia!  I'm making big progress.  I run a custom kernel, so thought that I would grab the precompiled linux-image-2.6.31 from the debian archive and start from there.

After installing the header files (I usually run a vanilla kernel, so the debian precompiled process was new to me), I compiled and copied the patched wacom driver.  Partial success!  The driver is now recognized properly and assigned to /dev/input/wacom and /dev/input/wacom-touch.

xxd of /dev/input/wacom shows a wealth of characters when hovering the pen over the pad.  However, my X server still doesn't recognize the pen inputs.  I'll work on this and report back.

I think that my custom kernel problem was that the mouse support was compiled in, not loaded as a module.  More soon...

---

### Post by neapolitan on 2009-11-14
Success!!!  Thanks guys.

My vanilla kernel did not work for debian.  I'll compile the mouse driver as a module, recompile, and see if this works and generally try to isolate what the problem was (I can post my 2.6.31 .config file too if that would help anybody.)

Using debian precompiled kernel, the above works beautifully with patches.  I just had to restart X to make everything work (it would not "hot-detect" the new /dev/input/wacom device.)

I am getting the "jumping" error where the cursor jumps 200 pixels diagonally northwest after lifting the stylus from the hover-zone.  I'm willing to test any new patches or try to help out if possible...  Thanks again to you guys.

---

### Post by neapolitan on 2009-11-14
Sorry, actually for the record I had success with the debian "linux-image-2.6.26-1-486" precompiled kernel, not 2.6.31 as I said above.  I normally boot to 2.6.31.5, but had to downgrade to compile the drivers.

---

### Post by Ayuthia on 2009-11-14
> **neapolitan said:**
> Success!!!  Thanks guys.

My vanilla kernel did not work for debian.  I'll compile the mouse driver as a module, recompile, and see if this works and generally try to isolate what the problem was (I can post my 2.6.31 .config file too if that would help anybody.)

Using debian precompiled kernel, the above works beautifully with patches.  I just had to restart X to make everything work (it would not "hot-detect" the new /dev/input/wacom device.)

I am getting the "jumping" error where the cursor jumps 200 pixels diagonally northwest after lifting the stylus from the hover-zone.  I'm willing to test any new patches or try to help out if possible...  Thanks again to you guys.

I am glad to see it working!  When I have a chance, I will link rebecca2525's post so that other Debian users can benefit from it.  

You are more than welcome to use the patches in the first post in this thread.  It should stop the "jumping".  It seems to be working pretty well so I am planning on moving that to our "stable" thread.

---

### Post by rebecca2525 on 2009-11-14
One little thing I noticed: After suspending to RAM and "unsuspending" (with tablet plugged in), the tablet does not work until you unplug/replug it. I haven't noticed this behaviour for other USB devices (mouse, keyboard,...). This isn't a big issue, just mentioning it.

---

### Post by Ayuthia on 2009-11-14
I am looking at the TabletPC code and it looks like there might be pressure data also.  Can someone with touch data test it out?  I think that the data might be in the third byte (data[2]) but I cannot confirm it.  We will need some light touches and some hard ones to see if we can max it out.  If we see 0xff in the third byte, we know that we have pressure.

---

### Post by dnprossi on 2009-11-14
> **Ayuthia said:**
> I am looking at the TabletPC code and it looks like there might be pressure data also.  Can someone with touch data test it out?  I think that the data might be in the third byte (data[2]) but I cannot confirm it.  We will need some light touches and some hard ones to see if we can max it out.  If we see 0xff in the third byte, we know that we have pressure.

Windows Dump
Yes third byte goes up to 0xff
With gradual increment of pressure you can see third byte vary up to 0xff and back to 0x00.
also when using two fingers the last byte varies 0x80-0x81
0x80-0x81 varies also if tapping first on right then on left of pad

---

### Post by Ayuthia on 2009-11-14
I have created a new patch for testing.  This will add the Bamboo Touch to the group.

With that, we are now entering the touch testing since we are getting some touch data.  We still have not figured out how to switch from touch to stylus yet.

There is a good chance that the code will break this time.  Since the data length is different from the pen and touch, I have created two new functions to separate them.  

I did change the naming scheme of the patch and source tarball so that it includes the patch number.

---

### Post by Ayuthia on 2009-11-14
> **dnprossi said:**
> Windows Dump
Yes third byte goes up to 0xff
With gradual increment of pressure you can see third byte vary up to 0xff and back to 0x00.
also when using two fingers the last byte varies 0x80-0x81
0x80-0x81 varies also if tapping first on right then on left of pad

Cool!  If the touch testing goes well, I will incorporate the pressure in the next set of patches.

The 0x81 has a shared bit that is used for the X coordinate.  

Once we get this moving further along, I will see if we can mimic the TabletPC data so that we can get the gestures for this device also.

---

### Post by rebecca2525 on 2009-11-14
Nothing is working now, and I don't get any reaction in log messages (only on plug in/out)

var/log/messages:
```
Nov 14 21:44:40 zam559 kernel: [  283.496087] usb 6-1: new full speed USB device using uhci_hcd and address 3
Nov 14 21:44:40 zam559 kernel: [  283.655853] usb 6-1: New USB device found, idVendor=056a, idProduct=00d3
Nov 14 21:44:40 zam559 kernel: [  283.655860] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 14 21:44:40 zam559 kernel: [  283.655866] usb 6-1: Product: CTH-661
Nov 14 21:44:40 zam559 kernel: [  283.655870] usb 6-1: Manufacturer: Wacom Co.,Ltd.
Nov 14 21:44:40 zam559 kernel: [  283.656067] usb 6-1: configuration #1 chosen from 1 choice
Nov 14 21:44:40 zam559 kernel: [  283.663982] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input17
Nov 14 21:44:40 zam559 kernel: [  283.677973] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input18
```

[And xorg log]("http://paste.pocoo.org/show/150651/")

---

### Post by marek_online on 2009-11-14
> **Ayuthia said:**
> I have created a new patch for testing.  This will add the Bamboo Touch to the group.

With that, we are now entering the touch testing since we are getting some touch data.  We still have not figured out how to switch from touch to stylus yet.

There is a good chance that the code will break this time.  Since the data length is different from the pen and touch, I have created two new functions to separate them.  

I did change the naming scheme of the patch and source tarball so that it includes the patch number.

Interesting! Touch, stylus and eraser all being picked up, buttons on the pad doing *something* in /var/log/messages. Everything is too jittery to be usable though, and while the buttons, stylus and eraser tips seem to produce something in the logs, they're not having an effect.

Feels like progress though!

EDIT:

Just looking the behaviour again. For both stylus and touch, the pointer seems to be making quite big jumps or moving too quickly - as though acceleration is much too high.

---

### Post by Ayuthia on 2009-11-14
Ok.  I have updated the calculations for X and Y and have added touch resolutions for the touch so hopefully this will help.  I am not picking up good vibes on this one though.

I have also added pressure to the mix.

marek_online, right now the stylus is not operating on your tablet.  You only have touch.  It looks like your device is now picking up the other event.  Hopefully we can get both going soon.

---

### Post by kgingeri on 2009-11-14
Sweetness All!!!

Can't wait to join in again, but i'm out of commission for the day likely.

Ayuthia, you rock!  :guitar:  ;)

---

### Post by rebecca2525 on 2009-11-14
I still don't get any data when using the tablet. Just plug/unplug shows up.

/var/log/messages:
```
Nov 14 22:53:07 zam559 kernel: [  240.236110] usb 6-1: new full speed USB device using uhci_hcd and address 3
Nov 14 22:53:07 zam559 kernel: [  240.399955] usb 6-1: New USB device found, idVendor=056a, idProduct=00d3
Nov 14 22:53:07 zam559 kernel: [  240.399963] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 14 22:53:07 zam559 kernel: [  240.399969] usb 6-1: Product: CTH-661
Nov 14 22:53:07 zam559 kernel: [  240.399973] usb 6-1: Manufacturer: Wacom Co.,Ltd.
Nov 14 22:53:07 zam559 kernel: [  240.400148] usb 6-1: configuration #1 chosen from 1 choice
Nov 14 22:53:07 zam559 kernel: [  240.407081] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input17
Nov 14 22:53:07 zam559 kernel: [  240.418090] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input18
```[URL="http://paste.pocoo.org/show/150665/"]
xorg log[/URL]

---

### Post by marek_online on 2009-11-14
> **Ayuthia said:**
> Ok.  I have updated the calculations for X and Y and have added touch resolutions for the touch so hopefully this will help.  I am not picking up good vibes on this one though.

I have also added pressure to the mix.

marek_online, right now the stylus is not operating on your tablet.  You only have touch.  It looks like your device is now picking up the other event.  Hopefully we can get both going soon.

:oops: The knuckle of my pinky finger was dragging across the pad as I used the stylus. 

The LED on the devices was turning red, though, as it normally does when picking up the pen.

The movement with the new touch resolutions is smooth, but very small, it takes seventeen swipes the width of the pad to get the pointer from one end of my screen to the other.  We're looking for something mid-way between the settings you've tried so far it looks like.

No effect of tapping on the pad as far as clicking goes.

---

### Post by Ayuthia on 2009-11-14
If you want to use touch, you will need some fast fingers so that you can get from one corner of the screen to the other...

Seriously though, it looks like the calculations are now correct, but it is not converting it to the screen resolution properly.

rebecca2525, I wonder if the issue with the size of the data coming in.  I will try to add some other debug information to see where/if it stops.

---

### Post by Favux on 2009-11-14
Hi everyone,

Could those with the new patches post the output of:
```
dmesg | grep [Ww]acom
```
and
```
ls -l /dev/input/by-path
```
along with
```
lshal>lshal.txt
```
Maybe time to try a new test .fdi.

Thanks.

---

### Post by rebecca2525 on 2009-11-14
> **Favux said:**
> Hi everyone,

Could those with the new patches post the output of:
```
dmesg | grep [Ww]acom
```and
```
ls -l /dev/input/by-path
```along with
```
lshal>lshal.txt
```Maybe time to try a new test .fdi.

Thanks.

See attachment.

EDIT: It's getting late over here, will be back tomorrow. Good luck!

---

### Post by Moophius on 2009-11-14
Well, I applied the new patches, yet my Touch is still not responding.  It looks like it is sensing as whenever I try to use it the white light gets a tad brighter, but nothing happens still.

It is still being recognized however, which I suppose is a good thing:

Bus 008 Device 003: ID 056a:00d0 Wacom Co., Ltd 

Attached are the current log after I ran though both sets of patches

Also, I am not 100% positive I am applying the patches correctly, mainly since my touch is still not working.  Is there any way I can verify it the patches were installed correctly?

---

### Post by Ayuthia on 2009-11-14
> **Moophius said:**
> Well, I applied the new patches, yet my Touch is still not responding.  It looks like it is sensing as whenever I try to use it the white light gets a tad brighter, but nothing happens still.

It is still being recognized however, which I suppose is a good thing:

Bus 008 Device 003: ID 056a:00d0 Wacom Co., Ltd 

Attached are the current log after I ran though both sets of patches

Also, I am not 100% positive I am applying the patches correctly, mainly since my touch is still not working.  Is there any way I can verify it the patches were installed correctly?

I am thinking that lshal might be the best place to check.  Can you attach that file to your next post:
```
lshal > $HOME/lshal.txt
cd
tar -cvjf lshal.txt.tar.bz2 lshal.txt
```
You can use the commands above to create the file and then create a .tar.bz2 file for it so that you can attach it to your post.  You will only need to attach lshal.txt.tar.bz2.

If you are not comfortable with the patches, you can download the pre-patched version that is listed in the first post.

---

### Post by Ayuthia on 2009-11-14
I have created a new patch to try out.  Hopefully it will fix the touch resolution issue that we are having.

I have also found that I was missing an entry for the 0xd0 in the X portion of the code.  moophius--the part that I missed is on a later part.  It looks like the kernel module might not be accepting your device properly yet but we can confirm that with your lshal results.

I did make a change for the pen tablets to only deal with 9 bytes of data instead of the 20.  

On the next patch I will add the missing byte to the debug data.  We will be needing that once we get the one-finger touch working.

---

### Post by Moophius on 2009-11-14
ok, here is the lshal as you requested

---

### Post by Ayuthia on 2009-11-14
> **Moophius said:**
> ok, here is the lshal as you requested

It looks like the kernel module did not attach to the device.  Can you try the pre-patched version listed under Option A in the first post?

Also, did you copy over the wacom.ko file over to /lib/modules/$(uname -r)/kernel/drivers/input/tablet and restart?

---

### Post by Moophius on 2009-11-14
I have two of the same files in very similar locations:

/lib/modules/2.6.28-16-generic/kernel/drivers/input/tablet
and
/lib/modules/2.6.31-14-generic/kernel/drivers/input/tablet

I will attempt the option a version and restart again though

*edit* no dice :(

---

### Post by kgingeri on 2009-11-14
For anyone who cares, Ayuthia's version on the patch messed my RebuildWacom script so I have changed it (BTW I totally agree with that versioning Ayuthia :)).  (See post [#145]("http://ubuntuforums.org/showpost.php?p=8313047&postcount=145")).  It now prints the version info and warns you that you may have to change it, before starting. :)

---

### Post by kgingeri on 2009-11-14
> **Moophius said:**
> I have two of the same files in very similar locations:

/lib/modules/2.6.28-16-generic/kernel/drivers/input/tablet
and
/lib/modules/2.6.31-14-generic/kernel/drivers/input/tablet

I will attempt the option a version and restart again though

*edit* no dice :(

Moophius, the wacom.ko should end up in the 31-14-generic directory only, delete them both (you'll have to do it with 'sudo rm ...') and reinstall and be sure you reboot after each new install.  ;)

---

### Post by GolemdX on 2009-11-14
This thread is moving too fast for me to follow... eugh. I'll try out the new patch and post what changes I've found, even if you already know them. I haven't read the changes yet, either.

---

### Post by neapolitan on 2009-11-14
Not just success... very good success.

On debian running latest kernel 2.6.31, using the soft-link header trick courtesy of Rebecca:

```

$ cd /usr/src/linux-headers-2.6.30-2-amd64/include/linux/
 $ ln -s /usr/src/linux-headers-2.6.30-2-common/include/linux/input.h 
 $ ln -s /usr/src/linux-headers-2.6.30-2-common/include/linux/input-polldev.h 
  
 $ ./configure --enable-wacom --with-kernel=/usr/src/linux-headers-2.6.30-2-amd64

```where you substitute 2.6.31-1-686 or whatever for your linux-headers version works beautifully, allowing clean compilation with 2.6.31.  Of note, the compiled kernel will still be in the src/2.6.28/ directory.

Ayuthia's latest patch eliminates the weird pixel-jump behavior.  Coming along beautifully!

P.S.  On modern debian, the hardcoding and avoiding of /dev/input/mice is NOT necessary.  I switched back to /dev/input/mice for the core pointer, as this allows simultaneous use of my pointing stick on thinkpad, a separate desktop USB mouse, AND the wacom device.

P.P.S.  I am a researching cardiologist, and just used my new tablet to draw a figure for a paper in inkscape.  You guys are doing great work with open-source support of hardware so quickly and I am very appreciative.  :)  :)  Kudos!

---

### Post by GolemdX on 2009-11-14
Well, I downloaded the new update (pre-patched), installed it, reboot, and what I've gathered is

[LIST][*]You can now use it as a touchpad, but you can't click.
[*]Cursor moves slowly when used as touchpad due to resolution(?).
[*]Pen is no longer working.[/LIST]
Correct?

[SIZE="1"][COLOR="DimGray"]----------
Bamboo Pen & Touch Variant (00d1)[/COLOR][/SIZE]

---

### Post by Ayuthia on 2009-11-14
> **GolemdX said:**
> Well, I downloaded the new update (pre-patched), installed it, reboot, and what I've gathered is

[LIST][*]You can now use it as a touchpad, but you can't click.
[*]Cursor moves slowly when used as touchpad due to resolution(?).
[*]Pen is no longer working.[/LIST]
Correct?

[SIZE="1"][COLOR="DimGray"]----------
Bamboo Pen & Touch Variant (00d1)[/COLOR][/SIZE]

That is looking like the case.  Somehow the touch kicked in for some devices and the pen stopped.  It might just be a matter of pointing the stylus to another event.

The pen only devices seem to be working fine though.

I will go back and see if I can get the X,Y coordinates set to the correct resolution.  I will check the initialization functions to see why the click is not working on the touch.

---

### Post by GolemdX on 2009-11-14
Wait, did I miss something here? No combination of tapping/pressing buttons works for me, but if it's working for other people maybe I'm doing it wrong?

I tried with my right hand too, but I'm still left-handed.

[size=1][COLOR="DimGray"]----------
Bamboo Pen & Touch Variant (00d1)[/COLOR][/size]

---

### Post by Ayuthia on 2009-11-14
> **GolemdX said:**
> Wait, did I miss something here? No combination of tapping/pressing buttons works for me, but if it's working for other people maybe I'm doing it wrong?

I tried with my right hand too, but I'm still left-handed.

[size=1][COLOR="DimGray"]----------
Bamboo Pen & Touch Variant (00d1)[/COLOR][/size]

The buttons are recognized by the kernel module, but right now nothing is being done with them yet.

Can you attach a copy of /var/log/messages and /var/log/Xorg.0.log?  I am trying to confirm that evdev is taking the touch instead of wacom.

From marek_online's logs, it looks like evdev has taken the other event.  The Xorg.0.log data is showing that wacom is not getting anything right now (the touch data is not being sent to it).  This explains why the click portion of the touch is not working and the pad is moving like a mouse touchpad.

---

### Post by Ayuthia on 2009-11-14
Can someone that is getting touch data try changing their code a little bit to see if we get the pen back?

In src/2.6.28/wacom_wac.c, can you go to line 972 and change:
```

void wacom_init_input_dev(struct input_dev *input_dev, struct wacom_wac *wacom_wac)
{
    switch (wacom_wac->features->type) {
        case BAMBOO_PEN:
        case BAMBOO_PT:
            input_dev_bpt(input_dev, wacom_wac);
        case WACOM_MO:
            input_dev_mo(input_dev, wacom_wac);

```
to be:
```

void wacom_init_input_dev(struct input_dev *input_dev, struct wacom_wac *wacom_wac)
{
    switch (wacom_wac->features->type) {
        case BAMBOO_PT:
            input_dev_bpt(input_dev, wacom_wac);
        case BAMBOO_PEN:
        case WACOM_MO:
            input_dev_mo(input_dev, wacom_wac);

```

And at line 1090 can you find your device in:
```

    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBTOUCH,   14732, 9144, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBFUN,   14732, 9144, 1023, 63, BAMBOO_PEN }, // CTL-460
    { "Wacom Bamboo Craft",       WACOM_PKGLEN_BBTOUCH,   14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-461/S
    { "Wacom Bamboo P&T 6x8",     WACOM_PKGLEN_BBTOUCH,   21648, 13530, 1023, 63, BAMBOO_PT }, // CTH-661
    { "Wacom Bamboo Touch",       WACOM_PKGLEN_BBTOUCH,   14732, 9144, 1023, 63, BAMBOO_PT },

```
and change WACOM_PKGLEN_BBTOUCH to WACOM_PKGLEN_BBFUN and BAMBOO_PT to BAMBOO_PEN.


EDIT:
For those who want to continue testing with the touch, can you change the .fdi to point over to the other event?

---

### Post by GolemdX on 2009-11-14
Well, I deleted my old messages and Xorg.0.log files, expecting them to be recreated with new log data (they were FILLED with old stuff), but they weren't. Sorry :(

I'll try that new thing now.

EDIT: The changes to wacom_wac.c didn't do anything. I recompiled and installed, anything more I'm supposed to do?
Also, what do you mean about changing the .fdi to point to the other event?

[size=1][COLOR="DimGray"]----------
Bamboo Pen & Touch Variant (00d1)[/COLOR][/size]

---

### Post by ob1kenobi on 2009-11-14
> **Ayuthia said:**
> Can someone that is getting touch data try changing their code a little bit to see if we get the pen back?

In src/2.6.28/wacom_wac.c, can you go to line 972 and change:
```

void wacom_init_input_dev(struct input_dev *input_dev, struct wacom_wac *wacom_wac)
{
    switch (wacom_wac->features->type) {
        case BAMBOO_PEN:
        case BAMBOO_PT:
            input_dev_bpt(input_dev, wacom_wac);
        case WACOM_MO:
            input_dev_mo(input_dev, wacom_wac);

```to be:
```

void wacom_init_input_dev(struct input_dev *input_dev, struct wacom_wac *wacom_wac)
{
    switch (wacom_wac->features->type) {
        case BAMBOO_PT:
            input_dev_bpt(input_dev, wacom_wac);
        case BAMBOO_PEN:
        case WACOM_MO:
            input_dev_mo(input_dev, wacom_wac);

```And at line 1090 can you find your device in:
```

    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBTOUCH,   14732, 9144, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBFUN,   14732, 9144, 1023, 63, BAMBOO_PEN }, // CTL-460
    { "Wacom Bamboo Craft",       WACOM_PKGLEN_BBTOUCH,   14732, 9144, 1023, 63, BAMBOO_PT }, // CTL-461/S
    { "Wacom Bamboo P&T 6x8",     WACOM_PKGLEN_BBTOUCH,   21648, 13530, 1023, 63, BAMBOO_PT }, // CTH-661
    { "Wacom Bamboo Touch",       WACOM_PKGLEN_BBTOUCH,   14732, 9144, 1023, 63, BAMBOO_PT },

```and change WACOM_PKGLEN_BBTOUCH to WACOM_PKGLEN_BBFUN and BAMBOO_PT to BAMBOO_PEN.


EDIT:
For those who want to continue testing with the touch, can you change the .fdi to point over to the other event?

Hey, just picked up one of the CTH-460 models with touch.  Been playing around with the code and patches.  I'm using linuxwacom-0.8.5.4 on ubuntu.  Looks like you're missing a critical piece of code to make touch and pen work.

In wacom_sys.c you need to let the urb return be more flexible on buffer size:

```

        case -ESHUTDOWN:
                /* this urb is terminated, clean up */
                dbg("%s - urb shutting down with status: %d", __func__, urb->status);
                return;

        case -EOVERFLOW:
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    urb->actual_length == (wacom->wacom_wac->features->pktlen - 2))
                        break;
                goto exit;

        default:
                dbg("%s - nonzero urb status received: %d", __func__, urb->status);
                goto exit;
        }

```I also set the WACOM_PKGLEN_BBTOUCH value to 20 since that's the amount of data my tablet returns when in touch mode.  It returns 18 bytes when in pen mode.

Preliminary touch breakdown is that byte 0 is still 2 and byte 1 is the 4 tablet buttons.  byte 17 has the 1,2,3 finger touch in the upper nibble and the lower nibble changes between 1 or 2 depending on your dual/triple finger spacing.  I'm working on the touch code now.

Also, I can confirm pen is still working and I'm getting touch data from the kernel module

---

### Post by Ayuthia on 2009-11-14
> **GolemdX said:**
> Well, I deleted my old messages and Xorg.0.log files, expecting them to be recreated with new log data (they were FILLED with old stuff), but they weren't. Sorry :(

I'll try that new thing now.

EDIT: The changes to wacom_wac.c didn't do anything. I recompiled and installed, anything more I'm supposed to do?
Also, what do you mean about changing the .fdi to point to the other event?

[size=1][COLOR="DimGray"]----------
Bamboo Pen & Touch Variant (00d1)[/COLOR][/size]

I think that it is a matter of adding:
```

       <merge key="input.device" type="string">/dev/input/event9</merge>
       <merge key="linux.device_file" type="string">/dev/input/event9</merge>

```
You will need to change the event9 to the correct one.  The correct event number should be in the Xorg.0.log file (a new one should be created when you restart X or restart your computer).  The log section should look like:
```

(II) config/hal: Adding input device Wacom Bamboo P&T 4x5
(**) Wacom Bamboo P&T 4x5: always reports core events
(**) Wacom Bamboo P&T 4x5: Device: "/dev/input/event10"
(II) Wacom Bamboo P&T 4x5: Found 10 mouse buttons
(II) Wacom Bamboo P&T 4x5: Found scroll wheel(s)
(II) Wacom Bamboo P&T 4x5: Found x and y absolute axes
(II) Wacom Bamboo P&T 4x5: Found absolute touchpad
(II) Wacom Bamboo P&T 4x5: Configuring as touchpad
(**) Wacom Bamboo P&T 4x5: YAxisMapping: buttons 4 and 5
(**) Wacom Bamboo P&T 4x5: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Wacom Bamboo P&T 4x5" (type: TOUCHPAD)

```
In this example it shows as /dev/input/event10.

Once you make the change, you will need to restart.

---

### Post by Ayuthia on 2009-11-15
> **ob1kenobi said:**
> Hey, just picked up one of the CTH-460 models with touch.  Been playing around with the code and patches.  I'm using linuxwacom-0.8.5.4 on ubuntu.  Looks like you're missing a critical piece of code to make touch and pen work.

In wacom_sys.c you need to let the urb return be more flexible on buffer size:

```

        case -ESHUTDOWN:
                /* this urb is terminated, clean up */
                dbg("%s - urb shutting down with status: %d", __func__, urb->status);
                return;

        case -EOVERFLOW:
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    urb->actual_length == (wacom->wacom_wac->features->pktlen - 2))
                        break;
                goto exit;

        default:
                dbg("%s - nonzero urb status received: %d", __func__, urb->status);
                goto exit;
        }

```I also set the WACOM_PKGLEN_BBTOUCH value to 20 since that's the amount of data my tablet returns when in touch mode.  It returns 18 bytes when in pen mode.

Preliminary touch breakdown is that byte 0 is still 2 and byte 1 is the 4 tablet buttons.  byte 17 has the 1,2,3 finger touch in the upper nibble and the lower nibble changes between 1 or 2 depending on your dual/triple finger spacing.  I'm working on the touch code now.

Also, I can confirm pen is still working and I'm getting touch data from the kernel module

Welcome to the group!  You really know how to make an introduction!

Can you send us a copy of what you have?

---

### Post by kgingeri on 2009-11-15
Hey Ob1kenobi, welcome to the thread, but where did you get all your info for bits and what they represent?!

Are you saying that you are running Ayuthia's patches on linuxwacom-0.8.5.4? Is that a typo - should it be 0.8.5-4?  
EDIT: all we see @ linuxwacom is 0.8.5-3!!

My understanding is that Ping @ Linuxwacom has very different code for everything after 0.8.5-3 :confused:

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Hey Ob1kenobi, welcome to the thread, but where did you get all your info for bits and what they represent?!

Are you saying that you are running Ayuthia's patches on linuxwacom-0.8.5.4? Is that a typo - should it be 0.8.5-4?  
EDIT: all we see @ linuxwacom is 0.8.5-3!!

My understanding is that Ping @ Linuxwacom has very different code for everything after 0.8.5-3 :confused:

I just found the [link]("https://sourceforge.net/projects/linuxwacom/files/").

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> I just found the [link]("https://sourceforge.net/projects/linuxwacom/files/").

Whoa! Ok, got it.  A rebuilding I go :)

EDIT: so Ob1kenobi, I take it there was no fdi file changes then?

EDIT: no worky for me!  Code definitely does not match source!
```
patching file src/util/10-linuxwacom.fdi
patching file src/2.6.27/wacom.h
patching file src/util/60-wacom.rules
patching file src/2.6.28/wacom_sys.c
Hunk #2 FAILED at 498.
1 out of 2 hunks FAILED -- saving rejects to file src/2.6.28/wacom_sys.c.rej
patching file src/2.6.28/wacom_wac.c
Hunk #4 succeeded at 951 with fuzz 2 (offset 11 lines).
Hunk #5 succeeded at 983 (offset 11 lines).
Hunk #6 succeeded at 1099 (offset 12 lines).
Hunk #7 succeeded at 1171 (offset 11 lines).
patching file src/2.6.28/wacom_wac.h
Hunk #1 FAILED at 38.
1 out of 1 hunk FAILED -- saving rejects to file src/2.6.28/wacom_wac.h.rej
patching file src/wacomxi/wacomcpl-exec
patching file src/util/wactablet.h
patching file src/xdrv/wcmConfig.c
Hunk #1 FAILED at 625.
1 out of 1 hunk FAILED -- saving rejects to file src/xdrv/wcmConfig.c.rej
patching file src/xdrv/wcmUSB.c
Hunk #1 succeeded at 427 (offset -10 lines).
Hunk #2 succeeded at 525 (offset -10 lines).
```

EDIT: not to mention compile errors.  Do send us what you got - I didn't see Ayuthia's post right after yours, Ob1.  Your not a Wacom programmer by chance r u ;)

---

### Post by ob1kenobi on 2009-11-15
> **Ayuthia said:**
> Welcome to the group!  You really know how to make an introduction!

Can you send us a copy of what you have?

Here's what I have based on 0.8.5-4.  You'll see I just coped the wacom_tpc functions to start hacking on the touch inputs.

EDIT: Forgot the hal changes, I'll add them in and attach the updated patch in another post

EDIT: Duh, you don't need them if you're not using more than one tablet... but I'll add them in anyway

---

### Post by Favux on 2009-11-15
Hi everyone,

Wow!  I don't think I've ever seen a new version in 3 days!

I am confused once again.  There appear to be two devices each with a separate udi containing 'if0' and 'if1'.  The first device seems to be for sure the stylus.  I've been assuming the second device ('if1') is touch.  That's the precedent with the tablet pc's with touch like the HP TX2000 and TX2500.  What little we know about the physical construction of the P & T's seems consistent with this also.  Two separate devices, the digitizer and the touch screen, sandwiched together.

Why do you want to append touch as a sub-device to 'if0'?  Doesn't that leave 'if1' open to be grabbed by another x11 driver like evdev?

Actually what I've been wondering is if the pad is on 'if1'.  The touch only Bamboo has a pad (buttons) while the Pen only one doesn't have a pad.

Since I am very confused at this point this .fdi is probably way off base.

---

### Post by ob1kenobi on 2009-11-15
> **kgingeri said:**
> Whoa! Ok, got it.  A rebuilding I go :)
Your not a Wacom programmer by chance r u ;)

Nope, I'm just that good ;)

---

### Post by kgingeri on 2009-11-15
> **ob1kenobi said:**
> Nope, I'm just that good ;)

HA!  But not modest either! :lol:  Well glad to have ya!! :D

---

### Post by kgingeri on 2009-11-15
> **Favux said:**
> Hi everyone,

Wow!  I don't think I've ever seen a new version in 3 days!

I am confused once again.  There appear to be two devices each with a separate udi containing 'if0' and 'if1'.  The first device seems to be for sure the stylus.  I've been assuming the second device ('if1') is touch.  That's the precedent with the tablet pc's with touch like the HP TX2000 and TX2500.  What little we know about the physical construction of the P & T's seems consistent with this also.  Two separate devices, the digitizer and the touch screen, sandwiched together.

Why do you want to append touch as a sub-device to 'if0'?  Doesn't that leave 'if1' open to be grabbed by another x11 driver like evdev?

Actually what I've been wondering is if the pad is on 'if1'.  The touch only Bamboo has a pad (buttons) while the Pen only one doesn't have a pad.

Since I am very confused at this point this .fdi is probably way off base.

Favux, is the attached fdi a new one then, with confusion built in?  ;)
*(Hey, there's gotta be one in every crowd, right!?)*

---

### Post by kgingeri on 2009-11-15
Not sure if this is helpful, but I noticed another mouse (pad maybe) now in by-path... (first is with tablet connected)
```
$ l /dev/input/by-path 
total 0
[B]lrwxrwxrwx 1 root root  9 Nov 15 00:20 pci-0000:00:1d.0-usb-0:1:1.0-event-mouse -> ../event9
lrwxrwxrwx 1 root root  9 Nov 15 00:20 pci-0000:00:1d.0-usb-0:1:1.0-mouse -> ../mouse3
lrwxrwxrwx 1 root root 10 Nov 15 00:20 pci-0000:00:1d.0-usb-0:1:1.1-event -> ../event10[/B]
lrwxrwxrwx 1 root root  9 Nov 14 22:24 pci-0000:00:1d.0-usb-0:2:1.0-event-mouse -> ../event7
lrwxrwxrwx 1 root root  9 Nov 14 22:24 pci-0000:00:1d.0-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 Nov 14 22:24 pci-0000:00:1d.7-usb-0:5.1:1.0-event -> ../event8
lrwxrwxrwx 1 root root 10 Nov 14 22:24 pci-0000:00:1d.7-usb-0:5.4:1.0-event -> ../event11
lrwxrwxrwx 1 root root  9 Nov 14 22:24 platform-i8042-serio-0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 10 Nov 14 22:24 platform-i8042-serio-2-event-mouse -> ../event13
lrwxrwxrwx 1 root root  9 Nov 14 22:24 platform-i8042-serio-2-mouse -> ../mouse5

$ l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root  9 Nov 14 22:24 pci-0000:00:1d.0-usb-0:2:1.0-event-mouse -> ../event7
lrwxrwxrwx 1 root root  9 Nov 14 22:24 pci-0000:00:1d.0-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 Nov 14 22:24 pci-0000:00:1d.7-usb-0:5.1:1.0-event -> ../event8
lrwxrwxrwx 1 root root 10 Nov 14 22:24 pci-0000:00:1d.7-usb-0:5.4:1.0-event -> ../event11
lrwxrwxrwx 1 root root  9 Nov 14 22:24 platform-i8042-serio-0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 10 Nov 14 22:24 platform-i8042-serio-2-event-mouse -> ../event13
lrwxrwxrwx 1 root root  9 Nov 14 22:24 platform-i8042-serio-2-mouse -> ../mouse5
```

---

### Post by Ayuthia on 2009-11-15
> **Favux said:**
> Hi everyone,

Wow!  I don't think I've ever seen a new version in 3 days!

I am confused once again.  There appear to be two devices each with a separate udi containing 'if0' and 'if1'.  The first device seems to be for sure the stylus.  I've been assuming the second device ('if1') is touch.  That's the precedent with the tablet pc's with touch like the HP TX2000 and TX2500.  What little we know about the physical construction of the P & T's seems consistent with this also.  Two separate devices, the digitizer and the touch screen, sandwiched together.

Why do you want to append touch as a sub-device to 'if0'?  Doesn't that leave 'if1' open to be grabbed by another x11 driver like evdev?

Actually what I've been wondering is if the pad is on 'if1'.  The touch only Bamboo has a pad (buttons) while the Pen only one doesn't have a pad.

Since I am very confused at this point this .fdi is probably way off base.

All I really wanted to do is have the touch point to the other event because I was thinking that is where the data is going.  My goal was not to try to attach it to if0.  

Sorry for causing the confusion.  I am not that good with the .fdi at this point.  I have always relied on you for it. :)

---

### Post by Favux on 2009-11-15
Hi kgingeri,

It's a confusingly built confusing .fdi by the extremely confused.  Just for fun I flipped the pad to 'if1' and left touch on it.  Since the .fdi you all have been using has touch appended on 'if0', I think, I thought (in confusion) someone ought to look at touch on 'if1'.  Just to spread the confusion. :P

---

### Post by Ayuthia on 2009-11-15
> **ob1kenobi said:**
> Here's what I have based on 0.8.5-4.  You'll see I just coped the wacom_tpc functions to start hacking on the touch inputs.

EDIT: Forgot the hal changes, I'll add them in and attach the updated patch in another post

EDIT: Duh, you don't need them if you're not using more than one tablet... but I'll add them in anyway

Part of the patches include the bluetooth, ISDV4, and changes the configure.  Are they needed?

---

### Post by ob1kenobi on 2009-11-15
> **Ayuthia said:**
> Part of the patches include the bluetooth, ISDV4, and changes the configure.  Are they needed?
 
For running on karmic in order (no, no, yes), but I used the apt-get source for wacom-tools and have been building debian packages to make it easier on myself.  So that's why the first two changes are in there.

---

### Post by kgingeri on 2009-11-15
> **Favux said:**
> Hi kgingeri,

It's a confusingly built confusing .fdi by the extremely confused.  Just for fun I flipped the pad to 'if1' and left touch on it.  Since the .fdi you all have been using has touch appended on 'if0', I think, I thought (in confusion) someone ought to look at touch on 'if1'.  Just to spread the confusion. :P

Well Favux, your confusion has results!!  My touch is now normal motion and absolute to my screen AND tapping works like a normal click!! :D

What else can I test for you?!

---

### Post by Favux on 2009-11-15
Hi kgingeri,

> I noticed another mouse (pad maybe) now in by-path... 
That's just weird.  That's with the test4 .fdi?  Pad shouldn't show up like that, it's appended as a sub-device.  And even if it did wouldn't it be on "0:1:1.1-event"?

Edit:  Great!  Cool!


Hi Ayuthia,

There's only confusion because I am such a dolt.  I was looking at your latest patches and I guess finally looked at your .fdi patch.  I thought I had already done that on the first set or so of patches.  Boom, I ran the patch through in my head and ...  :o

---

### Post by kgingeri on 2009-11-15
Favux, it does appear like I am dragging if I move my mouse over text - i.e. everything gets selected, like I'm holding down a left button.

---

### Post by Favux on 2009-11-15
Hi kgingeri,

That may be the .fdi, I'm not sure how.  I'm thinking it may be the code.  It sounds like there's no release on the click.

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Well Favux, your confusion has results!!  My touch is now normal motion and absolute to my screen AND tapping works like a normal click!! :D

What else can I test for you?!

Which version source are you using?  I am currently building a patch set without the bluetooth code in it.  I also have ob1kenobi's patched source built in case the bluetooth version does not work.

---

### Post by kgingeri on 2009-11-15
I don't see pad at all now...
```
$ xsetwacom list      
stylus           stylus    
touch            touch     
eraser           eraser

$ xinput --list --short        
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
"stylus"	id=3	[XExtensionKeyboard]
"touch"	id=4	[XExtensionKeyboard]
"eraser"	id=5	[XExtensionKeyboard]
"Sleep Button"	id=6	[XExtensionKeyboard]
"Video Bus"	id=7	[XExtensionKeyboard]
"Power Button"	id=8	[XExtensionKeyboard]
"Power Button"	id=9	[XExtensionKeyboard]
"Acer Crystal Eye webcam"	id=10	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=11	[XExtensionPointer]
"SynPS/2 Synaptics TouchPad"	id=12	[XExtensionPointer]
"Microsoft Compact Optical Mouse 500"	id=13	[XExtensionPointer]
```

BUT, not sure I ever have.

It'd be needed for defining buttons on the tablet - now that understand what the "pad" is - thx!

---

### Post by Favux on 2009-11-15
Hi kgingeri,

Try the alt.touch test3 or working .fdi in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") on the other thread.  And check again for pad.  Sounds like it's suppose to be a sub-device on 'if0'.

---

### Post by kgingeri on 2009-11-15
> **Favux said:**
> Hi kgingeri,

Try the alt.touch test3 or working .fdi in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") on the other thread.  And check again for pad.  Sounds like it's suppose to be a sub-device on 'if0'.

Nope still don't have "pad", but touch is working normal other then the held-button1 effect - as in the last one you posted a few posts back.  
EDIT: I did check the contents in /usr/share/hal/... to be sure I copied it right and it is the right one - pad is assigned under if0.  I did reboot too  ;)

I'm think I will 'hit the hay' now.  I'll catch up again tomorrow.

---

### Post by Favux on 2009-11-15
Hi kgingeri,

Thanks for checking into that.  So my hare brained idea that the pad may be on the 'if1' udi still isn't ruled out.

With the info.callout and pad stuff removed from touch, other than removing one or both (esp. CommonDBG) of the:
```
	<merge key="input.x11_options.DebugLevel" type="string">12</merge>
	<merge key="input.x11_options.CommonDBG" type="string">12</merge>
```
lines I can't see how the .fdi would be causing "held-button1 effect".

---

### Post by Ayuthia on 2009-11-15
I have created a pre-patched source of ob1kenobi's source and placed it in the first post for those who want to try it out.

I have also bumped up the version that we are testing with up to 0.8.5-4.  I have added the overflow rule that ob1kenobi mentioned but I dropped it down to 9 bytes instead of 18.  I have not switched this one over to the TabletPC version yet.  If the pen and touch start to work again with this version, we might continue with it and merge some of the TabletPC source to it.

The "held button-1 effect" is most likely with the code.  It could be that the double-tap is not getting cleared correctly.  Please try the new version to see if it is still there.

---

### Post by marek_online on 2009-11-15
Tried the new patch, with both the included fdi and Favux's new test4 fdi. Found the same behaviour for both.

I have the same mouse movement as kgingeri - held-button 1, absolute to my screen. If it makes any difference at this stage, there's no pressure in the GIMP that I can see.

I've attached the Xorg.0.logs for each session, and the messages file has both separated by a reboot.

Edit:
Oh, and here's the output to xinput --list --short:
```
"Virtual core pointer"  id=0    [XPointer]
"Virtual core keyboard" id=1    [XKeyboard]
"stylus"        id=2    [XExtensionKeyboard]
"eraser"        id=3    [XExtensionKeyboard]
"touch" id=4    [XExtensionKeyboard]
"pad"   id=5    [XExtensionKeyboard]
"AT Translated Set 2 keyboard"  id=6    [XExtensionKeyboard]
"DELL DELL USB Keyboard"        id=7    [XExtensionKeyboard]
"Foxlink Webcam"        id=8    [XExtensionKeyboard]
"Sleep Button"  id=9    [XExtensionKeyboard]
"Video Bus"     id=10   [XExtensionKeyboard]
"Power Button"  id=11   [XExtensionKeyboard]
"Macintosh mouse button emulation"      id=12   [XExtensionPointer]
"ImExPS/2 Generic Explorer Mouse"       id=13   [XExtensionPointer]
"Logitech Optical USB Mouse"    id=14   [XExtensionPointer]
```

---

### Post by rebecca2525 on 2009-11-15
I'm using patch 18 right now. I have touch! (But no stylus or eraser events are being picked up.) I have that left-button-pressed effect, too. I also noticed that it's working in absolute coordinates like a stylus and not relative like a touchpad. I.e. if I lift my finger and place it elsewhere, the cursor jumps to that position instead of staying where it was. In Vista, touch works like a touchpad. And the scale seems to be wrong, if I touch the lower right corner of the the touchpad, I end up roughly in the middle of the screen. [I]EDIT: Now I have (see post  below): When I'm in the middle of my touchpad the cursor is in the lower right corner.
[/I] 
I tried various taps and multi-touch gestures and tablet buttons, they all produce some data in var/log/messages. See attachment.

EDIT: I recall it was mentioned that the code is using some code from a touchscreen device, that would explain the relative/absolute coordinate stuff. And this is the CTH-661 (0d3), which is a medium sized tablet, maybe that's what's confusing the scale?

---

### Post by Favux on 2009-11-15
Hi marek_online,

Great!  Touch, but early days.  And you have pad too!  To soon to tell if 'if1' is the right place.  Could you post your lshal?


Hi rebecca2525,

Outstanding!  Third person with touch.  We're onto something.
> I lift my finger and place it elsewhere, the cursor jumps to that position instead of staying where it was.
That's how my touch screen behaves.

By the way thank you for the output earlier.  That helped alot.  Ayuthia wanted to look at the .fdi again to see if we could direct the other event to touch.  That's why I asked for that output.

Are you seeing pad also?

---

### Post by rebecca2525 on 2009-11-15
Yeah, I do see pad:

```
$ xsetwacom list
pad     pad
touch     touch
eraser     eraser
stylus     stylus
$ xinput --list --short   
"Virtual core pointer"    id=0    [XPointer]
"Virtual core keyboard"    id=1    [XKeyboard]
"Video Bus"    id=2    [XExtensionKeyboard]
"ThinkPad Extra Buttons"    id=3    [XExtensionKeyboard]
"AT Translated Set 2 keyboard"    id=4    [XExtensionKeyboard]
"Integrated Camera"    id=5    [XExtensionKeyboard]
"Sleep Button"    id=6    [XExtensionKeyboard]
"Power Button"    id=7    [XExtensionKeyboard]
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
"TPPS/2 IBM TrackPoint"    id=9    [XExtensionPointer]
"SynPS/2 Synaptics TouchPad"    id=10    [XExtensionPointer]
"pad"    id=11    [XExtensionKeyboard]
"touch"    id=12    [XExtensionKeyboard]
"eraser"    id=13    [XExtensionKeyboard]
"stylus"    id=14    [XExtensionKeyboard]
```

---

### Post by dnprossi on 2009-11-15
I also have touch, but not until [COLOR="Red"]changing fdi[/COLOR] to first test fdi [here]("http://ubuntuforums.org/showthread.php?t=1321238&page=3") and then trying favuk's test3 (Favux_Bamboo-Pen&Touch-alt.touch_test3_10-wacom.fdi.txt).

-The first gives correct touch movement as in windows but no click and errors in wacomcpl
-favuk's test3 gives touch and click but with jumping all over cursor, as reported by rebecca2525, and no errors in wacomcpl and pad is back..

was not there for a while and look at all that happened, WOW!!! Amazing!!

---

### Post by Favux on 2009-11-15
Hi rebecca2525,

Good, pad also.  I'm assuming marek_online and dnprossi have stylus also, so I don't know why you don't.  I guess I'd check and make sure you only have one .fdi installed.


Hi dnprossi,

Cool, isn't it?  I'm sure now that we have touch active Ayuthia will get it zeroed in.  Pad, and in wacomcpl.  Great!

---

### Post by dnprossi on 2009-11-15
> **Favux said:**
> 
Cool, isn't it?  I'm sure now that we have touch active Ayuthia will get it zeroed in.  Pad, and in wacomcpl.  Great!

Hi to you too favux, its just too cool, can't stop meandering on this thread for more...

Nope, no stylus but playing with fdi so.. Stylus is pinky touching pad...:D

---

### Post by rebecca2525 on 2009-11-15
> **Favux said:**
> I guess I'd check and make sure you only have one .fdi installed.

Oh, good idea! [COLOR=Red]Seems that the hal package installs a */usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi* file, which has something about Wacom in it.[/COLOR] (On Debian, anyway.) I removed it, and now things are different. Will report back soon...

EDIT: Still no stylus or eraser, I still have pad, touch, eraser and stylus in *xsetwacom list*. What has changed is the scale stuff: Now when I'm in the middle of my touchpad the cursor is in the lower right corner (the inverse of what I had before...).

New logs attached.

---

### Post by dnprossi on 2009-11-15
> **rebecca2525 said:**
> 
EDIT: Still no stylus or eraser, I still have pad, touch, eraser and stylus in *xsetwacom list*. What has changed is the scale stuff: Now when I'm in the middle of my touchpad the cursor is in the lower right corner (the inverse of what I had before...).


Hi rebecca2525,
what fdi are you using? depending on which one things change drastically..

The one auto-installed did not work at all.

the one on post [#28 here]("http://ubuntuforums.org/showpost.php?p=8289576&postcount=28"): will make touch work correctly but no click and
Favux_Bamboo-Pen&Touch-alt.touch_test3_10-wacom.fdi.txt [**here**]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") will work as a stylus with continuous click (selection enabled) and center is correct...

NO STYLUS YET...

I also have 10-tabletPCs.fdi on ubuntu karmic but removing and restoring it did not have any effect...

At least for me...

---

### Post by rebecca2525 on 2009-11-15
I'm using the one that came with the prepatched linuxwacom-0.8.5-4 patch 18 tar file in the first post. It seems to provoke a left-click as soon as you put your finger on the pad to move the cursor, and then, of course, you drag a selection when moving the cursor; and it works with absolute coordinates. (sounds what you are describing for *Favux_Bamboo-Pen&Touch-alt.touch_test3_10-wacom.fdi.txt...*

---

### Post by dnprossi on 2009-11-15
> **rebecca2525 said:**
> I'm using the one that came with the prepatched linuxwacom-0.8.5-4 patch 18 tar file in the first post. It seems to provoke a left-click as soon as you put your finger on the pad to move the cursor, and then, of course, you drag a selection when moving the cursor; and it works with absolute coordinates. (sounds what you are describing for *Favux_Bamboo-Pen&Touch-alt.touch_test3_10-wacom.fdi.txt...*

Confirmed... /src/util/10-linuxwacom.fdi is the same as Favux's..
Auto-installed one is not the same and does not work...

---

### Post by Ayuthia on 2009-11-15
Has anyone tried ob1kenobi's version to confirm that it works for pen and touch?

Just to make sure that I understand, the pre-patch source for the patch 18 does not work.  Is that correct?

---

### Post by dnprossi on 2009-11-15
> **Ayuthia said:**
> Has anyone tried ob1kenobi's version to confirm that it works for pen and touch?

Just to make sure that I understand, the pre-patch source for the patch 18 does not work.  Is that correct?

Haven't tried, will now and let you know...

---

### Post by dnprossi on 2009-11-15
Installed ob1kenobi's version
Stylus works but no visual touch movement..
messages.log is getting messages from touch..

Stylus messages: 02 00
Touch messages: 02 f1
....

touch data in xorg.0.log
```

xf86WcmReady for touch with 1 numbers of data
xf86WcmReadPacket: device=/dev/input/event9 fd=41 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 96 bytes

```

---

### Post by marek_online on 2009-11-15
> **Favux said:**
> Hi marek_online,

Great!  Touch, but early days.  And you have pad too!  To soon to tell if 'if1' is the right place.  Could you post your lshal?


lshal output attached. I'm not getting any stylus from the device with the current patch. I haven't tried ob1kenobi's yet though. Will have a look at that now, see if I get the same as dnprossi.

---

### Post by dnprossi on 2009-11-15
> **Ayuthia said:**
> Has anyone tried ob1kenobi's version to confirm that it works for pen and touch?

Just to make sure that I understand, the pre-patch source for the patch 18 does not work.  Is that correct?

pre-patch source patch 18 works. not with auto-installed fdi but with one from /src/util or from #28 post.
No stylus
touch works.
with /src/util fdi touch works like a stylus with absolute coordinates and in click drag mode..
with test fdi in #28 post touch works as expected.. no click drag mode...

---

### Post by ob1kenobi on 2009-11-15
> **dnprossi said:**
> Installed ob1kenobi's version
Stylus works but no visual touch movement..
messages.log is getting messages from touch..

Stylus messages: 02 00
Touch messages: 02 f1
....



What type of tablet do you have? and do you have a coffee cup sitting on button 1 by chance?

---

### Post by dnprossi on 2009-11-15
> **ob1kenobi said:**
> What type of tablet do you have? and do you have a coffee cup sitting on button 1 by chance?

hi ob1kenobi, 
0xd2 tablet no coffee cup... should things be different??

---

### Post by ob1kenobi on 2009-11-15
> **dnprossi said:**
> hi ob1kenobi, 
0xd2 tablet no coffee cup... should things be different??

I'd need to see the whole buffer with some changing data probably... on my 0xd1 the second byte has button status in the lower nibble of byte 1 where you are showing 0xf1

---

### Post by dnprossi on 2009-11-15
> **ob1kenobi said:**
> I'd need to see the whole buffer with some changing data probably... on my 0xd1 the second byte has button status in the lower nibble of byte 1 where you are showing 0xf1

sorry must have inverted:
messages from touch
```

02 00 72 80 b2 00 a1 80 b0 00 9d 00 00 00 00 00 80 11 00 00 
02 00 74 80 c6 00 9c 80 c4 00 9b 00 00 00 00 00 81 11 00 00 
02 00 89 80 d2 00 97 80 d1 00 95 00 00 00 00 00 80 11 00 00 
02 00 6a 80 e7 00 8a 80 e6 00 88 00 00 00 00 00 81 11 00 00 
02 00 59 80 f7 00 88 80 f2 00 86 00 00 00 00 00 80 11 00 00 
02 00 72 81 12 00 7d 81 10 00 77 00 00 00 00 00 81 11 00 00 

```

Buttons on left from top to bottom
```

02 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
02 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
02 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
02 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

```

messages from stylus
```

02 f1 45 1e 70 0f 93 01 1a 02 f1 56 1e 7c 0f 93 01 1a 
02 f1 60 1e b9 0f 9c 01 19 02 f1 53 1e e0 0f ad 01 19 
02 f1 fd 1d 7f 10 c0 01 19 02 f1 ea 1d a7 10 c1 01 1a 
02 f1 e9 1d c6 10 b5 01 1a 02 f1 f9 1d ca 10 ac 01 19 

```

---

### Post by marek_online on 2009-11-15
Weird. I tried ob1kenobi's and get no movement with stylus or touch, but do get data in /var/log/messages. Strangely, it actually inhibits my mouse for some reason (it's a laptop with an external mouse - the mousepad works fine, the usb mouse doesn't work at all).

I have the 0xd1 as well, so I'm a little confused.

Logs attached.

---

### Post by dnprossi on 2009-11-15
> **marek_online said:**
> Weird. I tried ob1kenobi's and get no movement with stylus or touch.

probably fdi problem look [here]("http://ubuntuforums.org/showpost.php?p=8320678&postcount=249")

---

### Post by ob1kenobi on 2009-11-15
> **dnprossi said:**
> sorry must have inverted:
messages from touch


Good, I thought that was going to be a real pain between models.  A preliminary break down of this data is:

```

 [FONT=Courier New]  1     2     3         4          5            6        7      8    9     10
| 02 | 00 | 72 80 b2 | 00 a1 | 80 b0 00 9d | 00 00 00 | 00 00 | 80 | 11 | 00 00 

1 - always 02
2 - bits 1 - 4 are on for button presses 1 through 4
3 - has to be byte swapped to 80b272 then it breaks down as
        upper bit denotes finger 1 down (note these three bytes make up the x position with this one flag and a mask of 0x1ffff for the reordered bytes
4 - y position for finger 1, but must be swapped with wacom_be16_to_cpu
5 - I don't know what this is yet, it looks like another set of coordinates, so it may be distance between two fingers
6 - x for finger 2, needs to be swapped around like field 3
7 - y for finger 2, same be16 conversion required
8 - don't know yet, but the upper bit is set when there is a finger down and the lower is set when your finger is on the right half of the pad
9 - upper nibble bits 1-2 indicate the number of finger points detected (looks like it maxes at 3.  lower nibble bits 1-2 appear to be binary determination of if there is a finger span detected (2) or if the fingers are close together (1)
10 - unused afaik[/FONT] 


```

---

### Post by kgingeri on 2009-11-15
Hey, those of you who have pad, try to use xsetwacom to assign buttons.
For example:

```
$ xsetwacom set pad Button1 "core key Enter"
```
This should trigger the top button to act as Enter.

For a list of all the settings you can play with, do:
```
$ xsetwacom list param
```

Gonna try to get my pad working.

EDIT: got pad working with prepatch and Favux's test3 fdi. I can use **xsetwacom**  but **no errors** and **no** action.  Maybe there are no hooks in the code yet.  Anyway, we do need touch working for sure first.  
EDIT: Interesting tho, X does keep track of the value:
```
$ xsetwacom set pad Button1 "key Enter"
$ xsetwacom get pad Button1
KEY  Enter
```

---

### Post by kgingeri on 2009-11-15
Here is something interesting.  It looks like touch is getting set as stylus?!  Here is the last part of changes in Xorg.0.log when I replug my tablet (note bolded - these are touch params, not stylus?):
```
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) config/hal: Adding input device stylus
(**) stylus: always reports core events
(**) stylus device is /dev/input/event9
(**) Option "DebugLevel" "12"
(**) WACOM: stylus debug level set to 12
(**) Option "CommonDBG" "12"
(**) WACOM: stylus tablet common debug level set to 12
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) stylus: reading USB link
(**) stylus: threshold = 61
(**) stylus: max x set to 480 
(**) stylus: max y set to 320 
(**) stylus: max z = 1023
(**) /dev/input/event9: Tablet PC buttons are on 
(**) /dev/input/event9: Touch is enabled 
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
BEGIN xf86WcmProc dev=0x98dd1c8 priv=0x9a96720 type=stylus(stylus) flags=16641 fd=-1 what=INIT
xf86WcmDevOpen
usbDetectConfig 
xf86WcmRegisterX11Devices (stylus) 5 buttons, 5 keys, 6 axes
Wacom "stylus" **max X=480 max Y=320** resol X=2540 resol Y=2540
Wacom device "stylus" top X=0 top Y=0 bottom X=0 bottom Y=0 
xf86WcmInitArea
xf86WcmInitialScreens for "stylus" number of screen=1 
xf86WcmInitialScreens for "stylus" topX[0]=0 topY[0]=0 bottomX[0]=1024 bottomY[0]=600 
xf86WcmRotateTablet for "stylus" 
rotateOneTool for "stylus" 
xf86WcmMappingFactor 
xf86WcmVirtaul**TabletSize for "stylus" x=480 y=320** 
xf86WcmMappingFactor Active tablet area x=480 y=320 (virtual tablet area x=480 y=320) map to maxWidth =1024 maxHeight =600
X factor = 2.13, Y factor = 1.88
xf86WcmMappingFactor 
xf86WcmVirtaulTabletSize for "stylus" x=480 y=320 
xf86WcmMappingFactor Active tablet area x=480 y=320 (virtual tablet area x=480 y=320) map to maxWidth =1024 maxHeight =600
X factor = 2.13, Y factor = 1.88
END xf86WcmProc Success 
BEGIN xf86WcmProc dev=0x98dd1c8 priv=0x9a96720 type=stylus(stylus) flags=16641 fd=18 what=ON
xf86WcmDevOpen
END xf86WcmProc Success 
```

---

### Post by Favux on 2009-11-15
Hi everyone and kgingeri,

Marek_onlines lshal shows the pad is being set up on 'if1'!  Maybe it can set up on either.  Kgingeri can you try this .fdi and see if you can get at least the same response with pad as with alt.touch test3?  I took the CommonDBG line out of 'if1'.  It's suppose to apply to the whole tablet and I've never been sure if using it for each device was right.  Basically all Wacom tablets just have one udi, 'if0'.  Since the pad shows up on either...

Touch showing up as stylus I think is the code.  We could try adding Touch "on" to the .fdi but I doubt that would do anything.

---

### Post by dnprossi on 2009-11-15
if you use [COLOR="Red"]fdi[/COLOR] from post [COLOR="Red"]#28[/COLOR] touch will work as touch and not as stylus...

that is what happened with ayuthia's 0.8.5-4

does not work with ob1kenobi's...

---

### Post by ob1kenobi on 2009-11-15
> **Favux said:**
> Hi everyone and kgingeri,

Marek_onlines lshal shows the pad is being set up on 'if1'!  Maybe it can set up on either.  Kgingeri can you try this .fdi and see if you can get at least the same response with pad as with alt.touch test3?  I took the CommonDBG line out of 'if1'.  It's suppose to apply to the whole tablet and I've never been sure if using it for each device was right.  Basically all Wacom tablets just have one udi, 'if0'.  Since the pad shows up on either...


from the linuxwacom website, it appears the pad as they refer to it is the "buttons" on the old larger pads around the edge (I actually have one).  These smaller tablets don't have those stylus actuated buttons on the tablet so I don't think it really applies to anything.  The hard buttons on the CTH-460 only show up in the touch message not the stylus message.

> 
Touch showing up as stylus I think is the code.  We could try adding Touch "on" to the .fdi but I doubt that would do anything.Still working on that part, I have the mouse moving with my finger now, but trying to figure out the scaling to the screen.  I've got dual screens and it says it's scaling to the full resolution, but it only moves on half of one screen.

```

xf86WcmEvent: c=0 i=3 t=0 s=0 x=17911 y=13104 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=4 
xf86WcmFilterCoord with common->wcmRawSample = 4 
xf86WcmSuppress at level = 2 return value = 2
commonDispatchDevice device type = 2
tool id=2 for Wacom Bamboo P&T 4x5
[touch] o_prox=true x=8956 y=6566 z=0 b=false b=0 tx=0 ty=0 wl=0 rot=0 th=0
[Wacom Bamboo P&T 4x5] abs prox=1    x=8956    y=6566    z=0    v3=0    v4=0    v5=0    id=3    serial=0    button=false    buttons=0
xf86WcmSetScreen v0=8956 v1=6566 currentScreen=0
xf86WcmMappingFactor 
xf86WcmVirtaulTabletSize for "Wacom Bamboo P&T 4x5" x=17920 y=17920 
xf86WcmMappingFactor Active tablet area x=17920 y=17920 (virtual tablet area x=17920 y=17920) map to maxWidth =3600 maxHeight =1200
X factor = 0.201, Y factor = 0.067
xf86WcmReady for Wacom Bamboo P&T 4x5 with 0 numbers of data
xf86WcmDevReadInput: Read (1)
xf86WcmReady for Wacom Bamboo P&T 4x5 with 1 numbers of data
xf86WcmReadPacket: device=/dev/input/event9 fd=56 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 120 bytes

```

---

### Post by Favux on 2009-11-15
Hi dnprossi,

Isn't the .fdi in post #28 the one where Ayuthia commented out touch?  So it isn't linuxwacom running touch.  It's probably evdev as a touchpad if you check.


Hi ob1kenobi,

It seems that would be a change in Wacom conventions to not direct tablet buttons through pad.  They are not all "stylus actuated buttons".  Usually it's a cluster of 4 physical buttons around a slider.  But I'm not arguing.  It's interesting you see the buttons on "touch" ('if1'?).

You'll need to add something like:
```
          <merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
          <merge key="input.x11_options.TVResolution" type="string">1440x900,1280x1024</merge>
          <merge key="input.x11_options.ScreenNo" type="string">0</merge>
```
Both to stylus and touch.

---

### Post by ob1kenobi on 2009-11-15
> 
You'll need to add something like:
```
          <merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
          <merge key="input.x11_options.TVResolution" type="string">1440x900,1280x1024</merge>
          <merge key="input.x11_options.ScreenNo" type="string">0</merge>
```Both to stylus and touch.

Actually stylus works in the full virtual resolution across both screens, just the touch doesn't scale correctly yet for some reason.  TwinView is only supposed to be for nvidia (i've got an onboard ati)

---

### Post by Moophius on 2009-11-15
I tried the new update, and I'm getting a new error:

FATAL: Module wacom not found.

---

### Post by Favux on 2009-11-15
Hi Moophius,

Which .fdi are you using?   Your lshal shows both 'if0' and 'if1', so the test4 or 5 should work for you.  I hope.


Hi ob1kenobi,

Sorry, I misunderstood.  Stylus showing up on half of both screens is common when things aren't defined.

---

### Post by GolemdX on 2009-11-15
I just noticed... doesn't touch only work in the PEN portion of the tablet? There's a white rectangle on it to show the pen borders, but touch only seems to work in that area, when normally touch is supposed to work on the whole thing.

---

### Post by Favux on 2009-11-15
Hi GolemdX,

I thought the touch pad was smaller than the digitizer.  That's what ehfortin said in [post #414]("http://ubuntuforums.org/showpost.php?p=8174189&postcount=414") on the other thread:
> However, the touch area is smaller. For the pen, we have 8.5 x 5.4 inches (that's what I used and multiply by 2540 to get to the right size of the tablet). For the touch area, we have 7.5 x 5.1 inches.
Are you saying it's the reverse?

---

### Post by dnprossi on 2009-11-15
> **Favux said:**
> Hi dnprossi,
Isn't the .fdi in post #28 the one where Ayuthia commented out touch?  So it isn't linuxwacom running touch.  It's probably evdev as a touchpad if you check.


Removed comments... but probably still evdev... just a test...

---

### Post by kgingeri on 2009-11-15
> **GolemdX said:**
> I just noticed... doesn't touch only work in the PEN portion of the tablet? There's a white rectangle on it to show the pen borders, but touch only seems to work in that area, when normally touch is supposed to work on the whole thing.

Nope, even Wacom specs mention that touch area is smaller.  I can't remember where I saw it but I think it was either in the manual (specs) or right on their web site.
[COLOR="DarkRed"]EDIT: the pen area is the larger area.  Here's specs from manual
Touch active area (W x D) 125.0 x 85.0 mm (4.92 x 3.35 in)
Pen active area (W x D)   147.2 x 92.0 mm (5.80 x 3.62 in)[/COLOR]

Favux, trying your fdi.  (took a nap, as I figured everyone else had ;))

UPDATE: Nope same thing Favux

---

### Post by Ayuthia on 2009-11-15
For those who are looking for the buttons to work with my set of patches, I have not set up the buttons to be sent to X yet.  I was wanting to see us get the touch portion going.

I am trying to catch up after being out all day today.  Is the touch resolution correct with patch 18 or is it off?  From dnprossi's post (#140), the usbproperties.txt shows that the resolution is 480x320.  It also sounded like from the group that there is pressure readings coming from the touch also.

ob1kenobi, the stylus and touch data for the 0xd series all report the information in the same way.  Of course the Bamboo Pen only reports stylus data and the Bamboo Touch only reports touch.

I was thinking that the touch only reported two fingers in Windows/Mac.  Is that correct?

---

### Post by rebecca2525 on 2009-11-15
Yeah, pen area is larger than touch. For my medium sized tablet:

pen: 217mmx 137mm
touch: 190mm x 130mm

---

### Post by rebecca2525 on 2009-11-15
> **Ayuthia said:**
> I am trying to catch up after being out all day today.  Is the touch resolution correct with patch 18 or is it off?

On my medium sized tablet (CTH-661, 0d3), when I'm in the middle of my touchpad the cursor is in the lower right corner of the screen. (patch 18 and the fdi that comes with it)

---

### Post by Ayuthia on 2009-11-15
> **rebecca2525 said:**
> On my medium sized tablet (CTH-661, 0d3), when I'm in the middle of my touchpad the cursor is in the lower right corner of the screen. (patch 18 and the fdi that comes with it)

Yes.  You have the bigger tablet if I recall correctly.  I have not found the correct resolution for yours yet.  I am going to try to double yours as soon as I see if I can use your id in the code.

EDIT:
Actually, instead of guessing, can you do me a favor and draw a line with your finger from the top left of the pad to the bottom right?  Once you do that, please submit your /var/log/messages data for it.  We can figure it out from there.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> For those who are looking for the buttons to work with my set of patches, I have not set up the buttons to be sent to X yet.  I was wanting to see us get the touch portion going.

I am trying to catch up after being out all day today.  Is the touch resolution correct with patch 18 or is it off?  From dnprossi's post (#140), the usbproperties.txt shows that the resolution is 480x320.  It also sounded like from the group that there is pressure readings coming from the touch also.

ob1kenobi, the stylus and touch data for the 0xd series all report the information in the same way.  Of course the Bamboo Pen only reports stylus data and the Bamboo Touch only reports touch.

I was thinking that the touch only reported two fingers in Windows/Mac.  Is that correct?

Ayuthia, my last test using the pre-patch archive (may be from the test5 fdi file) left me with only partial screen to touch.  It was full screen area before - looks like half now. (forgot to mention that Favux).  Sorry, I didn't mean to side track us - I'll forget about buttons for now.  ;)

Should we be testing using the pre-patch?
I will reinstall an older fdi and test again.

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Ayuthia, my last test using the pre-patch archive (may be from the test5 fdi file) left me with only partial screen to touch.  It was full screen area before - looks like half now. (forgot to mention that Favux).  Sorry, I didn't mean to side track us - I'll forget about buttons for now.  ;)

Should we be testing using the pre-patch?
I will reinstall an older fdi and test again.

I am about to send out a new patch.  It will include the button data (as long as I put it in the correct place and initialized it correctly).

I am not going to update the fdi for this one only because it does not look like we have settled on one yet.  If there is one that seems to be working somewhat, let me know and I can move that one in for the next release.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> I am about to send out a new patch.  It will include the button data (as long as I put it in the correct place and initialized it correctly).

I am not going to update the fdi for this one only because it does not look like we have settled on one yet.  If there is one that seems to be working somewhat, let me know and I can move that one in for the next release.

Ok, my current testing is using your prepatch and Favux's test4 fdi and things are good as in full screen (absolute) navigation - still have constant selection when using touch.  Don't think we've seen better than that.  :)

[I][COLOR="DimGray"]PS. Don't fuss with button stuff.  I just thought if code supported it I could work on the xsetwacom stuff for it and thus have info ready for wacomcpl patchs - it's no big deal tho, really. 
[/COLOR][/I]

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Ok, my current testing is using your prepatch and Favux's test4 fdi and things are good as in full screen (absolute) navigation - still have constant selection when using touch.  Don't think we've seen better than that.  :)

[I][COLOR="DimGray"]PS. Don't fuss with button stuff.  I just thought if code supported it I could work on the xsetwacom stuff for it and thus have info ready for wacomcpl patchs - it's no big deal tho, really. 
[/COLOR][/I]

I will get the test4 fdi for the next patch release.  I will edit the first post to point to that fdi for now.

I have made the changes to hopefully include the button data.  I am also trying to see if I can change the resolution for rebecca2525's device.  If we can get the touch data from the device, we can get a more accurate measure.

EDIT:  I see that the test 4 fdi is at [post 222]("http://ubuntuforums.org/showpost.php?p=8319667&postcount=222").  Is that correct?

---

### Post by kgingeri on 2009-11-15
> **Favux said:**
> Hi everyone and kgingeri,

Marek_onlines lshal shows the pad is being set up on 'if1'!  Maybe it can set up on either.  Kgingeri can you try this .fdi and see if you can get at least the same response with pad as with alt.touch test3?  I took the CommonDBG line out of 'if1'.  It's suppose to apply to the whole tablet and I've never been sure if using it for each device was right.  Basically all Wacom tablets just have one udi, 'if0'.  Since the pad shows up on either...

Touch showing up as stylus I think is the code.  We could try adding Touch "on" to the .fdi but I doubt that would do anything.

Favux, I forgot to mention and didn't realize it right away, but it looks like your test5 fdi cut my touch rez in about half.  I could only address the upper left quarter of my screen area.  Does that make sense?

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> I will get the test4 fdi for the next patch release.  I will edit the first post to point to that fdi for now.

I have made the changes to hopefully include the button data.  I am also trying to see if I can change the resolution for rebecca2525's device.  If we can get the touch data from the device, we can get a more accurate measure.

EDIT:  I see that the test 4 fdi is at [post 222]("http://ubuntuforums.org/showpost.php?p=8319667&postcount=222").  Is that correct?

Yes - that is the one.  BUT I just downloaded and installed patch 19 and whatever fdi is there seems to work the same.  I still have left button on constantly - but not sure what we're testing for at this point.

---

### Post by kgingeri on 2009-11-15
Ayuthia, just a thought.  I noticed that xsetwacom has a ClickForce threshold setting.  It doesn't seem to do anything for touch, but what if that threshold is 0 - we'd have constant left button action like we are seeing - not?!

EDIT: i.e...
```
$ xsetwacom get touch ClickForce
6
$ xsetwacom set touch ClickForce 32
Set: Value for 'ClickForce' (32) out of range (1 - 21)
$ xsetwacom set touch ClickForce 21
$ xsetwacom get touch ClickForce
21
```
...makes no difference - so maybe not

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Yes - that is the one.  BUT I just downloaded and installed patch 19 and whatever fdi is there seems to work the same.  I still have left button on constantly - but not sure what we're testing for at this point.

I think that I have the buttons.  I am not for sure what they are going to do though.  You should be able to define them through xsetwacom now though.  I also wanted to be sure that the resolution did not get messed up on the smaller sized tablets.

Can you post your Xorg.0.log when you use the touch?  Also, please test the pen and submit the /var/log/messages.  I added some debug messages to see if I am running into some issues with reporting the pen.

I am going to check on the left button issue.  The button is not getting reset when the finger is lifted.

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Ayuthia, just a thought.  I noticed that xsetwacom has a ClickForce threshold setting.  It doesn't seem to do anything for touch, but what if that threshold is 0 - we'd have constant left button action like we are seeing - not?!

The issue is that there is a key that I need to send over to the X wcmUSB.c that will tell it to remove the click.  With all the coding that I have done for my N-Trig device, you would think that I would know that key sequence by now.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> I think that I have the buttons.  I am not for sure what they are going to do though.  You should be able to define them through xsetwacom now though.  I also wanted to be sure that the resolution did not get messed up on the smaller sized tablets.

Can you post your Xorg.0.log when you use the touch?  Also, please test the pen and submit the /var/log/messages.  I added some debug messages to see if I am running into some issues with reporting the pen...

Nothing from xsetwacom on buttons - I tried all 3 pad, touch and stylus.

No stylus action or data in Xorg - see attached.

My /var/log/messages for the stylus was a lot of this, no matter what I did, buttons etc...
```
Nov 15 20:11:52 kgulnb kernel: [ 1335.025898] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.041897] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.057898] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.073895] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.085899] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.101894] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.117897] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.133895] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.145898] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.161902] Overflow value: 20
Nov 15 20:11:52 kgulnb kernel: [ 1335.177902] Overflow value: 20
```

EDIT: Ha - fat fingered the name (should be "zero" not "oh") but contents are fine  ;)

---

### Post by Ayuthia on 2009-11-15
Ok.  I have added more debug information for the stylus.  I think that it is there, but it is currently not reporting because I don't have the correct data length.

I think I have made the corrections for the tablet buttons.  I accidentally put the button data with the touch data so it never would have registered.

I am not for sure if I fixed the left click issue yet.  I changed the order of the two key events so hopefully that will clear the flag correctly this time.

If you can attach the /var/log/messages and the Xorg.0.log again for this test (patch 20), we hopefully can get the stylus back.

---

### Post by Ayuthia on 2009-11-15
I need a clarification on the touch left-click.  When you lift your finger of the tablet, does moving the mouse still keep the left-click?

With my touchscreen, the left-click is activated once your finger touches the screen.  It does not get released until the finger is removed.  If you press a button on a site with your finger, it will click it.

Is that how yours is working?

Favux, is that how the TabletPC versions work also?

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> I need a clarification on the touch left-click.  When you lift your finger of the tablet, does moving the mouse still keep the left-click?

With my touchscreen, the left-click is activated once your finger touches the screen.  It does not get released until the finger is removed.  If you press a button on a site with your finger, it will click it.

Is that how yours is working?

Favux, is that how the TabletPC versions work also?

EDIT: Yes Ayuthia (sorry read the post wrong), to reply I used touch - it selected all the text as I moved right down to the 'reply' button.  The cursor changed to a hand and I tapped and here I am replying.

Hope that helps.
Gotta go test patch 20 for you - was doing other stuff for a bit.

---

### Post by Favux on 2009-11-15
Hi Ayuthia and kgingeri,

Yes my touchscreen behaves just like your N-trig.  I think the confusion is that people are expecting touch pad behavior.  It sounds like it may act that way in Windows and OS X.  I suppose that could be coded for.

And just to clarify mine highlights everything too.  It always has.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> Ok.  I have added more debug information for the stylus.  I think that it is there, but it is currently not reporting because I don't have the correct data length.

I think I have made the corrections for the tablet buttons.  I accidentally put the button data with the touch data so it never would have registered.

I am not for sure if I fixed the left click issue yet.  I changed the order of the two key events so hopefully that will clear the flag correctly this time.

If you can attach the /var/log/messages and the Xorg.0.log again for this test (patch 20), we hopefully can get the stylus back.

Ok - same touch cursor action - hi-lites everything you move the mouse over.

No stylus action - nothing in Xorg.0.log for stylus activity and messages give lotsa this:
```
Nov 15 22:05:24 kgulnb kernel: [  546.146380] Overflow value: 20 20
Nov 15 22:05:24 kgulnb kernel: [  546.162355] Overflow value: 20 20
Nov 15 22:05:24 kgulnb kernel: [  546.174349] Overflow value: 20 20
Nov 15 22:05:24 kgulnb kernel: [  546.190337] Overflow value: 20 20
Nov 15 22:05:25 kgulnb kernel: [  547.385764] Overflow value: 20 20
Nov 15 22:05:25 kgulnb kernel: [  547.405757] Overflow value: 20 20
Nov 15 22:05:25 kgulnb kernel: [  547.421740] Overflow value: 20 20
Nov 15 22:05:26 kgulnb kernel: [  547.433737] Overflow value: 20 20
Nov 15 22:05:26 kgulnb kernel: [  547.449725] Overflow value: 20 20
```

I'll test buttons and update this post...

UPDATE: it appears that the first button (stating at top - right-hand orientation) is a middle click - 2nd nothing - 3rd nothing - 4th is right click by default.

However, assigning them is like this
```
$ xsetwacom set pad Button2 "core key T"
$ xsetwacom set pad Button3 "core key E"
```
produces "T" for the first (top) button and E from the last (bottom) button.
Progress there tho!  Other pads have more buttons so it looks like an addressing/index issue.  :)

EDIT: oh setting 1 and 4 have no effect.

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> EDIT: Yes Ayuthia (sorry read the post wrong), to reply I used touch - it selected all the text as I moved right down to the 'reply' button.  The cursor changed to a hand and I tapped and here I am replying.

Hope that helps.
Gotta go test patch 20 for Ayuthia - was doing other stuff for a bit.

I forgot to ask the important question, how does it work on other operating systems?  If it works differently, we can make adjustments to make it work the same way.

So now it looks like we have the multi-finger touch portion left, verify that there is pressure or not, and get the stylus back and operating.

From the testing perspective, we still need confirmation that the Bamboo Pen still works and we still need to get the Bamboo Touch working (we only have one person who has it).

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Ok - same touch cursor action - hi-lites everything you move the mouse over.

No stylus action - nothing in Xorg.0.log for stylus activity and messages give lotsa this:
```
Nov 15 22:05:24 kgulnb kernel: [  546.146380] Overflow value: 20 20
Nov 15 22:05:24 kgulnb kernel: [  546.162355] Overflow value: 20 20
Nov 15 22:05:24 kgulnb kernel: [  546.174349] Overflow value: 20 20
Nov 15 22:05:24 kgulnb kernel: [  546.190337] Overflow value: 20 20
Nov 15 22:05:25 kgulnb kernel: [  547.385764] Overflow value: 20 20
Nov 15 22:05:25 kgulnb kernel: [  547.405757] Overflow value: 20 20
Nov 15 22:05:25 kgulnb kernel: [  547.421740] Overflow value: 20 20
Nov 15 22:05:26 kgulnb kernel: [  547.433737] Overflow value: 20 20
Nov 15 22:05:26 kgulnb kernel: [  547.449725] Overflow value: 20 20
```

I'll test buttons and update this post...

Can you do me a favor and go into src/2.6.28/wacom_sys.c and go to line 94.  Change:
```

        case -EOVERFLOW:
                /* The stylus data for the Pen & Touch reports 20 bytes */
                if (wacom->wacom_wac->features->type == BAMBOO_PT)
                        printk("Overflow value: %d %d\n", urb->actual_length, wacom->wacom_wac->features->pktlen);
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    **urb->actual_length == (wacom->wacom_wac->features->pktlen - 2))**
                        break;
                goto exit;

```
To look like:
```

        case -EOVERFLOW:
                /* The stylus data for the Pen & Touch reports 20 bytes */
                if (wacom->wacom_wac->features->type == BAMBOO_PT)
                        printk("Overflow value: %d %d\n", urb->actual_length, wacom->wacom_wac->features->pktlen);
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    **urb->actual_length == (wacom->wacom_wac->features->pktlen))**
                        break;
                goto exit;

```

Hopefully, that will get the stylus back to reporting again in the kernel module.  However, I am thinking that we will need to make a change in the rules for the stylus because it is thinking that we are going to get a smaller packet.

---

### Post by Favux on 2009-11-15
Hi Ayuthia,

As far as I can tell you've gotten the touch screen working correctly.  The cursor goes to the finger, it clicks, and it drag selects.

Like you say, you need to concentrate on getting the stylus back and then the buttons.

> I forgot to ask the important question, how does it work on other operating systems? If it works differently, we can make adjustments to make it work the same way.
Going back over the posts it does behave differently.  They're expecting a Mac OS X multi-touch style touch pad (well not counting the three and four finger gestures).  I don't know if the new gesture code Ping said is in 5-4 is with the touch screen code.  Is there separate touch (pad-like) code for the E2 and E3?

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> 

EDIT: oh setting 1 and 4 have no effect.
Does buttons 1 and 4 register in /var/log/messages for you still?  Also, do you see anything in Xorg.0.log when you press them?

I think that button 1 and 4 are initialized in one of the functions but I don't see 2 and 3 initialized.  That might mean that we need to change the init values.

EDIT:
Are you saying that 1 and 4 work as the middle and right click or is that how it is supposed to work?

---

### Post by Ayuthia on 2009-11-15
> **Favux said:**
> Hi Ayuthia,

As far as I can tell you've gotten the touch screen working correctly.  The cursor goes to the finger, it clicks, and it drag selects.

Like you say, you need to concentrate on getting the stylus back and then the buttons.


Going back over the posts it does behave differently.  They're expecting a Mac OS X multi-touch style touch pad (well not counting the three and four finger gestures).  I don't know if the new gesture code Ping said is in 5-4 is with the touch screen code.  Is there separate touch (pad-like) code for the E2 and E3?

I am looking at the code right now and it does seem that there are some gesture rules in place for the E2 and E3.  I have not studied it carefully yet though.  There is some info there about touch without capacity. 

Once we get the stylus back, I will look at merging the E2/E3 rules for these devices.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> Does buttons 1 and 4 register in /var/log/messages for you still?  Also, do you see anything in Xorg.0.log when you press them?

I think that button 1 and 4 are initialized in one of the functions but I don't see 2 and 3 initialized.  That might mean that we need to change the init values.

EDIT:
Are you saying that 1 and 4 work as the middle and right click or is that how it is supposed to work?

I will make the changes in wacom_sys and let you know.

Button data for messages is:
```
TNov 15 22:39:54 kgulnb kernel: [ 2615.913911] [wacom-20] data:  0:2 1:1 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:39:54 kgulnb kernel: [ 2615.914022] [wacom-20]: reset tool 14d
Nov 15 22:39:54 kgulnb kernel: [ 2616.001902] [wacom-20] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:39:54 kgulnb kernel: [ 2616.001979] [wacom-20]: reset tool 14d

Nov 15 22:39:57 kgulnb kernel: [ 2618.437909] [wacom-20] data:  0:2 1:2 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:39:57 kgulnb kernel: [ 2618.438010] [wacom-20]: reset tool 14d
Nov 15 22:39:57 kgulnb kernel: [ 2618.501907] [wacom-20] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:39:57 kgulnb kernel: [ 2618.501985] [wacom-20]: reset tool 14d

Nov 15 22:39:58 kgulnb kernel: [ 2619.657901] [wacom-20] data:  0:2 1:4 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:39:58 kgulnb kernel: [ 2619.657979] [wacom-20]: reset tool 14d
Nov 15 22:39:58 kgulnb kernel: [ 2619.741907] [wacom-20] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:39:58 kgulnb kernel: [ 2619.741984] [wacom-20]: reset tool 14d

ENov 15 22:40:01 kgulnb kernel: [ 2622.481908] [wacom-20] data:  0:2 1:8 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:40:01 kgulnb kernel: [ 2622.482017] [wacom-20]: reset tool 14d
Nov 15 22:40:01 kgulnb kernel: [ 2622.589908] [wacom-20] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 22:40:01 kgulnb kernel: [ 2622.589986] [wacom-20]: reset tool 14d
```

Xorg is:
```
**T**xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 80 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 5 events received
usbParseChannel event[0]->type=1 code=257 value=1
usbParseChannel event[1]->type=1 code=325 value=1
USB Pad detected 145 (value=1)
usbParseChannel event[2]->type=3 code=40 value=15
usbParseChannel event[3]->type=4 code=0 value=240
usbParseChannel event[4]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=2 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=0 
initialize Channel data.
commonDispatchDevice device type = 16
tool id=16 for pad
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 80 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 5 events received
usbParseChannel event[0]->type=3 code=40 value=0
usbParseChannel event[1]->type=1 code=257 value=0
usbParseChannel event[2]->type=1 code=325 value=0
USB Pad detected 145 (value=0)
usbParseChannel event[3]->type=4 code=0 value=240
usbParseChannel event[4]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=0 cs=1 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 16
tool id=16 for pad

xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 128 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 4 events received
usbParseChannel event[0]->type=1 code=325 value=1
USB Pad detected 145 (value=1)
usbParseChannel event[1]->type=3 code=40 value=15
usbParseChannel event[2]->type=4 code=0 value=240
usbParseChannel event[3]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=0 
initialize Channel data.
commonDispatchDevice device type = 16
tool id=16 for pad
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 4 events received
usbParseChannel event[0]->type=3 code=40 value=0
usbParseChannel event[1]->type=1 code=325 value=0
USB Pad detected 145 (value=0)
usbParseChannel event[2]->type=4 code=0 value=240
usbParseChannel event[3]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=0 cs=1 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 16
tool id=16 for pad

xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 64 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 4 events received
usbParseChannel event[0]->type=1 code=325 value=1
USB Pad detected 145 (value=1)
usbParseChannel event[1]->type=3 code=40 value=15
usbParseChannel event[2]->type=4 code=0 value=240
usbParseChannel event[3]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=0 
initialize Channel data.
commonDispatchDevice device type = 16
tool id=16 for pad
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 64 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 4 events received
usbParseChannel event[0]->type=3 code=40 value=0
usbParseChannel event[1]->type=1 code=325 value=0
USB Pad detected 145 (value=0)
usbParseChannel event[2]->type=4 code=0 value=240
usbParseChannel event[3]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=0 cs=1 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 16
tool id=16 for pad

**E**xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 80 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 5 events received
usbParseChannel event[0]->type=1 code=260 value=1
usbParseChannel event[1]->type=1 code=325 value=1
USB Pad detected 145 (value=1)
usbParseChannel event[2]->type=3 code=40 value=15
usbParseChannel event[3]->type=4 code=0 value=240
usbParseChannel event[4]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=4 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=0 
initialize Channel data.
commonDispatchDevice device type = 16
tool id=16 for pad
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 80 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 5 events received
usbParseChannel event[0]->type=3 code=40 value=0
usbParseChannel event[1]->type=1 code=260 value=0
usbParseChannel event[2]->type=1 code=325 value=0
USB Pad detected 145 (value=0)
usbParseChannel event[3]->type=4 code=0 value=240
usbParseChannel event[4]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=0 cs=1 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 16
tool id=16 for pad
```

(remember buttons are still assign E and T - see bolding)

As for how touch works on my Mac, it is multi finger (at least 2, not sure if more than that, but there is no indication in settings to allow more) and moving your finger does not stay in constant select - you have to tap (on off quickly) then touch and move to initiate a selection.  Just retested now to be sure.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> ...
EDIT:
Are you saying that 1 and 4 work as the middle and right click or is that how it is supposed to work?

Sorry - missed this.  Yes, correct.  By default they are that way now.  I assigned them the letters T and E for testing. so they are assignable but but they assign as Button2 and Button3.  so...

```
$ xsetwacom set pad Button1 "core key A"
$ xsetwacom set pad Button2 "core key B"
$ xsetwacom set pad Button3 "core key C"
$ xsetwacom set pad Button4 "core key D"
$ # I will press each button 1 thru 4 - top to bottom with buttons on my left - right-handed.  Here are the results...
$ BC

```

---

### Post by Ayuthia on 2009-11-15
One other thing to check, can you check and see if you are getting any pressure for the finger?  If you do, I will go ahead and convert the code to match up with the E2/E3 series.

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> Sorry - missed this.  Yes, correct.  By default they are that way now.  I assigned them the letters T and E for testing. so they are assignable but but they assign as Button2 and Button3.  so...

```
$ xsetwacom set pad Button1 "core key A"
$ xsetwacom set pad Button2 "core key B"
$ xsetwacom set pad Button3 "core key C"
$ xsetwacom set pad Button4 "core key D"
$ # I will press each button 1 thru 4 - top to bottom with buttons on my left - right-handed.  Here are the results...
$ BC

```

I get it now.  Have you tried assigning Button5?  It might be tricky to figure out which button is which number.

EDIT:
Nevermind.  I will see if I can get the other two buttons assigned.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> Can you do me a favor and go into src/2.6.28/wacom_sys.c and go to line 94.  Change:
```

        case -EOVERFLOW:
                /* The stylus data for the Pen & Touch reports 20 bytes */
                if (wacom->wacom_wac->features->type == BAMBOO_PT)
                        printk("Overflow value: %d %d\n", urb->actual_length, wacom->wacom_wac->features->pktlen);
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    **urb->actual_length == (wacom->wacom_wac->features->pktlen - 2))**
                        break;
                goto exit;

```
To look like:
```

        case -EOVERFLOW:
                /* The stylus data for the Pen & Touch reports 20 bytes */
                if (wacom->wacom_wac->features->type == BAMBOO_PT)
                        printk("Overflow value: %d %d\n", urb->actual_length, wacom->wacom_wac->features->pktlen);
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    **urb->actual_length == (wacom->wacom_wac->features->pktlen))**
                        break;
                goto exit;

```

Hopefully, that will get the stylus back to reporting again in the kernel module.  However, I am thinking that we will need to make a change in the rules for the stylus because it is thinking that we are going to get a smaller packet.

BINGO :popcorn: We have stylus data when I took off the "-2" from urb pktlen!!  See attached - it represents a quick near touch and tap with the stylus...

---

### Post by Ayuthia on 2009-11-15
> **kgingeri said:**
> BINGO :popcorn: We have stylus data when I took off the "-2" from urb pktlen!!  See attached - it represents a quick near touch and tap with the stylus...

Great!  Just to be sure that I understand correctly from your log, the information is registering, but it is not working yet.  Is that correct?  If so, I will make the adjustments.

EDIT:
Can you also show me a portion of the stylus data from /var/log/messages?  It will help me see how the packet data is coming over.

---

### Post by ob1kenobi on 2009-11-15
Can you refresh my memory which tablet this is for?

EDIT: And I've got hid data if you're interested in removing the hardcoded x_max/y_max/x_phy/y_phy.

x_phy is at offset i + 5, x_max is at offset i + 8, y_phy is at offset i + 3 and y_max is at offset i + 6.

---

### Post by kgingeri on 2009-11-15
> **ob1kenobi said:**
> Can you refresh my memory which tablet this is for?

0xd1 - Pen & Touch

Bus 002 Device 002: ID 056a:00d1 Wacom Co., Ltd

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> Great!  Just to be sure that I understand correctly from your log, the information is registering, but it is not working yet.  Is that correct?  If so, I will make the adjustments.

EDIT:
Can you also show me a portion of the stylus data from /var/log/messages?  It will help me see how the packet data is coming over.

Hmmm must have forgot - I was going to give you messages - here it is...
(not for the exact same events, but same actions)
```
Nov 15 23:36:02 kgulnb kernel: [ 2077.054956] Overflow value: 20 20
Nov 15 23:36:02 kgulnb kernel: [ 2077.054969] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:02 kgulnb kernel: [ 2077.055041] [wacom-20]: reset tool 14d
Nov 15 23:36:02 kgulnb kernel: [ 2077.070951] Overflow value: 20 20
Nov 15 23:36:02 kgulnb kernel: [ 2077.070963] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:02 kgulnb kernel: [ 2077.071036] [wacom-20]: reset tool 14d
Nov 15 23:36:02 kgulnb kernel: [ 2077.090952] Overflow value: 20 20
Nov 15 23:36:02 kgulnb kernel: [ 2077.090965] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:02 kgulnb kernel: [ 2077.091037] [wacom-20]: reset tool 14d
Nov 15 23:36:02 kgulnb kernel: [ 2077.106957] Overflow value: 20 20
Nov 15 23:36:02 kgulnb kernel: [ 2077.106969] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:02 kgulnb kernel: [ 2077.107042] [wacom-20]: reset tool 14d
Nov 15 23:36:02 kgulnb kernel: [ 2077.406953] Overflow value: 20 20
Nov 15 23:36:02 kgulnb kernel: [ 2077.406965] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:02 kgulnb kernel: [ 2077.407038] [wacom-20]: reset tool 14d
Nov 15 23:36:02 kgulnb kernel: [ 2077.422955] Overflow value: 20 20
Nov 15 23:36:02 kgulnb kernel: [ 2077.422968] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:02 kgulnb kernel: [ 2077.423042] [wacom-20]: reset tool 14d
Nov 15 23:36:03 kgulnb kernel: [ 2077.450943] Overflow value: 20 20
Nov 15 23:36:03 kgulnb kernel: [ 2077.450960] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:f0
Nov 15 23:36:03 kgulnb kernel: [ 2077.451034] [wacom-20]: reset tool 14d
Nov 15 23:36:03 kgulnb kernel: [ 2077.462951] [wacom-20] data:  0:2 1:0 2:1f 3:81 4:5e 5:0 6:e4 7:81 8:5e 9:0 10:e3 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0 19:0
Nov 15 23:36:03 kgulnb kernel: [ 2077.463031] [wacom-20]: X=350 Y=228 pressure=31
Nov 15 23:36:03 kgulnb kernel: [ 2077.466944] Overflow value: 20 20
Nov 15 23:36:03 kgulnb kernel: [ 2077.466961] [wacom-20] data:  0:2 1:f0 2:72 3:24 4:3d 5:19 6:0 7:0 8:9 9:2 10:f0 11:8c 12:24 13:28 14:19 15:0 16:0 17:8 18:2 19:f0
Nov 15 23:36:03 kgulnb kernel: [ 2077.467064] [wacom-20]: reset tool 14d
Nov 15 23:36:03 kgulnb kernel: [ 2077.486959] Overflow value: 20 20
Nov 15 23:36:03 kgulnb kernel: [ 2077.486971] [wacom-20] data:  0:2 1:f0 2:9f 3:24 4:1b 5:19 6:0 7:0 8:8 9:2 10:f0 11:98 12:24 13:10 14:19 15:0 16:0 17:7 18:2 19:f0
Nov 15 23:36:03 kgulnb kernel: [ 2077.487045] [wacom-20]: reset tool 14d
Nov 15 23:36:03 kgulnb kernel: [ 2077.490964] [wacom-20] data:  0:2 1:0 2:1c 3:81 4:60 5:0 6:e2 7:81 8:5f 9:0 10:e2 11:0 12:0 13:0 14:0 15:0 16:81 17:11 18:0 19:0
Nov 15 23:36:03 kgulnb kernel: [ 2077.491073] [wacom-20]: X=352 Y=226 pressure=28
Nov 15 23:36:03 kgulnb kernel: [ 2077.502958] Overflow value: 20 20
Nov 15 23:36:03 kgulnb kernel: [ 2077.502971] [wacom-20] data:  0:2 1:f0 2:85 3:24 4:17 5:19 6:0 7:0 8:5 9:2 10:f0 11:63 12:24 13:2c 14:19 15:0 16:0 17:3 18:2 19:80
Nov 15 23:36:03 kgulnb kernel: [ 2077.503046] [wacom-20]: reset tool 14d
Nov 15 23:36:03 kgulnb kernel: [ 2077.506952] [wacom-20] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:0 10:0 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:0 19:0
Nov 15 23:36:03 kgulnb kernel: [ 2077.507026] [wacom-20]: reset tool 14d
Nov 15 23:36:03 kgulnb kernel: [ 2077.522958] Overflow value: 20 20
Nov 15 23:36:03 kgulnb kernel: [ 2077.522970] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:03 kgulnb kernel: [ 2077.523043] [wacom-20]: reset tool 14d
Nov 15 23:36:03 kgulnb kernel: [ 2077.534960] Overflow value: 20 20
Nov 15 23:36:03 kgulnb kernel: [ 2077.534972] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:0
Nov 15 23:36:03 kgulnb kernel: [ 2077.535044] [wacom-20]: reset tool 14d


Nov 15 23:36:06 kgulnb kernel: [ 2081.174936] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.174944] [wacom-20] data:  0:2 1:0 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:06 kgulnb kernel: [ 2081.174981] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.190956] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.190969] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:06 kgulnb kernel: [ 2081.191042] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.210959] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.210971] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:80 11:0 12:0 13:0 14:0 15:0 16:0 17:0 18:2 19:80
Nov 15 23:36:06 kgulnb kernel: [ 2081.211044] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.230963] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.230976] [wacom-20] data:  0:2 1:80 2:0 3:0 4:0 5:0 6:0 7:0 8:0 9:2 10:f0 11:1a 12:21 13:3a 14:f 15:0 16:0 17:f 18:2 19:f0
Nov 15 23:36:06 kgulnb kernel: [ 2081.231049] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.246953] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.246965] [wacom-20] data:  0:2 1:f0 2:29 3:21 4:2c 5:f 6:0 7:0 8:12 9:2 10:f1 11:39 12:21 13:27 14:f 15:b3 16:2 17:13 18:2 19:f1
Nov 15 23:36:06 kgulnb kernel: [ 2081.247038] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.262941] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.262955] [wacom-20] data:  0:2 1:f1 2:39 3:21 4:24 5:f 6:74 7:2 8:14 9:2 10:f1 11:30 12:21 13:1b 14:f 15:82 16:2 17:15 18:2 19:f1
Nov 15 23:36:06 kgulnb kernel: [ 2081.263028] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.274955] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.274968] [wacom-20] data:  0:2 1:f1 2:34 3:21 4:1c 5:f 6:94 7:2 8:16 9:2 10:f1 11:38 12:21 13:1b 14:f 15:93 16:2 17:16 18:2 19:f1
Nov 15 23:36:06 kgulnb kernel: [ 2081.275042] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.290953] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.290965] [wacom-20] data:  0:2 1:f1 2:36 3:21 4:15 5:f 6:95 7:2 8:18 9:2 10:f1 11:37 12:21 13:15 14:f 15:8f 16:2 17:18 18:2 19:f1
Nov 15 23:36:06 kgulnb kernel: [ 2081.291039] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.306957] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.306969] [wacom-20] data:  0:2 1:f1 2:39 3:21 4:14 5:f 6:8f 7:2 8:18 9:2 10:f1 11:3c 12:21 13:16 14:f 15:8b 16:2 17:19 18:2 19:f1
Nov 15 23:36:06 kgulnb kernel: [ 2081.307043] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.322959] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.322971] [wacom-20] data:  0:2 1:f1 2:39 3:21 4:14 5:f 6:8a 7:2 8:19 9:2 10:f1 11:39 12:21 13:12 14:f 15:93 16:2 17:19 18:2 19:f1
Nov 15 23:36:06 kgulnb kernel: [ 2081.323045] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.334956] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.334969] [wacom-20] data:  0:2 1:f1 2:3a 3:21 4:12 5:f 6:9c 7:2 8:19 9:2 10:f1 11:39 12:21 13:4 14:f 15:7b 16:1 17:19 18:2 19:f0
Nov 15 23:36:06 kgulnb kernel: [ 2081.335043] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.350953] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.350966] [wacom-20] data:  0:2 1:f0 2:37 3:21 4:df 5:e 6:0 7:0 8:17 9:2 10:f0 11:30 12:21 13:b1 14:e 15:0 16:0 17:12 18:2 19:f0
Nov 15 23:36:06 kgulnb kernel: [ 2081.351040] [wacom-20]: reset tool 14d
Nov 15 23:36:06 kgulnb kernel: [ 2081.366936] Overflow value: 20 20
Nov 15 23:36:06 kgulnb kernel: [ 2081.366949] [wacom-20] data:  0:2 1:f0 2:d 3:21 4:7f 5:e 6:0 7:0 8:d 9:2 10:f0 11:f8 12:20 13:59 14:e 15:0 16:0 17:6 18:2 19:80
Nov 15 23:36:06 kgulnb kernel: [ 2081.367023] [wacom-20]: reset tool 14d
```

EDIT: forgot to answer your other question Ayuthia - no I do not have any on screen activity relating to stylus - just log data.

---

### Post by ob1kenobi on 2009-11-15
> **kgingeri said:**
> 0xd1 - Pen & Touch

Bus 002 Device 002: ID 056a:00d1 Wacom Co., Ltd

Yup same as mine.  Touch is 18 and pen is 20 length.  Don't know why taking out the -2 makes it work.  The default buffer length is 20 which is what the urb is requesting and recieves from the pen (i.e. no EOVERFLOW condition).  When it gets 18 is when the EOVERFLOW should occur which is why the -2 was in there.

---

### Post by kgingeri on 2009-11-15
> **Ayuthia said:**
> ...
Great! Just to be sure that I understand correctly from your log, the information is registering, but it is not working yet. Is that correct? If so, I will make the adjustments.
...

Just in case you missed my edit to my last response Ayuthia - no, I do not have stylus activity just data in logs.

---

### Post by Ayuthia on 2009-11-15
> **ob1kenobi said:**
> Can you refresh my memory which tablet this is for?

EDIT: And I've got hid data if you're interested in removing the hardcoded x_max/y_max/x_phy/y_phy.

x_phy is at offset i + 5, x_max is at offset i + 8, y_phy is at offset i + 3 and y_max is at offset i + 6.

How far along are you in your set?  I am thinking that our code is about to sync up together now.  I am going to need to make the code changes to make the touch mimic the TPC code that is out there (I know that yours is coded that way).

The only main difference that I see right now is with the data packet length.  My stylus overflow is showing 18 bytes where the 0xd1 seems to be showing 20.  EDIT:  I thought that yours was a 0xd4.  Why is our rule different?

Can we have another copy of your changes?

kgingeri, did you have a chance to see if there was any pressure showing up for the touch?

Just as a note to everyone else--my next step is to match up the pen and touch rules to the TabletPC.  The rules are the same just the data packet structure might be different.

---

### Post by kgingeri on 2009-11-15
> **ob1kenobi said:**
> Can you refresh my memory which tablet this is for?

EDIT: And I've got hid data if you're interested in removing the hardcoded x_max/y_max/x_phy/y_phy.

x_phy is at offset i + 5, x_max is at offset i + 8, y_phy is at offset i + 3 and y_max is at offset i + 6.

I don't understand Ob1 - there is no i var in the function wacom_probe() - wacom_sys.c?
I do see what looks like your are talking about in the function above - wacom_parse_hid()?

Maybe Ayuthia knows tho and that's more important - unless you want me to do a quick test.  Then give me line #'s

---

### Post by ob1kenobi on 2009-11-15
> **Ayuthia said:**
> How far along are you in your set?  I am thinking that our code is about to sync up together now.  I am going to need to make the code changes to make the touch mimic the TPC code that is out there (I know that yours is coded that way).

I've been rolling some of yours into mine...

> 
The only main difference that I see right now is with the data packet length.  The 0xd4 stylus overflow is showing 18 bytes where the 0xd1 seems to be showing 20.
Like I said, I have a 0xd1 and it reports 18 as the overflow not 20 and I have the PKGLEN default to 20 on mine.

> 
Can we have another copy of your changes?
EDIT: Attached

EDIT 2: I had to move pad back up to the if0 pen device, it was messing up the "touch" virtual tablet area for some reason.  Basically the pad device was grabbing the 480x320 size and touch was left with 0,0 which caused some problems.  I don't like the left click on touch operation right now...  need to figure out how to tap vs move

> 
kgingeri, did you have a chance to see if there was any pressure showing up for the touch?
I am getting pressure data for touch from my latest build...

---

### Post by ob1kenobi on 2009-11-16
> **kgingeri said:**
> I don't understand Ob1 - there is no i var in the function wacom_probe() - wacom_sys.c?
I do see what looks like your are talking about in the function above - wacom_parse_hid()?

Maybe Ayuthia knows tho and that's more important - unless you want me to do a quick test.  Then give me line #'s

It is in wacom_parse_hid... new patch in post [http://ubuntuforums.org/showpost.php?p=8325757&postcount=314](http://ubuntuforums.org/showpost.php?p=8325757&postcount=314) shows

---

### Post by ob1kenobi on 2009-11-16
> **ob1kenobi said:**
> I've been rolling some of yours into mine...
I had to move pad back up to the if0 pen device, it was messing up the "touch" virtual tablet area for some reason.  Basically the pad device was grabbing the 480x320 size and touch was left with 0,0 which caused some problems.  I don't like the left click on touch operation right now...  need to figure out how to tap vs move

I am getting pressure data for touch from my latest build...

Fixed with this fdi.  I now have eraser,cursor,stylus,pad and touch.  Both stylus(pen) and touch move across the full dual screen size 3600x1200.  Tested pressure on pen and touch with gimp (touch is a little weak, you have to press really hard to get it to draw, but there is a difference with how hard you press).

That's it for me for tonight... good luck

---

### Post by Favux on 2009-11-16
Hi ob1kenobi,

OK, pad with stylus would be the consistent with the "standard" .fdi.  You can remove the cursor line under stylus and the info.callout with touch.  That gets us back to only one info.callout to hal-setup-wacom.  So it's basically the equivalent of the alt.touch test3 .fdi or working .fdi in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").  Since pad is setting up with either the only question is if it also works with the Touch only tablet.  Given it's lshal I think it will.

Oh, wait a minute, you were doing something different.
```
	<match key="input.originating_device" contains="if1">
	  <merge key="input.x11_driver" type="string">wacom</merge>
	  <merge key="input.x11_options.Type" type="string">pad</merge>
	  <merge key="input.x11_options.DebugLevel" type="string">12</merge>
          <merge key="input.x11_options.CommonDBG" type="string">12</merge>
	  <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	  <append key="wacom.types" type="strlist">touch</append.
```
Hmmm.

---

### Post by Ayuthia on 2009-11-16
Another set of patches has been created.  We are now merging ob1kenobi's kernel module code with our current changes.  Please note ob1kenobi's previous post (316) about the .fdi file to use.

If you want to use ob1kenobi's changes without patch 20's changes, you can get the source in the first post.

The main difference between the two should only be that the bluetooth data is present in ob1kenobi's source.  The patches that I provided do not have that.

We will now start testing everything!  Please check:
[LIST]
[*]Touch works with pressure
[*]Buttons on the pad all work
[*]Pen works with pressure
[*]Eraser works with pressure
[*]Switching from pen to eraser to pen to eraser works
[*]Two-finger touch does something--I am not for sure what gestures work.
[/LIST]

If the stylus does not work, please try the change in [post 297]("http://ubuntuforums.org/showpost.php?p=8325363&postcount=297").  This is where my source and ob1kenobi's source differed.

ob1kenobi, thanks for the source contribution!

Happy testing!  May the source be with you!  (Sorry.  I just had to do it.)

---

### Post by kgingeri on 2009-11-16
> **ob1kenobi said:**
> Fixed with this fdi.  I now have eraser,cursor,stylus,pad and touch.  Both stylus(pen) and touch move across the full dual screen size 3600x1200.  Tested pressure on pen and touch with gimp (touch is a little weak, you have to press really hard to get it to draw, but there is a difference with how hard you press).

That's it for me for tonight... good luck

No difference (no stylus) for me on this fdi, but I haven't installed your patch from 314 either.  Tomorrow - lights out for me too.

EDIT: Hmmm - guess I didn't refresh my page - didn't see Ayuthia's post above.  I really do need some sleep tho  ;)  *[COLOR="Indigo"]Ha, good to see there's a little sillyness in Ayuthia too ("may the source be with you") - I was trying to think of something good like that [/COLOR]* :lol:

---

### Post by rebecca2525 on 2009-11-16
Whoa, just trying to catch up with three pages of posts... 

Ayuthia, I will send you that scale data as soon as I'm home tonight. 

And since there was confusion as of how the touch should operate: On Windows, it behaves like a touchpad (not like a touchscreen), i.e. it has relative cursor movement and doesn't issue a left click when you put down your finger to move the cursor.

---

### Post by dnprossi on 2009-11-16
**I will hold my tests in this post making references when updated in next posts...**

Tests on:
Acer Aspire 5920g
Ubuntu Desktop Karmic - Kernel Linux 2.6.31-15-generic - 32bit
Wacom Bamboo Fun pen&touch Small - CTH-461 - 0xd2

**My cleaning up batch after each new install...**
```

# rmmod wacom
# rm /lib/modules/$(uname -r)/kernel/drivers/input/tablet/wacom.ko
# rm /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
# rm /lm /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
# apt-get purge wacom-tools xserver-xorg-input-wacom
# apt-get install wacom-tools xserver-xorg-input-wacom xserver-xorg-input-all

```
**+ reboot...**


[B]Test #1
linuxwacom-0.8.5-4-bamboo-[COLOR="Red"]34[/COLOR].tar.bz2 + 
Favux-new-generic_test2_10-linuxwacom.fdi 
Favux-new-generic_test3_10-linuxwacom.fdi[/B]

Stylus: 
[LIST]
[*]Pressure = OK
[*]Buttons hover mode (default) = OK
[*]Eraser = OK
(Gimp: [COLOR="Red"]no need[/COLOR] to setup stylus from pref- input dev)
[/LIST]

Touch:
[LIST]
[*]Works correctly without select effect (default - absolute mode)
[*]Tap once initiates drag selection
[*]Tap twice on folder icon moves away from folder not opening
[*]xsetwacom set touch mode relative - Works as Touchpad
[*]Tap once initiates drag selection only if finger dragging has not already started. So tap stop move finger works. Tap while moving will not work. (dunno if this is clear..):)
[*]Tap twice on folder icon opens folder correctly
[*]Moving finger slowly is jittery and not easy to position on icons buttons etc...
[*]Button 1 = Left-Click now released.
[*]Button 2 = Right-Click
[*]Button 3 = Scroll-Up
[*]Button 4 = Scroll-Down
[*]relative mode. All clicks disabled also when adding second finger on tablet. Pressing any other button on tablet resets to normal. ATTACHED messages.log below
[*]scale correct on reboot
[*]unplug/replug, leads to a wrong scale (confirming rebecca2525's find).
[/LIST]

---

### Post by Ayuthia on 2009-11-16
> **dnprossi said:**
> Confirmed...

WOW!!! you guys worked so hard and fast...

**Touch function default settings in Windows**
**click:** (fast double tap)
Touch with one finger = true
Additional left touch = true
**right click:**
touch with two fingers = true
Additional right touch = true
**drag/selection:**
drag = true
  drag block = false
**movements:**
scroll = true
zoom = true
rotation = true
back and forth = true

**[COLOR="Red"]***Caution***[/COLOR]**
[B]Hand and stylus on pad can move folders when not wanted. Sporadic freezes and all mice clicks can be disabled.
Very sensitive....[/B]

Ayuthia's **0.8.5-4-21** pre-patch with **/src/util/10-linuxwacom.fdi**

0.8.5-4-21 GIMP:
Stylus: OK
Stylus Buttons: NONE
Eraser: OK
Touch: YES but working with stylus movement and "click on touch" not working as touchpad movement and "click on fast double tap".
Touch Buttons: Active in messages.log


Ayuthia's **0.8.5-4-21** pre-patch with **ob1kenobi's fdi on post [#316]("http://ubuntuforums.org/showpost.php?p=8325874&postcount=316")**

0.8.5-4-21 GIMP:
Stylus: OK for movement - But no click at all
Stylus Buttons: NONE
Eraser: NONE
Touch: [COLOR="Red"]YES working as touchpad[/COLOR], "not as stylus" - but no click at all.
Touch Buttons: Active in messages.log

same test with ob1kenobi's latest 0.8.5-4 and both fdi's
same as above

Great!  The 0xd2 (Bamboo Craft--right?) works with the merged changes.

Can you help me understand what you mean by sporadic freezes?  When you say that the mouse clicks are disabled, does that also include the right-click?  It sounds like the click is not being cleared correctly somewhere.

Also, can you help clarify 
> Touch: YES but working with stylus movement
EDIT: Ok.  I think this is describing the behavior that ob1kenobi mentioned before the new fdi was used.

If possible, can you attach your /var/log/messages and Xorg.0.log?

---

### Post by dnprossi on 2009-11-16
> **Ayuthia said:**
> Great!  The 0xd2 (Bamboo Craft--right?) works with the merged changes.

Good morning Ayuthia, here afternoon...
yes 0xd2.. Bamboo fun pen & touch CTH-461

> 
Can you help me understand what you mean by sporadic freezes?  When you say that the mouse clicks are disabled, does that also include the right-click?  It sounds like the click is not being cleared correctly somewhere.


I'll try... When I use the stylus i usually pose my hand on tablet and raise stylus without lifting hand when making short movement, if the raising of stylus gets out of tablet range this causes immediate repositioning of cursor where hand is still touching and click grab is activated therefore when i reposition pen what ever has been grabbed is then moved...

in windows this does not happen there is a lag between raising pen with rest of hand on tablet...

the freezes happen sporadically after fast moving, raising, grabbing and repositioning i will try to recreate situation and send messages.log.

> 
If possible, can you attach your /var/log/messages and Xorg.0.log?

I will reinstall your version clean up messages.log and post it...

---

### Post by dnprossi on 2009-11-16
Message log is pretty large... Could not reproduce freeze yet, but i did reproduce stylus raise and repositioning at hand position. and found out that stylus buttons work only if you press before positioning on tablet.

This is with fdi from src/util in your patch...

EDIT...
The freeze is not a real freeze.. Real hard to explain... Happens only with ob1kenobi's fdi..
it is caused by the top right tablet button pressed while moving stylus or finger on tablet somehow the drag rectangle on desktop is not cleared causing temporary inactivity of menu button selection. I had this hidden by open window so i could not see it happening. On raising pen and quickly moving hand the cursor was repositioned to right bottom corner of desktop and that activated drag rectangle and hid it from view... WOW.. Hope this was clear...
 
added messages.log-2.txt.tar.gz where this happened

---

### Post by ob1kenobi on 2009-11-16
> **dnprossi said:**
> 

Ayuthia's **0.8.5-4-21** pre-patch with **ob1kenobi's fdi on post [#316]("http://ubuntuforums.org/showpost.php?p=8325874&postcount=316")**

0.8.5-4-21 GIMP:
Stylus: OK for movement - But no click at all
Stylus Buttons: NONE
Eraser: NONE
Touch: [COLOR=Red]YES working as touchpad[/COLOR], "not as stylus" - but no click at all.
Touch Buttons: Active in messages.log

same test with ob1kenobi's latest 0.8.5-4 and both fdi's
same as above

dnprossi,

Make sure you setup GIMP again.  I had to edit the extended input devices to turn them back on since the names change with the fdi I provided.  I had the same sort of problem until I did this.

---

### Post by dnprossi on 2009-11-16
> **ob1kenobi said:**
> dnprossi,

Make sure you setup GIMP again.  I had to edit the extended input devices to turn them back on since the names change with the fdi I provided.  I had the same sort of problem until I did this.

hi ob1, i'll try again using Ayuthia's 0.8.5-4-21 pre-patch with your fdi...

---

### Post by Ayuthia on 2009-11-16
I just made some minor changes to the overflow so that it covers both the 18 and 20 bytes for now.

I also flip-flopped the pad check to come before the touch so that it does not go through the touch data. 

Right now, I have not done anything for the timing of the pen to touch switch.  I might check with Ping to see how this should be handled.  I figure that the E2/E3 TabletPC models have the same issue.

These changes are all in the patch 22 version.  Please test it again with both fdi samples.

---

### Post by dnprossi on 2009-11-16
> **Ayuthia said:**
> 
These changes are all in the patch 22 version.  Please test it again with both fdi samples.

installed 22 version changed fdi to src/util/10-linuxwacom.fdi and reboot

after a few clicks with stylus on desktop i could not select menus and buttons or windows- temporary freeze - pen continued moving cursor though and everything restarted working after a few seconds...

attached messages.log

---

### Post by ob1kenobi on 2009-11-16
> **Ayuthia said:**
> I just made some minor changes to the overflow so that it covers both the 18 and 20 bytes for now.


I don't like the way I did that (it was just a hack to get it working). Here's a better way... (see attachments).  It compiles cleanly, but I don't have my tablet with me.

> 
Right now, I have not done anything for the timing of the pen to touch switch.  I might check with Ping to see how this should be handled.  I figure that the E2/E3 TabletPC models have the same issue.


Again hacked up tpc code, needs to probably be more like tpc touchInProx/stylusInProx rather than just stylusInProx.

---

### Post by dnprossi on 2009-11-16
the freeze is caused by hand on tablet...
here the log of the freeze.. I was not using the tablet but while writing i must have touched it and everything froze until tapped with eraser.. its all there...

---

### Post by Ayuthia on 2009-11-16
> **ob1kenobi said:**
> I don't like the way I did that (it was just a hack to get it working). Here's a better way... (see attachments).  It compiles cleanly, but I don't have my tablet with me.



Again hacked up tpc code, needs to probably be more like tpc touchInProx/stylusInProx rather than just stylusInProx.

These changes are now in patch 23.

dnprossi, I am going to look at your messages log.  Can you also attach a copy of the Xorg.0.log?  It will help us see what the X module is missing.

---

### Post by Ayuthia on 2009-11-16
> **dnprossi said:**
> the freeze is caused by hand on tablet...
here the log of the freeze.. I was not using the tablet but while writing i must have touched it and everything froze until tapped with eraser.. its all there...

Can you try rebuilding the source but use:
```
./configure --debug=true --enable-wacom --prefix=/usr
```
instead?  It looks like the touch might not be getting switched off.

When you say it froze, did the touch not work also?

---

### Post by marek_online on 2009-11-16
Hi everyone,

I've screwed something up and I can't think of what it might be. I've tried both the pre-patched source and the separate patch (both compile without errors) but neither get me any movement from touch or stylus or anything in /var/log/messages but this:
```
Nov 16 17:31:43 Childers kernel: [  689.600050] usb 7-1: new full speed USB device using uhci_hcd and address 5
Nov 16 17:31:44 Childers kernel: [  689.764598] usb 7-1: configuration #1 chosen from 1 choice
Nov 16 17:31:44 Childers kernel: [  689.772646] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input21
Nov 16 17:31:44 Childers kernel: [  689.793473] finger report data:09 30 35 00 46 e0 2e 26 e0 01 75 10 95 01 81 02 09 31 46 40
Nov 16 17:31:44 Childers kernel: [  689.793489] finger report data:09 31 46 40 1f 26 40 01 81 02 06 00 ff 09 01 26 ff 00 75 08
Nov 16 17:31:44 Childers kernel: [  689.793578] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input22
```I've tried the fdi file at post #316 and the one in src/util. Is there something obvious I'm missing?

EDIT:
Never mind. I'm an idiot Currently have touch with that held-button 1 effect, but no stylus or eraser. I'll look into it a bit more.

---

### Post by dnprossi on 2009-11-16
Ayuthia patch 23 has lost all functions..
no tablet no nothing...

> 
When you say it froze, did the touch not work also?


have not noticed but may be in messages.log...

---

### Post by Ayuthia on 2009-11-16
There is a bug with the most recent change for the overflow.  Please try going into src/2.6.28/wacom_sys.c and go to line 95 where you will find:
```

        case -EOVERFLOW:
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```
and change it to:
```

        case -EOVERFLOW:
[B]                if (wacom->wacom_wac->features->type == BAMBOO_PT)
                    break;[/B]
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```
You will need to recompile and it things should report again.  If it works, I will create a new patch.

---

### Post by ob1kenobi on 2009-11-16
> **Ayuthia said:**
> There is a bug with the most recent change for the overflow.  Please try going into src/2.6.28/wacom_sys.c and go to line 95 where you will find:
```

        case -EOVERFLOW:
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```and change it to:
```

        case -EOVERFLOW:
[B]                if (wacom->wacom_wac->features->type == BAMBOO_PT)
                    break;[/B]
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```You will need to recompile and it things should report again.  If it works, I will create a new patch.

I think the problem may be related to wacom_sys.c:583

```

 if (features->type == BAMBOO_PT && features->device_type == BTN_TOOL_DOUBLETAP) {
                usb_fill_int_urb(wacom->irq, dev,
                                 usb_rcvintpipe(dev, endpoint->bEndpointAddress),
                                 wacom_wac->data, features->pktlen[1],
                                 wacom_sys_irq, wacom, endpoint->bInterval);
        } else {
                usb_fill_int_urb(wacom->irq, dev,
                                 usb_rcvintpipe(dev, endpoint->bEndpointAddress),
                                 wacom_wac->data, features->pktlen[0],
                                 wacom_sys_irq, wacom, endpoint->bInterval);
        }

```I thought this should be called differently for each device instance (i.e. pen vs touch)
There should never be an EOVERFLOW condition with the above code in place and you should never see the EOVERFLOW dbg printout unless your device is different size than what I put in the device table in wacom_wac.c.  Maybe wacom_wac.c values need to be tweaked?

EDIT:  Also I left the EOVERFLOW in there to detect such problems, and it should not need any special break's since it is there to report a device urb length mismatch that needs to be corrected int he wacom_wac.c tables.  Are you seeing the overflow message in /var/log/messages?

---

### Post by marek_online on 2009-11-16
> **Ayuthia said:**
> There is a bug with the most recent change for the overflow.  Please try going into src/2.6.28/wacom_sys.c and go to line 95 where you will find:
```

        case -EOVERFLOW:
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```and change it to:
```

        case -EOVERFLOW:
[B]                if (wacom->wacom_wac->features->type == BAMBOO_PT)
                    break;[/B]
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```You will need to recompile and it things should report again.  If it works, I will create a new patch.

Did this - stylus and eraser are back working,  but no touch. When the pad is lying still tail -f /var/log messages produces endless lines of this:

```
Nov 16 17:58:49 Childers kernel: [ 2315.251669] 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Nov 16 17:58:49 Childers kernel: [ 2315.255666] 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Nov 16 17:58:49 Childers kernel: [ 2315.259666] 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Nov 16 17:58:49 Childers kernel: [ 2315.263666] 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Nov 16 17:58:49 Childers kernel: [ 2315.267667] 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```

---

### Post by ob1kenobi on 2009-11-16
But are you seeing urb EOVERFLOW messages with the length?

---

### Post by Ayuthia on 2009-11-16
> **dnprossi said:**
> Ayuthia patch 23 has lost all functions..
no tablet no nothing...



have not noticed but may be in messages.log...

We need to see the /var/log/Xorg.0.log to see what is happening.  The kernel module is getting the data, but it is not reporting it to X correctly.  The Xorg.0.log will help us see what it is getting.

Of course, the Xorg.0.log clears out after every session so we will need to recreate the freeze.  From what I understand, all you need to do is rest your hand on the tablet and it should happen again.

---

### Post by ob1kenobi on 2009-11-16
> **Ayuthia said:**
> We need to see the /var/log/Xorg.0.log to see what is happening.  The kernel module is getting the data, but it is not reporting it to X correctly.  The Xorg.0.log will help us see what it is getting.

Of course, the Xorg.0.log clears out after every session so we will need to recreate the freeze.  From what I understand, all you need to do is rest your hand on the tablet and it should happen again.

I think /var/log/Xorg.0.log.old should be the previous session's log

---

### Post by Ayuthia on 2009-11-16
> **ob1kenobi said:**
> But are you seeing urb EOVERFLOW messages with the length?

I don't think that the debugger is turned on.

Can you change the overflow line to look like this:
```

        case -EOVERFLOW:
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    (urb->actual_length == (wacom->wacom_wac->features->pktlen) ||
                     urb->actual_length == (wacom->wacom_wac->features->pktlen - 2)))
                    break;
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```
This should fix that problem hopefully.  I would have thought that the touch would have come back with the previous version though.

My guess is that we are always getting an overflow (wrong packet size)?

EDIT:  I just saw ob1kenobi's [message]("http://ubuntuforums.org/showpost.php?p=8328811&postcount=336") after posting this.

---

### Post by marek_online on 2009-11-16
> **Ayuthia said:**
> I don't think that the debugger is turned on.

Can you change the overflow line to look like this:
```

        case -EOVERFLOW:
                if (wacom->wacom_wac->features->type == BAMBOO_PT &&
                    (urb->actual_length == (wacom->wacom_wac->features->pktlen) ||
                     urb->actual_length == (wacom->wacom_wac->features->pktlen - 2)))
                    break;
                dbg("%s - urb overflow detected with size: %d", __func__, urb->actual_length);
                goto exit;

```This should fix that problem hopefully.  I would have thought that the touch would have come back with the previous version though.

My guess is that we are always getting an overflow (wrong packet size)?


So, I've tried this but it leaves me back with no working touch or stylus, and no information at all in /var/log/messages, just this:
```
Nov 16 18:43:12 Childers kernel: [  463.049554] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input13
Nov 16 18:43:12 Childers kernel: [  463.066400] finger report data:09 30 35 00 46 e0 2e 26 e0 01 75 10 95 01 81 02 09 31 46 40
Nov 16 18:43:12 Childers kernel: [  463.066428] finger report data:09 31 46 40 1f 26 40 01 81 02 06 00 ff 09 01 26 ff 00 75 08
Nov 16 18:43:12 Childers kernel: [  463.066585] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input14
Nov 16 18:43:12 Childers kernel: [  463.073422] usbcore: registered new interface driver wacom
Nov 16 18:43:12 Childers kernel: [  463.073427] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet drive
```

That said, I'm not sure you intended me to try that edit! Have to head away, will try to have a look again later.

---

### Post by Ayuthia on 2009-11-16
> **ob1kenobi said:**
> I think the problem may be related to wacom_sys.c:583

```

 if (features->type == BAMBOO_PT && features->device_type == BTN_TOOL_DOUBLETAP) {
                usb_fill_int_urb(wacom->irq, dev,
                                 usb_rcvintpipe(dev, endpoint->bEndpointAddress),
                                 wacom_wac->data, features->pktlen[1],
                                 wacom_sys_irq, wacom, endpoint->bInterval);
        } else {
                usb_fill_int_urb(wacom->irq, dev,
                                 usb_rcvintpipe(dev, endpoint->bEndpointAddress),
                                 wacom_wac->data, features->pktlen[0],
                                 wacom_sys_irq, wacom, endpoint->bInterval);
        }

```I thought this should be called differently for each device instance (i.e. pen vs touch)
There should never be an EOVERFLOW condition with the above code in place and you should never see the EOVERFLOW dbg printout unless your device is different size than what I put in the device table in wacom_wac.c.  Maybe wacom_wac.c values need to be tweaked?

EDIT:  Also I left the EOVERFLOW in there to detect such problems, and it should not need any special break's since it is there to report a device urb length mismatch that needs to be corrected int he wacom_wac.c tables.  Are you seeing the overflow message in /var/log/messages?

I have reverted the code back (I think).  I am going to look at this section a little more to see if we can figure out what is happening.  If it doesn't work, I will go back to patch 21 and we will start from there again.

---

### Post by prefiks2 on 2009-11-16
Two patches on top 21, first one fix x position overflow when reporting touch events, second one stops using {x,y}_max from touch on stylus (makes whole tablet useable not only top left corner). Both bugs spotted on BF medium.

---

### Post by Ayuthia on 2009-11-16
> **prefiks2 said:**
> Two patches on top 21, first one fix x position overflow when reporting touch events, second one stops using {x,y}_max from touch on stylus (makes whole tablet useable not only top left corner). Both bugs spotted on BF medium.

Welcome to the forum and thanks for the patches!  The changes have been implemented in patch 26.  

Patch 26 is going reverting back to patch 21 and I moved the check for the pad buttons before the touch data again.

---

### Post by prefiks2 on 2009-11-16
Yet another patch which prevents setting TPCButton to on, and as a result makes stylus buttons works even when stylus don't touch tablet.

---

### Post by ob1kenobi on 2009-11-16
> **Ayuthia said:**
> Welcome to the forum and thanks for the patches!  The changes have been implemented in patch 26.  

Patch 26 is going reverting back to patch 21 and I moved the check for the pad buttons before the touch data again.

prefiks2, welcome and good call on the copying features, it removes the need for additional pktlen.

Ayuthia,  here a 25x with some additional stylusInProx/touchInProx code, I left the urb changes in (albeit modified by prefiks2's change).  Also i bumped up the masking to 0x7ff on both x and y incase the larger pads need more (on mine they are zeros).

I'm just parking this here for later when I have access to my tablet.  Don't bother merging it until I get it tested.

EDIT: Updated with prefiks2's latest patch for TPCButton

---

### Post by Favux on 2009-11-16
Hi prefiks2,

I'm not sure but is the TPCButton patch needed?  In wacomcpl you can select in Tool Buttons for stylus hover mode by changing Side Switch Mode to Side Switch Only.  Is that what you're trying to do?

---

### Post by kgingeri on 2009-11-16
Hey All, in using the touch at work on my Mac I realized it is always in 'mouse mode' not 'pen mode' or absolute mode (those are my options in sys prefs).

This is DEFINITELY preferable!  We don't have to worry about it now, but just in case you come across code to make it relative instead of absolute.  That said, absolute may be better until we know we have x/y max's working etc.

I believe there is also a xsetwacom param for mode - not sure if it is this mode tho and if it's coded or not.

My 2 cents worth  ;)

---

### Post by Favux on 2009-11-16
Hi kgingeri,

You can switch between Absolute and Relative with an xsetwacom command too.  Or put it in the .fdi.  Not sure it needs to be coded.  It should be an option in wacomcpl but it isn't.

---

### Post by rebecca2525 on 2009-11-16
In case it is still needed (hard to keep track with all the activity going on ;)), [here is scale data]("http://paste.pocoo.org/show/151102/") where I dragged a line from upper left corner to lower right corner of the touch area, on a medium sized tablet.

---

### Post by marek_online on 2009-11-16
Patch 26, with the fdi from post #316 crashes X on reboot for me.
Edit: Just a little more detail. The crash looked familiar - the same kind of thing happened way back when, during some of the testing back on the old thread.

Xorg.0.log from the session attached.

Before reboot touch worked properly, but no movement from the stylus despite data appearing in /var/log/messages.

---

### Post by rebecca2525 on 2009-11-16
I'm using patch 26 now with the fdi that comes with it. Uh, I don't see that patch number in /var/log/messages anymore? Can you put that back in, I always found it reassuring to see that I'm really using the patch I think I'm using...

Anyhow, now I get data from touch, pen and stylus and tablet buttons in /var/log/messages, though the only thing that has any effect is the touch. As before, scale is not right for my tablet, movement is absolute and it issues a left-button click when I put my finger down to move the cursor, but otherwise it seems to work fine.


EDIT: Getting a lot of this in xorg.log:

```
stylus - usbParse: dropping empty event for serial 240
xf86WcmReady for stylus with 0 numbers of data
xf86WcmDevReadInput: Read (1)
xf86WcmReady for stylus with 1 numbers of data
xf86WcmReadPacket: device=/dev/input/event6 fd=31 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 48 bytes
usbParseEvent 
usbParseEvent
```

---

### Post by Favux on 2009-11-16
Hi rebecca2525,

Could you try in a terminal?:
```
xsetwacom set touch mode relative
```
Or maybe the t in touch needs to be capitalized.

---

### Post by rebecca2525 on 2009-11-16
> **Favux said:**
> Could you try in a terminal?:
```
xsetwacom set touch mode relative
```Or maybe the t in touch needs to be capitalized.
If I do that, I can't move the cursor at all (but left-click still works), if I set it back to absolute it reverts to the situation described above.

---

### Post by Ayuthia on 2009-11-16
> **marek_online said:**
> Patch 26, with the fdi from post #316 crashes X on reboot for me.
Edit: Just a little more detail. The crash looked familiar - the same kind of thing happened way back when, during some of the testing back on the old thread.

Xorg.0.log from the session attached.

Before reboot touch worked properly, but no movement from the stylus despite data appearing in /var/log/messages.

Did anything show up in /var/log/messages when X crashed?  Can you attach it?  I want to see if the kernel module crashed when X was launched.

---

### Post by Ayuthia on 2009-11-16
> **rebecca2525 said:**
> In case it is still needed (hard to keep track with all the activity going on ;)), [here is scale data]("http://paste.pocoo.org/show/151102/") where I dragged a line from upper left corner to lower right corner of the touch area, on a medium sized tablet.

Can you attach your Xorg.0.log (it shouldn't matter which version you use)?  I want to see if it logged the x_max and y_max.  ob1kenobi had changed the code so that it looked it up automatically, but either our setup is wrong or else the values are not correct.

EDIT: The x_max and y_max values are correct (740x500).

---

### Post by Favux on 2009-11-16
Hi rebecca2525,

OK.  On my touch screen the cursor will sit where I left it and I can set the finger down elsewhere and move it with the "offset".  Or I can put my finger back over the cursor and "pick it up" again.

I don't think there is an xsetwacom for touch to turn off the click.  I doubt:
```
xsetwacom set touch TPCButton off
```
will do anything for touch.  We could change the touch sensitivity level if the multi-touch pad is a capacitive touch device.  But I don't think that gets you anywhere either.

---

### Post by rebecca2525 on 2009-11-16
Ayuthia, see attachment

---

### Post by Ayuthia on 2009-11-16
> **rebecca2525 said:**
> I'm using patch 26 now with the fdi that comes with it. Uh, I don't see that patch number in /var/log/messages anymore? Can you put that back in, I always found it reassuring to see that I'm really using the patch I think I'm using...

Anyhow, now I get data from touch, pen and stylus and tablet buttons in /var/log/messages, though the only thing that has any effect is the touch. As before, scale is not right for my tablet, movement is absolute and it issues a left-button click when I put my finger down to move the cursor, but otherwise it seems to work fine.


EDIT: Getting a lot of this in xorg.log:

```
stylus - usbParse: dropping empty event for serial 240
xf86WcmReady for stylus with 0 numbers of data
xf86WcmDevReadInput: Read (1)
xf86WcmReady for stylus with 1 numbers of data
xf86WcmReadPacket: device=/dev/input/event6 fd=31 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 48 bytes
usbParseEvent 
usbParseEvent
```

This is strange.  What you are describing makes it sound like you are using an older version (The left-click issue).  However, you say that you no longer get the patch number (new patches currently don't have it).

Can you attach a portion of your /var/log/messages where there is some stylus information?  I just want to see if it is sending the correct packet size.

---

### Post by rebecca2525 on 2009-11-16
Stylus data:
```
Nov 16 23:07:29 zam559 kernel: [  251.612013] 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:07:29 zam559 kernel: [  251.632012] 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:07:29 zam559 kernel: [  251.648024] 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:07:29 zam559 kernel: [  251.672034] 02 80 00 00 00 00 00 00 00 02 00 35 0b 58 0d 0b 00 0b 02 f0 
Nov 16 23:07:29 zam559 kernel: [  251.692045] 02 f0 44 0b 50 0d 00 00 0d 02 f0 66 0b 54 0d 00 00 12 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.708050] 02 f1 56 0b 42 0d 87 01 12 02 f1 46 0b 34 0d f7 00 13 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.724059] 02 f1 47 0b 2d 0d 20 01 14 02 f1 47 0b 30 0d 17 01 15 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.736068] 02 f1 52 0b 33 0d e0 00 16 02 f1 62 0b 3b 0d dc 00 16 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.752075] 02 f1 80 0b 46 0d e3 00 17 02 f1 a2 0b 55 0d de 00 18 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.768080] 02 f1 cc 0b 6a 0d df 00 18 02 f1 02 0c 85 0d e0 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.784087] 02 f1 43 0c a1 0d dd 00 19 02 f1 84 0c c6 0d e2 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.796094] 02 f1 cd 0c ec 0d e1 00 19 02 f1 0e 0d 11 0e e1 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.812106] 02 f1 52 0d 40 0e e6 00 19 02 f1 9f 0d 6f 0e e2 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.828115] 02 f1 e4 0d 9e 0e e3 00 18 02 f1 29 0e d3 0e e6 00 18 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.844101] 02 f1 79 0e 0d 0f de 00 16 02 f1 d3 0e 4a 0f e6 00 16 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.856127] 02 f1 28 0f 88 0f e6 00 18 02 f1 78 0f cb 0f e4 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.872090] 02 f1 cd 0f 0f 10 eb 00 1b 02 f1 33 10 58 10 ea 00 1a 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.888143] 02 f1 97 10 9d 10 ed 00 1b 02 f1 ec 10 e4 10 f3 00 1b 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.904147] 02 f1 49 11 2a 11 f3 00 1b 02 f1 a3 11 73 11 fb 00 1b 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.916155] 02 f1 f4 11 b7 11 ff 00 1c 02 f1 52 12 fd 11 04 01 1b 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.932168] 02 f1 b7 12 49 12 0f 01 1b 02 f1 1a 13 90 12 0f 01 1a 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.948171] 02 f1 76 13 d7 12 15 01 19 02 f1 e2 13 1f 13 1c 01 17 02 f1 
```

---

### Post by Ayuthia on 2009-11-16
> **rebecca2525 said:**
> Stylus data:
```
Nov 16 23:07:29 zam559 kernel: [  251.612013] 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:07:29 zam559 kernel: [  251.632012] 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:07:29 zam559 kernel: [  251.648024] 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:07:29 zam559 kernel: [  251.672034] 02 80 00 00 00 00 00 00 00 02 00 35 0b 58 0d 0b 00 0b 02 f0 
Nov 16 23:07:29 zam559 kernel: [  251.692045] 02 f0 44 0b 50 0d 00 00 0d 02 f0 66 0b 54 0d 00 00 12 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.708050] 02 f1 56 0b 42 0d 87 01 12 02 f1 46 0b 34 0d f7 00 13 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.724059] 02 f1 47 0b 2d 0d 20 01 14 02 f1 47 0b 30 0d 17 01 15 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.736068] 02 f1 52 0b 33 0d e0 00 16 02 f1 62 0b 3b 0d dc 00 16 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.752075] 02 f1 80 0b 46 0d e3 00 17 02 f1 a2 0b 55 0d de 00 18 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.768080] 02 f1 cc 0b 6a 0d df 00 18 02 f1 02 0c 85 0d e0 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.784087] 02 f1 43 0c a1 0d dd 00 19 02 f1 84 0c c6 0d e2 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.796094] 02 f1 cd 0c ec 0d e1 00 19 02 f1 0e 0d 11 0e e1 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.812106] 02 f1 52 0d 40 0e e6 00 19 02 f1 9f 0d 6f 0e e2 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.828115] 02 f1 e4 0d 9e 0e e3 00 18 02 f1 29 0e d3 0e e6 00 18 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.844101] 02 f1 79 0e 0d 0f de 00 16 02 f1 d3 0e 4a 0f e6 00 16 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.856127] 02 f1 28 0f 88 0f e6 00 18 02 f1 78 0f cb 0f e4 00 19 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.872090] 02 f1 cd 0f 0f 10 eb 00 1b 02 f1 33 10 58 10 ea 00 1a 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.888143] 02 f1 97 10 9d 10 ed 00 1b 02 f1 ec 10 e4 10 f3 00 1b 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.904147] 02 f1 49 11 2a 11 f3 00 1b 02 f1 a3 11 73 11 fb 00 1b 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.916155] 02 f1 f4 11 b7 11 ff 00 1c 02 f1 52 12 fd 11 04 01 1b 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.932168] 02 f1 b7 12 49 12 0f 01 1b 02 f1 1a 13 90 12 0f 01 1a 02 f1 
Nov 16 23:07:29 zam559 kernel: [  251.948171] 02 f1 76 13 d7 12 15 01 19 02 f1 e2 13 1f 13 1c 01 17 02 f1 
```

Thanks!  I think that we do have a packet size issue.  The touch appears to be 18 bytes and the pen is 9.  I am going to see what can be done for this.

EDIT:
Apparently when I came back and tried to catch up, I missed a page.  There are some patches to review.

---

### Post by pourissage on 2009-11-16
Just to signal that I have just tested with bamboo pen (D4) and it seams too work correctly. No real problem found.
The only notices I have are that bomboo pen has no eraser and that there is a
device wacom-touch in /dev/input wich is useless.
I think there should be the same problem with bamboo touch wich has no stylus.

That's all.
Well done and thanks for the good work !

---

### Post by Ayuthia on 2009-11-16
> **prefiks2 said:**
> Yet another patch which prevents setting TPCButton to on, and as a result makes stylus buttons works even when stylus don't touch tablet.

I am only going to hold off on this one for now.  This is a configuration option that can be set in the .fdi file:
```

<merge key="input.x11_options.TPCButton" type="string">Off</merge>

```

---

### Post by Ayuthia on 2009-11-16
Patch 27 is now out.  I did not do too much to this one yet.  I changed the packet size to 18 so that the data fits better.  ob1kenobi has a change that can help report the data more accurately.  The patch number has been added back to /var/log/messages.

Please try this one out and let me know if this helps the stylus or not.  Also, can someone try out turning off the TPCButton as stated in the previous post?  You will need to add this to the stylus line (is that right Favux?).  Either that or you can also try:
```
xsetwacom set stylus TPCButton off
```
You might need to set it for the eraser also.

ob1kenobi and prefiks2 - Thanks for the code contributions!  It is nice to now have help in code and testing.

---

### Post by Favux on 2009-11-16
Hi Ayuthia,

Correct.  I'd add it in the stylus section just above the debug lines.  Or else use the xsetwacom command.  Which is basically what wacomcpl is doing.

---

### Post by kgingeri on 2009-11-16
> **rebecca2525 said:**
> If I do that, I can't move the cursor at all (but left-click still works), if I set it back to absolute it reverts to the situation described above.

Hey back in the ring!  Relative mode does work for me with:
```
xsetwacom set touch mode 0
```

(that's a zero) I find that if I do a "xsetwacom get ..." first, it give a hint of syntax  ;)

Relative mode is nice!

I am running patch 26 with ob1's fdi file - I'll attach it again as I'm to lazy to go looking for the post.  I also gives me full touch area response again, but still no stylus action.

I haven't caught up in reading posts tho so I'll do that first.
[COLOR="Red"][B]
WARNING TO ALL[/B]:  Can I suggest that we **_always reboot between all tests_** - even fdi changes.  This will ensure we don't mislead Ayuthia, Favux and Ob1 in testing results and keep us working efficiently :) - results are coming fast but they do need to be accurate, right?![/COLOR]

---

### Post by Favux on 2009-11-16
Hi kgingeri,

Nice find!  I hope it works for rebecca2525 and the rest.

---

### Post by Ayuthia on 2009-11-16
You can also configure it in the fdi:
```

<merge key="input.x11_options.Mode" type="string">Relative</merge>

```

You should be able to set it to 0 also like kgingeri stated.

So that everyone does not have to jump from page to page, I have included ob1kenobi's fdi file as an attachment in the first post.

---

### Post by kgingeri on 2009-11-16
> **Favux said:**
> Hi kgingeri,

Nice find!  I hope it works for rebecca2525 and the rest.

From my testing, "on" and "off" may not work - not sure - use boolean 1 or 0 and "xsetwacom get ..." to be sure.  Some params have other values of course.  However...
```
xsetwacom set **touch** TPCButton off
``` has no effect - still get selection when moving cursor with touch. 
```
$ xsetwacom set touch TPCButton on
$ xsetwacom get touch TPCButton   
1
$ xsetwacom set touch TPCButton off
$ xsetwacom get touch TPCButton 
0
```

Just a refresher, xsetwacom syntax is:
[INDENT]xsetwacom [get|set] <X device name as in 'xsetwacom list dev'> <param as in 'xsetwacom list param'> [value][/INDENT] 

EDIT: not sure but likely CASE is important.

Ayuthia, I will test the added fdi line 1st and then try with patch 27 also.

---

### Post by kgingeri on 2009-11-16
> **Favux said:**
> Hi Ayuthia,

Correct.  I'd add it in the stylus section just above the debug lines.  Or else use the xsetwacom command.  Which is basically what wacomcpl is doing.

Favux, "stylus"?!  Isn't it touch we want to change - or am I mixed up.  This is for the left-button down issue, right?!

EDIT: or is this a general xserver setting so it doesn't matter :)  At any rate it didn't make a difference for me  :( 
EDIT: Ok who stole my xinput devices!  I added that fdi line, right after "stylus" and before the 2 debug lines and I went to use xsetwacom and have no pad no stylus no touch...  More testing need here.  XML looks ok in fdi file - hmmmm...
I even followed my own suggestion and rebooted!!!  ;)  (I do learn from my mistakes Favux :D)
[COLOR="Red"]EDIT: Sorry not "xinput" - "xsetwacom list dev"![/COLOR]

---

### Post by Favux on 2009-11-16
Hi kgingeri,

I guessed you missed prefiks2's patch to put the stylus in "hover" mode.  That's where the stylus buttons work without touching the stylus tip to the tablet.  Generally you do that through wacomcpl, but you can use xsetwacom commands or their equivalent in xorg.conf or the .fdi.

---

### Post by kgingeri on 2009-11-16
> **Favux said:**
> Hi kgingeri,

I guessed you missed prefiks2's patch to put the stylus in "hover" mode.  That's where the stylus buttons work without touching the stylus tip to the tablet.  Generally you do that through wacomcpl, but you can use xsetwacom commands or their equivalent in xorg.conf or the .fdi.

Ah, ok. I did update my previous post - have a look.  I'll test more to make sure it's not fat-finger problems.

---

### Post by Favux on 2009-11-16
Huh!
> TPCButton     on|off                   turns on/off the buttons as Tablet PC buttons
I guess the thing to do is take the line out of the .fdi and see if you can do it through wacomcpl.  See this [post]("http://ubuntuforums.org/showpost.php?p=8329724&postcount=348").

Edit:  Actually we should do a "xinput --list" and "xsetwacom list" on ob1's .fdi and see which xsetwacom commands will apply.

---

### Post by kgingeri on 2009-11-16
> **Favux said:**
> Huh!

I guess the thing to do is take the line out of the .fdi and see if you can do it through wacomcpl.  See this [post]("http://ubuntuforums.org/showpost.php?p=8329724&postcount=348").

Oh brother - sorry, I meant "xsetwacom list dev", I get nothing now and my touch area is back to the top left 3rd of the screen area - which seems to happen depending on what fdi I use.  

You'd think is was late or something ;)  I'll sort this out **before** I post again and bother you.

---

### Post by Favux on 2009-11-16
Hi kgingeri,

With the current ob1 .fdi Ayuthia is asking you to use on post #1 xsetwacom commands and wacomcpl won't work.  xsetwacom list will be blank.

---

### Post by Ayuthia on 2009-11-16
> **Favux said:**
> Hi kgingeri,

With the current ob1 .fdi Ayuthia is asking you to use on post #1 xsetwacom commands and wacomcpl won't work.  xsetwacom list will be blank.

I am hoping that we can get the tablets working with the current .fdi file that we have.  Right now, I just want to confirm that ob1kenobi's fdi file works and then figure out what we need to fix to make the current fdi file work properly.

---

### Post by Favux on 2009-11-16
Hi Ayuthia,

This should fix it hopefully without interfering with function.  But I can't guarantee it.

---

### Post by kgingeri on 2009-11-16
> **Favux said:**
> Hi kgingeri,

With the current ob1 .fdi Ayuthia is asking you to use on post #1 xsetwacom commands and wacomcpl won't work.  xsetwacom list will be blank.

> **Ayuthia said:**
> I am hoping that we can get the tablets working with the current .fdi file that we have.  Right now, I just want to confirm that ob1kenobi's fdi file works and then figure out what we need to fix to make the current fdi file work properly.

OK, understood.  Will report findings.

*PS: For those who care - I've updated my RebuildWacom to be smart about versions. It now picks the most recent bz2 files - see post [#145]("http://ubuntuforums.org/showpost.php?p=8313047&postcount=145")*

---

### Post by GolemdX on 2009-11-16
**16 Nov, 2009 Report #1**
(patch 27 | standard FDI)

**What I gather...**
[list][*]Nothing Works.[/list]
Correct?

**Additional Information:** I'll try the other FDI and see if something happens.

---

### Post by GolemdX on 2009-11-16
**16 Nov, 2009 Report #2**
(patch 27 | ob1kenobi's FDI)

**What I gather...**
[list][*]Nothing Works.[/list]
Correct?

**Additional Information:** Is it just me, or is NOTHING working?

---

### Post by kgingeri on 2009-11-16
Ok, so I think I am squeaky clean and have patch 27 and ob1's fdi from Post #1 (not ob1-fav yet - that's next) and I've attached sample log data.  I have _NO touch or stylus_ at this point!?  Looks like I do have stylus data only too.

I'm a bit concerned tho, as others seemed to be getting different result then I was.  For some reason I'm not sure you should trust these results.  Just intuition tho - like I said I've done what I think is a very clean rebuild...

EDIT: Hmmmm - I feel better, just refreshed the page and saw GolemdX's results

---

### Post by Ayuthia on 2009-11-16
> **kgingeri said:**
> Ok, so I think I am squeaky clean and have patch 27 and ob1's fdi from Post #1 (not ob1-fav yet - that's next) and I've attached sample log data.  I have _NO touch or stylus_ at this point!?  Looks like I do have stylus data only too.

I'm a bit concerned tho, as others seemed to be getting different result then I was.  For some reason I'm not sure you should trust these results.  Just intuition tho - like I said I've done what I think is a very clean rebuild...

EDIT: Hmmmm - I feel better, just refreshed the page and saw GolemdX's results

Can you go into sys/2.6.28/wacom_wac.c and change the value of
```
#define WACOM_PKGLEN_BBPT
```
from 18 back to 20?  Once you rebuild it, please let us know if the touch and pen values come back.

There is currently a bug with the packet length that has currently caused the data to report differently.  ob1kenobi is planning on testing out a solution that looks promising.

---

### Post by kgingeri on 2009-11-16
> **Ayuthia said:**
> Can you go into sys/2.6.28/wacom_wac.c and change the value of
```
#define WACOM_PKGLEN_BBPT
```
from 18 back to 20?  Once you rebuild it, please let us know if the touch and pen values come back.

There is currently a bug with the packet length that has currently caused the data to report differently.  ob1kenobi is planning on testing out a solution that looks promising.

Ayuthia, I have pen values again but I get a constant stream of the following in var messages:
```
Nov 16 22:11:01 kgulnb kernel: [  230.185028] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.189029] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.193040] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.197021] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.201025] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
```

Nothing for touch on Xorg and this for pen (**not eraser**) in Xorg:
```
xf86WcmReadPacket: device=/dev/input/event9 fd=12 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=12 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=12 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=12 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=12 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
```

UPDATE: xinput and xsetwacom...
```
$ xinput --list --short
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"Wacom Bamboo P&T 4x5"	id=2	[XExtensionKeyboard]
"Wacom Bamboo P&T 4x5 cursor"	id=3	[XExtensionKeyboard]
"Power Button"	id=4	[XExtensionKeyboard]
"Acer Crystal Eye webcam"	id=5	[XExtensionKeyboard]
"Wacom Bamboo P&T 4x5"	id=6	[XExtensionKeyboard]
"AT Translated Set 2 keyboard"	id=7	[XExtensionKeyboard]
"Wacom Bamboo P&T 4x5 touch"	id=8	[XExtensionKeyboard]
"Video Bus"	id=9	[XExtensionKeyboard]
"Wacom Bamboo P&T 4x5 eraser"	id=10	[XExtensionKeyboard]
"Power Button"	id=11	[XExtensionKeyboard]
"Sleep Button"	id=12	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=13	[XExtensionPointer]
"SynPS/2 Synaptics TouchPad"	id=14	[XExtensionPointer]
"Microsoft Compact Optical Mouse 500"	id=15	[XExtensionPointer]
$ xsetwacom list dev

```

---

### Post by Ayuthia on 2009-11-16
> **kgingeri said:**
> Ayuthia, I have pen values again but I get a constant stream of the following in var messages:
```
Nov 16 22:11:01 kgulnb kernel: [  230.185028] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.189029] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.193040] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.197021] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:11:01 kgulnb kernel: [  230.201025] [wacom-27] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
```

]

This is with WACOM_PKGLEN_BBPT set to 20?  I am just confirming because the info above only has 18 reported.

---

### Post by Favux on 2009-11-16
Hi everyone,

Maybe I should mention that something in 0.8.5-4 is broken.  When I rotate the tablet the stylus, eraser, and touch don't rotate and remain messed up when I go back to laptop.  I've been assuming it's the xsetwacom rotate commands.  I haven't mentioned it before because it didn't seem relevant.  But...

There's a faint chance this could affect those of you adding the HALF line to the .fdi to make the tablet left-handed.  So maybe hold off on that for now.

---

### Post by kgingeri on 2009-11-16
> **Ayuthia said:**
> This is with WACOM_PKGLEN_BBPT set to 20?  I am just confirming because the info above only has 18 reported.

Ooops - I reran my script instead of manual compile (Duh!) - I should've check the data first.  

Will try again and update this post...
[B]
UPDATE:[/B] OK, **_already have touch back_** just reloading wacom.ko - will reboot tho anyway and give you logs.

---

### Post by kgingeri on 2009-11-16
> **Ayuthia said:**
> This is with WACOM_PKGLEN_BBPT set to 20?  I am just confirming because the info above only has 18 reported.

OK, much better again.  I have touch back (ver 27 ob1's fid - will try ob1-fav next)

Here's messages data...
```
Nov 16 22:53:01 kgulnb kernel: [  119.116665] [wacom-27] data: 02 00 45 80 dc 00 b6 80 d9 00 b3 00 00 00 00 00 81 11 00 00 
Nov 16 22:53:01 kgulnb kernel: [  119.136669] [wacom-27] data: 02 00 93 80 dc 00 b6 80 d9 00 b2 00 00 00 00 00 81 11 00 00 
Nov 16 22:53:01 kgulnb kernel: [  119.156660] [wacom-27] data: 02 00 93 80 dc 00 b4 80 d9 00 b1 00 00 00 00 00 81 11 00 00 
Nov 16 22:53:01 kgulnb kernel: [  119.176650] [wacom-27] data: 02 00 83 80 dd 00 b6 80 da 00 b2 00 00 00 00 00 81 11 00 00 
Nov 16 22:53:01 kgulnb kernel: [  119.192084] [wacom-27] data: 02 00 5b 80 dd 00 ba 80 da 00 b5 00 00 00 00 00 80 11 00 00 
Nov 16 22:53:01 kgulnb kernel: [  119.216645] [wacom-27] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

these msgs are not streaming now - just when there is activity - touch tap above....

Nov 16 22:54:13 kgulnb kernel: [  191.400532] [wacom-27] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 22:54:13 kgulnb kernel: [  191.416523] [wacom-27] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 22:54:14 kgulnb kernel: [  191.436498] [wacom-27] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 00 
Nov 16 22:54:14 kgulnb kernel: [  191.452507] [wacom-27] data: 02 00 51 24 37 16 12 00 12 02 f1 43 24 32 16 9a 02 13 02 f1 
Nov 16 22:54:14 kgulnb kernel: [  191.464499] [wacom-27] data: 02 f1 3b 24 34 16 66 02 14 02 f1 3b 24 2f 16 0e 02 15 02 f1 
Nov 16 22:54:14 kgulnb kernel: [  191.480495] [wacom-27] data: 02 f1 46 24 2d 16 f8 01 15 02 f1 46 24 26 16 fc 01 16 02 f1 
Nov 16 22:54:14 kgulnb kernel: [  191.496486] [wacom-27] data: 02 f1 49 24 28 16 f9 01 16 02 f1 50 24 21 16 ed 01 16 02 f1 
Nov 16 22:54:14 kgulnb kernel: [  191.512479] [wacom-27] data: 02 f1 5a 24 1b 16 bb 01 17 02 f1 67 24 13 16 6f 01 17 02 f1 
Nov 16 22:54:14 kgulnb kernel: [  191.524469] [wacom-27] data: 02 f1 78 24 11 16 ff 00 17 02 f1 92 24 10 16 42 00 17 02 f0 
Nov 16 22:54:14 kgulnb kernel: [  191.540465] [wacom-27] data: 02 f0 a6 24 0e 16 00 00 17 02 f0 b4 24 0c 16 00 00 15 02 f0 
Nov 16 22:54:14 kgulnb kernel: [  191.556456] [wacom-27] data: 02 f0 b9 24 03 16 00 00 13 02 f0 be 24 f8 15 00 00 11 02 f0 
Nov 16 22:54:14 kgulnb kernel: [  191.572429] [wacom-27] data: 02 f0 bb 24 f3 15 00 00 0e 02 f0 ba 24 f4 15 00 00 0b 02 f0 
Nov 16 22:54:14 kgulnb kernel: [  191.584443] [wacom-27] data: 02 f0 b8 24 ee 15 00 00 08 02 f0 bb 24 e9 15 00 00 06 02 f0 
Nov 16 22:54:14 kgulnb kernel: [  191.596436] [wacom-27] data: 02 f0 af 24 d8 15 00 00 04 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 22:54:14 kgulnb kernel: [  191.612424] [wacom-27] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 22:54:14 kgulnb kernel: [  191.628421] [wacom-27] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 00 

that was pen tap  

[Nov 16 22:54:36 kgulnb kernel: [  213.725367] [wacom-27] data: 02 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:54:36 kgulnb kernel: [  213.877287] [wacom-27] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:54:37 kgulnb kernel: [  214.984739] [wacom-27] data: 02 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:54:37 kgulnb kernel: [  215.160653] [wacom-27] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:54:38 kgulnb kernel: [  215.680386] [wacom-27] data: 02 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:54:38 kgulnb kernel: [  215.856302] [wacom-27] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:54:39 kgulnb kernel: [  216.424013] [wacom-27] data: 02 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 16 22:54:39 kgulnb kernel: [  216.551955] [wacom-27] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

that was all four buttons.
```

here is some from Xorg...
```
first touch...

xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 112 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 7 events received
usbParseChannel event[0]->type=3 code=0 value=234
usbParseChannel event[1]->type=3 code=1 value=143
usbParseChannel event[2]->type=3 code=24 value=149
usbParseChannel event[3]->type=3 code=40 value=3
usbParseChannel event[4]->type=1 code=333 value=1
USB Touch detected 14d (value=1)
usbParseChannel event[5]->type=1 code=330 value=1
usbParseChannel event[6]->type=0 code=0 value=0
xf86WcmEvent at channel = 0
xf86WcmEvent: c=0 i=3 t=2 s=0 x=234 y=143 b=1 p=149 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=402940 cs=0 
initialize Channel data.
commonDispatchDevice device type = 2
tool id=2 for Wacom Bamboo P&T 4x5 touch
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 touch - usbParse: dropping empty event for serial 0
xf86WcmReadPacket: device=/dev/input/event10 fd=14 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 112 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 7 events received
usbParseChannel event[0]->type=3 code=0 value=0
usbParseChannel event[1]->type=3 code=1 value=0
usbParseChannel event[2]->type=3 code=24 value=0
usbParseChannel event[3]->type=3 code=40 value=0
usbParseChannel event[4]->type=1 code=333 value=0
USB Touch detected 14d (value=0)
usbParseChannel event[5]->type=1 code=330 value=0
usbParseChannel event[6]->type=0 code=0 value=0
xf86WcmEvent at channel = 0
xf86WcmEvent: c=0 i=3 t=2 s=0 x=0 y=0 b=0 p=149 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=403159 cs=1 
xf86WcmFilterCoord with common->wcmRawSample = 4 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 2
tool id=2 for Wacom Bamboo P&T 4x5 touch


and pen...

xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 64 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 4 events received
usbParseChannel event[0]->type=1 code=325 value=0
USB Pad detected 145 (value=0)
usbParseChannel event[1]->type=3 code=40 value=0
usbParseChannel event[2]->type=4 code=0 value=240
usbParseChannel event[3]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=0 cs=2 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 16
no device matches with id=16, serial=240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 64 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 4 events received
usbParseChannel event[0]->type=1 code=325 value=1
USB Pad detected 145 (value=1)
usbParseChannel event[1]->type=3 code=40 value=15
usbParseChannel event[2]->type=4 code=0 value=240
usbParseChannel event[3]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=0 
initialize Channel data.
commonDispatchDevice device type = 16
no device matches with id=16, serial=240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 48 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 3 events received
usbParseChannel event[0]->type=1 code=257 value=1
usbParseChannel event[1]->type=4 code=0 value=240
usbParseChannel event[2]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=2 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 16
no device matches with id=16, serial=240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 48 bytes
usbParseEvent 
usbParseEvent 
usbParseEvent 
usbParseChannel 3 events received
usbParseChannel event[0]->type=1 code=257 value=0
usbParseChannel event[1]->type=4 code=0 value=240
usbParseChannel event[2]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=2 
xf86WcmSuppress at level = 2 return value = 1
commonDispatchDevice device type = 16
no device matches with id=16, serial=240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
xf86WcmReadPacket: device=/dev/input/event9 fd=13 
xf86WcmReadPacket: pos=0 remaining=256
xf86WcmReadPacket buffer has 32 bytes
usbParseEvent 
usbParseEvent 
Wacom Bamboo P&T 4x5 eraser - usbParse: dropping empty event for serial 240
^C

```

**UPDATE:** ob1-fav fdi didn't seem to make any difference except I do have xsetwacom devices listed.  However setting relative mode leaves the cursor stuck on the left side of my screen.

**ALSO** I am _only able to navigate the mouse in the upper left quad_ of my screen.  This is a 0xd1 tablet.

---

### Post by Ayuthia on 2009-11-16
I have removed a portion of a submitted patch in hopes that it will bring the packet data back to the way it was prior to all the data issues we have encountered today.

If this does not work, we will go back to patch 22 and start over.

I had to remove that patch because it seemed to cause more data to fill into the pen's report.  This could cause issues with the TabletPC devices if we keep the code there.

By the way, this is patch 29.  28 was there, but I realized that I forgot to fix another portion of the pen code.

---

### Post by ob1kenobi on 2009-11-16
> **Ayuthia said:**
> I have removed a portion of a submitted patch in hopes that it will bring the packet data back to the way it was prior to all the data issues we have encountered today.

If this does not work, we will go back to patch 21 again and start over.

I had to remove that patch because it seemed to cause more data to fill into the pen's report.  This could cause issues with the TabletPC devices if we keep the code there.

By the way, this is patch 29.  28 was there, but I realized that I forgot to fix another portion of the pen code.

Not to throw a wrench into things, but I now have my 0xD1 tablet back up and running with touch and pen (and eraser) based on the 25.x I put up earlier (which has more touch sensitive code).  The fdi I uploaded last night should not be used (yet).  I was having good results with it because I did not restart X.org.  Somehow there is a different initialisation order when X.org boots cleanly verses reinitialising input devices when the module is reinserted.  This is a bug in my opinion, and I'll have to figure out where it is.

I'm working on the patch now... upload in a few.
EDIT: Patch attached...

EDIT2: So this works, pen is now working to the white outline on the tablet instead of the full report range (Maybe because I enabled gestures in X.org code)?

EDIT3: ooooh, got a nice crunch crash "BUG: scheduling while atomic: Xorg" on CPU 3.  The stylus was in and out of range while I was drawing in gimp and touch was toggled a few times, may have something to do with the static int's for stylusInProx being read and written by two different usb devices.  May have to do a kernel mutex lock on the wacom before touching those variables... that's for tomorrow...

---

### Post by kgingeri on 2009-11-16
> **Ayuthia said:**
> I have removed a portion of a submitted patch in hopes that it will bring the packet data back to the way it was prior to all the data issues we have encountered today.

If this does not work, we will go back to patch 22 and start over.

I had to remove that patch because it seemed to cause more data to fill into the pen's report.  This could cause issues with the TabletPC devices if we keep the code there.

By the way, this is patch 29.  28 was there, but I realized that I forgot to fix another portion of the pen code.

No apparent changes Ayuthia.  Logs look about the same...messages pen data...
```
Nov 16 23:36:25 kgulnb kernel: [  509.973802] [wacom-29] data: 02 f0 26 1d ef 14 00 00 0b 02 f0 2b 1d e2 14 00 00 09 02 f0 
Nov 16 23:36:25 kgulnb kernel: [  509.989806] [wacom-29] data: 02 f0 45 1d dc 14 00 00 08 02 f0 61 1d d9 14 00 00 06 02 f0 
Nov 16 23:36:25 kgulnb kernel: [  510.005817] [wacom-29] data: 02 f0 80 1d dd 14 00 00 06 02 f0 af 1d e5 14 00 00 05 02 f0 
Nov 16 23:36:25 kgulnb kernel: [  510.017823] [wacom-29] data: 02 f0 c8 1d f0 14 00 00 04 02 f0 ee 1d dd 14 00 00 03 02 80 
Nov 16 23:36:25 kgulnb kernel: [  510.029836] [wacom-29] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:36:25 kgulnb kernel: [  510.045838] [wacom-29] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:36:25 kgulnb kernel: [  510.061839] [wacom-29] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:36:25 kgulnb kernel: [  510.077849] [wacom-29] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:36:25 kgulnb kernel: [  510.097857] [wacom-29] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
Nov 16 23:36:25 kgulnb kernel: [  510.113866] [wacom-29] data: 02 80 00 00 00 00 00 00 00 02 80 00 00 00 00 00 00 00 02 80 
```

Still only upper quarter of my screen navigable (is that a word?) for touch. Stylus data but no action.  :(

I think I better get some rest so I'm a little better for tomorrow ;)
Likely gone for the night now.

---

### Post by Favux on 2009-11-16
Hi kgingeri,

Could you try the working .fdi or alt.touch test3 in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") first?  If that doesn't work then the [test4 .fdi]("http://ubuntuforums.org/showpost.php?p=8319667&postcount=222") if you still have the energy.

---

### Post by kgingeri on 2009-11-16
> **Favux said:**
> Hi kgingeri,

Could you try the working .fdi or alt.touch test3 in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") first?  If that doesn't work then the [test4 .fdi]("http://ubuntuforums.org/showpost.php?p=8319667&postcount=222") if you still have the energy.

OK will do - and I'll update this post.

**NOTE**: This is with patch 29 Favux and all...

**UPDATE 1 of 2:** Ok with test3 I have full navigation with touch, constant selection but can set relative mode again. If I tap the stylus I get 10 Enter's -(yeah like pressing enter 10 times!) - no cursor tracking tho.  At times I see no constant select but I can reproduce that easily - may be pen and touch combo - not sure.  The eraser acts like a right click and the pad buttons appear to do nothing... xsetwacom for buttons does nothing either.  On to test 2...
EDIT: oops should mention that pen buttons did nothing.

**UPDATE 2 of 2:** Again full screen nav with touch, still constant selection with touch, can xsetwacom relative mode, button2/3 are assignable again but correspond to physical buttons 1 and 4.  Nothing at all stylus wise, not even in either log file!

Both of these tests are ONLY changing fdi files and rebooting.

---

### Post by Ayuthia on 2009-11-17
I have reverted the code and rebuilt from patch 22.  The only thing that is added is the fix for the resolution for the medium sized tablets.

The patch is now at 30.  I bumped it to 30 instead of using 22 again because of the one change.

If the test results from kgingeri's test in the previous post come out positive, we can go back to 29.

---

### Post by ob1kenobi on 2009-11-17
See post #390 if you missed it

---

### Post by kgingeri on 2009-11-17
> **Ayuthia said:**
> I have reverted the code and rebuilt from patch 22.  The only thing that is added is the fix for the resolution for the medium sized tablets.

The patch is now at 30.  I bumped it to 30 instead of using 22 again because of the one change.

If the test results from kgingeri's test in the previous post come out positive, we can go back to 29.

Done -see updates in that post  :)

---

### Post by kgingeri on 2009-11-17
> **ob1kenobi said:**
> See post #390 if you missed it

I did miss [#390]("http://ubuntuforums.org/showpost.php?p=8332594&postcount=390") Ob1.  Gotta run a small dog outside and I'll get back to you.  And I thought I was heading to bed! ;)

---

### Post by Ayuthia on 2009-11-17
If ob1kenobi's code tomorrow fixes the bug crash, we will continue from there.  Since kgingeri's results for patch 29 does not get the stylus working happily I will hold patch 30 as is for now.

The main change in patch 30 is with wacom_wac.c in line 171 where:
```
        x = wacom_be16_to_cpu ((unsigned char *)&data[3 + (idx * 9)]) & **0x1ff**;
```
is changed to:
```
        x = wacom_be16_to_cpu ((unsigned char *)&data[3 + (idx * 9)]) & **0x3ff**;
```

Otherwise, nothing else really changed.  So if the stylus does not report anything, you might try changing the bolded portion back to 0x1ff.

---

### Post by Favux on 2009-11-17
Hi kgingeri,

Thanks for checking them!  :)

---

### Post by kgingeri on 2009-11-17
[SIZE="5"][COLOR="DarkGreen"]HEY I HAVE PEN AND TOUCH FROM Ob1's PATCH!![/COLOR][/SIZE] :D

**But** I also had a system hang and had to do a _forced power off_ - ouch - mem leak?  :(

However, I had a seg fault trying to install wacom.ko the first time (weird) so I just repeated  the steps cleanly and I'll reboot and try again... standby...I'll update here.

EDIT: used whatever fdi is in his patch.

**UPDATE:** I had a full response nearly finish and my system got slow and hung before I could click save!!!  I've unloaded wacom so hopefully I'll get this posted!

Ok, Ob1's is onto something for sure.  Pen is FULLY functional :D  Touch is working as it has been - select constant with cursor movement.  I thought my system was going to be stable as both were working interactively for about 10 minutes.  Ob1 - a memory leak maybe?  On second reboot I tailed both logs with '-f' and there wasn't any constant data being logged with out tablet activity so not sure.

I do have a thought about installing sequence but I'll post this and do another post - it not critical likely.

---

### Post by kgingeri on 2009-11-17
Ok, I may be stable here again with out tablet plugged in and wacom removed.

My thought is that maybe Ayuthia's sequence in post #1 should be:
```
sudo make install
sudo modprobe -r wacom
sudo cp src/2.6.28/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
sudo modprobe wacom
```

Is it possible we are not always getting the wacom.ko loaded we think we are?!  Probably not an issue, but thought about it more since having the seg fault.  I may have been touching the tablet when I issued the command so maybe that could have done it?  It may just be a one-off to not worry about either.

OK, now I do gotta get some shut-eye... tomorrow guys and gals  :)

---

### Post by kgingeri on 2009-11-17
> **Ayuthia said:**
> If ob1kenobi's code tomorrow fixes the bug crash, we will continue from there.  Since kgingeri's results for patch 29 does not get the stylus working happily I will hold patch 30 as is for now.

The main change in patch 30 is with wacom_wac.c in line 171 where:
```
        x = wacom_be16_to_cpu ((unsigned char *)&data[3 + (idx * 9)]) & **0x1ff**;
```
is changed to:
```
        x = wacom_be16_to_cpu ((unsigned char *)&data[3 + (idx * 9)]) & **0x3ff**;
```

Otherwise, nothing else really changed.  So if the stylus does not report anything, you might try changing the bolded portion back to 0x1ff.

...OK just one more response ;)
Ayuthia, the pen was not TOTALLY unresponsive - a click on the tablet did give me 10 Enter's and the eraser was like a right click.  That's more than I've had before.  I did not get any cursor tracking tho - at all.

---

### Post by kgingeri on 2009-11-17
You know your a complete geek when you can't go to bed cuz you gotta try one more thing - right  :lol:

Well I thought I would try Favux's test3 fdi (it's the best one for me so far) and I have been running now (with 'top' in a terminal in case of crash) since a little after my last post - with BOTH touch and pen  :D  Also, you have the benefit of using xsetwacom to adjust things!  

One weird thing was when I set Button1 on pad, I lost touch (no pun intended ;)).  To set it back to default, don't include a value - so...
```
 ...to set Button1...
$ xsetwacom set pad Button1 "core key A"
...to reset...
$ xsetwacom set pad Button1  
``` ...back to default, I got touch back.  So the buttons are quite programmable properly just yet.

One thing I have noticed is after touch is idle, it seems to take a second or two to 'kick-in' again. The stylus works fine even while touching the tablet.  Did I mention that the stylus buttons all work, including eraser - oh and pressure too :D

I think I'll leave it run thru the night.  Dnprossi otta be up soon, so maybe he can try it too?  Nothing like global development ;)

**So to summarize:**
[LIST=1]
[*] use Ob1's patch from [here #390]("http://ubuntuforums.org/showpost.php?p=8332594&postcount=390")
[*] Favux's alt.touch_test3 fdi [here #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") in previous thread
[*] watch out for your system hanging solid.
[/LIST]

Have at it everyone!
...oh sleep, why doest thou allude me....zz z Z Z  Z   Z

---

### Post by Favux on 2009-11-17
Awesome kgingeri!!!

Didn't someone say one of the tablet buttons can/or does turn touch on/off in Win7?  So could Button1 be that button, and it's suppose to be toggling touch on and off?

---

### Post by dnprossi on 2009-11-17
> **Favux said:**
> Awesome kgingeri!!!

Didn't someone say one of the tablet buttons can/or does turn touch on/off in Win7?  So could Button1 be that button, and it's suppose to be toggling touch on and off?

hi Favux,
Yes, on windows, button 1 toggles touch on/off...

---

### Post by Favux on 2009-11-17
Hi dnprossi,

Thanks for confirming that.

I'm not sure how you would toggle touch on and off though.
```
xsetwacom set pad Button1 "????"
```
I don't see anything obvious.  Looking at:
```
xsetwacom list mod
```
doesn't show anything that jumps out at me.  At least kgingeri has shown us:
```
xsetwacom set pad Button1
```
sets it to touch on.  I guess a launcher with any other value would turn it off and one with no value turns touch back on.  Seems a little clumsy.  Be nicer to actually use the button.

---

### Post by dnprossi on 2009-11-17
hi favuk...
Was reading all missed posts and got lost, so decided to start with ayuthia's 30 patch and favuk's test 3 at first then messed it up a little and it may seem **heretic** but with the, maybe silly changes i did (playing around with a lot of imagination) I now got a 
[B]
tablet working as a touchpad
correct size pad 
receiving correct data in messages.log from buttons[/B]

Stylus working as should except buttons that work only on touching tablet with tip.

wacomcpl with errors but seem not to be important because everything works..

I attached fdi, please someone try it because it is strange...

I'll test ob1's patches now!!

---

### Post by Favux on 2009-11-17
Hi dnprossi,

Actually no, it now looks like the standard Wacom usb graphic tablet .fdi.  See [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  Except for touch, and I would have touch after pad.  And you are showing that touch can be appended to stylus with an info.callout through hal-setup-wacom just like a serial tablet pc with touch.  All of this on 'if0'.

My concern would be that I think we already ruled this out.  If you look closely I think there is a good chance that the touch is provided by a touchpad .fdi/driver through evdev or something similar.  And that's why wacomcpl looks funny with errors.

> Stylus working as should except buttons that work only on touching tablet with tip.
That's the default setting.  If you want to change it to "hover" mode in wacomcpl you go to Tool Buttons in stylus and change Side Switch Mode to Side Switch Only.

---

### Post by dnprossi on 2009-11-17
OK!! now i get it. Thanks for clearness. I will now try correct fdi's from ayuthia, ob1 and then your test3 as kgingeri's above...

> 
That's the default setting. If you want to change it to "hover" mode in wacomcpl you go to Tool Buttons in stylus and change Side Switch Mode to Side Switch Only.


Thanks! I must have read that in previous posts but just to much stuff to remember all...:)

---

### Post by dnprossi on 2009-11-17
**Because this thread is growing at the speed of light I will report my tests on an earlier post so please goto [#321]("http://ubuntuforums.org/showpost.php?p=8326473&postcount=321")**

[[COLOR="Red"]*** [/COLOR]Updated tests to ayuthia's patch [COLOR="Red"]0.8.5-4 30[/COLOR] ob1kenobi's [COLOR="Red"]0.8.5-4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8326473&postcount=321")

---

### Post by prefiks2 on 2009-11-17
This patch contains changes which make two finger gestures (left click, scroll and zoom) more or less work. It doesn't contains any recent changes, i think its based on 24 or 25, but doesn't at least doesn't broke anything on my setup.

Please be aware that two finger gestures doesn't work too well in relative mode.

---

### Post by Ayuthia on 2009-11-17
Can someone provide a sample of the /var/log/messages and /var/log/Xorg.0.log for patch 30 and for ob1kenobi's version?  I don't have a Wacom device so I need the log information to work on the code.  Any assistance here would be greatly appreciated.

---

### Post by Ayuthia on 2009-11-17
ob1kenobi and prefiks2 - There was memcopy change that was done for the features variable in wacom_sys.c.  Didn't that change how the data was being retrieved from the device?  Before that change, the stylus data only provided 18 bytes of data and with the change it brought in 20.  Is that correct?

If that is correct, we have to be cautious about breaking other devices.  wacom_probe is used by various devices and if the data stream changes for those devices, the patch that we provide will be rejected if it breaks any other device.

If that is not correct, do either of you know what caused the extra bytes to show up?

---

### Post by kgingeri on 2009-11-17
> **Ayuthia said:**
> Can someone provide a sample of the /var/log/messages and /var/log/Xorg.0.log for patch 30 and for ob1kenobi's version?  I don't have a Wacom device so I need the log information to work on the code.  Any assistance here would be greatly appreciated.

Very quick post!
Here is the last 5000 lines of both of mine - AND MY MACHINE IS STILL STABLE THIS MORNING :D

EDIT: Spoke too soon. Went to attach files to this post and everything locked up again!!!  :( Had to force a power off.

Gotta get to work tho.

---

### Post by prefiks2 on 2009-11-17
> **Ayuthia said:**
> ob1kenobi and prefiks2 - There was memcopy change that was done for the features variable in wacom_sys.c.  Didn't that change how the data was being retrieved from the device?  Before that change, the stylus data only provided 18 bytes of data and with the change it brought in 20.  Is that correct?


I always get 20 for touch and 18 for stylus, my latest patch even contains your quite modified change for removing that special case from overflow handling code

---

### Post by dnprossi on 2009-11-17
Ayuthia here are logs as requested referring to

[[COLOR="Red"]*** [/COLOR]Updated tests to ayuthia's patch [COLOR="Red"]0.8.5-4 30[/COLOR] ob1kenobi's [COLOR="Red"]0.8.5-4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8326473&postcount=321")

I deleted and recreated all logs for two tests using your fdi and followed steps below for each one.

**Steps taken with stylus: **
move on screen from far and tip on pad.
opened gimp new file.
pressure
eraser
closed gimp
button1 and button2

**Steps taken with touch:**
move on screen absolute
move on screen relative
Button1 2 3 4 in sequence...

---

### Post by Ayuthia on 2009-11-17
> **dnprossi said:**
> Ayuthia here are logs as requested referring to

[[COLOR="Red"]*** [/COLOR]Updated tests to ayuthia's patch [COLOR="Red"]0.8.5-4 30[/COLOR] ob1kenobi's [COLOR="Red"]0.8.5-4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8326473&postcount=321")

I deleted and recreated all logs for two tests using your fdi and followed steps below for each one.

**Steps taken with stylus: **
move on screen from far and tip on pad.
opened gimp new file.
pressure
eraser
closed gimp
button1 and button2

**Steps taken with touch:**
move on screen absolute
move on screen relative
Button1 2 3 4 in sequence...

Thanks!

Have you tried turning off the TPCButton for the touch:
```
xsetwacom set touch TPCButton 0
```
I think that is supposed to be the code to turn off the left-click action for touch.

---

### Post by dnprossi on 2009-11-17
> **Ayuthia said:**
> Thanks!

Have you tried turning off the TPCButton for the touch:
```
xsetwacom set touch TPCButton 0
```
I think that is supposed to be the code to turn off the left-click action for touch.

I tried that and different combinations but left-click action is always there...

In windows touch is set "left-click disabled" but there is no way that i found to enable it. Nothing in settings. Only way to select something is after a double tap to select an icon or double tap and drag multiple selection. You can also do that with some two finger solution but i never used it yet...

---

### Post by ob1kenobi on 2009-11-17
> **Ayuthia said:**
> ob1kenobi and prefiks2 - There was memcopy change that was done for the features variable in wacom_sys.c.  Didn't that change how the data was being retrieved from the device?  Before that change, the stylus data only provided 18 bytes of data and with the change it brought in 20.  Is that correct?

No, the features data was set to a wacom_features table address from wacom_wac.c which only had the data for the pen initially.  The table was then updated based on the information retrieved from the interface being probed on the device.  Since the wacom_probe is called twice (once for each interface on the tablet) and it was using the same pointer to the wacom_features table based on the usb id (e.g. 0xD1) it was overwriting the table data for the device with the information from the last interface probed (which is the touch in our case).

> 
If that is correct, we have to be cautious about breaking other devices.  wacom_probe is used by various devices and if the data stream changes for those devices, the patch that we provide will be rejected if it breaks any other device.

If that is not correct, do either of you know what caused the extra bytes to show up?
Other devices should work just fine with the change since most will have only one interface and only one probe call.  The extra bytes were my fault (I accidentally swapped the 20 and 18 sizes in the first 25x patch I provided yesterday when changing the WACOM_PKGLEN_BBPT definitions... sorry).

---

### Post by prefiks2 on 2009-11-17
As far as i studied this code there is no existing code for "touchpad left click"-like behaviour

---

### Post by ob1kenobi on 2009-11-17
> **kgingeri said:**
> Very quick post!
EDIT: Spoke too soon. Went to attach files to this post and everything locked up again!!!  :( Had to force a power off.
Gotta get to work tho.

kgingeri,
Added a spinlock to the wacom_bpt_irq call,  please test when you get a chance.  Hopefully you're at work by now and not wasting more time on this though;)

EDIT: Should also note that this incorporates prefiks2 last change to send MSC_SERIAL events (thanks prefiks2!)

EDIT2: Fix patch to be bzip2 compressed like it said it was...

---

### Post by rebecca2525 on 2009-11-17
ob1kenobi's patch is a tar.gz file, not a tar.bz2. Off testing...

---

### Post by ob1kenobi on 2009-11-17
> **rebecca2525 said:**
> ob1kenobi's patch is a tar.gz file, not a tar.bz2. Off testing...
Yes it is, sorry fat fingered h instead of j on the command line...

---

### Post by Ayuthia on 2009-11-17
I have created patch 31.  The goal of this patch is to slowly merge to ob1kenobi's changes.  Since something is causing the system to crash, I figured that we will slowly merge things to see if we can figure out where it is.

ob1kenobi, I was going to attach your patches and a pre-patched version to the first post also so that people can find it easier.  Should I use the most recent one out here or will you be creating a new set soon?  EDIT: Disregard this question.  I just saw your update.

I will also be adding prefiks2's patches soon for the gestures.  I just want to make sure that we have the touch and stylus sorted out first.

EDIT:
I have now attached the pre-patched source and patches for ob1kenobi's version.  The can be found in the first post at the bottom of the page.  The files are not attached in the forums but on another site so that if we need to go back to a previous patch, we now have a copy of them.

---

### Post by rebecca2525 on 2009-11-17
Using ob1's latest patch. Stylus and eraser seem to work as they should (with pressure and all), touch (with the left-click effect and absolute) works, and the scale is correct! The two topmost buttons (how do you count them? top to bottom?) issue middle and right clicks, the other two show up in /var/log/messages, but don't have any effect.

Wanted to use xsetwacom to try to set touch to relative, but am confused by this:
```

# xsetwacom list
Wacom_Bamboo_P&T_6x8     stylus
Wacom_Bamboo_P&T_6x8     stylus
Wacom_Bamboo_P&T_6x8_eraser     eraser
Wacom_Bamboo_P&T_6x8_pad     pad
```Errr, touch sometimes seems to stop working (or needs a while to react).

---

### Post by ob1kenobi on 2009-11-17
> **rebecca2525 said:**
> Using ob1's latest patch. Stylus and eraser seem to work as they should (with pressure and all), touch (with the left-click effect and absolute) works, and the scale is correct! The two topmost buttons (how do you count them? top to bottom?) issue middle and right clicks, the other two show up in /var/log/messages, but don't have any effect.

Wanted to use xsetwacom to try to set touch to relative, but am confused by this:
```

# xsetwacom list
Wacom_Bamboo_P&T_6x8     stylus
Wacom_Bamboo_P&T_6x8     stylus
Wacom_Bamboo_P&T_6x8_eraser     eraser
Wacom_Bamboo_P&T_6x8_pad     pad
```


Not sure why touch is not showing up.

It's a bit to explain, but there was a bug somewhere when I was testing that was causing problems with changing the info.product in the fdi file, which is why I went back to a semi-vanilla fdi file which creates these info.product_name.   I'll have to play around with it a bit more tonight... but it may end up requiring a change to the features->name field for each device to differentiate.


> Errr, touch sometimes seems to stop working (or needs a while to react).

Can you expand on this? May be related to the spinlocks taking up too much time?  Is there a certain time that it stops working (e.g. when you are switching from pen to touch?)

---

### Post by rebecca2525 on 2009-11-17
With patch 31, the data in /var/log/messages all looks like this:

```
Nov 17 19:09:44 zam559 kernel: [  418.997557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.001562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.005561] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.009557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.013554] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.017555] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.021560] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.025559] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.029562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.033561] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.037562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.041562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.045561] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.049556] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.053551] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.057557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.061555] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.065556] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.069562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.073562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.077559] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.081561] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.085552] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.089562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.093562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.097540] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.101554] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.105562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.109557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.113555] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.117562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.121562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.125553] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.129551] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.133554] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.137554] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.141555] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.145552] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.149523] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.153526] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.157558] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.161557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.165556] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.169558] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.173562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.177560] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.181558] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.185562] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.189556] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.193561] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.197556] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.201557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.205558] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.209551] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.213558] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.217558] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.221557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.225557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:09:44 zam559 kernel: [  419.229557] [wacom-31] data: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
```
no matter if I use touch, stylus, eraser, buttons. Lots of zeroes.

Wait a minute, it does produce that data when I'm not doing anything, using the tablet does not seem to have any effect...?

---

### Post by rebecca2525 on 2009-11-17
> **ob1kenobi said:**
> Can you expand on this? May be related to the spinlocks taking up too much time?  Is there a certain time that it stops working (e.g. when you are switching from pen to touch?)
So far it didn't happen in the midst of using touch, but when not having used the tablet at all or switching between stylus/touch. Sometimes it was just a few seconds not working, but sometimes long enough that I didn't think it might be back (but in the end, it always was back). Stylus didn't seem to be affected, and the effect didn't eat up any resources on my system as far as I could tell. I haven't used your version for very long though.

---

### Post by ob1kenobi on 2009-11-17
> **rebecca2525 said:**
> With patch 31, the data in /var/log/messages all looks like this:


Wait a minute, it does produce that data when I'm not doing anything, using the tablet does not seem to have any effect...?

Can you post the initialization data from /var/log/messages from when you do a modprobe wacom?  should be the first thing the module prints out.

---

### Post by rebecca2525 on 2009-11-17
```
Nov 17 19:19:44 zam559 kernel: [ 1019.468104] usb 6-1: new full speed USB device using uhci_hcd and address 3
Nov 17 19:19:45 zam559 kernel: [ 1019.628662] usb 6-1: New USB device found, idVendor=056a, idProduct=00d3
Nov 17 19:19:45 zam559 kernel: [ 1019.628670] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 17 19:19:45 zam559 kernel: [ 1019.628676] usb 6-1: Product: CTH-661
Nov 17 19:19:45 zam559 kernel: [ 1019.628681] usb 6-1: Manufacturer: Wacom Co.,Ltd.
Nov 17 19:19:45 zam559 kernel: [ 1019.628857] usb 6-1: configuration #1 chosen from 1 choice
Nov 17 19:19:45 zam559 kernel: [ 1019.649934] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input17
Nov 17 19:19:45 zam559 kernel: [ 1019.659684] finger report data:09 30 35 00 46 44 48 26 e4 02 75 10 95 01 81 02 09 31 46 d4 <7>/home/rbreu-nb/linuxwacom/linuxwacom-0.8.5-4-patch-31/src/2.6.28/wacom_sys.c: finger
Nov 17 19:19:45 zam559 kernel: [ 1019.659717] finger report data:09 31 46 d4 30 26 f4 01 81 02 06 00 ff 09 01 26 ff 00 75 08 <7>/home/rbreu-nb/linuxwacom/linuxwacom-0.8.5-4-patch-31/src/2.6.28/wacom_sys.c: finger
Nov 17 19:19:45 zam559 kernel: [ 1019.659915] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input18
Nov 17 19:19:45 zam559 kernel: [ 1019.663715] usbcore: registered new interface driver wacom
Nov 17 19:19:45 zam559 kernel: [ 1019.663723] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
Nov 17 19:19:45 zam559 kernel: [ 1020.038643] [wacom-31] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:19:45 zam559 kernel: [ 1020.042638] [wacom-31] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Nov 17 19:19:45 zam559 kernel: [ 1020.046638] [wacom-31] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
```

---

### Post by ob1kenobi on 2009-11-17
which kernel version are you compiling against?

---

### Post by rebecca2525 on 2009-11-17
2.6.30-2-amd64 which is the default kernel for Debian Testing (yeah, not on Ubuntu here...)

Compiling didn't go smoothly on my system, I had [this problem]("http://sourceforge.net/mailarchive/message.php?msg_name=20091111144702.645d1830%40zam559.zam.kfa-juelich.de")  which I [solved this way]("http://sourceforge.net/mailarchive/message.php?msg_name=20091111230322.6fbe7e18%40zam559"). I hope that isn't causing any problems now. It worked fine so far.[URL="http://sourceforge.net/mailarchive/message.php?msg_name=20091111144702.645d1830%40zam559.zam.kfa-juelich.de"]
[/URL]

---

### Post by marek_online on 2009-11-17
Hi everyone,

Just tried patch 31 and ob1kenobi's.

With patch 31, I have stylus and eraser with pressure, but no movement from touch, and X crashes on reboot as before.

With ob1kenobi's 25.x patch I have stylus and eraser, but touch is scaled to the top-left quarter of my screen after a reboot (it seemed to have been scaled to the whole screen before the reboot). The buttons on the pad are, in right-handed profile from the top-down: left-click, right-click, middle-click with upward movement, middle-click with downward movement.

The logs here are from the 25.x patch. I'm getting dragged out the door right now, but I'll try to post back later with something worthwhile on patch 31 (no doubt I'll be two version behind then!)

---

### Post by ob1kenobi on 2009-11-17
> **marek_online said:**
> Hi everyone,

With ob1kenobi's 25.x patch I have stylus and eraser, but touch is scaled to the top-left quarter of my screen after a reboot (it seemed to have been scaled to the whole screen before the reboot).

This is the fdi/X.org bug I was talking about in post #390

---

### Post by ob1kenobi on 2009-11-17
> **rebecca2525 said:**
> 2.6.30-2-amd64 which is the default kernel for Debian Testing (yeah, not on Ubuntu here...)

Compiling didn't go smoothly on my system, I had [this problem]("http://sourceforge.net/mailarchive/message.php?msg_name=20091111144702.645d1830%40zam559.zam.kfa-juelich.de")  which I [solved this way]("http://sourceforge.net/mailarchive/message.php?msg_name=20091111230322.6fbe7e18%40zam559"). I hope that isn't causing any problems now. It worked fine so far.[URL="http://sourceforge.net/mailarchive/message.php?msg_name=20091111144702.645d1830%40zam559.zam.kfa-juelich.de"]
[/URL]

Ok you must be missing the dbg definition in usb.h in the kernel headers.

You can add this after #define DEBUG in wacom_wac.c and wacom_sys.c to get the full printouts:

```

#ifdef DEBUG
#define dbg(format, arg...) printk(KERN_DEBUG "%s: " format "\n" , \
        __FILE__ , ## arg)
#else
#define dbg(format, arg...) do {} while (0)
#endif

```

EDIT:  then repost the message log entries from modprobe wacom please :)

---

### Post by kgingeri on 2009-11-17
> **ob1kenobi said:**
> kgingeri,
Added a spinlock to the wacom_bpt_irq call,  please test when you get a chance.  Hopefully you're at work by now and not wasting more time on this though;)

EDIT: Should also note that this incorporates prefiks2 last change to send MSC_SERIAL events (thanks prefiks2!)

EDIT2: Fix patch to be bzip2 compressed like it said it was...

I am at work - and trying like crazy to keep my nose clean  ;)
I should get a change later tonight (it's now 2:16pm my time)

---

### Post by rebecca2525 on 2009-11-17
> **ob1kenobi said:**
> Ok you must be missing the dbg definition in usb.h in the kernel headers.

You can add this after #define DEBUG in wacom_wac.c and wacom_sys.c to get the full printouts:

```

#ifdef DEBUG
#define dbg(format, arg...) printk(KERN_DEBUG "%s: " format "\n" , \
        __FILE__ , ## arg)
#else
#define dbg(format, arg...) do {} while (0)
#endif

```EDIT:  then repost the message log entries from modprobe wacom please :)

This doesn't change a thing in /var/log/messages, but I noticed that [there's more output in dmesg]("http://paste.pocoo.org/show/151264/"), is that the info you are looking for? (I always thought that the output in dmesg and /var/log/messages would be the same, but well...) Btw, I just plugged the tablet in for a couple of seconds without using it to produce that output.

---

### Post by ob1kenobi on 2009-11-17
> **rebecca2525 said:**
> This doesn't change a thing in /var/log/messages, but I noticed that [there's more output in dmesg]("http://paste.pocoo.org/show/151264/"), is that the info you are looking for? (I always thought that the output in dmesg and /var/log/messages would be the same, but well...) Btw, I just plugged the tablet in for a couple of seconds without using it to produce that output.

Didn't think about the logging structure, but I always do a tail -f /var/log/syslog instead of messages when I insert the module... Still not sure why the tablet appears to be streaming touch data on patch 31... hmmm

---

### Post by Ayuthia on 2009-11-17
It is because of the packet length.  In wacom_wac.c around line 1221 or so, you should see:
```

    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-460
    { "Wacom Bamboo Craft",       WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-461/S
    { "Wacom Bamboo P&T 6x8",     WACOM_PKGLEN_BBPT_PEN,  21648, 13530, 1023, 63, BAMBOO_PT }, // CTH-661
    { "Wacom Bamboo Touch",       WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT },

```
It should be:
```

    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-460
    { "Wacom Bamboo Craft",       WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-461/S
    { "Wacom Bamboo P&T 6x8",     WACOM_PKGLEN_BBPT_TOUCH,  21648, 13530, 1023, 63, BAMBOO_PT }, // CTH-661
    { "Wacom Bamboo Touch",       WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT },

```

I overlooked that section.

ob1kenobi, why do you have that section listed as PEN instead of TOUCH?  If we have it at TOUCH, we wouldn't need to configure it in wacom_probe in wacom_sys.c, right?

---

### Post by ob1kenobi on 2009-11-17
> **Ayuthia said:**
> 
ob1kenobi, why do you have that section listed as PEN instead of TOUCH?  If we have it at TOUCH, we wouldn't need to configure it in wacom_probe in wacom_sys.c, right?

Nope, there is only one feature entry per device id in that table.  Unfortunately these tablets are one device with two interfaces.  I default to PEN in the features entry for purely semantical reasons (i.e. the wacom's are traditionally pen devices).  In 25.2 I modify that pktlen entry to match the touch packet length if that is the current interface being probed.  And with prefiks2 dynamically allocated features patch, it creates two separate structures (one for each interface) with the separate and correct information for two interfaces on the device.

Still doesn't explain why tablet messages are always on from patch 31...
EDIT: Click... Yes it does, since patch 31 doesn't change the features->pktlen like 25.2 does, it registers usb_fill_urb_int with the shorter 18 message length.  Which is why changing the wacom_features table to BBPT_TOUCH makes 31 work.

---

### Post by rebecca2525 on 2009-11-17
> **Ayuthia said:**
> It is because of the packet length.  In wacom_wac.c around line 1221 or so, you should see:
```

    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-460
    { "Wacom Bamboo Craft",       WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-461/S
    { "Wacom Bamboo P&T 6x8",     WACOM_PKGLEN_BBPT_PEN,  21648, 13530, 1023, 63, BAMBOO_PT }, // CTH-661
    { "Wacom Bamboo Touch",       WACOM_PKGLEN_BBPT_PEN,  14720,  9200, 1023, 63, BAMBOO_PT },

```It should be:
```

    { "Wacom Bamboo P&T 4x5",     WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT },  // CTH-460
    { "Wacom Bamboo Pen 4x5",     WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-460
    { "Wacom Bamboo Craft",       WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT }, // CTL-461/S
    { "Wacom Bamboo P&T 6x8",     WACOM_PKGLEN_BBPT_TOUCH,  21648, 13530, 1023, 63, BAMBOO_PT }, // CTH-661
    { "Wacom Bamboo Touch",       WACOM_PKGLEN_BBPT_TOUCH,  14720,  9200, 1023, 63, BAMBOO_PT },

```I overlooked that section.

ob1kenobi, why do you have that section listed as PEN instead of TOUCH?  If we have it at TOUCH, we wouldn't need to configure it in wacom_probe in wacom_sys.c, right?

OK, I changed that, and things are looking more normal now. Will report back with more details.

---

### Post by Ayuthia on 2009-11-17
> **ob1kenobi said:**
> Nope, there is only one feature entry per device id in that table.  Unfortunately these tablets are one device with two interfaces.  I default to PEN in the features entry for purely semantical reasons (i.e. the wacom's are traditionally pen devices).  In 25.2 I modify that pktlen entry to match the touch packet length if that is the current interface being probed.  And with prefiks2 dynamically allocated features patch, it creates two separate structures (one for each interface) with the separate and correct information for two interfaces on the device.

Still doesn't explain why tablet messages are always on from patch 31...

I have not made those updates in 31-33 as of yet.  I wanted to see if the original way gets us moving a little bit and then I was going to start merging that portion in.

---

### Post by prefiks2 on 2009-11-17
Two new patches, one which adds null check which i forgot in one of my earlier patches, and seconds one for making touch works more like touchpad in regard of left mouse button clicks (it quite raw, but can be tested, please check if implemented behaviour is ok)

---

### Post by ob1kenobi on 2009-11-17
> **Ayuthia said:**
> I have not made those updates in 31-33 as of yet.  I wanted to see if the original way gets us moving a little bit and then I was going to start merging that portion in.

I edited my last post, but I'll repost why it does make a difference...

Since patch 31 doesn't change the features->pktlen like 25.2 does, it registers usb_fill_urb_int with the shorter 18 message length. Which is why changing the wacom_features table to BBPT_TOUCH makes 31 work.

---

### Post by ob1kenobi on 2009-11-17
With prefiks2's latest changes

---

### Post by rebecca2525 on 2009-11-17
Patch 31:

Stylus and eraser produce data, but don't have any effect.  --> worked in ob1's 25.2 patch.

Button 1: middle clicke, Button 2: right click, other buttons have no effect (numbered from top to bottom in right-handed mode) --> same as in ob1's 25.2 patch.

Touch works in absolute mode with left-click effect, scale is wrong (I can only reach the upper left quarter of my screen). --> in ob1's 25.2 patch.scale was ok, but touch sometimes stopped working

xsetwacom lists eraser, stylus, pad, touch --> ob1's 25.2 patch.missed touch

setting TPCButton with xsetwacom has no effect

setting touch mode to relative with xsetwacom and then touching the tablet hast the effect that the cursor gets placed at the left border of the screen and stays there.

---

### Post by ob1kenobi on 2009-11-17
can you try 25.2 with 31's fdi file please? see if that gets the touch to show up in xsetwacom list.

---

### Post by prefiks2 on 2009-11-17
> **rebecca2525 said:**
> Patch 31:
setting touch mode to relative with xsetwacom and then touching the tablet hast the effect that the cursor gets placed at the left border of the screen and stays there.

You can fix that with xsetwacom:

xsetwacom set touch bottomx 740
xsetwacom set touch bottomy 500

But driver should do that for you... (those numbers are correct for medium one tablet, i don't know correct values for smaller ones but you can find them in log you need to search for wacom_wac->features->{x,y}_max)

---

### Post by rebecca2525 on 2009-11-17
> can you try 25.2 with 31's fdi file please? see if that gets the touch to show up in xsetwacom list.

```
$ xsetwacom list
eraser     eraser
stylus     stylus
pad     pad
touch     touch
```Better. :) But scale isn't right on touch, I can only reach the upper left quarter of my screen, as before left-click-problem and absolute movement. Pen and stylus work fine (with pressure and all). Tablet buttons as before (Button 1: middle clicke, Button 2: right click, other buttons have no effect), using xsetwacom on mode and TPCButton as before (TPCButton --> no effect, touch mode relative --> touching the tablet hast the effect that the cursor gets placed at the left border of the screen and stays there.) Touch has not stopped working so far.

---

### Post by rebecca2525 on 2009-11-17
> **prefiks2 said:**
> You can fix that with xsetwacom:

xsetwacom set touch bottomx 740
xsetwacom set touch bottomy 500

But driver should do that for you... (those numbers are correct for medium one tablet, i don't know correct values for smaller ones but you can find them in log you need to search for wacom_wac->features->{x,y}_max)

**W00t!** Relative cursor movement!

---

### Post by rebecca2525 on 2009-11-17
oops, double post.

---

### Post by prefiks2 on 2009-11-17
> **rebecca2525 said:**
> oops, double post.

Now is triple ;)

---

### Post by rebecca2525 on 2009-11-17
Hehe. I can also set the relative cursor speed with xsetwacom, and stylus overwrites touch as it's supposed to be. Yay! Touch sometimes does stop working for a few seconds, but I'm not sure yet if there's a pattern.

Overall very nice! =D>

Wait a minute, in MyPaint I can already use two fingers to scroll sideways? How cool is that! (Although it scrolls in the opposite direction I thought it should. :lol:) And trying to scroll up and down has the cursor end up in the lower right corner of the screen. Or am I just seeing a side-effect of something else?

---

### Post by ob1kenobi on 2009-11-17
> **rebecca2525 said:**
> Hehe. I can also set the relative cursor speed with xsetwacom, and stylus overwrites touch as it's supposed to be. Yay! Touch sometimes does stop working for a few seconds, but I'm not sure yet if there's a pattern.

Overall very nice! =D>

Wait a minute, in MyPaint I can already use two fingers to scroll sideways? How cool is that! (Although it scrolls in the opposite direction I thought it should. :lol:) And trying to scroll up and down has the cursor end up in the lower right corner of the screen. Or am I just seeing a side-effect of something else?

Which patch are you on right now?

---

### Post by prefiks2 on 2009-11-17
> **rebecca2525 said:**
> And trying to scroll up and down has the cursor end up in the lower right corner of the screen. Or am I just seeing a side-effect of something else?

Its bug in gestures code, somehow its only visible in relative mode.

---

### Post by rebecca2525 on 2009-11-17
> **ob1kenobi said:**
> Which patch are you on right now?
Sorry, I'm so exited right now! ;) Your 25.2 with the 31 fdi.

---

### Post by ob1kenobi on 2009-11-17
> **rebecca2525 said:**
> Sorry, I'm so exited right now! ;) Your 25.2 with the 31 fdi.

Please try 25.3 in post #445 with 31s fdi. It has prefiks2's latest xorg code in it. You will need to recompile and install the xdrv and kernel module and reboot.

If it works, we may have a new target for patch 34.

---

### Post by rebecca2525 on 2009-11-17
> **prefiks2 said:**
> Its bug in gestures code, somehow its only visible in relative mode.
Confirmed.

During the last 40 minutes or so, X hung twice. The last time it got unstuck when I pressed a tablet button, don't recall what I did the first time (not restart, something else). I attached the xorg log.

> Please try 25.3 a few pages back with 31s fdi. It has prefiks2's latest xorg code in it. You will need to recompile and install the xdrv and kernel module and reboot.I'd love to, but I should go to bed now...

---

### Post by Favux on 2009-11-17
Hi everyone,

Cool, more progress.

Just for fun I decided to take a fresh look at the 10-linuxwacom.fdi in 0.8.5-4.  Following ob1's lead I've tried to make the minimum changes to support the Bamboo P & T's and yet keep all the previous Wacom tablets supported.  And hopefully (with a lot of luck) populate "xsetwacom list" for usb, serial, and bluetooth tablets.  So wacomcpl is available.

It's still not clear to me that for the P & T's that pad needs to be on 'if1' so I left it in 'if0'.  If it does need to be added to 'if1' I think that can be done with an info.callout to hal-setup-wacom and pad append without interfering with the pad on 'if0'.

---

### Post by Ayuthia on 2009-11-17
I have changed the first post to reflect the current progress going on with ob1kenobi and prefiks2 changes.  I feel that it would be easier than trying to test multiple versions at this point.  With the speed of all the changes, I did not join the correct fdi file yet, but I will do that for the next release.  I did add Favux's fdi file as a link for testing.  I also left ob1kenobi's version there in case we still need to test it.

---

### Post by Ayuthia on 2009-11-17
Additional items for testing:
[LIST]
[*]Pressing the middle buttons
[*]Testing out the fdi file from post 459
[*]When X gets stuck, does control-alt-F1 bring you to a console (control-alt-F7 to return to X) or if you use the stylus, finger, or one of the buttons bring things back to normal?  Also if it does not work, does control-alt-sys-rq R-E-I-S-U-B allow you to reboot without forcing the power down?  When it does crash, does anything show up in /var/log/messages or /var/log/Xorg.0.log?
[*]Test the changes with another Wacom device to see if it still works the same or better
[/LIST]

---

### Post by GolemdX on 2009-11-17
Hi everybody.

Just wanted to say that I appreciate all your work going into this, and I'm constantly following the thread and updating. It's interesting to read, however, I don't have much to offer in terms of help so I won't be posting in this thread anymore, unless I feel it's important.

See you later, bye.

---

### Post by kgingeri on 2009-11-17
> **Ayuthia said:**
> Additional items for testing:
[LIST]
[*]Pressing the middle buttons
[*]Testing out the fdi file from post 459
[*]**When X gets stuck, does control-alt-F1 bring you to a console (control-alt-F7 to return to X) or if you use the stylus, finger, or one of the buttons bring things back to normal?  Also if it does not work, does control-alt-sys-rq R-E-I-S-U-B allow you to reboot without forcing the power down?  When it does crash, does anything show up in /var/log/messages or /var/log/Xorg.0.log?**
[*]Test the changes with another Wacom device to see if it still works the same or better
[/LIST]

**Ayuthia**, in response to the bolded point above, my system locks up solid - nothing no how but a power off (tho I may not have tried Ctrl-Alt-F1).  I am not familiar with [COLOR="DimGray"]"control-alt-sys-rq R-E-I-S-U-B"[/COLOR]!  Is that Ctrl+Alt+SysRq held and then the lettered keys pressed in sequence?
I did find what I think is messages log info at the time of one of my hangs - it's attached.  I PM'd it to Ob1 last nigh already.  There is no activity visible at all at time of crash - not disk or network.  Seems like it could be a kernel loop/memory leak issue.  I had 'top' running last night but it was working for a long time until it crashed 7 or 8 hours later.  No pattern that I can tell.

Hey **GolemdX**, hope you left a real email address in your profile so we can PM (Private Message) you if we need you.  You had the Touch only tablet, right?  Thanks for joining in - it takes team work!!

To **All**, I'm only back in for a bit tonight - don't have much time.  In trying to get caught up, I'm not sure we are much further ahead as I had everything Rebecca2525 described last night BUT I will download from Post 1 and test again to be sure...  Away I go...  post back in a bit

Crash Forensics:
```
Nov 17 00:22:12 kgulnb kernel: [  507.996181] [wacom-29] data: 02 00 91 80 cd 00 79 80 cc 00 75 00 00 00 00 00 80 11 00 00
Nov 17 00:22:12 kgulnb kernel: [  508.020152] [wacom-29] data: 02 00 82 80 d2 00 87 80 d0 00 85 00 00 00 00 00 81 11 00 00
Nov 17 00:22:12 kgulnb kernel: [  508.036153] [wacom-29] data: 02 00 69 80 d5 00 90 80 d3 00 8c 00 00 00 00 00 80 11 00 00
Nov 17 00:22:12 kgulnb kernel: [  508.056142] [wacom-29] data: 02 00 34 80 d8 00 9c 80 d6 00 9a 00 00 00 00 00 81 11 00 00
Nov 17 00:22:12 kgulnb kernel: [  508.076127] [wacom-29] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Nov 17 00:26:16 kgulnb kernel: [  751.883500] ath5k phy0: unsupported jumbo
Nov 17 00:36:17 kgulnb kernel: [ 1353.076378] ath5k phy0: unsupported jumbo
Nov 17 00:42:55 kgulnb kernel: [ 1750.922395] usbcore: deregistering interface driver wacom
Nov 17 00:42:55 kgulnb kernel: [ 1750.969687] Modules linked in: binfmt_misc ppdev bridge stp bnep snd_hda_codec_realtek snd_hda_intel snd_hda_
Nov 17 00:42:55 kgulnb kernel: [ 1750.969888]
Nov 17 00:42:55 kgulnb kernel: [ 1750.969901] Pid: 6659, comm: modprobe Not tainted (2.6.31-14-generic #48-Ubuntu) AOA110
Nov 17 00:42:55 kgulnb kernel: [ 1750.969914] EIP: 0060:[<c01df4b2>] EFLAGS: 00210246 CPU: 1
Nov 17 00:42:55 kgulnb kernel: [ 1750.969934] EIP is at kfree+0xe2/0xf0
Nov 17 00:42:55 kgulnb kernel: [ 1750.969945] EAX: 80020028 EBX: f80d9f14 ECX: 00200296 EDX: c1701b20
Nov 17 00:42:55 kgulnb kernel: [ 1750.969957] ESI: f80d5a51 EDI: f80da020 EBP: db0bbe94 ESP: db0bbe80
Nov 17 00:42:55 kgulnb kernel: [ 1750.969969]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 17 00:42:55 kgulnb kernel: [ 1750.969999]  f80da020 db0bbe94 ef32b420 ef30e400 f80da020 db0bbea8 f80d5a51 2f093060
Nov 17 00:42:55 kgulnb kernel: [ 1750.970028] <0> ef30e400 ef30e41c db0bbec4 c04148c9 00000000 ef0ee800 ef30e41c f80da054
Nov 17 00:42:55 kgulnb kernel: [ 1750.970059] <0> ef30e450 db0bbed4 c03a26de ef30e41c f80da054 db0bbee8 c03a27bf c07780e0
Nov 17 00:42:55 kgulnb kernel: [ 1750.970135]  [<f80d5a51>] ? wacom_disconnect+0x51/0x70 [wacom]
Nov 17 00:42:55 kgulnb kernel: [ 1750.970157]  [<c04148c9>] ? usb_unbind_interface+0xe9/0x120
Nov 17 00:42:55 kgulnb kernel: [ 1750.970184]  [<c03a26de>] ? __device_release_driver+0x3e/0x90
Nov 17 00:42:55 kgulnb kernel: [ 1750.970208]  [<c03a27bf>] ? driver_detach+0x8f/0xa0
Nov 17 00:42:55 kgulnb kernel: [ 1750.970231]  [<c03a1a83>] ? bus_remove_driver+0x73/0x90
Nov 17 00:42:55 kgulnb kernel: [ 1750.970255]  [<c03a2cc6>] ? driver_unregister+0x46/0x80
Nov 17 00:42:55 kgulnb kernel: [ 1750.970274]  [<c023968d>] ? sysfs_remove_file+0xd/0x10
Nov 17 00:42:55 kgulnb kernel: [ 1750.970300]  [<c0413fe5>] ? usb_deregister+0x95/0xb0
Nov 17 00:42:55 kgulnb kernel: [ 1750.970339]  [<f80d6c81>] ? wacom_exit+0xd/0xf [wacom]
Nov 17 00:42:55 kgulnb kernel: [ 1750.970358]  [<c0171569>] ? sys_delete_module+0x169/0x200
Nov 17 00:42:55 kgulnb kernel: [ 1750.970377]  [<c0572d4b>] ? do_page_fault+0x19b/0x380
Nov 17 00:42:55 kgulnb kernel: [ 1750.970394]  [<c010336c>] ? syscall_call+0x7/0xb
Nov 17 00:42:55 kgulnb kernel: [ 1750.970598] ---[ end trace 2fb57dc83845f571 ]---
Nov 17 00:45:23 kgulnb kernel: Kernel logging (proc) stopped.
Nov 17 00:46:00 kgulnb kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Nov 17 00:46:00 kgulnb rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="757" x-info="http://www.rsyslog.com"] (re)start
```

---

### Post by kgingeri on 2009-11-17
Ayuthia, just downloaded from post 1 that read "wcm_patch-0.8.5-4-25.3.tar.bz2" but the file is actually wcm_patch-0.8.5-4-25.**_2_**.tar.bz2.  Will proceed anyway.

---

### Post by Ayuthia on 2009-11-17
> **kgingeri said:**
> Ayuthia, just downloaded from post 1 that read "wcm_patch-0.8.5-4-25.3.tar.bz2" but the file is actually wcm_patch-0.8.5-4-25.**_2_**.tar.bz2.  Will proceed anyway.

If it is .2, then it is pointing to the wrong file.  It should be .3.

EDIT:  The post was pointing to the wrong link.  It is now updated.  Sorry about that.

---

### Post by Ayuthia on 2009-11-17
> **kgingeri said:**
> **Ayuthia**, in response to the bolded point above, my system locks up solid - nothing no how but a power off (tho I may not have tried Ctrl-Alt-F1).  I am not familiar with [COLOR="DimGray"]"control-alt-sys-rq R-E-I-S-U-B"[/COLOR]!  Is that Ctrl+Alt+SysRq held and then the lettered keys pressed in sequence?


You have control-alt held and then SysRq and the lettered keys pressed in sequence.

---

### Post by kgingeri on 2009-11-17
> **Ayuthia said:**
> You have control-alt held and then SysRq and the lettered keys pressed in sequence.

Thx.  Will re-download and compile.

Any idea what the keys stand for - so my tiny brain can remember it?! ;)
*Sheesh... didn't know this one!*

---

### Post by Ayuthia on 2009-11-17
> **kgingeri said:**
> Thx.  Will re-download and compile.

Any idea what the keys stand for - so my tiny brain can remember it?! ;)
*Sheesh... didn't know this one!*

I guess it is only alt not control-alt.  From this [link]("http://kember.net/articles/231/reisub-the-gentle-linux-restart"):
```

    * R: Switch the keyboard from raw mode to XLATE mode
    * E: Send the SIGTERM signal to all processes except init
    * I: Send the SIGKILL signal to all processes except init
    * S: Sync all mounted filesystems
    * U: Remount all mounted filesystems in read-only mode
    * B: Immediately reboot the system, without unmounting partitions or syncing

```

---

### Post by Ayuthia on 2009-11-17
This is an odd request, can someone test the buttons on the tablet while either the pen or finger is on the pad?  I think I can see the button information in Xorg.0.log, but they are getting rejected:
```

usbParseChannel 6 events received
usbParseChannel event[0]->type=1 code=259 value=1
usbParseChannel event[1]->type=1 code=325 value=1
USB Pad detected 145 (value=1)
usbParseChannel event[2]->type=3 code=40 value=15
usbParseChannel event[3]->type=4 code=0 value=240
usbParseChannel event[4]->type=3 code=40 value=0
usbParseChannel event[5]->type=0 code=0 value=0
xf86WcmEvent at channel = 1
xf86WcmEvent: c=1 i=15 t=16 s=240 x=0 y=0 b=8 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=0
initialize Channel data.
commonDispatchDevice device type = 16
tool id=16 for pad
usbParseEvent
usbParseEvent
touch - usbParse: dropping empty event for serial 240

```
It looks like event[0] might be where the button is sent.  The codes are coming in at 257-260.

---

### Post by kgingeri on 2009-11-18
OK, testing with 25.3 is going ok so far and I can move the cursor full screen - scaling ok.  I DON'T HAVE the constant select!!  :)  If I tap and drag I can select but I have to double-tap to get out of constant select mode again.

Ayuthia - I've attached Xorg log info as you requested.  Sorry it took so long.  I have work to do on a clients machine tonight, so I'm a bit distracted.

EDIT: I should mention that functionally pen and touch are is fairly 'normal' - _we **are** getting there!_  Don't know about system stability yet - time will tell.

I am getting button actions - 1 (top) = middle-click, 2 = right-click, 3 = scroll-up and 4 = scroll down.

Can't use xsetwacom - no devices  :( so can't try relative mode - I'm in absolute by default.

Also seeing hesitation on initiating touch and sometimes pen BUT this machine has a SSD drive and isn't the quickest so maybe due to all the log data being written.  Give me xsetwacom devices back and I can turn off debug to find out  ;)

---

### Post by Ayuthia on 2009-11-18
I did not realize that all the buttons are now recognized.  Sorry for having you test it (unless this is new).

Which fdi file did you try?  Have you tried the fdi in post 459?  No need to test tonight.  I am about to head for bed.

As for relative mode, have you tried adding the command to the fdi?

---

### Post by kgingeri on 2009-11-18
> **Ayuthia said:**
> I did not realize that all the buttons are now recognized.  Sorry for having you test it (unless this is new).

Which fdi file did you try?  Have you tried the fdi in post 459?  No need to test tonight.  I am about to head for bed.

As for relative mode, have you tried adding the command to the fdi?

Yes - right after my last post I commented fdi debug and inserted Favux's suggested line below the "touch" line (maybe wrong?).

When I rebooted, scaling was messed up and it locked up my machine - the cursor still moved very jerky, but I couldn't click to active anything - all reboot/X key sequences did not work including REISUB - it was power off again!  Very weird but might be something you guys can use?

I then commented the relative fdi and left debug commented and now  scaling is still off still (after reboot again) but things are normal.

I may have been wrong with dbl-tap to quick select mode in touch - I think it is just very sensitive.  

I will try the other fdi now...

---

### Post by kgingeri on 2009-11-18
Ok, Favux's new_generic_test1_10 is working somewhat but differently...
[LIST]
[*]no pad buttons
[*]have xsetwacom devices
[*]relative mode keeps reseting cursor to bottom right
[*]no constant select with touch 
[*]after pen use, a tap with touch is require to activate touch (hmmm... was this the case other places too - not sure)
[*]stylus buttons and function are all well and good 
[/LIST]

I then the patch fdi is closer but needs the xsetwacom devices active.

That's it for me tonight.  :)

---

### Post by Favux on 2009-11-18
Hi kgingeri,

Thanks for testing it!

Well the best news is
> have xsetwacom devices
I was pretty sure that would work.  But still...cool.
Good news
> stylus buttons and function are all well and good
no constant select with touch
This might be good news, I'm not sure, at least not bad
> after pen use, a tap with touch is require to activate touch (hmmm... was this the case other places too - not sure)
Not sure what to make of
> relative mode keeps reseting cursor to bottom right
Bad news
> no pad buttons
Ok, so pad is(?) on 'if1' for the P & T, I guess.  Adding it to 'if1' won't hurt the other Wacom tablets.  I don't know if already having pad in 'if0' and adding it to 'if1' will mess up the P & T.  It shouldn't if the pad is really on 'if1' for the P & T.  One way to find out I guess.

Would someone please try this one (and maybe compare it to the one in post #459)

---

### Post by kgingeri on 2009-11-18
I had to finish up a clients system and had plugged my tablet in after a reboot (I usually have it always plugged in unless I've had a system lockup).  I didn't get very far.  Started Firefox, went to Logmein, logged in and went to remote control the system, did an F11 for full screen and lockup!

So I rebooted with tablet unplugged, redid the make install (just to restore the other fdi) rebooted again without tablet plugged in.  Plugged n tablet after system was up and again didn't get more than a few minutes into my session and LOCKUP in Terminal this time :(

I will try Favux's updated fdi in the post previous and try with tablet plugged in before booting.  Weird stuff - I don't like testing this way  ;)  good thing Linux is so reliable on recoverying after crashing!  
BTW no, and I mean NO key sequences are recognized.  The last to LOCKUPs left everything totally frozen.

EDIT: This is all with patch 25.3 from post #1 right now.
EDIT:  I am going to do a _complete recompile_ - just test your latest fdi Favux test2_10 and I had a lockup after starting Firefox up and bringing up this page!

---

### Post by kgingeri on 2009-11-18
Favux, that last fdi is just nasty ;)  I did a whole recompile of patch 25.3, then installed your test2_10 fdi and rebooted.  My system hung a the intro 'hydro meter' screen - I didn't even get a desktop!  Maybe we're honing in on what causes hangs?!

Anyway, I and reverting back to 25.3 and the fdi in it for now, to make sure that is still reliable.  I really don't mind testing, even if it hangs - hope I put a winky behind that statement!  :)  EDIT - I did ;)

**UPDATE:** Ok, so maybe it's not nasty Favux.  I can't reboot without hanging at all anymore with my tablet plugged in.  Not even with a clean recompile.  I may have a botched system here?!  Did anyone else get this hanging stuff - did Rebecca2525 maybe?  Favux, I think she reported the mouse getting reset to the bottom right too at one point maybe.

**UPDATE2:** _Favux's generic-test2 fdi is just fine and real good_.  BUTTONS WORK as does RELATIVE CURSOR! I think I can explain my system hangs - but not tonight - tomorrow - ok when the sun is up again  ;)

Anyway, I must get some rest and tomorrow is another day.  Night.  *(no really, ...for sure this time...)*

---

### Post by Favux on 2009-11-18
Hi kgingeri,

Once again thanks very much.  If the hang is from the .fdi and not the driver it would seem to imply the P & T is sending something related to the pad on 'if0', so maybe the buttons would be available there somehow.  The previous .fdi's that have been hanging (if it is them) have two info.callouts one in 'if0' and one in 'if1.  So again if the .fdi's were causing the hangs it might be due to having an info.callout to hal-setup-wacom in each.

But then how to get eraser on 'if0' and pad on 'if1'?

Edit:  Well not good for the team effort but it gives me some hope the test2 .fdi is ok.  It would be sweet to come up with a generic .fdi.

---

### Post by Favux on 2009-11-18
Hi Hi kgingeri,

**[SIZE="2"]Outstanding!  The new-generic_test2_10-linuxwacom.fdi works!!![/SIZE]**  Thank you kgingeri, that was above and beyond the call.  Wow!  It's possible we have a working generic wacom.fdi.

Good night.  You've earned it in my book.  :D

---

### Post by rebecca2525 on 2009-11-18
> **kgingeri said:**
> Did anyone else get this hanging stuff - did Rebecca2525 maybe?
The last patches I tested were 31 and 25.2, and while I had X hanging twice with the latter, I still could change to a Linux concole. One time X got unstuck when I pressed a tablet button. The other time I don't recall exactly, maybe I unplugged the tablet or pressed a tablet button or so; I didn't need to restart X or even reboot.

> Favux, I think she reported the mouse getting reset to the bottom right too at one point maybe.With 25.2, cursor got placed at the bottom right when I tried up/down two-finger-scaling while relative mode was enabled. Cursor got placed at the left border of the screen when I activated relative mode, but following prefiks2's advice got relative mode working:
> You can fix that with xsetwacom:

xsetwacom set touch bottomx 740
xsetwacom set touch bottomy 500

But driver should do that for you... (those numbers are correct for medium one tablet, i don't know correct values for smaller ones but you can find them in log you need to search for wacom_wac->features->{x,y}_max)
Anyhow, I can't do any further testing until late tonight.

---

### Post by dnprossi on 2009-11-18
[B]Test on 25.3 with requested fdi on post #1
[/B]
Stylus no problems encountered...

Touch works but with some issues when pressing buttons especially button 1 that disables all button clicks from all devices standard mouse included, pressing any other button returns functionality though...

when left idle for some time one has to tap once for touch to be enabled.

both absolute and relative modes work with a little difficulty in selecting and double tapping on icons in absolute mode as when releasing and tapping again shifts the cursor out of icon range...

No crashes

I will test new-generic_test2_10-linuxwacom.fdi now...

---

### Post by marek_online on 2009-11-18
You guys are awesome.

Basically, I now have a working tablet. If someone can remind me how to set the touchpad to relative mode I'll almost perfectly set!

After reboot, with both Favux's latest fdi and with the fdi included in Post #1I get:
Touch:
Absolute positioning
- No constant selection
Tapping = click, dragging possible
- No multi-touch yet (but are we working on that yet?)
All buttons on the pad working (left-click, right-click and two versions of middle-click - scroll up and down, basically).

Stylus:
Pen and eraser with pressure and working buttons.

Logs attached. Had to split the messages and Xorg for the Post #1 fdi session for size reasons.

---

### Post by rebecca2525 on 2009-11-18
```
xsetwacom set touch Mode relative
```> Cursor got placed at the left border of the screen when I activated relative mode, but following prefiks2's advice got relative mode working:
     Quote:
                                                 You can fix that with xsetwacom:

xsetwacom set touch bottomx 740
xsetwacom set touch bottomy 500

But driver should do that for you... (those numbers are correct for medium one tablet, i don't know correct values for smaller ones but you can find them in log you need to search for wacom_wac->features->{x,y}_max) We should collect important xsetwacom commands and stuff in the first post.

---

### Post by dnprossi on 2009-11-18
> **dnprossi said:**
> [B]Test on 25.3 with requested fdi on post #1
[/B]
Stylus no problems encountered...

Touch works but with some issues when pressing buttons especially button 1 that disables all button clicks from all devices standard mouse included, pressing any other button returns functionality though...

when left idle for some time one has to tap once for touch to be enabled.

both absolute and relative modes work with a little difficulty in selecting and double tapping on icons in absolute mode as when releasing and tapping again shifts the cursor out of icon range...

No crashes...

I will test new-generic_test2_10-linuxwacom.fdi now...

Here it is...
Same as up no major issue except buttons...
Difference from above **No xorg.0.log data received**..
No crashes...

Button1 left-click
Button2 right-click
Button3 scroll-up
Button4 scroll-down

Cheers....

---

### Post by marek_online on 2009-11-18
:
     ```
xsetwacom set touch Mode relative 
```
Excellent. Thanks Rebecca2525. At work now but will check it out when I get home.

---

### Post by dnprossi on 2009-11-18
After a two hour pause not using tablet but there since last test and some sporadic button clicks by mistake i used touch again and ubuntu froze...

attached message.log block when it happened... 

Still using favux latest fdi

**[COLOR="Red"]EDIT!![/COLOR]**
**Updated and detailed** test on post [#321]("http://ubuntuforums.org/showpost.php?p=8326473&postcount=321")

Went back to requested Post #1 fdi.

---

### Post by ob1kenobi on 2009-11-18
Hi all, just sending this out before I head off to work :)

This is 25.4, but I should probably start bumping the main version to get back on track with the next set.

It should fix any scheduling while atomic problems (if you've seen them).  The first was a change I made to fall in line with general kernel do's and don'ts.  wacom_sys_irq was passing on a pointer to a stack allocated structure, rather than that I changed it to a kzalloc, but forgot to make it GFP_ATOMIC, which will cause problems in an interrupt handler.  I thinks this was being reported as "BUG: scheduling while atomic: swapper".  The next is the spin locks in the wacom_bpt_irq function.  I had one big lock and every once in a while I'd get a "BUG:scheduling while atomic: X.org" which I think was related to locking and sending input commands to X.  While there are now more spin locks, they are activated only when reading or writing to the shared state variables between the pen and touch devices.  The other thing is that the device will periodically send pen up events "basically 02 00 00 ..." to clear any states I guess.  This was causing some interesting things with pen to touch transfers.  Also I rearranged the variable names ont he pen status bits after spending some time looking at the transfer.  I think they are mostly correct now and the lockups seen when switching from pen to touch are now gone.  There are logic problems that still have to be sorted out for multi-touch and if the cursor stops responding you should just tap/lift until it moves again.  Finally the device names are now reported independently and I removed the & from the names to make it easier to use the dynamic hal names the driver provides on the command line with xsetwacom.  Touch is reported as "<name from features struct> Touch" and Pen is reported as "<name from features struct> Pen".

Edit: you'll also notice that WACOM_PKGLEN_BBPT_PEN is back to 9... I know I introduced the 18 length thing(sorry). I realized last night that the 18 length being returned by the pen was actually two successive pen packets and back when there was only one urb buffer used it had to be 20 to get the touch packets. Now that the data transfers are separate the pen PKGLEN of 9 should work for everyone.

I used for ~2 hours without any crashes last night so I'm pretty sure that fixes any X.org lockup scenarios.

Good luck and hopefully this is one step closer to the finish line...:D

---

### Post by kgingeri on 2009-11-18
Ok the sun is up!  :D

So crashing I think is definitely button related.  Last night I didn't realize that my button1 was being held down - due to my setup here.  Also that button didn't seems to have much 'detent' or click and I think it make have got stuck on at times! But it sound like Ob1 is onto it!!!

[SIZE="5"]WE ARE ALOST THERE!!![/SIZE] - heading to work also.

---

### Post by Ayuthia on 2009-11-18
I am going to move the updates into the first post in a couple of hours.  I run into a busy morning over here.  I did not update one of my laptops that is running Gentoo and now I am paying the price for it, I was updating a guide to install 0.8.4-4 for N-Trig devices, and now I have to take my son to the library.  I sure hope my wife does not go into labor today.  

So if you don't hear from me within the next 24-hours, then the last sentence in the previous paragraph occurred.

---

### Post by dnprossi on 2009-11-18
> **Ayuthia said:**
> I am going to move the updates into the first post in a couple of hours.  I run into a busy morning over here.  I did not update one of my laptops that is running Gentoo and now I am paying the price for it, I was updating a guide to install 0.8.4-4 for N-Trig devices, and now I have to take my son to the library.  I sure hope my wife does not go into labor today.  

So if you don't hear from me within the next 24-hours, then the last sentence in the previous paragraph occurred.

What a great day for you.. Best wishes from Italy!!!!!!

---

### Post by marek_online on 2009-11-18
> **Ayuthia said:**
> I am going to move the updates into the first post in a couple of hours.  I run into a busy morning over here.  I did not update one of my laptops that is running Gentoo and now I am paying the price for it, I was updating a guide to install 0.8.4-4 for N-Trig devices, and now I have to take my son to the library.  I sure hope my wife does not go into labor today.  

So if you don't hear from me within the next 24-hours, then the last sentence in the previous paragraph occurred.

And best wishes from the Irish contingent too! 

(I was tempted to make some comment about how people should keep their priorities straight, but I'll keep that to myself ;)

On a less fun note, 25.4 breaks things for me. I get nothing in /varl/og/messages past the module loading:
```

Nov 18 16:30:58 Childers kernel: [  871.089614] usbcore: deregistering interface driver wacom
Nov 18 16:31:01 Childers kernel: [  874.340698] usbcore: registered new interface driver wacom
Nov 18 16:31:01 Childers kernel: [  874.340702] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
```I've attached Xorg.0.log in case there's anything useful in there.

EDIT:
Have gone back to 25.3, and everything's working great. My one minor whinge is that the statement for flipping it to left-handed mode isn't working:

```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```

I've tried it in a few different sections of the fdi, and tried it through xsetwacom, to no avail. Would appreciate any pointers!

---

### Post by rebecca2525 on 2009-11-18
On first quick test, 25.4 (and the fdi that comes with it) seems the same as yesterday: Stylus and eraser ok, topmost two buttons are right and middle click. With absolute touch I can only access the upper left quarter of my screen, had touch not reacting a few times. Will report back with specifics in a few hours.

---

### Post by ob1kenobi on 2009-11-18
> **marek_online said:**
> 
On a less fun note, 25.4 breaks things for me. I get nothing in /varl/log/messages past the module loading:
```

Nov 18 16:30:58 Childers kernel: [  871.089614] usbcore: deregistering interface driver wacom
Nov 18 16:31:01 Childers kernel: [  874.340698] usbcore: registered new interface driver wacom
Nov 18 16:31:01 Childers kernel: [  874.340702] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver
```I've attached Xorg.0.log in case there's anything useful in there.

Please start looking in /var/log/syslog.  Also please refresh my memory on which tablet you have. Thanks.
> 
EDIT:
Have gone back to 25.3, and everything's working great. My one minor whinge is that the statement for flipping it to left-handed mode isn't working:

```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```

Edit: clarified that the kernel module is reporting different interface names now.
Note that on 25.4 the Hal info.product reported by the kernel module has changed to differentiate interfaces.

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> On first quick test, 25.4 (and the fdi that comes with it) seems the same as yesterday: Stylus and eraser ok, topmost two buttons are right and middle click. With absolute touch I can only access the upper left quarter of my screen, had touch not reacting a few times. Will report back with specifics in a few hours.

Thanks for the report. I'm still trying to track down the sequencing issue with the touch and pad tools in the Hal file. X.org assigns the touch x_max and y_max to the pad if you don't restart x, a logout or reboot usually gets the correct scaling back for me.

---

### Post by Ayuthia on 2009-11-18
I have created patch 34.  The only changes to ob1kenobi's source is that I added the debug code in the kernel modules so that it will report additional data.  I have also added the patch version so that it will report the version number when reporting the touch/stylus data.

I will be updating the first post now to add the xsetwacom commands.

By the way, if I had my priorities straight, I would be living outside of my house and I don't think my wireless range is strong enough to get a good connection...  Also it is raining outside right now and laptops don't like rain.  :lol:

---

### Post by Ayuthia on 2009-11-18
> **marek_online said:**
> 
EDIT:
Have gone back to 25.3, and everything's working great. My one minor whinge is that the statement for flipping it to left-handed mode isn't working:

```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```

I've tried it in a few different sections of the fdi, and tried it through xsetwacom, to no avail. Would appreciate any pointers!

It looks like that function is currently not working in 0.8.5-4 based on Favux's [post]("http://ubuntuforums.org/showpost.php?p=8332378&postcount=386").

---

### Post by marek_online on 2009-11-18
> **Ayuthia said:**
> It looks like that function is currently not working in 0.8.5-4 based on Favux's [post]("http://ubuntuforums.org/showpost.php?p=8332378&postcount=386").

Ah. Indeed, should have found that one myself. Thanks.

Will have a look at the new patch.

---

### Post by ElaineM on 2009-11-18
Hi,  I have a wacom bamboo pen & touch, too. But I don't have enough knowlege to do all the patchs, could you tell me a not to heavy way to get my bamboo work? It would be enough if just using the pen would be working, I can wait for the rest.  I have Ubuntu 9.10, wacom-tools and xserver-xorg-input-wacom 0.8.4.1 are installed. The tablet is detected by usb but there is no entry with wacom.

---

### Post by marek_online on 2009-11-18
Hi ElaineM,

I probably don't know much more than you do, but kgingeri's HOWTO here:

[http://ubuntuforums.org/showpost.php?p=8262965&postcount=541](http://ubuntuforums.org/showpost.php?p=8262965&postcount=541)

is probably your best bet for the moment. It's a step by step breakdown of exactly what you need to do get some your pen and eraser working. 

This is the thread for the development of the driver that will get everything working properly, but it means that some versions of the patches won't work.

Ayuthia, ob1kenobi, prefiks, Favux and everyone else seem to be very close to getting things well and truly working though, so you probably won't have to wait all that long before we have a fully working version of things. In the meantime, kgingeri's HOWTO at the link above should tide you over.

---

### Post by marek_online on 2009-11-18
Okay, tried 25.4 again, this time with the included fdi instead of the Favux generic one that I had been using. Same problem (nothing from either stylus or touch).

I've syslog attached, but there's no mention of wacom in it. I'm not sure what else I'd be looking for.

---

### Post by ob1kenobi on 2009-11-18
> **marek_online said:**
> Okay, tried 25.4 again, this time with the included fdi instead of the Favux generic one that I had been using. Same problem (nothing from either stylus or touch).

I've syslog attached, but there's no mention of wacom in it. I'm not sure what else I'd be looking for.
Which OS/kernel version are you running? EDIT: Nevermind I see it in your syslog...

---

### Post by Ayuthia on 2009-11-18
> **marek_online said:**
> Okay, tried 25.4 again, this time with the included fdi instead of the Favux generic one that I had been using. Same problem (nothing from either stylus or touch).

I've syslog attached, but there's no mention of wacom in it. I'm not sure what else I'd be looking for.

Can you try it with the patches from the first post?  It includes the debugger information that might help.

---

### Post by marek_online on 2009-11-18
Yeah, just tried it with Patch 34. Logs attached. Everything works properly here, so I'm not sure what was wrong with the way I was using 25.4. 

Hi ob1, I'm using karmic, with 2.6.31-15-generic. My device is the 0xd1 (CTH-460, same as yours, I think).

The fdi file I'm using is Favux's latest I think. I'll attach that too just in case.

Gotta head off now - hopefully to watch the Irish soccer team pull of a miracle by hammering the French in Paris.

---

### Post by rebecca2525 on 2009-11-18
> **ob1kenobi said:**
> Thanks for the report. I'm still trying to track down the sequencing issue with the touch and pad tools in the Hal file. X.org assigns the touch x_max and y_max to the pad if you don't restart x, a logout or reboot usually gets the correct scaling back for me.
I've made it a habit to always reboot after installing a new patch. But I've found out: If the tablet is plugged in when I restart X, I get the correct scale. If I (re)plug it in later (no matter if it was or was not plugged in when X started) the scale is wrong.

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> I've made it a habit to always reboot after installing a new patch. But I've found out: If the tablet is plugged in when I restart X, I get the correct scale. If I (re)plug it in later (no matter if it was or was not plugged in when X started) the scale is wrong.
 
Yep, any time the Xorg input system inits or reinits the device after Xorg is already running the scale gets set on the pad subdevice rather than the touch device.  I'm guessing it is somewhere in the wacom xdrv code...

---

### Post by Ayuthia on 2009-11-18
> **rebecca2525 said:**
> I've made it a habit to always reboot after installing a new patch. But I've found out: If the tablet is plugged in when I restart X, I get the correct scale. If I (re)plug it in later (no matter if it was or was not plugged in when X started) the scale is wrong.

This isn't the most perfect solution, but we should be able to add it to the fdi file so that it will be recognized.  The xdrv would then be able to configure it every time.  I think you are able to configure the TopX and BottomX, the MaxX, and ResolutionX.  It does not have the MaxTouchX and MaxTouchY configurable though.

I would think that it would look something like:
```

<merge key="input.x11_options.TopX" type="string">0</merge>
<merge key="input.x11_options.TopY" type="string">0</merge>
<merge key="input.x11_options.BottomX" type="string">740</merge>
<merge key="input.x11_options.BottomY" type="string">500</merge>

```
I would guess that it would go under the touch definition, but I don't have too much experience with this.

---

### Post by ElaineM on 2009-11-18
I am a desperated because patching the wacom-driver as discribed here [http://ubuntuforums.org/showpost.php?p=8129913&postcount=144](http://ubuntuforums.org/showpost.php?p=8129913&postcount=144) doesn't work...

I always get this error in "sudo make":
```

cp /lib/modules/2.6.31-14-generic/build/drivers/hid/hid-ids.h .
cp: Aufruf von stat für „/lib/modules/2.6.31-14-generic/build/drivers/hid/hid-ids.h“ nicht möglich: No such file or directory
make[2]: *** [all] Fehler 1
make[2]: Verlasse Verzeichnis '/home/ich/Desktop/neuDownloads/wacomtreiber/linuxwacom-0.8.4-3/src/2.6.31'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/ich/Desktop/neuDownloads/wacomtreiber/linuxwacom-0.8.4-3/src'
make: *** [all-recursive] Fehler 1

```
Has anyone a idea what I might have done wrong?

---

### Post by rebecca2525 on 2009-11-18
25.4 with its fdi.

I don't have the left-click effect anymore, which is a great relief! Setting touch to relative mode works out of the box (no need to set bottomx and bottomy with xsetwacom). Eraser and stylus work fine. Stylus overwrites touch as it's supposed to be.

I had one occurence of X hanging. When it happend, I hadn't used the tablet for a while, but used the laptop touchpad to navigate around and open up Gimp. My cursor turned into a clock (my Windowmanager normally doesn't do that...) and the grahics card/monitor made an awful high-pitched sound (like an old TV set)... until I pressed the upper tablet button. After that everything worked fine again. I'm attaching logs from the seconds before/around the hang.

Edit:

 ```
$ xsetwacom list
Wacom_Bamboo_6x8_Pen     stylus
Wacom_Bamboo_6x8_Pen_eraser     eraser
Wacom_Bamboo_6x8_Touch     touch
Wacom_Bamboo_6x8_Touch_pad     touch
```
The pad is touch and not pad. Dunno if that's a bad thing?

---

### Post by kgingeri on 2009-11-18
> **Ayuthia said:**
> I am going to move the updates into the first post in a couple of hours.  I run into a busy morning over here.  I did not update one of my laptops that is running Gentoo and now I am paying the price for it, I was updating a guide to install 0.8.4-4 for N-Trig devices, and now I have to take my son to the library.  I sure hope my wife does not go into labor today.  

So if you don't hear from me within the next 24-hours, then the last sentence in the previous paragraph occurred.

WOW!!!  Much more exciting then tablet stuff Dad!!  ;)

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> 25.4 with its fdi.

I don't have the left-click effect anymore, which is a great relief! Setting touch to relative mode works out of the box (no need to set bottomx and bottomy with xsetwacom). Eraser and stylus work fine. Stylus overwrites touch as it's supposed to be.

I had one occurence of X hanging. When it happend, I hadn't used the tablet for a while, but used the laptop touchpad to navigate around and open up Gimp. My cursor turned into a clock (my Windowmanager normally doesn't do that...) and the grahics card/monitor made an awful high-pitched sound (like an old TV set)... until I pressed the upper tablet button. After that everything worked fine again. I'm attaching logs from the seconds before/around the hang.


There are still issues with the multi-touch and getting into a state where touch stops responding until you click a button on the tablet or touch inside the white box.
There's nothing in your logs that look like anything bad happened because of the wacom.

I think the monitor issue was probably a gremlin than being related to the wacom.;)

> 
Edit:

 ```
$ xsetwacom list
Wacom_Bamboo_6x8_Pen     stylus
Wacom_Bamboo_6x8_Pen_eraser     eraser
Wacom_Bamboo_6x8_Touch     touch
Wacom_Bamboo_6x8_Touch_pad     touch
```The pad is touch and not pad. Dunno if that's a bad thing?

That's a symptom of the scaling problem.

---

### Post by kgingeri on 2009-11-18
> **ElaineM said:**
> I am a desperated because patching the wacom-driver as discribed here [http://ubuntuforums.org/showpost.php?p=8129913&postcount=144](http://ubuntuforums.org/showpost.php?p=8129913&postcount=144) doesn't work...

I always get this error in "sudo make":
```

cp /lib/modules/2.6.31-14-generic/build/drivers/hid/hid-ids.h .
cp: Aufruf von stat für &#8222;/lib/modules/2.6.31-14-generic/build/drivers/hid/hid-ids.h&#8220; nicht möglich: No such file or directory
make[2]: *** [all] Fehler 1
make[2]: Verlasse Verzeichnis '/home/ich/Desktop/neuDownloads/wacomtreiber/linuxwacom-0.8.4-3/src/2.6.31'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/ich/Desktop/neuDownloads/wacomtreiber/linuxwacom-0.8.4-3/src'
make: *** [all-recursive] Fehler 1

```
Has anyone a idea what I might have done wrong?

Hi Elaine - welcome to the forum BTW!
I can't read German, but I think your problem is you didn't get the hid headers. did you do the lines...
```
# wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
# cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
# apt-get install patch
```
... did it install ok?

EDIT: This was from my howto at post [#541]("http://ubuntuforums.org/showpost.php?p=8262965&postcount=541") - you should do that howto COMPLETELY FIRST, then you can go to post #1 here if you want to try patching, but it may not work as you expect if you patch.  :)

---

### Post by ob1kenobi on 2009-11-18
> **ElaineM said:**
> I am a desperated because patching the wacom-driver as discribed here [http://ubuntuforums.org/showpost.php?p=8129913&postcount=144](http://ubuntuforums.org/showpost.php?p=8129913&postcount=144) doesn't work...

I always get this error in "sudo make":
```

cp /lib/modules/2.6.31-14-generic/build/drivers/hid/hid-ids.h .
cp: Aufruf von stat für „/lib/modules/2.6.31-14-generic/build/drivers/hid/hid-ids.h“ nicht möglich: No such file or directory
make[2]: *** [all] Fehler 1
make[2]: Verlasse Verzeichnis '/home/ich/Desktop/neuDownloads/wacomtreiber/linuxwacom-0.8.4-3/src/2.6.31'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/ich/Desktop/neuDownloads/wacomtreiber/linuxwacom-0.8.4-3/src'
make: *** [all-recursive] Fehler 1

```Has anyone a idea what I might have done wrong?

Hi ElaineM,

You need to make sure you followed post #1 of this thread.  The hid-ids.h needs to be retrieved from ubuntu's repository using the instructions you'll see in post #1.  Then it should build.

---

### Post by ob1kenobi on 2009-11-18
> **Ayuthia said:**
> This isn't the most perfect solution, but we should be able to add it to the fdi file so that it will be recognized.  The xdrv would then be able to configure it every time.  I think you are able to configure the TopX and BottomX, the MaxX, and ResolutionX.  It does not have the MaxTouchX and MaxTouchY configurable though.

I would think that it would look something like:
```

<merge key="input.x11_options.TopX" type="string">0</merge>
<merge key="input.x11_options.TopY" type="string">0</merge>
<merge key="input.x11_options.BottomX" type="string">740</merge>
<merge key="input.x11_options.BottomY" type="string">500</merge>

```I would guess that it would go under the touch definition, but I don't have too much experience with this.

Unfortunately that won't work for all pads since the 4x5's need 480x320 instead of 740x500.  I'm sure we can find the root of the problem and fix it in the kernel module or xorg driver :D

---

### Post by rebecca2525 on 2009-11-18
> **ob1kenobi said:**
> I think the monitor issue was probably a gremlin than being related to the wacom.;)
I'm afraid it is, because it was very similar to what I was experiencing yesterday with 25.2. (And I'm using my machine a lot without tablet, and it runs stable)

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> I'm afraid it is, because it was very similar to what I was experiencing yesterday with 25.2. (And I'm using my machine a lot without tablet, and it runs stable)

What type of graphics card and monitor are you running?

---

### Post by Ayuthia on 2009-11-18
> **ob1kenobi said:**
> Hi ElaineM,

You need to make sure you followed post #1 of this thread.  The hid-ids.h needs to be retrieved from ubuntu's repository using the instructions you'll see in post #1.  Then it should build.

ElaineM, sorry to send you all over the place.  You should be using the information in [post 541]("http://ubuntuforums.org/showpost.php?p=8262965&postcount=541") instead of 144.  kgingeri has been kind enough to rewrite the instructions for getting the pen portion working with our earlier set of patches.  I was planning on creating a new thread for the stable version, but I have not had a chance.

---

### Post by rebecca2525 on 2009-11-18
I just had touch not responding again (X was fine this time, though). I was just using touch, not switching between stylus or mouse or anything and the cursor stopped moving. When I tapped on the tablet, I still got right-click, but the cursor was still stuck. It got unstuck after I pressed the topmost button. Logs attached.

I'm using the Intel integrated graphics card (Lenovo Thinkpad).

---

### Post by Ayuthia on 2009-11-18
> **ob1kenobi said:**
> Unfortunately that won't work for all pads since the 4x5's need 480x320 instead of 740x500.  I'm sure we can find the root of the problem and fix it in the kernel module or xorg driver :D

I don't disagree with you.  It might just be an easier way for now until we get the fix out.  It wouldn't hurt to test it out so that we know that it does work.

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> I just had touch not responding again (X was fine this time, though). I was just using touch, not switching between stylus or mouse or anything and the cursor stopped moving. When I tapped on the tablet, I still got right-click, but the cursor was still stuck. It got unstuck after I pressed the topmost button. Logs attached.

I'm using the Intel integrated graphics card (Lenovo Thinkpad).

Just to clarify, did the squeal happen again, and did it happen on 25.2?

FYI: What you are describing above is some of the code I plan to look at tonight related to multi-touch logic that isn't quite right.

---

### Post by rebecca2525 on 2009-11-18
> **ob1kenobi said:**
> Just to clarify, did the squeal happen again, and did it happen on 25.2?

I have two different effects, both of which have occured with 25.2 and 25.4:

1.) touch stops moving the cursor
2.) X hangs completely with weird noise and cursor turning into a clock

Both situations can be escaped with clicking the topmost tablet button (I'm not sure if other buttons work as well, but tapping on the tablet doesn't work) The first effect is what happened in my last post, the second effect is what happened in my earlier post. The second effect  happens less often than the first.

---

### Post by Favux on 2009-11-18
Hi everyone,

Is the coordinates thing happening with a suspend and resume too?  That's been a long standing issue since the Jaunty Xorg.  We've been using the Wacom settings daemon monitor_wacom by cyberfish for that.  Obviously hotplugging hasn't been something we've had to contended with.

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> I have two different effects, both of which have occured with 25.2 and 25.4:

1.) touch stops moving the cursor
2.) X hangs completely with weird noise and cursor turning into a clock

Both situations can be escaped with clicking the topmost tablet button (I'm not sure if other buttons work as well, but tapping on the tablet doesn't work) The first effect is what happened in my last post, the second effect is what happened in my earlier post. The second effect  happens less often than the first.

A Lenovo desktop or laptop and where are the speakers?

---

### Post by rebecca2525 on 2009-11-18
For me, the tablet isn't working after resuming, I need to unplug/replug it afterwards, which leads to a wrong scale. (I'm on Debian Testing with Xorg 7.4)

---

### Post by rebecca2525 on 2009-11-18
> **ob1kenobi said:**
> A Lenovo desktop or laptop and where are the speakers?
It's a laptop, Lenovo Thinkpad T400, speakers are left of the Esc/F1 keys and right of the Backspace/PageUp/PageDown keys.

---

### Post by Favux on 2009-11-18
Hi rebecca2525,

I didn't realize the tablet wasn't working after a suspend/resume.  That's a different issue of course.

In case once you get that fixed you're then running into the settings issue I'll link you to the daemon.  It's in Section 4 of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").

I didn't think linuxwacom worked with Xorg 7.4 yet, at least with the pad.

Edit:  Sorry wrong version of Xorg:
> Keystroke is broken on Xorg 7.5 (X server 1.7). We are working on it.

Ping

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> It's a laptop, Lenovo Thinkpad T400, speakers are left of the Esc/F1 keys and right of the Backspace/PageUp/PageDown keys.

Can you definitely tell if the noise from the monitor or the speakers?

---

### Post by rebecca2525 on 2009-11-18
> **ob1kenobi said:**
> Can you definitely tell if the noise from the monitor or the speakers?
I will try to find out once it happens again, it's not that often. Off to bed now. :)

---

### Post by ob1kenobi on 2009-11-18
> **rebecca2525 said:**
> I will try to find out once it happens again, it's not that often. Off to bed now. :)
Ok, thanks.  Just trying to nail down where it might be.

---

### Post by ElaineM on 2009-11-18
> **kgingeri said:**
> 
```
# wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
# cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
# apt-get install patch
```... did it install ok?

EDIT: This was from my howto at post [#541]("http://ubuntuforums.org/showpost.php?p=8262965&postcount=541") - you should do that howto COMPLETELY FIRST, then you can go to post #1 here if you want to try patching, but it may not work as you expect if you patch.  :)

Yeah, that could be the problem..... 
before the code is written: "If running Ubuntu Karmic Remix or other minimal distro, you may have to do:" so I thought I have a full ubuntu installation, I won't need it.... -.-
I will try it.

Thanks to all of you for the kind help!!

I have an other very small problem: when typing "make clean" I get the error message that there is no rule to make "clean". I think it will not make any errors, but it confuses me. ;-)

---

### Post by dnprossi on 2009-11-18
> **ElaineM said:**
> 
I have an other very small problem: when typing "make clean" I get the error message that there is no rule to make "clean". I think it will not make any errors, but it confuses me. ;-)

Hi ElaineM,
As you are compiling for first time there is nothing to clean that's why you get that error skip cleaning lines.. Use them next time you have to compile...

cheers..

---

### Post by Ayuthia on 2009-11-18
> **ElaineM said:**
> Yeah, that could be the problem..... 
before the code is written: "If running Ubuntu Karmic Remix or other minimal distro, you may have to do:" so I thought I have a full ubuntu installation, I won't need it.... -.-
I will try it.

Thanks to all of you for the kind help!!

I have an other very small problem: when typing "make clean" I get the error message that there is no rule to make "clean". I think it will not make any errors, but it confuses me. ;-)

That usually means that the configure portion has not run so there is no Makefile that exists yet.  Once you do the next step, all should run fine.

EDIT:
Oops!  It looks like dnprossi beat me.

---

### Post by ElaineM on 2009-11-18
I CAN MOVE THE COUSOR WITH THE PEN!!!!!!!!!!!!!!!! IT IS WORKING!!!!!

I think I won't sleep this night ;-)

Ok, there are still some problems and I haven't rebooted yet, but it is moving!!!!!


I rebooted yet.
I am left-handed and usaly use my mouse with the left hand. As long as I select left-handed mouse a tip on the tablet ist treaten as a right click (if you are right-handed..... may-be calling it the second mouse button is clearer ;-) ).

I tested drawing in gimp - it is great!

---

### Post by dnprossi on 2009-11-18
Before going to sleep I tested patch 34 thoroughly its working well.
I have found one issue with two finger touch very similar to ex button1 effect not releasing...

Detailed test on post [#321]("http://ubuntuforums.org/showpost.php?p=8326473&postcount=321")

Good night to all.. I'll test anything i find in the morning... leaving pc on with tablet to see if it wakes on touch after suspend...

cheers...

[COLOR="Red"]EDIT[/COLOR]!!! 
**unplug/replug** scale change issue, reported by rebecca2525...
**suspend/resume** no scale change issue...

> **Ayuthia said:**
> 
It might just be an easier way for now until we get the fix out. It wouldn't hurt to test it out so that we know that it does work.


In fdi just after line 20 containing:
 
```
<merge key="input.x11_options.Type" type="string">touch</merge>
```

added  (480x320 for 0xd2)
```

<merge key="input.x11_options.TopX" type="string">0</merge>
<merge key="input.x11_options.TopY" type="string">0</merge>
<merge key="input.x11_options.BottomX" type="string">[COLOR="Red"]480[/COLOR]</merge>
<merge key="input.x11_options.BottomY" type="string">[COLOR="Red"]320[/COLOR]</merge>

```

unplug/replug scale correct... Ayuthia it works...
**Relative mode only on replug tapping on desktop the cursor is shifted a distance to the right sometimes to edge of screen... Needs reboot to resume**

i also added 
```

<merge key="input.x11_options.mode" type="string">relative</merge>

```
so i get relative mode as default...

[COLOR="Red"]toggle touch on/off[/COLOR]
```

xsetwacom set touch Touch off
xsetwacom set touch Touch on

```

---

### Post by dnprossi on 2009-11-19
Fdi related questions: Favux_new-generic_test2_10-linuxwacom.fdi.txt

What is this for? Can one set things for cursor in xsetwacom?
```

<append key="wacom.types" type="strlist">cursor</append>

```

Why is the following both in if0 and if1? (must have missed something:))
```

<append key="wacom.types" type="strlist">pad</append>

```

---

### Post by Favux on 2009-11-19
Hi dnprossi,

The cursor is for the Wacom mouse (puck) that some tablets have.  It might as well be mouse, i.e. cursor = Wacom mouse.

All the other Wacom usb tablets set up on 'if0'.  So that's why pad is on both 'if0' and 'if1'.  The Wacom Bamboo P & T's are different, as we have found out, and set up pad (tablet buttons) on 'if1'.

The .fdi should work for all previous Wacom usb tablets and as a bonus finally add support for the usb tablet pc's with touch like the HP TX2000 and TX2500.

Actually there is a brand new Wacom multi-touch touchscreen laptop, the HP dv3-2250ep (the E2), only available in Europe.  Would you do me the favor of testing the .fdi I have [here]("http://ubuntuforums.org/showpost.php?p=8345829&postcount=16")?  It's the only Wacom touchscreen that I know of that sets up on 'if0'.  I try to add it in on this test3 .fdi without breaking it for the P & T or other tablets.  I'm interested in knowing if it works for you.  In other words you shouldn't be able to  tell the difference between it and test2.

---

### Post by dnprossi on 2009-11-19
> **Favux said:**
> 
Actually there is a brand new Wacom multi-touch touchscreen laptop, the HP dv3-2250ep (the E2), only available in Europe.  Would you do me the favor of testing the .fdi I have [here]("http://ubuntuforums.org/showpost.php?p=8345829&postcount=16")?  It's the only Wacom touchscreen that I know of that sets up on 'if0'.  I try to add it in on this test3 .fdi without breaking it for the P & T or other tablets.  I'm interested in knowing if it works for you.  In other words you shouldn't be able to  tell the difference between it and test2.

Hello Favux.
it's working as before no trouble. I did have some issues with test2 this morning but these seem to have disappeared in last reboots and after a complete reinstall this before trying test3. 

nothing different from my test on post [#321]("http://ubuntuforums.org/showpost.php?p=8326473&postcount=321") and above post for now

I will keep test3 installed to see long term issues (if any).

Oups forgot.. pad appears twice in wacomcpl though..

---

### Post by rebecca2525 on 2009-11-19
OK, still on 25.4. So far I had one X hang, but it was gone so fast I hadn't time to investigate the source of the noise. Touch cursor movement has been very reliable thus far, no hangs (it was worse last night with the same patch. I did do a Debian update since then, but only a few unrelated packages were updated, and I can't think of anything else that might be different than last night). 

In general, cursor movement with touch is a little bit jittery. The left-button-click thing is still a bit unreliable. Normally, when you put your finger down on the pad to move the cursor, no left-click is issued, but sometimes it is. (I first thought it might be related to the pressure I use, but I don't think that's the case.) Vice versa, just tapping on the pad with no movement generally issues a left-click, but sometimes it doesn't. EDIT: Just issuing a left-click is not a problem, but "keeping" the click when moving the cursor (to drag things) is.

In Gimp, one time when I was drawing and then lifting the stylus and hovering over to the side, the brush didn't stop drawing. Not sure whether this is a driver bug or a Gimp bug though.

And one time, my window manager (Fvwm) and I had different opinions of which window should have focus. Whether that's a bug in Fvwm, X, a problem with the driver or just me doing things with the tablet I didn't mean to because of other tablet bugs, I'm not sure.

---

### Post by Favux on 2009-11-19
Hi dnprossi,

Thank you very much for testing test3!
> it's working as before no trouble.  nothing different from my test on post #321 and above post for now  I will keep test3 installed to see long term issues (if any).
Great!  Now if it only adds touch for the E2.

> Oups forgot.. pad appears twice in wacomcpl though.. 
Do you mean only with test3 or with test2 also?  I'm going to guess it is with both.  It would be really nice if that wasn't happening.  So then it must show up twice in "xinput --list" and "xsetwacom list".  What do their outputs look like?

Still the other Wacom tablets should only see one pad.  In wacomcpl do both pads "work" when you click on them or only one?  Is it only the second pad in the list that works?  Does clicking on both in wacomcpl cause any problems that you can see?


Hi rebecca2525,

It sounds like things are pretty good.  


We may be having a baby time out.

---

### Post by dnprossi on 2009-11-19
> **Favux said:**
> 
Do you mean only with test3 or with test2 also?  I'm going to guess it is with both.  It would be really nice if that wasn't happening.  So then it must show up twice in "xinput --list" and "xsetwacom list".  What do their outputs look like?

Still the other Wacom tablets should only see one pad.  In wacomcpl do both pads "work" when you click on them or only one?  Is it only the second pad in the list that works?  Does clicking on both in wacomcpl cause any problems that you can see?


Hi Favux,

pad appears twice in both test2 and test3
xinput --list - pad id 4 & pad id 14
xsetwacom list = yes it appears twice
in wacomcpl the two pads are set to serial No: F0
changing properties in one will change data in the other and opposite everything seems to work anyhow...

Any news from ayuthia and baby??

---

### Post by Favux on 2009-11-19
Hi dnprossi.

> changing properties in one will change data in the other and opposite everything seems to work anyhow...
Well that is good news anyway.  The P & T's are the only ones that seem to need pad on 'if1', it would be nice if it worked on 'if0' for them.  For fun could you try taking out the info.callout and pad lines from the .fdi on 'if1' and see if pad still shows up?  It probably won't be active.

The P & T's seem to be the only tablets that require two info.callouts to hal-setup-wacom and that makes me nervous.  There really isn't any documentation on hal-setup-wacom that I have seen.  But the precedent is using it only once per tablet, so...

> Any news from ayuthia and baby?? 
Not yet.

---

### Post by dnprossi on 2009-11-19
> **Favux said:**
> Well that is good news anyway.  The P & T's are the only ones that seem to need pad on 'if1', it would be nice if it worked on 'if0' for them.  For fun could you try taking out the info.callout and pad lines from the .fdi on 'if1' and see if pad still shows up?  It probably won't be active.

The P & T's seem to be the only tablets that require two info.callouts to hal-setup-wacom and that makes me nervous.  There really isn't any documentation on hal-setup-wacom that I have seen.  But the precedent is using it only once per tablet, so...


What about something like:
```

<match key="usb.product_id" contains="0xe2">

```
for P & T's

i'll try taking out the info.callout and pad lines from the .fdi on 'if1' and let you know on reboot...

[COLOR="Red"]EDIT!!![/COLOR] Nope... Pad is there, accepts changes in wacomcpl but  button activity is gone... Only works if in 'if0'..

---

### Post by Favux on 2009-11-19
Hi dnprossi,

> Nope... Pad is there, accepts changes in wacomcpl but button activity is gone... Only works if in 'if0'.. 
I think you mean the buttons work only if pad is in 'if1', correct?

OK, I tried to build the exclude you talked about.  See if this works for you.

---

### Post by dnprossi on 2009-11-19
> **Favux said:**
> Hi dnprossi,
I think you mean the buttons work only if pad is in 'if1', correct?


yes sorry... just a little tired...

> 
OK, I tried to build the exclude you talked about.  See if this works for you.

i'll try that immediately... Just let me reboot...

It does not exclude anything I also tried to simplify only for my 0xd2 but both pads still appear... and settings too work as before... 

I'll go to sleep now but will try again in the morning just to tired to do things right. If you have other test files just let me know and i'll try all..

Cheers...

---

### Post by Favux on 2009-11-19
Hi dnprossi,

Thanks for trying it.  At least it still works!  Good night.

OK, I'm probably too far out on the branch.  Hopefully it's not a syntax error.  I'll try going back up, with luck not too far.  I'm changing the naming convention.  Test4 is now test3.1 and I'll attach test3.2.

Edit:  It may have had a syntax error too.  But if so you eliminated it by using just 0xd2.  But I suppose it could still be both.  So if test3.2 doesn't work, maybe what we need is "contains_not_outof".  But that isn't on the list.  Let's try it anyway (maybe it's undocumented), otherwise we'd have to construct an if/else block with contains or something.  That wouldn't be worth it.  So if 3.2 doesn't work try 3.3.  And maybe also try changing 3.1(formerly test4) with "contains_not_outof".

---

### Post by dnprossi on 2009-11-20
> **Favux said:**
> 
It may have had a syntax error too.  But if so you eliminated it by using just 0xd2.  But I suppose it could still be both.  So if test3.2 doesn't work, maybe what we need is "contains_not_outof".  But that isn't on the list.  Let's try it anyway (maybe it's undocumented), otherwise we'd have to construct an if/else block with contains or something.  That wouldn't be worth it.  So if 3.2 doesn't work try 3.3.  And maybe also try changing 3.1(formerly test4) with "contains_not_outof".

Good Morning Favux,

contains_not_outof: does not exist giving wacomcpl errors.

contains_not="d0;d1;d2;d3;d4" does work but considers what is in quotes a whole string resulting in double pad appearing in wacomcpl and lists.

contains_not="d2" (my tablet) works and will show just one pad in wacomcpl.

contains_not="d0" works and will show two pads in wacomcpl

The only solution at the moment that comes to my mind is using
T & P tablets udi's instead of bamboo ones.
Eg. 
```

<match key="info.udi" contains_outof="30;31;32;33;34;35;37;38;90;93;9a">
  <append key="wacom.types" type="strlist">pad</append>
</match>

```
I have it working on my install. Don't know if those are correct udis though.

---

### Post by Favux on 2009-11-20
Hi dnprossi,

Good morning.

Well good, at least we know "info.udi" is a match key that works!  Maybe it will work for the E2.

I think this will work but it is ugly:
```
        <match key="info.udi" contains_not="d0">
        <match key="info.udi" contains_not="d1">
        <match key="info.udi" contains_not="d2">
        <match key="info.udi" contains_not="d3">
        <match key="info.udi" contains_not="d4">
	  <append key="wacom.types" type="strlist">pad</append>
        </match>
        </match>
        </match>
        </match>
        </match>
```
Something more elegant and compact would sure be nice.  It would have been good if "contains_not_outof" worked/existed.

I'm sorry, you've lost me.  I don't understand:
```
<match key="info.udi" contains_outof="30;31;32;33;34;35;37;38;90;93;9a">

```

---

### Post by dnprossi on 2009-11-20
> **Favux said:**
> Hi dnprossi,

Good morning.

Well good, at least we know "info.udi" is a match key that works!  Maybe it will work for the E2.

I think this will work but it is ugly:
```
        <match key="info.udi" contains_not="d0">
        <match key="info.udi" contains_not="d1">
        <match key="info.udi" contains_not="d2">
        <match key="info.udi" contains_not="d3">
        <match key="info.udi" contains_not="d4">
	  <append key="wacom.types" type="strlist">pad</append>
        </match>
        </match>
        </match>
        </match>
        </match>
```
Something more elegant and compact would sure be nice.  It would have been good if "contains_not_outof" worked/existed.

True... :)

> 
I'm sorry, you've lost me.  I don't understand:
```
<match key="info.udi" contains_outof="30;31;32;33;34;35;37;38;90;93;9a">

```

what i understood is that Pad in "if0" is needed by other tablets and not by "d0,d1,d2,d3,d4" therefore if other tablets are found it will activate the secondary pad... contains_outof does work...

is this not correct???

---

### Post by Favux on 2009-11-20
Hi dnprossi,

Oh, I see what you're saying.  Use the wacom.rules table and take the last two digits of the Product ID to get the info.udi for all usb tablets other than the P & T's.  OK, that's doable.  But we probably ought to test them, which would be a headache.  And maybe it would be better handled by an info.callout or one of the other similar callouts HAL allows to run some code.  The linuxwacom code has all those ID blocks now.  The code would need to parse the last two digits of the Product ID to get the info.udi and would need to exclude the P & T's.

---

### Post by dnprossi on 2009-11-20
Yes I imagined that! it could work, just threw it in basket of choices... but yes it would be better handled by an info.callout.

In the meantime I rebooted and confirm that the above solution is ugly but works well.

---

### Post by Favux on 2009-11-20
Great!  Two solutions!  It's not as bad as I made it sound because not all usb tablets have a pad, so the list is shorter than the whole wacom.rules table or ID tables in the code.  We'd have to figure out which ones had a pad and what their Product ID's are.

Thank you very much for exploring this with me.  :D

I think we should just ask Ayuthia to add it to his HOW TO on the front page.  Since the duplicate pad isn't a functional problem as far as we can tell he could offer a manual edit of the .fdi to eliminate it.  For example you would use (as you've already done):
```
        <match key="info.udi" contains_not="d2">
	  <append key="wacom.types" type="strlist">pad</append>
        </match>
```
I don't think either of our two solutions should be submitted to the generic wacom.fdi as they stand.

Unless of course we or someone comes up with something better.  ;)

---

### Post by dnprossi on 2009-11-20
Thank you too for help understanding all of it:D...

Would be great to have "contains_not_outof" functionality...

I'll work with tablet all day and see to point out some issues still there with tablet buttons that still are not released somehow causing freezes until other buttons are pressed. No real issue but annoying..

---

### Post by kgingeri on 2009-11-21
Hi All,

I haven't disappeared, nor having a baby...  Hope all is well with Ayuthia and that he's enjoying a new addition! - I am assuming that's the reason for his absence  ;)

I have not been very active lately as I have needed time to help prepare for a year-end annual kids camp meeting, but it happens next Tuesday and I should be available again.

Do we know where we are?  Is everything working and solid?!  I know I got hangs still with the last version (34) I tried, but that was only one test.  I should redo everything clean and have another go likely.

Favux and Dnprossi, I think your doing great stuff with the fdi - I can even follow along, although not be of much help likely.

Anxious to here from Ayuthia, of how things are :)

EDIT: Did redo things - I had a 10-wacomlinux.fdi and a 10-linuxwcom.fdi - HA!  Anyway all seems pretty good.  I can turn touch ON/OFF with...
```
$ xsetwacom set touch touch off
$ xsetwacom set touch touch on
```
...not sure how to assign that to a pad button yet.

---

### Post by ElaineM on 2009-11-21
Hi, I habe an other problem.... This time with installing wcm2_patch

This is the error:

```

* <11:50:08 ich@Ronja: ~/linuxwacom-0.8.4-3> sudo cp src/2.6.28/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
cp: calling of stat for „src/2.6.28/wacom.ko“ not possible: No such file or directory

```This time I translated (or tried to) the error message so it might be kind of strange but hopefully understandable.

---

### Post by rebecca2525 on 2009-11-21
Can you tell us how you run the configure command and what the last lines of output are? They should look something like this:
```

    BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.28
  module versioning - no 
      kernel source - yes /usr/src/linux-headers-2.6.30-2-amd64
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl
                 TK - yes /usr/include/tcl
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------

```

---

### Post by ElaineM on 2009-11-21
Here it is:

```

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.31
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-14-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal Uninit-called IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------

```
Edit: Ok, I found my fault, I use an other kernel....
Edit2: It seems to work.... but I didn't have to reboot.

---

### Post by rebecca2525 on 2009-11-21
OK, let's try find your wacom.ko file. Can you run
```
find . -name "*.ko"
```
in the linuxwacom directory and post the output?

---

### Post by dnprossi on 2009-11-21
Hi ElaineM,

as your kernel is 2.6.31 you should use the next line of code to copy wacom.ko to the correct place. 
```

# cp src/2.6.31/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/

```
and not the 2.6.28 one.

try, it should work.
Cheers...

OUPS!!! Just read your edit.. Great...

---

### Post by ElaineM on 2009-11-21
Are there any possibilities for left hand usage?
The buttons are under my hand most of the time while I'm writing. At the moment it isn't that  bad because they havn't any functions, but it would be nice to turn the tablet around

---

### Post by dnprossi on 2009-11-21
> **ElaineM said:**
> Are there any possibilities for left hand usage?
The buttons are under my hand most of the time while I'm writing. At the moment it isn't that  bad because they havn't any functions, but it would be nice to turn the tablet around

Try adding this line of code to your fdi and reboot

from terminal:
```

sudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

```
just after after:
```

  <merge key="input.x11_options.Type" type="string">stylus</merge>

```
add line:
```

<merge key="input.x11_options.Rotate" type="string">HALF</merge>

```

---

### Post by ElaineM on 2009-11-21
Thanks, it works. I had not to reboot, plugging the tablet out and in again was all I needed to rotate it.

---

### Post by dnprossi on 2009-11-21
> **ElaineM said:**
> Thanks, it works. I had not to reboot, plugging the tablet out and in again was all I needed to rotate it.

Yes plug/unplug did work in 0.8.4.3... Forgot!!!:D
Great, Cheers....

---

### Post by Ayuthia on 2009-11-21
> **kgingeri said:**
> Hi All,

I haven't disappeared, nor having a baby...  Hope all is well with Ayuthia and that he's enjoying a new addition! - I am assuming that's the reason for his absence  ;)



No baby over here yet.  I was just working trying to get my touchscreen to work with 0.8.5-4's gestures.  It was doing the zoom-in/zoom-out pretty well, but that was all it was doing.  I am trying to figure out if the the two touchpoints are too shaky (If I leave one finger on the screen, the coordinates don't stop at one point like the stylus does).

I have not had a chance to study the hangs quite yet.  I did see in one of the /var/log/messages from someone that there was a spinlock crash.

I might take another stab at trying to get it to work without the wacom_sys.c changes.

---

### Post by kgingeri on 2009-11-21
> **Ayuthia said:**
> No baby over here yet.  ...

I have not had a chance to study the hangs quite yet.  I did see in one of the /var/log/messages from someone that there was a spinlock crash.

Great to hear from you again Ayuthia, do let us know when the new addition arrives!

Excuse my ignorance, but what is a 'spinlock'?  ;)

EDIT: BTW, I don't have anything other than logs as far as lockups go.  I did noticed a mis-spelled fdi in my hal directory so maybe that was doing it - not sure.  I am stable now it seems, so maybe wait until we have more occurrences of it before spending much time on it.

---

### Post by kgingeri on 2009-11-21
> **ElaineM said:**
> Are there any possibilities for left hand usage?
The buttons are under my hand most of the time while I'm writing. At the moment it isn't that  bad because they havn't any functions, but it would be nice to turn the tablet around

ElaineM, first let me warn you that tho things seem to change with repugging your tablet, I wouldn't trust that just yet.  A reboot is still the best - at least while testing.  Results can be unpredictable sending our coders on a 'wild goose chase' ;)

Also, besides changing the fdi file, you can also do a command at system level for this.  I haven't tried it myself but it should be something like this:
```

$ xsetwacom list param | more
...
Rotate           - Sets the rotation of the tablet. Values = NONE, CW, CCW, HALF (default is NONE). 
		   Tablet mappings applied after this command will be based on the new tablet orientation. 
...
```
...therefore, something like...
```
$ sudo xsetwacom set stylus Rotate HALF
```
...should work?  You may not have to use the 'sudo' command, not sure.

EDIT: oh and not sure which or if all 'devices' are needed - 'xsetwacom list' gives you tha list.  Maybe at least 'stylus' and 'touch'

---

### Post by Ayuthia on 2009-11-21
> **kgingeri said:**
> 
EDIT: oh and not sure which or if all 'devices' are needed - 'xsetwacom list' gives you tha list.  Maybe at least 'stylus' and 'touch'
As far as I know, you will need to configure the touch and the stylus.

---

### Post by Ayuthia on 2009-11-21
> **kgingeri said:**
> 
Excuse my ignorance, but what is a 'spinlock'?  ;)

It basically means that there is a thread that is waiting for something to unlock so it keeps checking and not doing anything.

As for the other news, I will keep you all updated. :)

---

### Post by ElaineM on 2009-11-21
> **kgingeri said:**
> ElaineM, first let me warn you that tho things seem to change with repugging your tablet, I wouldn't trust that just yet.  A reboot is still the best - at least while testing.  Results can be unpredictable sending our coders on a 'wild goose chase' ;)
[\quote]
What do you mean by 'wild goose chase'? Leo.org has 2 different translations, one is like "fearless adventure" the other like "trying without having a chance for achievment".
I hate rebooting.... it takes a very long time in my laptop....

[quote]
Also, besides changing the fdi file, you can also do a command at system level for this.  I haven't tried it myself but it should be something like this:
```

$ xsetwacom list param | more
...
Rotate           - Sets the rotation of the tablet. Values = NONE, CW, CCW, HALF (default is NONE). 
           Tablet mappings applied after this command will be based on the n
...
```...therefore, something like...
```
$ sudo xsetwacom set stylus Rotate HALF
```...should work?  You may not have to use the 'sudo' command, not sure.

EDIT: oh and not sure which or if all 'devices' are needed - 'xsetwacom list' gives you tha list.  Maybe at least 'stylus' and 'touch'

I don't know what the difference between the two types of rotation the tablet are...
I don't even know how hal works at all....


And I have an other little problem: when I select left-handes mouse in gnome's mouse settings every tip on the tablet is interpreted as a click with the second mouse button.
At the moment it isn't that bad, because my touchpad cannot ne changes to left-handed since the upgrade to 9.10.

---

### Post by Favux on 2009-11-22
Hi dnprossi and everyone,

Eureka!  The new-generic .fdi works for the TX2000 too!  Gali98 was nice enough to test it.  Since he is seeing some extra devices I think the problem may be how I'm parsing the names.  Maybe I tried to be too economical.  So at the expense of adding extra lines I went back to the old style.  With luck maybe this will work.

Could someone please test the new-generic test3.4 attached below.

---

### Post by rebecca2525 on 2009-11-22
I've been using the tablet the whole day yesterday, mostly the stylus, not the touch (accidentally issuing left-clicks once in a while makes working with the touch a bit annoying). I had one hang of the touch cursor movement, but no logs for it because I was running out of diskspace from all that debug stuff. :wink:

At the moment, I'm using a dualhead setup with an external monitor, the scale of the touch and stylus is automatically adapted to the whole virtual screen, and all works fine. Now comes more of a general question than a problem with the driver: When you want to use the stylus for actually drawing things, I believe this could be not exactly useful (haven't tried it yet, though) since the x and y scale of the tablet differ so much. Does anyone have experience with that? I guess you could always try window mode in Gimp or MyPaint, but that doesn't work well with "focus follows mouse"...

I've tried to reassign tablet buttons with xsetwacom, but that had no effect, but I belive this might be due to the reason that the pad is listed as touch with 25.4's fdi:
```
Wacom_Bamboo_6x8_Touch     touch
Wacom_Bamboo_6x8_Pen     stylus
Wacom_Bamboo_6x8_Touch_pad     touch
Wacom_Bamboo_6x8_Pen_eraser     eraser
```

Ah, and when the stylus is close enought to the tablet do deactivate touch, it also deactivates the buttons. I guess (but am not sure) this is not desired?

I also had an X hang just a moment ago. About the noise: I would say it doesn't come from the speakers, as says my boyfriend, but it's really hard to say for sure. You can still switch to a linux console and back. During that, the monitor is switched off for a short moment, and the noise stops too (and is back as soon as the monitor is on again, both in console and X). As before, pressing tablet buttons stops the X hang and the noise. And it seems that those hangs mostly occur while using touch and doing window manager-y stuff (clicking on root window to open menus and opening new applications). Logfiles attached.

---

### Post by dnprossi on 2009-11-22
Hi rebecca2525,
something is wrong with your setup.
Try prepatched #34 version on first page. Ayuthia has also added the [wacom-34] you had requested to be back.:)
I had problems with the unpatched one too. Maybe compile issues.
I cant remember what tablet are you using???

---

### Post by rebecca2525 on 2009-11-22
I thought patch 34 is basically 25.4 that I'm using? Don't get confused by the fact that the paths in my debug masseges say 25.3, that's because I had named the directory wrong. Or what do you meabn by "something is wrong"?

My tablet is d3.  

If there is sth new in 34 I should test I can do that, but that will have to wait a bit.

---

### Post by dnprossi on 2009-11-22
Hello Rebecca2525,

I had very similar issues (without sounds) with non patched one. I did not spend much time on it then changed to #34 and issues where gone. I believe I had **build issues** somewhere. I'll retry 25.4 building to see if that was the problem.
[COLOR="Red"]
EDIT!!![/COLOR]

As I said 25.4 will not compile correctly.
```

patch -p1 < wactablet.h.patch - [COLOR="Red"]Not Found[/COLOR]

```
Not being patched this is causing touch to still work as stylus + left-click and several hangs

The following similar to your xsetwacom list output is caused by [COLOR="Red"]wrong fdi[/COLOR]
you may be using [COLOR="Red"]src/util/linuxwacom.fdi[/COLOR] should be using [COLOR="Red"]Favux test2 at bottom of post #1[/COLOR]:
```

Wacom_Bamboo_Craft_Touch     touch
Wacom_Bamboo_Craft_Touch_pad     touch
Wacom_Bamboo_Craft_Pen     stylus
Wacom_Bamboo_Craft_Pen_eraser     eraser

```

Try prepatch 34 and Favux fdi problems will be gone..

[COLOR="Red"]REEDIT!!![/COLOR]
You can also try adding in "if0" fdi part changing "d2" to your tablet id: d0, d1, d3, d4 
```

<match key="info.udi" contains_not="d2">
  <append key="wacom.types" type="strlist">pad</append>
</match>

```
in place of line
```

  <append key="wacom.types" type="strlist">pad</append>

```
This will get rid of double pad in xsetwacom list

---

### Post by rebecca2525 on 2009-11-22
OK, tried 34 with Favux test2 fdi from the first post.

One hang of cursor movement withh touch so far, and one occasion where somehow the focus was stuck to my terminal window. I could move the cursor elsewhere, just not issue clicks and the look of the cursor stayed the way it looks in the terminal window. I could escape that situation with the tablet buttons. (Tablet buttons seem to be the way out of anything :wink:)

Also, when I tap on the touch to issue a left click, the cursor jumps a bit, which makes left-clicking extremely hard. In relative mode, it jumps to the lower right corner of my first screen (still in dualhead right now). I didn't have that problem with 25.4 and its fdi.

Touch cursor movement still a bit jittery.

Xsetwacom now lists:
```
stylus     stylus
pad     pad
cursor     cursor
touch     touch
eraser     eraser
pad     pad
```

I don't have time to investigate any further now, gotta go. No X hang so far, but they didn't occur very frequently, so that doesn't mean anything.

---

### Post by dnprossi on 2009-11-22
Yes... Buttons are still causing some trouble.. But don't crash as before just need to be reclicked...

> 
Also, when I tap on the touch to issue a left click, the cursor jumps a bit, which makes left-clicking extremely hard. In relative mode, it jumps to the lower right corner of my first screen (still in dualhead right now). I didn't have that problem with 25.4 and its fdi.


Yes, confirm.. in absolute mode there are issues, when tapping the cursor moves a bit to much off direction.

In relative mode it is better.. Buttons together with finger movemnet may cause freeze and when button reclicked the jumps. Somehow resolution is reset differently. If you don't touch them though for now all should work fine.. Also a reboot is needed to fix things. **Plug/unplug will not work**

This helps when working stylus only
toggle touch on/off
```

  xsetwacom set touch Touch off
  xsetwacom set touch Touch on

```

Yes, confirm... Touch cursor movement still a bit jittery. Some sensitivity settings are needed like in windows.

This is what you got with src/util/10-linuxwacom.fdi
```

Wacom_Bamboo_6x8_Touch     touch
Wacom_Bamboo_6x8_Pen     stylus
Wacom_Bamboo_6x8_Touch_pad     touch
Wacom_Bamboo_6x8_Pen_eraser     eraser

```

> 
Xsetwacom now lists:
Code:

stylus     stylus
pad     pad
cursor     cursor
touch     touch
eraser     eraser
[COLOR="Red"]pad     pad[/COLOR]


Now your tablet is correctly found having correct fdi... You still have two pads though. That should be fixed with instructions on my previous post. I had some trouble because of that too.

Issue with src/util/10-linuxwacom.fdi is that to use stylus pressure in gimp you will have to set it up from Preferences whereas Favux test2 will enable automatic recognition of stylus within gimp...

---

### Post by Favux on 2009-11-22
Hi everyone,

I think I'm getting a handle on the duplicate sub-device problem.  It would be helpful to have the lshal from the new-working .fdi on [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") and the new-generic test 2 on the first post of this thread from the same P & T.  And also the lshal on the new-generic test 2 without the Wacom name "parser" at the end of the .fdi.

Either with an info.callout and append line(s) HAL/DeviceKit automatically sets up a logicaldev_input_subdev whether it exists or not; or hal-setup-wacom is not checking to see if the sub-device exists and is letting HAL/DeviceKit set it up.  In other words depending on how HAL/DeviceKit functions, it may be possible to code hal-setup-wacom to check if a sub-device exists, and if it doesn't, tell HAL not to set up the logicaldev_input_subdev for the non-existent sub-device.

Sanity check.  Does this make sense to anyone else?

Either way it may not be something we can tackle through the .fdi without a lot of new contains or contains_not lines.  We might just have to live with confusing duplicate non-functional names.

---

### Post by rebecca2525 on 2009-11-22
> **Favux said:**
> It would be helpful to have the lshal from the new-working .fdi on [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") and the new-generic test 2 on the first post of this thread from the same P & T.

See attached files.

> And also the lshal on the new-generic test 2 without the Wacom name "parser" at the end of the .fdi.
Which would be what part exactly?

---

### Post by Favux on 2009-11-22
Hi rebecca2525.

Thank you for the lshal's!  The "parser is":
```
  <device>
    <match key="input.x11_options.Type" contains="stylus">
      <merge key="info.product" type="string">stylus</merge>
    </match>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
    <match key="input.x11_options.Type" contains="touch">
      <merge key="info.product" type="string">touch</merge>
    </match>
  </device>
```
Also did you by any chance try the new-generic test3.4?  I'm interested in seeing if there's a different "xsetwacom list"/wacomcpl with it.  I tend to doubt it but it would be nice to be sure.

Edit:  Oops!  The lshal_new_working.txt doesn't have the lsahl (207 bytes).

---

### Post by Favux on 2009-11-22
Oh wow!  Maybe there is a difference that we can use to exclude!  Early days.  Please send the rest of the lshal's rebecca2525.

---

### Post by rebecca2525 on 2009-11-22
One of the files was an lsusb output, here it comes again.

---

### Post by Favux on 2009-11-22
Hi rebecca2525,

Great!  Thank you so much!

By the way from your lshal I could tell I accidentally left off the pad line in 'if0' for new-generic test3.4.

Ok, try this new-generic test3.5 .fdi and see if it gets rid of the cursor and extra pad in "xsetwacom list" and wacomcpl.

Edit:  I decided to stop procrastinating and post the release candidate.  It does work for the TX2000 and TX2500 but unfortunately the pad on 'if1' shows up.  The filter on the "parser" doesn't catch it due to an unexplained difference (at least to me) in how HAL handles subdev's on 'if1'.  It also adds the E2.  No sight of the E3 and the new Thinkpad X200t has a serial multi-touch screen that we haven't figured out yet.  Other than labeling things and adding a few serial lines it's the same as test3.5.  I also added a debug version for testing the P & T's on this thread.

Edit2:  We got the new X200t multi-touch set up with linuxwacom 0.8.5-6.  Using the .fdi in 0.8.5-6 as a template I modified the serial section and added more serial tablets, hence rc2 and the debug version.  21 downloads of rc1 and 9 of the debug version.

With any of the .fdi's below you should be able to use wacomcpl to calibrate and configure your P & T.  See "[Section 3: Calibrating your Tablet]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1")".

---

### Post by dnprossi on 2009-11-23
Hi Favux,
It works, you did get rid of pad and cursor..

---

### Post by Favux on 2009-11-23
Hi dnprossi,

Absolutely Outstanding!!!  Thank you!  :D

Great, we just need some more folks to confirm it works for them.

I'm already writing a release candidate for general testing.  Hope I'm not ahead of myself.  ;)

Edit:  Yes dnprossi, your test35-lshal looks the same as rebecca2525's.  So the new excludes in the name parser are working!  Apparently HAL/DeviceKit and/or hal-setup-wacom do already tell us when there is no active sub-device!

---

### Post by marek_online on 2009-11-23
Hi Favux, 

The new fdi seems to be working fine for me too (that's the 0xd1). No cursor and only one pad in wacomcpl, and xsetwacom list producing this:

```
stylus           stylus
touch            touch
pad              pad
eraser           eraser
```

lshal output attached.

I'm assuming that touch shouldn't have any options in wacomcpl - just stylus and eraser?

---

### Post by Favux on 2009-11-23
Thanks marek_online,

Great, it looks like we may have it.  An E2 just confirmed it worked for him too, whereas the original 0.8.5-4 .fdi didn't.

In wacomcpl there should be an option to calibrate touch.  And there should be options to configure pad.  If they're not there then the code probably isn't hooked up yet.  Or wacomcpl needs new code to support the P & T's, I'm not sure which.

---

### Post by rebecca2525 on 2009-11-23
Yes, confirmed for the d3:
```
$ xsetwacom list
touch     touch
stylus     stylus
eraser     eraser
pad     pad
```EDIT: Great, I can configure the tablet buttons now! For some reason, my buttons from top to bottom are Button2, Button3, Button4, Button5. :D

---

### Post by Favux on 2009-11-23
Hi rebecca2525,

Good!

> For some reason, my buttons from top to button are Button2, Button3, Button4, Button5.
Weird.


OK, I have the release candidate done but I'm going to hold off.  I think I ran into the E3 a few days ago and neither of us realized it.  And that's why we couldn't set him up.  If I'm right the configuration is a little strange but the new .fdi should work for it too.  I'll see if he is still around and wants to do a little more experimenting.

---

### Post by ob1kenobi on 2009-11-23
Hi all,

Well I kinda went down a rabbit hole and cleaned up so much that I'm not sure what to do:sad:

This type of change usually won't get accepted by the main stream development, but I figured I post it here if any one wants to take a look.

I've attached the prepatched tree.

Basically the Makefiles have been reworked and the kernel module now supports 2.6.x in a single set of sources (no more multi-versions of the kernel source).  Also, I've gotten all modules and tools to build without warnings (at least on Karmic :D).

I'm using it on my machine even though there are still issues with single click touch I'm trying to still fix (when doing a fast touch the cursor flies to the bottom left of the screen).  It does fix a few things:

1. Touch device scales correctly even if X server is already running when tablet is connected.
2. xsetwacom returning touch type for pad.  This was actually a comparison problem in wacomcfg.c since touch was checked before pad in the device name and the bamboo tables have Touch in their name.
3. The 10-linuxwacom.fdi should support all tablets without having to rewrite the info.product keys.  So the device product names now show up as reported by the kernel, like it's supposed to work.

Good luck, and hopefully someone finds this useful.

---

### Post by ZoomQuiet on 2009-11-24
Thanx for all! i'm Chinese, in Ubuntu 9.10 with BAMBOO CTH-461;
linuxwacom-0.8.5-4-bamboo-34.tar.bz2  is work!
but ... :
$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1953)

$ xsetwacom --help
xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
$ whereis xsetwacom
xsetwacom: /usr/bin/xsetwacom /usr/local/bin/xsetwacom /usr/share/man/man1/xsetwacom.1.gz
$ lsusbroll up
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 056a:00d2 Wacom Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

so what happen?
now, usage linuxwacom-0.8.5-4-bamboo-34.tar.bz2 included files:
- /lib/udev/rules.d/40-xserver-xorg-input-wacom.rule
- /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
my stylus move and click is OK, BUT not buttom support;
my touch pad move is bad; 4 buttom is none/right click/roll up/roll down;
Mnnn ...
that is sooo blame;
waht can i do?

---

### Post by rebecca2525 on 2009-11-24
Hi ob1kenobi,

just testing your latest patch with its fdi.

What I've noticed about starting X and plugging in the tablet:

**Start X while tablet is plugged in:**
Stylus and eraser are fine, touch is fine (although a bit jittery as with other patches). Touch scale is wrong (only about 3/4 of the width and 3/4 of the heighth of the tablet are used). No accidental left-clicks when putting down the finger to move the cursor so far.

**Start X while tablet is plugged in, then unplug/replug tablet:**

Stylus and eraser still fine, touch still as above (including the scale). But: tapping on the tablet for left-clicking moves the cursor to the lower right corner in relative mode and causes smaller cursor jumps in abslute mode. 

**Start X without tablet plugged in, then plug it in**

No touch.

```
xsetwacom list
Wacom_Bamboo_6x8_Pen_eraser     eraser
Wacom_Bamboo_6x8_Pen     stylus
```


I'm also getting closer to reproducing the X hangs (which I still have): It involves tapping on the tablet on the root window to open the menu of the window manager, then moving the cursor away with the menu still open and pressing the bottommost tablet button. This doesn't hang X every time, but quite often. Don't know if I can make it 100% reproducable.

Oh, and on Debian, I didn't get any compile warnings either. I'm wondering if I can drop my hack to place some links in the kernel header directory now...

---

### Post by marek_online on 2009-11-24
Hi Ob1kenobi,

For me, the new patch is an improvement on the old not just in terms of warnings at build time, but in touch use. There is still jitter there as rebecca2525 points out, particularly during slower and smaller movements, but it seems reduced for me - either way I'm finding using the touch to navigate and press buttons a little easier. Took me a little while to get used to dragging too, but I think I've got it now.

As for hotplugging - not so much success. I use touch in relative mode, and after replugging in a tap sends the pointer to the left-most edge of my screen, where it stays. The pen seems fine. This behaviour should be pretty much the last thing in the logs attached.

Thanks for this. Must try it with Favux's generic fdi now.

---

### Post by ob1kenobi on 2009-11-25
> **marek_online said:**
> Hi Ob1kenobi,

For me, the new patch is an improvement on the old not just in terms of warnings at build time, but in touch use. There is still jitter there as rebecca2525 points out, particularly during slower and smaller movements, but it seems reduced for me - either way I'm finding using the touch to navigate and press buttons a little easier. Took me a little while to get used to dragging too, but I think I've got it now.

As for hotplugging - not so much success. I use touch in relative mode, and after replugging in a tap sends the pointer to the left-most edge of my screen, where it stays. The pen seems fine. This behaviour should be pretty much the last thing in the logs attached.

Thanks for this. Must try it with Favux's generic fdi now.

Thanks for testing marek.  From your logs it looks like you are still using 34's kernel module.  Can you make sure that you are using 35's?

---

### Post by ob1kenobi on 2009-11-25
> **rebecca2525 said:**
> 
**Start X without tablet plugged in, then plug it in**

No touch.

```
xsetwacom list
Wacom_Bamboo_6x8_Pen_eraser     eraser
Wacom_Bamboo_6x8_Pen     stylus
```
I'm also getting closer to reproducing the X hangs (which I still have): It involves tapping on the tablet on the root window to open the menu of the window manager, then moving the cursor away with the menu still open and pressing the bottommost tablet button. This doesn't hang X every time, but quite often. Don't know if I can make it 100% reproducable.


Thanks for testing.  Can you post a lshal for this last case?  I'd like to see what drive got the touch interface.

> 
Oh, and on Debian, I didn't get any compile warnings either. I'm wondering if I can drop my hack to place some links in the kernel header directory now...
No, you will probably still need the hack.

---

### Post by kgingeri on 2009-11-25
> **ob1kenobi said:**
> Hi all,

Well I kinda went down a rabbit hole and cleaned up so much that I'm not sure what to do:sad:
...

Ha, I've been down one too - checking out Chrome OS  ;v)

I'll give it a try later tonight hopefully.

EDIT: BTW when I did an lsb_release command, it told me it was Karmic Koala!!!  Yeah, Chrome OS!!

---

### Post by Favux on 2009-11-25
Hi kgingeri,

This may explain why.
> Prerequisites
You need to have Linux. We currently support the following:

    * Ubuntu (Hardy 8.04 or newer, Karmic 9.10 recommended)
    * An account with root access (needed to run chroot and modify the mount table)
    * Chromium prerequisites (needed to build a Chromium-based browser as part of building Chromium OS)


From:  [http://www.chromium.org/chromium-os/building-chromium-os](http://www.chromium.org/chromium-os/building-chromium-os)

---

### Post by kgingeri on 2009-11-25
> **Favux said:**
> Hi kgingeri,

This may explain why.

From:  [http://www.chromium.org/chromium-os/building-chromium-os](http://www.chromium.org/chromium-os/building-chromium-os)

Cool - so let's port tablet stuff to Chrome OS!!
[SIZE="5"]
Kidding!!![/SIZE]  :lol:

---

### Post by Iuly on 2009-11-25
Hi everybody! I was reading almost all the pages of this post, because I just got a Wacom Bamboo Pen and I have problems with it. I use Ubuntu 9.04 
This is what appears after lsusb : 

Bus 002 Device 005: ID 056a:00d4 Wacom Co., Ltd 


I also tryied this [http://ubuntuforums.org/showpost.php?p=8313047&postcount=145](http://ubuntuforums.org/showpost.php?p=8313047&postcount=145)  and this is what gives me back , so I don't know what to do next.

iulda@iulda-desktop:~/Escritorio$ chmod +x wpen
iulda@iulda-desktop:~/Escritorio$ ./wpen
ls: no se puede acceder a linuxwacom*bz2: No existe el fichero ó directorio
ls: no se puede acceder a wcm_patch*bz2: No existe el fichero ó directorio

Linux Wacom Testing Builder

Enter linuxwacom version or press enter for []: 


I will be happy to test all and try to help with what I can.

---

### Post by LaHyenne on 2009-11-26
Hello,

I've everything and installed my driver as written in the automatic instal on post 1
I have the pen and touch CTH 460 and Karmic.

*What works : *
_For the stylus_ (all perfect or almost perfect)
-The pen, with pressure
-The eraser with pressure
-The stylus buttons
_For the pad_
-The four buttons
-The touch as a relative and absolute mouse (although it has a lot of bugs and is not usable in an everyday work)

*What doesn't work :*
-Does not work multiple fingers
-In the wacomcpl, I can configure pen and eraser but I have nothing under pad and touch pad
-when I unplug and plug it back, It mess up totally the touch
-I have two devices as touch ? Maybe some problems come from that ?

*xsetwacom list dev*
Wacom_Bamboo_4x5_Pen     stylus
Wacom_Bamboo_4x5_Pen_eraser     eraser
Wacom_Bamboo_4x5_Touch     touch
Wacom_Bamboo_4x5_Touch_pad     touch


I am willing to help test your advanced programming stuff, so let me tell where and how and what I should do.
Thanks for your extremely useful work,
LH

---

### Post by Favux on 2009-11-26
Hi LaHyenne,

Try using the .fdi in [post #579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").

---

### Post by LaHyenne on 2009-11-26
I did not notice changes.

But maybe I was doing something wrong ?
I just redid modprobe -r wacom and reboot.

What do I have to reinstall to test a new fdi ?

Thanks,
LH

---

### Post by Favux on 2009-11-26
Hi LaHyenne,

Just back up the current one:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi /home/yourusername/Desktop/10-linuxwacom.bak
```
And substitute the contents of the new one for it:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```
and reboot.

---

### Post by rebecca2525 on 2009-11-26
Replace the file /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi with the new fdi and reboot. Make sure that you don't have several fdi's for wacom in that directory.

---

### Post by LaHyenne on 2009-11-26
Okay.

So, no changes :
eeblanc@dell-desktop:~$ xsetwacom list devWacom_Bamboo_4x5_Touch     touch
Wacom_Bamboo_4x5_Pen     stylus
Wacom_Bamboo_4x5_Touch_pad     touch
Wacom_Bamboo_4x5_Pen_eraser     eraser

The touch seems much much smoother and I could use it like that.
There is somewhat two fingers, but I am not sure what.

What is suppose to work ?
Can we set something like a routine for testing ?
Is there something special that activates at each action ? (some log ?)
I could then try to do the following :
- one finger in each corner,
- then one finger from top left to bottom right
- then one finger from top to bottom, then one finger left to right, then right to left
- one finger click
- one finger double click
- two fingers click
- two fingers double click
- two fingers slide
- two fingers rotation
- two fingers expand and getting closer again.

Or something like that ?

Cheers, LaHyenne

(I'm so happy I can use the wacom now anyway, thank you guys ;) )

EDIT : Just saw that the pen buttons don't work anymore :(

EDIT : in fact, the buttons are working fine after I hit the left Control key on my keyboard... Other wise, it seems the Control key is locked down. It might be thanks to the try to use a Ctrl Z shortcut for my first pad button (and three others for the other buttons)



EDIT : Okay, I reinstalled all from scratch and had the same problem till I lost the mouse buttons as well. I unplugged the wacom and reboot and back to normal with my mouse.
I don't know what to do now so I'll wait for you guys.

---

### Post by ZoomQuiet on 2009-11-26
flow [#587]("http://swiss.ubuntuforums.org/showpost.php?p=8377865&postcount=587")
sorry for my poor Cnglish....
in my Ubuntu 9.10 with Bamboo Fun Pen and Touch(CTH-461),use linuxwacom-0.8.5-4-bamboo-34.tar.bz2
fixed base Ayuthia's[post #1]("http://swiss.ubuntuforums.org/showpost.php?p=8283168&postcount=1")
but some thing is odd...

```

$ /usr/local/bin/xsetwacom list
/usr/local/bin/xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

$  /usr/bin/xsetwacom list
stylus     stylus
touch     touch
pad     pad
eraser     eraser

$ /usr/bin/wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/bin/wacomcpl-exec" line 2042)

$ /usr/local/bin/wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1953)

```

so i usage Favux fdi
$ diff tmp/0day/wacom/579#Favux_new-generic_test3.5_10-linuxwacom.fdi.txt /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

NOW, touch pad is all OK; buttons auto set is(from top)&#65306;
- middle click
- right click
- page up
- page down

BUT! stylus pen buttons is not work ...
this very terrible;
because pen buttons for me set as "right click" and "middle click" is very very useful;

can i fixed .fdi to action pen buttons?

---

### Post by dnprossi on 2009-11-27
Hi ob1kenobi,

sorry I'm late,
tested #35  with your fdi on Ubuntu Desktop Karmic using 0xd2 tablet

Stylus works fine in all cases with correct resolution

Reboot after install with tablet plugged in, all works. tap, drag, select too.

plug/unplug resets to correct resolution but tapping moves to right of screen. This happens if in **relative mode**. 
Removing this setting from fdi and plug/replug in **absolute mode** tapping works with small jitter to top-right as always.

**xsetwacom set touch mode** absolute will not work, returns error:
```

Error (2): WacomConfigOpenDevice: No such device

```

xsetwacom list returns:
```

Wacom_Bamboo_Craft_Touch_pad     pad
Wacom_Bamboo_Craft_Touch     touch
Wacom_Bamboo_Craft_Pen_eraser     eraser
Wacom_Bamboo_Craft_Pen     stylus

```

**Tested also with latest Favux-fdi**
On reboot with tablet plugged-in everything works fine

**xsetwacom set touch mode** absolute or relative work fine, no errors

When plug/replug resolution is reset to upper-left quarter of screen

if 
```

<merge key="input.x11_options.Mode" type="string">relative</merge>

```
added to fdi in "if1" section and plug/replug touch is lost
 
xsetwacom list returns:
```
 
pad     pad
touch     touch
eraser     eraser
stylus     stylus

```

---

### Post by ob1kenobi on 2009-11-27
> **dnprossi said:**
> Hi ob1kenobi,

sorry I'm late,
tested #35  with your fdi on Ubuntu Desktop Karmic using 0xd2 tablet


Thanks for testing!

> 
**xsetwacom set touch mode** absolute will not work, returns error:
Note that with the provided fdi file you now have to use the device name below

> 
```

Wacom_Bamboo_Craft_Touch_pad     pad
Wacom_Bamboo_Craft_Touch     touch
Wacom_Bamboo_Craft_Pen_eraser     eraser
Wacom_Bamboo_Craft_Pen     stylus

```So the command becomes
**xsetwacom set Wacom_Bamboo_Craft_Touch mode absolute**

---

### Post by dnprossi on 2009-11-27
> **ob1kenobi said:**
> 
Note that with the provided fdi file you now have to use the device name below

So the command becomes
**xsetwacom set Wacom_Bamboo_Craft_Touch mode absolute**

Yes!! Figured it out after some trials.. It does work... Thanks..

[COLOR="Red"]EDIT!!![/COLOR]
With Favux FDI - Gimp automatically recognizes the stylus - Pressure eraser work without having to go to preferences to activate it.

With Your Fdi - Gimp does not recognize the stylus - One has to go to preferences - input devices - configure Extended Input Devices - select the wacom driver and activate it.

The result though is that stylus is not there and eraser works as stylus.

---

### Post by bako on 2009-11-28
hi all.

i've a question, the orientation of the tablet works for u?

if i rotate the tablet, oblique, and move the pen orizontal the pointer on the screen goes oblique and not orizontal.

another question: the guide in first page works for the 9.10?

---

### Post by dnprossi on 2009-11-28
Hi bako,

> **bako said:**
> 
if i rotate the tablet, oblique, and move the pen orizontal the pointer on the screen goes oblique and not orizontal.

rotation has to be set manually.

[instructions here ]("http://ubuntuforums.org/showpost.php?p=8360124&postcount=558")

> another question: the guide in first page works for the 9.10?

Yes it does work... Carefully follow instructions for Karmic 9.10. Download Option A and after untarring skip to Compile and install. also use [#579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579") fdi

Cheers...

---

### Post by bako on 2009-11-28
i'm using the version of apt-get and is the 0.1.9 and the rotate doesn't work

i tried the method in first page (using step A). edit: solved

now i have this problem:
```


stefano@stefano-desktop:~/linuxwacom-0.8.5-4$ xsetwacom set stylus Rotate CWError (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'


```

---

### Post by dnprossi on 2009-11-28
Before building you also need to install some dependencies:

```

# apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev 
# apt-get install xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
# apt-get install libhal-dev

```

---

### Post by bako on 2009-11-28
> **dnprossi said:**
> Before building you also need to install some dependencies:

```

# apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev 
# apt-get install xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
# apt-get install libhal-dev

```

i do that and the compilation and install goes ok.

but

now 

```
stefano@stefano-desktop:~$ xsetwacom list
Wacom_BambooFun_4x5_eraser     eraser
Wacom_BambooFun_4x5     stylus
stefano@stefano-desktop:~$ xsetwacom set stylus Rotate CW
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'

```

---

### Post by dnprossi on 2009-11-28
> **bako said:**
> 
```
stefano@stefano-desktop:~$ xsetwacom list
Wacom_BambooFun_4x5_eraser     eraser
Wacom_BambooFun_4x5     stylus
stefano@stefano-desktop:~$ xsetwacom set stylus Rotate CW
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'

```

You are using wrong fdi
download fdi file in post #579 [here]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579")
copy file
```

sudo cp Favux_new-generic_test3.5_10-linuxwacom.fdi.txt /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

```

Reboot...

[COLOR="Red"]EDIT!!![/COLOR]
This will not work!!!!
```
xsetwacom set stylus Rotate CW
```
try adding:
```
<merge key="input.x11_options.Rotate" type="string">CW</merge>
```
to fdi file...

instructions [here]("http://ubuntuforums.org/showpost.php?p=8360124&postcount=558") 

remember to reboot after change...

P.S. these are all test driver patches not all is working yet... enjoy!

---

### Post by marek_online on 2009-11-28
Looks like ROTATE doesn't work with the 0.8.5-4 code yet. At least it hasn't for me, and it would appear that Favux had the same problem

[http://ubuntuforums.org/showpost.php?p=8332378&postcount=386](http://ubuntuforums.org/showpost.php?p=8332378&postcount=386)

---

### Post by rebecca2525 on 2009-11-28
> **ob1kenobi said:**
> Thanks for testing.  Can you post a lshal for this last case?  I'd like to see what drive got the touch interface.
I haven't been able to reproduce that problem. Dunno if it was just a weird circumstance, or if my Debian updates since then have changed things...

---

### Post by kgingeri on 2009-11-29
Wow, this is all working pretty good for me.  I did a complete re-install of Karmic UNR on a netbook here, ran thru the steps in **post #1** *(BTW we don't say anywhere that kernel sources are needed, do we?)*, installed Favux's **Favux_new-generic_test3.5_10-linuxwacom.fdi** file and everyhting seems to work ticky-boo.  

One thing I noticed is that two finger scroll works, but seems to be backwards maybe?  ie. two fingers upward motion scrolls a windows contents down.

Replugging has nil effect on functionality that I see either - at this point.  :D

Have we got rid of the hanging?  Last issue I had with that, I was using my netbook all day before it hung.  Not a nice one to debug!

EDIT1: oh oh, spoke too soon.  Relative mode for touch leaves cursor stuck to the left.  Will try a full reboot to be sure tho.

EDIT2:  Hah - full reboot cleared that up. Replugging in relative mode leave my touch restricted to the upper left again.  But that's all I see for now.  :)

EDIT3: ok got the cursor hung on left again with touch, after a replug and setting/unsetting touch on/off and relative on/off.

---

### Post by LaHyenne on 2009-11-29
OKay.
I reinstalled everything, including the official wacom files.
I deleted all the wacom related files fdi AND rules

And it seems that this was part of the issue.
Because now I can use pretty much everything okay.

I do have the same "stuck on left" bug with relative for touch.
I will test further and tell you.

LH

---

### Post by TheguywholikesLINUX on 2009-12-01
Wow, I feel sooo outdated and a bit silly. I started the tread that caused this one to be created and I have not read a single post on this thread yet! And to make matters worse, I don't actually have my wacom bamboo working! (well it did kinda work, but then I got a new kernel and I have not been able to reinstall everything yet)

Anyway, If there is something I can do to help, please PM me so that I get your message, and it is not lost in hundreds of messages!

EDIT: are we still working on the pen/erasor/buttons, or have we moved on to touch?

---

### Post by ZoomQuiet on 2009-12-01
> EDIT: are we still working on the pen/erasor/buttons, or have we moved on to touch?

pen/erasor/buttons is better than touch!
because:
- we almost work under CLI
- the most option is need only one click

---

### Post by Favux on 2009-12-01
Hi TheguywholikesLINUX,

> are we still working on the pen/erasor/buttons, or have we moved on to touch? 
Everything's working now.  See Ayuthia's first post on this thread and use -34 and the [new-generic .fdi]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").  Still some minor problems so bug test and report any.  Or you could use obe1kenobe's latest update a page or two back.


Hi ZoomQuiet,

> pen/erasor/buttons is better than touch!
Not in all use scenarios.  At least Microsoft and a lot of OEM's are hoping touch is a viable interface.  A UI designed for touch helps.

If I'm using a Bamboo P & T for photos being able to pinch to zoom or rotate with a gesture can help speed up work flow.  Similar cases can be made for other tasks.

---

### Post by kgingeri on 2009-12-01
Quick update.  I haven't had an OS hang yet  :D  and all is still working fine.

Hi ZoomQuiet,
If you set touch to 'relative' mode and pen to 'absolute' (use xsetwacom), I'm sure you will find touch useful.

I switch back and forth for different tasks.  I have assigned a pad button to turn touch on and off so when working with the pen I don't get erratic cursor placement.  :)

---

### Post by TheguywholikesLINUX on 2009-12-01
Ok, I have followed the new instructions by Ayuthia and using Favux's .fdi mentioned above. I rebooted, and......

.... The pen works well! I don't have my mouse jumping when I take my pen away from the screen :) Pressure sensitivity seems to be improved aswell!
Unfortunately I still do not have any eraser (it won't move the mouse, and does not show up in wacomcpl or gimp)

As for touch, it worked at first, but I had to run xsetwacom otherwise I couldn't use it (and whenever you put your finger down it clicked, so you couldn't move the mouse with your figure without the mouse button being down, but this is the default behavior I think) But after trying to "tap" the mouse disappeared, I found it in the bottom right corner of the screen. After a few more attempts touch sopped working altogether!

It just started working again, but it is **very** jumpy and you can't get much accuracy with it (as low as +-10 pixels!)
I tried tapping, and once again it went straight to the bottom right hand corner. After putting two fingers onto the tablet to see if I could click by tapping the second one it stopped again. However this is fixed by pressing a tablet button, then you can move the mouse with your finger until you put two on again, and then you have to press a button again to get it to work etc.....

So the eraser and touch do not work quite as expected yet, but it seems everything else does, just some config to do!

---

### Post by TheguywholikesLINUX on 2009-12-01
> **kgingeri said:**
> I have assigned a pad button to turn touch on and off so when working with the pen I don't get erratic cursor placement.  :)

Could you tell me how because I found this feature useful when I tried my tablet out in windows. Thanks!

---

### Post by rebecca2525 on 2009-12-01
TheguywholikesLINUX, some of your problems sound like things we had but seem to have overcome (no eraser, the left-click issue). Are you sure you don't have any old fdi's or so hang around?

> **TheguywholikesLINUX said:**
> I tried tapping, and once again it went straight to the bottom right hand corner.
That's what I have in relative mode and when the tablet is not plugged in on X start. If I plug in the tablet before X (re)starts, there's no jump.

> After putting two fingers onto the tablet to see if I could click by tapping the second one it stopped again.
Confirmed. Tap with second finger does nothing at the first time, but stops touch on the second time.

Also, still X hangs with noise.

---

### Post by TheguywholikesLINUX on 2009-12-01
I'm using this .fdi:

> **Favux said:**
> the [new-generic .fdi]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").

I've attached the same files as you did, just in case ;)

---

### Post by brabender on 2009-12-01
Hello; I have the same issues than TheguywholikesLINUX; tablet here is CTH-460, identified as 056a:00d1  with lsusb. Stylus works OK, pressure is correct, and touch works (including two-finger scroll, for me it's not inverted; scroll down means the document scrolls down), but not rotation, even after correcting .fdi according to post #558, and eraser is not recognized. I've built the driver as in first post of the thread, using option A (pre-patched sources) and with Favux_new-generic_test3.5_10-linuxwacom.fdi.txt. 

xsetwacom list displays touch and stylus, nothing else, and in Gimp I have to configure extended input devices to enable the tablet.

Am I missing something? I've browsed through all the thread, but with 600+ posts it's easy to get lost, and easier if english is not your first language.

Anyway, thanks for making possible to use my new tablet in Ubuntu. I simply refuse to go back to Windows just to play with my new toy... errr  I mean just for use the tablet editing photos and stuff  ;-)

---

### Post by kgingeri on 2009-12-01
> **TheguywholikesLINUX said:**
> Could you tell me how because I found this feature useful when I tried my tablet out in windows. Thanks!

Ok, I can't do it again!  Weird - I may have been mistaken! The button numbering is (top down LED to left) Button2, Button3 (LED) Button4, Button5.
I believe this is due to the stylus buttons being 0 and 1?

BTW, I have the CTH-460 now too and have eraser working fine - at least in Xournal.

I'll update if I find how to toggle touch.

My Two-finger scroll works in the opposite direction that I use the pen if I drag the scroll-bar button with it.

---

### Post by kgingeri on 2009-12-01
> **brabender said:**
> Hello; I have the same issues than TheguywholikesLINUX; tablet here is CTH-460, identified as 056a:00d1  with lsusb. Stylus works OK, pressure is correct, and touch works (including two-finger scroll, for me it's not inverted; scroll down means the document scrolls down), but not rotation, even after correcting .fdi according to post #558, and eraser is not recognized. I've built the driver as in first post of the thread, using option A (pre-patched sources) and with Favux_new-generic_test3.5_10-linuxwacom.fdi.txt. 

xsetwacom list displays touch and stylus, nothing else, and in Gimp I have to configure extended input devices to enable the tablet.

Am I missing something? I've browsed through all the thread, but with 600+ posts it's easy to get lost, and easier if english is not your first language.

Anyway, thanks for making possible to use my new tablet in Ubuntu. I simply refuse to go back to Windows just to play with my new toy... errr  I mean just for use the tablet editing photos and stuff  ;-)

I can only think of three things (BTW your english is very good!):
[LIST=1]
[*] did you reboot after all installs and copies?
[*] use the fdi [here]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579") post #579
[*] do you have more than one 10-linuxwacom.fdi file defining wacom stuff in the /usr/share/hal/fdi/... directory - or did you not rename an original to that name?
[/LIST]

---

### Post by bromalex on 2009-12-01
Another, How-To Install Bamboo Pen&Touch (CTH-460) in Karmic (A newbie recollection of info from this Thread)

First I want to say that I am a newbie so I am trying to recreate the How-To's that more savvy users posted (thanks specially to Ayuthia, Favux, ob1kenobi and all the others)
This said, if you find anything wrong in these steps, please correct me! (I am not a native English speaker, so forgive me if I’m not clear). Thanks.

I followed Post#1(Ayuthia) but with the file from Post#586(ob1kenobi)

I am using a new Ubuntu Karmic installation (Not un upgrade from 9.04) with the latest updates (Dec, 1 2009) but with my work software installed (meaning I have new libraries not present in a fresh install). My kernel version is 2.6.31-15 and I have a Bamboo Pen & Touch CTH-460 (OxD1).

Already had xserver-xorg-input-wacom installed, so I added in Synaptic:
```

sudo apt-get install wacom-tools libhal-dev tk8.4-dev libncurses5-dev xserver-xorg-dev libxi-dev

```

wacom-tools added this: tcl, tk
libhal-dev added this: libdbus-1-dev
xserver-xorg-dev added this: libpciaccess-dev, libpixman-1-dev, x11proto-dri2-dev, x11proto-fonts-dev, x11proto-randr-dev, x11proto-render-dev, x11proto-video-dev

I already had the following installed: build-essential, libx11-dev, x11proto-input-dev, tcl8.4-dev

In terminal enter:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
```

I went then to Option A, but downloaded the pre-patched file (linuxwacom-0.8.5-4-35.tar.bz2) from user ‘ob1kenobi’ Post#586) 
Uncompress the tarball and change to the directory created:
```
tar -xvjf linuxwacom-0.8.5-4-35.tar.bz2
cd linuxwacom-0.8.5-4-35
```
Compile and install:
```
make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/kernel/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
```
To reload the module:
```
sudo modprobe -r wacom
sudo modprobe wacom
```

Some notes about the output of the compilation steps:
After ‘make clean’ terminal shows:
make: *** No rule to make target `clean'.  Stop.

After ‘make distclean’ terminal shows:
make: *** No rule to make target `distclean'.  Stop.

After ‘./configure --enable-wacom --prefix=/usr’ terminal ends with:
….
BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.31-15-generic-pae
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-15-generic-pae/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes
  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins

After ‘make’ terminal scrolls lots of data, and I had no errors.

After ‘sudo make install’ terminal scrolls lots of data, and I also had no errors.

The original instructions called for a: 
sudo cp src/kernel/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
but I couldn’t find src/2.6.28/ or 2.6.31 or wathever, so I used src/kernel/ where my recently compiled wacom.ko was located. Maybe this is because I am using ob1kenobi file.
To be safe I first did a backup of the original wacom.ko.
Any mistakes here, guys???

I rebooted and plugged my Wacom.

In GIMP I configured extended input devices. I have pressure sensitivity and if I turn the pen upside down it changes to eraser tool (also with pressure sensitivity) :-)

Some useful commands:
**xsetwacom**
To find all the parameters, in Terminal run:
```
xsetwacom list param
```
To display devices:
```
xsetwacom list dev
```
My output of ‘xsetwacom list dev’ was:
Wacom_Bamboo_4x5_Pen_eraser     eraser
Wacom_Bamboo_4x5_Pen     stylus
Wacom_Bamboo_4x5_Touch_pad     pad
Wacom_Bamboo_4x5_Touch     touch

To find the current used parameter, eg. resolution of touch
```
xsetwacom get Wacom_Bamboo_4x5_Touch touch bottomx
```
My output was:
1
480

To turn the touch on/off:
```
xsetwacom set Wacom_Bamboo_4x5_Touch touch Touch off
xsetwacom set Wacom_Bamboo_4x5_Touch touch Touch on
```

**Wacomcpl**
In Terminal run:
```
wacomcpl
```
 It will bring up a dialog that will allow you to configure your tablet and change which buttons do which. After you exit wacomcpl, your settings are saved to a file in your home folder named .xinitrc

(I don’t know if mine is correct, as I don’t find a Calibrate button/function anywhere. I am attaching a screenshot)

My Default settings for 'wacomcpl' are:

Pen_eraser>Feel>4,6,4,2
Pen_eraser>Tool Buttons>Button 1>Left,Absolute
Pen_eraser>Tracking>0,0,14720,9200

Pen>Feel>4,6,4,2
Pen>Tool Buttons>Button 1>Left
Pen>Tool Buttons>Button 2>Middle
Pen>Tool Buttons>Button 3>Right
Pen>Tool Buttons>Positioning Mode>Absolute
Pen>Tool Buttons>Side Switch Mode>Side Switch Only
Pen>Tracking>0,0,14720,9200

Touch_Pad>Tablet Controls>Button 1>Left
Touch_Pad>Tablet Controls>Button 2>Middle
Touch_Pad>Tablet Controls>Button 3>Right
Touch_Pad>Tablet Controls>Button 4>Fourth
Touch_Pad>Tablet Controls>Left Strip Up>Fourth
Touch_Pad>Tablet Controls>Right Strip Up>Fourth
Touch_Pad>Tablet Controls>Left Strip Down>Fifth
Touch_Pad>Tablet Controls>Right Strip Down>Fifth
Touch : doesn’t have any settings

Thank you so much for all who made it possible for my Bamboo to work in Ubuntu :D
Hope this will help someone and sorry for such a lengthy post.

PS: I have some doubts but will use another post for that.

---

### Post by bromalex on 2009-12-01
Hi

I didn't test Touch so much, but it does seem that it is still not working 100% (some unwanted clicks, cursor can jump, but as I said I didn't test it properly).

So my first question is:
How to assign a 'Touch Toggle' function to the top Button on the Tablet?
The only way I can do it is by:
xsetwacom set Wacom_Bamboo_4x5_Touch touch Touch off
But can I use **wacomcpl** and paste this function, instead of a keystroke?
How to do it with **wacomcpl**? Or any other way?

Second question:
In **wacomcpl** what is the difference between this setting:
'Side Switch Only' and 'Side Switch+Tip'

Third question:
In **wacomcpl** the buttons are (from top to bottom) 2,3,4 but the last one I don't know.
There are also references to Left and Right Strip, Up and Down, but Bamboo doesn't have those!
Also I tried to change all Buttons to 'ignore', but still the last button (bottom) always behaves as 'mouse wheel' and, in my case, it will change workplaces (as does Compiz with the mousewheel).
I want to set this last button as 'left click' but I don't know how.
[COLOR="Red"]EDIT: added screenshot[/COLOR]

Fourth question:
After I issue 'xsetwacom set Wacom_Bamboo_4x5_Touch touch Touch off' indeed Touch will be OFF, but a:
'xsetwacom set Wacom_Bamboo_4x5_Touch touch Touch on' doesn't recuperate Touch.
I will get Touch back if I change to VT1 (Alt+Ctrl+F1) and back to Gnome(Alt+Ctrl+F7)
Any ideas about this behavior?

Thanks in advance for your time and patience!

---

### Post by bromalex on 2009-12-02
Hi

In **wacomcpl** I changed buttons 3 and 4 (at least for now, while I am waiting for some info on how to change top and bottom buttons). I also changed Pen>Feel>Tip Sensitivity to 3 (idem to Eraser).

Based on Favux info in this [post]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"), I did these steps that enabled my **wacomcpl** modifications to stick between logouts and reboots.
Turn file executable
```
chmod +x ~/.xinitrc
```
Go to System->Preferences->Startup Applications and click on add and for the command write (with the quotes):
```
sh -c "sleep 8; exec /home/xxxxxx/.xinitrc"
```

Replace xxxxxx with your home name.
Give it a title and test this with a logout/login.
I added the sleep command otherwise it was as if it hadn't run.

Favux! Is it still needed to comment out the file "xinitrc" in "/etc/X11/xinit/" as you wrote?
# invoke global X session script
#. /etc/X11/Xsession

Thanks

[COLOR="Red"]ATTENTION: After more testing I had lots of problems with X, so I dropped this idea and changed to a manual Launcher that I created in gnome-panel to run ~/.xinitrc when I  need it.[/COLOR]

---

### Post by royleith on 2009-12-02
lshal gives me,

  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 2.0 (2) (double)

lsusb gives me 

Bus 004 Device 002: ID 056a:00d3 Wacom Co., Ltd

I've been working through the 'howto' and always get stuck at this point,

roy@laptop:~/linuxwacom-0.8.5-4-35$ sudo ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... configure: error: unsafe absolute working directory name

Any idea how I can get this to work? Perhaps I need to start up as root.

Regards
Roy Leith

---

### Post by sphh on 2009-12-02
Hi everybody,

Thanks for the wonderful work you've done already!

Here is my success with the Bamboo Pen & Touch, CTH-461:
```

$ lsusb
Bus 005 Device 002: ID 056a:00d2 Wacom Co., Ltd 

```I followed the wonderful step-by-step guide by [Ayuthia]("http://swiss.ubuntuforums.org/member.php?u=286983") to the point going for option A.

[LIST]
[*] I use the **original** 10-linuxwacom.fdi (for reasons I'll explain later).
[*]I have a **left**-handed mouse.
[*]I use Ubuntu Karmic.
[/LIST]
Here is what works (and what does not work):

:)
 
[LIST]
[*]**Pen** works (position and buttons)
[*]**Eraser** works (position and buttons)
[*]**Buttons** along tablet work (that is, I can assign commands to them)
[*]**Touch** works in "Absolute" mode (as long as I never change the mode)
[/LIST]
 :|

[LIST]
[*]**Scrolling Gesture** works, but very slow. (IMHO in the right way: When I move the fingers down, the page moves down - think grabbing the page and move it under the window.)
[/LIST]
 :(
 
[LIST]
[*]**Touch** does not work in "Relative" mode.
[*] I have to reassign all pen and eraser buttons to work as expected (mainly swapping buttons 0 and 2). I assume this is due to my left handed mouse. Would it be possible to simulate not mouse clicks but to issue the correct events?
[*] I cannot reassign the button which is clicked when I touch the pad with my finger. I always get the context sensitive menu, regardless of 'xsetwacom set touch Button1 "Button 3"'.
[*] I cannot rotate the pad. Neither with [http://ubuntuforums.org/showpost.php?p=8360124&postcount=558](http://ubuntuforums.org/showpost.php?p=8360124&postcount=558), nor with 'xsetwacom set stylus Rotate HALF'.
[*]The pen never opens an autohidden panel in Gnome. The cursor stops one or two pixels short of the edge of the screen.
[/LIST]
 :?

[LIST]
[*] I cannot figure out how the toggle the touch feature. The only command I found is 'xsetwacom set touch Touch on/off'. So I need one button for switching off, another one for switching on again.
[/LIST]

Whenever I use Favux_new-generic_test3.5_10-linuxwacom.fdi from [http://ubuntuforums.org/attachment.php?attachmentid=137218&d=1258919694](http://ubuntuforums.org/attachment.php?attachmentid=137218&d=1258919694) I get the following problem:

[LIST]
[*]In touch mode the cursor is trapped in an area approximately 1/9th of the screen. This area is located in the upper left corner of the screen. It's possible to address the whole screen with the pen.
[/LIST]

I hope this helps. If anybody wants to see some logs, please feel free to ask. I am happy to collect and send them but don't want to fill the forum with useless data.

Thanks!
Stephan

---

### Post by Favux on 2009-12-02
Hi Stephan,

Sounds pretty good!

> I cannot rotate the pad. Neither with [http://ubuntuforums.org/showpost.php...&postcount=558](http://ubuntuforums.org/showpost.php...&postcount=558), nor with 'xsetwacom set stylus Rotate HALF'.
Right now rotation is broken in 0.8.5-4 and unfortunately in 0.8.5-5 which came out yesterday.  So you lefties are temporarily out of luck.

```
In touch mode the cursor is trapped in an area approximately 1/9th of the screen. This area is located in the upper left corner of the screen.
```
I don't recall anyone to reporting that type of behavior with the newer patches.  I'm not sure why that's happening for you.

Touch toggling requiring two buttons is definitely a problem.  You might want to look at "6) Turning touch on and off" on this [HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1") for some ideas.

---

### Post by brabender on 2009-12-02
> **kgingeri said:**
> I can only think of three things (BTW your english is very good!):
[LIST=1]
[*] did you reboot after all installs and copies?
[*] use the fdi [here]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579") post #579
[*] do you have more than one 10-linuxwacom.fdi file defining wacom stuff in the /usr/share/hal/fdi/... directory - or did you not rename an original to that name?
[/LIST]

Yes, I've rebooted. Also, the fdi is that one, or at least had the same name before copying an renaming it, and it's the only .fdi file in that directory that contains wacom references, I renamed the original file to .xxx  

By the way, I'm running Jaunty, so I skipped commands only meant for Karmic from first post of the thread. Reading it again, I've noticed that there is an advice to follow instructions in post #541, but it says that this one has just pen working, no touch, and it's two weeks old; first post was edited one week ago.

---

### Post by kgingeri on 2009-12-02
> **brabender said:**
> Yes, I've rebooted. Also, the fdi is that one, or at least had the same name before copying an renaming it, and it's the only .fdi file in that directory that contains wacom references, I renamed the original file to .xxx  

By the way, I'm running Jaunty, so I skipped commands only meant for Karmic from first post of the thread. Reading it again, I've noticed that there is an advice to follow instructions in post #541, but it says that this one has just pen working, no touch, and it's two weeks old; first post was edited one week ago.

Hi, if you only renamed the original file AND left it in the same directory then it could be that it is still getting picked up.  I'd move it to your home folder.  

You are right about #541 - it is getting old now.  Linuxwacom also seems like a bit of a moving target right now (0.8.5-5 came out yesterday) so we may have to wait that out a bit. Not sure what to tell you - maybe it time to upgrade?!  Possibly retrace steps very carefully or use Ayuthia's option B if you used A first - or visa versa?  :/

---

### Post by brabender on 2009-12-03
> **kgingeri said:**
> Hi, if you only renamed the original file AND left it in the same directory then it could be that it is still getting picked up.  I'd move it to your home folder.  

You are right about #541 - it is getting old now.  Linuxwacom also seems like a bit of a moving target right now (0.8.5-5 came out yesterday) so we may have to wait that out a bit. Not sure what to tell you - maybe it time to upgrade?!  Possibly retrace steps very carefully or use Ayuthia's option B if you used A first - or visa versa?  :/

Reading a post from Favux in another thread, I've seen that the name of the .fdi file is not the same in Jaunty and in Karmic, and I was using the wrong one. I renamed it and I moved the old .fdi to my home directory. It works like before, no eraser.

Also, I've noticed that files in my /var/log like syslog, debug and kern.log are being filled with messages concerning the tablet. Each one is now about 40 MB of size, and it seems that every time I move the pen on the tablet it writes debugging info, like this:

Dec  3 11:12:56 sobremesa kernel: [ 6192.880615] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->pktlen = 20
Dec  3 11:12:56 sobremesa kernel: [ 6192.880622] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->name = Wacom Bamboo 4x5 Touch
Dec  3 11:12:56 sobremesa kernel: [ 6192.880626] [wacom-34] data: 02 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Dec  3 11:12:56 sobremesa kernel: [ 6192.880667] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_wac.c: touch_out idx=0
Dec  3 11:12:56 sobremesa kernel: [ 6192.880676] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_wac.c: touch_out idx=1
Dec  3 11:12:56 sobremesa kernel: [ 6193.116631] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->pktlen = 20
Dec  3 11:12:56 sobremesa kernel: [ 6193.116637] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->name = Wacom Bamboo 4x5 Touch
Dec  3 11:12:56 sobremesa kernel: [ 6193.116641] [wacom-34] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Dec  3 11:12:56 sobremesa kernel: [ 6193.140630] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->pktlen = 20
Dec  3 11:12:56 sobremesa kernel: [ 6193.140635] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->name = Wacom Bamboo 4x5 Touch
Dec  3 11:12:56 sobremesa kernel: [ 6193.140639] [wacom-34] data: 02 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Dec  3 11:12:56 sobremesa kernel: [ 6193.140675] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_wac.c: touch_out idx=0
Dec  3 11:12:56 sobremesa kernel: [ 6193.140683] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_wac.c: touch_out idx=1
Dec  3 11:12:56 sobremesa kernel: [ 6193.484661] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->pktlen = 20
Dec  3 11:12:56 sobremesa kernel: [ 6193.484667] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->name = Wacom Bamboo 4x5 Touch
Dec  3 11:12:56 sobremesa kernel: [ 6193.484671] [wacom-34] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 



and so on. Any thoughts?

---

### Post by royleith on 2009-12-03
Please ignore my problem in post #630 with the 

./configure --enable-wacom --prefix=/usr

stage. I think I had the folder buried too deep in the directory. Bringing it up to my /home folder solved the problem. Don't go too far, though. I haven't got to the end of the process, yet!

Regards
Roy Leith

---

### Post by royleith on 2009-12-03
It works!

Bus 004 Device 002: ID 056a:00d3 Wacom Co., Ltd

Default Wacomcpl Settings

Wacom_Bamboo_6x8_Touch: No Settings

Wacom_Bamboo_6x8_Touch_pad

Button1: left   Button2: Middle   Button3: Right   Button4: Fourth
Left Strip Up:   Fourth   Right Strip Up: Fourth
Left Strip Down: Fifth    Right Strip Down: Fifth

Wacom_Bamboo_6x8_Pen

Feel 6,1,4,2 
Tracking Top 0,0 Bottom 21640, 13530
The pen matches the screen, exactly in 'Absolute' mode with these default settings.

Tool Buttons
Button1: Left   Button2: Middle   Button3: Right
Side Switch Mode: Side Switch + Tip
Position Mode: Absolute   Screen Mapping: None

Wacom_Bamboo_6x8_Pen_eraser
Feel: 6.1.4.2

Tool Buttons
Button 1: Left   Positioning Mode: Absolute    Screen Mapping: None


There is no Touch configuration for Absolute and Relative Modes

The two finger scroll works (up scrolls UP), but it works in absolute mode even though touch is set to relative mode. Each time one returns to the bottom of the screen, the display instantly scrolls back to its former position.

I have enabled pen mode and eraser mode in Gimp, but the eraser mode works as a pen and does not erase. I think I remember the same problem with my serial Intuos1 so I am not too surprised.
Both work in pressure sensitive mode. To be honest, it is the pen mode that is most important to me so I am very happy. The screen mapping will not be used as I don't use dual screen mode on my laptop.

I discovered, by accident, that zoom-in and zoom-out work as long as the two-finger expand and contract movements are in the vertical plane.

Unplugging and plugging in the USB connection makes the 'Touch' cursor fly to the bottom-right of the screen. It can be moved away, but soon flicks back.

Using,
xsetwacom set Wacom_Bamboo_6x8_Touch touch Touch off

Turns the Touch mode 'Off' which is a really important feature for me. Turning it back on does not work. Unplugging and plugging it in restores the 'Touch' mode, but with the problem mentioned. above.

As reported, elsewhere, the 'Rotate' function is not implemented.

All in all it is all very promising

Regards
Roy Leith

---

### Post by dnprossi on 2009-12-03
> **royleith said:**
> It works!


Try using fdi on post [#579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579")

download it and copy file:

```

sudo cp Favux_new-generic_test3.5_10-linuxwacom.fdi.txt /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

```

Reboot after copy things should be a little better.

Plug/unplug is not solved yet in drivers..
Only mal function is plug/unplug that goes nuts but settings are a little easyer.

To my understanding Wacom_Bamboo_6x8_Touch Wacom_Bamboo_Craft etc are old series tablet and will not work correctly...

---

### Post by royleith on 2009-12-04
> **dnprossi said:**
> Try using fdi on post [#579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579")


I thought i had done that, but after making sure, Gimp preferences are working differently. However, erase still works like the pen tip.

> **dnprossi said:**
> Plug/unplug is not solved yet in drivers..
Only mal function is plug/unplug that goes nuts but settings are a little easyer.

To my understanding Wacom_Bamboo_6x8_Touch Wacom_Bamboo_Craft etc are old series tablet and will not work correctly...

This model is called the Bamboo Fun Medium and is one of the latest models.

Regards
Roy Leith

---

### Post by bromalex on 2009-12-04
> **brabender said:**
> 
Also, I've noticed that files in my /var/log like syslog, debug and kern.log are being filled with messages concerning the tablet. Each one is now about 40 MB of size, and it seems that every time I move the pen on the tablet it writes debugging info, like this:

Dec  3 11:12:56 sobremesa kernel: [ 6192.880615] /home/antonio/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: and so on. Any thoughts?

Hi
Thank you brabender for calling our attention to this.
I checked my laptop and my logs are 798 MB, 709 MB, 442 MB and 264 MB !!!!:o

I need to regain control of my computer !!

It seems that there is a debug option turned on which is causing this.

**ob1kenobi**, since I'm using your file can you confirm this? Or is it something else.

Thanks

---

### Post by Favux on 2009-12-04
Hi bromalex and brabender,

It's test code not working code and Ayuthia has debug lines in it.  That's why you are seeing all that in your logs.  The idea is to post relevant parts of your logs for bugs you are encountering.

---

### Post by bromalex on 2009-12-04
> **Favux said:**
> Hi bromalex and brabender,

It's test code not working code and Ayuthia has debug lines in it.  That's why you are seeing all that in your logs.  The idea is to post relevant parts of your logs for bugs you are encountering.

Thanks Favux

Is it possible to turn this option off?

---

### Post by Ayuthia on 2009-12-04
> **bromalex said:**
> Thanks Favux

Is it possible to turn this option off?

You should be able to turn some of it off by going into src/2.6.28/wacom_wac.c and src/2.6.28/wacom_sys.c and look for:
```
#define DEBUG 1
```
in the first few lines of the code.  Replace it with:
```
#define DEBUG 0
```and then recompile it.

ob1kenobi has some dbg commands in there and I am not for sure if they are showing up or not for you.  If you see anything like:
```
"wacom->wacom_wac->features->pktlen = 
```then you are getting the dbg information.  If you are getting that, then we will need to update the code so that it will not always show up.

---

### Post by bromalex on 2009-12-04
Dear Ayuthia

Thank you. I'll try this.

Edit: I checked and I do have that dbg information in the logs.

Victor

PS: Congratulations and I whish you and your family (particularly the little one) all the happiness :D

---

### Post by marek_online on 2009-12-05
Ayy! Congratulations Aythia! All the best.

---

### Post by dnprossi on 2009-12-05
Dear Ayuthia, Congratulations!!!!!

> **royleith said:**
> I thought i had done that, but after making sure, Gimp preferences are working differently. However, erase still works like the pen tip.


Hi royleith,
To get eraser to work in gimp you need to turn stylus and click on the eraser icon in the **tool box**. You can assign anything in the tool box to stylus eraser, also different brush. Thats gimp functionality, no driver bug...

Cheers...

---

### Post by royleith on 2009-12-05
> **dnprossi said:**
> 
To get eraser to work in gimp you need to turn stylus and click on the eraser icon in the **tool box**. You can assign anything in the tool box to stylus eraser, also different brush. Thats gimp functionality, no driver bug...

Cheers...

I found that when I clicked the stylus on erase, the eraser stayed on brush. I had just come back to the forum to see if anyone could explain it.

Anyway, many thanks for your reply. That is a very powerful feature and means that the Wacom is just what I hoped for in Linux.

It's my turn, now.

Dear Ayuthia, Congratulations!!!!!

Regards
Roy Leith

---

### Post by djurny on 2009-12-05
> **Ayuthia said:**
> You should be able to turn some of it off by going into src/2.6.28/wacom_wac.c and src/2.6.28/wacom_sys.c and look for:
```
#define DEBUG 1
```
in the first few lines of the code.  Replace it with:
```
#define DEBUG 0
```and then recompile it.

ob1kenobi has some dbg commands in there and I am not for sure if they are showing up or not for you.  If you see anything like:
```
"wacom->wacom_wac->features->pktlen = 
```then you are getting the dbg information.  If you are getting that, then we will need to update the code so that it will not always show up.

that wont work, code has 
```
#ifdef DEBUG
``` in it ;) you should comment out the entire ```
#define DEBUG 1
``` line in order to prevent the generous amount of debug logging :)

---

### Post by milkfish on 2009-12-05
Updated from  linux-image-2.6.31-15-generic to linux-image-2.6.31-16-generic today and after the reboot my CTL-460 was not working. Of course it is because every time the kernel version changes, one has to redo the last part of the install.

As root, in the linuxwacom-0.8.4-3 directory:
```

./configure --enable-wacom --prefix=/usr
cp /lib/modules/2.6.31-15-generic/build/drivers/hid/hid-ids.h /lib/modules/2.6.31-16-generic/build/drivers/hid/
make
make install
cp src/2.6.31/wacom.ko /lib/modules/2.6.31-16-generic/kernel/drivers/input/tablet/
insmod /lib/modules/2.6.31-16-generic/kernel/drivers/input/tablet/wacom.ko 
depmod -e

```And now it's working again. I guess this will work, as a script, until they hit 2.6.32 and beyond, at which point we might need a new linuxwacom tarball to work from.

---

### Post by Favux on 2009-12-05
Hi djurny,

Which in C would be:
```
// #define DEBUG 1
```
correct?

---

### Post by djurny on 2009-12-05
> **Favux said:**
> Hi djurny,

Which in C would be:
```
// #define DEBUG 1
```
correct?

well to be completely accurate; thats a c++ comment, but it will also do :)

[SIZE="1"]```
/* #define DEBUG 1 */
``` is a c comment..[/SIZE]

---

### Post by Favux on 2009-12-05
Thanks, I never keep that straight.

---

### Post by Ayuthia on 2009-12-05
> **djurny said:**
> that wont work, code has 
```
#ifdef DEBUG
``` in it ;) you should comment out the entire ```
#define DEBUG 1
``` line in order to prevent the generous amount of debug logging :)

Thanks for pointing that out.  I did not look at the code that closely and the lack of sleep did not help that much either.

Thanks everybody for the kind wishes!  The little one and mom are doing well but he doesn't realize that we all like to sleep every once in a while.  Too bad he wasn't born on 11.10 or 11.04.  I could have named him in the same way as the Ubuntu naming scheme (like Lucid Lynx).  I doubt that my wife would let me get by with something like that though...

---

### Post by 289Shelby on 2009-12-06
Has anyone managed to get a Bamboo pen working with Hardy 8.04 with the 2.6.24-26 kernel on a desktop?

I've read through all the HOW-TO's and tried the fixes but have been unable to get any kind of response from the tablet whatsoever. I'm probably missing something simple but frustration is starting to get the better of me.

Thanks to anyone who might be able to help.

---

### Post by ElaineM on 2009-12-06
Hi,

is it possible to use the patch wcm_2_patch with kernel 2.6.31-15?
I don't know how to do....

---

### Post by Favux on 2009-12-06
Hi everyone,

I posted the new-generic release candidate at [post #579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").  No significant difference for the P & T's.  Except there is a debug version too for testing.

---

### Post by marek_online on 2009-12-07
> **ElaineM said:**
> Hi,

is it possible to use the patch wcm_2_patch with kernel 2.6.31-15?
I don't know how to do....

Hi ElaineM,

Yes, it's possible - I was running the 2.6.31-15 kernel for most of this thread (now running 2.6.31-16 and everything's fine with that too).

You just need to recompile by following the instructions in post #1 as normal, but make sure that you have the linux-headers for the new kernel installed. Do that from your favourite apt GUI or by running this in a terminal:
```
sudo apt-get install linux-headers-2.6.31-15
```

When copying the wacom.ko file after compiling, you'll need to run this to make sure it goes into the right place::
```
sudo cp src/2.6.28/wacom.ko /lib/modules/2.6.31-15/kernel/drivers/input/tablet/
```And run depmod -a and the modprobe commands as normal.

Good luck with it.

---

### Post by TheguywholikesLINUX on 2009-12-07
> **royleith said:**
> I found that when I clicked the stylus on erase, the eraser stayed on brush. I had just come back to the forum to see if anyone could explain it.

Anyway, many thanks for your reply. That is a very powerful feature and means that the Wacom is just what I hoped for in Linux.

It's my turn, now.

Dear Ayuthia, Congratulations!!!!!

Regards
Roy Leith

In gimp, the pen tip, and eraser both behave as two different tools, you can have the pen on the clone tool, and the eraser on the smudge tool, and whenever you turn the pen around it switches tools.
Or you can have the pen on brush with a small brush size, and the eraser also on brush, with a big brush size (I think)
So to get the eraser on eraser you need to turn the pen around so that the eraser is on the tablet, and click on the eraser. (lol, if that makes any sense!) And your pen will stay on what it was on before. Or you could put your pen on eraser, and you eraser on brush even!

---

### Post by ElaineM on 2009-12-07
Ok, thanks, it works.

I still have the problem that a click on the tablet is treated as a right click because I switched my mouse buttons for left-handed use.
How can this be changed?

Is it possible to use the buttons at the moment? How could this be done?

---

### Post by Oenologist on 2009-12-07
I have two identical laptops, both 9.10 (one KDE, one Gnome). I installed the Bamboo effortlessly using the tutorial from the first post. Works absolutely brilliant. 

But!

After a couple of days everything stoped working on both computers. Is it possible that after the kernel update the driver disappeared or something? Is it possible to create a fixed, stable configuration of this driver, or make it loading automatically each time? I'm puzzled.

---

### Post by kgingeri on 2009-12-08
Haven't been on this fast paced thread for a while, and the[SIZE="4"] biggest news[/SIZE] is a _proud dad_!

[SIZE="4"]Congrats Ayuthia!!![/SIZE] :KS

Ok, so the rest looks good too. Gotta redo my install as I've just upgraded the kernel.

---

### Post by dnprossi on 2009-12-08
> **Oenologist said:**
> 
After a couple of days everything stoped working on both computers. Is it possible that after the kernel update the driver disappeared or something?

Hi Oenologist,
Yes, the new kernel overwrites the previously wacom modified one.

> 
Is it possible to create a fixed, stable configuration of this driver, or make it loading automatically each time? I'm puzzled.

Not yet. But you can write a small batch script to help reinstall wacom drivers with just one click.

open gedit copy code and save anyname.sh outside wacom dir. make file executable, run it...

eg. for linuxwacom-0.8.5-4-bamboo-34.tar.bz2 on post #1
```

#!/bin/sh
cd linuxwacom-0.8.5-4/
sudo cp src/2.6.28/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
sudo modprobe wacom

```

For ob1's linuxwacom-0.8.5-4-35.tar.bz2 on post #586
just change line: 
```

sudo cp src/2.6.28/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input

```
to
```

sudo cp src/kernel/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/

```

Reboot in both cases...

---

### Post by marek_online on 2009-12-08
> **ElaineM said:**
> 
I still have the problem that a click on the tablet is treated as a right click because I switched my mouse buttons for left-handed use.
How can this be changed?


You should be able to change those settings by running "wacomcpl". I'm not sure if the changes will stay across reboots though. Maybe someone else could give some guidance on that?

When using wacomcpl, touching on the pad is "Button 1", while the other pad buttons are (from top to bottom, with the pad in "right-handed" orientation - that's wire coming out to the left) Button2, Button 3, Button 4 and the last button I think is actually undefined at the moment, but I could be wrong on that.

With the stylus, Button 1 is the tip and buttons two and three the lower and higher rocker switch. 

wacomcpl will allow you to set these buttons to pretty much whatever you want.

---

### Post by bromalex on 2009-12-08
> **Ayuthia said:**
> 
ob1kenobi has some dbg commands in there and I am not for sure if they are showing up or not for you.  If you see anything like:
```
"wacom->wacom_wac->features->pktlen = 
```then you are getting the dbg information.  If you are getting that, then we will need to update the code so that it will not always show up.

Hi Ayuthia

Would it be possible that, in between some diaper changing ;), you could tell us how to remove that dbg information that is also coming out?
If it is too complicated, never mind, we'll wait.

Thanks




[SIZE="1"]PS: A new upload (0.8.5-6) to Linux Wacom Project ([http://linuxwacom.sourceforge.net/index.php/chg](http://linuxwacom.sourceforge.net/index.php/chg)) From what I gather, still no support to Bamboo Pen&Touch :-(
2009-12-08 Ping Cheng &ltpingc@wacom.com>
    * Merged src/2.6.28 into src/2.6.27 so we have less files to worry
    * Removed src/2.6.28
    * Updated src/2.6.27 to version 1.52 in the kernel tree
    * Support new serial Tablet PCs: 0xE2, 0xE3, and 0x9F. Supported new serial ISDv4 TabletPCs
    * Avoid duplicated and invalid devices and types for X server 1.4 and later
    * Support kernels up to 2.6.32

More News:
[Linuxwacom-devel]From: Enrico Ros - 2009-12-09 14:06
Hello, I just opened a git clone of xf86-input-wacom on Gitorious at:
[http://gitorious.org/linuxwacom/xf86-input-wacom](http://gitorious.org/linuxwacom/xf86-input-wacom)
In this repository I'll try to merge the changes that some people at Ubuntu
Forums did to support newer devices, like the Bamboo Fun. Unfortunately their
patches are 'snapshots based' and don't apply nor work on current xf86-input-
wacom.

[Linuxwacom-devel]From: Enrico Ros - 2009-12-09 17:17
Hello, in the process of merging the work the guys at Ubuntu Forums did, here
is the second patch adding some device IDs mapped to the 'usbBamboo' kind of
tablet. This is fairly trivial but makes my recent Bamboo Fun Pen & Touch
work.
The commit is in the 'for-whot' branch too. You can pull the current (2 atm)
commits with:
git pull git://gitorious.org/linuxwacom/xf86-input-wacom.git for-whot
Enrico[/SIZE]

---

### Post by Favux on 2009-12-10
Hi everyone,

I also had breaking news on Enrico Ros's new [git branch]("http://gitorious.org/linuxwacom/xf86-input-wacom") where he's submitting the patches on this thread for the Bamboo P & T to xf86-input-wacom.  But with the forums down and what not I see bromalex has scooped me.

But what is new and breaking is that Peter Hutterer is accepting the patches!  See Peter's post [here]("http://sourceforge.net/mailarchive/forum.php?thread_name=20091210030554.GC14380%40barra.bne.redhat.com&forum_name=linuxwacom-devel").

---

### Post by bromalex on 2009-12-10
> **Favux said:**
> Hi everyone,

I also had breaking news on Enrico Ros's new [git branch]("http://gitorious.org/linuxwacom/xf86-input-wacom") 
...
But what is new and breaking is that Peter Hutterer is accepting the patches!

Good news indeed. I found that Enrico has bought a Bamboo Fun Pen & Touch so he has also a personal interest that this project moves swiftly, I guess.

As I understood, xf86-input-wacom will replace linuxwacom for the job, so I am curious and hence this question:

How to install software from git?

Any HOW-TO or a simple explanation on how to proceed to try out this new "driver"

---

### Post by munooka on 2009-12-10
I followed post 1 and got my bamboo pen working almost glitch free. However I bought the model specifically for the touch function (bad wrists) and this is very erratic for me. For example when I try two finger scrolling the cursor totally disappears and I have to use the normal mouse (no scrolling either. When the cursor is in the window that is in focus it works fairly well. However once I try to use the window controls all hell breaks loose, the cursor becomes very erratic and click events do not work. This eventually leads to an x input freeze where I can only input or in the focus window (with keyboard, mouse and bamboo). to resolve this I had to remove the bamboo and plug it in again and click the upper button. On doing this the cursor is restricted to the upper left portion of the screen (Looks like the native resolution of the pad (X=480 Y=320). Trying to switch the touch on and off through the xsetwacom does not help neither does using relative. The pen works even well.
I would really love to help getting the touch usable on my system as it looks like the ideal solution for my sore wrists.

---

### Post by Iuly on 2009-12-13
Hello again! As I said in an older post I have a Wacom Bamboo Pen. (Bus 002 Device 004: ID 056a:00d4 Wacom Co., Ltd ) I downloaded the linuxwacom-0.8.4-4 ,  unpacked, and all was going well untill the "make install " step. 
This is the error message :

[COLOR=Navy]iulda@iulda-desktop:~/Escritorio/linuxwacom-0.8.4-4$ make install
Making install in src
make[1]: se ingresa al directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
Making install in .
make[2]: se ingresa al directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[3]: se ingresa al directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[3]: No se hace nada para `install-exec-am'.
test -z "/usr/local/share/man/man4" || /bin/mkdir -p "/usr/local/share/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/local/share/man/man4/wacom.4x.gz'
/usr/bin/install: no se puede borrar «/usr/local/share/man/man4/wacom.4x.gz»: Permiso denegado
make[3]: *** [install-wmanpageHEADERS] Error 1
make[3]: se sale del directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[2]: *** [install-am] Error 2
make[2]: se sale del directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[1]: *** [install-recursive] Error 1
make[1]: se sale del directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make: *** [install-recursive] Error 1
iulda@iulda-desktop:~/Escritorio/linuxwacom-0.8.4-4$ 

:(

[/COLOR]

---

### Post by marek_online on 2009-12-13
> **Iuly said:**
> Hello again! As I said in an older post I have a Wacom Bamboo Pen. (Bus 002 Device 004: ID 056a:00d4 Wacom Co., Ltd ) I downloaded the linuxwacom-0.8.4-4 ,  unpacked, and all was going well untill the "make install " step. 
This is the error message :

[COLOR=Navy]iulda@iulda-desktop:~/Escritorio/linuxwacom-0.8.4-4$ make install
Making install in src
make[1]: se ingresa al directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
Making install in .
make[2]: se ingresa al directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[3]: se ingresa al directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[3]: No se hace nada para `install-exec-am'.
test -z "/usr/local/share/man/man4" || /bin/mkdir -p "/usr/local/share/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/local/share/man/man4/wacom.4x.gz'
/usr/bin/install: no se puede borrar «/usr/local/share/man/man4/wacom.4x.gz»: Permiso denegado
make[3]: *** [install-wmanpageHEADERS] Error 1
make[3]: se sale del directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[2]: *** [install-am] Error 2
make[2]: se sale del directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make[1]: *** [install-recursive] Error 1
make[1]: se sale del directorio `/home/iulda/Escritorio/linuxwacom-0.8.4-4/src'
make: *** [install-recursive] Error 1
iulda@iulda-desktop:~/Escritorio/linuxwacom-0.8.4-4$ 

:(

[/COLOR]
Hi Luly.

From what you posted here, it looks like you ran "make install" as a normal user. You need to run it as superuser, like this:

```
sudo  make install
```

---

### Post by Lucretia9 on 2009-12-14
Ok, got it all compiled, I can only repeat what other's have stated already:

[list]
[*] Touch is jerky (not really usable for me yet)
[*] Eraser in gimp doesn't work unless I select eraser (which seems to be pointless)
[*] Can turn touch on/off
[*] Unplugging and plugging in the bamboo causes the touch to only use a small portion of the screen and the resolution is tiny (i.e. it's got slow movement)
[*] Can see the various interfaces in wacomcpl
[/list]

```

$ uname -a
Linux rogue 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

```

Using Favux_new-generic_test3.5_10-linuxwacom.fdi.txt

Thanks,
Luke.

---

### Post by bromalex on 2009-12-14
Hi Luke

In GIMP use the eraser side of the pen and select Gimp's Eraser Tool. Now turn pen to stylus side and select Airbrush Tool (for ex.)

Start drawing and then try to use the pen's eraser side to erase. It should work.

I agree that touch is still not usable. That's why I always disable it with my custom Panel Launcher.
Still sometimes when you touch with your hand the tablet as you approach the pen, a few strokes can appear (even if you still haven't pressed the pen against the tablet's surface).

But I am grateful for the great job done here. It'll do while we wait the final version. :)

---

### Post by Favux on 2009-12-14
Hi bromalex,

I don't totally know the answer to your git question, but since no one has answered you yet, here are some links which you may already have.

xf86-input-wacom:
[http://cgit.freedesktop.org/~whot/xf86-input-wacom/commit/?id=xf86-input-wacom-0.10.2](http://cgit.freedesktop.org/~whot/xf86-input-wacom/commit/?id=xf86-input-wacom-0.10.2)
[http://cgit.freedesktop.org/~whot/xf86-input-wacom/tag/?id=xf86-input-wacom-0.10.2](http://cgit.freedesktop.org/~whot/xf86-input-wacom/tag/?id=xf86-input-wacom-0.10.2)
[http://cgit.freedesktop.org/~whot/xf86-input-wacom/](http://cgit.freedesktop.org/~whot/xf86-input-wacom/)

And online git books:
By one of the original dev.s:  [http://progit.org/](http://progit.org/)

[http://book.git-scm.com/](http://book.git-scm.com/)

Hope this is helpful.

Edit:  I found the merger plan and instructions for using the git and here they are:  [http://old.nabble.com/linuxwacom-and-xf86-input-wacom-plan-td25760339.html](http://old.nabble.com/linuxwacom-and-xf86-input-wacom-plan-td25760339.html)

---

### Post by bromalex on 2009-12-15
> **Favux said:**
> Hi bromalex,
...
Hope this is helpful.

Thank you so much Favux.

I am in for a lot of reading, it looks ;)

---

### Post by royleith on 2009-12-15
Favux,

I wonder if you might be able to help. I have (after some daft errors) managed to install using the 0.8.5-4-35 fileset and then again after a kernel upgrade. I restored the previous version of Karmic from a backup after an attempt to get irda working (don't ask!) left me with an unstable installation. I upgraded to the latest kernel and files and then tried to reinstall the bamboo drivers. I tried several times doing the make clean and make distclean before each attempt. Then I tried the install with the pre-patched file at the start of this thread. In all cases I get a whole stream of 'make' errors starting with,

In file included from wacomcfg.c:36:                                                                                                         
wacomcfg.h:26:22: error: X11/Xlib.h: No such file or directory         

Everything up to that point seems to work as originally. I have installed or reinstalled all of the referenced hal, wacom and xserver files and always sudo myself into superuser mode for each line just in case.

Any idea why, after two successful installs, the process now seems to fail?

Regards
Roy Leith

---

### Post by yellowbosch on 2009-12-15
Hello all,
I'm having the same problem...after a kernel update wacom stoped working...installed xubuntu64 again and I can't install wacom like the first time....any ideas?
thanks,

---

### Post by Lucretia9 on 2009-12-15
> **yellowbosch said:**
> Hello all,
I'm having the same problem...after a kernel update wacom stoped working...installed xubuntu64 again and I can't install wacom like the first time....any ideas?
thanks,

You need to reinstall as the original (kernel) driver will have been reinstalled along with the new kernel.

Luke.

---

### Post by bromalex on 2009-12-15
**_HOW-TO GET RID OF DEBUG INFO IN /var/log/ FILES_**

> **bromalex said:**
> Hi Ayuthia
Would it be possible that, in between some diaper changing ;), you could tell us how to remove that dbg information that is also coming out?
If it is too complicated, never mind, we'll wait.
Thanks


Hi
I decided to try myself some debug code cleaning (must warn you that I did it based on [_Ayuthias_]("http://ubuntuforums.org/showpost.php?p=8441824&postcount=643")'s hint, on a post by [_tyranos_]("http://ubuntuforums.org/showpost.php?p=8481235&postcount=638") and some intuition. I don't think I broke anything, but ... )

The reason is, otherwise your /var/log/ messages syslog debug and kern.log files will grow enormously as debug info is produced while you use your tablet.

So, before installation I used **gedit** to alter **linuxwacom-0.8.5-4-35**:

I edited src/kernel/wacom_wac.c and commented (add **/*** and ***/** so everything in between will be disregarded at compilation time) the following:

/* #define DEBUG 1
next 6 lines
*/

and also the following **dbg** commands at lines:

178, 200, 227, 232, 236, 243, 251, 261, 268, 292-305 (ifdef DEBUG loop), 405, 409, 413 and 424.

I repeated for src/kernel/wacom_sys.c:

/* #define DEBUG 1
next 6 lines
*/

and the following **dbg** commands at lines:

97, 102, 103, 117, 249, 255, 417, 434, 436, 439-444 (ifdef DEBUG loop), 446, 481, 485-491 (ifdef DEBUG loop), 522, 528, 534, 544, 686 and 687.

I then installed based on Ayuthia's post#1 instructions with the above modified linuxwacom-0.8.5-4-35 from [_ob1kenobi_]("http://ubuntuforums.org/showpost.php?p=8376047&postcount=586") and Favux latest [_10-linuxwacom.fdi_]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").

PS: the reason I am writing this is because **tyranos **commented some **printk **commands, but I could not find them in 0.8.5-4-35.
If someone needs, I could attach the 2 modified files.

Bye

[COLOR="Blue"]EDIT: For those who asked, after you decompress linuxwacom-0.8.5-4-35 replace the originals with these 2 modified files that I now attach, where the changes above are already done.
[/COLOR]
[COLOR="SeaGreen"][SIZE="1"]If you want to use linuxwacom-0.8.5-4-34 modify the files as following:
wacom_wac.c:

/* #define DEBUG 1
next 6 lines
*/

and also the following **dbg** commands at lines:

178, 200, 227, 228, 233, 283-295 (ifdef DEBUG loop), 395, 399, 403 and 414.

And wacom_sys.c:

/* #define DEBUG 1
next 6 lines
*/

and the following **dbg** commands at lines:

93, 98, 99, 113, 214-220 (all lines), 384, 401, 403, 405-411 (ifdef DEBUG loop), 413, 448, 452-458 (ifdef DEBUG loop), 489, 495, 501, 511, 636 and 637.[/SIZE][/COLOR]

---

### Post by Favux on 2009-12-15
Hi royleith,

It looks like you don't have libx11-dev installed.  It should place Xlib.h in "/usr/include/X11/Xlib.h".  I guess due to your reinstall.  You could install it (libx11-dev) through Synaptic Package Manager.

I looked at Ayuthia's HOW TO up front and I guess it assumes you have the development tools installed.  Since you've reinstalled Karmic you might want to run these commands:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade
```
so your reinstall has everything.

---

### Post by royleith on 2009-12-16
@ Favux,

YES!!! 

I have not tried the tablet out yet, but the install went fine after that. Many thanks. 

You have neatly avoided a huge follow-on message of all the things I uninstalled and reinstalled. I even had a go at running that line of Ayuthia's with build-install in it, but got error messages the first time around.

Got to go, now, and back up my Bamboo enabled installation. Many thanks again.

Regards
Roy Leith

---

### Post by Favux on 2009-12-16
Hi royleith,

Good, that sounds like that did it.


Hi everyone,

**Breaking News**:  The Bambo P & T's have been added to linuxwacom!!!
> December 15, 2009 - Updated serial Tablet PCs support. Added 5 new Bamboo tablets support. - kernel patch submitted by K Gingerich. - xorg by Enrico Ros &ltenrico.ros@gmail.com. Label 0.8.5-7.

Also I updated the .fdi to rc2 at [post #579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").

---

### Post by Favux on 2009-12-18
Hi everyone,

Oops!
> Community provided Bamboo support will be merged into the next unstable
release, 0.8.5-8. In fact, we have tried to include it in 0.8.5-7. Somehow
one of the kernel pieces were missing. Let's say you can have it next week.

Ping
So next week or so.

---

### Post by david21 on 2009-12-19
Hi,

Using the instructions in this thread I managed to get my Bamboo Craft working (Thanks!). However, I just noticed that for some reason the tablet is filling my log files (debug, kernel.log and syslog) with messages every time I use it.

This is a problem because my log files are getting huge (2GB+), any ideas how to fix this?

These are the messages that I am getting in the log:
> 
kernel: [24348.480364] /home/david/Downloads/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->pktlen = 9
kernel: [24348.480372] /home/david/Downloads/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->name = Wacom Bamboo Craft Pen
kernel: [24348.480378] [wacom-34] data: 02 80 00 00 00 00 00 00 00 
kernel: [24348.480395] /home/david/Downloads/linuxwacom-0.8.5-4/src/2.6.28/wacom_wac.c: [wacom-34]: reset tool 140
kernel: [24348.480398] 
kernel: [24348.488371] /home/david/Downloads/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->pktlen = 9
kernel: [24348.488380] /home/david/Downloads/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: wacom->wacom_wac->features->name = Wacom Bamboo Craft Pen
kernel: [24348.488387] [wacom-34] data: 02 80 00 00 00 00 00 00 00 
kernel: [24348.488405] /home/david/Downloads/linuxwacom-0.8.5-4/src/2.6.28/wacom_wac.c: [wacom-34]: reset tool 140
kernel: [24348.488408] 

---

### Post by Favux on 2009-12-19
Hi david21,

Welcome to Ubuntu forums!

That's because the patches are for testing and not yet working patches.

See bromalex's [post #677]("http://ubuntuforums.org/showpost.php?p=8504798&postcount=677").  But be careful, Ayuthia just updated the patches today, so make sure what bromalex is telling you to do still applies.

---

### Post by Ayuthia on 2009-12-19
> **Favux said:**
> Hi david21,

Welcome to Ubuntu forums!

That's because the patches are for testing and not yet working patches.

See bromalex's [post #677]("http://ubuntuforums.org/showpost.php?p=8504798&postcount=677").  But be careful, Ayuthia just updated the patches today, so make sure what bromalex is telling you to do still applies.

I have not updated the patches.  I forgot to update the edit message.  I updated the instructions a little bit because I saw a build-dep in the wrong line.  So bromalex's information should still be valid.

I was going to create a patch version that did not contain the debug messages, but it looks like the code is going to be merged into linuxwacom really soon so it might not be necessary.

---

### Post by david21 on 2009-12-20
Thank you very much for your prompt response!

---

### Post by legatek on 2009-12-20
I just got a Pen and Touch CTH-460 and an trying to install it in 64-bit jaunty. I am following the instructions in post 1, but there is no wacom.ko file to copy over after the make install.

find . -name "*.ko"

in the linuxwacom-0.8.5-4 directory returns nothing. How should I proceed?

---

### Post by Favux on 2009-12-20
Hi legatek,

If it isn't in "/src/2.6.28/wacom.ko" and you didn't get any errors then most likely you forgot the "--enable-wacom" in:
```
./configure --enable-wacom --prefix=/usr
```

---

### Post by legatek on 2009-12-20
I am cutting and pasting from the top post, so I'm sure I haven't forgotten anything. However, I notice there are some errors at the end of the make command, which I don't know how to solve.

Output of the ./configure command:

[http://paste.ubuntu.com/343974/](http://paste.ubuntu.com/343974/)

Output of the make command:

[http://paste.ubuntu.com/343975/](http://paste.ubuntu.com/343975/)

---

### Post by Favux on 2009-12-20
Hi legatek,

In your build directory your path is:
```
monkey@monkey-Dell:~/wacom build/linuxwacom-0.8.5-4$ make

```
or
```
make[1]: Entering directory `/home/monkey/wacom build/linuxwacom-0.8.5-4/src'

```
That's not a valid path as you are not allowed a space in "wacom build".  It would have to be "wacom-build" or "wacom_build" or "wacombuild".

---

### Post by legatek on 2009-12-20
Excellent! That fixed it, thank you very much.

---

### Post by mikio on 2009-12-21
How do I permanently disable the touch functionality?

As described early in the post this disables it on the fly:

xsetwacom set touch Touch off

However, how can I set it to off permanently. I figure it should be in the fdi file - right? 

I tried putting it in the .xinitrc file and starting that script automatically on login. However, that does not work when I plug the tablet in later. So it is not the right way to do it..

Many thanks for any hints,
miki

---

### Post by Favux on 2009-12-21
Hi miki,

It should be:
```
<merge key="input.x11_options.Touch" type="string">off</merge>
```
Add it to the touch section of the .fdi so it looks like:
```
  <!-- for most Wacom USB tablets with touch -->
  <device>
    <match key="input.originating_device" contains="if1">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">touch</merge>
        <merge key="input.x11_options.Touch" type="string">off</merge>
        <!-- for Bamboo Pen & Touch tablets -->
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
```

---

### Post by mikio on 2009-12-21
Thank you very much! Not just for this, but for all the work put in - it is very much appreciated!

---

### Post by Favux on 2009-12-21
Hi miki,

Thank you for the thank you.  But the real work was put in by Ayuthia, obe1knobe, prefkits and all the testers.

---

### Post by nocentis on 2009-12-22
hey
When can I expect the drivers to the wacom touch & fun?

---

### Post by TheguywholikesLINUX on 2009-12-22
Ok, I had a new kernel installed, and I've finally gotten round to installing the wacom drivers again!
I used obi1kenobi's patch from post #586 and I used the .fdi at the end of Ayuthia's first post, and followed the instructions there too. Without rebooting, the pen works, have not tried pressure sensitivity yet, but buttons work, touch works (for moving, I switched to relative because I don't like absolute and relative is more precise) but tapping the touch pad still does not work :( putting 2 fingers on the touch pad, stops the mouse from moving, and occasionally causes it to jump to the bottom right hand corner, as with a tap.
I found it quite hard to get the mouse cursor to the very top left pixel, or bottom right for that matter, but this can easily be fixed with a tweak in wacomcpl that gives you a bit more room around the edges.

---

### Post by Favux on 2009-12-23
Hi everyone,

**[SIZE="2"]Breaking News:[/SIZE]**  A holiday present from Ping Cheng at the LWP.  :D

Linuxwacom 0.8.5-8 has been released!!!  Rotation is fixed and hopefully the Bamboo P & T patches are now working.

So you lefties can now rotate your tablets HALF.  There is a little quirk with touch, at least on my tablet.  It's a little misaligned on rotation and the cursor jumps several cm.s when the finger is lifted.  But it hops right back when you touch the tablet again.  It's being looked at.

I'm interested in hearing if it works for you.  See the linuxwacom [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

**[SIZE="3"]Notice:[/SIZE]**  linuxwacom 0.8.5-8 does not work for the P & T.  Because of the rapid changes in the driver with the merger with Xorg's x86f driver there were some incompatible kernel changes among other things.  This is being looked at.

---

### Post by munooka on 2009-12-23
I tried Linuxwacom 0.8.5-8 (hopefully) following your instructions. The device is recognised but there is no response from buttons, touch or pen.

Here is the output from my dmesg:

[  689.222156] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input12
[  689.234837] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input13
[  689.240789] usbcore: registered new interface driver wacom
[  689.240794] wacom: v1.52-pc-0.1:USB Wacom tablet driver

Any ideas?

EDIT: Well it looks like the device is not recognized in xinput:

"stylus"	id=7	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1

AND xsetwacom list produces two stylus entries with no touch, eraser or pen

stylus     stylus

Here is the lsusb info:
Bus 005 Device 003: ID 056a:00d1 Wacom Co., Ltd 


 
> **Favux said:**
> Hi everyone,

**[SIZE="2"]Breaking News:[/SIZE]**  A holiday present from Ping Cheng at the LWP.  :D

Linuxwacom 0.8.5-8 has been released!!!  Rotation is fixed and hopefully the Bamboo P & T patches are now working.

So you lefties can now rotate your tablets HALF.  There is a little quirk with touch, at least on my tablet.  It's a little misaligned on rotation and the cursor jumps several cm.s when the finger is lifted.  But it hops right back when you touch the tablet again.  It's being looked at.

I'm interested in hearing if it works for you.  See the linuxwacom [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Favux on 2009-12-23
Hi munooka,

Don't worry about the double stylus in xsetwacom, that's normal.  You should have the stylus working from what you've shown.  Did you use the rc2 or test3.5 .fdi?  They are in [post #579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").

---

### Post by munooka on 2009-12-24
Well I tried the fdi with the compile, rc2 and 3.5 but still my Bamboo CTH-460 touch and pen do not work with 0.8.5-8. Do I need to use the 60-wacom.rules? Using the patched version and the method in post 1, I had touch, eraser, pad and stylus options I think.

---

### Post by Favux on 2009-12-24
Hi munooka,

Hmmm.  It sounds like the compile and install of 0.8.5-8 went OK without errors for you.  Certainly stylus is being seen by xinput and xsetwacom.  The one thing I can think of that could give symptoms like you describe is if you forgot to copy the newly compiled wacom.ko into place.  So the dmesg would be from the previous wacom.ko?

Could you try repeating that step?  Remember the wacom.ko will be in the 2.6.27 folder so you use the Intrepid copy command.

The other option is 0.8.5-8 still doesn't support the P & T's.  Maybe having the same glitch as in 0.8.5-7.  Or a new one?  I'm pretty sure Ping thinks it supports the P & T's because I told him I'd notify the P & T threads.  So I doubt there's a misunderstanding.

The .fdi with the compile is rc2.  I submitted it and Ping accepted it and included it in 0.8.5-8.

---

### Post by munooka on 2009-12-24
I redid the step and then reloaded the wacom module still no joy.
Here are the outputs from dmesg:
sudo modprobe -r wacom
[ 2804.453781] usbcore: deregistering interface driver wacom
sudo modprobe wacom
[ 2850.142460] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input16
[ 2850.155205] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input17
[ 2850.162139] usbcore: registered new interface driver wacom
[ 2850.162144] wacom: v1.52-pc-0.1:USB Wacom tablet driver

---

### Post by Favux on 2009-12-24
Hi munooka,

It sure seems like you have usb communication with your tablet.

Let's look at your Xorg.0.log.  It's in "/var/log/".  Right click on it and compress it with Create Archive.  Then attach it to your next post with Manage Attachments.

---

### Post by munooka on 2009-12-24
OK here are the Xorg data.

---

### Post by Favux on 2009-12-24
Hi Hi munooka,

Well that's bizarre.  There are multiple attempts to attach by linuxwacom which repeatedly fail.

Do you have more than one wacom.fdi?  There should be only one, but I keep seeing a debug level 12 suggesting you have at least a debug .fdi installed.  I really just want to see rc2 or 3.5 without the extra debug lines.

Do you have touch turned off?  My understanding is one of the button pairs toggles touch on and off and the other pair is left and right mouse click?  Or a .fdi with touch off?

Given all the 'xf86's' I see it does look like 0.8.5-8 is installed.  When you compiled did you do the purge line?

---

### Post by munooka on 2009-12-24
Do you mean:

sudo apt-get install wacom-tools xserver-xorg-input-wacom

sudo apt-get purge wacom-tools xserver-xorg-input-wacom

If so I did this prior to:

sudo make install

---

### Post by Favux on 2009-12-24
Hi munooka,

Ok, and you're telling me there is only one wacom.fdi in "/usr/share/hal/fdi/policy/20thirdparty/"?  And it is not a debug version?

Could I see your lshal?:
```
lshal>munooka_lshal.txt
```
Same instructions to post as Xorg.0.log.

I sure hope we can get some other folks to try with 0.8.5-8 and confirm your negative results.

I'm not eager to tell Ping 1/2 of his Christmas present is missing.  It was pretty awesome the way he tackled the rotation problem in the middle of everything else he's doing and hammered that out in a day for us.

---

### Post by munooka on 2009-12-24
Sorry this is gonna have to wait till tomorrow as I am away from my work machine just now. I am checking the hdd for duplicate wacom stuff just now but cannot test the bamboo till 8AM JST.

---

### Post by Favux on 2009-12-24
Hi munooka and everyone,

Ayuthia has looked at your stuff and it looks like there are two issues.

1)  There was a miscommunication somewhere and the patches in 0.8.5-8 are apparently early versions that only support the pen, not touch or the pad.

2)  Something is wrong with 0.8.5-8 for the P & T because the stylus, stylus button, and eraser should probably be working.  I have an OpenSuse user with the same problem i.e. no response from the tablet.

So unless you want to experiment with 0.8.5-8 you are most likely best off with following Ayuthia's instructions on the first post for now.

Sorry.  :(

---

### Post by munooka on 2009-12-24
OK thanks a lot Favux and Ayuthia, this is a very rapid moving post. 
This explains a lot, any ideas if any of Ayuthia patches can be applied to the new code or should I go back to the previous patched version for now?
I did notice that gedit did put a 10-linuxwacom.fdi~ file in the directory. I forgot about this gedit "feature" and forgot to disable it after installing Koala (I use geany now but copy and pasted the commands). Removing it made no difference to the Bamboo's non-operational state. I don't even know if this file is read.


Seasonal Greetings!

---

### Post by Favux on 2009-12-24
Hi munooka,

> any ideas if any of Ayuthia patches can be applied to the new code
I tend to doubt the patches would apply cleanly.  You'd have to look at each one of them and make sure the changes were correct.  Ayuthia could tell you better.

I'm pretty sure 10-linuxwacom.fdi~ wouldn't be read.

The take home message is that support for the P & T's in linuxwacom is close.

Happy holidays.

---

### Post by Favux on 2009-12-24
Alright, your lshal shows both stylus and touch being set up correctly.  So most likely it is an early patch because you don't see touch in xinput or xsetwacom.

However eraser and pad are not being setup.  Their sections just aren't ther.  I doubt it's a problem with hal-setup-wacom.  My guess is a problem with the code defining sub-devices (tools) for the tablet ID.

---

### Post by scicode on 2009-12-25
first everything worked fine, but after playing around with wacomcpl the stylus mode was set to relative (I think I did not set that). When I tried to open wacomcpl again i got

```
$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/lib ]"                                                                                                                          
Error in startup script: Get: Unknown parameter 'SBottomX8'                                                                                                             
    while executing                                                                                                                                                     
"exec xsetwacom get $dev SBottomX$i "
    (procedure "createScreenList" line 7)
    invoked from within
"createScreenList $dev"
    (procedure "createDeviceList" line 38)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/bin/wacomcpl-exec" line 2042)

```

also setting the mode with xsetwacom did not work

```
xsetwacom set Wacom_Bamboo_Craft_Pen Mode Absolute
X Error: 8 BadMatch (invalid parameter attributes)
```

---

### Post by elmo64 on 2009-12-25
Hello everybody, 
I'm completely new to this forum, 45 years old and from northern Germany. My english is a bit "rusted", so please be patient. 

I just purchased a Bamboo Fun Pen&Touch (Model CTH-461) about 2 weeks ago, and I couldn't get it to work on any of my distris. Right now I'm trying on Linux Mint8 which is, as I understand, based on ubuntu karmic koala. 
I followed the steps fom the first post of this thread, and after executing the "make"-command, there are lots of errors :-(. 
Here is whot I got:```
elmar@otto ~/Installation debs etc/linuxwacom-0.8.5-4 $ make
Making all in src
make[1]: Betrete Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src'
Making all in .
make[2]: Betrete Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src'
make[2]: Für das Ziel »all-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src'
Making all in wacomxi
make[2]: Betrete Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src/wacomxi'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src/wacomxi'
Making all in util
make[2]: Betrete Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src/util'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic  -g -O2 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c -o wacomcfg.lo wacomcfg.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -g -O2 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
In file included from wacomcfg.c:36:
wacomcfg.h:26:22: error: X11/Xlib.h: No such file or directory
wacomcfg.h:27:35: error: X11/extensions/XInput.h: No such file or directory
wacomcfg.h:28:36: error: X11/extensions/XIproto.h: No such file or directory
In file included from wacomcfg.c:36:
wacomcfg.h:58: error: expected specifier-qualifier-list before ‘Display’
wacomcfg.h:62: warning: struct has no members
wacomcfg.h:67: error: expected specifier-qualifier-list before ‘XDevice’
wacomcfg.h:75: error: expected ‘)’ before ‘*’ token
In file included from wacomcfg.c:39:
../include/Xwacom.h:23:24: error: X11/keysym.h: No such file or directory
wacomcfg.c: In function ‘CfgError’:
wacomcfg.c:72: error: ‘WACOMCONFIG’ has no member named ‘pfnError’
wacomcfg.c:73: error: ‘WACOMCONFIG’ has no member named ‘pfnError’
wacomcfg.c: In function ‘CfgGetDevs’:
wacomcfg.c:83: error: ‘WACOMCONFIG’ has no member named ‘pDevs’
wacomcfg.c:83: warning: implicit declaration of function ‘XListInputDevices’
wacomcfg.c:83: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:84: error: ‘WACOMCONFIG’ has no member named ‘nDevCnt’
wacomcfg.c:86: error: ‘WACOMCONFIG’ has no member named ‘pDevs’
wacomcfg.c: At top level:
wacomcfg.c:96: error: expected ‘)’ before ‘*’ token
wacomcfg.c: In function ‘WacomConfigListDevices’:
wacomcfg.c:136: error: ‘XDeviceInfo’ undeclared (first use in this function)
wacomcfg.c:136: error: (Each undeclared identifier is reported only once
wacomcfg.c:136: error: for each function it appears in.)
wacomcfg.c:136: error: ‘info’ undeclared (first use in this function)
wacomcfg.c:140: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:146: error: ‘WACOMCONFIG’ has no member named ‘pDevs’
wacomcfg.c:160: error: ‘WACOMCONFIG’ has no member named ‘nDevCnt’
wacomcfg.c:162: error: ‘WACOMCONFIG’ has no member named ‘pDevs’
wacomcfg.c:164: error: ‘IsXExtensionDevice’ undeclared (first use in this function)
wacomcfg.c:186: error: ‘WACOMCONFIG’ has no member named ‘nDevCnt’
wacomcfg.c:188: error: ‘WACOMCONFIG’ has no member named ‘pDevs’
wacomcfg.c: In function ‘WacomConfigOpenDevice’:
wacomcfg.c:294: error: ‘XDevice’ undeclared (first use in this function)
wacomcfg.c:294: error: ‘pDev’ undeclared (first use in this function)
wacomcfg.c:295: error: ‘XDeviceInfo’ undeclared (first use in this function)
wacomcfg.c:295: error: ‘pDevInfo’ undeclared (first use in this function)
wacomcfg.c:295: error: ‘info’ undeclared (first use in this function)
wacomcfg.c:295: warning: left-hand operand of comma expression has no effect
wacomcfg.c:296: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:302: error: ‘WACOMCONFIG’ has no member named ‘pDevs’
wacomcfg.c:306: error: ‘WACOMCONFIG’ has no member named ‘nDevCnt’
wacomcfg.c:308: error: ‘WACOMCONFIG’ has no member named ‘pDevs’
wacomcfg.c:332: warning: implicit declaration of function ‘XOpenDevice’
wacomcfg.c:332: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:344: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c: In function ‘WacomConfigCloseDevice’:
wacomcfg.c:353: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c:354: warning: implicit declaration of function ‘XFree’
wacomcfg.c:354: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c: In function ‘WacomConfigSetRawParam’:
wacomcfg.c:363: error: ‘XDeviceResolutionControl’ undeclared (first use in this function)
wacomcfg.c:363: error: expected ‘;’ before ‘c’
wacomcfg.c:364: error: ‘XDeviceControl’ undeclared (first use in this function)
wacomcfg.c:364: error: ‘dc’ undeclared (first use in this function)
wacomcfg.c:364: error: expected expression before ‘)’ token
wacomcfg.c:364: error: ‘c’ undeclared (first use in this function)
wacomcfg.c:370: error: ‘DEVICE_RESOLUTION’ undeclared (first use in this function)
wacomcfg.c:376: warning: implicit declaration of function ‘XChangeDeviceControl’
wacomcfg.c:376: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:376: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c:381: error: ‘BadValue’ undeclared (first use in this function)
wacomcfg.c:381: error: ‘BadRequest’ undeclared (first use in this function)
wacomcfg.c:390: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:390: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c:402: warning: implicit declaration of function ‘XSetDeviceMode’
wacomcfg.c:402: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:402: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c: In function ‘WacomConfigGetRawParam’:
wacomcfg.c:410: error: ‘XDeviceResolutionControl’ undeclared (first use in this function)
wacomcfg.c:410: error: expected ‘;’ before ‘c’
wacomcfg.c:411: error: ‘XDeviceResolutionState’ undeclared (first use in this function)
wacomcfg.c:411: error: ‘ds’ undeclared (first use in this function)
wacomcfg.c:412: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:418: error: ‘c’ undeclared (first use in this function)
wacomcfg.c:418: error: ‘DEVICE_RESOLUTION’ undeclared (first use in this function)
wacomcfg.c:424: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:424: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c:425: error: ‘XDeviceControl’ undeclared (first use in this function)
wacomcfg.c:425: error: expected expression before ‘)’ token
wacomcfg.c:427: error: ‘BadValue’ undeclared (first use in this function)
wacomcfg.c:427: error: ‘BadRequest’ undeclared (first use in this function)
wacomcfg.c:433: error: expected expression before ‘)’ token
wacomcfg.c:448: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:449: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c:450: error: expected expression before ‘)’ token
wacomcfg.c:458: error: expected expression before ‘)’ token
wacomcfg.c:470: error: ‘WACOMCONFIG’ has no member named ‘pDisp’
wacomcfg.c:470: error: ‘WACOMDEVICE’ has no member named ‘pDev’
wacomcfg.c:471: error: expected expression before ‘)’ token
wacomcfg.c:473: warning: implicit declaration of function ‘XFreeDeviceControl’
wacomcfg.c:473: error: expected expression before ‘)’ token
make[2]: *** [wacomcfg.lo] Fehler 1
make[2]: Verlasse Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src/util'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/elmar/Installation debs etc/linuxwacom-0.8.5-4/src'
make: *** [all-recursive] Fehler 1

```I believe, this is not what it should look like. 

Hopefully you can help me, please.

---

### Post by Favux on 2009-12-25
Hi scicode,

I think we need to know a little more.  Which patch set did you use and what instructions did you follow?


Hi elmo64,

Welcome to Ubuntu forums!

Less rusty than my Deutsch I bet.

Luckily your problem is easily fixed.  The spaces you have in your directory path are not allowed.  "Installation debs etc" needs to be "Installation-debs-etc" or "Installation_debs_etc".

Since the Desktop allows spaces we all forget and make the same mistake.  :)

---

### Post by elmo64 on 2009-12-25
Hi Favux, 
thanks for your reply, but correcting the directory didn't help. "make" returns exactly the same errors as before. :(

---

### Post by Favux on 2009-12-25
Hi elmo64,

Alright, then in addition you might not have all the dependencies installed.  In particular the X11 library.  So try:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get install libhal-dev

sudo apt-get upgrade
```
And then try to patch and compile as per Ayuthia's instructions in the first post.

---

### Post by elmo64 on 2009-12-25
Yes, thank you very much :). My tablet has finally come to life, although not yet working properly. 
Maybe this has got sth. to do with the .fdi file? At that point I find this thread a bit confusing (unübersichtlich in german). 
If I get it right, I should use the file from post #579 (...debug-version_rc2_...) and put it in /usr/share/hal/fdi/policy/20thirdparty ? Would that be all I have to do?

---

### Post by Favux on 2009-12-25
Hi elmo64,

With any luck that should do it!

---

### Post by WvBraun on 2009-12-27
Hello everybody,

here is my story so far, maybe you can push me in the right direction to see something working with my tablet
Tablet Model: Bamboo Fun Pen&Touch CTH-661 Dev-Code (from lsusb): 056a:00d3
System: Ubuntu Karmic with latest Kernel 2.6.31generic 64bit

I used the instructions here to get and install the 0.8.5-8 version of the linuxwacom driver and the latest fdi I could find. I did NOT purge wacom-tools and xserver-xorg-input-wacom before updating the kernel module wacom.ko. I found, that I get worse results if I do so (the howto also tells me not do purge this packages on karmic).

So this is what I get, when I plug in my Bamboo:
 - lsusb reports the tablet to be connected (with device code)
 - lshal.txt (see attachment): Looking good so far as I read it.
 - /var/log/messages reports:
```

Dec 27 12:40:03 DanielsPC kernel: [  731.917334] usb 6-1: USB disconnect, address 2
Dec 27 12:40:21 DanielsPC kernel: [  750.480018] usb 6-1: new full speed USB device using ohci_hcd and address 3
Dec 27 12:40:21 DanielsPC kernel: [  750.672117] usb 6-1: configuration #1 chosen from 1 choice
Dec 27 12:40:21 DanielsPC kernel: [  750.674154] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/input/input12
Dec 27 12:40:21 DanielsPC logger: device input12 is bound to the driver
Dec 27 12:40:21 DanielsPC logger: must rebind
Dec 27 12:40:21 DanielsPC kernel: [  750.698183] input: Wacom Bamboo P&T 6x8 as /devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.1/input/input13
Dec 27 12:40:21 DanielsPC logger: device input13 is bound to the driver
Dec 27 12:40:21 DanielsPC logger: must rebind

```   does not look to bad - only the 'must rebind' things look a bit strange..

 - xinput --list --short reports
```

"eraser"    id=3    [XExtensionKeyboard]
"stylus cursor"    id=4    [XExtensionKeyboard]
"stylus pad"    id=6    [XExtensionKeyboard]
"stylus"    id=7    [XExtensionKeyboard]
"pad"    id=8    [XExtensionKeyboard]

```   and xsetwacom list tells me:
eraser     eraser
stylus     stylus
pad     pad

 - Xorg.0.log shows:
```

(II) config/hal: Adding input device eraser
(**) Option "Device" "/dev/input/event9"
(**) eraser: always reports core events
(**) eraser device is /dev/input/event9
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=21648 maxY=13530 maxZ=1023 resX=2540 resY=2540  tilt=disabled
(II) config/hal: Adding input device stylus cursor
(**) Option "Device" "/dev/input/event9"
(**) stylus cursor: always reports core events
(**) stylus cursor device is /dev/input/event9
(**) stylus cursor is in relative mode
(**) WACOM: suppress value is 2
(**) stylus cursor: reading USB link
(**) stylus cursor: threshold = 61
(**) stylus cursor: max x set to 21648 
(**) stylus cursor: max y set to 13530 
(**) stylus cursor: max z = 1023
(**) Option "BaudRate" "9600"
(**) stylus cursor: serial speed 9600
(II) XINPUT: Adding extended input device "stylus cursor" (type: Wacom Cursor)
(II) config/hal: Adding input device stylus pad
(**) Option "Device" "/dev/input/event9"
(**) stylus pad: always reports core events
(**) stylus pad device is /dev/input/event9
(**) stylus pad is in relative mode
(**) WACOM: suppress value is 2
(**) stylus pad: reading USB link
(**) stylus pad: threshold = 61
(**) stylus pad: max x set to 21648 
(**) stylus pad: max y set to 13530 
(**) stylus pad: max z = 1023
(**) Option "BaudRate" "9600"
(**) stylus pad: serial speed 9600
(II) XINPUT: Adding extended input device "stylus pad" (type: Wacom Pad)
(II) config/hal: Adding input device stylus
(**) Option "Device" "/dev/input/event9"
(**) stylus: always reports core events
(**) stylus device is /dev/input/event9
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) stylus: reading USB link
(**) stylus: threshold = 61
(**) stylus: max x set to 21648 
(**) stylus: max y set to 13530 
(**) stylus: max z = 1023
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) config/hal: Adding input device pad
(**) Option "Device" "/dev/input/event10"
(**) pad: always reports core events
(**) pad device is /dev/input/event10
(**) pad is in relative mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) pad: serial speed 9600
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=21648 maxY=13530 maxZ=1023 resX=2540 resY=2540  tilt=disabled
(II) config/hal: Adding input device touch
(**) Option "Device" "/dev/input/event10"
(EE) PreInit returned NULL for "touch"
(EE) config/hal: NewInputDeviceRequest failed (8)

```   Here the Errors for touch worry me a bit, but who knows?

 - I also can see the devices in /dev/input as 'wacom' and 'wacom-touch' sym-links to event9 and event10
 - ls -l /dev/input/by-id returns
```

lrwxrwxrwx 1 root root 10 2009-12-27 13:13 usb-Wacom_Co._Ltd._CTH-661-event-if01 -> ../event10
lrwxrwxrwx 1 root root  9 2009-12-27 13:13 usb-Wacom_Co._Ltd._CTH-661-event-mouse -> ../event9
lrwxrwxrwx 1 root root  9 2009-12-27 13:13 usb-Wacom_Co._Ltd._CTH-661-mouse -> ../mouse3

```
 - I can also use the wacomcpl program to make some settings

The problem is now: I get no response from the tablet anyways ... OK, the indicator LED of the Bamboo reacts to my actions, but this is not an indication of anything. I tried to xxd event9, event10, mouse3 - to no avail! There is also no reaction on the desktop or in GIMP or inkscape whith my wonderful new hardware :(.

I think, I'm stuck somewhere. What do you propose? I read above somewhere, that Rebecca2525 reported a working stylus on CTH-661 with version 08.5-1 would this be a starting point?

I would also like to contribute something, if I can - but I don't know where wo start. Most important thing for me now is to get ANY working reaction from my tablet.

Thanks in advance for your help, Daniel.

---

### Post by Favux on 2009-12-27
Hi WvBraun,

Sorry, my fault it looks like.

You are the third P & T user to report that their P & T doesn't work on 0.8.5-8.  Another Ubuntu user and an OpenSuse user.  Apparently there were some kernel changes etc. that caused the submitted patches to not work.  The linuxwacom drivers are being merged with the Xorg x86f linuxwacom drivers and so there are rapid changes occuring.  They are straightening that out.

So for right now you should probably use Ayuthia's -34 patches for 0.8.5-4 and instructions in the first post and the new-generic rc2 .fdi.  Another option would be ob1kenobe's -35 patched linuxwacom. 

I guess you missed the post several posts later where I announced 0.8.5-8 didn't seem to be working.  And with your post I think it's totally confirmed.  I'll edit the original post now.

By the way your lshal looks fine, so whichever .fdi you are using is working.

---

### Post by Favux on 2009-12-28
Hi everyone,

Enrico Ros has kindly summarized the current state of Bamboo P & T support and what is needed to merge it:
> Here is the current status of the merge of UbuntuForums changes into the xf86-
input-driver and linuxwacom code trees.

Contents of 'bamboo-34' UbuntuForums patch:
A. kernel changes against 2.6.28
B. XInput changes
C. hal(fdi) + udev + minor changes

xf86-input-wacom vs. bamboo-34:
* Half of the B changes already merged and shipped in 0.10.3
* Greatly improved since the merge (thanks to Ping)
* There is one B patch remaining, bringing some Touch logic [1]. This is the
last bit of B changes to merge

linuxwacom-0.8.5-8 vs. bamboo-34:
* diverged A - can't say which one is better, but with linuxwacom my 0xD2
tablet doesn't work
* half of B has been ported from xf86-input-wacom (not merged from bamboo-34)
* some of C has been applied: 10-linuxwacom.fdi: merged, 60-wacom.rules: non
applied, wacomcpl-exec: non applied.

Remaining steps:
* pull [1] into xf86-input-wacom and apply it to linuxwacom/src/xdrv - this
will sync all the B changes
* linuxwacom/src/2.6.27: merge with the kernel changes of bamboo-34 - this
won't be an easy task. you can use my git mirror [2] for easily diffing trees
(linuxwacom / ubuntuforums) and revisions

[1] git://gitorious.org/linuxwacom/xf86-input-wacom.git - 'for-whot' branch
[2] git://gitorious.org/linuxwacom/linuxwacom-mirror.git

Regards,
Enrico 
from:  [http://sourceforge.net/mailarchive/forum.php?thread_name=200912281807.26164.enrico.qt%40email.it&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=200912281807.26164.enrico.qt%40email.it&forum_name=linuxwacom-devel)

---

### Post by Favux on 2009-12-31
Hi everyone,

**[SIZE="3"]A call for testers.[/SIZE]**  Linuxwacom 0.8.5-9 has been released:
> Incorporated Ayuthia's Bamboo P&T patch -34. Fixed some kernel misplacement. Fixed a protocol4 mouse button click issue.
As you can see Ping had to fix some kernel issues.  Hopefully that won't prevent this one from doing the job.

Good luck!

---

### Post by bromalex on 2009-12-31
> **Favux said:**
> Linuxwacom 0.8.5-9 has been released:

Hi

I tried 0.8.5-9 but I only have Touch.

Stylus, eraser and stylus buttons do not work :(

It could be my fault, so if any of you savvy guys want some more info please ask.

The Touch function is still not fine. I get unwanted left clicks and every time I touch the Tablet, the cursor moves somewhere around Top Left screen position. (But this behavior was already present in my laptop with 0.8.5-4-34/35)

The tablet buttons work as (Top to Bottom): midlle click, right click, PgUp and PgDn. They are named (respectively) in **wacomcpl** as Button2, Button3, Button4, ???
I still can't figure out how to change the assignment to the last tablet button (the bottom one). (Again, all this is identical to 0.8.5-4-34/35)

Bye

PS: BAMBOO PEN & TOUCH - CTH-460 (OxD1)

My only steps, starting from a "working" lnuxwacom-0.8.5-4-35:
```
tar xjvf linuxwacom-0.8.5-9.tar.bz2
cd linuxwacom-0.8.5-9
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp ./src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
Reboot and plug-in Bamboo

```

---

### Post by Favux on 2009-12-31
Hi Bromalex,

Thanks for testing.  Sounds like it's getting closer.  At least partial function this time.

Could I see your Xorg.0.log (in /var/log/)?  It would be good to know if the Wacom driver is providing touch and the pad.  It would also help figure out what's happening with stylus.

---

### Post by bromalex on 2009-12-31
> **Favux said:**
> ..
Could I see your Xorg.0.log ...

Sure here it is.

A wondrous 2010 for all:P

---

### Post by Favux on 2009-12-31
Hi bromalex,

Happy New Year!  :)

I asked Ayuthia and ob1kenobi if they could take a look at things and help us.  I think/hope we're close!

Edit:  Huh, it looks good.  I'll look closer.  What does your 'xinput --list' and 'xsetwacom list' look like?  What shows up in wacomcpl?

---

### Post by Favux on 2009-12-31
Hi bromalex,

Yep, the Xorg.0.log looks good.  Sytlus and eraser on event 10 and touch and pad on event 11.  The Synaptic touchpad is on event 9.  It looks like the wacom driver is attaching and things should be working.  :confused:

Could you also post your lshal?

---

### Post by bromalex on 2009-12-31
> **Favux said:**
> Hi bromalex,
Could you also post your lshal?

I am hopping between the party and here !!

---

### Post by bromalex on 2009-12-31
> **Favux said:**
> What does your 'xinput --list'

Another one

---

### Post by bromalex on 2009-12-31
> **Favux said:**
> 'xsetwacom list' look like

eraser     eraser
stylus     stylus
pad     pad
touch     touch

---

### Post by bromalex on 2009-12-31
> **Favux said:**
> What shows up in wacomcpl?

Some screenshots of wacomcpl.
The eraser info is the same as stylus

---

### Post by Favux on 2009-12-31
Hi bromalex,

Perfect!  Everything looks good up to wacomcpl where you are seeing duplicates.  As if you have an extra wacom.fdi or a .fdi and an xorg.conf.

I'm guessing that's the code.  Unless 0.8.5-9 is now loading an extra .fdi like Ayuthia tried to do.  As I recalled he was trying to get the .fdi to be automatically placed when the patches were compiled.  Maybe it's now working?  Might want to check for that because the .fdi he was using I think was before we came up with a working one.

Now get back to the party!

---

### Post by bromalex on 2009-12-31
> **Favux said:**
> Hi bromalex,

Perfect!  Everything looks good up to wacomcpl where you are seeing duplicates.  As if you have an extra wacom.fdi or a .fdi and an xorg.conf.


I quite don't understand that duplication you're seeing in wacomcpl. As I recall it it looks the same as with Ayuthia's or ob1kenobi. Except maybe "stylus>screen mapping" in "Dysplay Mapping" where the options are greyed.

---

### Post by kawaji on 2009-12-31
Thank you very much everyone for your works to progress development.
Happy New Year! :popcorn:

I've got Bamboo Pen & Touch(CTH-460) and now tried 0.8.5-9.
Stylus, eraser, stylus buttons and tablet buttons seem not to work on my system.
I also have the same problem with touch function as bromalex.
'xsetwacom set touch Mode Relative' command fixes the cursor jump to top left screen behavior, though.

```
$ lsusb
Bus 004 Device 003: ID 056a:00d1 Wacom Co., Ltd
```

```
$ lsmod | grep wacom
wacom                  29124  0
```

```
$ modinfo -n wacom
/lib/modules/2.6.31-16-generic/kernel/drivers/input/tablet/wacom.ko
```

```

$ xsetwacom list
stylus     stylus
touch     touch
```

```
$ dmesg | grep Wacom
[   88.463479] wacom: v1.52-pc-0.2:USB Wacom tablet driver
[  118.219949] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input5
[  118.233946] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input6
[  234.849607] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input7
[  234.864082] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input8
```

```
$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ImExPS/2 Generic Explorer Mouse"	id=5	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 13
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"stylus"	id=7	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 12000
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 8000
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"touch"	id=8	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 12000
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is 8000
		Resolution is 0
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
```

```
$ lshal
udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'CTH-460'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/004/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 262  (0x106)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.max_power = 98  (0x62)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'CTH-460'  (string)
  usb_device.product_id = 209  (0xd1)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 262  (0x106)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 209  (0xd1)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'  (string)
  info.product = 'touch'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'  (string)
  input.product = 'Wacom Bamboo P&T 4x5'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'touch'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input8/event6'  (string)
  wacom.types = {'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 262  (0x106)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 209  (0xd1)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'  (string)
  input.product = 'Wacom Bamboo P&T 4x5'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input7/event5'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)
```

---

### Post by Favux on 2009-12-31
Hi bromalex,

My oops!  I was looking at the labels on .png's.  Nevermind.  :)


Hi kawaji,

Happy New Year!

Alrighty, I'll take a look at your stuff too.

---

### Post by bromalex on 2009-12-31
Okay guys

It is past 4 o'clock in the morning over this side of the pond and I am going to bed.

Hopefully I will find even better news when I'm back here.

Thank you all you guys, who are helping to get our Bamboos working.

---

### Post by Favux on 2009-12-31
Hi kawaji,

Interesting.  I just saw something like that from a P & T in Gentoo.  In your dmesg you have 4 input events for the tablet.  There should be only two.  The 5 & 6 seem to be the ones in the .fdi.  The 7 & 8 seem to be showing up as the wacom symlinks in Xorg.0.log 'wacom' and 'wacom-touch'.  So I am confused now.

Could you check your udev rule wacom symlinks?  Should be in "/lib/udev/rules.d/40-xserver-xorg-input-wacom.rules" and make sure there isn't a duplicate rule for 056a:00d1.  You might also want to check "/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules".  There shouldn't be a wacom.rules there.  When you've ruled that out maybe try commenting out the rule in the first location and see if that gets you down to two events in dmesg and if pad and eraser now show up in Xorg.0.log correctly?

I wonder if this is because you don't do the purge lines in Karmic?

---

### Post by WvBraun on 2010-01-01
Hey folks,

happy new year to all of you and thanks for working for a better experience with our favourite OS.

Here are my results of testing linuxwacom 0.8.5-9:

OS-Version: Karmic (9.10)
Kernel: 2.6.31generic
Bamboo Fun CTH-661, dev code: 056a:00d3

attached are the results of:
 - /var/log/messages (looks fine, except maybe the 'rebind' stuff)
 - lshal (only relevant portion, still looks fine)
 - Xorg.0.log (no more errors here)

Some more results:
 - xinput --list --short
```

"eraser"    id=11    [XExtensionKeyboard]
"pad"    id=12    [XExtensionKeyboard]
"stylus cursor"    id=13    [XExtensionKeyboard]
"touch"    id=14    [XExtensionKeyboard]
"stylus pad"    id=15    [XExtensionKeyboard]
"stylus"    id=16    [XExtensionKeyboard]

``` - xsetwacom list
```

eraser     eraser
pad     pad
touch     touch
stylus     stylus

``` - /dev/input/by-id
```

lrwxrwxrwx 1 root root 10 2010-01-01 12:59 usb-Wacom_Co._Ltd._CTH-661-event-if01 -> ../event11
lrwxrwxrwx 1 root root 10 2010-01-01 12:59 usb-Wacom_Co._Ltd._CTH-661-event-mouse -> ../event10
lrwxrwxrwx 1 root root  9 2010-01-01 12:59 usb-Wacom_Co._Ltd._CTH-661-mouse -> ../mouse3

``` - two sym-links in /dev/input
```

lrwxrwxrwx 1 root root      7 2010-01-01 12:59 wacom -> event10
lrwxrwxrwx 1 root root      7 2010-01-01 12:59 wacom-touch -> event11

```

I can see the following functionality:
 - touch works in approximately the upper left fourth of the screen and it is in absolute mode, when touching the tablet I get a left button down (always)
 - stylus does not work anyway
 - tablet buttons work fine
 - wacomcpl lets me set configuration for:
   - stylus (OK, no results but i can set things)
   - eraser (same as stylus)
   - pad (buttons definitions and so on)
   - touch appears but there are no controls or buttons

I do not see any activity on the sym-linked events with xxd - is this expected behaviour?

Questions or suggestions, what else I could supply for helping you guys?

So far from this side, Daniel.

---

### Post by kawaji on 2010-01-01
Hi Favux,
Thank you for your help.

> Could you check your udev rule wacom symlinks? Should be in "/lib/udev/rules.d/40-xserver-xorg-input-wacom.rules" and make sure there isn't a duplicate rule for 056a:00d1.

"40-xserver-xorg-input-wacom.rules" not found, only "40-xserver-xorg-input-wacom.rules.bak" was in "/lib/udev/rules.d", and no wacom rules in "/etc/udev/rules.d" on my system.

So, I copied "src/util/60-wacom.rules" from the linuxwacom-0.8.5-9 source package to "/lib/udev/rules.d/40-xserver-xorg-input-wacom.rules" and rebooted, but now stylus and even the touch funciton do not work at all.
I can not find any "00d1" string in the "src/util/60-wacom.rules" file. 
that's the cause of this problem ?

I ran dmesg again, and got the following result.
```
[   85.217700] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[   85.236355] input: Wacom Bamboo P&T 4x5 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input5
[   85.242704] wacom: v1.52-pc-0.2:USB Wacom tablet driver
```

$ lshal
```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'CTH-460'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/004/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 262  (0x106)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.max_power = 98  (0x62)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'CTH-460'  (string)
  usb_device.product_id = 209  (0xd1)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 262  (0x106)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 209  (0xd1)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'  (string)
  info.product = 'touch'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if1'  (string)
  input.product = 'Wacom Bamboo P&T 4x5'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'touch'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input5/event5'  (string)
  wacom.types = {'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 262  (0x106)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 209  (0xd1)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_d1_noserial_if0'  (string)
  input.product = 'Wacom Bamboo P&T 4x5'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4/event4'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)
```

---

### Post by WvBraun on 2010-01-01
Whoops sorry, forgot to attach some files ;)

Here they come...

---

### Post by APchris on 2010-01-01
Hi folks...

...first, a BIG thank you to Favux, Ayuthia, kgingeri and others for the excellent information and help in getting my new Bamboo Pen (model CTL 460) up and running :P

I'm still having a problem though :( In GIMP, the stylus doesn't draw in the same place as the cursor. There is a misalignment that increases when I move the stylus toward the edges of the screen. The stylus position and cursor only align perfectly in the centre of the screen.

I have tried various setting in "Configure Extended Input Devices", changing Mode from 'Disable' to 'Window' and 'Screen' but it made no difference:confused: ...so thinking the solution would be to configure the Bamboo I tried opening wacomcpl but I get the following error in Terminal...

[I]
wacomcpl: using TCLLIBPATH="
[list  /usr/local/lib ]"
Error in startup script: invalid escape %D found in path template
invalid escape %D found in path template
Unable to open config file
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1953)
[/I]

Any ideas what might be going on here?

---

### Post by WvBraun on 2010-01-01
Ah and by the way: when plugged in during startup, the operational range of the touch-functionality is still in absolute mode, but reduced a VERY small area in the upper left corner of the screen.

Just for your information ;)

---

### Post by bromalex on 2010-01-01
> **WvBraun said:**
> Ah and by the way: when plugged in during startup, the operational range of the touch-functionality is still in absolute mode, but reduced a VERY small area in the upper left corner of the screen.

Yes. I have the same behavior.

As a suggestion. It would be nice if, as default, the top tablet button would function as in the window$ driver: it enables/disables the touch function on Bamboo

---

### Post by Favux on 2010-01-01
Hi APchris,

Welcome to Ubuntu forums!

Use screen in Gimp.  I think there's still a bug that causes and offset if you don't.

Can I get a little more information.  Which version of linuxwacom and which patch set did you use?  Did you install the dependencies in Section 1 step 2) of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1")?


Hi WvBraun,

What you are describing sounds like the Synaptic touchpad .fdi/driver is grabbing your tablet.  I can't see if that's the case on what you provided.

But it's probably worthwhile for anyone with a Bamboo P & T to use Ayuthia's fix for the Synaptic .fdi so it isn't so grabby.  See [post #22 here]("http://ubuntuforums.org/showpost.php?p=8372380&postcount=22").

---

### Post by APchris on 2010-01-01
Hi Favux... many thanks for the quick response :P

Just set all the various Wacom Tablet entries in "Configure Extended Input Devices" in GIMP to 'Window' and it works perfectly now.. so another BIG thank you for that.

As for what I did... well I tried so many things it's difficult to remember precisely what! What finally worked for me was following your post #384 then kgingeri's instructions in post #541 along with Ayuthia's patch instructions in post #144 which uses linuxwacom-0.8.4-3. I'd previously been using 0.8.4-4 and got nowhere.

Prior to that I created a 10-linuxwacom.fdi file from your rc2 code (I didn't have 10-linuxwacom.fdi before doing that) and have added the ATTRS{idProduct} reference lines in 40-xserver-xorg-input-wacom.rules both for my tablet 00d4 and for 00d1.

Thanks for all the time you guys spend helping us newbies, its very much appreciated :P

---

### Post by Gondrano on 2010-01-02
Hello everybody!

I'm a fresh new guy converted (really happily) to Ubuntu.
This is my first post and I think to be in the good thread.

So here is the problem: I have a Wacom Bamboo cth-460 connected through a USB to my Asus A6VM on Karmic Koala.

I don't know almost nothing about programming, compiling, and Linux structure.
I just would like to use my tablet on this easy and light o/s. 

I wonder if I must read all this thread (which sound quite impossible) or  if maybe there is a short version, or better, a step by step explication concerning only Asus & cth-460 that i can study.

I'm really a beginner but I like Ubuntu and I would do everything possible to keep it.
(but I need the tablet to sketch!!)

thanks in advance

---

### Post by Favux on 2010-01-02
Hi Gondrano,

Welcome to Ubuntu forums!

The simplest is to follow Ayuthia's instructions on the first post of this thread.  Before you compile you may want to follow bromalex's instructions in [post #677]("http://ubuntuforums.org/showpost.php?p=8504798&postcount=677") to remove the debug code from the patches.  Otherwise your log files will fill up.  The .fdi file you want to use is at [post #579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").  If you don't know how to install the .fdi instructions are in Section 2 b) on this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

It might seem a little intimidating but it is not really that hard.  Just read things through a couple of times to get it straight in your head.

Hope this helps.  Good luck!

---

### Post by kgingeri on 2010-01-02
> **Gondrano said:**
> Hello everybody!

I'm a fresh new guy converted (really happily) to Ubuntu.
This is my first post and I think to be in the good thread.

...

I'm really a beginner but I like Ubuntu and I would do everything possible to keep it.
(but I need the tablet to sketch!!)

thanks in advance

Welcome to Ubuntu & the forum Gondrano!

Like anything computer related, little-by-little will get you there. Favux is right, if you get stuck, you can always ask! We're here to help :)

Happy new year All!

@Favux: Gotta confess something... sold my Cintiq 12wx (just too bulky and overkill for what I need) and bought a ASUS T91MT (multi-touch) and have been busy getting it all working & **LOVE** it!!  Haven`t got everything working yet but VERY useable (I been posting in the ASUS threads).  However I intend to try my CTH again soon. 1'll let you know..

(PS: wrote this all using CellWriter & EasyStroke ;))

---

### Post by kgingeri on 2010-01-02
> **Gondrano said:**
> Hello everybody!

I'm a fresh new guy converted (really happily) to Ubuntu.
This is my first post and I think to be in the good thread.

...

I'm really a beginner but I like Ubuntu and I would do everything possible to keep it.
(but I need the tablet to sketch!!)

thanks in advance

Welcome to Ubuntu & the forum Gondrano!

Like anything computer related, little-by-little will get you there. Favux is right, if you get stuck, you can always ask! We're here to help :)

Happy new year All!

@Favux: Gotta confess something... sold my Cintiq 12wx (just too bulky and overkill for what I need) and bought a ASUS T91MT (multi-touch) and have been busy getting it all working & **LOVE** it!!  Haven't got everything working yet, but VERY useable (I've been posting in the ASUS threads).  However I intend to try my CTH again soon. 1'll let you know..

(PS: wrote this all using CellWriter & EasyStroke ;))

---

### Post by bromalex on 2010-01-02
I added the 2 modified files with no Debug information in my [**post**]("http://ubuntuforums.org/showpost.php?p=8504798&postcount=677"), for those who asked, while we wait for the "white smoke" coming from the almighty code cruncher super brainiacs ... 
[-o<

---

### Post by Gondrano on 2010-01-03
Hi guys, thanks for your support. 

I tryed to do what is written in the first post but I have some troubles with the installation pack. I'm blocked in **option A in the first post **(I followed the 541 post) untill the same result.

Maybe because I have already tried with other packages (previus versions) and follow different ways, (caotic, fractional, not ending up ways) No way to say what I exactly did why I just don't remember (something with .fdi and linuxwacom file, and some imput device's copy&paste[is that compiling?])

terminal answering to unpacking commands:

root@brezeler-laptop:~# tar -xvjf linuxwacom-0.8.5-4-bamboo-34.tar.bz2t
tar: linuxwacom-0.8.5-4-bamboo-34.tar.bz2t: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@brezeler-laptop:~# tar -xjvf linuxwacom-0.8.4-3.tar.bz2
tar: linuxwacom-0.8.4-3.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

I'm really sorry to bother you with so** low** level of competence

---

### Post by Gondrano on 2010-01-03
I was in "root" capacities, I went out and the following work:

tar -xvjf linuxwacom-0.8.5-4-bamboo-34.tar.bz2
cd linuxwacom-0.8.5-4

Question: for root abilities is: sudo -i, and then for coming back? what do I need to type?

Now I go forward to compiling (I think)

I write you again then I had other problems ;)

---

### Post by WvBraun on 2010-01-03
Hi Gondrano,

don't worry, it's just a typo error. After cd'ing to the directory, where you keep your downloaded file, issue an **ls **to see, what exact name the downloaded file has - then you can go on and enter the line with **tar** and insert the filename letter by letter.

This should help so far - don't worry. After a few iterations of this stuff you will be way ahead of all your colleagues and you can feel like the EXPERT. ;)

EDIT: You were faster ...
So I just use **sudo COMMAND **with only one command at a time. It's better in my opinion, as sudo remembers your password a specified time. Anyways - to get back to your normal user, use just **exit**. 

Regards, Daniel.

---

### Post by bromalex on 2010-01-03
> **Gondrano said:**
> 
Question: for root abilities is: sudo -i, and then for coming back? what do I need to type?


Type:
```
exit
```

You could look at my post [**#627** ]("http://ubuntuforums.org/showpost.php?p=8423278&postcount=627") where I tried to make a newbie How-To to make my Bamboo Pen & Touch work.
If you don't want your Log files to fill with Debug messages, after decompressing linuxwacom-0.8.5-4-35, replace the original files (wacom.wac.c and wacom.sys.c) in directory /src/kernel/ with the modified ones you can download from post **[#677]("http://ubuntuforums.org/showpost.php?p=8504798&postcount=677")**.

If you need help, just say!

---

### Post by WvBraun on 2010-01-03
OK guys,

a new report from me and my Bamboo Fun (CTH-661) :
Decreasing grabbiness of synaptics-touchpad-driver in hal-policies did not change anything. I did not expect it to help, because my logs show now appearance of the synaptics driver anywhere.

But now this brought me somewhere:
 - I went to post   #[**586**]("http://ubuntuforums.org/showpost.php?p=8376047&postcount=586") and grabbed the linuxwacom-0.8.5-4-35 provided by [ob1kenobi]("http://ubuntuforums.org/member.php?u=955305")
 - unpacked the archive
 - went to post #[**677**]("http://ubuntuforums.org/showpost.php?p=8504798&postcount=677") and got the no-debug-version provided there by [bromalex]("http://ubuntuforums.org/member.php?u=693913")
 - used this files to overwrite the originals in 0.8.5-4-35
 - then compiled and installed the stuff
```

./configure --enable-wacom --prefix=/usr
make
sudo make install
```- after that copied the wacom.ko
```

sudo cp ./src/kernel/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```- reboot
 - as touch gave me erratic behaviour I temporarily deactivated it by entering (will look at this later)
```

xsetwacom set Wacom_Bamboo_6x8_Touch Touch 0
```

And now: the pen, eraser  and the pad WORK!
I checked this with inkscape - pen and buttons on the pen work as well as the eraser.

If I should provide logs or info on this - feel free to ask me.
A big fat thanks to you so far.

Daniel.

---

### Post by bromalex on 2010-01-03
> **WvBraun said:**
> 
And now: the pen, eraser  and the pad WORK!
I checked this with inkscape - pen and buttons on the pen work as well as the eraser...
Daniel.

Hi Daniel

Unlike Gimp I can't make Inkscape behave such that, when using a pen tool if you turn the stylus upside down to the eraser side, it switches automatically to the eraser tool.
Is this possible?

---

### Post by Gondrano on 2010-01-03
Hello Favux!

I have followed the instructions and I have finally installed the Wacom tablet!!I'm so happy!:)
I must admit that for a newbie like me sounds all really magic!

Thanks a lot to everybody who spends time, patience, and coffee on it.
The Favux Howto explication is very well done. 

My tablet's calibration default is ok but not perfect,so tried to change it permanently but i **can not save the xinitrc file** (adding "#")

It says that I can not file the file because I'm not the permission (owner permission?)

What can I do?

thanks in advance and Happy new year!

---

### Post by Gondrano on 2010-01-03
AAAAAhhhhhhhhh!

I restart my laptop because I suddently had some trouble with the cursor pad...

That was not really a good idea. I forgot the looping about the x11 driver and I lost the trash and brightness applet, but the worst thing is I cannot enter in the terminal.

All this caused by the unchanged file xinitrc.

I wonder what I must do to fix it, or just to come one  step back.

Any help is welcomed.


Gondrano

---

### Post by kgingeri on 2010-01-03
> **bromalex said:**
> Another, How-To Install Bamboo Pen&Touch (CTH-460) in Karmic (A newbie recollection of info from this Thread)...

This looks good Bromalex.  It _doesn't hurt_ to keep making how-to's better IMHO. :D

EDIT: meant to type "doesn't hurt" - corrected

---

### Post by kgingeri on 2010-01-03
> **Gondrano said:**
> AAAAAhhhhhhhhh!

I restart my laptop because I suddently had some trouble with the cursor pad...

That was not really a good idea. I forgot the looping about the x11 driver and I lost the trash and brightness applet, but the worst thing is I cannot enter in the terminal.

All this caused by the unchanged file xinitrc.

I wonder what I must do to fix it, or just to come one  step back.
Any help is welcomed.

Gondrano

Gondrano, while you boot up press down-arrow when you see lines about Linux version and choose a safe-mode line & press enter.  This will get to a place were you can do commands again. Permissions issues are usually because you are not 'root' - use 'sudo ...'

EDIT: As a 'newb' I would recommend using sudo - it's much safer ;)

---

### Post by Favux on 2010-01-03
Hi everyone,

Chris King at linuxwacom-discuss may have the P & T problem in 0.8.5-9 mostly figured out.  See:  [http://sourceforge.net/mailarchive/forum.php?thread_name=875c7e071001030849w33ec068av6ff2ff763fbf015d%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=875c7e071001030849w33ec068av6ff2ff763fbf015d%40mail.gmail.com&forum_name=linuxwacom-discuss).

Progress, I'm hoping.

---

### Post by bromalex on 2010-01-03
> **kgingeri said:**
> This looks good Bromalex.  It does hurt to keep making how-to's better IMHO. :D

Thanks.
If it is useful to someone, it's worth it!

---

### Post by kgingeri on 2010-01-03
> **bromalex said:**
> Thanks.
If it is useful to someone, it's worth it!

Oh brother - just realized I said "does" instead of "doesn't".  Hey English is my native language so take it easy on me!  ;)

---

### Post by munooka on 2010-01-03
I tried the new Driver today (0.8.5-9). The touch and stylus are recognised using xsetwacom list.
The touch has started to move the mouse around but it behaves like the left mouse button is always depressed (selects everything) and none of the touchpad's buttons actually work. The stylus is still totally dead. I will try to post a report at LinuxWacom's site. I used the fdi thgat compiled with the driver as the one here was not working. So I guess there is still someway to go!

---

### Post by Favux on 2010-01-03
Hi munooka,

You might want to hold off posting on the LWP site.  Ob1kenobi is looking at 0.8.5-9 and it looks like he has made some real progress.

---

### Post by munooka on 2010-01-03
After reading through some of the posts it looks like the same bugs have been reported. One question I did have was do I also need to compile the new xf86-input-wacom 0.10.3?

---

### Post by Favux on 2010-01-03
No, that's only if you had the new Xorg and Xserver 1.7.x that will be in Lucid.

---

### Post by munooka on 2010-01-03
Many thanks! I'll just switch back to the method in the first post until 0.8.5-10.

---

### Post by ob1kenobi on 2010-01-04
Hi all,

Here is a patch for linuxwacom version 0.8.5-9 that gets everything working for me (touch and pen) for my Bamboo 0xd1 model.

Unfortunately, the Capacity is not being set properly by HAL (you'll see it in the 10-linuxwacom.fdi file.  So in order to get rid of touch with constant left click, you have to run the following command once you are logged into X.org:

```
xsetwacom set touch Capacity 1
```This gets rid of a check in the wcmUSB code that turns on left click for all devices without capacity support.  Like I said there's a bug somewhere that is resetting Capacity to the default -1 even after HAL passed and the X.org driver accepts the value of 1.

Other than that everything should be functional.
Happy Testing :)

ob1kenobi

---

### Post by WvBraun on 2010-01-04
Thanks Ob1,

I can't wait to get home from the job today (well, just started now ;) ).

With 0.8.5-4-35 I now have the following behaviour after rebooting and keeping the tablet (CTH-661) connected:
 - I can use touch in relative mode without any further configuration. It works as expected, no constant left clicks, tapping the tablet results in a double click. However, the rotation with two fingers does not work, zooming works sometimes, but when you use it too often, it kills touch somehow...
 - stylus works perfectly, eraser and pad too

I will report my experience with the new patch this evening (in let's say 12 hours).

About inkscape and the eraser: I could not find a simple way to configurer the eraser click as something like 'left click'+'delete' or something alike. I will do some more research here (I think this is not primarily a tablet issue but something for Inkscape configuration details - I will report also).
Edit 2: There's an option in Inkscape preferences->Mouse->Switch tool based on tablet device ... I only have the german version here and my tablet is not in my office. I will try this today in the evening and report back also.

Regards, Daniel.

Edit: wrote some crap about inkscape - sry

---

### Post by munooka on 2010-01-04
Sorry for such a dumb question but I cannot seem to patch the wacom linux code. It just hangs there. I have tried:
~/Downloads/linuxwacom-0.8.5-9$ patch --verbose -p1 wcm_patch-0.8.5-9-1.patch.txt 

Without --verbose -p1 and also removing the .txt extension.

Thanks

EDIT: Ooops silly me forgot to use "<"

~/Downloads/linuxwacom-0.8.5-9$ patch -p1 < wcm_patch-0.8.5-9-1.patch.txt

---

### Post by bromalex on 2010-01-04
> **WvBraun said:**
> 
About inkscape and the eraser:...
Edit 2: There's an option in Inkscape preferences->Mouse->Switch tool based on tablet device


Thanks Daniel

You set me in the correct path.
Indeed you have to turn on that setting in Preferences!
I also configured File>Input Devices> and set:
eraser Mode:screen
stylus cursor Mode:screen
stylus Mode:screen

Now if you draw something and then switch the Bamboo pen to its eraser side, it will erase!

The only problem is that, unlike Gimp, if you then switch back to the stylus side, the Inkscape tool will still remain as "eraser". You have to select again another drawing tool.

Minor quirk!

---

### Post by munooka on 2010-01-04
Thanks Obi and Fav. The stylus no working pretty well much glitch free. 
The touch is also much better it took me  30 minutes to crash X. 
It wants to jump to the left bottom corner and after a little while X becomes unresponsive and I have to jump into a tty to bail myself out. 
The top mouse button reacts like a middle mouse click for me (pasting selected stuff), but the other buttons seem to check out. 
Is it possible to use xsetwacom to switch it? I tried xsetwacom set touch button1 1 and also xsetwacom pad button1 1 but it didn't work.
Sometimes I even get double finger scrolling and zooming out and in gestures working but this is buggy. 
Are there any xsetwacom settings that can be used to try to get this tuned? I looked through the manual and nothing was obvious except the Capacity integer which makes X fail at different rates on touch mode.

---

### Post by bromalex on 2010-01-04
> **ob1kenobi said:**
> 
Here is a patch for linuxwacom version 0.8.5-9 that gets everything working for me (touch and pen) for my Bamboo 0xd1 model.

```
xsetwacom set touch https://startpage.com/Capacity 1
```
ob1kenobi

Hi

Thank you Ob1kenobi

I tried your 0.8.5-9 patched version.

1. That command didn't work in my system. Something about it couldn't find [https://startpage.com](https://startpage.com) .... [COLOR="RoyalBlue"]Typo?????[/COLOR]
So I disabled Touch with: xsetwacom set touch Touch off

2. Apart from that almost all is OK, because,

3. Unlike 0.8.5-4-35, with this version when I unplug and replug, my Bamboo P&T CTH-460 doesn't work :-(

---

### Post by WvBraun on 2010-01-04
Hi Bromalex,

I looked up some more inkscape pages and noticed, that they want to integrate a real tablet configuration in future - so we will hopefulyy get more and even better support than now for our wonderful devices. We can live with the current behaviour so far. ( [http://wiki.inkscape.org/wiki/index.php/Tablet_Dialog](http://wiki.inkscape.org/wiki/index.php/Tablet_Dialog) )

One Hint:

```

xsetwacom set touch Capacity 1

```Should to the trick. By the way:
```

xsetwacom list param

```gives you a complete list of Parameters, you can use with get and set. Obviously there's no parameter with URL-style ;)

So far...

---

### Post by bromalex on 2010-01-04
> **WvBraun said:**
> [http://wiki.inkscape.org/wiki/index.php/Tablet_Dialog](http://wiki.inkscape.org/wiki/index.php/Tablet_Dialog)

Nice!

> **WvBraun said:**
> 
```

xsetwacom set touch Capacity 1

```


Of course:oops:

Thank you

---

### Post by munooka on 2010-01-04
So I tried the pad for the first time on a windows XP machine and I noticed that the buttons on CTH-460 are not really mapped correctly at all (I am right handed so didn't change anything). The Top button is mapped to a middle button copy and paste (default toggle ouch XP), second top is right click, third top is scroll up and bottom is scroll down. Maybe I am being stupid but I can't seem to change these buttons using wacomcpl or xsetwacom (where they appear to be setup OK). What is the correct syntax? I have tried examples (modified from the manual pages) but nothing seems to work right now:
xsetwacom set pad Button1 "button 1"  and
xsetwacom set pad Button1 1
:confused:

---

### Post by bromalex on 2010-01-04
> **munooka said:**
> So I tried the pad for the first time on a windows XP machine ...

Hi Munooka

I already asked that same question, but I assume the lack of answers means that with the available versions of the Linux Driver it is still not possible to map all the tablet buttons.

Summing up (Buttons from top to bottom)
WinXP
1. Touch toggle
2. Back
3. Right click
4. Left click

Linux
2. Middle click
3. Right click
4. Pg Up
?. Pg Dn

Using **wacomcpl** I can change buttons 2. 3. and 4. but not the bottom one.

Also I can't assign a Touch toggle function to any of the buttons (I don't even know if this Toggle exists in the Linux driver)

---

### Post by Favux on 2010-01-04
Hi munooka,

That sounds like what others have been saying.  I read a review that said the top (?) pair of buttons was on and off for touch.  The bottom pair was left and right click.  This was in Win7 I think.  Someone said one button toggles touch on and off.  So who knows.

This should be right:
```
xsetwacom set pad Button1 "1"
```
but "Button1" for "1" should also work.  Also in the first button after pad I've seen it capitalized and not so it doesn't look like it is suppose to be case sensitive, as in:
```
xsetwacom set pad button1 "1"
```
But I've noticed for some folks it does seem case sensitive so try both.

Edit:  Bromalex beat me to it.  No touch toggle I know of.  Definitely a feature request worth making.  Tabulating tablet button functions is a good idea.  :)  Let's get Vista and Win7 and see if they are the same.

---

### Post by Gondrano on 2010-01-04
Hi guys,

I restored my system getting out of the loop thanks to the ibernate button, which let me delete the start-up application. (next time I will use down arrow in booting step)

Unfortunately I have tried several times to change the xinitrc file adding "#" at the beginning of the last line. It just saids that I have no permissions.

So today I tried to open the xinitrc file by terminal, but with no results.

which is the right way?

brezeler@brezeler-laptop:~$ cd linuxwacom-0.8.5-4
brezeler@brezeler-laptop:~/linuxwacom-0.8.5-4$ sudo -i
[sudo] password for brezeler: 
root@brezeler-laptop:~# ./xinitrc.sh
-bash: ./xinitrc.sh: No such file or directory
root@brezeler-laptop:~# ./xinitrc
-bash: ./xinitrc: No such file or directory
root@brezeler-laptop:~# cd /ect/X11/xinit/xinitrc
-bash: cd: /ect/X11/xinit/xinitrc: No such file or directory
root@brezeler-laptop:~#

---

### Post by Favux on 2010-01-04
Hi Gondrano,

You are in the wrong directory.  It is not in your unpacked linuxwacom tar, it is at "/etc/X11/xinit/".  Please see "Section 3: Calibrating your Tablet" at this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by munooka on 2010-01-04
Yeah this is windows XP configuration and linux.
So it would seem that somewhere the mapping has got mixed up. Like bromolex I can change the other keys except for ? using wacomcpl. But there is no left click by default. A toggle may be able to script if you can assign a key to a script.

> **bromalex said:**
> Hi Munooka

Summing up (Buttons from top to bottom)
WinXP
1. Touch toggle
2. Backspace
3. Right click
4. Left click

Linux
2. Middle click
3. Right click
4. Pg Up
?. Pg Dn

Using **wacomcpl** I can change buttons 2. 3. and 4. but not the bottom one.



I can also change using xsetwacom. Bewfore I was only trying to change button 1 (which may be the mystery key). I get this in my dmesg when I click it:

[10715.998719] [wacom-0.8.5-9/1] data: 02 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
[10716.122703] [wacom-0.8.5-9/1] data: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Another issue I had was that I can't seem to move the cursor if the mouse button is depressed.
Anyway this is a great I can't wait to get touch working. Even though its fairly ropey I noticed you can zoom in/out and scroll with two fingers.
Are there plans afoot to have two finger swiping and rotation?

---

### Post by bromalex on 2010-01-04
Bamboo P&T tablet button assignments in Win XP

Top    : Toggle Touch 
MidTop : Back*
MidBot : Right click
Bottom : Left click

* - move Back within browser (???. It is not Backspace or Sh+Left). Can't figure it out.

Attaching screenshot.[ATTACH]142412[/ATTACH]

---

### Post by WvBraun on 2010-01-04
OK,

here I am again with my report:

model: Bamboo Fun CTH-661
kernel: 2.6.31generic
modernized wacom fdi and degrabbyfied synaptics fdi
linuxwacom 0.8.5-9 with patch suggested by ob1kenobi

works: Stylus, pad, touch movement, eraser
sometimes works: scrolling, zooming (OK, maybe I'm not used to it enough)
doesn't work: rotation, swipes

Good work!! Really impressive.

I installed CellWrite and now I will enjoy my tools in inkscap ...

Regards, Daniel.

---

### Post by Favux on 2010-01-05
Hi everyone,

Ob1kenobi updated his patch to .2 (fixing the Capacity issue) for linuxwacom 0.8.5-9 and introduced another to correct a spelling error:  [http://sourceforge.net/mailarchive/forum.php?thread_name=bc07448c1001041824y9af2afei55538dedb3ccb5ca%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=bc07448c1001041824y9af2afei55538dedb3ccb5ca%40mail.gmail.com&forum_name=linuxwacom-devel)  (you might want to check it out Daniel)

Ping has apparently accepted it and it will be in 0.8.5-10:
> The errors under 2.6.26/wacom* is my fault.  I will fix it in -10.
There are other updates from Jason Childs, which will be merged into
-10 too.
From:  [http://sourceforge.net/mailarchive/forum.php?thread_name=167e8a331001051533y17c22353y1523528f9a7dc743%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=167e8a331001051533y17c22353y1523528f9a7dc743%40mail.gmail.com&forum_name=linuxwacom-discuss)

So we might finally be there!  :D

Edit:  Oops.  Spoke too soon.  They want some (hopefully) minor changes.  But ob1's got the attention of both lead dev.s so I think they definitely are interested.


Hi bromalex and munooka,
> Using wacomcpl I can change buttons 2. 3. and 4. but not the bottom one.
I believe the buttons are reported as 2,3,4,5.  Apparently there is a bug in Xorg that is reporting it as 4 buttons and then cuts off the buttons at 4 which is why 5 isn't configurable.  Folks with the old style Bamboo are seeing this with their Touch ring:  [http://sourceforge.net/mailarchive/forum.php?thread_name=200912252140.01694.linux-wacom%40tarottoni.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=200912252140.01694.linux-wacom%40tarottoni.com&forum_name=linuxwacom-discuss)  It sends scroll up (button4) but not scroll down (button5).  The posting is disjointed and not consolidated into 1 thread for some reason so I couldn't find Alexia's patch again.  So anyway apparently this is an Xserver/Xinput problem, not a linuxwacom problem.

---

### Post by javahollic on 2010-01-06
I followed the install instructions (I'm using Jaunty), everything compiles, but I dont seem to get the /dev/wacom or /dev/input/... devices created, and so 'xsetwacom list' gives me nothing as yet.

The driver got installed: 
ls /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko -las
72 -rw-r--r-- 1 root root 71105 2010-01-06 11:34 /lib/modules/2.6.28-17-generic/kernel/drivers/input/tablet/wacom.ko

I can see the device via lsusb:
Bus 001 Device 006: ID 056a:00d4 Wacom Co., Ltd

And have a matching entry in /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules:
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00d4", SYMLINK="input/tablet-wacom-bamboo-pen_touch-$env{WACOM_TYPE}"

Checking 'messages' I see the following:
Jan  6 11:34:21 serv kernel: [  755.624570] usbcore: deregistering interface driver wacom
Jan  6 11:34:25 serv kernel: [  760.309168] input: Wacom Bamboo 4x5 Pen as /devices/pci0000:00/0000:00:13.5/usb1/1-4/1-4.1/1-4.1.3/1-4.1.3:1.0/input/input6
Jan  6 11:34:25 serv kernel: [  760.341638] finger report data:09 30 35 00 46 e0 2e 26 e0 01 75 10 95 01 81 02 09 31 46 40 <7>/usr/local/src/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: features->device_type = 333
Jan  6 11:34:25 serv kernel: [  760.341666] finger report data:09 31 46 40 1f 26 40 01 81 02 06 00 ff 09 01 26 ff 00 75 08 <7>/usr/local/src/linuxwacom-0.8.5-4/src/2.6.28/wacom_sys.c: finger
Jan  6 11:34:25 serv kernel: [  760.341861] input: Wacom Bamboo 4x5 Touch as /devices/pci0000:00/0000:00:13.5/usb1/1-4/1-4.1/1-4.1.3/1-4.1.3:1.1/input/input7
Jan  6 11:34:25 serv kernel: [  760.378004] usbcore: registered new interface driver wacom
Jan  6 11:34:25 serv kernel: [  760.378013] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver

Can anyone suggest something to get the devices hooked up?

---

### Post by Favux on 2010-01-06
Hi javahollic,

Did you install the .fdi?  See [post #579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").  Either the new-generic rc2 or test3.5.

Is the wacom.ko auto-loading?  In a terminal:
```
lsmod | grep wacom
```

---

### Post by Ayuthia on 2010-01-07
Hopefully this does not create confusion for everyone, but I have updated the first post to be based on ob1kenobi's submitted patches based on Favux's message in this [post]("http://ubuntuforums.org/showpost.php?p=8617344&postcount=786").

As usual, I do not have one of these devices so all I was able to do is compile the source to verify that it compiles cleanly.  Please let me know if something is missing.

---

### Post by WvBraun on 2010-01-07
Ah Ayuthia,

I saw, that I'm not able to configure anything regarding touch with wacomcpl :)

(CTH-661, Karmic)

But it is not a big thing... I do not need big config games, as the resent version of the driver does exactly what I want, thanks a lot.

Regards, Wv

---

### Post by Ayuthia on 2010-01-07
> **WvBraun said:**
> Ah Ayuthia,

I saw, that I'm not able to configure anything regarding touch with wacomcpl :)

(CTH-661, Karmic)

But it is not a big thing... I do not need big config games, as the resent version of the driver does exactly what I want, thanks a lot.

Regards, Wv

Can you try going into src/wacomxi/wacomcpl-exec and go to line 1927 wher the code looks like:
```

    # Bamboo Pen and Touch
    for { set i 208 } { $i <= 212 } { incr i 1 } {
        set hasPad($i) 1
        set numPadButtons($i) 4
    }

```
and change it to look like:
```

    # Bamboo Pen and Touch
    for { set i 208 } { $i <= 212 } { incr i 1 } {
        set hasPad($i) 1
        set numPadButtons($i) 4
        set hasTouch($i) 1
    }

```

Hopefully that will allow you to configure touch.  If it does, please let us know and we can get it added.

---

### Post by ob1kenobi on 2010-01-07
Hi all,

I've been posting some patches over on linuxwacom-devel, and we are trying to hash out some changes and get testing on them.  I've attached a patch that get's the bamboo's working with an update to the wacom_ids structure that may have been causing the crashes we initially had.  If anyone has a chance to test this patch against 0.8.5-9 that would be great.  This is a small increment so just the basics should work (Pen and Touch).  Some things that won't work is that touch will single click on first finger down and the scaling issue without restarting x is not in here.  Really it's just a test to see if the spinlocks or the features structure was causing crashes.

Thanks
Ob1

---

### Post by bromalex on 2010-01-08
> **ob1kenobi said:**
> Hi all,
Some things that won't work is that touch will single click on first finger down and the scaling issue without restarting x is not in here.  Really it's just a test to see if the spinlocks or the features structure was causing crashes.
Thanks
Ob1

Hi Ob1

A)
After installation, reboot and then USB plugging my Bamboo P&T CTH-460:
1- using Touch, the cursor always reverts to a position somewhere in the top left quadrant (with left click always on). It is in Absolute mode but the mapping is not right (I called this: Touch crippled).
If I then issue **xsetwacom set touch Mode Relative**, the cursor gets stuck in the left border of the monitor and I have no response.
2- Also I have no Pen.

B)
I then left the Bamboo connected and did a Log Out/Log In and this time the Touch uses Absolute mode but, as you said, with left click always on, and one can use all the laptop screen (Touch OK).
This time a **xsetwacom set touch Mode Relative**, gives me Relative mode.

C)
I then disabled Touch with **xsetwacom set touch Touch off** and tested the Pen. It all seems fine*: Stylus, Eraser, pressure, Pen buttons, etc

D)
The 4 tablet buttons work as Middle click, Right Click, PageUp and PageDown. Didn't try to remap them, because I think you and the other developers still didn't fix the impossibility we have to change the bottom button (and also to deliver us a Toggle touch function assigned to the Top tablet button, as the Windos$ driver has).

E)
I then suspended the laptop and it resumed normal operation with the tablet. Stylus operational :-) Remember Touch was off.

F)
But if I unplug and replug my Bamboo, the behaviour is as I described when I first plugged the tablet after initial installation (A). Touch is present but crippled and I have no Pen. But differently, this time, a Log Out/Log In will only restore Touch function but STILL I have no Pen.

This problem is the reason that I, for daily operation, still use your 0.8.5-4-35 version, that accepts hot-plugging without a problem.

G)
I then tried a restart with the tablet plugged: All is fine. Touch, Buttons and Pen.

H)
Finally I unplugged the Bamboo, restarted the laptop and then plugged the Bamboo:
1- Touch is crippled and Pen is fine.
2- Another Log Out/Log In (still Bamboo plugged) and Touch is fine (apart from left click always on) and Pen is fine.

In summary I liked this version, apart from the hot-plugging that doesn't work, forcing a restart, all seemed stable and I had no crashes in the limited time that I tested this.
Honestly I can't find any differences between this third patch version and the previous (patch 2) were you had those _spinlock_ instructions.  

Hope you can make some sense of the Touch/Pen behaviour with these variables: Restart, Log out/in and USB plug in/out.

Sorry for such a long text (maybe I could have spared some words).
If you need more help or if my English was not clear at some point, just ask.

Bye

PS:* my only complaint is that in the drawing software **MyPaint** (and only with this program, not in **Gimp** or **Inkscape** or **Xournal**) if I wiggle around the pen without actually touching the tablet and sometimes force a light touch with my hand (to elicit a Touch white light) as I move the pen, sporadically it will draw very faint lines. It looks as if, despite Touch is off, the tablet is still responding to these inputs and **MyPaint** translates that as Stylus very light strokes. This effect I feel is less pronounced in this version, than in all previous ones.

---

### Post by WvBraun on 2010-01-10
@ Ayuthia: Yep - this does the trick. Thanks :)

I just noticed now, that wacomcpl does not allow configuring things like abs./rel. mode - is this not possible by design?

Regards, Wv

---

### Post by 289Shelby on 2010-01-10
Can someone advise on what the problem is here please.

This is a Bamboo Pen on Hardy using linuxwacom 0.8.5-9

From Xorg.0.log

```

EE) touch: No type or invalid type specified.
Must be one of stylus, touch, cursor, eraser, or pad
(EE) PreInit returned NULL for "touch"
(EE) stylus: No type or invalid type specified.
Must be one of stylus, touch, cursor, eraser, or pad
(EE) PreInit returned NULL for "stylus"

```

The tablet seems to show up in all the right places but so far I have been unable to get any reaction out of it at all.

Thank you.

---

### Post by Favux on 2010-01-10
Hi 289Shelby,

I can't tell for sure from what you posted, but did you apply the patches to 0.8.5-9 that Ayuthia and ob1kenobi are working on?  They are in the first post of this thread.  What you've posted seems consistent with straight 0.8.5-9 without the patches.

---

### Post by 289Shelby on 2010-01-11
Thanks for replying Favux.

Yes, I did apply those patches. That was the first thing I did following the guide on that page. Is it possible that for some reason they didn't 'take' correctly?

---

### Post by 289Shelby on 2010-01-11
Some progress. I went back to the first page and started again. I can now move the cursor with the pen and use the buttons on the pen.:-)

Xorg.0.log still shows the same error msgs.

Wacdump doesn't show the make or model but I can move the cursor around.

xxd produces no output.

---

### Post by Favux on 2010-01-11
Hi 289Shelby,

It doesn't sound like you are noticing errors when patching or compiling.  And you'd get an error if you weren't copying the wacom.ko in place with:
```
sudo cp src/2.6.24/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/

```
Maybe the problem is with your xorg.conf configuration?  I have a couple of sample xorg.conf's here:  [http://ubuntuforums.org/showpost.php?p=8165182&postcount=384](http://ubuntuforums.org/showpost.php?p=8165182&postcount=384)  Notice you need the symlink rule in wacom.rules to use the symlink.

---

### Post by 289Shelby on 2010-01-11
Thanks Favux.

I wasn't aware of any compile or patching errors but I could have missed them if there were any.

Output of locate wacom.ko

```

/lib/modules/2.6.24-26-generic/kernel/drivers/input/tablet/wacom.ko

```

The symlink rule in wacom.rules

```

ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00d4",  SYMLINK+="input/tablet-bamboo-pen"

```


I'm going to alter xorg.conf. At the moment I've got stylus, cursor, eraser and pad in there. It looks like I should just have stylus.

Edit: The xorg.log file still shows the same errors. It's looking like compile/patch errors that I haven't noticed. Maybe time to start again from scratch.

---

### Post by Favux on 2010-01-11
That's right the stylus and the stylus buttons.  No eraser, unfortunately.  And of course Hardy doesn't use:
```
Identifier	"X.org Configured"
```
in "ServerLayout".

Did you also remove the lines for eraser, touch, and pad from "ServerLayout"?

---

### Post by 289Shelby on 2010-01-11
> **Favux said:**
> 

Did you also remove the lines for eraser, touch, and pad from "ServerLayout"?

Yes I did.

Do you think it might help if I re-did it using the pre-patched version in order to eliminate any patching errors at least?

It seems to be working OK so maybe a case of 'leaving well alone'.

---

### Post by mikelward on 2010-01-16
Hi Guys

Favux on the linuxwacom-discuss list pointed me to this thread.

All the basics of my Bamboo Touch now seem to be working.

Will do some more reading to see how to increase the sensitivity, improve accuracy (possibly conflicting goals, but the Windows driver seems to be more sensitive AND more accurate), and enable gestures if that's supported.

But for now, just wanted to say thanks!

Only other thing I don't think the docs mention is that I had to issue
```
export CPPFLAGS="-I/usr/include/dbus-1.0"
```

before running
```
./configure --enable-wacom
```

---

### Post by bromalex on 2010-01-16
Hi Mikelward

The developers are working hard to give us a better driver. We have to be patient.

I have a Pen & Touch and I also consider the Touch function not fully usable. So much, that I usually turn it off and only use the Pen.

Bye

---

### Post by mikelward on 2010-01-16
> **bromalex said:**
> The developers are working hard to give us a better driver. We have to be patient.

Sorry if that sounded like a complaint.  It wasn't.  :)

I'm very glad people are working on this.

---

### Post by gomar on 2010-01-18
I too finally got my Bamboo Pen & Touch running using the linuxwacom-0.8.5-4-35.tar.bz2 archive and HAL. Thanks guys for your efforts! :D

One minor niggle remaining is the pad's four buttons: I haven't managed to map them to specific actions in Inkscape.

I've verified that they work by running xidump on the pad device, and they also have some generic actions assigned.  Yet whether I leave them on defaults or map them to 0 (via xsetwacom, to disable the default assignment), they don't do what I configure them to in Inkscape (and not in Gimp either, which appears to use the same means of configuration). :(

Has anyone managed to set up his Bamboo Pen & Touch's pad buttons for custom actions in Inkscape or the Gimp?  If so, I'd much appreciate any pointers as to how this has been accomplished.

On a second minor niggle: For some reason, I need to keep my Windows key (mapped to Meta) pressed in Inkscape if I want to use the stylus's lower button's default assignment (MMB equivalent) to pan the drawing area.  If I don't do this, moving the stylus while holding down the button tends to rotate my Compiz desktop cube.  Yet this doesn't happen all the time.  I have not yet figured out whether this is related to my particular configuration of Compiz's "Rotate cube" functionality.  Very odd indeed, but I guess this at least is an Inkscape issue, as the Gimp is not affected.

---

### Post by bromalex on 2010-01-18
Hi Gomar

As far as I know it is still not possible to map all the pad buttons. Using **wacomcpl** you can map the 2 middle buttons, but the top one is always mapped to middle mouse click and the bottom one is always PgDown.
You can try **wacomcpl** also to remap the stylus buttons (I've never tried).

Unless someone knows better, I guess we have to wait for a more refined driver version.

I believe the developers are now more dedicated to making the touch function perfect (as it is still rough) together with the gestures for zoom and scroll, etc.

---

### Post by Gondrano on 2010-01-19
Hi Guys,

I have succesfully installed the usb wacom CTH-460 tablet drives.

**I wonder which was the file (log?) that make troubles because grow bigger and bigger.**
I would like to fix it before it start to record imput errors. Can anyone tell me how to do that? Or show me the last post that explain it? 

I used the belowing files:

   -linuxwacom-0.8.5-9-prepatch 
   -Favux_new-generic_rc2_10-linuxwacom.fdi

**Besides I am left-handed. Is there the possibility to "turn" the tablet?**

thanks in advance

---

### Post by Ayuthia on 2010-01-19
> **Gondrano said:**
> Hi Guys,

I have succesfully installed the usb wacom CTH-460 tablet drives.

**I wonder which was the file (log?) that make troubles because grow bigger and bigger.**
I would like to fix it before it start to record imput errors. Can anyone tell me how to do that? Or show me the last post that explain it? 

I used the belowing files:

   -linuxwacom-0.8.5-9-prepatch 
   -Favux_new-generic_rc2_10-linuxwacom.fdi

**Besides I am left-handed. Is there the possibility to "turn" the tablet?**

thanks in advance

In that version, there are no debug commands in the code so you should not get any in /var/log/messages.  The .fdi also does not set any debugging modes so there should not be anything being logged to /var/log/Xorg.0.log.

As for turning, I am not for sure if it is operational yet or not.  If it is, the command should be:
```
xsetwacom set stylus rotate X
```
Just replace the X with a number between 0 to 3.  0 is normal, and I forgot what the other ones are (either left, right, or inverted).  Favux or someone else can probably explain it better.

---

### Post by Gondrano on 2010-01-19
Hello Ayuthia, 

thanks for the answer I will immediately start to draw.
Unfortunately the next command:
xsetwacom set stylus rotate Xdo not seem to work. I tried also typing it in root by terminal, but nothing.
Maybe I need to reboot? I'll try it. Nope does not work.

---

### Post by Favux on 2010-01-19
Hi Gondrano,

He meant:
```
xsetwacom set stylus rotate HALF
```
or instead of HALF you should be able to use 3.

But since you want the tablet left-handed permanently it's probably best to place:
```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```
in your 10-linuxwacom.fdi

In the section headed by:
```
<!-- for all Wacom USB tablets -->
```
place it after the stylus line like so:
```
<merge key="input.x11_options.Type" type="string">stylus</merge>
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
```

In the section headed by:
```
<!-- for most Wacom USB tablets with touch -->
```
place it after the touch line:
```
<merge key="input.x11_options.Type" type="string">touch</merge>
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
<!-- for Bamboo Pen & Touch tablets -->
```

And we need to figure out what's filling up your log file since it shouldn't be the patched linuxwacom drivers.  Take a look at your Xorg.0.log in /var/log/.  If you see something you want us to look at right click on it and compress it with Create Archive.  Then attach it to your next post with Manage Attachments.

Edit:  I updated [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") with the rotation stuff for lefties.

---

### Post by Gondrano on 2010-01-19
Thank you very much! It work perfectly!

favux says:
"And we need to figure out what's filling up your log file since it shouldn't be the patched linuxwacom drivers. Take a look at your Xorg.0.log in /var/log/. If you see something you want us to look at right click on it and compress it with Create Archive. Then attach it to your next post with Manage Attachments."

I do not know if is my log filling up (I don't think is filling up, I only wanted to be sure it does not ), Ayuthia said it schould not does that with the files I had used:

-Favux_new-generic_rc2_10-linuxwacom.fdi.txt
-linuxwacom-0.8.5-9-prepatch.tar.bz2

ps Sorry for the quote! :(

pss Should be no problem if I delete all tar and fdi file in downloaded and personal folder, right?

---

### Post by Favux on 2010-01-19
Hi Gondrano,

Great!

> Should be no problem if I delete all tar and fdi file in downloaded and personal folder, right? 
No, but it is probably a good idea to keep them as backup copies in your /home/username directory.  Just make a new folder with a name you like and place them in it.  Then drag it to where you want in Nautilus.

---

### Post by JW3 on 2010-01-21
Hi, 

what is the most recent, recommended way of installing a Wacom Bamboo Pen & Touch Medium tablet? (0xd3)

I have followed the instructions from [here]("http://ubuntuforums.org/showthread.php?p=8262965#post8262965"), but I am not sure whether this is still the right way to go. The tablet works nicely, but only the pen -- not the buttons and not the "touch" (not that it matters much).

It would be extremely helpful if there was an edit labeled with a recent date in the OP of the thread.

Kind regards, and thanks for all the work you are doing!

---

### Post by WvBraun on 2010-01-21
Hi JW3,

with 0xd3 you just follow the OP on this thread. I just tried it and it works as expected.
This is the best you can do so far.

Regards, Wv

---

### Post by zebarbu on 2010-01-22
Hi folks,
I just received my bamboo P&T (0x00d1), thanks for your work for making it working on Linux ! (karmic64 for my case)

Aside the fact I miss a better touch support (precision) and gestures, I would like to know **if there is a way to set a threshold on stylus in both ways** :
[LIST]
[*]make it recognize only when it really touches the tablet (and not as far as ~10mm above it)
[*]make it clic only when I press more than x% of its possible pressure
[/LIST]

=> I use it as the mouse (as long as the touch is not much usable for that), but I find it would be better that way for that use... any idea ?

and once again, _thanks for all, devels_ ! I 'complain' about things not yet done, but really appreciate what you have already done !

---

### Post by zebarbu on 2010-01-22
ok, found that ```
xsetwacom set stylus  Threshold 400
``` allows me to put the stylus on the tablet and move without making it clic. It only clics if I press slightly harder, cool :)

So there is still only one question (for now ;) ) :
**Is there any way to avoid cursor's position be updated when the stylus doesn't touch the tablet ?** Really annoying on Relative mode...

---

### Post by ob1kenobi on 2010-01-23
Hi all,

Here is a new combined bamboo p&t patch for linuxwacom-0.8.5-9.  Hoping some people can test it and provide feedback.  This should get everything on the tablet working 95% including touch gestures.  There are now better defaults for the gesture timeouts and they are configurable using xsetwacom such as:

```

xsetwacom set "Wacom_Bamboo_P&T_4x5_Touch" RightClickDistance 100

```If you still have a fdi file that renames the device, it will be
```

xsetwacom set touch RightClickDistance 100

```The new configurable items are:

```

RightClickDistance : maximum finger spacing allowed for a right click touch gesture
ZoomPinchDistance : minimum distance required before starting a zoom touch gesture
ActivateDistance : minimum finger motion distance required for starting any gesture
ScrollActivateDistance : minimum finger motion distance required for starting a scroll gesture
GestureTapTime : maximum time between events required to start a gesture

```If you have 6x8 tablet you will need to update these defaults probably, and if anyone can post what works best for them for either tablet size, I can update the defaults.  The defaults work for me on my 4x5.

Thanks,
Ob1

---

### Post by zebarbu on 2010-01-23
Just tested, it provides better default values for the touch, but the only gesture I get is the zoom... No scroll, no right button, etc... tested on karmik64 with P&T (0xd1)

edit0 : few 'bugs':
[LIST=1]
[*]the touch 'button1' is not remapable ```
xsetwacom set "Wacom_Bamboo_P&T_4x5_Touch" Button1 "core key quotedbl touch space button1 space pressed quotedbl"
``` does nothing, the clic is still passed to X.
[*]the touch_pad buttons are wrong: 1&2 correct, 3=1 and 4=2
[/LIST]
I test buttons of each device (all found in xsetwacom list) with this:
```

function initIt()
{
        DEVICE="$1"

        xsetwacom set $DEVICE Gesture on

        (( i=1 ))
        while [ $i -lt 33 ];
        do
#init all buttons to display a string
                xsetwacom set $DEVICE Button$i "core key quotedbl ${DEVICE} space button$i space pressed quotedbl" 2>/dev/null

#set default button
#                xsetwacom set $DEVICE Button$i "button $i" 2>/dev/null
        (( i=${i}+1 ))
        done

        for event in RelWUp  RelWDn AbsWUp  AbsWDn StripLUp StripLDn StripRUp StripRDn
        do
#init all gestures to display a string
                xsetwacom set $DEVICE $event "core key quotedbl $DEVICE space $event space pressed quotedbl"

        done
}


```

---

### Post by permeakra on 2010-01-24
> **ob1kenobi said:**
> Hi all,

Here is a new combined bamboo p&t patch for linuxwacom-0.8.5-9.  Hoping some people can test it and provide feedback. 
I tested it. It does work on my gentoo system after i patch original config.in to disable xf86config . However, 60-wacom.rules from debian herd did not work on my system, I had to comment string with KERNEL!="event[0-9]*" to make device working.

thanks a lot!

---

### Post by zebarbu on 2010-01-24
> **permeakra said:**
> I tested it. It does work
you mean gestures works ? you get scroll, pitch, rotate, ... events ?
can't manage to have them :(

---

### Post by permeakra on 2010-01-24
> **zebarbu said:**
> you mean gestures works ? you get scroll, pitch, rotate, ... events ?
can't manage to have them :(
click, double click, scroll did work
rotate was not tested
right click and back/forward does not work (possible reason is mapping to incorrect mouse events)

after checking i can say, that udev rules did work. I do not understand, why when no correct wacom module loaded we need to comment filter rule to appear /dev/input/wacom and with driver do not. Looks unnatural for me.

---

### Post by texaswriter on 2010-01-24
Hi, many thanks to Ayuthia and Favux and everybody else for getting these new Wacom tablets working on Linux. That's definitely a life saver for me at school. 

OK, I did a fresh install of my Dell recovery CD [Ubuntu Jaunty] and then upgraded to Karmic [net install as the CD gave errors upgrading last I attempted]. 

I then followed the instructions from the *very* first post of this thread by Ayuthia. These instructions also include the commands to set the touch to act like the synaptic touch pad. [also the resolution thing...]

For the most part, things work to my satisfaction. Pen works great, driver loads each time I restart. Hotplugging/replugging works perfectly. I do have to run the commands every time I relog [aka set touch to act like mouspad and bottomx/y coords]. Also, clicking still acts like pen [aka leaves a mark in jarnal]. So clicking is like touching the pen down. 

This post has been provided in case there are any updates being made within the patched driver provided. There are my results anyways. 

In no way is it a post of dissatisfaction, as the support is enough for my purposes. I am not using the pen for art, but rather just for taking notes. 

If anybody has any suggestions that may be of help, I would of course welcome them, otherwise let me know if you need me to test any features. I'm familiar enough with Linux to be of help in that regard.

Thanks again to the hard work of all in this thread and of course at open source wacom @ sourceforge. 

:popcorn:

---

### Post by bromalex on 2010-01-24
> **ob1kenobi said:**
> Hi all,
Here is a new combined bamboo p&t patch for linuxwacom-0.8.5-9.  Hoping some people can test it and provide feedback....
Thanks,
Ob1

Hi Ob1

I am trying 0.8.5-9 with your latest patch. Excellent work!

For me, Touch wise, it is the best I've experienced.

Touch problems:

1)
Occasionally the cursor will jump to some seemingly random point on the screen.

2)
Occasionally the cursor will engage a left click as you move around. It just dragged one of my Gnome-Do/Docky icons to the desktop making it disappear in a smoke cloud to never be seen again :-( 

3)
The scrolling behaviour is opposite to what I expect (and the way Window$ driver functions):
 - 2 fingers on Bamboo. Drag them downwards. The scroll bar will move upwards and vice-versa. (I expect drag down/scroll down).

4)
The zoom gesture (2 fingers in the centre and spreading them to zoom in) is not consistent.
I get a better zoom-in zoom-out with the same gesture used for scrolling. Maybe this is a program related behaviour.
I should add that I am using the same conventions that are referred in the Window$ manual. As everyone who buys a Bamboo will receive that PDF manual, I think this should be taken into account.

Tablet Buttons:

A)
The default (top to bottom) and the **wacomcpl** button numbers are
left Click - Button 1
Middle - Button 2
left Click - Button ????
Right click  - Button 3

Again, as per Window$ and for consistency, I would like the 2 bottom buttons to be Right click and Left Click, instead of Left Click and Right click as it is now. But since I couldn't change The Button ???? assignment...

B)
A touch toggle button would be phenomenal. I find that when drawing with the stylus, the Touch gets in the way.
Again (and I promise I'll never mention Win$ again) there, the top button is a Touch Toggle.

Don't get the impression that I am whining and complaining too much. I find the current state a tremendous improvement on Touch function.
We all thank the hard work from the developers.

And I'll add that if it was not from the work that started here in Ubuntuforums with Ayuthia, Favux and Ob1kenobi, I have the impression that our Bamboos would still be waiting, gathering dust, because all I hear from the official Wacom Linux driver developer is that is has some real urgent matters to attend and, in his hands, it seems that Bamboo is still not a priority!

---

### Post by bromalex on 2010-01-24
**TOUCH TOGGLE FUNCTION**

While we wait for a Touch Toggle function assigned to the top Bamboo tablet button, I used [Favux information]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1") to generate an alternative.

Generate a file named "Bamboo_touch_toggle.sh" (for eg.)
with this content:
```
#!/bin/bash

STATUS=`xsetwacom get "Wacom_Bamboo_P&T_4x5_Touch" touch`
if [ "$STATUS" == "0" ]
  then
    echo "Touch was OFF, enabling."
    xsetwacom set "Wacom_Bamboo_P&T_4x5_Touch" touch on
else
    echo "Touch was ON, disabling."
    xsetwacom set "Wacom_Bamboo_P&T_4x5_Touch" touch off
fi

```Save file in your home directory. Right click>Properties>Permissions>check Allow executing...

In Gnome panel>Right click>Add to panel>Custom Application Launcher>Add

Give it a Name
Use for Command: /home/xxxxx/Bamboo_touch_toggle.sh
 (change path appropriately)

Now I can turn Touch on and off as needed by clicking this Launcher.

EDIT:
I downloaded this icon [IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Gnome-input-tablet.svg/120px-Gnome-input-tablet.svg.png[/IMG] ([http://commons.wikimedia.org/wiki/File:Gnome-input-tablet.svg](http://commons.wikimedia.org/wiki/File:Gnome-input-tablet.svg))
and assigned it to the Launcher.

[COLOR=Red]EDIT: With linuxwacom-0.8.5-10 one has to change this script. See [Post#897]("http://ubuntuforums.org/showpost.php?p=8832768&postcount=897")[/COLOR]

---

### Post by texaswriter on 2010-01-24
Having used the tablet a bit more now, I second Bromalex's post about the functioning of touch. Also, eraser function doesn't work as expected.

---

### Post by bromalex on 2010-01-24
> **texaswriter said:**
> Having used the tablet a bit more now, I second Bromalex's post about the functioning of touch. Also, eraser function doesn't work as expected.

I have no problems with the eraser, as far as I can tell.

What's wrong?

---

### Post by texaswriter on 2010-01-24
Great to hear. Mine actually *does* work, just not as an eraser. Eraser function writes... same as pen function I believe.

---

### Post by bromalex on 2010-01-24
Hi texasrider

Could you try in GIMP.

Menu Edit>Preferences>Input Devices>Configure Extended Input Devices
Then choose Device>Wacom Bamboo P&T ... Pen>Mode:Screen
Then choose Device>Wacom Bamboo P&T ... Pen eraser>Mode:Screen
Choose Save.

Use the eraser side of the pen and select the Gimp's Eraser Tool. Now turn pen to stylus side and select Airbrush Tool (for ex.)
Start drawing and then try to use the pen's eraser side to erase. It should work and with pressure sensitivity both in pen and eraser.

---

### Post by texaswriter on 2010-01-24
> **bromalex said:**
> Hi texasrider

haha, funny. 



> **bromalex said:**
> Could you try in GIMP.

Menu Edit>Preferences>Input Devices>Configure Extended Input Devices
Then choose Device>Wacom Bamboo P&T ... Pen>Mode:Screen
Then choose Device>Wacom Bamboo P&T ... Pen eraser>Mode:Screen
Choose Save.

Use the eraser side of the pen and select the Gimp's Eraser Tool. Now turn pen to stylus side and select Airbrush Tool (for ex.)
Start drawing and then try to use the pen's eraser side to erase. It should work and with pressure sensitivity both in pen and eraser.

OK, gotcha, yes, in Gimp, with the above settings, I could set different tools for the mouse, stylus, and eraser.. and they all had pressure sensitivity. Not sure how I'd get that working in Jarnal. I don't take notes in GIMP, although probably could [won't though lol]. I did actually try the same trick in Jarnal, it just doesn't work the same way. Stylus and eraser seem to be the same thing elsewhere [including when used as a mouse in the rest of the ui].

---

### Post by bromalex on 2010-01-24
> **texaswriter said:**
> I don't take notes in GIMP, although probably could [won't though lol].

Did you try **Xournal**?

Here you get pen and eraser working.

Bye

PS: sorry for the mistake "texaswriter" :)

---

### Post by texaswriter on 2010-01-24
LOL, didn't come here looking for help, still got some great useful help. :D 

Yeah, I tried Xournal and it works great, Just had to enable eraser tip in Options... Also has pressure sensitivity. 

Thanks alot Bromalex
:popcorn::KS:D

---

### Post by HansHeinrich on 2010-01-26
Many thanks for the great work! Switching btw Pen and Eraser seems to be working fine.
Touch did not quite work as expected out of the box (only using part of the screen, gestures do not seem to work). Being a Wacom-Newbye, I'll now do my homework of checking for proper configuration options :D
__
Ubuntu 9.10

---

### Post by munooka on 2010-01-29
Sorry I haven't had time to test the patch till now.

It certainly is the best yet, great work Ob1. 
The buttons seem to be performing correctly mapped, movement works much better (although it still jumps every now and again) and I no longer get lock ups in touch mode. The pen worked out-of-the-compile, and I get full eraser, pen and touch functions which I have set up for eraser, paint/draw and select, respectively in gimp and inkscape ("Nice", said in a jazz voice).

A couple of minor irritations:
1) Double finger right click appears to be non-functional.
2) Two finger scroll is counter intuitive so when I move up the screen scrolls down and vice versa. Left and right on GIMP and INKscape work as expected but are a bit jerky.
3) Gestures in general seem a bit buggy. I will play around with the parameters in your post to see if its just my Ogre like fingers that are the problem [-X .
4) Zoom gestures do not work on Inkscape or GIMP. Is this a bug or were they never supported?
5) Will swiping be supported at some point? I noticed that you can use a two finger swipe on windows for back and forward.


> **ob1kenobi said:**
> Hi all,

Here is a new combined bamboo p&t patch for linuxwacom-0.8.5-9.  Hoping some people can test it and provide feedback.
Ob1

---

### Post by texaswriter on 2010-01-30
How would I go about testing a new "round" of patches. Would I have to completely uninstall drivers? I used the pre-patched drivers from post #1. Tia.

---

### Post by munooka on 2010-01-30
The drivers install over the top of the current files. I  did this:
```
wget -N http://downloads.sourceforge.net/project/linuxwacom/linuxwacom-dev/0.8.5-9/linuxwacom-0.8.5-9.tar.bz2
tar -xvjf linuxwacom-0.8.5-9.tar.bz2

```
downloaded ob1's patch from post [818]("http://ubuntuforums.org/showpost.php?p=8711822&postcount=818") to the ***_same_*** directory as the linuxwacom-0.8.5-9.tar.bz2 file.
```

cp linuxwacom-0.8.5-9-bamboo-patch-set-v2.patch.doc ./linuxwacom-0.8.5-9/linuxwacom-0.8.5-9-bamboo-patch-set-v2.patch
cd linuxwacom-0.8.5-9
patch -p1 < linuxwacom-0.8.5-9-bamboo-patch-set-v2.patch

```
then compiled the code as normal
```

make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
sudo modprobe -r wacom
sudo modprobe wacom

```

> **texaswriter said:**
> How would I go about testing a new "round" of patches. Would I have to completely uninstall drivers? I used the pre-patched drivers from post #1. Tia.

---

### Post by texaswriter on 2010-01-30
> **munooka said:**
> The drivers install over the top of the current files. I  did this:


K, thanks, I'll do that next day off of school & work and then post results/changes...

---

### Post by palsehmi on 2010-02-01
> **Ayuthia said:**
> This thread is the development thread for the Wacom Bamboo Pen and Touch series tablets (0xd1, 0xd2, 0xd3, and 0xd4 devices).  We are trying to develop the patches to submit to the linuxwacom source.  We currently have the pen portion working for the device and if you would like to try it out, please follow the instructions in [post 541]("http://ubuntuforums.org/showpost.php?p=8262965&postcount=541") from this [thread]("http://ubuntuforums.org/showthread.php?t=1290251").  If you want to help in the testing of the device, please continue.

Just a little note of warning, this is not stable code.  There are going to be times where the code might not work.

We are going to try a different approach on getting the driver installed.  To make sure that you have all the development tools:
```
sudo apt-get update
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get install libhal-dev
sudo apt-get build-dep xserver-xorg-input-wacom
```
Do the following if you are NOT using Karmic:
```

sudo apt-get purge wacom-tools xserver-xorg-input-wacom

```
If you are using Karmic also include the following:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h

```

We are going to test out the 0.8.5-9 version based on ob1kenobi's submitted patch.
**Option A**
For now I have created a pre-patched source that you can download [here]("http://linuxfans.keryxproject.org/packages/wacom/builds/linuxwacom-0.8.5-9-prepatch.tar.bz2").
Unpack the source:
```

tar -xvjf linuxwacom-0.8.5-9-prepatch.tar.bz2
cd linuxwacom-0.8.5-9-prepatch

```
Then jump to the compile and install section below.

**Option B**
You can retrieve this version from [here]("http://downloads.sourceforge.net/project/linuxwacom/linuxwacom-dev/0.8.5-9/linuxwacom-0.8.5-9.tar.bz2?use_mirror=cdnetworks-us-2").  Attached at the bottom of this post is the current set of patches for the source.  

Prepare the source for patching:
```
tar -xvjf patches-0.8.5-9.tar.bz2
cp patches-0.8.5-9/* linuxwacom-0.8.5-9
cd linuxwacom-0.8.5-9
```

Patch the source:
```

patch -p1 < linuxwacom-0.8.5-9-2.patch
patch -p1 < linuxwacom-0.8.5-9-spelling.patch

```

Compile and install:
```
make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
```
To reload the module:
```
sudo modprobe -r wacom
sudo modprobe wacom
```
NOTE: The 'make clean' and 'make distclean' will produce an error message if you have not done a ./configure before.  This is because the source has never been compiled yet and the Makefiles have not been created yet (the Makefile gets built with the ./configure command).  Therefore there is nothing to clean up.

**Some helpful xsetwacom commands**
To set your touch so that it works like a mouse touchpad:
```

xsetwacom set touch Mode Relative

```
To set the resolution of your touch (Example is for the medium sized tablet -- the small is X=480 Y=320):
```

xsetwacom set touch bottomx 740
xsetwacom set touch bottomy 500

```
To turn the touch on/off:
```

xsetwacom set touch Touch off
xsetwacom set touch Touch on

```

If there are any corrections that need to be made, please let me know.

Here is the link to the patches: 
[patches-0.8.5-9.tar.bz2]("http://linuxfans.keryxproject.org/packages/wacom/builds/patches-0.8.5-9.tar.bz2")
and for those who want to just build and go, here is the pre-patched source:
[linuxwacom-0.8.5.9-prepatch]("http://linuxfans.keryxproject.org/packages/wacom/builds/linuxwacom-0.8.5-9-prepatch.tar.bz2")

It looks like there are still some adjustments needed for the .fdi files.  Please refer to this [post]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").
Thank you, this worked for me without any issues. I am using a Bamboo Fun Medium Pen & Touch with Karmic 9.10 - release 18.

---

### Post by Fabian Lamers on 2010-02-02
Thanks for all the work and sharing.

I am using a Bamboo Fun Medium Pen & Touch and allmost everything is working for me.
Tapping too click doesn't work for me. 
Isn't that supported yet or is there something that i can do about that?

---

### Post by gunar on 2010-02-02
**great work!** 
for me the mini howto by Ayuthia worked great!

only point is that **eraser doesn't work at all**. which means that eraser input doesn't move the mouse. moreover eraser (and pad) doesn't appear in wacompl... (there is only touch and stylus)

**is there any knowledge about this error?**

thanks!

---

### Post by zebarbu on 2010-02-02
for me, both stylus and eraser are working, but no gestures or click on touch :(

---

### Post by WvBraun on 2010-02-03
This is for the german speaking audience:

Some other Wacom owner and I made up a german article on the ubuntuusers.de-wiki. This article describes how to get a Wacom tablet working on the recent version of Ubuntu.
It is now in the staging phase. It is open for contributions and improvement.

Take a look at : [http://wiki.ubuntuusers.de/Baustelle/Wacom_USB-Tabletts](http://wiki.ubuntuusers.de/Baustelle/Wacom_USB-Tabletts)

The article is based on our own experience and the contributions to this thread here on ubuntuforums.org.
We would appreciate you comments and suggestions.

Thanks again for the great efforts and your good work in the  development of the project.

Vielen Dank, Wv

edit: typo

---

### Post by syco on 2010-02-07
hello, I apologize once for my English but I also have problems using wacomcpl. I have an HP tx2500 tablet. I configured the touch and Digitalizer through xorg.conf but the configurator does not start. the error is this:
```
wacomcpl: using TCLLIBPATH="[list  /usr/lib ]"
Error in startup script: Get: Unknown parameter 'SBottomX8'
    while executing
"exec xsetwacom get $dev SBottomX$i "
    (procedure "createScreenList" line 7)
    invoked from within
"createScreenList $dev"
    (procedure "createDeviceList" line 38)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/bin/wacomcpl-exec" line 2062)
```
seems to me a case of "out of bound" given that the possible parameters are SBottomX0-SBottomX7. someone had already asked on page 72, but from the discussion I did not understand if it is possible to solve.
However there is another way to calibrate the device?

---

### Post by texaswriter on 2010-02-07
Hi, just a heads up. I think the new kernel change yesterday for Karmic [I think yesterday, coulda been Friday as well] broke wacom driver. It loads [I even sudo modprobe wacom] but there is no functionality whatsoever of the Wacom tablet.   I have a CTH-460/K fwiw.   BTW, I did load the previous kernel from the loader and the driver loads fine and the functionality is returned.   Hope this helps.

---

### Post by texaswriter on 2010-02-07
> **syco said:**
> hello, I apologize once for my English but I also have problems using wacomcpl. I have an HP tx2500 tablet. I configured the touch and Digitalizer through xorg.conf but the configurator does not start. the error is this:
```
wacomcpl: using TCLLIBPATH=&quot;
[list  /usr/lib ]&quot;
Error in startup script: Get: Unknown parameter 'SBottomX8'
    while executing
&quot;exec xsetwacom get $dev SBottomX$i &quot;
    (procedure &quot;createScreenList&quot; line 7)
    invoked from within
&quot;createScreenList $dev&quot;
    (procedure &quot;createDeviceList&quot; line 38)
    invoked from within
&quot;createDeviceList &quot;
    (procedure &quot;createControls&quot; line 8)
    invoked from within
&quot;createControls&quot;
    (file &quot;/usr/bin/wacomcpl-exec&quot; line 2062)
```seems to me a case of &quot;out of bound&quot; given that the possible parameters are SBottomX0-SBottomX7. someone had already asked on page 72, but from the discussion I did not understand if it is possible to solve.
However there is another way to calibrate the device?

 Try this thread out, may do you some good, may not... A script made for tablet pc owners. I know the tx2500 is the newer [if not newest model].... Hard to say your results.   [http://ubuntuforums.org/showthread.php?t=1327867](http://ubuntuforums.org/showthread.php?t=1327867)

---

### Post by milkfish on 2010-02-07
> **texaswriter said:**
> Hi, just a heads up. I think the new kernel change yesterday for Karmic [I think yesterday, coulda been Friday as well] broke wacom driver. It loads [I even sudo modprobe wacom] but there is no functionality whatsoever of the Wacom tablet.   I have a CTH-460/K fwiw.   BTW, I did load the previous kernel from the loader and the driver loads fine and the functionality is returned.   Hope this helps.
I can confirm, upgrading to 2.6.31-19 from 2.6.31-18 (x86) broke my CTL-460 tablet input too, I can rebuild the wacom.ko, but insmod complains that File exists.

---

### Post by texaswriter on 2010-02-07
> **milkfish said:**
> I can confirm, upgrading to 2.6.31-19 from 2.6.31-18 (x86) broke my CTL-460 tablet input too, I can rebuild the wacom.ko, but insmod complains that File exists.
Correct, except on my it was upgrading from 2.6.31-17 .


After rebuilding try this

```

sudo modprobe -r wacom
sudo rmmod wacom
sudo insmod wacom
sudo modprobe wacom

```If that works, please post exact commands you did to rebuild wacom.ko.

---

### Post by Favux on 2010-02-07
Hi,

That will happen with every kernel update.  The new directory:
```
/lib/modules/2.6.31-19/kernel/drivers/input/tablet/

```
does not have the compiled wacom.ko in it like:
```
/lib/modules/2.6.31-18/kernel/drivers/input/tablet/

```
does after you used the copy (cp) command:
```
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/

```
First try copying your compiled wacom.ko from your patched unpacked source code tar again.  That should/may work, otherwise you'll have to recompile.

You'll have to do that until the driver supports the P & T, hopefully in Lucid.


Hi syco,

See Jaunty and Karmic Users near the top of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  That has .fdi's and a xorg.conf for your TX2500 as well as other useful stuff.

---

### Post by milkfish on 2010-02-08
Thanks, I was now able to get the module working and have pen functionality on my tablet. I had a script that was sufficient for previous kernel updates but this time required the "modprobe -r" and "rmmod" steps as well:
```
#!/bin/sh
cd $HOME/project/bamboo/linuxwacom-0.8.4-3
./configure --enable-wacom --prefix=/usr
cp ../hid-ids.h /lib/modules/$(uname -r)/build/drivers/hid/hid-ids.h
make
make install
cp src/2.6.31/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
insmod /lib/modules/$(uname -r)/kernel/drivers/input/tablet/wacom.ko 
depmod -e
exit

```(execute with sudo) The line that was failing was the insmod, because the module that came with the kernel had not been removed.

Thanks!

---

### Post by jryoung on 2010-02-08
Hi, firstly, great work from everyone involved in the P&T support. I am actually using Fedora 12 - with xorg 1.7.n and hence have to use the linuxwacom 0.8.5-9 kernel driver and the bamboo branch of the xf86-input-wacom xorg driver. The Pen support on my CTH-460 is working fine (I also have a Intuos 4 medium which works too), but the touch functionality isn't really usable. I can set the **Mode** to **Relative** or **Absolute**, but I have a couple of main issues:
1. It always acts as if I am Left-clicking, so I can't move the Mouse Pointer without dragging something, or clicking on it. 
2. The Mouse Pointer jumps around sometimes to a different part of the screen.
I don't use an xorg.conf, and the output of xsetwacom list is:
/usr/bin/xsetwacom list
Wacom Bamboo P&T 4x5 Pen eraser ERASER    
Wacom Bamboo P&T 4x5 Pen cursor CURSOR    
Wacom Bamboo P&T 4x5 Pen pad PAD       
Wacom Bamboo P&T 4x5 Pen STYLUS    
Wacom Bamboo P&T 4x5 Touch eraser ERASER    
Wacom Bamboo P&T 4x5 Touch cursor CURSOR    
Wacom Bamboo P&T 4x5 Touch touch TOUCH     
Wacom Bamboo P&T 4x5 Touch pad PAD       
Wacom Bamboo P&T 4x5 Touch STYLUS

The CURSOR/TOUCH/PAD/STYLUS words are not part of the device, so xsetwacom would be used like:
xsetwacom set "Wacom Bamboo P&T 4x5 Touch touch" Mode Relative
However - I am not sure that I should really have CURSOR and STYLUS devices for my "Touch" core device, as wouldn't this conflict with the touching?
Also, none of the new settings in xsetwacom work (eg RightClickDistance ) but I did read that they haven't been added to the xf86-input-wacom code yet (not even the bamboo branch).
Any clues to getting the touch working ? in particular, making the click only happen when I tap.

---

### Post by texaswriter on 2010-02-08
> **Favux said:**
> Hi,

That will happen with every kernel update.  The new directory:
```
/lib/modules/2.6.31-19/kernel/drivers/input/tablet/

```does not have the compiled wacom.ko in it like:
```
/lib/modules/2.6.31-18/kernel/drivers/input/tablet/

```does after you used the copy (cp) command:
```
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/

```

OK, sudo cp'ed the file from the 2.6.31-17-generic [for me] to 2.6.31-19-generic. Did have to do a sudo modprobe wacom when I rebooted into 2.6.31-19 kernel. Not sure if I will continue to have to do that [last time it remembered and auto loaded with my wireless driver].

---

### Post by Favux on 2010-02-08
Hi jryoung,

Welcome to Ubuntu forums!

See [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") for the devices.  Your Bamboo P & T does not have a cursor.  That's linuxwacom speak for the Wacom tablet mouse.  The stylus is fine and should be there.

As for the clicking, jumping, etc. you should talk to Chris Bagwell on linuxwacom-discuss.  I don't think he's ported all of the Ayuthia/ob1kenobi code over into xf86-input-wacom yet.  He just solved one of the problems (emitKeysym crash):
> OK, turns out to be simple issue and unique to xf86-input-wacom. It
declares emitKeysym as a static function in wcmCommon.c and provides
no prototype for it in wcmTouchFilter.c.

Aligning prototypes to linuxwacom and it starts working like linuxwacom.
And Peter already applied the patch to xf86-input-wacom.  So I think he's getting closer.

---

### Post by jryoung on 2010-02-09
Hi, just pulled the latest code from the Bamboo branch of xf86-input-wacom and the touch is now usable. Nice. Saw a new property of Gesture value 3, but not the others (rightclickdistance for example). Will be keeping an eye on the updates!

---

### Post by RiBBiT on 2010-02-09
Hi,
Thank you all for the great work. I'm a new Wacom tablet user, and I'm really enjoying it. However I have a strange problem with my Bamboo Pen & Touch tablet. When I slowly move the pen towards the tablet, there is a point when the cursor starts to jump to the top-left corner and back to its original position very rapidly. This happens exactly the same time when the LED on the tablet turns from white to red. Even the LED starts to blink very fast at this point.
I'm not sure whether it is a software related problem, so I would like to know if you could reproduce this bug with your own tablet.

---

### Post by Favux on 2010-02-09
Hi jryoung,

Cool!  They're getting there.  Chris is changing the gesture logic and adding new ones I think.


Hi RiBBiT,

Don't worry you're not alone.

Jason (ob1) and Chris are seeing the jumps too.  Chris says they are a lot less with his changes to gestures.  Ping has added a new filter(s) to touch on the X side.  Right now they're trying to figure out if the kernel side of things is contributing to the jumps and whether they need to add a filter there.  Basically they're not sure they've traced it to the root cause.  Which is what they'd like to do so they can fix it once and for all.

---

### Post by RiBBiT on 2010-02-10
Thank you for your quick reply.

---

### Post by sandr on 2010-02-12
Hi, just wanted to say thanks for all the work. I have a Bamboo Pen (CTL-460) which I use as a substitute for the mouse. This works fine now! (with linuxwacom 0.8.5-9 and patch)
With 0.8.4-3 and patch, I had the problem that the pointer would jump some distance towards the top-left corner every time I took the pen away from the tablet, but this problem has disappeared now.
One thing that does not work out of the box is the eraser in GIMP.

---

### Post by gomar on 2010-02-12
> **sandr said:**
> One thing that does not work out of the box is the eraser in GIMP.

IIRC, the Bamboo Pen has no eraser (in contrast, the P&T does).

---

### Post by texaswriter on 2010-02-12
> **sandr said:**
> Hi, just wanted to say thanks for all the work. I have a Bamboo Pen (CTL-460) which I use as a substitute for the mouse. This works fine now! (with linuxwacom 0.8.5-9 and patch)
With 0.8.4-3 and patch, I had the problem that the pointer would jump some distance towards the top-left corner every time I took the pen away from the tablet, but this problem has disappeared now.
One thing that does not work out of the box is the eraser in GIMP.

FOR the eraser in GIMP scroll back slowly through the pages, it should only be 2-3 pages back at most... Somebody walked me through setting that up... the instructions are more or less the same... you will have to watch for the eraser and stuff to be named SLIGHTLY different in your version of GIMP than what the instructions say.. Otherwise, following them exactly will result in you configuring your eraser tow ork properly.. GOOD LUCK!!!

---

### Post by Ayuthia on 2010-02-12
Hopefully this does not create any confusion for anyone, but there is now a new 0.8.5-10 release and it contains ob1kenobi's patches.  I have updated the first post to reflect the information.  If I missed anything, please let me know.

---

### Post by Favux on 2010-02-12
Hi nossifer,

We need to look at the output of:
```
xinput --list
```
and
```
xsetwacom list
```
Please sepecify which .fdi you're using.  Also did you remember to copy the newly compiled wacom.ko into place?

We should also look at your lshal.  In a terminal:
```
lshal>nossifer_lshal.txt
```
Compress it by right clicking on it and Create Archive.  Then upload it to your post with Manage Attachments.

---

### Post by nossifer on 2010-02-12
Hi Favux.

I did the instructions on Post 1 and it had instructions to copy that .ko file.  The .fdi is the same one as used in the 5-10.  The rest of the stuff you asked for is attached (including an error message)

EDIT:  I am going to try back on my normally used laptop (XPS).  I can post back the results, and if you like include a similar attachment if it helps you diagnose stuff.

---

### Post by Favux on 2010-02-12
Hi nossifer,

I'm out the door (way late) but it's looking like in your lshal the new .fdi (that's what you're using right?) is making a hash of things.

I'll look at it later.  In the mean time you could try the new-working .fdi on [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

---

### Post by nossifer on 2010-02-12
> **Favux said:**
> Hi nossifer,

I'm out the door (way late) but it's looking like in your lshal the new .fdi (that's what you're using right?) is making a hash of things.

I'll look at it later.  In the mean time you could try the new-working .fdi on [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

Hi,

Tried the new-working, and it seems to behave similarly: no touch.  The stylus is working, and that will keep carpal away.  Touch is a bonus and the gestures is really the super-bonus.  Have a great weekend.

---

### Post by Favux on 2010-02-13
Hi nossifer,

With the new-working do you see eraser in xsetwacom?  With it xsetwacom should look something like:
```
stylus		stylus
eraser		eraser
touch		touch
pad		pad
```
Basically what's happening with the default wacom.fdi in 0.8.5-10 is it is not distinguishing between the two usb channels labeled with udi's (unique device identifiers) that differ by containing 'if0' or 'if1'.  In other words there should be two separate usb pci by-paths.  But the .fdi is treating them as one so the info.callout to hal-setup-wacom is duplicating everything.  The lshal shows two each of stylus, eraser, cursor, pad, and touch.  A mess.

And bizarrely your webcam is showing up as:
```
CNF7129     stylus
```
Which is something we are also just seeing with N-trig using linuxwacom 0.8.5-9.  Maybe something is messed up in the linuxwacom code also?

So I need you to post a repeat of all the diagnostics like before, this time using the new-working .fdi.  It would also help if you could include the 'Xorg.0.log' which is in '/var/log'.  That'll also need to be compressed.  That may tell us if another driver is grabbing touch and that's why you are not seeing it.

---

### Post by texaswriter on 2010-02-13
> **Ayuthia said:**
> Hopefully this does not create any confusion for anyone, but there is now a new 0.8.5-10 release and it contains ob1kenobi's patches.  I have updated the first post to reflect the information.  If I missed anything, please let me know.this is so confusing. Lol, not really. Anyways, since there's another new release, I'll try it as sson as possibe and post my results. What kernel directory should I take the new wacom.ko driver out of this time.

---

### Post by Favux on 2010-02-13
Hi texaswriter,

It still should be 2.6.27.

---

### Post by mmiicc on 2010-02-13
Hi 
I've just started with Bamboo Fun Pen&Touch A5. Yetserday I've done all what was in the very first post of this thread. All went fine. Today I see there's new version (0.8.5-10) and I did the same as yesterday but with this new version.
 
Now, this is my problem:
> Some helpful xsetwacom commands
To set your touch so that it works like a mouse touchpad:


```
xsetwacom set touch Mode Relative
```

To set the resolution of your touch (Example is for the medium sized tablet -- the small is X=480 Y=320):

```

xsetwacom set touch bottomx 740
xsetwacom set touch bottomy 500
```

To turn the touch on/off:

```

xsetwacom set touch Touch off
xsetwacom set touch Touch on
```



When I try any of these commands I get:
```
michal@michal-desktop:~$ xsetwacom set touch Touch off
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'touch'
```

Is something changed in this version, or I'm doing something wrong.


Thanks for great effort to make this stuff work!

---

### Post by Favux on 2010-02-13
Hi mmiicc,

Welcome to the thread!

That's what nossifer and myself are trying to figure out.  I assume your pen is working along with eraser?  See the last few posts by us.

Either we need to change the .fdi somehow or 0.8.5-10 has broken touch and maybe the pad (tablet buttons).

---

### Post by mmiicc on 2010-02-13
Actually, now I can't configure GIMP to work well. Pen works just like mouse. Yesterday I've got working both pen and eraser. 

Update:
Alexia Death helped me with "touch" thing. I had to use:
```
xsetwacom set "Wacom BambooFun 2FG 6x83 touch" Touch off
```
instead of ```
xsetwacom set touch Touch off
```

Another update:

I've managed to configure GIMP. Pen and eraser works. :)

After another unplug and plug "Wacom BambooFun 2FG 6x83 touch" changed to "Wacom BambooFun 2FG 6x85 touch".

---

### Post by Favux on 2010-02-13
Hi mmiicc,

OK, good.  So the "make white space not matter" change in 0.8.5-1 allows us to follow the format in xsetwacom:
```
"Device name"     Device type
```
Where the Device name is what the kernel is returning.  Now does that work with rotate commands I wonder?  And were we fooled by the broken rotation that wasn't fixed until 0.8.5-8?  [Actually that's been working since Jaunty and is ridiculously cumbersome, since you have to rename everything.  Unless wacomcpl now handles it without renaming?]

Which wacom.fdi are you using?

For Gimp you'll need to reconfigure your extended input devices again because the names have changed.

Edit:  Good!  So what's working now?  Stylus and eraser of course.  Touch is working too?  Is it better than before?  How about the pad?  Does wacomcpl show your devices in the list?  What is it calling them?  And again which .fdi?

Edit2:  Did the name change after replugging wreck the xsetwacom command?

---

### Post by nossifer on 2010-02-13
> **Favux said:**
> Hi nossifer,
So I need you to post a repeat of all the diagnostics like before, this time using the new-working .fdi.  It would also help if you could include the 'Xorg.0.log' which is in '/var/log'.  That'll also need to be compressed.  That may tell us if another driver is grabbing touch and that's why you are not seeing it.

Hi Favux,
I have attached the docs you asked for.  Thanks once again.
I have used the working.fdi and copied it over to the correct directory.  Also, I renamed it to both:  10-linuxwacom.fdi AND 10-wacom.fdi as I am not sure which is the one to be using on Karmic and 5-10.  So, it is the same file (new-working) as both.


$ xsetwacom set touch Touch on
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set touch value for 'Touch'

$ xsetwacom set touch bottomx 740
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set touch value for 'BottomX'

---

### Post by Favux on 2010-02-13
Hi nossifer,

OK, now we're getting somewhere.  The lshal looks much more reasonable with the new-working .fdi.

The .fdi name you want in Karmic is 10-linuxwacom.fdi not 10-wacom.fdi.  So remove the 10-wacom.fdi because we only want one wacom.fdi to run.

Let's see if that helps.  So what's working?  Stylus, eraser, and pad (tablet buttons)?  The wacomcpl .png was helpful!

The lshal looks OK now but the Xorg.0.log seems to show the Synaptic Touchpad driver is grabbing the touch screen/pad part of your tablet.  There's an easy fix for that if need be.  Is touch kind of working?  Anyway let's see what removing the extra .fdi does before we go on.

---

### Post by nossifer on 2010-02-13
> **Favux said:**
> Hi nossifer,
The wacomcpl .png was helpful!

I have done enough tech support to just say "send me a screenshot" :)

I removed the extra .fdi and Touch is, as it was, completely unresponsive.  I am not seeing any differences, and it is not recognized by wacomcpl.  Earlier versions (5-9) had the touch mainly 'unusable', and gestures were completely out, but this one just doesnt recognize my fingers at all.  Actually, I think one of the patches you directed me to previously had the touch working pretty well, but no gestures.

If it helps, I can reinstall an older version and send the log files if it helps with diagnosis.

While I don't use gimp often, I decided to configure it to test the eraser and sensitivity.  A quick tutorial later, and I think all is working as expected.  That is good news there.

---

### Post by Favux on 2010-02-14
Hi nossifer,

OK, so the stylus and eraser are good.  How about the 4 tablet buttons?

We may need to construct a new .fdi and see if that gets it to work.  But first let's see if it is the Syaptic driver causing the problem.  This is Ayuthia's fix, for n-trig digitizers that were having this problem.  We alter the Synaptic .fdi so it isn't so grabby.  You nest a second set of match lines for the Synaptic .fdi.  It's called "11-x11-synaptics.fdi" and it's located at "/usr/share/hal/fdi/policy/20thirdparty/".  Add:
```
    <match key="info.product" contains="Synaptics">

    </match>
```
So it looks like:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
    <match key="info.product" contains="Synaptics">

......

    </match>
    </match>
  </device>
</deviceinfo>
```
I'd use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```
to edit, and then reboot.  If we're lucky that will fix touch for you.

---

### Post by shazeal on 2010-02-14
Works great on 2.6.33-rc8 kernel on gentoo using CTH-661. Thanks :D

Have all buttons, touch, pen and eraser working :)

---

### Post by Favux on 2010-02-14
Hi shazeal,

Welcome to Ubuntu forums!

Great!  :D

Do you mean with linuxwacom 0.8.5-10?  Or with the 2.6.33-rc8 kernel did you have to use the bamboo branch of xf86-input-wacom?  And if you used a .fdi, which one?

---

### Post by shazeal on 2010-02-14
> **Favux said:**
> Hi shazeal,

Welcome to Ubuntu forums!

Great!  :D

Do you mean with linuxwacom 0.8.5-10?  Or with the 2.6.33-rc8 kernel did you have to use the bamboo branch of xf86-input-wacom?  And if you used a .fdi, which one?

I used linuxwacom-0.8.5-10 with the 2.6.33-rc8 kernel. I just had to add some header files that were missing from the new kernel.

```
echo '#define CONFIG_MODULES 1' > /usr/src/linux/include/linux/autoconf.h

echo '#define UTS_RELEASE "2.6.33-rc8"' > /usr/src/linux/include/linux/utsrelease.h
```

I am just using the standard xf86-input-wacom-0.10.4 package from portage, no other fdi it just works :)

---

### Post by Favux on 2010-02-14
Hi shazeal,

Good, thanks for the information!

Could you do me a favor and attach the wacom.fdi in the standard xf86-input-wacom-0.10.4 package from portage to your next post?

---

### Post by mmiicc on 2010-02-14
> Hi mmiicc
Hi Favux
I'm really new to tablets, so excuse my ignorance.

> Which wacom.fdi are you using?
I don't actually know what it is and what it does. Anyway after command:
```
locate wacom.fdi
``` I have following results:
```
michal@michal-desktop:~$ locate wacom.fdi
/home/michal/linuxwacom-0.8.5-10/src/util/10-linuxwacom.fdi
/home/michal/linuxwacom-0.8.5-9-prepatch/src/util/10-linuxwacom.fdi
/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```
I suppose it is the last one which I use. Content of that file attached.

> Touch is working too? Is it better than before?
I can't compare as I didn't use touch to much. It now works somehow. I can move pointer, and I discovered that when I tap with my finger on the touchpad whilst I have my other finger already on it, the right click menu appears. Also I've noticed pinch to zoom works with some applications. 
I don't know any more "touch gestures" I can try. It'd be useful to put some info about it in the first post.

> How about the pad?
Sorry, but I don't understand this question. Do you mean how the buttons work?

> Does wacomcpl show your devices in the list? What is it calling them?
It shows:
```
Wacom_BambooFun_2FG_6x8_Pen4_eraser
Wacom_BambooFun_2FG_6x8_Pen4
Wacom_BambooFun_2FG_6x85_Pen4_pad
Wacom_BambooFun_2FG_6x85_Pen4_touch
```

> Did the name change after replugging wreck the xsetwacom command
Yes I have to set everything again after replugging.

---

### Post by nossifer on 2010-02-14
Hi Favux,

Touch is working!  Thanks for that last instruction.  

I would call touch maybe 65% usable.  It is rather "touchy" in that you will often need to do the same action a few times to get it to work.  I must be careful to move my fingers very slowly or else it will just stop tracking.  I will then need to take my finger off and start again to get it to continue tracking.  The mouse pointer on the screen isnt smooth, it moves rather jerky.  Gestures, while working have the same symptoms, they may or may not work at any given attempt.  It seems that if you get them to respond, then they will for a few times, then give up the ghost for a few attempts.

I did the xsetwacom set touch bottomx 740 and I am not sure if that had any effect.  I think it is using more of the touchpad now.  These commands used to throw an error and now work as expected.  Thanks.

I think one final thing of note is that at some point in the past, there was a calibration on wacomcpl for Touch. There currently isnt one.  Touch is showing up in wacomcpl, but there is no config for it.

Buttons seem to do what they are supposed to do. All four give a response.  The only oddity I can report on them is that one attempt in the past had the scrolling buttons with the ability to just hold down the button and it would auto-repeat.  Now, if you press it and hold it down, you just get a single click.

---

### Post by RiBBiT on 2010-02-14
Hi,

Yesterday, I installed linuxwacom-0.8.5-10.tar.bz2. It is really good, as the annoying jumps have totally disappeared. Unfortunately there is a new problem. I used to set up my button configuration by a simple script at startup. Now xsetwacom commands don't work at startup, I have to unplug and plug back my tablet. But then, its name is changed:

```
ribbit@ribbit-ubuntu:~$ xsetwacom list
Wacom_BambooFun_2FG_4x5_Pen2_eraser     eraser
Wacom_BambooFun_2FG_4x5_Pen2     stylus
Wacom_BambooFun_2FG_4x53_pad     pad
Wacom_BambooFun_2FG_4x53_touch     touch
Wacom_BambooFun_2FG_4x53     stylus

ribbit@ribbit-ubuntu:~$ xsetwacom list
Wacom_BambooFun_2FG_4x5_Pen4_eraser     eraser
Wacom_BambooFun_2FG_4x5_Pen4     stylus
Wacom_BambooFun_2FG_4x55_pad     pad
Wacom_BambooFun_2FG_4x55_touch     touch
Wacom_BambooFun_2FG_4x55     stylus

ribbit@ribbit-ubuntu:~$ xsetwacom list
Wacom_BambooFun_2FG_4x5_Pen6_eraser     eraser
Wacom_BambooFun_2FG_4x5_Pen6     stylus
Wacom_BambooFun_2FG_4x57_pad     pad
Wacom_BambooFun_2FG_4x57_touch     touch
Wacom_BambooFun_2FG_4x57     stylus
```

This is quite annoying, as I have to manually enter xsetwacom commands to config my buttons every startup.

One more thing I don't really understand: If I am right, wacomcpl is just a graphical editor of ~/.xinitrc. It seems that my system doesn't run this script at startup. Is this normal?

---

### Post by shazeal on 2010-02-14
> This is quite annoying, as I have to manually enter xsetwacom commands to config my buttons every startup.

This is the script I use on startup.

All you need to change for yours is the IN_1-4 variables which would just be in lowercase for you, and your options in place of mine of course. 


```
#!/bin/bash
sudo modprobe -r wacom
sudo modprobe wacom

sleep 2 

IN_1=ERASER
IN_2=STYLUS
IN_3=PAD
IN_4=TOUCH

ERASER=$( xsetwacom --list | grep $IN_1 | sed "s/$IN_1//g" | sed "s/ *$//"  )
STYLUS=$( xsetwacom --list | grep $IN_2 | sed "s/$IN_2//g" | sed "s/ *$//" )
PAD=$( xsetwacom --list | grep $IN_3 | sed "s/$IN_3//g" | sed "s/ *$//"  )
TOUCH=$( xsetwacom --list | grep $IN_4 | sed "s/$IN_4//g" | sed "s/ *$//"  )


# FIX FOR LEFTIES
xsetwacom set "${STYLUS}" Rotate half
xsetwacom set "${PAD}" Rotate half

# USE ONE SCREEN ONLY
xsetwacom set "${STYLUS}" TwinView horizontal

# SET LEFT SCREEN BY DEFAULT
xsetwacom set "${STYLUS}" Screen_No 0

exit 0
```

And .xinitrc should only be called if you start X manually using start X iirc.

EDIT: Sorry I see you have an extra stylus device in your too so you may want to do an extra grep for 'Pen' like this...

```
STYLUS=$( xsetwacom --list | grep $IN_2 | grep Pen | sed "s/$IN_2//g" | sed "s/ *$//" )
```

---

### Post by texaswriter on 2010-02-14
RiBBit, Shazeal> Yeah, a script is the way to go for that type of thing. 

BTW, once you get wacom working [i.e., in the correct system directory], you shouldn't need to sudo modprobe wacom more than once. Ubuntu will actually be smart and pick it up next time if it detects the same hardware. Ubuntu has done that with both my wireless card and my wacom tablet now... Because I had to do custom steps to get both working in Karmic, I had to modprobe them. On reboot, they were already loaded. Try this out... see if it works for you. 

Also, you can chmod +x your script and add it to start automatically. This way the process is completely seamless and **"just works". **I do this for a couple of things on my laptop. 

Hope this helps. 

Ayuthia/Favux> No rushing/impatience at all, just curious... When is the next stable release of the open source wacom drivers expected. I was going to predict it according to the last few, but that would put it way later this year before a release (eeh gads lol). I figure somebody close to dev side might have a better perspective on that. 

Actually, was hoping a stable version could be pushed that just had pen and eraser functionality and whatever touch/gesture functionality works so far... Since stylus and eraser functionality is the essentials, the touch and gestures are bonuses. Is there a way I could suggest this to the maintainer of the Open Source Wacom driver website?

---

### Post by Favux on 2010-02-14
**It's looking like 0.8.5-10 works for the Bamboo P & T's!**

**[SIZE="3"]Wow, this is sooo Cool!!![/SIZE]**  :D

Back in October when TheguywholikesLINUX and I started messing with his Bamboo Pen & Touch we had no idea what we were in for.  Without Ayuthia, ob1kenobi (Jason), kgingeri, and  all the rest joining in I'm sure we wouldn't have gotten far.  And now with Ping and Chris here we are!

I'm going to take a moment to celebrate.

---

### Post by nossifer on 2010-02-14
> **Favux said:**
> **It's looking like 0.8.5-10 works for the Bamboo P & T's!**

I'm going to take a moment to celebrate.

Congratulations to you all on your hard work. I only witnessed this tail end of it but am blown away by how awesome you all are.

---

### Post by munooka on 2010-02-14
For me 0.8.5-10 is a bit of a regression wrt touch. My experiences are similar to nossifer's with touch becoming unusable. I guess not all the changes were implemented or they clash with other parts of the driver. So back to -9 with ob1's patches until -11 is released.

Anyway its all good and I can't wait till -11.


> **nossifer said:**
> Hi Favux,

Touch is working!  Thanks for that last instruction.  

I would call touch maybe 65% usable.  It is rather "touchy" in that you will often need to do the same action a few times to get it to work.  I must be careful to move my fingers very slowly or else it will just stop tracking.  I will then need to take my finger off and start again to get it to continue tracking.  The mouse pointer on the screen isnt smooth, it moves rather jerky.  Gestures, while working have the same symptoms, they may or may not work at any given attempt.  It seems that if you get them to respond, then they will for a few times, then give up the ghost for a few attempts.

I did the xsetwacom set touch bottomx 740 and I am not sure if that had any effect.  I think it is using more of the touchpad now.  These commands used to throw an error and now work as expected.  Thanks.

I think one final thing of note is that at some point in the past, there was a calibration on wacomcpl for Touch. There currently isnt one.  Touch is showing up in wacomcpl, but there is no config for it.

Buttons seem to do what they are supposed to do. All four give a response.  The only oddity I can report on them is that one attempt in the past had the scrolling buttons with the ability to just hold down the button and it would auto-repeat.  Now, if you press it and hold it down, you just get a single click.

---

### Post by bromalex on 2010-02-14
> **shazeal said:**
> This is the script I use on startup.

All you need to change for yours is the IN_1-4 variables which would just be in lowercase for you, and your options in place of mine of course. 
...


Hi Shazeal

With the same problem of changing IDs after each plug-in, I followed your script and tried to adapt it. It failed obviously because I don't fully understand what I am doing :-(
Could you help?
This is my script to disable and enable Touch:

```
#!/bin/bash

IN_4=touch

TOUCH=$( xsetwacom list | grep $IN_4 | sed "s/$IN_4//g" | sed "s/ *$//"  )

STATUS=`xsetwacom get "${TOUCH}" touch`

if [ "$STATUS" == "0" ]
  then
    echo "Touch was OFF, enabling."
    xsetwacom set "${TOUCH}" touch on
else
    echo "Touch was ON, disabling."
    xsetwacom set "${TOUCH}" touch off
fi

```I get this error:
```
 
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'Wacom_BambooFun_2FG_4x57_'
Touch was ON, disabling.
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Wacom_BambooFun_2FG_4x57_'

```By the way, I had to change "xsetwacom --list" to "xsetwacom list".

Thanks

---

### Post by Favux on 2010-02-14
Hi everyone,

That's why I'm interested in knowing if wacomcpl works with the .fdi in 0.8.5-10 or do you need one of the .fdi's I've posted, or what?

While you can use a xsetwacom script you shouldn't need to if wacomcpl works.  It will save your configuration as a series of xsetwacom commands in it's script .xinitrc.  That is a hidden file in your "/home/username" directory.  All you need to do is make it executable and add it to your Startup Applications as described in "Section 3: Calibrating your Tablet" in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Saves you from reinventing the wheel.  And is much more convienent.

Also interested in if the xsetwacom rotation commands work, say to HALF (for lefties).

So if a .fdi that doesn't rename things to stylus, eraser, touch, and pad but instead uses the device names works in wacomcpl I'd love to know.  A screen shot with wacomcpl and the devices in the device list would be helpful.

By the way it turns out Ping changed the way the devices are named slightly in 0.8.5-10 which explains some of my confusion.  It's not clear to me they realize that the naming changes (1 to 2 or whatever) every time you replug.  I'm thinking they don't.

---

### Post by gunar on 2010-02-15
The new version (0.8.5-10) worked for me (CTH-460) "out of the box".

Thanks a lot!

---

### Post by RiBBiT on 2010-02-15
Hi!

This script from Shazeal was a very clever idea. The regexp didn't work for me, I got the same error message as Bromalex. Here is my modified (simplified) version:

```
#!/bin/bash

sudo modprobe -r wacom
sudo modprobe wacom

sleep 2 

PAD=$( xsetwacom list | grep pad | sed "s/ .*$//"  )
TOUCH=$( xsetwacom list | grep touch | sed "s/ .*$//"  )

xsetwacom set "${PAD}" button1 "core key CONTROL z"
xsetwacom set "${PAD}" button2 "core key CONTROL y"
xsetwacom set "${PAD}" button3 "core key o"
xsetwacom set "${PAD}" button4 "core key p"
xsetwacom set "${TOUCH}" touch off

exit 0
```

By the way, "o", and "p" are to rotate the canvas in MyPaint.


Favux >

I don't really use wacomcpl, because for example I cannot disable the touchpad with it, so I have to manually edit the script. See attachment for a screenshot.

---

### Post by Favux on 2010-02-15
Hi RiBBiT,

Great!  Thanks for the screen shot.

It looks like wacomcpl can finally work with the device names even when they aren't the same as the device types.  Neat!

Some bugs yet.  The list box should be resizable so it doesn't cut of the device names listed, or at least have a horizontal scroll bar.  Understandable when it was just stylus, eraser, cursor, pad, and touch.  I've got to admit those also look better.  These long device names from the kernel aren't exactly appealing, to me at least.  Too bad wacomcpl can't translate them internally.

> for example I cannot disable the touchpad with it
What options are available with touch (screen shot?).  Because I'm pretty sure one of ob1kenobi's patches for wacomcpl had a touch relative option and I thought touch off.  As you know one of the tablet buttons (first (top) one I think) is suppose to be touch on or off.

Have you tried one of the old P & T .fdi's that renames the device names?

---

### Post by mmiicc on 2010-02-15
This is how touch in Wacomcpl looks like for me:

[IMG]http://img39.yfrog.com/img39/8851/screenshot056n.png[/IMG]

I wonder if you guys are aware of this program: [http://www.gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309](http://www.gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309)

---

### Post by Favux on 2010-02-15
Hi mmiicc,

Thanks.  You need to click on the list of 4 device names/types in the box and find the one that is touch.  Or did you and nothing showed up?

Yes I know about it.  But last time I used it it rewrote my xorg.conf with options I didn't have and made a mess.  Given that the "new" update for HAL is 5/09(?) I'd be cautious about trying it.

---

### Post by mmiicc on 2010-02-15
> **Favux said:**
> Hi mmiicc,

Thanks.  You need to click on the list of 4 device names/types in the box and find the one that is touch.  Or did you and nothing showed up?


You right, as you can see, nothing showed up. :) The same situation is on the RiBBiT's screenshot.

---

### Post by Favux on 2010-02-15
Ah, thanks for clearing that up.  If that's the case then we need to see if one of the .fdi's modified for the P & T's gets wacomcpl working for you.  You could try the new-working .fdi in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

---

### Post by bromalex on 2010-02-15
> **RiBBiT said:**
> Hi!

This script from Shazeal was a very clever idea. The regexp didn't work for me, I got the same error message as Bromalex. Here is my modified (simplified) version:


Hi RiBBiT

Thank you so much for your "modified" script.
With it, I could adapt my "Touch toggle script" from [Post#825]("http://ubuntuforums.org/showpost.php?p=8717734&postcount=825").
I can now enable and disable Touch, even when I unplug and replug my Bamboo.

```

  #!/bin/bash
   
  sleep 1
   
  TOUCH=$( xsetwacom list | grep touch | sed "s/ .*$//"  )
   
  STATUS=`xsetwacom get "${TOUCH}" touch`
  if [ "$STATUS" == "0" ]
    then
      echo "Touch was OFF, enabling."
      xsetwacom set "${TOUCH}" touch on
  else
      echo "Touch was ON, disabling."
      xsetwacom set "${TOUCH}" touch off
  fi
  
  
```

---

### Post by sandr on 2010-02-16
> **gomar said:**
> IIRC, the Bamboo Pen has no eraser (in contrast, the P&T does).
You know, you're absolutely right. :D

---

### Post by xiota on 2010-02-16
I got a CTH-460 not too long ago.  It worked with a patched linuxwacom-0.8.4-3 ...  There was no touch, and the buttons didn't work.  (The linuxwacom-0.8.5-? available at the time didn't work at all.)

Yesterday, I noticed linuxwacom-0.8.5-10.  I decided to try it.  The buttons work, and touch (kind of) works.  (It doesn't work anywhere near as well as synaptics touchpads, and it interferes with the pen.)

The problem:  With 0.8.5-10, the pen stops working once it hits the white border drawn on the pad.  With 0.8.4-3, the cursor would still move along the edge of the screen when it was outside the "border".  That made it easier to click and control things along the edge of the screen, like icons and scroll bars.

---

### Post by Favux on 2010-02-21
Hi everyone,

It looks like there may be a problem with the linuxwacom 0.8.5-10 wacomcpl and the Bamboo P & T's.  Since it works fine for me this may be something P & T specific or possibly a problem with the compiling instructions.  It is in wacomcpl (line 1830:  linuxwacom-0.8.5-10/src/wacomxi/wacomcpl-exec):
```
    # Bamboo Pen and Touch
    for { set i 208 } { $i < 212 } { incr i 1 } {
        set hasPad($i) 1
        set numPadButtons($i) 4
	set hasGesture($i) 1
    }
```
They did make a lot of changes to wacomcpl for the P & T, including gestures, along with other changes like the device naming you've encountered.  So it may just be broken or it is possible that there is a version conflict.

The version conflict might be between wacom-tools versions, given the amount of changes in it.  If this is only happening in Karmic this may be the case.  I can't tell for sure from the posts.  So the following is only if you are using Karmic and have already compiled and installed linuxwacom with Ayuthia's HOW TO.  And **wacomcpl doesn't work for you**.

To test this theory out you would recompile.  We'll still basically use the HOW TO on the first post of this thread but with some modifications.

First we'll make sure you have all the libraries and dependencies needed to build wacomcpl:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade
```
Then we'll purge wacom-tools.  If there is a conflict this should fix it:
```
sudo apt-get purge wacom-tools
```
Then in Ayuthia's HOW TO skip the lines:
```
sudo apt-get update
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get install libhal-dev
sudo apt-get build-dep xserver-xorg-input-wacom

```
You already have xserver-xorg-input-wacom (and hence xserver-xorg-input-all) installed so you don't need to re-install it.  Also libhal-dev should be installed.  We don't want a copy of wacom-tools present that we end up compiling over, we want a clean install of wacom-tools.

You can also skip the two hid-ids.h lines:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
```
Since it is already installed.  And let's pull down a fresh copy of linuxwacom 0.8.5-10 (remove or rename your old one).
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.5-10.tar.bz2
```
Then just start with:
```
tar -xvjf linuxwacom-0.8.5-10.tar.bz2
```
and continue.  Don't worry if 'make clean' complains.

Purging wacom-tools should remove the .fdi so re-install a .fdi from [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") or whichever .fdi you prefer.  It will also probably remove the udev rules so those will need to be re-installed if you were using them, again see post #384.

---

### Post by nossifer on 2010-02-22
> **Favux said:**
> Hi everyone,

It looks like there may be a problem with the linuxwacom 0.8.5-10 wacomcpl and the Bamboo P & T's. 

Hi Favux,

What is the problem this addresses?  Following the instructions on this thread, I can launch wacomcpl, but cannot calibrate Touch in it.  All else seems fine.

---

### Post by Favux on 2010-02-22
Hi nossifer,

Great!  That's what I need to know.  So wacomcpl is working for you?  When you click on a device in the device list the options for it show?  Even the touch options (minus calibration)?

Others were saying despite the device names appearing in the device list the options aren't showing for anything.

Are you using the new-working .fdi?

---

### Post by texaswriter on 2010-02-22
Congratz to everybody to getting this working. This rocks!!!! :popcorn::popcorn::KS:D

Just wanted to say, I just installed the latest according to the last directions given. That is, I should have an unpatched version of the driver running. Haven't tested pen [assuming that works ;-) ], I left my pen at home today. But gestures are alot better, actually usable now. But what was previously stated is true. Loses track if you move too fast and sometimes you have to repeat gestures. 

If there is anything somebody would like me to investigate, lemme know. I'll keep you guys informed if I run into any problems. 

Otherwise, thanks for getting me cth-460 working :D 

kudoS!!!

---

### Post by bromalex on 2010-02-22
> **Favux said:**
> Hi everyone,
It looks like there may be a problem with the linuxwacom 0.8.5-10 wacomcpl and the Bamboo P & T's. 

Hi Favux

I am using linuxwacom 0.8.5-10 with its original .fdi with my P&T CTH-460.

Wacomcpl is working as ever (meaning, still can't change assignments to some tablet buttons), but as far as I can tell, all is "well". But with Touch I have absolutely no options (no calibrating, no nothing).

If you need more help, drop us a line.

---

### Post by Favux on 2010-02-22
Hi bromalex,

Thanks.

Ok, so in the wacomcpl you're seeing something similar to:
```
Wacom_Bamboo_2FG_4x51_touch
```
and when you click on it no options for touch.

However other device names, like ending with nothing, give you the stylus options as normal.  Or eraser gives you those options and pad the button options.  Correct?  If so it is a P & T specific problem.  That narrows it down significantly and means we can hope for a quick fix.

Is there any problem when you replug the tablet and the name changes to?:
```
Wacom_Bamboo_2FG_4x53_touch
```

Re the buttons.  It looks like they now have a handle on that.  There is a problem with what button numbers Xinput expects scroll events on.  So hopefully that will be fixed in 0.8.5-11 due out in w 2 to 3 weeks.

That's why I'm trying to get a handle on wacomcpl so it's fixed for 0.8.5-11.


Hi texaswriter,

Great!
> Just wanted to say, I just installed the latest according to the last directions given.
I assume you mean Ayuthia's on the first post.  Could you please clarify?

---

### Post by texaswriter on 2010-02-22
> **Favux said:**
> 
Hi texaswriter,

Great!

I assume you mean Ayuthia's on the first post.  Could you please clarify?

Yes, but I installed the new one that somebody posted a few pages ago, but it was with th same instructions as on Ayuthia's first post. But it was the [0.8.5-10]("http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.5-10.tar.bz2") driver that was linked in afore mentioned post a few pages ago. 

[http://ubuntuforums.org/showpost.php?p=8862862&postcount=900](http://ubuntuforums.org/showpost.php?p=8862862&postcount=900)

There's the link to the post. 

Hope that helps.

---

### Post by bromalex on 2010-02-22
> **Favux said:**
> Hi bromalex,
Thanks.
Ok, so in the wacomcpl you're seeing something similar to:


Favux

Yes. That is the behavior I am getting.
Maybe some screenshots will help. (last 3 pics, after a replug)
After a replug I get the same behavior, only the names will change.

---

### Post by Favux on 2010-02-22
Hi texaswriter,

OK, I think I've got you.  You followed the little how to I posted for 0.8.5-10.  But that was the first time you tried 5-10, correct?  It wasn't because you were on 0.8.5-10 with the wacomcpl not working?  Previously it had been the patched 0.8.5-9 or whatever for you, right?

Anyway glad you like -10!

Hi bromalex,

Thanks again.  Those screen shots showed me something I wasn't aware of.  The number after a re-plug is going on the end of Pen (the device type), say Pen16.  But on touch and pad it's going on the end of the Pad dimensions, as in 4x516, and before the device type.  I don't think that is intended behavior.

Wacomcpl works for you except for touch.

The device name is cut off in the list box, but you can see it in the top device name box.  I already told them about that.

Does the name changing interfere with xsetwacom scripts?  Since the script has one name and then it changes.  Or is xsetwacom handling that?

Cool!  So wacomcpl can now accept device names rather than just stylus, eraser, cursor, pad, and touch.  Although to be honest those seem more elegant to me.  The device names seem a little lengthy and cumbersome, although informative.

---

### Post by nossifer on 2010-02-22
> **Favux said:**
> Hi nossifer,

Great!  That's what I need to know.  So wacomcpl is working for you?  When you click on a device in the device list the options for it show?  Even the touch options (minus calibration)?

Others were saying despite the device names appearing in the device list the options aren't showing for anything.

Are you using the new-working .fdi?

Hi Favux.
Yes, using the new-working.  Followed your latest instructions and I think the gestures are improved as well!
My names were originally the descriptive ones, but on reboot, they are just "Touch" etc.  I cant care either way, as long as they both work (which they do)

Yes. wacomcpl gives the same results as bromalux's screencaps.

---

### Post by Favux on 2010-02-22
Hi nossifer,

Thank you for the update.  That's interesting, your results seem to be hinting at some version conflict.

The reason you lost the descriptive name is probably "purge wacom-tools" removed the new-working .fdi.  Or 0.8.5-10 now installs the .fdi automatically when compiled.  Not sure which.  You could check and see if the .fdi was changed.  If you want the descriptive names you could use the new-working .fdi.

Actually I'd be interested in knowing if going back to (if it was overwritten) the new-working changed the performance any.

---

### Post by bromalex on 2010-02-23
> **Favux said:**
> 
Hi bromalex,
Does the name changing interfere with xsetwacom scripts?  Since the script has one name and then it changes.  Or is xsetwacom handling that?


Hi Favux

Yes it does. Whenever you replug Bamboo those changing names preclude using a fixed script for xsetwacom commands.

Fortunately some clever guys concocted a script that "greps" the newest name for the devices.

I have a script for enabling/disabling Touch based on that. Check Posts [#891]("http://ubuntuforums.org/showpost.php?p=8831542&postcount=891") and [#897]("http://ubuntuforums.org/showpost.php?p=8832768&postcount=897")

Bye

---

### Post by nossifer on 2010-02-23
> **Favux said:**
> Hi nossifer,

Thank you for the update.  That's interesting, your results seem to be hinting at some version conflict.

The reason you lost the descriptive name is probably "purge wacom-tools" removed the new-working .fdi.  Or 0.8.5-10 now installs the .fdi automatically when compiled.  Not sure which.  You could check and see if the .fdi was changed.  If you want the descriptive names you could use the new-working .fdi.

Actually I'd be interested in knowing if going back to (if it was overwritten) the new-working changed the performance any.

Hi Favux.
I will rerun the purge and see what .fdi is where along the way. TTY later in the day.

---

### Post by texaswriter on 2010-02-23
> **Favux said:**
> Hi texaswriter,

OK, I think I've got you.  You followed the little how to I posted for 0.8.5-10.  But that was the first time you tried 5-10, correct?  It wasn't because you were on 0.8.5-10 with the wacomcpl not working?  Previously it had been the patched 0.8.5-9 or whatever for you, right?

Anyway glad you like -10!


You have it correct. I was using the patched whatever from the OP. Thanks again!!

---

### Post by Favux on 2010-02-23
Hi texaswriter,

You're welcome.
> I was using the patched whatever from the OP.
So that hints at a resolved version conflict also.  This time between the wacom-tools installed when patching and compiling 0.8.5-9.


Hi nossifer,

OK, that will be interesting.  The purge this time shouldn't do anything because the compiled linuxwacom shouldn't have registered with the package manager so it won't remove the wacom-tools package because as far as it is concerned it isn't there.


Hi bromalex,

> Whenever you replug Bamboo those changing names preclude using a fixed script for xsetwacom commands.  Fortunately some clever guys concocted a script that "greps" the newest name for the devices.
I saw that but just wanted it confirmed.  Thanks.  By the way nice work on the scripts guys!

One final question.  Have you tried the .fdi's on [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384")?  Do either work for you?  If so does it obviate the need for a script that parses the Device name?  In other words can you go back to fixed scripts?

---

### Post by Jored on 2010-02-25
Obrigado, Bromalex.

I followed your guide step by step and got no errors.

However, while "lsusb" shows "Bus 004 Device 002: ID 056a:00d2 Wacom Co., Ltd", "xsetwacom list dev" produces no output, "wacomcpl" shows no device and GIMP does not show the tablet in its Input Devices list.

I'm running Karmic, kernel 2.6.31-19 and my tablet is a Bamboo Fun Pen & Touch.

Any ideas why it doesn't work?

---

### Post by Jored on 2010-02-25
Earlier post refers to bromalex HowTo in post #627

---

### Post by texaswriter on 2010-02-25
Hey, just wanted to bring to y'alls attention a weird problem I have... It's actually with a program that used the tablet, but the problem is weirdly enough resolved by 1) restarting 2) logging out [if you can manage that] 3) unplugging & replugging the tablet

So, as a result, I am not sure if it is the program, Xournal causing the problem or something with the tablet itself. 

The problem is: almost all icons, whether in the program, on the gnome panels stop responding to clicks [whether from the mouse or touch/stylus]... No matter what, you can still write on the xournal, even if you manoage to open another program. Minimizing doesn't work... 

I can hit control-alt-delete, and probably other shortcuts work as well. Hitting Alt-Fn-F1 will highlight the Applications menu, but moving the arrow keys does not actually open the menu [aka, LITERALLY, the Applications is highlighted but the actual menu does not open...]. According to moving the arrow keys, focus is still in the Xournal program. 

I can Control-S for save, continue writing [erasing doesn't work]...

Do you think that is a program bug or does it sound like something in the driver?

Edit: I should mention, it just does this occasionally. Rarely, in fact, but if I run it long enough, it seems it will eventually do that. Even more rarely, it will resolve itself over time.. It's really weird.

---

### Post by bromalex on 2010-02-25
> **Jored said:**
> Obrigado, Bromalex.
I followed your guide step by step and got no errors.
...
Any ideas why it doesn't work?

Hi Jored

Things have progressed and the latest version of linuxwacom is now 0.8.5-10.
I would advise you to follow instructions in [Post #1]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") to install the latest version. Follow Option A in that Post and hopefully you'll do fine.
If the problems persist, I am hoping that Favux could help you. I am just a rookie in this linuxwacom thing.

---

### Post by Kennethfaria on 2010-02-26
Hey guys i've got the bare necessities working and im wondering how I can modify the buttons and get sensitivity working.

Also, this is a bit unrelated but is there a program like one note that allows me to take notes via tablet pen and save it in a notebook?

Thanks!

---

### Post by Favux on 2010-02-26
Hi Kennethfaria,

Xournal, and it has pressure.  For letter recognition CellWriter.

To get pressure in Gimp or Inkscape etc. (programs that have it) you have to configure the extended input devices, see the [Wacom wiki]("https://help.ubuntu.com/community/Wacom") near the end.

Buttons aren't completely straightened out yet.  Should be better when 0.8.5-11 comes out in a couple of weeks.  For some ideas see the scripts a couple of pages back.

---

### Post by sny2ksa on 2010-02-26
I have HP pavilion TX2170EE tablet pc with windows 7 now i install the ubuntu  but the touch screen not works pen is working also the what i can i do without wireless.
Not working :)
can some one help me?

---

### Post by Favux on 2010-02-26
Hi sny2ksa,

You are on the wrong thread.

Install the Broadcom wireless driver through System > Administration > Hardware Drivers.  Called "Broadcom STA wireless driver".

You didn't mention which release of Ubuntu.  I am going to guess Karmic.  See "Jaunty and Karmic" near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  That will explain how to get set up.

Good luck!

---

### Post by blackSP on 2010-02-27
New problem...

I got the P&T working on 9.10 64-bit following all the instructions.
However, when I boot, my window manager forgets to draw the window borders and the cursor shows 'busy mode'  i.e. the normal arrow doesn't appear.

When I check 'visual effects' it's set to 'none'. Changing it back to 'normal or extra' returns things back to normal.

I couldn't find any directions to solving this. Has to be Wacom related as that's the only thing I fiddled with the last 3 hours.

Any ideas?

---

### Post by Jored on 2010-02-28
Hi:

I have installed my Bamboo Pen % Touch (CPH-461) successfully following the instructions in Post #1 in this thread.

The tablet seems to work OK, pen and touch, with my Dell Dimension 9200 running Karmic.

The tablet listed in wacomcpl is (strangely) a Wacom Bamboo Craft, with a number that changes almost every time I reconnect the tablet or restart wacomcpl.

However, I cannot save setup changes in Gimp (Input Devices) as clicking on the Save button with either the pen or the mouse has no effect.

---

### Post by blackSP on 2010-03-01
With no response to my problem mentioned up here I decided to really fix it. I re-installed Ubuntu. Damn pad!

---

### Post by dennus on 2010-03-04
I&#7743; having a bit of a problem settings the "area".

xsetwacom list is giving me this;

Wacom_Bamboo1_eraser     eraser
Wacom_Bamboo1_cursor     cursor
Wacom_Bamboo1_pad     pad
Wacom_Bamboo1_touch     touch
Wacom_Bamboo1     stylus

What command is now use to set the size of the active zone?

I know I should use something like 
```
xsetwacom set "Wacom_Bamboo1_touch" bottomx 480
```

but nothing happens, not even after I do

sudo modprobe -r wacom 
sudo modprobe wacom

any help is much appreciated!

---

### Post by nossifer on 2010-03-04
> **dennus said:**
> I&#7743; having a bit of a problem settings the "area".


I know I should use something like 
```
xsetwacom set "Wacom_Bamboo1_touch" bottomx 480
```




I think you are missing the word "touch" before bottomx

FYI:  at least in Karmic KDE4.4, there was a kernel update which made me reinstall the Wacom drivers.  No biggie... just thought in case a noob comes here, they may need to do the same.

---

### Post by dennus on 2010-03-04
OK, here's what I did;

in a terminal I typed 

```
xsetwacom set "Wacom_Bamboo0" touch bottomx 200
xsetwacom set "Wacom_Bamboo0" touch bottomy 200
sudo modprobe -r wacom
sudo modprobe wacom

```

No luck.

Actually it doesn't seem to matter if I enter "Wacom_Bamboo0_touch" or "Wacom_Bamboo0".  Both give the same output... none :-)

I know I'm missing something, but can't figure out what...

---

### Post by nossifer on 2010-03-04
> **dennus said:**
> OK, here's what I did;

in a terminal I typed 

```
xsetwacom set "Wacom_Bamboo0" touch bottomx 200
xsetwacom set "Wacom_Bamboo0" touch bottomy 200
sudo modprobe -r wacom
sudo modprobe wacom

```

No luck.

Actually it doesn't seem to matter if I enter "Wacom_Bamboo0_touch" or "Wacom_Bamboo0".  Both give the same output... none :-)

I know I'm missing something, but can't figure out what...

Try without the quotes.

What is or isnt working on your wacom?  If everything is working, great, if not, then post other symptoms / error messages.

```

xsetwacom list
Wacom_BambooFun_2FG_6x8_Pen0     stylus
Wacom_BambooFun_2FG_6x81_touch     touch
Wacom_BambooFun_2FG_6x81_pad     pad
Wacom_BambooFun_2FG_6x8_Pen0_eraser     eraser
~$ xsetwacom set Wacom_BambooFun_2FG_6x81_touch bottomx 740
~$ xsetwacom set Wacom_BambooFun_2FG_6x81_touch bottomy 500

```

** There are no confirmation / error messages.  I don't there there should be any if it worked.

---

### Post by dennus on 2010-03-05
If my tablet was working fine I wouldn't have to ask for help :-)
Like I said, I wanted to change the working area of my tablet. My wrist gets stressed out when I have to use the whole area of the tablet. I just need a little part to move the pen around.

Anyway, got it figured out now.  Perhaps it helps other people too.

*xsetwacom list*  got me the name of the tablet, which in my case is Wacom_Bamoo0. The full output is;

Wacom_Bamboo0_eraser     eraser
Wacom_Bamboo0_cursor     cursor
Wacom_Bamboo0_pad     pad
Wacom_Bamboo0_touch     touch
Wacom_Bamboo0     stylus

To get a 'feel' of the settings I entered

```
xsetwacom get Wacom_Bamboo0 bottomx
```

There is no need for the _touch, touch or " ". I got the number 14760.  So, instead of the GET I did a SET. Like so... 

```
xsetwacom set Wacom_Bamboo0 bottomx 5000
```

No need for sudo modprobe -r wacom and/or sudo modprobe wacom.

I did the same for bottomy.
And...  just to see if it works  topy  and  topx.  And it did :-)

So, all is set now using (my preferences)

xsetwacom set Wacom_Bamboo0 topx 500
xsetwacom set Wacom_Bamboo0 bottomx 5000
xsetwacom set Wacom_Bamboo0 topy 500
xsetwacom set Wacom_Bamboo0 bottomy 5000

I haven't tried if the settings will be stored though. Guess I&#314;l find out after my reboot .. hahaha


Edit:  last my my computer crashed and after a reboot I did have to re-enter the settings.

---

### Post by xtnsgo on 2010-03-07
First post, please excuse any breaches in etiquette, etc... 

Thank you--followed directions in post #1 and now my Bamboo Pen (CTL-460) is working quite well--no complaints:)

Granted, mine is basic (no buttons on tablet, no eraser) but what options exist are working fine--as smoothly as the Logitech trackball I use for everyday activities.  I have not fully explored button function as far as programmability (partially as a result of my own ignorance) but those functions to which the device defaults (touching stylus to pad = left click, near button [the one closest the nib] = center click, far button = right click) are working well.  Pressure sensitivity is fully functional as well.

Issues I have experienced:  

1.) When in 'relative' mode, GIMP input is erratic and unusable.  I prefer 'absolute', so no worries (for me, anyway).  

2.) On occasion, input in the GIMP file-open dialog has limited functionality (only the button which closes the dialog box works), but upon restarting GIMP, function returns.

3.) My trackball (Logitech Trackman Wheel, wired) loses full functionality--but only in GIMP--when plugged in at the same time as the Bamboo Pen tablet.  It can access menus, etc... but can perform no actions on the image being worked on other than repositioning the image with center click & drag.  Again, no worries--that's why I got the tablet:)

Other comments:  

--I have only actively tested functionality in GIMP and Kdenlive, though in both programs the tablet works quite well.  In all other programs it appears to function as a normal 3-button mouse.

--xsetwacom commands work, as does wacomcpl, though changes are not persistent.  I made a little script that flips the tablet for left-handed use on start up.  Not that big a deal for most, but i am just learning scripts as well, so i'm pleased.  (I'm not a lefty, but i like using the wide space on the tablet as a wrist-rest.)  

--when issuing xsetwacom commands, only the full device name works (i.e.--Wacom_Bamboo_Pen_4x5_Pen0).

--No issues with hotplugging whatsoever.  

Vital Statistics:

Computer: Toshiba Satellite M115-S3094, 2Gb memory (she's old, but she'll get you where you need to go...)

OS: Ubuntu Linux 9.10 (Karmic)

Kernel: 2.6.31-20-generic

Blood Type: B- 


Please pardon the verbosity (and possible redundance) of this post.

A final, very unrelated comment:  This is my first post, but i have been lurking hereabouts for some time and may i say the spirit and attitude of these forums is really quite nice to observe.  That I have yet to see an "RTFM" delivered in anything but jest is refreshing.  

Anyway, thanks to you and the community for your all your hard work.  Cheers!!!

---

### Post by WvBraun on 2010-03-08
Great News with Inkscape!

I have no idea why and how this works, but it does, what?
After installing kernel 2.6.31-20 and linuxwacom 0.8.5-10 yesterday and reconfiguring inkscape (names of the wacom devices changed) I get a fantastic new behavior: using bezier tool on the tip and switching to the eraser, the eraser tool in Inkscape kicks in. So far so good - BUT: flipping the stylus to the tip again switches back to the tool associated with the tip!! This is new - and GREAT!

I noticed some issues with touch on my CTH-661, but I will give that a look today in the evening.

Thanks a lot, WvBraun.

---

### Post by nossifer on 2010-03-08
Not sure if anyone else is experiencing this or not.

Symptom:  The left mouse click button on the pen, and my regular laptop trackpad (never use) become disabled for a few minutes.

EDIT>  I thought this was related to me running a virtual machine... it happened while I was not using the VM, and this time I caught what happened (I think)
I was tracking with the pen, and pressed click on the grey plastic body part of my 661.  That caused any type of left click to become trapped, and not pressable.  I unplugged the Wacom and reattached.  That seemed to have fixed it.  So, no biggie, likely human error anyway.

---

### Post by Ayuthia on 2010-03-10
The Linux Wacom developers have released 0.8.5-11 today.  I have updated the first post to point to an archived 0.8.5-10 in case there are issues.  Please try using 0.8.5-11 because the stable release of 0.8.5-X is building off of these changes.  The link that that source can be found right above the xsetwacom commands in the first post.

Here is the information from Ping Cheng that lists the highlights:
> 
This dash release:

    * Added HAL_CFLAGS to CFLAGS
        - by Pedro Gimeno <pg-lwd391@personal.formauri.es>
    * Retrieve tablet_id early on in wcmValidateDevice
    * Call getRange for both touch and pad, whichever comes the first
        - by Chris Bagwell <chris@cnpbagwell.com>
    * Fixed a keystroke bug for non-core mode of older Xorgs
        - by Stefan Schimanski
    * Added wacom XRandR daemon to support RandR settting change
        - by Takashi Iwai <tiwai@suse.de>
    * Added modifiers (right) to wcmAction.c
    * Fixed a copy/paste error in the license statement
    * Support kernel 2.6.33
    * Cleaned kernel drivers for 2FGT

The kernel and Xorg driver changes for Bamboo touch from Chris have not incorporated into this release yet.

The whole 0.8.5 unstable release:

Support USB tablets 0xE2, 0xE3, and 0x9F. Support new serial ISDv4 Tablet PCs.
Avoid duplicated and invalid devices and types for X server 1.4 and later.
Support kernels up to 2.6.34. Added 5 new Bamboo devices.


---

### Post by ivotron on 2010-03-11
Hi,

I received my bamboot touch today and I tried to configure it with no luck :(

I followed the steps from post #1 and used the latest version of the driver. The pad seems to kind of work (I can scroll a web page but nothing else), when I type:
```
xinput -list
```
I get entries for stylus, eraser, touch and pad. But when I run
```
xsetwacom list
```
I get nothing, so I can't calibrate mya pad.

I'd really appreciate your advice here, Thanks!!

---

### Post by portets on 2010-03-11
my thread might help. i had the same problem.

i never got touch working *completely*, but it should help.

[http://ubuntuforums.org/showthread.php?t=1410430&highlight=bamboo+fun](http://ubuntuforums.org/showthread.php?t=1410430&highlight=bamboo+fun)

---

### Post by portets on 2010-03-11
Ayuthia, Favux, and others.

**i think i just found out why some people don't have working wacomcpl's.**

this is for the people that get an error box when opening wacomcpl and clicking any of the devices in the list box.

all you need to do is copy and paste wacomcpl from /usr/bin/ to usr/local/bin/ after you've built and installed the latest linuxwacom-0.8.5-11.

i think the "make install" forgets to copy the new wacomcpl into the correct directory. and maybe other people didn't have these problems because the old wacomcpl still works on their devices?

i don't know, hopefully this helps those people.

---

### Post by Ayuthia on 2010-03-11
> **portets said:**
> Ayuthia, Favux, and others.

**i think i just found out why some people don't have working wacomcpl's.**

this is for the people that get an error box when opening wacomcpl and clicking any of the devices in the list box.

all you need to do is copy and paste wacomcpl from /usr/bin/ to usr/local/bin/ after you've built and installed the latest linuxwacom-0.8.5-11.

i think the "make install" forgets to copy the new wacomcpl into the correct directory. and maybe other people didn't have these problems because the old wacomcpl still works on their devices?

i don't know, hopefully this helps those people.

Out of curiosity, are you building the source with a
```
--prefix=/usr
```in the configure portion?  If you are, let me know and I can add this information to the first post.

---

### Post by portets on 2010-03-11
yes. and 100% sure about it.

---

### Post by mr_lundis on 2010-03-11
I needed to install  *libxrandr-dev* to build 0.8.5-11, otherwise I got an error saying X11/extensions/Xrandr.h couldn't be found.

---

### Post by Ayuthia on 2010-03-11
Thank you for finding that!  I have now updated the first post to reflect the wacomcpl issue and added the libxrandr-dev to the install list.

---

### Post by TheguywholikesLINUX on 2010-03-11
I'm back again (finally) since my wacom stopped working, so I've made the time to fix it. I've just followed the guide by Ayuthia on the first post, and the pen works straight away, just like it used to, pressure sensitivity and pen buttons. But the eraser *still* does not work, and neither does the touch.

Wacomcpl shows an option for "stylus" and various settings for it, but nothing else.

---

### Post by portets on 2010-03-11
> **Ayuthia said:**
> Thank you for finding that!  I have now updated the first post to reflect the wacomcpl issue and added the libxrandr-dev to the install list.

no problem, just glad i can configure my device now. :D

now everything works perfect except for touch. all pen features, pen and tablet buttons all work and are configurable.
touch is still really bad though. it seems as though the touch resolution is really low. the mouse cursor moves about 5 pixels at a time instead of 1. multitouch only partially works. oh, and the touch option in the control panel doesn't have any options, someone else reported that also. but otherwise, it's working perfect.

in a different post didn't you say that 0.8.5-11 didn't include some of the very latest work for the pen and touches? do you know what that latest work included?

---

### Post by Ayuthia on 2010-03-11
> **portets said:**
> no problem, just glad i can configure my device now. :D

now everything works perfect except for touch. all pen features, pen and tablet buttons all work and are configurable.
touch is still really bad though. it seems as though the touch resolution is really low. the mouse cursor moves about 5 pixels at a time instead of 1. multitouch only partially works. oh, and the touch option in the control panel doesn't have any options, someone else reported that also. but otherwise, it's working perfect.

in a different post didn't you say that 0.8.5-11 didn't include some of the very latest work for the pen and touches? do you know what that latest work included?

I think that the discussion was about redefining how the fingers were reported.  They are changing the kernel module to report the two fingers using the Multi-Point X (MPX) rules so that the code is more up to date.  If I remember correctly, Chris Bagwell is working on it.  You can find the discussion in their March 2010 [archive]("http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-devel").

---

### Post by portets on 2010-03-11
ahh, okay. looks interesting.

can't wait for 0.8.5-12(maybe -13?) looks like it should finally get the p & t's working the way they should.
using mpx would give us true multi-touch. the windows drivers don't actually use a "true" multitouch system, do they?

well anyway, i'll continue to test and report any new findings.

---

### Post by Ayuthia on 2010-03-11
> **portets said:**
> ahh, okay. looks interesting.

can't wait for 0.8.5-12(maybe -13?) looks like it should finally get the p & t's working the way they should.
using mpx would give us true multi-touch. the windows drivers don't actually use a "true" multitouch system, do they?

well anyway, i'll continue to test and report any new findings.

At this point, Windows provides one and two-finger gestures and they allow multi-finger drawing for things like MS-Paint.  However, I don't think that you will be able to resize windows by touching the opposite corners and shrinking/expanding the window.

When MPX gets a little more developed, we will see the capabilities of multi-touch.  Lucid will provide a taste of MPX, but there are not enough applications out there to show its value.

---

### Post by texaswriter on 2010-03-11
OK did an upgrade and am now running the latest kernel 2.6.31-20-generic, and did a fresh install of the wacom drivers, latest as well. 

The driver no longer gives complete priority to the stylus when both a hand/finger and the stylus are touching the pad at the same time. The cursor will constantly flash between the two points. This also happens when two fingers are touching the pad at the same time. 

The stylus + hand/finger thing is almost enough to make me revert, but I'll try using it before I make that decision. Edit: After using it, I decided that the best way to go is to turn touch off. The stylus is mostly unusable with the touch co-interaction being the way it is. 

I used this to disable touch on my machine: ```
xsetwacom list
xsetwacom set Wacom_BambooFun_2FG_4x5_Finger_touch Touch off

```
Otherwise SINGLE finger touch by itself works a bit better. Multi-touch is completely shot atm.

---

### Post by TheguywholikesLINUX on 2010-03-12
Actually, touch does work! but for scrolling only, using two fingers, and weird results for one finger. and sometimes it middle clicks or left clicks.

Does anyone know how to get my eraser working?

---

### Post by texaswriter on 2010-03-12
> **TheguywholikesLINUX said:**
> Actually, touch does work! but for scrolling only, using two fingers, and weird results for one finger. and sometimes it middle clicks or left clicks.

Does anyone know how to get my eraser working?

Yeah, single touch. I think I mentioned that works better. Single touch + single touch clicking. Although sometimes the single touch click works as a right click [not sure why]... 

I find that sometimes, when I am trying to disable touch, I have to do this complete sequence
```
sudo modprobe -r wacom; sudo modprobe wacom; xsetwacom list; //This lists the names of your devices on YOUR computer
xsetwacom set Wacom_BambooFun_2FG_4x5_Finger_touch Touch off

``` 

Anyways, that works on my computer. 

I'll await hearing possible fixes on the touch. I figure disabling touch is better temporarily [for y'all] then reverting entirely. So, if y'all have some fixes you want tested, just lemme know and I'll try them asap. 

:popcorn::KS:p

---

### Post by tontonraoul on 2010-03-12
Hello there,
first post for me here, though I've been wandering for a while on this forum. Thank you all active members for this hard work !
I just installed my Bamboo Pen on Karmic. No major problem following the how-to : xsetwacom list shows every component, and wacomcpl seems to work fine.

The major problem for me is related to a strange "shifting" of the cursor towards the upper left corner when pulling off the pen from the tablet. The shift distance is progressive from 0 at the upperleft corner of the screen to maximum at the lower right corner. Hope I'm clear enough...

Sorry if the problem was already reported, but none of the keyworks I submitted returned any answer...

Thanks in advance for your advices, and hope this helps improving the development.

Yours,

---

### Post by salvian on 2010-03-12
Hello.
I have a problem with Bamboo P&T on Karmic. I installed linuxwacom-0.8.5-11 from source and did all the things from the first post, but still have nothing :( no pen, no eraser, no touch.
```
usbcore: registered new interface driver wacom
wacom: v1.52-pc-0.4:USB Wacom tablet driver
usb 4-2: new full speed USB device using uhci_hcd and address 13
usb 4-2: configuration #1 chosen from 1 choice
input: Wacom BambooFun 2FG 6x8 Pen as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input24
input: Wacom BambooFun 2FG 6x8 Finger as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input25
device input24 is bound to the driver
device input25 is bound to the driver
must rebind
```means driver is ok, I suppose. But I have nothing on /dev/input/event* and /dev/input/wacom*
What can I do to help myself and linuxwacom? :)

Thanks.

---

### Post by magick.crow on 2010-03-14
What program does the eraser not work? I know I was a bit tricked by gimp. The pen and the eraser do the same thing. Trick? You can change ether end to do different things. You  want an eraser? Just use the eraser end to pick eraser in the gimp tools menu.

Also in gimp settings make sure that you have all the different pen components set to screen and not disabled! Give me more details and I will give more help, I hope. Same thing in inkscape, make sure you have it turned on in the input settings.

---

### Post by eWheeler on 2010-03-14
Hello,

I just installed the CTH-460 (Bamboo P&T, 056a:00d1) using the 0.8.5-11 driver and the pen/eraser works quite well. After about 4-hours of reading posts and playing with the new Bamboo,   I have a few questions and greatly appreciate any help you can offer:

1. The touchpad ("touch" device) is choppy and stops mid-stroke.  Have I setup something wrong?   (I have tried playing with the Suppress, Accel and SpeedLevel, but to no avail...)  

2. The pad and cursor devices are not loading in Xorg:
```
(**) Option "Device" "/dev/input/wacom"
(EE) PreInit returned NULL for "cursor"
(**) Option "Device" "/dev/input/wacom"
(EE) PreInit returned NULL for "pad"
```Is there a "cursor" device on the CTH-460?  If so, what does it do?

3. Can someone point me in the direction of gesture documentation (Slide/Ring)?  Specifically I am looking for scrolling --- and zoom (ctrl+scroll) would be great too! 

4. I have read that multi-touch is in development.  What is the current state of multi-touch?  Can someone point to multi-touch documentation?

**Distro:** Ubuntu 9.10/Karmic 

**Kernel:**
Linux geektop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux
**Configuration:** 
Used Favux's thread ([here]("http://ubuntuforums.org./showpost.php?p=6546012&postcount=1")) and picked up pieces here and there from many forum posts.

**xsetwacom list**
```
stylus     stylus
eraser     eraser
touch     touch
```**xinput --list --short**
```
"Virtual core pointer"    id=0    [XPointer]
"Virtual core keyboard"    id=1    [XKeyboard]
"Keyboard0"    id=2    [XExtensionKeyboard]
"Mouse0"    id=3    [XExtensionPointer]
"stylus"    id=4    [XExtensionKeyboard]
"eraser"    id=5    [XExtensionKeyboard]
"touch"    id=6    [XExtensionKeyboard]
```**xorg.conf:**
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "DisplayLinkScreen" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice "stylus"  "SendCoreEvents"
    InputDevice "eraser"  "SendCoreEvents"
    InputDevice "cursor"    "SendCoreEvents"
    InputDevice "pad"   "SendCoreEvents"
    InputDevice "touch"   "SendCoreEvents"
EndSection
Section "InputDevice"
  Driver "wacom"
  Identifier "pad"
  Option "Device" "/dev/input/wacom"
  Option "Type" "pad"
  Option "USB" "on"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "touch"
  Option "Device" "/dev/input/wacom-touch"
  Option "Type" "touch"
  Option "USB" "on"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  Option "Device" "/dev/input/wacom"
  Option "Type" "stylus"
  Option "USB" "on"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  Option "Device" "/dev/input/wacom"
  Option "Type" "eraser"
  Option "USB" "on"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  Option "Device" "/dev/input/wacom"
  Option "Type" "cursor"
  Option "USB" "on"
EndSection

# I have a USB mouse and a generic laptop touchpad on this system
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```**Relevent portions of the Xorg log:**
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-11 $
[... snip ...]
(**) Option "Device" "/dev/input/wacom"
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
Got range USB Bamboo maxX=0 maxY=0 maxZ=1023 resX=2540 resY=2540
(==) Wacom using pressure threshold of 61 for button 1
display range USB Bamboo maxX=0 maxY=0 maxZ=1023 resX=2540 resY=2540
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14720 maxY=9200 maxZ=1023 resX=2540 resY=2540  tilt=disabled
(**) Option "Device" "/dev/input/wacom"
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) eraser: reading USB link
(**) eraser: threshold = 61
(**) eraser: max x set to 14720 
(**) eraser: max y set to 9200 
(**) eraser: max z = 1023
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/input/wacom"
(EE) PreInit returned NULL for "cursor"
(**) Option "Device" "/dev/input/wacom"
(EE) PreInit returned NULL for "pad"
(**) Option "Device" "/dev/input/wacom-touch"
(**) Option "SendCoreEvents"
(**) touch: always reports core events
(**) touch device is /dev/input/wacom-touch
(**) touch is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) touch: reading USB link
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "touch" (type: Wacom Touch)
Got range USB Bamboo maxX=480 maxY=320 maxZ=1023 resX=2540 resY=2540
(==) Wacom using pressure threshold of 61 for button 1
display range USB Bamboo maxX=480 maxY=320 maxZ=1023 resX=2540 resY=2540
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=480 maxY=320 maxZ=1023 resX=2540 resY=2540  tilt=disabled
(II) config/hal: Adding input device Wacom BambooFun 2FG 4x5 Finger
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Wacom BambooFun 2FG 4x5 Finger touch
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Wacom BambooFun 2FG 4x5 Finger pad
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Wacom BambooFun 2FG 4x5 Finger cursor
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Wacom BambooFun 2FG 4x5 Finger eraser
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Wacom BambooFun 2FG 4x5 Pen
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Wacom BambooFun 2FG 4x5 Pen touch


```

---

### Post by magick.crow on 2010-03-15
The gestures are working on my system but they don't work so well. The scale is 2 fingers moving apart. The scroll is 2 fingers moving together in what ever direction you want the page to go. 

Read the Wacom site for more. They have vids and a manual for download there.

Don't know about your other questions as I just started last night.

---

### Post by TheguywholikesLINUX on 2010-03-15
> **magick.crow said:**
> What program does the eraser not work? I know I was a bit tricked by gimp. The pen and the eraser do the same thing. Trick? You can change ether end to do different things. You  want an eraser? Just use the eraser end to pick eraser in the gimp tools menu.

Also in gimp settings make sure that you have all the different pen components set to screen and not disabled! Give me more details and I will give more help, I hope. Same thing in inkscape, make sure you have it turned on in the input settings.

It's not in a particular program, the eraser does not work in what ever I use it for.
xsetwacom list only gives me touch and stylus, no eraser input. And there is no eraser device listed in the gimp settings, I had already put the stylus on screen mode and it functions well with pressure sensitivity.

---

### Post by gabe_rosser on 2010-03-16
Hi All,

I've been trawling through the posts here but I can't find anything related to my specific problem... I hope I didn't miss anything obvious, I'm a bit new to this.

I have a Bamboo Pen (old school, no touch) and Karmic x64_86.  It didn't work at all out of the box so I compiled and installed 0.8.5-11 Linux Wacom Project.  Also copied the RC .fdi file into the appropriate location.  

1) There are no entries in my xorg.conf relating to the tablet and ```
xxd /dev/input/wacom
``` returns no activity from the tablet.  However the tablet works fine and ```
xidump -u raw stylus
``` does pick up activity so I'm guessing this is HAL rather than X?

2) I have a dual screen setup (two 1920x1080) and the tablet is mapped to the whole thing.  I want to localise it to one screen, or even better, a subregion of one screen, to maximise the resolution and give me a natural ratio.

wacomcpl works fine for pressure changes, change from absolute to relative etc but seems to ignore all references to screen mapping.  I've tried the following but it has no effect at all.

```
xsetwacom set stylus screen_no 0
xsetwacom set stylus twinview horizontal
```

any ideas folks?  Thanks for your help, and all of the help you've already given me :)

---

### Post by texaswriter on 2010-03-17
GabeRosser> Navigate to the original post [abbreviated OP] and follow the instructions there. I would not recommend trying to custom compile from the website. **If you follow the instructions exactly inj the Original post, with either the 0.8.5-10 or 0.8.5-11 PRE PATCHED that are in the links in that like same post you can't go wrong. **

Good luck!!


> **gabe_rosser said:**
> Hi All,

I've been trawling through the posts here but I can't find anything related to my specific problem... I hope I didn't miss anything obvious, I'm a bit new to this.

I have a Bamboo Pen (old school, no touch) and Karmic x64_86.  It didn't work at all out of the box so I compiled and installed 0.8.5-11 Linux Wacom Project.  Also copied the RC .fdi file into the appropriate location.  

1) There are no entries in my xorg.conf relating to the tablet and ```
xxd /dev/input/wacom
``` returns no activity from the tablet.  However the tablet works fine and ```
xidump -u raw stylus
``` does pick up activity so I'm guessing this is HAL rather than X?

2) I have a dual screen setup (two 1920x1080) and the tablet is mapped to the whole thing.  I want to localise it to one screen, or even better, a subregion of one screen, to maximise the resolution and give me a natural ratio.

wacomcpl works fine for pressure changes, change from absolute to relative etc but seems to ignore all references to screen mapping.  I've tried the following but it has no effect at all.

```
xsetwacom set stylus screen_no 0
xsetwacom set stylus twinview horizontal
```any ideas folks?  Thanks for your help, and all of the help you've already given me :)

---

### Post by moorking on 2010-03-17
Thanks for sharing about touch series.

---

### Post by texaswriter on 2010-03-17
On another note, I ditched Gnome and reinstalled with Kubuntu. I reverted back to 0.8.5-10 so I didn't have to run a huge script that included

```
sudo modprobe -r wacom
sudo modprobe wacom
 xsetwacom list
xsetwacom <insert really long name of device here> touch off

```

just to disable touch everytime I boot [which is at the beginning of EVERY class even if the classes run right after each other. 

As soon as somebody has done something new to the drivers so the touch isn't so buggy [mostly just concerned with the interaction when the stylus is in use], which by the way is the majority of my interest in the wacom pad right now, then I'll be sure to test that new version **right away!! **

Anyways, 0.8.5-10 is working great with Kubuntu by the way. :popcorn::KS:p

And once again, I don't offer any of these comments [or previous posts for that matter] as a complaint. I am completely satisfied in the performance of all the patched drivers since I started using them. All comments provided are intended for the continuous improvement of the driver. 

Great job guys and keep up the great work. I can't wait to see the new multi-touch in action when it gets going.

---

### Post by magick.crow on 2010-03-17
2) I have a dual screen setup (two 1920x1080) and the tablet is mapped to the whole thing.  I want to localise it to one screen, or even better, a subregion of one screen, to maximise the resolution and give me a natural ratio.

wacomcpl works fine for pressure changes, change from absolute to relative etc but seems to ignore all references to screen mapping.  I've tried the following but it has no effect at all.

```
xsetwacom set stylus screen_no 0
xsetwacom set stylus twinview horizontal
```

any ideas folks?  Thanks for your help, and all of the help you've already given me :)[/QUOTE]

I don't know why but the wacomcpl program has a bunch of settings that look like what you want and it says that they only work with Nvidia Graphics cards.

---

### Post by gabe_rosser on 2010-03-17
> GabeRosser> Navigate to the original post [abbreviated OP] and follow the instructions there. I would not recommend trying to custom compile from the website. If you follow the instructions exactly inj the Original post, with either the 0.8.5-10 or 0.8.5-11 PRE PATCHED that are in the links in that like same post you can't go wrong.

Good luck!!

Thanks for the suggestions, texaswriter and magick.crow.  I just tried the 0.8.5-10 pre-patched files and it has made no difference.  The stylus still works, as it did before, but is stretched across both of the screens, which makes it nearly impossibly sensitive to use.

I have tried both wacomcpl and xsetwacom to restrict the pointer to one screen (should make no difference since they do the same thing, right?) and neither have any effect at all.  I can think of two things that might be causing it:

1) My xorg.conf is somehow incompatible?  I've attached it.  Standard Nvidia twinview setup.

2) I need to tell the wacom config the resolutions of my screens.  I found the command
```
>> xsetwacom get "Wacom_Bamboo_Pen_4x5_Pen0" tvresolution0
-1

```
and tried to set the resolution of my screens.  However I'm unsure of the syntax for the command and everything I've tried results in:
```
>> xsetwacom set "Wacom_Bamboo_Pen_4x5_Pen0" tvresolution0 "1920x1080"
ParseValues: only two values allowed for TVResolution0. 
Please check your values' format. 

```
When I searched for it I found this post [Bug#571025: xserver-xorg-input-wacom: Impossible to set TVResolutions]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a880de63414f2390?pli=1").  Not sure if it's related?

---

### Post by texaswriter on 2010-03-18
There is a way to set the *touch* to behave either like the synaptic pad or like how the stylus is mapped to a specific location of the screen per specific location of the tablet. I don't know if you can do the same thing [switching] for the stylus too. If it did, it might give you more power to control the resolution. 

Also, be aware that xsetwacom list will show the device names. Just double check that you are using your command with the correct device name. 

Hope that helps. 

> **gabe_rosser said:**
> Thanks for the suggestions, texaswriter and magick.crow.  I just tried the 0.8.5-10 pre-patched files and it has made no difference.  The stylus still works, as it did before, but is stretched across both of the screens, which makes it nearly impossibly sensitive to use.

I have tried both wacomcpl and xsetwacom to restrict the pointer to one screen (should make no difference since they do the same thing, right?) and neither have any effect at all.  I can think of two things that might be causing it:

1) My xorg.conf is somehow incompatible?  I've attached it.  Standard Nvidia twinview setup.

2) I need to tell the wacom config the resolutions of my screens.  I found the command
```
>> xsetwacom get "Wacom_Bamboo_Pen_4x5_Pen0" tvresolution0
-1

```and tried to set the resolution of my screens.  However I'm unsure of the syntax for the command and everything I've tried results in:
```
>> xsetwacom set "Wacom_Bamboo_Pen_4x5_Pen0" tvresolution0 "1920x1080"
ParseValues: only two values allowed for TVResolution0. 
Please check your values' format. 

```When I searched for it I found this post [Bug#571025: xserver-xorg-input-wacom: Impossible to set TVResolutions]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a880de63414f2390?pli=1").  Not sure if it's related?

---

### Post by msquared86 on 2010-03-19
ok after much playing with xsetwacom i figured out how to constrain the tablet to one monitor this is the way i have it set up

my resolutions on both monitors are 1440x900

in the wacomcpl the tracking is set to 
TopX 0
TopY 0
BottomX 1472
BottomX 9200

now if you double BottomX (1472 * 2) you get 29444.

Now since wacomcpl wont go that high you have to use xsetwacom so this is how:
```

xsetwacom Your_Device_Name BottomX 29444

```BottomX doesnt get changed as its the height of your monitors, Now this would only work if both your monitors are the same resolution.

not sure if it matters but i have the wacom bamboo CTL-460/k and i am running twinview so hopefully this helps!!

---

### Post by ianni67 on 2010-03-19
Hi everyone,
I have a karmic desktop 32 bit.

I just bought a bamboo pen and touch and started googling.

My configuration is a bit unusual therefore I decided to post here my short experience in the hope it can help someone and get me some help.

I have two monitors: one (screen0) is horizontal, the other one (screen1) is vertical, i.e. rotated 90°cw. This configuration is very useful for reading and editing full-page documents.

I have a nvidia card so I use the xinerama extension to have a sort of twinview. It works great and I can move a window from one screen to the other and have a window just in the middle of the two screens (completely unuseful, but it gives the idea).

I bought the bamboo mainly to use it as a touch device, sort of a touchpad. I have pain in my wrist and this makes me hate the mouse.

So this is what I got till now:
- the pen is working, it stays confined in the screen where I put it with the mouse. If I want to change screen I grab the mouse, click on the target screen and that's all.
- the pen works great, indeed.

- the first two  buttons on the tablet act as the up and down arrown in the keyboard. The other buttons do not work.
- the button on the pen acts as the central button of the mouse. 
- The pen tip click is okay.

- The touch 'sort of' works: it's a bit unstable but responds. I'm using it in relative mode, i.e. it emulates a touchpad. Sometimes it looses the contact, i.e., it seems that the sensibility changes at run time. Sometimes I have to press veeeery lightly and sometimes I have to be a little more rude in order to have a reaction.
- only single touch, no multitouch, no gestures (I actually disabled them). When I tried gestures I got a big mess (only some sort of magnification, quite unstable).

- the very pain in the... uh, neck, is the tapping: if I tap on the bamboo with my finger, I always get the rightclick-menu. So tapping is currently connected to right button (button 3). How can I fix this?

This is the sequence of xsetwacom commands I gave to get my configuration up, after a fresh installation of linux-wacom 8.5.10 pre-patched:

```
- xsetwacom set Wacom_Bamboo_Craft1_touch Capacity 1
-  xsetwacom set Wacom_Bamboo_Craft1_touch Accel 7
-  xsetwacom set Wacom_Bamboo_Craft1_touch Gesture off
- xsetwacom set Wacom_Bamboo_Craft1_touch TwinView Xinerama
- xsetwacom set Wacom_Bamboo_Craft1_touch MMonitor off
- xsetwacom set Wacom_Bamboo_Craft_Pen0 MMonitor off
- xsetwacom set Wacom_Bamboo_Craft_Pen0 TwinView Xinerama
```



I hope this post is useful and that someone can help.

I apologise for my rocky-balboa english: I'm quite tired and here is night.

best wishes and thank you very much for your great work.

---

### Post by bobelix on 2010-03-20
I bought my daughter, who is a budding artist, the Wacom Bamboo Pen Model CTL-460 to use on her Dell Latitude D400 Laptop which has Ubuntu Karmic loaded.
I bought this specific model because Ubuntu information sites said it should run "out of the box". Ha! Ha! What do these glib liars get out of misleading people like that? I now have one very upset daughter and a totally non-functioning piece of hardware.
I've been trying for 5 hours now to get it to work with no success. I went into Synaptic and loaded the wacom tools/driver files there - nothing. I followed 3 sets of instructions (none of which I understood but copied into Terminal faithfully) and still nothing.What was really annoying about the instructions were statements like "download tarball and extract" EXTRACT TO WHERE? I eventually figured out it was probably to Home but still no reaction from the tablet.
Along the way, I got error references to non-existent xorg-servers - whatever they are - and one site said I should copy an .fdi file into one of the directories that descend from USR which I duly tried to do and was told that I didn't have rights to do this - despite the fact that I was using my daughter's login and she's the only user of the computer. This is driving me crazy!
Can anyone (who still remembers what PLAIN ENGLISH for NON-SPECIALISTS looks like) please help??????? If it has to involve half a ton of code, please don't make statements like "now simply open up your xfscdbogbrush file and all will be obvious". Nothing is obvious - please lead me by the hand; I don't speak code and only loaded Karmic because everyone was claiming it was just as user-friendly as Windows (of which I was heartily sick because of the eternal virus war and the slowness of running).
Yours in hope,
Bob

---

### Post by ianni67 on 2010-03-20
Dear Bob,
Linux is nowadays as much user-friendly as windows, and in some cases even more.

The point is that the producer of the bamboo (Wacom) does not provide any driver for linux. This means that - to put it simply- the tablet is not supposed to work with linux. 
If we where talking about Windows or Apple, then the story would probably end here. No way to solve this problem. One way to the trash can or to ebay.
But we are talking about linux, and linux is another world. 
Linux is open source, which means collaboration. 
A group of brave programmers started working - for the sake of helping us poor users - on the tablet and have written the missing software.
For this reason, we can now use this and so much other hardware on linux-  _without any support from the producers_ ! 
Please, note that this would never ever happen for other operating systems.
Now, the problem is that those programmers do not want to spend time in repeating some basic information which is needed to use such kind of software and think that - since this kind of information is often needed when dealing with open source software - we all know it.

I'm talking about compiling a software from the source code and installing it. 
Please, note that under windows or Apple OS/X, this is a matter for just a few, skilled users. No way to do it unless you buy expensive compilers (software needed to compile other software from its source code). Well, there are some free compilers also for windows, but they are as cryptic as in linux and even more, to use.

You need to compile the driver for some hardware from its source code, usually, when the hardware is not widely used or when it is still quite new. In those cases you might wait for some months and probably the drivers will make it to synaptics. If they don't, probably your hardware is not widely used and therefore it's not worth spending time to make it work under linux (please, don't forget that almost all the work to build those drivers is made for free by volunteers).

The final lesson is that you need some basics if you want to use the driver for your tablet right now, otherwise wait until it makes it to synaptics.

In your specific case, you do not need to compile the source code, but only to install the precompiled driver in the correct place. 

The tarball must be extracted in your home and then you must open a terminal, enter the directory created by the expansion (cd name-of-the-directory) and type:

```
cd prebuilt
sudo -s
(type password when requested)
apt-get remove linuxwacom
./uninstall
./install
reboot
```

that should be all, after reboot the tablet should work.

If you need more settings you can launch from the terminal the application: wacomcpl.

All this information is written in a text file in the directory created by extracting the tarball. 
The file is named README. Catch the suggestion: read it.

hope this helps.
Best wishes and welcome to the frustration world:;) you swallowed the redpill ([http://en.wikipedia.org/wiki/Redpill](http://en.wikipedia.org/wiki/Redpill)). 

ianni

---

### Post by texaswriter on 2010-03-20
> **bobelix said:**
> I bought my daughter, who is a budding artist, the Wacom Bamboo Pen Model CTL-460 to use on her Dell Latitude D400 Laptop which has Ubuntu Karmic loaded.
 I bought this specific model because Ubuntu information sites said it should run "out of the box". Ha! Ha! What do these glib liars get out of misleading people like that? I now have one very upset daughter and a totally non-functioning piece of hardware.
 I've been trying for 5 hours now to get it to work with no success. I went into Synaptic and loaded the wacom tools/driver files there - nothing. I followed 3 sets of instructions (none of which I understood but copied into Terminal faithfully) and still nothing.What was really annoying about the instructions were statements like "download tarball and extract" EXTRACT TO WHERE? I eventually figured out it was probably to Home but still no reaction from the tablet.

Bobelix> Just to start off, almost ALL Wacom [or any tablet] works out of the box [as in hotplugging]. The model you are referring to is new. You will find the OP in this thread to be very instrumental in getting it working FLAWLESSLY for any stylus operations. You may peruse the many pages of this thread for plenty of tips as far as command to customize. 

Otherwise, had you gotten an older model of Wacom, it would've worked out of the box. In the near future even those 4 models that are new will work out of the box due to the hard work and dedication of the programmers on the Open Wacom Driver site as well as the main posters of this thread and everybody who helped, contributed, and tested. 

To answer your question about installing: Follow the instructions EXACTLY in the ORIGINAL POST of this thread. When prompted to download a file in the Original Post, download the 0.8.5-10. If you download the 0.8.5-11, be prepared to disable the touch [see a post I made a few pages back]. 

You can download and compile it yourself from the opensource wacom site, but it won't be patched. 

Oh, on more thing, when you do the step with the ./configure, scroll back up through the results to see if there is some prerequisite that isn't installed. 

Notably, on fresh installs of this you need to install the following BEFORE any of the steps in the original post. : ```
sudo aptitude install fort77
```It will ask you to install some prerequisites. ```
y
``` and hit enter. Then proceed with the steps in the Original Post. 



Hope this helps. 

Please peruse all the pages of this thread to find many helpful suggestions towards exactly what you are trying to do with this tablet. 

:popcorn::KS:P

---

### Post by texaswriter on 2010-03-20
Ianni> I'm not sure on what kind of tangent you are trying to go off on here. 

The original post is the best reference for anybody trying to install this driver. 

Although somewhat of what you are saying is true, most of it does not pertain to the problem or question it supposedly respond to.

---

### Post by ianni67 on 2010-03-21
> **texaswriter said:**
> Ianni> I'm not sure on what kind of tangent you are trying to go off on here. 

I'm not trying to take a tangent. Just to help. Bob seemed upset and the point is, that he is right (from his point of view). I tried to explain a concept which, I admit, does not strictly pertain to this thread and I apologize for this. I now that such discussions can degenerate to flames and, of course, this is not what I want.

> **texaswriter said:**
> 
The original post is the best reference for anybody trying to install this driver. 
 

You'd better provide Bob the link to the Original Post, as he might not find it immediately. This is exactly the kind of problem highlighted by Bob: please try to be clear. 

> **texaswriter said:**
> 
Although somewhat of what you are saying is true, most of it does not pertain to the problem or question it supposedly respond to.

I won't reply to this, as it is your opinion and I respect the opinions of the others. Please, do the same.

BTW, if I'm allowed to add some more information about my experience with linuxwacom:

after a second reboot things are getting better: *the touch is now working too* :-D, and the tap now gives a "mouse click" event. I suspect that I still had some unwanted module still loaded.

The only remaining issue is the following:
as I said in my previous post, I use

```
xsetwacom set Wacom_Bamboo_Craft_Pen0 MMonitor off
```

to confine the cursor to a single screen and switch screen by using the mouse to move the cursor to the desired screen. 

This approach works perfectly with the pen but with touch it has a strange behaviour.

I can (I should not!) move the cursor to the other screen by using the touch, but after moving to the second screen I cannot move it back to the first and have to use the mouse. 
It looks like a one-way fence. I tried everything I could figure out.

Please, any suggestion?

More, and more, thanks to all those who wrote, improved and helped us in using those and all the other drivers.

---

### Post by ianni67 on 2010-03-21
Please one more question (a "pertaining" one): 

I compiled the source following the instructions in this thread but realized later that there was a "precompiled" directory in the tarball.

Is it wrong to install from the "precompiled" directory without recompiling?

---

### Post by abcdefgj on 2010-03-21
The Bamboo Touch works not on Lucid:(

---

### Post by ianni67 on 2010-03-22
maybe this could help?
[http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

---

### Post by texaswriter on 2010-03-22
> **abcdefgj said:**
> The Bamboo Touch works not on Lucid:(

According to what I understand, if you are installing Lucid, it is a beta or alpha. Some things aren't finished. It isn't that it doesn't work, I believe something it actually relies on isn't yet supported. I did actually try to upgrade to Lucid [just to see what would happen] and MANY things were broken before being able to install the things that would get a) my wireless nic card working b) Wacom tablet... 

So, if tablet usage is important, I would stick with Jaunty or Karmic for the time being.

I installed Lucid about a month or two ago. Things may have changed since then. If anybody is using Lucid and has a CTH-460 model Wacom tablet working, please post with setup details.

---

### Post by texaswriter on 2010-03-22
> **ianni67 said:**
> I'm not trying to take a tangent. Just to help. Bob seemed upset and the point is, that he is right (from his point of view). I tried to explain a concept which, I admit, does not strictly pertain to this thread and I apologize for this. I now that such discussions can degenerate to flames and, of course, this is not what I want.

Yes, I'm not trying to be mean or ugly or anything. I'm just commenting that your response to a specific question seemed to veer off target. 


> **ianni67 said:**
> You'd better provide Bob the link to the Original Post, as he might not find it immediately. This is exactly the kind of problem highlighted by Bob: please try to be clear. 

Yes, that sounds like a good suggestion in case **original post** isn't understood: 

[http://ubuntuforums.org/showpost.php?p=8283168&postcount=1](http://ubuntuforums.org/showpost.php?p=8283168&postcount=1)



> **ianni67 said:**
> I won't reply to this, as it is your opinion and I respect the opinions of the others. Please, do the same.

As I said before, not trying to be mean or ugly, just commenting that your response seemed off target from the question. Otherwise, alot of the points you made were valid, just NOT answers to the question posed. Just as an example, if I asked how many spots does a leopard have and you responded that leopards live on every continent except Australia, you are technically correct, but you did not respond to the given question. 

So, please take no offense from my comment, it was not intended. When I answer somebody's question I try to be to the point and concise. 




As far as your previous question, following the next quotation is one definite possible solution [it would solve your problem depending on whether you actually need touch enabled] and the other solution you can try. 

> **ianni67 said:**
> 
```
xsetwacom set Wacom_Bamboo_Craft_Pen0 MMonitor off
```to confine the cursor to a single screen and switch screen by using the mouse to move the cursor to the desired screen. 

This approach works perfectly with the pen but with touch it has a strange behaviour.

I can (I should not!) move the cursor to the other screen by using the touch, but after moving to the second screen I cannot move it back to the first and have to use the mouse. 
It looks like a one-way fence. I tried everything I could figure out.

Please, any suggestion?

More, and more, thanks to all those who wrote, improved and helped us in using those and all the other drivers.

OK, I think I can help you with your problem.  if you do this command ```
xsetwacom list
``` you will see that there are MANY devices listed. These are the handles to the other things, like touch. You can try your MMonitor command with others of these [i.e. in replace ofWacom_bamboo_craft_pen0 etc]. Also, scrolling a few pages back, you will find a post by me that will be helpful in instructing you how to disable touch altogether. Hopefully one of these methods will prove useful. 

Either way, your results would be interesting to hear as I'm sure there are lots of artists with multi-monitor setups using wacom tablets.

---

### Post by TheguywholikesLINUX on 2010-03-22
> **texaswriter said:**
> There is a way to set the *touch* to behave either like the synaptic pad or like how the stylus is mapped to a specific location of the screen per specific location of the tablet. I don't know if you can do the same thing [switching] for the stylus too. If it did, it might give you more power to control the resolution. 

You can get the stylus to work like a finger on a laptop touch pad (in windows anyway)

---

### Post by Ayuthia on 2010-03-22
> **texaswriter said:**
> According to what I understand, if you are installing Lucid, it is a beta or alpha. Some things aren't finished. It isn't that it doesn't work, I believe something it actually relies on isn't yet supported. I did actually try to upgrade to Lucid [just to see what would happen] and MANY things were broken before being able to install the things that would get a) my wireless nic card working b) Wacom tablet... 

So, if tablet usage is important, I would stick with Jaunty or Karmic for the time being.

I installed Lucid about a month or two ago. Things may have changed since then. If anybody is using Lucid and has a CTH-460 model Wacom tablet working, please post with setup details.

The source code that is being used in Lucid is different than what is in Karmic.  A decision was made to rebuild the source for Xorg 1.7.  The other change is that the kernel module source and the Xorg source are now separated.  From what I can see, the kernel module is not up to date for the Pen and Touch but I have not checked the xorg source yet.  When I have some time, I will try to see if we can get the kernel module patched up so that we can get the device to work again.

---

### Post by gabe_rosser on 2010-03-22
Hi @ianni67, it sounds like your setup is similar to mine.  The exceptions: I don't rotate one of my screens, and I only have a Bamboo pen (not pen and touch).  My graphics card is also Nvidia.

Could I please ask you about your xinerama setup?  I can't localize my stylus pointer to one screen - it just ignores that command completely.  I'm wondering whether it's because I have xinerama disabled and should be using it.

Would you mind having a look in your /etc/X11/xorg.conf and telling me if there's any reference to xinerama there?  The relevant lines in mine are:

```
Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

so it looks like I have xinerama disabled but TwinView enabled.

Thanks for your help with this.

> **ianni67 said:**
> Hi everyone,
I have a karmic desktop 32 bit.

I just bought a bamboo pen and touch and started googling.

My configuration is a bit unusual therefore I decided to post here my short experience in the hope it can help someone and get me some help.

I have two monitors: one (screen0) is horizontal, the other one (screen1) is vertical, i.e. rotated 90°cw. This configuration is very useful for reading and editing full-page documents.

I have a nvidia card so I use the xinerama extension to have a sort of twinview. It works great and I can move a window from one screen to the other and have a window just in the middle of the two screens (completely unuseful, but it gives the idea).

I bought the bamboo mainly to use it as a touch device, sort of a touchpad. I have pain in my wrist and this makes me hate the mouse.

So this is what I got till now:
- the pen is working, it stays confined in the screen where I put it with the mouse. If I want to change screen I grab the mouse, click on the target screen and that's all.
- the pen works great, indeed.

...

best wishes and thank you very much for your great work.

---

### Post by gabe_rosser on 2010-03-22
Hi @texaswriter, thanks again for your suggestions.

> **texaswriter said:**
> There is a way to set the *touch* to behave either like the synaptic pad or like how the stylus is mapped to a specific location of the screen per specific location of the tablet. I don't know if you can do the same thing [switching] for the stylus too. If it did, it might give you more power to control the resolution. 

What is the command/setting for the touch please?  Perhaps I can use a similar setting on my Bamboo Pen?

> Also, be aware that xsetwacom list will show the device names. Just double check that you are using your command with the correct device name.

Yes, I've noticed that the names depend on the .fdi in use.  I check the device names before I use the command - and if I get them wrong it throws an error anyway - so that's not the problem.

Anyone else with any ideas here?  It's not an annoying little problem, I really can't use my Bamboo Pen as it stands :(  The horizontal hypersensitivity and unnatural ratio makes it practically useless.  Surely someone must know how to prevent the stylus mapping to the *entirety* of a dual screen setup?!

Thanks all.

---

### Post by ianni67 on 2010-03-22
> **gabe_rosser said:**
> Hi @ianni67, it sounds like your setup is similar to mine.  The exceptions: I don't rotate one of my screens, and I only have a Bamboo pen (not pen and touch).  My graphics card is also Nvidia.

Could I please ask you about your xinerama setup?  I can't localize my stylus pointer to one screen - it just ignores that command completely.  I'm wondering whether it's because I have xinerama disabled and should be using it.

...

so it looks like I have xinerama disabled but TwinView enabled.

...


The xinerama and the twinview extensions are quite different in behaviour.
I did not try recently the twinview mode so I cannot tell you how to make it work with the Bamboo.

You might try my configuration. Just keep in mind that my monitor is rotated so in my configuration there are a couple of commands to re-align the two monitors.

Here is my xorg.conf:


```
Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "QBL QB19F-4WLH-B"
	HorizSync       30.0 - 83.0
	VertRefresh     50.0 - 76.0
	Option         "DPMS"
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Unknown"
	ModelName      "Samsung SyncMaster"
	HorizSync       30.0 - 81.0
	VertRefresh     56.0 - 75.0
EndSection

Section "Screen"
	Identifier     "Configured Screen Device"
	Device         "Configured Video Device"
	Monitor        "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Virtual     2880 900
	EndSubSection
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "RandRRotation" "true"
	Option         "TwinView" "0"
	Option         "metamodes" "DFP: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Screen"
	Identifier     "Screen1"
	Device         "Device1"
	Monitor        "Monitor1"
	DefaultDepth    24
	Option         "RandRRotation" "true"
	Option         "Rotate" "CCW"
	Option         "TwinView" "0"
	Option         "metamodes" "CRT: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "Extensions"
	Option         "Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 665
	Screen      1  "Screen1" 1440 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
	Option         "Xinerama" "1"
	#    Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Driver         "nvidia"
	Option         "NoLogo" "True"
	#	Option         "RandRRotation" "true"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 8400 GS"
	BusID          "PCI:1:0:0"
	Screen          0
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Device"
	Identifier     "Device1"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 8400 GS"
	BusID          "PCI:1:0:0"
	Screen          1
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option         "Xinerama" "1"
	Option         "RenderAccel" "True"
	Option         "DamageEvents" "True"
	Option         "BackingStore" "True"
	# Removed Option "Xinerama" "0"
EndSection

```

Sorry for posting this long file but I hope to make things clearer.

Please note also my ~/.xinitrc, containint a few configurations for the tablet:

```
xsetwacom set "eraser" TwinView "1"
xsetwacom set "eraser" Screen_No "-1"
xsetwacom set "stylus" TwinView "1"
xsetwacom set "stylus" Screen_No "-1"
xsetwacom set "pad" StripRDn "Button 5"
xsetwacom set "pad" StripRUp "Button 4"
xsetwacom set "pad" StripLDn "Button 5"
xsetwacom set "pad" StripLUp "Button 4"
xsetwacom set "pad" Button4 "Button 4"
xsetwacom set "pad" Button3 "Button 3"
xsetwacom set "pad" Button2 "Button 2"
xsetwacom set "pad" Button1 "Button 1"
xsetwacom set stylus MMonitor off
xsetwacom set eraser MMonitor off
# run the primary system script
. /etc/X11/xinit/xinitrc
```

I'm currently using the .fdi made by Favux (see:[http://ubuntuforums.org/showpost.php?p=8165182&postcount=384](http://ubuntuforums.org/showpost.php?p=8165182&postcount=384)) to get rid of the changing device names, but there are some problems with the touch which I will describe in my next post. The pen works perfectly.

I hope that this helps you.

---

### Post by ianni67 on 2010-03-22
@texaswriter: 
Thank you for clarifying your previous post.
I fully understand your point. Again, I apologize for going somewhat off-topic.
My intension was to make clear the fact that what we get here is entirely volunteering work.

Now, back to the Bamboo: currently my pen is working perfectly with the configuration I posted above. My problem is that I really need also touch.

With my configuration, using the file .fdi (the one specific for Bamboo P & T) posted by Favux ([http://ubuntuforums.org/showpost.php...&postcount=384](http://ubuntuforums.org/showpost.php...&postcount=384)), I obtain the following output from xinput --list (I removed the unrelevant entries):

```

"pad"	id=2	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 8
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 480
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 320
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 71
		Resolution is 1
"touch"	id=5	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 480
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is 320
		Resolution is 1
"eraser"	id=6	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14720
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9200
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"stylus"	id=10	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14720
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9200
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
```
Note that the "touch" device is of type TOUCHPAD, but should be "Wacom touchpad". So something goes wrong, probably with the .fdi file.

Or, some other driver is capturing the touch and I cannot get rid of it.

If I launch the command: 

```
ianni@goliath:~$ xsetwacom set touch MMonitor off
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set touch value for 'mmonitor'
```

The same command works perfectly with stylus and eraser.

Any help, please?

---

### Post by gabe_rosser on 2010-03-22
Hi Ianni67,

Thanks for the suggestion.  I just tried your configuration.  I get dual screen display as expected but notice the following:

- Composite is disabled, meaning I lose my desktop effects (no more nice Compiz).  I think this is a limitation of Xinerama.

- The pointer now gets properly restricted to a screen and switching works.

- However there is an offset between the mouse pointer and the actual drawing in GIMP and Inkscape.  Described in a few posts online:
[https://bugzilla.gnome.org/show_bug.cgi?id=66813]("https://bugzilla.gnome.org/show_bug.cgi?id=66813")
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267]("https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267")
I haven't had a chance to try out the solutions.

Ultimately I don't think I'm willing to sacrifice Compiz and 3D effects for the tablet - Xinerama seems like a step backwards from where I am now, since TwiView allows both screens to render 3D effects.


> **ianni67 said:**
> The xinerama and the twinview extensions are quite different in behaviour.
I did not try recently the twinview mode so I cannot tell you how to make it work with the Bamboo.

You might try my configuration. Just keep in mind that my monitor is rotated so in my configuration there are a couple of commands to re-align the two monitors.

...

I hope that this helps you.

---

### Post by gabe_rosser on 2010-03-22
Dear All,

Having had little success with my attempts to limit the tablet to one screen in a dual head setup running TwinView (nVidia graphics), I have created a new post to deal with it:

[http://ubuntuforums.org/showthread.php?p=9011810#post9011810]("http://ubuntuforums.org/showthread.php?p=9011810#post9011810")

Please take a look if this relates to your problem.  Also if you are a developer!  I'll leave this thread to those of you trying to get touch to work (at least I don't have to worry about that :) )

---

### Post by ianni67 on 2010-03-23
> **gabe_rosser said:**
> Hi Ianni67,

Thanks for the suggestion.  I just tried your configuration.  I get dual screen display as expected but notice the following:

- Composite is disabled, meaning I lose my desktop effects (no more nice Compiz).  I think this is a limitation of Xinerama.

...

Ultimately I don't think I'm willing to sacrifice Compiz and 3D effects for the tablet - Xinerama seems like a step backwards from where I am now, since TwiView allows both screens to render 3D effects.

Sorry for forgetting this detail.

I sacrificed compiz but I still have compositing with metacity -c, No 3D but smooth windows motion, screenlets and much more stability. I like compiz (I've been using it since the very first time) but I can live without it.

---

### Post by texaswriter on 2010-03-23
> **ianni67 said:**
> Now, back to the Bamboo: currently my pen is working perfectly with the configuration I posted above. My problem is that I really need also touch.


I think you already have the mode set: What I was referring to was ```
xsetwacom set touch Mode Relative
``` 
I think you already have that set. 

I find that I get two different effects. If I plug the wacom tablet in as my computer is starting [before OS loads], my touch is weird, acts like scrollbar [which actually isn't bad for me since I don't actually use touch. The scrolling is actually useful :-D :popcorn::KS teehee!! But the stylus works perfectly [always]

BUT, if, after everything is loaded, i do the following 
```
sudo modprobe -r wacom
sudo modprobe wacom
```
then the touch works like it should. And since it is 0.8.5-10 [as opposed to 11] the touch works like it is supposed to it mostly. Actually works better than it ever used to... Touch works almost perfectly, except it will get lost if you move to fast. Touch, moving, multi-touch, works very good. It never was near perfect when I had it installed last time.

So, I would try doing the above code routine with every reboot and see if that helps.

---

### Post by ianni67 on 2010-03-24
This is weird: 
I did a reboot, then 
```
sudo apt-get install wacom-tools
sudo apt-get purge wacom-tools
cd linuxwacom-0.8.5-10
sudo make install
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
sudo modprobe -r wacom
sudo modprobe wacom
```

(note that the module was already compiled as I compiled _and installed_ it some days ago according to the original post.)

Then plugged the tablet in and:

```
xinput --list
```

gave me TWO touch devices! One is the correct one (wacom) but has a wrong name ("touch touch") and the other one is still the wrong one with the right name.

```
ianni@goliath:~/Scrivania/linuxwacom-0.8.5-10$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ImPS/2 Generic Wheel Mouse"	id=2	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Darfon Wireless Keyboard & Mouse"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Darfon Wireless Keyboard & Mouse"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 18
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Sleep Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Trust GM-4200 Gamer Optical Mouse"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 14
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"eraser"	id=9	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14720
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9200
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"pad"	id=10	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 8
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 480
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 320
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 71
		Resolution is 1
"touch touch"	id=11	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 480
		Resolution is 25
	Axis 1 :
		Min_value is 0
		Max_value is 320
		Resolution is 25
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"touch"	id=12	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 480
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is 320
		Resolution is 1
"stylus"	id=13	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14720
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9200
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1

```

Oh my... what should I do?
I suppose I have _two_ drivers but cannot figure out which module I should remove. I never installed other drivers for touch devices, where does this "other" driver come from?

---

### Post by alpharesearch on 2010-03-24
Hello,

I have a Bamboo CTH-661 (Pen and Touch) and a Nvidia GTX260  both set to TwinView (xsetwacom get stylus NumScreen gives me a 2, any idea?) because I have two monitors. I don't need touch right now and only want to get the pen working on only one screen (1920x1080); right now the combined resolution is 3840x1080. I tried for a couple of hours now but it is not going to just one screen. I don't want to use Xinerama because I like to have 4 panels. From what I read this is not supported right now? Any suggestions?


Here is my xorg.conf file:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
As a test I did remove the whole screen1 sction and this makes no difference at all. I also removed the TwinViewXineramaInfoOrder line and this also makes no difference at all.

Here is my 10-linuxwacom.fdi file:
```

<?xml version="1.0" encoding="ISO-8859-1"?>

<!-- Wacom:  tablets, tablet pc's, and touch screen laptops -->
<deviceinfo version="0.2">
  <!-- for all Wacom USB tablets -->
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.Twinview" type="string">horizontal</merge>
	<merge key="input.x11_options.TVResolution" type="string">1920x1080,1920x1080</merge>
	<merge key="input.x11_options.ScreenNo" type="string">0</merge>
	<merge key="input.x11_options.Mmonitor" type="string">off</merge>
	<merge key="input.x11_options.Button1" type="string">1</merge>
	<merge key="input.x11_options.Button2" type="string">2</merge>
	<merge key="input.x11_options.Button3" type="string">3</merge>
	<merge key="input.x11_options.Button4" type="string">4</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<append key="wacom.types" type="strlist">pad</append>
        <!-- for HP dv3-2250 multi-touch laptop -->
        <match key="info.udi" contains="e2">
          <merge key="input.x11_options.Type" type="string">touch</merge>
        </match>
      </match>
    </match>
  </device>
  <!-- for most Wacom USB tablets with touch -->
  <device>
    <match key="input.originating_device" contains="if1">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">touch</merge>
        <!-- for Bamboo Pen & Touch tablets -->
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <!-- for Wacom Serial tablets -->
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf;FUJ02e5;FUJ02e7">
	<append key="info.capabilities" type="strlist">input</append>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
	<merge key="input.device" type="copy_property">serial.device</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<!-- Serial tablets with touch capabilities -->
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009;WACf010;WACf008A;WACf00B;WACf00C;WACf00D;WACf00E;FUJ02e7">
	  <append key="wacom.types" type="strlist">touch</append>
	</match>
        <!-- Serial tablets that operate at higher baud rate -->
        <match key="@info.parent:pnp.id" contains_outof="WACf008">
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
        </match>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
	  <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	  <append key="wacom.types" type="strlist">eraser</append>
	  <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
  <!-- Wacom names "parser" -->
  <device>
    <match key="info.udi" contains_not="subdev_0">
    <match key="info.udi" contains_not="subdev_1">
    <match key="info.udi" contains_not="subdev_2">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="info.product" type="string">stylus</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="info.product" type="string">eraser</merge>
      </match>
      <match key="input.x11_options.Type" contains="cursor">
        <merge key="info.product" type="string">cursor</merge>
      </match>
      <match key="input.x11_options.Type" contains="pad">
        <merge key="info.product" type="string">pad</merge>
      </match>
      <match key="input.x11_options.Type" contains="touch">
        <merge key="info.product" type="string">touch</merge>
      </match>
    </match>
    </match>
    </match>
  </device>
</deviceinfo>

```

On the Twinview" type="string">horizontal< I tried also the other ones like leftof etc... and I tried to change the screenNo to 1.
It would be nice to configure for example Button1 to switch between screens... I tried this in wacomcpl, but this did also not change anything.

---

### Post by texaswriter on 2010-03-25
I think somebody posted a thread for this dual monitor issue. Obviously, I think this thread and those that attend it [myself including] have proven that any question relating to wacom tablets are welcome, this particular thread is more centered around the basic functionality of the touch & pen bamboo tablets with respect to the alpha/beta drivers being developed by the volunteers. So, hopefully that thread proves useful for those particular users. 

As a question to somebody who is a bit more "in the know" about the kernel changes, I noticed when I did the last update to the Kubuntu kernel, the wacom tablet no longer works at startup. I have to do the following to get even the stylus and touch to work. Then the stylus and touch work as per my previous post. ```
sudo modprobe -r wacom; sudo modprobe wacom;
``` How is the small kernel changes effecting this so much. before, the stylus worked, but the touch acted like a scroll bar. [as one of my previous posts says]. 
The last kernel update updated the kernel headers, but I'm not entirely sure that it was an actual revision number change... I thought the uname-r was the same. 2.6.31-20-generic-pae

---

### Post by gabe_rosser on 2010-03-25
> **alpharesearch said:**
> Hello,

I have a Bamboo CTH-661 (Pen and Touch) and a Nvidia GTX260  both set to TwinView (xsetwacom get stylus NumScreen gives me a 2, any idea?) because I have two monitors. I don't need touch right now and only want to get the pen working on only one screen (1920x1080); right now the combined resolution is 3840x1080. I tried for a couple of hours now but it is not going to just one screen. I don't want to use Xinerama because I like to have 4 panels. From what I read this is not supported right now? Any suggestions?

...

On the Twinview" type="string">horizontal< I tried also the other ones like leftof etc... and I tried to change the screenNo to 1.
It would be nice to configure for example Button1 to switch between screens... I tried this in wacomcpl, but this did also not change anything.

Hi @alpharesearch,

I've been experiencing the exact same problem I think - look at my earlier posts on this thread.  I created a new thread too to see if anyone had any suggestions, but after 2 days no one has posted:

[http://ubuntuforums.org/showthread.php?t=1436543]("http://ubuntuforums.org/showthread.php?t=1436543")

I also registered this as a bug on Sourceforge, where the Linux Wacom developers hang out (I hope!) but again no reply yet:

[https://sourceforge.net/tracker/index.php?func=detail&aid=2975590&group_id=69596&atid=525124]("https://sourceforge.net/tracker/index.php?func=detail&aid=2975590&group_id=69596&atid=525124")

Maybe it would help our case if you visited the bug report and the thread above and just stated that you have the same problem?

---

### Post by alpharesearch on 2010-03-26
> **Ayuthia said:**
> 
Compile and install:
```
make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
```


To get my dual screen working I had to add this --enable-quirk-tablet-rescale to ./configure

```
make clean
make distclean
./configure --enable-wacom --prefix=/usr --enable-quirk-tablet-rescale
make
sudo make install
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
```

Please put this note in your howto, thank you.

Now thoses two lines in the file:
/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
file work:
<merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
<merge key="input.x11_options.ScreenNo" type="string">0</merge>

Markus

---

### Post by Ayuthia on 2010-03-26
> **alpharesearch said:**
> To get my dual screen working I had to add this --enable-quirk-tablet-rescale to ./configure

```
make clean
make distclean
./configure --enable-wacom --prefix=/usr --enable-quirk-tablet-rescale
make
sudo make install
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
```

Please put this note in your howto, thank you.

Now thoses two lines in the file:
/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
file work:
<merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
<merge key="input.x11_options.ScreenNo" type="string">0</merge>

Markus

Thank you!!  I have added it to the first post.

---

### Post by Ayuthia on 2010-03-26
> **texaswriter said:**
> I think somebody posted a thread for this dual monitor issue. Obviously, I think this thread and those that attend it [myself including] have proven that any question relating to wacom tablets are welcome, this particular thread is more centered around the basic functionality of the touch & pen bamboo tablets with respect to the alpha/beta drivers being developed by the volunteers. So, hopefully that thread proves useful for those particular users. 

As a question to somebody who is a bit more "in the know" about the kernel changes, I noticed when I did the last update to the Kubuntu kernel, the wacom tablet no longer works at startup. I have to do the following to get even the stylus and touch to work. Then the stylus and touch work as per my previous post. ```
sudo modprobe -r wacom; sudo modprobe wacom;
``` How is the small kernel changes effecting this so much. before, the stylus worked, but the touch acted like a scroll bar. [as one of my previous posts says]. 
The last kernel update updated the kernel headers, but I'm not entirely sure that it was an actual revision number change... I thought the uname-r was the same. 2.6.31-20-generic-pae

Whenever there is a kernel update, you will need to rebuild the kernel module.  This is because kernel updates will send new kernel modules over since they are compiled with the updated kernel source.  This will usually overwrite the kernel module that you compiled.  Even though the uname -r info is the same, there was a point release (2.6.32-20.XX) that changed something for the kernel.  I hop that answers your question.

---

### Post by portets on 2010-03-27
0.8.5-12 came out today. everything is the same for me; pen working perfectly, touch barely working.

two differences with the newer version though; multitouch stopped working, but it barely worked before anyway so it's no loss to me. and now the "touch" section in wacomcpl returns an error message when clicked. but it still has no options.

> Get: Unknown parameter 'gesture'
Get: Unknown parameter 'gesture'
    while executing
"exec xsetwacom get "$device" gesture "
    (procedure "createPanel" line 47)
    invoked from within
"createPanel 1 1 0 1"
    (procedure "CreateDevicePanel" line 10)
    invoked from within
"CreateDevicePanel $type $model"
    (procedure "updateDevice" line 25)
    invoked from within
"updateDevice"
    (command bound to event)

the rest of wacomcpl still works fine though. (stylus, eraser, pad)

---

### Post by ianni67 on 2010-03-29
An update to my status:
after fighting a little more, I foud that I had installed the synaptics drivers (I don't even imagine why, probably by default).
I uninstalled them and now I only have my bamboo device in the output of xinput.

But still with the "touch touch" name.

No way to confine the cursor on a sigle screen: it can move to the second, and then cannot move back to the first: it stays confined to the second. It's like the border between the two screens is one-way.

---

### Post by leny2010 on 2010-03-31
Have just installed 0.8.5-12 and my Wacom Bamboo Fun Touch & Pen CTH-661/S now works reliably with the stylus (on 0.8.5-11 I got a dancing pointer and phantom button presses). Touch doesn't work (yet) but I can live with a working stylus :-).

---

### Post by Arialia on 2010-04-03
Hi 

Thanks for this topic

i apply the first post and everything work fine for my Bamboo Pen

some remarks : 
if your X11 is managed by Hal ( Ubuntu Karmic for example) don't forget to install the lib hal developpement as Ayuthai show us in the first post

it will be great to simulate mouse wheel when stylus move on tablet with button 2 press like under windows

How do this under linux ? it is possible with actual driver or need modifications of it ?

another thing which could be great is emulation of more button : button 1 (stylus) and button 2 press together emulate button 4 for example

---

### Post by texaswriter on 2010-04-04
Ayuthia/other developers> I compiled the latest version from the open source website and am using that. Touch is working as well [it seems] as in the version downloaded here. Touch and multitouch work ok. Same problem with losing track if you move too fast. I just downloaded the version on the website and compiled according to the directions in the first post.

The new version is installed on my home computer, but same OS: Kubuntu Karmic. 

For anybody doing this however, the part of the steps where you copy the driver to your $(uname -r), the SOURCE directory has to be updated because the driver is no longer compiled and put into the 27 kernel directory, it's now put in the 30... so replace the "27" with "30".

---

### Post by PidgeyBlock on 2010-04-05
Hi guys

I have just bought a Bamboo pen and touch and I am having a problem with the "make clean" command. Although I have been using Ubuntu for nearly a year now, I am still relatively unexperienced with terminal commands, in the end I just copy paste whatever you tell me too.

This bit of code keeps coming up after I use the make clean command in the second code bubble in the **Option A** section and I dont know what to do from here, is this normal?
```

make clean
make: *** No rule to make target `clean'.  Stop.

```I am just making a normal compile and install. Also I don't wont to move on as I don't want to mess anything up.

Thanks

Sorry if this has been said before, but scouring through a thread with 100 pages is just too much.

---

### Post by Arialia on 2010-04-05
> **PidgeyBlock said:**
> Hi guys

I have just bought a Bamboo pen and touch and I am having a problem with the "make clean" command. Although I have been using Ubuntu for nearly a year now, I am still relatively unexperienced with terminal commands, in the end I just copy paste whatever you tell me too.

This bit of code keeps coming up after I use the make clean command in the second code bubble in the **Option A** section and I dont know what to do from here, is this normal?
```

make clean
make: *** No rule to make target `clean'.  Stop.

```I am just making a normal compile and install. Also I don't wont to move on as I don't want to mess anything up.

Thanks

Sorry if this has been said before, but scouring through a thread with 100 pages is just too much.
as it is first time you compile the driver , this error is normal because it has nothing to clean , but after compiling , if you made changes it is better to do 'make clean'

so don't be afraid about this 'error' it is perfecly normal

---

### Post by notafish on 2010-04-05
> **alpharesearch said:**
> 
Please put this note in your howto, thank you.

Now thoses two lines in the file:
/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
file work:
<merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
<merge key="input.x11_options.ScreenNo" type="string">0</merge>

Hello,

Is there a specific location in the file where these lines should go?
Thanks!

---

### Post by PidgeyBlock on 2010-04-05
> **Arialia said:**
> as it is first time you compile the driver , this error is normal because it has nothing to clean , but after compiling , if you made changes it is better to do 'make clean'

so don't be afraid about this 'error' it is perfecly normal

Oh thank you Arialia, I was afraid I did something wrong. I am going to continue on with the installation thing then.

Thanks so much

EDIT: Yay I'm lucky 1000

---

### Post by PidgeyBlock on 2010-04-05
Hi guys, I am back again and I think I am having a problem with the "cp" of the wacom.ko file.

```
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
cp: cannot stat `src/2.6.27/wacom.ko': No such file or directory

```I have checked to see if the linuxwacom-0.8.5-12/src/2.6.27wacom.ko exists there and it does not. 
But when I checked the /lib/modules/2.6.31-20-generic/kernel/drivers/input/tablet it seems to be there. Am I thinking of this copying and pasting thing back to front? Or is it that I am missing the wacom.ko file in the linuxwacom-0.8.5-12 altogether?

I am just going to push on through the instructions for now and see if I can get this working.

Thanks

PS: There is a wacom.ko file in the src/2.6.30 folder. You think its a good idea to copy paste that one instead? It seems to be the latest one.

---

### Post by texaswriter on 2010-04-06
> **texaswriter said:**
> For anybody doing this however, the part of the steps where you copy the driver to your $(uname -r), the SOURCE directory has to be updated because the driver is no longer compiled and put into the 27 kernel directory, it's now put in the 30... so replace the "27" with "30".

Pidgey> Try searching the thread if you have a question... As you said, 1000 posts, chances are good somebody might have asked. In fact, not 3 or 4 posts previous to yours I addressed that. 

The file you are looking you may find in the above named directory IF everything compiled right. Also, double check the following below as well. 

Ayuthia> Can you put the following in your directions... compiling will fail without it. A Fortran 77 compiler needs to be installed. The only way I know how to do it is by 
```
sudo aptitude install f2c
```

It will ask to install a few things... one of them is something 77 that is not as intuitive to find using aptitude search as one might think... So, Do that before ./configure or make or make install and everything should go fine.

---

### Post by PidgeyBlock on 2010-04-06
> **texaswriter said:**
> Pidgey> Try searching the thread if you have a question... As you said, 1000 posts, chances are good somebody might have asked. In fact, not 3 or 4 posts previous to yours I addressed that. 

The file you are looking you may find in the above named directory IF everything compiled right. Also, double check the following below as well. 


Wow, sorry for not checking. I will be more vigilant in the future I hope. Thanks Texaswriter.

EDIT: Wow my wacom works now, thanks Texas writer for the help, it wasn't nearly as complicated as I thought!

---

### Post by SaintDanBert on 2010-04-06
> **kgingeri said:**
> 
...
BTW another minor correction in post #1...

should be /usr/share/hal/fdi/policy/[COLOR="Navy"]20thirdparty/[/COLOR]

This is my observation - yes.  The by-path links show up, but no sym-links until you copy in the rules files.  The tablet does work with only the by-path, but I still like the more human-readable sym-links.
...


**wacomcpl** and other tools do not see the tablet devices. However, X11 detects the hardware and does reasonable, but incomplete things ...
*thus my need to read this thread*.

I've tried to follow what I've found in various threads, but so far no joy. It seems that I need to tinker with my FDI files because **wacom-tools** expects one set of names but **hal** detects and uses a different set of names.

I'm running Ubuntu Jaunty [recent patches] on a Thinkpad X61-tablet.
My kernel is v2.6.28-18-generic.

Stumped,
~~~ 0;-Dan

---

### Post by ianni67 on 2010-04-06
> **texaswriter said:**
> Ayuthia/other developers> I compiled the latest version from the open source website and am using that. Touch is working as well [it seems] as in the version downloaded here. Touch and multitouch work ok. Same problem with losing track if you move too fast. I just downloaded the version on the website and compiled according to the directions in the first post.

The new version is installed on my home computer, but same OS: Kubuntu Karmic. 

For anybody doing this however, the part of the steps where you copy the driver to your $(uname -r), the SOURCE directory has to be updated because the driver is no longer compiled and put into the 27 kernel directory, it's now put in the 30... so replace the "27" with "30".

I can fully confirm on my Ubuntu Karmic. 
Using the last version (0.8.5-12) downloaded from the sourceforge linuxwacom project web site ([http://downloads.sourceforge.net/project/linuxwacom/linuxwacom-dev/0.8.5-12/](http://downloads.sourceforge.net/project/linuxwacom/linuxwacom-dev/0.8.5-12/)) everything works exactly the same as with the patched version downloadable from the link in the first post here.

update: now the touch device is detected with its correct name: "touch". It was detected as "touch touch" with my previous setup (0.8.5.10 with patch). I still have the troubles described in my previous posts with confining the touch to a single screen. I suspect this is related to my unconventional settings (one monitor is horizontal and the second is vertical, i.e. rotated 90° cw).

---

### Post by halthur on 2010-04-07
Hi All!

Could someone help a stupid sod with explaining exactly what to do to get the tablet to work? I just bought the Bamboo Fun Pen and Touch (small). I have Ubuntu 9.10, and my knowledge in Ubuntu/Linux is completely limited to starting the computer and clicking the "Gimp" icon.  Some basic knowledge in programming is in there somewhere. But I really need a "for dummies"-version, preferably in just one reply.

Pls help?

/the other half

---

### Post by SaintDanBert on 2010-04-07
Is there any way to see or fetch all [aka, 100%] of this thread as one screen or file or "printer friendly"?

There are loads of details that weave in and out making screen reading
to pick out stuff relevant to me a bit troublesome.

Thanks,
~~~ 0;-Dan

---

### Post by texaswriter on 2010-04-08
> **halthur said:**
> Hi All!

Could someone help a stupid sod with explaining exactly what to do to get the tablet to work? I just bought the Bamboo Fun Pen and Touch (small). I have Ubuntu 9.10, and my knowledge in Ubuntu/Linux is completely limited to starting the computer and clicking the "Gimp" icon.  Some basic knowledge in programming is in there somewhere. But I really need a "for dummies"-version, preferably in just one reply.

Pls help?

/the other half

Hi Halthur, 

First off, please check this post [it's in this thread]

[http://ubuntuforums.org/showthread.php?p=9075022#post9075022](http://ubuntuforums.org/showthread.php?p=9075022#post9075022)

Then, head off to the VERY first post in this thread, here is that link as well...

[http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238) 

Follow the instructions PRECISELY and don't worry if you go get "errors" when you do clean or make clean. You'll be up and running in no time. 

And, ONCE you get that installed, return to this thread and click "search this thread" for GIMP to see if you find any useful hints for you. 

Good luck and let us know how it goes.

---

### Post by SaintDanBert on 2010-04-09
The "Wacom Serial Tablet PC Pen Tablet/Digitizer" (report from 'xinput')
for my Thinkpad X61-tablet, tablet-PC works ... sort of. I've tried much of this thread that looked like it might help without success. Can someone point me in the right direction?

1. As a laptop (screen landscape; with real keyboard) I can run **xournal** and use the stylus to make digital ink. [highlight]The eraser makes digital ink, too.[/highlight] It does not ... erase.

2. I can rotate the screen into tablet (screen portrait; real keyboard hidden) mode and the orientation changes. [highlight]The cursor does not follow the stylus.[/highlight]. It moves when the stylus moves but is in some un-related location on the display.

3. I cannot find the event that fires when I (a)extract the stylus, or (b) store the stylus with the built-in stylus storage slot. I know there is an event because win-dose reports extract and replace actions with a pop-up.

Cheers,
~~~ 0;-Dan

---

### Post by texaswriter on 2010-04-10
SaintDanBert> In Xournal, goto <Options> and select <Eraser tip> 

All the other special configurations for buttons can be found there. 

I don't know about your other two. Screen rotation works. If you are having problems, maybe you are using the wrong commands. Try searching the thread for "rotate" or "rotation".

---

### Post by TechGeek22 on 2010-04-12
I followed the instructions in the first post for my CTH-661 (bamboo fun pen and touch) on Karmic (2.6.31-20-generic).  Needed to set the bottom x and y.  

After setting, the touch used the fill size of the pad but if you move your finger faster is looses tracking... I assume this has to do with switching to gesture interpretation... Can this be adjusted?

After a reboot touch doesn't work. and I need to restart the driver with: 

sudo modprobe -r wacom
sudo modprobe wacom

Please let me know if I can provide anything else to "help you help me"...

---

### Post by texaswriter on 2010-04-12
TechGeek> These are my observations as well. The touch does seem to "lose track" if you move too fast. It's just that way. And yes, I have to do the ```
sudo modprobe -r wacom; sudo modprobe wacom
``` as well on reboot.

---

### Post by Ayuthia on 2010-04-12
> **texaswriter said:**
> TechGeek> These are my observations as well. The touch does seem to "lose track" if you move too fast. It's just that way. And yes, I have to do the ```
sudo modprobe -r wacom; sudo modprobe wacom
``` as well on reboot.

Before you do the modprobe commands, did you check to see if the wacom module is loaded?
```
lsmod|grep wacom
```
If it is not there, you can add it to the /etc/modules file and it should load it automatically when you boot.

---

### Post by TechGeek22 on 2010-04-13
Does this mean it's loaded?

user@my-desktop:~$ lsmod|grep wacom
wacom                  36584  0

---

### Post by Ayuthia on 2010-04-13
> **TechGeek22 said:**
> Does this mean it's loaded?

user@my-desktop:~$ lsmod|grep wacom
wacom                  36584  0

Yes.

---

### Post by munooka on 2010-04-13
I managed to get my bamboo touch working on Lucid (no gestures but everything else checks out)

I posted it here:
[http://ubuntuforums.org/showpost.php?p=9119518&postcount=782](http://ubuntuforums.org/showpost.php?p=9119518&postcount=782)

---

### Post by texaswriter on 2010-04-14
> **Ayuthia said:**
> Before you do the modprobe commands, did you check to see if the wacom module is loaded?
```
lsmod|grep wacom
```If it is not there, you can add it to the /etc/modules file and it should load it automatically when you boot. :popcorn::guitar::P:):KS:popcorn:

Learn something everyday.

---

### Post by pschulz01 on 2010-04-16
> **salvian said:**
> Hello.
I have a problem with Bamboo P&T on Karmic. I installed linuxwacom-0.8.5-11 from source and did all the things from the first post, but still have nothing :( no pen, no eraser, no touch.
```
usbcore: registered new interface driver wacom
wacom: v1.52-pc-0.4:USB Wacom tablet driver
usb 4-2: new full speed USB device using uhci_hcd and address 13
usb 4-2: configuration #1 chosen from 1 choice
input: Wacom BambooFun 2FG 6x8 Pen as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input24
input: Wacom BambooFun 2FG 6x8 Finger as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input25
device input24 is bound to the driver
device input25 is bound to the driver
must rebind
```means driver is ok, I suppose. But I have nothing on /dev/input/event* and /dev/input/wacom*
What can I do to help myself and linuxwacom? :)

Thanks.

Did you manage to get your tablet to work? I am seeing the same issue with my new Bamboo.

I get nothing when I do the following...

  xxd /dev/input/event*

---

### Post by SimbaStovall on 2010-04-22
Thanks for the help there.  I was finally able to get my tablet working.  Now the question I have is how to I set it for left handed use?  I'm a lefty and I feel akward trying to avoid the buttons.  Give it to me line by line in terminal please.  BTW there is a new driver linuxwacom-0.8.5-12 now.  Just thought I would let you know

---

### Post by Favux on 2010-04-24
Hi SimbaStovall,

For lefties see 4) in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").  Actually the production version 0.8.6 is out.  I'm sort of hoping someone will comment on it and compare it to the last development versions like -11 & -12.

---

### Post by maracaib0 on 2010-04-26
Hi All,
got a GTH 661/s, pen eraser, and buttons working on Karmic. however, 
touch is not working, in spite of LED reacting.
I checked the blogs but as a newbie maybe I am just clueless - sorry.
Grateful for any hints.

ok, used the issue -wacom touch was captured by synaptics driver. Solved issue due to post #875> 
thanks to Favux for his good description, bugfix and working fdi.

trying now to fix bamboo touch losing track on faster movements...

---

### Post by Favux on 2010-04-26
Hi maracaib0,

Welcome to Ubuntu Forums!

Glad the Synaptics fix worked for you.  Good find!

Are you using linuxwacom 0.8.6?

---

### Post by maracaib0 on 2010-04-26
Hi Favux, 
using .12.
THX for the nice welcome!

---

### Post by h2osoriano on 2010-04-28
Hi 
What i need to do if i want to install my wacoom bamboo pen in Lucid (Ubuntu 10.04)?

---

### Post by Favux on 2010-04-28
Hi h2osoriano,

Welcome to Ubuntu Forums!

I wouldn't recomment going to Lucid yet.  Ping just submitted a Gestures patch for the P & T's for xf86-input-wacom.  Right now I don't think xf86-input-wacom supports the P & T's too well, esp. on gestures.  Once the patch is accepted and committed then you can clone the git repostitory for the X driver xf86-input-wacom for Xserver 1.7 and compile a recent linuxwacom, say 0.8.6, for the usb kernel module.  See the [linuxwacom HOW TO ]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1")for what to do.

The above is if you want the most complete fuctionality available.  I don't know for sure if the stylus and single finger touch work out of the box in Lucid with xf86-input-wacom 0.10.6 and the default wacom.ko (the usb kernel module).  It may well.

Hope this helps.

---

### Post by rebecca2525 on 2010-04-30
Back after a break. :) 

The first post says to use linuxwacom 0.8.5-10 or 0.8.5-11; however,  the latest release is 0.8.5-12, which means the older versions aren't available anymore. Could someone upload an older version, or is -12 fine, too?

**ETA: Never mind, found the link in the first post to the old version... **:oops:

---

### Post by jpbouza on 2010-05-01
Installing the package from these page made my Bamboo Pen & Touch work in Lucid (even with the touch pad :)).

[https://launchpad.net/ubuntu/+source/xf86-input-wacom/1:0.10.5-0ubuntu4/+build/1702889](https://launchpad.net/ubuntu/+source/xf86-input-wacom/1:0.10.5-0ubuntu4/+build/1702889)

---

### Post by letatcest on 2010-05-03
I wasn't as lucky as jpbouza... 
I installed the Wacom Bamboo a few times in 9.10. Working fine, but had to re-install after every kernel update. 
Unfortunately I spend Sunday afternoon (using the [well known post (link)]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") trying to get the thing to work again in Lucid. I can't get it to work again. Any special solution for 10.04?

---

### Post by _Apollo_ on 2010-05-04
Hello, I have the  same problem, but I found a temporary solution. [COLOR=Magenta]**[Here]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/")**[/COLOR]  read.

[SIZE=1] here will forgive my bad English, I use google  translator.[/SIZE]

---

### Post by Favux on 2010-05-04
Hi _Apollo_,

Welcome to Ubuntu forums!

The solution was also posted by munooka on the first Bamboo P&T thread ["New Wacom Bamboo not working" post 782]("http://ubuntuforums.org/showpost.php?p=9119518&postcount=782").  It has been incorporated into the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Hope this helps.

---

### Post by texaswriter on 2010-05-04
On Kubuntu 10.04, I have linuxwacom-0.8.6-1 working. Touch and stylus works. As far as I know multi-touch/gestures don't work. Edit: clicking with touch doesn't work at all as far as I can tell. Otherwise working great for me!!!

Followed these instructions: [http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/](http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/)

Good luck!!

Edit [for clarification]: I have installed this on Kubuntu 10.04. I haven't tried it on Ubuntu 10.04 yet.

---

### Post by jpbouza on 2010-05-05
Hey guys, I'm having some troubles configuring my tablet with xsetwacom. It is not a problem with the driver or with the tablet. I think it must be some kind of trick with xsetwacom parameters.

The problem is assigning symbols to the buttons of the tablet. For instance, this line works just fine:

xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button4 core key CTRL

But if I put "+" or "-" instead of CTRL, it doesn't work... Normal keys work perfectly fine.

Any hints on this??

Thanks!

PD: By the way, I've got a Bamboo Pen & Touch, but xsetwacom recognizes it as a Bamboo Fun :s

---

### Post by _Apollo_ on 2010-05-05
**Favux, **Thank  you very much, your link helped me a lot.
WBR

---

### Post by lvanderv on 2010-05-07
> **jpbouza said:**
> 
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button4 core key CTRL

But if I put "+" or "-" instead of CTRL, it doesn't work... Normal keys work perfectly fine.


Use "plus" or "minus", as in:
```
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button4 "core key CTRL plus"
```

I hope this helps.

---

### Post by ionospheric on 2010-05-10
I did a fresh install of Ubuntu 10.04 and then installed the Wacom driver according to the instructions at

[http://ubuntuforums.org/showthread.php?t=1466770]("http://ubuntuforums.org/showthread.php?t=1466770")

I am repeating them here:```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2

tar -xf linuxwacom-0.8.6-1.tar.bz2
cd linuxwacom-0.8.6-1
./configure --enable-wacom
cd src/2.6.30/
make
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
sudo rmmod wacom
sudo modprobe wacom
```

After that, using the pad to move the mouse pointer worked perfectly.

I am using my Wacom Bamboo Touch CTT460 as a mouse replacement (basically the same as the trackpad on a laptop).

The problem that I am having now is that I don't know how to get the driver to recognize a single tap as a mouse click. When I move the mouse pointer over an unselected icon and tap, nothing happens at all.

I verified that xsetwacom works:

```
xsetwacom set "Wacom Bamboo 2FG Finger pad" Button4 core key CTRL plus
```

and button 4 on the pad will lead to the zooming feature.

But how do I get the driver to recognize a tap with the finger as a mouse event, specifically a left mouse click? Are there any xsetwacom commands to do that?

Thanks!!

---

### Post by lvanderv on 2010-05-11
Button1 of, in your case, "Wacom BambooFun 2FG 4x5 Finger"  (no "pad") should, by default, be button 1 (left click).  What is your output from this command:

```

xsetwacom -s get "Wacom BambooFun 2FG 4x5 Finger" Button1

```

---

### Post by ionospheric on 2010-05-11
> **lvanderv said:**
> Button1 of, in your case, "Wacom BambooFun 2FG 4x5 Finger"  (no "pad") should, by default, be button 1 (left click).  What is your output from this command:

```

xsetwacom -s get "Wacom BambooFun 2FG 4x5 Finger" Button1

```

When I issue

```
xsetwacom -s get "Wacom Bamboo 2FG Finger" Button1
```

I get

```
xsetwacom set "Wacom Bamboo 2FG Finger" "Button1" "1"

```

I believe that is what it is supposed to be, but still, no reaction when I tap the pad. But I can move the mouse pointer.

For completeness, here is the output of xsetwacom --list

```
Wacom Bamboo 2FG Pen eraser ERASER    
Wacom Bamboo 2FG Pen STYLUS    
Wacom Bamboo 2FG Finger pad PAD       
Wacom Bamboo 2FG Finger TOUCH  
```

---

### Post by kylos16 on 2010-05-13
hello, bamboo Fun Pen & touch user on Lucid (also, another hello from another ubuntu newbie here :P).

as of right now, nothing works, 

tried to install via various methods, none of them worked at all, and quite frankly, every method I try ends up with a roadblock, and I'm feeling like a fish out of water.

in fact the following code [FONT=monospace]ends up with a 404 error[/FONT][FONT=monospace]
[/FONT] ```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2
```

---

### Post by Ayuthia on 2010-05-13
> **kylos16 said:**
> hello, bamboo Fun Pen & touch user on Lucid (also, another hello from another ubuntu newbie here :P).

as of right now, nothing works, 

tried to install via various methods, none of them worked at all, and quite frankly, every method I try ends up with a roadblock, and I'm feeling like a fish out of water.

in fact the following code [FONT=monospace]ends up with a 404 error[/FONT][FONT=monospace]
[/FONT] ```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2
```

It looks like they are updating their version to [0.8.6-2]("http://sourceforge.net/projects/linuxwacom/files/linuxwacom/0.8.6-2/linuxwacom-0.8.6-2.tar.bz2/download").

---

### Post by kylos16 on 2010-05-13
> **Ayuthia said:**
> It looks like they are updating their version to [0.8.6-2]("http://sourceforge.net/projects/linuxwacom/files/linuxwacom/0.8.6-2/linuxwacom-0.8.6-2.tar.bz2/download").

ah, no wonder.

---

### Post by acermobile on 2010-05-15
Hi everyone.

I finally got the touchpad working (more or less...) and the stylus and the eraser working smooth. However, I am encountering the following problems:

Using xsetwacom I can reassign the plus sign "+" to the the pen or any other button, but the keycode is not properly replicated! More precisely, the keycode of the character corresponding to an US Intl Keymap is produced (ß). The same behavious is found for the minus key.

I have tried everything (at least everything that came up in my mind):
- "plus" instead of "+"
- modifying xsetwacom.c to particularly assign XK_Plus of XK_Minus to ks
- I have verified that the keystroke correponds to the proper UTF-8 character (0x002b and 0x002d for + and -, respectively).

Can anybody tell me what went wrong? BTW: I am using a german keyboard layout.

---

### Post by acermobile on 2010-05-16
For those interested here is a (minor) xsetwacom improvement:

edit xsetwacom.c (in xf86-input-wacom/tools)
add in line 2008: (before "switch(param->prop_format)")
printf("%-16s   -   ", param->name);

Then the property listing includes the parameter description which is much more comfty to use.

Another improvement is (imo) to comment out
//         fprintf(stderr, "Property offset doesn't exist.\n");
Then the listing (with the above patches applied) is comprehensive and includes only parameters supported by the device.

Hope this is of help for some of you.

---

### Post by marek_online on 2010-05-18
> **ionospheric said:**
> When I issue

```
xsetwacom -s get "Wacom Bamboo 2FG Finger" Button1
```I get

```
xsetwacom set "Wacom Bamboo 2FG Finger" "Button1" "1"

```I believe that is what it is supposed to be, but still, no reaction when I tap the pad. But I can move the mouse pointer.


I'm having the same problem as ionospheric here - movement on the touchpad, but no click on tapping the pad (indeed, all of the buttons on the pad just send the pointer to the top left of the screen). I'm using the CTL-460 (Pen & Touch), which is picked up as the BambooFun.

I've tried a the fdi file included in 0.8.6-2, as well as Favux's new-working version, just in case, but no change. I've also tried a few different versions of the "xsetwacom set" command above, to no avail. xsetwacom works fine for other things, such as setting touch to relative and rotating. wacomcpl just hangs before it opens a window though.

Great development overall though - great to see.

---

### Post by jpbouza on 2010-05-21
Thanks for the "plus" and "minus" tip guys!!! It worked! :D

---

### Post by aklo on 2010-05-24
I need  help installing my wacom bamboo on lucid.

My wacom bamboo pen used to work on lucid(when it was first released) then after 1week+ of not using it, the next time i need to use the tablet, it won't work.

The guide on the first page works for my new installed Lucid lynx when 10.04 went official but now it doesn't work.

Some specs:
Kernel version:2.6.32-22-generic

Some output of various commands (i saw from different guides)
xinput -list

yes i have 2mouse 1 for gaming 1 for normal use.
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer DeathAdder                      id=8    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft  Microsoft Basic Optical Mouse v2.0     id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]


```

lsusb

```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 056a:00d4 Wacom Co., Ltd 
Bus 004 Device 003: ID 1532:0016 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Additional info: I've tried various method (usually simply copy and pasting of provided codes) and editing various conf file which i forget which 1 is it...some xorg or something
so i'm not sure if it will make things complicated.

So i'll be visiting this thread whenever i'm at home for new solutions.

---

### Post by Favux on 2010-05-24
Hi aklo,

It's hard to tell what's wrong because you have worked with the configuration files and haven't supplied specifics.

Probably what happened is you had a kernel update which knocked out your tablet.  The reason that happens is the new kernel has a new modules directory (/lib/modules/`uname -r`/kernel/drivers/input/tablet/) and the wacom.ko you compiled is only in the old kernel's module directory.  So you have to copy the compiled wacom.ko to the new directory if you still have it or compile linuxwacom 0.8.6-2 for a new wacom.ko.  See the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") and first page of this thread.

---

### Post by aklo on 2010-05-24
alright i manage to get the bamboo pen working but it seems to work weirdly....


When i draw in gimp, if i draw a stroke and try to move the pointer, it just stucks there. I have to raise the pen higher till the board doesn't detects the pen and move to a new point to draw.

---

### Post by Favux on 2010-05-25
Did you reconfigure the extended input devices in Gimp?

---

### Post by aklo on 2010-05-25
Yes i did but still no luck.

I configured wacom 4x5 pen (Since i used this settings back in karmic)

I'm thinking that it may be 1 of the other config files but i'm not sure since i did all that can be done in GIMP...unless my settings are wrong?

I'm using wacom bamboo pen (CTL460)

Either way i'll be installing virtualbox in a weeks time hopefully i can use my tablet in winxp virtually..if i can't make if work in lucid.

---

### Post by acermobile on 2010-05-26
Hi.
I have experienced the same issue with the pen not moving after a "touch" event. My solution was setting up the propper wacom kernel driver (follow the instructions in this thread) and setup the stylus in xorg.conf (I also tried xorg.conf.d, but was not pleased with the result). Also, you have to relaunch the X-Server after plugging in (go to KDM Login and press ALT-E). Hopefully hot plug support is being added rather shortly.

---

### Post by Favux on 2010-05-26
Hi,

If I'm understanding what I'm reading correctly it seems we are back to the Hal/.fdi problems Intrepid had.  Basically you can not configure a dependent device in the 10-wacom.conf snippet, just as you could not configure a dependent device in the wacom.fdi until they came up with hal-setup-wacom for Jaunty.  In other words since eraser is a dependent device of the stylus, you can configure stylus but not the eraser.  Since touch is a separate device with the P & T you should be able to make another snippet for touch using the right MatchProduct line to pull it out but you won't be able to configure the pad (touch's dependent device).  I hope this is making sense.

So to configure dependent devices you are back to using the xorg.conf ([see post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384")).

The dev.s at the LWP just had a vote, and as soon as they implement the changes this is how you'll do it in the 10-wacom.conf, using eraser as an example:
```
Section "InputClass"
        Identifier "Wacom eraser class"
        MatchProduct "Wacom"
        MatchProduct "eraser"
        Option "Foo" "bar"
  EndSection

```
So it will require two match product lines.  No idea when this will be implemented.

---

### Post by aklo on 2010-05-28
I'm going to stop trying for now. I have exams next week.

However after exams, I'm determine to get my wacom working on this LTS since if i can get it to work, i'll probably don't have to worry about it till the next kernel update (which i will certainly not upgrade)

Basically next week, my term break I will reformat my entire computer to clear those junks in winxp that my bro and sis have and i'll assign an even larger partition to my personal ubuntu...ok I'm talkig too much...

**To main point:**

I need someone who knows how to configure a wacom bamboo pen to guide me through step by step and I really mean step by step. I've already did my share of reading and search and trying but it just don't work...to make it worst I have no idea what those commands are for... really so there is no point in directing me to another post...since I will not understand / or have already tried that solution.

I will try to give my kernel version or other specs require when the time comes which will be next week thursday.

Thanks for reading.

---

### Post by texaswriter on 2010-05-29
> **texaswriter said:**
> On Kubuntu 10.04, I have linuxwacom-0.8.6-1 working. Touch and stylus works. As far as I know multi-touch/gestures don't work. Edit: clicking with touch doesn't work at all as far as I can tell. Otherwise working great for me!!!

Followed these instructions: [http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/](http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/)

Good luck!!

Edit [for clarification]: I have installed this on Kubuntu 10.04. I haven't tried it on Ubuntu 10.04 yet.

Aklo> OK, I have gotten the pen portion of this working fine on Kubuntu 10.04 [which will basically work just the same on Ubuntu 10.04]. I did it on Kubuntu 10.04 from an update [though that shouldn't matter much either].  I followed these instructions

[http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/](http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/)

Just follow the instructions given, they work!! 

Good luck with your exams. Are you in quarter system if you have finals now? Or is it just summer I where you are.

---

### Post by aklo on 2010-05-29
Note: this package only supports Xorg server older than 1.6.5.
          You are running a newer version. 
Please build xf86-input-wacom instead.

You can build the kernel driver from this package though.

I got this error. So i downloaded what it suggested xf86-input-wacom  but after that i'm stuck, there are no instruction what so ever, I read the README inside and did

    $ ./configure && make

afterwards nothing happen.

Right now i'm stuck with a tablet which works but have no use to me because it does not sense where my stylus tip is if i did not touch the pad. It only move when the stylus is in contact with the pad and this make me unable to draw since i need it to work like it is a pencil/pen.

---

### Post by texaswriter on 2010-06-01
aklo> Yeah, come to think of it, I think I downloaded the most recent version from the website and merely followed the instructions from the link. Choose your file as is appropriate, but the instructions worked for me in Lucid.

---

### Post by aklo on 2010-06-01
I'll be reformating my computer today or tomorrow morning and i'll try again.

My guess is because i mess up some files...as i tried lots of method...editing xorg config file, editing some other xorg files other than config and using some .FDI file and place into hal or whatever shyt that is...haha....hope this time my problem will be solve.

If it works i'll post here, if it doesn't i'll post my frustration here too :)

---

### Post by Favux on 2010-06-01
Hi aklo,

To install xf86-input-wacom please see Appendix 5 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  You probably want to read Lucid near the top too.

---

### Post by aklo on 2010-06-01
> **Favux said:**
> Hi aklo,

To install xf86-input-wacom please see Appendix 5 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  You probably want to read Lucid near the top too.

Ok I just did the following:


**Appendix 5:  Installing xf86-input-wacom for Lucid**

1) First install git (you only need to do this once).  Open a terminal  and enter (copy & paste):
 	Code:
 	sudo apt-get install git-core 
2) Then change directory to your Desktop and clone the  xf86-input-wacom git repository (download xf86-input-wacom):
 	Code:
 	cd ./Desktop

git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom 
3) Next install the needed libraries and updates using the  following apt-get commands:
 	Code:
 	sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libncurses5-dev xutils-dev autoconf libtool pkg-config

sudo apt-get upgrade 

cd xf86-input-wacom

./autogen.sh --prefix=/usr

make && make install

**Lucid-configuring through 10-wacom.conf**:  You can still use  xorg.conf as in a).  Currently I recommend:
 	Code:
 	Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

 Section "InputClass"
 	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
	Option "Button2" "3"
 EndSection 
To edit use:
 	Code:
 	gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf 





I did all the above in order...still don't work.

The errors i encounter when doing the make && make install

make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
/usr/bin/install: cannot create regular file `/usr/share/hal/fdi/policy/20thirdparty/wacom.fdi': Permission denied
make[2]: *** [install-dist_fdiDATA] Error 1
make[2]: Leaving directory `/home/kelvin/xf86-input-wacom/conf'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/kelvin/xf86-input-wacom/conf'
make: *** [install-recursive] Error 1



I'm not sure if you mean by working that means that if i move my stylus, the pointer also move. Yes that works BUT when i tap my stylus once, it will just get stuck on the screen till i remove my stylus from the drawing area....and i have to move my stylus back before the pointer will move with my stylus again...and the process repeat.

I will try the above again maybe because i tried too many times and something gets destroyed so i'll try the above solution again when i do a fresh install.

You cannot imagine how many times i've tried every solution possible...

---

### Post by Favux on 2010-06-01
Hi aklo,

I'm a little confused.  You're in Lucid correct?  Lucid doesn't use HAL/.fdi so I have no idea why configure.in is trying to write a .fdi file:
```
/usr/bin/install: cannot create regular file `/usr/share/hal/fdi/policy/20thirdparty/wacom.fdi': Permission denied
```
Are you seeing errors in configure?  If so what are they?

Also the default wacom.ko in Lucid does not support the Bamboo P & T's.  Have you compiled, say linuxwacom 0.8.6-2 for it's wacom.ko?

---

### Post by aklo on 2010-06-01
Yes i'm definitely using lucid.

I have no idea too....that was the only errors i saw...all the above code runs ok.

Hmm I did that before the last time i tried compiling the wacom.ko using instruction from [this]("http://ubuntuforums.org/showthread.php?t=1458678&highlight=wacom+bamboo+pen") thread...and it was that thread that told me to use xf86-input wacom...but either way i did compile it and copying the files using this command:

sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/


Ok right now my computer is in a mess so things might not be working correct, i'll do is again with a fresh install.

So the 1st step i should do is to compile the wacom.ko using linuxwacom-0.8.6-2, then follow your instructions like i pasted above? Did i miss out any steps from your instructions?

I've read about calibrating the wacomcpl but is that for lucid?

---

### Post by Favux on 2010-06-01
Actually all you need to do in Lucid is to compile the newer wacom.ko (usb kernel driver).

The 01.10.5 xf86-input-wacom in Lucid already supports your tablet.  There might be some improvement in the newer 0.10.6 or the up to date git repository but probably not enough to make it worth compiling.  There is a new touch/gesture patch winding it's way through the approval process.  Once it's committed to the git repository it would be worthwhile to clone the git.

---

### Post by Favux on 2010-06-02
Hi everyone,

The new/updated 2 finger touch gestures just got added to the xf86-input-wacom git repository.  Any one interested in trying them out needs to clone the git repostiory and compile it.

---

### Post by abhiram.sharma on 2010-06-03
this is nice news- 2 finger touch gestures :)
sorry for my lack of knowlege, but- how do you clone the git repository and compile? i'll check older posts...

---

### Post by abhiram.sharma on 2010-06-03
Found this post- #782 by munooka, i think this should work

[http://ubuntuforums.org/showpost.php?p=9119518&postcount=782](http://ubuntuforums.org/showpost.php?p=9119518&postcount=782)

code:
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
cd xf86-input-wacom/
./autogen.sh --prefix=/usr
./configure && make
sudo make install

---

### Post by Favux on 2010-06-03
Hi abhiram.sharma,

You can also use Appendix 5 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

There may be a problem though.  They updated macros to 1.8 yesterday and Lucid has l.5 so I don't think you'll be able to clone the git.

We need to figure out if there is a way to update the Lucid macro version.

---

### Post by portets on 2010-06-03
what's macros?

and does the just released linuxwacom 0.8.7-2 have the gestures patch?

---

### Post by Favux on 2010-06-03
Hi portets,

I found the 1.8's at the Xorg site.  If there's a Ubuntu Lucid package I haven't found it.  So unfortunately that means compiling the macros too.  See:  [http://ubuntuforums.org/showthread.php?t=1038949&page=106](http://ubuntuforums.org/showthread.php?t=1038949&page=106)

---

### Post by aklo on 2010-06-03
> **Favux said:**
> Actually all you need to do in Lucid is to compile the newer wacom.ko (usb kernel driver).

The 01.10.5 xf86-input-wacom in Lucid already supports your tablet.  There might be some improvement in the newer 0.10.6 or the up to date git repository but probably not enough to make it worth compiling.  There is a new touch/gesture patch winding it's way through the approval process.  Once it's committed to the git repository it would be worthwhile to clone the git.


Thank you it works PERFECTLY now.

It turns out as you said...I only need to compile the newer wacom.ko. I didn't need to do anything else at all. 

Part of the problem why nothing works previously is because I did too many different configs and things might be working against each other....so after reformating and I tried again it works.

---

### Post by Favux on 2010-06-03
Hi aklo,

Great!  Nice job.  Enjoy it.  :)

---

### Post by aklo on 2010-06-04
There is a new kernel update today...the name is same to the one I already have 2.6.32-22 ...Hmm if i upgrade, do i need to complile the wacom.ko again?

---

### Post by Favux on 2010-06-04
You could first try copying your already copied wacom.ko into the new kernel's new modules directory.  If that doesn't work then compile.

---

### Post by dryder on 2010-06-05
Hi all,
WACOM BAMBOO CTL-460

After more than 1000 posts and tips, is anybody game to post a new ´HOWTO´ for the latest kernel release 2.6.32-22.36.x? Please?

It is very confusing trying to work out what to do especially when it comes to the conf files.

I have twice installed Lucid AMD64 and still can get the tablet working and it is a tool I very much need. Didn´t it work in Jaunty? I don´t understand why now is different.

David:)

---

### Post by Favux on 2010-06-05
Hi David,

Why it is different in Lucid is that the wacom drivers have been split.  Xorg took over the Xdriver part for Xserver 1.7 and linuxwacom kept the usb kernel part.  That's actually the more standard way to set it up.

To get it working in Lucid you need to compile a newer wacom.ko (the usb kernel driver) than the default one in Lucid.  So go to the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") and compile linuxwacom 0.8.6-2.  Read Lucid near the top and follow the instructions in Section 1.  There's a lot of explanation in there that makes it look more complicated than it is.

That will get your Bamboo working.

---

### Post by dryder on 2010-06-06
Thanks Favux,

I´ll do as you suggest - many thanks for that and the explanation.

David

---

### Post by dryder on 2010-06-06
Hi Favux,
AMD6D

I got to:
> 4) Now change directory into xf86-input-wacom and then compile and install xf86-input-wacom:
cd xf86-input-wacom

./autogen.sh --prefix=/usr

I checked evdev_drv.so is in /usr/lib/xorg/modules/input
but I received this:
```
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:44: error: xorg-macros version 1.8 or higher is required but 1.5.0 found
/usr/share/aclocal/xorg-macros.m4:39: XORG_MACROS_VERSION is expanded from...
configure.ac:44: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1

```
Can you suggest what I should do, please?

David

---

### Post by aklo on 2010-06-06
Hello 

I just configured my wacom bamboo pen few days ago follow this method.
[http://ubuntuforums.org/showthread.php?t=1458678&highlight=wacom+bamboo+pen](http://ubuntuforums.org/showthread.php?t=1458678&highlight=wacom+bamboo+pen)

Just replace linuxwacom-0.8.6.tar.gz  with linuxwacom-0.8.6-2

You can download linuxwacom-0.8.6-2 from [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-2.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-2.tar.bz2)

You won't have to do anything else.

It is actually the same method as the thread **Favux **suggested that you read but I have to say the post is quite confusing...

So maybe it is just us but to Favux: Great job on helping so many wacom users to get their wacom tablet working but maybe the post can be edited to make it easier for people like me who don't really know how linux work but just want to get their pen working.

From the extremely long guide, there are multiple methods like using the xf86-wacom-input thingy...which for me I didn't require that.



Edit: Dryder: If the above method don't work, you may have edited stuff which are not required...thus affecting the tablet from working correctly. Well it happened to me...I used the same method but don't work (as I tried various methods before)....so I did a reformat to make sure anything which I edited are returned to their original state and then it worked.

---

### Post by Favux on 2010-06-06
Hi David,

Remember I said to just follow Section 1 for the wacom.ko, which is the usb kernel driver.  Did you have a reason for following Appenix 5, which is for compiling the X driver xf86-input-wacom?

The problem you've run into is that they updated to the 1.8 macros for xf86-input-wacom a couple of days ago while Lucid has the 1.5 version.  I link to the Xorg 1.8 macros, but you have to compile them first before you can compile xf86-input-wacom.  Do you follow?  So unless you really want to clone the xf86-input-wacom git repository, say to get the new 2FG gesture patch, I recommend leaving it alone.  Or you could download the 0.10.6 tar which would avoid the macro issue.


Hi aklo,

I'd love to simplify it.  Since it deals with multiple versions of linuxwacom on multiple releases of Ubuntu that's a tall order.  If I split it up into multiple HOW TO's folks would get confused on which HOW TO to use.  If I remove explanations folks complain about having to follow commands by rote and not knowing what they are for.

Besides it looks simple to me.  If you concentrate on the commands, and don't get lost confusing the forest for the trees, it's telling you to do the following if you have a Bamboo P&T in Lucid:
```
cd ./Desktop

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-2.tar.bz2

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

(Do the purge lines in Lucid?  Haven't had enough reports to know, so skip for now.)

sudo apt-get install linux-headers-generic

tar xjvf linuxwacom-0.8.6-2.tar.bz2

cd linuxwacom-0.8.6-2

./configure --enable-wacom --prefix=/usr

make

sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a

reboot

(now check if the wacom.ko is auto-loading.)

lsmod | grep wacom
```
So what, 12 lines (if you count changing directory into the desktop)?  And thirteen if you count the check.  I guess that's part of the problem, at this point it seems straightforward to me.

---

### Post by djinnkeeper on 2010-06-06
ALRIGHT!  

So that worked for me (it autoloads at boot now) .. THANKS! 

However, I would like to restrict the pen to my primary monitor but if possible, keep using xinerama.  Currently, when I get about 2/3 of the way across the screen the pointer jumps to the other monitor.

Can I fix that with xsetwacom / wacomcpl or must I delve in to xorg.conf?  I'm scared. :(

Super happy to finally see some results though.  I was starting to *really *miss my Graphire.

---

### Post by Favux on 2010-06-06
Hi djinnkeeper,

Great!  :)  I guess I should have said "do the following if you have a Bamboo P&T or Graphire in Lucid"?

But seriously what model Graphire?  Is it a new model?

Unfortunately there is no wacomcpl in Lucid.

Yes, you should be able to use xsetwacom commands.  Partly the setup depends on your video card.  What do you have?  See if this thread:  [http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)   helps you.

---

### Post by djinnkeeper on 2010-06-06
Actually, I should have said, "Having this lump of a non-functional Bamboo Pen was making me long for my Graphire, which I recently gave to my brother.."  It's a Graphire 4 ..I actually sorta miss how you could take off the translucent face for cleaning + having the ability to decorate behind it.. but I need the Bamboo for widescreen comfort.  Essentially the same product though; more of an update than an upgrade.

I have the Pen without Touch.. is that going to matter?  I mean, is this method meant strictly for "Pen and Touch" or does it apply for the whole line (Touch, Pen + Pen and Touch)?

---

### Post by Favux on 2010-06-06
Ahhh.

Should work for all of them including the Pen.

---

### Post by djinnkeeper on 2010-06-06
..oh but I failed to answer your followup about my graphics card, which is an nvidia 9600gt.  When I gksudo nvidia-settings, I get this error:
> Xlib:  extension "RANDR" missing on display ":0.0".To my recollection, I have not manually modified xorg.conf since installing Lucid.. so what I'm about to show you has been generated and may be offensive or disturbing to children.
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC EA231WMi"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL P1110"
    HorizSync       30.0 - 121.0
    VertRefresh     48.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1600x1200_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Though I have read about it a bit in the past, Xinerama and TwinView still kinda confuse me.  I just want to avoid having a strip of unviewable desktop space. (because of the different resolutions of my monitors)

---

### Post by Favux on 2010-06-06
Hi djinnkeeper,

OK, nvidia, which is why you have a xorg.conf.  Not sure what you are asking/describing.  Did you check out the thread I linked you to?

Nvidia settings does some unnecessary things.  You can remove these sections from your xorg.conf:
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

```
along with these two lines in "ServerLayout":
```
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"

```
As always backup your current working xorg.conf and be prepared to restore it at the command line in case X is broken.

---

### Post by eWheeler on 2010-06-06
Hello All,

Favux suggested that I post in this thread; my question on this topic started [here](http://ubuntuforums.org/showthread.php?t=1038949&page=103#1024)

Here are the details:

[LIST]
[*]I am running Lucid x64 using a CTH-460  (056a:00d1 lsusb version).
[*]I am running the 0.8.7-2 linuxwacom kernel module and 0.10.6 Xorg module on Lucid's Xorg 1.7.
[*](I tried to use today's git of xf86-input-wacom and it complains of xorg-macros needing to be 1.8 since Lucid has 1.5)
[/LIST]

And the issues:

[LIST]
[*]I cannot figure out how to get tap-to-click working.
[*]When I move the cursor with my finger, it acts as if my screen has a 10x10 pixel grid across it, and the mouse is snapping to that grid.  It is not a smooth motion like it is with the pen.  I am using two nvidia displays at 1920x1200 for a Screen-0 size of 3840x1200.
[*]I have tried to play with the TopX/Y/BottomX/Y parameters--and while I can make the mouse jumpier (larger "grid") with big values like 0,0,40000,40000--I cannot make the mouse 1-pixel smooth.
[/LIST]

Any idea what I might try next?

-Eric

---

### Post by aklo on 2010-06-06
> **Favux said:**
> 

Besides it looks simple to me.  If you concentrate on the commands, and don't get lost confusing the forest for the trees, it's telling you to do the following if you have a Bamboo P&T in Lucid:
```
cd ./Desktop

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-2.tar.bz2

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

(Do the purge lines in Lucid?  Haven't had enough reports to know, so skip for now.)

sudo apt-get install linux-headers-generic

tar xjvf linuxwacom-0.8.6-2.tar.bz2

cd linuxwacom-0.8.6-2

./configure --enable-wacom --prefix=/usr

make

sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a

reboot

(now check if the wacom.ko is auto-loading.)

lsmod | grep wacom
```So what, 12 lines (if you count changing directory into the desktop)?  And thirteen if you count the check.  I guess that's part of the problem, at this point it seems straightforward to me.

Follow the above code.  
Or
More detailed version: [Here]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1")

---

### Post by dryder on 2010-06-07
Hi Favux,

Re-reading Section 1, I haven´t the foggiest how or why I ended up in Appendix 5.

I understand (too well) that it is frustrating when people do not follow simple requests and end up following different/wrong instructions than indicated. I apologise for causing any frustration. Perhaps my need clouded my reading of your Section 1 as I can find nothing in it to lead me to Appendix 5.

I will start again, hopefully nothing I did means a clean install is needed.

Thank you for your patience.

David

---

### Post by dryder on 2010-06-07
Hi Favux,

Re-doing Section 1, I see how I ended up in Appendix 5. In terminal, after:
> ./configure --enable-wacom --prefix=/usr
the last message was:
> Note: this package only supports Xorg server older than 1.6.5.
You are running a newer version. 
Please build _xf86-input-wacom_ instead.
You can build the kernel driver from this package though.

I ASSumed I was supposed to do that ...

Anyhow, after re-doing just Section 1 it works - I have not tested it extensively. So THANKS!

David

---

### Post by Favux on 2010-06-07
Hi David,

Great!  :)

Ahh, I see.  What happened is Ping added a Xserver check into linuxwacom 0.8.6-2 because people weren't able to compile linuxwacom anymore on Xserver 1.7 or up.  That's of course because the config.in was trying to build the X driver.  And linuxwacom's X driver doesn't work in 1.7 or up.  So for the first time it said "Oh, I'm in Xserver 1.7 or higher and I can only make the wacom.ko not the X driver or wacomcpl".  That's what the warning is telling you.  Unfortunately it doesn't quite say that, you're suppose to read as above I guess by context.

---

### Post by dryder on 2010-06-07
Hi Favux
AMD64 - Wacom Bamboo CTL-460

The more I grasp the more I realise how quickly the modules are updated even carrying the same name/number, a practise I am not used to. linuxwacom 0.8.6-2.x tells me more than always keeping the same number but I guess there is a good reason why. (I would just parse off the 0.8.6.2 if the .x did not ´matter´, so to speak).

Now, one question if I may. CTL-460 is pen only. But my mouse is set to left-handed. I seem to be up the creek in so far as I can not work out how to get the pen to be left handed. Is this a curse I am lefty with and so must always revert to right handed for the pen? I hope this is a linuxwacom related question or do I need to post it elsewhere?

David
PS Thanks for all your hard work on the guide. I do agree with you that studying and understanding it is better than just copy and paste.

David

---

### Post by Favux on 2010-06-07
Hi David,

Right, but I think you mean linuxwacom 0.8.6-x for the format.  That's the current "stable" branch and the current development branch is 0.8.7-x.

We should be able to rotate the tablet into lefty mode using xsetwacom commands, see [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

But since the tablet is pen only I'm fairly confident adding a rotate option to the 10-wacom.conf will also work.  So let's try it.  It's located in /usr/lib/X11/xorg.conf.d/.  To edit:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
Change the usb snippet/section from:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,	Option "Rotate" "HALF"
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

```
to
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Rotate" "HALF"
EndSection

```
Save, Close, and reboot.

---

### Post by dryder on 2010-06-08
Hi Favux

> I think you mean linuxwacom 0.8.6-x for the format.
Quite right - carelessness.

I tried changing the code (though my file did not have any commented out lines) with partial success.

In Gimp (oh, when are they going to work in 64 bit??) at least I could get the, for instance, Free Select Tool selected and hover over the picture. However, as soon as I actually touched the pad a menu keeps coming up - same as left click on a lefty handed mouse, right click for other odd folk:p

I couldn´t find any commands that would affect the pen changing action just because it touched the pad.

David

---

### Post by Favux on 2010-06-08
Hi David,

Alright, the tablet rotated?  But the button map didn't?  Stylus tip is suppose to be Button1 mapped as 1 (left mouse click) as default.  But instead it is 3 (right mouse click).  Hmmm, I don't recall other lefties reporting that.  So the rotate option in the snippet doesn't work right?  Let's try the xsetwacom commands in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") instead.
```
xsetwacom set stylus rotate HALF
xsetwacom set eraser rotate HALF
xsetwacom set touch rotate HALF
```
In Lucid you need to use:
```
xinput --list
```
to find out what device names stylus, eraser, and touch now have and substitute them with quotes into the commands.

Then let's see how the stylus tip behaves.  Actually we could also try xsetwacom commands to remap the buttons.

By the way cute doggie.  What's the breed?

---

### Post by dryder on 2010-06-10
Hi Favux

Please excuse the belated reply. I am not seeing the wood for the trees. 

xinput --list gives:

> david@ubuntu64:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen eraser             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                    	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger pad             	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                 	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=8	[slave  keyboard (3)]
Wacom Bamboo 4x5 Pen id=12 [slave pointer (2)] being what I am interested in (presumably).

You say:
> Bamboo Pen (CTL460) (without touch):
Code:

ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00d4", SYMLINK+="input/tablet-wacom-bamboo-pen"


/lib/udev/rules.d/40-xserver-xorg-input-wacom.rules does not exit and /etc/X11/xorg.conf doesn´t seem to have any bearing on wacom that I can see.

May I ask if you could explain what I should edit and enter please? Sorry to be a pain but I´ m finding it very confusing.

To answer your question, she was a Corgi - my protector Companion dog I loved dearly.

David

---

### Post by Favux on 2010-06-10
Hi David,

stylus = "Wacom Bamboo 4x5" = 12
eraser = "Wacom Bamboo" 4x5 Pen eraser" = 11
touch = "Wacom Bamboo 4x5 Finger" = 14

So the xsetwacom commands become:
```
xsetwacom set "Wacom Bamboo 4x5" rotate HALF
xsetwacom set "Wacom Bamboo" 4x5 Pen eraser" rotate HALF
xsetwacom set "Wacom Bamboo 4x5 Finger" rotate HALF
```
or
```
xsetwacom set 12 rotate HALF
xsetwacom set 11 rotate HALF
xsetwacom set 14 rotate HALF
```
If those entered in a terminal get the tablet setup "lefty" for you then you can make a script that runs at startup to automatically do it for now on.  Don't worry about the udev symlink rule/xorg.conf stuff you showed.

PS:  I just lost my Basenji a cpl. of months ago.  She was quite the snuggle pup.  It's hard to lose them isn't it?

---

### Post by dryder on 2010-06-10
Yes. Yes, it is very hard. I am sorry you lost yours.


Thanks - I´ ll try that. A bash script at startup makes it easy to understand ' where´ - thanks.

(Apologies for the spaces - Lucid mis-identified my Microsoft keyboard and insists on treating the single quote(´) as an accent character - hence ¨I ' m¨ becomes ¨I&#7743;¨ - damned annoying. Even the double quote requires two shift key presses to get it.)

David

---

### Post by dryder on 2010-06-12
Hi Favux,

Whatever I do, I can not get the pen to behave the same in Gimp as if it was set as right-handed. I have to hold the button down instead of just acting with the pen on pad. And even that is erratic.

I have tried the Gimp Input devices section too, but to no avail.

I notice too that xinput --list gives different values each reboot / plug in of the tablet. E.G. now it is:
> david@ubuntu64:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger pad             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                 	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen eraser             	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                    	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=8	[slave  keyboard (3)]
david@ubuntu64:~$ 

Thus,
stylus = "Wacom Bamboo 4x5" = 14
eraser = "Wacom Bamboo" 4x5 Pen eraser" = 13
touch = "Wacom Bamboo 4x5 Finger" = 12
so it seems a bash script at boot would not help unless a) the pad is plugged in and b) the values remain the same.

Perhaps running a script to change mouse lefty to right handed as I launch GIMP is the only solution?

David:(

---

### Post by Favux on 2010-06-12
Hi David,

That's confusing.  The changing numbers was a bug in the device naming that was fixed in the linuxwacom 0.8.5-12 (and up).  Yet you compiled the 0.8.6-2 wacom.ko, correct?

If you manually enter the commands, using the new 'xinput --list' numbers, do you still have the problem in Gimp?

Separately at least a couple P & T users have notice a serious lag between the stylus and lines forming in Gimp.  Have you seen this?

---

### Post by dryder on 2010-06-13
Hi Favux,

> you compiled the 0.8.6-2 wacom.ko, correct?
That is correct.

Using the new 'xinput --list' numbers if I use the xsetwacom commands. Gimp then works a bit better but I still need to use buttons on the pen whereas in Right mouse I do not. EG, to lassoo an object freehand in lefty mode I need to press a button on the pen to complete the lassoo - but whether it completes is a bit random _and_ dependant on the accuracy of being exactly at the start point of the lassoo. In right mouse mode it does it normally.

For me, there is no lag time with lines, lassooing etc - only on clicking menus, choosing tools etc some of which require a very adept simultaneous button press.

Here is this morning's  xinput --list with the tablet plugged in at turn on:
> david@ubuntu64:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen eraser             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                    	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger pad             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                 	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=8	[slave  keyboard (3)]
david@ubuntu64:~$ 


David

---

### Post by Favux on 2010-06-15
> Using the new 'xinput --list' numbers if I use the xsetwacom commands. Gimp then works a bit better but I still need to use buttons on the pen whereas in Right mouse I do not.
I have no idea what's going on.  The rotation commands shouldn't have this affect.  As far as I know no one else has reported anything similar.

So is it Gimp, the xsetwacom rotation commands, xf86-input-wacom, or the 0.8.6-2 wacom.ko?
> For me, there is no lag time with lines, lassooing etc - only on clicking menus, choosing tools etc 
Regarding the lag I mentioned:  do you have a 64-bit or 32-bit install?

I'm beginning to wonder if we are getting some sort of version conflict like we used to experience without the purge command.  Unfortunately we haven't been able to use the purge routine in Karmic or Lucid because of the new xserver-xorg-input-all dependency.  There was some indication of version conflicts occuring in Karmic.

---

### Post by dryder on 2010-06-15
Hi Favux,

AMD64 - 64 bit version installed - all updates
CTL-460 - with CTL-460/K above the barcode

Thanks for your reply. This is, to me, showing indications of:
* a conf file ether being ignored or over-ridden by other settings - it should be simple to swap functionality of input devices equally. i.e. mouse settings lefty or right handed should equally be read for all hand input devices? A purge, as you imply, would be good.
* it is not Gimp per se as having to hold the pen button while clicking menu etc. problems are global, or
* did I irrevocably change incorrectly a file when I:> xsetwacom set "Wacom Bamboo 4x5" rotate HALF
xsetwacom set "Wacom Bamboo" 4x5 Pen eraser" rotate HALF
xsetwacom set "Wacom Bamboo 4x5 Finger" rotate HALF
Incidentally, this only works (for me) if I use "Wacom Bamboo Pen 4x5".
* A problem in the kernel? As it all has to be repeated after a kernal upgrade then presumably it is reasonable to think the kernel either handles part of the process or updates files that have been changed by us for this without telling us or keeping the changes.

Canonical seem to focus on seemingly less important issues (such as the intended 'windicators' obsession already started by re-positioning of window min, max and close buttons) instead of current problems such as no [[COLOR="Blue"] sound when pressing a modifier key[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8453454&postcount=1"); some icons showing with the [[COLOR="Blue"]wrong background colour in panel [/COLOR]]("http://ubuntuforums.org/showpost.php?p=9200679&postcount=1") and more. I've been using Ubuntu since 6.04(?) and Accessibility features have always had problems - imho playing with things like windicators and ignoring things that are not working is unforgivable. Lucid is an LTS and things that used to work should be fixed quickly, things that always had problems should likewise get fixed.

Hmm, sorry for the rant :oops:

David

---

### Post by djinnkeeper on 2010-06-15
We cheapo Bamboo users (and Daves.. go team!) have to stick together .. I'm with you on your rant - I don't think many will blame you for being frustrated by your problems.  I assure you that by comparison, my rant was much less justifiable and much more ridiculous (I somehow managed to mention Batman.. :-s)

During my initial fumbling with xsetwacom, I had been attempting to use each of the 4 "Bamboo" device numbers in the xinput list (10-13 for me).  Though it appeared to save the changes I made to each number, they seemed to have no affect on the tablet's performance.  It was not until I stuck to "Wacom Bamboo 4x5 Pen" that things began to make some sort of sense.  I knew it didn't have a touch pad, but I had overlooked the fact that there was no eraser on the pen.  So I can confirm that your experience is easily reproducible or whatever.

..but I mostly wanted to have a reason to post so I could thank Favux and everyone even remotely affiliated with the handholding I've required to get this thing working.  All of the banter in all of the related threads has been a real big help in teaching me some basics about how devices are handled.

---

### Post by Favux on 2010-06-16
Hi David,

Since, as djinnkeeper points out, the CTL460 lacks an eraser, and touch for that matter, try just:
```
xsetwacom set "Wacom Bamboo 4x5" rotate HALF
```
Maybe xsetwacom is erroring out with non-existent devices:
```
xsetwacom set "Wacom Bamboo" 4x5 Pen eraser" rotate HALF
xsetwacom set "Wacom Bamboo 4x5 Finger" rotate HALF 
```
and not recovering gracefully.  And that's affecting Gimp.

I sort of agree with you about Lucid.  But I think it's mainly because Canonical lacks the developer resources and they have different priorities.  I think if we followed the twice yearly developer summits closer we'd have a better idea of what they are.  I know with the recent reorganization they are serious about getting into the black.

Besides in Lucid there is a serious regression for the Wacom tablet end user because of the lack of wacomcpl.  And that's due to Xorg taking over the wacom X driver with their xf86-input-wacom, not Canonical.  In fact as far as I can tell we are lucky to have xsetwacom in Lucid.  The LWP's developer resources are also spread thin.  Part of our problem is that xsetwacom isn't completely implemented.  And it's not clear to me what parts are still missing.  The new 'man xsetwacom' they added helps a little.

---

### Post by dryder on 2010-06-16
Hi djinnkeeper,

Are you lefty handed? If so, what do you do to set the pen please?

I stand corrected - it is, as you say, "Wacom Bamboo 4x5 Pen" and not what I typed ("Wacom Bamboo Pen 4x5").

Thanks. Glad yours is working (no sarcasm).

David

---

### Post by dryder on 2010-06-16
Hi Favux,

Today my xinput --list gives me the same numbers. After unplugging and re-plugging in, after xsetwacom... and after rebooting!

I tried ```
xsetwacom set "Wacom Bamboo 4x5" rotate HALF
``` but received the error as attached.

```
xsetwacom set "Wacom Bamboo 4x5 Pen" rotate HALF
```was accepted.

A slight improvement - I can now lassoo and complete but only with a deft button/pen co-ordination. Unfortunately, still needing the pen button is the killer.

After all the years I have not been aware of the twice yearly developer summits. I have not seen them even mentioned in the forums. Do you have a link?

I understand Canonical's intent to get into the black. Ipso facto, isn't that a very good reason to get old problems (Accessibility) and regressions (sound keys) sorted out? However much the linux faithful may hate to hear it, Ubuntu and others will never be taken seriously unless such basics are working and to the ex-Windows people it works without doing what we are doing. This sort of thing drives people away, not convert them.

May I ask the difficulties of using xf86-input-wacom as opposed to Section 1 of your tutorial? I'm only interested academically on the different approaches the two have, not criticising :p

Favux, I agree with djinnkeeper in thanking you and everybody else 'hanholding' us to try and get it working. Mine works perfectly - except in lefty mode - which just happens to be important to me. ](*,)

Until you mentioned it I was not even aware Xorg was separate from Canonical ... 

David

---

### Post by Favux on 2010-06-16
> A slight improvement - I can now lassoo and complete but only with a deft button/pen co-ordination. Unfortunately, still needing the pen button is the killer.
I'm wondering if the Pen is defaulting to 'hover' mode?  You could try:
```
xsetwacom set "Wacom Bamboo 4x5 Pen" TPCButton "on"
```
and off.  From:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)
> twice yearly developer summits. I have not seen them even mentioned in the forums. Do you have a link?
They're usually announced in stickies in the Development & Programming forum and Cafe a week or two before and during.  There's links to online streaming of sessions, etc..  I can't seem to find my links but here is some semi-relevant stuff.  Starting with the composite blog that usually carries a bunch of info. on the Summit.
[http://planet.ubuntu.com/](http://planet.ubuntu.com/)
[http://www.youtube.com/user/ubuntudevelopers](http://www.youtube.com/user/ubuntudevelopers)
[https://wiki.ubuntu.com/LucidLynx/TechnicalOverview](https://wiki.ubuntu.com/LucidLynx/TechnicalOverview)
> May I ask the difficulties of using xf86-input-wacom as opposed to Section 1 of your tutorial? I'm only interested academically on the different approaches the two have
Well what happened is that for Xorg's Xserver 1.7 (the one Lucid has) linuxwacom was split into two.  And xf86-input-wacom is the X driver part (wacom_drv.so) that Xorg took over.  The kernel part (wacom.ko) is still linuxwacom's as well as the X driver for Xservers lower than 1.7.

I was going to say that you should be good with the default 0.10.5 xf86-input-wacom that comes with Lucid and the only reason to update it would be if you have touch and wanted to try out the new Gestures patch.  But actually some additional stuff has been added like the escape key, up/down/left/right, and the xsetwacom manual (man xsetwacom).  But I'm not sure any of that's worth the adventure of cloning the git for you.

---

### Post by dryder on 2010-06-19
Hi Favux,

Thanks for the links and "9.0 - Command Line Configuration Interface (xsetwacom) is informative."

```
xsetwacom set "Wacom Bamboo 4x5 Pen" TPCButton "on"
xsetwacom set "Wacom Bamboo 4x5 Pen" TPCButton "off"
```

A definite improvement. Now, although the mouse still moves without the pen touching the pad, at last I have to touch the pad to start/stop an action, be it choosing something on the menu or starting/finishing a lassoo. The mouse moves while hovering or not touching the pad just as it does in right handed mode.

This had no effect at all used with the above, whether done before or after:```
xsetwacom set "Wacom Bamboo 4x5 Pen" rotate HALF
```

I have done comparisons in lefty / right modes. In lefty mode, the only thing now, for me, is having to use the pen button as well. It's behaviour is best described as without pressing the pen button it is like clicking the wrong button on the mouse - a menu comes up instead of the action happening.

I am perplexed why man xsetwacom says > No manual entry for xestwacom Have I corrupted the system?

I've lost my Windows wacom CD for the Bamboo Pen 4x5 - can anybody tell me how big the contents are please in MB and if prepared to zip and email me? Many thanks.

David
*PS My apologies for late replies at the moment*

---

### Post by Favux on 2010-06-19
Hi David,

Slowly getting there.  I need to see your whole current xsetwacom script, rather than one command at a time.  Along with the 'xinput list', at least with the tablet stuff.  Are the ID #'s still changing.

Man xsetwacom was added to xf86-input after 0.10.6.  You're still on the default 0.10.5 correct?  0.10.7 just came out two days ago.  There have been additions and fixes for xsetwacom and the 2FG gesture patch.  You're still using the 0.8.6-2 linuxwacom wacom.ko, correct?

Most everything seems to be "working" now in Lucid.  I even have Button1 acting as a touch on/off switch (with notification like Win!  :)).  Still some troubles in Gimp.  I have it "working" with either wacom.conf or xorg.conf.  I'm toying with the idea of posting my xsetwacom script along with the touch toggle script in post #384 in the next few days.  I basically imitate the default Win XP set up.

---

### Post by Favux on 2010-06-19
Hi,

I've updated [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") and added a sample xsetwacom script.  I also added a touch toggle script you can attach to one of your tablet buttons.

---

### Post by dryder on 2010-06-20
Hi Favux.

> I need to see your whole current xsetwacom script  ....  Are the ID #'s still changing.


Taking the second part of the above first, yes, the id's change each reboot. I have not written any of my own start-up scripts because of this - just enter into terminal. I can't think of a way of in a script to do 'xinput --list' and then substitute the correct number into a variable.

The first part, the only xsetwacom scripts I have are from those two created when I followed your Section 1 guide - one script for 32 bit the other for 64 bit (I assume). The 64 is attached as is a screenshot of  xinput --list. You can see it changed from 14 one day to 12 the next.
> 
You're still on the default 0.10.5I believe so.
> You're still using the 0.8.6-2 linuxwacom wacom.koYes.

> posting my xsetwacom script along with the touch toggle script in post #384Got them - thanks.

What other scripts do I need to attach?

David

---

### Post by Favux on 2010-06-20
Hi David,

I'm lost.  I think we're having a communication problem.

I don't know why you posted that "xsetwacom script".  It isn't one.  Hopefully the scripts I posted will help you.

Given your screen shots you don't have a Bamboo Pen, you have at least a Bamboo Pen and Touch.  What's your model number again?

You shouldn't see ID numbers varying with linuxwacom 0.8.6-2.  So either something went wrong with the compile or it's something else.  Are you using a hub to plug the tablet in?  Or are you plugging other devices in sometimes but not others?  I'm not seeing that in xinput but have to ask.

Besides that using the "Device name" should get around that unless that's changing too.  The name is the same in the two screen shots so the device should be found be xsetwacom.  That suggests an xsetwacom/xf86-input-wacom problem.  Have you gone to Synaptics Package Manager and told it to reinstall xserver-xorg-input-wacom and rebooted?

Summary:
Wacom Bamboo ?? in Lucid
kernel?  (run 'cat /proc/version_signature')
32-bit or 64-bit install?
linuxwacom 0.8.6-2 wacom.ko
xf86-input-wacom 0.10.5 (Lucid default)
using default 10-wacom.conf?
tablet plugged directly into usb port?
tablet works fine in Windows?

---

### Post by dryder on 2010-06-21
Hi Favux,

If I've messed things up or not understood I apologise - and am grateful for your perseverance, as always.
> 
Given your screen shots you don't have a Bamboo Pen, you have at least a Bamboo Pen and Touch. What's your model number again?See jpg - Wacom Bamboo Pen CTL-460. Requested and sold as 'Pen only'.
> Are you using a hubI wasn't initially but then I didn't want the tablet on all the time so moved it to a hub. This may be part of my undoing.(Clarification: I'm Ubuntu, work is Windows.)
In Windows, each hub position appears to remain the same for devices in so far as links to a usb device only work if the device is in the correct hub socket for that link BUT if in the same socket in the hub they retain the same device info however many times unplugged/rebooted.
I never gave this a thought in Ubuntu with the pad as I always use the same hub socket. My scripts for nightly backups to usb drives work fine in Ubuntu regardless of the hub socket so I never questioned the tablet. During my attempts to get it working the pad has remained in the same socket all the timed and the ids only change on reboots, remaining the same if unplugging/plugging in.
If I leave the tablet plugged into a usb port permanently, my test today show that the numbers remain the same (shutdown, restart etc). However, if in the hub they only remain the same per session for unplugging/plugging in.
> are you plugging other devices in sometimes but not others No.
> using the "Device name" should get around that unless that's changing tooDevice names do not change.
> Synaptics Package Manager and told it to reinstall xserver-xorg-input-wacom and rebooted?No - I did not see that in Section 1 nor have I today re-reading section 1. Reference was made to it constantly being updated, I think that is all. Should I? If so I misunderstood.


Summary:
Wacom Bamboo ?? in Lucid -- see jpg
kernel? -- Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2
32-bit or 64-bit install? -- 64-bit install
linuxwacom 0.8.6-2 wacom.ko -- attached
xf86-input-wacom 0.10.5 (Lucid default) -- yes
using default 10-wacom.conf? -- see attached
tablet plugged directly into usb port? -- see above
tablet works fine in Windows? -- yes - direct port and in hub

Re your previous post, > whole current xsetwacom script I haven't written any - only used terminal when I start testing. I assume none were generated during compile? I thought you meant the one in ~/linuxwacom-0.8.6-2/... folder. My apologies.


Favux, I know that I am not any good at this area of linux. You say that using the device name should overcome changing ids - that makes it possible then for me to write a startup script, surely? If so, that means I only have to solve the problem of needing to use a pen button when in lefty mode.

---

### Post by Favux on 2010-06-21
Hi David,

No worries.  I was trying to gently suggest that we needed to review some things.  I'm sorry if it came across harsher than that.

To sum up:
-You have a Bamboo Pen in Lucid.
-kernel = Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2
-64-bit install
-linuxwacom 0.8.6-2 wacom.ko - yes, you compiled it
-xf86-input-wacom 0.10.5 (Lucid default) - yes
-using default 10-wacom.conf - modified, let's remove the rotate option, see below
-tablet plugged directly into usb port - will be for now on while we trouble shoot

AFAIK the minimum to getting a Pen working in Lucid is to update the wacom.ko to at least linuxwacom 0.8.6-2.

Since you have a Bamboo Pen your .xsetwacom.sh script should look something like this (rather than the script in post #384):
```
## Device name and ID number from 'xinput --list'.

## stylus = ID ? = "Wacom Bamboo 4x5 Pen"
xsetwacom set "Wacom Bamboo 4x5 Pen" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom Bamboo 4x5 Pen" RawSample "4"  # default is 4
xsetwacom set "Wacom Bamboo 4x5 Pen" ClickForce "6"  # 1-21
xsetwacom set "Wacom Bamboo 4x5 Pen" PressCurve "5 10 90 95"  # default 0 0 100 100
xsetwacom set "Wacom Bamboo 4x5 Pen" TPCButton "on"  # side switch+tip; off=side switch only or "hover"
xsetwacom set "Wacom Bamboo 4x5 Pen" Mode "Absolute"  # or Relative
xsetwacom set "Wacom Bamboo 4x5 Pen" Button1 "1"  # left mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen" Button2 "3"  # right mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen" Button3 "2"  # middle mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen" Rotate "HALF"  # rotate 180 degrees
```
Set it up to auto-start as [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") demonstrates.  Go ahead and remove the rotate line so the usb snippet looks like:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
Usually a hub doesn't affect anything but I have seen them do weird stuff before, so it's best not to use them when trouble shooting a device.  Try it after things are working.
> If I leave the tablet plugged into a usb port permanently, my test today show that the numbers remain the same (shutdown, restart etc). However, if in the hub they only remain the same per session for unplugging/plugging in.
Good detective work.  That's what we want to avoid.  And so if you use the hub you'll have to use "Device name".

I guess it's my ignorance.  I don't know why a Pen would populate the 'xinput --list' the same as a Pen & Touch.  If I recall correctly the extra sub-devices, imaginary for the Pen, didn't show up in lshal for Karmic and Jaunty.

I'm thinking some of the confusion is due to my mistake.  When I told you to try xsetwacom rotate commands with eraser and touch.  Let's see if this fixes the stylus/stylus button behavior.

If not we can try remapping the stylus buttons.
> [QUOTE]Synaptics Package Manager and told it to reinstall xserver-xorg-input-wacom and rebooted?
No - I did not see that in Section 1 nor have I today re-reading section 1. Reference was made to it constantly being updated, I think that is all. Should I? If so I misunderstood.
[/QUOTE]
The xserver-xorg-input-wacom package contains xf86-input-wacom 0.10.5 along with xsetwacom and the 10-wacom.conf, etc..  We may need to try to update 0.10.5 to 0.10.7 if nothing else works.  Appendix 5 tells you how to do that.  Section 1 is for the wacom.ko.

---

### Post by dryder on 2010-06-24
Hi Favux,
Just wanted to say that I will do the above in a day or so. Not lazy or lack of interest - things need doing here before 30 Jun.

David

---

### Post by Favux on 2010-06-24
Not a problem.  You might want to take a look at the new [HOW TO Set Up the Bamboo Pen & Touch in Lucid]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by dryder on 2010-06-25
Hi Favux,

Thank you for the hard work in the new guide. 

> II. Install Xorg's xf86-input-wacom for Lucid (the X driver)Oops - I wasn't supposed to do that in my original attempt when you started helping me. Is this a dumb question - before I embark into the wild world of wacom, using this new guide are you advocating I now use the git and xf86-input-wacom section?

Presumably compiling the new 0.8.8-3 will overwrite any files I have changed?

David

---

### Post by Favux on 2010-06-25
Well remember with linuxwacom 0.8.3-3 you're only after the wacom.ko.  So the only file that gets over written is the wacom.ko.

> are you advocating I now use the git and xf86-input-wacom section?
Yes.  It looks like in Lucid to get things working right you need to update the X driver from xf86-input-wacom 0.10.5 (the default) to at least 0.10.7.  Cloning the get will get you updated past that.  And this will overwrite the default files.  Now that the macros thing is straightened out I think this part is no more difficult than compiling for the wacom.ko.

---

### Post by h2osoriano on 2010-07-11
Hi favux!
I've got  wacom bamboo pen, and i'm installing it in lucid following this how to [http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html)
But when i run this command ./configure –enable-wacom
the exit is 
NOTE: this package only supports Xorg server older than 1.7.
          You are running a newer version.
Please build the X driver from xf86-input-wacom.
What i need to do ?
Excuse me i'm not english 
I wait your answer

---

### Post by Favux on 2010-07-11
Hi h2osoriano,

The guide you are following is obsolete.  Starting with linuxwacom 0.8.6-2, linuxwacom was made aware of the Xserver version.  This is so it wouldn't try to build the Xdriver wacom-drv.so.  When it did that it wouldn't compile under Xserver 1.7 (Lucid).  That's why we went to the extra directory change (cd src/2.6.30/) to get around this.  This is no longer needed.

The warning just tells you that that version of linuxwacom is aware it is on Xserver 1.7 and so won't build the Xdriver.  And if you want it you need to compile xf86-input-wacom.  Follow?

I suggest you follow a more up to date HOW TO.  See:  [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)

---

### Post by portets on 2010-07-28
so did the touch patch ever get committed to linuxwacom?

---

### Post by Favux on 2010-07-28
Hi portets,

Yes and xf86-input-wacom got it by 0.10.7.

---

### Post by dsavi on 2010-07-29
I am  pulling my hair out trying to get twinview to work with my Bamboo Fun Medium. I spent several hours yesterday and more time today trying to get it to work. I compiled linuxwacom with --enable-wacom --enable-quirk-tablet-rescale, followed the instructions in [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1) but I can't figure out how to get it to work with Twinview.

Bamboo fun medium, 32bit lucid, 2.6.32-23-generic, I've compiled xf86-input-wacom 0.10.8 and linuxwacom-0.8.8.8. My tablet works fine otherwise (Windows doesn't do anything about dual screens either), I'm just trying to configure 10-wacom.conf, or if necessary, my xorg.conf for twinview. I don't know if that's all the info someone needs to help me.

[SIZE="5"]EDIT:[/SIZE]

This works **perfectly**: [http://kishalmi.net/cms/node/90](http://kishalmi.net/cms/node/90)

---

### Post by portets on 2010-08-16
will the linux wacom project leverage this? [http://www.phoronix.com/scan.php?page=news_item&px=ODUxMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODUxMQ)

and this: [http://www.phoronix.com/scan.php?page=news_item&px=ODUxMg](http://www.phoronix.com/scan.php?page=news_item&px=ODUxMg)

---

### Post by Favux on 2010-08-16
Hi portets,

I think there is little doubt of it.
> The X Gesture Extension is to work hand-in-hand with the recently-drafted X.Org Multi-Touch Protocol Specification that was written by input-expert Peter Hutterer.

A draft of the X Gesture Extension specification can be found on xorg-devel. The X Gesture Extension provides an interface
for X clients to register and receive primitive gesture events and an interface for these clients to act as a gesture engine.

Peter Hutterer is the Xorg developer who has been responsible for developing xf86-input-wacom for Xservers 1.7 and up.  He's on record as objecting to the gestures code in linuxwacom/xf86-input-wacom, because he wanted standardized code, not different code for each driver.  He allowed it to be included "temporarily" because there wasn't an alternative.  Looks like now there is.

---

### Post by jcannonsr on 2010-09-04
This worked for my pen and touch:

[http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html) 

Goto comment by:

ripps says:
JUNE 16, 2010 AT 7:17 PM
Hey guys, I’ve made a dkms packge that should allow people to build new wacom modules automatcially when new kernels are installed. I’d appreciate it people could test it for me.

sudo add-apt-repository ppa:ripps818/wacom; sudo apt-get update; sudo apt-get install wacom-dkms

---

### Post by dr4ziw on 2010-09-18
First of all: thanks to Favux for the great work you're doing!

Stylus is working! 
Touch, with the wcmCommon.c workaround applied, is working as well, yet not perfectly. The cursor's not moving smoothly, but in steps of a few pixels when I try to control it with my fingers -- they're neither too dry, nor too oily! ;)
At first, I thought this is a configuration issue. So I started playing around with xsetwacom.
xorg.0.log shows bottomX and bottomY as 740 and 500. Changing these values seems to have no effect while in "relative" mode. But it DOES in "absolute" mode. That is, setting these values to 370x250 (/2) makes the cursor move in larger steps, while doubling these values makes the touch pad only use about half the screen -- 1680x1050 here. 

"Absolute" mode aside -- who uses a touch pad in that mode? --, let me raise a few questions.
Could this be some kind of resolution problem? The cursor precision should increase when you move your fingers slower, right? On the other hand, it should decrease at a higher speed. Sounds like the "acceleration" value, which you can specify for every mouse? 
Obviously, the cursor moves further, when I move my finger faster. Yet, when I draw a line on the tablet from top-left -- cursor on screen, and finger on pad -- to bottom right really slow, the cursor follows just like in "absolute" mode. To me, it looks like the cursor can't move slow enough, or that the driver doesn't interpret these slow speeds properly.

Maybe this helps solving this issue.

- draziw -

---

### Post by vmatherly on 2010-10-02
Hello,

I have just setup a bamboo Touch CTT460 (no pen touch only). I used the instructions from this thread: 

[http://ubuntuforums.org/showpost.php?p=9496609&postcount=1]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1")

I am using Lucid Lynx. Everything is working as its suppose to accept if I move my finger across the pad to quickly the cursor just stops dead. I have to move my finger a bit slow to move the cursor. Anyone else having this issue?

---

### Post by Favux on 2010-10-02
Hi vmatherly,

Did you try the fix (described in blue text near top of HOW TO) in post #110 or Troubleshooting?

---

### Post by vmatherly on 2010-10-02
> **Favux said:**
> Hi vmatherly,

Did you try the fix (described in blue text near top of HOW TO) in post #110 or Troubleshooting?


I did, or at least I thought I did. I went bank and rebuilt the  xdriver with the fix and its working fine now. Thanks for pointing that out.

---

### Post by sylaulove on 2010-10-08
Hi everybody, I'm back

That's not an issue, my tablet is working just fine.

I'd like to run a script I made (to set my preferences with xsetwacom) each time I plug in my tablet.

For now, I have to run the script each time I plug the tablet because some settings I really dislike (like TPCButton on)

I'm sure it is possible (everything is possible on Ubuntu) to make this script run automatically on every plugging of my tablet.

It is not useful to run it on my login since I have a laptop, so I boot the computer, get my stuff out, plug the tablet later, sometimes I unplug/plug and it sets back the original settings.

Thanks

---

### Post by leandromartinez98 on 2011-05-24
The installation through the tutorials here used to work until some weeks ago. Now, I get my bamboo pen working, but I cannot set its mode to relative anymore, with the 

xsetwacom --set "Wacom Bamboo 4x5 Pen" mode relative

command anymore (it used to work until very recently).

The problem now is:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  17
  Current serial number in output stream:  17

Also, although the device is listed with

xinput --list:

xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                    	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; HID-compliant Mouse HID-compliant Mouse 	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Apple, Inc Apple Keyboard               	id=12	[slave  keyboard (3)]
    &#8627; Apple, Inc Apple Keyboard               	id=13	[slave  keyboard (3)]


The device is not listed with the "xsetwacom --list dev" command. I must note, furthermore, that the "xinput set-mode 8 relative" doesn't work either. 

Any idea on how to fix this recent new issue?

---

### Post by hectorbernal on 2011-10-09
Hey! I'm having lots of problem getting my Wacom Bamboo Pen and Touch working on Natty. I'm not that good using the terminal (I mean I can type what you write but I don't really understand what I'm doing:O )
Ok but I tried to follow this tutorial but when I get to this part: 
> **Ayuthia said:**
> Compile and install:
```
make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.30/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a
```


[post]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

When I call make clean, I get this error:
make: *** No rule to make target `clean'.  Stop.

Can you help me?

I start considering returning the tablet :(

Thanks

---

### Post by Favux on 2011-10-09
Hi hectorbernal,

You are on an old thread.  This thread is one of two where the Bamboo Pen and Touch drivers were originally developed and the information is outdated.

You want this HOW TO:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

Most models of the BambooPT work out of the box now in Natty.  Check the model numbers near the top of the HOW TO.  Also check out the model # on the back of the tablet and find out the tablet's product ID by using the following terminal command:
```
lsusb
```
Post the Wacom line in the output.

Please post any further questions on the HOW TO.

---

