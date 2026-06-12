---
title: "MX5000, hiddev devices, bluetooth."
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by Refrozen on 2006-12-25
I have recently purchased an MX5000 and tried to set it up with my linux box, after a few hours of screwing around with getting mx5000tools installed, I've reached another problem... which is that calling the mx5000-tool program gives me this error "Could not open device or improper device (No such file or directory)".

" -d, --device <path>   Path to the hiddev device"

I can't figure out what the hiddev device is, or even what hiddev is. Google's not helping, how can I find the hiddev device for my Logitech MX 5000 keyboard, and why isn't the program detecting it?

e: I used [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) to set up the device.

---

### Post by spockrock on 2007-01-01
hmmm I am having the same problem here I am trying to figure it out but no luck here either.  I am sure it has to do something with me not having the /dev/usb or /dev/usb/hid folders....but I do get hiddev0 in my /dev folder...so :s

---

### Post by eriol78 on 2007-01-05
if you have a /dev/hiddev0 file, try:

```
sudo max5000-tool --device /dev/hiddev0 --beep
```

if you hear a double beep, then you 've got it. 

If you do have a /dev/usb file, try running mx5000-tool with sudo, it just might work.

---

### Post by justintime32 on 2007-01-05
I'm having the same problem.

When I run the command above, I do hear two beeps, and the mx5000-tools program works fine for everything else. However, I cannot run the daemon (mx5000d). When I run this command:
```
sudo mx5000d  --device=dev/hiddev0
```
I just get this error:
```
** ERROR **: Can't open input device: No such file or directory (2)
aborting...
Aborted (core dumped)
```
Any ideas?

---

### Post by spockrock on 2007-01-07
hmm I do have the beep but I still get a core dump on mx5000d.... :s

I have tried sudo mx5000d -d /dev/hiddev0

and I get this error, ......

```
** ERROR **: Could not open hiddev device

aborting...
Aborted (core dumped)
```

I am perplexed about mx5000d but tools works fine........

---

### Post by gearshifter on 2007-01-11
i've got the same problem

Anyone get mx5000d to work yet?


edit:  I also have the problem with the volume touchpad where if i go all the way down to the mute, i can't track it back up to volume.  It gets stuck down there.

---

### Post by spockrock on 2007-01-13
funny thing is when I setup my volume hotkeys for some reason the up slider is read, it says volume up on the hotkey setup, however it doesnt work in gnome.

---

### Post by edmondt on 2007-01-22
Thanks for the tip, it works and displays the time when I do:

sudo mx5000-tool --device /dev/hiddev0 --t

This displays my name :)

sudo mx5000-tool --device /dev/hiddev0 -n Edmond

So from what I saw from the forum, I'll create a rule by creating this file:

sudo gedit /etc/udev/rules.d/19-local.rules

and put this in for the correct permission:

KERNEL=="hiddev*", NAME="%k", MODE="666"

now I can run **mx5000-tool --device /dev/hiddev0 -n** Edmond without sudo.

not sure about mx5000d... I think it might have something to do with this to fix.

---

### Post by bunger2 on 2007-02-12
> **spockrock said:**
> hmm I do have the beep but I still get a core dump on mx5000d.... :s

I have tried sudo mx5000d -d /dev/hiddev0

and I get this error, ......

```
** ERROR **: Could not open hiddev device

aborting...
Aborted (core dumped)
```

I am perplexed about mx5000d but tools works fine........



I can report the same issue here. Tools works fine (although I am somewhat unsure what to do with it), but the daemon will not start. Core dump every time.

---

### Post by dremon on 2007-02-24
Try sudo modprobe uinput.
It works for me.

---

### Post by Timtro on 2007-03-11
> **dremon said:**
> Try sudo modprobe uinput.
It works for me.

Wow, that seems to work. After I do this, the deamon seems to start (although I still have to figure out what to do with it)

Why does that work? I maned modprobe, and it says that it removes modules from the kernel. I can't see how that would help!

Thanks!

---

