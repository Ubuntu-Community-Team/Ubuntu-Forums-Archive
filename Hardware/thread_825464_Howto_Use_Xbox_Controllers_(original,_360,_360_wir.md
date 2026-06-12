---
title: "Howto: Use Xbox Controllers (original, 360, 360 wireless, 360 guitar) with Linux"
date: 2008-06-11
forum: Hardware
---

### Post by wootah on 2008-06-11
[SIZE=5]Howto: Use Xbox Controllers (original, 360, 360 wireless, 360 guitar) with Linux[/SIZE]
[SIZE=1](June 10th, 2008 ) by ~Wootah[/SIZE]
 
[SIZE=4][COLOR=Red]EDIT[/COLOR][/SIZE][COLOR=Red]:[/COLOR]
[COLOR=Red]June 7th, 2011: This information has changed significantly since its original posting. Please see the edits that follow (mostly link updates)[/COLOR]

[SIZE=5]Intro[/SIZE]
 Currently, Xbox controller support for Linux has been limited at best and the only available option we have, is the xpad kernel driver. Unfortunately, this driver doesn't work with 360 game pads (well or at all?). Thus, grumbel wrote a user space driver for xbox controllers.

 The author, grumbel, provided very good instructions on how to install and use the driver, but I figured this would help out a lot and provide more exposure so we could potentially help better the driver.

 As of this writing (June 10th, 2008 )the current version from his website is **0.2rc1**.

[SIZE=5][COLOR=Red]Warning (as always :())[/COLOR][/SIZE]
 Please note, I based this guide off of my system, Ubuntu 7.10. Please let me know if there are any changes for newer versions of Ubuntu (8.04+). This howto is a guide and may not work 100% for your system, setup, geographical location, humidity, country, gender or personal height. I am not responsible for what you do to your machine, cat, parents, body, xbox (and its controllers) or any item by following this guide and neither is the author of the xbox driver, grumbel. No guarantees what so ever folks.

**Do so at your own risk (also known as try it on a test machine first, please :))**

[SIZE=4]Supported Controllers[/SIZE]
[LIST]
[*]Original Xbox controllers through USB (with a cable modification)
[*]Xbox 360 USB Controllers
[*]Xbox 360 Wireless Controllers through the Wireless USB Adapter
[*]Xbox 360 USB Guitar
[/LIST]
 Some third party controllers may work as well (MadCatz) and they are probably already available. To check support for a particular controller, review the file *xboxdrv.cpp* and look for the line *XPadDevice xpad_devices*. You may even be able to add in support for your particular controller by adding the hardware identifiers into xboxdrv.cpp and recompiling the driver (the README talks about this further in depth).

[SIZE=4]Features[/SIZE]
[LIST]
[*]Executes in user space on top of libusb. This means that you do not have to recompile the kernel
[*]Provides a joystick device (/dev/input/js0)
[*]Allows remapping of the buttons and axises
[*]Support of the analog triggers (LT, RT) along with reconfiguration into a digital mode (they function just as buttons)
[*]Change the LED status of the ring of light on the 360 pads
[*]Many other features! See the author's webpage listed in the links below
[/LIST]

[SIZE=4]Missing Features[/SIZE]
 Not all features have been implemented, as the current version is 0.2 which was released on May 3rd, 2008. 
[LIST]
[*]Rumble support is limited with no force feed-back. Only scripts or simple testing may use this feature.
[*]No Mouse emulation (yet)
[*]Xbox dancemat (for games like Dance Dance Revolution) is still untested. The author would like some help :)
[*]Chatpad and Headset are not implemented yet. Once again, the     author needs help.
[/LIST]
 [SIZE=5]Installation[/SIZE]
 Alright, down to business.
 
[SIZE=4]Requirements/Setup Overview[/SIZE]
[LIST=1]
[*]The following kernel modules must be included and loaded:
[LIST=1]
[*]uinput
[*]joydev
[/LIST]
 
[*]The **xpad** kernel module **IS NOT LOADED**.
[*]The following libraries and     tools for compiling:
[LIST=1]
[*]libusb
[*]boost
[*]scons
[*]uinput (Ubuntu 7.10 already provides this, *afaik*)
[/LIST]
 
[*]The driver itself from the author's website [http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")[]("http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2")
[/LIST]
 For the advanced users along with those familiar with **scons**, this should be enough to get you going. You lucky guys can skip the next section (and check out **Driver Usage**), but for myself and the others, please continue :)

[SIZE=4]Pre-compiling Setup

[/SIZE] [SIZE=3]Step One[/SIZE]
 We must ensure we have the kernel modules loaded listed in 1a and 1b. To check, we can issue the following commands at the terminal:
```

lsmod | grep uinput
lsmod | grep joydev

```If these modules are not loaded, you may load them by issuing modprobe commands:
```

sudo modprobe uinput
sudo modprobe joydev

``` If you did add these modules, then you should probably ensure that they are automatically loaded every time you start up your machine. To ensure this occurs, edit */etc/modules* and add the modules at the end (perhaps with a comment to let you know what they are used for and maybe a date for reference.) Example:
 /etc/modules :
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
fuse

# The following two modules are used with the xbox controller driver.
# Added on June 10th, 2008
uinput # for creating userspace drivers. 
joydev # for joystick devices

```[SIZE=3]Step Two[/SIZE]
 Check to see if the xpad module is loaded:
```

lsmod | grep xpad

```For my machine, this module was not loaded; thus, I lucked out. If it is loaded for you, you may issue the rmmod command:
```

sudo rmmod xpad

```The author states that *"rmmod might not be enough since it might be automatically loaded again"*.

 **Could someone let me know how one would fix that?**

[SIZE=3]Step Three[/SIZE]
 Now that we have the proper modules loaded, we need the software and libraries to compile everything together. If you do not have the build-essential package, you will need that first:
```

sudo apt-get install build-essential

```Issue the following commands:
 **libusb:**
```

sudo apt-get install libusb-dev

``` [B]
libboost:[/B]
```

sudo apt-get install libboost-date-time-dev libboost-date-time1.34.1 libboost-dev libboost-doc libboost-filesystem-dev libboost-filesystem1.34.1 libboost-graph-dev libboost-graph1.34.1 libboost-iostreams-dev libboost-iostreams1.34.1 libboost-program-options-dev libboost-program-options1.34.1 libboost-python-dev libboost-python1.34.1 libboost-regex-dev libboost-regex1.34.1 libboost-signals-dev libboost-signals1.34.1 libboost-test-dev libboost-test1.34.1 libboost-thread-dev libboost-thread1.34.1

``` [B]
scons:[/B]
```

sudo apt-get install scons

``` [B]
OR FOR YOU IMPATIENT :(:[/B]
```

sudo apt-get install libusb-dev libboost-date-time-dev libboost-date-time1.34.1 libboost-dev libboost-doc libboost-filesystem-dev libboost-filesystem1.34.1 libboost-graph-dev libboost-graph1.34.1 libboost-iostreams-dev libboost-iostreams1.34.1 libboost-program-options-dev libboost-program-options1.34.1 libboost-python-dev libboost-python1.34.1 libboost-regex-dev libboost-regex1.34.1 libboost-signals-dev libboost-signals1.34.1 libboost-test-dev libboost-test1.34.1 libboost-thread-dev libboost-thread1.34.1 scons

```[SIZE=4]
Compiling! (Step Four)[/SIZE]
 The best part! We can now grab the driver from the author's website. As of this writing, version** 0.2rc1** is available here: *removed*.[]("http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2") [COLOR=Red]**(****EDIT: This link is old. Please go directly to the website for the latest version: [http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2"))**[/COLOR]. The best way to do this for now, would be to create a temp. directory in your home directory, download the driver there and extract its contents. At the terminal:
```

cd ~
mkdir tmp
cd tmp
wget http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2
tar -xvvf xboxdrv-linux-0.2.tar.bz2  

```Now we can move into that directory and start compiling! At the terminal:
```

 cd xboxdrv-linux-0.2 
 scons

```If everything goes alright, the driver should compile successfully and you should now have a beautiful program sitting there begging for you to use it:
```

tripp@eclipse-desktop:~/tmp/xboxdrv-linux-0.2$ ls -lsa xboxdrv 
1272 -rwxr-xr-x 1 tripp tripp 1297401 2008-06-10 18:47 **xboxdrv**

```[SIZE=5]Driver Usage[/SIZE] 

So if you have made it this far with no problems, that either means I did  my job right, or your system is unique/different :P. From this point, we can now plug in the wireless receiver or the xbox controller. If you issue a lsusb, you should see your device listed somewhere in the list.

[SIZE=4]Impatient People and Insta-Test[/SIZE]
 Let's test the driver right away.

 For this example, I will be using the Xbox 360 Wireless Receiver USB Adapter and an Xbox 360 Wireless Controller. I plugged in the wireless adapter, issued the following command, turned on my controller and finally sync'd the two together.

 Issuing the following command at the terminal in the installation directory gives me these reults (which I will explain in depth later on):
```

 tripp@eclipse-desktop:~/tmp/xboxdrv-linux-0.2$ sudo ./xboxdrv --wid 0 
 USB Device:        003:007 
 Controller:        "Microsoft Xbox 360 Wireless Controller (PC)" (idVendor: 0x045e, idProduct: 0x0719) 
 Wireless Port:     0 
 Controller Type:   Xbox360 (wireless) 
 Deadzone:          0 
 Rumble Debug:      off 
 Rumble Speed:      left: 0 right: 0 
 LED Status:        auto 
 ButtonMap:         none 
 AxisMap:           none 
 Starting with uinput 
  
 Your Xbox/Xbox360 controller should now be available as: 
   /dev/input/js0 
   /dev/input/event6 
  
 Press Ctrl-c to quit 
  
 Connection status: nothing 
 Connection status: nothing 
 Connection status: nothing 
 Connection status: controller connected 
 Serial:  d:f6:10:d2:26:4d: 0 
 Battery Status: 161 
 Unknown: len: 29 data: 0x00 0x00 0x00 0x20 0x1d 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00  
 Unknown: len: 29 data: 0x00 0x00 0x00 0x00 0x05 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00  
 Unknown: len: 29 data: 0x00 0x00 0x00 0x40 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00  
 Unknown: len: 29 data: 0x00 0xf8 0x02 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00  
 Unknown: len: 29 data: 0x00 0xf8 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00  
 Unknown: len: 29 data: 0x00 0xf8 0x02 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00  
 Unknown: len: 29 data: 0x00 0xf8 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00  
 Unknown: len: 29 data: 0x00 0xf8 0x02 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

``` From here, if we do anything on the controller, it will show up. This is how we know things are working ok:

```

 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:1 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0 
 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0 
 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:1 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0 
 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0 
 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:1 Y:0  LB:0 RB:0  LT:  0 RT:  0 
 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0 
 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:1  LB:0 RB:0  LT:  0 RT:  0 
 S1:( -2106,   4124)  S2:(  -319,   1673) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0 

``` From here we can see that I pressed and released A, B, X and Y. Awesome. Stuff works!
 **To stop, we issue CTRL-C twice**.

[SIZE=4]Patient People and More Details[/SIZE]

 When I read these tutorials I like to know my that stuff is working alright which is why I included the impatient part. Anyways, here are some of the features of the driver:
```

 ./xboxdrv --help
 Usage: ./xboxdrv (OPTION)... 
 Xbox360 USB Gamepad Userspace Driver 
  
 General Options:  
   -h, --help               display this help and exit 
   --help-led               list possible values for the led 
   --help-devices           list supported devices 
   -s, --silent             do not display events on console 
   -i, --id N               use controller with id N (default: 0) 
   -w, --wid N              use wireless controller with wid N (default: 0) 
   -L, --list-controller    list available controllers 
   -R, --test-rumble        map rumbling to LT and RT (for testing only) 
   --no-uinput              do not try to start uinput event dispatching 
  
 Device Options:  
   -d, --device BUS:DEV     Use device BUS:DEV, do not do any scanning 
  
 Status Options:  
   -l, --led NUM            set LED status, see --list-led-values (default: 0) 
   -r, --rumble L,R         set the speed for both rumble motors [0-255] (default: 0,0) 
   -q, --quit               only set led and rumble status then quit 
  
 Configuration Options:  
   --deadzone INT           Threshold under which axis events are ignored (default: 0) 
   --trigger-as-button      LT and RT send button instead of axis events 
   --trigger-as-zaxis       Combine LT and RT to form a zaxis instead 
   --dpad-as-button         DPad sends button instead of axis events 
   --dpad-only              Both sticks are ignored, only DPad sends out axis events 
   --type TYPE              Ignore autodetection and enforce controller type 
                            (xbox, xbox-mat, xbox360, xbox360-wireless, xbox360-guitar) 
   -b, --buttonmap MAP      Remap the buttons as specified by MAP 
   -a, --axismap MAP        Remap the axis as specified by MAP 
  
 Report bugs to Ingo Ruhnke <snipped to help avoid spam!> 

``` I believe most of the options are very straight forward, but there is one part that needs a little bit of attention, **--id** and --**wid**.

 If you are using a wired controller, use the --id option; for a wireless controller, use the --wid. In the impatient example, I used --wid because I was using a wireless controller which happened to be the only controller I wanted connected. You can connect additional controllers, but you must run the command for each controller. For example, if you had two wireless controllers:
```

 ./xboxdrv --wid 0
 ./xboxdrv --wid 1

``` Two wired controllers?
```

 ./xboxdrv --id 0
 ./xboxdrv --id 1

``` Nice and clear? Great! But what if you don't know what the ID or the WID is?
```

 tripp@eclipse-desktop:~/tmp/xboxdrv-linux-0.2$ ./xboxdrv -L 
  id | wid | idVendor | idProduct | Name 
 ----+-----+----------+-----------+-------------------------------------- 
   0 |   0 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 0) 
   0 |   1 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 1) 
   0 |   2 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 2) 
   0 |   3 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 3) 

``` This example shows my wireless receiver and the four ports it provides for xbox controllers. Now unfortunately I don't have any wired controllers to test, but I imagine it is very similar.

[SIZE=5]Test with a Game[/SIZE]  

If you can see that everything is working ok, we can now test with a game. I have tried TuxKart and Neverball so far and they seem to work as expected. Load up the driver with the appropriate options and leave it running in the terminal then try it with the two games I mentioned as I know these work.

 Leave some messages with other games that you know work. Pretty much any game that will let you use a joystick should work.

[SIZE=5]Post Game Test[/SIZE]

Once you know things work properly with games, you can append the --silent option to suppress the reporting of the driver for better performance.

[SIZE=5]The End Part[/SIZE]

Hopefully everything works out ok and the driver functions as expected. Please remember, this driver is only version 0.2 and is considered as the first release candidate. There is a README file with additional information in the installation directory that may answer any other problems that you encounter—try taking a look there before posting a question.

 If you have any major problems or would like to contribute to the driver effort, please visit the author's web page at: [http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")

 **I would also like to thank grumbel for releasing this great driver along with its code, as it works wonderfully for my system! Also, most of this information comes from him anyways.**

 *Please* seriously consider helping out the author in any way possible folks (documentation, coding, providing information for the chatpad/headset, donations [I'm saying that purely out of my own accord—grumbel didn't put me at gunpoint or offer me incentives] or any other skills that this community can provide).

 If anyone can provide corrections or suggestions, please let me know by a PM and I will update this howto and mention your name.

 I would love to be able to use all the features of the controller with Linux and I'm sure in the future it will work better than the Windows equivalent!

[SIZE=5]Common Driver Executions[/SIZE] 
[LIST]
[*]One Wired Controller: ```
sudo ./xboxdrv --id 0
```
[*]One Wireless Controller: ```
sudo ./xboxdrv --wid 0
```
[*]Suppress console logging on a wireless controller: ```
sudo ./xboxdrv --wid 0 --silent
```
[*]List connected controllers: ```
./xboxdrv --list-controller
```
[/LIST]

[SIZE=5]Links[/SIZE]
[LIST]
[*]grumbel's website - [http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")
[*][COLOR=Red]Downloads (PPA, git, source, scroll down a bit) -[/COLOR] [http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")
[*]Another thread that might be useful (mentions xpad driver just in case this how-to doesn't work) - [http://ubuntuforums.org/showthread.php?t=404577](http://ubuntuforums.org/showthread.php?t=404577)
[/LIST]

[SIZE=5]Additional Thoughts/Problems[/SIZE]
[LIST]
[*]For whatever reason, I had to run the driver using sudo. I probably goofed somewhere, but things seem to be ok
[*]Check permissions on /etc/input/uinput. Somewhere they suggested changing the permissions to 664. This might help someone?
[/LIST]

---

### Post by Garudi on 2008-06-11
Awesome guide :) works great with my wireless 360 controller. I've been looking for something like this for a while now. /off to test with some emulators :)

---

### Post by wootah on 2008-06-11
> **Garudi said:**
> Awesome guide :) works great with my wireless 360 controller. I've been looking for something like this for a while now. /off to test with some emulators :)
Hey, let us know how the emulators work :)

---

### Post by Boktai1000 on 2008-06-12
Im thinking about trying this, do you have to execute that command every time you want to use your controller? Also im using Xpad right now and when I boot i cant have my guitar and my controller both plugged in, do you know if this will let me? (Guitar Hero X-Plorer + Microsoft Xbox Wireless Receiver [Wireless 360 Controller])

---

### Post by wootah on 2008-06-12
> **Boktai1000 said:**
> Im thinking about trying this, do you have to execute that command every time you want to use your controller? Also im using Xpad right now and when I boot i cant have my guitar and my controller both plugged in, do you know if this will let me? (Guitar Hero X-Plorer + Microsoft Xbox Wireless Receiver [Wireless 360 Controller])

For now, yes, since it runs in userspace and it is not a kernel module. This driver will let you use both, but you will have to run two instances of it. Luckily, they can run as silent in the background :)

---

### Post by wootabix on 2008-06-13
I just tried this with a wired controller but it doesn't seem to work. 

xboxdrv hangs at the following: 


USB Device:        001:009
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none


There are no /dev/input/jsX devices created. I added some logging to the code and it seems it is hanging trying to find the /dev/input/jsX devices at this line in find_jsdev_number in xboxdrv.cpp: 

      if (access(filename1, F_OK) != 0 && access(filename2, F_OK) != 0)
 
Note: to get this far I have to start xboxdrv as root. If I don't, it bombs out after the AxisMap: none message with "Exception: Error couldn't claim the USB interface"

I'm running ubuntu-8.04 desktop (64bit)

Any suggestions?

---

### Post by wootah on 2008-06-13
Are the kernel modules *uinput *and *joydev* still are listed in lsmod? It sounds like the joystick device is not being created.

---

### Post by wootabix on 2008-06-14
Actually, it gets further than I said, but still hangs. joydev and uinput are there. It can't open the usb device for some reason. An strace shows:

ioctl(3, USBDEVFS_REAPURBNDELAY, 0x7fffaca55098) = -1 EAGAIN (Resource temporarily unavailable)
select(4, NULL, [3], NULL, {0, 1000})   = 0 (Timeout)

I wonder if it is 64bit issue ? (I am running 64bit Ubuntu 8.04)

---

### Post by wootah on 2008-06-15
> **wootabix said:**
> Actually, it gets further than I said, but still hangs. joydev and uinput are there. It can't open the usb device for some reason. An strace shows:

ioctl(3, USBDEVFS_REAPURBNDELAY, 0x7fffaca55098) = -1 EAGAIN (Resource temporarily unavailable)
select(4, NULL, [3], NULL, {0, 1000})   = 0 (Timeout)

I wonder if it is 64bit issue ? (I am running 64bit Ubuntu 8.04)

You could very well be correct. I have no experience in a 64bit environment, so I have no idea what kind of problems might occur.

Did you try running the xboxdrv with sudo ?

EDIT: Where is the uinput and joydev devices located on your system ? */dev/input/uinput *?

---

### Post by dudude on 2008-06-19
I am also running Hardy 64 bit and when I this is what I get when I run xboxdrv

```
robert@robert-desktop:~/Desktop/Icons/xboxdrv-linux-0.2$ sudo ./xboxdrv 
USB Device:        003:007
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface
```

I double checked to make sure that xpad was not loaded, joydev and uinput were, and that the controller was showing up at /dev/input/js0.

I got the program to start, but then it ran into an error.

```
ioctl(3, USBDEVFS_SUBMITURB, 0x7fffedef1250) = -1 ENOENT (No such file or directory)
write(1, "Exception: USBError: -2\n", 24Exception: USBError: -2
) = 24
write(1, "error submitting URB: No such fi"..., 48error submitting URB: No such file or directory
) = 48
exit_group(0)                           = ?
Process 26941 detached
```

---

### Post by wootah on 2008-06-19
> **dudude said:**
> I am also running Hardy 64 bit and when I this is what I get when I run xboxdrv

```
robert@robert-desktop:~/Desktop/Icons/xboxdrv-linux-0.2$ sudo ./xboxdrv 
USB Device:        003:007
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface
```I double checked to make sure that xpad was not loaded, joydev and uinput were, and that the controller was showing up at /dev/input/js0.

I got the program to start, but then it ran into an error.

```
ioctl(3, USBDEVFS_SUBMITURB, 0x7fffedef1250) = -1 ENOENT (No such file or directory)
write(1, "Exception: USBError: -2\n", 24Exception: USBError: -2
) = 24
write(1, "error submitting URB: No such fi"..., 48error submitting URB: No such file or directory
) = 48
exit_group(0)                           = ?
Process 26941 detached
```

Very interesting! Did you try: ```
sudo ./xboxdrv --id 1 (or --id 0)
``` I'm working with the dev. right now, so I'll ask him and see what he says :)

---

### Post by dudude on 2008-06-19
Here is my output of that command.

```
robert@robert-desktop:~/Desktop/Icons/xboxdrv-linux-0.2$ sudo ./xboxdrv --id 0
USB Device:        003:007
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Starting with uinput

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event4

Press Ctrl-c to quit

Exception: USBError: -2
error submitting URB: No such file or directory

```

---

### Post by BigSilly on 2008-06-20
Can anyone help me with this? I've obviously gotten so far, because I'm getting this -

```
No Xbox or Xbox360 controller found
```

What have I done wrong? It's a Speed-Link (Chinese made probably) Xbox 360 style pad. Cheers.

---

### Post by wootah on 2008-06-20
> **BigSilly said:**
> Can anyone help me with this? I've obviously gotten so far, because I'm getting this -

```
No Xbox or Xbox360 controller found
```What have I done wrong? It's a Speed-Link (Chinese made probably) Xbox 360 style pad. Cheers.

This is great! We can add another one to the list. Is this wireless, or wired? We basically just need the ids so we can add it into xboxdrv.cpp.

Is this controller wired or wireless? 

Plug the controller in and do a lsusb. Find the line that has your xbox controller on it and you want the id (ex: Bus 003 Device 002: ID **04a9:10a2** Canon, Inc.) If you want to use it right away, you'll have to add it into the xboxdrv.cpp as follows (starting on line 39):

  { GAMEPAD_XBOX360,          0x0738, 0x4716, "Mad Catz Xbox 360 Controller" },
  { GAMEPAD_XBOX360,          0x162e, 0xbeef, "Joytech Neo-Se Take2" },
  **{ GAMEPAD_XBOX360,       0x04a9,0x10a2**,** "Speed-Link Xbox 360 Controller"},**

Something along those lines. Basically, you are just adding on to the list. After you done, save it and recompile at the command line with **scons**. Now try running the program again with sudo ./xboxdrv. See if that works.

---

### Post by BigSilly on 2008-06-20
Hi there. Thanks for your response. I'll certainly hold on to it if you think you can get it working! For the record, [it's this one.]("http://www.play.com/PC/PCs/-/673/880/-/3507653/Speed-Link-XBOX-360-Style-USB-Gamepad-For-Windows-With-Force-Vibration-Black/Product.html?searchtype=genre") It's a wired USB pad. I've bought pads from Speed-Link before, and they've all worked perectly in Linux, which is why I went for this one. But as the other I have is made by Greenasia, this one's made by Acrux. Those are the device names I see in my emulators.

Gah. I don't know what I'm doing wrong here, but when I type lsusb into a terminal, I only get this -

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1a34:0802  
Bus 001 Device 001: ID 0000:0000 
```

I'm not altogether clear on what to do, but I think I managed to follow your original instructions OK. Let me know if there's something I did wrong.

---

### Post by wootah on 2008-06-20
> **BigSilly said:**
> Hi there. Thanks for your response. I'll certainly hold on to it if you think you can get it working! For the record, [it's this one.]("http://www.play.com/PC/PCs/-/673/880/-/3507653/Speed-Link-XBOX-360-Style-USB-Gamepad-For-Windows-With-Force-Vibration-Black/Product.html?searchtype=genre") It's a wired USB pad. I've bought pads from Speed-Link before, and they've all worked perectly in Linux, which is why I went for this one. But as the other I have is made by Greenasia, this one's made by Acrux. Those are the device names I see in my emulators.

Gah. I don't know what I'm doing wrong here, but when I type lsusb into a terminal, I only get this -

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1a34:0802  
Bus 001 Device 001: ID 0000:0000 
```I'm not altogether clear on what to do, but I think I managed to follow your original instructions OK. Let me know if there's something I did wrong.

So you are looking to add: **1a34:0802** into the xboxdrv.cpp. Add this line in at around line 76 of xboxdrv.cpp:
```

{ GAMEPAD_XBOX360,          0x1a34, 0x0802, "Speed-Link Xbox 360 USB Controller" },

```
You can use nano if you wish (nano xboxdrv.cpp). After saving these changes, compile everything by usings *scons*. After that, try running the xboxdrv again.

It looks like everything you have done is right, just this controller isn't listed as being a valid controller--yet. That is what we are doing here, just adding to the list :)

Let me know if you need further help, or if this works :D

---

### Post by BigSilly on 2008-06-20
Thanks very much for your replies. 

Are you saying I need to add this line manually to the file you suggest, and then re-compile the program? Do I need to remove the original driver program I've compiled and start again from scratch, yeah?

Sorry. I'm trying to keep up...:D

---

### Post by BigSilly on 2008-06-20
OK. I think I did what you said, but now I'm getting this. I added the line as you said, but it doesn't seem to want to play. This is the full readout, so you can see what I've done -
```

bigsilly@bigsilly-desktop:~$ cd '/home/bigsilly/Desktop/My Downloads/xboxdrv-linux-0.2' 
bigsilly@bigsilly-desktop:~/Desktop/My Downloads/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o xboxdrv.o -c -g -O0 -Wall xboxdrv.cpp
g++ -o xboxdrv xboxdrv.o xboxmsg.o uinput.o helper.o xbox_controller.o xbox360_controller.o xbox360_wireless_controller.o -lusb
scons: done building targets.
bigsilly@bigsilly-desktop:~/Desktop/My Downloads/xboxdrv-linux-0.2$ sudo ./xboxdrv
[sudo] password for bigsilly: 
USB Device:        001:003
Controller:        "Speed-Link Xbox 360 USB Controller" (idVendor: 0x1a34, idProduct: 0x0802)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface
```

What do you think? Thanks in advance.

---

### Post by wootah on 2008-06-20
> **BigSilly said:**
> OK. I think I did what you said, but now I'm getting this. I added the line as you said, but it doesn't seem to want to play. This is the full readout, so you can see what I've done -
```

