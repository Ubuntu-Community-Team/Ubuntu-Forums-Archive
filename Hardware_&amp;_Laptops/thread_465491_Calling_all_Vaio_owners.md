---
title: "Calling all Vaio owners"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by IntuitiveNipple on 2007-06-05
**[COLOR="RoyalBlue"]Sony Notebook Control[/COLOR]**

**Revised 23 April 2008**

Recently I've been working on **enabling Fn keys, screen dimmer, bluetooth and wireless LAN power, suspend/resume and VMX (VT)** on a Vaio VGN-FE41Z.

I've been working to develop a better understanding of how SNC works in order to develop a driver that supports 100% of the SNC functionality so Linux is on an equal footing with Windows.

The primary thrust of that work was to reverse-engineer the Windows driver. That has been done although there is a constant battle of catch-up as newer models appear. Unfortunately the way the SNC is handled isn't uniform across models or even BIOS versions so there needs to be some complicated code to ensure the Linux driver can handle all systems correctly.

**Collecting ACPI DSDT of every model**

For a while it looked like I didn't need any more ACPI DSDT tables collecting so I removed the instructions from this thread. However, it seems I was a bit hasty and so I'm reinstating the instructions now.

I need to collect the exact model numbers, BIOS versions, and ACPI DSDT (Differentiated System Description Table) from as many different Vaio models as possible (portables, not desktops, since we're mainly dealing with portable-specific issues).

The DSDT can change when BIOS versions change so please check the [Model-BIOS table](http://tjworld.net/snc/) I'm collating to see if your combination of model and BIOS version is already known. If it isn't in that list then please run the script attached to this posting and attach the file it creates to this thread.

**[color=green]Thanks to all the Vaio owners[/color]** that have already posted the DSDT. If you posted the DSDT of your model already can you please check that you used the correct format in the filename of the attachment since my automated tools can't deal with it if it doesn't have the format:

RANGE-MODEL-BIOS_VERSION.dsdt.tar.gz

e.g. VGN-FE41Z-R0200J3.dsdt.tar.gz

UPPERCASe is important since the filename is used in creating the HTML analysis tables. If your attachment didn't have that name format please use the script I've attached to this post to regenerate your report. Thank you.

**Script Instructions**

Download the script and save it to a convenient location. Change the permissions of the script so it is executable, and then run it using sudo so it has root permissions to install the dmidecode and acpidump packages, and so it can access /dev/mem to read the DMI and DSDT data:
```

$ chmod 755 snc-dsdt.sh
$ ls -l snc-dsdt.sh
-rwxr-xr-x 1 tj tj 903 2008-04-23 04:28 snc-dsdt

$ sudo ./snc-dsdt.sh
Checking and installing tools...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dmidecode is already the newest version.
acpidump is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Getting model information: Model: VGN-FE41Z, BIOS: R0200J3
Dumping the ACPI Differentiated System Description Table (DSDT)
Packing and compressing the DSDT...
All done, thank-you

If you want, you can now remove the acpidump and dmidecode packages using:
        sudo apt-get remove acpidump dmidecode

Please attach the file /tmp/VGN-FE41Z-R0200J3.dsdt.tar.gz to a new post in this Ubuntu forums thread:

http://ubuntuforums.org/showthread.php?t=465491

```

**Progress**

Since this article was first published asking for DSDTs great progress has been made. I now have a complete understanding of the way the ACPI devices are managed and probably more importantly, the way the Sony Windows SNC driver and utilities work. As a result my focus now is on reproducing the same functionality for Linux with no missing pieces or rough edges. I've not had the time or motivation to focus on it over the past few months but someone has recently re-engaged my interest and we're cooperating on getting a decent driver out the door.

The biggest challenge is writing the Vaio model-identification functions. It is complicated because Sony haven't maintained a consistent interface across models, and in some cases they have implemented different functionality under the same function-name - the only way to deal with that is for the driver to 'know' which model it is running and adjust accordingly. A complication is introduced because the code often makes calls into the Sony eXtended BIOS (SXBIOS) and being able to do that on 32-bit and 64-bit, and from within the kernel, presents difficulties.

Once this has been done the rest of the driver is pretty simply to implement (notifications to the input layer, etc.). I'm focused on delivering a driver that will work on Edgy, Feisty, Gutsy, Hardy, Intrepid and beyond (2.6.17+) from one code-base so no users who choose to stick with an older kernel or distro will loose out. 

There will be two user-space control applications - command line and Gnome applet. In addition there will likely be a supporting package of scripts for automating the handling of screen brightness, suspend, video-switching, and so on.

---

### Post by IntuitiveNipple on 2007-06-05
An alternative way to find your BIOS version without needing to reboot is:
```
$ sudo apt-get install dmidecode
$ sudo dmidecode -t bios

```

---

### Post by Bluecircle on 2007-06-05
**VGN-TX770PB-R0051V1**

As far as my laptop goes, everything is working except for the volume up/down buttons on the front. The mute button works, the brightness buttons, bluetooth and wireless LAN power, suspend/resume are all running great.

[VGN-TX770PB-R0051V1.tar.gz]("http://www.nointer.net/VGN-TX770PB-R0051V1.tar.gz")

Edit: I work at a computer store, so I'll grab whatever else I can get, but we mostly get emachines and dell stuff.

---

### Post by Migs on 2007-06-05
** I'm running Vista at this moment so i cannot go in depth as it goes on answering Linux Ubuntu specific questions but I am very curious and willing to help in any way.*

When running Edgy 6.10 a couple of month's ago I had problems that there was no DSDT detected. I have no knowledge if the ACPI dump utility can get the DSDT if it can't be found. But as I already stated running in Vista does not stop me to help :p

I have downloaded the windows version of the Intel ASL compiler and decompiled the DSDT in Vista. Hope it will help you, good luck!

---

### Post by am.pyka on 2007-06-06
On my vaio c1z/b there was no changes after doing that, no fn shortcuts functioning, in several previous installations of feisty in this laptop  the fn shortcuts to volume were ok, but at this time there are no fn shortcuts for nothing.... Can you help me?

---

### Post by Bluecircle on 2007-06-06
> **am.pyka said:**
> On my vaio c1z/b there was no changes after doing that, no fn shortcuts functioning, in several previous installations of feisty in this laptop  the fn shortcuts to volume were ok, but at this time there are no fn shortcuts for nothing.... Can you help me?

There shouldn't be any changes. All that does is dump your laptop's info into a file so he can look at it and find out how to fix it.

---

### Post by IntuitiveNipple on 2007-06-06
Wow! Thanks for responding so quickly. :)

Mattia has collected a few DSDTs which he sent over to me this morning. I shall be disassembling them to AML-style source code, isolating the Device (EC) and Device (SNC) parts and looking for commonalities and differences that will help us make the sony-laptop driver know how to configure more models.

Currently the sony-laptop driver module code is in the 2.6.22-rc4 kernel source but if it is possible I'll be wanting to ensure it is backward compatible to 2.6.20 for Feisty at a minimum.

---

### Post by buggybug on 2007-06-06
**PCG-K215S-R0110X1**

Hey guys!
I think it's neat what you're trying to do here!

Ok for my laptop, nothing works, except the WLAN-adapter, the FN keys don't work, nor does the memorystick slot work (but I don't know how far that can be managed) and suspend/resume... well it goes to hibernation but the resume is... well let's call it "black" ;)

hope to hear from you ;)

---

### Post by IntuitiveNipple on 2007-06-06
So that you can keep up-to-date and see how your contribution is helping I've put together a web page with tables generated by scripts to show the information we are gathering.

It'll change frequently as we add more models to the tables and start to be able to make firm conclusions.

Don't be too concerned if activity seems to have stopped; that'll mean we're hacking about with the drivers.  At some point we might ask people with particular models to test out versions of the driver for us.

[Sony Notebook Control, ACPI Method Analysis]("http://tjworld.net/sony-laptop/")

---

### Post by xenoph0be on 2007-06-06
Here's the DSDT file from a VGN-FE660G.  Purchased late summer 2006.  The mute button, vol up and down buttons work.  Currently the FN combos and 2 S buttons do not work... Hope this helps.  If I can give more info on my laptop that may help please let me know.

Jacob

---

### Post by spier on 2007-06-06
Here is a VGN FS740W. Everything works, almost out of the box! Just Fn keys had to be tweaked, following [this howto]("http://ubuntuforums.org/showthread.php?t=309533"), FS series specific.

---

### Post by fbmx24 on 2007-06-06
I have a VGN-AR320E  and everything except the brightness keys work. The volume worked right out of the box and the suspend worked after I did the kernel update for some reason.

---

