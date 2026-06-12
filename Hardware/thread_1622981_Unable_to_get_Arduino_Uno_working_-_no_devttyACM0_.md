---
title: "Unable to get Arduino Uno working - no /dev/ttyACM0 in IDE"
date: 2010-11-16
forum: Hardware
---

### Post by seanlano on 2010-11-16
I have just bought myself a new Arduino Uno development board. When I plug it into my computer (with the appropriate USB cable, of course) the TX light flashes a few times, and a device is listed at /dev/ttyACM0. I can confirm that Ubuntu recognises the device with:
```
dmesg
...
[16735.456541] usb 7-2: USB disconnect, address 7
[16736.688025] usb 7-2: new full speed USB device using uhci_hcd and address 8
[16736.886418] usb 7-2: configuration #1 chosen from 1 choice
[16736.889377] cdc_acm 7-2:1.0: ttyACM0: USB ACM device

```

I have a 64bit Ubuntu Maverick installation on a laptop and a 32bit Lucid installation on a desktop, both with Arduino-0021, librxtx, and Sun Java installed as I think it should be. However, the serial port /dev/ttyACM0 does not show up in the Arduino IDE on either machine (on the laptop the Tools -> Serial Port menu is greyed out, because there are no other serial ports; and on the desktop only /dev/ttyS0 and /dev/ttyS1 are listed, neither of which work in communicating with the Uno).

I have tried manually linking the librxtx library on the 64bit Maverick install, because I read the 32/64bit differences mean the included libraries don't work (or something like that), but to no avail. Then I tried the 32bit Lucid machine [because I read]("http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1272888964/3") that it should be working fine. Apparently not...

Do I still need to do something with Java and the librxtx thing? Since /dev/ttyACM0 shows up in the various Linux places, it would seem to be a problem with Java (typical) not being able to "see" it for some reason. What should I do?

---

### Post by rodrigo.toste.gomes on 2010-11-16
I have the same problem.
My arduino board seems to have had a problem with the USB board, and, although it seems to be working now, the bootloader appears to have disappeared. I want to confirm if that's the problem by reuploading it, through an AVR programmer I have, but it uses a ttyACM port, which the Arduino IDE doesn't detect (it only detects ttyUSB ports!).

---

### Post by seanlano on 2010-11-16
I managed to get it working in 32bit Lucid by installing the Arduino and librxtx packages [from the Natty repository]("http://packages.ubuntu.com/natty/arduino-core"). Then /dev/ttyACM0 showed up in the Arduino IDE, without any additional tinkering. I'm now about to try the same thing in 64bit Maverick...

---

### Post by seanlano on 2010-11-16
OK, I've got it all working! Yay!

I installed "[librxtx-java]("http://packages.ubuntu.com/natty/librxtx-java")", "[arduino-core]("http://packages.ubuntu.com/natty/arduino-core")", and "[arduino]("http://packages.ubuntu.com/natty/arduino")" from the Natty packages repo. 

I did not need to install Sun Java, **it works fine with OpenJDK**.

I love the way the Ubuntu devs make everything so easy. :)
But it would have been nice if Arduino 0021 could have been put into the Maverick repository to upgrade from 0018, then I would never have even needed to worry about this. Or maybe the Arduino team could make an Ubuntu PPA, that would be really awesome.

---

### Post by catnap on 2010-12-03
Thanks seanlano.
I have a similar problem and hopefully this may provide the answer.

I'm still running Lucid Lynx - What's the easiest way of installing the natty packages. The reason I ask is that I recently installed some mysql packages from a forward distribution.  This worked OK until a subsequent update broke the apt mechanism.

---

### Post by perryrt on 2010-12-05
> I'm still running Lucid Lynx - What's the easiest way of installing the natty packages.

I'm in the same boat. Looks like the Uno I just received only works with version 020 or better of the IDE - in the PPA package, I can only get 018.

Plus I have the same problem as the OP - I can see the USB connection at ACM0, but can't get the IDE to "see" it as a board.

Seanlano, how did you do it? I always thought that installing packages not designed for your particular release was A Bad Thing.

Any help would be appreciated.

---

