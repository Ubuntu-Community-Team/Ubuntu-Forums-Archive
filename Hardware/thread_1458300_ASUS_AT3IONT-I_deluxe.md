---
title: "ASUS AT3IONT-I deluxe"
date: 2010-04-19
forum: Hardware
---

### Post by njsharp on 2010-04-19
I'm not sure if this belongs in this forum.  Better suggestions welcome.

From Sydney, Australia.

I am very interested in the possibility of running Ubuntu (probably 10.04 by now) on an ASUS motherboard AT3IONT-I DELUXE.  See spec:

[http://www.asus.com/product.aspx?P_ID=iHWm73RqE6MCmCtw&templete=2](http://www.asus.com/product.aspx?P_ID=iHWm73RqE6MCmCtw&templete=2)

No CPU fan (big passive heat sink), no PSU fan (laptop-like external brick instead)

So, the only noise: a few SATA2 disks, and perhaps not even that if I can work out how to turn them all off when not actually in use.  The board has 4xSATA2 and my plan might be 1xsmall SATA2 for OS, 2xhuge SATA2 RAID0 for SAMBA and TV storage, 1x SATA2 DVD/RW.  Plus a digital TV PCI-Ex16 TWO-channel card (which? suggestions please!)

Functions:
house internet connection and firewall, DHCP server, DNS proxy, SAMBA server, PVR (MythTV? Not had much luck with that so far - still on WMC oh dear!), my desktop machine (firefox, thunderbird, openoffice), perhaps wireless router and bluetooth connector.

And cappuccino maker. :P

My current firewall is CentOS5.4/Dell C640laptop, so is nearly silent - just as well as it is 2M from my bed!

Comments and thoughts welcome.

---

### Post by stevefrench88 on 2010-04-19
I recently purchased this mobo with the plan of installing ubuntu + XBMC and using as a HTPC/torrent box.  I have so far installed ubuntu 10.04 to a USB stick and boot from that until my HDD arrives. I initially attempted to run the PC with ubuntu 9.1, however, I could not get the resolution to display correctly via HDMI - this issue seems to have been addressed with the update to 10.04.

I also have an Apple Airport-Extreme Base Station with multiple external HDDs attached, from which I will stream all my media to the HTPC, as well as being the location to save all of my torrent downloads. 

As well, I purchased a VESA mountable case from minibox, so that the PC will be mounted directly onto the back of my LCD HDTV, and all that will be visible from the viewing angle will be the IR receiver for the remote.  I also chose this particular case as there is a jumper setting for the power button that sets the system to an "always on" state.  Basically, if the power goes out, or if one of my roomates accidentally unplug the PC, it will automatically boot up once power is restored.  Transmission is set to startup and resume once ubuntu loads, as well as XBMC - so as far as anybody in the living room is concerned it's just a "media box", easy for them to use, while I can do all the config remotely via VNC.

I especially love that there is very little to generate any noise in this PC. Both the mobo and case are fanless, however, i did mount a small 40mm fan to help out which is also proving to be whisper quiet.

The only real issue I'm having is that the included ASUS IR remote doesn't fully work with ubuntu.  Some of the "basic" buttons work (ie. the volume buttons), however none of the "special" buttons seem to work. 

This wouldn't be a huge deal, except that one of those "special" buttons include the "back" button - therefore when in XBMC, I can not back out of any menus (i.e. if i want to change from watching videos to listening to music, or even just switching between the folder levels in the video menu).

I have installed LIRC and have tried various methods of configuring, but ubuntu just doesn't seem to recognize the key codes for these buttons, so I can't even customize these buttons for XBMC or have ubuntu "learn" them.

A friend of mine also has the same hardware, and has successfully installed WinXPSP3.  Since asus included all the drivers for WinXP, there were no issues with the installation/setup. He was also able to use Event Ghost to completely customize all the commands for the asus IR remote in XBMC.

I may end up just doing the same and running WinXP on my box for the time being, but I would still prefer the ubuntu setup, so please if anyone comes across a method for successfully get the remote to function fully and/or be customizable with XBMC, I love to know!

---

### Post by moore82 on 2010-05-01
To stevefrench88.

How did you get the sound card working?
I can only get Stereo from the optical output. Do you use your optical output for surround sound?

Best Regards,

Morgan Sundqvist

---

### Post by emisariuss on 2010-05-03
To make HDMI sound output work, You should run alsamixer, and switch mute off on spdif* (or something like this).

Any progress with IRDA device?

---

### Post by rauli on 2010-05-04
I got this board yesterday. Really nice. But I can't get the irda working with lirc. Any ideas? Few of the buttons work with MythTv but not all. What I want to do is use the irda receiver and then make my own config file to use any remote I want, but I can't get irrecord to work. I don't know which driver to use or where the device is located.

Has anyone worked with lirc and this irda?

---

### Post by emisariuss on 2010-05-04
Good news, I have configured 2 buttons: power and back!!

1). sudo apt-get install xmodmap xev

2). xev
Check what keycode You receive by pressing power button and back button (I get 150 and 166)

3). xmodmap -pke > ~/.Xmodmap
create custom .Xmodmap file

4). edit ~/.Xmodmap file, and modify following lines
keycode 150 = s
...
keycode 166 = BackSpace NoSymbol BackSpace

5). xmodmap ~/.Xmodmap
apply custom xmodmap

run XBMC :)

Remember to run (5) every time You run X11 (the best choice is to make an appropriate script and run it at KDE/GNOME/XFCE start).

---

### Post by pj7 on 2010-05-07
Hi,

I have the board and I've been struggling for days with lirc and the remote. I've tried everything but the 8 special buttons do not work.
I've modified mceusb driver to recognize it but it's not working right since the usb interface of the device reports only one endpoint. Then with lirc and devinput driver I think the problem is that the codes that the special buttons send, are outside of the valid keycode range. 
Then I used EventGhost in a windows laptop to discover the keycodes (used the generic hid driver). It reports 4 interfaces, one for each button group. The 3rd interface is for the special buttons and the raw data reveal quite big numbers as keycodes.
So, it's a dead end. Better get another remote.:sad:

The on-board bluetooth (appears in lsusb as 0cf3:3002 Atheros Communications, Inc.) needs the ath3k module which is not on the latest lucid kernel. However the module is coming on a kernel soon and you can grab the code to compile it yourself:
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/ath3k.git
cd ath3k
make
sudo make install
sudo modprobe -v ath3k
echo ath3k | sudo tee -a /etc/modules
```

---

### Post by rauli on 2010-05-07
I also gave up with the included remote. I had a serial Evation irman lying around, so I got a used internal serial cable for 1 € and connected that to the MB. Now I can use lirc and any remote conrtoller I want. I'm running MythBuntu.

---

### Post by sankukai93 on 2010-05-12
Hi rauli,

I use the asus remote with lirc (devinput driver) and of corse, i cant use special button

I've also a serial Evation irman but i dont know how configure it ! :(

Can you help me and say please ? 
is it work with the asus remote ?

Sankukai93

---

### Post by pj7 on 2010-05-12
Hi,

I have been more stubborn than the remote of this board, so I wrote a hid kernel driver that maps the special buttons to useful keys.
It works fine now! \\:D/

I am making a DKMS build system for this driver and the bluetooth driver as well and I will make a deb package that you can install.

---

### Post by sankukai93 on 2010-05-12
pj7,

Really ? Fentastic, it's an excellent news ! :popcorn:

is it possible to have your hid driver, and the way for install it  ? 

I'm very excited.

Thanks

---

### Post by pj7 on 2010-05-13
Ok, I made a deb file (asus-at3iont-i-deluxe-dkms_1.0.1_all.deb) that you guys can install. 
Download it from here: [http://ubuntuone.com/p/3aX/]("http://ubuntuone.com/p/3aX/")

It contains the sources (not prebuilt modules) for my driver (hid-philips-asus) for the remote and the ath3k driver for the bluetooth.

[LIST=1]
[*]Installation
Just install the deb file
```
sudo dpkg -i asus-at3iont-i-deluxe-dkms_1.0.1_all.deb
```

DKMS will automatically build and install both kernel modules to your system, for your existing kernels or after any future installation.


[*]Module loading

The bluetooth module (ath3k) will be loaded automatically after reboot.

The remote module (hid-philips-asus) needs special treatment:
The module depends on usbhid but it has to be loaded *before* the usbhid module, in order to claim the device. Otherwise usbhid claims the device and hid-philips-asus can not act on it.

The problem is that other loaded hid modules might depend on usbhid, so you cannot just unload it.
As a dirty workaround I made a script 'load-module.sh' which unloads all loaded hid modules, loads hid-philips-asus first and then reloads the rest of previously loaded hid modules.

The script has to be run as root:
```
sudo sh /usr/src/asus-at3iont-i-deluxe-1.0.1/drivers/hid-philips-asus/load-module.sh
```

I suggest executing this script from /etc/rc.local so that the remote operates in the desired way after boot. You can add there the line above before the exit command.

Note that if you use lirc then you might want to restart it after executing this script.


[*]Module rebuild
After you edit configuration files (see below) you can automatically rebuild the modules with this command:
```
sudo dpkg-reconfigure asus-at3iont-i-deluxe-dkms
```


[*]DKMS Configuration
The files will be placed in /usr/src/asus-at3iont-i-deluxe-1.0.1 directory.

There you will find a modules.conf file, which has one option to select which modules will be built. By default it contains both modules. On some next kernel release the ath3k module will be included by default, so then you can remove it from that list.


[*]Remote Configuration
You can change the default button mappings by editing the file mappings.h under drivers/hid-philips-asus subdir.
I tried to put some sane default mappings but you can change them as you like.
After editing you need to rebuild the module (step 3)

Note that the remote will operate as keyboard, so you don't really need lirc, if you map all buttons to normal keycodes.
For example  you can map the middle special button to KEY_M instead of KEY_MENU. This in XBMC will bring up the menu.
Personally I don't use lirc. I just put my key mappings in the remote, and then configured various programs that I use (xbmc, mythtv, vlc, mplayer etc) to use the same key shortcuts.

[/LIST]

That's it, install it and tell me how it went.

EDIT:
After loading the remote module as I instructed above, you should see something like this in syslog:

> input: PHILIPS MCE USB IR Receiver- Spinel plusf0r ASUS as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4.1/1-4.1.3/1-4.1.3:1.0/input/input60
philips_asus 0003:0471:206C.0004: input: USB HID v1.00 Keyboard [PHILIPS MCE USB IR Receiver- Spinel plusf0r ASUS] on usb-0000:00:0b.1-4.1.3/input0
That means that the desired driver (philips_asus) claimed the device and applied the custom mappings.

Otherwise (if usbhid got it first) it will be like this:
> input: PHILIPS MCE USB IR Receiver- Spinel plusf0r ASUS as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4.1/1-4.1.3/1-4.1.3:1.0/input/input63
generic-usb 0003:0471:206C.0005: input,hiddev98,hidraw3: USB HID v1.00 Keyboard [PHILIPS MCE USB IR Receiver- Spinel plusf0r ASUS] on usb-0000:00:0b.1-4.1.3/input0


---

### Post by MrCoOkie on 2010-05-14
Thanks a million! You just saved me days!

On an unrelated note, the download link is broken with Chrome. Not that it really matters.

---

### Post by pj7 on 2010-05-14
> **MrCoOkie said:**
> Thanks a million! You just saved me days!

On an unrelated note, the download link is broken with Chrome. Not that it really matters.
You're welcome!
I am using chrome unstable and the download link works as expected.

---

### Post by jugglingcats on 2010-05-14
This is great - thanks. But I have a problem. Now that I've installed your module some of the special keys work but some of the normal keys don't, notably the OK key. If I uninstall the module the OK key starts working again.

Is there any way I can snoop the codes being sent by the remote, to see what's different on mine and adjust the source accordingly? Tried googling but didn't get very far - lost in usbcore vs. usbhid confusion, sorry!

Thanks, Alfie.

---

### Post by pj7 on 2010-05-14
> **jugglingcats said:**
> This is great - thanks. But I have a problem. Now that I've installed your module some of the special keys work but some of the normal keys don't, notably the OK key. If I uninstall the module the OK key starts working again.

Is there any way I can snoop the codes being sent by the remote, to see what's different on mine and adjust the source accordingly? Tried googling but didn't get very far - lost in usbcore vs. usbhid confusion, sorry!

Thanks, Alfie.
You don't need to snoop the codes, I've done it already!
Install the package and then open this file into a text editor as root:
```
gksudo gedit /usr/src/asus-at3iont-i-deluxe-1.0.1/drivers/hid-philips-asus/mappings.h
```
There you will see a list of buttons and their assigned KEY_* keycode. All you have to do is change the keycode for the button you want. For example to change the OK button to Enter:
```
#define BUTTON_OK      KEY_ENTER
```
You can do changes to any button you wish. Just make sure that the KEY_* keycode is a valid keycode, included in [**linux/input.h**]("http://lxr.linux.no/linux+v2.6.33/include/linux/input.h#L123"). If it's not then the building will fail.

Save the file and run this command to rebuild the module:
```
sudo dpkg-reconfigure asus-at3iont-i-deluxe-dkms
```

Now reload the module:
```
sudo sh /usr/src/asus-at3iont-i-deluxe-1.0.1/drivers/hid-philips-asus/load-module.sh
```
That's it, your new codes should be working.

EDIT:
You can verify the keycodes by installing "evtest" and executing:
```
sudo evtest /dev/input/by-id/usb-PHILIPS_MCE_USB_IR_Receiver-_Spinel_plusf0r_ASUS-event-ir
```. Start pressing the buttons and you'll see the key events.

---

### Post by rauli on 2010-05-15
@ Sankukai93
 
Hi. I followed instructions here: [http://www.bsmdev.com/Reference/Sections/InstallNotes-MythTV_section-1.29.html](http://www.bsmdev.com/Reference/Sections/InstallNotes-MythTV_section-1.29.html)
 
Follow the "irman" drivers!
 
I don't know if irman will work with the remote that came with the motherboard, but I suppose it should work because you should be able to use any remote with irman. With the instructions you can try to configure it. I am using a remote that came with my crappy Vision digibox. 
 
My problem now is that when my system boots, sometimes my remote works sometimes not. For some reason lirc does not load on every boot. But if I restart lirc on terminal and restart mythfrontend everything works. Also on this system my remote is a bit slow. On my desktop test machine with mythbuntu 9.10 everything works better. The remote is still useable, so when I get it to load every time I will be happy.
 
I'm using Mythbuntu 10.04 for now.
 
Rauli.

---

### Post by jugglingcats on 2010-05-15
@pj7 many thanks - am making progress now - just need to decide which mappings to use best for MythTV!!

---

### Post by PhracturedBlue on 2010-05-15
I took a slightly different direction to get my remote working.

Initially I followed pj7's directions which work great, but I wanted to use a universal remote (Atlas OCAP) so I had one remote to control Myth and my TV.

I used an IR receiver I already had to capture the cods from the remote, and converted them to an rdmu file.  I then added lots of other keys (like the numbers) and programmed my Atlas with a JP1.3 cable.

You would need a JP1 programmable remote, and a way to program it to use this method, but it means I can fully utilize my universal remote (and don't actually need to use pj7's module to boot)

FYI, the Asus remote uses the MCE protocol, but with a nonstandard device and subdevice

If you are familiar with JP1, the rdmu file can be found here:

[http://www.hifi-remote.com/forums/dload.php?action=file&file_id=8426](http://www.hifi-remote.com/forums/dload.php?action=file&file_id=8426)

---

### Post by jugglingcats on 2010-05-16
> **PhracturedBlue said:**
> I used an IR receiver I already had to capture the cods from the remote, and converted them to an rdmu file.  I then added lots of other keys (like the numbers) and programmed my Atlas with a JP1.3 cable.

I have a Sony universal remote and was planning to have it learn the buttons from the Asus but of course it's still limited to the total number of buttons the Asus has.

I wonder is there any way to get additional buttons working from a universal remote using the Asus receiver (without additional kit)?

As an aside, the Sony universal remote (RM-VL600T) is fine but doesn't have skip back/forward buttons, ie. for DVD chapters. Just in case anyone is considering it...!

---

### Post by PhracturedBlue on 2010-05-16
> **jugglingcats said:**
> 
I wonder is there any way to get additional buttons working from a universal remote using the Asus receiver (without additional kit)?


It should be possible.  I did:
sudo cat /sys/kernel/debug/hid/*:0471:206C.*/events

and pressed buttons on a generic MCE remote, and I see each button press there.  So it should not be hard to create a driver that works with a stock MCE remote, or any remote that can do RC6 protocol even.

For a non JP1 remote, you'd need to find a built-in device that uses RC6 (hint, try Philips devices), then it should not be hard to map all keys using a slight modification to pj7's code.
If you do the above, then try different device codes, you should be able to find one that causes messages to be spewed out (assuming your remote has RC6 capabilities).  There is a possibility that you only get every other key though, since MCE has a toggle bit for each button press that is different than most RC6.  There isn't any way to know unless you try though.


A question for pj7:
how did you get the scancodes you use in your table?
When I look at the HID output, I see things like:
-------
report (size 6) (numbered)
report 5 (size 6) =  05 00 80 0f 04 1f
ff00.0083 = 0
ff00.0003 = 1
ff00.001f = 0
ff00.001e = 1
--------
which I'm not sure how to translate into a scan-code for the table.  I've worked extensively with USB devices, including remotes before, but know next to nothing about the hid system.

---

### Post by pj7 on 2010-05-16
> **PhracturedBlue said:**
> 
A question for pj7:
how did you get the scancodes you use in your table?
When I look at the HID output, I see things like:
-------
report (size 6) (numbered)
report 5 (size 6) =  05 00 80 0f 04 1f
ff00.0083 = 0
ff00.0003 = 1
ff00.001f = 0
ff00.001e = 1
--------
which I'm not sure how to translate into a scan-code for the table.  I've worked extensively with USB devices, including remotes before, but know next to nothing about the hid system.
Hi & thanks for the enlightenment on the universal remotes, I might try what you suggested.

Now to your question: I also have no idea of hid programming, I just took a look on the source code of the other hid drivers. It seemed pretty easy and what I was only missing where the correct hid_usage codes (which are different than input codes) that where generated on button presses. I finally snooped the codes by trial and error.
First I just put some debug printk's in "input_mapping" and "event" functions. Like this:
```

int page, code;
page=(usage->hid & HID_USAGE_PAGE);
code=(usage->hid & HID_USAGE);
printk(DRIVER_NAME ": %s called: %x, %x, %x\n", __func__, page, code, usage->hid);

