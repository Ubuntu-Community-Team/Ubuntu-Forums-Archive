---
title: "IR REciever... Setup and use"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by encompass on 2006-03-13
I have purchased a "homebrew" reciever as according to:
[http://www.zapway.de/index1.htm](http://www.zapway.de/index1.htm)
As this was the recommended on to uses from:
[www.lirc.org](www.lirc.org)
I had once used my remote with a laptop and a remote control to control my XMMS music.
I would like to do simmilar things... but can't seem to get it to work.
I have the Com port.. I have only one in the back and only one shows in my Device Manager for gnome... and it is assigned to /dev/ttyS0
but I can get anything to work with the device.
I have been searching the lirc website, but am very unsatified with the way they have treated me.
I have now been searching here and have found nothing to help me with the device.  None of the steps anyone has given have worked for me.  I am confused.
It shouldn't be too hard due to the fact that it is such a simple device.  But I guess some of the simplest things can be the hardest to work with.
Any help would be appreciated.
I have tried the fallowing...
installed lirc and the lirc-modules
tried:
mode2 and did not recieve any imput..
sudo dpkg-reconfigure lirc and selected the homebrew model.
and nothing.  what can I do from here... feel free to message me.. I am more than happy to give any information you may way.  Even an account to take a look for yourself.
:-?

---

### Post by Stormbringer on 2006-03-13
Man - that thing deserves to be called "basic" ...

I assume you've selected the correct IR model for your receiver.

Start a terminal and type:

# lircd
To start the lirc daemon

# irw
This program will monitor the IR receiver. Now take a remote and press some buttons - do you see any output (this would tell us that the receiver is "seeing" the remote), or is there no output at all?

If there's no output, then you probably selected the wrong receiver type - check back with the lirc homepage and see what driver they recommend.

Just report back how it goes.

Storm.

[EDIT]
Corrected some typos.
[/EDIT]

---

### Post by encompass on 2006-03-13
I used...
> sudo dpkg-reconfigure lirc
and picked the homebrew... if you look at the link you can see the device.  it is the one recommended by lirc's website.
and I did both of those commands to no avail.  I didn't see anything.  I have checked my connections.  Even made sure my COM port was available in the bios.  I have tried weeding threw the lirc website.  But I get confused and lost.  They are not very verbose or organised.
I know I need to edit an lirc.conf file.  I have looked into /etc/lirc.conf and it gives me a file that says it is not configured.  Thats fine.  but if it had an example of what it looks like... or a list of drivers.  or someway to just uncomment them.  I would have a better understanding.  sorry... I am rabbling.
What is my next step.

---

### Post by encompass on 2006-03-13
here are the details of my outputs.
> jason@tabby:~$ sudo lircd --nodaemon
Password:
lircd 0.7.0[8466]: error in configfile line 10
lircd 0.7.0[8466]: reading of config file failed
lircd 0.7.0[8466]: lircd(any) ready
lircd 0.7.0[8466]: accepted new client on /dev/lircd
lircd 0.7.0[8466]: could not get file information for /dev/lirc
lircd 0.7.0[8466]: default_init(): No such file or directory
lircd 0.7.0[8466]: caught signal
Terminated


The accepted new... on is all after trying to run irw
irw gives me no output but throws me strait back to the terminal...

I have the fallowing in the configs...
hardware.conf> # /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc"
MODULES="lirc_dev lirc_serial"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

and lircd.conf
> #UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian
# Customized settings for lirc daemon

# The hardware driver to use, run lircd --driver=? for a list

DRIVER=default

# Hardware driver module to load
HWMOD=lirc_serial

DEVICE=/dev/lirc/serial

# Serial port for the receiver (for serial driver)
COM_PORT=/dev/ttyS0
DRIVER_OPTS="irq=4 io=0x3f8"
#These irq's and IO are according to my bios settings.

Thanks for your helps so far...

---

### Post by Stormbringer on 2006-03-14
The config files you posted look good for a start.

'irw' giving no output tells us that the kernel doesn't recognize your transceiver by default. You have to compile the necessary modules...

# sudo apt-get install lirc-modules-source
# cd /usr/src
# sudo tar -xzf lirc-modules.tar.gz

Now you have a directory called "modules" within /usr/src ... please follow the README inside that directory to compile the modules.

BE SURE TO USE GCC-3.4 SINCE ALL THE KERNEL STUFF IS COMPILED WITH GCC-3.4 INSTEAD OF THE DEFAULT GCC 4.0.x (sorry for shouting, but this is crucial).

Before starting the compilation set the envirmonment variable:

# CC=gcc-3.4
# export CC

As soon as the lirc-modules are compiled and installed the transceiver should start to work.

Storm.

---

### Post by encompass on 2006-03-17
>   3)   To build the LIRC modules, execute:
               make-kpkg --revision number modules_image

