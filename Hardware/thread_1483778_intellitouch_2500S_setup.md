---
title: "intellitouch 2500S setup"
date: 2010-05-15
forum: Hardware
---

### Post by dglnz on 2010-05-15
I've got a touchscreen MFG from effinet model 1503x this written on the back of the screen (this being using serial or the touch screen).

On the winXP HD the device is recorded as being an intellitouch 2500S.

Installed and got working (needed calibration on 6.10LTS) so thought it'd be as easy to get working on lucid-lynx, This has proven far from true.

I've installed the xserver-xorg-input-elographics driver 1:1-2-3 (most recent driver but haven't been able to get any reaction to the finger when pressed to the monitor.

lshal and lspci don't show *any* references to a touch screen
the elo driver doesn't get loaded.

from the command screen i've tried to test if the screen device is correct by using the following commands

             cat /dev/ttyS0 << intermittent reaction to finger presses
             od -h -w10 </dev/ttyS0 << again intermittent reaction

by intermittent i mean that the first time if get a something appear on screen, But the next time nothing.

I've followed a number of forum postings on this matter and followed this URL advise with little luck using 10.04LTS
[https://help.ubuntu.com/community/EloTouchScreen](https://help.ubuntu.com/community/EloTouchScreen)
can anyone suggest what else i do?

also tried to compile from source the elo drivers but not knowing C am stumped (going to a friends place who i hope will help me here) I thought maybe by doing this i could get around the issues of the deb package not being loaded.

I believe my problems maybe due to the touch screen not being known about by the system and or not knowing the right MFG code and monitor codes to be used as per the URL above.

By this i mean going a search of the logs and the dmsg I see no reference to the touch screen. The graphics driver used is vga16.

anyone able to help or point me somewhere I'd be grateful.

---

### Post by Favux on 2010-05-16
Hi dglnz,

So are you using the elo or evtouch driver?

Is there a .conf file at /usr/lib/X11/xorg.conf.d/ that's elo or whatever.

The xorg.conf should be at the usual place /etc/X11/.  If it's not there you should be able to create a blank xorg.conf file using root permission.

---

### Post by dglnz on 2010-05-17
No I was not using xorg.conf as I'm of the understanding that it is depreciated and had created a new file in /usr/shard/X11/xorg.conf.d directory a new file called 69-xx as per directions in the fore mentioned url setup guide.

dave.


> **Favux said:**
> Hi dglnz,

So are you using the elo or evtouch driver?

Is there a .conf file at /usr/lib/X11/xorg.conf.d/ that's elo or whatever.

The xorg.conf should be at the usual place /etc/X11/.  If it's not there you should be able to create a blank xorg.conf file using root permission.

---

### Post by Favux on 2010-05-17
Hi Dave,

You are correct and a .conf file is preferred but you can still use xorg.conf.  Can I see your 69-touchscreen.rules in /etc/udev/rules.d/?  Remember adding udev rules doesn't complete configuration. You need a xx-elo.conf or xorg.conf too.

---

### Post by dglnz on 2010-05-19
I have tried but failed to get files to attach to this message.

So here they are, each one has it's a from noting the path and filename. 

from /etc/init.d/rc.local<< My comment :)

/etc/opt/elo/loadelo
/etc/opt/elo/eloser ttyS0


from /usr/share/hal/fdi/policy

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SMGL -*-->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="ELO TouchSystems">
      <match key="info.capabilities" contains="input">
        <merge key="input.x11_driver" type="string">elo</merge>
        <merge key="input.x11_options.minx" type="string">130</merge>
        <merge key="input.x11_options.miny" type="string">197</merge>
        <merge key="input.x11_options.maxx" type="string">3945</merge>
        <merge key="input.x11_options.maxy" type="string">3894</merge>
        <merge key="input.x11_options.swapx" type="string">1</merge>
        <merge key="input.x11_options.swapy" type="string">1</merge>
      </match>
    </match>
  </device>
</deviceinfo>

from /etc/udev/rules.d

#ELO Touchscreen
KERNEL=="EVENT*", SUBSYSTEM=="input", ATTRS{idVendor}=="2582", ATTRS{idproduct}=="8086", SYMLINK+="input/elo_event"


result of running CAT /DEV/TTYS0 from commandline
I touched the screen in 3 places!

dave@ibm:~$ cat /dev/ttyS0
UT&#65533;&#65533;%/UT&#65533;&#65533;%7T&#65533;&#65533;%< UT&#65533;&#65533;$= UT&#65533;&#65533;"? UT&#65533;&#65533; ?UT&#65533;&#65533;?UT&#65533;&#65533;?T&#65533;&#65533;&#9618;UT&#65533;&#65533;&#9618;AUT&#65533;&#65533;&#9618;D&#9618;UT&#65533;&#65533;&#9618;DUT&#65533;&#65533;&#9618;BUT&#65533;&#65533;&#9618;0UT&#65533;&#65533;&#9618;&#65533;UT&#65533;^
                                                                                             7
                                                                                              &#65533;UT&#65533;_
                                                                                                   7&&#65533;UT&#65533;b
      74&#65533;UT&#65533;l
             7?&#65533;UT&#65533;s
                    9D&#65533;UT&#65533;u
                           :G&#65533;UT&#65533;w
                                  <M&#65533;UT&#65533;x
                                         =QUT&#65533;x
                                               ?U
UT&#65533;x
    AXUT&#65533;x
          CZUT&#65533;x
                EP
                  UT&#65533;x
                      FIUT&#65533;x
                            FEUT&#65533;x
                                  FC&#65533;UT&#65533;z
                                         D8&#65533;UT&#65533;{
                                                C/&#65533;UT&#65533;|
                                                       B&#65533;UT&#65533;l

&#65533;UT&#65533;l
&#65533;UT&#65533;m
!&#65533;UT&#65533;n
"&#65533;UT&#65533;p