bigsilly@bigsilly-desktop:~$ cd '/home/bigsilly/Desktop/My Downloads/xboxdrv-linux-0.2' 
bigsilly@bigsilly-desktop:~/Desktop/My Downloads/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o xboxdrv.o -c -g -O0 -Wall xboxdrv.cpp
g++ -o xboxdrv xboxdrv.o xboxmsg.o uinput.o helper.o xbox_controller.o xbox360_controller.o xbox360_wireless_controller.o -lusb
scons: done building targets.
bigsilly@bigsilly-desktop:~/Desktop/My Downloads/xboxdrv-linux-0.2$ sudo ./xboxdrv
[sudo] password for bigsilly: 
USB Device:        001:003
Controller:        "Speed-Link Xbox 360 USB Controller" (idVendor: 0x1a34, idProduct: 0x0802)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface
```What do you think? Thanks in advance.

Alright, it recognized your controller, let's try the following:
```
sudo ./xboxdrv --id 0
```
if that doesn't work:
```
sudo ./xboxdrv --id 1
```

---

### Post by BigSilly on 2008-06-21
> **wootah said:**
> Alright, it recognized your controller, let's try the following:
```
sudo ./xboxdrv --id 0
```
if that doesn't work:
```
sudo ./xboxdrv --id 1
```

I get -

```
bigsilly@bigsilly-desktop:~/Desktop/My Downloads/xboxdrv-linux-0.2$ sudo ./xboxdrv --id 0
[sudo] password for bigsilly: 
USB Device:        001:003
Controller:        "Speed-Link Xbox 360 USB Controller" (idVendor: 0x1a34, idProduct: 0x0802)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface
```

for the first command, and this -

```
bigsilly@bigsilly-desktop:~/Desktop/My Downloads/xboxdrv-linux-0.2$ sudo ./xboxdrv --id 1
No Xbox or Xbox360 controller found
```

for the second one. Let me know what you think. Thanks.

---

### Post by BigSilly on 2008-06-21
...Are you still there?

:)

---

### Post by jarvis13 on 2008-06-21
also had to add my controller to the .cpp file. it was 045e:028f, so you can add it to future additions

I get these errors:

```
joshua@joshua-linuxlaptop:~/tmp/xboxdrv-linux-0.2$ sudo ./xboxdrv --wid 1
USB Device:        001:009
Controller:        "Microsoft Xbox 360 Wireless Controller (PC)" (idVendor: 0x045e, idProduct: 0x028f)
Wireless Port:     1
Controller Type:   Xbox360 (wireless)
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Xbox360WirelessController: Error couldn't claim the USB interface 2

```

---

### Post by BigSilly on 2008-06-22
> **jarvis13 said:**
> also had to add my controller to the .cpp file. it was 045e:028f, so you can add it to future additions

I get these errors:

```
joshua@joshua-linuxlaptop:~/tmp/xboxdrv-linux-0.2$ sudo ./xboxdrv --wid 1
USB Device:        001:009
Controller:        "Microsoft Xbox 360 Wireless Controller (PC)" (idVendor: 0x045e, idProduct: 0x028f)
Wireless Port:     1
Controller Type:   Xbox360 (wireless)
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Xbox360WirelessController: Error couldn't claim the USB interface 2

```

Yeah, that's a similar error to mine. On the bottom of the last page here.

---

### Post by jarvis13 on 2008-06-22
Yeah, I saw that. I'm also using Hardy and with a wireless remote. I wonder if that's what the problem could be. Hmm. I'd really like to get this working, as it would make playing MAME so much more enjoyable!

I've played around with it a bit more, but no such luck yet.

---

### Post by BigSilly on 2008-06-22
Well mine's a wired pad, but it still won't work. For what it's worth (probably nothing), I mentioned it in the Ubuntu Ideas Pool in the Development forum. Maybe a dev will think it's a good idea and implement it? Who knows.

---

### Post by dudude on 2008-06-22
I don't know anything about it, but I was getting errors that said 
```
ioctl(3, USBDEVFS_SUBMITURB, 0x7fffedef1250) = -1 ENOENT (No such file or directory)
```
and
```
write(1, "error submitting URB: No such fi"..., 48error submitting URB: No such file or directory
) = 48
```
Which leads me to believe that the problem is with URB messages that the program is trying to send.
Like I said, I don't know anything about this, but this seems to be part of the problem with the program trying to claim the USB interface. 

It seems that the program is so close to working and it would be so much nicer to use this than have to use the somewhat lacking xpad driver.

---

### Post by wootah on 2008-06-23
> **dudude said:**
> I don't know anything about it, but I was getting errors that said 
```
ioctl(3, USBDEVFS_SUBMITURB, 0x7fffedef1250) = -1 ENOENT (No such file or directory)
```and
```
write(1, "error submitting URB: No such fi"..., 48error submitting URB: No such file or directory
) = 48
```Which leads me to believe that the problem is with URB messages that the program is trying to send.
Like I said, I don't know anything about this, but this seems to be part of the problem with the program trying to claim the USB interface. 

It seems that the program is so close to working and it would be so much nicer to use this than have to use the somewhat lacking xpad driver.

Well this is good news! The dev works on this very actively and I can compile a list of issue of problems for him to work through. It's really too bad it didn't work out of the box for the above people :(

Luckily we can fix these problems quickly and get stuff working :-D I'll let the dev know and re-submit.

For dudude, you have the joydev and uinput working, correct? Did you try chmoding /dev/input/uinput to 664 ?

PS: Sorry about the delay, I went on a trip this weekend :)

---

### Post by BigSilly on 2008-06-23
Anything you could recommend for me Wootah? :D I replied to your earlier question at the bottom of the last page.

I sent an email to the makers of this pad, apparently a German company, requesting Linux drivers. I didn't know if it would be useful or not, but I got an email back saying that they are unable to produce drivers themselves as it would prove too costly for them to support so many distros. However, the email did say -

> Under Windows this Gamepad use the Windows own HID Driver, with this you can write your own Driver for Linux.


...I believe they used Babelfish to translate from German to English for me! 

I don't know how useful that is (or even what a HID driver is), but, well, there it is.

---

### Post by wootah on 2008-06-23
> **BigSilly said:**
> Anything you could recommend for me Wootah? :D I replied to your earlier question at the bottom of the last page.

I sent an email to the makers of this pad, apparently a German company, requesting Linux drivers. I didn't know if it would be useful or not, but I got an email back saying that they are unable to produce drivers themselves as it would prove too costly for them to support so many distros. However, the email did say -



...I believe they used Babelfish to translate from German to English for me! 

I don't know how useful that is (or even what a HID driver is), but, well, there it is.

HID = human interface device. This should basically mean that everything we did should work :(

Is there any other information you can post? You are using 32bit Hardy correct? Followed all the steps in the tutorial (just in case :)) ?

We could always try the last version from git ? Let me know what you think :)

---

### Post by BigSilly on 2008-06-23
Yes, I'm running 32bit Hardy, and I followed your instructions right down and double checked as I went. I'm a bit noobish when it comes to compiling, but your instructions were very clear and easy to follow.

I dunno. I think I'm screwed! I can't imagine what I need to do, but I've just tried again to get it going, and I'm still getting the "couldn't claim the USB device" error. 

Looks like if I want any new pad fun, I'm going to have to stick on XP. :(

...bugger.

---

### Post by wootah on 2008-06-23
> **BigSilly said:**
> Yes, I'm running 32bit Hardy, and I followed your instructions right down and double checked as I went. I'm a bit noobish when it comes to compiling, but your instructions were very clear and easy to follow.

I dunno. I think I'm screwed! I can't imagine what I need to do, but I've just tried again to get it going, and I'm still getting the "couldn't claim the USB device" error. 

Looks like if I want any new pad fun, I'm going to have to stick on XP. :(

...bugger.

This really sux since it worked very nicely for me. Luckily we should be able to get this fixed quickly. I can't think of anything to help right now at this very moment (I'm not at my desktop computer so I can't really try anything). If I have time later on today, I'll try some stuff out and see what happens.

Don't give up yet :)

---

### Post by BigSilly on 2008-06-23
> **wootah said:**
> This really sux since it worked very nicely for me. Luckily we should be able to get this fixed quickly. I can't think of anything to help right now at this very moment (I'm not at my desktop computer so I can't really try anything). If I have time later on today, I'll try some stuff out and see what happens.

Don't give up yet :)

Hey, don't sweat it. I appreciate your advice and assistance. I'll keep an eye on this thread and the games one in case you crack it, but not to worry. I haven't installed XP anyway. I've been threatening the missus' that I'm going to do it for a while now, but haven't. I don't reckon I will either truthfully. I like my Linux too much to remove it for a simple games pad! :)

Thanks for all your time anyway. Take care, and see you around the forums.

---

### Post by jarvis13 on 2008-06-23
The upside is that the more problems we can fix now, maybe it will be stable enough to work out of box and be included in a future release.

---

### Post by dudude on 2008-06-24
I don't know when I tried it, but I think I did try chmoding the /dev/input/uinput/js0 to 775 or something along those lines. It could have been at a different time than when I did the strace though, but I won't be able to confirm it for a while since I won't have my 360 controller for a couple of weeks.

But I too think it would be great if this driver could be up and running for everyone so that it could hopefully be included in Intrepid.

---

### Post by Xyvir on 2008-06-25
Thank you for bringing my attention to this program! I was trying to use the xpad module with my wired xbox 360 controller and it was giving me headaches, mostly because I wanted to change the triggers to buttons and set a dead zone. Anyway I was going to ask... I'm kind of new to Linux, but unless I'm mistaken it seems you could mess with the udev rules to run this program automatically whenever a compatable device is plugged in, and then kill the process when you unplug, so you wouldn't have to manually run it every time you want to use your joypad. There is a howto here: [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html") I would attempt it, but I'm fearful of breaking something, and I don't know that it would even work.

Plus, when you say rmmoding might not remove xpad: I was having some problems with rmmoding xpad. It would either crash the terminal or say it was in use. But you can blacklist the module in /etc/modprobe.d/blacklist by adding a line that says 'blacklist xpad' and restart your computer. That seemed to work for me. 

Anyway, thanks for the link!

---

### Post by wootah on 2008-06-25
> **Xyvir said:**
> Thank you for bringing my attention to this program! I was trying to use the xpad module with my wired xbox 360 controller and it was giving me headaches, mostly because I wanted to change the triggers to buttons and set a dead zone. Anyway I was going to ask... I'm kind of new to Linux, but unless I'm mistaken it seems you could mess with the udev rules to run this program automatically whenever a compatable device is plugged in, and then kill the process when you unplug, so you wouldn't have to manually run it every time you want to use your joypad. There is a howto here: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) I would attempt it, but I'm fearful of breaking something, and I don't know that it would even work.

Plus, when you say rmmoding might not remove xpad: I was having some problems with rmmoding xpad. It would either crash the terminal or say it was in use. But you can blacklist the module in /etc/modprobe.d/blacklist by adding a line that says 'blacklist xpad' and restart your computer. That seemed to work for me. 

Anyway, thanks for the link!

Ahh right, you bring a good point to the table. To the above gentlemen(or ladies?), are you sure that xpad is still removed?

---

### Post by cespinal on 2008-06-25
this look way too complicate to my noobish experience with ubuntu... I'll give a try once it gets simpler :P

---

### Post by wootah on 2008-06-25
> **cespinal said:**
> this look way too complicate to my noobish experience with ubuntu... I'll give a try once it gets simpler :P
Nah, it's pretty straight forward, it's just that it is still somewhat beta :(

---

### Post by dudude on 2008-06-25
For me, just to make sure that xpad would never load I would enter
```
updatedb
locate xpad
```
then remove any occurances of xpad from the system one directory at a time.

I'm sure that there is a command to remove xpad permanently, but I did not feel like learning the difference between rmmod and modprobe -r or whatever other commands there are for kernel modules.

---

### Post by bumbleskull on 2008-06-30
Anyone got any ideas. I am getting these errors, whenever I try to compile

```

scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.



```

---

### Post by wootah on 2008-07-02
bumbleskull: Do you have build-essential installed?

---

### Post by Mad_Gouki on 2008-07-10
I just grabbed a used rockband guitar from GameStop(they had a ton apparently) and I'm working on installing this driver for it now.  The line to add in the xboxdrv.cpp file for it is
  { GAMEPAD_XBOX360_GUITAR,   0x1bad, 0x0002, "Rockband Stratocaster"  },
I'll let you know how the build goes :D

EDIT: Woot! Works great with frets on fire(except I suck at it) :D  Still gotta look into making the tap buttons autostrum when hit.
I'm guessing to get the tap buttons working like tap buttons, it will require some snooping on the signals sent over the usb?  How hard would it be for me to run some app(like the usb debugging app that came with the driver) and then send your friend the output of each button press in that and have it coded into the program?

---

### Post by bigplrbear on 2008-07-15
When I run the program in the terminal, I get this-
```

S1:(   726,    145)  S2:(  -725,   -727) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
S1:(   726,    145)  S2:(  -725,   -654) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
S1:(   799,    145)  S2:(  -653,   -727) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
S1:(   726,    145)  S2:(  -725,   -654) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0

```
FOREVER. It appears that the problem is with my axises being really loose (as in, I dropped my controller one day, broke the thing and now I need to buy a new one :P)
But, I don't have this problem when I run it in Windows or on an Xbox 360 (the characters don't move to the right/left by themselves), so I know it's not the controller. Any quick fixes for one of the impatient ones?

---

### Post by Dyer on 2008-07-16
Try ```
./xboxdrv --deadzone 1000
``` This will create a deadzone where coordinates under the value of 1000 (as your unwanted values are) will be ignored.

---

### Post by rumplefreakinstiltskin on 2008-07-19
Hi,

Noticed in my google searchign that you guys were talking about xbox controllers.  It just so happens that I've recently added support for the xbox 360 controller to a little game I've been working on, and using the xpad driver that's in the linux kernel 2.6.26 from kernel.org...and guess what?

RUMBLE WORKS!

So I added support for rumble to my game.

It's here: [http://wordwarvi.sourceforge.net](http://wordwarvi.sourceforge.net)

Enjoy.

-- steve

---

### Post by asmugone on 2008-07-22
Hey gang, first off this needs to be edited to the front of the post, in order to stop xpad from loading edit /etc/modprobe.d/blacklist and add xpad to the bottom, DONE.

Second: the fix the cannot claim usb problem, simply run the program as root. examp: sudo ./xboxdrv

works like a charm! =)

Now heres my problem, im trying to play gta vice city using the controller and I did the command to make the triggers buttons and that worked beautifully but I cannot get my right analog stick to register as anything ingame. IS there a file or something so that I can make the driver do default binding like it does with the left analog stick or perhaps make it register the right stick as buttons instead of axis???
if there was just a way to switch the bindings from the mouse to the right analog stick I would be in HEAVEN!

---

### Post by dudude on 2008-07-23
I don't know if this would help any, but I used a program called qjoypad to get the input working the way I wanted it to in some programs. 
If the stick doesn't work at all in or out of wine, then I really don't know what to do.

---

### Post by reidms on 2008-08-14
> **dudude said:**
> I am also running Hardy 64 bit and when I this is what I get when I run xboxdrv

```
robert@robert-desktop:~/Desktop/Icons/xboxdrv-linux-0.2$ sudo ./xboxdrv 
USB Device:        003:007
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface
```


Same exact error for me.  I am running Hard 64bit as well

---

### Post by xen-uno on 2008-08-14
You can't stop xpad with the commands in Wootah's first post ... at least I couldn't. You must blacklist xpad then reboot. Doing so corrected the "claim" error on x64 Hardy here. So I've gotten past that ... uinput and joydev are loaded (uinput manually since it was not autoloading). The driver loads now with no error but seems to hang after the "Axis Map" with a flashing cursor ...

```
jan@ubuntu:~/tmp/xboxdrv-linux-0.2$ sudo ./xboxdrv --id 0
USB Device:        004:002
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
<flashing cursor here>    

```

The wired controller quadrants flash but the controller is not working (no test dialog results like Woot's or action in SuperTuxKart). It's not locked up as I can Ctrl-C and unplug the controller to terminate driver.

---

### Post by shiver on 2008-08-15
Does this driver support the wireless 360 guitar controller, too? Is it correct that you also need the MS wireless gaming adapter?

---

### Post by Silver Streak on 2008-08-24
> **xen-uno said:**
> ... The driver loads now with no error but seems to hang after the "Axis Map" with a flashing cursor ...

I saw this thread after searching for solutions to xpad's hotplug bug... I went ahead and compiled the drivers, and now I'm experiencing this exact problem. I also cannot pass the -v (verbose) option for debugging, as it says in the readme to do. Can anyone help with either of these two issues?

---

### Post by shmup on 2008-08-28
::EDIT:: answered my own question.

---

### Post by ntessore on 2008-08-29
The problem is the hardcoded interface number, in my syslog, it complains about using interface 1 and not claiming it.

Edit: After setting all interface numbers to 1, it worked.

Edit2: Now, it no longer works!

---

### Post by ntessore on 2008-08-29
Found the error: When using usb_interrupt_write, you have to use endpoint 1. :)

Reading a bit, the interface = 1 stuff was rubbish. I don't think hard-coding would be a problem either.

---

### Post by xen-uno on 2008-08-30
What file did you edit? Where is it?

---

### Post by ntessore on 2008-08-30
For the wired 360 controller, you'd edit xbox360_controller.cpp. There should be three occurences of usb_interrupt_write.

For the wireless controller, I just have one and hardcoded endpoint to 1 in the upper part of xbox360_wireless_controller.cpp. No idea how that behaves with multiple wireless controllers.

---

### Post by truffsekka on 2008-09-04
> **ntessore said:**
> Found the error: When using usb_interrupt_write, you have to use endpoint 1. :)

Reading a bit, the interface = 1 stuff was rubbish. I don't think hard-coding would be a problem either.

> **ntessore said:**
> 
For the wired 360 controller, you'd edit xbox360_controller.cpp. There should be three occurences of usb_interrupt_write.

For the wireless controller, I just have one and hardcoded endpoint to 1 in the upper part of xbox360_wireless_controller.cpp. No idea how that behaves with multiple wireless controllers.

I was getting the "Error couldn't claim the USB interface" error and this fixed it for ubuntu 8.04 64 bit.

---

### Post by gexla on 2008-09-12
Ok, how about the headset?  :lolflag:

---

### Post by dudude on 2008-09-12
So what changes need to be made exactly to the xbox360_controller.cpp file in order for the USB 360 controller to work properly?

---

### Post by JonnyTheDreamer on 2008-09-16
I fix it to it:
usb_interrupt_write(handle, 1, buffer, len, 0);
usb_interrupt_write(handle, 1, rumblecmd, sizeof(rumblecmd), 0);
usb_interrupt_write(handle, 1, ledcmd, sizeof(ledcmd), 0);
And it start working!

---

### Post by Nonni on 2008-09-18
> **bumbleskull said:**
> Anyone got any ideas. I am getting these errors, whenever I try to compile

```

scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.



```

I have the same problem. I have build-essential installed. I'm running the intrepid alpha.

---

### Post by domanti on 2008-10-01
Hey. I did this tutorial and seem to have a pretty big problem. (In my opinion atleast). I got all the way to the set where it tells you to plug in the controller and run lsusb to see if the controller it recognized. Well, when I plugged the controller in, the led's were all flashing. I run lsusb, and terminal hangs up, and gives me no feedback on my usb devices. I restart my machine with the controller plugged in, it didn't want to load ubuntu (either that, or taking an extremely long time). But, when the controller isn't plugged in, lsusb still hangs, but my ubuntu still loads.

I figure I've screwed up in compiling the driver, somewhere, but I don't know where and don't know how I would go about fixing it. Still really newbish to Linux!

I'm using Hardy 32b, btw :P forgot to include that in my post.

---

### Post by rocky5051 on 2008-10-04
Hey everyone. I followed the tutorial so I could use my GH III controller, and after doing the change to make the endpoint = 1, it still said it couldn't claim the USB interface. HOWEVER, I went and checked the gamepad manager in System Settings, and it was working and responding there regardless.

I didn't test it without the little change but all I can say is if any more people run into this similar situation, they should test the controller they use regardless of that specific error message in a game or a gamepad config program (I know there is one for KDE, I don't know about Gnome and everything else).

---

### Post by darkpaladin79 on 2008-10-04
Hey everyone, I've been trying to get a pelican xbox controller (has two bumpers for white and black buttons, will work nicely for ps1/2 emulated games) to work under linux with no luck.  Thing is, I don't think the problem is drivers.  When I use lsusb, it doesn't show up as connected.  But, when I use lsusb -vt I get this: (product 0x8801 is the controller, the other is my mouse)

```
ivan@ubuntu:~/Downloads/tmp/xboxdrv-linux-0.2$ lsusb -vt
Bus#  7
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  6
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  5
`-Dev#   1 Vendor 0x0000 Product 0x0000
  `-Dev#   2 Vendor 0x046d Product 0xc041
Bus#  4
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  3
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  2
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  1
`-Dev#   1 Vendor 0x0000 Product 0x0000
ivan@ubuntu:~/Downloads/tmp/xboxdrv-linux-0.2$ lsusb -vt
Bus#  7
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  6
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  5
`-Dev#   1 Vendor 0x0000 Product 0x0000
  `-Dev#   2 Vendor 0x046d Product 0xc041
Bus#  4
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  3
`-Dev#   1 Vendor 0x0000 Product 0x0000
  `-Dev#  97 Vendor 0x0e6f Product 0x8801
Bus#  2
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  1
`-Dev#   1 Vendor 0x0000 Product 0x0000
```

These two commands were sent not more than a second apart.  The cables seem to be connected fine, no shorts.  Here's a dmesg dump from when it gets connected:

```
[ 7903.563786] usb 3-1: new full speed USB device using uhci_hcd and address 98
[ 7904.083227] usb 3-1: device not accepting address 98, error -71
[ 7904.195110] usb 3-1: new full speed USB device using uhci_hcd and address 99
[ 7904.350019] usb 3-1: unable to read config index 0 descriptor/all
[ 7904.350025] usb 3-1: can't read configurations, error -71
[ 7904.462821] usb 3-1: new full speed USB device using uhci_hcd and address 100
[ 7904.870385] usb 3-1: device not accepting address 100, error -71
[ 7904.982266] usb 3-1: new full speed USB device using uhci_hcd and address 101
[ 7905.032327] usb 3-1: string descriptor 0 read error: -71
[ 7905.032426] usb 3-1: configuration #1 chosen from 1 choice
[ 7905.037404] usb 3-1: can't set config #1, error -71
[ 7905.249998] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 7905.250004] usb 3-1: USB disconnect, address 101
[ 7905.361860] usb 3-1: new full speed USB device using uhci_hcd and address 102
[ 7905.531923] usb 3-1: configuration #1 chosen from 1 choice
[ 7905.534847] hub 3-1:1.0: USB hub found
[ 7905.539308] hub 3-1:1.0: config failed, can't read hub descriptor (err -22)
```

The hardware worked on an xbox.  Any ideas?

---

### Post by Modax42 on 2008-10-08
Hi there,

I tried to add the modules to /etc/modules, but it told me I don't have the permissions to do so because I am not the owner

I tried to add the xpad module with sudo rmmod xpad, but I get the message:

> Module xpad does not exist in /proc/modules

Does anyone have the solution for this?

---

### Post by Modax42 on 2008-10-09
Okay, I compiled the driver, but something still isn't right here.

USB Device:        005:002
Controller:        "Microsoft Xbox 360 Wireless Controller (PC)" (idVendor: 0x045e, idProduct: 0x0719)
Wireless Port:     0
Controller Type:   Xbox360 (wireless)
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Xbox360WirelessController: Error couldn't claim the USB interface 0

---

### Post by darkpaladin79 on 2008-10-09
Try running the driver as root, as stated earlier in the thread:
sudo ./xboxdrv

---

### Post by Modax42 on 2008-10-10
I did it again, and it appears to have worked, and Snes9x and Supertux even detect my controller now, but they will not register my button presses.  I had this working perfectly on my old computer on 32 bit 8.04...

> USB Device:        006:002
Controller:        "Microsoft Xbox 360 Wireless Controller (PC)" (idVendor: 0x045e, idProduct: 0x0719)
Wireless Port:     0
Controller Type:   Xbox360 (wireless)
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Starting with uinput

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event11

Press Ctrl-c to quit

Connection status: controller connected
Serial: 3f:10:40:c7:12:21:30
Battery Status: 167
Connection status: nothing

When I push buttons on the controller at this point, nothing happens.

---

### Post by hcaleman on 2008-10-11
I've got some progress but also running into the URB error.  I am using a wireless controller, but have it connected to my computer via the USB charging adapter (could this possibly be an issue?).  lsusb can see the controller and I added the needed line for the program to recognize the controller.  Any ideas to help me resolve this?  

```


shotgun@Zohan:~/Temp/xboxdrv-linux-0.2$ sudo ./xboxdrv -w 0
USB Device:        004:004
Controller:        "Microsoft Xbox 360 Controller Charger" (idVendor: 0x045e, idProduct: 0x028f)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Starting with uinput

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js1
  /dev/input/event6

Press Ctrl-c to quit

Exception: USBError: -2
error submitting URB: No such file or directory

```

---

### Post by darkpaladin79 on 2008-10-11
I get the URB error now also, I don't think anyone has resolved that.

---

### Post by hcaleman on 2008-10-12
What is URB by the way?  I'm newish to linux so bear with me.  If I have a better understanding of what URB is then I can go ahead and look around a bit more on my own.

---

### Post by hcaleman on 2008-10-12
After a bit of reading it seems that I can't use this Charge & Play setup with a wireless controller on a PC.  The controller still functions in wireless mode.  So I'll either have to go see if shops around here sell the PC receiver (I haven't seen them before, but have never looked either) or just pick up a cheap wired controller.

---

### Post by Modax42 on 2008-10-12
Now it works!  I don't think i did anything differently, but when I tried it again just now, my controller now works with all games.

---

### Post by soelk on 2008-10-18
I'm making some progress with my Hardy 32-bit and the wired controller. When I used: 

lsmod | grep xpad 

the first time it returned nothing. But nevertheless I got this when i ran the driver:

desktop:~/xboxdrv/xboxdrv-linux-0.2$ sudo ./xboxdrv -i 0
USB Device:        001:011
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface

Restarted the session and it still didn't work. Did 

lsmod | grep xpad 

again. And sure enough xpad was running several services. Did 

sudo rmmod xpad

and NOW the ./xboxdrv gives me data from the controller. Just thought I should share that in case it helps anyone.

---

### Post by soelk on 2008-10-18
[SIZE="4"]Update: A small error in the howto.[/SIZE]

The following file doesn't start the modules because the comments are on the same lines as the commands:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
fuse

# The following two modules are used with the xbox controller driver.
# Added on June 10th, 2008
uinput # for creating userspace drivers. 
joydev # for joystick devices
```

This slightly modified file works. You may already have other modules listed besides lp and fuse listed (I have one for audigy2). Your file may have other modules. Don't remove them, just add uinput and joydev.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
fuse

# The following two modules are used with the xbox controller driver.

# for creating userspace drivers.
uinput

# for joystick devices
joydev
```

[SIZE="4"]In addition to the howto[/SIZE]

Like Xyvir wrote earlier in this thread, it helps to blacklist xpad in /etc/modprobe.d/blacklist by adding something like this (with or without the comment, only remember to put it on it's own line...):

```
#replaced by XBOX360 userspace driver
blacklist xpad
```

I'll pm wootah about this. If he doesn't have time I'll make a new howto. This is important stuff. (I watched the documentary "King of Kong" yesterday which lead me to this howto in the hopes of getting zsnes running with the XBOX360 controller :D)

---

### Post by TrevE on 2008-10-18
Hey guys I think I got this driver working properly, but I cannot get games to pick up on it.  I am trying to play ioquake, it picked up immediately with xpad but i cant get it to find this at all.

I ran:
> sudo  ./xboxdrv --wid 0

it returns

> USB Device:        002:002
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Starting with uinput

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js1
  /dev/input/event6

Press Ctrl-c to quit

S1:(   161,  -1276)  S2:( -3488,  -1608) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:1 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
S1:(   161,  -1276)  S2:( -3488,  -1608) [u:0|d:0|l:0|r:0]  back:0 guide:0 start:0  sl:0 sr:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0


I see button input go by when I press buttons, but when I open up ioquake it doesn't' respond to the joystick at all.  Any ideas?

---

### Post by dreamer84 on 2008-10-26
Hi,
I wanted to try this with my big ben wireless gamepad (identified as ACRUX RF USB GAMEPAD 8206, but only via ```
$ sudo tail -fn0 /var/log/messages
Oct 26 12:51:03 xxxx kernel: [  469.951382] usb 2-2.3: new low speed USB device using uhci_hcd and address 3
Oct 26 12:51:03 xxxx kernel: [  470.163029] usb 2-2.3: configuration #1 chosen from 1 choice
Oct 26 12:51:03 xxxx kernel: [  170.805068] input: ACRUX RF USB GAMEPAD 8206 as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input10
Oct 26 12:51:03 xxxx kernel: [  170.836746] input,hidraw1: USB HID v1.00 Joystick [ACRUX RF USB GAMEPAD 8206] on usb-0000:00:10.1-2.3

```
while lsusb only shows the ID 1a34:0801 without label) which should behave like an xbox-controller. The USB-Receiver already creates a /dev/input/js0 and jscalibrator identifies the gamepad properties correctly, but I can't get it connected, whenever I press a button on the pad it only blinks 10 times like it does when the receiver is not plugged in at all. So I tried xboxdrv, by adding to xboxdrv.cpp XPadDevice xpad_devices[] = { ... ```
  { GAMEPAD_XBOX360_WIRELESS, 0x1a34, 0x0801, "ACRUX RF USB GAMEPAD 8206" },