I am a little confused here... I know that it wants me to run this command... I have that program installed. but what would be the proper number.
I tried this...
> make-kpkg --revision linux_2.6.12_9_686_smp lirc
but got this...
> jason@tabby:/usr/src/modules/lirc$ make-kpkg --revision linux_2.6.12_9_686_smp lirc
Error: Unknown target lirc
use --targets to display help on valid targets.
jason@tabby:/usr/src/modules/lirc$

I could be totally wrong on this one.
Thanks thus far...

---

### Post by bartoni on 2006-03-24
Have you got thjis working? I'm having the same problems. I've a home made serial IR device that works fine with Windows. LIRC seems impossible to configure for such a simple device -- do we really need to recompile kernel modules to use a serial port?  It's driving me mad.   Please tell us if you have succeeded!

--Edit--
Update : I've had some success... It's still broken... but I'm a bit further now.

from  /usr/src/linux
make-kpkg  modules_image

This generates a deb, install it : 
dpkg -i lirc-modules-2.6.10_0.7.0.1-1ubuntu1+10.00.Custom_i386.deb

Will generate lirc_serial.o  in /lib/modules/...wherever...

That's as far as I've got. However LIRC still complains : "I couldn't load the required kernel modules".

Bah.

--Edit--

7 hours of trying all kinds of stuff and I'm still no better off.  I can compile 'lirc_serial.o'  but aparently I need a 'lirc_serial.ko'.  

Can someone please offer some advice. I'm seriously close to throwing this wretched machine out the window.

---

### Post by encompass on 2006-03-24
Well you got further than me... if you notice where I got stuck... Something ubuntu rocks with, that's why I use it, other things, people just don't know how.  I am going to try to contact the guy who made this reciever maybe they can help me.  I will post hee with an update... I figure the first one of us to get the solution should make a howto.  Anyway, thanks so far...](*,)

---

### Post by bartoni on 2006-03-27
I've finally got it working!

Here's what I did, I've been messing around with this for days, so I may have missed a something down here :

Remove / uninstall anything you've done so far, remove any lirc or linux source / headers you may have installed.  Start afresh.

