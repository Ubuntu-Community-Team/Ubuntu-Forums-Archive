---
title: "Keyboard Dell Sk-8135"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by p47 on 2006-06-25
Hello I hope you can help me becouse ubuntu does not detect my volume control button.

I have a desktop Dell XPS and I have a multimedia keyboard and I have selected "Dell multimedia keyboard" in the keyboards but I think that the problem is not that selection if not that ubuntu doesn't detect my button.

What should I do ?
When I go to conbination of keys and I select the volume control and I move the botton of vomule, ubunto doesn't make nothing, that is the reason thath I think Ubunto doesn't detec that key or roll button.

Can you help me !

---

### Post by mabaw on 2006-08-11
> **p47 said:**
> Hello I hope you can help me becouse ubuntu does not detect my volume control button.

I have a desktop Dell XPS and I have a multimedia keyboard and I have selected "Dell multimedia keyboard" in the keyboards but I think that the problem is not that selection if not that ubuntu doesn't detect my button.

What should I do ?
When I go to conbination of keys and I select the volume control and I move the botton of vomule, ubunto doesn't make nothing, that is the reason thath I think Ubunto doesn't detec that key or roll button.

Can you help me !

everything is explained there : 

[http://txzone.net/blog/index/2005/11/25/89-volume-du-sk-8135-sous-ubuntu](http://txzone.net/blog/index/2005/11/25/89-volume-du-sk-8135-sous-ubuntu)

There's also a more detailled guide (in chinese, but babelfish is your friend) which also shows how to setup the Logitech MX series mouses.

[http://blog.istef.info/2006/07/28/configure-dell-sk8135-and-logitech-mx500-in-ubuntu606/](http://blog.istef.info/2006/07/28/configure-dell-sk8135-and-logitech-mx500-in-ubuntu606/)

---

### Post by p47 on 2006-09-02
Hello mabaw.
I am be really grateful for your response.

I have been reading about devices but it doesn't answerd my questions, so had to contact Liu and he sends me the solution.
Now I've the solution in english because I think that it is only in other Language, I hope can help.

English... [http://patch.timesofcoffee.com/data/files/sk8135.txt](http://patch.timesofcoffee.com/data/files/sk8135.txt)

Español ...[http://patch.timesofcoffee.com/index.php?blog/show/Multimedia_Keyboard_Dell_sk8135](http://patch.timesofcoffee.com/index.php?blog/show/Multimedia_Keyboard_Dell_sk8135)

Kind Regards

---

### Post by QettoE on 2006-09-27
> **p47 said:**
> Hello mabaw.
I am be really grateful for your response.

I have been reading about devices but it doesn't answerd my questions, so had to contact Liu and he sends me the solution.
Now I've the solution in english because I think that it is only in other Language, I hope can help.

English... [http://patch.timesofcoffee.com/data/files/sk8135.txt](http://patch.timesofcoffee.com/data/files/sk8135.txt)

Español ...[http://patch.timesofcoffee.com/index.php?blog/show/Multimedia_Keyboard_Dell_sk8135](http://patch.timesofcoffee.com/index.php?blog/show/Multimedia_Keyboard_Dell_sk8135)

Kind Regards



I love ya!

---

### Post by infinitezero on 2007-02-23
Can someone please repost the instructions in English.



Thanks,
iz

---

### Post by infinitezero on 2007-02-23
Does anyone know if it is support under EDGY?

---

### Post by ratthing on 2007-03-14
> **infinitezero said:**
> Can someone please repost the instructions in English.
The instructions were in a new place on p47's web site [http://patch.timesofcoffee.com/?p=9]("http://patch.timesofcoffee.com/?p=9").  There's also a Spanish version there.  

I've cleaned them up for clarity and added some additional information and notes of my own.  Thanks to p47 and [Liu]("http://blog.istef.info/2006/07/28/configure-dell-sk8135-and-logitech-mx500-in-ubuntu606/"), who helped p47 figure this all out.

The downside: after following all the directions, mine doesn't work when started from the command line.  However, I'm using Kubuntu, so that may be part of the issue.  I also haven't rebooted my system as I am in the middle of some other things and can't just randomly reboot.  It may be an issue with the udev rule, too, I'm not familiar with that stuff, and I thought that part of p47's & Liu's instructions were a little unclear, so I was kind of guessing.

YMMV, I hope this helps out someone else.

If anyone knows the closest match for SK-8135 in xkeycaps' list of keyboards, could you please share here?  I'm trying to resolve a keymapping issue in QEMU, which is how I found this thread.

Edit: I accidentally rebooted while fiddling with my QEMU session :-(, and this did not make sk8135-pcm work.  For that matter the "play/pause" key also does not work under Kubuntu, either, though all the other multimedia keys do.


TIA--
=RT=

==============RT's Instructions=====================

1. Pre-requisites:
[LIST]
[*]aumix
[*]libxosd-dev (will install some other dependencies)
[*]linux-headers appropriate for your arch and kernel version, for example linux-headers-2.6.17-11-386
[/LIST]

sudo apt-get install auxmix libxosd-dev linux-headers-KERNELXX-ARCH

1a. Get sk8135 here: [http://patch.timesofcoffee.com/wp-content/uploads/2007/02/sk8135-pcm.c]("http://patch.timesofcoffee.com/wp-content/uploads/2007/02/sk8135-pcm.c")

2. Compile the file sk8135 and move to /usr/bin
gcc `xosd-config --cflags --libs` sk8135-pcm.c -o sk8135-pcm
sudo cp ./sk8135-pcm /usr/bin/.

(I found these compile instructions for xosd-using programs [http://ldots.org/xosd-guide/using_libxosd.html]("http://ldots.org/xosd-guide/using_libxosd.html"))

3. Now we need to figure out what event handler our keyboard's special keys are using:

cat /proc/bus/input/devices  

Look for "Dell Dell USB Keyboard Hub" or "Dell Dell USB Keyboard".  In my case I found two entries for "USB Keyboard".

NOTE: The &#8220;event?&#8221; is the number of the event that it shows associated with a device in the above output, look for a line under your device like this:

H: Handlers=kbd event1

It might be "event1", or it could be another event number.  Again, in my case I had two entries, "event1" and "event2"; YMMV depending on what you have hooked up to your computer.

4.  Let's test to make sure we have the correct event number:

sudo sk8135-pcm /dev/input/event?  

Insert your event number instead of the "?".  Now turn your volume control dial, and if you have the correct event number, a green bar will appear on your monitor near the top left hand corner, with "-----" symbols.  I could detect no movement as a result of turning the nob. 

If you got the event number right on your first try, exit the program with <Ctrl>+<C>.  If you didn't see a bar, try a different event number.  In my case, the special keys were the second event number in the list.

5. Now type:

 udevinfo -a -p $(udevinfo -q path -n /dev/input/event?)

again entering the event number that resulted in a bar instead of "?".  You should find a line:

SYSFS{modalias}=="usb:v413Cp2010d0200dc00dsc00dp00ic03isc00ip00"

If it doesn't match exactly, you should use yours in the udev rule below; the line above is the very first SYSFS{modalias}=="usb:" line in the output of udevinfo.

6. Now you have to create a udev event rules: 

sudo gedit /etc/udev/rules.d/19-local.rules

Add to this file, the following, all on one line (and check your quotes if you are cutting and pasting):

KERNEL=="event[0-9]*", SYSFS{modalias}=="usb:v413Cp2010d0100dc00dsc00dp00ic03isc00ip00 ", NAME="input/event?"

Again, enter your event number to replace the "?", e.g. "input/event2"

7. Create a startup script in /etc/init.d so the sk8135-pcm program will start on boot:

sudo gedit /etc/init.d/local 

#!/bin/sh
echo "Setting up Dell SK-8135 Keyboard..." sk8135-pcm /dev/input/event? &

Again, replace "?" with your event number, save your file and exit.

8. Now change the permissions on the start up script, and add it to the startup sequence:

sudo chmod 744 /etc/init.d/local 
sudo update-rc.d local defaults

==========end RT's Instructions========================

**The following is verbatim from p47's site, I didn't modify the source******
Note: when you download the file of liu&#8217;s web-site the volume control is very slow you can change the velocity of that change some parameters on the source.

sprintf(buffer, &#8220;aumix -w+%d&#8221;, ev[yalv].value);and
sprintf(buffer, &#8220;aumix -w%d&#8221;, ev[yalv].value);change ev[yalv].value to ev[yalv].value*2.now save the file sk8135-pcm.c and compilegoogle.com &#8212; how to compile in ubuntu &#8212; and after do all again ¡you know! just if you want to do faster your volume control.
If you dont understand me. this is the email that liu answer me some months ago. 
|||||||||||||||||||||||
Hello p47,
With the help of GNOME XKB Extension, most multimedia keys in SK-8135 work fine except the Volume Control. To make the volume control works, you need the two software below:
1. sk8135-pcm
Download it from my site: [http://blog.istef.info/files/sk8135-pcm](http://blog.istef.info/files/sk8135-pcm) to /usr/bin, and make it excuteable ( sudo chmod +x /usr/bin/sk8135-pcm).
2. aumix
sudo apt-get install aumix
Then, we should get the keyboard events. Type the following command in console.
cat /proc/bus/input/devices
find the device named Dell Dell USB Keyboard Hub (may have two), get their event handlers (Handlers)
Do a test to find which event is what we want.
sudo sk8135-pcm /dev/input/event?
the event? is the event handlers that you get above.
After that command, play a music and twist the volume control. If the volume changes, the event is right. Press Ctrl+C to quit this program.Type udevinfo -a -p $(udevinfo -q path -n /dev/input/event?) in console, write down the first SYSFS{modalias}. It may like this: SYSFS{modalias}==&#8221; usb:v413Cp2010d0100dc00dsc00dp00ic03isc00ip00&#8243;

Write an udev rule:
sudo gedit /etc/udev/rules.d/19- local.rulesAdd following linesKERNEL==&#8221;event[0-9]*&#8221;, SYSFS{modalias}==&#8221;usb:v413Cp2010d0100dc00dsc00dp00ic03isc00ip00 &#8220;, NAME=&#8221;input/event10&#8243;
NOTE you should change the blue string to yours.
Modify the /etc/init.d/local
sudo gedit /etc/init.d/local
Add following lines:
echo &#8220;Setting up Dell SK-8135 Keyboard&#8230;&#8221;
sk8135-pcm /dev/input/event10 &
Save, then
sudo chmod 755 /etc/init.d/local
sudo update-rc.d local defaults
to make the rules take effects. Reboot your computer, the multimedia Volume Control should work.
|||||||||||||||||||||||
 Rick I hope it will works fot you !
****************end p47's and Liu's comments***********************

---

### Post by p47 on 2007-03-14
I hope it work's for you :P

[http://patch.timesofcoffee.com/?p=9](http://patch.timesofcoffee.com/?p=9)

ratthing: I think your text is better. lol xD.

México México México ...

---

### Post by Species9999 on 2007-05-03
Hi !

I tested the Volume with 

sudo sk8135-pcm /dev/input/event5 

and the green Line on the top of the Screen works.


The output of 

udevinfo -a -p $(udevinfo -q path -n /dev/input/event5) 

is:

```

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/input/input5/event5':
    KERNEL=="event5"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{dev}=="13:69"

  looking at parent device '/class/input/input5':
    KERNELS=="input5"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{modalias}=="input:b0003v413Cp2010e0110-e0,1,3,k71,80,8C,8E,90,9B,9E,9F,A3,A4,A5,A6,AB,AC,AD,ra20,mlsfw"
    ATTRS{uniq}==""
    ATTRS{phys}=="usb-0000:00:1d.0-1.1/input1"
    ATTRS{name}=="Dell Dell USB Keyboard Hub"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1':
    KERNELS=="2-1.1:1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{interface}=="Dell USB Keyboard Hub"
    ATTRS{modalias}=="usb:v413Cp2010d0100dc00dsc00dp00ic03isc00ip00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="01"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1':
    KERNELS=="2-1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{product}=="Dell USB Keyboard Hub"
    ATTRS{manufacturer}=="Dell"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="3"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0100"
    ATTRS{idProduct}=="2010"
    ATTRS{idVendor}=="413c"
    ATTRS{bMaxPower}==" 50mA"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{configuration}=="KKMPD94302"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1':
    KERNELS=="2-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{product}=="Dell USB Keyboard Hub"
    ATTRS{manufacturer}=="Dell"
    ATTRS{maxchild}=="3"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="2"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0100"
    ATTRS{idProduct}=="1003"
    ATTRS{idVendor}=="413c"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}=="Dell USB Keyboard Hub"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.20-15-generic uhci_hcd"
    ATTRS{maxchild}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00008086d000027C8sv00001028sd000001ABbc0Csc03i00"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="18"
    ATTRS{class}=="0x0c0300"
    ATTRS{subsystem_device}=="0x01ab"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{device}=="0x27c8"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

There is no line with 

[COLOR="Red"]SYSFS[/COLOR]{modalias}=="usb:v413Cp2010d0200dc00dsc00dp00 ic03isc00ip00"

I put the Line 

KERNEL=="event[0-9]*", ATTRS{modalias}=="usb:v413Cp2010d0100dc00dsc00dp00ic03isc00ip00", NAME="input/event5"

in my 19-local.rules but this doesent work

SYSFS.... doesent work too.

Someone an Idea ?

MFG Species9999

P.S. Sorry for my English, i am German :-)

---

### Post by jsteidl on 2007-05-07
hi!

i tried that too, but i have the same problem as Species9999.
Any ideas or progress on this one?

---

### Post by icantdothatdave on 2007-05-30
I am also having the same problem as Species9999. Could this be because it works in Edgy, but not in Feisty? Please help!

---

### Post by oiram on 2007-06-27
What I've noticed following RT's manual that in Feisty there is a line:

ATTRS{modalias}=="usb:v413Cp2010d0100dc00dsc00dp00ic03isc00ip00"

and I reckon ATTRS replaced SYSFS as the rest matches details provided by RT.
Anyway it is working for me fine, thanks RT.

oiram

---

### Post by jsteidl on 2007-06-28
After trying every possible version of strings i still cant get the knob to work.

for those of you that managed it:

please post your xorg.conf
```
Section "InputDevice"
        Identifier  "Keyboard0"

```

with all the details.

also: which model did you select in the GNOME (if you are using GNOME) Keyboard-Settings-Dialogue?

hope this will get me forward :)

---

### Post by p47 on 2007-07-02
it should work's fine man ... let me think about !

---

### Post by Species9999 on 2007-07-13
When I start Ubuntu, the Volume doesn't work.

I Press alt+F2 an type:   sk8135-pcm /dev/input/event5

and than my volume works fine (with the green +++++ on the top).


There is something wrong at start up !?
Perhaps the group "audio" or the "user" can not start the script. (Only Root can do?)


How or where can I see if there are errors during start up ?


I start my volume control now manual with alt+F2, that's not comfortable.

Species !

---

### Post by dulbirakan on 2007-07-26
I was having that same problem with species9999. I noticed that there is a mistake in the 7th step of instructions. I have solved my problems at work, now I will try to sort things out at home.

Just use ATTRS..... in the 5th step and in the 7th step write this in the file:

#!/bin/sh
echo "Setting up Dell SK-8135 Keyboard..."
sk8135-pcm /dev/input/event? &

I hope it works for you.

---

### Post by dulbirakan on 2007-08-01
Hi guys, I still could not get it working at home. I can see the green dashes on the screen but turning the knob has no effect on volume. Also I see no pluses. 

I am using Creative SB Audigy LS btw.

Suggestions?

---

### Post by Species9999 on 2007-08-01
> **dulbirakan said:**
> I was having that same problem with species9999. I noticed that there is a mistake in the 7th step of instructions. I have solved my problems at work, now I will try to sort things out at home.

Just use ATTRS..... in the 5th step and in the 7th step write this in the file:

#!/bin/sh
echo "Setting up Dell SK-8135 Keyboard..."
sk8135-pcm /dev/input/event? &

I hope it works for you.

Thanx..... This works fine for me :-)

Hope you found a way for yourself.

Species !

---

### Post by dulbirakan on 2007-08-02
Glad to hear that Species,

I removed my SB Audigy LS (was not so different than the OB solution anyway) and now sk8135 is working.

And for the problem in start up there is another (perhaps better) solution. Just add the commands to /etc/init.d/rc.local and it should work. For more detail look [here]("http://ubuntuforums.org/showthread.php?p=3088639").

Also I found another solution I think it might be worth taking a look: [btimby's blog]("http://ben.timby.com/?page_id=37").

All seems fine now but I have a huge problem. I am upmixing all sound to 5.1 and both sk8135pcm and volumed control only the front speakers.

Suggestions?

---

### Post by RingWraith on 2007-10-11
This is to all that have problems using the above tutorial in **Gutsy**!

The aumix package in Ubuntu seems to be buggy. In  order to check, fire up a terminal and launch aumix. If the only message displayed is "aumix: SOUND_MIXER_READ_DEVMASK", this is probably your case.

As far as I know a bug has been already filed in Launchpad.

You basically have two solutions:

1) Wait for the maintainer to fix the package.
2) Download and install a good package from Debian:

[ftp://ftp.debian.org/debian/pool/main/a/aumix/aumix_2.8-19_i386.deb]("ftp://ftp.debian.org/debian/pool/main/a/aumix/aumix_2.8-19_i386.deb")

After installing this package, everything should work just fine (including the green bar with pluses and minuses). BTW, I have used ATTRS{modalias}...

I hope this helps.

Cheers

---

### Post by Yarbo on 2007-11-09
You'd think the developers would write something like this into Ubuntu so that it works out of the box.  Especially now that Dell officially offers PC's pre-installed with Ubuntu.

This is waaaay more work then the average Linux n00b can figure out.  I am pretty pretty new to Linux myself.

I managed to get this working, but only after a few hours of frustration.

---

### Post by []Milo on 2007-11-20
> **Yarbo said:**
> You'd think the developers would write something like this into Ubuntu so that it works out of the box.  Especially now that Dell officially offers PC's pre-installed with Ubuntu.

This is waaaay more work then the average Linux n00b can figure out.  I am pretty pretty new to Linux myself.

I managed to get this working, but only after a few hours of frustration.

Agreed.  i'm not exactly a linux n00b but really don't have time for all of that fannying about :) 
OOTB solution please!!!  (and yes, why on earth not, since Dell distributes Ubuntu)

---

### Post by szczym on 2007-11-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/139582](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/139582) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Helo 

Where actually is valid solution for that problem? Most of tutorials mentioned in that thread give 404, palpably its better idea to  copy and paste the solution to ubuntu wiki.

Also is that a valid bug for that problem ?
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/139582](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/139582)

cheers !

---

### Post by Jyhem on 2007-12-01
> **RingWraith said:**
> 
[ftp://ftp.debian.org/debian/pool/main/a/aumix/aumix_2.8-19_i386.deb]("ftp://ftp.debian.org/debian/pool/main/a/aumix/aumix_2.8-19_i386.deb")



This definitely helped my (more general) issues with aumix.
(I wanted to map keyboard keys to 'aumix -v +4')

That's on a kubuntu 7.10

---

### Post by QualityPancakes on 2007-12-29
I am very new to linux(less than 24 hours), and the workarounds that are being posted are pretty well beyond me, or at least what I'm willing to get myself involved in at this point. This keyboard is such a huge headache. I saw one of the computers at work with one and really liked it, so I ordered one for my winbox. Took almost a week to track down the drivers required to get the thing to work properly(to my knowledge Del still hasn'e actually released any drivers specifically for it).

---

### Post by SilvaRizla on 2008-04-12
This is fixed in Hardy, but one notch turns the volume by 10% which is just too much, anyone know how to configure this?  I'm on KDE is that makes things any different.

---

### Post by []Milo on 2008-04-27
Indeed, this does work in Hardy but I get a full 18 clicks from 0 to 100% vol (in Gnome), which I think is actually fine.

Thanks again to whomever made this work, you rock:guitar:

---

### Post by billynomates on 2008-06-17
> 
1a. Get sk8135 here: [http://patch.timesofcoffee.com/wp-content/uploads/2007/02/sk8135-pcm.c]("http://patch.timesofcoffee.com/wp-content/uploads/2007/02/sk8135-pcm.c")

2. Compile the file sk8135 and move to /usr/bin
gcc `xosd-config --cflags --libs` sk8135-pcm.c -o sk8135-pcm
sudo cp ./sk8135-pcm /usr/bin/.

(I found these compile instructions for xosd-using programs [http://ldots.org/xosd-guide/using_libxosd.html]("http://ldots.org/xosd-guide/using_libxosd.html"))

Hey, the link doesn't work any more, but I found the same C program [here]("http://www.google.co.uk/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Ftxzone.net%2Ffiles%2Fprojects%2Fsk8135%2Fsk8135-pcm.c&ei=ntBXSIG8KZCc0QSzs5WFBw&usg=AFQjCNGn-3S_NnavKzz2_qYksBjMUCq1VQ&sig2=_Q9CEo0NJtmwhEAgPdr7gw"). However, it doesn't compile! I get a bunch of undefined reference errors.
Do you have the original program, or know where to find it?

---