```
It appears that when the driver connects to the device, the input_mapping function is called for every hid_usage code that the device supports. So you will see a huge list in syslog.
Then in "event" function (which btw is not needed at the end, so I removed it from the code - but you can see it in other hid drivers) every button press generated a syslog dump of all the codes that belong in the same "page" or category.
Generally there are 13 general pages/categories of these codes (look at linux/hid.h for "HID usage tables"). The special buttons of this remote belong to HID_UP_LOGIVENDOR page.
After the debugging, I knew the page of every button and also the list of supported codes in that page.
So I started to map every possible hid_usage code, to normal keys like a, b, c, d, etc and then by pressing the buttons I was able to identify the correct hid_usage code for every button.:)

---

### Post by sankukai93 on 2010-05-18
Hi,

PJ7, congratulations for this driver, it's great work!
All buttons on my remote are recognized with the command "evtest" but how to map keys with xbmc? do I have to use "evrouter? if so, how?

Otherwise, it is possible to adjust the key repeat (i would like more speed for volume + / -)?

Rauli, thank you for your link but I have not had time to look here! :)

---

### Post by pj7 on 2010-05-19
> **sankukai93 said:**
> All buttons on my remote are recognized with the command "evtest" but how to map keys with xbmc? do I have to use "evrouter? if so, how?

The most straightforward solution is to change the mappings (like I suggested above) to resemble xbmc shortcuts.
Like ok button to KEY_ENTER, central special button to KEY_M and so on. Look at xbmc wiki for the default keymap.


> **sankukai93 said:**
> 
Otherwise, it is possible to adjust the key repeat (i would like more speed for volume + / -)?

Not sure about that.

---

### Post by Ramos_GR on 2010-05-22
Hello to all,

I am a new entry in this forum and in a LINUX world, and I hope that you are not too much hard with me!!!:P 
I hope that you can help me into configure the Asus AT3IONT-i deluxe remote control. 
I have installed the XBMCFreak Livecd v14 and the 8 special keys don't work? I have used the .deb file of @pj7 but after the installation (with ctrl+alt+F1 I go into terminal) I obtained a following error:

B]Error! Bad return status for module build on kernel: 2.6.31-20-generic (i386)
Consult the make.log in the build directory
/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/ for more information.
dpkg: error processing asus-at3iont-i-deluxe-dkms (--install):
subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
asus-at3iont-i-deluxe-dkms[/B]](*,)

After that I have tried to perform all step guide of @pj7, but when I sent the code:

**sudo sh /usr/src/asus-at3iont-i-deluxe-1.0.1/drivers/hid-philips-asus/load-module.sh**

I obtained:

**Module 'hid-philips-asus' is not installed.**

I don't have familiarity with linux but I learn in hurry and I hope can you help me!!!!:)

---

### Post by pj7 on 2010-05-23
> **Ramos_GR said:**
> 
B]Error! Bad return status for module build on kernel: 2.6.31-20-generic (i386)
Consult the make.log in the build directory
/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/ for more information.

Hi and welcome,
please post here the contents of that file:
/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/make.log

Obviously something fails to build with that kernel. I have only tested this in Lucid kernels (>=2.6.32).

---

### Post by Ramos_GR on 2010-05-23
> **pj7 said:**
> Hi and welcome,
please post here the contents of that file:
/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/make.log

Obviously something fails to build with that kernel. I have only tested this in Lucid kernels (>=2.6.32).

The contents of **make.log** is:

[I]DKMS make.log for asus-at3iont-i-deluxe-1.0.1 for kernel 2.6.31-20-generic (i386)
Sun May 23 15:31:20 CEST 2010
mkdir modules
make -C drivers/hid-philips-asus
make: *** drivers/hid-philips-asus: Permission denied.  Stop.
make: *** [hid-philips-asus] Error 2[/I]

Thanks for your support and I hope that you can help me...:P

---

### Post by pj7 on 2010-05-23
> **Ramos_GR said:**
> The contents of **make.log** is:

[I]DKMS make.log for asus-at3iont-i-deluxe-1.0.1 for kernel 2.6.31-20-generic (i386)
Sun May 23 15:31:20 CEST 2010
mkdir modules
make -C drivers/hid-philips-asus
make: *** drivers/hid-philips-asus: Permission denied.  Stop.
make: *** [hid-philips-asus] Error 2[/I]
That's really weird. I will try to debug it sometime soon.

---

### Post by pj7 on 2010-05-23
Well it seems that in earlier distributions (like the ones that xbmc live cds have) dkms has a bug with permissions (trying to build as user nobody). The drivers build fine though, you just have to do it the manual way.
So if you get that error during the building process and you don't want to upgrade to 10.04 (where this deb works fine), here's the manual way. Open a console and go:
[LIST=1]
[*]Uninstall the package but copy the source code first:
```

sudo cp -r /usr/src/asus-at3iont-i-deluxe-1.0.1 /tmp
sudo apt-get purge asus-at3iont-i-deluxe-dkms
sudo cp -r /tmp/asus-at3iont-i-deluxe-1.0.1 /usr/src

```


[*]Build & install the drivers manually
```

cd /usr/src/asus-at3iont-i-deluxe-1.0.1
sudo make
sudo make install
sudo sh drivers/ath3k/fw_inst.sh

```

[/LIST]
Now it should work. You can modify the mappings as instructed above and then rebuild the modules with step 2.
Remember that when you install a new kernel you will have to boot at that kernel and rebuild the modules for that kernel.
If you upgrade to 10.04 distribution, you will not need all this, just install the deb package and it should work.

---

### Post by Ramos_GR on 2010-05-24
> **pj7 said:**
> Well it seems that in earlier distributions (like the ones that xbmc live cds have) dkms has a bug with permissions (trying to build as user nobody). The drivers build fine though, you just have to do it the manual way.
So if you get that error during the building process and you don't want to upgrade to 10.04 (where this deb works fine), here's the manual way. Open a console and go:
[LIST=1]
[*]Uninstall the package but copy the source code first:
```

sudo cp -r /usr/src/asus-at3iont-i-deluxe-1.0.1 /tmp
sudo apt-get purge asus-at3iont-i-deluxe-dkms
sudo cp -r /tmp/asus-at3iont-i-deluxe-1.0.1 /usr/src

```
[*]Build & install the drivers manually
```

cd /usr/src/asus-at3iont-i-deluxe-1.0.1
sudo make
sudo make install
sudo sh drivers/ath3k/fw_inst.sh

```
[/LIST]
Now it should work. You can modify the mappings as instructed above and then rebuild the modules with step 2.
Remember that when you install a new kernel you will have to boot at that kernel and rebuild the modules for that kernel.
If you upgrade to 10.04 distribution, you will not need all this, just install the deb package and it should work.

I will try as soon as possible and I'll know.
Thanks again.:P

---

### Post by Ramos_GR on 2010-05-24
> **pj7 said:**
> 
[*]Module rebuild
After you edit configuration files (see below) you can automatically rebuild the modules with this command:
```
sudo dpkg-reconfigure asus-at3iont-i-deluxe-dkms
```


Hi Pj7,

GREAT... Now remote control Work!!!:P

I have tried to reconfigure some key like OK_Buttom as suggested by you 
```
#define BUTTON_OK      KEY_ENTER
```,
and after I have rebuilded the module 
```
sudo dpkg-reconfigure asus-at3iont-i-deluxe-dkms
```,
but I have obtained

*/usr/sbin/dpkg-reconfigure: asus-at3iont-i-deluxe-dkms is not installed*

and I have not succeeded to reconfigure the key.

Can you help me on this.

Thanks for the commendable support.=D>

---

### Post by pj7 on 2010-05-24
You're welcome, glad I helped!
Perhaps I wasn't clear enough. In your case, to rebuild the modules you have to use the manual way, that is step 2 from my previous post.

---

### Post by PhracturedBlue on 2010-05-27
Has anyone tried modifying the lirc driver to add 0471:206c, removing the usbhid module, and loading lirc_mceusb?

For folks who want to use the included remote, pj7's solution is definitely the easiest, but using lirc would allow the use of virtually any universal remote.

Another option would be to do something like they used to do with the DVB remotes, and modify pj7's driver to add an interface in /proc that allows full customization of the scan codes.

---

### Post by PhracturedBlue on 2010-05-27
I've done some more snooping.  The IR receiver seems a bit odd.
It does not behave like a standard MCE receiver (which reports raw pulses).  Instead it interprets MCE codes and reports the resulting decoded signal.  It may be possible to use LIRC with it, but probably not with the mceusb driver.

It also seems to have an internal mapping of keyboard codes.  If I press a key it knows about, the output is a valid scan code (a single signal for press, and another for release...this is recognizable by the keyboard driver..though for some codes, a modified driver is needed).  If I use my MCE remote, it passes the signal directly through (I see continuous signals while the button is pressed, and tehre is no release code.  The hid driver can convert this to a scancode, but you can't get key-repeat with it as far as I can tell)

If I use a non MCE remote, it reports nothing at all (so the only remotes that will work will be those that know the MCE protocol)

So the end result is that the way pj7 is doing this is probably the easiest way to use the IR receiver, and you will likely be limited to either a JP1 remote, the supplied remote, or a universal that can learn the asus remote.  Getting more keys is likely only possible with a JP1 remote.

---

### Post by pj7 on 2010-05-28
> **PhracturedBlue said:**
> Has anyone tried modifying the lirc driver to add 0471:206c, removing the usbhid module, and loading lirc_mceusb?
Oh yes, that was my first attempt actually. I modified the lirc_mceusb code and added 0471:206c. But it fails (at mceusb_dev_probe function), as lirc_mceusb driver requires an inbound and an outbound endpoint, wheareas this device lacks the outbound endpoint.

---

### Post by PhracturedBlue on 2010-05-29
Ok, I am finished mucking around with this remote.
I have all buttons of my Atlas Remote mapped to keys that MythTV can see after much pain.

I am including the following:
1) modifications to pj7's code to add all keycodes that the IR receiver supports
2) mappings from linux keys to x11 keys (x11 can't see everything in linux/inputs.h)
3) mapping of the button codes in the driver to HEX codes for RemoteMaster (these are the codes the remote sends that generate the proper scan-codes)
4) RMDU file for RemoteMaster that maps buttons to the remote

I'm not sure many folks would want to go through the effort of setting up a JP1 remote, but getting everything to work properly proved to be more of a challenge than I expected, so I'm documenting it here (especially in case I ever need to do it again)

pj7, feel free to incorporate my changes if you like.

---

### Post by PhracturedBlue on 2010-05-29
FYI, it is possible to force hid-philips-asus to run before usbhid by adding the following to /etc/modprobe.d/hid-philips-asus.conf:
```

sudo sh -c 'echo "install usbhid /sbin/modprobe hid_philips_asus ; /sbin/modprobe -i usbhid ; true" > /etc/modprobe.d/hid-philips-asus.conf'
sudo sh -c 'echo hid-philips-asus >> /etc/initramfs-tools/modules
sudo update-initramfs -u

```

This is more unixy than running pj7's shell script during startup

---

### Post by PhracturedBlue on 2010-05-29
On a different topic here are some alsa settings I found from around the web that work with this board:

To use HDMI audio by default, create ~/.asoundrc and add:
```

pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:0,3"
}
}
```
No need to reboot, it should take effect immediately (fyi, I'm using the nvidia graphics drivers..I'm not sure if that is necessary or not)

To use analog 5.1 audio (from the 3 headphone jacks in the rear panel):
```

sudo sh -c 'echo "options snd-hda-intel model=3stack-6ch enable=1 index=0" >> /etc/modprobe.d/alsa-base.conf'

