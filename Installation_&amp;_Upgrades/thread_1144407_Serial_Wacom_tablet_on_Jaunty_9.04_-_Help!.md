---
title: "Serial Wacom tablet on Jaunty 9.04 - Help!"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by wtc on 2009-04-30
Hi all,

I made fresh Jaunty 9.04 install; was trying to configure Serial tablet Wacom Intous2 (Pen and Mouse). Tablet was not recognized out-of-the-box (no surprise, same in previous Ubuntu releases), so I edited xorg.conf properties for the tablet. In all Ubuntu releases I have had starting from 7.04 to 8.10 the Wacom Mouse and Pen worked smooth afterwards.

Now in Jaunty, when moving the Wacom Mouse on the Tablet surface, mouse arrow on the display reacts with ~0.5-1sec delay, which makes me really crazy:(. However when I put the Intous Pen and not the Mouse to the Tablet surface, it works fast!!

Here are some outputs:

wtc@wtc-desktop:~$ dmesg | grep ttyS
[    1.532782] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.533125] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

wacdump /dev/ttyS0 shows the correct device (Serial Intous2 etc); values change when changing coordinates and pressing mouse buttons.

XOrg.0.log shows lots of messages 
xf86WcmSerialValidate: bad magic at 1 v=f0 l=9
xf86WcmSerialValidate: bad magic at 1 v=f0 l=9
xf86WcmSerialValidate: bad magic at 1 v=f0 l=9
...

Help would be very appreciated, thanks!!

---

### Post by Favux on 2009-04-30
Hi wtc,

In Jaunty you are suppose to use the HAL/.fdi method not xorg.conf.  Actually a lot of people report that using wacom entries in xorg.conf with the specially patched linuxwacom 0.8.2-2 drivers in Jaunty breaks X.

There are some attempts at custom .fdi's on this thread, the latest ending in post #169 by mzuther:  [http://ubuntuforums.org/showthread.php?t=967147&page=17](http://ubuntuforums.org/showthread.php?t=967147&page=17)  He also gives the link to the Wacom.fdi wiki.  Remember his is a usb tablet and you would have to modify the serial subsection of the 10-wacom.fdi.

---

### Post by tajmox on 2009-05-01
Hi, What did you do to get the serial tablet working?  Can you pastebin your xorg.conf for me please?  I can't get it working with xorg.conf or the fdi files.  I'm using an Intuos2 serial tablet.

---

### Post by wtc on 2009-05-01
Hi tajmox,

Identical to that from Intrepid, I pasted it below. I'm happy if this helps for you...
1. I fresh-installed 9.04 from liveCD;
2. Copied xorg.conf from backup to /etc/X11/
3. sudo apt-get install wacom-tools (not really needed to start the tablet)
4. Reboot - that's it. But I have now delay problem with Wacom Mouse, described above.
Maybe to mention, I have the tablet always power on. On WinXP works smooth...

xorg.conf:

```

# text text text....
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Device" "/dev/ttyS0"
	Option "Type" "stylus"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "eraser"
	Option "Device" "/dev/ttyS0"
	Option "Type" "eraser"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "cursor"
	Option "Device" "/dev/ttyS0"
	Option "Type" "cursor"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "stylus"  "SendCoreEvents"
	InputDevice "eraser"  "SendCoreEvents"
	InputDevice "cursor"  "SendCoreEvents"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by wtc on 2009-05-01
Hi again,

I don't know how to explain it but tablet works like a charm now!

I was playing around the .fdi file from the forum link that Fidux advised (thanks to you for comment!). I commented out the xorg.conf part of wacom, rebooted - nothing, Tablet dead. 

And there - mirracle: 
since Ubuntu already booted in graphical mode and Tablet didn't react, I went via Ctrl+Alt+F2 to terminal mode and killed /usr/sbin/gdm. Then, uncommented wacom part in xorg.conf, started gdm again - and tablet worked without any delays in movement! No errors any more in XOrg.0.log file. I rebooted my PC couple of times, Tablet REALLY works now.

wacom.fdi file is still in /etc/hal/fdi/policy folder, but i think Ubuntu doesn't use it. (Maybe somebody has idea how to check this? Would be usefull for other users).

Cheers!

---

### Post by Favux on 2009-05-01
Hi wtc,

Good for you!  That's very interesting.

As far as I know Jaunty uses the same location for the 10-wacom.fdi as Intrepid.  It should be in /usr/share/hal/fdi/policy/20thirdparty/.  On the Wacom.fdi wiki:  [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)  they do say to put your custom .fdi in /etc/hal/fdi/policy/custom_wacom.fdi.  Notice that the examples are from the usb section of the 10-wacom.fdi in Jaunty, not the serial section.

It looks like something is flaky about the way Jaunty handles serial tablets, or maybe your Jaunty install is flaky. :)

The xorg.conf takes precedent over the .fdi file.  If xorg.conf is working the .fdi will be ignored.  In Intrepid when Wacom occasionally glitched (say a resume from suspend) then the .fdi would take over and I'd be reduced to just my stylus.  And no entries would show up in wacomcpl.  But since I have usb the old hotplug commands ctrl-alt-F1 and then ctrl-alt-F7 would restore things.

---

### Post by bradtem on 2009-05-20
I'm not having much luck.  My tablet was working before upgrade.  Now the system does not appear to see it.  xinput --list does not show it, xsetwacom does not show it, lshal shows ttys0 but not any tablet.  I must have something more basic wrong here.  I am running jaunty amd64, and have the wacom penpartner, which is an older serial tablet plugged into ttyS0.  All tablet lines are commented out in xorg.conf, and nothing shows up in Xorg.0.log about tablets.    Tablet has power (via the keyboard) and did not work before or after installing an fdi file as suggested.   Restarted hald to make sure it loaded.

Any other thoughts?

---

### Post by Favux on 2009-05-20
Hi bradtem,

I wonder, given how old the tablet is, whether it's identifier is in the serial tablet subsection of the .fdi file?  They are:
```
"WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5"
```
Do you know what it is?  Any chance you ran:
```
more /proc/bus/input/devices
```
before installing Jaunty?  Or "lshal"?

---

### Post by bradtem on 2009-05-20
Alas, no, I don't have pre-jaunty records of that.  Because it is powered by the keyboard it is non-trivial to remove to plug into an old system, but I will try to do that.

But to show my ignorance, what do you mean by "the serial tablet subsection of the .fdi file"?   None of the sample FDI files I saw had a serial tablet subsection.  The docs say you don't need to make the fdi at all except to set options, but you may be suggesting to me that if I can find some serial tablet options I can get hald to probe the serial port and find the tablet?

---

### Post by Favux on 2009-05-20
Hi bradtem,

> I can get hald to probe the serial port and find the tablet?
I don't know about that.  Here's the serial subsection of the 10-wacom.fdi:
```
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
```
You can add options to it like you used to in xorg.conf.

---

### Post by bradtem on 2009-05-21
But that's already in 10-wacom so it should be acted on, no?

It gets curious.  The tablet works under Windows, though I had to tell it what serial port it is on.   wacdump /dev/ttyS0 does not seem to get anything, it just drops the baud rate and prints nothing else.     based on lsof, nothing has ttyS0 open, and I tried it as root.   Connecting to ttyS0 with cu shows nothing, but it didn't under windows either.

This tablet has been supported in the linux wacom driver for many years.

Adding notes:  Putting a serial analyser on the port, I never see it get opened, though lshal does report ttyS0 in its list of hardware.  When I run wacdump (this is after a reboot) it does open it and output stuff to the port (hard to say if stuff comes back) but after a short time it reports "WacomOpenTablet: Connection timed out", which it did not do yesterday, oddly.  If I had not seen the tablet work on windows I would wonder if it were bad.

I can't see much debugging on hal, I would like to figure out what is happening when, and if, it opens the serial port to look for devices connected to it, and what it is doing.  Is there a way to get this level of debug?

---

### Post by bradtem on 2009-05-25
> **Favux said:**
> Hi bradtem,

I wonder, given how old the tablet is, whether it's identifier is in the serial tablet subsection of the .fdi file?  They are:
```
"WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5"
```
Do you know what it is?  Any chance you ran:
```
more /proc/bus/input/devices
```
before installing Jaunty?  Or "lshal"?

I put the tablet on a hardy machine and configured it as serial wacom in xorg.conf.  It works.   It does not show up in /proc/bus/input/devices and does not appear to show up in lshal (just the serial port does.)

When xorg boots, in hardy, it reports this success with it
```
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
(==) Wacom tablet model : CT-0045R00,V1.3-5
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Serial PenPartner tablet speed=9600 maxX=5040 maxY=3780 maxZ=255 resX=1000 resY=1000  tilt=disabled
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=5040 bottom Y=3780
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=5040 bottom Y=3780
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=5040 bottom Y=3780