0&#65533;UT&#65533;r
&#65533;;&#65533;UT&#65533;s
&#65533;<&#65533;UT&#65533;u
&#65533;?&#65533;UT&#65533;w
&#65533;B&#65533;UT&#65533;w
&#65533;C&#65533;UT&#65533;w
&#65533;A&#65533;UT&#65533;w
&#65533;?&#65533;UT&#65533;w
&#65533;=&#65533;UT&#65533;w
&#65533;;&#65533;UT&#65533;w
&#65533;9&#65533;UT&#65533;w
&#65533;-&#65533;UT&#65533;w
&#65533;d^C
dave@ibm:~$

TOUCHED THE SCREEN IN 4 PLACES.

dave@ibm:~$ od -h -w10 < /dev/ttyS0
0000000 2a00 5455 a292 8a0f 2100
0000012 4100 5455 a292 890f 4000
0000024 5f00 5455 a292 810f 5600
0000036 6d00 5455 a292 7c0f 5f00
0000050 7100 5455 a292 750f 6c00
0000062 7700 5455 a292 720f 7300
0000074 7b00 5455 a092 730f 7900
0000106 8000 5455 9f92 740f 7b00
0000120 8200 5455 9d92 760f 7a00
0000132 8100 5455 9b92 780f 6700
0000144 6e00 5455 9b94 790f 0000
0000156 0a00 5455 5191 9300 140f
0000170 eb00 5455 4f92 9300 2b0f
0000202 0100 5455 4992 9300 3a0f
0000214 0a00 5455 4692 9300 3f0f
0000226 0c00 5455 4392 9300 4a0f
0000240 1400 5455 4492 9200 510f
0000252 1b00 5455 4592 9100 540f
0000264 1e00 5455 4792 8f00 5b0f
0000276 2500 5455 4992 8d00 5c0f
0000310 2600 5455 4b92 8b00 5e0f
0000322 2800 5455 4d92 8900 5b0f
0000334 2500 5455 4e92 8800 520f
0000346 1c00 5455 4f94 8700 000f
0000360 cc00 5455 9791 840f 160f
0000372 3300 5455 9792 840f 380f
0000404 5600 5455 9792 840f 580f
0000416 7600 5455 9792 840f 6d0f
0000430 8b00 5455 9792 840f 740f
0000442 9200 5455 9792 840f 810f
0000454 9f00 5455 9792 840f 860f
0000466 a400 5455 9792 830f 860f
0000500 a300 5455 9692 810f 800f
0000512 9a00 5455 9592 800f 780f
0000524 9000 5455 9392 7f0f 550f
0000536 6a00 5455 9394 7f0f 000f
0000550 1700 5455 5191 6b00 1200
0000562 b200 5455 5192 6b00 2b00
0000574 cc00 5455 5192 6b00 3d00
0000606 de00 5455 5192 6b00 4b00
0000620 ec00 5455 5192 6b00 4f00
0000632 f000 5455 5192 6b00 5500
0000644 f600 5455 5192 6b00 5700
0000656 f800 5455 5192 6b00 5200
0000670 f300 5455 5192 6b00 4500
0000702 e600 5455 5194 6c00 0000
^Z
[3]+  Stopped                 od -h -w10 < /dev/ttyS0
dave@ibm:~$ 


from kernel log files

2010-05-19 19:55:06	ibm	kernel	[   18.152294] elok_s: module license 'Elo TouchSystems, All rights reserved. Copyright(c) 2008' taints kernel.

from System log

2010-05-19 19:55:06	ibm	kernel	[   18.152294] elok_s: module license 'Elo TouchSystems, All rights reserved. Copyright(c) 2008' taints kernel.

Now over the weekend (14th & 15th) I tried to install from source from the ELOtouch website their drivers and after seeking help got them built and installed on Monday 17th.

the output from the cmdline1 & 2 files I believe are because of this.
I have done this all this in the hopes that something here will help you.

note in the 69-touchscreen.rules I've changed the idVendor and idproduct values from the guide to what you see now from a command I gave which produced among other output the values 0x2582 for a vendor code and 0x8086 for the product code (well it was octal values).
my helper who knows C better than I entered the values you see in the file anyway.

look forward to your help.

P.s if it's easier to create a xorg.conf file then is it a matter of running these commands?
touch xorg.conf (inside the directory /etc/X11/)
then putting in the text below

Section "InputDevice"
        Identifier "ELO Touchscreen"
        Driver     "elographics"
        Option     "Device"     "/dev/ttyUSB0"
        Option     "AlwaysCore"
        Option     "screenNo"    "1"
        Option     "MinX" "4100"
        Option     "MaxX" "0"
        Option     "MinY" "0"
        Option     "MaxY" "4100"
        Option     "UntouchDelay" "5"
        Option     "ReportDelay" "1"
EndSection

note minx/y and maxx/y would need to be changed for my screen and also InputDevice    "ELO Touchscreen" put in the serverlayout section?

dave.


> **Favux said:**
> Hi Dave,

You are correct and a .conf file is preferred but you can still use xorg.conf.  Can I see your 69-touchscreen.rules in /etc/udev/rules.d/?  Remember adding udev rules doesn't complete configuration. You need a xx-elo.conf or xorg.conf too.

---

### Post by Favux on 2010-05-19
Hi Dave,

Not sure you need any help from me.  Between you and your helper it looks like you've got it covered.

Yes, for the xorg.conf the "ServerLayout" would look something like this:
```
Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"ELO Touchscreen"
EndSection
```
Assuming the file was empty to begin with, without video sections.  Or any video sections were setup automatically by Xorg.  It looks like your MaxX and MinX are reversed.  Some of the other options may no longer be needed, such as:
```
Option "AlwaysCore"
```
I'm curious about:
```
Option "Device" "/dev/ttyUSB0"
```
Is that due to a serial to usb adaptor?  Shouldn't it be '"/dev/input/elo_event"' since you set up a symlink in the udev rule?  I'd be happy to look at your proposed xorg.conf.