grab linux source... (i'm using 2.6.10)

$sudo apt-get source kernel-source-2.6.10


get gcc if you haven't already

$sudo apt-get install build-essential

unpack linux source

$cd /usr/src/

$sudo tar xvjf linux-source-2.6.10.tar.bz2

link to /usr/src/linux

$sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux

$sudo make oldconfig 
$sudo make menuconfig
$sudo make include/linux/version.h 
$sudo make modules
(That line takes forever.)
$sudo touch /usr/src/linux/Rules.make 

get a copy of lirc  - dont use apt-get, its an old version and won't compile to .ko.  Go to LIRC's site and download a the tar.bz2, I downloaded version 0.8.0

Uncompress LIRC, in the lirc directory you just uncompressed do

$sudo ./setup.sh

use the on screen menus to select your serial IR device, then do save and configure.

$sudo make
$sudo make install

$sudo update-modules
$sudo depmod -ae
$sudo modprobe lirc_serial
$sudo modprobe lirc_dev

you should get a /dev/lirc  or /dev/lirc0

Clear the serial port :   (you'll have to  apt-get install setserial first)

$setserial /dev/ttyS0 uart none   (ttyS0  or ttyS1 depending on your COM port) 

finally : 
$sudo mode2 

will display lots of numbers on button presses! Hurray!

It works for me... kind of, when I reboot I lose the /dev/lirc/ and I have to reload the modules by hand. I'm hoping that's an easy fix though.

---

### Post by encompass on 2006-03-27
Hey now that last step I can do.... you at it too the end of your boot... at least in my Quickcam Messenger howto that I maintain I do it...  I han't the time right now... but here it the link to the howto...
[http://ubuntuforums.org/showpost.php?p=633963&postcount=5](http://ubuntuforums.org/showpost.php?p=633963&postcount=5)  The some of the lines have bad typo's  But you should get the idea...  In that case you have to rmmod the module... but I don't think you need to do that for this one...
Hope that it works for you... I don't ahve the time right now... but wanted to share this with you asap.  I will get started on your howto as quick as I can.
8)

Boy this kernel stuff... just not good at it... 
jason@tabby:/usr/src/linux$ sudo make menuconfig
> 
  HOSTLD  scripts/kconfig/mconf
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

make[2]: *** [scripts/lxdialog/ncurses] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2
jason@tabby:/usr/src/linux$ sudo apt-get install ncurses-devel
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ncurses-devel

Hmm...
haha ignored for the heck of it and got this too... if related or not I am not sure...
> jason@tabby:/usr/src/linux$ sudo make modules
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
  HOSTCC  scripts/genksyms/genksyms.o
  HOSTCC  scripts/genksyms/lex.o
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/conmakehash
make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make: *** [arch/i386/kernel] Error 2
jason@tabby:/usr/src/linux$


---

### Post by encompass on 2006-04-01
UPDATE!! I got it sorta working too...
I have installed the way that you said... I had to install ncurses to do the compile of the kernel... forgot about that simple answer...  and everything else compiled from there without a problem.
after running mode 2 yes.. I got a wonderfu bunch of numbers..
It works!  But... I have inserted the remote information into a new /lircd.conf file and lircd starts... but I can't see it doing anything for me... what is a good way to test if lirc is configured correctly... and how have you set it up to work with your computer.  xmms is a start for me cause that is what I used to use the ir with before. THANK YOU SO MUCH!  Lets just hope I can go yet a step further.
:-k

---

### Post by bartoni on 2006-04-03
I'm using it with an small 20 x 4 alpha numeric lcd on my PC, I aim to be able to scroll through a list of MP3s using the remote and to play them.

So far I've created my own php scripts for browsing the mp3s and I'm using LCD4LINUX to display the results on the lcd.  The PHP script is called navigate.php and it takes one parameter called button.

I'm using Lirc's IREXEC to execute my php script. /etc/lircrc looks something like this :

begin
remote = SKY_NAVIGATOR_RC-6
prog = irexec
button = UP
repeat = 2
config = ./home/david/lirc-scripts/navigate.php up
end

begin
remote = SKY_NAVIGATOR_RC-6
prog = irexec
button = DOWN
repeat = 2
config = ./home/david/lirc-scripts/navigate.php down
end

etc.. etc..

I'm using Mplayer to play mp3s. Mplayer has built in support for LIRC.  I've set up a config for mplayer that looks something like : 

begin
     button = BACK
     prog = mplayer
     config = quit
end

begin
     button = VOL+
     prog = mplayer
     config = volume +1
        repeat = 1
end


begin
     button = VOL-
     prog = mplayer
     config = volume -1
     repeat = 1
end

and then to use it with mplayer : 

mplayer -lircconf /path/to/conf.conf  - playlist /whatever/

I've an ongoing blog about this here : [www.plingboot.com](www.plingboot.com)

Hope that helps.

---

### Post by encompass on 2006-04-03
I will have to say... this is fantastic what your doing... could you create a howto on how to setup differnet programs and components involving IR homebrew recievers?  I would love to learn how... I especially need to learn the point between getting a signal from mode2 to teaching the remote to the computer with irrecord.  That is where I am now.  I even have a little webspace you could use.  I use it for my webcam page... I run a howto for ubuntu there.  Still getting worked on but it is... [www.slicehaven.com/ubuntu/](www.slicehaven.com/ubuntu/) Anyway...
Hope you can help me with those last steps.
PS I also wanted to say, I think you have to setserial before you mod probe for things to work correctly.  I could be wrong.

---

### Post by encompass on 2006-04-11
In addition... it would be important to note that you have to setseriel before placing the modules... and everytime you reboot...
and...
you need sudo for mode2 and with the mode2 I had to pick the device...
> sudo mode2 -d /dev/lirc0
then it worked
hope this helps... I have been working on programming my remote... it is not supported
and as a nother note... I get this when I run some programs... I think it is jsut because of my lirc file not setup write...
> jason@tabby:~$ sudo lircd -n
lircd: lircd(serial) ready
lircd: accepted new client on /dev/lircd
lircd: could not get file information for /dev/lirc
lircd: default_init(): No such file or directory
lircd: caught signal
Terminated

anyway, rockon linux... lets get this thing going...

---

### Post by encompass on 2006-04-11
I had to use raw mode but I got it to work...
I assigned all the different keys of my remote to different things... as attatched...
But how do I make those signals worth something when I start a program?
Thanks for the help...


MORE UPDATES:
I made a link from lirc0 to lirc
> sudo ln lirc0 lirc
don't know if that is bad or good... but anyway...
when I try to run mplay it actually atatches to the lirc without an error and lircd doesn't terminate and attatchs like this...
> jason@tabby:~$ sudo lircd -n /etc/lircd.conf
lircd: lircd(serial) ready
mpla    lircd: accepted new client on /dev/lircd

The updates just keep coming... well after finding the remote I wanted to use is somewhat broken... I will be getting a new one... but I did figure out how to change the settings in the .lircrc file so that they work with mplayer.  But I use mplay when I can't use anything else.  Is there a way to get the bindings for totem?  I will start a new thread for this question.
cool huh!?? huh!??
so now to setup my home .lircrc file to work with mplayer...
ideas?  I would love the help...

---

### Post by encompass on 2006-04-16
I have got it working... everyhting is bound and working... I jsut need to make the changes permenent and it will be working perfectly from now on.  My wife loves it.  And thanks for your help.  If your not doing it... I want to create a howto to make more details instructions, from setup to software bindings... to a growing collection of ideas.

---