### Post by spockrock on 2007-03-12
I tried sudo modprobe uinput and still cant run the mx5000d daemon...

---

### Post by Timtro on 2007-03-12
> **spockrock said:**
> I tried sudo modprobe uinput and still cant run the mx5000d daemon...

Thats fine, even though it ran for me, it--of course-- didn't work. I read the website for mxtools (still trying to find the documentation though) and found that it explicitly says that the uinput module must be loaded in order to use this software. It seems to have something to do with the act of listening for keystrokes from the keys that the standard drivers don't handle.

---

### Post by dremon on 2007-03-12
The daemon translates certain special keys (not all of them, though) to the recognized xorg key codes.
For example I've managed to bind the "Messenger" key (the one with the buddy icon) to start gaim. And the zooming touch-slider seems to work now.

You can check yourself which keys are working by using xev command.

I've also created an /etc/init.d script to automatically start the mx5000d daemon and the rules to shut it down and start over again for suspend/resume ACPI events. If anybody is interested I can post  this stuff here.

---

### Post by Timtro on 2007-03-12
> **dremon said:**
> The daemon translates certain special keys (not all of them, though) to the recognized xorg key codes.
For example I've managed to bind the "Messenger" key (the one with the buddy icon) to start gaim. And the zooming touch-slider seems to work now.

You can check yourself which keys are working by using xev command.

I've also created an /etc/init.d script to automatically start the mx5000d daemon and the rules to shut it down and start over again for suspend/resume ACPI events. If anybody is interested I can post  this stuff here.


Although I don't have the daemon working yet, I would love it if you would post your clever work. I'm sure it will be quite useful in a very short time.

Thank you.

---

### Post by Timtro on 2007-03-12
Ha! Finally got it to work. I feel a little silly. I finally figured out that modprobe would be ADDING the UINPUT module. Anyhow, I did a little tinkering to remove some of the stuff that I already tried, and in the end, this worked:

```
sudo modprobe uinput
mx5000d -d /dev/hiddev0
```

Which is of course what everyone has been saying to begin with.

Now I really would like dremon's script :)

Dremon:

Would you mind giving me some details of how you managed to bind the keys? I'm not very familiar with the end of Linux. Thanks!

---

### Post by dremon on 2007-03-13
Please find the attached archive with the mx5000 startup scripts.
Installation:
```
# sudo tar xjvf mx5000-daemon.tar.bz2 -C /etc
```
Starting/stopping:
```
# sudo /etc/init.d/mx5000 start|stop
```

The symbolic links are placed in the rcX.d directories to allow automatic starting.

To make it work with ACPI suspend/resume, add the "mx5000" to the STOP_SERVICES parameter in /etc/default/acpi-support file.