```

Note that wacdump does not seem to get anything from the tablet under either hardy (where the tablet works) or jaunty (where it does not)

If I increase xorg debug, will it let me get the number you are looking for?

---

### Post by Favux on 2009-05-25
Hi bradtem,

Sorry to hear you haven't had any success.  Looking at &#8220;50-xserver-xorg-input-wacom.rules&#8221; in &#8220;/etc/udev/rules.d/&#8221; the symlink for your tablet is the first one and identifies as:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0000", SYMLINK+="input/tablet-penpartner"
```
Would that imply the HAL equivalent should be "WACf000"?  I have no idea.  I wonder which tablet is "WACf001"?  If it is not showing up in "lshal" I don't know how to pull it out.  Maybe you could try:
```
lshal>penpartner_lshal.txt
```
This would give you a text file you could search with gedit for "WAC" and "wacom" etc.

Otherwise how important is hotplugging to you?  Do you have a usb tablet you use too?  Maybe you could compile the most recent linuxwacom and configure it through xorg.conf as before?  Certainly the most recent udev wacom.rules has your tablet.

---

### Post by bradtem on 2009-05-26
I have no great need of hotplug, but I have grown, over time, to hate custom configuring my kernel.  It means I must re-do it every time I get a new kernel (which is pretty frequent) and must also re-do it when I rebuild systems from scratch.  (It's getting so that rebuilding a system from scratch now involves many hours of work beyond just installing to get it the way I like it.)

So frankly, it's a level where I would seriously consider just buying another tablet rather than make my system harder to administer.  I spend too much of my life on system administration.

This is a strange situation, where a well-established tablet stops working in a new release.  I would rather help efforts to see it fixed for all users of serial tablets.  

What I am hoping somebody can answer is what tools can help me figure out what is happening.  There is much less documentation on hal that I expected, and how it is configured to probe serial ports to look for devices etc.   When I start hal, it does not appear to open ttyS0, though it does list it in lshal output.

As I have noted earlier, no wacom shows up in the output of lshal currently. I will hadd WACf0000 to the list of IDs in 10-wacom.fdi and reconnect the tablet at some point.  But if anybody knows how I can see debug streams from lshal and what it does to find the tablet, let me know.   I have to presume it opens serial ports and tries various outputs to see what it gets back to look for devices?  I see no sign of it doing that.     When I run wacdump I see it do some output to the serial port for a short period (after it opens it) and then it stops.  Action on the tablet does not appear to send things back, but it hasn't been told to wake up yet I presume.

---

### Post by Favux on 2009-05-26
Hi bradtem,

I can understand that.  I usually only get the standard kernel updates so it's not an issue for me.

Anyway re HAL.
> One useful tip is that hald's --use-syslog option isn't documented in the Debian man page, and without it you can't see anything that hald is up to. (I've submitted a bug about this.) Update: As the message from hald --help suggests, --use-syslog only works if you also have --verbose=yes.

To get detailed information on your logs, ask hald to be verbose changing your /etc/conf.d/hald to HALD_VERBOSE="yes"

And from man hald:
--use-syslog
Enable logging of debug output to the syslog instead of stderr.
Use this option only together with --verbose.