### Post by kraftm on 2007-06-06
Sony SZ-120pc.  All FN and S1/S2 keys working properly.  Suspend / Hibernate crap out the system every time I try them (so I've given up).  The brightness settings in power management don't work at all.

Wireless worked right after installing 7.04, but the webcam and fingerprint reader don't work currently.  I haven't tried the memory stick port, but the SD Express card works.

Battery life is definitely not at the same level as WinXP.

Hopefully this helps.

Mark

---

### Post by tinaught on 2007-06-07
Hi. You may also find this page useful [http://gentoo-wiki.com/HARDWARE_Sony_VGN-S4](http://gentoo-wiki.com/HARDWARE_Sony_VGN-S4) for random solutions to the fn-key problems for various laptops.

I also attach a patch against sony-laptop.c (the one at [http://www.linux.it/~malattia/sony-laptop/](http://www.linux.it/~malattia/sony-laptop/)) that provides a ecdump method (the code is taken from ibm-acpi, with some bits commented out) that allows to read and write the memory of the EC. If you write it will give a write error, but it will write. By writing you may destroy-crash your laptop, so don't blame me. :p

I was trying to find a way to set different thresholds for the fan, but using it I didn't really find anything that wasn't already in the DSDT. The only 2 things for now are:

0x17 holds the address last written
0xc9 seems to be another temperature sensor. (as 0xc1, already used in ATF0)

Cheers,
Pietro (aka pieffe)

---

### Post by thewall83 on 2007-06-07
VGN-FE11H-R0074J3.dsdt

I hope you will find the way to get working the Fn keys.

Thanks!

---

### Post by fpooon on 2007-06-07
I have a VGN-FJ170 with Ubuntu 7.04 on it.  I just installed it today so I'm about halfway through piddling with everything to see if any of it works... but so far, no luck.  I've run the little shell script provided by Max Luebbe at [http://intentionallyobsolete.com/?p=23](http://intentionallyobsolete.com/?p=23) (edited for kernel version, of course), started the fsfn daemon and ran fsfn -o in X.  All I end up with are a bunch of defunct fsfn processes.  I'm a total loser. :KS

Manually echo'ing 1-8 into /proc/acpi/sony/brightness works, though.

John

---

### Post by Depressed Man on 2007-06-07
Have a VGN-FE880EH, FN keys worked after some tinkering with information on the forums (though only some of the FN keys work. S1 and S2 don't work, screen brightness can't be controlled thru keys or gnome power manager, hibernate/suspend doesn't work. 

Microphone doesn't work, webcam works after tinkering (though it shows the image in black and white). Card reader works.

---

### Post by whayong on 2007-06-08
PCG_SRX77.  As far as I can tell, most of the Fn keys work.  I can't get the external LCD/monitor to work though.  But that may just be a video card problem.  Oh yeah, I hope I did it right.

---

### Post by woodsmoke on 2007-06-08
HI
this is a new one to me....

I'm an immigrant from another distro....but I have a spankin new Vaio with Vista thereupon that I HAVE...to have for work...

I've got the latest Ubuntu Live CD...that's what I'm typing this on now...on a PIV.... but anyway...

I've run the live cd on the Vaio.....

I am familiar wih su but not with what I would do with a live cd, if you could possibly give me a quick step by step then I could post what info I can obtain.

woodsmoke

---

### Post by louistan3 on 2007-06-08
ive got a VGN-SZ28GP which i think has everything working... not sure about the SD card slot.. but like the one before me.. the fingerprint reader and webcam dont work..  all of the FN keys work perfectly..

---

### Post by ckarrie on 2007-06-08
Nice Work. Hope you get the FN Keys working.

---

### Post by frank58 on 2007-06-08
this is from my vaio vgn fe21 m

---

### Post by IntuitiveNipple on 2007-06-08
Thanks for all your DSDTs - and keep them coming!

The collection has grown to 28 now. I've spent some time writing automated scripts to process them and produce the analyse. You can start to see patterns in terms of which groups of models support particular functions. This should help us spot when a solution for one model-type will work on another model.

[Sony Notebook Control, ACPI Method Analysis]("http://tjworld.net/sony-laptop/")

---

### Post by forceflow2 on 2007-06-08
Here's the dump from my VGN-FE770G. Volume related keys work, but the Fn keys (with respect to triggering some sort of ACPI event or the like) and shortcut keys do not.

---

### Post by TrevorNC on 2007-06-09
Here is the information you requested for VGN-N230E. Thanks and good luck.

---

### Post by Tripmonkey_uk on 2007-06-09
Hi all..
Just added a post to the [Ubuntu-FS]("http://ubuntufs.wordpress.com/") site to let people know of this thread & I've tried to write an even [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") for new users to follow. Please let me know if it needs improving at all.

Just thinking that it might be a good idea if the Ubuntu devs add the acpidump software to the next Live CD. This would allow anyone to help out, regardless of the operating system they have installed. It's also a handy piece of software to have on a Live CD anyway ;)

Here's my contribution from a VGN-FS215E with the R0040J1 BIOS..
[ATTACH]34772[/ATTACH]
Good luck!

---

### Post by IntuitiveNipple on 2007-06-09
Thanks everyone, the collection of DSDTs is really helpful in gaining insights into the meaning of the cryptic ACPI method names. Mattia and me have been discussing how best to monitor/debug the ACPI handling, which is where the problem seems to be.

At the moment it looks as if things such as key-press notification events are either not being collected by the Embedded Controller (EC), or that when the kernel ACPI driver receives them from the EC it fails to forward them to the sony-laptop driver despite it having registered with the ACPI driver to receive event notifications.

At some point later next week I hope we can have a driver module built for generic Feisty kernels for you to install and test. I'll post a request for testers here when we do.

---

### Post by mdebrauw on 2007-06-09
I've got wireless lan working on VGN-FE41M. Hibernation works but very shaky. No bluetooth and camera sofar.

---

### Post by IntuitiveNipple on 2007-06-09
> **mdebrauw said:**
> I've got wireless lan working on VGN-FE41M. Hibernation works but very shaky. No bluetooth and camera sofar.
Your model is in the same range as mine (FE41Z). I got the bluetooth and camera working without a problem. See [my forum post in the Hardware Compatibility List]("http://ubuntuforums.org/showthread.php?p=2702973").

Are you using Feisty?

---

### Post by ngaio on 2007-06-09
Thank you.  My model is an VGN-SZ381P.  I'm definitely keen to see if you can enable the virtualization features for use by VMware that Sony etc. has not enabled in the bios!  I have no idea why they would sell a machine with an expensive CPU and then not enable all its features in the bios.

---

### Post by ectoon on 2007-06-09
**VGN-FS315H-R0080J1**

Hi , I just discovered this thread .
I am using ubuntu-studio on this laptop

dmesg is telling to me :

[   33.768000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   33.817000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 657)
[   33.865000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
[   33.949000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)

my fan is working all time , and the CPU is used too for nothing .

(PS:When i unplug the power cable and the laptop is working on the battery , the CPU is used
at 0% , but the fan continue to work all time.)

What do I have to do? :)

cheers,

---

### Post by b102 on 2007-06-09
**vgn-fs965f**

---

### Post by mdebrauw on 2007-06-09
> **IntuitiveNipple said:**
> Your model is in the same range as mine (FE41Z). I got the bluetooth and camera working without a problem. See [my forum post in the Hardware Compatibility List]("http://ubuntuforums.org/showthread.php?p=2702973").

Are you using Feisty?

Yep, using Feisty. Bluetooth indeed works now (was working all the time, hadn't looked into it yet). Looking at the camera now. Thanks for the tip!!

Mark

---

### Post by SergeiAB on 2007-06-09
Hallo! My vaio VGN-C240E/B, I installed fiesty kubuntu. brightness not working. I hope you will fix it soon. Thak You.

---

### Post by morphi on 2007-06-10
Most of the Keys and Camera works as expected, but the two S Keys do nothing. 

The strange and weird thing is that the Stamina / Speed Switch works not as expected, if you are in Speed mode you can change to Stamina, if you are in Stamina mode you can't switch to Speed, you can only change it on Windows.

Using Kubuntu Feisty

---

### Post by coffeecat on 2007-06-10
I notice you've already had the FS215E with the same bios as mine but, for what it's worth:

---

### Post by SendDerek on 2007-06-10
This is a great thread!  I love to see the community get together to try and solve a problem!  And seeing that it was updated only an hour ago gives me a lot of hope for a resolution!

Anyways, my dsdt.tar.gz is attached!

In Fiesty Fawn out of box:

**WORKS** 
[LIST]
[*]Sound Control (Mute, Up, Down)
[*]Touch Pad (Vertical scroll, etc.)
[*]Card Reader
[*]Firewire
[*]Wireless and Wired
[*]VGA Port
[/LIST]

**DOESN'T WORK**
[LIST]
[*]Hot Keys (F5 - Less Bright, F6 - More Bright, F7 - Monitor Out, F10 - Zoom, F12 - Hibernate)
[*]MS Pro Duo Card Reader in Front
[*]Brightness Control (Neither hot keys or Gnome Power Manager)
[*]Suspend/Hibernate is buggy and slow.
[*]MotionEye WebCam 
```
Bus 005 Device 004: ID 0ac8:c002 Z-Star Microelectronics Corp.
Bus 005 Device 003: ID 054c:0281 Sony Corp.
```
[/LIST]

And, just in case it helps, here is the output of the "dmesg | grep sonypi" command:
```

[   21.776000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   21.776000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   21.776000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   21.776000] sonypi: device allocated minor is 63
[   21.880000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   21.920000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 657)
[   21.964000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
[   22.004000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)

```

---

### Post by samir85 on 2007-06-10
Here are the information about my VGN-FE11H laptop. (btw: I think I updated my Bios over the Sony update tool once.)

---

### Post by bazoo on 2007-06-10
I look forward to this stuff working.

---

### Post by G2k on 2007-06-10
Great idea!! I completely support you guys :p
Sony Vaio VGN-FS660/W

None of my FN keys work out of the box with a clean Feisty install. My S1 and S2 keys do nothing. The rest looks sexy.

---

### Post by heldmar on 2007-06-10
Hi, I posting here my VGN-FS730W so I can contribute with the investigation. 

I can say that my S1/S2 keys are not working, neither is my FN key. And the thing that makes more angry is my Memory Stick reader which is not working neither.

I hope we can make them work by any method.

Many thanks.

---

### Post by NikoC on 2007-06-11
Following file is from a sony vaio VGN-S4HP/B. Functions keys s1, s2, and Fn+F7 (switch to external monitor) are not working neither are hibernate or suspend (suspend leaves me with a black screen on resume, ctrl + alt + f1 gets me to CLI from which I can restart Gnome; hibernate does not function at all, i.e. I get no reaction when I choose hibernate). Other function keys for sound (e.g. Fn + F2) and brightness are working fine.

Edit: Running Feisty Fawn

---

### Post by thitux on 2007-06-11
Hello,

Following file is from a **sony vaio VGN-C2Z/B**. 
- FN Keys are working for sound only
- Suspend or hibernate doesn't work at all
- brightness **can not **be set by writing to /proc/acpi/sony/brightness
- bluetooth led stay on, even if bluetooth itself seemes to be off using this command : *sudo hciconfig hci0 down*

Hope it helps !

Thieffen

---

### Post by robbster on 2007-06-11
Great Thread! I just found it... :-) 

Model: (another) **VGN-FE11H**

**WORKING:**
[LIST]
[*]sound control: Mute button and (+) (-) buttons worked out of the box.
[*]touchpad
[*]WLAN and wired
[*]video (GeForce Go 7400) - I only got it working with the nVidia installer
[*]suspension
[*]Numlock, Win-Key, F-Keys etc. work fine
[/LIST]

**NOT WORKING**
[LIST]
[*]MS Pro Duo card reader
[*]brightness control (but it works fine with smartdimmer out of the box)
[*]hibernation: can't wake it up any more after hibernating
[*]FN Keys
[/LIST]

**NOT TESTED YET**
[LIST]
[*]IEEE1394
[*]TV-out
[*]VGA-out
[/LIST]

The FE11 is equipped with S1 and S2 buttons (which do NOT work). There are the following **FN-Keys combinations**: 
F5: brightness-- (not working)
F6: brightness++ (not working)
F7: Monitor output selection (not working)
F10: Zoom (not working)
F12: Hibernate (...neither)
NUM: scroll lock (**working**, but the LED doesn't light up when activated)
insert: pause (? - not yet needed)
del: break (german: "unterbrechen") (? - not yet needed)

edit: pause and break DO work, I tried it with 'xev'. These Keys are beeing recognized whereas the others are not as descirbed.

---

### Post by ASIL007 on 2007-06-12
Posting for a VAIO PCG-K15. Thanks for the initiative!

---

### Post by Bluecircle on 2007-06-12
Just to let you know, since my first post I've upgraded to Gutsy and now the brightness keys do not work. So the sound up/down and brightness up/down keys don't work now.

(VGN-TX770P)

---

### Post by SteveRichards on 2007-06-13
**VGN-SZ330PB-R0094N0**

I'm running OpenSuSE 10.2...
 I would especially like the FN7 switch to external display to work as I keep the laptop remote and just use the external display. Unfortunately the display is black until X starts and I can never see boot messages.

Also would like to get VT (vmx mode) enabled.

Thanks

---

### Post by rsain on 2007-06-13
I'll post the info for my VGNs360 if I can get some assistance in this thread for install problems:

[http://ubuntuforums.org/showthread.php?t=471983](http://ubuntuforums.org/showthread.php?t=471983)

- Ryan

---

### Post by slab on 2007-06-13
Vaio S150, purchased Summer 2004, had a whole mess of hardware problems since. (The motherboard's been replaced twice!) It's running Feisty, with kernel 2.6.20-16-generic.

I haven't used the keyboard much recently; I mostly use it with an external keyboard and monitor. Brightness, suspend (Fn-Esc), and volume keys all seem to work fine. When I used Debian, I used to use Fn-S/D/F to control mpd via a daemon listening on the sonypi device. Lid close causes the screensaver to activate (kinda annoying with an external monitor, but whatever).

I've never tried the actual Bluetooth module for this laptop; one exists for this model, but since it costs about a hundred dollars (since I have to get it from Sony), I never bothered to get it. Replacing the modem card with a combo modem/BT card pulled from another laptop left me with no way to enable the BT. Sigh.

I've never used the Memorystick reader, but the tifm_7xx1 driver seems to recognize it.

I'm not sure if you've seen this already, but I expect that all of the models listed here are going to be very similar: [http://www.edepot.com/reviews_sony_vaio_s.html](http://www.edepot.com/reviews_sony_vaio_s.html)

---

### Post by cremone on 2007-06-13
**VGN_FS-115M**

Everything worked fine with fsfn since the upgrade to feisty in march, then i had to thinker a little and got it working again.

Now since last kernel update it's not working anymore (that's why i noticed this post on the forums) and indeed theres no fnkey entry under /proc/acpi/sony.

It's getting quite tiresome.

---

### Post by giuseppe.dem on 2007-06-15
This is the dsdt file for VGN-FJ91S
Any fn key is not working.
IN particular I need the dual screen mode.
G

---

### Post by giuseppe.dem on 2007-06-15
The file...

---

### Post by nithrandil on 2007-06-16
here you are

---

### Post by IntuitiveNipple on 2007-06-16
Thanks for the new DSDTs.

---

### Post by IntuitiveNipple on 2007-06-16
Whilst hacking the DSDTs of various laptops I've discovered what appears to be a bug in the Sony DSDT relating to the battery.

In the battery device's _BIF() method (get Battery Information) I found that there is a hard-coded value for battery_technology which causes ACPI to say the battery technology is ***non-rechargeable***. The value is hard-code as 0 (Zero) whereas it should be 1 (One).

```
  Method (_BIF, 0, NotSerialized)	// get Battery InFormation
  {
   Name (MULV, Zero)
   Name (BATI, Package (0x0D)
   {
        Zero, 			// power_unit
        0x2710, 		// design_capacity
        0x2710, 		// last_full_capacity
        Zero, 			// battery_technology
        Ones, 			// design_voltage
        0x03E8, 		// design_capacity_warning
        0x0190, 		// design_capacity_low
        0x64, 			// battery_capacity_granularity_1
        0x64, 			// battery_capacity_granularity_2
        "", 			// model_number
        "", 			// serial_number
        "LiOn", 			// battery_type
        "Sony Corp."		// oem_info
   })
```
The ACPI specification v3.0 says:
> Battery Technology DWORD
 0x00000000 &#8211; Primary (for example, non-rechargeable)
 0x00000001 &#8211; Secondary (for example, rechargeable)

As a result ACPI will report "**battery technology: non-rechargeable**":
```
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         57720 mWh
last full capacity:      57720 mWh
battery technology:      non-rechargeable
design voltage:          118530 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
```
I've tested the installation of a corrected DSDT and it solves this issue.
```
$ cat /proc/acpi/battery/*/info
present:                 yes
design capacity:         57720 mWh
last full capacity:      57720 mWh
battery technology:      rechargeable
design voltage:          125460 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
```
I've scanned all the DSDTs I've received so far and every single one reports BATI.battery_technology == 0. It is possible something has recently changed in the Linux ACPI battery-handling to cause this "non-rechargeable" report because I'm pretty sure it was okay before the latest Feisty kernel upgrade.

I'd be interested in other Vaio users posting their Vaio model number and BIOS version,  OS version, and ACPI battery results. These commands will get the ACPI battery technlogy and BIOS version (you may need to install dmidecode with 'sudo apt-get install dmidecode'):
```
$ uname -a
$ cat /proc/acpi/battery/BAT0/info | grep 'battery technology'
$ sudo dmidecode | grep 'Version: R'

```
I've detailed the issue and the solution in the thread [ACPI: battery-technology reported as non-rechargeable](http://ubuntuforums.org/showthread.php?t=475801)

---

### Post by merlockmagus on 2007-06-17
Here's my DSDT for my VGN-S660P Vaio. Hope it helps.

---

### Post by Dseed on 2007-06-17
Sony VAIO VGN-N130G-R0020J4

Linux river-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

battery technology:      non-rechargeable

here is my DSDT file you requested.

Peace!

---

### Post by Necrome on 2007-06-17
Hello,

I have posted this on one of the sticky topics above but had no reply. Can anyone help me out?

Thanks..

> Hi there,

I have not been able to find any info if Feisty works fine with Sony Vaio VGN-TX3XP. Does anone know? The graphics card (Mobile intel 945GM Express Chipset Family) gave me a lot of problems with Fedora Core 6.

Thanks in advance.. (Sorry if this is the wrong place to post this question)

---

### Post by Migs on 2007-06-17
> **IntuitiveNipple said:**
> Whilst hacking the DSDTs of various laptops I've discovered what appears to be a bug in the Sony DSDT relating to the battery.

[...]


Good Job! The battery bug is quite obvious if you know where to look for, but still all your work is quite amazing for what you have done already =D>

What I like to know if we can help you with something, like testing or sorting out key functions.

Ps. because of you i am going to kick Vista of my Vaio and install Ubuntu on it again :D

> 
Necrome  	Hello,

I have posted this on one of the sticky topics above but had no reply. Can anyone help me out?

Thanks..

Quote:[quote]
Hi there,

I have not been able to find any info if Feisty works fine with Sony Vaio VGN-TX3XP. Does anone know? The graphics card (Mobile intel 945GM Express Chipset Family) gave me a lot of problems with Fedora Core 6.

Thanks in advance.. (Sorry if this is the wrong place to post this question)[/quote]
This is not the right topic for it... but did you look at the wiki's? Using google i found some usefull information:

[http://www.oiepoie.nl/linux_on_d620/](http://www.oiepoie.nl/linux_on_d620/) 

It's for a dell latidude but is has the same video chipset. Using 915 resolution fix and the i810 driver should help you out.

---

### Post by Necrome on 2007-06-17
Hey Migs,

Thanks a lot for your help. I have been looking around for the right place to post it but couldn't find where. Anyway, thanks again.

---

### Post by IntuitiveNipple on 2007-06-17
> **Migs said:**
> Good Job! The battery bug is quite obvious if you know where to look for, but still all your work is quite amazing for what you have done already =D>

What I like to know if we can help you with something, like testing or sorting out key functions.

There will be shortly. I'm hoping we will soon be able to put together a development-test version of sony-laptop with new functionality and debugging code that will help us analyse the results of our efforts here.

Mattia is the #1 man when it comes to the sony-laptop driver, he's been doing it quite a while. I'm getting up to speed with it quickly by collecting, analysing, and playing with the ACPI DSDT data collected here.

I've done kernel-hacking before so that side is not a problem; the issue here is to understand what each of the Sony SNC and EC methods does, look at how the custom Sony Utilities in Windows uses them, and from that create fresh code for Linux to provide the same or better functionality.

To make it easy to manage all the functions from one place I'm writing a Gnome panel applet that will gather all the functions into one tabbed-dialog. That should make it easy for Vaio users to get the most of the functionality. I'll be needing user feedback and usability testing for this too.

For example, in Vista Sony Programmable keys doesn't offer many options for what you want the S1 S2 keys to do. With the help of the Gnome panel applet we should be able to allow the user to assign any function, program, or shell script to the keys using the standard Linux programmable-key support.

I'm also working on a separate kernel module to enable VMX (Virtualisation) on the Intel CPUs. This requires me to decompress the BIOS files of every Vaio to analyse the modules and trace the machine-code to see *where* in NVRAM each stores the flag that indicates VMX should be enabled so that it can use BIOS ESCD read/write functionality to read the data, set the flag in the correct location, and write the data back to NVRAM.

Potentially  vmx-enable will need to know where every model & BIOS combination stores that information, although from what I've seen so far it is a standard part of the Phoenix BIOS modulised code that Sony use.

vmx-enable will only need to be run once to set/reset the flag after BIOS updates or NVRAM is cleared. The Sony/Phoenix BIOS will do the actual enabling every time the system boots just as if the Sony setup menu had the option available.

```
Ps. because of you i am going to kick Vista of my Vaio and install Ubuntu on it again :D
```
Uh-oh! I've left Vista in a reduced 27GB partition. Once VMX is enabled it will be possible to run Vista from the disk as a guest OS with Ubuntu GNU/Linux as the host OS :)

---

### Post by NavS on 2007-06-17
Here I did this.

---

### Post by benhelfman@hotmail.com on 2007-06-17
I can't get Ubuntu to install on my Sony Vaio VGN-SZ220.  I get the following error message and then the system hangs

Uncomopressing Linux ... Ok, booting the kernel.
[17175570, 448000] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

Any help?

Ben Helfman

---

### Post by anchois on 2007-06-18
Hello all,

here is the dump of My Vaio FS315E.

- FN keys are all working fine (volume, brightness, vga out, S1 and S2)
- Hibernation and suspend are working also (not when I suspend or hibernate twice without powering off/on, but it's ok)
- Wifi is working also (but not the soft switch on the front side of the laptop, doesn't seem to do any keyboard or acpi interrupt)

I have to boot with the kernel options ***noapic nolapic*** in order to have a decent boot time and I have those message in /var/log/messages:

```
ACPI Exception (acpi_battery-0207): AE_NOT_FOUND, Evaluating _BST [20060707]
```

---

### Post by IntuitiveNipple on 2007-06-18
> **anchois said:**
> I have to boot with the kernel options ***noapic nolapic*** in order to have a decent boot time...
Do you recall what the original problem was that required the APICs to be disabled?

---

### Post by qfingers on 2007-06-18
I'm really a gentoo guy and want to see it work for all distributions.  But I used kubuntu for my initial install and it worked great.  I prefer more control so I use gentoo.  Here are a couple of links I used to get stuff working.

For the MotionEye: [http://lsb.blogdns.net/ry5u870](http://lsb.blogdns.net/ry5u870)
For the WIFI interface: [http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)

Fn+X keys don't work
S1 & S2, Eject, Channel -, Channel +, TV Rec, AV Mode keys don't work

My unit also came with a TV tuner with mpeg encoder and a ATSC USB AVer Media Volar Card.  There is driver suport in 2.6.22 but it's too new and the ipw3945 driver won't compile against it.

Hope this helps someone.

q

---

### Post by SergeiAB on 2007-06-19
IntuitiveNipple!   

(You have my DSDT Vaio VGN-C240E/B)

Hmmm... i did your battery hacking. 
1. Yes it was - "battery technology:      non-rechargeable"
2. After it is "battery technology:      rechargeable"
BUT
Befor it, the time, showing by powersave, was near reasonable, about - 3h.
Now it is funny - it showing time from 30h to 30min in tha same charging percent.
Have you any ideas?

I installed a sony_acpi. ([http://popies.net/sonypi/sony_acpi.tar.gz](http://popies.net/sonypi/sony_acpi.tar.gz)) 
It should be a 3 files after start this program in /proc/acpi/sony/ directory, but i have 2 onely, the file fnkeys missing.
But i can change brightness by command line, like it described in sony_acpi.txt.
(# echo "1" > /proc/acpi/sony/brightness
# echo "8" > /proc/acpi/sony/brightness)
It works.

May be it will help you.
GOOD LUCK!

---

### Post by ngaio on 2007-06-19
Linux dlynch3 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
battery technology:      non-rechargeable
Version: R0096N0

VGN-SZ381P

New bios revision attached.  Previous bios was submitted by me already: VGN-SZ381P-R0094N0.dsdt.tar.gz

---

### Post by ngaio on 2007-06-19
BTW I'm not sure if this is the appropriate place in which to mention this, but it seems to me there is a bug the BIOS of the VGN-SZ381P.  Using BIOS R0094N0, and BIOS R0096N0, the BIOS fails to assign a proper interrupt to a 32 bit PC Card (cardbus) with three IEEE1394 ports.  Linux reports a failure to be able to use an interrupt as soon as an external hard drive is powered on.  I have tried two different models of brand new PC Cards (one powered by Texas Instruments, and another powered by VIA) and they both fail to operate.  (It also fails in Vista, with a code 12, which is the same problem).  I've let Sony know via technical support.  I don't know if a workaround can be easily developed should Sony not act on the bug.

---

### Post by IntuitiveNipple on 2007-06-19
> **SergeiAB said:**
> I
Hmmm... i did your battery hacking. 
1. Yes it was - "battery technology:      non-rechargeable"
2. After it is "battery technology:      rechargeable"
BUT
Befor it, the time, showing by powersave, was near reasonable, about - 3h.
Now it is funny - it showing time from 30h to 30min in tha same charging percent.
Have you any ideas?
Are you using Feisty and kernel 2.6.20-16?  Many people have reported erratic battery reporting in this upgrade. I see it occasionally if the battery hasn't done a full discharge/charge cycle but the actual data coming from the battery *appears* to be correct.

---

### Post by IntuitiveNipple on 2007-06-19
> **ngaio said:**
> ...it seems to me there is a bug the BIOS of the VGN-SZ381P.  Using BIOS R0094N0, and BIOS R0096N0, the BIOS fails to assign a proper interrupt to a 32 bit PC Card (cardbus) with three IEEE1394 ports.  Linux reports a failure to be able to use an interrupt as soon as an external hard drive is powered on. 

I don't know if a workaround can be easily developed should Sony not act on the bug.
It is possible to alter the DSDT to tell the OS what resources to allocate. My suggestion would be to identify another model with the same internal hardware for Card Bus but with a different BIOS series (the last 2 digits of the BIOS version, e.g. J1 instead of N0).

You could then compare the decompiled DSDT of each and see if there is something the 'good' BIOS does that the N0 BIOS is forgetting to do when configuring the PC Card interface/bus.

---

### Post by SergeiAB on 2007-06-19
> **IntuitiveNipple said:**
> Are you using Feisty and kernel 2.6.20-16?  Many people have reported erratic battery reporting in this upgrade. I see it occasionally if the battery hasn't done a full discharge/charge cycle but the actual data coming from the battery *appears* to be correct.
Yes it is. Fiesty and kernel 2.6.20-16. But i upgraded immediately after Fiesty insallation...

---

### Post by xenoph0be on 2007-06-19
I have noticed a few posts to this thread mentioning that the gnome-power-manager does not change the brightness of the LCD.  Please see [this thread]("http://ubuntuforums.org/showthread.php?p=2877962#post2877962") for instructions on how to get the power manager to change the brightness.

[http://ubuntuforums.org/showthread.php?p=2877962#post2877962]("http://ubuntuforums.org/showthread.php?p=2877962#post2877962")

Jacob

---

### Post by IntuitiveNipple on 2007-06-19
> **xenoph0be said:**
> I have noticed a few posts to this thread mentioning that the gnome-power-manager does not change the brightness of the LCD.  Please see [this thread]("http://ubuntuforums.org/showthread.php?p=2877962#post2877962") for instructions on how to get the power manager to change the brightness.

[http://ubuntuforums.org/showthread.php?p=2877962#post2877962]("http://ubuntuforums.org/showthread.php?p=2877962#post2877962")

Jacob
Some Vaio's have Nvidia video chip-sets, in which case the 'standard' brightness controls don't work (they're for the Intel video chip-sets). I wrote a [Gnome panel applet](http://ubuntuforums.org/showthread.php?t=451781) to work with smartdimmer, one of the utilities (the other being nvclock) that can adjust brightness for Nvidia chip-sets.

---

### Post by xenoph0be on 2007-06-19
> **IntuitiveNipple said:**
> Some Vaio's have Nvidia video chip-sets, in which case the 'standard' brightness controls don't work (they're for the Intel video chip-sets). I wrote a [Gnome panel applet](http://ubuntuforums.org/showthread.php?t=451781) to work with smartdimmer, one of the utilities (the other being nvclock) that can adjust brightness for Nvidia chip-sets.

Thanks for the heads up.  I will edit my posts to reflect the information.

---

### Post by SergeiAB on 2007-06-20
> **xenoph0be said:**
> I have noticed a few posts to this thread mentioning that the gnome-power-manager does not change the brightness of the LCD.  Please see [this thread]("http://ubuntuforums.org/showthread.php?p=2877962#post2877962") for instructions on how to get the power manager to change the brightness.

[http://ubuntuforums.org/showthread.php?p=2877962#post2877962]("http://ubuntuforums.org/showthread.php?p=2877962#post2877962")

Jacob
Yes it works!!! on my  VGN-C240E/B, Ubuntu Feisty 2.6.20-16 with KDE.
Thank You!!!

---

### Post by gregorygreg on 2007-06-20
here is sony fe series 590P

---

### Post by nebulus-design on 2007-06-20
Here is my stuff from a fresh out of the box sz4xwn

Following many links almost everything is working (including motion eye, but I need to reboot into vista (yuk) to get it to work, but since is flawless), FN+X works for audio and screen brightness.

Not working:

Integrated memory card reader (though tifm_core spots insertion in dmesg)

Not Investigated:

fingerprint scanner and battery acpi stuff (not sure if it is an issue on this machine)


Keep up the great work!

---

### Post by IntuitiveNipple on 2007-06-20
> **nebulus-design said:**
> Integrated memory card reader (though tifm_core spots insertion in dmesg)
If it is a MemoryStick slot as on my FE41Z then, as I mentioned in another thread,  [you won't be able to use it yet](http://ubuntuforums.org/showthread.php?p=2870057#post2870057).

---

### Post by Migs on 2007-06-20
> **IntuitiveNipple said:**
> If it is a MemoryStick slot as on my FE41Z then, as I mentioned in another thread,  [you won't be able to use it yet](http://ubuntuforums.org/showthread.php?p=2870057#post2870057).

Eh.. I am a little confused.

Are we talking about the build-in memory stick Duo/Pro reader or are we talking about the pci-express 5in1 card known as VGP-MCA20? The VGP-MCA20 works here out of the box without any problems.

More info: [http://www.qbik.ch/usb/devices/showdev.php?id=3698](http://www.qbik.ch/usb/devices/showdev.php?id=3698)

---

### Post by IntuitiveNipple on 2007-06-20
> **Migs said:**
> Eh.. I am a little confused.

Are we talking about the build-in memory stick Duo/Pro reader or are we talking about the pci-express 5in1 card known as VGP-MCA20?
***nebulus-design*** said it was the internal slot with tifm_core, which is what I was referring to.

The VGP-MCA20 5-in-1 ExpressCard/34 adaptor uses the standard kernel usb driver.

---

### Post by roeltje25 on 2007-06-21
Here is the DSDT for the VAIO VGN-AR31S. It is a european model as far as I know. Have fun, and thanks!!!

---

### Post by john_spiral on 2007-06-21
Would info from a 6 year old Vaio **PCG-141c** be of any use?

---

### Post by d3x7r0 on 2007-06-21
here it is my dump from my [Sony Vaio VGN-C2S/H](www.nonsensebb.com/VGN-C2S-R0080J4.tar.gz).

---

### Post by wvengen on 2007-06-22
Here's the DSDT for the Sony VAIO VGN-FE41E; see also [https://wiki.ubuntu.com/LaptopTestingTeam/SonyVGN-FE41E](https://wiki.ubuntu.com/LaptopTestingTeam/SonyVGN-FE41E)

---

### Post by IntuitiveNipple on 2007-06-22
**Update**

You'll be please to know we've got a handle on how to detect the Fn+xx keys now, It shouldn't be long before there is an initial release of an updated sony-laptop kernel module for testing.

We're also making progress on identifying how all the other custom-hardware functionality is handled. This is partly through intelligent analysis of the decompiled ACPI code in the DSDTs you are providing, and partly from analysing what the Windows utilities, SnyUtil.dll, and SnyNC.sys do.

---

### Post by CheeseEatingBulldog on 2007-06-22
I have installed two Vaios with Feisty, one which is mine (see sig) and the other is my GF's which is a larger model. Never had suspend/hibernate work, but the rest pretty much does (including FN keys).

---

### Post by joe_steeve on 2007-06-22
I'm not quite sure whether this has already been submitted. But still.. :D Here is the dsdt for my vgn-c22gh.

---

### Post by purple melon on 2007-06-22
Hi hope this helps as I have not yet managed to get any of the Fn keys working on my PCG-K115B, cheers

---

### Post by jpryor68 on 2007-06-23
Here's mine.

---

### Post by tmaus on 2007-06-23
hope this one helps as well

greetings and thanks from berlin

---

### Post by gnocci on 2007-06-23
Great work!

Here comes a rare one, the VGN-C140G (sometimes known as PCG-6P2L ?), running Feisty.

Works:
Volume and mute from Fn keys
5in1 PCI reader
Video&WiFi

Doesn't work:
Brightness (FIXED with [this]("http://ubuntuforums.org/showthread.php?p=2899582"), but still no trough Fn keys)
Hibernate/Suspend
MemoryStick Pro reader.


from dmesg | grep sonypi i get

> [   25.460000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   25.460000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   25.460000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   25.460000] sonypi: device allocated minor is 63
[   25.552000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   25.588000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 657)
[   25.628000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
[   25.668000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)


---

### Post by benivilch on 2007-06-24
here's mine sony vaio VGN-FE870E

---

### Post by tom613 on 2007-06-24
Hello,

I own a VAIO VGN-FE31M and would like to use all the functions... (especially the FN-Keys!!!).
S1/S2 and FN-Keys don't work at all...I really need the monitor out option...(so I don't have to use Winblows)
I haven't tested the memory-stick reader.

Thanks for the hard work!

---

### Post by mossmann on 2007-06-25
DSDT for SZ450 attached.  Thanks for working on this!  I've just started with my SZ450 and am documenting my progress at [http://ossmann.com/mike/laptop/sz450.html]("http://ossmann.com/mike/laptop/sz450.html").

So far, I have had neither sonypi nor sony_laptop in my kernel.  I am lacking screen brightness control, I haven't had any luck with the S1 and S2 buttons, and the Fn combinations do nothing (except FnF2, FnF3, and FnF4 give interesting key codes).  I'm about to try 2.6.22-rc5 with CONFIG_SONY_LAPTOP.  Thanks again!

---

### Post by technomaniac on 2007-06-25
I have a [COLOR="Red"][SIZE="5"]Sony Vaio VGN c15[/SIZE][/COLOR]. It has I[COLOR="Red"][SIZE="5"]ntel Pro Wireless 3945 [/SIZE][/COLOR]on board. EarlierI had installed ubuntu without any problem but now I am getting a strange problem. I have installed Ubuntu with the restricted drivers(for Intel Pro Wirelss) but it refuses to boot.I have been able to boot only once. The [COLOR="Red"][SIZE="5"]problem seems to be related to the IPW 3945.[/SIZE][/COLOR] I have a switch to turn off Wireless. Now when the boot freezes I switch off wireless I get a message [COLOR="Red"][SIZE="6"]"Radio Frequency kill switch is on[/SIZE][/COLOR]". And thats it. Booting does not continue any further. What do I do? I want to run Ubuntu on my system.

---

### Post by Migs on 2007-06-25
> **technomaniac said:**
> I have a [COLOR="Red"][SIZE="1"]Sony Vaio VGN c15[/SIZE][/COLOR]. It has I[COLOR="Red"][SIZE="1"]ntel Pro Wireless 3945 [/SIZE][/COLOR]on board. EarlierI had installed ubuntu without any problem but now I am getting a strange problem. I have installed Ubuntu with the restricted drivers(for Intel Pro Wirelss) but it refuses to boot.I have been able to boot only once. The [COLOR="Red"][SIZE="1"]problem seems to be related to the IPW 3945.[/SIZE][/COLOR] I have a switch to turn off Wireless. Now when the boot freezes I switch off wireless I get a message [COLOR="Red"][SIZE="1"]"Radio Frequency kill switch is on[/SIZE][/COLOR]". And thats it. Booting does not continue any further. What do I do? I want to run Ubuntu on my system.

Could you please remove those caps! It's makes this topic much less readable...

---

### Post by mitkaese on 2007-06-25
Hey, thanks for this great work toward having a fully useful Ubuntu laptop!

Vaio VGN-FE670G.  No luck with brightness controls (or any changes such as CPU speed when running on batter), no FN keys, and both suspend/hybernate fail to wake up.  I have no experiences with the memory stick.

Also, not sure if it's included in the plan, but MotionEye camera is also SOL.

again, thanks!

---

### Post by Gerhard1979 on 2007-06-25
here is my new sony vaio...VGN-C2S
gerhard

---

### Post by IntuitiveNipple on 2007-06-26
**[color=red][size=5]Request For Additional Data[/size][/color]**

Thanks for all the DSDT files, they have been a great help. Although I'll continue collecting them to build comprehensive analysis tables they are not so important now..

Now what I need is the output of dmidecode for **very** old models. I am **particularly interested in [color=red]old models[/color]** that ***don't*** have the conventional BIOS name format of RxxxYz (e.g. R0200J3).

Please run the following commands:
```
$ sudo apt-get install dmidecode
$ sudo dmidecode -t bios | grep -E 'PIZZA|DIRETTO|PASTA|PTGD2-OM|ENLIL|P5LP-OM|PRAQUE|TALAS|TALAS2R|TALAS2D|NIACIN|TOKYOTOWER|TROGDOR'
```
 and if the grep command finds a match post the results of the following command in a reply here.

**Note:** If you have an old model that doesn't have an RxxxYz format BIOS name and the command above ***doesn't match anything*** your report  is ***even more important*** since it may mean that Linux doesn't report the strings where I expect it to.
```
$ sudo dmidecode -t bios
```
The results will help me ensure the model-detection functions support every Vaio model that the Sony Windows driver supports. I already know how the Windows driver identifies these older models but because I don't have one to hand I can't be sure precisely where in the DMI information Linux will report the signature strings.

Over the last 24 hours I've finally identified how the Windows Vista driver works and am well on the way to reproducing every bit of functionality in the Linux driver. I've reproduced the complex model-identity tables that define what functionality each model has, and how to control it from the driver (the same functionality is sometimes controlled in different ways).

This approach means the SNC driver will support every model in the exact same way the original Sony Windows drivers do.

---

### Post by Nubbie on 2007-06-26
a big thank you to xenoph0be for helping me get my brightness controls working on my vaio vgn c240e/b.
just run
```
sudo locate -u && for i in $(locate lcd-???-brightness); do sudo cp $i $i.bak; sudo sed -i '1 s|#!/bin/sh|#!/bin/bash|g' $i; done
```
and you should be able to control brightness with power management or via the brightness control panel applet.

Also if somebody could help me fix suspend to ram i would be extremely grateful. the laptop sleeps fine, but upon waking the lcd does not turn back on, and afaik the keyboard as well. i'm using the intel drivers.

---

### Post by Nubbie on 2007-06-26
bleargh

---

### Post by IntuitiveNipple on 2007-06-27
**[color=blue][size=5]Update[/size][/color]**

Can you please **keep this thread on the topic** of the **Sony Notebook Control driver** support  for Fn hot-keys, radio switch, power control, video-device switching and the other functionality provided by the SNC.

**If you need help about something else** please search the forums for related threads and articles - there are lots of solutions for Vaio issues with the motion-eye camera, Fn keys on FE models, Suspend/Resume (a very buggy area on Linux currently), HDA sound, and more.

For those of you that have missed it please check out my recent [Request For Additional Data]("http://ubuntuforums.org/showpost.php?p=2914426&postcount=100").

The DSDT investigative work to learn how to use the SNC device is now over - the new driver is rapidly developing and I expect to make a beta-test release to cover all models and kernel versions 2.6.17+ by the 1st week of July, so watch this space and be ready to help provide beta feedback.

At this point the driver can recognise *every* Sony model and adjust itself to the capabilities of the individual model (there are 80 types and counting!).

On my FE41Z I have fully working Fn hot-keys, S1 & S2 programmable keys and radio-kill-switch. I'm investigating how best to support video-device switching. Later I shall be adding support for reading device status and providing on/off functions where appropriate.

I'm currently modularising the code I'm writing into three blocks:
[list=1]
[*]Model recognition and subsequent capabilities adjustment
[*]Notification handlers for SNC and the video devices (to provide display-switching)
[*]Linux event handling and userspace interface
[/list]

To make it useful for you I need to support the driver with a userspace command-line program so scripts can interact with the SNC device easily.
To make things even easier for Ubuntu users I'm developing a new Gnome Preferences application and panel-applet to make configuring the controls easier than it is on Windows.

---

### Post by d3x7r0 on 2007-06-27
> **IntuitiveNipple said:**
> The DSDT investigative work to learn how to use the SNC device is now over - the new driver is rapidly developing and I expect to make a beta-test release to cover all models and kernel versions 2.6.17+ by the 1st week of July, so watch this space and be ready to help provide beta feedback.

Great! Can't wait to try it out on my vaio, that way I'll be able to say he is virtually 100% supported by Linux and that'll make me proud :D

---

### Post by SergeiAB on 2007-06-27
Sorry, i don't understand what i need to update?

---

### Post by Depressed Man on 2007-06-27
The update or driver isn't available yet, maybe on the first week of July. But right now IntuitiveNipple needs the DSDTs of very old VAIO laptop models. Hmm.. I wonder. My cousin has a laptop with XP (not that much RAM maybe 512 MB?) and he bought it a few years ago (2003 I think). Would that work? 

My mom also has an old VAIO, from around 03-04 too. Though they would never let me install Linux onto them, could I dump the DSDTs using a Live CD?

---

### Post by IntuitiveNipple on 2007-06-27
> **Depressed Man said:**
> But right now IntuitiveNipple needs the DSDTs of very old VAIO laptop models.
Not quite... the new request is simply the DMI BIOS report from **dmidecode** so I can be certain of where in the Linux output I can expect to find those old 'legacy' strings - I suspect they are in the model info not the BIOS name based on how the Windows code messes about :)

---

### Post by Depressed Man on 2007-06-28
Haha sorry, I was going off my memory about what I thought I read before. But anyway, are those two laptops I gave info about old enough to fit what you need? I can grab their model numbers next time I'm around them too if it helps.

---

### Post by IntuitiveNipple on 2007-06-29
> **Depressed Man said:**
> ...are those two laptops I gave info about old enough to fit what you need? I can grab their model numbers next time I'm around them too if it helps.
I doubt they are, unfortunately. Simple to find out though just check the BIOS version report in the Setup menus during boot.

I have a couple of 2002-vintage notebooks and they have the modern BIOS versioning. I suspect the models affected are from 2000 or earlier, or are desktop/notebook hybrids (some desktops have the SNC).

---

### Post by IntuitiveNipple on 2007-06-30
**[COLOR="RoyalBlue"][SIZE="4"]Update report and Request for Feedback[/SIZE][/COLOR]**

After more work on the 'machine ID' detection algorithms and subsequent configuration of model-specific functionality I've split the configuration task in two based on how easy it is to get the information from the PC.

There are two methods of configuration:
[list=1]
[*]Directly based on machine ID
[*]Indirectly via calls to SXBIOS (Sony eXtended BIOS functions)
[/list]
I've not yet fully traced the SXBIOS path of the Windows drivers and as the models that require that seem to be older ones I'm inclined to put that down the bottom of the ToDo list (it could delay initial release of the driver by a couple of weeks or more). 

I'm publishing my intention here in case the models affected by my decision are popular ones that you folks are using. If your Vaio model is in the "*List of models requiring SXBIOS functionality*" it would mean my driver won't be able to support it until the SXBIOS functionality has been developed.

Therefore, **if your model is in that list** let me know by replying to this post so I can calculate how many end-users would be affected by the decision (I have two models in the list, both with U2 BIOS). If enough of you are using the affected models I will increase the priority of the SXBIOS functionality although it will delay initial release of the driver.

[COLOR="Green"]**List of models currently supported:**[/COLOR]

Machine IDs 55 to 80 (except ID 61) have these BIOS signatures (last 2 characters of BIOS name, e.g. R0200**[color=red]J3[/color]**, or legacy codename)

**BIOS signatures:** F2, V0, X4, F3, PTGD2-OM, V1, ENLIL, X6, TALAS, TALAS2R, TALAS2D, NIACIN, PRAQUE, N0, N1, J3, F4, W1, W2, N2, N3, J6, X7, N5, N6, J4 (76), J4 (77), TOKYOTOWER, TROGDOR, J7

**[COLOR="DarkOrange"]List of models requiring SXBIOS functionality:[/COLOR]**

**BIOS signatures:** Z0, H0, K1, K0, A0, M0, Z1, Z2, D0, K2, A1, D1, U0, U1, P0, P1, Z3, C0, E0, U2, C1, B0, B1, G0, B2, G1, K7, F0, B3, K9, W0, G2, G3, X2, X1, F1, G4, G5, G7, G9, X3, J0, J1, J2, PIZZA, DIRETTO, PASTA

---

### Post by Depressed Man on 2007-06-30
I have a R0200JE (JE) and its not on the list at all?

---

### Post by IntuitiveNipple on 2007-07-01
> **Depressed Man said:**
> I have a R0200JE (JE) and its not on the list at all?
I bet  you a million $$$ you don't :)

---

### Post by tomlohave on 2007-07-01
I hope this one can help :

vaio VGN-N31Z

---

### Post by IntuitiveNipple on 2007-07-01
> **tomlohave said:**
> I hope this one can help :

vaio VGN-N31Z
Not without knowing the BIOS version string (looks similar to R0200J3)

---

### Post by tomlohave on 2007-07-01
sorry,

for VGN-N31Z, the bios version string is R0100J4

---

### Post by Depressed Man on 2007-07-01
> **IntuitiveNipple said:**
> I bet  you a million $$$ you don't :)

Haha..so does that mean I gave the wrong BIOS orginally? Or I'm just reading it wrong?

---

### Post by IntuitiveNipple on 2007-07-02
Not entirely on-topic but hopefully something useful for a lot of you: **long-life batteries**.

Because I travel extensively I needed a couple of long-life batteries for the VGN-FE41Z. Sony sell the [**VGP-BPL2C ** 79.92 Wh (11.1V/7200mAh)]("https://www.sonystyle.co.uk/SonyStyle/catalog/setCurrentItem/(xcm=PCM_b2ccrmstandard&layout=15_108_60_115_109_113_2&citemarea=3E9957D0304E7370E10000002BC29B8F&uiarea=2&ctype=areaDetails&next=seeItem&z_accStore=z_accStore&carea=43B33496B25B002F000000002BC29B85&citem=3E9957D0304E7370E10000002BC29B8F4368F6CC8F0901B8020000002BC29B72)/.do") for **£279 ($460)** [color=red]*each*[/color] - now I call that **[color=blue]daylight robbery[/color]**!

I went in search of a 3rd-party equivalent and discovered **[pandawoods, a seller on eBay](http://stores.ebay.co.uk/pandawoods_Battery_For-Laptops_SONY_W0QQcolZ4QQdirZ1QQfsubZ7484211QQftidZ2QQtZkm)** that sells VGP-BPL2/C equivalents (79.92Wh) for **£36 ($72)** including shipping from Hong Kong.

At that price they are almost throw-away so I ordered two. They arrived in about 6 days. Unfortunately the FE41 refused on a hardware and software level to charge them although they would provide power (they are delivered just under 50% charged) - the charging LED blinked rapidly. 

I had an exchange of emails and arranged to have them swapped for another 2. The exchange happened rapidly and within 8 days I had another 2 batteries but they had the same problem!

Luckily Linux came to the rescue. Simply by sending the supplier the output of
```
$ cat /proc/acpi/battery/*/state
$ cat /proc/acpi/battery/*/info

```
which was passed on to the factory, they were able to fix the problem (smart batteries all have flash EEPROMs and 'talk' to the host PC). The problem was that the FE41 series requires higher ratings than FSxx and other FE series laptops that use the VGP-BPL2 (not VGP-BPL2C).

As a result today I received another 2 replacements and both work properly with the FE41Z. So for the sake of a bit of hacking and some liaison with the supplier & factory, I've **saved £487 ($975)** :D

As for Sony's warnings about *inferior batteries* I just point to the recall of about **4 million Sony batteries** last year because of *the risk of fire*!

---

### Post by d3x7r0 on 2007-07-02
> **IntuitiveNipple said:**
> As for Sony's warnings about *inferior batteries* I just point to the recall of about **4 million Sony batteries** last year because of *the risk of fire*!

Of course Sony batteries were recalled, that's why Vaios use Panasonic batteries :lol:

---

### Post by Depressed Man on 2007-07-03
Nevermind, I figured out what I was intepreting wrong. Hehe..sorry!

---

### Post by buggybug on 2007-07-03
> **[COLOR="DarkOrange"]List of models requiring SXBIOS functionality:[/COLOR]**

**BIOS signatures:** Z0, H0, K1, K0, A0, M0, Z1, Z2, D0, K2, A1, D1, U0, U1, P0, P1, Z3, C0, E0, U2, C1, B0, B1, G0, B2, G1, K7, F0, B3, K9, W0, G2, G3, X2, X1, F1, G4, G5, G7, G9, X3, J0, J2, PIZZA, DIRETTO, PASTA

Hi.

Im using the PCG-K215S with BIOS version R0110**X1** and i would be effected by your decision of putting the traceback of SXBIOS functionality at the bottom of yout TODO list and wouldn't be happy about it :(

greetz

---

### Post by tiepi on 2007-07-06
is that possible to get DSDT in fedora system? I can't find acpidump utility for fedora.  

will install ubuntu if the new sony module can enable VMX  for me. 

my laptop is VGN-FE45G/W. still need DSDT?

Eric

---

### Post by Toufik on 2007-07-07
Sony Vaio VGN-FS315B
Bios verion: R0084J1

Generic kernel is choppy (since edgy), so I have to use 386 where it seems that sony_laptop is missing (since feisty, it worked in edgy). So I've to compile my own kernel in order to have fn keys handle.

---

### Post by alberto.m.vasquez on 2007-07-07
Hi there,

Thanks for all this work guys! Here I attached the DSDT for this
brand new Sony Vaio VGN-FZ140E. Please find below the list of 
problems detected so far. The resolution problem I solved it following 
this blog instructions: [http://www.blaise.ca/blog/?p=14](http://www.blaise.ca/blog/?p=14) Note that that
HP has the same graphic accelerator as my Sony. Once again,
thanks for this work, and let me know if I can give more info on
this model. Cheers!

LIST OF PROBLEMS having installed Feisty with 2.6.20-16-generic.

(Note: all hardware was working fine with the Windows Vista that
came with the machine, Once I checked that all worked fine I
just deleted Vista, so Vista was usefull after all).

1. Resolution is fixed at 800x600 (while this Sony handles 1280x800)
2. Even if installed the OS from the DVD unit, after reboot the optical 
    unit is not seen at all by the system, so can not be used.
3. Wireless does not work.
4. The "Fn" functions (like brightness controls) do not work
5. Sound comes out by speakers, but no sound comes out of 
    the headphones (and when you plug the headphones the sound
    still comes out of the speakers).
6. The special "multimedia" keys do not work.

Final note: All USB-hot-devices I tried seem correctly recognized
and working fine (a couple of flash-mems, a 2nd gen iPod nano).

Cheers!
Alberto.
p.s. Let me know if I can help more.

---

### Post by alberto.m.vasquez on 2007-07-07
Sorry, in my previous email I forgot the BIOS. here is the complete thing attached.

---

### Post by p1r0 on 2007-07-07
Hi!

A friend of mine has a VGN-SZ3XP Sony Vaio and would like to contribute but neither him nor me know how to get the ACPI DSDT file.

Is there any help someone could give to prepare and send this file???

Thanks in advance,
Tabaré-

---

### Post by alberto.m.vasquez on 2007-07-07
Hey Tabaré,

First, to find out your BIOS version do:

$ sudo apt-get install dmidecode
$ sudo dmidecode -t bios

The BIOS version shows up as one of the first outputs
(example: R0050J7).

To get the DSTP do:

$ sudo apt-get install acpidump
$ sudo acpidump -b -t DSDT -o FileName
$ tar cvfz FileName.tar.gz FileName
$ sudo rm FileName.dsdt

Where Filename should be in the following format to make 
things easier for the Ubuntu developers:

  SERIES-MODEL-BIOS.dsdt
  (example: VGN-SZ3XP-YOURBIOSHERE.dsdt)

For more details check: 
[http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/](http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/)

Cheers,
Alberto.

---

### Post by d3x7r0 on 2007-07-07
> **alberto.m.vasquez said:**
> 4. The "Fn" functions (like brightness controls) do not work
5. Sound comes out by speakers, but no sound comes out of 
    the headphones (and when you plug the headphones the sound
    still comes out of the speakers).


Got this issues in my VGN-C2S/H except I can get sound from the headphones, It's just the auto-detection of the headphone jack that doesn't work.

---

### Post by perun on 2007-07-09
Here's my dmidecode -t bios information as well as my acpidump information from my SZ330P.

---

### Post by G2k on 2007-07-09
Hey I'm running Gentoo on a VAIO VGN-FS660W so I was wondering how I can make use of this project once it has reached a stable state on my Gentoo box without having to switch distros just to be able to fully use my VAIO.
Thanks

---

### Post by ululu on 2007-07-10
Here is what I got for my SZ1M. Hope it helps.

---

### Post by justU on 2007-07-11
@IntuitiveNipple

I have a VGN-FS215B with bios version R0040J1 (someone posted already the dsdt file).
So the signature must be "J1". I couldn't find this signature in your supported/not supported list!
Do I need SXBIOS functionality?

---

### Post by IntuitiveNipple on 2007-07-11
> **justU said:**
> @IntuitiveNipple

I have a VGN-FS215B with bios version R0040J1 (someone posted already the dsdt file).
So the signature must be "J1". I couldn't find this signature in your supported/not supported list!
Do I need SXBIOS functionality?
Ah yes, I must have missed typing it when I was preparing the list. It has the same machine ID as J0 and J2, and is in the SXBIOS group. I've added J1 to the list now, thanks for spotting it.

I've been delayed in releasing a test driver due to other more pressing projects but I'm hoping to   get back on-track over the next week.

---

### Post by gnocci on 2007-07-12
The list at [http://tjworld.net/snc/](http://tjworld.net/snc/) doesn't contain VGN-C14G (for which i posted the info a time ago). Just in case, does that mean something?

---

### Post by Migs on 2007-07-14
Sony released a new bios for my FE11M. I am going to reinstall Vista and install the bios en then use the windows version of iasl to obtain the dsdt file.

---

### Post by IntuitiveNipple on 2007-07-14
> **gnocci said:**
> The list at [http://tjworld.net/snc/](http://tjworld.net/snc/) doesn't contain VGN-C14G (for which i posted the info a time ago). Just in case, does that mean something?
Yes, it means I downloaded a bunch of attached archives at the same time on June 26th and promptly forgot I'd done so, and therefore didn't extract the DSDTs or regenerate the table :p

Well spotted - I've added them all now. 

Since I've managed to reverse-engineer how Windows handles the SNC the tables have become largely superfluous although they do help see how models relate to one another.

---

### Post by IntuitiveNipple on 2007-07-14
> **Migs said:**
> Sony released a new bios for my FE11M. I am going to reinstall Vista and install the bios en then use the windows version of iasl to obtain the dsdt file.
If it is R0172J3, R0190J3 or R0200J3 then I've already got it.

---

### Post by Migs on 2007-07-14
> **IntuitiveNipple said:**
> If it is R0172J3, R0190J3 or R0200J3 then I've already got it.

No it's R0174J3:

---

### Post by sab0403 on 2007-07-14
Well, I'm confused.

I have a VAIO laptop, model VGN-FJ250F... I want to help out here but I don't know how...

What do I need to do?

---

### Post by steckerman on 2007-07-14
Hi, this is the dsdt of my VAIO laptop (FE31Z).

---

### Post by IntuitiveNipple on 2007-07-14
> **sab0403 said:**
> Well, I'm confused.

I have a VAIO laptop, model VGN-FJ250F... I want to help out here but I don't know how...

What do I need to do?
You don't need to do anything - the DSDTs already collected are sufficient. The information from the data-collection exercise helped whilst I was reverse-engineering the Windows Vista driver to confirm certain assumptions.

 I had hoped to publish a beta test version of the Linux driver in the first week of July but unexpected complications, other commitments and projects have delayed me somewhat.

I'm hoping to spend a few days polishing it this coming week and getting the userspace applications that support it completed so I can publish something that is almost complete.

To support all models I have to reverse-engineer the Windows SXBIOS driver used by a lot of older Vaios. I posted a comment on that recently - basically support for identifying those models is on my *ToDo* list but isn't my top priority.

The driver as it stands **does** support the functionality the SXBIOS models require, but until I can replicate the way SXBIOS identifies each model I have no way for the Linux driver to know which model it is and therefore what configuration it should use.

---

### Post by gnocci on 2007-07-14
> **IntuitiveNipple said:**
> Yes, it means I downloaded a bunch of attached archives at the same time on June 26th and promptly forgot I'd done so, and therefore didn't extract the DSDTs or regenerate the table :p


Pfew, for a moment i feared it meant something, you know, *bad* 8-[

---

### Post by justU on 2007-07-15
> **IntuitiveNipple said:**
> The driver as it stands **does** support the functionality the SXBIOS models require, but until I can replicate the way SXBIOS identifies each model I have no way for the Linux driver to know which model it is and therefore what configuration it should use.
Ok, that sounds like we poor "old vaio" users will have to wait a long time to get support for our notebooks :(
But isn't it possible to have a workaround until the SXBIOS is reverse-engeneered?
If the detection of the model is the problem, isn't it possible to define the model manually until detection is integrated?

I have to apologize for my impatience, but I am waiting for years now to get support for my sony laptop ;)

---

### Post by IntuitiveNipple on 2007-07-15
> **justU said:**
> Ok, that sounds like we poor "old vaio" users will have to wait a long time to get support for our notebooks :(
But isn't it possible to have a workaround until the SXBIOS is reverse-engeneered?
If the detection of the model is the problem, isn't it possible to define the model manually until detection is integrated?

I have to apologize for my impatience, but I am waiting for years now to get support for my sony laptop ;)
Well, as just another poor "old vaio" user myself (I have two SRX models)  I'm in the same boat. If you've been waiting years, why haven't you done something about it? The entire point of Free and Open Source Software (FOSS) is that we, the users, have the opportunity to add functionality or support others to do so.

If enough of the community had got together and either persuaded Sony to release specifications or supported other developers through funding or whatever else they might need maybe a comprehensive module would have been developed before this. There have been three prior attempts at doing this all of which could only provide patchy support and were obsoleted by changes made by Sony. 

I got into this in May when I realised my new PC lacked support for the Fn keys. As it is I've spent over 150 hours so far, simply because I want this functionality for myself. It's a steep learning curve since although I'm an experienced programmer/hacker this is my first foray into serious kernel development. I have to say though that 90% of the time has been spent doing the reverse-engineering so far.

The entire point of FOSS and the GNU/Linux way of doing things is ***Give*** and ***Take***: although you get to *take* for free (as in no money), you may well pay more in time and effort by *giving* back to the community in any way you can.

As I see it, GNU/Linux has one great advantage over closed-source alternatives. When something needs doing, you can do it yourself rather than expect someone else to do it for you. The GPL ensures that when you work with GNU/Linux you benefit by having the right to do whatever you want to the source code and that you give the changes back to the community if you distribute.

---

### Post by justU on 2007-07-15
> **IntuitiveNipple said:**
> Well, as just another poor "old vaio" user myself (I have two SRX models)  I'm in the same boat. If you've been waiting years, why haven't you done something about it? The entire point of Free and Open Source Software (FOSS) is that we, the users, have the opportunity to add functionality or support others to do so.

If enough of the community had got together and either persuaded Sony to release specifications or supported other developers through funding or whatever else they might need maybe a comprehensive module would have been developed before this. There have been three prior attempts at doing this all of which could only provide patchy support and were obsoleted by changes made by Sony. 

I got into this in May when I realised my new PC lacked support for the Fn keys. As it is I've spent over 150 hours so far, simply because I want this functionality for myself. It's a steep learning curve since although I'm an experienced programmer/hacker this is my first foray into serious kernel development. I have to say though that 90% of the time has been spent doing the reverse-engineering so far.

The entire point of FOSS and the GNU/Linux way of doing things is ***Give*** and ***Take***: although you get to *take* for free (as in no money), you may well pay more in time and effort by *giving* back to the community in any way you can.

As I see it, GNU/Linux has one great advantage over closed-source alternatives. When something needs doing, you can do it yourself rather than expect someone else to do it for you. The GPL ensures that when you work with GNU/Linux you benefit by having the right to do whatever you want to the source code and that you give the changes back to the community if you distribute.
Your are absolutely right! But as a non developer I can only help with bug reports and feature requests.
I am using linux for years now and whenever I got a Problem with hardware support I contacted the manufacturer
and asked for linux support ... But do you really think that sony was interested in linux support
two years ago? ...perhaps time will change, especially after dell is now offering Ubuntu for the desktop market.

You wrote that people with old vaios should mention it in this thread... and I did so. The only thing I wanted to know is,
if it is possible to get a simple workaround. My attention was not to attack you!
I am lucky that someone is working on this problem!

Perhaps I expressed myself wrongly in my last post. My english is not that good, sorry.

---

### Post by IntuitiveNipple on 2007-07-15
> **justU said:**
> Your are absolutely right! But as a non developer I can only help with bug reports and feature requests.
There is something much more important you can always do, no matter your level of *skill in the art* and that is to motivate and mobilise other users in order to find a solution.

All it took for me was to start this thread asking for information about other people's Vaios - when I posted it I had no idea that quite so many people were in the same position as me and wanting a solution without all the messing about.
> **justU said:**
> I am using linux for years now and whenever I got a Problem with hardware support I contacted the manufacturer and asked for linux support ... But do you 
really think that sony was interested in linux support two years ago?  ...perhaps time will change, especially after dell is now offering Ubuntu for the desktop market.

I'd refer you to my previous comment on this. You'd be amazed sometimes on how you can move a manufacturer if you can show them the business or public relations benefits - take your Dell example. As a result of their IdeaStorm site someone asked for laptops with Linux pre-installed, publicised it, it struck a chord in tens of thousands of others who probably all thought they were just isolated individuals with an unrealisable desire that a 'big corporate' would ignore... and now we have Ubuntu shipping pre-installed on some Dell models.

> **justU said:**
> You wrote that people with old vaios should mention it in this thread... and I did so. The only thing I wanted to know is, if it is possible to get a simple workaround.
No, there isn't a workaround. To manually set how the functionality was applied you'd need to be able to do whatever it is that the SXBIOS library does - and until I (or someone else) has reverse-engineered it your guess would be as good as mine. The problem is, the way Sony have developed the models over the years there is no *standard* formula you can use to predict what is available or how to use it.

There are 80+ machine IDs, each one is assigned to any of 29 classes. Based on these two variables the driver will choose different code paths. Then add to this specific code-paths that over-ride these major variables and the most annoying part of all, the fact that the same internal function request number can mean two different operations on different models. For example, there is a situation where the op-code in some models for changing the wireless radio state is used in other models to switch video output ports!

With that kind of issue to deal with the driver has got to know precisely which model it is working with or else at the least it could cause a lot of confusion (imagine turning your wireless on and the screen going blank because the SNC had switched to the external VGA port!) and at worst could actually damage the hardware.
> **justU said:**
>  My attention was not to attack you! I am lucky that someone is working on this problem!

Perhaps I expressed myself wrongly in my last post. My english is not that good, sorry.
I didn't see your comments as an attack, but what I did perceive is something I see alot around FOSS and that is a kind of apathy where users seem to have lost sight of the ideals behind FOSS, and also don't seem to realise it is so easy to get the ball rolling to solve a problem by motivating others to help.

As to the case in point - SXBIOS model support - it is on my *ToDo* list as I said, but won't be in the first release of the driver. I'm already a couple of weeks behind where I wanted to be with it. The good news is that being on my ToDo list doesn't mean it has been consigned to some 'never-will-be-done' pile. 

My intention is that once I've got the driver out there and dealt with any mistakes and bugs in the driver and the associated userspace applications that make it useful, I will tackle SXBIOS.

I would expect that to be within the next couple of months so it's not a case of having to wait years for it.

---

### Post by Cavalier1723 on 2007-07-15
Do you need any info from a vaio FZ190 CTO /w Blu-ray. Its basically the same as an FZ180. Probably everything for the driver you are making would be the same as the FZ140 which someone already gave info on.

thanks for your work

---

### Post by IntuitiveNipple on 2007-07-15
> **Cavalier1723 said:**
> Do you need any info from a vaio FZ190 CTO /w Blu-ray. Its basically the same as an FZ180. Probably everything for the driver you are making would be the same as the FZ140 which someone already gave info on.

thanks for your work
The driver functionality is determined by the last two characters of the BIOS name. What's the BIOS version (e.g. RxxxYz) ?

---

### Post by Cavalier1723 on 2007-07-15
> **IntuitiveNipple said:**
> The driver functionality is determined by the last two characters of the BIOS name. What's the BIOS version (e.g. RxxxYz) ?

The bios version is R0050J7. I noticed that there are no 'J7' on the list at [http://tjworld.net/snc/](http://tjworld.net/snc/).

edit: my bad. I just noticed it is the same bios version as someone posted for a FZ140. in post #124 (page 13).

---

### Post by fb12 on 2007-07-16
Here is the dsdt of my Vaio VGN-FS315M.. I hope this will help..
Thank you for your work!

---

### Post by jruschme on 2007-07-16
Here's the one from my PCG-K37.

BTW, my battery technology is reported as "rechargeable".

---

### Post by Migs on 2007-07-17
Here is the new dsdt.dsl file output from the new bios-release for the VGN-FE11M. I cannot see directly if it differs allot from the dsdt output i posted earlier(R0172J3).

By the way, I installed Opensuse for a change and I was surprised that while installing it recognized my notebook model name and even posted my tagnumber. Could they way OpenSuse recognize my model name help you out writing the patch? Anyway good luck and keep up the good work =D>

---

### Post by IntuitiveNipple on 2007-07-17
> **Migs said:**
> By the way, I installed Opensuse for a change and I was surprised that while installing it recognized my notebook model name and even posted my tagnumber.
I didn't know SUSE had already taken advantage of the information but it is something I've built into the GNOME **Vaio SNC Preferences** application I'm writing that will be launched by a right-click of the panel brightness icon, or from System->Preferences.

I would guess they do what I do and derive the information from a DMI call. You can see the same information using:
```
$ sudo dmidecode -t system
# dmidecode 2.8
SMBIOS 2.40 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: Sony Corporation
        Product Name: VGN-FE41Z
        Version: 01
        Serial Number: 28201250-5001257
        UUID: CD10AD40-B1EB-11DB-8074-0013A98651BD
        Wake-up Type: Power Switch
        SKU Number: N/A
        Family: N/A

Handle 0x0010, DMI type 32, 20 bytes
System Boot Information
        Status: No errors detected
```

---

### Post by justinux on 2007-07-17
Attached is a dmidecode output and a DSDT.dsl for my PCG-SRX99 / 87 (its a 99 motherboard with 87 everything else)
The BIOS has been upgraded since factory to whatever Sony has as the latest available BIOS.

This is a rather old laptop (2002?) and I don't see it listed in the ACPI Method Analysis page so I thought I'd post.

The Volume / Brightness function keys work adequately and the laptop suspends and returns from suspend ok.  (Problem with returning from suspend: the IP settings are lost for eth1 which is the built-in wireless card.  Can be resolved with ifdown eth1 followed by ifup eth1) 

Let me know if I can provide anything else.

---

### Post by Migs on 2007-07-18
> **IntuitiveNipple said:**
> I didn't know SUSE had already taken advantage of the information but it is something I've built into the GNOME **Vaio SNC Preferences** application I'm writing that will be launched by a right-click of the panel brightness icon, or from System->Preferences.

I would guess they do what I do and derive the information from a DMI call. You can see the same information using:
```
$ sudo dmidecode -t system
# dmidecode 2.8
SMBIOS 2.40 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: Sony Corporation
        Product Name: VGN-FE41Z
        Version: 01
        Serial Number: 28201250-5001257
        UUID: CD10AD40-B1EB-11DB-8074-0013A98651BD
        Wake-up Type: Power Switch
        SKU Number: N/A
        Family: N/A

Handle 0x0010, DMI type 32, 20 bytes
System Boot Information
        Status: No errors detected
```

It seems Suse uses something differently, dmidecode is not present on my system. It's seems like it is reading information from HAL? and probing /dev/mem[0xdc010, 802].

 I've made a copy of the Yast hardware information output.

---

### Post by MrsHudson on 2007-07-18
Mine is a VGN-FS285H that was sold in Germany. I'm a bit confused because on the back there are two different model labels: One says Sony PCG-7A1M, the other Vaio VGN-FS285H. However, when I log into Sony's support site using my serial number the laptop is identified as VGN-FS285H.

so long, Mrs H.

---

### Post by IntuitiveNipple on 2007-07-18
> **Migs said:**
> It seems Suse uses something differently, dmidecode is not present on my system. It's seems like it is reading information from HAL? and probing /dev/mem[0xdc010, 802].
As far as I'm aware this uses the DMI library calls to obtain the model and tag information - dmidecode is simply a user front-end to accessing that information but isn't necessary for other programs.

---

### Post by IntuitiveNipple on 2007-07-18
> **justinux said:**
> Attached is a dmidecode output and a DSDT.dsl for my PCG-SRX99 / 87 (its a 99 motherboard with 87 everything else)
The BIOS has been upgraded since factory to whatever Sony has as the latest available BIOS.

If you can post just the DSDT without decompiling it, that is more helpful. The BIOS version from your dmidecode is R0223U2 so name the file PCG-SRX99-R0223U2.dsdt and then gzip/bzip2 it.

---

### Post by justinux on 2007-07-18
... Compiled PCG-SRX99-R0223U2.dsdt is attached

---

### Post by artimon06 on 2007-07-19
Sony vaio VGN S4XP with Ubuntu 7.04

- LCD perfect (including Fn keys
- sound perfect (including Fn keys)
- hibernate is not working (was working with Dapper)
- suspend to ram is not working, as usual :(
- I can control the CPU but it's not perfect: goes automatically to the maximum when plugged !
- touchpad almost perfect

- no file /proc/acpi/battery/BAT0

- cat /proc/acpi/battery/BAT1/info     
present:                 yes
design capacity:         79920 mWh
last full capacity:      79920 mWh
battery technology:      non-rechargeable
design voltage:          11100 mV
design capacity warning: 0 mWh
design capacity low:     120 mWh
capacity granularity 1:  0 mWh
capacity granularity 2:  10 mWh
model number:            
serial number:           
battery type:            LION
OEM info:                Sony Corp.


- BIOS:  Version: R0092V0

- DSDT bellow 


Thanks for your work !

---

### Post by huntnplay on 2007-07-19
Here is what I got for my VGN-FE690, hope it helps all of us.

---

### Post by tiepi on 2007-07-23
yesterday, I changed my fedora 7 with Ubuntu 7.  now i can upload DSDT table.

I like Ubuntu.

---

### Post by Migs on 2007-07-23
> **tiepi said:**
> yesterday, I changed my fedora 7 with Ubuntu 7.  now i can upload DSDT table.

I like Ubuntu.

Thats total nonsense your posting. It's not nesasery to use ubuntu to post an acpi output with acpi-dump. It can be done in every distro even in windows! With intel's iasl tool you can use acpixtract and get the dsdt.dsl file in both linux and windows. 

you should love intel for that, not ubuntu!

---

### Post by tiepi on 2007-07-23
> **Migs said:**
> Thats total nonsense your posting. It's not nesasery to use ubuntu to post an acpi output with acpi-dump. It can be done in every distro even in windows! With intel's iasl tool you can use acpixtract and get the dsdt.dsl file in both linux and windows. 

you should love intel for that, not ubuntu!
It's not just a DSDT. I got another sata disk and want to try ubuntu. DSDT is just an add ons for me.

Intel should thanks me because I buy their product. :-)

---

### Post by Depressed Man on 2007-07-25
Just curious (it's an issue worth checking). Does anyone's Sony laptop do a  hiccup type clicking when they boot it up (before BIOS and Grub load). Or even before their OS (rather it's Ubuntu or WIndows loads) and unload on shutdown?

Check out this thread. 

[http://ubuntuforums.org/showthread.php?p=3079288#post3079288](http://ubuntuforums.org/showthread.php?p=3079288#post3079288)

I saw it but my laptop doesn't do the three clicks on boot up of Ubuntu or Shutdown. Only when it boots up (before the BIOS splash screen shows) and before grub loads.

---

### Post by dustrho on 2007-07-26
I'm running Ubuntu 7.04 on the Sony Vaio PCG-TR3A laptop. Here's my DSDT output. Hope it helps!

---

### Post by chadlewis on 2007-07-26
Has anyone yet found a way to fix the *speakers not shutting off when headphones are plugged* in thing? Of course I've tried all the regularly suggested methods, such as recompiling audio drivers from scratch and enabling headphones (which were already enabled).

---

### Post by Optimaximal on 2007-07-28
Here's my submission - Sony Vaio VGN-BX195EP.

Anyone else having trouble shutting the computer down?  When I click shutdown, the OS closes and I hear the HDD power down, but the rest of the system still runs in a comatose state - I have to hold down the power button for the usual 4 seconds to sort it.

---

### Post by David A Knight on 2007-07-28
Here's the DSDT output for my VGN-FZ11M

Audio mute works fine, as do the volume buttons, it's the usual brightness/monitor/webcam/sleep buttons that do not function.

---

### Post by cyke on 2007-07-29
here's mine.  s1 s2 button, camera does not work.

---

### Post by 0live on 2007-08-04
Hi everyone and thanks for your work IntuitiveNipple!
Here are my data:

[VGN-FS115Z Technical Specifications]("http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-FS&m=1811")

```
os@compy:~$ sudo dmidecode -t bios
# dmidecode 2.8
SMBIOS 2.34 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0100J0
        Release Date: 02/25/2005
        Address: 0xE4690
        Runtime Size: 113008 bytes
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

```

---

### Post by ntetreau on 2007-08-04
It's unrelated i know, but for all those looking for help with their webcam, check out this blog: [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)

I installed the deb and my camera is now working (need a reboot though).

Nic

---

### Post by lolcats on 2007-08-05
well, in the spirit of telling:

Theres one bug i cant seem to get out of my system: ACPI dumps cause the terminal to exit abruptly (sometimes segfaulting just before that)
Heres an excerpt:
```

idiot@drake> apci -A -V
ACPI Status:
SEGFAULT in acpit.c: cant load acpi drivers! no device found under /dev/hda!
Temp:
  OK @ 35 degrees C
SEGFAULT: acpic.c: cant load acpi drivers! no device found under /proc/acpi/temp!

Gnome-Terminal: SEGFAULT. Bad terminal descriptor.
*terminal dissapears*

```

this is on (gods) an old Vaio PCG-F250.

Another thing that i've done is used the official ETCH debian ones from mirrors.kernel.org -- it doesnt cause this problem.


Dang guys, i like upbuntu, but make it run on this old thing... i have a 6.06 server running apache and MySQL and it runs great... and xubuntu runs on every other machine! even the ainchent 386 200Mhz box with no hd!

---

### Post by cacycleworks on 2007-08-06
> **Tripmonkey_uk said:**
> Hi all..
Just added a post to the [Ubuntu-FS]("http://ubuntufs.wordpress.com/") site to let people know of this thread & I've tried to write an even [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") for new users to follow. Please let me know if it needs improving at all.

Here's my contribution from a VGN-FS215E with the R0040J1 BIOS..
Good luck!

Your tutorial is far more a contribution than the attachment! I read page 1 a bunch of times trying to figure out why "all vaio owners" were being called. The way you present it, I saw what was wanted of us. The top post was simply a bunch of statements without any explicit requests.

Maybe the initial post could be edited to something more like:

If you have sony Vaio, please do *this*. And then below have the rest of the post. I must say a huge thank you to those driving this effort! In trying to get my new Dell to simply work, I have a huge appreciation for the engineering it takes to learn this stuff.



about my sony:
SZ220 all intel-based. Duo core 1.8 Ghz
Works out of box with Kubuntu Fiesty: eth0, eth1 (wlan), sound, optical drive (cd and cd-r) . Fn keys that work... volume, brightness, boot from CD, boot from USB stick and boot from USB HD.

Doesn't work: camera, fingerprint reader, Sony memory stick slot.

Untested: suspend, hibernate, bluetooth (tho all indications show it would), SD/Multi Card reader device by Texas Instruments, DVD functionality untested.

Will gladly help more, please reply with specifics. Also, am getting my new Dell up and running as my production laptop, so will start experimenting more on the Sony. :)

---

### Post by cualquiercosa on 2007-08-06
Here's the dsdt file from my vgn-fe31z with R0172J3 bios.

The things that doesn't work are the s1 and s2 buttons and the screen dim. You also talk about vt, it should be great if vt works. I've been searching for info on how to make it work and it seems to be a bios problem.

---

### Post by yomyom on 2007-08-07
Here is the DSDT file for my VGN-FE21M. Cheers!

---

### Post by Migs on 2007-08-07
IntuitiveNipple: are you making any progress yet? 

If you have still problems figuring out how to "autodetect" the type of laptop why don't make something like a wrapper and specific driver for each model? You don have to write a lot specific drivers because most laptops are related to each other. For an example the FE11, FE21 and FE31 have the same table output. 
You could use then a setup which xorg uses by numbering the models and by selecting the right number the driver would be assigned to the wrapper. It is just something I thought off it...during my vacation.

---

### Post by robgill on 2007-08-07
Vgn-fs640w-r0040j1

---

### Post by djsb on 2007-08-08
Hello,

My Sony laptop identify itself as:

```

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0100J4
        Release Date: 02/08/2007
        Address: 0xE7210
        Runtime Size: 101872 bytes
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 10.0
        Firmware Revision: 10.0

```

working: brightness control via /sys, 'mute' key, 'sound level up' key and 'sound level down' up
NOT working: brightness control keys, display switch key, zoom key and sleep key

ACPI dump is attached.

---

### Post by AlbinoButt on 2007-08-09
Here's the dsdt for my VGN-TZ90HS. Thanks for the hard work!

---

### Post by uncommon on 2007-08-10
Hi!

I have a SONY VAIO VGN-BX195SP laptop. Bios is R0190X5.

 "sudo dmidecode -t bios" says:

```
# dmidecode 2.9SMBIOS 2.31 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0190X5
        Release Date: 07/10/2006
        Address: 0xE1BF0
        Runtime Size: 123920 bytes
        ROM Size: 1024 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                IEEE 1394 boot is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
```


I hope the DSDT file can help...

Keep up the good work!

uncommon

---

### Post by uncommon on 2007-08-10
> **Optimaximal said:**
> Here's my submission - Sony Vaio VGN-BX195EP.

Anyone else having trouble shutting the computer down?  When I click shutdown, the OS closes and I hear the HDD power down, but the rest of the system still runs in a comatose state - I have to hold down the power button for the usual 4 seconds to sort it.

Yes I have the same issue under Feisty. Annoying.

I upgraded to Gutsy and the problem is gone.

---

### Post by ntetreau on 2007-08-18
Bios on a VGN-SZ3XWP, Fn keys all work, at least when running the nvidia chip.

```
# dmidecode 2.9
SMBIOS 2.31 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0091N0
        Release Date: 07/10/2006
        Address: 0xE4510
        Runtime Size: 113392 bytes
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

```

---

### Post by gotomah on 2007-08-18
Hi guys, 
here's another file for your list:

I have a VGN-FE31Z and the only keys that work are the volume ones, and those are not even using the *Fn* key; i mean they are buttons on their own.

Hope it's all going cool
Salud!

---

### Post by Ferri on 2007-08-19
Thanks for your efforts.
I haven't been able to see my laptop here (VGN-FS415B). Until now I've been able to make my Fn keys following [this post]("http://ubuntuforums.org/showthread.php?t=309533"), but any improvement is, of course, wellcome.
Here's my dsdt file.

---

### Post by mex23 on 2007-08-19
Below my table of the Vaio Ar11-M :)

[ATTACH]41062[/ATTACH]

---

### Post by ssRNA on 2007-08-23
> **samir85 said:**
> Here are the information about my VGN-FE11H laptop. (btw: I think I updated my Bios over the Sony update tool once.)

Srry i'am noob, how to using this VGN-FE11H-R0074J3.dsdt.tar.gz file. I'm really noob... Please help me.

Best Regards

---

### Post by djsb on 2007-08-23
> **ssRNA said:**
> Srry i'am noob, how to using this VGN-FE11H-R0074J3.dsdt.tar.gz file. I'm really noob... Please help me.

tar.gz or tar.bz2 files are compressed archives (like zip or rar files). Most of the files posted on this thread contain information about power management (ACPI) on sony laptops. There is nothing really insteresting for you to do with them if your not an ACPI expert. What is interesting for you will be the piece of software that will be coded thanks to all these information. It could improve power management and some other related things such as special keys or display brightness control on Sony laptops.

---

### Post by merlinof2 on 2007-08-24
Great Project:
I have a Sony Vaio VGN-TX650P that I used the SuSe re-partitioning S/W on and resized the Windows Partition without any data loss.  KEWL.
I then ran a completely incident free Ubuntu Fiesty install and absolutely love the result.. GRUB allows both to boot fine.
HIBERNATE = WORKS
BRIGHTNESS=WORKS UP AND DOWN
SWITCH TO EXTERNAL MONITOR = DOES NOT WORK
WIRELESS LAN = WORKS (requires me to use "sudo wlassistant" but that's flawless
MUTE = WORKS
VOLUME = WORKS
BLUETOOTH = THINK IT WORKS, the file xfer module pops up but will not accept the ID code ?

what else can I provide?

don.m

---

### Post by protechvn on 2007-08-24
Please help me
My Sony vaio VGN-S560P fail when I upgrade bios. I Can't find original bios for it.
I need original bios for it. Please hepl me.

---

### Post by popat007 on 2007-08-26
Here is my Sony VAIO VGN-AR290G DSDT file

---

### Post by collins_ on 2007-08-27
Thanks for your work, I'm waiting for the new driver too :).
At this time everything runs on my laptop sony vaio SZ3VP with the old-fashion driver  :  [http://linuxsonyvaio.wetpaint.com/]("http://linuxsonyvaio.wetpaint.com/")
I wrote a tutorial several months ago about : howto install sonypi and sony_acpi modules for hardware control of your laptop, howto switch automatically between the 2 video boards, howto install flash 64 bit, howto install the Ricoh module for webcam, howto install the 3D desktop Beryl, and howto manage power with powernowd and scaling governors...

i join in the next reply my DSDT file :)

Collins

---

### Post by collins_ on 2007-08-27
My DSDT file for my vaio VGN-SZ3VP

---

### Post by d3m1g0d on 2007-08-27
hello,

i've attached the dsdt of my sony vaio vgn-fe28b.

keep up the good work.

rgds

---

### Post by r3tex on 2007-08-27
Wow! if you could manage to turn on VMX I would pay you.

---

### Post by LT1Caprice57L on 2007-08-28
Here's the dmidecode -t bios response on my PCG-K33:

```
Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0105X3
        Release Date: 10/26/2004
        Address: 0xE3250
        Runtime Size: 118192 bytes
        ROM Size: 512 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                8042 keyboard services are supported (int 9h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

```

EDIT: Looks like with the X3 bios, I'm one of the ones who will suffer from that one being at the bottom of the T/D list :( oh well...

---

### Post by CancelloCornorosso on 2007-08-29
Vaio VGN-S1XP.

Keep up with this good work!

---

### Post by mozjonathan on 2007-08-30
Hi,

This looks promising ! My Vaio is a PCG-K115M, and the fn keys are handled via a patched sony_acpi driver and a homemade userspace program, but that's definitely not the best solution.

Here is my DSDT, my bios reference ends with X1 so I guess that's related to the SXBIOS functionality. Best wishes for the upcoming work,

Jonathan

---

### Post by lfvsouza on 2007-08-31
Vaio SZ360P here.

 Everything work just fine, except for the fingerprint reader that I am currently trying to setup correctly. So, let's see:

 . FN keys work fine (both brig and sound keys are ok)
 . Sound works fine 
 . MIC works fine
 . webcam works fine (test under aMSN is also ok)
 . wi-fi ok
 . cd / dvd ok (one exception here: i am having a hard time playing commercial DVDs but i am on my way to solve this as well)
 . touchpad ok
 . video ok (nvdia driver ok - using under Beryl and others)
 
 ok, so, pretty much everything up and running.

---

### Post by timfelgentreff on 2007-08-31
Hey, had a look at your list and didn't see my model listed, so heres my output of dmidecode:

```

# dmidecode 2.9
SMBIOS 2.34 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0044J2
        Release Date: 05/19/2006
        Address: 0xE4410
        Runtime Size: 113648 bytes
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

```

---

### Post by aprogram on 2007-09-01
Here is the output for my VGN-FZ11S. Thank you for implementing this cool driver!

---

### Post by jrb114 on 2007-09-01
Here's my output. Thanks for all your efforts.

---

### Post by Flumpy on 2007-09-02
Hi, I'm quite new to Ubuntu and I've been working with it
for a month or so. I've got a Sony Vaio PCG-FR215M.

This is my dmidecode:
```
# dmidecode 2.8
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0105K7
        Release Date: 06/20/2003
        Address: 0xE41F0
        Runtime Size: 114192 bytes
        ROM Size: 512 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                8042 keyboard services are supported (int 9h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

```

But when I look in (/proc/acpi/) the dsdt file is empty. :confused:
The fn key doesn't work.

Thanks

---

### Post by AlfyBoy on 2007-09-02
Here you are, i hope it helps.

I know this is not the place to address problems, but if someone can point me on the right direction i would appreciate it. I got my fn keys working using this tutorial:

[http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/#comment-1113](http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/#comment-1113)

 but after updating linux headers from the automatic update service my fn keys no longer work…:confused:, is there a way to fix this? linux-headers-2.6.20-16 v: 2.6.20-16.31 on feisty 

Thanks a lot for your hard work
:guitar:

---

### Post by LT1Caprice57L on 2007-09-03
I can't figure out how to get the DSDT file.

However, looking through the thread, it looks like you've already got a DSDT from a PCG-K37...which is, in terms of BIOS, identical to the K33.

---

### Post by Ferri on 2007-09-03
> **AlfyBoy said:**
> Here you are, i hope it helps.

I know this is not the place to address problems, but if someone can point me on the right direction i would appreciate it. I got my fn keys working using this tutorial:

[http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/#comment-1113](http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/#comment-1113)

 but after updating linux headers from the automatic update service my fn keys no longer work…:confused:, is there a way to fix this? linux-headers-2.6.20-16 v: 2.6.20-16.31 on feisty 

Thanks a lot for your hard work
:guitar:
It will happen every time you upgrade your kernel.
You just need to repeat the process and it should work again.

---

### Post by lester on 2007-09-03
Vng-fs395vp-r0080j1

---

### Post by eRadaR on 2007-09-09
:)

---

### Post by andreids on 2007-09-09
VGN-FE41E
Fn key and MIC do  not work
Thank you for your effort

---

### Post by mcj0422 on 2007-09-10
VGN-N170G Ubuntu 7.10. fn and sound is working. dimmer all around is not working be it fn and keys or brightness panel applet. other thing that is not working would be  the fn and lcd/monitor out button. suspend/hibernate not sure which one it is does not really work either. at this point that is all i recognize to be a problem or to be working fine. if you need me test anything else please do not hesitate to ask.

---

### Post by AlfyBoy on 2007-09-12
> **Ferri said:**
> It will happen every time you upgrade your kernel.
You just need to repeat the process and it should work again.
Thanks!!!

---

### Post by vorlon on 2007-09-12
I hope this is the information you wanted

---

### Post by eldergod on 2007-09-13
Didn't see the VGN-FE780G on the list so here is mine.

---

### Post by IntuitiveNipple on 2007-09-14
Wow! Thanks for the continuing reports. The newer models are useful.

Sorry I've been quiet on this front for a while. I've been distracted by a combination of intense hacking on Gutsy bugs leading up to the release next month, continued analysis of the Windows SNC driver, and other projects.

I thought I'd report that I've finally discovered how to enable hardware VT (Virtualisation Technology) on Vaios (or any PC that has a Phoenix BIOS) where the CPUs have VT capability.

A couple of days ago I discovered a Phoenix utility called **symcmos** (stands for SYMbolic CMOS), a DOS program that can read and write all the extended NVRAM settings for a Phoenix BIOS. I created a FreeDOS boot-diskette and did some tests.

As a result of comparing what *symcmos* does (and its output) with the Phoenix BIOS module code I found out how to associate the correct NVRAM setting (known as a ***Token***) with the VT-enable functionality of the BIOS.

If you're interested in the full technical story you can find it in the thread [What do you know about BIOS NVRAM hacking?](http://www.wimsbios.com/phpBB2/topic9326-15.html) at **Wim's BIOS** forums.

Now I am confident of being able to enable VT safely I am working on a Linux version of *symcmos* that can be used to enable VT (and other NVRAM settings) for any Phoenix-BIOS equipped PC.

---

### Post by LT1Caprice57L on 2007-09-16
Any news on the SXBIOS front?

---

### Post by BillShepp on 2007-09-17
Here's the DSDT from a brand-new VGN-FZ190 w/Blu-ray and Nvidia graphics which I'm desperately hoping you'll be able to support - lack of suspend/hibernate and brightness control currently force me to Vista.

Curiously, the SD slot works, while the MS slot doesn't (though it does provide a notification in dmesg); this is a minor issue, however.  Fn-F2 works for mute with a nice onscreen graphic, as does volume (what process is grabbing those keys?).

Thanks for the support,

Bill

---

### Post by r3tex on 2007-09-17
> **IntuitiveNipple said:**
> Now I am confident of being able to enable VT safely I am working on a Linux version of *symcmos* that can be used to enable VT (and other NVRAM settings) for any Phoenix-BIOS equipped PC.

Holy crap! I'm cheering you on! This would be an AWESOME feature. Thank you so much.

---

### Post by vins32 on 2007-09-19
Hi,

I've recentely got a new Vaio VGN-FZ11S. Brightness control is not supported. Fn keys do not seem to work.
Here is the DSDT.... hope it helps!

---

### Post by s.kaniff on 2007-09-20
Fn Keys dont work. Memory Stick slot doesnt work. Camera works after installing the drivers. Other things that i use work.

---

### Post by jorgecabral on 2007-09-23
Here's the DSDT file from a VGN-FS115M.

---

### Post by bbeirnaert on 2007-09-23
Hi here is the dstn for a vaio VGN-SZ4VWN with bios R0111N0

---

### Post by Flumpy on 2007-09-24
This is the DSDT file of a Sony Vaio PCG-FR215M.

---

### Post by BillShepp on 2007-09-24
Not sure if this is news, but on an FZ190N using the latest Nvidia drivers from Nvidia (100.14.19) and s2disk (from package uswsusp) I'm able to hibernate and resume without incident (so far).  Still no luck suspending.

---

### Post by johnlil on 2007-09-25
Here's a real blast from the past, quite pleased as a complete newbie to get anything working at all. Function keys, camera, bluetooth all do not appear to work, suspend/resume does something not quite sure of the difference. Enjoy.

---

### Post by coca25 on 2007-09-25
DSDT for Sony Vaio VGN-FE28B

---

### Post by messenjer on 2007-09-29
Vgn-fs315b-dsdt

---

### Post by maaaax on 2007-09-29
Hi, here the DSDT for a vaio FZ11Z, hope they are still usefull.
thx a lot for your work...

---

### Post by Toufik on 2007-10-03
Hi,

I've done the upgrade to Gutsy beta. I've still some problems with my Vaio (VGN-FS315B). Is the new driver already in the kernel? Should it work?

My problems:
* none of the FN keys works
* the light for the card reader is always on (I guess it should be on only when there is a card)

Depending on your answer I'll submit a bug report or not.

Thanks

Toufik

Edit: after more investigations,
1) `$ lsmod | grep sony` gives me:
sony_laptop            32088  0 
sonypi                 23960  0 
sony_acpi               6668  0 

Strange, I thought sony-laptop should have replace sony-acpi. Am I right?

2) sony-laptop seems to NOT provide fn keys mapping, rather offers a way to map them easily. Right? If yes, how?

3) when plugging/unplugging the power, gnome-power-manament does the correct dimming of my screen AND displays a nice OSD (a nice image) showing the current brightness. Therefore I've got the feeling that all the ingredients are available to have a nice dealing of fn keys, but I cannot find any useful documentation of the whole, nor an up-to-date tutorial (I'm rather bothered of the ugly osd of fsfn). Does it exists?

---

### Post by BillShepp on 2007-10-03
On my FZ190 I've got the same three Sony modules.  I think sony-laptop is due to replace sonypi.  I'm seeing inconsistent behavior with onscreen display and FN-key handling (under KDE) - at times I'll find that Fn-F2 and the volume keys will work and show a perfect OSD.  Most of the time they have no response.  I suspect there may be some interaction with /dev/nvram permissions, but I haven't tracked this down yet, and can't determine why after some boots the Fn keys work and other times they don't.

I'm also told that 2.6.23 has support for the FZ Fn keys - I'm currently downloading 2.6.23rc9 and will report back if it improves things.

Finally, I've decided hibernate isn't working well.  It often works, but it also often ends up causing strange iwl4965 weirdness, and occasionally just doesn't work.  Does anyone have reliable suspending or hibernating working with Nvidia 8400-based VAIOs?

Bill

---

### Post by BillShepp on 2007-10-04
Further update on VGN-FZ190 after installing 2.6.23rc9 kernel (and reinstalling 100.14.19 Nvidia drivers:[LIST]
[*]Had to install ALSA (1.0.15rc3) after updating kernel.  Doing so **fixed the issue where the internal speakers still played when headphones were plugged in**.  Note that I had to add a line to /etc/modprobe.d/options: "options snd_hda_intel model=vaio"
[*]I was able to suspend successfully once using "/etc/acpi/sleep.sh force".  An additional attempt failed, but I think I may have changed something.  Still working on this.
[*]I discovered that sonypi was being loaded by /etc/init.d/hotkey-setup even though I had blacklisted it in /etc/modprobe.d/blacklist.  I commented out this line in hotkey-setup (leaving sony-laptop).
[*]Most FN keys seem to be recognized now by xev or /var/log/acpid.  Fn-F2 (mute) and the volume keys are not currently working for me; they have worked intermittently, but I've not been able to track down why they sometimes do and sometimes don't.[/LIST]Remaining big issues:[LIST]
[*]Reliable suspend and hibernate support
[*]Ability to adjust screen brightness[/LIST]Note - I used [KernelCheck]("http://ubuntuforums.org/showthread.php?t=556726") to update the kernel, it worked beautifully, makes it very easy to revert back to previous kernel.

Bill

---

### Post by skizerdthewizerd on 2007-10-05
As far as I know only my home, pgup, pgdn, end function keys work correctly. I can dim screen with Fn F5 and brighten with Fn F6, which is a little different from windows.

---

### Post by master_kernel on 2007-10-07
> **BillShepp said:**
> Further update on VGN-FZ190 after installing 2.6.23rc9 kernel (and reinstalling 100.14.19 Nvidia drivers:[LIST]
[*]Had to install ALSA (1.0.15rc3) after updating kernel.  Doing so **fixed the issue where the internal speakers still played when headphones were plugged in**.  Note that I had to add a line to /etc/modprobe.d/options: "options snd_hda_intel model=vaio"
[*]I was able to suspend successfully once using "/etc/acpi/sleep.sh force".  An additional attempt failed, but I think I may have changed something.  Still working on this.
[*]I discovered that sonypi was being loaded by /etc/init.d/hotkey-setup even though I had blacklisted it in /etc/modprobe.d/blacklist.  I commented out this line in hotkey-setup (leaving sony-laptop).
[*]Most FN keys seem to be recognized now by xev or /var/log/acpid.  Fn-F2 (mute) and the volume keys are not currently working for me; they have worked intermittently, but I've not been able to track down why they sometimes do and sometimes don't.[/LIST]Remaining big issues:[LIST]
[*]Reliable suspend and hibernate support
[*]Ability to adjust screen brightness[/LIST]Note - I used [KernelCheck]("http://ubuntuforums.org/showthread.php?t=556726") to update the kernel, it worked beautifully, makes it very easy to revert back to previous kernel.

Bill
Thanks for the KernelCheck mention!

master_kernel

---

### Post by giardn on 2007-10-08
This is the DSDT file of a Sony Vaio VGN-SZ650N.

---

### Post by trebiani on 2007-10-08
> **IntuitiveNipple said:**
> Recently I've been working on ..... **VMX (VT)** on a Vaio VGN-FE41Z.

has someone else managed to enable VT on a Sony Vaio Core2Dua Laptop? i'm using a Sony Vaio AR21S and would like to enable VT for using it with XEN and Ubuntu. Can someone help me please?

thank you in advance,
treb

---

### Post by BillShepp on 2007-10-08
Update on FZ190 suspend:

I've been able to suspend/resume repeatedly over the weekend without stability issues (running 2.26.23rc9 kernel and 14.19.100 Nvidia drivers).  I believe it may be related to my having removed "fbcon" as a boot initramfs module (though this means I get really ugly console fonts).  To suspend I'm using "sudo /etc/acpi/sleep.sh force" from a terminal window under KDE (though I have no reason to believe it would operate differently under Gnome).

Bill

---

### Post by bijan2021 on 2007-10-13
I installed Xp on my Fz190n2 but my bluetooth and function key are not working, please help me how can I fix it?

---

### Post by RedStarLabs.org on 2007-10-13
Please make FnKeys work! Thanks!

---

### Post by BattlePanic on 2007-10-13
DSDT output for VGN-FS675P/H is attached

Thanks for the wonderful work.  As an Ubuntu/Linux newbie I had some trouble figuring out how to capture the DSDT output that you're requesting.  I found a link to [[COLOR="Sienna"]_this how-to_[/COLOR]]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") buried among the replies and it explained exactly what I needed to do.  I think that posting a link to that how-to on the first page will improve this thread's usability.  Thanks again!

---

### Post by s.kaniff on 2007-10-15
Thanks for the link to the howto.. here's my dsdt according the it..

---

### Post by yesuratnam on 2007-10-16
Hi I have installed 7.1 ubuntu two weeks back on sony vaio VGN-FZ190, Function keys for mute and volume up and down are working. Brightness control is not working. I had a Nvidia 8400M GT card.  
lsmod shows sony-laptop and sonypi loaded, but found no sony scripts & directory  under /sys/class/backlight  or /proc/acpi.

Attached is the DSDT file for VGN-FZ190. Please make the function keys working

Thanks
Yesuratnam

---

### Post by bitwalk on 2007-10-16
Hi! Attached is the dump from my Sony Vaio VGN-TX2XP.

---

### Post by giardn on 2007-10-17
I posted the results of dmidecode previously with the Intel GM965 active. I have an SZ model that has two graphics cards, the Intel and an nVidia 8400GS. Would the results of the dmidecode be different if a different graphics device were enabled? Should I rerun the dmidecode with the nVidia active?

Also, previously the following info was requested:

giardn@sony:/dev$ uname -a
Linux sony 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
giardn@sony:/dev$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         62640 mWh
last full capacity:      62640 mWh
battery technology:      non-rechargeable
design voltage:          626 mV
design capacity warning: 0 mWh
design capacity low:     120 mWh
capacity granularity 1:  0 mWh
capacity granularity 2:  10 mWh
model number:
serial number:
battery type:            LION
OEM info:                Sony Corp.
giardn@sony:/dev$
giardn@sony:/dev$ sudo dmidecode  | grep 'Version: R'
        Version: R0081S5

nathan

---

### Post by Depressed Man on 2007-10-17
I would assume yes. Since part of the code has helped with things like screen brightness controls which is graphics card dependent.

---

### Post by thewall83 on 2007-10-18
Hi intuitive_nipple, are there any news about the driver?
I compiled yesterday the 2.6.23.1 kernel (and I enabled the sony-laptop module in the config) but i didn't manage to change my brightness with the Fn keys; I also tried to change the brightness with gnome-power-manager but anything happened.

Launching xev the keys seem recognized, now i would like to assign them some functions....
Can you help me?

EDIT: I have a SONY VAIO FE11H

---

### Post by LT1Caprice57L on 2007-10-18
Hate to be a nag, IN, but do we have any update on the SXBIOS stuff?

---

### Post by BillShepp on 2007-10-18
I've been in touch with the author of smartdimmer, which is what is used for channging brightness on Nvidia-based systems.  He's given me some pointers to try to track down the registers used on the 8400M via the Windows tool RivaTuner but we haven't made much headway.  Very frustrating to not be able to dim the screen...

---

### Post by webustany on 2007-10-19
**VGN-SZ61MN-R0081S5**
Everything works except the brightness control on a Fedora 8 test 3 (the webcam needs the driver, and you've got to upgrade gstreamer to 10.14.1 too). Suspend/hibernate works.

---

### Post by Sunspark on 2007-10-19
Hi, on a Vaio VGN-FS620/W the backlight did work under the Gutsy Beta CD, but not after that. I filed a bug report 152731 and today I got this reply back:

"I have a sony vaio laptop also and the path for changing the brightness
for me is at /sys/class/backlight/sony/ ; as a workaround i use "echo
$value > /sys/class/backlight/sony/brightness" does that works for you
guys? Do you have an entry regarding the laptop_panel in hal-device-
manager?"

I only have access to the laptop once a week. Maybe one of you folks could test that snippet to see if it gets your backlight working, and maybe also figure out what changed between the beta and the release that stopped it from working.

---

### Post by dracomordag on 2007-10-22
alright, i may be stupid, but I can't find this driver anywhere... is it still in development or something? I'm on a VAIO FZ with Gusty Gibbon, and I'm still working on getting the webcam, headphone jack, and the function keys to work. Not to mention the S-Video out for a dual-screen setup.

any help would be most appreciated.

---

### Post by webustany on 2007-10-22
It's in the mainstream kernel, you must have it in your gutsy kernel

---

### Post by steelie on 2007-10-22
Here's a dsdt file for a Sony Vaio VGN-N11S/W

---

### Post by Depressed Man on 2007-10-22
Dunno if it's in .22 (Gutsy's kernal) but I know in .23 the Sony stuff is in (FN keys should work in it)

---

### Post by dracomordag on 2007-10-22
> **webustany said:**
> It's in the mainstream kernel, you must have it in your gutsy kernel
okay, well in that case it's just not doing anything.

---

### Post by galland on 2007-10-23
Hi guys,

This is my DSDT for my Sony VGN-AR21B:
[ATTACH]47481[/ATTACH]

I include also several information on my BIOS:
[ATTACH]47482[/ATTACH]

Working features :)
[LIST]
[*]mute button
[*]sound volume up
[*]sound volume down
[*]multimedia play/pause
[*]multimedia stop
[*]multimedia previous track
[*]multimedia next track
[*]wireless, supported by the kernel's driver for 3125 INTEL/pro wireless cards
[*]SD card, see [http://www.arakhne.org/spip.php?article47](http://www.arakhne.org/spip.php?article47)
[*]MotionEye webcam, see [http://www.arakhne.org/spip.php?article47](http://www.arakhne.org/spip.php?article47)
[/LIST]

Not working features :confused:
[LIST]
[*]buttons S1 and S2
[*]DVD eject button
[*]all Fn keys (brightness up/down, screen switch, zoom, suspend...)
[*]AV MODE button
[/LIST]

The problems are the same on the Feisty and on the Gutsy distributions.

Regards.

---

### Post by roledred on 2007-10-24
This is my configuration file

---

### Post by rwind on 2007-10-24
From [http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/](http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/)

Here is my file.


My laptop:

Sony VGN-FS920


None of my function keys work. :/

---

### Post by zamurai on 2007-10-25
Hi,

I just found out about this post. Would like to know how to I get this "dsdt" thing? Sorry for the dumb question. I'm really a beginner.


Thankx

---

### Post by galland on 2007-10-25
Two ways to obtain your DSDT:

1) see [http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/](http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/)

2) do the following commands:

$> sudo apt-get install iacl
$> sudo cat /proc/acpi/dsdt > sony_vaio_vgn_ar21b.dat
$> sudo iasl -d sony_vaio_vgn_ar21b.dat
$> gzip sony_vaio_vgn_ar21b.dsdt

---

### Post by LT1Caprice57L on 2007-10-25
k, finally figured out this DSDT thing.

EDIT: Forgot to attach the file.  GO ME! ^_^

---

### Post by spier on 2007-10-25
> **rwind said:**
> ...
Sony VGN-FS920

None of my function keys work. :/

Got my FS series FN keys working following  this[howto]("http://ubuntuforums.org/showthread.php?t=309533"). First applied it on Edgy, reapplied after Feist & Gutsy upgrades!

---

### Post by rwind on 2007-10-26
Wow, I got my brightness keys working (FN+F5/F6) but no volume control. Is there a way to get a graphic display to show on screen when you press the buttons?

---

### Post by zamurai on 2007-10-26
> **galland said:**
> Two ways to obtain your DSDT:

1) see [http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/](http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/)

2) do the following commands:

$> sudo apt-get install iacl
$> sudo cat /proc/acpi/dsdt > sony_vaio_vgn_ar21b.dat
$> sudo iasl -d sony_vaio_vgn_ar21b.dat
$> gzip sony_vaio_vgn_ar21b.dsdt




Hi, when I do the 1st command I got this:

xxx-ubuntu:~$ sudo apt-get install iacl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iacl



what is iacl?

---

### Post by derick on 2007-10-26
VGN-AR51SU laptop.

Volume and mute buttons work.  Multi-media, function and eject buttons dont.

---

### Post by raphenry on 2007-10-27
I have done the bios read on my Sony Vail, PCG-FXA49, it is as follows: EDIT this has the most recent update of Ubuntu, updated today.

# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Sony Corporation
        Version: R0114K5    
        Release Date: 02/24/2002
        Address: 0xE68D0
        Runtime Size: 104240 bytes
        ROM Size: 512 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                ACPI is supported
                USB legacy is supported
                AGP is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
   
I hope that this helps for the building of new drivers...
My problem is that my monitor will not show proper resolution, it will not go to 768x1024 like it is supposed to.

Raph

---

### Post by jee rom on 2007-10-27
Here is the VGN-B1VP (aka PCG-5B1M) table.

S1 & S2 buttons send same keycode, and same keycode on press or release.

---

### Post by galland on 2007-10-27
> **zamurai said:**
> Hi, when I do the 1st command I got this:

xxx-ubuntu:~$ sudo apt-get install iacl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iacl



what is iacl?

Sorry, this is iasl (the Intel ASL compiler/decompiler)

---

### Post by zamurai on 2007-10-27
Finally got it, here's mine:

[ATTACH]48023[/ATTACH]



I'm using Vaio FS25GP. None of the Fn key works, and I can't even adjust my brightness. 

:cry:

---

### Post by schiebcn on 2007-10-28
hey there :)

I have a sony vaio **VGN-TX3HP/W aka PCG-4H1M (bios version R0022N3)**, a german model. dsdt file is attached.

working out of the box (running gutsy with 2.6.22-14-generic):
* brightness -/+ on fn+f5/f6
* hibernate on fn+f12 or closing the lid (very slow, producing some error messages concerning usb not going down correctly :/)
* wlan and bluetooth on/off when using the button in the front
* opening the cd/dvd drive on using the corresponding button next to the power-button

not working:
* fn+f10 for zoom (who needs that at all?!?)

not tested:
* fn+f7 for vga out
* magic gate card reader

mute and volume -/+ are working by hitting fn+f2/f3/f4... but **sony has own buttons in the front for that issues on the tx-models** (and there aren't any symbols on f2 to f4 ;)).
unfortunately, these buttons in the front aren't working :/
volume +/- produce the same keycode (using xev), mute isn't producing a keycode...
any ideas?

---

### Post by Ferromán on 2007-10-28
I've read all the line and i couldn't find my model. Here you have the info file.
Thanks a lot for the great work being done there.

---

### Post by Tlarhices on 2007-10-29
Here is the file from my VGN-FS485B, hope this can help.
Continue the great work.

---

### Post by drryu on 2007-10-30
Great Effort. Please keep up the work

Here is my file. Fn Keys don't work

---

### Post by choch on 2007-10-30
VGN-N11S-R0030J4

everything working except fn keys above f4.  Memory stick slot not tested.

---

### Post by Junx on 2007-10-30
Here's the .dsl for a VGN-FS550 since I don't see it on the technical page.

---

### Post by olwe on 2007-10-30
I've got a new VGN-NR120E, the new low-end machine. How do I get the dsdi file? BTW, sleep or screen saver tends to lock machine. Also, the sound wants to come out of both the speakers and the headphones... Here's the BIOS info:

$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0130J9
        Release Date: 07/18/2007
        Address: 0xE6C60
        Runtime Size: 103328 bytes
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 13.0
        Firmware Revision: 13.0

---

### Post by tscook on 2007-10-31
I just got an VGN NR120E and it has a horribly broken DSDT setup, attempting to recompile it brought up **200** errors before it halted. It checks first for Vista, then for XP then anything else, including GNU/Linux. If you were to boot with the acpi=off option, the headphones and speakers would work as they should. I've tried to attempt to fool the DSDT with acpi_os_name="Windows 2006" or acpi_osi="Windows 2006" but they both resulted in kernel panics....

---

### Post by k-o-x on 2007-11-01
Here is the ACPI dump for my VGN-FS415S
Hope it will help

---

### Post by grouperman on 2007-11-02
PCG-F520-R0115K1

This laptop is very old. It was made back when rocks were soft. 

The f keys from 1 to 5 work, so at least I can control the sound. The vaio was given to me with dead batteries, so no problem with power management issues. Running Gutzy ok, but limited to 800 x 600 resolution.



Thanks for helping.

---

### Post by danielwen on 2007-11-02
Here is the ACPI dump for my VGN-FE21S.

The volume- and mute-buttons are working fine and when I press the Windows-key instead of the fn-key I can even enable Num-lock. But when it comes to brightness, the Win-key workaround doesn't help. Once upon a time, I think it was on Dapper Drake, I had those damn keys running, but can't remember how I did it or the way I did it doesn't work any more with Gutsy Gibbon.

Thanks for the work!

---

### Post by gsoundsgood on 2007-11-03
here it is...

---

### Post by ricardo.chavez on 2007-11-03
Hello everybody.
Since my laptop's model (VGN-FJ270) does not appear in the 'Sony Notebook Control, ACPI Method Analysis' page, here is my contribution:

Things that work: wireless LAN, touchpad (w/scroll)
Things that do not work: FN keys (after installing fsfn, the brightness keys worked, although the control was not as fine-grained as in Windows), built-in camera (though, after installing Gutsy, the LED next to the camera blinks once every time I boot into Ubuntu, so I'll give it a try later).
I haven't tested the other features (memory card reader, etc.)

Hope this helps, and thanks in advance!

Update: the built-in camera works like a charm in Gutsy *thumbs up*, just had to install Camorama to test it.

---

### Post by makrook on 2007-11-04
Hi,
I'm a little desperate because currently I've foud absolutely NO WAY to dim my lcd.
beside that Fn+F2,3 & 4 are working OK, sdcard reader as well, don't really know about the rest.
so I can't really use linux (I'm on gutsy using kernel 2.6.22)
 here's my dmidecode and the DSTD is attached, please, please keep up with your work.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0130J9
        Release Date: 07/18/2007
        Address: 0xE6C60
        Runtime Size: 103328 bytes
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 13.0
        Firmware Revision: 13.0

---

### Post by fortegas on 2007-11-05
Vaio VGN-FZ21S

Hi, I have been using Gutsy and can't control my lcd brightness. Can this help me?

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R1120J7
        Release Date: 07/04/2007
        Address: 0xE6C60
        Runtime Size: 103328 bytes
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 12.0
        Firmware Revision: 12.0

Thanks you

---

### Post by cref on 2007-11-05
I have the same problems. I can not adjust the brightness on my Vaio SZ56. But the fn+f2,f3,f4(control volume works well). I'm on Gutsy 7.10 in kernel 2.6.22. Hope the update driver may help. 
I have another question. Shall we load both sonypi and sony_laptop in the file /etc/init.d/hotkey-setup? The sony_pi module make some error when booted like this

Nov  4 22:46:18 PhobosL kernel: [   18.968000] sonypi: Sony Programmable I/O Controller Driver v1.26.
Nov  4 22:46:18 PhobosL kernel: [   18.968000] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
Nov  4 22:46:18 PhobosL kernel: [   18.968000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
Nov  4 22:46:18 PhobosL kernel: [   18.968000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
Nov  4 22:46:18 PhobosL kernel: [   18.968000] sonypi: device allocated minor is 63
Nov  4 22:46:18 PhobosL kernel: [   18.968000] input: Sony Vaio Jogdial as /class/input/input6
Nov  4 22:46:18 PhobosL kernel: [   18.980000] input: Sony Vaio Keys as /class/input/input7
Nov  4 22:46:22 PhobosL kernel: [   23.528000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Nov  4 22:46:22 PhobosL kernel: [   23.580000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Nov  4 22:46:22 PhobosL kernel: [   23.632000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Nov  4 22:46:22 PhobosL kernel: [   23.680000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Nov  4 22:46:22 PhobosL kernel: [   23.708000] sony-laptop: Sony Notebook Control Driver v0.5.
Nov  4 22:46:22 PhobosL kernel: [   23.708000] input: Sony Vaio Keys as /class/input/input8
Nov  4 22:46:22 PhobosL kernel: [   23.708000] input: Sony Vaio Jogdial as /class/input/input9
Nov  4 22:46:22 PhobosL kernel: [   23.804000] Failure registering capabilities with primary security module.

After all, below is my dsdt file. 
Sony Corporation
Product Name: VGN-SZ56_C
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0101S5
        Release Date: 09/05/2007
        Address: 0xE51A0
        Runtime Size: 110176 bytes
        ROM Size: 1024 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 10.1
        Firmware Revision: 10.1

---

### Post by cref on 2007-11-05
sorry, forgot the dsl file

---

### Post by jakal323 on 2007-11-06
Here's a decompiled DSDT from a PCG-K23.

---

### Post by linhjvn on 2007-11-08
Vaio VGN-FS 550

The hotkey is not active (Fn button), please send the hotkey's driver to me, thanks a lot. Please help me.

---

### Post by Franck Gillé on 2007-11-09
Hi i have vgn-AR51M with gutsy, brightness control don't work, no fn shortcuts functioning
The volume and mute work, eject S1 S2 don't work
Hope this helps. If I can give more info on my laptop that may help please let me know.

---

### Post by nexius on 2007-11-10
Ok, This is just mine dsdt.dat file. For an SZ18M. Everything seams works grate except for hyberantion, and lcd brightness dimmer...

I hope this can help to fix these problems.

Nex

---

### Post by npendar on 2007-11-10
Here is my dsdt file. I have a VGN-FS680_W with R0040J1 bios version. I'm running gutsy with kernel 2.6.22-14-generic.

At boot time, I get

[    9.915534] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

System is stable, but hibernate corrupts swap (changes UUID in fstab) and standby doesn't work. Fn keys don't work either.

Thanks

---

### Post by handspringer on 2007-11-11
First: Thank you very much for all your endeavors!

Attached ist my dsdt file (Sony Vaio VGN-FS115M, german model). 
Unfortunately NOT ONE of the FN-Keys works.

F2 = speakers on/off
F3/F4 = volume down/up
F5/F6 = brightness down/up
F7 = external monitor
F10 = Zoom
F12 = standby

So I am very interested in the new hotkey driver.

Hope this helps...

---

### Post by andiheinz on 2007-11-12
Greetz from Hamburg
Would be nice to get vmx working
Here's mine:

---

### Post by linhjvn on 2007-11-16
VaiO VGN-FS 550
Fn key don't work, please help me

---

### Post by viciousvex on 2007-11-16
Hi!

Thanks for your effort to get these things working. Just wanted to supply additional information for my Sony VAIO TX2XP notebook, but unfortunately I don't know where to find the information you're looking for.

The only thing I found in this thread is the dmidecode part - but that does not seem to be the data you're expecting.

Can someone please guide me to the info about the necessary steps to take?

Regards
vex

---

### Post by francholi on 2007-11-16
sony vaio vgn-fz18m, acquired in Spain on September 2007. Now i'm using ubuntu 7.04 with no problems. but....
The screen bright controls doesn't work, and the VT option is hidden and disabled by our friends of sony.
The rest of the components run smoothly.
Here goes de DSDT files.
Thx for your efforts.
I think that even with a small disclaimer at the end of some web page, Sony folks doesn't have the legal rights to disable this huge capability of Intel microprocesors.
They should put a big letter on the notebook and the websites of sony saying that they doesn't support this technology on the most important part of the computer.... 
please forgive my english....

Francisco Lopez.

---

### Post by viciousvex on 2007-11-18
Here is the DSDT file for Sony Vaio TX2XP/B.

Regards
vex

---

### Post by ephemy on 2007-11-19
here's one for my sony piece of sh173....I don't think I'll ever buy a computer from them again (thankfully work paid for this one...!)

---

### Post by merlinof2 on 2007-11-19
First, I love my Sony.  It's a VGN-TX650P.  It had XP on it originally.  I used the Gentoo recover disk to repartition after defragging the windows into one section of the drive.  then installed ubuntu 7.04.  smooth as silk. now I've got a dual boot system on this 2.5 pound notebook. amazed at how much worked.  then upgraded to 7.10.  more works
bluetooth works
wireless lan works
lan interface works
FN keys
   brightness up
   brightness down
   break
   pause
audio works both play and record
firewire 1394 works, captures from Digi Vid cam cleanly

what doesn't work
LCD to external monitor with FN key
Magnify (FN +F10) but it doesn't seem to do anything under windows either

the only thing I REALLY want to work that I can't get working is my Sierra Wireless 860 card for Internet.

attached my DSDT file.

---

### Post by jehuty on 2007-11-19
Hi i have a vaio VGN-A497XP and pretty much nothing works, only the fn key that changes the brightness, the mute sound button, and one of the up/down buttons (since ubuntu seems to detect each one as the same).

BIOS Information
        Vendor: American Megatrends Inc.
        Version: R0080F2
        Release Date: 03/14/2005
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 512 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

don't know if this is really useful, I would like to know how can i create those DSDT files that everyone seems to be posting so i can be of assistance.

---

### Post by Chozac on 2007-11-24
Hi

This is my DSDT for VGN-FZ21S
FN key don't work except media control

---

### Post by zecamarada on 2007-11-24
UBUNTU 7.04 upgraded to 7.10 *GUSTY
... 
Fn keys dont detected on Gusty intall,but its ok on sound and brightness with sony_acpi and FSFN... error on FN+F7  (lcd->CRT) Fn+F10 (zoom) and Fn+F12 (stand by)...
Wireless not detected and need install, but its fine!

Error to use dual head on monitor CRT, I can use only CLONE mode with resolution problem...

Sorry of my english

---

### Post by Convert on 2007-11-26
Sony VAIO laptop model VGN-SZ650NC, Bios R0081S5.

New Linux user here.  Forced to dump that thing they call an OS that came with the laptop (Vista) and figured it was a good time to wean myself off of XP.  It's somewhat difficult to tell if some things are working or not as there is no help that I can find to say how to go about using the hardware that is built-in (example, what program should I use to try out the built-in motion eye camera?).

I know for sure that the blue function keys for the sound volume work, and know for sure that the brightness function keys do NOT work.  Wireless works and the system found my Brother printer on my home network.  Bluetooth seems to work but the device IDs that are listed cannot be connected to (for example, it always says ""obex://[00:16:20:7d:4a:8d]" is not a valid location." for my cell phone that is listed).  Other than that, I'm still exploring.

One issue I have that is probably related to proprietary Sony hardware somehow (and something that I want to fix first) is that the sound does not work with any headphones.  That is, plugging in any headphone has no effect.  The headphone does not output any sound and the internal speaker continues to output the sound.

There was some program that I ran that stepped through a few hardware things and "tested" them but I can't seem to find that same program anymore.  I mention this because one thing it tested was the sound -- it attempted to play a sound and asked if it worked -- it did not.  The strange thing is that the sound does work on the laptop, it just didn't work with this particular program.  It was probably using a different driver than the one the system is using.  Too bad I can't find the program anymore.

Hopefully the attached DSDT file will be helpful to someone.

---

### Post by webustany on 2007-11-27
For the headphones to work you might try adding those two lines to /etc/modprobe.conf :
alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0 model=vaio

actually you should already have the first, maybe the second. I had to add the third (I'm using fedora)

BTW, I also enabled ahci and VT-X on mine, but ahci prevents suspend from working so I only left VT-X. I can post the explanations if needed.

---

### Post by ntetreau on 2007-11-27
@webustany: Please post the explanations if you can.

@convert:  good to have you on board.  Laptops in general are always a bit difficult to get perfectly working and that seems right in pretty much every OS. You have the added difficulty that your machine is very new are somewhat rare. With that said, your machine will most probably work fine in the end but you may need to experiment a bit or wait a little for newer versions of drivers and programs to come out. In the mean time, you can check out the following link. The guy as the same machine as yours and got pretty much everything working but he was at least an "intermediate" linux user (you'll know what I mean when reading his page!).  You can always contact him directly if you really want to dive in, I'm sure he'll be helpful!

[http://moelhave.dk/gnulinux-ubuntu-gutsy-gibbon-710-on-the-sony-vaio-sz6-series/](http://moelhave.dk/gnulinux-ubuntu-gutsy-gibbon-710-on-the-sony-vaio-sz6-series/)

Also, if you have further problems, you should start your own threads as this one is meant to be a direct link between the sony vaio users and the developer of the vaio kernel module only.

---

### Post by acketon on 2007-11-28
I have a Sony Vaio pcg-v505ec

I don't see instructions on how to generate the file with the info you need in the first post...was it removed? I'd just like to help out if you need.

Most of the function already work and have for the past year, I believe using the sonypi driver. 

I currently have working sound keys & brightness keys for the most part.

---

### Post by mdoube on 2007-12-03
Hi Vaio kids

I have a new SZ650N, which is quite nice really.  Having the usual new-laptop-teething-problems though (Ubuntu Gutsy, updated)

Screen dimmers don't work, suspend doesn't work, are the first things... display drivers a bit rough.  Here's a DSDT though, for your enjoyment.

Looking forward to full support of the bells and whistles, though to be honest I really got it for the carbon fibre chassis not the webcam!

Cheers

Mike

---

### Post by webustany on 2007-12-03
Suspend and display drivers worked out of the box for me (fedora 8). For the screen dimmer, there's more hope (but it still does not work) with the bios sony released for the xp downgrade

---

### Post by webustany on 2007-12-03
I meant fedora 8, didn't think of the smiley :-p

---

### Post by mdoube on 2007-12-03
This is a really minor thing: how come the WLAN LED stays off, while the bluetooth LED goes on when either bluetooth or WLAN are active?  My old acer has a WLAN (bcm43xx) LED that would flicker on data transfer, which was cool.

Mike
VGN-SZ650N

---

### Post by mdoube on 2007-12-03
@Convert: snap!  Thought I'd give Vista a chance but it was bloated and annoying so I dumped it.  The recovery partition was handy to put Ubuntu on.

---

### Post by GVaio on 2007-12-07
Sony Vaio PCG-SRX77: **Attempt to Hibernate actually _BREAKS_ the swap space.**  
If I go into hibernate mode it looks like it's trying to do a "hibernate" but ends up doing more of a total "powerdown".  Then at power-up it looks like a standard cold-start and during usplash one of the text messages is "[COLOR="DarkOrange"]Activating swap...[/COLOR]    [COLOR="Red"]failed[/COLOR]".  
Sure enough, after login, doing "*[COLOR="Blue"]free[/COLOR]*" shows no swap space allocated and I have to used [COLOR="Blue"]*mkswap*[/COLOR] and [COLOR="Blue"]*swapon*[/COLOR] to fix it.
Suspend mode (System/Quit/Suspend) works ok, as do Fn keys for screen brightness and volume.  Have not tried external monitor.

---

### Post by biene on 2007-12-13
VAIO VGN-FE890E
R0200J3

Thank you for your work!

---

### Post by Soilman on 2007-12-14
Here is a 2 1/2 year old subcompact model. VGN-T350P on front and PCG-4E1L on base. I think the P is for XP-Professional not sure though. 
Memory Stick Light always lit.

---

### Post by AirLancer on 2007-12-19
Hi,
I got a VGN-BX570B

sorry forgot the attachment.

---

### Post by junkMonkey on 2007-12-20
Most everything seems to work out of the box on Gutsy. Nice work. My webcam (motion eye) and its associated 'capture' button aren't working. However, the wireless card worked from the start!!! Weeee Haaaa! Please find attached my dsdt for the VGN-CR220E.

Thanks and Good Job!

---

### Post by dogscoff on 2007-12-21
I have a wobbly old vaio pcg-fx701 running Xubuntu gutsy (upgraded from Feisty.) 

Xubuntu installed OK from the Feisty alternate CD, but wouldn't run the Ubuntu Feisty Live CD at a usable speed, and wouldn't install from it at all. Once Xubuntu was in, everything appeared to work well enough. It picked up the wireless card in my PCMCIA slot straight away. 

Fn keys didn't work out the box, but got the volume controls working with the following Xmodmap:
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute

When I first installed xubuntu and tried futzing with the screen resolution, I had a problem with a little square of horizontal black lines appearing in the top left corner that would not go away, and persisted after a reboot. I fixed this by simply deleting the file .config in my home folder.

The graphics card (ATI Rage M1 Mobility, I think) won't let me switch the hardware acceleration on, so 3D functions are painfully slow (even screensavers are clunky). Haven't found a fix for this.

The keyboard is a little wierd too, but that's probably my fault: there's something strange going on with deadkeys that won't let me make apostrophes without the alt-gr key.

I'll happily provide you with one of those dsdt files if you want it, how do I generate one?

---

### Post by junkMonkey on 2007-12-21
> **dogscoff said:**
> I have a wobbly old vaio pcg-fx701 running Xubuntu gutsy (upgraded from Feisty.) 

Xubuntu installed OK from the Feisty alternate CD, but wouldn't run the Ubuntu Feisty Live CD at a usable speed, and wouldn't install from it at all. Once Xubuntu was in, everything appeared to work well enough. It picked up the wireless card in my PCMCIA slot straight away. 

Fn keys didn't work out the box, but got the volume controls working with the following Xmodmap:
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute

When I first installed xubuntu and tried futzing with the screen resolution, I had a problem with a little square of horizontal black lines appearing in the top left corner that would not go away, and persisted after a reboot. I fixed this by simply deleting the file .config in my home folder.

The graphics card (ATI Rage M1 Mobility, I think) won't let me switch the hardware acceleration on, so 3D functions are painfully slow (even screensavers are clunky). Haven't found a fix for this.

The keyboard is a little wierd too, but that's probably my fault: there's something strange going on with deadkeys that won't let me make apostrophes without the alt-gr key.

I'll happily provide you with one of those dsdt files if you want it, how do I generate one?

I used the instructions on this page:
[http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/](http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/)

---

### Post by c72578 on 2007-12-22
PCG-FX802(DE)-R0121K5

Here is the dmesg output:
sonypi: Sony Programmable I/O Controller Driver v1.26.
sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
sonypi: ioport 0x1080 busy, using sony-laptop? if not use check_ioport=0
soypi: failed to request ioports
sonypi: probe of sonypi failed with error -16

---

### Post by yogaman69 on 2007-12-28
Hi,

I'm all new to Ubuntu (Gutsy) and have been struggling with a few things on my VGN-T17GP. one of them is the volume controls not working. mute works, but volume up and down do the same thing. tried to configure in the keyboard shortcuts preference, but they give the same 'signal'.

another problem is with CPU temperature being higher than under XP and battery life very short. any advice someone would have would be much appreciated.

good luck with your project

---

### Post by vedel on 2007-12-29
Here is the information from my FZ21E (with NVidia GeForce 8400M GT) : VGN-FZ21E-R1120J7.tar.gz

I'm still busy with setting up Ubuntu 7.10 Gutsy Gibbon).
I can already report that my headphones are not working (still need to examine this issue)
I connected a second monitor (Acer AL1921) and altered the xorg.conf to work in twin-view (see info in attached file).
The twin-view seems to work but currently I'm struggling with a problem in the firefox web-browser :
When scrolling through a web-page, the text is getting unreadible (seems like the screen refresh isn't working properly). When activating the reload-page icon, everything gets refreshed properly. I'm looking on the Internet for some clues to resolve this issue, so far without result.
Does anyone has a hint ?

Thanks !

---

### Post by Nepherte on 2008-01-02
Here's the acpidump of my laptop: Sony vaio sz61xn/c:

---

### Post by webustany on 2008-01-02
For the sz6 owners (and maybe others), the xbacklight utility can set the backlight intensity on my sz61mn/b

---

### Post by Nepherte on 2008-01-02
I can confirm that, but it is an intel vga specific tool. So it doesn't work for the nvidia vga.

---

### Post by mdoube on 2008-01-02
xbacklight works in Gutsy for the Intel (stamina) adapter but not the nVidia (speed) adapter, nor in Hardy alpha-2, on the SZ650N (US model similar to the British SZ61's).  This is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888](https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888)

Mattia knows about the problem too:
[http://www.linux.it/~malattia/wiki/index.php/Sony-laptop#Brightness](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop#Brightness)

---

### Post by sk0rp10 on 2008-01-02
Here is DSDT for VGN FE 11 S

note: sony_laptop does not recognize and load fnkey sys file on this model.

Hotkey events are not captured. 

Using: Kubuntu Gutsy.

---

### Post by blekos on 2008-01-03
Hi and excuse my ignorance,
I have a sony vaio sz3p and never needed to install xbacklight. Only spicctrl.
The Fn+Increase/ Decrease brightness works flawlessly.

Could you explain about xbacklight?

Thank you.

P.S running dual boot XP & Kubuntu 7.10

---

### Post by mdoube on 2008-01-03
[http://packages.ubuntu.com/hardy/x11/xbacklight](http://packages.ubuntu.com/hardy/x11/xbacklight)
"xbacklight is a simple command-line utility to set the backlight level using the RandR 1.2 BACKLIGHT output property."

It's a method to control the backlight for those of us with newer Vaios that aren't yet supported fully by default - so far, xbacklight is the only method I've found that can change screen brightness on the SZ6 (and with the caveats mentioned above).  If spicctrl works, you don't need to install xbacklight.

---

### Post by 0rg on 2008-01-03
Hello i have a VGN-NR180E and here is my DSDT field
See you.. have a nice day..
Salute from Argentina.

---

### Post by djerius on 2008-01-05
Here's another one:

---

### Post by psyeye on 2008-01-07
Hi!

Is there still interest in DSDT's from Sony Vaio Laptops?
I recently bought a Sony Vaio **SZ61MN/B** and a quick search in this thread showed up nothing on that particular model.
Since the brightness keys do not work when using the nVidia gfx chip I'd be glad to be of any help if there is any interest.

regards,
psyeye

---

### Post by chiacchio on 2008-01-07
I have exactly the same model of your notebook (VGN-SZ61MN) and actually fn keys and internal mic are still not working. I don't know how to create my DSDT to upload here otherwise I'd have done it!

---

### Post by steeef on 2008-01-07
I've got a VGN-SZ680N. Volume/Mute F-keys work, brightness keys do not, power button doesn't work.

---

### Post by mdoube on 2008-01-08
psyeye and chiacchio:
Instructions for getting your DSDT are here:
[http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/](http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/)

You can also get your BIOS version by looking at the output of:
$ sudo apt-get install dmidecode
$ sudo dmidecode -t bios

---

### Post by psyeye on 2008-01-08
Here goes my DSDT...

...if I can be of any help, just let me know!


regards,
psyeye

---

### Post by chiacchio on 2008-01-08
Ok, thank you very much for your work!!

Here follows my dsdt. Similar to the psyeye's...

---

### Post by Seeed on 2008-01-08
Here's my DSDT, hope this helps.

---

### Post by bugmenot2345332 on 2008-01-09
Sony Vaio VGN-AR41E

---

### Post by wiloland on 2008-01-09
Hi, 
I think I'm the only one who own this model: pcg-fr315S
Cordially

---

### Post by unit3 on 2008-01-09
I've got a brand new VGN-CR205E (I think the E is a BestBuy specific model). Everything works except that sleep and hibernate do not seem to work at all with any tools (default, uswsusp, pm-utils), and the LCD brightness keys don't do anything. Hopefully this info will help get those fixed for Hardy.

---

### Post by stasyancheg on 2008-01-09
Hope my .dsdt file will help  all VAIO owners.

---

### Post by murmel on 2008-01-09
Sweet! 

And here is my dsdt-file.

---

### Post by philhow on 2008-01-10
VGN-NR110E
Volume and Mute Fn's work
Brightness Fn's don't work
Lid switch works
Network does not work
Switching between monitors does not appear to work

---

### Post by philhow on 2008-01-10
Forgot to make the attachment to the last post. Here it is.

---

### Post by psyeye on 2008-01-10
Hi all,

I'm not so sure if this is the right place to ask - I'll try nonetheless but will open a new thread if requested.

Using the current 8.04 release at least I get ACPI events when pressing the FN+brightness keys! But the script /etc/acpi/sonybright.sh relies on the existence of /sys/class/backlight/sony/actual_brightness, which is not there.

Is this worth a bug report?

regards,
psyeye

---

### Post by laurax17 on 2008-01-15
hello,

perhaps this post is a little late, but I have a vaio laptop- a VGN- TX850P, which I notice was not accounted for on the tables on the posted link for the technical analysis.  I am a complete newbie when it comes to ubuntu (and many techy things), and am not sure if this model would have much variation from the regular TX850 (which there is information for).

If you do need DSDT info for the VGN- TX850P, I would be happy to provide it, but would maybe need an explanation of how to find this information (a google search on this topic was way too complicated).  Thanks!

---

### Post by kompas on 2008-01-16
Owner of a Vaio VGN-NR110E also here, successfully followed the immensely informative posts here to get everything working.. touchpad, wireless card, and basic graphics. The screensavers look great and graphics card seems to be working, but I can't activate desktop effects!

Is there anyone on this forum who might have the knowledge  to help me activate this?

---

### Post by remarks on 2008-01-16
A rare model (maybe)... I think it was only released in Tawian. VGN-SZ46TN

---

### Post by TJSNY on 2008-01-18
Please pass this info along.

I also have a VGN-NR110E running Ubuntu 7.10 64 bit.
I got the wireless adapter working using ndiswrapper - but I get no LED on the switch on the front of the laptop - hence 0% signal strength.

Any help you can provide would be great.  I hate being tied down to a ethernet cable..

Thanks in advance!

---

### Post by tuatha on 2008-01-19
Hi,

Couldn't see any FZ laptops at [http://tjworld.net/snc/](http://tjworld.net/snc/) so here are the details for my new FZ21S.

It has SNC only, spicctrl does nothing & smartdimmer errors with:

init_nvclock() failed!

Method Summary from the file:

sg@sg-vaio:~/Documents/sys\> egrep 'Method.*\([A-Za-z]' VGN-FZ21S_R1120J7_DSDT.txt | awk '{print $2}' | tr '(,' '  ' | sort -u 
 AINT  BRTN   BRTW  CBMF  CSXB  DBGC  EAWK  GBDA  GDCK  GDDI  GDMA  GECR  GETB 
 GETF  GETP  GETT  GHDS  GLID  GNOT  GSCI  GSNE  GWDP  HKDS  LSDS  NCPU  NVIF  P8XH 
 PARD  PDRD  PHDD  PHS  PHS0  PHSB  PHSD  PHSW  PNOT  PSTS  PWAK  RBMF  RPPC  RSBI 
 SBCB  SDMA  SECR  SETP  SETT  SN00  SN01  SN02  SN03  SN04  SN05  SN06  SN07  SNAV 
 SNCM  SNF0  SNF1  SNF2  SNF3  SNF4  SNF5  SNF6  SNF7  SNFC  SNFD  SNFE  SNFF  SNGN 
 SODV  SSNE  STCS  TRAP 

Hope this helps.

---

### Post by artful on 2008-01-22
I've just joined the forum, here is output from my PCG-K115M with R0110X1 bios.  Hope this helps

ubuntu@ubuntu:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R0110X1
        Release Date: 05/19/2004
        Address: 0xE3250
        Runtime Size: 118192 bytes
        ROM Size: 512 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                8042 keyboard services are supported (int 9h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

---

### Post by andresmontanez on 2008-01-23
Hi All.

I have a Sony Vaio VGN-NR160, EVERYTHING works FINE (wifi, sound, eth, mmcards).
The ONLY ONE THING that is not working is the backlight manager; not even touching it in the /proc.

Any ideas? Any fixes? Any fixes in soon releases?

I had tried the other aproaches (the sh to bash; etc) but this modes doesn't save the backlight in sony/video.

Ideas?

Thanks a lot!

---

### Post by linuxmangr on 2008-01-26
Hi All.

I test  a Sony Vaio VGN-BX195VP, EVERYTHING works FINE (wifi, sound, eth,other things).
The ONLY ONE THING that is not working is the backlight manager; F3,F4 volume manager,F5,F6 light manager, I cant find how make it to work but I get following this guide[ DSDT]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/")

the dsdt 

Any ideas? Any fixes? Any fixes in soon releases?

i upload attached file .

---

### Post by linuxmangr on 2008-01-27
> **econlab said:**
> Hi All.

I test  a Sony Vaio VGN-BX195VP, EVERYTHING works FINE (wifi, sound, eth,other things).
The ONLY ONE THING that is not working is the backlight manager; F3,F4 volume manager,F5,F6 light manager, I cant find how make it to work but I get following this guide[ DSDT]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/")

the dsdt 

Any ideas? Any fixes? Any fixes in soon releases?

i upload attached file .
Ok, I follow the DSDT guide and load the F5 and F6 to work for the brightness but not work sound dow and up F3 and F4 and if some one have info about F7 to send to LCD answer me please .

---

### Post by vishketan on 2008-01-27
Hi!

From my new Sony Vaio VGN-SZ483N. I did not see this entry so I decided to post it here. 

Brightness and volume controls work (on a live CD). Haven't tested the rest. 

vishy

---

### Post by angelo costa on 2008-02-10
Hi, i have a Sony Vaio VGN-CR21S

The result of: sudo dmidecode -t bios

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Phoenix Technologies LTD
        Version: R1100Q0
        Release Date: 10/18/2007
        Address: 0xE72F0
        Runtime Size: 101648 bytes
        ROM Size: 1024 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 10.0
        Firmware Revision: 20.1

The S1 and S2, Fn keys arent working, capture button isn't working. All the other functions are ok.

---

### Post by giacomo.fiorin on 2008-02-18
My Vaio is a SZ680, using debian sid, 2.6.24.  All Fn keys are mapped correctly to ACPI events, the S1 and S2 programmable buttons are mapped to the same event,  the power button into none at all.  So far, the major problem is that nothing is present under /sys/class/backlight

---

### Post by k84 on 2008-02-18
Is there a way we can just decompile windows drivers and see what we can do about the brightness on the vaio FZ series? I know it's illegal but my eyes can't take it anymore!!!

---

### Post by sojusnik on 2008-02-20
Deleted by author.

---

### Post by Paco758 on 2008-02-20
Here is the DSDT from a Sony VAIO VGN-NR290E purchased January 2008. I didn't see it in the table at [http://tjworld.net/snc/](http://tjworld.net/snc/) so I thought that it might help. 

Thanks. John

---

### Post by Xamindar on 2008-02-22
Here is the one from my Sony vaio laptop.  I didn't see it in the table.  PCG-7Z1N

Volume controls do work for me but the brightness does not.  Anyone know how to get brightness working for Fn+F5/F6?  xbacklight works for me to change the brightness but it would be nice to have the key combination working.

---

### Post by sojusnik on 2008-02-22
Hi,

I've bought recently a new Sony Vaio FZ21E and installed Ubuntu 7.10. So I am new to Linux at all. Everything seems to work fine exept of the 2 buttons above the keyboard named "S1" and "AV Mode". GNOME doesn't recognise these 2 buttons, but the remaining buttons above the keyboard are working well, for example with audacious.
Fn+F2 is working. It stands for "Mute".

Fn+F5/Fn+F6 aren't working. They stand for "brightness regulation".

Fn+F7 isn't working either. Stands for "Switching LCD to external Display".

Fn+F10 isn't working.

Fn+F12 also not working. Stands for "Suspend Mode".

Hibernate and Standby not working properly. After following tweak, it seems to work, but the network manager is not starting automatically at resume, so WLAN is not connecting automatically...

In /etc/X11/xorg.conf Section "Device" change following:
> Section "Device"
            
Driver          "nvidia"
Option          "NvAGP"       "1"

EndSection
In /etc/default/acpi-support change following:
> # Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

to

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false
Using "iwl3945" Driver for WLAN because the standard ist reconnecting automatically from time to time...

Hope this helps!

---

### Post by baucha_linux on 2008-02-23
my dsdt file for VGN-NR160E

---

### Post by benste on 2008-02-23
Can someone help me to get FN keys work??

VGN FE 31m

I can post all the thing you want to have but you should tell me where I can get them (enter ... in the console)

---

### Post by vishketan on 2008-02-24
Try the instructions here [http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/](http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/)

---

### Post by benste on 2008-02-25
Here is my file:

hopefully awaiting a solution of ACPI Problem

---

### Post by DarkAquarian on 2008-02-27
Greetings!

I seem to be the only person in the known universe that owns a VGN-AR270G.  I find next to nothing on the web for my laptop!

In regards to your project, my volume control buttons work, but my CD Eject, S1, S2, and media control (Play/Pause, Stop, Rewind, Fast Forward, and AV Mode), and Fn buttons do not (though I have not tried any of the posted fixes for the Fn buttons, so they may work).

What I'd really like to work is the CD Eject button because the way Sony designed the case for the AR270G make using the actual CD button irritating.

I hope the attached DSDT file will help.

Thanks.

---

### Post by benste on 2008-02-27
Nice idea your tutorial - but I can't edit the way ACPI is used in the bios.

As add: I can use Volume keys out of the box, but I'm missing FN and S1 and S2 key

---

### Post by ganxo on 2008-03-05
Hy pals, i hope this can manage to help all vaio users of ubuntu/linux.

I still cant use ubuntu because my lack of crontol of the brightness.

here my dsdt.

ps: anyone can change de brightness on a vgn-fz21e

---

### Post by ntetreau on 2008-03-05
UPON FURTHER GOOGLING, IT SEEMS LIKE THIS SCRIPT ONLY REDUCES THE COLOUR BRIGHTNESS AND NOT THE BACKLIGHT INTENSITY, SO DON'T BOTHER, SORRY!

For those with an nvidia graphics chip like me with my SZ6, you can use a script that links your brightness keys to the nvidia brightness settings.  I'll try to explain as much as possible how this is done.

You need nvidia-settings:
```
sudo aptitude install nvidia-settings
```

```
sudo touch /etc/acpi/var/brightness
```

this where the brightness count will be kept.

```
sudo gedit /etc/acpi/sonybright.sh
```

paste this script in gedit:
```
#!/bin/bash
function adjust
{
BRIGHTNESS=$1
if [ "$BRIGHTNESS" -ge 0 ]; then
BRIGHTNESS=0
fi

if [ "$BRIGHTNESS" -le -9 ]; then
BRIGHTNESS=-9
fi
echo $BRIGHTNESS >/etc/acpi/var/brightness
B=0.$BRIGHTNESS
B=`echo $B | sed 's/0.-/-0./'`
logger "adjusting brightness $B"
/usr/bin/nvidia-settings -c ":0.0" -V \
-assign BlueBrightness="$B" \
-assign RedBrightness="$B" \
-assign GreenBrightness="$B" 2>/tmp/sonybright.log
}

BRIGHTNESS=$(cat /etc/acpi/var/brightness)

if [ "x$1" = "xdown" ]; then
BRIGHTNESS=$(( $BRIGHTNESS - 1 ))
adjust $BRIGHTNESS
elif [ "x$1" = "xup" ]; then
BRIGHTNESS=$(( $BRIGHTNESS + 1 ))
adjust $BRIGHTNESS
else
echo >&2 Unknown argument $1
fi

```

Now you need to know the codes for your brightness keys.  To do that, run acpi_listen in a terminal and hit the Fn+F# combinations for your vaio.  Mine are Fn+F5 and Fn+F6 and I get this in terminal:

```
 acpi_listen 
sony/hotkey SPIC 00000001 00000010
sony/hotkey SPIC 00000001 0000003b
sony/hotkey SPIC 00000001 00000011
sony/hotkey SPIC 00000001 0000003b

```

The relevant bits are SPIC 00000001 00000010 for Fn+F5 (brightness down) and SPIC 00000001 00000011 for Fn+F6 (brightness up)

```
sudo gedit /etc/acpi/events/brightness-up.conf
```

Copy this code, change the key code for yours
```
# brightness up
event=sony/hotkey SPIC 00000001 00000011
action=/etc/acpi/sonybright.sh up

```


```
sudo gedit /etc/acpi/events/brightness-down.conf
```

Copy this code, change the key code for yours
```
# brightness down
event=sony/hotkey SPIC 00000001 00000010
action=/etc/acpi/sonybright.sh down

```

Lastly, you need to add this last bit:

```
gedit .bashrc
```

add this line at the end:

```
xhost +local:root > /dev/null 2>&1
```

save cloe, reboot, try

---

### Post by travis2615 on 2008-03-05
Hi,   
  Hope this is the right place to post this.  I am interested in helping the effort, I have a VGN-UX490N.  I recently installed 7.10 and almost everything seems to be working.  WLAN, bluetooth and memory stick duo slot/card are all good.  Something weird i noticed though, when i initially booted the live CD, my memory stick duo slot didnt work.  After a regular install i had no problems.  I dont know how to retrieve the DSDT info for the computer either.

I am really interested to try and install 7.10 to a memory stick duo and boot from that.  This Vaio model only has a 40GB solid state drive and work stuff takes up a majority of that on the windows side. 
Thanks
Travis

---

### Post by scubajeff on 2008-03-05
Mine is a TR2C. It's a model for Chinese market. Should be the same as TR2A.

---

### Post by BillShepp on 2008-03-06
> **ntetreau said:**
> For those with an nvidia graphics chip like me with my SZ6, you can use a script that links your brightness keys to the nvidia brightness settings.  I'll try to explain as much as possible how this is done.

As I recall from experimenting with the nvidia-settings parameters, this doesn't actually reduce the backlight, it only reduces the intensity of the colors.  It has no effect in terms of power-saving, which I imagine is what many of us are looking for.

Bill

---

### Post by benste on 2008-03-06
@ntetreau  

1.
```
benste@vaio-fe-31m:~$ sudo touch /etc/acpi/var/brightness
[sudo] password for benste:
touch: kann „/etc/acpi/var/brightness“ nicht berühren: No such file or directory
```

gives an error and


```
acpi_listen
```
gives no output!!
help me please

---

### Post by ntetreau on 2008-03-06
> **BillShepp said:**
> As I recall from experimenting with the nvidia-settings parameters, this doesn't actually reduce the backlight, it only reduces the intensity of the colors.  It has no effect in terms of power-saving, which I imagine is what many of us are looking for.

Bill

I did not know that, what kind of experimentation did you do and what were the results?  I mean the brightness does go down so one would be led to believe that it uses less power, not to say you are not right though.

---

### Post by ntetreau on 2008-03-06
Sorry, create the /etc/acpi/var folder first.  Also, I don't get any output either from acpi_listen until I press the key, which I guess you tried as well...  BillShepp seems to think this doesn't reduce the power consumption anyway so it may not be worth the trouble.

---

### Post by ntetreau on 2008-03-06
Well, let me try something else then!

For those like me who also have an intel 965 chipset (x3100), xbacklight doesn't work because of a silly bug in xrandr.  If you have the same problem, you can fix it:

```
xrandr --output LVDS --set BACKLIGHT_CONTROL native

```

then 

```
xbacklight -set 40
```

your backlight intensity should decrease, hope I'm right this time!

---

### Post by benste on 2008-03-07
@ntetreau:

I'm using a nvidia chipset - brigthness only works when you use

```
nvclock -S 25%
```
--> nvclock is a part of nvidia graphics driver (nvidia-settings)

```
benste@vaio-fe-31m:~$ sudo touch /etc/acpi/var/brightness
```
exists now but it is empty
```
benste@vaio-fe-31m:~$ sudo gedit /etc/acpi/sonybright.sh
```
done
```
benste@vaio-fe-31m:~$ acpi_listen
```
still no output

but when I use FN+Num -
there apears a new gnome-terminal
```
benste@vaio-fe-31m:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  186
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

I don't now wha  it is but I think it's because of nvidia != intel


Can you help me again ?
I'm not shure wheater FN keys work or not because of FN + Num


EDIT: ```
nvclock -S 25%
``` has a big effect on battery time !!! with 15% I've got 3hours battery with 100% ~45min battery!!

---

### Post by woody__ on 2008-03-07
Hi, i have a VGN-NR10M.

I'm using Debian (testing), Fn keys doesn't work and apci_listen doesn't give anything. Suspend mode doesn't work too.
I tried Ubuntu Live 7.10, and only volume Fn keys worked, but i didn't try acpi_listen. I'll try better when i have a moment.

PD: sorry for my english, it's my bad memory, i have to study again :S

---

### Post by darylb on 2008-03-08
Hi,

I have a Sony Vaio VGN-SZ71WN. I'm running Ubuntu Gutsy 7.10. The backlight FN-key controls do not work in either stamina (intel 965) or speed (nvidia 8400M GS) mode. In stamina mode I can use "xbacklight -set n" to change the brightness. I have not tried this in speed mode.

The Fn keys for brightness do not work in Hardy Alpha 6 either (I tried it in Live CD mode).
I have attached the dsdt file for my machine.

Thanks,
Daryl

---

### Post by mynk on 2008-03-09
Hi,

I got a Sony Vaio VGN-FZ240E recently and I have seen the following problems on Gutsy:

1. Mike & headphone jack does not work. Tried a couple of tips suggested but without much luck.

2. Webcam not working.

3. Brightness fixed using xbacklight for now. Fn blue keys not working for brightness(works for mute though). For switching screen (LCD/projector) I haven't been able to test. 

4. The keys on the above panel - S1, AV Mode, etc not working except for volume. Not been able to test thoroughly.

5. Suspend/Hibernate -  seeing issues.

I am a newbie and found the [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") by Tripmonkey_uk pretty useful.

Hope this helps. The DSDT tgz attached along with.

---

### Post by lexod on 2008-03-13
This is for a PCG-TR2A model vaio.

And just in case you can help me out, I have been having problems with my vaio's screen lately and am having to use an external moniter to use this machine.  I've detailed my problem on a separate thread.  Any help would be greatly appreciated. :)
[http://ubuntuforums.org/showthread.php?t=722907]("http://ubuntuforums.org/showthread.php?t=722907")

---

### Post by benste on 2008-03-13
Here is my new one, I'm usind 8.04 Hardy Alpha6 now.

---

### Post by hoogland on 2008-03-13
Output for Sony VGN-SZ750N/C running 7.10 64-bit.

---

### Post by deletarus on 2008-03-14
I recently purchased a VAIO TZ150N from a COMPUSA going out of business sale.

Here is the requested information (It doesn't have a file extension, though that shouldn't matter)

Thus far running Hardy Alpha 6 with all current updates (as of 3-14-08 ) the following have been tested and working

Fn mute, volume, brightness, Pg Up, down etc.
wireless works out of the box, as does sound

Hibernate and suspend to not function properly as of my last test, SD and MS Pro slots do not work, AV and eject front mounted buttons do not work, fingerprint scanner? camera? bluetooth I think works...

if you care here is my lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
09:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
09:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
09:04.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
09:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

if any other info would be useful, just let me know. I would very much like to have a fully functioning ubuntu install on my new laptop.

---

### Post by sunnymoon on 2008-03-17
FnKeys: Not Working, although xev detects some of them (Brightness and Sleep are not even detected, nor is AV and S1)

BlueTooth: Not Working... no bluetooth device detected, apparently

if insmod sony-laptop there is no /proc/acpi/sony directory!

Best regards... may I help some other way?
JPereira

---

### Post by exkis on 2008-03-21
Hi,

I have got a VAIO VGN-SZ61MN with ubuntustudio 7.10 (based on gutsy).
Brightness doesn't work (even with xbacklight) as well as Mike & headphone jack (I tried some tips suggested wiithout success), webcam "motion eye" not working. 'Fn' key works with F2, F3, and F4, the volume adjustment keys. WLAN works perfectly.
I have attached the file. I thank you a lot guys.

---

### Post by benste on 2008-03-22
@exkis:

yoiu've got a NVIDIA GeForce 8400M GS and an Intel GMA X3100  grafic card.

with the nvidia graic card, brightnees would work when you install the nvidia driver and nvclock

then you use a termianl and type[PHP]nvclock -S 15%[/PHP]

---

### Post by darylb on 2008-03-22
Hi benste,
I have a Vaio VGN-SZ71WN with the same nvidia graphics card:
```
$ lspci | grep -i nvi
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
```
However nvclock reports that it is not compatible with this card, only 6200 & 7x00 series cards:
```
$ nvclock -S 15%  
Error!
Smartdimmer is only supported on certain laptops using a Geforce 6200/7x00Go. If you want support on your laptop contact the author.

```
This is with NVClock v0.8 (Beta3), I'm running Hardy beta.

---

### Post by benste on 2008-03-22
I'm sorry for this - I only a desktopuser :-)
MAybe you try anewer version: [http://www.linuxhardware.org/nvclock/]("http://www.linuxhardware.org/nvclock/") reports: 
> Firday January 4 2008
It is finally time for a new beta release 0.8 Beta3. I would have liked to do a non-beta release but lots of users have been asking for this release because of the 8800GT fan bug in Nvidia driver 169.07. Note this release is beta, some Geforce8 features are still missing and also realize that the release is still very experimental. When you encounter problems or bugs please report them.

Changes:
# Geforce8 support
# Rewritten lowlevel Geforce6/7 overclocking backend [experimental]
# Added bios PLL table parsing for Geforce6/7/8 cards
# Fanspeed adjustments for 8800 cards equipped with ADT7473 chips
# Support for additional Geforce7 AGP cards
# Add support for more NV-CONTROL OpenGL settings in GTK
# Geforce6 fake Quadro bugfixes
# Geforce6 pipeline modding bugfixes
# Tons of bugfixes

so geforce should be supported in the newer beta version.



Someone an idea when FN keys and smartimmers - gnome desktop integration will work?

---

### Post by minijoe on 2008-03-25
Here is my VAIO VNG-AR630E file running Hardy

---

### Post by rlubke on 2008-03-25
Model: VGN-SZ546P
Using Ubuntu Heron Beta.

Only fn keys that work are those that affect volume.  The others for wlan, brightness, external monitor and suspend to disk do no work.  Closing the notebook lid does not cause a suspension either.

---

### Post by stavallo on 2008-03-25
Hi,

I got a VAIO VGN-FZ39VN. Please find attached the disassembled DSDT.
I am using kernel 2.6.24. Some Fn keys (e.g., Mute) do not produce any event (I am using acpi_listen to listen to events), as well as the Volume Up/Down buttons. The Fn keys to increase/decrease brightness produce events but actually do nothing. I am also not able to change the brightness of the display by manually echoing a value into the brightness files I can find in the /sys directory.
If I can help further, please let me know.
thanks

---

### Post by originof on 2008-03-26
Hi, 
I got a VGN-NR21Z and i can't change the brightness.
I tried to load and reload the module-sony laptops and sonypi, but the / sys / class / backlight directory is empty, then I tried with nvidia-settings - assign etc. .. But I said: ERROR: Error parsing assignment....
So then I tried with smartdimmer, but unsuccessfully. ](*,)

---

### Post by wittelw on 2008-03-30
My contrib from** VGN-CR120E** running Heron with latest updates.

Buttons on this laptop have never worked (jumped on board during 7.10 Beta). A week or so ago screen brightness in Power Management stopped working (maybe by design because the slider disappeared). Hope this helps the effort.

Many thanks to:
IntuitiveNipple, for all the great work! I hope this can make it into Heron release, but I know it is down to the wire.

[QUOTE=Tripmonkey_uk;2809262]Hi all..
Just added a post to the [Ubuntu-FS]("http://ubuntufs.wordpress.com/") site to let people know of this thread & I've tried to write an even [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") for new users to follow. Please let me know if it needs improving at all.

Tripmonkey_uk, hope other new users spot your [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") before they grovel all the other links trying to figure out how to capture this stuff (although I guess I'm a bit less-new and better for the experience :)).

IntuitiveNipple, a pointer to Tripmonkey's [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/")  in your #1 post (and point to the ability to "search this thread" for model #) might speed up the process for other VAIO users and get you even more work :lolflag:.

P.S. URLs for Tripmonkey's tutorial aren't showing up in preview, but other readers can just look for post #26 in this thread if they don't come through.

---

### Post by sunstealer on 2008-03-30
Hi IntuitiveNipple,

Are you or Mattia still interested in these dsdt dumps or has worked ceased on this for now? I note that a lot of people have continued to post theirs but you have not replied to this thread since September 2007. Please don't take this as a criticism! I am sure everyone (myself included) is very grateful for all the time you have already devoted to this. However, I (and I suspect others) would be very grateful if you could confirm whether or not continued efforts to post more models to add to your list is still helpful. Being a hopeful sort of fellow, I am adding mine with this post as it doesn't feature on your website.

Many thanks for all your efforts so far!

---

### Post by nomail on 2008-04-03
Well anyways, im gonna post my DSDT aswell
VGN-FE21B

---

### Post by inferiorwang on 2008-04-04
Alright, I've been running hardy (2.6.24-12 and -14) for a couple of weeks on my new vaio.  It is a VGN-CR123E with the x3100 video and 4965agn wireless.  I can change the screen brightness by echoing 0-7 to  /sys/class/backlight/sony/brightness.  Fn keys don't work. (Suprise)  I haven't tried the memory stick, since I don't have any memory sticks and I haven't even tried messing with the camera, yet.  It is on my list, but isn't a priority.  Anyway, I hope this is still being worked on and since people are still posting their DSDTs, here's mine.

---

### Post by siddesu on 2008-04-12
sony vaio vgn-sz55b 

don't work: 
[LIST]
[*]brightness control (sony-laptop driver)
(that has nothing to do with the _keys_, they work fine, events are sent, etc. it is just brightness that doesn't change)
[LIST]
[*]    on intel - doesn't work at all
[*]    on nvidia - using nvidia-settings kind of dims the display, but power usage doesn't change)
[/LIST]
[*] fingerprint reader - it's a sony, so they have to screw you
[*] felica card - i didn't even hope for that :)
[*] the sony hdaps
[/LIST]

kinda works, but has issues:
[LIST]
[*]camera
[*] iwl3945
[*] i'm hitting bug #177895 with ubuntu sources. gentoo sources work fine
[/LIST]

everything else works fine

---

### Post by mdoube on 2008-04-13
Check this stuff out:

> **siddesu said:**
> sony vaio vgn-sz55b 

don't work: 
[LIST]
[*]brightness control (sony-laptop driver)
(that has nothing to do with the _keys_, they work fine, events are sent, etc. it is just brightness that doesn't change)
[LIST]
[*]    on intel - doesn't work at all

try installing xbacklight:
sudo apt-get install xbacklight

then setting the brightness:
xbacklight -set n (where 0 >= n >= 100)

and installing the script on this report
check [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173652)
and [https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888](https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888)

> 
kinda works, but has issues:
camera

I guess you have a vcc of some version, try this page: [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)
> 
iwl3945

almost there - try linux-backports-modules

---

### Post by Tlarhices on 2008-04-15
No function key is working currently but the brightness works (through applet or command line) on a VAIO VGN-FS-485B, bios version R0044J2.

---

### Post by LT1Caprice57L on 2008-04-16
OK, I hate to sound like a jerk, but is the SXBIOS functionality *ever* going to materialize?  In the last update about it, we were made to believe it would be "a couple of extra weeks"...that's now turned into *seven months* and still waiting, and the OP hasn't been seen in this thread in about the same time frame.

What gives? :( At least an update on the situation would be nice...  At this point the computer is working fine, I can live without the ability to change brightness or suspend/hybernate, it'd just be nice if I could be told for sure what's happening, or if the driver has been deemed complete.

---

### Post by Bunpitsu on 2008-04-16
I own a AR320E, and the eject doesn't work. Meh.

---

### Post by Tripmonkey_uk on 2008-04-17
> **wittelw said:**
> 

Tripmonkey_uk, hope other new users spot your [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") before they grovel all the other links trying to figure out how to capture this stuff (although I guess I'm a bit less-new and better for the experience :)).

IntuitiveNipple, a pointer to Tripmonkey's [easier tutorial]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/")  in your #1 post (and point to the ability to "search this thread" for model #) might speed up the process for other VAIO users and get you even more work :lolflag:.

P.S. URLs for Tripmonkey's tutorial aren't showing up in preview, but other readers can just look for post #26 in this thread if they don't come through.

Cheers for that wittelw :)

Another bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119672") for the FN keys with some interesting tips on it. Might be useful to someone on here?

---

### Post by Filipe_Cruz on 2008-04-17
i have a vaio vgn-ar31s that was working with vista , there are some tutorial about shrinking the partition in vista - first error there are already 2 partitions by default- i think this was my mistake i shrunk the second one and instal ubuntu 7.10 studio edition, after doing it i got this grub 21 error , tried several things and installed again , and again (lots of mistakes i know but i was getting mad at it)now i lost everything and installed vista again with the sole propose of formating the hard drive and al of l its partitions because i need none, some help doing this properly ?where do i find the drivers. like the one about network adapter and the blue ray  drive .... i hope i haven't made a mistake about turning to linux.
Filipe

---

### Post by tall_one on 2008-04-18
VGN-FS215S

None of the Fn keys work as standard.

---

### Post by Toufik on 2008-04-18
If you have a **Vaio FS***, here is the solution to your problems:

I wrote a new version of fsfn which work with sony-laptop driver rather than the old and deprecated sony_acpi. So the fn keys work nearly out of the box! You just need to download and install a debian package. That's all...

[http://www.fyma.ucl.ac.be/files/fsfn_2.0-1_i386.deb](http://www.fyma.ucl.ac.be/files/fsfn_2.0-1_i386.deb)

[COLOR="Red"]This works for Hardy and probably gutsy[/COLOR]
[COLOR="Red"]I don't know for feisty and older: try at your own risk (it shouldn't harm but...)[/COLOR]

Full explanation: [http://ubuntuforums.org/showthread.php?p=4743422](http://ubuntuforums.org/showthread.php?p=4743422)

---

### Post by Tripmonkey_uk on 2008-04-18
Cheers Toufik, i'm hammered at the mo, but I'll check in the morn if it works on Hardy Heron and link to it on the site :)
... God am I out of it :D

p.s they changed the folders after Feisty so this should be fine :)

---

### Post by Tripmonkey_uk on 2008-04-18
k  might be alittle bit out of it, but after a quick test.. The volume keys work. so do the brightness and mute key wOOT!

Installing programs on Linux can't be that hard if I can do it when drunk as a skunk lol

---

### Post by troylb on 2008-04-22
I have a VGN-AR630e and have confirmed the following:

**NOT WORKING:**
the fn-keys and S1, S2 and eject keys.
*Audio out, Line in and Optical out. 
HDMI

**WORKING:**
A/B/G/N wireless
10/100/1000 Wired Ethernet
SD Card
USB
VGA

**NOT TESTED:**
PCMCIA
PC Express cards
SVIDEO
Firewire
built-in camera
Modem

* = After changing some config settings in the /etc/modprob.d/alsa-base to include:
options snd-hda-intel model=vaio position_fix=0

I was able to get sound out the headphone/line out jack. Line in and optical out still do not work. Also, the built-in speakers do not shut off when using headphones. There is no way to turn them off.

---

### Post by Amorget on 2008-04-22
Sony VGN-AR670

S1, S2, CD Eject, and Fn Keys don't work.  I got the camera working (kinda).

Volume and Mute work (like seemingly everyone).

I've attached my dsdt

Hopefully this helps in some way!

Douglas

---

### Post by IntuitiveNipple on 2008-04-23
**[color=red]Update[/color]**

I have updated the first post of the thread with instructions, progress update, and an automated script for collecting the DSDT and BIOS information since many of the attachment filenames weren't in a format my automated analysis scripts could make use of.

I've not had much time to spend on this over the past months but I've recently been prompted into spending more time on it, and as I now understand much of the Windows SNC functionality the issues to address are now clearly defined and being worked on.

Thanks to everyone for contributing your DSDT images. Please ensure that your attachment used the correct naming convention since without it, my automated scripts have no way of associating model and BIOS version with the DSDT, and that makes it useless.

---

### Post by mynk on 2008-04-23
Toufik,

Could you kindly point me to the 64bit equivalent of the package you mention? I can try that on my laptop.

Intuitive Nipple,
Attached along with is the DSDT file as generated by the new script provided.

The new hardy desktop image doesn't boot for me. Will try the latest image again today and let you know if I see any improvement.

Thx,
Mynk

---

### Post by Amorget on 2008-04-23
Crud, sorry, here it mine generated from the script

---

### Post by IntuitiveNipple on 2008-04-23
> **mynk said:**
> 
The new hardy desktop image doesn't boot for me. Will try the latest image again today and let you know if I see any improvement.


This may be [ bug #191137 "[Hardy] ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet' option is enabled or AC power is connected"](https://bugs.edge.launchpad.net/linux/+bug/191137)

Try removing the kernel command line option "quiet" and/or running only on battery for the few seconds whilst the kernel boots.

---

### Post by Toufik on 2008-04-23
> **mynk said:**
> Toufik,
Could you kindly point me to the 64bit equivalent of the package you mention? I can try that on my laptop.

Yes, here you are: [http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz]("http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz")

If you install by and, look at the README and at the INSTALL files. You need to install some packages first:
```
$ sudo apt-get install libxosd-dev libxosd2
```

---

### Post by Franck Gillé on 2008-04-23
Here my file for vgn-ar51m
I hope it's OK
Thanks 
Franck

---

### Post by sandgroper3 on 2008-04-23
My VAIO was purchased while on holiday through SE Asia. Hope this is helpful. Please advise of any additional requirements and thanks for your efforts.

---

### Post by Paco758 on 2008-04-24
**vgn-nr290e-r1101j9**

EDIT: Sorry, I forgot to mention that currently there is only Fn key functionality on Mute: Fn+F2, Volume Down: Fn+F3, Volume Up: Fn+F4. Brightness changes only work when xbacklight is invoked in the shell or by a script. The 'sonybright' scripts do invoke xbacklight, but the system is not calling on them for any acpi event, whether through the panel or the fn keys.

---

### Post by blueglow on 2008-04-24
Firstly, thank you for for working on this. :)

**Results on a VGN-A397XP running Hardy:**
Currently keyboard Fn + F2..F7 works, but the 'special' keys above the keyboard (volume up/down, brightness, magnify, S1) don't work. CD eject doesn't work either, though both Fn + E and the CD eject (main button not little one) used to under Gutsy and an icon appeared on screen. Not sure what's going on there.

The memory stick reader doesn't still work (light permanently on) - please see [https://bugs.launchpad.net/ubuntu/+bug/48987](https://bugs.launchpad.net/ubuntu/+bug/48987) and post mem-stick probs there.

**BTW**: I note that when I  acpi_listen and press the 'special' keys above the keyboard they all say the same thing: "sony/hotkey SPIC 00000001 00000020". Other buttons and Fn combos are fine. Dunno if that's at all relevant.

**Finally**: Does anyone know if anyone's managed to get the ambient light sensor (auto brightness adjust) to work or at least report its values?

---

### Post by Tripmonkey_uk on 2008-04-24
Decided to update my bios to the latest version, hopefully it will help as well.
Had to install WinXP on my spare HD to do it though. Man do I feel dirty.. and not the good kind of dirty either :(

VGN-FS215E - version R0044J1

---

### Post by mdoube on 2008-04-25
> **Paco758 said:**
> **vgn-nr290e-r1101j9**

EDIT: Sorry, I forgot to mention that currently there is only Fn key functionality on Mute: Fn+F2, Volume Down: Fn+F3, Volume Up: Fn+F4. Brightness changes only work when xbacklight is invoked in the shell or by a script. The 'sonybright' scripts do invoke xbacklight, but the system is not calling on them for any acpi event, whether through the panel or the fn keys.
Have you checked 
[https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/173652)

The last few comments have some suggestions for getting Fn keys to control xbacklight, which work on my SZ650N/C

---

### Post by ColdWind on 2008-04-26
Here we go: VGN-CR21S_W, BIOS: R1070Q0

---

### Post by akkadian on 2008-04-26
is this thread dying?
No luck with the brightness on my fz21e....
Hope to find the cure....
any news?

---

### Post by sojusnik on 2008-04-27
Same here with my FZ21E on 64-Bit Hardy...

---

### Post by marliss on 2008-04-27
No FN key functionality for mine. I can alter the brightness manually by writing to /proc/acpi/sony/brightness
The 2.6.24-16-generic kernel seems to remove /proc/acpi/sony and breaks the wireless interface as well, so I have to revert to 2.6.22-14-generic to get those working.

---

### Post by benste on 2008-04-27
Yeah, seems to be,
I posted my DSTS months ago, but there is still no howto for my FN Keys - Is there No expert who can help me?

---

### Post by mdoube on 2008-04-28
Not Dead! It's sprung back into life recently, see the update on the first post; lots of new models have been added and I'm looking forward to seeing a new sony-laptop kernel module soon.

---

### Post by IntuitiveNipple on 2008-04-28
Far from being dead! What you have to realise is, the aim is to reproduce 100% of the functionality Windows enjoys. Working out how that happens is a painstaking process that requires hours of analysis and plenty of frustration. I'm not prepared to release something that only has patchy functionality or doesn't cover all models - amongst other things I don't want the support headaches that'd cause.

In the last few days we've developed a break-through method of reliably reporting the ID and capabilities of new models that will be released in the future (without imposing any workload on the developers), and a way to plug the capabilities into the driver at run-time so the driver isn't always having to play catch-up with new version releases. The tools - which run on Windows - grab the info from the PC and automatically submit it to the web site database. That solved a major issue.

Knowing what capabilities each model has, and how they are controlled and queried, is crucial for the driver. Once we are confident that we can control the SNC functions safely without unintended side-effects (Alex managed to disable the glide-pad but couldn't re-enable it!) the driver will be released.

---

### Post by benste on 2008-04-28
Sounds nice! Thank you for you big investigastion.

---

### Post by topolab on 2008-04-28
vaio pcg-sr21k
anybody with this?

---

### Post by Yatzek Platzek on 2008-04-28
Hi, 
Here is the outcome of your script from Vaio Vgn-s3hp. Thank you for your attempt to put everything right with vaio's. I have problems with getting my machine back to work after putting it into suspend or hibernate mode. And also the battery lasts for about 30-45min less than it used to when I used Windows.

---

### Post by caesar_bs on 2008-04-28
Hi all,

IntuitiveNipple : Thank you so much for your help. Your work rockz \\:D/
When do hardware companys learn to provide good linux drivers   ](*,)

anyway, here is my dsdt, its a FE 21B.
Atm, with Hardy 8.04 they battery status doesnt work properly, neither do they S1 and S2 buttons, the sleep, lcd and brightness Fn keys.

Have Fun all

Julius

---

### Post by mdoube on 2008-04-29
Hello

This is the result of your script on a PCG-V505DX.  Pretty much everything works on this model, though the Fn keys are mapped slightly differently than under windows: 

Fn +...
Win: F3 = mute; Ub: F2 = mute
Win: F4 activates vol, then arrow up and down to change
Ub: F3 = Vol down, F4 = vol up
Win: F5 activates backlight control, arrow keys to control
Ub: F5 = dim, F6 = bright.

Thanks for your efforts - much appreciated by many!

---

### Post by akkadian on 2008-04-29
> **IntuitiveNipple said:**
> Far from being dead! What you have to realise is, the aim is to reproduce 100% of the functionality Windows enjoys. Working out how that happens is a painstaking process that requires hours of analysis and plenty of frustration. I'm not prepared to release something that only has patchy functionality or doesn't cover all models - amongst other things I don't want the support headaches that'd cause.

In the last few days we've developed a break-through method of reliably reporting the ID and capabilities of new models that will be released in the future (without imposing any workload on the developers), and a way to plug the capabilities into the driver at run-time so the driver isn't always having to play catch-up with new version releases. The tools - which run on Windows - grab the info from the PC and automatically submit it to the web site database. That solved a major issue.

Knowing what capabilities each model has, and how they are controlled and queried, is crucial for the driver. Once we are confident that we can control the SNC functions safely without unintended side-effects (Alex managed to disable the glide-pad but couldn't re-enable it!) the driver will be released.

Hy, great news from you guys, i know that your work is hard and, believe me, the community recognize it. I am desirous to test the tool, and give you some help.
If you want i can be a tester :)

Best regards

---

### Post by arrrgh... on 2008-04-29
Hi,

   as an owner of a half-year old VGN-SZ61XN/C I'd like to submit my DSDT. Currently running under Debian-lenny 2.6.24-1-amd64, I have problems with the following thingies:
- Fn keys do not work (except for the sound section);
- modification of backlight intensity (though I've not tried xbacklight yet).

   Moreover, at the moment sony-laptop detects controls in this model as Type2, and somehow I feel that it should be Type3 (at least one of my friends, who owns an older model has this detection as Type3 and everything works out of the box).

   Hope this data proves to be of use. If you guys will be looking for someone to test your work - I'm in. Last but not least - any rough estimates concerning the moment at which you want to have a test release?

   Kind regards

---

### Post by Tripmonkey_uk on 2008-04-29
> **IntuitiveNipple said:**
> The tools - which run on Windows - grab the info from the PC and automatically submit it to the web site database.

You need some help with that feel free to give me a shout. I can do another install of Windows and test some stuff for you :)

> **arrrgh... said:**
> somehow I feel that it should be Type3 (at least one of my friends, who owns an older model has this detection as Type3 and everything works out of the box).

Mine was set to **Type 3** for Windows, but only works if set to **Type 1** for Linux. You might be best trying them all just to be sure m8.

---

### Post by Deten on 2008-04-29
Hope you still need them.  I randomly found this by having a sound problem... I have no idea why this was the top threads :)

8.04
I am able to use bluetooth and wireless fine.  My brightness doesnt work, nor any of my function keys.  

Good Luck!

How do we find out what happenes with this project?

---

### Post by Deten on 2008-04-29
Forgive me :) forgot to attach

---

### Post by ordex986 on 2008-04-30
from my VGN-NR21Z

---

### Post by biloti on 2008-05-01
Hi

I ran your script on my sony vaio VGN-SZ640. The result is attached.

R.Biloti

---

### Post by mynk on 2008-05-02
> **IntuitiveNipple said:**
> This may be [ bug #191137 "[Hardy] ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet' option is enabled or AC power is connected"](https://bugs.edge.launchpad.net/linux/+bug/191137)

Try removing the kernel command line option "quiet" and/or running only on battery for the few seconds whilst the kernel boots.
The latest images of Hardy work like a charm on both my T61 and Vaio 64 bit. The initial hiccups that I saw have all been fixed. Eagerly awaiting the fix for the function keys on Vaio however.

---

### Post by cref on 2008-05-02
Hope the attached file may help

---

### Post by djvishnu on 2008-05-02
Attaching file for SZ1XP

I haven't read the whole thread, so please let me know if any of this is already commented:

I have been reading about the accelerometer used in the hard disk protection system (in an attempt to access it). I discovered this patent:
[http://appft1.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PG01&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.html&r=1&f=G&l=50&s1=%2220070150211%22.PGNR.&OS=DN/20070150211&RS=DN/20070150211](http://appft1.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PG01&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.html&r=1&f=G&l=50&s1=%2220070150211%22.PGNR.&OS=DN/20070150211&RS=DN/20070150211)

If you look at the attached patent diagrams, you can see that the accelerometer is connected to an ADC which is connected to the Embedded Controller. I guess one could access the ADC with one of the acpi methods (i really don't know what i'm talking about here, but i'm trying to learn). Anyway, the patent paper is interesting reading. 


It'd be really cool to interface the accelerometer in software, could be used for many cool thing. :) I really want to play around with this, but atm i'm not even sure where to start - ex how do i perform calls to the SNC or EC? Guess i'll have to read up a bit more.

---

### Post by arrrgh... on 2008-05-03
> **Tripmonkey_uk said:**
> Mine was set to **Type 3** for Windows, but only works if set to **Type 1** for Linux. You might be best trying them all just to be sure m8.

Could You please help me out in one thing? Namely - how to set the Type? I assumed that it's autodetected, and haven't been able to find out how it can be set manually...

---

### Post by Tripmonkey_uk on 2008-05-03
> **arrrgh... said:**
> Could You please help me out in one thing? Namely - how to set the Type? I assumed that it's autodetected, and haven't been able to find out how it can be set manually...

It will probably be in your bios. Check my tutorial [here]("http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/") for help on that and give me a shout if you have any trouble :)

---

### Post by benste on 2008-05-04
Is there an ability of an Bios downgrade? - I'm currently using the ones wich was delivered with the Vista upgrade - search this thread for my dsdt

---

### Post by speedkx on 2008-05-05
I'd like to keep up the hope of everybody with a backlight/brightness problem: apparently the problem is with the nvidia driver and it's not just a Sony problem. I've heard similar complains from HP, Dell and Lenovo owners. There is beta driver available at NVIDIA's site that is supposed to fix backlight not being recognized, but I had no success with install. If anyone has more luck replacing the ubuntu supplied stable driver with stock 173.08 Beta and having /sys/class/backlight populated after this, please share the good news.

Function keys: I've no idea what SPIC or SNC is but ACPI scripts expect SPIC <some number> and when I run acpi_listen it reports the same numbers but with SNC prefix. It's the case with all newer F series.

I have an FZ21E.

---

### Post by wuddiwupp on 2008-05-05
I hope it helps to get this F*** keys working :lolflag:

---

### Post by benste on 2008-05-06
Short question, - is there a "bug" for this big sony laptop problem in launpad? - this one should be critical or?

---

### Post by bemused0 on 2008-05-06
Well done sir, good luck with the endeavor if its still happening.

Here's the data from a VGN-FZ340E.

Volume, (most) FN keys work; no brightness... (Using Hardy)

---

### Post by Huffleme on 2008-05-10
Here's the file for the VGN FZ38M. I've really got to find out how to get the F7 (external monitor) working soon.
Good luck.

Pip

---

### Post by Kamronn on 2008-05-10
Hi, just installed Hardy Heron on my VAIO so just wanted to support your efforts with this:

---

### Post by bobcosta on 2008-05-11
Hi,

I just installed Hardy Heron on my Sony Vaio PCG-SRX77.  I had to use the alternative installer to get it to work, but it seems like it doesn't have all the correct drivers, especially for the screen.  I'm stuck at 800x600 with no option to change it up to 1024x768.

Most other things work, FN key F2, F3, F4, F5 and F6, wired network, USB, PCMCIA DVD-ROM, except I can't get wireless to work with WPA-Personal.

Any advice on the screen resolution or WPA would be appreciated.

Attached dsdt file:

---

### Post by cyberdanycool on 2008-05-11
Hello, here is the grab for my Sony Vaio PCG-K315Z. Fn & Memorystick don't work. Wireless with WPA, VGA, Audio, wired network work great out of box. For the FN, I remember that smartdimmer was ok on Gutsy, but my wife doesn't use it (she need user friendly application :-) ).

---

### Post by ookami on 2008-05-13
Here's the dump from my VGN-SZ95S. This is the customizable "SZ premium" version currently (spring 2008 ) selling at [Sonys japanese Sonystyle page]("http://www.jp.sonystyle.com/Style-a/Product/Sz95/index.html"). I'm running Hardy and currently the Fn-keys work for volume only and I've yet to find a way to adjust the brightness of the monitor. Neither suspend or hibernate seems to work properly. 

Both the Intel-ABGN wireless and the wired networks work fine. With manual driver installation the Ricoh webcam works and sound including the mic works after some tweaking even though the volume is much lower than in Windows (both input and output).

I also have the docking station for this laptop which works fine except for X.org and Nvidia still being utterly crap at handling multiple displays and dynamic display setup (i.e. detect my external display when hooked up and remember that I want it as the primary display when it's attached, and of course panel and window placement as well as the whole "maximize over both displays" annoyance) but that's beyond the scope of this thread.

---

### Post by JamesNeko on 2008-05-13
Hi. Hope the data from my picturebook helps.

The function keys aren't working at the moment, though they used to - annoying, and I haven't gotten around to figuring out why. I can use spicctrl to change the backlight and activate the bluetooth.. sometimes. So maybe it was an Xorg update that killed my fn keys (the jog-dial too!). TV-out kinda works, and the built-in Motion Eye webcam sadly does not.

---

### Post by makrook on 2008-05-15
here's the dsdt for a NR11S/S
fn+F5 and fn+F6 for luminosity are not working.

---

### Post by bistory on 2008-05-15
Here is the dsdt of my VAIO VGN-FZ11E
acpi_listen say that the fn keys work (on Hardy) but the luminosity isn't managed...
Hibernate/sleep doesn't work...

I hope that it will be useful for you :)

---

### Post by napalm brain on 2008-05-15
VAIO VGN-FZ190N information here.

Fn keys have never worked for me since I started to use Ubuntu. I have never been able to hibernate/sleep, and the power-manager kind of...well, to put it bluntly, blows. I am not really sure if the power leak has anything to do with my hardware, but I would assume so.

Hopefully this helps.
Cheers.

---

### Post by jizo on 2008-05-15
Hey IntuitiveNipple/Mattia, 

You guys rock.  Keep up the good work.

Here is my dump for the VGN_FZ35G.  I've got same problems most everbody else seems to be having.  Screen dimmer doesn't work.  Bluetooth kind of half works, but doesn't work well (which is a problem seeing as how I'm a python developer writting code for nokia phone :( ).  And hibernate/suspend never wakes up.

---

### Post by gulper_eel on 2008-05-16
Hello, i have a TXN that had bios R0051N3, the same that some users here have, but made the mistake of upgrading it... Now the fan is working all the time and is really anoying.
The problem is that i can't find on the net r0051n3 bios dump.
Can someone please make one from yours and send me ? 
I would be very thankfull.

Best Regards, Ricardo.

---

### Post by benste on 2008-05-16
ask sony support :-) (You destroyed your Bios bla bla - hope they'll not tell you to recover :-))

-> Can you explain me how you get your old Bios? - I made the same mistake because a Bios upgrade was provided with Vista Upgrade.
(Using VGN-FE 31 m)

---

### Post by gulper_eel on 2008-05-16
I make a request to anyone who can help me and allot of other TX users that have been tricked by new bios...

Who has Bios R0051N3 (can enter bios to check it, when start computer perss F2 to enter bios), if they can please proceed this steps, it wont harm your computer. I alredy tested in mine and was quite easy:


1.)
Download the "Phoenix Winpflash Utility".
For example from here:
[ftp://ftp.support.acer-euro.com/util...sh-utility.zip](ftp://ftp.support.acer-euro.com/util...sh-utility.zip)

After this, install and run the "Phoenix Winpflash Utility".

[http://bnobtc.pix-art.com/images/bor...kup-bios00.png](http://bnobtc.pix-art.com/images/bor...kup-bios00.png)


2.)
Choose: "Backup BIOS only"

[http://bnobtc.pix-art.com/images/bor...kup-bios01.png](http://bnobtc.pix-art.com/images/bor...kup-bios01.png)


3.)
It sounds weird and crazy, but take any PhoenixBIOS update,
for example from acer:
[ftp://ftp.support.acer-euro.com/note...3a06_intel.zip](ftp://ftp.support.acer-euro.com/note...3a06_intel.zip) ([ftp://ftp.support.acer-euro.com/note...3a06_intel.zip](ftp://ftp.support.acer-euro.com/note...3a06_intel.zip))
You can also take any other (256K/512K/1024K) Phoenix BIOS updates.


4.)
Extract and add the .wph file from the mentioned
example BIOS file: 3a06_intel.zip to the: "Specify new BIOS file" -field
and choose: "Advanced settings".

[http://bnobtc.pix-art.com/images/bor...kup-bios02.png](http://bnobtc.pix-art.com/images/bor...kup-bios02.png)

5.)
Then deselect all clickboxes and press Ok.

[http://bnobtc.pix-art.com/images/bor...kup-bios03.png](http://bnobtc.pix-art.com/images/bor...kup-bios03.png)


6.)
Now press: "Backup BIOS"

[http://bnobtc.pix-art.com/images/bor...kup-bios04.png](http://bnobtc.pix-art.com/images/bor...kup-bios04.png)


7.)
Accept the following message/ info dialog box...:
[http://bnobtc.pix-art.com/images/bor...kup-bios05.png](http://bnobtc.pix-art.com/images/bor...kup-bios05.png)


...and go on with backup your BIOS.

8.)
When backup process is finished...
[http://bnobtc.pix-art.com/images/bor...kup-bios09.png](http://bnobtc.pix-art.com/images/bor...kup-bios09.png)

...you sould see the BIOS dump...
[http://bnobtc.pix-art.com/images/bor...kup-bios10.png](http://bnobtc.pix-art.com/images/bor...kup-bios10.png)

Finally, you can send the BIOS file to me (ricardocarvalho@sapo.pt)
Very thankfull

---

### Post by Nizarus on 2008-05-18
DSDT file for VGN-FE31 H

---

### Post by reto4334 on 2008-05-19
Hey 
I have a VGN-FE31M but I changed the BIOS with a Version of the Vaio FE41Z R0200J3 and it works fine so far. I ran the script and post you now the  file. when will the driver ready for use?
Thanks

---

### Post by jack24 on 2008-05-19
Thanks for working on this.  I have a VGN-SZ750N.  Everything I need is working well enough, but mostly for the challenge I'm still trying to get all of the Fn keys and the memory stick reader working.

Jack

---

### Post by momo07 on 2008-05-19
Help I need some help pls.
I have succesfully installed Ubuntu 8.04 on my Sony Vaio VGN-SZ5MN. Everything works except for my wireless connection and the S function keys.  Could you pls help.

Thanks

---

### Post by akkadian on 2008-05-20
I have just tried the new nvidia beta driver 173.* and did not work fixing my backlight problem, at least i tried many ways. 
The driver looks fine but not enough yet.

Regards

---

### Post by Griffin3 on 2008-05-20
DSDT file for elderly Sony VGN-A190 ...

---

### Post by hihihi on 2008-05-20
> **k84 said:**
> Is there a way we can just decompile windows drivers and see what we can do about the brightness on the vaio FZ series? I know it's illegal but my eyes can't take it anymore!!!

how could we do that?
there are other drivers ported into linux, or not?

---

### Post by hihihi on 2008-05-20
> **akkadian said:**
> I have just tried the new nvidia beta driver 173.* and did not work fixing my backlight problem, at least i tried many ways. 
The driver looks fine but not enough yet.

Regards

this driver works better than the 169 one, but i cannot get TV-out to show image,
do you?

---

### Post by akkadian on 2008-05-20
> **hihihi said:**
> this driver works better than the 169 one, but i cannot get TV-out to show image,
do you?

I did not test it. 
Im only preocupated with the backlight.
Btw, Linux/Ubuntu is eating my harddrive cycles about 4 per minute.
I will not use Linux for now. 
Read the thread that talks about it.

---

### Post by arrrgh... on 2008-05-20
> **Tripmonkey_uk said:**
> It will probably be in your bios.

Sorry for the late response, but I had some time without a net connection. There seems to be a slight problem, as there is no section responsible for setting the type in the bios of this model... Any other ideas? :)

---

### Post by BandD on 2008-05-21
DSDT file for Sony VGN-FS620P/W:

---

### Post by love2learn on 2008-05-21
Thanks for all your help.

---

### Post by jmfrank63 on 2008-05-22
Here is the Sony VGN-NR21E. I hope it is no duplicate.

---

### Post by rafttrip on 2008-05-22
what I did was click and drag the file into the terminal and hit enter.

'/home/g***/Documents/VAIO Info/snc-dsdt.sh' 
Checking and installing tools...
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Getting model information: /dev/mem: Permission denied
/dev/mem: Permission denied
Model: , BIOS: 
Dumping the ACPI Differentiated System Description Table (DSDT)
/home/gabe/Documents/VAIO Info/snc-dsdt.sh: line 20: acpidump: command not found
Packing and compressing the DSDT...
tar: invalid option -- .
Try `tar --help' or `tar --usage' for more information.
All done, thank-you

If you want, you can now remove the acpidump and dmidecode packages using:
	sudo apt-get remove acpidump dmidecode

Please attach the file /tmp/-.dsdt.tar.gz to a new post in this Ubuntu forums thread:

[http://ubuntuforums.org/showthread.php?t=465491](http://ubuntuforums.org/showthread.php?t=465491)

That is the out put from when I run the file that I downloaded.

I would love to help and send you the information you are asking for but I'm afraid I don't understand how to go about doing what you ask.......never mind I put sudo before the file path and it seams to be doing it's thing.

Sorry  about the mix up and thank you for you time and effort.

---

### Post by Migs on 2008-05-22
In wich way is this project linked/compared to the HAL quirk site? It would be a pitty if both efforts lead to the same results in activating various HAL quirks. 

I am refering [http://people.freedesktop.org/~hughsient/quirk/]("http://people.freedesktop.org/~hughsient/quirk/")

---

### Post by IntuitiveNipple on 2008-05-22
> **Migs said:**
> In wich way is this project linked/compared to the HAL quirk site? It would be a pitty if both efforts lead to the same results in activating various HAL quirks. 

I am refering [http://people.freedesktop.org/~hughsient/quirk/]("http://people.freedesktop.org/~hughsient/quirk/")

I am aware of the quirks initiative, but it has little if any impact on what I'm doing since the end-result here is a driver that manages all the SNC capabilities correctly and presents them to the system in the 'currently preferred' way.

Quirks are only required where a system does something unexpected that needs individual attention. There should be no need of them for the SNC.

---

### Post by Migs on 2008-05-22
> **IntuitiveNipple said:**
> I am aware of the quirks initiative, but it has little if any impact on what I'm doing since the end-result here is a driver that manages all the SNC capabilities correctly and presents them to the system in the 'currently preferred' way.

Quirks are only required where a system does something unexpected that needs individual attention. There should be no need of them for the SNC.
Thats good to hear and quite a relief that no double work was done. I was afraid the quirk initiative was doing the same, because they where releasing some HAL quirks for specific models. Anyway I will keep an eye on the linux 
-kernel acpi mailinglist;)

---

### Post by 2hot6ft2 on 2008-05-23
Sony Vaio PCG-FXA48 same as the PCG-FXA49 which is already in here.

I know this thread is about the fn key functions, however I've been reading sooo many posts and threads tonight I'm not sure where it was I read that the battery is showing up as not-rechargable which mine was doing I thought I would share this just the same before I hit the sack.

I installed kpowersave (it's in the repositories) on my PCG-FXA48 rebooted to xp and made sure everything was fine there as far as the battery was concerned (fully charged and being read) then rebooted back into ubuntu (while running on battery) and the battery info shows up like it should.

Even ran it for a couple hours on battery mousing over the battery indicator once in a while and it gradually dropped and gave a realistic estimate of charge left.

It finally got down to 15% left a few minutes ago at which time I plugged the power back in and it now shows it on a/c power and charging when mousing over it. 17% and charging with 30 mins. of approx. battery run time left.

We now return you to the topic at hand.

My fn key works with the mute, volume only so I'm hoping there will be a fix for the fn key soon. Sleep and hibernate put it in a coma.

---

### Post by freakin-chicken on 2008-05-23
Hi, here are the results for my VGN-NR21Z.
Like many users here, only mute and sound up/down working (Hardy) ...
Hope this will help ... Anyway thanks for all this good job !

---

### Post by benste on 2008-05-26
Regarding your great work !!!
My Fn keys seems to be recognized since the last update, can someone help me to get these ACPI events into keys? -> gnome doesn't know these events

```

benste@vaiofe31m:~$ acpi_listen
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b

```
FN + F5 --> Brightnes down (must linked to nvclock -S -10%)
```

benste@vaiofe31m:~$ acpi_listen
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

```
FN + F5 --> Brightness up (must linked to nvclock -S +10%)
```

benste@vaiofe31m:~$ acpi_listen
sony/hotkey SNC 00000001 00000012
sony/hotkey SNC 00000001 0000003b

```
Fn+ F7 --> change display output mode (should be linked to nvidia settings or xrandr)
```

benste@vaiofe31m:~$ acpi_listen
sony/hotkey SNC 00000001 00000015
sony/hotkey SNC 00000001 0000003b

```
Fn + F10 --> Zoom desktop (maybe it should be linked to compiz)
```

benste@vaiofe31m:~$ acpi_listen
sony/hotkey SNC 00000001 00000017
sony/hotkey SNC 00000001 0000003b

```
FN + F12 --> hibernate (- link it to standby)
```

benste@vaiofe31m:~$ acpi_listen
sony/hotkey SNC 00000001 00000090
sony/hotkey SNC 00000001 00000010

```
S1 - special programable key
```

benste@vaiofe31m:~$ acpi_listen
sony/hotkey SNC 00000001 00000091
sony/hotkey SNC 00000001 00000011

```
S2 - special programbale key 2

---

### Post by benste on 2008-05-26
Callin all Vaio owners:
Same for me: I'm calling all european vaio users who are registered in Club Vaio: 

Please give a short statement into [http://club.vaio.sony.de/clubvaio/de/de/forum/viewthread?thread=54628]("http://club.vaio.sony.de/clubvaio/de/de/forum/viewthread?thread=54628") that we all need sonys help: the more users are posting the bigger the chance of sony with linux driver help.

PS: why is this post in the archive section - please move it - it's up to date also for hardy

---

### Post by Lmack769 on 2008-05-26
here is a PCG-K23 file.

---

### Post by mdoube on 2008-05-26
Hi Benste

I've had some success getting backlight stuff to work on my SZ6.  Currently this issue is being tracked on launchpad
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173652)

While it's not specific to your model, hopefully it will give you some ideas to get started with.  The main thing is to find out which script (if any) is being triggered by your Fn keys, then modify them so they do what they should.  If you discover anything useful, please add it to the bug report!

I've also written a few configuration instructions that might be helpful to people, especially those with later SZ's:
[http://doube.org/hardy-vaio.html](http://doube.org/hardy-vaio.html)

---

### Post by nxfs on 2008-05-27
Well, thanks for your great work on trying to create the driver

I have a VGN-C150P (PCG-6P2L)

I tried spicctrl
got it from synaptic, but that didn't work at all.

Waiting for your drivers, hopefully that'll work.:)

---

### Post by benste on 2008-05-27
One additional thing to your page goube.org:

I added something to launchpad, 

You said that you're using UBuntu 64bit because of 4 GB RAM:
I thought this "bug" in 32bit version is only relevant for Windows systems isn't it?
+ See launchpad post for nvidia way of changing backlight

---

### Post by hihihi on 2008-05-27
> **benste said:**
> Callin all Vaio owners:
Same for me: I'm calling all european vaio users who are registered in Club Vaio: 

Please give a short statement into [http://club.vaio.sony.de/clubvaio/de/de/forum/viewthread?thread=54628]("http://club.vaio.sony.de/clubvaio/de/de/forum/viewthread?thread=54628") that we all need sonys help: the more users are posting the bigger the chance of sony with linux driver help.

PS: why is this post in the archive section - please move it - it's up to date also for hardy


this is a great idea, the best so far beside writting a new driver. 
i' ll put my comment in that thread, thx all.

btw: acpi_listen does not read my fn keys f5 and f6 anymore since upgrade to kernel 2.6.24-17-generic
on xubuntu hardy 64bit.
on 2.6.24-16-generic acpi_listen would see the keys and print the codes...
something is changing...

on

---

### Post by benste on 2008-05-27
My acpi events are also listend in .17
But I don't know what they adress or how to set them to connect with nvclock -S -10 for example

---

### Post by fabrix on 2008-05-28
here is VGN-NR21Z

---

### Post by onlinelli on 2008-05-31
Sony Vaio AR31M

---

### Post by Oztafan on 2008-06-01
Hi IntuitiveNipple

Here is the DSDT file from my Sony Vaio VGN-FS195VP (a swiss model bought about three years ago) running on Ubuntu Hardy Heron. I should mention that when reading the existing dsdt file and recompiling it with Intel's ASL-Compiler (iasl) there are no errors or warnings:

cat /proc/acpi/dsdt > dsdt.aml
iasl -d dsdt.aml > dsdt.asl

Therefore my actual dsdt seems to be fine. However, not one of the FN-keys works! Only after installing Toufik's fsfn-script ([http://ubuntuforums.org/showthread.php?p=5090420#post5090420](http://ubuntuforums.org/showthread.php?p=5090420#post5090420)) they finally responded and everything is fine ... for now.

Keep up the good work! André Barmasse

---

### Post by barlas on 2008-06-01
Sony Vaio VGN-NR220E

---

### Post by lawlezz on 2008-06-02
Any information/support for VGN-G118GN?

---

### Post by benste on 2008-06-02
G118GN
is not listed yet - try it your self and attach the file please.
(You can use search this thread modus)

---

### Post by lusis89 on 2008-06-05
I have a Sony VGN-NR21E; everything except the brightness keys and the wireless switch work.

---

### Post by jkbr on 2008-06-06
Just got an NR21S and most things work under Hardy. The only working function keys are volume and mute, nothing I've tried (xbacklight etc.) works with the backlight -- presumably the same NVidia issues as others have reported.

Thanks for working on this.

---

### Post by ghrider on 2008-06-07
Here's my DSDT. I'm running zenwalk btw. I had to edit the script - one problem, i think, was that acpidump was choking on the created filename.

Here's what the filename was: "PCG-R505DL(UC)      -R0206C1.dsdt.tar.gz"
with parenthesis and spaces - yuk.

I hard coded FILENAME="PCG-R505DL-R0206C1.dsdt" in the script.

So, here's the result. Hope it helps. This laptop has the usual issues in zenwalk - fn keys do nothing, suspend wakes back up with a black screen. I had Hardy Heron 8.04 on it, and the problems were worse. The fn keys would get the machine flashing in an infinite loop - reboot!

---

### Post by esplinter on 2008-06-07
not sure is this version has allready been posted.

I couldn´t get brightness buttons working in this model :(

---

### Post by Ikkath on 2008-06-08
Hey guys, good work.

I have a weird problem with Heron - Vaio FE31Z and everything _almost_ works.

That is sony-laptop loads with no problem, acpi_listen detects the keypresses correctly for shortcuts, and smartdimmer works perfect from the command line.

Here is the problem, nothing is integrated! Gnome_power_manager does not fire smartdimmer (though the scripts seem to use smartdimmer), and the acpi event does not seem to raise the sonybright.sh script?

How do I tie everything together?

---

### Post by benste on 2008-06-09
I've got the same problem on a FE31m,
I'll report asap if there is a solution. -> There seems to be a problem with nvclock which isn't solved yet

---

### Post by pihhan on 2008-06-09
Look how these events does look like. If there is SPIC work after sony/hotkey, or SNC. Common problem for nvidia based laptop is presence of newer Sony Controller instead of SPIC.

If you have SNC in event name, go to /etc/acpi/event.d
There modify every file beginning with sony- .

There is something like:
event=sony/hotkey SPIC 00000001 00000011

change it to:
event=sony/hotkey (SPIC|SNC) 00000001 00000011

modify only SPIC to (SPIC|SNC), numbers are number of event and should be left intact.

Then reload acpid: sudo invoke-rc.d acpid reload
 and try again keys. Backlight might work, volume control, if it havent worked before also.

---

### Post by benste on 2008-06-09
i'm in contact with phihan or so,
It's much more complicated:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652")
I'll post asap if there is something new

---

### Post by shawe_ewahs on 2008-06-09
Here for Vaio FZ38M I add the dmesg output also.

---

### Post by antoniomj on 2008-06-09
Pcg-k25

---

### Post by salemboot on 2008-06-15
My VGN-N220E

---

### Post by benste on 2008-06-16
phihan submited me a solution for FN key problem on my model:
[http://club.vaio.sony.eu/clubvaio/gb/en/forum/viewthread?thread=54628]("http://club.vaio.sony.eu/clubvaio/gb/en/forum/viewthread?thread=54628")

---

### Post by lawlezz on 2008-06-24
> **benste said:**
> G118GN
is not listed yet - try it your self and attach the file please.
(You can use search this thread modus)

I'm having problem loading or getting the dsdt information. I'm using Ubuntu hardy and is completely new to Linux.

Need some help here..

---

### Post by shropshirehobbit on 2008-06-25
please find attached files for a VGN-SZ110. I was checking your tables don't think you've got this model yet ...

---

### Post by dking87 on 2008-06-25
soooo im new to linux and i recently installed it on my vaio vgn-n320e.

reading the beginning of this post i didnt understand how to download the script or even how to make it work. so that is 1 problem and the other is like everyone else is my backlight function keys does not work. if someone could just help me get this workin it would be greatly appreciated.

---

### Post by dulfe on 2008-06-25
One more:

---

### Post by k84 on 2008-06-26
Any updates on this project? maybe an alpha release? I'll be happy to test it. Thanks!

---

### Post by lexus on 2008-06-26
one more
VGN-N230FH

---

### Post by williamportal on 2008-06-26
I am running unders Suse 10.3.  When I run acpi_listen under root, I get output for fn keys like F1 and F2 but nothing for Fn+brightness up or Fn+brightness down.  What does that mean?  Does that mean the brightness control key does not even generate an event under Linux?

---

### Post by pihhan on 2008-06-26
> **williamportal said:**
> I am running unders Suse 10.3.  When I run acpi_listen under root, I get output for fn keys like F1 and F2 but nothing for Fn+brightness up or Fn+brightness down.  What does that mean?  Does that mean the brightness control key does not even generate an event under Linux?

Tell us what notebook do you have, what kernel do you have (uname -r) and we might be able to help you. Check if you have sony-laptop module loaded (lsmod |grep sony_laptop). For my FZ version for example i need 2.6.23 or higher linux kernel.

---

### Post by areskz on 2008-06-27
Here is mine - **VGN-NR11SR/S**.

---

### Post by meisterkarsten on 2008-06-28
here is mine:

---

### Post by jackhynes on 2008-06-28
Vaio VGN-FJ1S

---

### Post by d_skillz on 2008-06-28
I am a new Linux user, Used to mess around the various distros, knoppix, redhat & mandrake. Using Pcs for 22 years from MSDOS & Win 3.1. I have just been using Ubuntu 8.04 Hard Herron for 2 weeks now on my Sony vaio vgn-n325e laptop and I have serious acpi problems. Machine wont shutdown without hard power-off, restarts fine, cant see battery state or ac adapter states. Please help, I have completely formatted vista, I am so impressed with the system responsiveness but need full laptop compatibility.

[http://ubuntuforums.org/showthread.php?t=842922](http://ubuntuforums.org/showthread.php?t=842922)

---

### Post by lawlezz on 2008-07-03
> **lawlezz said:**
> I'm having problem loading or getting the dsdt information. I'm using Ubuntu hardy and is completely new to Linux.

Need some help here..

Yes... I managed to.. FINALLY understand the instruction. Pls see attached and where and when can we know if we can get fully compatible hardware working on Ubuntu Hardy for VGN-G118GN

BTW, I'm having problem with the following:
1) Mono sound speaker is not giving out full output from built-in speakers
2) Suspected Power leakage/discharge causing accute pain to skin of forearm which is in contact
3)Fingerprint no working still. Trying to get it up with Thinkfinger with no success
4)Windows Logo key not working.
5)Fn F7 display switch not working
6)WLAN lights not responding. Does not switch on when I'm on Wifi connection.

Appreciate any  helpful replies or any available website links to get the above issues fixed.. 

E-mail me @ [email]lawlezz75@gmail.com[/email] if possible.

Thanks,
Lawrence

---

### Post by darylb on 2008-07-03
Hi lawlezz,

For the wifi light, see this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090"). The fix involves installing the "linux-backports-modules-hardy" package. See the description of that bug for more details.

Daryl

---

### Post by lawlezz on 2008-07-03
Thanks a lot Daryl.. I've got this fixed... 

Cheers! I love Linux community!

Lawlezz

---

### Post by darylb on 2008-07-03
:) Glad I could help.

---

### Post by ajk73 on 2008-07-03
Vgn-ar51j-r1050j8

---

### Post by d_skillz on 2008-07-03
Here's my file, I can't shutdown or use the fn keys or check battery or ac adapter state. Please help.

---

### Post by ewal on 2008-07-05
Hi, I am fairly new to this. My Vaio VGN FE28B's FN hot key is not working for any of the buttons and my volume buttons have also stopped working :S any suggestions please?

---

### Post by d_skillz on 2008-07-05
I am seriously beginning to think this thread has been abandoned...
The Function keys are trivial unless you want to project unto an external monitor. What is crucial is monitoring the battery and recharge state does anyone have a fix for that, I really need to use that for my notebook when I am away from a power source.

---

### Post by ganxo on 2008-07-06
so any news about the backlight control?
fz21e with 8400gtm here still using vista.... and now affected by the harddrive problem.

---

### Post by pihhan on 2008-07-07
Check please my directions at [http://www.pihhan.info/sony/sony-hotkeys.html](http://www.pihhan.info/sony/sony-hotkeys.html) and try to get FN keys working. 

But that would not fix backlight control for nvidia cards in any way. We have to wait, until someone find magic registers somewhere to control backlight, or Sony does release how to do that, or nvidia incorporates it into their GPU driver. As first is very rare and second not likely to happen, we can only hope nvidia is able to make it into their drivers soon. But that we cannot solve here, as nvidia drivers are closed source. I know it is not great, but you can alway try to disassemble Sony drivers to get needed registers and accepted values in free time.

To the battery, it is strange, as it does work perfectly for me on my Vaio FZ210CE. Put here please output of command:
cat /proc/acpi/battery/BAT0/*

It happened to me a few times, that i somehow disabled battery status notifying when playing with SNC acpi methods CSBI a RSBI, but i never figured out how i did that nor i was trying hard. But by default i have it working well.

---

### Post by ganxo on 2008-07-07
Well i'm very disappointed with Sony and Nvidia, my old acer 4001 just did the work fine backlight was controled totally by hardware, did not need to use drivers... if it was today i would not buy this laptop, i like it very much ( very small and raw, good screen quality and good overall performance ) but if i want to use linux or bsd or whatever forget... I have everything working on linux minus the backlight...... oh well what can we do.....

---

### Post by d_skillz on 2008-07-07
tried that commmand, this is the result
cat /proc/acpi/battery/BAT0/*
cat: /proc/acpi/battery/BAT0/*: No such file or directory

---

### Post by Toufik on 2008-07-07
/proc/acpi/ is obsolete and kept for backward compatibility. Ubuntu Power Manager uses /sys/class/... So type this:
cat /sys/class/power_supply/BAT0

---

### Post by d_skillz on 2008-07-07
> **Toufik said:**
> /proc/acpi/ is obsolete and kept for backward compatibility. Ubuntu Power Manager uses /sys/class/... So type this:
cat /sys/class/power_supply/BAT0
$ cat /sys/class/power_supply/BAT0
cat: /sys/class/power_supply/BAT0: No such file or directory

---

### Post by dannym978 on 2008-07-08
HI, PSA, this is for a Sony VAIO VGN=CR42S. (ATI Mobility GPU)

Any idea on when the driver will be ready?

---

### Post by brayanbv5 on 2008-07-09
> **bbeirnaert said:**
> hi Here Is The Dstn For A Vaio Vgn-sz4vwn With Bios R0111n0





Hey Could You Help Me By Telling Me How Do I Use This File You Are Showing...and Do You Know How I Can Make My Fn Key Work? I Have The Same Model Of Notebook As That  Vgn-sz4   Thank You!

---

### Post by darylb on 2008-07-10
Hi brayanbv5,

That file will not help you (directly anyway). It is a capture of some ACPI data from your model of Vaio from another user. Its intended use is by the developers working on the driver for the Sony Vaio's FN keys. Once that work is complete, getting your FN keys to work should be easier. For more information on the work they are doing, see the first post of this thread.

---

### Post by benste on 2008-07-10
Dear all, as you may know Vaio will publish new laptops on it's 10th aniversity. Three of them get detailed in several blogs (they're unofficially).

My favorite is the new Z series like in the picture.
Let's think of it how compatible it will be ok ?


[LIST=1]
[*]Hybrid grafic -> we can use the same quirk like in the sz series or?
[*]webcam - included in v4L?
[*]sound - realtec driver works with pulseaudio
[*]fingerprint may not work or?
[*]4 GB RAM -- no problem for UBuntu or? - or should I use a 64 bit version?
[*]Bluetooth Toshiba stack should work
[*]Memory Stick - SD Card Reader - may not work like in older series (TI Card reader)
[*] HSDPA - as far as I remeber they're using a modul wich is supported by the vodafone-mobile... connect linux software
[*]Software PAckage - not useable - why everytime windows

PS: the linux request to sony is stil open
[/LIST]

[IMG]http://img296.imageshack.us/img296/3180/z11wnam3.jpg[/IMG]

---

### Post by benste on 2008-07-10
PS: Does someone know how to scale the image?

---

### Post by Toufik on 2008-07-10
> **benste said:**
> PS: Does someone know how to scale the image?
Gimp ... Images > Scale Image

---

### Post by benste on 2008-07-10
But if I would download the image and scale it (I know about gimp :-))
It may be not so good for me,- someone could say that I published confidental informations :-)

I searched something like html including css - I'll try the HTML TAg



Doesn't work - Does someone know a BB code for resizing the image here?

---

### Post by Toufik on 2008-07-10
I tought you put the image on imageshack... Just insert a link to the image then...

---

### Post by benste on 2008-07-10
:-) would be the normal way but,

---

### Post by swordfish_one on 2008-07-10
Hi,

here is my contribution ...

I am desperate about the Brightness control!!! I wish everything worked, but the brightness is just about 1000 times more important for me than everything else!

I will VERY VERY VERY much appreciate if the brightness control can be sorted out as it is just unbearable, and for various reasons I can't do my work under Windows, so I am loosing my eyesight now and getting headaches on every overcast day!!!

Thank you for your efforts!

Waiting in anticipation!

---

### Post by L815 on 2008-07-12
> **swordfish_one said:**
> Hi,

here is my contribution ...

I am desperate about the Brightness control!!! I wish everything worked, but the brightness is just about 1000 times more important for me than everything else!

I will VERY VERY VERY much appreciate if the brightness control can be sorted out as it is just unbearable, and for various reasons I can't do my work under Windows, so I am loosing my eyesight now and getting headaches on every overcast day!!!

Thank you for your efforts!

Waiting in anticipation!

I agree, I need brightness control on my Vaio for battery life. 
But the front of my laptop gets a bit too hot than what it was on Vista with normal use, so I hope they fix that or I can figure out what it was.
I don't want my laptop to fry o_o

Model: Vaio FZ240E

---

### Post by girishv on 2008-07-14
Hi,

I recently got Sony VAIO VGN-CR343N laptop in India. I installed Linux Mint Elyssa based on Hardy heron. Most of the things including wireless worked out of box, except for function keys for brightness and suspend/hibernate.
The hot keys for volume control works directly. The brightness control works from gnome brightness control (from panel), but not through the function keys after changing sh to bash in the hal scripts.

I am attaching my dst file for your reference as I didnt see it posted in here.


Hope to get the function keys to work . . . .

Girish

---

### Post by giolekva on 2008-07-16
Hi, here is my VGN-FE21B dstd. But on my laptop I can't install wireless driver, can anyone help me. I think that ubuntu can't detect any wireless adapter. I've install ubuntu hardy.

---

### Post by rebegin on 2008-07-16
Hey, thanks for you work in advance :)

here's my VGN-SZ740 N4's generated file

---

### Post by shadwstalkr on 2008-07-16
Hope it helps!

---

### Post by mdoube on 2008-07-19
Hi everyone:
If any SZ owners have been having trouble getting suspend-to-RAM to work while using Hardy and Intel (STAMINA) graphics, a solution has been posted on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/178286") and [here]("http://doube.org/hardy-vaio.html#suspend").

---

### Post by samusz on 2008-07-22
Report for the  Sony Vaio SZ1M/B 

Mostly problems with batteries always on charge and stated as non-rechargeable (seen your posts about it) :

> samusz@Azazel:~$ acpitool -Bv
  Battery #1     : present
    Remaining capacity : 55970 mWh, 100.0%, 00:00:00
    Design capacity    : 57720 mWh
    Last full capacity : 55970 mWh, 96.97% of design capacity
    Capacity loss      : 3.032%
    Present rate       : 100 mW
    Charging state     : charging
    Battery type       : non-recharge, LION

samusz@Azazel:~$ cat /proc/acpi/battery/BAT1/info 
present:                 yes
design capacity:         57720 mWh
last full capacity:      55970 mWh
battery technology:      non-rechargeable
design voltage:          11100 mV
design capacity warning: 0 mWh
design capacity low:     120 mWh
capacity granularity 1:  0 mWh
capacity granularity 2:  10 mWh
model number:            
serial number:           
battery type:            LION
OEM info:                Sony Corp.
The fan is always too fast and I slow it down with ```
while true; do spicctrl -f 12; sleep 0.05; done
``` in a script... not great I gess 

and also a faliure to revert from a suspend or hibernation state from time to time ... (related to acpi ?) > mdoube : thanks for pointing for direction in your post.. I'll go check that ...right now!

No other problems besides the S1 and S2 keys ... that do nothing (and couldnt find a post that solves this) 

Hope it helps !

---

### Post by yleekiyote on 2008-07-22
HELP!!!!

Some nutjob brought us his Sony VGN SZ110 to our office and we can not get it to install from the partition. We tried XP recovery options but also installed XP from different disc and Sony's drivers will not load because the software is not formatted by Sony. Does anyone have the recovery CD's out there for this product, since the nutjob didn't do that first BEFORE blantantly downloading some kind of virus that screwed up his system.

Much love, 

Thanks
yleekiyote

---

### Post by mdoube on 2008-07-22
Yleekiyote:
You can find recovery installation media here: it will fix all XP- and virus-related problems
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