Now about the key binding:
- add the xbindkeys to the startup programs (in the System->Preferences->Sessions)
- create the ~/.xbindkeysrc file with the key bindings. This is an example of my settings (I'm using mpd, mpc and gmpc for audio playback control and gaim as a messenger):

```

# Start Media Player
"gmpc"
  m:0x0+c:129

# Play next song
"mpc next"
  m:0x0+c:153

# Play previous song
"mpc prev"
  m:0x0+c:144

# Toggle playback
"mpc toggle"
  m:0x0+c:162

# Stop playback
"mpc stop"
  m:0x0+c:164

# Gaim Messenger
"gaim"
  m:0x0+c:121

```

You can set up this file semi-automatically using xbindkeys-config program, however it may screw things up if you don't place the comments and empty lines exactly like in my example.

---

### Post by Timtro on 2007-03-14
Thats a million dremon. Your efforts are appreciated. I'm in the middle of a rough patch at school, and I don't have a lot of time to go chasing down these details myself.

Cheers,


Tim.

---

### Post by Timtro on 2007-03-14
Notes:

To make this work, I needed to su to root in order to "sudo /etc/init.d/mx5000 start|stop".

Needed to 'sudo apt-get install xbindkeys'.

Thanks.

---

### Post by Apertotes on 2008-02-24
hello, sorry for necroing this thread, but i didnt find any newer related one. i have a problem with MX5000tools.

i have downloaded, configured and installed MX5000tools, at least that is what i think

but everytime i try to run 

> sudo mx5000-tool -d /dev/hiddev0 -b

to make the keyboard emit a sound, i get this

> mx5000-tool: error while loading shared libraries: libmx5000.so.0: cannot open shared object file: No such file or directory

i have tried with many hiddev#, from 0 to 15, but still no luck. i also tried with "-t" instead of "-b" to get the time showing on the lcd panel, but i get the same error.

can anybody help me?

pd: yes, i am a linux noob, so please, try to be patient with me. thanks

---

### Post by fireandlight27 on 2008-03-05
> mx5000-tool: error while loading shared libraries: libmx5000.so.0: cannot open shared object file: No such file or directory

Run:
```
sudo ldconfig
```

That solved the problem for me.

---

### Post by raver_cc on 2008-03-18
Hy there!
I also got an MX5000 with mx5000-tools.
the thing is: the mx5000-tools working fine but when I'm using mx5000d I get an error

```

sudo mx5000d -d /dev/usb/hiddev0
Segmentation fault

```

I hope someone can help me...
cheers!

---

### Post by ghell on 2008-03-20
I've been writing a [cross platform human interface device library](http://sourceforge.net/projects/libhidnet) recently using the MX5000 for testing (I did some of the work on the library by E. Heidstra that mx5000tools is based on).

I've also written [an MX5000 library](http://www.helyar.net/MX5000Lib06.zip) using this HID library. It's not a daemon, it exposes keyboard functionality just like mx5000tool (the tool section, not the daemon section) and the original mx5000lib by E. Heidstra.

The advantages over mx5000lib are that it allows any image format that .net can read (bmp, jpeg, gif, png etc) and it is cross platform (as opposed to only working on 32 bit windows)
The advantages over mx5000tool are that it supports more write options, read options (mx5000tool doesn't do any reading at all from the keyboard), is cross platform and can read more image formats
The disadvantage is that it requires Mono.

Getting the keyboard to beep is as simple as```
MX5000 keyboard = new MX5000();
keyboard.Beep();
```but there is a test application with the library that shows some of the things that can be done.

You must have read access to the /dev/usb/hiddev# of the keyboard. Write access is not required to get the keyboard to beep so you can just use something similar to **[font=monospace]# chmod 644 /dev/usb/hiddev0[/font]** to give all users access to the device without having to run the application as root. If it doesn't have read access to a particular device node and thus can't tell if that device is a mx5000, it will tell you so.

I would appreciate any feedback on this.

Thanks :)

---

### Post by Skerit on 2008-03-22
Even after loading the uinput module I still can't load the daemon ..

I'm getting the same error as other people in this thread:

Could not create uinput device: Cannot allocate memory
** ERROR **: Could not open uinput

What kind of "memory" is it talking about?

---

### Post by deadball on 2008-04-02
I don't even have any hiddev in /dev. Only hidraw! But hidraw doesnt work obviously :(

Running Ubuntu 8.04 with actual bluez-utils (if important ..).

Any Tips?

Thx,
db

---

### Post by Skerit on 2008-04-02
You don't have any hiddev "files" in /dev? (You're not running in the emulated mode, are you? :P)

I still haven't gotten it to work, either.. After an entire week of trying ...

---

### Post by ghell on 2008-04-02
> **deadball said:**
> I don't even have any hiddev in /dev. Only hidraw! But hidraw doesnt work obviously :(

Running Ubuntu 8.04 with actual bluez-utils (if important ..).

Any Tips?

Thx,
dbThe hiddev nodes should be in /dev/usb/ rather than /dev/

---

### Post by Skerit on 2008-04-04
Hmm, they're not ... 

They were at one time, though, but now /dev/usb/ doesn't even exist and all MY hiddev-files are in regular /dev

Doesn't matter where they are, though, it still doesn't work