I also started on a .conf file, call it 90-elo.conf at /usr/lib/X11/xorg.conf.d/.  Obviously uneeded if you use the xorg.conf.  But anyway:
```
Section "InputClass"
	Identifier "Elo class"
	MatchProduct "2582|8086"
	MatchDevicePath "/dev/input/event*"
	Driver "elographics"
EndSection
```
Options need to be added.  Alternate lines could be:
```
	MatchProduct "ELO TouchSystems"
```
and/or
```
	MatchDevicePath "/dev/input/elo_event"
```

Rename the .fdi file to .bak or remove.  Although HAL might not be installed let's not confuse the issue.

And as always backup any config files you plan to change and be prepared to reinstall them from the command line if we break X.

---

### Post by dglnz on 2010-05-20
Favux~,

The problem is that the screen doesn't respond to touches ie mouse is in the middle of the screen - touch a corner or edge and the mouse doesn't move!
this is why I was thinking it might be the [idVendor] code or [idProduct] code.
in the /etc/udev/rules.d file.

> **Favux said:**
> Hi Dave,

Not sure you need any help from me.  Between you and your helper it looks like you've got it covered.

Think the "fix so far was with the compiling from source the touch screen driver files.

Yes, for the xorg.conf the "ServerLayout" would look something like this:
```
Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"ELO Touchscreen"
EndSection
```
Assuming the file was empty to begin with, without video sections.  Or any video sections were setup automatically by Xorg.  It looks like your MaxX and MinX are reversed.  Some of the other options may no longer be needed, such as:
```
Option "AlwaysCore"
```
I'm curious about:
```
Option "Device" "/dev/ttyUSB0"
```

No this was the original code I'd cut and pasted from another forum post I found when I trailed Kubuntu 6.10LTS the USB was altered to ttyS0 which as proven is my monitors device (the poster had a USB touchscreen 2500U) in that post.

The only thing was once the deb that came with the liveCD was to add in along with the code I added into Xorg.conf in /etc/X11 was that it wasn't calibrated :) at this point I wiped that install with Kubuntu 10.4LTS.

I mean apt-get install elo-touchgraphic then edit the /etc/X11/xorg.conf to have new code in it then perform a reboot of X and mouse pointer moved the finger touch it was simple as 123
> 
Is that due to a serial to usb adaptor?  Shouldn't it be '"/dev/input/elo_event"' since you set up a symlink in the udev rule?  I'd be happy to look at your proposed xorg.conf.

I also started on a .conf file, call it 90-elo.conf at /usr/lib/X11/xorg.conf.d/.

does this mean you move to another method as it didn't work for you?

> 
  Obviously uneeded if you use the xorg.conf.  But anyway:
```
Section "InputClass"
	Identifier "Elo class"
	MatchProduct "2582|8086"
	MatchDevicePath "/dev/input/event*"
	Driver "elographics"
EndSection
```
Options need to be added.  Alternate lines could be:
```
	MatchProduct "ELO TouchSystems"
```
and/or
```
	MatchDevicePath "/dev/input/elo_event"
```


Will try this on the PC.
Is the above code a good to go with xorg.conf be it in /etc/X11 or /usr/lib/X11/xorg.conf.d or would the text be different?

Also WHY is it so necessary to have all these config files?
Is it due to the transition from xorg.conf -> HAL -> the new setup of X11?

What do you consider to be the accepted approach?

why I'm asking this is because i might have a whole lot of installs to do in say 3 months time and so would like to be able to hit each install with a preferred way of doing it so that things won't break when upgrades come along (be it kernels or kubuntu versions).

> 
Rename the .fdi file to .bak or remove.  Although HAL might not be installed let's not confuse the issue.

And as always backup any config files you plan to change and be prepared to reinstall them from the command line if we break X.

Will report back once I see results.

It seems to me being someone very much not used to dabbling with the system like I have been that I sticking files in a lot of places.

I'd have thought I'd need to edit an existing file or create a new file in one place and then things happened like it did in Kubuntu 6.10LTS.

cheers,

dave.

---

### Post by Favux on 2010-05-20
> **dglnz said:**
> 
The problem is that the screen doesn't respond to touches ie mouse is in the middle of the screen - touch a corner or edge and the mouse doesn't move!
this is why I was thinking it might be the [idVendor] code or [idProduct] code.
in the /etc/udev/rules.d file.
OK, we can check both ID's if you haven't already identified them on your system.  If you're worried about the format here's a relevant part of a Wacom rule: 
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00c7"
```
> **dglnz said:**
> 
No this was the original code I'd cut and pasted from another forum post I found when I trailed Kubuntu 6.10LTS the USB was altered to ttyS0 which as proven is my monitors device (the poster had a USB touchscreen 2500U) in that post.

The only thing was once the deb that came with the liveCD was to add in along with the code I added into Xorg.conf in /etc/X11 was that it wasn't calibrated :) at this point I wiped that install with Kubuntu 10.4LTS.
That seems a pretty old version, why not Kubuntu 8.04LTS?  OK, so when you added the xorg.conf section to xorg.conf and changed usb to serial it worked, just not calibrated?  And you didn't upgrade you did a clean install?
> **dglnz said:**
> 
I mean apt-get install elo-touchgraphic then edit the /etc/X11/xorg.conf to have new code in it then perform a reboot of X and mouse pointer moved the finger touch it was simple as 123

does this mean you move to another method as it didn't work for you?
Sorry for the confusion.  The xorg.conf in /etc/X11 has always been available to configure devices.  Starting with Intrepid you were "suppose" to configure through the .fdi files instead of xorg.conf.  The main reason being the HAl/.fdi method gave you usb hot plugging.  But the HAL/.fdi method was a detour because they didn't have anything else available to give hot plugging.  Starting with Lucid it has been dropped in favor of the .conf files in /usr/lib/X11/xorg.conf.d/.  So the .conf files are the "new" .fdi files and the current "preferred" method for configuring devices.  But since you know how to do it in xorg.conf that's where you should do it.  I was just showing you the start of an elo.conf file in case you were interested and wanted to mess with it. 
> **dglnz said:**
> 
Will try this on the PC.
Is the above code a good to go with xorg.conf be it in /etc/X11 or /usr/lib/X11/xorg.conf.d or would the text be different?
It should be.  The xorg.conf section you showed me plus the "ServerLayout" section I posted.  I can look at your proposed xorg.conf before you try it.
> **dglnz said:**
> 
Also WHY is it so necessary to have all these config files?
Is it due to the transition from xorg.conf -> HAL -> the new setup of X11?

What do you consider to be the accepted approach?
It isn't.  Either use the xorg.conf or a .conf file.  As I explained above the accepted approach are the new .conf file, but the xorg.conf is fine.
> **dglnz said:**
> 
why I'm asking this is because i might have a whole lot of installs to do in say 3 months time and so would like to be able to hit each install with a preferred way of doing it so that things won't break when upgrades come along (be it kernels or kubuntu versions).
I think you are also permitted to add custom .conf files to /etc/X11/xorg.conf.d.  If so and you develop an elo.conf file that may then be where you want it so upgrades don't over write.

Hope this clears things up.

---

### Post by dglnz on 2010-05-21
Hi Favux,

taken in what you've said (well think I have).

I created an elo.conf file in /usr/lib/X11/xorg.conf.d
```