```
then reboot and run alsamixer to enable the proper channels

---

### Post by pj7 on 2010-05-30
Excellent work PhracturedBlue, thanks!
I will update the package to include it.

---

### Post by backons on 2010-06-02
Yesterday I saw that my mainboard is connected with the wifi only with  54mbit/sec. So I changed my router that he accepts only Draft-N Wifi.  But after this I cant´t connect with the mainboard to the wifi anymore [IMG]http://forum.xbmc.org/images/smilies2/confused1bb.gif[/IMG]
Do I have a wrong driver for the Wifi ?? 
I am using Ubuntu 9.10

---

### Post by get_ on 2010-06-06
First: many thanks pj7 for the great work with the drivers and for sharing it here.

And onto my question: Have anyone experienced problems with HD-material in XBMC. For me, I have some stutter and occasional problems with audio synchronization. 

There is this great guide here: [http://forum.xbmc.org/showthread.php?t=70068](http://forum.xbmc.org/showthread.php?t=70068) which seems to have helped many XBMC Linux users.

I was able to follow it and setup the correct displaymodes in my xorg.conf. The results? I think I had an improvement but I still have some jerkiness, and problems with audio sync.

Anyone else having similar problems with AT3IONT-I on Lucid?

---

### Post by PhracturedBlue on 2010-06-08
> **get_ said:**
> 
And onto my question: Have anyone experienced problems with HD-material in XBMC. For me, I have some stutter and occasional problems with audio synchronization. 

There is this great guide here: [http://forum.xbmc.org/showthread.php?t=70068](http://forum.xbmc.org/showthread.php?t=70068) which seems to have helped many XBMC Linux users.

I was able to follow it and setup the correct displaymodes in my xorg.conf. The results? I think I had an improvement but I still have some jerkiness, and problems with audio sync.

Anyone else having similar problems with AT3IONT-I on Lucid?
I'm not using XBMC (Mythtv instead on Lucid) but I haven't had any issues with HD material (either H264 or MPEG2) while using VDPAU.  I've used both analog and digital output without any audio issues.  I haven't yet tried watching BluRay media yet (that is a lot higher bandwidth).  I do sometimes notice a little tearing (always 1/4 from the top of the screen.  I'll need to check the deinterlacer settings.

---

### Post by get_ on 2010-06-09
Today I got a break trough in my issues with HD video stutter, by installing libvdpau from the Nvidia PPA:

```
sudo add-apt-repository  ppa:nvidia-vdpau/ppa
sudo apt-get update
sudo apt-get install libvdpau1
```

After trying out a lot of xorg.conf settings recommended across forums, I found out that you can see some performance metrics during playback in XBMC by pressing 'o'. The framerate of the video could not catch up to the needed ~24 Hz, and the CPU usage was fairly heavy. After the libvdpau thing the CPU percentages went down significantly, no framedrops and the framerate was steady. 

Finally the gnawing thought that my configuration is suboptimal, leading to trial and error sessions long into the night, perhaps will disappear. :D

---

### Post by freaksworth on 2010-06-12
Hi,
thanks for your work, pj7.
When I remove ath3k from modules.conf, because I am using the remote on another pc and do not need the bt modules, it does not build anymore using dpkg-reconfigure.
modules.conf
```
# modules build config file

# Comma separated list of kernel drivers to build
# Avialable drivers are:
#       Remote driver:          hid-philips-asus
#       Bluetooth driver:       ath3k
MODULES=&quot;hid-philips-asus&quot;
```shell:
```
------------------------------
Deleting module version: 1.0.1
completely from the DKMS tree.
------------------------------
Done.
Loading new asus-at3iont-i-deluxe-1.0.1 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-22-generic
Building for architecture i686
Building initial module for 2.6.32-22-generic

Error!  Build of ath3k.ko failed for: 2.6.32-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/ for more information.
```make.log:
```