---

### Post by ghell on 2008-04-04
Make sure the kernel has hiddev loaded (I do not use Ubuntu so I don't know whether it is by default) and try using mknod (plenty of examples of mknod with hiddev0 to 15 on the web)

---

### Post by thwint on 2008-07-16
I think the problem is that refrozen has used the following guide to configure the keyboard.
> **Refrozen said:**
> 

e: I used [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) to set up the device.

He did not use the USB-dongle. 

I have an mx5500 keyboard which is basically the same thing. When I connect my keyboard through this dongle I have a hiddev0 device file and can use mx5000tools.

As my notebook has a built in bluetooth adapter I wanted to get rid of the dongle and configured the connection more or less the same way as described in the mentioned guide.

Since this configuration change I don't have a hiddev file anymore, because Linux directly uses the bluetooth connection. Instead the keyboard is now recognized as event11 (see /proc/bus/input/devices). 
The mx5000tool needs to have the hiddev to work. It tries to verify if the connected device is a "Logitech Logitech BT Mini-Receiver". Therefore it fails with any other devices.

I think using the MX5000 directly connected to bluetooth needs changes in the programming of mx5000tools. 

Is there anyone out there able to implement these changes?

---

### Post by ghell on 2008-07-16
> **thwint said:**
> Is there anyone out there able to implement these changes?

You can email its author and he will make the changes for you. If you tell me what needs changing, I can probably port my Mono MX5000 library to MX5500 (this has been requested on Windows before for the library but as I do not have the keyboard, I cannot test the changes).

Note that my library supports much more than mx5000tools (such as reading from the device) but requires Mono be installed.

---

### Post by thwint on 2008-07-16
Hello Ghell
Browsing the source of the Windows library I've seen, that there's much more than what's in the mx5000tools.

Does your library work with Linux? If so, I can test it for you. Also if you need additional information I can try to find out.

Are you the author of the original MX5000lib? If so, are you aware that the year is not set when updating the date? (I also submitted a bug concerning this)

The only changes needed to be done is native bluetooth support, so that the USB dongle is not needed anymore (direct opening of hci device). 

I already tried to find out how to modify the source, but I don't know how to open the bluetooth device. I'm not sure if the event device can be used (input driver?).

---

### Post by ghell on 2008-07-16
The keyboard seems to have no concept of years. I assume that it just relies on you updating the date frequently enough to be able to correct leap years, daylight savings and the like. If you do not update it frequently it will just say "Logitech MX 5000" on the LCD anyway.

I am not the original author of MX5000lib but I did a lot of work with the original author. I was about to release an entirely new version of that library when my MX5000 completely died unless I used bluetooth (which was not an option for me because it makes dual booting a complete PITA) and it did not start working again on my machine in RF mode until Vista was released.


mx5000tools only works on Linux and only performs a subset of the write operations. The original MX5000lib only works on 32 bit Windows. My library works on 32 bit Windows, 64 bit Windows and any other operating system that has Mono and Hiddev (including Linux, tested on x86 and x64 Debian Lenny).

On top of this portability, it adds many efficiency improvements over the original MX5000lib by removing duplicate and redundant transmissions and reducing the size of large transmissions such as images (where the original MX5000lib essentially padded out every image transmission with 14 packets of unnecessary whitespace). It should also provide a better API to work with and makes use of System.Drawing so that standard image types (PNG, JPEG, BMP, GIF, etc) can be used, and further image types can be used if they are derived from the System.Drawing.Image class, for TGA images and so on). The original library could only use the (propitiatory, I belive) HBMP format for images.