Section "InputClass"
	Identifier "Elo class"
	MatchProduct "2582|8086"
	MatchDevicePath "/dev/input/event*"
	Driver "elographics"
EndSection

```

also replace the above lines with these below 

```

    MatchDevicePath "/dev/input/elo_event"
    MatchProduct "ELO TouchSystems"

```

to no avail.

things I've tried tonight (as an aside I got touchcal working from source and my settings are shown further below).

    1. created a file 90-elo.conf, rebooted (no reaction from touch)
    2. renamed my fdi file in /usr/hal/fdi/policy/20thirdparty (no joy)
    3. changed lines from 1st code segment above to second segment (no joy)
 
looked at 05-evdev.conf and saw it referring to evdev as a driver for the touchscreen section so thought Okay I'll change that to elographics_drv and see if it works - Nope it didn't <sigh>.

having re read you're comments while writing all this, I will tomorrow add in a serverlayout section like you have mentioned (I had at work printed of ONLY the instructs above in the code blocks and trailed them).

```

Got touchcal working and dropped to console and ran it. the resulting co-ordinates are below
      co0 x 4025    y 153
      co1 x 4014    y 3957
      co2 x 35      y 138
after press enter for the last time the output was this

     option min x 4071
     option min y 4083
     option max x -11
     option max y 27

```

Would I insert the calculated minimum & maximum values above into the elo.conf file somehow or doesn't it matter, well should I say would there be another file somewhere for the calibration info to be put?

*** some things deleted ***
       
> 
That seems a pretty old version, why not Kubuntu 8.04LTS?  OK, so when you added the xorg.conf section to xorg.conf and changed usb to serial it worked, just not calibrated?  And you didn't upgrade you did a clean install?


I had chucked out a number of copies and hadn't found the 6.10LTS at that time and when I decided to trail the touch screen found that copy and comments where that "it just works" I tried it as a test :P then decided to install lucid- lynx deleting *_everything that was on the Hard drive_*


> 
Sorry for the confusion.  The xorg.conf in /etc/X11 has always been available to configure devices.

this is where from reading postings for touchscreens it is *very* murky well from my reading it was this - "/etc/X11/xorg.conf is no longer used and you have to use fdi (mind you I think it's because lucid is **such a new beast with a new approach to managing X**)

So I might do a cut down version of my trails once I've got it going.
to try and help those in the future.

> 
  Starting with Intrepid you were "suppose" to configure through the .fdi files instead of xorg.conf.  The main reason being the HAl/.fdi method gave you usb hot plugging.  But the HAL/.fdi method was a detour because they didn't have anything else available to give hot plugging.  Starting with Lucid it has been dropped in favor of the .conf files in /usr/lib/X11/xorg.conf.d/.  So the .conf files are the "new" .fdi files and the current "preferred" method for configuring devices.  But since you know how to do it in xorg.conf that's where you should do it.  I was just showing you the start of an elo.conf file in case you were interested and wanted to mess with it. 


Now this makes sense pity there wasn't a readme file in which it states what you've said above - for the noobs like myself :)

> 
It should be.  The xorg.conf section you showed me plus the "ServerLayout" section I posted.  I can look at your proposed xorg.conf before you try it.


this part I've only just re read after my trails failed tonight :(

> 
It isn't.  Either use the xorg.conf or a .conf file.  As I explained above the accepted approach are the new .conf file, but the xorg.conf is fine.

I think you are also permitted to add custom .conf files to /etc/X11/xorg.conf.d.  If so and you develop an elo.conf file that may then be where you want it so upgrades don't over write.

Hope this clears things up.
It does indeed.

with luck I'll have something positive to post tomorrow after I add in the serverlayout section into my elo.conf file.

I am wondering if the compiled ELO driver i did has made any differences to the report I posted to you earlier, because to be honest before I got the driver compiled i got intermittent reaction from the typing in at kconsole of the commands would you be able to comment?
```

   cat /dev/ttyS0 
   od -h -w10 < /dev/ttyS0 