```
Now
```

$ ./xboxdrv -L
 id | wid | idVendor | idProduct | Name
----+-----+----------+-----------+--------------------------------------
  0 |   0 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 0)
  0 |   1 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 1)
  0 |   2 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 2)
  0 |   3 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 3)

$ sudo ./xboxdrv
USB Device:        002:004
Controller:        "ACRUX RF USB GAMEPAD 8206" (idVendor: 0x1a34, idProduct: 0x0801)
Wireless Port:     0
Controller Type:   Xbox360 (wireless)
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Xbox360WirelessController: Error couldn't claim the USB interface 0

```

Maybe this is because of the already created /dev/input/js0, so how can I free it? Or does anyone else have an idea how to tell the gamepad that the receiver is plugged in so they can connect?

---

### Post by soelk on 2008-10-28
> **dreamer84 said:**
> Hi,
I wanted to try this with my big ben wireless gamepad (identified as ACRUX RF USB GAMEPAD 8206, but only via ```
$ sudo tail -fn0 /var/log/messages
Oct 26 12:51:03 xxxx kernel: [  469.951382] usb 2-2.3: new low speed USB device using uhci_hcd and address 3
Oct 26 12:51:03 xxxx kernel: [  470.163029] usb 2-2.3: configuration #1 chosen from 1 choice
Oct 26 12:51:03 xxxx kernel: [  170.805068] input: ACRUX RF USB GAMEPAD 8206 as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input10
Oct 26 12:51:03 xxxx kernel: [  170.836746] input,hidraw1: USB HID v1.00 Joystick [ACRUX RF USB GAMEPAD 8206] on usb-0000:00:10.1-2.3

```
while lsusb only shows the ID 1a34:0801 without label) which should behave like an xbox-controller. The USB-Receiver already creates a /dev/input/js0 and jscalibrator identifies the gamepad properties correctly, but I can't get it connected, whenever I press a button on the pad it only blinks 10 times like it does when the receiver is not plugged in at all. So I tried xboxdrv, by adding to xboxdrv.cpp XPadDevice xpad_devices[] = { ... ```
  { GAMEPAD_XBOX360_WIRELESS, 0x1a34, 0x0801, "ACRUX RF USB GAMEPAD 8206" },

```
Now
```

$ ./xboxdrv -L
 id | wid | idVendor | idProduct | Name
----+-----+----------+-----------+--------------------------------------
  0 |   0 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 0)
  0 |   1 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 1)
  0 |   2 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 2)
  0 |   3 |   0x1a34 |    0x0801 | ACRUX RF USB GAMEPAD 8206 (Port: 3)

$ sudo ./xboxdrv
USB Device:        002:004
Controller:        "ACRUX RF USB GAMEPAD 8206" (idVendor: 0x1a34, idProduct: 0x0801)
Wireless Port:     0
Controller Type:   Xbox360 (wireless)
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Xbox360WirelessController: Error couldn't claim the USB interface 0

```

Maybe this is because of the already created /dev/input/js0, so how can I free it? Or does anyone else have an idea how to tell the gamepad that the receiver is plugged in so they can connect?

Maybe. Have you tried to run 

lsmod | grep xpad

**after** you insert the reciever into the USB port? It's possible that xpad tries to provide plug and play for you, when you least want it.

---

### Post by dreamer84 on 2008-10-29
soelk,
no, xpad doesn't load, though I tried manually loading it to check whether that would make the pad working, but it didn't.

I think the problem is that the bigben gamepad is a PC pad, I only read that they also designed the xbox-pads and hoped for compatibility. Their support unfortunately couldn't help me, but I'm still waiting for a reply from acrux21.com (because that's who the USB-Stick tells it is made by).

now I'm already quite off-topic, sorry about that, but does anyone happen to know which mod is responsible for the already created js0 so I can unload that? I suppose that's the reason why xboxdrv can't claim the USB interface :-(
the usb-stick does not provide a sync button, so i guess the windows driver regularly tries that internally. is there any way to sniff windows<->USB traffic? that is probably the only thing I'd need to insert into whatever mod already provides js0... (or probably rather I'd need some nice person to insert for me)

edit: found [http://sourceforge.net/projects/usbsnoop/]("http://sourceforge.net/projects/usbsnoop/"), I'll give it a try. also because this is definitely off-topic, so I'll post any further results in [http://ubuntuforums.org/showthread.php?t=959127]("http://ubuntuforums.org/showthread.php?t=959127")

---

### Post by topalof on 2008-10-31
Can anyone help me? I installed everything and compiled xboxdrv, uinput and joydev are loaded and xpad is blacklisted and not loaded. But everytime I try to use the driver it only shows this:
```

USB Device:        001:014
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none


```
Then it stays there indefinitely. When I look at /var/log/messages it says
```
Oct 31 20:48:19 laptop kernel: [12472.138199] usb 1-2.4: usbfs: process 8679 (xboxdrv) did not claim interface 1 before use
```

That's it, I can't use it in any games and the LEDs on the controller keep blinking. It's a wired controller.

---

### Post by Grumbel on 2008-11-06
> **TrevE said:**
> I see button input go by when I press buttons, but when I open up ioquake it doesn't' respond to the joystick at all.  Any ideas?
Your gamepad gets registered as /dev/input/js1, if ioquake is only listening to /dev/input/js0 it won't here any events coming in. So you have to figure out where /dev/input/js0 is coming from and get rid of it or do it the brute force way and do:

mv /dev/input/js0  /dev/input/js0.old
mv /dev/input/js1  /dev/input/js0

Not exactly a clean solution, but should work at least till the next reboot. 

You can use "jstest /dev/input/js0" to figure out the name of the joystick.

---

### Post by ajhtiredwolf on 2008-11-06
I get the same error that several other people in here have posted 
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors

---

### Post by KhaaL on 2008-11-07
> **Nonni said:**
> I have the same problem. I have build-essential installed. I'm running the intrepid alpha.

I also have this problem:

```
khaal@Xeraphim:~/Desktop/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```

I am also running 8.10, could that be the problem?

---

### Post by sixstringmonk on 2008-11-07
> **KhaaL said:**
> I also have this problem:

```
khaal@Xeraphim:~/Desktop/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```

I am also running 8.10, could that be the problem?

I'm having the same problem with 8.10. Build-essential is installed.

---

### Post by ajhtiredwolf on 2008-11-08
THe problem is due to this guide referencing the old driver, download the latest driver from here [http://pingus.seul.org/%7Egrumbel/xboxdrv/](http://pingus.seul.org/%7Egrumbel/xboxdrv/), version 0.3. Follow all of the guides instructions but with using that driver and it should work fine.

---

### Post by wootah on 2008-11-08
Hi folks!

It has been awhile since I have been on the forums. I appreciate people continuing on with experimenting with this driver, but please remember, it is early beta. I haven't been around to answer questions as university has taken a major portion of my time. I have a work term coming up in January in which I will get back with dev and update this guide for a more rounded and easier approach.

Subscribe to this post as I'll post more information linking to a newer guide when it becomes available. Also, another user contacted me about creating a newer HowTo--maybe that will show up sometime :)

---

### Post by danbaatar on 2008-11-08
I'm having trouble with xboxdrv in Intrepid also.  Here's a typical session where I try and get it to work:

```

dan@fileserver:~$ lsmod | grep input
dan@fileserver:~$ sudo modprobe uinput
[sudo] password for dan: 
dan@fileserver:~$ lsmod |grep xpad
dan@fileserver:~$ cd xboxdrv/
dan@fileserver:~/xboxdrv$ sudo ./xboxdrv -L
 id | wid | idVendor | idProduct | Name
----+-----+----------+-----------+--------------------------------------
  0 |   0 |   0x045e |    0x028e | Microsoft Xbox 360 Controller
dan@fileserver:~/xboxdrv$ sudo ./xboxdrv -i 0
USB Device:        001:002
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none

```

and it just hangs there.  I can't even kill it with CTRL-C.

I saw that others were having similar problems, but I was hoping that someone might have a solution.  By the way, when I look at the output of dmesg I get this:

```
[  237.777606] usb 1-3: usbfs: process 7233 (xboxdrv) did not claim interface 1 before use
```

I am using the latest copy of the code, checked out just an hour or two ago from the git repository.

---

### Post by mnorton_B9 on 2008-11-08
hi,

I have been hopping lots of threads on how to get the xbox360 controllers to work. I gave up on xpad and I am trying this solution. No luck.

This is the flavor of Ubuntu I am running, 2.6.24-21-generic (AMD 64Bit).

scons appears to have run fine for me and I have the target files.

```

mnorton@skynet:~/xpad/xboxdrv-linux-0.3$ lsmod | grep uinput
uinput                 11904  0 
mnorton@skynet:~/xpad/xboxdrv-linux-0.3$ lsmod | grep joydev
joydev                 15488  0 

```

When I run the xboxdrv I see the familair Exception: USBError: -2.

```

mnorton@skynet:~/xpad/xboxdrv-linux-0.3$ sudo  ./xboxdrv --id 0
[sudo] password for mnorton: 
USB Device:        002:003
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028f)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Starting with uinput

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event6

Press Ctrl-c to quit

Exception: USBError: -2
error submitting URB: No such file or directory

```

More info if helpful

```

mnorton@skynet:~/xpad/xboxdrv-linux-0.3$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller
Bus 002 Device 002: ID 0430:0005 Sun Microsystems, Inc. Type 6 Keyboard
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

How do I get the xboxdrv to run on my 64-bit machine?

thanks in advance!

---

### Post by danbaatar on 2008-11-08
I've been trying to do some debugging of my problem, I put in some printouts to try and figure out where things were going wrong.  As best I can tell, the code never returns from this call in void
Xbox360Controller::set_led(uint8_t status):

```

usb_interrupt_write(handle, 2, ledcmd, sizeof(ledcmd), 0);
```

I have printouts (with flushes) right before and right after this call, and only the first shows up, then the program hangs.

Does anyone have a quick suggestion as to how to proceed?  I don't mind giving a hand with the debugging, but I'd prefer not to spend hours researching libraries and the ins and outs of the usb system in Linux if there is a fairly simple fix available.

Because of the information from my previous post, I have an idea that it has something to do with the way the driver tries to claim the usb interface earlier on.  I am on a 64-bit system.  Could that have anything to do with it?

--dan

---

### Post by danbaatar on 2008-11-09
I found the solution in another thread.  The endpoints of the calls to usb_interrupt_write need to be ones instead of twos on my system.  You can see the solution in [an earlier post in this thread]("http://ubuntuforums.org/showpost.php?p=5798873&postcount=60").

---

### Post by kielanmatt on 2008-11-09
WTF ffs how long!!! i have been trying to make my gamepad work, and it stops at

```

kielanmatt@ubuntu:~/xboxdrv-linux-0.2$ sudo ./xboxdrv --id 0
USB Device:        001:008
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none


```
and then it just flashes i have unloaded xpad and blacklisted it SO WTF is WORNG WITH IT!?!?!

---

### Post by KhaaL on 2008-11-09
using 0.3, the driver finally worked! but i realized i couldnt assign keys to it in frets on fire; the guitar was instead controlling my mouse (the tilt and whammy was controlling the x and y axis respectively). How did this happen?

---

### Post by xen-uno on 2008-11-10
I've gotten around the problem by attaching the controller to a 360 console instead (attached to the comp monitor directly via component input). Now I just need to get Ubuntu's DHCP server working for Xbox Live.

---

### Post by ncanna1 on 2008-11-10
I'm having some trouble with the scons.  Whenever I execute scons, I get the following output:
```

nick@goetterdaemmerung:~/tmp/xboxdrv-linux-0.2$ sudo scons                                       
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```

---

### Post by walkmanpo on 2008-11-18
> **ncanna1 said:**
> I'm having some trouble with the scons.  Whenever I execute scons, I get the following output:
```

nick@goetterdaemmerung:~/tmp/xboxdrv-linux-0.2$ sudo scons                                       
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```

Try
 
```
sudo apt-get install linux-headers-`uname -r` build-essential automake
```

then scons again

---

### Post by paraplegicpanda on 2008-11-19
Hey guys, I'm having some problems with the flashing cursor hangup. I'm using an Xbox 360 Wired Controller (the officially licensed controller, not a third-party controller). Here's my terminal when I run the driver with my controller attached:

```

paraplegicpanda@hacktopix:~/tmp/xboxdrv$ lsmod | grep uinput && lsmod | grep joydev
uinput                 11904  0 
joydev                 15488  0 
paraplegicpanda@hacktopix:~/tmp/xboxdrv$ lsmod | grep xpad
paraplegicpanda@hacktopix:~/tmp/xboxdrv$ sudo ./xboxdrv -L
 id | wid | idVendor | idProduct | Name
----+-----+----------+-----------+--------------------------------------
  0 |   0 |   0x045e |    0x028e | Microsoft Xbox 360 Controller
paraplegicpanda@hacktopix:~/tmp/xboxdrv$ sudo ./xboxdrv --id 0
USB Device:        001:006
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
{{{FLASHING CURSOR}}}

```

When I hit CTRL+C I get:

```

Shutdown initiated, press Ctrl-c again if nothing is happening

```

Then I finally unplug my controller and it says this:

```

Starting with uinput

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event9

Press Ctrl-c to quit

Exception: USBError: -19
error submitting URB: No such device

```


I have tried running the driver with and without --id 0 and I get no change. I have also tried going in and changing all of the instances of usb_interrupt_write from 2 to 1 and back to 2. I have both versions still.

I am using v0.3 of the driver. I have blacklisted xpad and added uinput and joydev to modules with the comments moved so that they autoload correctly, I have rebooted, and I am still having no luck.

Any further help would be excellent, thanks!



HP Pavilion dv6704nr 
Ubuntu Intrepid Ibex 8.10

---

### Post by ncanna1 on 2008-11-22
> **walkmanpo said:**
> Try
 
```
sudo apt-get install linux-headers-`uname -r` build-essential automake
```

then scons again

still not finishing.  this is what i get back:

```
nick@goetterdaemmerung:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o helper.o -c -g -O0 -Wall helper.cpp
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```

---

### Post by ajhtiredwolf on 2008-11-23
> **ncanna1 said:**
> still not finishing.  this is what i get back:

```
nick@goetterdaemmerung:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o helper.o -c -g -O0 -Wall helper.cpp
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```



You need to use the newest driver 0.3 not 0.2.

---

### Post by joobloo on 2008-11-26
I'm getting the same problem as Khaal.  Version .3 compiles fine, and even seems to load fine.  But the whammy takes control of the mouse, and the buttons don't respond in FoF.  Jscalibrator sees the controller (xbox360 guitar) at /dev/input/js0, but the buttons don't respond.  If I use the --no-uinput argument, then the driver doesn't take control of the mouse, but still the buttons don't respond.  I'm using Ubuntu 8.10.  I added xpad to my blacklist file.  Anyone know a solution?

---

### Post by Chrono Reaper on 2008-12-03
Is it too late to correct these problems if I screwed up the first time because I'm still getting the problem where the wired Xbox 360 controller is still blinking and acting like a mouse

---

### Post by NoThanksM$ on 2008-12-03
In looking around various forums, some people have had success with the suggestion found in this thread:
[http://ubuntuforums.org/showthread.php?t=982579](http://ubuntuforums.org/showthread.php?t=982579)
However, it only worked partially for me.  I'd be interested in hearing what kind of success others here have with it.

---

### Post by AoDZelda on 2008-12-10
Does anyone know if this has been updated? I'm using 8.10 Intrepid. I haven't tried this yet myself since I'm at work and browsing around. Has anyone tried this in Intrepid? I will try myself when I get home from work.

---

### Post by wootah on 2008-12-12
> **AoDZelda said:**
> Does anyone know if this has been updated? I'm using 8.10 Intrepid. I haven't tried this yet myself since I'm at work and browsing around. Has anyone tried this in Intrepid? I will try myself when I get home from work.
I will be updating this guide in a few weeks, as I have just got my new mobile dev machine and a bunch of time once finals are over :)

Check back soon gentlemen/ladies :)

---

### Post by nemuri on 2008-12-14
I seem to be stuck with a different issue. uinput and joydev running, xpad is definitely not loaded, and I get as far as:

```
Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event6

Press Ctrl-c to quit
```

...At which point I get no response whatsoever pressing any of the buttons on the controller. I am able to quit with Ctrl+C twice, but otherwise, nothing.

I have a feeling I'm missing something really basic - is there something I need to do with the controller to get it to link, other than turning it on by pressing the guide button? (Not familiar as I don't actually own an Xbox 360; bought the controller exclusively for use with XBMC.) Any suggestions much appreciated...

---

### Post by xxsamoxx on 2008-12-19
THANK YOU for this howto!  I am a linux newb but it was easy to get set up.  I wanted to contribute a small part, I have a Hori Fighting stick Ex2 it works if you add 

```
  { GAMEPAD_XBOX360,          0x0f0d, 0x000d, "Hori Fighting Stick Ex2" },
``` 
into xboxdrv.cpp before you compile.  This should also work for Hori's Soul Calibur and Doa4 controllers as well.  They use the same PCB.  The only think about this controller is the LT and RT do not work unless I map them to a different button

```
 --buttonmap lt=tl,rt=tr 
``` works for me.

What do you guys do with this driver though.  I would like to have it load quietly every time I plug in my controller but right now I have to start it manually.

---

### Post by Grumbel on 2008-12-26
> **xxsamoxx said:**
> What do you guys do with this driver though.
I start the driver always manually, since most games require a special set of options to work properly (--buttonmap, --dpad-only, etc.), so it wouldn't make sense to run it in the background.

There is a --daemon option and with some udev magic one might be able to get it started automatically, but I never bothered to try that and I have some doubt that it would work well without some further code changes/fixes. Maybe one could also hack something together with hal, but I never really looked into it.

Are people still having trouble with the vanilla source freezing on startup without the 2 -> 1 replacement in xbox360_controller.cpp? If so could anybody of those contact me so that we can work out a proper fix, I think the 2->1 just works because it makes all controller communication fail and thus LED and rumble no longer work.

---

### Post by Dr. GoS on 2009-01-02
Sorry, I am new to this discussion. If I go out and buy a wired controller, what will I need to do to get it working as a mouse?

---

### Post by Grumbel on 2009-01-03
> **Dr. GoS said:**
> Sorry, I am new to this discussion. If I go out and buy a wired controller, what will I need to do to get it working as a mouse?
Latest development version of xboxdrv would do, from the README:

[[ Mouse Emulation ]]
---------------------

xboxdrv does not support real mouse emulation, however due to Xorg hotplug brokeness and ugly hackery, the following gives you mouse emulation, its not pretty, but sort of works:

  % ./xboxdrv --ui-buttonmap A=BTN_LEFT,B=BTN_RIGHT -s  --relative-axis X1=64000,Y1=64000 --deadzone 4192

This assumed that you have not applied any of the Xorg workarounds and are using a version of Xorg that will handle your gamepad as mouse.

---

### Post by Dr. GoS on 2009-01-03
> **Grumbel said:**
> Latest development version of xboxdrv would do, from the README:

[[ Mouse Emulation ]]
---------------------

xboxdrv does not support real mouse emulation, however due to Xorg hotplug brokeness and ugly hackery, the following gives you mouse emulation, its not pretty, but sort of works:

  % ./xboxdrv --ui-buttonmap A=BTN_LEFT,B=BTN_RIGHT -s  --relative-axis X1=64000,Y1=64000 --deadzone 4192

This assumed that you have not applied any of the Xorg workarounds and are using a version of Xorg that will handle your gamepad as mouse.

Oh, that's great, thanks!

---

### Post by adrianmck on 2009-01-07
Hi

I'm running Hardy 64 and I've been having some problems getting this driver to work.

I've been able to compile version 0.3 but whenever I run it I get the following 

```

adrian@adrian-dell:~/src/xboxdrv/xboxdrv-linux-0.3$ ./xboxdrv --id 0
USB Device:        002:006
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Exception: Error couldn't claim the USB interface
Try to run 'rmmod xpad' and start xboxdrv again

```

and if I do it as root it just hangs

```

adrian@adrian-dell:~/src/xboxdrv/xboxdrv-linux-0.3$ sudo ./xboxdrv --id 0
USB Device:        002:006
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: 0 right: 0
LED Status:        auto
ButtonMap:         none
AxisMap:           none

```

from /var/log/messages

```

Jan  8 01:32:54 adrian-dell kernel: [ 1617.262592] usb 2-9: usbfs: process 7989 (xboxdrv) did not claim interface 1 before use
Jan  8 01:33:19 adrian-dell kernel: [ 1626.841850] usb 2-9: usbfs: process 7999 (xboxdrv) did not claim interface 1 before use

```

In both cases no /dev/input/js0 is created

uinput ans joydev are loaded and xpad is blacklisted

Also I tried version 0.4 which but it won't compile

```

adrian@adrian-dell:~/src/xboxdrv/xboxdrv-linux-0.4$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/evdev_helper.o -c -g -O2 src/evdev_helper.cpp
src/evdev_helper.cpp: In constructor 'EvDevBtnEnum::EvDevBtnEnum()':
src/evdev_helper.cpp:541: error: 'KEY_MEDIA_REPEAT' was not declared in this scope
scons: *** [src/evdev_helper.o] Error 1
scons: building terminated because of errors.

```

Any help would be much appreciated

---

### Post by Grumbel on 2009-01-07
> ```

src/evdev_helper.cpp:541: error: 'KEY_MEDIA_REPEAT' was not 
```
Nasty, looks like a key define is missing in your headers. Just remove that line in evdev_helper.cpp to make it work and any other line in that file that might cause similar trouble.

What kernel are you running? Anything self compiled or standard Ubuntu default kernel for 64bit?

---

### Post by adrianmck on 2009-01-07
Hi Grumbel,

I'm just using the standard kernel 2.6.24-22-generic.

So I followed your advise and commented out 'KEY_MEDIA_REPEAT' in evdev_helper.cpp recompiled and everything appears to be working. All I can say is thanks

```

    add(KEY_CONTEXT_MENU,    "KEY_CONTEXT_MENU");
//    add(KEY_MEDIA_REPEAT,    "KEY_MEDIA_REPEAT");
    add(KEY_DEL_EOL,         "KEY_DEL_EOL");

```

---

### Post by s3kt0r on 2009-01-10
```

s3kt0r@g7000:~/xboxdrv-linux-0.4.1$ ./xboxdrv 
xboxdrv 0.4
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        001:003
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Square Axis:       no
RelativeAxisMap:   none
AutoFireMap:       none
ForceFeedback:     disabled

Starting with uinput... done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event12

Press Ctrl-c to quit

Exception: USBError: -2
error submitting URB: No such file or directory

```
Well, I've also been having this URB error thing, but I noticed that this error always appears (to me anyways, and that is the problem I think) when, after I run the driver (don't even have to run it through sudo), I can't terminate the driver, hit Ctrl+C once, twice, it just hangs there. 
Then, if I close the terminal, and load the driver again, the URB error appears. 
If I unplug the controller (which is the 360 wired, btw), plug it in again, and run the driver, it works. 
Getting passed this phase, the driver immediately recognizes every action, being buttons, dpad or analog sticks, but when I set out to try it in one of my favourites Streets of Rage 3, I can't really calibrate it right. 
The dpad doesn't work, and the left analog stick doesn't seem to be accurate, it's very very sensitive. The buttons, on the other hand, seem to be working fine. Also tried running with option --dpad-only, didn't work.
So...For me it's  now just a matter of calibrating the controller, right? Except I don't know how to. Should I try altering xbox360_controller.cpp?
Oh, I'm running on kernel 2.6.8, uinput and joydev are loaded, xpad is blacklisted.
I'm out of leads and feeling a little bit lost, maybe anyone can help out?

---

### Post by Grumbel on 2009-01-10
> **s3kt0r said:**
> Well, I've also been having this URB error thing, but I noticed that this error always appears (to me anyways, and that is the problem I think) when, after I run the driver (don't even have to run it through sudo), I can't terminate the driver, hit Ctrl+C once, twice, it just hangs there.
Could you launch gdb to figure out where the driver hangs?

% gdb --pid PID_OF_XBOXDRV
(gdb) <Ctrl-c>
(gdb) bt


And have a look at dmesg for anything that looks suspicious?

Your kernel seems rather old, so it might very well just a bug or incompatibility.

> Then, if I close the terminal, and load the driver again, the URB error appears.
Thats kind of expected, since no two apps can mess around with a single USB device, even so I am a bit surprised that it happens that late in the process. 

> Also tried running with option --dpad-only, didn't work.
Look like I broke dpad-only, going to fix it later this day and upload a new version.

> So...For me it's  now just a matter of calibrating the controller, right?
No, you don't have to calibrate current days gamepads. There however is a --deadzone 8000 option you might want to try in xboxdrv, that removes the sensitivity.

---

### Post by Grumbel on 2009-01-10
New xboxdrv version is available, fixes the issue with dpad-only:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)
[http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv-linux-0.4.2.tar.bz2](http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv-linux-0.4.2.tar.bz2)

---

### Post by Fenris_rising on 2009-01-11
Hi there
I have run through this from page 1. very straight forward and easy to follow. But......there had to be one :D I am having the same problem as quite a few others of you. heres the code and this is from the most recent available DL. I have uinput and joydev loading at boot and xpad is blacklisted. I am also running this on an eee pc with netbook mix 8.04.1

```
fenris@Macra:~/Desktop/xboxdrv-linux-0.4.2$ sudo ./xboxdrv --id 0
xboxdrv 0.4.2
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        001:005
Controller:        "Microsoft X-Box pad v1 (US)" (idVendor: 0x045e, idProduct: 0x0202)
Controller Type:   Xbox Classic
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
ButtonMap:         none
AxisMap:           none
Square Axis:       no
RelativeAxisMap:   none
AutoFireMap:       none
ForceFeedback:     disabled

Starting with uinput... done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event9

Press Ctrl-c to quit

Exception: USBError: -2
error submitting URB: No such file or directory

```

Any help would be appreciated.

Regards

Fenris

---

### Post by Grumbel on 2009-01-11
Could you send me the output of:

% sudo lsusb -d 045e:0202 -v

---

### Post by Fenris_rising on 2009-01-11
Hi there

Thanks for looking. Heres the output.

```
Bus 001 Device 005: ID 045e:0202 Microsoft Corp. Xbox Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x045e Microsoft Corp.
  idProduct          0x0202 Xbox Controller
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        88 
      bInterfaceSubClass     66 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
Device Status:     0x0000
  (Bus Powered)
```

regards

Fenris

---

### Post by Grumbel on 2009-01-11
Open src/xbox_controller.cpp line 71, replace:

int ret = usb_interrupt_read(handle, 1 /*EndPoint*/, (char*)data, sizeof(data), timeout);

with:

int ret = usb_interrupt_read(handle, 2 /*EndPoint*/, (char*)data, sizeof(data), timeout);

Seems like different Xbox controller use different endpoints.

---

### Post by Fenris_rising on 2009-01-11
OK i have done that. No change in the error though. Should I have done this then re compiled? I am 6 months into Linux so not completely ofay with all the ins and outs.

regards

Fenris

I recompiled :D it seems to be working..........well I have streams of figures in terminal

---

### Post by Fenris_rising on 2009-01-11
Hi there

Just going back through this post to find the 'null point' setting for the stick. Thanks for your help.

regards

Fenris

---

### Post by Fenris_rising on 2009-01-11
Neverball works fine. Speedtux2 not so good it seems to be misinterpreting the pad inputs. Is is possible to configure the controls at all? Im thinking for warsow? or is it a question of what coding has been done in the game? I've had to set my deadspot at 4000 as the pad has sen a lot of action. Great tut and it was easier than it seemed here and there to tweak it into running.

regards

Fenris

---

### Post by NoThanksM$ on 2009-01-11
I just downloaded and compiled version 0.4.2 of xboxdrv after reading this and another thread, trying to get the wired Xbox 360 guitar to work.  I run
```
sudo rmmod xpad
```
and then try to start ./xboxdrv, but when I do that I get the following exception:
```
Error couldn't claim the USB interface: Operation not permitted
Try to run 'rmmod xpad' and start xboxdrv again.
```
I try running sudo rmmod xpad again, but it's already unloaded.  Then, if I try running
```
sudo ./xboxdrv
``` it seems to work except I get the following scrolling endlessly through the terminal window:
```
 whammy:-32768 tilt: -4260 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-32768 tilt: -4096 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-32768 tilt: -4260 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-32768 tilt: -4096 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-32768 tilt: -4260 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 

```
until I finally end it (and quit xboxdrv) by typing Cntrl-C.  