And this might help:  [http://people.freedesktop.org/~david/hal-spec/hal-spec.html#device-properties-input](http://people.freedesktop.org/~david/hal-spec/hal-spec.html#device-properties-input)

And:  [http://freedesktop.org/wiki/Software/hal](http://freedesktop.org/wiki/Software/hal)

---

### Post by bradtem on 2009-05-26
I had tried those things before but got very little logging, it only reporting what it found, not what it didn't find, no reports of how it opened the serial port and looked for devices, did not find them etc.   I have a debugger on the serial port and I don't see it being opened (even briefly) though in theory I could miss it.

As for "I usually get only the standard kernel updates" I am not sure what you mean by that.  I find there are kernel updates on a fairly regular basis with ubuntu, and it is annoying if one must recompile all custom drivers each time.

---

### Post by bradtem on 2009-05-26
A further note.  Hal debugging (you need to use both the syslog option and the verbose option) shows it doing a few probes at ttyS0 but nothing regarding the tablet.

So I re-enabled the tablet lines in xorg.conf.  (Before I just re-enabled the commented input device lines, I didn't realize that the 3 lines in the serverlayout were gone -- not commented out -- and I put them back in.)

This makes the tablet work, sort of.   When the pen is touching the tablet, enough to click or draw, it works ok.  But removing the pen from the tablet just a little, or having it touch lightly -- the usual way of moving without drawing, causes the cursor to move but on a time delay of about half a second, which is of course very disconcerting and makes it very difficult to use.

I added the Wacf000 to the fdi file but it did not help.

---

### Post by Favux on 2009-05-26
Hi bradtem,

Have you tried to calibrate and configure your tablet with wacomcpl yet?  The stylus might be the default TPCButton "on" not being applied.  There are a couple of other possible settings.  See Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  You might want to look at Jaunty Users near the top.

The LWP HOWTO is helpful if you haven't been to it:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

### Post by aerialyx on 2009-05-27
Hi, I got a similar problem wtc described in the first post. I have tried most of your suggestions, but didn't have any success...
My tablet is a very old serial UD-1212-r. In wacdump everything seems perfect, but without editing xorg, X doesn't seem to recognise the wacom tablet and I don't know what I should write in a cusom_wacom.fdi as the 10-wacom.fdi contains a serial part... 
Could you help me? Thanks in advance.

---

### Post by Favux on 2009-05-27
Hi aerialyx,

Does this, with the tablet plugged in:
```
dmesg | grep ttyS
```
show output like wtc got?

If you do a:
```
lshal>UD-1212-r_lshal.txt
```
can you find at least one section with wacom/your tablet?  Large output to comb through so be prepared.

---

### Post by aerialyx on 2009-05-28
Hi, 
Sorry that I forgot to post this:```
dmesg | grep ttyS0 #wacdump only works with /dev/ttyS0
[    1.436313] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.436665] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
I get this output also when the tablet is unplugged.
Unfortunaltey I couldn't find anything related to wacom or my tablet neither in Xorg.log nor in lshal. 
Thanks for your efforts, Favux :)

---

### Post by Favux on 2009-05-28
Hi aerialyx,

Frankly I'm not sure what's going on.  I think what is suppose to happen is that some .fdi's upstream of the 10-wacom.fdi are suppose to configure the serial stuff so that, if your tablet identifier is in the .fdi, the .fdi then works for you.

Previously did you have to install setserial and add a line to serial.conf based on the info. "dmesg | grep ttyS" gives you?

I wonder if all you need is setserial installed?  Maybe that's the missing ingredient?  Have you checked Synaptics Package Manager to see if it is installed?

---

### Post by aerialyx on 2009-05-28
Hi Favux,
Indeed, setserial wasn't installed, but what do I have to do with setserial? I did a ```
sudo dpkg-reconfigure setserial
```, but this didn't change anything...
Should I add ```
/dev/ttyS0	uart	16550A	port 0x3f8 irq 4
``` to usr/share/doc/setserial/serial.conf?

---

### Post by Favux on 2009-05-28
Hi aerialyx,

I'm not sure.  Things may have changed in Jaunty.  What use to work in Intrepid and earlier was:
```
apt-get install setserial
```
Then enter the /dev/ttyS0 (COM0) settings in /etc/serial.conf. Add to the file:
```
/dev/ttyS0 port 0x3f8 irq 4 autoconfig
```
But I'm not sure if that's the right place for Jaunty.  To apply the settings immediately:
```
sudo /etc/init.d/setserial reload
```
Which then might actually need several reboots and restartings of X to kick in.

But starting in Intrepid I think it was, it seemed some didn't need the serial.conf entry.  If their udev wacom.rules had their symlinks then in xorg.conf having " Option		"Device"	"/dev/input/wacom" " in their wacom sections seemed to work.  Others still needed the line and had to use "/dev/ttyS0" or whatever.  There didn't seem to be a rhyme or reason to it.

Not much help, I know.  Good luck!

---