```

Intermittent I mean by 2 out of 10 times I'd get a reaction like those posted for both commands.

dave.

---

### Post by Favux on 2010-05-21
Hi Dave,

> add in the serverlayout section into my elo.conf file.

"ServerLayout" is only for xorg.conf not elo.conf in xorg.conf.d.  Let me give you some links on the new .conf files:
[https://fedoraproject.org/wiki/Input_device_configuration](https://fedoraproject.org/wiki/Input_device_configuration)
[http://who-t.blogspot.com/2010_01_01_archive.html](http://who-t.blogspot.com/2010_01_01_archive.html)

Yes, I think you should be able to add the coordinates you found to the elo.conf.

One of your earlier suspicions may be correct and the problem is not using the correct identifier for elo in the the Match lines.  We can try wading through udevadm info and see if we can find or verify the identifiers:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```

---

### Post by dglnz on 2010-05-22
Hi Favux,

Just want to say many thanks for you're helping me.

After reading the links you've posted I'd like you to confirm if I've read it right.

1. The xorg.conf file in /etc/X11 is read before anything else for x server and supersedes other instructions that maybe encountered in other conf files in /usr/lib/X11/Xorg.conf.d OR /etc/X11/xorg.conf.d.

2. Files in /usr/lib/X11/xorg.conf.d are for "system" files not anything the user may want to add on.

based on this then it sounds more acceptable that the user add-ins get put into the conventional x-org.conf file located in /etc/X11.