DKMS make.log for asus-at3iont-i-deluxe-1.0.1 for kernel 2.6.32-22-generic (i686)
Sa 12. Jun 15:53:12 CEST 2010
mkdir modules
make -C drivers/hid-philips-asus
make[1]: Betrete Verzeichnis '/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/drivers/hid-philips-asus'
make -C /lib/modules/2.6.32-22-generic/build M=/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/drivers/hid-philips-asus modules
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/drivers/hid-philips-asus/hid-philips-asus.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/drivers/hid-philips-asus/hid-philips-asus.mod.o
  LD [M]  /var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/drivers/hid-philips-asus/hid-philips-asus.ko
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-22-generic'
make[1]: Verlasse Verzeichnis '/var/lib/dkms/asus-at3iont-i-deluxe/1.0.1/build/drivers/hid-philips-asus'
cp drivers/hid-philips-asus/hid-philips-asus.ko modules
```It still works, if I compile and install hid-philips-asus manually.
regards f

---

### Post by PhracturedBlue on 2010-06-12
> **get_ said:**
> After trying out a lot of xorg.conf settings recommended across forums, I found out that you can see some performance metrics during playback in XBMC by pressing 'o'. The framerate of the video could not catch up to the needed ~24 Hz, and the CPU usage was fairly heavy. After the libvdpau thing the CPU percentages went down significantly, no framedrops and the framerate was steady.

FYI, I've been reading about others who had vdpau issues, and it has been mentioned that performance is much better when using 2 sticks of ram than 1 (i.e. 2x1GB has better performance than 1x2GB)  I have not been able to verify myself though.

---

### Post by dubbeljoe on 2010-06-17
@PJ7;
I want to follow your guide and .deb, but unfortunately the download page doesn't work (IE8)
is it me or is it something else?
 
Thanks in advance for your reaction.
 
Dubbeljoe

---

### Post by get_ on 2010-06-19
> **PhracturedBlue said:**
> FYI, I've been reading about others who had vdpau issues, and it has been mentioned that performance is much better when using 2 sticks of ram than 1 (i.e. 2x1GB has better performance than 1x2GB)  I have not been able to verify myself though.

I have actually tried both 1x2GB and 2x2GB, but since i had libvdpau properly set up, there is no difference as far as x264 playback is concerned. Though when I first installed the second memory stick, I again started experiencing choppy playback. It turned out that the chassis fan was broken and the problems this time was because of overheating :)

---

### Post by PhracturedBlue on 2010-06-23
> **get_ said:**
> I have actually tried both 1x2GB and 2x2GB, but since i had libvdpau properly set up, there is no difference as far as x264 playback is concerned. Though when I first installed the second memory stick, I again started experiencing choppy playback. It turned out that the chassis fan was broken and the problems this time was because of overheating :)

Interesting.  I am running fan-less on mine (with netboot, so no heat from a disk-drive either), with a single 2G stick of RAM.  I watch almost exclusively HD material (using vdpau of course).  No overheating problems in the last month I've been using it.  We'll see how it holds up through the summer.

---

### Post by dubbeljoe on 2010-06-25
Forget about my previous posting, it works now!
thnx PJ7

---

### Post by neovandeen on 2010-06-27
Hi, I bought this board too, and I love it.
My small case is also fanless and the temperatures popped a little bit high, so I installed a quite 40mm fan. The Q-Fan function in the BIOS works great too (runs the fan at 2-3000 rpm instead of 4500 rpm. 
I don't have the deluxe version (without IR and wireless)
The box runs 10.04 with auto login.
As my frontend I use Boxee. I set it up as default session, so I don't have to use Gnome.
As a remote, I use the Android app for Boxee.

Don't forget the VDPAU driver for hardware accelerated video playback.

I'm so happy with this little piece of hardware.

---

### Post by gabesword on 2010-07-02
Edit:  Nevermind.  I ended up installing to a hard drive.


I have this board and am having trouble getting ubuntu to boot.  I have the install disk on a USB thumbdrive and another thumbdrive that I am trying to install the OS on.

I can boot the install disk and it says the install is successful.  When I boot from the stick with the fully installed OS on it, I just see a black screen with a flashing underscore cursor.

When I look at the thumbdrive on another PC I can see that all of the file structure looks normal.


Anybody have any ideas what I'm doing wrong?

---

### Post by MichaelRX8 on 2010-07-11
I have this board. In sysinfo and system monitor it says it has 4 cpus? Is this right?

---

### Post by cascade9 on 2010-07-11
> **MichaelRX8 said:**
> I have this board. In sysinfo and system monitor it says it has 4 cpus? Is this right?

No, its got 1 CPU with 2 cores + hyperthreading for each core (which appears as a core, but its not a real core)

---

### Post by Jenga201 on 2010-07-16
I am having trouble with 1080p playback.  The sound is fine, but the video just stops.  I can navigate forward in VLC and where the video just freezes.

I have libvdpau1 and nvidia-current installed.  Is there anything else i need to do to have 1080p playback?

---

### Post by cascade9 on 2010-07-16
Last time I looked, getting VLC to work with VDPAU wasnt easy. 

You might be better off trying smplayer. Its a lot easier to get VDPAU going with that ;)

---

### Post by Jenga201 on 2010-07-16
VLC is just a test player.  I can try playing test videos with smplayer, but my main concern is boxee.

Playing 1080p in boxee results in lots of lag.  I tried everything with tiny7 and the nvidia driver for windows in boxee and it played flawlessly. 

Other people have gotten 1080p  to work on this board.  Did you guys just install nvidia-current and libvdpau1 and have it work?

---

### Post by Jenga201 on 2010-07-16
Well, i feel like an idiot.  My problem was in boxee.  In settings there's an option to enable hardware acceleration which was checked (i thought nothing of it).  But if you uncheck that, you have the option to select VDPAU.

Now on to setting up the remote. :)

---

### Post by Kendric Evans on 2010-08-08
Hey, I've been lurking around these forums for some time and have been playing with various forms of ubuntu media servers/desktops/whatevers for a few years.
I recently purchased this at3ion-t deluxe motherboard and I was incredibly pleased to notice that PJ7's bluetooth drivers worked flawlessly!
However, I have been having trouble with the infrared remote:  The events register just fine in evtest, but don't seem to actually do anything anywhere else.
I'm running Ubuntu Lucid on a headless box and no special frontend.  I'd like to be able to control my media player and at least pause/skip/rewind the music that's playing.

---

### Post by dubbeljoe on 2010-08-28
can someone tell me if the "asus-at3iont-i-deluxe-dkms_1.0.1_all.deb" is still available somewere? the link given by PJ7 doesn't seem to work anymore?
 
Thanks in advance
 
DubbelJoe

---

### Post by jasiu85 on 2010-09-02
Hey guys,

I'm also planning to buy this mobo and build a workstation/htpc/router thing around it. Could anyone who already bought it do a `lspci` for me? I'm especially interested if the built-in wifi can be put in access mode.

Thanks,

Mike

---

### Post by disparil on 2010-09-02
Many thanks pj7!

the package works perfectly.

now I have xbmc running in lucid, with wifi + bt + remote working. Thanks again!

Actually, that first attempt, was that everything worked with XBMC Live 9.11 but not even detected the wifi, so I decided to install Ubuntu Lucid.

---

### Post by firegeek on 2010-09-06
I was curious to know where you mounted the fan. I also ordered a 40mm quite fan. Some appear to have just stacked directly on top of the cpu heat sink. But, I was considering mounting it to the case to have to air flow over the heat sink. I'm waiting for all my parts to arrive to include the Thermaltake Case ([http://hardwarebistro.com/index.php?option=com_simple_review&Itemid=84&review=142-Thermaltake-Element-Q-Case-Review](http://hardwarebistro.com/index.php?option=com_simple_review&Itemid=84&review=142-Thermaltake-Element-Q-Case-Review)).

---

### Post by neovandeen on 2010-09-07
Hi, I mounted it with some cable ties between the case and the heatsink. It fits very strong and in case, it's easy to remove.

---

### Post by firegeek on 2010-09-07
Thanks for the reply and pics. I chose a Thermaltake "Q" case, 4gb ddr3, 1tb WD caviar Black and a Sony sata dvd drive. My thoughts on the case was that I may install a fuul size graphics card and use the 200watt power supply just for it if I'm not pleased with the on-board graphics. But, all that I have read most are pleased. One question that I have all in this thread/forum, since this is my first dedicated Linux box, should I create a partition for the os and a ntfs partition for the data as some suggest?

---

### Post by neovandeen on 2010-09-07
As you can see, my case is for htpc's. I don't think you'd be satisfied enough with the dual core atom, if you're planning to install a bigger graphics card (you'll probably play games or so). 
The ION chipset is, in my opinion, very useful for h.264 encoding, like full HD movies and so on. On Linux there are some drivers called "vdpau", which lets you access the cuda API. (video will be rendered on graphics card, instead of cpu).
The partitioning layout could vary from case to case. 
If you're planning to dual boot Linux and Windows, it could be useful to have a shared NTFS partition, where you can access your files from both operating systems.
If you're running only Linux, there's no need to do that.

---

### Post by firegeek on 2010-09-07
All valid points! I think that the on-board graphics will serve my purpose. The case just came with a 220 amp ps and I have a few graphic cards just laying around--one with a tuner. Not much on gaming. Would love to but at 49 my hands and brain just can't deal with all the buttons. We have a PS3, HP home server, (3) Tivos and several Windows machines on our lan. I'm building this just for the experience, podcast, internet on the big screen, etc. As for adding a ntfs partition, this was suggested in anther post for sharing, but know as I read your comments I might just dedicate it all to Unbuntu/Boxee.

---

### Post by neovandeen on 2010-09-07
Good choice! I'm running Boxee on my htpc too. I've got it running as a session because I don't need Gnome and all the other software on my tv. So it directly starts into it and my tv is ready to go, whatever I want to watch. Well, you might've noticed, if you close Boxee, the pc won't shut down. What you can do is to write a wrapper script around the boxee binary and change some permissions on /sbin/shutdown and it'll do it.
Tell me, if you need some advice.

---

### Post by ddewaele on 2010-09-07
I've installed this board in both a Lian Li PC-Q07 case, and in an Antec ISK 310-150.

I manage to run it fan-less. Highest temperature reading I got from the GPU was 74 degrees in the Antec case, and 70 degrees in the Lian Li case (both after several hours of 1080p video decoding). The Antec Tricool Case fan in the Antec case was emitting low noise (in the low setting) but it was still audible.

I wanted to have [URL="http://do-it-yourself-htpc.blogspot.com/2010/08/asus-at3iont-i-deluxe-review_866.html"]a complete silent HTCP setup.
[/URL]
What's your experience with these 40mm fans ? Aren't they rather noisy (high pitch tones). I have an AsRock Ion box that's driving me crazy (fan noise) after several hours of movie watching.

---

### Post by neovandeen on 2010-09-07
I looked out for the slowest 40mm fan. Dont't know which brand it was. In the bios settings, there is a feature called "Q-Fan" or so, which dynamically adjusts the fan speed to the temperature. This works great for me. The fan runs at 2500rpm and the CPU/GPU is at about 45° celsius. In this case, I can't hear the fan.

---

### Post by Pwyll123 on 2010-09-08
Hi,
I also installed that MohterBoard in a ThermalTake Q case. Running without any fan, GPU was going up around 70°C. So I installed a 80mm fan (Noctua NF-R8) in the case. I actually dismonted the build-in power supply in the case, and screwed the fan where the powersupply fan was residing.

Thanks to the dynamic speed adjustment of the MB, my fan runs at 1000 RPM and is completly noiseless. Heat does not fo over 45°C for the GPU.

Pwyll

---

### Post by bolojo on 2010-09-08
Hi to all.
Because of the absence of an AT3IONT-I dedicated thread and the same sound card on the two mobos (AT3IONT-I and AT3IONT-I deluxe) I write this here:
I want to know if all of you have any problem with the sound over hdmi, only in the case of ubuntu 10.04 usage,because i have no sound (from none of the cards (realtek or hdmi)) at all when digital sound is enabled,neither with spdif enabled nor with spdif disabled)
Thx in advance

---

### Post by Pwyll123 on 2010-09-08
Hi Bolojo,
They may be many reasons why you do no get any sound. I also depends in which applications (GNOME, XBMC, Boxee, etc) you want sound available. There exists many thread regarding sound issues in Ubuntu, especially with HDMI/SPDIF output.

First thing to male sure of is that your master sound is not mute off. You can verify this with the alsamixer command (or the equivalent gnome-alsamixer packahe to install). 

Second check in the Sound Preferences GNOME menu that your HDMI output is selected in the Hardware tab.

And finaly try to issue the speaker-test command in the terminal. This should enable you HDMI output in GNOME and other applications using PulseAudio.

For a more detailed configuration in XBMC (enabling 5.1 output in SP/DIF), you can follow this thread
[http://forum.xbmc.org/showthread.php?t=73767](http://forum.xbmc.org/showthread.php?t=73767)

Good luck, it's not an easy matter :)
Pwyll

---

### Post by bolojo on 2010-09-11
thx for your reply!
1)the sound is not muted (alsamixer and gnome panel tested)
2)i both tested the hdmi output option in the gnome's sound preferences and the hdmi output/analoginput option->no luck
3)i will try this test speaker-test command in the terminal and post the results, but i'm not optimistic about that
 
and btw i want to be able to listen sound on gnome and on a kind of video player like vlc or totem in order to play hd videos via hdmi cable on a LG flatron tv
 
> **Pwyll123 said:**
> Hi Bolojo,
They may be many reasons why you do no get any sound. I also depends in which applications (GNOME, XBMC, Boxee, etc) you want sound available. There exists many thread regarding sound issues in Ubuntu, especially with HDMI/SPDIF output.
 
First thing to male sure of is that your master sound is not mute off. You can verify this with the alsamixer command (or the equivalent gnome-alsamixer packahe to install). 
 
Second check in the Sound Preferences GNOME menu that your HDMI output is selected in the Hardware tab.
 
And finaly try to issue the speaker-test command in the terminal. This should enable you HDMI output in GNOME and other applications using PulseAudio.
 
For a more detailed configuration in XBMC (enabling 5.1 output in SP/DIF), you can follow this thread
[http://forum.xbmc.org/showthread.php?t=73767](http://forum.xbmc.org/showthread.php?t=73767)
 
Good luck, it's not an easy matter :)
Pwyll

---

### Post by bolojo on 2010-09-11
bolojo@bolojo-nettop-htpc:~$ speaker-test 

speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11.462907
 0 - Front Left
Time per period = 11.465330
 0 - Front Left
Time per period = 11.459576
 0 - Front Left
Time per period = 11.457166
 0 - Front Left
Time per period = 11.458273
 0 - Front Left

As you can see my friend nothing,fyi i have only the hdmi cable connected to the tv!

---

### Post by phjr on 2010-09-14
Hi guys, I'm thinking about this board, to use it for my Ubuntu+XBMC HTPC - but I have a question, not really related to the software, but surely to the remote; is it possible to use the remote to actually power on the system? Or does it only work once it is powered?

Thanks a lot, cheers!

---

### Post by rauli on 2010-09-16
@bolojo: When you get the sound working on ubuntu, VLC needs it's own settings to get the hdmi sound working. Check here: [http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/](http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/) . Look at "VLC sound settings".
 
> **bolojo said:**
> thx for your reply!
1)the sound is not muted (alsamixer and gnome panel tested)
2)i both tested the hdmi output option in the gnome's sound preferences and the hdmi output/analoginput option->no luck
3)i will try this test speaker-test command in the terminal and post the results, but i'm not optimistic about that
 
and btw i want to be able to listen sound on gnome and on a kind of video player like vlc or totem in order to play hd videos via hdmi cable on a LG flatron tv

---

### Post by bolojo on 2010-09-16
By now my problem doesn't seem to be the player but the sound... I love VLC because before the HD era it was my favorite player and I hope I can use it to see HD videos, WITH SOUND:biggrin:
> **rauli said:**
> @bolojo: When you get the sound working on ubuntu, VLC needs it's own settings to get the hdmi sound working. Check here: [http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/](http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/) . Look at "VLC sound settings".

---

### Post by firegeek on 2010-09-17
Up and running! Wow, this was my first endeavor into the linux world. All is going pretty well. Installed 10.4 and Boxee and had to fool around with scaling to get the toolbars visible on my desktop...Know trying to get the Bluetooth running. I downloaded PJ7 file, but it's still not recognizing the on-board BT. I have a lot to learn about the interface, terminal, etc. But, I'm having a blast with 60" of Unbuntu and all that goes with it. I would love to get my Logitech BT keboard/track pad working to get me off the leash. Below is the return--maybe someone can direct me in the right direction. Thanks in advance...

firedo@dcm-htpc:~$ sudo dpkg -i asus-at3iont-i-deluxe-dkms_1.0.1_all.deb
[sudo] password for firedo: 
dpkg: error processing asus-at3iont-i-deluxe-dkms_1.0.1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 asus-at3iont-i-deluxe-dkms_1.0.1_all.deb
firedo@dcm-htpc:~$ sudo dpkg -i asus-at3iont-i-deluxe-dkms_1.0.1_all.deb
dpkg: error processing asus-at3iont-i-deluxe-dkms_1.0.1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 asus-at3iont-i-deluxe-dkms_1.0.1_all.deb
firedo@dcm-htpc:~$

---

### Post by firegeek on 2010-09-17
I finally figured it out! I now have BT working. I went to the folder where the .deb file was located > r click > used GDebi Installer > restart > YES!

I know that this has got to be simple for most of you, but again this is my first experience with any Linux other a boot-disk version. Oh, how I can see me getting addicted to this. Next I'll solve the sound issue. At this point I have hooked straight to 50" Sony Bravia via HDMI. But, soon will move it to one of the inputs on my Yamaha RX-V2700 receiver. My home network consist of several desktops, laptops, PS3, Wii, (3) Tivos, (2) IP cameras and a HP Home Server. So, I have plenty of tweaking to do. Thanks again to all involved. I appreciate all the long hours dedicated to all open source software. BTW--I'm now typing untethered via a Logitech BT keyboard/trackpad (PS3 ver.) that has been collecting dust. Initially the plan was to run Yellow Dog on the PS3. Very problematic and Sony did away with the option to install another os in an update. Not to mention the one only one option you had in partitioning the hd.

The code for the remote states that it has to be run as "root". Can some one lead in the right direction...

---

### Post by anjohan on 2010-09-18
Hi guys,

After reinstalling Ubuntu I cannot get the bluetooth module working. I've installed Pj7's deb file and sorted HDMI sound and the remote settings. However, on luck whatsoever with the BT. Note that it was running fine before I reinstalled and that I have used the same method this time as far as I know.

I am new to Ubuntu and Linux so how do I debug this? I have installed blueman, reinstalled the deb file from Pj7 and played around with it without any luck.

Also, while booting up the system there is an error message: nForce2_smbus 0000:00:03.2: Error probing SMB1. Haven't figured out what that is. Could it be correlated with the bluetooth issue?

Cheers

---

### Post by firegeek on 2010-09-18
My problem was that I double-clicked the .deb file in the download folder and acted as if it was installing. It wasn't until open the download folder > right clicked on the .deb file > selected use Gdebi Installer that my started working. I thought it working like a .exe file.
I hope that this works for you as it did for me running 10.4...

---

### Post by anjohan on 2010-09-19
It seams to appear my Microsoft mouse connected to one of the front usb ports caused some kind of conflict. Once I relocated the mouse to another mouse and restarted the system the bluetooth appeared in Ubuntu.

---

### Post by firegeek on 2010-09-20
Where oh where did my Bluetooth go? The only thing I did was change the setting in the mb bios for the front audio jack from HD to AC7. My keyboard stopped working and I'm back to the point where it;s not seeing the Bluetooth adapter. I re-installed the driver as I did in the beginning > restart x 2 for both and to still not there. BTW--I used Debi Installer. I'm going back and change the bios setting--as I just thought about that this was the only change that was made.

---

### Post by firegeek on 2010-09-21
Update: I reinstalled Unbuntu 10.04.1 and the drivers just like the first time. It's not seeing my Bluetooth device. It's enabled in the bios. I have no idea where to go from here. Please help!

---

### Post by firegeek on 2010-09-23
This is not a "bump" a plea for help! Please help me find a solution to my Bluetoth issue. I'm thinking it's probably my like of knowledge of Unbuntu/Linux skills or the hardware is bad. I had it working and it disappeared. I refuse to be tethered to a cord. In fact and I hope this don't get me kick off this forum, but a $25 reward for a working solution to be paid via PayPal. Just give a fix and an address via private message and I will reward...I don't want to go backwards to MS.

---

### Post by bolojo on 2010-09-24
guys i have great news i finally solved my issue. The problem with no sound comming out of hdmi from the ion was that i hadn't had unmuted the all three spdifs that the alsa mixer but only one please check out this guide: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
Hope that helps

---

### Post by anjohan on 2010-09-26
> **firegeek said:**
> Where oh where did my Bluetooth go? The only thing I did was change the setting in the mb bios for the front audio jack from HD to AC7. My keyboard stopped working and I'm back to the point where it;s not seeing the Bluetooth adapter. I re-installed the driver as I did in the beginning > restart x 2 for both and to still not there. BTW--I used Debi Installer. I'm going back and change the bios setting--as I just thought about that this was the only change that was made.

Same problem here. I've tried everything I can think of. Still, the BT adapter is sometimes working, next time I am booting up the computer it is not. It is all very unreliable which makes me f*cked off wanting throw this box through the window and go back to my macbook.

Additionally, I cannot change the  remote mappings any longer. I have been able to do this before however after reinstalling Ubuntu from scratch I seam to be rebuilding the same module after changing the mappings.h file. Tried "sudo dpkg-reconfigure asus-at3iont-i-deluxe-dkms" and the manual rebuilding method described. No change.

Can anyone help, please?

---

### Post by firegeek on 2010-09-30
Wow! I've been digging around and cannot find any answers to my Bluetooth issue. Maybe Linux is just above me at this point. I hate to say that I just ordered (4) Win7 Pro licenses and pre-ordered a Boxee/D-Link box from Amazon. What will really suck if the next release of Unbuntu cures this issue or when I get Windows installed and find it to be a hardware issue. I guess I could pick up a Bluetooth usb dongle and see if this works.

---

### Post by firegeek on 2010-09-30
Wow! I've been digging around and cannot find any answers to my Bluetooth issue. Maybe Linux is just above me at this point. I hate to say that I just ordered (4) Win7 Pro licenses and pre-ordered a Boxee/D-Link box from Amazon. What will really suck if the next release of Unbuntu cures this issue or when I get Windows installed and find it to be a hardware issue. I guess I could pick up a Bluetooth usb dongle and see if this works.

---

### Post by Pwyll123 on 2010-09-30
Regarding Bluetooth adapter, I also had lots of issue with it. Sometimes it works, sometime it does not. I can see immediately when BT is working or not during boot: the Asus boot screen takes ages (10-15s) before Ubuntu starts from the HDD.

Finally I remembered I had a Linksys BT USB dongle, which I plugged in one the back USB port. I use since 3-4 weeks without any single trouble :)

I have disable the internal BT adapter, and my system boots in 10sec and BT is always working now ...

Pwyll

---

### Post by anjohan on 2010-09-30
Rite... IR keyboard and mouse it is then :(

Anyone got similar issues modifying the remote mappings as I described in my previous post?

---

### Post by vfacko on 2010-10-01
Hello,

I have purchased same board and have problems with bluetooth.

I have add required firmware ath3k but I can not even see the bluettoth in lsusb output.

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 002: ID 0471:206c Philips (or NXP)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 152e:1640 LG (HLDS)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


There should be Atheros....
I had it already working but then I was trying this magic wit remote control and since that I am not able to get bluettoth back working.

Thank you!

---

### Post by ychu on 2010-10-03
> **vfacko said:**
> Hello,

I have purchased same board and have problems with bluetooth.

I have add required firmware ath3k but I can not even see the bluettoth in lsusb output.

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 002: ID 0471:206c Philips (or NXP)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 152e:1640 LG (HLDS)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


There should be Atheros....
I had it already working but then I was trying this magic wit remote control and since that I am not able to get bluettoth back working.

Thank you!
My case is the same as vfacko's.
I am sure that I had enabled bluetooth in BIOS and I made the ath3k driver worked. But after I tried the IR solution, the bluetooth hardware disappeared in lsusb.

lsusb:
Bus 001 Device 003: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05af:3062 Jing-Mold Enterprise Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0471:206c Philips 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Can anyone give us a hand?

---

### Post by disparil on 2010-10-03
Hi all,

I started installing the XBMC Live CD 9.11 with this board, but not detected wifi neither bluetooth, so I installed Ubuntu 10.04. 
This version, found the wifi but no bluetooth, no IR, so I installed pj7 drivers, and everything worked for me OK. Later, installing LIRC, I unconfigure something, because when I reboot the wifi does not detected either the IR. 
After trying several times, I decided to install Mythbuntu because it appears to be  more prepared for HTPC, and the latest version detected my Wi-Fi, Bluetooth and IR (also lets you choose between several models of remote control) so it's a good base distribution for HTPC. Then I installed XBMC "standalone" (because i don't want MythTV) and I have it "almost" everything working.

Solved problems:
[LIST]
[*]The problem was with the sound over HDMI, since in Ubuntu I solved it unmuting the SPDIF in alsamixer, this is not enough in Mythbuntu  and you have to select the output you want to use, and being XFCE and not GNOME, no brings the application (Sound Preferences i think) to select the output (HDMI output), so I had to install several packages to make it (surely there are other way).

[*]Another problem is with nVidia, I have always to set the Overscan Compensation to fit the screen (my tv has a 1366x768 native resolution) as neither 1280x720 or 1920x1080, or 1366x768, nothing fits ... How hard is to get standard 720p or 1080i resolution with nVidia in Ubuntu?
[/LIST]

Almost solved problems:
[LIST]
[*]The return key on the remote, not does what it should on some screens of XBMC, but that's another story. I guess that this is solved mapping this key to another function.

[*]Make Mythbuntu boot directly to XBMC.
[/LIST]

In any case I recommend trying the Mythbuntu LiveCD to see if it detect everything correctly.

---

### Post by firegeek on 2010-10-04
I'm working a 24 hour shift that may turn into a 48 and cannot wait to get home and try the Mythbuntu distro. I hope this solves my Bluetooth issues--as I was really wanting to run Linux on this box.

---

### Post by firegeek on 2010-10-06
Decided to wait on the 10.10 release and see if this resolves my issue...

---

### Post by DrTebi on 2010-10-08
I have just finished the main work on my HTPC with the Asus AT3IOT-I (*not* the deluxe version), installed XBMC Live 9.11 and it all runs great.

I wonder about the temperature though; right now only the power supply has a fan, I don't have any other fans in the case (a former CD-Player case, very low profile with thick steel plates around it...), and after watching some movies for about an hour, the CPU was at around 135F and the Motherboard at 105F (about 41C and 57C).

Should I be concerned? I read that the maximum temperature this Atom processor can take is 80C. I have left a space for a 40mm fan that would blow across the 2.5" hard drive and motherboard, but I wonder if it's really necessary.

Another thing, how can I check the temperatures while XBMC is loaded? I tried to go to the console and use "sensors"--but it's not installed, and apt-get gave me a message that the sensors package cannot be found... no ports installed I guess... any help would be appreciated!

(attached a couple of pictures from my custom HTPC project)

---

### Post by pspreston on 2010-10-08
Hi

I have the ASUS AT310NT-I (NOT DELUXE) and I'm having a very hard time getting the Rosewill Remote to work.  See here for thread at XBMC.org [http://forum.xbmc.org/showthread.php?t=82693](http://forum.xbmc.org/showthread.php?t=82693)

The remote is this one from Newegg. [http://www.newegg.com/Product/Product.aspx?Item=N82E16880101002](http://www.newegg.com/Product/Product.aspx?Item=N82E16880101002)

I've installed lirc but when I test it with the irw command I get nothing back. I've tested the remote under windows 7 and it works fine. I've tested the usb ports with memory sticks and a mouse and they work fine.

Any ideas would be great... should i try the driver in this thread?

Please help.

---

### Post by Varazir on 2010-10-10
How do I add a program to a button ? 
I tried just add xbmc and spotify but it failed to reconfigure then 

//Daniel

---

### Post by frunns on 2010-10-12
> **DrTebi said:**
> I wonder about the temperature though; right now only the power supply has a fan, I don't have any other fans in the case (a former CD-Player case, very low profile with thick steel plates around it...), and after watching some movies for about an hour, the CPU was at around 135F and the Motherboard at 105F (about 41C and 57C).

I'd say you're really safe. The deluxe comes without a fan and in my cramped box it went up to 70C somewhere I think, and I think even a temperature that high is safe.

---

### Post by Ixzat on 2010-10-12
> **pj7 said:**
> 
Remote Configuration
You can change the default button mappings by editing the file mappings.h under drivers/hid-philips-asus subdir.
I tried to put some sane default mappings but you can change them as you like.
After editing you need to rebuild the module (step 3)

Note that the remote will operate as keyboard, so you don't really need lirc, if you map all buttons to normal keycodes.
For example  you can map the middle special button to KEY_M instead of KEY_MENU. This in XBMC will bring up the menu.
Personally I don't use lirc. I just put my key mappings in the remote, and then configured various programs that I use (xbmc, mythtv, vlc, mplayer etc) to use the same key shortcuts.


Is there someone willing to share a sane and working keymap.xml with this setup?

---

### Post by eiki2 on 2010-10-22
I try to install pj7´s asus-at3iont-i-deluxe-dkms_1.0.1_all.deb
but I get error;
dpkg-deb: unexpected end of file in version number in asus-at3iont-i-deluxe-dkms_1.0.1_all.deb

How can I download and compile this manually? I have kernel 2.6.32-25-generic

edit: Corrupt download! I redownloaded and everthing are fine now :-)

---

### Post by schaeffer on 2010-11-07
I have bought a TV card (PowerColor ATI Theater 600) with a Philips remote. 
A photo :

[IMG]http://hardware.am/Photo/Products/TVTuner/Other/PowerColor_ATI_TV_Wonder-600.jpg[/IMG]
This driver works perfectly on my openSUSE. So, how to remap this remote ? I want to configure numeric buttons like a numpad and the home button like backspace. I use this remote to control XBMC.
Volume, play, pause buttons work fine.
Thanks for your answers.

Sorry for my English language, I'm french.

---

### Post by jandom29 on 2010-11-10
I just buy this board ( ASUS AT3IONT-I ) and the poweroff does not work (whether by command or clicking on button poweroff) the power supply does not switch off. I install ubuntu 10.10 but i tried with 10.04 and i had the same problem. Is someone had the same problem and how can i solve it?

---

### Post by Varazir on 2010-11-10
> **jandom29 said:**
> I just buy this board ( ASUS AT3IONT-I ) and the poweroff does not work (whether by command or clicking on button poweroff) the power supply does not switch off. I install ubuntu 10.10 but i tried with 10.04 and i had the same problem. Is someone had the same problem and how can i solve it?

Dose the OS shutdown ? 
The led on the mother board and on the AC adapter is always on that's normal.

---

### Post by jandom29 on 2010-11-10
Yes, the OS  shutdowns, but the fan of PC and the fan of the power supply is working, and the screen of the monitor always displays the information of the poweroff (service stop [oK],...) on the splash image.
An other information : the poweroff does not work if the tuner card is plugged in the pci-e  slot. If this tuner card is un-plugged the poweroff works fine.

---

### Post by Varazir on 2010-11-10
> **jandom29 said:**
> Yes, the OS  shutdowns, but the fan of PC and the fan of the power supply is working, and the screen of the monitor always displays the information of the poweroff (service stop [oK],...) on the splash image.
An other information : the poweroff does not work if the tuner card is plugged in the pci-e  slot. If this tuner card is un-plugged the poweroff works fine.

You don't have the deluxe version. can you setup the mother board outside the chassis ? Could be something that is giving the system a feedback loop that is keeping running. 

or when the system  is shutting down remove the network/video cable

---

### Post by michael2690 on 2010-11-20
Hi, 

I have a problem with my power button. If I use this Command in the mappings.h file, It doesn't do anything: 
 
/* Power button */
#define BUTTON_POWER
                      "KEY_POWER"

But if i change The key to "KEY_END" it will suspend the device perfectly _but only if I am staying in the Home Menu_. 

I just want to turn off the device staying in any menu.


I am using xbmc live and suspend mode in xbmc.

Could someone please help me?


Thanx
Michael

---

### Post by Varazir on 2010-12-02
> **Varazir said:**
> How do I add a program to a button ? 
I tried just add xbmc and spotify but it failed to reconfigure then 

//Daniel

Anyone could give me a answer ? 

> **Ixzat said:**
> Is there someone willing to share a sane and working keymap.xml with this setup?

Yes I'm looking for a good file too.

---

### Post by BugMaster on 2010-12-05
> **sankukai93 said:**
> Hi,

PJ7, congratulations for this driver, it's great work!
All buttons on my remote are recognized with the command "evtest" but how to map keys with xbmc? do I have to use "evrouter? if so, how?

Otherwise, it is possible to adjust the key repeat (i would like more speed for volume + / -)?

Rauli, thank you for your link but I have not had time to look here! :)


Hi,

After a deep search for myself, I've finally success to repeat all remote key.

In the kernel module hid-philips-asus.c, I've redefine the macro like this:
```
#define pa_map_key(c)   set_bit(EV_REP, hi->input->evbit); \
                        field->flags &= ~HID_MAIN_ITEM_RELATIVE; \
                        hid_map_usage_clear(hi, usage, bit, max, EV_KEY, (c))

