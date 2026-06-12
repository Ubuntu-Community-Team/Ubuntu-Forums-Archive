---
title: "Trying to get LT WinModem to work"
date: 2005-01-26
forum: Hardware &amp; Laptops
---

### Post by hyspah on 2005-01-26
it's been hell trying to get an LT WinModem work out for me...

anyone happens to have gone through this?

 [-X 

Linux is Joyous...
Getting hardwares to work is really intreasting...

---

### Post by recmar on 2005-01-27
Maybe you should try this.  The author claims it should work but on my acer with agere ac'97 modem doesn't. Maybe you will have more luck and experience to do this. 

"Here are some modem modules I compiled using the stock Warty kernel headers.

Lucent linmodem driver:
[http://www.vif.com/users/mzajac/ltm...8.31a9_i386.deb](http://www.vif.com/users/mzajac/ltm...8.31a9_i386.deb)

Ndiswrapper 0.11 (My prism2_usb device needs this to work)
[http://www.vif.com/users/mzajac/ndi...-3-386_i386.deb](http://www.vif.com/users/mzajac/ndi...-3-386_i386.deb)
[http://www.vif.com/users/mzajac/ndi...s_0.11_i386.deb](http://www.vif.com/users/mzajac/ndi...s_0.11_i386.deb)

SL-Modem modules compiled from the source package in universe:
[http://www.vif.com/users/mzajac/sl-....9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-....9.9-1_i386.deb)
###EDIT###
MULTIVERSE, not universe. You still will need the sl-modem-source package since sl-modem-daemon depends on it. Try to download the two sl-modem packages (daemon and source).
[http://archive.ubuntu.com/ubuntu/po....9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/po....9.9-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/po....9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/po....9.9-1_i386.deb)

sudo dpkg -i sl-modem-deamon* sl-modem-s*
it will complain about dependancies - they are all found on your cd. Get them with:
sudo apt-get -f install

By default, sl-modem-daemon will try to use the GPL alsa driver for the intel chipset) You may need to edit /etc/default/sl-modem-daemon to specify the device if 'auto' fails.
SLMODEMD_DEVICE=hw:0 #(or hw:1depends on your soundcard, I guess)

If it still don't work, download and install the modules (or make them youself...)

Then reconfigure sl-modem-daemon to use the slarm modules instead of the snd_intel8x0m module...

sudo dpkg -i sl-modem-modules*
sudo dpkg-reconfigure sl-modem-daemon

Sorry for the confusion.
If these do funny things to your system, It's not my fault...
I have described how to build these in earlier posts..."

---

### Post by az on 2005-01-27
I made those packages, and the ltmodem package build without error.  No one ever told me that it didn't work until somewhat recently.

Try this:

[www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a10_i386.deb](www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a10_i386.deb)

Now, tell me if this works.

I had to use Hoary's kernel-packge to work around a bug.  Somebody please tell me if this works, since I no longer have such a modem.

---

### Post by az on 2005-01-28
Not that I want to discourage you from trying this out...


When I booted this morning, and after X did not start, I realised that you should not install this package unless you actually have the hardware.   I had to stop the installation last night, after it hung, scanning for modem hardware.

I had to do a 

sudo depmod -a 

to resolve the small problem, but nonetheless, there you go.  I guess I should have uninstalled the package afterwards.

Probably, the remove script would have done that for me, so if you try to install the package and it it not the right driver for you, just apt-get removing the package should unscrew your system..

Just a thought.

Do not hold me responsible for this sort of thing.

---

### Post by Dana on 2005-01-28
Hmmm, what Lucent modem was this for? I trying to enable a winmodem in my ThinkPad A22M. The scanModem utility identifies the modem as:

Class 0700: 11c1:045c   Serial controller: Lucent Microelectronics LT WinModem (rev 01) (prog-if 00 [8250])
  SubSystem 8086:2205   Intel Corp.: Unknown device 2205
	Flags: medium devsel, IRQ 11
	I/O ports at 1840
	Memory at f4121000 (32-bit, non-prefetchable) [size=4K]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:045c 8086:2205 debian 2.6.8.1-3-386 3.3.4     i686


 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:045c
 DSP=1

It is a Lucent mini combo card.
To date I have not had any success. I obtained a kernel module driver that I believed was the correct one from [www.heby.de/ltmodem](www.heby.de/ltmodem), The binary being:
ltmodem-2.6.8-1-686_8.31a_i386.deb.
No luck though it is quite possible I was doing something incorrectly since I am fairly unfamiliar with Linux. In particular several errors I found in logs were:

1. a needed ppp protocol missing
2. not found devfsd.conf (daemon package needed for symbolic link support)

I've downloaded the module from the link you offered but I would prefer to know what it is purported to support before I try installing it. 

It has been a frustrating bit of business so far trying to get this to work and being pretty certain the modem is indeed supported.

Regards....

---

### Post by Dana on 2005-01-29
I went ahead and tried to install the kernel module. Still no success though this went slightly better in some respects.  Still, /etc/modprobe.conf is not found; insmod fails with both lt_modem.ko and lt_serial.ko; no proper aliases in modules.conf. I've been up until 1-4 in the morning the last week trying to work this out and I'm getting nowhere. It does appear to be the driver required by my winmodem though.

regards...

---

### Post by az on 2005-01-29
"insmod fails with both lt_modem.ko and lt_serial.ko"

This driver is built with the stock Warty kernel (386)  are you using that?

---

### Post by Dana on 2005-01-29
uname - r reports kernel release 2.6.8.1-3-386 and kernel version #1 Tue Oct 12 12:41:57 BST 2004. I think.

That is the stock Warty kernel is it not? 

Dana

---

### Post by Dana on 2005-01-29
A couple observations for which I do not know if any significance exists.

Looking at various logs produced during or after the attempt to install with dpkg I see reported that /etc/modprobe.conf is not found. And in indeed I do not find it on my drive... rather I see /etc.modprobe.d. Man pages seem to indicate they do the same thing? That is my interpretation. Does this mean that the binaries are looking for /etc/modprobe.conf and the install is failing because it is not there? Or does it also look for /etc/modprobe.d? 

Also reported is that no devfsd.conf file can be found, nor can I find it. Is this part of the "normal" Ubuntu install Again does this play a part in the ltmodem binary failing to install the drivers? The best I can tell the ltmodem package referenced in this thread is matched to the kernel installed on my laptop.

Dana

---

### Post by az on 2005-01-29
The package is pretty much made for Debian.  There are some differences with Ubuntu, but it is difficult for me to ell, since I do not have the hardware.

Would you do

sudo depmod -a
sudo modprobe lt_modem
sudo modprobe lt_serial

and tell me what happens?

---

### Post by Dana on 2005-01-30
Well, it is a laptop, so some peculiarity in the implementation is certainly possible.
I'll run your suggestions. I have in my notes that depmod -a was done, writing to /lib/modules/2.6.8.1-3-386/modules.*. Same notes show modprobe -v lt_serial and then insmod with "invalid module format" the result.... will look at it again.

---

### Post by Dana on 2005-01-30
I can confirm that depmod -a writes to /lib/modules/2.6.8.1-3-386/modules*. Didn't try to copy specifics. Probably I need to post to the linmodems.org, but I wanted to get an Ubuntu perspective on the problem first. I suppose I should consider trying to recompile the kernel with the ltmodem support but I have not compiled a kernel before and would prefer to get a handle on reaons for failure with the kernel module before taking that on.

The following is the output from the checkout script which is included with the .deb binaries to which I have added some annotations in upper case.


# this report may enable you to solve problems.
# But if further help is needed  send /usr/share/doc/ltmodem-2.6.8.1-3-386/utils/checkout.txt to [email]discuss@linmodems.org[/email]
# Please use as the following as the email Subject:
SUBJECT=(checkout, debian, testing/unstable, kernel 2.6.8.1-3-386)
DEVFS=
UNAME_A=Linux thinkpad 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux
VERS=/usr/share/doc/ltmodem-2.6.8.1-3-386 /usr/share/doc/ltmodem-2.6.8-1-686
start modules section -------------------
MODULES_AT=/lib/modules/2.6.8.1-3-386/extra
-rw-r--r--    1 root     root       560247 2005-01-27 23:05 lt_modem.ko
-rw-r--r--    1 root     root        19756 2005-01-27 23:06 lt_serial.ko
SITE_D=/lib/modules/2.6.8.1-3-386/extra/lt_modem.ko
SITE_S=/lib/modules/2.6.8.1-3-386/extra/lt_serial.ko
FAIL=
End modules installed section -------------------

modules.dep:
modules.dep:
modules.symbols:alias symbol:default_hwif_iops ide_core
modules.symbols:alias symbol:default_mtd_writev mtdcore
modules.symbols:alias symbol:default_hwif_mmiops ide_core
modules.symbols:alias symbol:nand_default_bbt nand
modules.symbols:alias symbol:GetLtModemInterface lt_modem
modules.symbols:alias symbol:default_hwif_transport ide_core
modules.symbols:alias symbol:default_mtd_readv mtdcore
modules.symbols:alias symbol:SetLtModemInterface lt_modem
modules.symbols:alias symbol:ltmodemDependency lt_modem
modules.symbols:alias symbol:get_default_font font
end modules dependencies section -------------------
Device node section -------------------
crw-rw----    1 root     dialout   62,  64 2005-01-28 23:14 /dev/ttyLT0
NODE=/dev/ttyLT0
GROUP= dialout
lrwxrwxrwx    1 root     root           11 2005-01-28 23:14 /dev/modem -> /dev/ttyLT0
LINK=/dev/modem
Driver loading section ----------------------------
modprobe -v lt_serial  THE OUTPUT FROM MODPROBE IS ESSENTIALLY IDENTICAL TO THE OUTPUT FROM INSMOD BELOW. THE DRIVERS ARE NOT LOADING  :sad: 
-----------------
insmod /lib/modules/2.6.8.1-3-386/extra/lt_modem.ko 
WARNING: Error inserting lt_modem (/lib/modules/2.6.8.1-3-386/extra/lt_modem.ko): Invalid module format
insmod /lib/modules/2.6.8.1-3-386/extra/lt_serial.ko 
FATAL: Error inserting lt_serial (/lib/modules/2.6.8.1-3-386/extra/lt_serial.ko): Invalid module format
-----------------
LOADED=
end Module loading section -------------------
Expected lines are:
---------------------------------
  # lt_drivers: autoloading and insertion parameter usage
  alias char-major-62 lt_serial
  alias /dev/modem lt_serial
  alias /dev/tts/LT0 lt_serial
  # options lt_modem vendor_id=0x115d device_id=0x0420 Forced=3,0x130,0x2f8
  # section for lt_drivers ends 
--------------------------------
of which the third alias line is only relevant to Systems using the device file system.  THERE IS THE DEVFSD AGAIN   :?: 
These lines provide for loading of the modem drivers whenever
there is a query to /dev/ttyLT0 , either directly or through its symbolic links.

Installed lines are:
----------------------------------
----------------------------------NO INSTALLED LINES FROM THE SECTION ABOVE


----------------------------------
alias char-major-108	ppp_generic
alias /dev/ppp		ppp_generic
alias tty-ldisc-3	ppp_async
alias tty-ldisc-14	ppp_synctty
alias ppp-compress-21	bsd_comp
alias ppp-compress-24	ppp_deflate
alias ppp-compress-26	ppp_deflate
----------------------------------

---

### Post by az on 2005-01-30
No.  I think that the problem may be that I used an updated kernel.  I do not have the time to install an un-updated Warty system and rebuild the drivers, so I used my updated Warty system.

If you want to try building the drivers, please do this:  (You will need to download some stuff and transfer it to your Ubuntu laptop.  I hope you have an USB key or something)

Remove the ltmodem modules package
Install build-essential from your cd.
Install the linux-source package and the kernel-package package (download it)
Get the ltmodem driver from [http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz](http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz)

cd /usr/src/tar xvzf linux-source*
cd linux-source*
cp /boot/config-2.6* .config
sudo make-kpkg --revision=9 --append-to-version=-3-386 kernel_headers
symlink the kernel source tree (/usr/src/linux-source-2.6.8.1-3-386) to /lib/modules/2.6.8.1-3-386/build

untar the ltmodem driver (anywhere, like in your /home) and build it (read the doc)

Please tell me how this goes.

---

### Post by Dana on 2005-01-30
I truly don't understand everything in your post regarding building the drivers for myself. When time permits I will see if I can locate everything you indicate I need and then see if I can follow the docs. Thanks.

---

### Post by Dana on 2005-01-30
Boy... do I feel as if I just discovered computers but I have been using them for over 20 years beginning with CP/M, through the flavors of Windows, OS/2 and a bit of Linux. This Thinkpad I am working with is now a triple-boot system with Windows 2000 pro, OS/2, and now Ubuntu. 

Yet I am clueless. Using Synaptic to grab the build-essentials off the CD, I am told it needs to download about 4Mb of files in addition to what is on the CD. And of course I have no working modem. In addition I looked at the repositories listed in Synaptic. [http://archive/ubuntu.com/ubuntu](http://archive/ubuntu.com/ubuntu) and I cannot figure out exactly what I need to download in terms of source and kernel-packages. And it fact when I attempt to download something I think may be correct it turns out to be a 10Kb file. I'm hopeless.

---

### Post by az on 2005-01-30
The problem is:
1-  The driver is not open source and so you only have one place to get it.  If you have trouble with that, you are stuck.
2-  The driver is compiled with either the kernel or the kernel-headers.  The kernel-headers were made with a tool called kernel-package.  The version of kernel-package used for the kernel-headers on your cd is buggy(?)  The driver and those headers do not play well together.  In the meantime, the kernel has been upgraded for security reasons.  This is why I think the drivers I build are not loading on your machine.

I will make another version with the most recent kernel-image. You will need to install that.

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/linux-image-2.6.8.1-4-386_2.6.8.1-16.10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/linux-image-2.6.8.1-4-386_2.6.8.1-16.10_i386.deb)


I will make the drivers as soon as my 10-month-old and two-year-old let me.  

Please stand by.

---

### Post by Dana on 2005-01-30
Hey... it really is a low-priority deal. I have a 32 month old boy in the house so I sympathize with trying to do things, especially if it is the problem of someone other than yourself. After getting the boy to bed I've been staying up until 1 or 2, even 4 in the morning trying to sort things out.

In the meantime I removed the kernel module and stuck an old pccard modem in. It is dialing out and reaching the local node but I have  few configuration problems to work out before it will actually make a connection with my ISP. That should not be too hard to figure out.

Dana

---

### Post by az on 2005-02-02
This will not work.

The build_deb script does not work for Ubuntu and I just do not have the time to hack it.

As well, I do not have the hardware, so I would not know if it works or not.  I am not going to build seven or eight tries and post them here.

Please install the linux-headers and install the driver from the link I provided above.  You may probably have success with the build_modules script since it may not try to do too many things as the build_deb does.

basically untar the driver
tar xvzf ltmdem*
cd ltmodem*
sudo build_module


Please tell me if it works!

---

### Post by Dana on 2005-02-03
Thanks for the help. I've save your suggestions/instructions and get back to the problem. For the moment I'm working with a pccard modem. Getting that to dial out and connect with the ISP modem but haven't figured out how to get the logon just yet. Almost there. Want to get that done so I can make use of Synaptic to get the parts I need to try and wake up the winmodem if that proves to be possible.

Dana

---

### Post by az on 2005-02-03
Try pppconfig.

The networking tool is not really made for modem users.

sudo pppconfig
Enter your information.  Add your user to the dip group in the advanced menu.
logout and back in so that the permissions change.
pon should get you on the net
poff should hang you up.

sudo tail -f /var/log/messages to see what is going on with your attempt to connect.
(run it in a different console)

---

### Post by Adler on 2005-02-05
I've lived through this about a year or so ago. I use the Linuxant drivers for both Dial-Up and Wireless. The Dial-Up Driver is free, but performs at a reduced baud rate versus the purchased version.

---

### Post by az on 2005-02-05
That is for a different chipset.  Conexant decided to support linux by selling the rights to the linux driver (or something to that effect) to linuxant.

Lucent makes a linux driver, but does not share the source code.  As it is, there is one guy who takes care of building scripts to link that driver (an object file) with kernel source.

Smart-link use various chipsets in their modems.  An older version of their linux driver mis-dialed when it found a compatible chipset, but from a different manufacturer.  I found this out a six in the morning when some guy started to phone me back.  A newer version stopped doping that, presumably because they started to use more dirfferent boards.  The newest versino of the driver (not in universe, but on the sl-modem website) has a licence which prevents you from using the driver unless you bought it from smart link.

There are several other chipsets like Motorola, ESS, US Robotics.  These are not supported.  PCtel is supposed to have been bought out by Conexant.

People should be aware of these things before they buy a modem or any other piece of hardware.  When companies change hands, the user is left behind.

---

### Post by graham on 2005-02-13
[QUOTE=azz]This will not work.
   
   The build_deb script does not work for Ubuntu and I just do not have the time to hack it.[/QUOTE]
   
   This may help to get it working, but I'm (obviously) not sure if it's the same problem you're referring to.
   
   [http://ubuntuforums.org/archive/index.php/t-9549.html]("http://ubuntuforums.org/archive/index.php/t-9549.html")
   
 For people who are just trying to get build_module to work this post is probably more useful (my original message, not so much the reply):
   
   [http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:16224:200411:dnokeploldfghkndppga]("http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:16224:200411:dnokeploldfghkndppga")
   
   > basically untar the driver
   tar xvzf ltmdem*
   cd ltmodem*
   sudo build_module
   
   
   Please tell me if it works!
   
   It worked for me with ltmodem-8.31a10, after I'd patched it slightly and moved the modules by hand (see second link above).
   
 I've also just got /dev/modem made automatically by udev, which means that I don't need to keep running the autoload script (joy of joys!).
   
 It turned out to be quite simple, once I'd worked out what I needed to do. Just add a file called /etc/udev/rules.d/10-local.rules, with this text in it:
   
    ```

  #ltmodem
   KERNEL="ttLTM0", SYMLINK="modem"
```
   
 My laptop is an IBM T23. I've no idea if the kernel device name will vary between models of the modem/other laptops. Try watching /var/log/syslog when the lt_serial module gets loaded to see what it's called (udev makes /dev/ttLTM0 automatically for me when the module is loaded).
   
 Adding a line containing the word lt_serial to /etc/modules means that all this now happens automatically for me at bootup, and I'm a happy camper.

---