I split the base of this library off into its own cross platform SourceForge HID project (which needs quite a bit of work)
[http://sourceforge.net/projects/libhidnet](http://sourceforge.net/projects/libhidnet)

And you can find the cross platform MX5000 library that uses "libhidnet" at [http://www.helyar.net/MX5000Lib06.zip](http://www.helyar.net/MX5000Lib06.zip) (this requires that Mono be installed from the repos, I assume that hiddev is already in Ubuntu's standard kernels)

This is a library rather than an application so to get some command line application similar to mx5000tools, a small amount of coding is necessary. However, this should only be a few lines of C# and a small set of example code should be packaged with the library anyway.

---

### Post by thwint on 2008-07-17
Hi ghell
I downloaded the source of libhidnet now. To start with I just tried to compile the examples to try if it already works, but I think I miss something with the linking options. 

For now I just added the Product ID (0xb30b) of the new keyboard to the library and compiled it on my system. 

I also compiled the examples for testing. Running the new binary it always gives me the following error: "No MX5000s found.".
Browsing through the code I've seen that the library tries to find /dev/usb/hiddevX.

As the keyboard is connected directly via bluetooth there are now hiddev files for my keyboard. Except /dev/input/input12 I don't know what devices I can use for my MX5500 keyboard.

```

I: Bus=0005 Vendor=046d Product=b30b Version=0100
N: Name="Logitech MX5500 Keyboard"
P: Phys=00:03:7A:DB:64:69
S: Sysfs=/class/input/input12
U: Uniq=00:07:61:9D:D2:50
H: Handlers=kbd event12 
B: EV=12001f
B: KEY=37fff 2c3027 bf004444 0 0 1 10f84 8a27c007 ffff7bfa d9415fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=701 0
B: MSC=10
B: LED=1f

```

---

### Post by ghell on 2008-07-17
> **thwint said:**
> Hi ghell
I downloaded the source of libhidnet now. To start with I just tried to compile the examples to try if it already works, but I think I miss something with the linking options.

The following would compile the libhidnet example for the MX5000 under windows:
```
C:\MX5000\examples>csc /r:..\Hid.Linux.dll,..\Hid.Win32.dll,..\Hid.Net.dll LogitechMX5000.cs
``` so, if I remember rightly, it should just be a case of changing "/r" to "-r" and "csc" to "mcs" or "gmcs" and of course "\" to "/".

This should make it something like```
$ cd ~/MX5000/examples
$ gmcs -r:../Hid.Linux.dll,../Hid.Win32.dll,../Hid.Net.dll LogitechMX5000.cs
```
You probably need to add the standard System.Posix dll from Mono too but this might just be when compiling Hid.Linux.dll.

Really, I should change the layout of those 3 dlls. They were done that way so that I could compile the smallest bit possible on windows and the smallest bit possible on Linux and then compile Hid.Net.dll from either, with the idea that everyone would need all 3 to make it cross platform anyway. However, it seems that many people just want to use part of the library to target one platform, in which case moving a couple of classes around would mean that Linux only users could just use Hid.Linux.dll, Windows only users could just use Hid.Win32.dll and anyone who wants to be cross platform could use Hid.Net.dll (which depends on the other 2 so all 3 then need to be distributed together anyway).


When running the example, you must have read permissions on /dev/usb/hiddevX (usually hiddev0). If it can open a file descriptor even as read only, it can write to it. Mono won't even open the file descriptor if it thinks that you don't have read permissions and you try to open it as read-only, unfortunately.

AFAIK, you have to use /dev/usb/hiddevX because that is how we communicate with HID devices. event and input should be able to listen for keystrokes but not much else.

The MX5000 has different product IDs for bluetooth and RF (bluetooth+hci uses the same as RF, to get it into bluetooth mode you had to hold the red button on the dongle when inserting it), so that might be something that you should look out for on the MX5500 too. I found bluez pretty unstable and saw no reason to use it over RF anyway, unless you want to connect more bluetooth devices up (not including the mouse, that will connect with RF too).

You can try doing something like enumerating all of the connected Logitech HID devices with```
IDevice devices = DeviceFactory.Enumerate(0x046d);
Console.WriteLine("{0} Logitech devices found.", devices.Length);
```

If it says that you have 1 or more found, you can try getting their information. If you cast them to "LinuxDevice"s, you will be able to get more information than if you leave them on "IDevice"s because some of the functionality is limited by ambiguity on Windows. This means that you can do something like```
foreach(IDevice device in devices)
{
  LinuxDevice linuxDevice = (LinuxDevice)device;
  Console.WriteLine("Product ID: {0:x4}, Name: {1}",
    linuxDevice.ProductID, linuxDevice.Name);
}
```

---

### Post by thwint on 2008-07-17
Finally I was able to build the example.exe. I downloaded and installed monodevelop.

There is no hiddev device when I connect the keyboard using laptop internal bluetooth device instead of the Logitech BT Mini Receiver. 

As soon as the keyboard is connected through this dongle I have a hiddev and the example works. My goal is to not use the USB dongle.

So is there a way to get a hiddev device when connected using bluez-utils? Or is it possible to modify the library to open any other device files?

---

### Post by Kiwi-Hawk on 2008-07-17
Hi

I have a Logitech MX5000 Keyboard & Mouse thats dead in the water

on first boot the blue tooth icon show then despairs,..

From what I'm reading Blue tooth is all sorted and should run by default under Elyssa 5
I'm also seeing that the Logitech stuff can be a dog to get going

I want to use this system as a Media center and it would be much safer both for hardware and people not
to have cables across the lounge floor .

I have had no luck so far so any hep would be much appreciated ,.. thanks in advance
Edit:

Did a reboot and got mouse showing as an MX1000, tried to connect and got his error:

Couldn't display "obex://[00:07:61:98:c1:a2]/"

error: host down
Please select another viewer and try again

The thing that blows me away is it works in Mybuntu fine after a little time which the same under garage right?

cat /proc/bus/input/devices

returns:

I: Bus=0003 Vendor=046d Product=c70e Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:04.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
U: Uniq=00076192B5A3
H: Handlers=kbd event4 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:04.0-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input5
U: Uniq=00076192B5A3
H: Handlers=kbd mouse3 event5 
B: EV=1f
B: KEY=37fff ac3027 bf004444 0 0 fff0001 f84 8a37c000 667bfa d941dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0
B: MSC=10


But nothing shows up to load or if it does I get the error at beginning of this message


Cheers
Kiwi-Hawk

---

### Post by thwint on 2008-07-17
With my keyboard combo (MX5500 with MX Revolution) I only had some problems connecting the keyboard.
The mouse was never a problem.

Here's how I did it in Ubuntu:

[LIST]
[*]right click on the bluetooth icon (Bluetooth Manager upper right corner)
[*]in the new window click on "Services" tab
[*]click on "Input service"
[*]click the "Add" button
[*]press the "Connect" button of your mouse
[*]Select your mouse
[*]press the "Connect" button
[/LIST]

For the keyboard I had to go a different way. As my version of Ubuntu doesn't contain hidd I had to do the following from command line:

press the "Connect" button of your keyboard

```
hcitool scan
Scanning ...
        00:07:61:XX:XX:XX       Logitech MX Revolution Mouse

```

```
sudo dbus-send --system --type=method_call --print-reply --dest=org.bluez /org/bluez org.bluez.Manager.ActivateService string:input 
method return sender=:1.8 -> dest=:1.213 reply_serial=2<br>
   string ":1.8"

```
The value after string and the address you received with the previous command are needed for the next command
```
sudo dbus-send --system --type=method_call --print-reply --dest=":1.8" /org/bluez/input org.bluez.input.Manager.CreateDevice string:00:07:61:XX:XX:XX
method return sender=:1.8 -> dest=:1.223 reply_serial=2
   string "/org/bluez/input/keyboard2"

```
With the keyboard string you can do 
```
sudo dbus-send --system --type=method_call --print-reply --dest=":1.8" /org/bluez/input/keyboard2 org.bluez.input.Device.Connect 
method return sender=:1.8 -> dest=:1.242 reply_serial=2

```

Now you're done. The keyboard should work and should be connected every time you restart your system. With this method any mx5000-tools don't work (the problem I try to find a solution now).

---