```It's the HID_MAIN_ITEM_RELATIVE, which is not correctly set, which control key repetition for all input event. Volume and other key (except left, right, ...) are not considered from keyboard so it does'nt  repeat.

Cheers,

---

### Post by JoePrima on 2010-12-13
thank you for this driver pj7, but I have some questions:

1. is it possible to have play and pause on one Button on the remote? My play button didn't work at all, so I configured it to KEY_P, which means it has only a play function, but no pause. Is there another way?
2. previous and next track buttons do not work. How do I have to set them up in my keyboard.xnl?
3. Do I have to set the remote as keyboard in the XBMC input device settings? (under system)

Most other buttons work well :)


PS: in ubuntu 10.10 the ath3k module is already included, so i get an errormessage. Bluetooth still works, but I wanted to metnion it.

---

### Post by JoePrima on 2010-12-14
Good. Spent a little time with it and everything works now! :)

---

### Post by JsARCLIGHT on 2010-12-16
Complete Linux/Ubuntu newbie here. I have an Asus AT3IONT-I Deluxe HTPC that I built out about eight months back. It has been running flawlessly with Win7 Home Premium 64bit and just on a lark I decided to blank that and try Ubuntu on it last night. The system has 4gb of ram but only has a small 40gig Intel X-25V SSD as its hard drive as I've been using it only to stream internet content (Hulu, Netflix, etc).

I read this thread at length as well as a few other threads at other places which all gave me the feeling this was going to be an easy install and setup... but I've hit a snag.

Ubuntu 10.10 64bit launches from the install DVD just fine, displays perfectly in 1080p and lets me install it. But when it comes to the first launch off the installed seat it fails to load every time. I see the Asus BIOS screen then it goes to a blank screen with a flashing prompt in the upper left corner and never loads any further. The screen keeps "popping" every few seconds which gives me the impression it is trying to initiate but it simply won't.

I see what I believe is this same problem -everywhere- in forums online. I see multiple supposed "fixes" but all of them seem to rely on you being able to hold shift or "e" and get into GRUB. Well, I can't get there. The blank screen with the flashing prompt responds to no keyboard entry except for ctrl-alt-del to reset. I'm using a USB dongle wireless keyboard but the BIOS sees it and works with it so I don't think it is causing any issues. I'm going to borrow a PS2 keyboard from my office tonight just in case.

If I reinsert the install DVD and F8 launch from it, it works just fine every single time... but it won't launch from the install and hangs 100% of all four attempts I've made.

Is this a 64 bit issue? Do I need to be installing 32 bit instead? Or is this still the nVidia video card driver issue? Could it be the SSD? Win7 64bit launched from it flawlessly, does Ubuntu have SSD related launch issues? 

Obviously tons of other people have this or a similar setup so Ubuntu obviously works with this motherboard, but darned if I can get it to launch.

---

### Post by wolfydRg on 2010-12-22
@JsARCLIGHT
I think that the your problem is the miss loading of boot sector.
Enter to the bios, go to boot option, select as first boot device your hard drive. Try to make some combination here.

My turn :D:

I request help to configure alsa sound to make analogic 5.1 out.
2.0 analogic and digital out works fine. But no success on 5.1 analogical out. A lite hint will be welcome.

---

### Post by JsARCLIGHT on 2010-12-22
I managed to get it to load finally by changing the SATA port the SSD was plugged into. Apparently the install was always failing to figure out where the hard drive was. For some reason it was looking for it in only one place. Turns out my hard drive was hooked into the SATA2 port instead of SATA1. Windows had no problem with this and the BIOS was even set to boot that drive first, but for some reason Ubuntu needed it plugged into SATA1...

---

### Post by wolfydRg on 2010-12-23
Finally i fixed the issue with 5.1 analog sound. Look what I did :

1)
I reinstalled ALSA at 1.0.23 like here :
-http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/

rebooted

2)
I added into /etc/modprobe.d/alsa-base.conf:
-"options snd-hda-intel model=3stack-6ch-dig" 

rebooted

3)
I set unmute in ALSA mixer and i increased the volumes for all devices.
And the most important setting in my opinion for analogic 5.1 it was: were is analog channels i founded set at 2 channels: with up arrow i changed at 6 channels.

4)
I set .asoundrc in user home directory and in xbmc (because i need use XBMC with 5.1 analog) directory (i don't know where is ok to be placed) like here:

        [INDENT]pcm.!default {
        type plug
        slave {
        pcm "both"
        }
        }

        pcm.both {
        type route
        slave {
        pcm multi
        channels 6
        }
        ttable.0.0 1.0
        ttable.1.1 1.0
        ttable.0.2 1.0
        ttable.1.3 1.0
        ttable.0.4 1.0
        ttable.1.5 1.0
        }

        pcm.multi {
        type multi
        slaves.a {
        pcm "tv"
        channels 2
        }
        slaves.b {
        pcm "receiver"
        channels 2
        }
        slaves.c {
        pcm "analog"
        channels 2
        }
        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1
        bindings.2.slave b
        bindings.2.channel 0
        bindings.3.slave b
        bindings.3.channel 1
        bindings.4.slave c
        bindings.4.channel 0
        bindings.5.slave c
        bindings.5.channel 1
        }

        pcm.tv {
        type hw
        card 0
        device 3
        channels 2
        }

        pcm.receiver {
        type hw
        card 0
        device 1
        channels 2
        }

        pcm.analog {
        type hw
        card 0
        device 0
        channels 2
        }[/INDENT]



6) I tested the outs:

sudo speaker-test

And miracle the sound is 5.1 ...

---

### Post by Zaptor on 2010-12-27
> **Ixzat said:**
> Is there someone willing to share a sane and working keymap.xml with this setup?

Same here, just got this system and i would really appreciate an xbmc keymap!

---

### Post by frank-w on 2011-01-17
Hi,
is it possible to define Keyboard-combinations for the remote-control?
e.g. ALT+F4 ?

btw. the right mapping for button_STOP is 
#define BUTTON_STOP   KEY_STOPCD

in this case smplayer knows stop-button as "Media Stop"

regards Frank

---

### Post by dekkelkamp on 2011-02-05
Below is the keymap i use with XBMC, put this in your /usr/src/asus-at3iont-i-deluxe-1.0.1/drivers/hid-philips-asus/mappings.h file and recompile the module.

```
/***************************************************
 * Button mappings
 *
 * Change the key values according to linux/input.h
 * and then rebuild the driver
 ***************************************************/

