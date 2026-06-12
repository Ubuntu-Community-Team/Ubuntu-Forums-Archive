---
title: "How To: Nostromo n50/52 Speedpad Installation"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by Ironlenny on 2007-08-29
Here is the steps I took to install my Nostromo n52 on Kubuntu 7.04, but these instructions should still be valid for all flavors of Ubuntu, and the entire line of Nostromo products.

First download the Nostromo linux (nostromo_n50-1.3.tar.gz **NOT** nostromo_driver-0.1.3.tar.gz) driver from [http://sourceforge.net/project/showfiles.php?group_id=61608&package_id=91299&release_id=382235]("http://sourceforge.net/project/showfiles.php?group_id=61608&package_id=91299&release_id=382235")

Then download and install these dependencies:
libxtst-dev
g++
libgtk2.0-0
libxml++2.6-dev
fluid
libfltk1.1-dev
libxtst-dev
libgtk2.0-dev

type:
sudo modprobe evdev (please make sure that your speed pad is not plugged in)
sudo chmod a+rw /dev/input/event1

unpack nostromo_Driver-0.1.3.tar.gz
cd into the directory

Next type:
sudo ./configure
sudo make
sudo make install

Once you have install the driver, plug in your device **before** running the daemon and type:
nostromo_config

**You need to run nostromo_config before running nostromo_daemon**

You need to create a profile for your device before you can load the driver. Simple saving an empty profile will do.

Now type:
sudo nostromo_daemon

You should see an icon in your system try, and the mode lights on your device should cycle.

I hope this is helpful and I would appreciate any feed back.  Specific feed back that I would like includes whether or not the alternate install method works, is automake1.9 necessary, and how to uninstall the driver.

---

### Post by rBoa on 2007-09-01
I think the file you want to download is [http://sourceforge.net/project/showfiles.php?group_id=61608&package_id=91299]("http://sourceforge.net/project/showfiles.php?group_id=61608&package_id=91299")

The download file in the orig post does not have a "configure" file in it.

I have not been able to get the n52 working for either of the two paths shown above.

When should you plug-in the n52?

I think my problem is the nostromo_daemon does not keep running.

---

### Post by Sleaka J on 2007-09-06
I get an error message with the nostromo_n50-1.3.tar.gz file telling me that a gtk or xml library aren't installed and to try and set a couple of environment variables. I'll try and get the exact error message and post it here

---

### Post by ddoxey on 2007-09-06
Firstly, thank you **Ironlenny** for documenting you experience.

As for me, I downloaded and unpacked the source files.
One by one I installed the dependencies via Synaptic as I identified them in the output of **configure**.

Some of the dependencies appeared to be installed already and I was a little mystified.
However, I found that it's necessary to install the nnn-**dev** packages to get the libraries necessary for building new C++ modules.

After I installed all the dependencies I was still getting strange error messages about missing files in the **src** directory. I tried shifting things around with limited success. So I deleted the source files and did a clean extraction and **configure**. That seemed to make a big difference.

Bottom line, install the dependencies before attempting to build. Or, start clean after getting the dependencies installed ( via Synaptic ).

However, after all is said and done and things appear copasetic, I'm getting no dice with the Nostromo.

One question for Ironlenny. At what point to you finally plug in the Nostromo?
I've tried plugging in after starting the nostromo_daemon, and after.

**lsusb** indicates:[COLOR="DarkRed"]
Bus 002 Device 004: ID 050d:0805 Belkin Components Nostromo N50 GamePad
[/COLOR]

**dmesg** output:[COLOR="DarkRed"]
[ 1830.604000] usb 2-4: new low speed USB device using ohci_hcd and address 7
[ 1830.808000] usb 2-4: configuration #1 chosen from 1 choice
[ 1830.820000] input: HID 050d:0805 as /class/input/input8
[ 1830.820000] input: USB HID v1.00 Gamepad [HID 050d:0805] on usb-0000:00:02.0-4
[ 1830.840000] usb 2-4: string descriptor 0 read error: -32
[/COLOR]

It would appear that my next line of action is to identify the cause of: [COLOR="DarkRed"]string descriptor 0 read error: -32[/COLOR]

Any wisdom greater than my own is welcomed gladly.

---

### Post by Ironlenny on 2007-09-12
@rBoa:  You are right about wanting to download nostromo_n50.  I will make the correction in my guide.

@rBoa and ddoxey:  I am sorry that it wasn't very clear, but you must plug the control pad in before you run the daemon.  Other wise the daemon while not see it and shut down.  It also must be plugged in before you configure it.  I will clarify that in my guide.

@Sleaka J:  Did you download libgtk2.0-0 and libxml++2.6-dev?  Those dependencies are necessary for the configure script to run.

---

### Post by kilroo on 2007-09-15
I believe somewhere it was actually recommended that the driver not be run with root permissions. Actually, using sudo didn't even work for me and I don't know why.

This is how I set it up on Xubuntu Feisty.

Everything up until just before running the daemon is the same.

I ran lsusb from the terminal to get the vendor and product ID's for the speedpad.

I added the following line to /etc/udev/10-local.rules (I created that file for this purpose):

KERNEL=="event*", BUS=="usb", SYSFS{idVendor}=="050d", SYSFS{idProduct}=="0815", MODE="0660", GROUP="games"

Then I added the group "games", made all users whom I wanted to be able to use the gamepad members of it, added nostromo_daemon to my startup applications, and restarted.

On the Sourceforge forums for the project someone (I think it's the developer, actually?) suggests this rule instead:

KERNEL=="event*", SYSFS{product}="Nostromo SpeedPad2", NAME="input/%k", MODE="0660", GROUP="games" 

From my limited understanding of udev rules, I have no idea whether either of these means of identifying the device (product or vendor/product id's) is more certain to work universally. I also don't understand why he has the NAME-"input/%k" in there. But...what I did works.

---

### Post by Ironlenny on 2007-09-15
Thank you kilroo for the information.  I'll have to try it out and update my guide.  I can't answer your question though, I know even less about udev rules  then you do.

---

### Post by niko45 on 2007-09-21
sudo chmod 666 /dev/input/event*

this is what was needed for my install to keep the daemon running

---

### Post by oliver123 on 2007-10-11
Thanks for your detailed recipe! But there was just someone on #ubuntu who had problems with this because his config file was not found...

Turned out that "sudo nostromo_daemon" seemed to search at /root/.nostromorc while the config file was created in his normal home dir... Running "sudo nostromo_config" fixed that... maybe you can add that to your recipe?

---

### Post by Ironlenny on 2007-10-18
I tried to make that clear.  You **can not** run nostromo_daemon before you run nostromo_config.

---

### Post by Xceptiona1 on 2007-11-04
I received this error at the end of my ./configure process.
----------------
configure: error: Package requirements (gtk+-2.0 libxml-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the NOSTROMO_CFLAGS and NOSTROMO_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
-----------------
I tried apt-get gtk+-2.0 libxml-2.0, but that doesn't work. Am I needing to do somthing with the  NOSTROMO_CFLAGS and NOSTROMO_LIBS environment variables? If so, I have no clue what/how to do that.

PS. Let me know if you've found a better method. Thank you

---

### Post by jobyjoby on 2007-11-07
I have the same question as Xceptional, all dependencies listed in original post are installed

---

### Post by jobyjoby on 2007-11-09
(it was probably gtk2-devel, check if you have that)

---

### Post by Xceptiona1 on 2007-11-09
> **jobyjoby said:**
> I have the same question as Xceptional, all dependencies listed in original post are installed

libgtk2.0-dev

---

### Post by Ironlenny on 2007-11-15
I need some help cleaning up, and improving the how to. Specifically, I appear to have left out some dependencies.  If people would post a list of the packages they had to install, I can add them to how to. Also, if anyone has suggestions on how to improve the how to I would appreciate it.

---

### Post by money2themax on 2008-01-05
i just bought one of these how do i get it to run you weren't quite clear

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
money2themax@MX-Ubuntu-000:~/Desktop/nostromo_n50-1.3$ sudo make
make: *** No targets specified and no makefile found.  Stop.
money2themax@MX-Ubuntu-000:~/Desktop/nostromo_n50-1.3$ sudo make install

```

i keep getting this what's wrong?

---

### Post by money2themax on 2008-01-05
bumb i'm sry but i have to get this working otherwise i'll have to return it tomorrow

---

### Post by Knightsky on 2008-01-22
Hrm, I followed the steps in the first post to the letter, and haven't been successful. Everything seems to take, but the last sudo nostromo_daemon fails to do anything...no icon in the tray, and pressing buttons 6-10 still results in ASDF.

EDIT: Ah, there we go, yes, the sudo chmod 666 /dev/input/event* is necessary, followed by running nostromo_daemon

---

### Post by Colemanvt on 2008-03-28
I got everything going it worked great! except for the daemon it doesn't seem to want to start I did everything like you said run the conf file before running the daemon. Well... the daemon icon doesn't show up and the lights don't cycle when I run the daemon. Could it be the fact that it's running on another daemon set up to work with this device in 7.10? (I'm running Ubuntu 7.10)

I tried the sudo chmod 666 /dev/input/event* then running the daemon from the driver directory but nothing happened. how do I need to run the chmod? from any directory? do I just type sudo chmod 666 /dev/input/event* in to the terminal and hit ender and then sudo nostromo_daemon?

update: I had to go back and sudo nostromo_config to get it to work in the walk through it only said nostromo config. sorry :-)

---

### Post by marcus-brutus on 2008-05-03
> **Colemanvt said:**
> 
I tried the sudo chmod 666 /dev/input/event* then running the daemon from the driver directory but ....

The correct way of doing this is with udev rules.
In Hardy, for example, you add the following to /etc/udev/rules/50-nostromo.rules.
(should work with most modern versions of udev)

```

# Allow members of hid group to access Nostromo n50
# Note that the ProductID is different for the n52
KERNEL=="event*", BUS=="usb", \
    ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0805", \
    GROUP=="hid", MODE="0660"

```

To ensure that your user is a member of the hid group:
```

$ sudo usermod -aG hid $USER

```

This will avoid the problems that many of you seem to have with configs all over the place ;)




MODE CYCLE
==========
There have been some posts lamenting the lack of a "Mode Cycle" option.
See attached patch ([ATTACH]68702[/ATTACH]).

CONFIG MENU ITEM
================
It annoyed me that I had to start nostromo_config seperately.
Crude patch attached ([ATTACH]68703[/ATTACH]).

APPLYING PATCHES
================
```

$ tar -zxpf nostromo_n50-1.3.tar.gz
$ zcat configure_menu.patch.gz | patch -p0
$ zcat mode_cycle.patch.gz | patch -p0
$ cd nostromo_n50-1.3
$ ./configure && make && sudo make install

```

Then, all you need to do is add **nostromo_daemon** to your session startup.

Hope that helps some of you.

Regards,

Marcus.

---

### Post by Sleaka J on 2008-05-12
Ok, it's been a number of months since I last attempted to get my n52 up and running under Ubuntu. Before I was using 7.04, now it's 8.04 and about the only thing that has changed is my understanding of how Linux works.

But, I got it up and running.

Followed IronLenny's instructions (btw, you have libxtst-dev listed twice). But the daemon wouldn't load properly, so I used a combination of instructions from kilroo and marcus-brutus and created the rule ("/etc/udev/rules" didn't exist, but "/etc/udev/rules.d" did) and group (the n50 is "0805" and the n52 is "0815") and added a session to start the daemon on startup.

Now that I got it running perfectly, I'm never formatting this PC again. NEVER!!!

---

### Post by JoeG on 2008-05-12
First off, thanks SO much for this!  My N52 is now working flawlessly!  Is it possible to have the daemon run ONLY when the N52 is connected.  As in, as soon as the system detects that it's plugged in, start the daemon?

---

### Post by 99bluefoxx on 2008-05-17
got one of these as part of a trade i did on craigslist[awesome site =Dlook it up], and following instructions in first post, got it going perfectly :)[never have i known how to compile before XD now i do know how XP and the power of "./". knew the comand, never bothered with it...]
anyways, i wanted to use it as a shortcut launcher[its the n50], button one for a terminal, 02 for firefox, and such
problem is, gnome keyboard shortcuts doesnt detect it :/
and one got ideas how to do this?
also, it would be awesome to use the scroll on there for the compiz-desktop-zoom feature[and dpad to navagate XP]
thanks
-bluefoxx

---

### Post by BrokenPoet on 2008-05-23
I recently purchased a n52te (they no longer offer the n52, the n52te has some silly blue backlight in it, otherwise unchanged) and have been following the discussions/directions in the thread to set it up.  I am still having a problem getting the daemon to remain in the tray after startup.  I created the rules file, chmod'd, added the daemon to session startup, have a config saved, etc.  I can run the 'nostromo_config' utility fine, but when I test in a word processor or game, I only see the default settings.

   The only difference I can find between the old units and the new 'te' version is the Product ID.  Where the n50 was '0805' and the n52 was '0815', lsusb returns '0200' as the n52te product id.  I reflected the '0200' in my rules file  so it would map to the correct device.
   I know (from previous thread discussions) that the daemon will quit if it doesn't find a connected device.  Could it be checking for either a '0805' or '0815' Product ID, and ignoring my version?  If so, how can I alter it's behavior (trick it, add the '0200' ID to the source code, or force it to ignore the check results?)

   Any thoughts or suggestions?


Edit 5/24/08: I edited the 'daemon.cxx' file, substituting the n52te Product ID for the n52 Product ID in the initial '#define' statement and everything is now working.  The good news is that the n52te is responding exactly as an n52 would (i.e. no hardware changes requiring driver changes.)  Does anyone have a better understanding of the daemon program flow so we can update the driver for future n52te users, vice my crude fix?  I found about 5 places in the code where I _think_ mods are required, but I may be missing something deeper in the code.

---

### Post by Hooligan on 2008-05-30
How do I exactly get this n52te working. The config tool is running fine and I have a profile set. When I start the daemon I get no error, but I don't think it's working either. But when I touch the keys it does nothing more then "asdw.."

Please help me out.

---

### Post by BrokenPoet on 2008-06-23
After some further experimenting, it seems that the daemon is unable to shift LEDs on the n52te model.  I have verified that the configuration program is able to program keys to shift modes, and all modes (Normal, Red, Green, blue) work, but the LEDs do not change color to indicate the change to the user.  I am stuck with the blue LED on all the time following startup.
I can see where it's supposed to be changed in the code, but my C is way to rusty to attempt it.  Is anyone else actively working this?

---

### Post by fsenseman on 2008-07-05
I've got an n52te as well and so far everything is working now, except the LED is stuck on blue.  I'd also like to know if anyone has had any success in getting the LED to reflect the current mode.....

Thanks all for your help, it's nice to finally be able to use this thing :)

Fleet

---

### Post by Jack the R on 2008-07-14
I'm attempting to install the driver for an N52, no luck so far.

I'm using 64 bit 8.04 LTS.

I downloaded the most recent driver, nostromo_n50-1.4 (BTW, does anyone know what updates were made to this driver?  Does it include marcus-brutus's mode cycle and config menu item patches?).

I created /etc/udev/rules/50-nostromo.rules, and entered this code:

> # Allow members of hid group to access Nostromo n50
# Note that the ProductID is different for the n52
KERNEL=="event*", BUS=="usb", \
    ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0815", \
    GROUP=="hid", MODE="0660"

Being careful to set idProduct for the N52.

I've made 3 attempts at following the instructions on the first page.  I noticed I was missing gawk on the 2nd try (another dependency to add to the first page tutorial).  Here's the complete text of my third attempt - 

[Link](http://www.extinctionlevelevent.com/misc/linux/nostromo_install_try_01.odt)

I just noticed that I forgot to run sudo usermod -aG hid $USER.  I've tried, and got this -  

> jeremy@r1e:~/nostromo_n50-1.4$ sudo usermod -aG hid $USER
[sudo] password for jeremy: 
usermod: unknown group hid
jeremy@r1e:~/nostromo_n50-1.4$ sudo usermod -aG hid $jeremy
usermod: user hid does not exist


What should I be doing here?

I plugged my pad in after running sudo nostromo_config, and before running sudo nostromo_daemon.

What happened - nostromo_config popped up a control panel, which did not work.  The buttons were grayed out and nonfunctional.  I saved the empty file.  

Nothing seems to have happened after running nostromo_daemon.  The speedpad lights continued their flashing pattern, and the keys deliverd the familiar "asdf."

What went wrong?  I got a segmentation fault (whatever that is) on running nostromo_config, and there were numerous "nothing to be done for's" during the initial setup, but I don't know what I should have done different.

---

### Post by Jack the R on 2008-07-15
I've got it working.  Has anyone been able to enter modifying keys such as ctrl, shift, alt?  

Also, my led's keep flashing and the whole thing seems to be hanging up the system somewhat.  It's very noticeable as I type this, causing lots of errors.

---