Any thoughts or advice on how to fix this and get the guitar working?

---

### Post by Grumbel on 2009-01-12
> **NoThanksM$ said:**
> it seems to work except I get the following scrolling endlessly through the terminal window
Are the reported events correct? If so it is working as intended, use -s to suppress the printing of events. If Xorg grabbed your guitar see the README for workarounds.

---

### Post by Grumbel on 2009-01-12
> **Fenris_rising said:**
> Is is possible to configure the controls at all?
Yes, see README, pretty much everything from FCS Flightstick emulation for DOSBOX, to keyboard emulation to FPS with mouse emulation is possible. If you have a game or situation that xboxdrv can't handle let me know.

---

### Post by Fenris_rising on 2009-01-12
hi there

i shall have a good look. Thanks for your help :)

regards

Fenris

---

### Post by Fenris_rising on 2009-01-12
hi there

Had a bit of a play with Warsow. I think I understand what to do to tweak the warsow file as far as button control goes (i had to use keyboard to fire and jump) also is there a different method of setting the mouse to xbox pad if all you have is a track pad? as only the left stick worked for step left/right and forward/back. I had to use the cursor keys to turn left/right. My inexperienced thinking is....
setup the controls in the game settings as far as what keyboard button does  what then make the required edits to the Warsow pad controls that are in the read me file..........have I understood that well enough?

regards

Fenris

---

### Post by Grumbel on 2009-01-14
The Warsaw config in the README is just an example, not a 100% fine tuned control setup, so for the buttons you likely have to adjust them a bit to fit you liking.

If the mouse emulation does not work for you, you have to look where the events end up, i.e. use evtest to  look if the devices are created and report events also  use xinput to check that the devices get picked up by Xorg. If they don't get picked up messing around with HAL is required.

---

### Post by s3kt0r on 2009-01-18
First of all, sorry for the one week (or more) late response, but college is keeping me very busy, it's the final year before graduation so...Anyways, let's get to business.

> **Grumbel said:**
> Could you launch gdb to figure out where the driver hangs?

% gdb --pid PID_OF_XBOXDRV
(gdb) <Ctrl-c>
(gdb) bt


And have a look at dmesg for anything that looks suspicious?


gdb --pid PID_OF_XBOXDRV output
```
#2  0xb8015a5d in ?? () from /lib/libusb-0.1.so.4
#3  0x08067e57 in Xbox360Controller::read (this=0x809e130, msg=@0xbfb4c57c, 
    verbose=false, timeout=10) at src/xbox360_controller.cpp:103
#4  0x0804bd9d in controller_loop (uinput=0x809e148, controller=0x809e130, 
    opts=@0xbfb4c880) at src/xboxdrv.cpp:1064
#5  0x0804e4eb in run_main (opts=@0xbfb4c880) at src/xboxdrv.cpp:1296
#6  0x0804feac in main (argc=1, argv=Cannot access memory at address 0x4
) at src/xboxdrv.cpp:1335
```

dmesg output
```
[  616.440095] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  616.652127] usb 1-1: configuration #1 chosen from 1 choice
[  670.065536] usb 1-1: usbfs: process 9088 (xboxdrv) did not claim interface 1 
before use
[  670.070794] input: Xbox Gamepad (userspace driver) as /class/input/input13

```
> 
Your kernel seems rather old, so it might very well just a bug or incompatibility.


Ah, sorry Grumbel, that's not really the case, I just forgot  to type the 2, it's the latest one I think (if another release hasn't gone out since last month), 2.6.28.

> 
Look like I broke dpad-only, going to fix it later this day and upload a new version.


Going to try it, just in case, but gdb and dmesg outputs were in 0.4.1, I'll check out the outputs with 0.4.2 and paste them here if you want, although if you only corrected --dpad-only shouldn't resolve much. 

> 
No, you don't have to calibrate current days gamepads. There however is a --deadzone 8000 option you might want to try in xboxdrv, that removes the sensitivity.


Thanks, haven't bought a controller in years so..I'll also try that deadzone option, having seen it before never tried to test it, didn't have any guess on the numbers I should try.

Stickin' with this, learning is always a good thing!

---

### Post by Grumbel on 2009-01-18
> **s3kt0r said:**
> gdb --pid PID_OF_XBOXDRV output
Hm, that output show that it hangs in read() which is to be expected, that however doesn't explain why you can't kill it with two 'Ctrl-c'.

```
[  670.065536] usb 1-1: usbfs: process 9088 (xboxdrv) did not claim interface 1 before use
[  670.070794] input: Xbox Gamepad (userspace driver) as /class/input/input13

```
That looks wrong, could you run:

lsusb -v -d 045e:028e 

And post the output. xboxdrv shouldn't do anything with interface 1, but different controllers seem to have different endpoint/interface settings.

Also there is a new version of xboxdrv available, I don't think it fixes any of your problems, but can't hurt to be up to date.

---

### Post by mole2006 on 2009-01-18
Hey I followed the guide everything worked fine until I tried to run scons, I got this error:

```

g++ -o src/evdev_helper.o -c -g -O2 -Wall -ansi -pedantic src/evdev_helper.cpp
src/evdev_helper.cpp:19:22: error: X11/Xlib.h: No such file or directory
src/evdev_helper.cpp:590: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:590: error: template argument 1 is invalid
src/evdev_helper.cpp:590: error: template argument 3 is invalid
src/evdev_helper.cpp:590: error: template argument 4 is invalid
src/evdev_helper.cpp:608: error: 'Display' has not been declared
src/evdev_helper.cpp: In constructor 'Keysym2Keycode::Keysym2Keycode()':
src/evdev_helper.cpp:596: error: 'Display' was not declared in this scope
src/evdev_helper.cpp:596: error: 'dpy' was not declared in this scope
src/evdev_helper.cpp:596: error: 'XOpenDisplay' was not declared in this scope
src/evdev_helper.cpp:604: error: 'XCloseDisplay' was not declared in this scope
src/evdev_helper.cpp: In member function 'void Keysym2Keycode::process_keymap(int*)':
src/evdev_helper.cpp:611: error: 'XDisplayKeycodes' was not declared in this scope
src/evdev_helper.cpp:615: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:615: error: 'keymap' was not declared in this scope
src/evdev_helper.cpp:617: error: 'XGetKeyboardMapping' was not declared in this scope
src/evdev_helper.cpp:621: error: 'NoSymbol' was not declared in this scope
src/evdev_helper.cpp:623: error: expected `;' before 'keysym'
src/evdev_helper.cpp:628: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:632: error: 'XFree' was not declared in this scope
src/evdev_helper.cpp: In function 'int xkeysym2keycode(const std::string&)':
src/evdev_helper.cpp:640: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:640: error: expected `;' before 'keysym'
src/evdev_helper.cpp:642: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:642: error: 'NoSymbol' was not declared in this scope
src/evdev_helper.cpp:647: error: 'KeySym' cannot appear in a constant-expression
src/evdev_helper.cpp:647: error: template argument 1 is invalid
src/evdev_helper.cpp:647: error: template argument 3 is invalid
src/evdev_helper.cpp:647: error: template argument 4 is invalid
src/evdev_helper.cpp:647: error: expected initializer before 'i'
src/evdev_helper.cpp:648: error: 'i' was not declared in this scope
src/evdev_helper.cpp:648: error: request for member 'end' in 'sym2code.Keysym2Keycode::mapping', which is of non-class type 'int'
src/evdev_helper.cpp:655: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:655: error: 'XKeysymToString' was not declared in this scope
scons: *** [src/evdev_helper.o] Error 1
scons: building terminated because of errors.

```

---

### Post by Grumbel on 2009-01-18
> **mole2006 said:**
> Hey I followed the guide everything worked fine until I tried to run scons, I got this error:
apt-get install libx11-dev x11proto-core-dev

---

### Post by s3kt0r on 2009-01-19
@ Grumbel

lsusb -v -d 045e:028e output

```

Bus 001 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x028e Xbox360 Controller
  bcdDevice            1.14
  iManufacturer           1 &#65533;Microsoft Corporation
  iProduct                2 Controller
  iSerial                 3 08A9219
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          153
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      1 
      iInterface              0 
      ** UNRECOGNIZED:  11 21 00 01 01 25 81 14 00 00 00 00 13 01 08 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      3 
      iInterface              0 
      ** UNRECOGNIZED:  1b 21 00 01 01 01 82 40 01 02 20 16 83 00 00 00 00 00 00 16 03 00 00 00 00 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               2
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              64
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 01 22 84 07 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    253 
      bInterfaceProtocol     19 
      iInterface              4 
      ** UNRECOGNIZED:  06 41 00 01 01 03
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

```

I sure hope this is helping somehow, not just giving you extra work :)

Also tried 0.4.3, and as expected, didn't improve the situation.

---

### Post by NoThanksM$ on 2009-01-19
Thanks for your suggestion in post 123.  Adding "-s" helped partially, and then your hint about Xorg grabbing the guitar led me to use info from another post in a different thread, located here:
[http://ubuntuforums.org/showpost.php?p=6267529&postcount=4](http://ubuntuforums.org/showpost.php?p=6267529&postcount=4)

"Adding to the /etc/X11/xorg.conf only the following code

Section "ServerFlags"
Option "AutoAddDevices" "False"
EndSection

will make the guitar work perfectly."

I did this, rebooted, followed the instructions in this thread and the guitar is working great now!  The one oddity I did notice, which doesn't matter at all to me but I thought you might want to know, is that the "up" and "down" controls for the D-pad on the guitar are reversed.  No matter which one I enter into the game as "up" and which one I enter as "down," when I press "up" it goes "down" in menus, and vice versa, even though it wasn't that way when the xpad driver worked in previous Ubuntu versions.  Again, doesn't bother me, but thought it might be helpful for you to know.

Thanks so much for this driver and your quick responses to all of our questions here!

---

### Post by Grumbel on 2009-01-20
> I sure hope this is helping somehow, not just giving you extra work :)
As expected the endpoints are different on your controller then on mine, you can temporary fix that by replacing all:
 
