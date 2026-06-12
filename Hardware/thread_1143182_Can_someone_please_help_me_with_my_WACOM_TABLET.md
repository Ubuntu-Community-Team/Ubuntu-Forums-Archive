---
title: "Can someone please help me with my WACOM TABLET"
date: 2009-04-29
forum: Hardware
---

### Post by tajmox on 2009-04-29
It's a serial tablet, usually I just have to add the simple code in my xorg.conf and it works.  I have installed wacom-tools and xserver-xorg-input-wacom

[http://pastebin.com/m23a90bbc](http://pastebin.com/m23a90bbc)

THANKS!!!

---

### Post by Favux on 2009-04-29
Hi tajmox,

In Jaunty you are not suppose to use the xorg.conf.  HAL/.fdi files are suppose to handle everything.  So first you should remove all wacom entries to your xorg.conf and return it to its original state.  Actually I'm surprised the wacom entries haven't broken X.

Then see if you get anything out of the tablet.  If not we can try some other things.

When you say you installed the linuxwacom stuff do you mean the 0.8.2-2 version in Jaunty (Synaptics Package Manager)?

---

### Post by tajmox on 2009-04-29
Thanks for your reply.

Yes, I understand the tablet is supposed to simply 'work' but it didn't do anything after I installed Ubuntu, so I assume it's because I'm using a serial tablet and not USB..?

Okay, I removed the lines in xorg.conf and still nothing.
I have the wacom.fdi file in my /etc/hal/fdi/policy folder, it's the default one mentioned on the Ubuntu documentation.

I tried lshal but nothing with the word 'wacom' appears.

---

### Post by Favux on 2009-04-29
Hi tajmox,

Alright.  In Synaptic do you show that you have the linuxwacom 0.8.2-2 installed (drivers=xserver-xorg-input-wacom and wacom-tools)?  The 10-wacom.fdi should contain a subsection for serial tablets:
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
I ask because Jaunty originally started with linuxwacom 0.8.1-6 and a simpler .fdi that looked like the one in Intrepid, before they got updated in the beta and final release.

Let's see what the output of:
```
xsetwacom list
```
and
```
xinput --list
```
looks like.

---

### Post by tajmox on 2009-04-29
Wow, I don't even have that file at all... this is my whole /etc/hal directory contents:

./fdi/information
./fdi/policy
./fdi/policy/preferences.fdi
./fdi/policy/Wacom.fdi
./fdi/preprobe

Can you please paste the whole thing?
I should replace that with my Wacom.fdi right?  Docs say only use one wacom fdi file at a time.

xsetwacom list gave me no output.
xinput --list only listed my keyboard and mouse.

---

### Post by Favux on 2009-04-29
Hi tajmox,

The "native" linuxwacom 0.8.2-2 for Jaunty was specially patched by Timo Aaltonen to work with Xserver 1.6 and HAL/.fdi.

The 10-wacom.fdi file installed by the package xserver-xorg-input-wacom  is in /usr/share/hal/fdi/policy/20thirdparty/ in both Intrepid and Jaunty.

Loic2's Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  has a link to  Wacom.fdi wiki:  [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

How did you set up your tablet before.  Not the xorg.conf stuff, that's equivalent to the .fdi stuff.  You used the pre-installed linuxwacom drivers, correct?  Did you have to install setserial or anything like that for the serial end of things?  What happens if you:
```
dmesg | grep ttyS
```
and
```
ls /dev/ttyS*
```
Tablet having been plugged in during boot, and stayed plugged in.

---

### Post by tajmox on 2009-04-30
Output of dmesg | grep ttyS
```
[    1.557747] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.558043] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

And here is what is in /dev:
```
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3
```

I'm going to try putting the 10-wacom.fdi file into /etc/hal/fdi/policy, do you think that'll do anything?

Before, all I had to do is install wacom-tools and then add the xorg.conf stuff.

---

### Post by Favux on 2009-04-30
Hi tajmox,

It might, I don't know for sure.

What Wacom tablet do you have exactly?

When you modifying the xorg.conf were you using a line like?:
```
	Option		"Device"	"/dev/input/wacom"
```

---

### Post by tajmox on 2009-05-01
I'm using a Wacom Intuos 2 4x5 Serial.

No, I'm not using /dev/input/wacom because that's for USB.  I'm using Driver "wacom" and Device "/dev/ttyS0" 
See pastebin at original post for my xorg.conf.

I tried the .fdi file, and it doesn't work, with or without the xorg.conf changes.

It seems this user didn't get the tablet working with HAL either, and had to use xorg.conf [http://start.ubuntuforums.org/showthread.php?t=1144407](http://start.ubuntuforums.org/showthread.php?t=1144407)
I wonder what he did to get it working, I'll post him a reply or PM.

Meanwhile, do you know anything else I can try?  This is pretty important for work.

---

### Post by Favux on 2009-05-01
Hi tajmox,

As you can see wtc posted how he did it.

Actually /dev/input/wacom works for serial tablets too.  It just depends on whether the wacom symlinks are established in your &#8220;50-xserver-xorg-input-wacom.rules&#8221; in &#8220;/etc/udev/rules.d/&#8221;.  As far as I could tell the latest wacom.rules covered most serial tablets.

Which brings up this thought.  What if your tablet (and wtc's) has inadvertently been left out of:
```
<match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">

```

I can think of two ways to check.  One is to install gnome-device-manager through Synaptics Package Manager.  This is the HAL front end gui.  Then be sure properties is checked in View after you start it.  It should install in Applications>System Tools.  Try to locate your tablet and see if there is an identifier like "WACf001".  Then see if it is in the list above.  Presumably it should be in a line similar to "@info.parent: pnp.id" (I had to put a space after the colon to avoid a smilie).

The other way is to open a terminal and:
```
cd Desktop
lshal>lshal.txt
gedit lshal.txt
```
This will place the output of lshal on your desktop and then open it with gedit.  You need to do this because it is a long list.  You comb through it looking for your tablet section(s) and see what the identifier(s) is/are.  This is tedious, I know because I've done it several times.  In gedit I'm hoping you can use search and simplify things by searching Wacom or @info.parent: pnp.id or pnp.id or WACf* etc.

If you find it and it isn't in there then I think all you would have to do is put it in.

---

### Post by tajmox on 2009-05-01
There wasn't really anything good in my lshal, I tried searching for WAC, wacom, tablet, ttyS, and this is the only interesting thing:
```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
```
And I looked in /etc/udev/rules.d/ and this is what's there```
blake@blake-desktop:/etc/udev/rules.d$ ls
70-persistent-cd.rules  70-persistent-net.rules  README
```
Should I just make a “50-xserver-xorg-input-wacom.rules” file and put that code that you mentioned above?

---

### Post by Favux on 2009-05-02
Hi tajmox,

Good job!  It sure lookes like you found it to me.  You don't have a serial modem, or old serial printer plugged in do you?  Or something similar.

Notice:
```
  info.capabilities = {'serial', 'access_control'} (string list)

```
does indeed contain "serial".  So looking at:
```
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)