### Post by seanlano on 2010-12-09
To help you out, look at the list of Natty packages ([http://packages.ubuntu.com/natty/allpackages](http://packages.ubuntu.com/natty/allpackages)) and find the ones you need. For me, I used the packages linked in my previous post, but this should work for any package. 

Once the list has loaded (it's very long, it could take a while) you can use Ctrl + F in Firefox to "Find" by name. Search for the package you want, and click on its link. Listed here too is the version of the package. Once you click on the link you will see a list of the package's dependencies, if you scroll down past this you will see "download". For some packages it will list the architecture (usually i386 or amd64), if not it says "all". Download the file by clicking on the architecture type you have, or "all" if the file is architecture independent. This will bring up a list of mirrors, choose whichever you want. 
Save the file somewhere, then once it's done go to this file. Right-click and select "Open with Ubuntu Software Centre" or "Open with GDebi Package Installer". Click "Install" and enter your password when prompted. Ubuntu will automatically install required packages, unless they cannot be found. To install "arduino" you need to install "arduino-core" first.

---

### Post by perryrt on 2010-12-09
Great - I'll give it a shot. Thanks for the help. It's fascinating - everytime I think I'm finally learning something about Ubuntu, I get reminded that "I am but an egg."

---

### Post by perryrt on 2010-12-09
...and I have a cheerfully blinking pin 13 LED now.:D

One note - I had the 018 version already installed (I was following the PPA instructions on the Arduino playground wiki) and when I tried to install the arduino-core package, it failed. Using synaptic to remove the -018 package fixed that. Works fine now.

Thanks.

---

### Post by lz1dsb on 2010-12-20
> **perryrt said:**
> ...and I have a cheerfully blinking pin 13 LED now.:D

One note - I had the 018 version already installed (I was following the PPA instructions on the Arduino playground wiki) and when I tried to install the arduino-core package, it failed. Using synaptic to remove the -018 package fixed that. Works fine now.

Thanks.

Hi perryrt, 
It looks like I'm in the same situation as you are. I see the same messages in the dmesg log, the only difference is that I'm using Ubuntu Karmic. Could you be more specific in what you did? You uninstalled the arduino IDE 0018 which came from the PPA and installed the arduino 0021 manually? Is that correct. Did you change anything on the other supporting packages? And what you see in dmesg now when you plug in the USB cable?

Cheers, 
Boyan

---

### Post by perryrt on 2010-12-20
Sure - sorry it's taken me a little while to get back to you (was a busy weekend.)

Actually, what I did specifically was to use Synaptic Package Manager to remove the -018 package. If you search on "arduino", the package should come up (with a little green square in front). If you right click on it, it will give you options - I chose "mark for complete removal" and then clicked the green "apply" checkmark.

Then I deleted the PPA back out of the repositories list.

Once that was done, I installed the arduino-core (do that one first) and arduino packages using seanlano's procedure above. (I had already installed the javarxtx package when I ran into this issue.)

And my current dmesg when I hook up the Arduino looks like:

```
[199895.112102] usb 6-2: new full speed USB device using uhci_hcd and address 3
[199895.305869] usb 6-2: configuration #1 chosen from 1 choice
[199895.846276] cdc_acm 6-2:1.0: ttyACM0: USB ACM device
[199895.848915] usbcore: registered new interface driver cdc_acm
[199895.849010] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```

Hope that helps! As I said above, I'm still definitely learning.

---

### Post by lz1dsb on 2010-12-21
Thank you Richard. When I'll give it a shot. I get absolutely the same output from dmesg. So it seems to me that the kernel is recognizing the device correctly but the Arduino IDE for some reason isn't able to communicate with it...

Regards,
Boyan

---

### Post by qlue on 2010-12-22
> **seanlano said:**
> To help you out, look at the list of Natty packages ([http://packages.ubuntu.com/natty/allpackages](http://packages.ubuntu.com/natty/allpackages)) and find the ones you need. For me, I used the packages linked in my previous post, but this should work for any package. 

Once the list has loaded (it's very long, it could take a while) you can use Ctrl + F in Firefox to "Find" by name. Search for the package you want, and click on its link. Listed here too is the version of the package. Once you click on the link you will see a list of the package's dependencies, if you scroll down past this you will see "download". For some packages it will list the architecture (usually i386 or amd64), if not it says "all". Download the file by clicking on the architecture type you have, or "all" if the file is architecture independent. This will bring up a list of mirrors, choose whichever you want. 
Save the file somewhere, then once it's done go to this file. Right-click and select "Open with Ubuntu Software Centre" or "Open with GDebi Package Installer". Click "Install" and enter your password when prompted. Ubuntu will automatically install required packages, unless they cannot be found. To install "arduino" you need to install "arduino-core" first.
Ok, I've installed arduino-core and arduino from the natty repositories! But I still can't select /dev/ttyACM0 from the Arduino IDE. It still only gives me two options, /dev/ttyUSB1 and /dev/ttyUSB2 so now what?

---

### Post by qlue on 2010-12-22
> **seanlano said:**
> OK, I've got it all working! Yay!

I installed "[librxtx-java]("http://packages.ubuntu.com/natty/librxtx-java")", "[arduino-core]("http://packages.ubuntu.com/natty/arduino-core")", and "[arduino]("http://packages.ubuntu.com/natty/arduino")" from the Natty packages repo. 

.

OOPS! my bad! :o
I didn't see read that properly!

---

### Post by lz1dsb on 2010-12-25
An update from my side. Today I removed the Arduino IDE version 0018 and now I run version 0021. I didn't do anything else. Now port ttyACM0 is accessible from Arduino IDE. I was also able to upload without any issues the demo Blink program. Here's the output from dmesg when I plug in my Arduino Uno board:

[ 2717.910159] usb 6-1: new full speed USB device using uhci_hcd and address 2
[ 2717.966383] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff88011830e000
[ 2718.111435] usb 6-1: configuration #1 chosen from 1 choice
[ 2718.180831] cdc_acm 6-1:1.0: ttyACM0: USB ACM device
[ 2718.183411] usbcore: registered new interface driver cdc_acm
[ 2718.183417] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

Cheers,
Boyan

---

### Post by ozwon on 2010-12-28
The installation of the natty packages worked for me! Even on maverick 64bit.  Thx guys

---

### Post by perryrt on 2010-12-29
> The installation of the natty packages worked for me! Even on maverick 64bit.

Great! I was wondering about the 64-bit thing myself.

Now, if I could just get processing to work, I'd be all set. I don't suppose any of you guys have figured that one out yet? I can get it to install and it works fine doing things on my computer like drawing items etc, but the interface between a processing sketch on my computer and an arduino sketch running on my arduino is a no-go.

What I'm actually trying to do is accomplish the last chapter of the O'Reilly "Getting Started With Arduino" book - it has you creating a three-color LED lamp that interacts with a sketch running on your computer (which in turn is reading a RSS feed and counting words.)

I cannot get the two to talk to each other...

Anyway, I can post this somewhere else if you guys would like, but since we're already most of the way there, I figured I would ask.

---

### Post by jaapdevries on 2011-01-01
Thanks guys I had the same problems and it is solved now.

---

### Post by WadeH2o on 2011-01-02
> **seanlano said:**
> OK, I've got it all working! Yay!

I installed "[librxtx-java]("http://packages.ubuntu.com/natty/librxtx-java")", "[arduino-core]("http://packages.ubuntu.com/natty/arduino-core")", and "[arduino]("http://packages.ubuntu.com/natty/arduino")" from the Natty packages repo. 

I did not need to install Sun Java, **it works fine with OpenJDK**.

I love the way the Ubuntu devs make everything so easy. :)
But it would have been nice if Arduino 0021 could have been put into the Maverick repository to upgrade from 0018, then I would never have even needed to worry about this. Or maybe the Arduino team could make an Ubuntu PPA, that would be really awesome.

Thank You!

---

### Post by rjanca on 2011-01-04
Hello, it seems that even though I have installed the natty packages lbrxtx, arduino-core, and arduni, I am still seeing only /dev/ttyS0 for a serial option; my dmesg shows that I am connecting via ttyACM0, so why doesn't it populate in the IDE?

just wondering - I am on lucid, and it's runnign arduino 0021 - i have both an UNO and MEGA 2560, no luck on either one...

please help - THANKS!

---

### Post by arduinux on 2011-01-14
I had a similar problem. In the Sun-Java installation I forgot to delete the rxtx libraries that I had copied into these folders.

After deleting these files arduino IDE recognizes /dev/ttyACM0 perfectly :-)

sudo rm /usr/lib/jvm/java-6-sun/jre/lib/amd64/librxtxParallel.so 
sudo rm /usr/lib/jvm/java-6-sun/jre/lib/amd64/librxtxSerial.so
sudo rm /usr/lib/jvm/java-6-sun/jre/lib/ext/RXTXcomm.jar

Then I installed the Natty version of arduino (the above mentionend 3 deb-Files) and ... it works for me.

Ubuntu Lucid + SunJava-JDK 1.6 64-bit

---

### Post by Renaissance-man on 2011-02-26
Try this link and it'll work out fine !!


[http://code-redefined.blogspot.com/2010/11/getting-arduino-working-on-ubuntu-1010.html](http://code-redefined.blogspot.com/2010/11/getting-arduino-working-on-ubuntu-1010.html)

---

### Post by trigoman05 on 2011-03-11
> **arduinux said:**
> 
After deleting these files arduino IDE recognizes /dev/ttyACM0 perfectly :-)

sudo rm /usr/lib/jvm/java-6-sun/jre/lib/amd64/librxtxParallel.so 
sudo rm /usr/lib/jvm/java-6-sun/jre/lib/amd64/librxtxSerial.so
sudo rm /usr/lib/jvm/java-6-sun/jre/lib/ext/RXTXcomm.jar



This absolutely helped! I also downloaded a new copy of the Arduino IDE from Google Code Project and that seems to have done it.

---

### Post by phil0stine on 2011-03-12
or 
D) None of the Above....

This poorly named thread saved the night for me ;)

[http://arduino.cc/forum/index.php/topic,52447.0.html](http://arduino.cc/forum/index.php/topic,52447.0.html)

---