/* Power button */
#define BUTTON_POWER		KEY_POWER

/* Play, rewind, forward buttons */
#define BUTTON_REWIND		KEY_REWIND
#define BUTTON_PLAYPAUSE	KEY_PLAYPAUSE
#define BUTTON_FORWARD		KEY_FASTFORWARD

/* Previous, stop, next buttons */
#define BUTTON_PREVIOUS		KEY_PREVIOUSSONG
#define BUTTON_STOP		KEY_STOPCD
#define BUTTON_NEXT		KEY_NEXTSONG

/* Volume buttons */
#define BUTTON_MUTE		KEY_MUTE
#define BUTTON_VOLUMEUP		KEY_VOLUMEUP
#define BUTTON_VOLUMEDOWN	KEY_VOLUMEDOWN

/* Arrow buttons */
#define BUTTON_RIGHT		KEY_RIGHT
#define BUTTON_LEFT		KEY_LEFT
#define BUTTON_DOWN		KEY_DOWN
#define BUTTON_UP		KEY_UP

/* OK button */
#define BUTTON_OK		KEY_ENTER

/* Back button */
#define BUTTON_BACK		KEY_BACKSPACE

/* Special buttons from left to right counter clockwise*/
#define BUTTON_HOME		KEY_ESC
#define BUTTON_WINDOWS		KEY_C
#define BUTTON_RADIO		KEY_Q
#define BUTTON_MUSIC		KEY_I
#define BUTTON_DTS		KEY_L
#define BUTTON_TRANQUIL		KEY_S
#define BUTTON_FULLSCREEN	KEY_TAB