```
is "pnp_PNP0501" your pnp.id (plug and play id)?  I'm not sure enough of the syntax to be sure.  My guess is that it is.  If so you just need to change the line:
```
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
```
to
```
      <match key="@info.parent:pnp.id" contains_outof="PNP0501;WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
```
Does this make sense to you?  You'd think it would start with WAC for wacom.  If it doesn't work there is enough stuff there including the uid that we should be able to get somewhere.

No big surprise with the wacom.rules file.  The symlinks in it are only used in xorg.conf.  And since Jaunty isn't suppose to use xorg.conf naturally it isn't there.  But you apparently can use xorg.conf in Jaunty if you manually compile linuxwacom 0.8.3-2.  Let's not go there if we don't have to.

---

### Post by tajmox on 2009-05-02
I added PNP0501 to both the /etc/hal/fdi/policy/10-wacom.fdi as well as the /usr/share/hal/fdi/20thirdparty/10-wacom.fdi just as you suggested.  Which one is the proper file?  (I copied the usr one to the /etc/hal/fdi/policy directory)

Perhaps it's not reading the fdi file properly?

What files should be in my /etc/hal/fdi/policy directory? 
Right now there is just 10-wacom.fdi and preferences.fdi

---

### Post by Favux on 2009-05-02
Hi tajmox,

That's not clear to me.  Looking at:  [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi) it seems to be saying placing a custom_wacom.fdi in /etc/hal/fdi/policy/ takes precedent over the original 10-wacom.fdi in /usr/share/hal/fdi/policy/20thirdparty/.  But it actually doesn't come out and say that, that I see.

So I would nename your .fdi in /etc/hal/fdi/policy/ to whatever.bak instead of .fdi.  Save a copy of the original .fdi in /usr/share/hal/fdi/policy/20thirdparty/ somewhere else also renamed, say .bak.  And then modify the original left in /usr/share/hal/fdi/policy/20thirdparty/.  It just gives us one less thing to worry about.

---

### Post by tajmox on 2009-05-02
Okay, this is bad..
I plugged in my Intuos 3 (USB) to see what happens, and it crashes X.
Well actually, my screen goes totally black with no cursor.  Even CTRL-ALT-F4 doesn't give me a login.

Guess I'll revert everything back to normal and see if this Intuos3 can work... Really prefer the Intuos 2 (it has grip pen)

I'll let you know if it even works after restoring the fdi files.

---

### Post by Favux on 2009-05-02
Bummer.

Looking at the Wacom.fdi again now I think it's saying you can supplement the 10-wacom.fdi by adding the custom_wacom.fdi.  It's not replacing it, it is adding options to it.  So you are suppose to leave the original .fdi alone and add options to it through the custom one?  I'm not sure that makes much sense.  Hmmm.

Good luck!

---

