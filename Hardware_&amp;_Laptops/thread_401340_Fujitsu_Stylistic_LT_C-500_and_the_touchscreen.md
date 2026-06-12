---
title: "Fujitsu Stylistic LT C-500 and the touchscreen"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by Jodokos on 2007-04-04
Hello!

After a day of tinkering around, despair is near ;-)

I succuessfully installed ubuntu 6.10 on my Fujitsu Stylistic LT C-500. X-server works but unfortunately not the touchscreen.

As stated in:
[http://www.neurath.org/stylistic_lt_c500/](http://www.neurath.org/stylistic_lt_c500/)

There should be a serial device "/dev/ttyS4". But there isn't. After installing setserial, I had serial devices from ttyS0-ttyS3 in the /dev directory.

So I added the kernel-option 8250.nr_uarts=6 and finally I had my /dev/ttyS4.
But this device is of no use, I'm pretty sure that it is not connected to the touchscreen.

So which debugging steps do I have to do in order to detect the touchscreen?
I'm not new to ubuntu, but new to this hardware/system stuff.


Help is very much appreciated!
Thnx
J.

---

### Post by Jodokos on 2007-04-05
Update:

I tried 
```

/bin/setserial /dev/ttySxxx autoconfig
/bin/setserial /dev/ttySxxx uart 8250 irq 5 port 0xfd68 low_latency

```
with xxx ranging from 0-3 (the already existing ports).

Now, X gets input from the pen, but the cursor jumps around randomly when touching the screen.

the following is in my xorg.conf:

```

Section "InputDevice"
        Identifier      "tscreen"
        Driver          "fpit"
        Option          "Device"                "/dev/ttySxxx"
EndSection
```

```

mknod -m 666 /dev/ttyS4 c 4 68
```

created my node but it doesn't seem to be valid:

```

josef@prometheus:~$ setserial /dev/ttyS4 autoconfig
/dev/ttyS4: No such device or address

```

If somebody could help me, I'd be glad :-)

Greetings
J.

---

### Post by Jodokos on 2007-04-05
Argh, everytime I give up on the problem and post for help, I find the solution. After two days of tinkering around and trying every possible combination, I found the solution.

If somebody has the same problem at a later point:
[http://www.die.net/doc/linux/man/man4/fpit.4.html](http://www.die.net/doc/linux/man/man4/fpit.4.html)
Helped me. The correct settings are:

```

setserial /dev/ttyS3 autoconfig
setserial /dev/ttyS3 uart 16450 irq 5 port 0xfd68

```

And in xorg.conf:

```

Section "InputDevice"
  Identifier "mouse0"
  Driver "fpit"
  Option "Device"   "/dev/ttyS3"
  Option "BaudRate" "9600"
  Option "MaximumXPosition" "4070"
  Option "MaximumYPosition" "4020"
  Option "MinimumXPosition" "0"
  Option "MinimumYPosition" "0"
  Option "Passive"
  Option "SendCoreEvents"
EndSection

```

---

### Post by Northerner on 2007-10-08
J- If you're still around, thanks taking the time to post this info. Having just acquired a C-500, it will come in very useful. :KS

---

### Post by xaragon on 2008-02-17
So I've been frustrated by the annoyance of getting the touchscreen working on my Stylistic LT C-500.

I finally got it working tonight.  I wanted to post my solution to help others and so I can find it again after I mess up my tablet.  I apologize for my messy post; it is my first.

I attempted to follow all the other solutions that I found, but none of them worked for me.  My touchscreen is on /dev/ttyS1, this is different than most.

In the end I had to modify two files.
  **/var/lib/setserial/autoserial.conf**
  **/etc/X11/xorg.conf**

Before modifying autoserial.conf run  **dpkg-reconfigure setserial** and set the configuration to manual.  I then add the following line to the **/var/lib/setserial/autoserial.conf**.
  ```
/dev/ttyS1 uart 16450 port 0xfd68 irq 5
```

My **/etc/X11/xorg.conf** has the following lines that I retrieved from [http://translate.google.com/translate?hl=en&sl=de&u=http://www.grassmann.info/misc.html&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dfpit%2Bdriver%2Blinux%2Bc-500%2BttyS1%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DG]("http://translate.google.com/translate?hl=en&sl=de&u=http://www.grassmann.info/misc.html&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dfpit%2Bdriver%2Blinux%2Bc-500%2BttyS1%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DG"):

```
Section "InputDevice"
Identifier "Touchscreen" Identifier "touchscreen"
Driver "fpit" Driver "fpit"
Option "Device" "/dev/ttyS1" "Device" "/ dev/ttyS1"
Option "Baudrate" "9600" "Baud rate" "9600"
Option "MaximumXPosition" "4096" "MaximumXPosition" "4096"
Option "MaximumYPosition" "4096" "MaximumYPosition" "4096"
Option "MinimumXPosition" "0" "MinimumXPosition" "0"
Option "MinimumYPosition" "0" "MinimumYPosition" "0"
EndSection
```

```
InputDevice "touch screen" "SendCoreEvents"
```

Well I'm glad that I finally got mine to work, I hope this helps you.

---

### Post by EagleGCIL08 on 2008-04-17
i also have this tablet, can you provide me with a basic walkthru on how you installed ubuntu on it? i would greatly appreciate it, i do not have a  CD or Floppy for mine.

Thanks in advance

---

### Post by nise8181 on 2008-04-21
I was lucky to get xubuntu 7.10 installed and finaly xserver runs fine at 800x600 but when going ahead to install the touchscreen drivers i got stock because the missing file /bin/setserial

Where does it come from? do i have to install something else?


(to install xubuntu you should realy visit [http://www.neurath.org/stylistic_lt_c500/](http://www.neurath.org/stylistic_lt_c500/) and follow the instructions until the touchscreen installation)

---

### Post by nise8181 on 2008-04-23
hey xaragon.

```
/dev/ttyS1 uart 16450 port 0xfd68 irq 5
```

was already set.

but what do you mean with?

 ```
InputDevice "touch screen" "SendCoreEvents"
```

Where do I have to set that?

Could you post your complete /etc/X11/xorg.conf file please

And finaly should it work straight after the changes or do I have to restart the system or anything like that?

---

### Post by JJAAES on 2008-07-08
I bought one of these  Fujitsu Stylistic LT C-500 off of ebay.

I have never been able to get it to work completely - first had a corrupt register.

Ebay person sent me an exchange.

Now - no pen calibration, no pen, touchscreen won't work and it gets very hot.

Has anyone else had all of these problems and have you tried to return it for a refund?

I have spent weeks reading the internet and trying everything to correct the problems with no success.

I am tired of this thing that I thought would be a great little gadget.

---

### Post by brousch on 2008-07-10
I also recently bought one of these on eBay. The vendor had a pretty large stock of them, so we probably bought from the same vendor (laptopenterprise). Mine worked well with the pre-installed Win2k (except for the minuscule virtual keyboard), but I've been working on getting Ubuntu Hardy Installed.

To install Hardy, I moved the hard drive to my laptop (IBM Thinkpad T30) and installed Ubuntu 6.04.1 Desktop. I think it's important that the install be done on an Intel processor because that's what the Stylistic uses. I also installed the following packages:
[LIST]
[*]xvkbd - Virtual keyboard
[*]setserial - used to set up the touchscreen device
[*]fpit - drivers for the touchscreen
[/LIST]

I then moved the hard drive back to the Stylistic and everything except the touchscreen worked correctly. When using xvkbd, the following command as a custom Panel button sets it up nicely across the bottom of the screen:
```
xvkbd -geometry 800x100-10-10 -no-functionkey -modal
```

I've been using the information at [this page]("http://www.neurath.org/stylistic_lt_c500/") and [this page]("http://www.xfree86.org/current/fpit.4.html") to work through the touchscreen config. The instructions are similar to those in the posts in this thread. He uses ttyS4 which does not exist for me, but I disabled the built-in COM port in the BIOS. I believe my touchscreen is ttyS3. As soon as I get a working touchscreen I'll post my xorg.conf here.

In the meantime, hopefully my suggestions will get you going with a USB mouse.

---

### Post by brousch on 2008-07-14
Getting Hardy running on the LT C-500 was simple - except the touchscreen. After a couple of days of frustration, I noticed there is [a bug filed against the fpit driver in Hardy]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/220869"). I don't see any work-arounds, so I'm going to go back and try Gutsy.

---

### Post by bornagainpenguin on 2008-07-15
> **brousch said:**
> Getting Hardy running on the LT C-500 was simple - except the touchscreen. After a couple of days of frustration, I noticed there is [a bug filed against the fpit driver in Hardy]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/220869"). I don't see any work-arounds, so I'm going to go back and try Gutsy.

Have you had any luck with this?  I'm thinking about buying one of these off eBay myself and I'd like to know if Ubuntu will be an option for me...

--bornagainpenguin

---

### Post by brousch on 2008-07-17
I didn't have much more luck with Gutsy. Once again, everything except the touchscreen works. The fpit driver and settings mentioned previously in this thread don't crash anything, but they also don't seem to do anything.

I will probably try Dapper next.

---

### Post by signifer123 on 2008-07-22
Using the settings listed by xaragon, but i replaced /dev/ttyS1 with /dev/ttyS3. I didn' try on ubuntu because i had a debian disk with me at the time. But it worked for me. the wireless card that was tossed in has drivers avalable for download from realtek, or using ndiswrapper on the windows ones worked in ubuntu, but not debian. I messed up somehow and I have to put setserial in /etc/init.d/rc.local, it kept blocking all my other setserials, just in case anyone else has problems with it.

Unfortunately the touchscreen does not work at the login screen. :(

Anyone know of a DE meant for touchscreens?

---