usb_interrupt_write(handle, 2, ...

with

usb_interrupt_write(handle, 1, ...

A more permanent solution will follow shortly.

**Update**: auto detection of endpoints is now in git:

git clone [http://pingus.seul.org/~grumbel/xboxdrv.git](http://pingus.seul.org/~grumbel/xboxdrv.git)

---

### Post by Grumbel on 2009-01-20
> I did this
If you want to preserve auto detection you can use for less drastic workarounds, documented at:

[http://github.com/Grumbel/xboxdrv/blob/85a72e7e1981c3129764639ff900484ccc00376d/README](http://github.com/Grumbel/xboxdrv/blob/85a72e7e1981c3129764639ff900484ccc00376d/README)

> The one oddity I did notice, which doesn't matter at all to me but I thought you might want to know, is that the "up" and "down" controls for the D-pad on the guitar are reversed.
Hm, if you remap the controls in the game and they still come out wrong, that sounds more like an issue with the game then with xboxdrv.

You could of course always do a:

./xboxdrv --buttonmap du=dd,dd=du

to swap up and down on the dpad, but normally mapping the buttons in the game should fix things easily.

---

### Post by thomzon on 2009-02-07
Hello,

Firstly, if the person/team behind this driver reads this : THANK YOU !!!
Seriously, it's marvellous. I hope the satisfaction and pleasure I get from using my Hori Fighting Sticks with Mame gets back to you tenfold.

Now to my 2 little problems:

1. Actually, everything runs fine when starting the driver manually. However, since I only use my controllers with one single application, I tried to set up some udev rules to auto-launch the drivers when plugging in my sticks. This did not work for me, because apparently the rule will only trigger AFTER the driver has been launched. When plugging the device, it appears when doing "lsusb", but fails to trigger any udev rule. Do someone know if it is possible to get this working ?

2. When simply running the driver without any options (other than button mapping), the stick itself is not recognized in jscalibrator (meaning when I move the stick around, it is not recognized as one of the axis, and I cannot use it in Mame for example).
I manage by adding the "--dpad-as-button" option, but I kind of hope to get it working normally. Any suggestions for me ?

---

### Post by Grumbel on 2009-02-07
> **thomzon said:**
> Do someone know if it is possible to get this working?
It might somehow be possible in theory, but I wouldn't recomment it. Launching driver stuff via udev just doesn't seem to be the proper way to do it. Having a daemon running in the background that listens to HAL events and then starts/kills the xboxdrv should be much cleaner, but so far I haven't bothered looking deeper into it.

What I do at the moment is simply writing a little shell script for each game that starts and stops xboxdrv:

```
#!/bin/sh

xboxdrv --trigger-as-button --force-feedback -s &
XBOXPID=$!

cd "/home/ingo/games/TombRaiderAnniversary/drive_c/Program Files/Tomb Raider - Anniversary"
wine ./tra.exe

kill $XBOXPID
wait $XBOXPID

```

> 2. When simply running the driver without any options (other than button mapping), the stick itself is not recognized in jscalibrator (meaning when I move the stick around, it is not recognized as one of the axis, and I cannot use it in Mame for example).
There shouldn't be a need to run jscalibrator. If you want to test your joystick you should use jstest.

I assume that the stick behaves as dpad, which means that it will come in as 6th and 7th axis, which for many games doesn't work and is perfectly normal. You can use the --dpad-only option to fix that and move the dpad into the first position and still have it behave as axis instead of buttons.

---

### Post by thomzon on 2009-02-07
Hello,

Thanks for your reply. I will try the dpad only option ASAP.

For the driver launch, I actually use the Hori Stick on my Linux Media Center Box only for the Mame emulator.
I did write a script that loads the driver then launch the emulator. It's nice, but here is my ideal scenario:
- When plugging in my joysticks, run a script that stops my Media Center (XBMC), load the drivers, and launch the emulator.
- When unplugging the joysticks, kill the emulator and relaunch XBMC.

I can survive without this, but it would really make the box plug&play, and would be very neat.

How would you go about making this background script ? I do not know anything about HAL events. I am comfortable with programming though, so don't hesitate to throw some technical stuff.

Thanks a lot.

---

### Post by Grumbel on 2009-02-07
> **thomzon said:**
> How would you go about making this background script?
Haven't really looked much into it, but it should be pretty easy, all you have to do is register a callback for DeviceAdd/Remove with HAL and then check if any of that matches a device supported by xboxdrv. Some example scripts that might be helpful (just random stuff found on google, but it seems to go into the right direction):

[http://redclay.altervista.org/wiki/doku.php?id=projects:hal-automount](http://redclay.altervista.org/wiki/doku.php?id=projects:hal-automount)
[http://davyd.livejournal.com/206645.html](http://davyd.livejournal.com/206645.html)

---

### Post by thomzon on 2009-02-07
Thanks! I'll look into it and post any relevant results.

---

### Post by thomzon on 2009-02-08
Hello,

Firstly, thanks for the --dpad-only option, it works like a charm. I can now select and run my games in Mame with my joystick, no need for a mouse/keyboard anymore.

I have put in place the python script in the first link you posted about HAL event listening. I have changed it a little so that it runs one of my script call "usb_added" when an USB device is plugged in. It also calls another script "usb_removed" when it is unplugged. Here is what these scripts do :

usb_added: Checks if it is the first or second Hori Fighting Stick to be plugged in. If it is the first, kill XBMC, load the driver, and launch MAME (of course it first checks if this was already done, in case another USB device is plugged in that is not a Hori Stick). If it is the second Joystick, just load the driver for this one.

usb_removed: If there still are one or more Joystick plugged in, do nothing. Otherwise, kill the drivers, kill MAME, and relaunch XBMC.

I have to tell you, the result is just formidable. I just turn on my TV, plug in my Joystick, and voilà : XBMC stops, MAME launches, the driver is loaded, and I can select and launch the game I want with the joystick. When I'm done, I remove the stick, and XBMC starts again. I then pick up my remote and start my music/photo/video.

If anyone is interested in getting the code of the 3 scripts involved, please just ask.

A very big thank you to Grumbel for his help and suggestions.

---

### Post by Grumbel on 2009-02-09
> **thomzon said:**
> If anyone is interested in getting the code of the 3 scripts involved, please just ask.
Send me (grumbel@gmail.com) what you got, I'll look over it and include it in the next xboxdrv release.

---

### Post by thomzon on 2009-02-09
I will do that with pleasure as soon as able!

---

### Post by zenbachry on 2009-03-11
Uhm...yeah, hi. I have an issue....when I do the scons, before the driver usage, I get an error.

```
benjamin@benjamin-desktop:~/tmp/xboxdrv-linux-0.4.6$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/evdev_helper.o -c -g -O2 -Wall -ansi -pedantic src/evdev_helper.cpp
src/evdev_helper.cpp:19:22: error: X11/Xlib.h: No such file or directory
src/evdev_helper.cpp:590: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:590: error: template argument 1 is invalid
src/evdev_helper.cpp:590: error: template argument 3 is invalid
src/evdev_helper.cpp:590: error: template argument 4 is invalid
src/evdev_helper.cpp:608: error: 'Display' has not been declared
src/evdev_helper.cpp: In constructor 'Keysym2Keycode::Keysym2Keycode()':
src/evdev_helper.cpp:596: error: 'Display' was not declared in this scope
src/evdev_helper.cpp:596: error: 'dpy' was not declared in this scope
src/evdev_helper.cpp:596: error: 'XOpenDisplay' was not declared in this scope
src/evdev_helper.cpp:604: error: 'XCloseDisplay' was not declared in this scope
src/evdev_helper.cpp: In member function 'void Keysym2Keycode::process_keymap(int*)':
src/evdev_helper.cpp:611: error: 'XDisplayKeycodes' was not declared in this scope
src/evdev_helper.cpp:615: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:615: error: 'keymap' was not declared in this scope
src/evdev_helper.cpp:617: error: 'XGetKeyboardMapping' was not declared in this scope
src/evdev_helper.cpp:621: error: 'NoSymbol' was not declared in this scope
src/evdev_helper.cpp:623: error: expected `;' before 'keysym'
src/evdev_helper.cpp:628: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:632: error: 'XFree' was not declared in this scope
src/evdev_helper.cpp: In function 'int xkeysym2keycode(const std::string&)':
src/evdev_helper.cpp:640: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:640: error: expected `;' before 'keysym'
src/evdev_helper.cpp:642: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:642: error: 'NoSymbol' was not declared in this scope
src/evdev_helper.cpp:647: error: 'KeySym' cannot appear in a constant-expression
src/evdev_helper.cpp:647: error: template argument 1 is invalid
src/evdev_helper.cpp:647: error: template argument 3 is invalid
src/evdev_helper.cpp:647: error: template argument 4 is invalid
src/evdev_helper.cpp:647: error: expected initializer before 'i'
src/evdev_helper.cpp:648: error: 'i' was not declared in this scope
src/evdev_helper.cpp:648: error: request for member 'end' in 'sym2code.Keysym2Keycode::mapping', which is of non-class type 'int'
src/evdev_helper.cpp:655: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:655: error: 'XKeysymToString' was not declared in this scope
scons: *** [src/evdev_helper.o] Error 1
scons: building terminated because of errors.

```
And, even when I do it with the version that is used in the very first one, I get basically the same thing.

```
benjamin@benjamin-desktop:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.
```

---

### Post by Grumbel on 2009-03-11
See the README, you have to install:

 apt-get install \
     libboost1.35-dev \
     scons \
     libusb-dev \
     git-core \
     libx11-dev \
     x11proto-core-dev \
     python-dbus

---

### Post by zenbachry on 2009-03-11
I followed the instructions word for word...I even went back to make sure I didn't miss a step...I'll check the readme to make sure there isn't something I didn't miss....

---

### Post by zenbachry on 2009-03-11
Ok, my apologies.  I checked the Readme, and there were somethings that had to be done.  Thank you!

---

### Post by FraggedLocust on 2009-03-14
I had the same problem as zenbachry in his second code sample when running scons on the old driver even after adding the boost libraries and stuff. The new driver, however, had no problems. continuing with install now.

---

### Post by linuxguru1 on 2009-03-14
Uhm... this tool makes the Guitar Hero Controller control the mouse.
I ran Frets on Fire and did the xboxdrv thing at the same time. Then I tried changing controls in FoF, but the X-Ploder controller just kept on controlling the mouse. I found someone else also had this issue in this topic, but no solution was offered...

Help?

---

### Post by Grumbel on 2009-03-14
> **linuxguru1 said:**
> Uhm... this tool makes the Guitar Hero Controller control the mouse.
See the README, its not a issue with xboxdrv, but an issue with Xorg, README contains a list of workarounds.

---

### Post by linuxguru1 on 2009-03-14
Sorry, I seem to be blind... can you quote the part where it gives me the solution?

---

### Post by Grumbel on 2009-03-14
> **linuxguru1 said:**
> Sorry, I seem to be blind... can you quote the part where it gives me the solution?

```

[[ Xorg Trouble ]]
------------------

If you start xboxdrv and instead of having a fully working joystick,
you end up controlling the mouse that might be due to recent changes
in Xorg and its device hotplug handling. There are four workarounds,
the one that involves editing /etc/hal/fdi/policy/preferences.fdi is
the recommont one.

1) Temporary workaround using hal-device
----------------------------------------

Get the device id from hal:

 % hal-find-by-property --key 'info.product' --string 'Xbox Gamepad (userspace driver)'

Then remove the device from hal with:

 % hal-device -r $DEVICEID

2) Temporary workaround using xinput
------------------------------------

Second workaround works with xinput:

 % xinput list
 % xinput set-int-prop $DEVICEID 'Device Enabled' 32 0

3) Permanent woraround using .fdi files
---------------------------------------

The former two workarounds are just temporary and have to be redone
after each start of xboxdrv, the last workaround is a permanent one:

You have to edit:

 /etc/hal/fdi/policy/preferences.fdi

And insert the following lines:

    <match key="input.product" string="Xbox Gamepad (userspace driver)">
      <remove key="input.x11_driver" />
    </match>

4) Permanent workaround by disabling device auto detection
----------------------------------------------------------

A fourth workaround involved disabling the autodetection of Xorg
completly, you can do that by adding the following lines to
/etc/X11/xorg.conf:

Section "ServerFlags"
  Option "AutoAddDevices" "False"
EndSection

Note that without auto detection you will have to manually configure
all your mice and keyborads or your Xorg Server won't start up
properly. So unless you are already familiar with editing Xorg you
better avoid this workaround. Workaround 3) has basically the same
effect, except that auto detection only gets disabled for the single
device it is causing problems.

```

---

### Post by escher on 2009-03-14
> **thomzon said:**
> Hello,

Firstly, thanks for the --dpad-only option, it works like a charm. I can now select and run my games in Mame with my joystick, no need for a mouse/keyboard anymore.

I have put in place the python script in the first link you posted about HAL event listening. I have changed it a little so that it runs one of my script call "usb_added" when an USB device is plugged in. It also calls another script "usb_removed" when it is unplugged. Here is what these scripts do :

usb_added: Checks if it is the first or second Hori Fighting Stick to be plugged in. If it is the first, kill XBMC, load the driver, and launch MAME (of course it first checks if this was already done, in case another USB device is plugged in that is not a Hori Stick). If it is the second Joystick, just load the driver for this one.

usb_removed: If there still are one or more Joystick plugged in, do nothing. Otherwise, kill the drivers, kill MAME, and relaunch XBMC.

I have to tell you, the result is just formidable. I just turn on my TV, plug in my Joystick, and voilà : XBMC stops, MAME launches, the driver is loaded, and I can select and launch the game I want with the joystick. When I'm done, I remove the stick, and XBMC starts again. I then pick up my remote and start my music/photo/video.

If anyone is interested in getting the code of the 3 scripts involved, please just ask.

A very big thank you to Grumbel for his help and suggestions.

First, thanks to both of you, and the guy who wrote the detailed instructions on the first page.  As far as the basics go, I'm up and running and all the inputs are working as expected.  However...

My Linux config knowledge is somewhat lacking.  What exactly do I need to do to get it to run xboxdrv-daemon.py at startup?  I've been poking around with /etc/init.d/ scripts, but nothing seems to be working.

As an aside, I'm attempting to do a similar thing (using the controller for MAME, though not on an Xbox).  Even when I start the xboxdrv by hand and the controller happily has a solid P1 light, running xmame -jt1 says that it can't find any joystick devices.  Any ideas?

Thanks in advance.

---

### Post by Grumbel on 2009-03-14
> **escher said:**
> I've been poking around with /etc/init.d/ scripts, but nothing seems to be working.
The process goes something like this:

$ cp /etc/init.d/skeleton /etc/init.d/xboxdrv
$ vi /etc/init.d/xboxdrv
# edit file to properly start/stop xboxdrv
$ update-rc.d /etc/init.d/xboxdrv defaults

The last step registers the init script so that it is used on boot. You can test it with:

$ /etc/init.d/xboxdrv start
# check if things start
$ /etc/init.d/xboxdrv stop
# check if things stop

I haven't tried to write a proper xboxdrv init script myself, so there might be problems and issues poping up. In general I prefer to simply write wrapper scripts around the applications that use a joystick, to let them start/stop xboxdrv instead of starting it at boot (example for that in the README).

> As an aside, I'm attempting to do a similar thing (using the controller for MAME, though not on an Xbox).  Even when I start the xboxdrv by hand and the controller happily has a solid P1 light, running xmame -jt1 says that it can't find any joystick devices.  Any ideas?
xmame seems to look in the wrong place for a joystick device, this might help:

 $ xmame -jt 1 -jdev /dev/input/js0

---

### Post by escher on 2009-03-14
> **Grumbel said:**
> I haven't tried to write a proper xboxdrv init script myself, so there might be problems and issues poping up. In general I prefer to simply write wrapper scripts around the applications that use a joystick, to let them start/stop xboxdrv instead of starting it at boot (example for that in the README).


xmame seems to look in the wrong place for a joystick device, this might help:

 $ xmame -jt 1 -jdev /dev/input/js0

Come to think of it, that's simpler and works for me.  Thanks for the heads up on the joystick port, too.

One thing of note that you might want to add to the sample script in the README.  I had to throw in a quick sleep between driver init and xmame (in this case) because otherwise the driver hadn't finished loading by the time xmame was fired up.  You've done a great job to make this as friendly as possible, and that's something I could see tripping someone up.

---

### Post by Grumbel on 2009-03-14
> **escher said:**
> One thing of note that you might want to add to the sample script in the README.  I had to throw in a quick sleep between driver init and xmame (in this case) because otherwise the driver hadn't finished loading by the time xmame was fired up. 
Good idea, will do.

---

### Post by Castigate on 2009-03-16
Hi, I've been trying to get my xbox 360 guitar controller to work with frets on fire.  I read this how to carefully and tried it a few times. I've read all the pages of this thread, but I keep getting errors.  I really would appreciate any help.  Unfortunately I have to boot into winblows to play.  If I could get this to work I could be able to ditch windoze :popcorn:  All the steps were successful until I run scons.  Here is the error message get.

scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o helper.o -c -g -O0 -Wall helper.cpp
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

---

### Post by Grumbel on 2009-03-16
> **Castigate said:**
> All the steps were successful until I run scons.  Here is the error message get.
Download the latest version from:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

---

### Post by Castigate on 2009-03-16
Thanks for getting back to me fast.  I got the guitar controller to work with the new driver, but I'm still having problems. The guitar seems to take over my mouse.  I cannot use my mouse when the guitar is enabled.  I also cannot use the guitar in frets on fire.  I don't know if it makes a difference but I'm using fofix.   I can use the keyboard to try and change control to guitar, but the guitar is not detected in frets on fire. Any Ideas?

---

### Post by Grumbel on 2009-03-16
> **Castigate said:**
> Any Ideas?
See README of xboxdrv and a few posts up in this thread, its an issue with Xorg.

---

### Post by Castigate on 2009-03-16
I did read the posts in this thread and I read the how-to and readme file.  I still can't get the guitar to work in FOF.  I guess it's too complicated for me.  I'll have to dual boot until I can figure out the problem:(.  Thanks for you help.

---

### Post by hellhere on 2009-05-04
I was irritated at having to use sudo to run this driver.  If you feel the same way, you can create a udev rule to apply whatever permissions you want to the uinput device and the {whatever usb device your controller is} device. 

```
# xboxdrv
# Gives 660 permissions to the uinput device, and I guess hopefully any Xbox 
# 360 controller.  And sticks both in the plugdev group.

BUS=="usb", SYSFS{idVendor}=="045e", SYSFS{idProduct}=="028e", MODE="0660", GROUP="plugdev"
KERNEL=="uinput", MODE="0660", GROUP="plugdev"
```

I saved that (as root) as **45-permissions-xboxdrv.rules** in **/etc/udev/rules.d/** .

What it does is give the permissions specified by **MODE=""** and the group specified by **GROUP=""** to the device files.  So in the example above, it gives read/write permissions to root (which is still the owner) and the plugdev group.

The thing that you will have to change for your particular controller are the **SYSFS{idVendor}** and **SYSFS{idProduct}** comparisons.  For my (wired) controller, I was able to get those values just from **lsusb** :

```
Bus 001 Device 005: ID _**045e:028e**_ Microsoft Corp. Xbox360 Controller
```


Just thought I would share.  I should warn you that I have no idea if this is a 'smart' thing to do in the linuxdork sense.

---

### Post by Grumbel on 2009-05-04
> **hellhere said:**
> I was irritated at having to use sudo to run this driver.
Yep, noticed that too. Something changed between the last Ubuntu and the new one, in the last one it used worked fine as user (when in group 'root'), in the new one it doesn't, as the device is no longer readable for root group members.

USB devices themselves still are 660,root:root so the first line shouldn't be needed if one is in group root.

I'll add it to the xboxdrv docu.

---

### Post by hellhere on 2009-05-06
Thanks for making this driver, by the way.  I appreciate it :)

---

### Post by keypox on 2009-06-18
This guide seems to be dated some if helpful though?  OR just doesnt work but i think instructions from the readme work. 

You need to install this 

apt-get install \
     libboost1.35-dev \
     scons \
     libusb-dev \
     git-core \
     libx11-dev \
     x11proto-core-dev \
     python-dbus

Unload everything like in guide or in readme from driver.  Then scons

But not sure if im having issues or its supposed to do this but if no buttons are pressed a get this repeating over and over:

Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data: 
Unknown: len: 0 data:


Also J2b_Right things its allways pressed.  Anyone know how to fix this?

---

### Post by Grumbel on 2009-06-18
> **keypox said:**
> But not sure if im having issues or its supposed to do this but if no buttons are pressed a get this repeating over and over:

Unknown: len: 0 data: 
Thats normal, I'll filter it out in the next release.

---

### Post by Rigorous on 2009-06-19
USB Device:        004:004
Controller:        "RedOctane Guitar Hero X-plorer" (idVendor: 0x1430, idProduct: 0x4748)
Controller Type:   Xbox360 Guitar
Deadzone:          0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled
Exception: Error couldn't claim the USB interface: Operation not permitted
Try to run 'rmmod xpad' and start xboxdrv again.

I run "sudo rmmod xpad" and started xboxdrv again and i get the same error, i even blacklisted xpad and what do i do now?

Edit:I ran xboxdrv as sudo and i got something..uhh...new:

 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  4032 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  4032 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3696 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  4032 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  4032 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  4032 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3696 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3696 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  4032 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3864 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 
 whammy:-26651 tilt:  3696 | up:0 down:0 left:0 right:0 | back:0 guide:0 start:0 | green:0 red:0 yellow:0 blue:0 orange:0 

Just spams up the screen and i pressed Ctrl+C and it stopped(thankfully i remembered this combination from reading through!!) I read you have to type "-s" so i tried to quickly type it in but it was spamming up the box too fast that i couldn't type it in and i managed to get it in and it just kept spamming away? I can't move my mouse away from it to try out if my guitar works.

I have been at this from 8:00pm until 1:27 AM. Any help in absolute beginner terms I would be soooo greatful! I'm going to sleep hope someone helps :(

---

### Post by keypox on 2009-06-19
> **Grumbel said:**
> Thats normal, I'll filter it out in the next release.

ok cool

what about one of the joysticks always thinking its being pressed?  I had this driver working better on previous install.  Dunno what i did differently 

Thanks for the word

---

### Post by Grumbel on 2009-06-19
> **Rigorous said:**
> Edit:I ran xboxdrv as sudo and i got something..uhh...new:
The running as root thing is a problem with the current Ubuntu version, as users no longer have access to uinput, there are workarounds, but its easiest to just run:

sudo ./xboxdrv -s

The '-s' goes on the command line, it can't be typed after xboxdrv is already running.

You should also check the README of xboxdrv, which contains a lot more information.

---

### Post by Grumbel on 2009-06-19
> **keypox said:**
> what about one of the joysticks always thinking its being pressed?  I had this driver working better on previous install.
Need some more details, what is J2b_Right? Is it xboxdrv that things the button is constantly pressed or an application that is using the joystick device? Does it register presses at all and they get stuck or is it just always pressed?

---

### Post by Rigorous on 2009-06-19
Thank you for the reply grumbel, after doing that i get this:

Starting with uinput... done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event5

Press Ctrl-c to quit

I can't move my mouse away from the terminal after that so do i quit and do something else?

Huh i found out i can move my mouse as i tilt my guitar??
So how am i suppose to use it on a game?
All i can move is up and down, but i want to navigate to the game screen so i can play frets on fire already!

---

### Post by Grumbel on 2009-06-19
> **Rigorous said:**
> [quote]I can't move my mouse away from the terminal after that so do i quit and do something else?
Its a problem with Xorg handling your joystick as mouse, see README, especially the section "Xorg Trouble" for workarounds.

---

### Post by keypox on 2009-06-19
> **Grumbel said:**
> Need some more details, what is J2b_Right? Is it xboxdrv that things the button is constantly pressed or an application that is using the joystick device? Does it register presses at all and they get stuck or is it just always pressed?

oh sorry, i guess lack of details would be a problem. 

I am running epsxe via wine.  And when i setup the controller, it thinks that either one of the joysticks are always pressed in one direction.  

So in game i can only go up or right.  Then Another time up and left. The dpad is not recognized in epsxe. 

I have tried the calibration settings from the readme. But that didnt help.

Here are the commands i tried:
./xboxdrv --deadzone 4000
 % ./xboxdrv --calibration X2=-32768:0:32767

---

### Post by Grumbel on 2009-06-19
> **keypox said:**
> I am running epsxe via wine.  And when i setup the controller, it thinks that either one of the joysticks are always pressed in one direction.
Calibrate won't help you, that is meant for broken controllers. 

Normally deadzone should help, but you already tried that. You could try setting an even larger deadzone. You could also try to rotate all joysticks around before starting the configuration, sometimes they are stuck in default positions. 

Another option might be to by pass whatever GUI epsxe offers and configuring the axis via a psxe config file. 

Another possibility is that psxe gets confused by the analog trigger, this might fix it:

./xboxdrv --trigger-as-button

> The dpad is not recognized in epsxe.
Try: 

./xboxdrv --dpad-as-button

---

### Post by keypox on 2009-06-20
Hey thanks i think dpad-as-button fixed my current issue.... still has the joystick issue mabye program specific.  Doesnt matter i guess :) Cause dpad is working and thats what i want. 

Swweeeet epsxe with 360 controller thanks man!  

If you need any tested done let me know.

EDIT: Its not the joystick its the RT thinks is being held down.  Thats ok i dont think this game even needs thouse.

---

### Post by keypox on 2009-06-21
Next you have to load the uinput kernel module which allows userspace
programms to create input devices and the joydev module which gives
you the /dev/input/jsX device:

 % modprobe uinput
 % modprobe joydev

i dont have a jsX file?  Should i jsut create it in this location? Or i have to run these two every time i reboot.

---

### Post by Grumbel on 2009-06-21
> **keypox said:**
> i dont have a jsX file?  Should i jsut create it in this location? Or i have to run these two every time i reboot.
The jsX file should be automatically created once you start xboxdrv and have a controller plugged in. 

You can insert the two modules into /etc/modules to have them loaded automatically on boot.

---

### Post by keypox on 2009-06-21
> **Grumbel said:**
> The jsX file should be automatically created once you start xboxdrv and have a controller plugged in. 

You can insert the two modules into /etc/modules to have them loaded automatically on boot.

Hmm that file is not created.  And i did add 

# The following two modules are used with the xbox controller driver.
# Added on June 10th, 2008
uinput # for creating userspace drivers. 
joydev # for joystick devices

to /etc/modules  but fro some reason they dont get loaded.  Should i add the command to startup programs?

EDIT: I bet i need sudo in there? I guess I will try that bet that is the problem

---

### Post by Grumbel on 2009-06-21
> **keypox said:**
> Hmm that file is not created.  And i did add
Try it without the comments after the module name (i.e. only the module name on a single line), I think the format of /etc/modules can't handle those.

---

### Post by keypox on 2009-06-22
> **Grumbel said:**
> Try it without the comments after the module name (i.e. only the module name on a single line), I think the format of /etc/modules can't handle those.

k will do...

this dpad as buttons is working great.  Do i have to run the driver like that everytime?  Also anyway to collibrate the controller to be more responsive?  Seems buttons dont always realize input, and sometimes get stuck.  

All minor issues in FF7, but i would imagine for other games this couple be a problem.

---

### Post by Grumbel on 2009-06-22
> **keypox said:**
> this dpad as buttons is working great.  Do i have to run the driver like that everytime?
Yes. There is tools/xboxdrv-daemon.py, which can auto-start the driver when a pad gets plugged in, but in general I recomment starting it manually.

Best thing to do is writting a little wrapper script for your favorite games to start it automatically when the game starts, README contains examples.

> Also anyway to collibrate the controller to be more responsive?  Seems buttons dont always realize input, and sometimes get stuck.
What kind of pad are you using? USB or wireless?

In xboxdrv.cpp there is:

timeout = 25; // FIXME: How long should we wait for a new event?

you can set it to 0, which might fix the problem, but will stop some functions from working (autofire, throttle emulation).

It might also help to increase the priority of the process, like:

sudo nice -n -20 ./xboxdrv

I don't have the problem myself and I am not really sure what is causing it or how to avoid it.

---

### Post by Ashfire908 on 2009-06-29
Hello, has there been any progress with this error?

```
Error: Xbox360Controller: USBError: -2
error submitting URB: No such file or directory
```I have a Xbox 360 Wireless Controller connected to a Desktop via The Play and Charge kit. It has a slightly different id then the normal controller. I attached a patch to the source file I pulled from your git repo with the added controller. I'm not going to go and buy a wireless receiver or a wired controller just to make this work so fixing this error for me (since I'm primarily a console gamer and not a PC gamer) is important. At one point the xpad driver in kernel space supported Xbox 360 Wireless via charge kit, but apparently there was a regression at some point and it no longer works, so this is my only option (since this apparently is active over the kernel driver).

I'm willing to help out with testing. My main system (for which I want to use this on) runs Gentoo 2008.0, though that shouldn't really effect anything. I'm running 2.6.29-gentoo-r5, though if need be I can downgrade and configure the kernel to meet Ubuntu's kernel. Also I have a EEE PC with Ubuntu 9.04 which I could also test this on. I'm fairly available so you can ask me any time and I should shortly be able to do testing for you.

EDIT: I'm also getting this on my Xbox Original controller (the v1).

---

### Post by Grumbel on 2009-06-29
> **Ashfire908 said:**
> I have a Xbox 360 Wireless Controller connected to a Desktop via The Play and Charge kit. It has a slightly different id then the normal controller.
I was always under the assumption that the play&charge kit only gives power to the controller, not data. If that is the case there is nothing that can be done to fix that. 

So first step would be to confirm that it actually is possible in theory and that play&charge does transmit data, so:

1) Does your Xbox360 controller work in Windows?

2) Could you give me the full output of "lsusb -v -d 045e:028f" when the controller is plugged in?

The Xbox(v1) issue might be due to the pad having a different endpoint then the normal Xbox(v1) pad. Again, the output of "lsusb -v" would be needed.

---

### Post by Ashfire908 on 2009-06-29
In Windows XP Pro, when I plugged in the Xbox 360 controller, it correctly identified it as a Xbox 360 Wireless controller with a play and charge kit and installed the driver for that. If it was just taking power there would be no driver being installed (you can pull power bus without asking perfectly fine). I could not get it set up with Microsoft's Xbox 360 controller software or any other way, though I didn't spend much time on it because I'm not trying to get it work on Windows. I do remember though getting it to work on an older version of Ubuntu.

For the USB data, here's the Xbox 360 Wireless controller over the Play and Charge kit:
```
Bus 003 Device 002: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x028f Xbox360 Wireless Controller
  bcdDevice            1.05
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           18
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol    255 
      iInterface              0 
Device Status:     0x0000
  (Bus Powered)
```

And here's the old-style first party original Xbox controller data:
```
Bus 003 Device 004: ID 045e:0202 Microsoft Corp. Xbox Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x045e Microsoft Corp.
  idProduct          0x0202 Xbox Controller
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        88 
      bInterfaceSubClass     66 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by Grumbel on 2009-06-29
> **Ashfire908 said:**
> I could not get it set up with Microsoft's Xbox 360 controller software or any other way,
That, along with the lsusb log, which doesn't show any endpoints from which one could receive data, further confirms that Play&Charge does only work for power, but not data. So unless you can make it work in Windows I have to assume that it just doesn't work with Play&Charge.

> And here's the old-style first party original Xbox controller data:
As expected it seems to be an endpoint problem, for the moment you can work around it by eding src/xbox_controller.cpp line 71 and changing:

int ret = usb_interrupt_read(handle, 1 /*EndPoint*/, (char*)data, sizeof(data), timeout);

to:

int ret = usb_interrupt_read(handle, 2 /*EndPoint*/, (char*)data, sizeof(data), timeout);

(i.e. the 1 to a 2), then recompile.

---

### Post by Ashfire908 on 2009-06-30
> **Grumbel said:**
> So unless you can make it work in Windows I have to assume that it just doesn't work with Play&Charge.

I'll find the version of Ubuntu that had xpad that worked with it.

> **Grumbel said:**
> As expected it seems to be an endpoint problem, for the moment you can work around it by eding src/xbox_controller.cpp line 71 and changing:

int ret = usb_interrupt_read(handle, 1 /*EndPoint*/, (char*)data, sizeof(data), timeout);

to:

int ret = usb_interrupt_read(handle, 2 /*EndPoint*/, (char*)data, sizeof(data), timeout);

(i.e. the 1 to a 2), then recompile.

Yeah, that fixed it. Maybe you could autodetect this so a code change and recompile is not needed? Also, profiles might be a nice feature to add. And while I'm at it, is there a way to set a null zone or is that not possible?

EDIT: Never mind, deadzone performs the function of a nullzone (sorry if I'm using the wrong terminology).

---

### Post by Ashfire908 on 2009-07-02
I'm working on a profile wrapper script that will let people set up profiles for games and then be able just to run "./xboxdrvwrap -p nexuiz" or something similar. I should be done within the next day or two. Meanwhile, I attached a patch (for the current git sources) that will supress the Token: debug messages.

---

### Post by dlzerocool on 2009-07-16
This driver is great, but sadly it's not built as a kernel driver, I mean, this driver really works better than the old xpad driver who as been written 2 years ago.

I really hope this driver will get better and will get built in kernel
with all the features and support that this driver deserve.

---

### Post by essence25 on 2009-10-15
I have a question in regards to the xboxdrv/src/uinput.o module that gets compiled/created with xboxdrv, it seems like it does not actually load... 

When we do modprobe uinput it loads the module from eg.:
/lib/modules/2.6.28-15-generic/kernel/drivers/input/misc/uinput.ko

Which is basically the old uinput module that comes with the kernel...

How can we make the new xboxdrv/src/uinput.o into uinput.ko and load in in the kernel?

Or this module is embedded into the "xboxdrv" executable? then why we still need the uinput.ko from kernel? We can still run xboxdrv with: --no-uinput flag and it still works without the uinput.ko module loaded.

Hope I'm making sense here, as I'm new to programming/compiling etc...:-)

Can someone clarify....

---

### Post by Grumbel on 2009-10-15
xboxdrv/src/uinput.o and ../input/misc/uinput.ko are completly different files. xboxdrv/src/uinput.o is simply the part of xboxdrv that talks to the uinput kernel module.

---

### Post by essence25 on 2009-10-15
> **Grumbel said:**
> xboxdrv/src/uinput.o and ../input/misc/uinput.ko are completly different files. xboxdrv/src/uinput.o is simply the part of xboxdrv that talks to the uinput kernel module.
 
 
Great that is what I speculated. That clears it for me. Thanks...

---

### Post by gekados on 2009-11-13
Hi.
 
I'm having problems with uinput.. Seems like it's placing itself in /dev/uinput and not /dev/input/uinput as it should...
How can I configure either uinput or driver to match each other ?
 
>  
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <[EMAIL="grumbel@gmx.de"]grumbel@gmx.de[/EMAIL]>
License GPLv3+: GNU GPL version 3 or later <[http://gnu.org/licenses/gpl.html](http://gnu.org/licenses/gpl.html)>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
USB Device:        002:005
Controller:        "Logitech Xbox Cordless Controller" (idVendor: 0x046d, idProduct: 0xca84)
Controller Type:   Xbox Classic
Deadzone:          0
Trigger Deadzone:  0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled
Starting with uinput... Error: /dev/input/uinput: No such file or directory
done
Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event5
Press Ctrl-c to quit


 
Great forum by the way, learned a lot in here since i started my long and glorious endavour into linux (about 4 days ago, hehe) :)

---

### Post by Grumbel on 2009-11-14
> **gekados said:**
> I'm having problems with uinput.. Seems like it's placing itself in /dev/uinput and not /dev/input/uinput as it should...
xboxdrv is trying "/dev/input/uinput", "/dev/uinput" and "/dev/misc/uinput", the (slightly confusing) error message just indicates that the first one failed and it goes to the next one.

If xboxdrv isn't working for you, you have to look elsewhere for a problem (see README for common issues and ways to debug things).

---

### Post by gekados on 2009-11-14
Thank you !
 
It definately worked anyway. Just had to add a Keymap.xml in my /userdata/Keymaps folder. Before loading xboxdrv it took keymap from /usr/share/ ..
 
Edited my keymap and now everything is smooooth :)

---

### Post by truthseer0 on 2009-11-15
sorry if i shouldn't be posting here for some reason, but i'm using the xboxdrv and a Madcatz wired 360 controller. i have everything working smoothly except for one thing, joystick as mouse. i've gotten it working for games, but now i want an over-glorified mouse. everything is seemly set right and i've tried everything, and i think its a problem with uinput and mouse events just not liking each other ;) . has anyone gotten this to work? joystick controlling the mouse?
xpad won't do it for me and xboxdrv will make the mouse JUMP to a new place, where it should be, *after* i jiggle my *real* mouse. 
i can add my current script if you want if you think it'll help. 
thank you, in advance for any responses

---

### Post by Grumbel on 2009-11-15
> **truthseer0 said:**
> i've gotten it working for games, but now i want an over-glorified mouse.
Have you tried the snipped from the README?

```
./xboxdrv \
  --axismap -y2=y2 \
  --ui-axismap x1=REL_X,y1=REL_Y,y2=REL_WHEEL:3:50 \
  --ui-buttonmap a=BTN_LEFT,b=BTN_RIGHT,x=BTN_MIDDLE,y=KEY_ENTER \
  --ui-buttonmap rb=KEY_FORWARD,lb=KEY_BACK \
  --ui-buttonmap dl=KEY_LEFT,dr=KEY_RIGHT,du=KEY_UP,dd=KEY_DOWN \
  -s --deadzone 5000  --dpad-as-button

```

---

### Post by truthseer0 on 2009-11-16
yes i have, let me attach my current script to get it working.

```
#!/bin/bash
gksudo modprobe uinput
sudo modprobe joydev
sleep 1s
sudo xboxdrv --name XboxKeypad --type xbox360 --device-by-id 0x1bad:0xf016 -s --deadzone 2500 --deadzone-trigger 250 --dpad-as-button --trigger-as-button --axismap -y2=y2 --ui-axismap x1=REL_X,y1=REL_Y,y2=REL_WHEEL:3:50 --ui-buttonmap a=KEY_PLAYPAUSE,b=KEY_ESC,x=KEY_CALC,y=XK_F4,rb=KEY_LEFTALT,lb=KEY_LEFTCTRL,dl=KEY_LEFT,dr=KEY_RIGHT,du=KEY_UP,dd=KEY_DOWN,lt=KEY_PREVIOUSSONG,rt=KEY_NEXTSONG,guide=KEY_MEDIA,start=KEY_HOMEPAGE,back=KEY_MAIL,tl=XK_Tab,tr=KEY_ENTER
```
running Ubuntu 9.10 Karmic Koala. 
tried every bloody thing i can think of including editing xorg.conf and messing with fdi files.

---

### Post by truthseer0 on 2009-11-18
can someone at least post and tell me to give up? :(...

---

### Post by Grumbel on 2009-11-18
> **truthseer0 said:**
> can someone at least post and tell me to give up? :(...
Just tried it myself and it does in fact not work. Mouse wheel, keyboard and such work, but moving the pointer doesn't. evtest shows that X,Y events are properly registered and "xinput list" shows that the device is recognized by Xorg.

Only difference I see between the xboxdrv device and a real mouse is that the real mouse generates these events:

Event: time 1258550716.624580, type 0 (Reset), code 0 (Reset), value 0

Which xboxdrv doesn't. Not sure what they do.

---

### Post by Grumbel on 2009-11-18
> **truthseer0 said:**
> can someone at least post and tell me to give up? :(...
Try the latest version from Git:

 git clone [http://pingus.seul.org/~grumbel/xboxdrv.git](http://pingus.seul.org/~grumbel/xboxdrv.git)

Added a fix that sends out (EV_SYN, SYN_REPORT), mouse emulation now kind of works, but still feels a bit broken. When moving around in large circles it works as expected, but when moving only on X or Y axis it seems slow and sluggish. Might be related to the input system eating up duplicate events:

[http://www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/drivers/input/mousedev.c#L383](http://www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/drivers/input/mousedev.c#L383)

Edit: Tweaking the VALUE and REPEAT options makes the sluggishness get smaller, but not completly disappear:

```
--ui-axismap x1=REL_X:10:20,y1=REL_Y:10:20
```

---

### Post by truthseer0 on 2009-11-18
thank you very much. i had tried everything i could think of that could POSSIBLY help and hadn't. checked xev and it wasn't sending the events until real mouse was moved so it'd jump.
thank you for the update, and i'll download it now and post back/edit back whether it works for me or not.
TY TY TY TY TY ^_^ you've made a very happy kid, because i've been working on this for a month trying everything both i and two of my friends could think of.

---

### Post by truthseer0 on 2009-11-18
hmm... well i git cloned it and built with scons and it didn't return any errors, and now the stick doesn't even make the cursor jump. and i'm tired, no ideas, this is way out of my ballpark now. can you help Grumbel? is it merely because my controller is a Madcatz and not a normal microsoft wired controller?

---

### Post by Grumbel on 2009-11-18
> **truthseer0 said:**
> can you help Grumbel?
Try the config from the README again, that should work. Your config doesn't, because a mouse needs buttons to be recognized by Xorg as mouse device, so you need to add something like:

--ui-buttonmap a=BTN_LEFT

> is it merely because my controller is a Madcatz and not a normal microsoft wired controller?
No, that has nothing to do with this.

---

### Post by truthseer0 on 2009-11-18
ahhh works perfectly now! i forgot i had changed the buttons around after having given up on making it work as a mouse. thank you very much! now i just need to go back and rethink the overall layout of this thing. 

... is there any chance i can use it as a chorded keyboard? just btw, if you don't mind answering

thank you for all the help, and the update to the driver, and the advice

Sincerely,
truthseer0

---

### Post by Grumbel on 2009-11-18
> **truthseer0 said:**
> is there any chance i can use it as a chorded keyboard?
No, that would require some programming as the current code isn't flexible enough to handle key combinations.

---

### Post by truthseer0 on 2009-11-18
ah alright. didn't think so but doesn't hurt to ask. once again, thank you for all your help.

---

### Post by dahuey on 2009-11-19
hi all

ive been trying to get a xbox 360 wirless controller setup.
im all set, i compiled, launched the driver through putty as root.
i dont know if its to do with the driver or keymap.xml but im having problems with the triggers and analog sticks.

after i have launched the driver i can scroll up or down in a list with the left or right trigger but only up or down. if i go up then it works as per usual but as soon as i pull the trigger to go down both triggers stop working and i cannot go up or down. 
it seems that this issue also effects the right analog stick.
after starting the driver i can use the volume up or down all the time until i use the triggers, after that it wont register the right analog stick at all.

ive tried changing the deadzone from 3000 to 4000 to 12000 to 18000 but no dice, it doesnt help.
this is my driver startup command

```
./xboxdrv --dpad-as-button --deadzone 12000
```this is my keymap.xml file

[http://www.filedropper.com/keymap](http://www.filedropper.com/keymap)

any help would be great as i bought the controller just for trigger scrolling.
cheers

---

### Post by T1z3R on 2009-11-19
> **Ashfire908 said:**
> I'm working on a profile wrapper script that will let people set up profiles for games and then be able just to run "./xboxdrvwrap -p nexuiz" or something similar. I should be done within the next day or two. Meanwhile, I attached a patch (for the current git sources) that will supress the Token: debug messages.

did you get the 360 controller working with the play & charge kit?

ive used it successfully in vista to play GTA but put off trying to set it up in ubuntu as almost every thread i read said it wasnt supported·

---

### Post by Grumbel on 2009-11-19
> **dahuey said:**
> any help would be great as i bought the controller just for trigger scrolling.
Have a look at --trigger-as-button and --trigger-as-zaxis one of those should solve your problem, which one depends on if you need axis or button events.

---

### Post by Grumbel on 2009-11-19
> **T1z3R said:**
> did you get the 360 controller working with the play & charge kit?
The controller does not work with play&charge, as play&charge only provides power, not data. You need the Xbox360 Wireless Receiver to have the wireless controller working on the PC.

> ive used it successfully in vista to play GTA
You might be confusing things. Play&charge shouldn't work on Windows either, as again, its just power, not data. 

If for some reason it does in fact work and my information is wrong, I would be very interested in some USB protocol dumps, as those should make it rather easy to get the thing working in Linux.

---

### Post by T1z3R on 2009-11-20
the only thing thats ever confused me is why people have reported that the play and charge kit doesnt work in windows. ive used it to play a handful of games. ive never had a wired controller or a wireless receiver (that i can remember at least lol) so im not sure why no one has had it working.

to be certain, and not to waste anyones times getting their hopes up, ill plug my wireless controller into my Vista machine via my play & charge kit tonight when i get home from work and will post up to confirm.

good work on the driver though...even if i cant get my wireless controller working with the play & charge kit ill certainly be picking up a wired one or a wireless receiver to make use of it in ubuntu :p

---

### Post by Grumbel on 2009-11-20
> **T1z3R said:**
> to be certain, and not to waste anyones times getting their hopes up, ill plug my wireless controller into my Vista machine via my play & charge kit tonight when i get home from work and will post up to confirm.
If you have success the next step would be do get a protocol dump, which can be done with (GUI is rather straight forward to use):

[http://www.usblyzer.com/](http://www.usblyzer.com/)

And the output of 'lsusb -v' in Linux would also be useful.

---

### Post by echotone on 2009-11-20
Does it matter what kind of xbox360 wired controller it is? I have one from gamestop. And pardon the newbie-ness but if it will work, can somebody please pm me and walk me through it? 9.10 doesnt pick it up as a mouse but it lights up 1/4 of the xbox light. (and changes to the next sequential number every time it is plugged in)

---

### Post by dahuey on 2009-11-22
> **Grumbel said:**
> Have a look at --trigger-as-button and --trigger-as-zaxis one of those should solve your problem, which one depends on if you need axis or button events.

yeah ive tried both those commands without success.

--trigger-as-button doesnt let me scroll through list with the triggers. it also changes the left trigger into the back button for some reason. whereas the right trigger essentially does nothing. start stays the same.

--trigger-as-zaxis doesn't work as well. it turns the right analog stick left and right into volume instead of up and down, its also reversed. so left it volume up right is volume down.
right analog stick down is fast forward by x4 for a small deviation from the center and goes to 32x for all the way down. the triggers don't work at all.

im pretty sure it has something to do with the keymap.xml that im using but i have no idea what, or how to change it.

any help would be amazing.
cheers

---

### Post by John Forseti on 2009-12-06
It seems to install the driver fine, but when I run I get this;

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo ./xboxdrv --wid 0 
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        002:004
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Trigger Deadzone:  0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled
Error: Error couldn't claim the USB interface: Device or resource busy
Try to run 'rmmod xpad' and start xboxdrv again.
forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ rmmod xpad
ERROR: Removing 'xpad': Operation not permitted

any help?

---

### Post by truthseer0 on 2009-12-06
whenever i get that, it's because it's already running
try a ```
killall xboxdrv
``` and try again.

---

### Post by Grumbel on 2009-12-06
> **John Forseti said:**
> forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ rmmod xpad
ERROR: Removing 'xpad': Operation not permitted
sudo rmmod xpad

---

### Post by John Forseti on 2009-12-07
Okay, I unplugged the controller and restarted;

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo ./xboxdrv --wid 0 
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

No Xbox or Xbox360 controller found

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ killall xboxdrv
xboxdrv: no process found

#I now plug my controller in


forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo ./xboxdrv --wid 0 
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        002:004
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Trigger Deadzone:  0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled
Error: Error couldn't claim the USB interface: Device or resource busy
Try to run 'rmmod xpad' and start xboxdrv again.

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ killall xboxdrv
xboxdrv: no process found

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo rmmod xpad

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo rmmod xpad
ERROR: Module xpad does not exist in /proc/modules

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo ./xboxdrv --wid 0 
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        002:004
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          0
Trigger Deadzone:  0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled

Starting with uinput... Error: /dev/input/uinput: No such file or directory
done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js1
  /dev/input/event6

Press Ctrl-c to quit

Unknown: len: 3 data: 0x02 0x03 0x00 
Headset: noneX1:   695 Y1:  2098  X2: -2191 Y2:   694  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0

---

### Post by John Forseti on 2009-12-07
oh. despite the error message it appears to be working! :D

Was there a guide to getting the headset to work with it aswell? I'd really like to be able to use it as a mic.

---

### Post by truthseer0 on 2009-12-07
sudo killall xboxdrv
sudo rmmod xpad
sudo modprobe uinput
sudo modprobe joydev
sudo xboxdrv
well looking at your output, its a little odd to sort out. a tad confusing must say. that last set of lines there says "hey i'm working" and should spit out what buttons are being pressed and also the joystick location, and then earlier with "starting with uinput" there is what looks like a failure. that's my 2 cents :) i hope grumbel posts in a few min to help more. so the code above is what i think.

---

### Post by truthseer0 on 2009-12-07
> **John Forseti said:**
> oh. despite the error message it appears to be working! :D

Was there a guide to getting the headset to work with it aswell? I'd really like to be able to use it as a mic.

lol i posted too late. and i'm sorry i can't help on that part, but i'm going to keep watching this thread for that answer! i'd love that!! never really thought of it though (don't ask why, i couldn't tell you)

---

### Post by John Forseti on 2009-12-07
> **truthseer0 said:**
> lol i posted too late. and i'm sorry i can't help on that part, but i'm going to keep watching this thread for that answer! i'd love that!! never really thought of it though (don't ask why, i couldn't tell you)

I tried the commands you said to see if it would work without the first error, for the first two commands they gave an error but it was that they were already not running(I'd already ctrl+c'ed out of the earlier bit). The next two didn't present any error messages, just skipped right along like this;

forseti@Forseti:~$ sudo modprobe uinput
forseti@Forseti:~$ sudo modprobe joydev

but the last one gave me trouble;

forseti@Forseti:~$ sudo xboxdrv
sudo: xboxdrv: command not found

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo xboxdrv
sudo: xboxdrv: command not found

---

### Post by truthseer0 on 2009-12-07
forseti@Forseti:~$ sudo xboxdrv
sudo: xboxdrv: command not found

forseti@Forseti:~/tmp/xboxdrv-linux-0.4.9$ sudo xboxdrv
sudo: xboxdrv: command not found[/QUOTE]

sorry, that's because you need to to ./xboxdrv like you were earlier. what i did, i made a softlink for it in /usr/bin
sudo ln -s /usr/bin {insert path of xboxdrv here}
except you want to make sure that it doesn't break... so move it into your home folder instead of tmp, or copy the binary to /usr/bin
also, i made a script for my controller because it isn't automatically recognized. you can do alot with the driver, i have all my media keys on my xbox controller as well as mouse function and a couple of random things like tab and enter, along with alt and control, its quite useful.

---

### Post by isaacmartin13 on 2009-12-15
so I'm a newbie around here and been using ubuntu over the last year, right now I'm running Karmic.
When I get to Step Four of the "how to" I can get past the "scons" camand, i get this
```

satch13@satch13-desktop:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:47: error: 'strerror' was not declared in this scope
uinput.cpp:61: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:61: error: 'exit' was not declared in this scope
uinput.cpp:76: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:76: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:150: error: 'memset' was not declared in this scope
uinput.cpp:151: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:235: error: 'memset' was not declared in this scope
uinput.cpp:236: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:262: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:276: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.
```and my uinput.cpp looks like this

```
/* 
**  Xbox360 USB Gamepad Userspace Driver
**  Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
**
**  This program is free software: you can redistribute it and/or modify
**  it under the terms of the GNU General Public License as published by
**  the Free Software Foundation, either version 3 of the License, or
**  (at your option) any later version.
**
**  This program is distributed in the hope that it will be useful,
**  but WITHOUT ANY WARRANTY; without even the implied warranty of
**  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
**  GNU General Public License for more details.
**
**  You should have received a copy of the GNU General Public License
**  along with this program.  If not, see <http://www.gnu.org/licenses/>.
*/

#include <assert.h>
#include <stdexcept>
#include <iostream>
#include <errno.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <linux/uinput.h>
#include "xboxmsg.hpp"
#include "uinput.hpp"
#include <stdint.h>
#include <stdio.h>

uInput::uInput(GamepadType type, uInputCfg config_)
  : fd(-1), config(config_)
{
  // Open the input device
  const char* uinput_filename[] = { "/dev/input/uinput", "/dev/uinput", "/dev/misc/uinput" };
  const int uinput_filename_count = (sizeof(uinput_filename)/sizeof(char*));

  for (int i = 0; i < uinput_filename_count; ++i) 
    {
      if ((fd = open(uinput_filename[i], O_WRONLY | O_NDELAY)) >= 0)
        {
          break;
        }
      else
        {
          std::cout << "Error: " << uinput_filename[i] << ": " << strerror(errno) << std::endl;
        }
    }

  if (fd < 0)
    {
      std::cout << "Error: No stuitable uinput device found" << std::endl;
      std::cout << "" << std::endl;
      std::cout << "Troubleshooting:" << std::endl;
      std::cout << "  * make sure uinput kernel module is loaded " << std::endl;
      std::cout << "  * make sure joydev kernel module is loaded " << std::endl;
      std::cout << "  * make sure you have permissions to access the uinput device" << std::endl;
      std::cout << "  * start the driver with ./xboxdrv -v --no-uinput to see if the driver itself works" << std::endl;
      std::cout << "" << std::endl;
      exit(EXIT_FAILURE);
    }
  else
    {
      if (type == GAMEPAD_XBOX360 || type == GAMEPAD_XBOX || type == GAMEPAD_XBOX360_WIRELESS)
        {
          setup_xbox360_gamepad(type);
        }
      else if (type == GAMEPAD_XBOX360_GUITAR) 
        {
          setup_xbox360_guitar();
        }
      else
        {
          std::cout << "Unhandled type: " << type << std::endl;
          exit(EXIT_FAILURE);
        }

      if (ioctl(fd, UI_DEV_CREATE))
        {
          throw std::runtime_error("Unable to create UINPUT device.");
        }
    }
}

void
uInput::setup_xbox360_gamepad(GamepadType type)
{
  ioctl(fd, UI_SET_EVBIT, EV_ABS);
  ioctl(fd, UI_SET_EVBIT, EV_KEY);

  ioctl(fd, UI_SET_ABSBIT, ABS_X);
  ioctl(fd, UI_SET_ABSBIT, ABS_Y);

  if (!config.dpad_only)
    {  
      ioctl(fd, UI_SET_ABSBIT, ABS_RX);
      ioctl(fd, UI_SET_ABSBIT, ABS_RY);
    }

  if (config.trigger_as_button)
    {
      ioctl(fd, UI_SET_KEYBIT, BTN_TL2);
      ioctl(fd, UI_SET_KEYBIT, BTN_TR2);
    }
  else if (config.trigger_as_zaxis)
    {
      ioctl(fd, UI_SET_ABSBIT, ABS_Z);
    }
  else
    {
      ioctl(fd, UI_SET_ABSBIT, ABS_GAS);
      ioctl(fd, UI_SET_ABSBIT, ABS_BRAKE);
    }

  if (!config.dpad_only)
    {
      if (!config.dpad_as_button)
        {
          ioctl(fd, UI_SET_ABSBIT, ABS_HAT0X);
          ioctl(fd, UI_SET_ABSBIT, ABS_HAT0Y);
        }
      else
        {
          ioctl(fd, UI_SET_KEYBIT, BTN_BASE);
          ioctl(fd, UI_SET_KEYBIT, BTN_BASE2);
          ioctl(fd, UI_SET_KEYBIT, BTN_BASE3);
          ioctl(fd, UI_SET_KEYBIT, BTN_BASE4);
        }
    }

  ioctl(fd, UI_SET_KEYBIT, BTN_START);
  ioctl(fd, UI_SET_KEYBIT, BTN_SELECT);
        
  if (type == GAMEPAD_XBOX360 || type == GAMEPAD_XBOX360_WIRELESS)
    ioctl(fd, UI_SET_KEYBIT, BTN_MODE);

  ioctl(fd, UI_SET_KEYBIT, BTN_A);
  ioctl(fd, UI_SET_KEYBIT, BTN_B);
  ioctl(fd, UI_SET_KEYBIT, BTN_X);
  ioctl(fd, UI_SET_KEYBIT, BTN_Y);

  ioctl(fd, UI_SET_KEYBIT, BTN_TL);
  ioctl(fd, UI_SET_KEYBIT, BTN_TR);

  ioctl(fd, UI_SET_KEYBIT, BTN_THUMBL);
  ioctl(fd, UI_SET_KEYBIT, BTN_THUMBR);

  struct uinput_user_dev uinp;
  memset(&uinp,0,sizeof(uinp));
  strncpy(uinp.name, "Xbox Gamepad (userspace driver)", UINPUT_MAX_NAME_SIZE);
  uinp.id.version = 0;
  uinp.id.bustype = BUS_USB;
  uinp.id.vendor  = 0x045e; // FIXME: this shouldn't be hardcoded
  uinp.id.product = 0x028e;

  if (config.dpad_only)
    {
      uinp.absmin[ABS_X] = -1;
      uinp.absmax[ABS_X] =  1;
      
      uinp.absmin[ABS_Y] = -1;
      uinp.absmax[ABS_Y] =  1;
    }
  else
    {
      uinp.absmin[ABS_X] = -32768;
      uinp.absmax[ABS_X] =  32767;

      uinp.absmin[ABS_Y] = -32768;
      uinp.absmax[ABS_Y] =  32767;
    
      uinp.absmin[ABS_RX] = -32768;
      uinp.absmax[ABS_RX] =  32767;
      
      uinp.absmin[ABS_RY] = -32768;
      uinp.absmax[ABS_RY] =  32767;
    }

  if (config.trigger_as_zaxis)
    {
      uinp.absmin[ABS_Z] = -255;
      uinp.absmax[ABS_Z] =  255;         
    }
  else if (!config.trigger_as_button)
    {
      uinp.absmin[ABS_GAS] = 0;
      uinp.absmax[ABS_GAS] = 255;

      uinp.absmin[ABS_BRAKE] = 0;
      uinp.absmax[ABS_BRAKE] = 255;
    }
      
  if (!config.dpad_as_button && !config.dpad_only)
    {
      uinp.absmin[ABS_HAT0X] = -1;
      uinp.absmax[ABS_HAT0X] =  1;

      uinp.absmin[ABS_HAT0Y] = -1;
      uinp.absmax[ABS_HAT0Y] =  1;
    }

  write(fd, &uinp, sizeof(uinp));
}

void
uInput::setup_xbox360_guitar()
{
  ioctl(fd, UI_SET_EVBIT, EV_ABS);
  ioctl(fd, UI_SET_EVBIT, EV_KEY);
        
  // Whammy and Tilt
  ioctl(fd, UI_SET_ABSBIT, ABS_X);
  ioctl(fd, UI_SET_ABSBIT, ABS_Y);

  // Dpad
  ioctl(fd, UI_SET_KEYBIT, BTN_BASE);
  ioctl(fd, UI_SET_KEYBIT, BTN_BASE2);
  ioctl(fd, UI_SET_KEYBIT, BTN_BASE3);
  ioctl(fd, UI_SET_KEYBIT, BTN_BASE4);

  // Base
  ioctl(fd, UI_SET_KEYBIT, BTN_START);
  ioctl(fd, UI_SET_KEYBIT, BTN_SELECT);
  ioctl(fd, UI_SET_KEYBIT, BTN_MODE);

  // Fret button
  ioctl(fd, UI_SET_KEYBIT, BTN_1);
  ioctl(fd, UI_SET_KEYBIT, BTN_2);
  ioctl(fd, UI_SET_KEYBIT, BTN_3);
  ioctl(fd, UI_SET_KEYBIT, BTN_4);
  ioctl(fd, UI_SET_KEYBIT, BTN_5);

  struct uinput_user_dev uinp;
  memset(&uinp,0,sizeof(uinp));
  strncpy(uinp.name, "Xbox360 Guitar (userspace driver)", UINPUT_MAX_NAME_SIZE);
  uinp.id.version = 0;
  uinp.id.bustype = BUS_USB;
  uinp.id.vendor  = 0x045e; // FIXME: Shouldn't be hardcoded
  uinp.id.product = 0x028e;

  uinp.absmin[ABS_X] = -32768;
  uinp.absmax[ABS_X] =  32767;

  uinp.absmin[ABS_Y] = -32768;
  uinp.absmax[ABS_Y] =  32767;

  
  write(fd, &uinp, sizeof(uinp));  
}

uInput::~uInput()
{
  ioctl(fd, UI_DEV_DESTROY);
  close(fd);
}

void
uInput::send_button(uint16_t code, int32_t value)
{
  struct input_event ev;      
  memset(&ev, 0, sizeof(ev));

  gettimeofday(&ev.time, NULL);
  ev.type  = EV_KEY;
  ev.code  = code;
  ev.value = (value>0) ? 1 : 0;

 write(fd, &ev, sizeof(ev));
}

void
uInput::send_axis(uint16_t code, int32_t value)
{
  struct input_event ev;      
  memset(&ev, 0, sizeof(ev));

  gettimeofday(&ev.time, NULL);
  ev.type  = EV_ABS;
  ev.code  = code;
  ev.value = value;

 write(fd, &ev, sizeof(ev));  
}

void
uInput::send(XboxGenericMsg& msg)
{
  switch(msg.type)
    {
      case GAMEPAD_XBOX:
      case GAMEPAD_XBOX_MAT:
        send(msg.xbox);
        break;

      case GAMEPAD_XBOX360:
      case GAMEPAD_XBOX360_WIRELESS:
        send(msg.xbox360);
        break;

      case GAMEPAD_XBOX360_GUITAR:
        send(msg.guitar);
        break;
        
      default:
        std::cout << "XboxGenericMsg type: " << msg.type << std::endl;
        assert(!"uInput: Unknown XboxGenericMsg type");
    }
}

void
uInput::send(Xbox360Msg& msg)
{
  send_button(BTN_THUMBL,  msg.thumb_l);
  send_button(BTN_THUMBR,  msg.thumb_r);

  send_button(BTN_TL,  msg.lb);
  send_button(BTN_TR,  msg.rb);

  send_button(BTN_START,  msg.start);
  send_button(BTN_MODE,   msg.guide);
  send_button(BTN_SELECT, msg.back);

  send_button(BTN_A, msg.a);
  send_button(BTN_B, msg.b);
  send_button(BTN_X, msg.x);
  send_button(BTN_Y, msg.y);

  send_axis(ABS_X, msg.x1);
  send_axis(ABS_Y, -msg.y1);

  send_axis(ABS_RX, msg.x2);
  send_axis(ABS_RY, -msg.y2);

  if (config.trigger_as_zaxis)
    {
      send_axis(ABS_Z, (int(msg.rt) - int(msg.lt)));
    }
  else if (config.trigger_as_button)
    {
      send_button(BTN_TL2, msg.lt);
      send_button(BTN_TR2, msg.rt);    
    }
  else
    {
      send_axis(ABS_BRAKE, msg.lt);
      send_axis(ABS_GAS,   msg.rt);
    }
  
  if (config.dpad_as_button && !config.dpad_only)
    {
      send_button(BTN_BASE,  msg.dpad_up);
      send_button(BTN_BASE2, msg.dpad_down);
      send_button(BTN_BASE3, msg.dpad_left);
      send_button(BTN_BASE4, msg.dpad_right);
    }
  else
    {
      uint16_t dpad_x = ABS_HAT0X;
      uint16_t dpad_y = ABS_HAT0Y;
      
      if (config.dpad_only)
        {
          dpad_x = ABS_X;
          dpad_y = ABS_Y;
        }

      if (msg.dpad_up)
        {
          send_axis(dpad_y, -1);
        }
      else if (msg.dpad_down)
        {
          send_axis(dpad_y, 1);
        }
      else
        {
          send_axis(dpad_y, 0);
        }

      if (msg.dpad_left)
        {
          send_axis(dpad_x, -1);
        }
      else if (msg.dpad_right)
        {
          send_axis(dpad_x, 1);
        }
      else
        {
          send_axis(dpad_x, 0);
        }
    }
}

void
uInput::send(XboxMsg& msg)
{
  send_button(BTN_THUMBL,  msg.thumb_l);
  send_button(BTN_THUMBR,  msg.thumb_r);

  send_button(BTN_TL,  msg.white);
  send_button(BTN_TR,  msg.black);

  send_button(BTN_START,  msg.start);
  send_button(BTN_SELECT, msg.back);

  send_button(BTN_A, msg.a);
  send_button(BTN_B, msg.b);
  send_button(BTN_X, msg.x);
  send_button(BTN_Y, msg.y);

  send_axis(ABS_X, msg.x1);
  send_axis(ABS_Y, msg.y1);

  send_axis(ABS_RX, msg.x2);
  send_axis(ABS_RY, msg.y2);

  if (config.trigger_as_zaxis)
    {
      send_axis(ABS_Z, (int(msg.rt) - int(msg.lt)));
    }
  else if (config.trigger_as_button)
    {
      send_button(BTN_TL2, msg.lt);
      send_button(BTN_TR2, msg.rt);
    }
  else
    {
      send_axis(ABS_BRAKE, msg.lt);
      send_axis(ABS_GAS,   msg.rt);
    }

  if (config.dpad_as_button)
    {
      send_button(BTN_BASE,  msg.dpad_up);
      send_button(BTN_BASE2, msg.dpad_down);
      send_button(BTN_BASE3, msg.dpad_left);
      send_button(BTN_BASE4, msg.dpad_right);
    }
  else
    {
      if (msg.dpad_up)
        {
          send_axis(ABS_HAT0Y, -1);
        }
      else if (msg.dpad_down)
        {
          send_axis(ABS_HAT0Y, 1);
        }
      else
        {
          send_axis(ABS_HAT0Y, 0);
        }

      if (msg.dpad_left)
        {
          send_axis(ABS_HAT0X, -1);
        }
      else if (msg.dpad_right)
        {
          send_axis(ABS_HAT0X, 1);
        }
      else
        {
          send_axis(ABS_HAT0X, 0);
        }
    }
}

void
uInput::send(Xbox360GuitarMsg& msg)
{
  send_button(BTN_BASE,  msg.dpad_up);
  send_button(BTN_BASE2, msg.dpad_down);
  send_button(BTN_BASE3, msg.dpad_left);
  send_button(BTN_BASE4, msg.dpad_right);

  send_button(BTN_START,  msg.start);
  send_button(BTN_MODE,   msg.guide);
  send_button(BTN_SELECT, msg.back);

  send_button(BTN_1, msg.green);
  send_button(BTN_2, msg.red);
  send_button(BTN_3, msg.yellow);
  send_button(BTN_4, msg.blue);
  send_button(BTN_5, msg.orange);

  send_axis(ABS_X, msg.whammy);
  send_axis(ABS_Y, msg.tilt);
}

/* EOF */
```Any advice?!

---

### Post by Grumbel on 2009-12-15
> **isaacmartin13 said:**
> Any advice?!
Go to:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

And grab the latest version, yours is very old.

---

### Post by AgentZ86 on 2010-01-01
crap ?

Karmic 9.10 64bit giving me this ?
When using the command 
prompt$ scons

scons: Reading SConscript files ...
Checking for C++ library X11... yes
Checking for C++ library usb... no
libusb must be installed!
agent86@agent86-desktop:~/src/xboxdrv-linux-0.4.9$ scons
scons: Reading SConscript files ...
Checking for C++ library X11... yes
Checking for C++ library usb... yes
Checking for C++ header file boost/thread/thread.hpp... yes
Checking for C++ library boost_thread-mt... yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/arg_parser.o -c -g -O2 -Wall -ansi -pedantic src/arg_parser.cpp
g++ -o src/command_line_options.o -c -g -O2 -Wall -ansi -pedantic src/command_line_options.cpp
g++ -o src/evdev_helper.o -c -g -O2 -Wall -ansi -pedantic src/evdev_helper.cpp
g++ -o src/firestorm_dual_controller.o -c -g -O2 -Wall -ansi -pedantic src/firestorm_dual_controller.cpp
g++ -o src/force_feedback_handler.o -c -g -O2 -Wall -ansi -pedantic src/force_feedback_handler.cpp
g++ -o src/helper.o -c -g -O2 -Wall -ansi -pedantic src/helper.cpp
g++ -o src/linux_uinput.o -c -g -O2 -Wall -ansi -pedantic src/linux_uinput.cpp
g++ -o src/modifier.o -c -g -O2 -Wall -ansi -pedantic src/modifier.cpp
g++ -o src/pretty_printer.o -c -g -O2 -Wall -ansi -pedantic src/pretty_printer.cpp
g++ -o src/saitek_p2500_controller.o -c -g -O2 -Wall -ansi -pedantic src/saitek_p2500_controller.cpp
g++ -o src/uinput.o -c -g -O2 -Wall -ansi -pedantic src/uinput.cpp
src/uinput.cpp: In static member function 'static ButtonEvent ButtonEvent::from_string(const std::string&)':
src/uinput.cpp:70: warning: 'ev.ButtonEvent::type' may be used uninitialized in this function
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
src/usb_read_thread.cpp: In member function 'int USBReadThread::read(uint8_t*, int, int)':
src/usb_read_thread.cpp:70: error: 'memcpy' was not declared in this scope
scons: *** [src/usb_read_thread.o] Error 1
scons: building terminated because of errors.

another try produces this:

scons: Reading SConscript files ...
Checking for C++ library X11... (cached) yes
Checking for C++ library usb... (cached) yes
Checking for C++ header file boost/thread/thread.hpp... (cached) yes
Checking for C++ library boost_thread-mt... (cached) yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
src/usb_read_thread.cpp: In member function 'int USBReadThread::read(uint8_t*, int, int)':
src/usb_read_thread.cpp:70: error: 'memcpy' was not declared in this scope
scons: *** [src/usb_read_thread.o] Error 1
scons: building terminated because of errors.

Looks like it was close, but just didn't complete
Please advise
thanks

---

### Post by Grumbel on 2010-01-01
> **AgentZ86 said:**
> Karmic 9.10 64bit giving me this ?
When using the command
Add:

#include <string.h>

to the file that gives you the error message or wait for a new release (maybe in the next days if I don't forget it).

---

### Post by AgentZ86 on 2010-01-01
> **Grumbel said:**
> Add:

#include <string.h>

to the file that gives you the error message or wait for a new release (maybe in the next days if I don't forget it).

Thanks, I'll try it

I noticed in this thread the topic of adding lines into the xboxdrv.ccp which I thought might be related to my compilation failure since I have a Mad Catz xbox 360, however mine does not actually say that when I do lsusb
Mine says Harmanics Music ?

Anyhow I've seen it suggested in this thread to add to the xboxdrv.cpp

{ GAMEPAD_XBOX360,          0x1bad, 0xf016, "Mad Catz Xbox 360 Controller"   }

But I don't see the xboxdrv.cpp

I see in the input folder a file called xbox360_driver.cpp which has some lines that appear similar
I'm not sure I even need to try this, or exactly where I would add this line in order re-compile as directed in a previous thread.

Anyhow thanks for the response I'll add
#include <string.h>

to the usb_read_thread.cpp file and try to re-compile

Thanks





Thanks again

---

### Post by AgentZ86 on 2010-01-01
> **Grumbel said:**
> Add:

#include <string.h>

to the file that gives you the error message or wait for a new release (maybe in the next days if I don't forget it).

Thanks I added:
#include <string.h>
to the usb_read_thread.cpp file

It completed the compiliation as follows:

scons: Reading SConscript files ...
Checking for C++ library X11... (cached) yes
Checking for C++ library usb... (cached) yes
Checking for C++ header file boost/thread/thread.hpp... (cached) yes
Checking for C++ library boost_thread-mt... (cached) yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
g++ -o src/xbox360_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox360_controller.cpp
src/xbox360_controller.cpp: In member function 'virtual bool Xbox360Controller::read(XboxGenericMsg&, bool, int)':
src/xbox360_controller.cpp:240: warning: dereferencing type-punned pointer will break strict-aliasing rules
src/xbox360_controller.cpp:245: warning: dereferencing type-punned pointer will break strict-aliasing rules
g++ -o src/xbox360_wireless_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox360_wireless_controller.cpp
src/xbox360_wireless_controller.cpp: In member function 'virtual bool Xbox360WirelessController::read(XboxGenericMsg&, bool, int)':
src/xbox360_wireless_controller.cpp:159: warning: dereferencing type-punned pointer will break strict-aliasing rules
g++ -o src/xbox_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox_controller.cpp
src/xbox_controller.cpp: In member function 'virtual bool XboxController::read(XboxGenericMsg&, bool, int)':
src/xbox_controller.cpp:86: warning: dereferencing type-punned pointer will break strict-aliasing rules
g++ -o src/xboxdrv.o -c -g -O2 -Wall -ansi -pedantic src/xboxdrv.cpp
g++ -o src/xboxmsg.o -c -g -O2 -Wall -ansi -pedantic src/xboxmsg.cpp
g++ -o src/xpad_device.o -c -g -O2 -Wall -ansi -pedantic src/xpad_device.cpp
g++ -o xboxdrv src/xboxdrv.o src/xboxmsg.o src/uinput.o src/arg_parser.o src/pretty_printer.o src/helper.o src/modifier.o src/command_line_options.o src/xbox_controller.o src/xpad_device.o src/xbox360_controller.o src/xbox360_wireless_controller.o src/firestorm_dual_controller.o src/saitek_p2500_controller.o src/evdev_helper.o src/linux_uinput.o src/usb_read_thread.o src/force_feedback_handler.o -lX11 -lusb -lboost_thread-mt
scons: done building targets.

So I completed, with some warnings

Anyhow at least I can play with the xboxdrv now and see how things react.

Thanks

P.S
Do you think the adding of the line for xboxdvr.cpp that was referenced would have let the compilation complete or is this not related to my original errors ?

Thanks again

P.S - 2
I am getting this when running silent:

Starting with uinput... Error: /dev/input/uinput: No such file or directory
done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event6

But it does not seem to be causing a problem that I'm aware of ?

What do you think ?

Thanks to all.

---

### Post by AgentZ86 on 2010-01-01
I get the following from sudo ./xboxdrv

No Xbox or Xbox360 controller found
agent86@agent86-desktop:~/src/xboxdrv-linux-0.4.9$ 

I'm guessing something to do with the fact I have a strange controller and not actual XBOX

I'm not sure where to put the vendor ID and type etc.

If you think this could be the problem, please advise

Thanks

---

### Post by AgentZ86 on 2010-01-01
Weeeee

I added this line to the xpad_device.cpp
as directed in the readme.

  { GAMEPAD_XBOX360, 	      0x1bad, 0xf016, "Harmonix Music / MadCat Generic X-Box" },

Recompiled and produced this:
scons: Reading SConscript files ...
Checking for C++ library X11... (cached) yes
Checking for C++ library usb... (cached) yes
Checking for C++ header file boost/thread/thread.hpp... (cached) yes
Checking for C++ library boost_thread-mt... (cached) yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
scons: done building targets.

And sudo ./xboxdrv

I get the console window which indicates my controller is working and I appear to be able to use the controller now

NOW the fun part testing out a game WOOHOO

Thanks Grumble

---

### Post by Grumbel on 2010-01-01
> **AgentZ86 said:**
> I'm not sure where to put the vendor ID and type etc.
src/xpad_device.cpp

There are also command line options when you don't want to edit source, see README

---

### Post by AgentZ86 on 2010-01-01
My notes to self regarding Xbox 360 wired controller
Focused on Karmic Ubuntu 9.10 64 bit
But will also be helpful info for wireless and perhaps other ubuntu versions
Also my notes assumes that xpad has not been installed or attempted to install (if so) then refer to readme to remove/disable it.
These notes are my results from my process with the help of this How To and Grumble's added help in this forum.

---------
Section 1
---------
Subject:
Installing xboxdrv from [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)
And as noted in the Readme file located at:
[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)
---------
Section 2
---------

First edit the file: etc/modules and add these line to make things happen on bootup:

#start here:
# XBOX controller NOTES: 1-1-09
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

# The following two modules are used with the xbox controller driver.
#uinput is for creating userspace drivers. 
#joydev is for joystick devices

uinput
joydev

#end here:

note: if you don't know how to edit and save then you need to go to the terminal and type:
sudo gedit

Then once gedit opens you can select Open and browse to the file for editing
Once your done editing then save the file
---------
Section 3
---------

The readme file is very thorough and indicates the following packages you will need for Ubuntu (see readme file for referrences):

g++ \
     libboost1.37-dev \
     libboost-thread1.37-dev \
     scons \
     libusb-dev \
     git-core \
     libx11-dev \
     x11proto-core-dev \
     python-dbus
---------
Section 4
---------
Readme suggests APT get but I'm a clickety sort of guy so I used synaptic
I searched synaptic and installed this way

Open synaptic from System/Administration/Synaptic Package Manager
search for the following and then right click and mark for installation

g++ (right click and mark for install)
libusb-dev (right click and mark for install)
libboost1.40-all-dev (right click and mark for installation
scons (right click and mark for install)
libx11-dev (right click and mark for install)
x11proto-core-dev (right click and mark for install)
python -dbus (right click and mark for install)
git-core (right click and mark for install) but likely not needed for synaptic or manuall download method
libboost-thread-dev (right click and mark for install)

Then click apply and synaptic will do the rest
---------
Section 5
---------
Now to download,compile and test.
Download the latest file from:
[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

To make things simple and permissions seem ok for me I (created a folder called (src) in my home directory) and put the file I downloaded into the src folder I just created.

Right click the downloaded file and extract here:

So for me the folder will end up being located at xxxuser@xxxuser-desktop:~/src/xboxdrv-linux-0.4.9$

So to navigate to that folder just type at the terminal
cd src/xboxdrv-linux-0.4.9

Now from within the folder you just navigated to type:
scons

The compiling/installing etc will occur (almost there)
---------
Section 6
---------
You may get errors or other things make note of these errors and which file it refers to:

The error I got at first was this:
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
src/usb_read_thread.cpp: In member function 'int USBReadThread::read(uint8_t*, int, int)':
src/usb_read_thread.cpp:70: error: 'memcpy' was not declared in this scope
scons: *** [src/usb_read_thread.o] Error 1
scons: building terminated because of errors.

Grumble suggested to add this line to the indicated file:
#include <string.h>

In my case it was (usb_read_thread.cpp) file
Without knowing much about anything I was able to edit the file
NOTE:You can not save/edit as regular user so you need to run gedit as superuser
So from the terminal I opened gedit with this command:
sudo gedit

Now you can simply navigate to your files you want to edit and open them
In this case I navigated to the file (usb_read_thread.cpp) located in the home/src folder I created

I then added Grumble's suggested line: #include <string.h> to the file
Then clicked save and now back to trying to compile the driver
---------
Section 7
---------
From the terminal again make sure your in the proper location to run scons
If not you need to get back to:xxxuser@xxxuser-desktop:~/src/xboxdrv-linux-0.4.9$

Anyhow then type the command again:
scons

Compiling and install should start
And should end with - done

Now your ready to test your controller by typing
sudo ./xboxdrv

And you should see the console open with language when you move your controller etc.
---------
Section 8
---------
When you run: sudo ./xboxdrv
If you get a message like I did such as:
No Xbox or Xbox360 controller found

In this case you likely have to add a line to the xpad_device.cpp
And re-compile again with the scons command again.

Weeeee it works.
I added this line to the xpad_device.cpp
as directed in the readme.
In my case I had to find the Vendor ID and stuff first

So I did this by typing at the terminial:
lsusb

which shows me this line item which I know is my controller because when I unplug it this line is not there anymore:
So the lsusb in my case produced this line item:

Bus 005 Device 002: ID 1bad:f016 Harmonix Music

So I go to terminal again to add the info to the (xpad_device.cpp) file
I type command:
sudo gedit
I navigate to the xpad_device.cpp file
Add this line right to the top of the list
But I keep the same format as in the file already. I mostly just want to use the ID's that the lsusb produced for me, here is my line that I added and note the (0x1bad, 0xf016) this is the most important part.

{ GAMEPAD_XBOX360, 0x1bad, 0xf016, "Harmonix Music / MadCat Generic X-Box" },

note: -- don't forget the comma at the end or it won't work

Then SAVE the file.
--------
Section 9
--------

Then back to compile again with the scons command
-make sure your still in the proper directory

Once that completes

Then back to testing
sudo ./xboxdrv

And WOW my controller is giving me the computer language in the terminal which indicates it is now working

select: Ctrl+c to stop the driver

Then you can quite down all the computer noise and load the driver with the -s option

like this:
sudo ./xboxdrv -s


NOW for testing out my games and having fun


Vendetta online works really well a bit sensitive, but I will make a change to that as listed in the readme file

I hope this is helpful to someone
Thanks to everyone for all the work on this.

I'm really happy to be able to use the xbox controller

Anyhow I could not do a better job then the original poster, but this was what I could understand at my level so thats what I did.

And it's working

Happy Hacking

---

### Post by manco on 2010-01-02
Has anyone confirmed if this will work with a Wireless Xbox 360 controller in 9.10?

That's really the only reason I have to dual-boot with Vista anymore

---

### Post by Grumbel on 2010-01-03
> **manco said:**
> Has anyone confirmed if this will work with a Wireless Xbox 360 controller in 9.10?
If you have a wirless receiver, yes, then it should work.

---

### Post by manco on 2010-01-03
> **Grumbel said:**
> If you have a wireless receiver, yes, then it should work.
I have the wireless receiver; is this the guide I should follow to get it working?

---

### Post by manco on 2010-01-03
> **wootah said:**
> [SIZE=4]
Compiling! (Step Four)[/SIZE]

The best part! We can now grab the driver from the author's website. As of this writing, version** 0.2rc1** is available here: [http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2]("http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2"). The best way to do this for now, would be to create a temp. directory in your home directory, download the driver there and extract its contents. At the terminal:

```

cd ~
mkdir tmp
cd tmp
wget http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2
tar -xvvf xboxdrv-linux-0.2.tar.bz2  

```

Now we can move into that directory and start compiling! At the terminal:

```

 cd xboxdrv-linux-0.2 
 scons

```

I keep getting this error after entering the 2nd code above:

```

yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.2$  scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o helper.o -c -g -O0 -Wall helper.cpp
In file included from helper.cpp:21:
helper.hpp:24: error: 'uint8_t' has not been declared
helper.cpp:23: error: 'uint8_t' has not been declared
scons: *** [helper.o] Error 1
scons: building terminated because of errors.
yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.2$ 

```

Any thoughts please?

**EDIT:**

After a little more tweaking, I now get this error after "scons"

```

yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:62: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:62: error: 'exit' was not declared in this scope
uinput.cpp:77: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:77: error: 'exit' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```

All I did was add some "#include" files I saw online pertaining to this...

Looks like the error lies somewhere in "uinput.cpp"

---

### Post by Grumbel on 2010-01-04
> **manco said:**
> I keep getting this error after entering
Go to [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) and download the latest version.

---

### Post by manco on 2010-01-04
> **Grumbel said:**
> Go to [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) and download the latest version.
Thanks for the reply

I downloaded "xboxdrv-linux-0.4.9.tar.bz2"

Ran it like before, with the file name changed:

```

yellowsnow4free@Anthony-PC:~$ cd tmp
yellowsnow4free@Anthony-PC:~/tmp$ cd xboxdrv-linux-0.4.9
yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.4.9$ scons
scons: Reading SConscript files ...
Checking for C++ library X11... no
libx11-dev must be installed!
yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.4.9$ 

```

What am I missing?

---

### Post by Grumbel on 2010-01-04
> **manco said:**
> What am I missing?

 % apt-get install \
     g++ \
     libboost1.37-dev \
     libboost-thread1.37-dev \
     scons \
     libusb-dev \
     git-core \
     libx11-dev \
     x11proto-core-dev \
     python-dbus

See README for more details.

---

### Post by manco on 2010-01-04
> **Grumbel said:**
> % apt-get install \
     g++ \
     libboost1.37-dev \
     libboost-thread1.37-dev \
     scons \
     libusb-dev \
     git-core \
     libx11-dev \
     x11proto-core-dev \
     python-dbus

See README for more details.
Okay, I can see it under the README.

Seeing as I'm still a Ubuntu noob, *how* do I install the above? :confused: I just need a little more instruction to get started :)

Thank you for all your help! :KS

---

### Post by Grumbel on 2010-01-04
> **manco said:**
> Seeing as I'm still a Ubuntu noob, *how* do I install the above?
Copy&paste all the lines, witout the leading '%', into a terminal.

---

### Post by manco on 2010-01-04
> **Grumbel said:**
> Copy&paste all the lines, witout the leading '%', into a terminal.
I think it worked... here's my code:

```

yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.4.9$ sudo ./xboxdrv --wid 0
[sudo] password for yellowsnow4free: 
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        005:002
Controller:        "Microsoft Xbox 360 Wireless Controller (PC)" (idVendor: 0x045e, idProduct: 0x0719)
Wireless Port:     0
Controller Type:   Xbox360 (wireless)
Deadzone:          0
Trigger Deadzone:  0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        auto
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled

**Starting with uinput... Error: /dev/input/uinput: No such file or directory**
done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event8

Press Ctrl-c to quit

X1: -1262 Y1:   608  X2:  2272 Y2:  1303  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
Connection status: nothing
Connection status: nothing

```

Ran it the first time, didn't work.  Ran it a second time, seems to be working.  Oh well, works for me!

Special thanks to Grumbel for all the help and patience.

---

### Post by AgentZ86 on 2010-01-05
Hi

I'm lacking understanding about keymaps ?

Is there a post someplace about setting this up.

I'm using the xbox360 wired on ubuntu karamic currently it working well.

But there are the let and right button just above the trigger that I want to use as keyboard buttons.

For example:
left button mapped to X key on the keyboard.

right button mapped C key on the keyboard.

I read the readme files but I'm having trouble understanding this.

Does this mapping have to be one or the other because the controller works great in vendetta but I just want to add functionality to the un-used buttons and there are also a couple other buttons I would like mapped to a keyboard stroke as well.

Please clarify or if there is another post about this please advise.

Thanks

---

### Post by Grumbel on 2010-01-06
> **AgentZ86 said:**
> left button mapped to X key on the keyboard.

right button mapped C key on the keyboard.

I read the readme files but I'm having trouble understanding this.
Something like:

./xboxdrv -s --ui-buttonmap lb=KEY_X,rb=KEY_C

should work. 

There might however be issues with what Xorg registers automatically as keyboard. So in case it doesn't work you have to tweak /etc/hal/fdi/preprobe/xboxdrv.fdi as documented in the README.

---

### Post by pogue.mahone on 2010-02-03
sorry, noob here.

but i'm trying to follow the instructions to install xboxdrv by grumbel.
i've installed all the other necessary programs except libboost1.37-dev and libbost-thread1.37-dev
whenever i try to install what these, i get this message:

$ sudo apt-get install libboost1.37-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libboost1.37-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libboost1.37-dev has no installation candidate

i'm running ubuntu netbook remix 9.10
any help would be very appreciated.
i've been reading through plenty on this topic and haven't seen this problem.
again i'm a super noob, but really want to convert over to ubuntu.
thanks

---

### Post by paraplegicpanda on 2010-02-03
Unless you need to add a new repo to download it, you probably just need to make sure you have all of the default repos enabled. Go to System > Administration > Software Sources. On the 'Ubuntu' tab make sure everything but Source Code is checked. Go to the 'Other Software' tab and check all of the boxes. When you close the dialog it should automatically update all of your repos. Try to install it again after that.

---

### Post by pogue.mahone on 2010-02-04
This doesn't seem to help.

All my sources except source code are checked under ubuntu software

under other software i have two checked
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
&
[http://ppa.launchpad.net/jason_scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason_scheunemann/ppa/ubuntu) karmic main

the only one not checked here is
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (source code)

the program didn't seem to like me check marking this one....

---

### Post by paraplegicpanda on 2010-02-04
First, have you tried installing Xpad? I'm assuming so if you're here, but if not you should try installing Xpad before you mess with Grumbel's xboxdrv.

Second, the problem is that libboost has been updated in the repositories. Not that that's really an issue... Rather than doing it with apt just go to 'System > Administration > Synaptic Package Manager' and search for libboost. Install the most up-to-date versions of the libraries you need and you should be golden. As of right now it looks like 1.40 is the most recent version.

---

### Post by pogue.mahone on 2010-02-04
no, wrong assumption i guess. i wasn't aware of it.
but i just checked for the software and instead downloaded some sticky note program?

how can i install xpad for my xbox 360 controller?

---

### Post by paraplegicpanda on 2010-02-04
Try this tutorial from Xbox Scene:
[http://www.xboxscene.com/articles/controller-linux.php]("http://www.xboxscene.com/articles/controller-linux.php")

And not to be a dick, but try googling a bit more next time, it helps to find the best solution to your problems. It also helps to keep the information here on the forums relevant.

---

### Post by AgentZ86 on 2010-02-04
> **Grumbel said:**
> Something like:

./xboxdrv -s --ui-buttonmap lb=KEY_X,rb=KEY_C

should work. 

There might however be issues with what Xorg registers automatically as keyboard. So in case it doesn't work you have to tweak /etc/hal/fdi/preprobe/xboxdrv.fdi as documented in the README.

Thanks

---

### Post by AgentZ86 on 2010-02-06
Hi all

Ubuntu 9.10 Karmic 64

I've got the Xbox360 wired working perfectly with xboxdrv; and the Logitech Extreme works perfectly out of the box but they only work separately so I have 2 questions:

[LIST=1]
[*]When I start the xboxdrv -s I get this:> Starting with uinput... Error: /dev/input/uinput: No such file or directory
done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event6

Press Ctrl-c to quit

Unknown: len: 3 data: 0x02 0x03 0x00 

Although the xbox360 controller appears to be working perfectly I wondered what this text might be or what effect it might have ? 
[*]Also when the xboxdrv is running and xbox360 is plugged in to usb port, when I try to plugin the logitech extreme 3D pro usb then the machine just freezes and I have to unplug the logitech and restart the machine.
[/LIST]

I was wondering if there was a way to get them both working, I'm trying to use both the joystick right handed controls for turning and pitch etc. but I wanted to use the xbox360 controller for left handed controls like throttle and strafe or basically wanted to use the xbox360 in my left hand instead of the hat on the joystick 
I wanted to use the xbox360 controller dpad in my left hand for the hat controls and perhaps roll.

Sort of like a saitek x45 or x52 flight gear thing, but was considering using the logitech and xbox360 controller to simulate this.

Anyhow, if anyone knows of a work around to have them both working at the same time that would be great

Please advise

Thanks in advance

---

### Post by Grumbel on 2010-02-06
> **AgentZ86 said:**
> Although the xbox360 controller appears to be working perfectly I wondered what this text might be or what effect it might have ?
Completely harmless. xboxdrv is searching in multiple locations for the uinput device and will give an error for locations where it hasn't found the device, but its not an error, it will just look in the next location. And if I remember correctly I have already removed that error message from the latest version.

> Also when the xboxdrv is running and xbox360 is plugged in to usb port, when I try to plugin the logitech extreme 3D pro usb then the machine just freezes and I have to unplug the logitech and restart the machine.
That sounds rather broken. Do you get an complete freeze with no way to recover from it other then reboot? Is it possible to get the output from "dmesg" after plugging in the Logitech joystick? Do you run xboxdrv manuelly or via xboxdrv-daemon.py? In the first case it shouldn't be xboxdrv's fault, as xboxdrv shouldn't care about other USB devices. In the later case I would switch to using xboxdrv instead. It might also help to plugin the logitech joystick first. But it kind of sounds like a problem with the logitech driver.

---

### Post by manco on 2010-02-08
Okay, no problem getting it to work.  I've had to reinstall Ubuntu a few times and it's worked every time.

Quick question though:

It's kind of a pain having to go through all the steps in terminal to get the controller connected.  I created a ".sh" file that (I think) should work, but isn't.

Here's my code:

```
$ lsmod | grep uinput
$ sudo modprobe uinput

$ lsmod | grep joydev
$ sudo modprobe joydev

$ lsmod | grep xpad
$ sudo rmmod xpad

$ cd "Saved Games"
$ cd xboxdrv

$ ls -lsa xboxdrv
$ sudo ./xboxdrv --wid 0
```
I have the .sh file set so it can be run as a program (not sure if this is correct either)

Can someone help me?  I'd just like to be able to run a file that will run all the required terminal commands for me.

Thanks!

---

### Post by Grumbel on 2010-02-08
> Can someone help me?  I'd just like to be able to run a file that will run all the required terminal commands for me.
Are the "$" actually in the file? If so, remove them. Also add  "#!/bin/sh" as the first line, which is needed to make it executable. You also have to give the "cd" commands the full path, i.e. /home/juser/src/xboxdrv/... or wherever you have stored it.

Shell script aside: You can add modules to /etc/modules to be automatically loaded and you can create a file /etc/modprobe.d/xpad.conf with the content "blacklist xpad" to stop xpad from getting loaded.

---

### Post by manco on 2010-02-08
> **Grumbel said:**
> Are the "$" actually in the file? If so, remove them. Also add  "#!/bin/sh" as the first line, which is needed to make it executable. You also have to give the "cd" commands the full path, i.e. /home/juser/src/xboxdrv/... or wherever you have stored it.

Shell script aside: You can add modules to /etc/modules to be automatically loaded and you can create a file /etc/modprobe.d/xpad.conf with the content "blacklist xpad" to stop xpad from getting loaded.
Worked perfectly!  Thanks!

---

### Post by manco on 2010-02-09
Okay, I've made 2 files that should (hopefully) make the installation/running of the driver(s) much easier.

The first is a file called "INSTALL.sh".  You'll need to edit the directories though (use your username, not mine, for example).  Double-click the file and select "Run in Terminal"

The second is "RUN.sh".  Once again, edit the directories.  Turn on/plug in your Xbox 360 controller, then double-click the file and select "Run in Terminal"

---

### Post by skibum3027 on 2010-02-17
> **manco said:**
> Okay, I've made 2 files that should (hopefully) make the installation/running of the driver(s) much easier.

Thanks for these!
While they worked for me, they also returned a couple of errors (no installation candidates for libboost1.37-dev or libboost-thread1.37-dev). Seeing as it worked, it's probably nothing though.

Also, since it seems the people who maintain this software pay attention to this thread, I had to add the following line (with comma) to the table in xpad_device.cpp to get my particular controller to work. (It's the Mad Catz controller sold at Gamestop.)

```
{ GAMEPAD_XBOX360,          0x1bad, 0xf016, "Mad Catz Xbox 360 Controller" },
```

---

### Post by regrad on 2010-03-21
> **manco said:**
> I keep getting this error after entering the 2nd code above:

```

yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.2$  scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o helper.o -c -g -O0 -Wall helper.cpp
In file included from helper.cpp:21:
helper.hpp:24: error: 'uint8_t' has not been declared
helper.cpp:23: error: 'uint8_t' has not been declared
scons: *** [helper.o] Error 1
scons: building terminated because of errors.
yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.2$ 

```Any thoughts please?

**EDIT:**

After a little more tweaking, I now get this error after "scons"

```

yellowsnow4free@Anthony-PC:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:62: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:62: error: 'exit' was not declared in this scope
uinput.cpp:77: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:77: error: 'exit' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

```All I did was add some "#include" files I saw online pertaining to this...

Looks like the error lies somewhere in "uinput.cpp"

Add this headers:

helper.hpp:
```

#include <stdint.h>

```uinput.cpp:
```

#include <cstdlib>

```[IMG]http://www.google.com.pe/images/cleardot.gif[/IMG]
I had the same problem and solved it by adding the headers :D

---

### Post by LukeLinux on 2010-04-30
Just thought I should mention here that this guide doesn't work 100% with Ubuntu 10.04 Lucid Lynx. **Everything works in Steps 1 and 2**, but once you get past libusb-dev in step three, there are some issues.

For one thing, to get libboost, you can't use 1.34.1 as is shown in the guide code. You have to use Lucid's version (1.40.0), which makes the code this:

```
sudo apt-get install libboost-date-time-dev libboost-date-time1.40.0 libboost-dev libboost-doc libboost-filesystem-dev libboost-filesystem1.40.0 libboost-graph-dev libboost-graph1.40.0 libboost-iostreams-dev libboost-iostreams1.40.0 libboost-program-options-dev libboost-program-options1.40.0 libboost-python-dev libboost-python1.40.0 libboost-regex-dev libboost-regex1.40.0 libboost-signals-dev libboost-signals1.40.0 libboost-test-dev libboost-test1.40.0 libboost-thread-dev libboost-thread1.40.0
```For another thing, adding uinput and joydev to /etc/modules doesn't seem to work in 10.04. I haven't figured out a way to make it automatically load them up yet, but it's not that hard to just type

```
sudo modprobe uinput
sudo modprobe joydev
```before loading up xboxdrv in a terminal. **And**, since xboxdrv has been updated many times since the guide's 0.2, you need to download [xboxdrv-linux-0.4.10.tar.bz2]("http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv-linux-0.4.10.tar.bz2") instead, and then use the appropriately different codes for compiling as well, as seen below:

```
cd ~
mkdir tmp
cd tmp
wget http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv-linux-0.4.10.tar.bz2
tar -xvvf xboxdrv-linux-0.4.10.tar.bz2
```...and here we run into another issue. If we were to go ahead and navigate to the xboxdrv directory and type 'scons' in the terminal, it wouldn't be able to do it due to a missing prerequisite. So, before we go on, we have to add in another code.

```
sudo apt-get install libx11-dev
```After that is done, we can finally get around to compiling

```
cd xboxdrv-linux-0.4.10 
scons
```When that's done, if all went well, you can type

```
ls -lsa xboxdrv
```and it will show up! Driver execution is the same as shown in the guide, just remember to navigate to the updated folder, or shorten the process by typing:

```
cd ~/tmp/xboxdrv*
```

Hope this helps other 10.04 users out! :guitar:

---

### Post by yanom on 2010-05-02
You can buy gamestop xbox360 controllers for about $50 less than Microsoft xbox360 controllers.

---

### Post by Realnot on 2010-05-02
sorry,  but this howto applies to Microsoft LifeChat ZX 6000?

[http://www.notebookcheck.net/typo3temp/pics/83c045527e.jpg](http://www.notebookcheck.net/typo3temp/pics/83c045527e.jpg)

---

### Post by Grumbel on 2010-05-07
I have created some .deb's for xboxdrv, you can find the PPA at:

[https://launchpad.net/~grumbel/+archive/ppa](https://launchpad.net/~grumbel/+archive/ppa)

and the packages themselves at:

deb [http://ppa.launchpad.net/grumbel/ppa/ubuntu](http://ppa.launchpad.net/grumbel/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/grumbel/ppa/ubuntu](http://ppa.launchpad.net/grumbel/ppa/ubuntu) lucid main 

Haven't tested them much, so bug reports are welcome. A proper man page is now included (containing mostly info from the README and some more).

The PPA also contains sdl-jstest, which can be quite useful when it comes to configuring SDL.

Edit: PPA URL has changed

---

### Post by AgentZ86 on 2010-05-15
Hi,

Curious about the multiple xbox360 controller use ?

In otherwords could I use one xbox360 wired controller in vendetta as I do now, but also add a second controller which I plan to use for a rudder pedal device that will use the second xbox360

I mean to say can you use 2)xbox360 wired controllers for the same game ?

I want to add rudder control and use the second xbox360 wired for this.

Can this be done ?

Please advise
Thanks

---

### Post by Grumbel on 2010-05-15
> **AgentZ86 said:**
> I mean to say can you use 2)xbox360 wired controllers for the same game ?
Kind of, but only if the game support multiple joysticks. xboxdrv itself can only handle one gamepad per instance, so you have to start xboxdrv multiple times for multiple gamepads, this however means that you will get multiple joystick devices and thus need a game that can handle it. If the game can't handle it, you would need to fall back to keyboard emulation or other hackery which might not give satisfying results.

---

### Post by AgentZ86 on 2010-05-15
> **Grumbel said:**
> Kind of, but only if the game support multiple joysticks. xboxdrv itself can only handle one gamepad per instance, so you have to start xboxdrv multiple times for multiple gamepads, this however means that you will get multiple joystick devices and thus need a game that can handle it. If the game can't handle it, you would need to fall back to keyboard emulation or other hackery which might not give satisfying results.

Hmmmmm, thanks

This gives me something to think about.

I see this USB pedals on ebay wondering if I could use those along with only one instance of xboxdrv if the game supports it.

Thanks for the info

---

### Post by AgentZ86 on 2010-06-11
xbox 360 wired with logitech 3d extreme usb joystick

I seem to be able to use the 360 controller or the logitech in vendetta, but not at the same time.
I don't think the logitech is being recognized while running xboxdrv for some reason ?

How can test to see if the logitech is working while the 360 is plugged in ?

At least I can determine if it's game related or something to do with the combination

Before I get the pedals I wanted to try and see if the known working units will work simultaneously first.

Please advise
Thanks

---

### Post by Grumbel on 2010-06-12
> **AgentZ86 said:**
> How can test to see if the logitech is working while the 360 is plugged in ?
jstest

---

### Post by skript_teaze on 2010-07-15
I'm a bit stuck help!

I followed all of the steps down to the second part of the compiling (running the scons command in the new directory from the .tar) And I have this error message:

matt@matt-linux:~/tmp$ cd xboxdrv-linux-0.2
matt@matt-linux:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o helper.o -c -g -O0 -Wall helper.cpp
In file included from helper.cpp:21:
helper.hpp:24: error: 'uint8_t' has not been declared
helper.cpp:23: error: 'uint8_t' has not been declared
scons: *** [helper.o] Error 1
scons: building terminated because of errors.

At the start of the instructions I copied and pasted the pre-compiling steps one line at a time. Nothing seemed to happen in terminal it just started a new line. Am I right in thinking this part didnt work quite right for me?

Also I was getting an error message that the libboost files were not available so I ran the command:

sudo apt-get install libboost-all-dev

As I thought the files listed were out of date and I couldn't be bothered to change all of the files from 1.34.1 to whatever they are at now.

Any ideas what has gone wrong for me? 

Sorry if i come across incredibly stupid but I'm pretty new to linux.

---

### Post by skript_teaze on 2010-07-15
OK So I should have read all of the replies...

I now have it installed I think.

matt@matt-linux:~/tmp/xboxdrv-linux-0.4.10$ ls -lsa xboxdrv
3048 -rwxr-xr-x 1 matt matt 3120865 2010-07-16 00:20 xboxdrv

now what?? lol

---

### Post by Grumbel on 2010-07-15
> **skript_teaze said:**
> now what?? lol
Start it:

./xboxdrv

then test with:

jstest /dev/input/js0

last one might require 'apt-get install joystick', also read the README of xboxdrv.

---

### Post by skript_teaze on 2010-07-16
> **Grumbel said:**
> Start it:

./xboxdrv

then test with:

jstest /dev/input/js0

last one might require 'apt-get install joystick', also read the README of xboxdrv.

I'm getting:

 bash: ./xboxdrv: No such file or directory

(using ubuntu 10.04)
Does this mean I haven't installed it correctly or am I using the wrong command to execute it?

I have tried the command from ~$ and also the xboxdrv directory but no luck so far.

---

### Post by Grumbel on 2010-07-16
> **skript_teaze said:**
> I have tried the command from [...] the xboxdrv directory but no luck so far.
No, you haven't. Your earlier 'ls' output showed the binary was there, so you have to have been in the wrong directory. Also read a basic bash tutorial.

---

### Post by skript_teaze on 2010-07-16
> **Grumbel said:**
> No, you haven't. Your earlier 'ls' output showed the binary was there, so you have to have been in the wrong directory. Also read a basic bash tutorial.

Yep I was in the wrong directory I had two xboxdrv directories... lol!

---

### Post by skript_teaze on 2010-07-17
I have to run rmmod xpad each time before, I run xboxdrv both with sudo in ubuntu 10.04 using a wireless controller. Would there be a way to create a panel icon to do this for me when I click it, or is that a very winblows thing to ask?

---

### Post by Grumbel on 2010-07-17
> **skript_teaze said:**
> I have to run rmmod xpad each time before, I run xboxdrv both with sudo in ubuntu 10.04 using a wireless controller. Would there be a way to create a panel icon to do this for me when I click it
Two options:

1) Add a line "blacklist xpad" to /etc/modprobe.d/blacklist.conf, this will stop xpad from getting loaded.

2) Create a shell script:

#!/bin/sh
rmmod xpad
path/to/xboxdrv

and set it executable to start xboxdrv.

---

### Post by skript_teaze on 2010-07-22
I have installed xboxdrv, xpad is sorted and out of the way, but I'm having problems with uinput and joydev, I cant get them to load automatically. I edited the modules.conf file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# The following two modules are used with the xbox controller driver.
# Added on 22nd July 2010 By Matt

input
joydev

Have I done this correctly? I get an error....
"Starting with uinput... Error: /dev/input/uinput: No such file or directory
done"

I'm using ubuntu 10.04

---

### Post by Grumbel on 2010-07-22
> **skript_teaze said:**
> Have I done this correctly? I get an error....
"Starting with uinput... Error: /dev/input/uinput: No such file or directory
done"
In latest Ubuntu it is now /dev/uinput not /dev/input/uinput, but xboxdrv should figure that out on its own unless you are using an completly outdated version. The error message is harmless and can be ignored.

---

### Post by skript_teaze on 2010-07-23
> **Grumbel said:**
> In latest Ubuntu it is now /dev/uinput not /dev/input/uinput, but xboxdrv should figure that out on its own unless you are using an completly outdated version. The error message is harmless and can be ignored.

Ok thanks i'll ignore the mesaage from now on..... I still get the error:

Starting with uinput... Error: /dev/input/uinput: No such file or directory
Error: /dev/uinput: No such file or directory
Error: /dev/misc/uinput: No such file or directory
Error: No stuitable uinput device found

I have to run sudo modprobe uinput & sudo modprobe joydev to get it to work everytime I changed my modules.conf file to include uinput and joydev but they dont seem to load automatically. This is only a minor problem for me as the driver actually works no problem. I would just like to have to type less at the terminal to get it to work :P

Maybe I'm just being lazy.

---

### Post by Grumbel on 2010-07-23
Your /etc/modules lists "input" not "uinput".

---

### Post by skript_teaze on 2010-07-23
> **Grumbel said:**
> Your /etc/modules lists "input" not "uinput".

LOL thanks I've sorted it now.

---

### Post by MAFoElffen on 2010-07-31
> **Grumbel said:**
> Two options:

1) Add a line "blacklist xpad" to /etc/modprobe.d/blacklist.conf, this will stop xpad from getting loaded.

2) Create a shell script:

#!/bin/sh
rmmod xpad
path/to/xboxdrv

and set it executable to start xboxdrv.
(Running 10.04.1) ... Install went fine.  Tests fine. 

Shell script(?)  Name as 'anything' and save in a logical directory such as ."./xboxdrv-linux-0.4.10"?  Set the "file properties" as executable right? And tie the execution to what?  (Such as a button or an autostart event?)

---

### Post by mcarans on 2010-08-04
[FONT=Times New Roman][SIZE=2][FONT=&quot]I have completed a wrapper around xboxdrv called[/FONT][/SIZE][/FONT][FONT=Times New Roman][SIZE=2][FONT=&quot] runxboxdrv. It is run [/FONT][/SIZE][/FONT][FONT=Times New Roman][SIZE=2][FONT=&quot] using:
runxboxdrv --cfg=/home/mike/oolite.cfg /usr/bin/oolite

It handles:
1. Shutting cleanly any existing xboxdrv process
2. Checking and unloading if necessary xpad.
3. Checking and loading if necesary uinput and joydev
4. Checking and changing if necessary uinput device permissions
5. Loading a configuration file and converting its contents to xboxdrv
command line arguments
6. Running xboxdrv with said arguments
7. Running game once xboxdrv outputs "Press CTRL-C to quit"
8. Shutting cleanly xboxdrv after user shuts down game

Oolite.cfg (the gamepad configuration) looks like this:
[options]
silent=true
trigger-as-button=true
dpad-as-button=true
led=0

[axis-sensitivity]
X1=-1.0
X2=-1.0
Y2=-1.0

[axismap]
Y2=-Y2

[ui-axismap]
Y1=XK_1:XK_2

[ui-buttonmap]
# speed
du=XK_Up
dd=XK_Down
...[/FONT][/SIZE][/FONT]


[FONT=Times New Roman][SIZE=2][FONT=&quot]/usr/bin/oolite is the game I am playing with the gamepad[/FONT][/SIZE][/FONT]. 



Can someone try this out for other games and let me know if it works ok? I've attached it as a zip as this forum won't allow it to be uploaded as is.



Cheers,
Mike

---

### Post by ToFue on 2010-08-07
> 
For my machine, this module was not loaded; thus, I lucked out. If it is loaded for you, you may issue the rmmod command:
```

sudo rmmod xpad

```The author states that *"rmmod might not be enough since it might be automatically loaded again"*.

 **Could someone let me know how one would fix that?**


@ skript_teaze;
I put mine in a diff file, it works but what's the difference in ../blacklist.conf and ../blacklist-watchdog.conf ?

```

$ sudo gedit /etc/modprobe.d/blacklist-watchdog.conf

```
   with..
```

blacklist xpad 

```
added

---

### Post by mcarans on 2010-08-08
> **ToFue said:**
> @ skript_teaze;
I put mine in a diff file, it works but what's the difference in ../blacklist.conf and ../blacklist-watchdog.conf ?

```

$ sudo gedit /etc/modprobe.d/blacklist-watchdog.conf

```   with..
```

blacklist xpad 

```added

I suggest trying the wrapper (runxboxdrv) I posted in the message just before yours ([http://ubuntuforums.org/showpost.php?p=9676862&postcount=284](http://ubuntuforums.org/showpost.php?p=9676862&postcount=284)) as it handles all of this. There is no need to edit system files or remember to sudo this or that.

Cheers,
Mike

---

### Post by Grumbel on 2010-08-08
> **ToFue said:**
> I put mine in a diff file, it works but what's the difference in ../blacklist.conf and ../blacklist-watchdog.conf ?
No difference, everything *.conf should work.

---

### Post by cactusgenie on 2010-08-27
> **LukeLinux said:**
> Just thought I should mention here that this guide doesn't work 100% with Ubuntu 10.04 Lucid Lynx. **Everything works in Steps 1 and 2**, but once you get past libusb-dev in step three, there are some issues.

.....lots of helpful things ...... :popcorn:
Hope this helps other 10.04 users out! :guitar:

Thanks mate, awesome stuff. except I used version 0.5.0.

---

### Post by zoso375 on 2010-08-28
Can anyone tell me if this how-to works for Lucid?  Do I need to dig through all 29 pages on this thread and sift through the bits and pieces of updated material?  Or will the original instructions work?

---

### Post by ICANSEEYOU7687 on 2010-09-07
Im a little confused.  I want to get a XBOX360 controller (preferably a wireless one) to work on ubuntu 10.04, but most of the things I found are from older versions.

I read somewhere that the wired xbox360 controller you can just plug and play now, and I havent heard anything about the wireless version.

Any insight on this?

---

### Post by ICANSEEYOU7687 on 2010-10-12
BUMP

Still curious.  I know the wired controller in 10.04 was just plug n play.  But how about the wireless controller now?

---

### Post by casacerian on 2011-03-21
> **zoso375 said:**
> Can anyone tell me if this how-to works for Lucid?  Do I need to dig through all 29 pages on this thread and sift through the bits and pieces of updated material?  Or will the original instructions work?

This is my question as well. Not that I mind going through all 29 pages, but may as well ask beforehand.

---

### Post by Grumbel on 2011-03-21
> **casacerian said:**
> This is my question as well. Not that I mind going through all 29 pages, but may as well ask beforehand.
Both wired and wireless Xbox360 controllers work on Ubuntu and have worked for quite a while. There are two main ways to get them to work:

1) Use the xpad kernel drivers, these come with Ubuntu and should work automatically, just plug&play

2) Use the xboxdrv userspace driver mentioned in the howto on page one. The instructions are a bit outdated (you no longer have to manually compile it, Ubuntu packages for Lucid and Maverick are provided on the webpage), but should overall still apply.

Things to keep in mind: Wireless controller need a Microsoft Wireless Receiver, they do NOT work with generic Blutooth adapter and they do NOT work with the Play&Charge USB cable either.

The buildin xpad driver has a few short comings, such limited configurability, it always displays four wireless controller when a wireless receiver is plugged in, even when only one controller is synced and there have been bugs in the past (not sure if they have been fixed), which is why xboxdrv exists as alternative.

---

### Post by Nasair on 2011-04-22
First:
I have Googled this and found a few things but no answers.
I've gone through this entire thread...and mostly outdated information.
Also, found this page: [http://ubuntu.bryanludvigsen.com/?p=217](http://ubuntu.bryanludvigsen.com/?p=217)

I found this for some help on mapping with xboxdrv:
[http://ubuntuforums.org/showthread.php?t=980196](http://ubuntuforums.org/showthread.php?t=980196)

Found someone having have the same issue:
[http://www.jupitercolony.com/viewtopic.php?f=3&t=8637](http://www.jupitercolony.com/viewtopic.php?f=3&t=8637)

What I can get working:
1 or more controllers manually running:
```
sudo xboxdrv --wid 0
sudo xboxdrv --wid 1
```And if more controllers I'll use more statements, as in wid 3...etc...

What I can't get working:
Using the controller as a mouse at all.

I run:
```
xinput list
```Now I get the following:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech BT Mini-Receiver          id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech Logitech BT Mini-Receiver          id=8    [slave  keyboard (3)]
    &#8627; HID 3351:3715                               id=10    [slave  keyboard (3)]

```And like in the link I found with the same issue as me I can confirm xpad is installed as well, and since I can get the controller working with xboxdrv I know something is working right.

I have xboxdrv installed on Ubuntu 10.10 64bit but what I would like is to be able to turn on my computer turn on my computer and start using my XBox controller as a mouse (using my PC as a media center with XBMC) to start XMBC or to load up a rom manager etc... All this would be awesomeR if I didn't need to enter in a password for sudo since I have it auto login as is.

Additionally, if possible it would also be nice if I turn on my second, or third, or heck, even my 4th controller they would auto connect and work for playing some Super Smash Bros.

Any help would be awesome!

---

### Post by Grumbel on 2011-04-22
> **Nasair said:**
> Also, found this page: [http://ubuntu.bryanludvigsen.com/?p=217](http://ubuntu.bryanludvigsen.com/?p=217)
Thats outdated, that was essentially a bug where Xorg detected  all joysticks as misconfigured mouse-like devices, making them useless as joysticks and mice. That has since been fixed and joysticks act as joysticks.

What you wanna try is actual mouse emulation, which can be done with:

```
sudo xboxdrv --wid 0 --mouse
```

--mouse is a shortcut for the stuff from:

/usr/share/doc/xboxdrv/examples/mouse.xboxdrv

You might also want to look at the lengthy and convoluted man page:

[http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html](http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html)

> I have xboxdrv installed on Ubuntu 10.10 64bit but what I would like is to be able to turn on my computer turn on my computer and start using my XBox controller as a mouse (using my PC as a media center with XBMC) to start XMBC or to load up a rom manager etc... All this would be awesomeR if I didn't need to enter in a password for sudo since I have it auto login as is.
You can configure sudo to not take a password. There is also a XBMC configuration for xboxdrv in the examples/ directory which you might wanna try, it doesn't do mouse emulation, but maps the controller so that XBMC is happy.

> Additionally, if possible it would also be nice if I turn on my second, or third, or heck, even my 4th controller they would auto connect and work for playing some Super Smash Bros.
Thats what Daemon mode is for:

```
xboxdrv --daemon
```

But that is sadly currently still kind of broken and in development, maybe in another few weeks.

---

### Post by Nasair on 2011-04-22
[FONT=monospace]Thank you so much!

[/FONT]```
sudo xboxdrv --wid 0 --mouse
```[FONT=monospace]
Rocks my world. Oh, and XBMC actually uses this better to me then the configuration in xboxdrv. But I can't see a way to have the controller switch from mouse to game pad on demand.

I have been to the xboxdrv site but I guess I was just overwhelmed last time because after doing some looking all over the Internet and now coming back to the site it makes more sense.

And if you want to have xboxdrv auto load controllers I find the below works best since the code you mention (--daemon) only works for one device:

[/FONT]```
echo PASSWORD | sudo -S rmmod xpad | sudo -S xboxdrv --daemon \
  --next-controller \
  --next-controller \
  --next-controller
```[FONT=monospace]

I added in the code so that I can make a start-up script without the need for entering my sudo password.
[/FONT]

---

### Post by hfxdesign on 2011-04-25
Using stable 0.6.6 - had a quick question. Is there anyway to hide the "Unknown: len: 29 data: 0x00 0x00 0x00 0x00" etc. from parsing?

---

### Post by fmdex2011 on 2011-04-27
xboxdrv install on Ubuntu 10.10 amd64 2.6.35-29-generic
Gateway 2.13Ghz i3 CPU with 3.5 GiB memory

1st I would like to thank Grumbel for this program!  

I used to have something similar on win7 and I missed it a lot when I switched to Ubuntu

My install went a little bit differently than what I have read here and I have some questions on the application

I downloaded the xboxdrv-linux-0.7.3.tar.bz2 file and extracted it in an empty folder in my home directory called "hold"

I then followed the instructions from the README file in the package starting with:

sudo apt-get install \
         g++ \
         libboost1.42-dev \
         libboost-thread1.42-dev \
         scons \
    pkg-config \
    libusb-1.0-0-dev \
    git-core \
    libx11-dev \
    libudev-dev \
    x11proto-core-dev \
         libdbus-glib-1-dev

I just copied and pasted all that into the Terminal and everything went perfectly

Next in Terminal I typed:

fmdex2011@NV5913u:~$ **cd hold/xboxdrv-linux-0.7.3**

and to compile I typed:

fmdex2011@NV5913u:~/hold/xboxdrv-linux-0.7.3$ **scons**

Again everything went perfectly, and to finish it off I typed: **sudo checkinstall** instead of **make install** to create a xboxdrv-linux_0.7.3-1_amd64.deb file

Then I moved everything out of the hold folder and into my software folder

Now here is where the fun begins, I typed: **sudo rmmod xpad**, to unload xpad, then I typed:

**sudo modprobe uinput**, and got the following:

WARNING: All config files need .conf: /etc/modprobe.d/dgc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/dgc.conflicts, it will be ignored in a future release.

I typed: **lsmod**, and found that joydev was loaded but **uinput** was not, then I looked in the etc directory and found that uinput device was present but was it doing anything ? I don't know ?  Is this OK ? ( 1st question )

Anyway I moved forward and typed: **sudo xboxdrv --id 0**, ( I am using a wired controller ) results:

SB Device:        002:006
Controller:        Microsoft Xbox 360 Controller
Vendor/Product:    045e:028e
Wireless Port:     -
Controller Type:   Xbox360

Starting with uinput

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event6

Press Ctrl-c to quit, use '--silent' to suppress the event output

X1:   278 Y1:  1386  X2: -2735 Y2: -1298  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1:   167 Y1:  1386  X2: -2735 Y2: -1298  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0

All 21 functions work!, at the time of this writing I have been using the string: 

**sudo xboxdrv --id 0 --silent --mouse --deadzone 3000**

Everthing is working great but now I want to create some other configuration files

I understand the format and the syntax of the configuration files, it similar to windows ini files, but how do I apply the files ?

Do I sudo xboxdrv --config --myfile.ini ? or sudo xboxdrv --config --myfile.xboxdrv ? or ?

and what directory should I put myfile in ?  and what directory is the mouse file in ?

I have read the **man xboxdrv** page in Terminal and the xboxdrv manpage at [http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html]("http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv.html") several times, but I still don't get it !

Thanks

---

### Post by fmdex2011 on 2011-04-28
**Some questions answered **( maybe )

To use a different configuration file type:

```
sudo xboxdrv --config /path/to/your/file/filename.xboxdrv
```which in my case was,

```
sudo xboxdrv --config /home/fmdex2011/Software/xboxdrv-linux-0.7.3/examples/mouse2fmd.xboxdrv
```( just figured out how to use the cute little code box thing LOL )

So it does not matter where you put your configuration files as long as you know the path

I still want to see the default joystick and mouse files if anybody knows where they are ?

Also, is there a list of ev KEYS anywhere ? 

I want to use the ALT key on one of my buttons and I can't get it to work

Thanks

---

### Post by Grumbel on 2011-04-28
> **fmdex2011 said:**
> I still want to see the default joystick and mouse files if anybody knows where they are ?
When installed, /usr/share/doc/xboxdrv/examples/mouse.xboxdrv or else just the examples/ subdirectory of the source.

> Also, is there a list of ev KEYS anywhere ?
xboxdrv --help-key

> I want to use the ALT key on one of my buttons and I can't get it to work
KEY_LEFTALT

---

### Post by fmdex2011 on 2011-04-28
**WOW, thank you Grumbel !!!**

All those keys are going to keep me busy for quite a while

My head is still spinning from all the possibilities

Thank you very much !

---

### Post by fmdex2011 on 2011-04-30
Here is a different mouse configuration

Left stick - mouse

Right stick - scroll up, down, left. and right

Left trigger - ESC

Right trigger - F4

Left bumper - C

Right bumper - V

Left thumb stick press - CTRL

Right thumb stick press - ENTER

Back button - ALT

Guide button - Backspace

Start button - TAB

X button - browser back

Y button - browser forward

A button - left mouse button

B button - right mouse button

D pad - keyboard arrow up, down, left. and right

```
[xboxdrv]
ui-clear=true
silent=true
trigger-as-button=true

[ui-axismap]
x1^dead:4000 = REL_X:750:-1
y1^dead:4000 = REL_Y:750:-1

y2^dead:6000^invert = rel-repeat:REL_WHEEL:1:50
x2^dead:6000 = rel-repeat:REL_HWHEEL:1:50

[ui-buttonmap]
lt = KEY_ESC
rt = KEY_F4

[ui-buttonmap]
lb = KEY_C
rb = KEY_V

[ui-buttonmap]
tl = KEY_LEFTCTRL
tr = KEY_ENTER

[ui-buttonmap]
back  = KEY_LEFTALT
guide = KEY_BACKSPACE
start = KEY_TAB

[ui-buttonmap]
x = KEY_BACK
y = KEY_FORWARD
a = BTN_LEFT
b = BTN_RIGHT

[ui-buttonmap]
dl = KEY_LEFT
dr = KEY_RIGHT
du = KEY_UP
dd = KEY_DOWN

# EOF #
```Copy and paste the code into a new text file and name it "anyfilename.xboxdrv" then open a terminal and use it with:

```
sudo xboxdrv --config /path/to/your/file.xboxdrv
```Now you can sit back, relax, and enjoy your computer without touching your keyboard!

**Just be very careful with what buttons you press so that you don't have any accidents !!!**

no warranties are expressed or implied

---

### Post by .hfxdesign on 2011-04-30
Running 0.6.6 version of xboxdrv. I had success with running through dolphin-emu and zsnes. However, no luck with visual boy advance, anyone have suggestions?

P.S. I prefer not to map the controller to keyboard.

---

### Post by Grumbel on 2011-04-30
> **.hfxdesign said:**
> Running 0.6.6 version of xboxdrv. I had success with running through dolphin-emu and zsnes. However, no luck with visual boy advance, anyone have suggestions?
Looks like VisualBoyAdvance supports joysticks, but not automatically, so you have to hack together a VisualBoyAdvance.cfg:

[http://mandrivausers.org/index.php?/topic/8836-configuring-visual-boy-advance/](http://mandrivausers.org/index.php?/topic/8836-configuring-visual-boy-advance/)

---

### Post by tuxuser360 on 2011-05-09
Hey,

At first: thx grumbel for all your work done on the driver, its highly appreciated!

To my problem: Is it possible that this driver does not handle the Endianess properly or that it has any other problem related to the powerpc architecture.

I am trying to use the mouse emulation on my xbox360.. the pointer gets detected by Xorg but its behaving very odd... its jumping randomly across the screen.. so the handling does not really work.

I tried every parameters suggested in this thread regarding the mouse emulation.
I am using xboxdrv v0.7.3. I tested the driver on i386 ARCH just with

```

xboxdrv --mouse

```which works like a charm.

On my X360 / powerpc it looks like that (hope you can recognize the cursor and dont mind my music :P)

[http://file.libxenon.org/free60/linux/xboxdrv_mouse_emulation.avi](http://file.libxenon.org/free60/linux/xboxdrv_mouse_emulation.avi)

You can find me on your IRC channel in FreeNode #xboxdrv or check your gmx mails ;)

Thx in advance
Greetz
tux

---

### Post by Grumbel on 2011-05-09
> **tuxuser360 said:**
> To my problem: Is it possible that this driver does not handle the Endianess properly or that it has any other problem related to the powerpc architecture.
The Xbox360 controller data is currently interpreted via a plain memcpy it into a bitfield, so yeah, that won't work on PowerPC.

> I am trying to use the mouse emulation on my xbox360.. the pointer gets detected by Xorg but its behaving very odd... its jumping randomly across the screen.. so the handling does not really work.
Have you looked at the data it prints to stdout? If its an endian issue then the axis values should already be messed up long before mouse-emulation comes into play.

---

### Post by yax51 on 2011-05-13
I was going through this process, and am trying to compile the driver 0.7.3 and when I run scons I get this error: [http://paste.ubuntu.com/606855/](http://paste.ubuntu.com/606855/) and I don't know how to get past that post. There were a few hiccups along the way with missing packages and such, which for some reason or another were not included in the build essentials, but was able to get them and continue on. Now I'm stuck here, and don't know what to do. Any help would be appreciated!!

P.S. feel free to e-mail a solution if you have one. [email]yax51@hotmail.com[/email]. Thanks!!

---

### Post by Grumbel on 2011-05-19
> **yax51 said:**
> I was going through this process, and am trying to compile the driver 0.7.3 and when I run scons I get this error: [http://paste.ubuntu.com/606855/](http://paste.ubuntu.com/606855/) and I don't know how to get past that post. There were a few hiccups along the way with missing packages and such, which for some reason or another were not included in the build essentials, but was able to get them and continue on. Now I'm stuck here, and don't know what to do. Any help would be appreciated!!
Have you installed all the packages mentioned in the README? Could you post the full compile output if that didn't help?

---

### Post by Nicodemus144 on 2011-06-07
> **AgentZ86 said:**
> Weeeee

I added this line to the xpad_device.cpp
as directed in the readme.

  { GAMEPAD_XBOX360, 	      0x1bad, 0xf016, "Harmonix Music / MadCat Generic X-Box" },


hi there, i just switched over to Ubuntu full time and am having some trouble with my Xbox controller.

I have the Tron version, which is third party (might be MadCatz.)  in any case, it shows up under lsusb the same as the controller above:

0x1bad 0xf016 "Harmonix Music"

is it still necessary for me to add this line to xpad_device.cpp?

thanks!

---

### Post by Grumbel on 2011-06-07
> **Nicodemus144 said:**
> is it still necessary for me to add this line to xpad_device.cpp
No. The only important part is:

GAMEPAD_XBOX360, 0x1bad, 0xf016

The name is just cosmetic.

---

### Post by Nicodemus144 on 2011-06-07
> **Grumbel said:**
> No. The only important part is:

GAMEPAD_XBOX360, 0x1bad, 0xf016

The name is just cosmetic.

right, sorry, that's what i meant.  in that, i still have to edit the file.

thanks!

quick question, if i may: is this a common problem?  and if so, why hasn't the fix been applied going forward?  just curious.  not sure if it conflicts with other hardware (guitars maybe?)

---

### Post by Grumbel on 2011-06-07
> **Nicodemus144 said:**
> right, sorry, that's what i meant.  in that, i still have to edit the file.
No you have not. Its just cosmetic and thus meaningless.

---

### Post by Nicodemus144 on 2011-06-07
> **Grumbel said:**
> No you have not. Its just cosmetic and thus meaningless.

wait, so i *don't* have to edit the file?  maybe we're misunderstanding each other here.  let me break it down again:

i have a third party Xbox controller.

it appears that xpad doesn't work well with it and xboxdrv doesn't recognize it as an Xbox controller.

therefore, if i edit xpad_device.cpp with:

GAMEPAD_XBOX360, 0x1bad, 0xf016

will xboxdrv then recognize my controller as a legitimate Xbox controller?

=)

---

### Post by Grumbel on 2011-06-07
> **Nicodemus144 said:**
> it appears that xpad doesn't work well with it and xboxdrv doesn't recognize it as an Xbox controller.
You are likely running a completely outdated version of xboxdrv, i.e. the first post refers to 0.2, its currently at 0.8. Grab the latest version from (prebuild Ubuntu packages are available):

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

---

### Post by Nicodemus144 on 2011-06-07
> **Grumbel said:**
> You are likely running a completely outdated version of xboxdrv, i.e. the first post refers to 0.2, its currently at 0.8. Grab the latest version from (prebuild Ubuntu packages are available):

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

ah, ok.  i was running .66.  if you think .8 is stable enough i'll go higher.

i'll give it a go tonight when i get home and report back.

thanks!

---

### Post by Nicodemus144 on 2011-06-07
ok, in installed the latest version.  still no good.  sorry, my code doesn't match the code of the other guy.  it's just similar.

Bus 005 Device 002: ID 1bad:f903 Harmonix Music 

this is the code for the special Tron Xbox 360 controller.

now, do i need to edit xpad_device.cpp for xboxdrv to recognize my controller?  

and will you add this code to a future update of xboxdrv?

thanks!

---

### Post by Grumbel on 2011-06-07
> **Nicodemus144 said:**
> my code doesn't match the code of the other guy.  it's just similar.

Bus 005 Device 002: ID 1bad:f903 Harmonix Music 

this is the code for the special Tron Xbox 360 controller.

now, do i need to edit xpad_device.cpp for xboxdrv to recognize my controller?
Yes, you have to edit it. Add:

```

 { GAMEPAD_XBOX360,          0x1bad, 0xf903  "Tron Xbox 360 controller" },

```

You can also run xboxdrv without any source changes via:

./xboxdrv --device-by-id 1bad:f903 --type xbox360

> and will you add this code to a future update of xboxdrv?
Yes, already done.

---

### Post by Nicodemus144 on 2011-06-07
wonderful!  thank you so much for your responsiveness. =D

i look forward to future versions. =D

thanks for all your hard work!

---

### Post by Nicodemus144 on 2011-07-16
hi again, grumbel!  xboxdrv has been working great for me,

can you help me understand something?  is there a way to have the right analog stick function as if i were moving the mouse cursor?

i don't quite understand the mouse sections on the xboxdrv help page.

thanks!

---

### Post by Grumbel on 2011-07-16
> **Nicodemus144 said:**
> is there a way to have the right analog stick function as if i were moving the mouse cursor
Quick and dirty way:

./xboxdrv --axismap X1=X2,-Y1=Y2,X2=X1,-Y2=Y1   --mouse  -s

More proper way, copy "examples/mouse.xboxdrv", modifify it to your liking and run:

./xboxdrv -c examples/your-mouse-config.xboxdrv

---

### Post by Nicodemus144 on 2011-07-16
> **Grumbel said:**
> Quick and dirty way:

./xboxdrv --axismap X1=X2,-Y1=Y2,X2=X1,-Y2=Y1   --mouse  -s

More proper way, copy "examples/mouse.xboxdrv", modifify it to your liking and run:

./xboxdrv -c examples/your-mouse-config.xboxdrv


thanks, that did help me understand these maps better.  the part i was looking for was this:

--ui-axismap x2=REL_X:15:20,y2=REL_Y:15:20

so i can set up different binds for my other buttons, and just set the right analog to control the mouse cursor.

thanks Grumbel!

---

