---
title: "Kyocera KPC650 w/ Verizon Broadband (working!)"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by ksaling on 2005-10-16
I have this working (partially) on Ubuntu Hoary 5.04.  Here is what I did.

1.  Got the card activated by a buddy who uses the same card in his Apple Powerbook.  Apparently, the KPC650 is now supported on OSX and even comes with the Verizon AccessManager software.  So, he ejected his card and inserted mine, "Activated" it and updated the Preferred Roaming List (PRL).  Note: this step can also be done on a Windows box I suppose.

2.  Insert card in Ubuntu laptop

3. rmmod usbserial ; modprobe usbserial vendor=0xc88 product=0x17da

4. mknod /dev/ttyUSB0 c 188 0 ; mknod /dev/ttyUSB1 c 188 1

5. Created an /etc/wvdial.conf file like this:
[Dialer verizon]
Phone = #777
Password = vzw
Username = {my.verizon.phone#}@vzw3g.com
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 115200
Init = ATZ
Dial Command = ATDT
Stupid mode = 1


Now, I just do `wvdial verizon` to bring up the ppp0 interface and connect.  This works well for several minutes (haven't tested b/w yet, but it seems very fast).  


THE PROBLEM
After a few minutes, the ppp0 interface stops sending traffic.  I can kill the wvdial session, which drops the ppp0 interface, but I cannot redial.  At this point, the card seems to be in an unknown state.  wvdial just prints garbage on the console when I try to dial.  If I eject the card and reinsert, I can repeat this cycle.


SOLUTION?
I think this will fix it:
[http://www.junxion.com/opensource/linux_highspeed_usbserial.html](http://www.junxion.com/opensource/linux_highspeed_usbserial.html)

However, I cannot get this to compile on Hoary 5.04 using 2.6.10-5-686 or 2.6.10-5-386.  I get this:

```
root@jet:/usr/src/linux/drivers/usb/serial# gcc -D__KERNEL__ -I/usr/src/linux-source-2.6.10/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i386 -DMODULE -nostdinc -iwithprefix include -DKBUILD_BASENAME=usbserial -DEXPORT_SYMTAB -c usb-serial.c
```

```
In file included from /usr/src/linux-source-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-source-2.6.10/include/linux/usb.h:15,
                 from usb-serial.c:338:
/usr/src/linux-source-2.6.10/include/linux/irq.h:71: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux-source-2.6.10/include/linux/irq.h:73,
                 from /usr/src/linux-source-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-source-2.6.10/include/linux/usb.h:15,
                 from usb-serial.c:338:
/usr/src/linux-source-2.6.10/include/asm/hw_irq.h:28: error: `NR_IRQ_VECTORS' undeclared here (not in a function)
/usr/src/linux-source-2.6.10/include/asm/hw_irq.h:32: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux-source-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-source-2.6.10/include/linux/usb.h:15,
                 from usb-serial.c:338:
/usr/src/linux-source-2.6.10/include/linux/irq.h:78: error: `NR_IRQS' undeclared here (not in a function)
```

Anyone, have any pointers?

...Kevin

---

### Post by ksaling on 2005-10-20
Hrm.  Replying to myslef.  Not a good sign.

Well, turns out 2.6.10-5-686 was the problem.  I got this to compile in 2.6.10-5-386 and it works great.  Bandwith is consistently at or above 400Kbps and it runs for hours with no disconnects.

Unfortunately, the -386 kernel only sees the first 900MB of my 1GB of RAM.  :(  That was the whole reason I switched to -686 in the first place.  Looks like I have to choose between 1GB RAM or Verizon Wireless.

---

### Post by chz on 2005-12-23
I'm going to be getting a verizon card soon for work. I'm not sure if I will be getting the Kyocera, but do you think your instructions should work for any model, or is this specific to the one you have? I also have breezy on my laptop, could this affect its performance as well? Thanks in advance.

---

### Post by gaucho on 2006-06-14
WOW! Thanks for this! I am working on setting mine up, but being a complete noob to Linux I need some help.

I have never compiled code in Linux and would love to have a sort of step-by-step guide (i.e. what compiler do I use, where do i specify the kernel I'm currently on, etc...)

your help would be greatly appreciated it!

Thanks!

---

### Post by gaucho on 2006-06-14
[QUOTE=gaucho]WOW! Thanks for this! I am working on setting mine up, but being a complete noob to Linux I need some help.

I have never compiled code in Linux and would love to have a sort of step-by-step guide (i.e. what compiler do I use, where do i specify the kernel I'm currently on, etc...)

your help would be greatly appreciated it!

Thanks![/QUOTE]

Nevermind, I found a step by step but now I am having difficulty making sense of the instructions on the reffered link... studying up on my C...

---

### Post by jbwiv on 2006-06-29
[QUOTE=ksaling]
```
root@jet:/usr/src/linux/drivers/usb/serial# gcc -D__KERNEL__ -I/usr/src/linux-source-2.6.10/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i386 -DMODULE -nostdinc -iwithprefix include -DKBUILD_BASENAME=usbserial -DEXPORT_SYMTAB -c usb-serial.c
```

```
In file included from /usr/src/linux-source-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-source-2.6.10/include/linux/usb.h:15,
                 from usb-serial.c:338:
/usr/src/linux-source-2.6.10/include/linux/irq.h:71: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux-source-2.6.10/include/linux/irq.h:73,
                 from /usr/src/linux-source-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-source-2.6.10/include/linux/usb.h:15,
                 from usb-serial.c:338:
/usr/src/linux-source-2.6.10/include/asm/hw_irq.h:28: error: `NR_IRQ_VECTORS' undeclared here (not in a function)
/usr/src/linux-source-2.6.10/include/asm/hw_irq.h:32: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux-source-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-source-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-source-2.6.10/include/linux/usb.h:15,
                 from usb-serial.c:338:
/usr/src/linux-source-2.6.10/include/linux/irq.h:78: error: `NR_IRQS' undeclared here (not in a function)
```

Anyone, have any pointers?

...Kevin[/QUOTE]

Instead of using that gcc command, I switched in the kernel source top level directory (/usr/source/linux-whatever) and issued a "make modules". This worked, and recompiled the module. I then copied it over the existing one and was able to load it issueing the maxSize paramter. However, still slow with Verizon's network and disconnecting every two minutes or so.

What maxSize did you use?

---

### Post by Jim March on 2006-11-23
In case anybody else is wrestling with this, see my post here:

[http://ubuntuforums.org/showthread.php?t=157113](http://ubuntuforums.org/showthread.php?t=157113)

It's a weird but good solution involving hardware and zero drivers.

---

### Post by Praxicoide on 2007-01-06
I'm wrestling with this, but the solution you offer (which is a very good solution, in a way) is being sold here for US$400.00, which is lot more than what I can afford at the moment.

The guy with the service provider recommended that to me also.

Anyways, I'm trying to follow the maxSize patch, and in my /usr/src folder I have two folders: linux-headers-2.6.17-10 and inux-headers-2.6.17-10-generic

My understanding is that I have to cd to one of them and then put

```
 diff -Naur drivers/usb/serial/usbserial.c drivers/usb/serial/usbserial_junxion.
```

is this right? and from which one do I need to do it?

---

### Post by Megaqwerty on 2007-03-17
I have been frusterated with this issue as well. I'm glad someone figured out how to get it to work!

However, I can't proceed as I don't seem to have the usbserial.c file.

Is the an apt-get command or something to download it?

Thanks,

Megaqwerty

---

### Post by Megaqwerty on 2007-03-18
*deleted*

---

### Post by Megaqwerty on 2007-03-18
Okay, I have one (hopefully) final problem. When I use your command for compiling the source code (it seemed to work for you in the end) gcc has errors.

```
 
# gcc -D__KERNEL__ -I/usr/src/linux-source-2.6.17/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i386 -DMODULE -nostdinc -iwithprefix include -DKBUILD_BASENAME=usbserial -DEXPORT_SYMTAB -c usb-serial.c
usb-serial.c:1: error: expected identifier or &#8216;(&#8217; before &#8216;--&#8217; token
usb-serial.c:1:56: error: invalid digit "8" in octal constant
usb-serial.c:2:39: error: invalid digit "9" in octal constant
usb-serial.c:3: error: stray &#8216;@&#8217; in program
usb-serial.c:3: error: stray &#8216;@&#8217; in program
usb-serial.c:3: error: stray &#8216;@&#8217; in program
usb-serial.c:3: error: stray &#8216;@&#8217; in program
usb-serial.c:9: error: &#8216;SERIAL_TTY_MINORS&#8217; undeclared here (not in a function)
usb-serial.c:10: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;LIST_HEAD&#8217;
usb-serial.c:10: warning: parameter names (without types) in function declaration
usb-serial.c:11: error: stray &#8216;@&#8217; in program
usb-serial.c:11: error: stray &#8216;@&#8217; in program
usb-serial.c:11: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
usb-serial.c:11: error: stray &#8216;@&#8217; in program
usb-serial.c:11: error: stray &#8216;@&#8217; in program
usb-serial.c:13: error: expected identifier or &#8216;(&#8217; before &#8216;goto&#8217;
usb-serial.c:14: error: expected identifier or &#8216;(&#8217; before &#8216;}&#8217; token
usb-serial.c:15: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
usb-serial.c:16: error: expected identifier or &#8216;(&#8217; before &#8216;+&#8217; token
usb-serial.c:17: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;->&#8217; token
usb-serial.c:18: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;->&#8217; token
usb-serial.c:19: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;->&#8217; token
usb-serial.c:20: error: stray &#8216;@&#8217; in program
usb-serial.c:20: error: stray &#8216;@&#8217; in program
usb-serial.c:20: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
usb-serial.c:20: error: stray &#8216;@&#8217; in program
usb-serial.c:20: error: stray &#8216;@&#8217; in program
usb-serial.c:23: error: expected &#8216;)&#8217; before string constant
usb-serial.c:24: error: expected identifier or &#8216;(&#8217; before &#8216;+&#8217; token
usb-serial.c:25: error: expected identifier or &#8216;(&#8217; before &#8216;+&#8217; token

```

I really want this to work. Can someone post their patched usb-serial.c file? It would appear I didn't apply the patch correctly.

Thanks,

Megaqwerty

EDIT: nevermind, I got it working using make modules.

---

### Post by rushkoff on 2007-03-29
Can you post your step-by-step? I'm assuming it's for 6.10?

There's a bunch of people over on the EVDO forums who I want to share this with, as well.

---

### Post by Megaqwerty on 2007-03-29
> **rushkoff said:**
> Can you post your step-by-step? I'm assuming it's for 6.10?

There's a bunch of people over on the EVDO forums who I want to share this with, as well.

Well, I'm not the original poster, but here is how I got it to work:

First, you need to download the linux source code: ```
sudo aptitude install linux-source  
``` Then do this: ```
cd /usr/src
sudo tar xvjf linux-source-*.tar.bz2
cd linux-source-*/drivers/usb/serial
sudo nano patchfile
```

Put this text into the file: ```
 --- usb-serial.c	2005-11-27 04:33:51.000000000 -0600
+++ usb-serial.c	2005-11-27 04:39:13.000000000 -0600
@@ -361,6 +361,7 @@
    drivers depend on it.
 */
 
+static ushort maxSize = 0;
 static int debug;
 static struct usb_serial *serial_table[SERIAL_TTY_MINORS];	/* initially all NULL */
 static LIST_HEAD(usb_serial_driver_list);
@@ -1061,7 +1062,7 @@
 			dev_err(&interface->dev, "No free urbs available\n");
 			goto probe_error;
 		}
-		buffer_size = le16_to_cpu(endpoint->wMaxPacketSize);
+		buffer_size = (endpoint->wMaxPacketSize > maxSize)?endpoint->wMaxPacketSize:maxSize;
 		port->bulk_in_size = buffer_size;
 		port->bulk_in_endpointAddress = endpoint->bEndpointAddress;
 		port->bulk_in_buffer = kmalloc (buffer_size, GFP_KERNEL);
@@ -1434,3 +1435,5 @@
 
 module_param(debug, bool, S_IRUGO | S_IWUSR);
 MODULE_PARM_DESC(debug, "Debug enabled or not");
+module_param(maxSize, ushort,0);
+MODULE_PARM_DESC(maxSize,"User specified USB endpoint size");
```

Save, and exit. Then we have to apply the patch: ```
sudo patch -p0 < patchfile
```

We now have to go back to the top level and issue "make modules" ```
cd ../../../
sudo make oldconfig 
sudo make modules
```

Then, after that's finished, we need to make a backup of the old usbserial.ko, and replace it with our patched one. ```
sudo cp /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko.backup
sudo cp drivers/usb/serial/usbserial.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko
```

Now you can consider your driver patched.

You can change whatever you had to modprobe usbserial to add the newly added maxSize parameter so it looks like this: ```
sudo modprobe usbserial vendor=0x0c88 product=0x17da maxSize=2048
```

The methods in all the other posts to dial never worked for me, and I was too lazy to make them work, so I created some that do. If you want me to post them, just ask.

If you have further questions, I'll try to answer them as soon as I can.

Good luck,

Megaqwerty

---

### Post by rushkoff on 2007-06-13
Thanks! I'm just starting over with 7.04, and will try this on there.

---

### Post by Megaqwerty on 2007-06-13
> **rushkoff said:**
> Thanks! I'm just starting over with 7.04, and will try this on there.

Hi, I wanted to tell you that you will probably run into an error while following my steps to patch usb-serial.c due to the many updates to the kernel since my last post.

I am editing my tutorial to work with any kernel in the future (assuming the way linux handles things doesn't change too much in the future.) However, the one part of the tutorial that I can't guarantee will work with new kernels is the patchfile, so please post here if you need me to update it, and if for some reason the forums don't alert me to the new post, you can try PM'ing me as well.

Anyway, here is the updated patchfile for the 2.6.20 kernel: 

```
 --- usb-serial.c	2007-04-12 10:16:12.000000000 -0700
+++ usb-serial.c	2007-06-13 08:44:08.000000000 -0700
@@ -57,6 +57,7 @@
    drivers depend on it.
 */
 
+static ushort maxSize = 0;
 static int debug;
 static struct usb_serial *serial_table[SERIAL_TTY_MINORS];	/* initially all NULL */
 static LIST_HEAD(usb_serial_driver_list);
@@ -813,7 +814,7 @@
 			dev_err(&interface->dev, "No free urbs available\n");
 			goto probe_error;
 		}
-		buffer_size = le16_to_cpu(endpoint->wMaxPacketSize);
+		buffer_size = (endpoint->wMaxPacketSize > maxSize)?endpoint->wMaxPacketSize:maxSize;
 		port->bulk_in_size = buffer_size;
 		port->bulk_in_endpointAddress = endpoint->bEndpointAddress;
 		port->bulk_in_buffer = kmalloc (buffer_size, GFP_KERNEL);
@@ -1187,3 +1188,5 @@
 
 module_param(debug, bool, S_IRUGO | S_IWUSR);
 MODULE_PARM_DESC(debug, "Debug enabled or not");
+module_param(maxSize, ushort,0);
+MODULE_PARM_DESC(maxSize,"User specified USB endpoint size");
```

-Megaqwerty

---

### Post by JesCed on 2007-08-21
Hello. I also have a Kyocera KPC650 eVDO card, and would like to get it running under Ubuntu Feisty. I tried following the instructions on the first post of this thread, but after trying rmmod, I get the message "Module usbserial is in use by airprime", and that's as far as I get. Being new to these type of proceedings, I really don't know what to do. I guess I have to stop "airprime", but I don't know how to do it, or what it is.

Any help would be greatly appreciated.

---

### Post by Megaqwerty on 2007-08-21
```
sudo rmmod airprime
```

Hope that helps,

Megaqwerty

---

### Post by senor_smile on 2007-08-24
I tried the directions in the first post, and after typing the rmod command I get: 

```
ERROR: Module usbserial does not exist in /proc/modules
FATAL: Error inserting usbserial (/lib/modules/2.6.15-28-386/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted
```

help

---

### Post by Megaqwerty on 2007-08-24
The First message means that you have already removed usbserial from the kernel, and the second line is saying you need root privileges to do whatever you were doing there (this can be remedied by putting **sudo** in front of the command.

-Megaqwerty

---

### Post by senor_smile on 2007-08-24
Now, when I enter:

 rmmod usbserial ; modprobe usbserial vendor=0xc88 product=0x17da


I get:

ERROR: Removing 'usbserial': Operation not permitted

---

### Post by senor_smile on 2007-08-24
I tried doing  a :

wvdial verizon

and it seems like it's connecting, saying: 

--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
```
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Aug 25 08:05:01 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5538
--> Using interface ppp0
--> local  IP address 70.192.82.153
--> remote IP address 66.174.26.4
--> primary   DNS address 66.174.92.14
--> secondary DNS address 66.174.95.44

```

but I have no internet access.  It is even showing what looks like valid ip addresses.  I feel like I'm close.  What should I try now?

---

### Post by Megaqwerty on 2007-08-26
You are very close indeed! You need to run: ```
sudo route add default gw 66.174.26.4
``` Where **66.174.26.4** is your remote ip address.
You should now have internet access.

Enjoy,

Megaqwerty

---

### Post by Megaqwerty on 2007-09-12
Hi everyone! I've been having problems recently with disconnects due to the lack of a strong signal in my area. I've created a script to alert me when I lose the connection, and to re-establish the connection automatically.

Tell me what you think! (Change the values in bold to fit your card)
```
#!/bin/bash
# 
# Author: Megaqwerty (megaqwerty22 [at] gmail [dot] com)
# This script is licenced under the GPL. A copy of the GPL can be found in /usr/share/common-licenses/GPL

while true; do {

	if [ `pgrep ppp` ]; then {
		sleep 10
		
	}
	else 
	{
		zenity --info --title "warning" --text "Lost Connectivity."
		zenity --question --text "Reconnect EVDO?"
		answer=$?
		if [ $answer -eq 0 ]; then
			zenity --info --title "Connecting" --text "Connecting..."
			sudo pppd **/dev/ttyUSB0** 115200 debug noauth defaultroute usepeerdns connect-delay 10000 user **6191521229**@vzw3g.com password vzw show-password crtscts lock lcp-echo-failure 4 lcp-echo-interval 65535 connect "chat -v ABORT 'NO CARRIER' ABORT 'ERROR' ABORT 'NO DIALTONE' ABORT 'BUSY' ABORT 'NO ANSWER' '' ATZ OK-AT-OK ATDT#777 CONNECT \d\c "
			sleep **30**
			gateway=`tail /var/log/messages | grep remote | awk '{print $9}'`
			zenity --info --title "Adding gateway" --text "Adding $gateway as default gateway..." &
			sudo route add default gw $gateway
			continue		
		else
			exit
		fi
	}

	fi
}
done
```

EDIT: Change /dev/ttyUSB0 to wherever your card is mounted, 6191521229 to your card's number and 30 to how many seconds you want to wait until the script looks for the remote ip.

-Megaqwerty

---

### Post by Megaqwerty on 2007-11-13
I have finalized the script, and it operates completely  in a GUI now. You just need to change the variables at the top to fit your card. ```
#!/bin/bash
# 
# Author: Matthew Beaver (megaqwerty22@gmail.com)
# This script is licenced under the GPL. A copy of the GPL can be found in /usr/share/common-licenses/GPL

#You can modify these variables to fit your EVDO card
mountpoint="/dev/ttyUSB0"
phone_number="6198691229"



sudopass=`zenity  --entry --hide-text --title "Password" --text "Please enter your sudo password here"`
	
while true; do {

#Set sudo password
sudopwdset="false"
count=0
		while [ "$sudopwdset" != "true" ] && [ $count -lt 3 ]; do
			sudo -k
			count=$(($count+1))
			if (echo $sudopass | sudo -S echo -n "" 2> /dev/null); then
				sudopwdset="true"
			fi
		done
		unset count
		if [ "$sudopwdset" = "false" ]; then
			zenity --info --text "The password you provided seems to be wrong, so it will be re-asked in the terminal when needed."
			sudo -k
			sleep 2
		fi
#Check if process is alive

	if [ `pgrep ppp` ]; then {
		sleep 10
		
	}
	else 
	{
		zenity --question --title "Lost Connectivity" --text "Reconnect EVDO?"
		answer=$?
		if [ $answer -eq 0 ]; then
			zenity --info --title "Connecting" --text "Connecting..."
			tail -f -n 0 /var/log/messages 2>&1 | zenity --text-info --title "Connection Status" --width 600 --height 600 & 
			sudo pppd $mountpoint 115200 debug noauth defaultroute usepeerdns connect-delay 10000 user $phone_number@vzw3g.com password vzw show-password crtscts lock lcp-echo-failure 4 lcp-echo-interval 65535 connect "chat -v ABORT 'NO CARRIER' ABORT 'ERROR' ABORT 'NO DIALTONE' ABORT 'BUSY' ABORT 'NO ANSWER' '' ATZ OK-AT-OK ATDT#777 CONNECT \d\c "
			sleep 50
#Add gateway
			gateway=`tail /var/log/messages | grep remote | awk '{print $9}'`
			if [ ! $gateway == "" ]; then
				zenity --info --title "Adding gateway" --text "Adding $gateway as default gateway..." &
				sudo route add default gw $gateway
			
			else
				zenity --info --text "It doesn't look like you were assigned a gateway yet..." &
				sleep 4

			fi

			continue		
		else
			exit
		fi
	}

	fi
}
done
```

---

