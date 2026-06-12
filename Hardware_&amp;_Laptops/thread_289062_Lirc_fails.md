---
title: "Lirc fails"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by anders.149 on 2006-10-30
Hi!

I have followed superm1's great howto on getting Lirc to work on Ubuntu Edgy at [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy) . I can't get Lirc to work though. After I have typed in "sudo /etc/init.d/lirc start" Lirc spits out the following: 

anders@anders:~$ sudo /etc/init.d/lirc start
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.


My remote came with my Leadtek Winfast 2000 XP (PAL) TV-tuner. I have typed in "lirc_gpio" as the module in /etc/lirc/hardware.conf and then followed the instructions in the howto. The only thing I didn't do was installing lirc-modules-source using apt-get since apt-get complained about its size. I took it of the repository using Firefox and installed it using GDebi instead.

Anyone know what could be causing this?


I also tried modprobing lirc_gpio with this result: 

anders@anders:~$ sudo modprobe lirc_gpio
FATAL: Error inserting lirc_gpio (/lib/modules/2.6.17-10-generic/misc/lirc_gpio.ko): Invalid request code


If anyone knows anything please tell me! =)

---

### Post by toganet on 2006-11-11
I'm getting the same error today, after having it working fine just hours ago.  The change I made was to add a second tuner to my system, and in so doing I believe I have severed the connection between the remote and the IR connection.

To be more precise, the card changed from being bttv0 to bttv1, so I am not sure if the lirc_gpio module knows which bttv driver to attach to.  I've checked all the config files that seem to be related, and nothing specifies a device that the lirc daemon should be using.

Looking at the devices in cat /proc/bus/input/devices, the remote seems to be there:

```
I: Bus=0001 Vendor=107d Product=6609 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:02:03.0/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=100003
B: KEY=8fc204 140000 0 0 0 0 0 90 40004001 1e0000 4400 100000 10000ffc
```

I'm going to keep messing with it, and post back here if I make progress.  ](*,)

---

### Post by mazirian on 2006-11-11
Are you using edgy?  I'd be interested in knowing how you built the lirc_gpio modules, since there seems to be a broken dependency.

---

### Post by toganet on 2006-11-12
I am using edgy, and I built the modules using a howto linked from these forums, though I can't locate it right now.  I did have to add some extra sources to my /etc/apt/sources.list, though:

```
#Mario's Lirc Repository
deb http://home.eng.iastate.edu/~superm1 edgy lirc
deb-src http://home.eng.iastate.edu/~superm1 edgy lirc
```

I had to build the modules from source using module-assistant, too.

I can post my lirc.conf and hardware.conf if you need them.

---

### Post by toganet on 2006-11-14
Excuse my cross-post, but I found my problem:  I needed to pass the lirc_gpio module the correct parameters. Duh!.

Turns out lirc_gpio is smart enough to detect all but two of its parameters via modprobe:  debug and card.  

Of course, since I had added a second card, lirc_gpio didn't know which one to attach to, so it defaulted to the first.  In my case, the Leadtek card is actually /dev/video1, so I issued:

```

sudo modprobe lirc_gpio card=1

```

I then started lirc via /etc/init.d/lirc start and it works!

---

### Post by ilias on 2006-11-15
I get the following error
 ```
FATAL: Module lirc_dev not found.
```

I used the same how to and I built the module-sources package with module assistant for the kernel version that I'm using.
everything went fine...
My infrared is a usual laptop infrared port, which is working properly with irda_utils...
Any guesses on what is going wrong

---

### Post by mazirian on 2006-11-15
Not sure what m-a command you used, but did you install the debs that m-a generated after it built the modules?  I only mention it because I made that mistake.

---

### Post by ilias on 2006-11-22
yes I did install them...but nothing
anyway...never mind I'll build a new kernel and see what I can do

---