/* Middle special button */
#define BUTTON_HOMETHEATER	KEY_H
```

Some information about what the buttons functions are in XBMC:

The home button takes you to the home screen of XBMC
The button below the home button shows the popup menu (right mouse button)
The music button is used to show information
The DTS button is used to select subtitles
The sleep button brings up the shutdown menu of XBMC
The button below the 'back' button is used to switch between menu and a playing movie/music

All of the other buttons do what theyre supposed to do.

---

### Post by fabridelo on 2011-02-10
hello at all

I'm Fabrizio i have this Motherboard too.
I seek a solution like in the post 116 but i have optical cable on spdif .

Wolfydrg can you help me?

I use Xbmc and Vdr on Ubuntu 10.04

Thank

Sorry for my bad English

---

### Post by wolfydRg on 2011-02-11
I unable to "play" with my optical out, but i think that this will help you :

[http://forum.xbmc.org/showthread.php?t=68243](http://forum.xbmc.org/showthread.php?t=68243)

---

### Post by Twiggeh on 2011-03-09
Im about to buy the deluxe motherboard for my future seedbox/xbmc/ftp server, and im gonna plug it to my tv via HDMI, tho i want to use the RCA ports to send sound to my amplifier for smexier soundquality.

So, i just want to know if the hdmi port will "steal" all sound, or can i send audio through the rca ports while video gets sent through hdmi?

(and im not sure wether i'll use Ubuntu or Debian, but it shouldnt really matter regarding this question i suppose)

---

### Post by wolfydRg on 2011-04-08
Go for this motherboard. I use exclusively video on HDMI port and the sound is not stoled by HDMI. I am able to commute audio on analog/hdmi/digital out port.

---

### Post by allwise on 2011-08-04
I've recently upgraded Ubuntu to 11.04 (shouldn't have done that in first place...). The video in XBMC got laggy (but I've managed to fix that by enabling the classic desktop in Ubuntu) and also the remote stopped working. I've tried lots but cannot seem to solve it. If I run ```
sudo ./hid_mapper --list-devices
``` I get nothing in reply. If I run lsmod and connect and disconnect the USB-remote reciever nothing happen or if I press any buttons on the remote nothing happen either. 

Do anyone have any suggestions what to try? I've used linux for 10 years but I'm not very used in drivers and hardware...

Thanks! 

//A

---

### Post by allwise on 2011-08-04
> **allwise said:**
> I've recently upgraded Ubuntu to 11.04 (shouldn't have done that in first place...). The video in XBMC got laggy (but I've managed to fix that by enabling the classic desktop in Ubuntu) and also the remote stopped working. I've tried lots but cannot seem to solve it. If I run ```
sudo ./hid_mapper --list-devices
``` I get nothing in reply. If I run lsmod and connect and disconnect the USB-remote reciever nothing happen or if I press any buttons on the remote nothing happen either. 

Do anyone have any suggestions what to try? I've used linux for 10 years but I'm not very used in drivers and hardware...

Thanks! 

//A

Solved it! Have rebooted the computer at least 20 times since I upgraded I did it today again and also unplugged all USB-cables and replugged them and then it worked =) Silly error...

---

### Post by W. Irving on 2011-09-18
Am considering using this board in a HTPC build with XBMC or Showtime. Looks more appealing than Asus E35M1-I Deluxe thanks to VDPAU and lower TDP, in spite of the no doubt lower performance.

Only one question - how is Bluray playback? :)

---

### Post by daemonsx on 2012-06-27
> **BugMaster said:**
> Hi,

After a deep search for myself, I've finally success to repeat all remote key.

In the kernel module hid-philips-asus.c, I've redefine the macro like this:
```
#define pa_map_key(c)   set_bit(EV_REP, hi->input->evbit); \
                        field->flags &= ~HID_MAIN_ITEM_RELATIVE; \
                        hid_map_usage_clear(hi, usage, bit, max, EV_KEY, (c))

```It's the HID_MAIN_ITEM_RELATIVE, which is not correctly set, which control key repetition for all input event. Volume and other key (except left, right, ...) are not considered from keyboard so it does'nt  repeat.

Cheers,

excuse my blindness, but if i copy the mentioned lines into hid-philips-asus.c and recompile it again with:
sudo dpkg-reconfigure asus-at3iont-i-deluxe-dkms
nothing happened.

did i missed something? 
would be good to have repeat volume keys :)

Thanks in advance

---

### Post by rigo88 on 2012-08-31
hi
i install the xbmcbuntu and it doesnt recognises the factory remote-s "special" buttons. even if i look at the realtime report  tail -f /home/rigo/.xbmc/temp/xbmc.log
if i press them nothing happens.
if i press right left ...... its shown. but not the spec buttons.
i did the dpkg thing step by step but nothing.

---