I added in the ServerLayout in the elo.conf file and killed X :(.

So now the file elo.conf contains this...

```

Section "InputClass"
    Identifier "Elo class"
    MatchProduct "2582|8086" OR with "ELO TouchSystems"
    MatchDevicePath "/dev/input/event*" OR with "/dev/input/elo_event"
EndSection

Section ServerLayout
   Identifier "X-org Configured"
   InputDevice "Elo Touchscreen"
EndSection

```

Now regardless of what is in the MatchProduct line or MatchDevicePath line
I get and error referring to the InputDevice "Elo Touchscreen" causing the and error and killing the X server from starting.

Tried using ELO Touchscreen, ELO TouchSystems, elographics and elographics_drv in for the InputDevice line with no luck.

Note I have changed this line in 05-evdev.conf file in /usr/lib/xorg.conf.d
```

   Section "InputClass"
	Identifier "evdev touchscreen catchall"
	MatchIsTouchscreen "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"  *changed this to be "elogrpahics_drv"*
EndSection

What I will try after this is to ....

1. revert the above line back to evdev
2. create an /etc/X11/corg.conf file with the InputClass & ServerLayout sections you've already posted into it remove the elo.conf file out of usr/lib/X11/xorg.conf.d directory .
3. run udevadm info --export-db > $HOME/udevadm-info.txt and if I can see something obvious will put it in the newly created xorg.conf file and also post the output to you.

As an aside I read in the links to just posted that HAL and udev are mutually exclusive (how can you prove which is being used?) 

also note I've renamed the fdi rule )shown below to fdi.old this just in case I shouldn't have and it is needed.

[CODE]
from /usr/share/hal/fdi/policy

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SMGL -*-->
<deviceinfo version="0.2">
<device>
<match key="info.product" contains="ELO TouchSystems">
<match key="info.capabilities" contains="input">
<merge key="input.x11_driver" type="string">elo</merge>
<merge key="input.x11_options.minx" type="string">130</merge>
<merge key="input.x11_options.miny" type="string">197</merge>
<merge key="input.x11_options.maxx" type="string">3945</merge>
<merge key="input.x11_options.maxy" type="string">3894</merge>
<merge key="input.x11_options.swapx" type="string">1</merge>
<merge key="input.x11_options.swapy" type="string">1</merge>
</match>
</match>
</device>
</deviceinfo>

```


> **Favux said:**
> Hi Dave,


"ServerLayout" is only for xorg.conf not elo.conf in xorg.conf.d.  Let me give you some links on the new .conf files:
[https://fedoraproject.org/wiki/Input_device_configuration](https://fedoraproject.org/wiki/Input_device_configuration)
[http://who-t.blogspot.com/2010_01_01_archive.html](http://who-t.blogspot.com/2010_01_01_archive.html)

Yes, I think you should be able to add the coordinates you found to the elo.conf.

One of your earlier suspicions may be correct and the problem is not using the correct identifier for elo in the the Match lines.  We can try wading through udevadm info and see if we can find or verify the identifiers:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```

---

### Post by Favux on 2010-05-22
> 1. The xorg.conf file in /etc/X11 is read before anything else for x server and supersedes other instructions that maybe encountered in other conf files in /usr/lib/X11/Xorg.conf.d OR /etc/X11/xorg.conf.d.

2. Files in /usr/lib/X11/xorg.conf.d are for "system" files not anything the user may want to add on.

based on this then it sounds more acceptable that the user add-ins get put into the conventional x-org.conf file located in /etc/X11.

Actually I'm not 100% sure.  I think the way it goes is that the Xserver starts to read xorg.conf and then is diverted to xorg.conf.d and the .conf files.  It treats the snippets in the .conf files as xorg.conf sections.  Then it goes back and finishes by reading xorg.conf.  And what is read last is suppose to control.  So you can look at it as xorg.conf.d .conf files are read followed by xorg.conf which means the xorg.conf entries controls.  You can check and see if what you're reading gibes.

The reason X broke is the "ServerLayout" goes in xorg.conf, not the elo.conf in xorg.conf.d.

I agree, set evdev back to default.  Evdev only picks up your touch screen when the elo driver rejects it.  If elo was setting up evdev wouldn't enter the picture.  Besides I think what you wanted was the evtouch driver, not evdev.

I think what we need is the udevadm info so we can be sure of the match lines.  I'd do that before trying anything else.

HAL isn't installed by default on Lucid, so unless you deliberately installed it udev should be what's configuring things.

---

### Post by dglnz on 2010-05-22
> **Favux said:**
> Actually I'm not 100% sure.  I think the way it goes is that the Xserver starts to read xorg.conf and then is diverted to xorg.conf.d and the .conf files.  It treats the snippets in the .conf files as xorg.conf sections.  Then it goes back and finishes by reading xorg.conf.  And what is read last is suppose to control.  So you can look at it as xorg.conf.d .conf files are read followed by xorg.conf which means the xorg.conf entries controls.  You can check and see if what you're reading gibes.


Well I think I've Proven lastnight that /etc/X11/xorg.conf is parsed 1st as I'm getting the same error still refering it's referring to  InputDevice "Elo Touchscreen" line in the xorg.conf file very early on in the xorg.o.log file.

I had removed the elo.conf file from /usr/lib/X11/xorg.conf.d directory (but did copy it to home 1st :)).

managed to get kdm up again but it won't accept any key events! (even with my new xorg.conf file not there. :mad:

until i beat this issue I'm sunk (note I encrypted the home directory and have already tried to access it via the LiveCD I have.

also ran your command but found nothing that said anything about touch, screen, elo by using grep over the txt file generated in home directory.

Do you think a fresh install is in order (one that doesn't have the compiled elo driver installed?

dave.


 
The reason X broke is the "ServerLayout" goes in xorg.conf, not the elo.conf in xorg.conf.d.

I agree, set evdev back to default.  Evdev only picks up your touch screen when the elo driver rejects it.  If elo was setting up evdev wouldn't enter the picture.  Besides I think what you wanted was the evtouch driver, not evdev.

I think what we need is the udevadm info so we can be sure of the match lines.  I'd do that before trying anything else.

HAL isn't installed by default on Lucid, so unless you deliberately installed it udev should be what's configuring things.[/QUOTE]

---

### Post by Favux on 2010-05-22
It's not clear to me what broke your system.  A driver shouldn't do that.

What I need to look at is your udevadm info and Xorg.0.log.  Right click on them and compress using Create Archive and then post using Manage Attachments below.

Obviously if you need to do a clean install to get your system working again we could look at what you did to install the elo driver.

---

### Post by dglnz on 2010-05-23
I had to re install lucid-lynx :(

I've installed the elographics driver from the repositories and have attached the following files archived as attachments.

Inside is a xorg.0.log which shows things without the file xorg.conf I created and put in /etc/X11

the other is one with the xorg.conf in the /etc/X11 directory.

xorg.conf1 shows what I had at the time the error was created in the log file.

xorg.conf shows the settings i used when 6.10LTS worked (me thinking that this my hold a key to how to set things up in 10.04LTS).

The only things I've not done is to recreate the fdi file or compile from source the elographics driver.

also got but not copied the udevadm - sorry.
was called to family duties and never got back to it, the PC & screen is out in the garage, Time is late so WILL get you the files (1 before elographics driver loaded and 1 after in case it shows something up that is of importance for you).



> **Favux said:**
> It's not clear to me what broke your system.  A driver shouldn't do that.

What I need to look at is your udevadm info and Xorg.0.log.  Right click on them and compress using Create Archive and then post using Manage Attachments below.

Obviously if you need to do a clean install to get your system working again we could look at what you did to install the elo driver.

Note ran both commands cat /dev/ttyS0 & od -h -w10 </dev/ttyS0 before and after the elo driver from repositories and the response was VERY limited or nothing! (as opposed to the postings earlier). again don't know if this is of interest to you.

dave.

---

### Post by Favux on 2010-05-23
Family duties will do that.  :)

Alright, this is proving unnecessarily difficult.

The xorg.conf1 is not a correct xorg.conf.  You have mixed a xorg.conf.d elo.conf into an xorg.conf which is why X was broken.

You've done a fresh install and installed the elotouch driver.  Fine stop there, unless there were errors.  If so tell me about them.

Show me your current xorg.conf from your fresh install.  Don't do anything else.

Exception would be the udevadm info if and when you get it.

---

### Post by dglnz on 2010-05-23
Hi Favux,

Attached are 2 info files.

udevadm-info.txt is one i did before installing the elographics driver and udevadm-info1.txt is after installation of the deb file.

I thought i'd do this so that it may highlight better any differences to you between have the elo driver installed and not installed.

Tonight i will seperate out the two Sections.

InputLayout into a file called elo.conf under /usr/lib/xorg.conf.d

ServerLayout in the current xorg.conf in the current place 
/etc/X11

rgds,

Dave.

> **Favux said:**
> Hi Dave,


"ServerLayout" is only for xorg.conf not elo.conf in xorg.conf.d.  Let me give you some links on the new .conf files:
[https://fedoraproject.org/wiki/Input_device_configuration](https://fedoraproject.org/wiki/Input_device_configuration)
[http://who-t.blogspot.com/2010_01_01_archive.html](http://who-t.blogspot.com/2010_01_01_archive.html)

Yes, I think you should be able to add the coordinates you found to the elo.conf.

One of your earlier suspicions may be correct and the problem is not using the correct identifier for elo in the the Match lines.  We can try wading through udevadm info and see if we can find or verify the identifiers:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```

---

### Post by Favux on 2010-05-23
Alright, let me look at them.  I don't want you to do elo.conf at all.  Let's just concentrate on getting it working with xorg.conf in /etc/X11 first.  And if that file is present on your system after a fresh install please post it.

---

### Post by Favux on 2010-05-23
Is this thing a serial or usb device?  Serial correct?

Do you have the thing plugged in???  There's not a sign of it.  Can you link me to a site that has a picture of it and some sort of technical spec.s?

---

### Post by dglnz on 2010-05-24
Pictures Attached.

> **Favux said:**
> Hi Dave,


"ServerLayout" is only for xorg.conf not elo.conf in xorg.conf.d.  Let me give you some links on the new .conf files:
[https://fedoraproject.org/wiki/Input_device_configuration](https://fedoraproject.org/wiki/Input_device_configuration)
[http://who-t.blogspot.com/2010_01_01_archive.html](http://who-t.blogspot.com/2010_01_01_archive.html)

Yes, I think you should be able to add the coordinates you found to the elo.conf.

One of your earlier suspicions may be correct and the problem is not using the correct identifier for elo in the the Match lines.  We can try wading through udevadm info and see if we can find or verify the identifiers:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```

---

### Post by Favux on 2010-05-25
Hi dglnz,

A touch screen juke box would be cool!

OK, back to my questions.  If you have an xorg.conf in /etc/X11/ please post it.

Now the xorg.conf where you say it worked in 6.10 or whatever shows it is a serial touchscreen.  In other words the internal connection between the touch screen and computer is serial not usb.  Is this correct?  Can you actually see the serial cable, ie it really isn't internal?

Also when using the Elo driver for the touchscreen.  Was that a happy coincidence or do you know that Elo is the manufacturer of the Touchscreen?

I'm trying to get a handle on why it isn't showing up in udevadm info or 'xinput --list'.

---

### Post by dglnz on 2010-05-25
Right I shall try to go though the steps (even before starting this thread).

Did a troll of google looking for help of touchscreens on K/Ubuntu.

found a few posting that talked about ...
[LIST=1]
[*]elogrpahics
[*]evtouch
[*]mtouch
[/LIST]

I then tried to find out some info about MY screen by searching Effinet and 1503x - very little joy.

Spoke with the local techie who supports these things.
He said they use ELO drivers in winXP.

I found the site and they had source code to build the driver with so i downloaded this.

Further searches showed that there where issues with 7.04 up so to try and get a handle on what is going on I installed 6.10LTS 
then installed the elographics driver from the liveCD repository.

copied the info below from this url [https://help.ubuntu.com/community/EloTouchScreen](https://help.ubuntu.com/community/EloTouchScreen)

> 
Configuration
Edit /etc/X11/xorg.conf and add a new InputDevice section similar to this one. This example comes from a screen test on a laptop that is configured so the external graphics device is on X screen 1 (note the screenNo option) rather than the default screen 0. 
*** Added the section below into the original xorg.conf in /etc/X11 ***
Section "InputDevice" 
        Identifier "ELO Touchscreen"
        Driver     "elographics"
        Option     "Device"     "/dev/ttyS0" << original was for USB!
        Option     "AlwaysCore"
        Option     "screenNo"    "1"
        Option     "MinX" "4100"
        Option     "MaxX" "0"
        Option     "MinY" "0"
        Option     "MaxY" "4100"
        Option     "UntouchDelay" "5"
        Option     "ReportDelay" "1"
EndSection
Note: edit the Device value (/dev/ttyUSB0) ***note i changed it to ttyS0 as mine is a serial not usb connected screen*** to match the input device name the touch-screen input has. In this case, the device is a serial touch-screen connected via a serial-to-USB converter. 
You may have to invert the minimum and maximum X- and Y-scale values if the input values from the touch-screen are inverted. Use `man elographics" to see all the options and defaults. 
Add the input device to the ServerLayout section so it looks similar to this: 
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 768
    Screen      1  "Screen1" Above "Screen0" << removed this as I've not got a second screen
    InputDevice    "Synaptics Touchpad"
    InputDevice    "ELO Touchscreen"   <<<< added this line into the default xorg.conf in /etc/X11
EndSection
Save the file and log-out to restart the X server.
Rebooted X and lo and behold touch worked!
it needed calibration but it worked.

After experiencing HOW easy it was with 6.10LTS I thought it'd be even easier (well the history of this thread proves otherwise :???:

So the above excerpt from the above URL is what got me going on 6.10LTS.


> **Favux said:**
> Hi dglnz,

A touch screen juke box would be cool!

OK, back to my questions.  If you have an xorg.conf in /etc/X11/ please post it.

I've not changed xorg.conf as yet So the current xorg.conf as it's been posted about 8 posting on the 1st page.
The **only difference is that I haven't created from source the graphics driver**.

It was only after I had done this that i could see any reference to the touchscreen in any log files or dmesg search etc.


> 
Now the xorg.conf where you say it worked in 6.10 or whatever shows it is a serial touchscreen.  In other words the internal connection between the touch screen and computer is serial not usb.  Is this correct?  Can you actually see the serial cable, ie it really isn't internal?


The Touchscreen side IS serial if you look at one of the pics I posted you'll see the wires....
[LIST]
[*]Blue is the video
[*]Black is the serial (for touch screen)
[*]a grey round cable for sound
[*]on the back of the PC left side there are 2 serial cables 
   [*] 1 for the thermal printer (may not be visible in the pics)
   [*] 1 for the touch screen (this underneath the printer D9 plug)
[*]power cable from it's own power supply
[/LIST]


> 
Also when using the Elo driver for the touchscreen.  Was that a happy coincidence or do you know that Elo is the manufacturer of the Touchscreen?

Well it may have been a happy coincidence on 6.10LTS But if it had not worked then i'd have moved onto one of the other 2 drivers.

> 
I'm trying to get a handle on why it isn't showing up in udevadm info or 'xinput --list'.

I suspect it's got something to do with when i compiled successfully from source the elographic driver as It was *hit and miss* for me to get output from the cat /dev/ttyS0 and od -h -w10 < /dev/ttyS0 commands from terminal after it was installed I posted the output in a previous post and the output you see was from three and four screen touches respectively at different places on the screen.

before I post again i will split the input section from the server layout section as *you have said the input section should be in a file called elo.conf and put in /usr/lib/X11/Xorg.conf.d*

I suspect from what's happened before i did the reinstall is that if i compile and loaded from source the elo driver and split out the server layout section to xorg.conf in /etc/X11 and have the original elo.conf file put into /usr/lib/X11/xorg.conf.d then **it just might work**

But i shall do this in 2 stages.
[LIST=1]
[*]Split out the two sections as posted just before i did the re install
[*]compile and install the elo driver from source
[/LIST]

your thoughts on my proposed action.

---

### Post by Favux on 2010-05-25
Ok, so we could actually try evtouch if needed.

Let's just work on xorg.conf for now.

Please post your current xorg.conf.  Please don't make me ask again.

We need to figure why ttS0 signal is intermittent.  I'm assuming that's why udevadm info is not showing anything.  Trying to help others with serial devices it looks like there is something wrong with how Lucid handles serial devices.  Maybe a lack of udev rules upstream for serial devices.

---

### Post by dglnz on 2010-05-26
here be the xorg.conf file.
> 

Section "InputClass"
    Identifier "ELO class"
    MatchProduct "2582|8086"
    MatchDevicePath "/dev/input/event*"
    Driver "elographics"
EndSection

Section "ServerLayout"
    Identifier "Xorg configured"
    InputDevice "ELO Touchscreen"

EndSection


Please note before I stuffed up the previous install the above conf file was in use, and is again.

I remembered you saying to split the split the ServerLayout and Input into seperate files so did that tonight.

Now KDM wont start on boot and when I type in from the console startx I get the same error as above.
*note the difference this time is that the I can access the Hard Drive from a LiveCD and so can edit the conf files etc easier (I'm not too hot on commandline calls much more comfortable in X*

regards,

Dave.

Attached a readme file from the ELO source files on howto go about compiling the driver etc from source (in case it helps you to see where or what happened before I kill X to make the touchscreen come to like be it from the commandline *cat /dev/ttyS0 and od -h -w10 < /dev/ttyS0*

Also do you think it's worth trailing mtouch or evtouch as there seems to be no head way on this matter using ELO graphics driver?

QUOTE=Favux;9357625]Ok, so we could actually try evtouch if needed.

Let's just work on xorg.conf for now.

Please post your current xorg.conf.  Please don't make me ask again.

We need to figure why ttS0 signal is intermittent.  I'm assuming that's why udevadm info is not showing anything.  Trying to help others with serial devices it looks like there is something wrong with how Lucid handles serial devices.  Maybe a lack of udev rules upstream for serial devices.[/QUOTE]

---

### Post by Favux on 2010-05-26
Hi dglnz,

I see the misunderstanding.  I thought you were showing me your 90-elo.conf not your xorg.conf.
```
Section "InputClass"
Identifier "ELO class"
MatchProduct "2582|8086"
MatchDevicePath "/dev/input/event*"
Driver "elographics"
EndSection
```
Is elo.conf syntax, not xorg.conf syntax.  When I say .conf file I am talking about the .conf files in xorg.conf.d not the xorg.conf file in /etc/X11/.  Your xorg.conf should look something like:
```
Section "InputDevice"
   Identifier "ELO Touchscreen"
   Driver "elographics"
   Option "Device" "/dev/ttyS0"
   Option "AlwaysCore"
   Option "screenNo" "1"
   Option "MinX" "4100"
   Option "MinY" "0"
   Option "MaxX" "0"
   Option "MaxY" "4100"
   Option "UntouchDelay" "5"
   Option "ReportDelay" "1"
EndSection

Section "ServerLayout"
   Identifier "Xorg configured"
   InputDevice "ELO Touchscreen"
EndSection
```
Some of those options like "AlwaysCore" may not be needed.  You'll also need to adjust the coordinates.  I know they are from the EloTouchScreen wiki but like I mentioned before they looked wrong to me.  So I have them more how I think they should be with min x and y at 0, ie upper left hand corner of the screen.

Lets see if this now picks up the elographics driver.  We still have to worry about the intermittant ttyS0.

---

### Post by toqer on 2010-05-27
Favux:

Nearly the same touchscreen here, and most of the same troubleshooting steps.  I'm making a "fingerpaint" system for my 4 year old with an old epia-m mobo.

I just did the xorg.conf as you suggested.  It's working but it seems like all axis's are inverted and it need calibration.  I'll bang on it some more, and let you know if I fix it.

---

### Post by Favux on 2010-05-27
Hi toqer,

Glad you joined us!  Happy the xorg.conf is "working".
> It's working but it seems like all axis's are inverted and it need calibration.
Notice on the [EloTouchScreen wiki]("https://help.ubuntu.com/community/EloTouchScreen") that the coordinates for X are reversed from what I posted:
```
        Option     "MinX" "4100"
        Option     "MaxX" "0"
        Option     "MinY" "0"
        Option     "MaxY" "4100"

```
Maybe I shouldn't have reversed them?  I was just trying to follow the coordinate convention every other screen uses.  Maybe Elo doesn't!

---

### Post by toqer on 2010-05-27
Yup, that was it.  Just reversed those values and it worked like magic.  My 4yr old is going to be stoked on her new fingerpaint pc.

---

### Post by Favux on 2010-05-27
Outstanding!  :)

So Elo insists on being unique in its coordinate scheme.  Good to know.

---

### Post by dglnz on 2010-05-29
Guess what?

**[SIZE="5"][COLOR="Green"]IT WORKS :P[/COLOR][/SIZE]**

What I did was to delete the elo.conf I had in /usr/X11/xorg.conf.d and delete the xorg,conf file in /etc/X11

Put in the code you supplied before toqer post posted his comments.

The default code made touch work and as posted my X & Y was back to front.

I have compiled a program call touchcal that after touching the 3 points gave me these co-ordinates.
option minx = "4026"
option maxx = "0"
option miny = "4026"
option maxy = "-16"

NOW Calibrated!!!

I will post a howto on the sticky Desktop compatibility list as a way of perhaps making things easier for those who follow with a link to this post.

Note the things I did from ELO source file had NO effect on getting the touchscreen to work.

Many thanks for your help, thoughtfulness and time Favux as I know I would get here without you're help.

ALso I hope that this may help someone else.

regards,

 Dave.

---

