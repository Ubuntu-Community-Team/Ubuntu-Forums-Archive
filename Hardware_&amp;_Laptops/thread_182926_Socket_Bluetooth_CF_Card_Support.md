---
title: "Socket Bluetooth CF Card Support"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by Roner on 2006-05-27
**UPDATE:** For a patch that works for kernel 2.6.23 in Gutsy, see [post no. 11]("http://ubuntuforums.org/showpost.php?p=3627287&postcount=11").

This is a question for a kernel developer, or anyone else who may be able to help this newbie.

I own a Socket Bluetooth CF Card, which I use in my laptop's PCMCIA slot with an adapter.  It's a wonderful card, both in its performance, and due to the fact that it does not protrude at all.  It does not work out of the box, however.  I did a lot of googling and discovered that it did work out of the box on the 2.4 kernels (my revision of the card is revision G).

To make it work, the kernel file 8250.co under linux/drivers/serial needs to be changed as follows:

After the lines
```

        struct uart_8250_port *up = (struct uart_8250_port *)port;
        unsigned char cval, fcr = 0;
        unsigned long flags;

```
change the line
```

       unsigned int baud, quot;

```
to
```

       unsigned int baud, quot, max_baud;

```

After the lines
```

        /*
         * Ask the core to calculate the divisor for us.
         */

```
replace the line
```

       baud = uart_get_baud_rate(port, termios, old, 0, port->uartclk/16);

```
with the lines
```

       max_baud = (up->port.type == PORT_16C950 ? port->uartclk/4 : port->uartclk/16);
       baud = uart_get_baud_rate(port, termios, old, 0, max_baud);

```
and immediately after the following line, which reads
```

       quot = serial8250_get_divisor(port, baud);

```
add the following lines:
```

       /* 
        * 16C950 supports additional prescaler ratios between 1:16 and 1:4
        * thus increasing max baud rate to uartclk/4. The following was taken
        * from kernel 2.4 by Mathias Adam <[EMAIL PROTECTED]> to make the Socket
        * Bluetooth CF Card work under 2.6.13.
        */
       if (up->port.type == PORT_16C950) {
               if (baud <= port->uartclk/16)
                       serial_icr_write(up, UART_TCR, 0);
               else if (baud <= port->uartclk/8) {
                       serial_icr_write(up, UART_TCR, 0x8);
               } else
                       serial_icr_write(up, UART_TCR, 0x4);
       }

```

The line numbers of these modifications change between kernels, but searching for them and replacing them worked for me on 2.6.12, 2.6.13, 2.6.15 and 2.6.16.

After compiling the custom kernel and booting into it, one has to run the command
```

hciattach /dev/ttyS0 socket

```
to make the card available to bluetooth managers (it may be a different ttyS number).  This command hangs without the kernel patch.  It can be added to the session startup commands.

Here is my question: am I doomed to have custom kernels only because of that patch?  Does this patch affect the functionality of other devices, and if it does not, can it be considered for future releases of the ubuntu stock kernel?  I would appreciate any insight anyone has, and in the meanwhile, I'll be happy if my instructions help anyone with getting that card to work.

---

### Post by shizeon on 2007-04-27
Has anyone tried this on the feisty kernel?  I have an Socket CF revG and want to try to get it working.

Thanks!

---

### Post by Roner on 2007-04-28
**UPDATE:** For a patch that works on kernel 2.6.23 and Gutsy, see [post no. 11]("http://ubuntuforums.org/showpost.php?p=3627287&postcount=11") in this thread.

Good timing. I just got my 2.6.20.9 kernel to compile with another 8250.c patch.

First of all, download and extract the kernel sources to /usr/src, and symlink the directory to /usr/src/linux.

Now, create the patch file in /usr/src (name it anything you want, mine is 8250c_patch). Copy and paste into it (or simply use the file I attached to this post):
```

--- linux/drivers/serial/8250.c	2005-08-29 01:41:01.000000000 +0200
+++ linux/drivers/serial/8250.c	2005-09-16 12:18:14.000000000 +0200
@@ -7,6 +7,9 @@
  *
  *  Copyright (C) 2001 Russell King.
  *
+ *  2005/09/16: Enabled higher baud rates for 16C95x.
+ *		(Mathias Adam <a2@adamis.de>)
+ *
  * This program is free software; you can redistribute it and/or modify
  * it under the terms of the GNU General Public License as published by
  * the Free Software Foundation; either version 2 of the License, or
@@ -1652,6 +1655,14 @@
 	else if ((port->flags & UPF_MAGIC_MULTIPLIER) &&
 		 baud == (port->uartclk/8))
 		quot = 0x8002;
+	/*
+	 * For 16C950s UART_TCR is used in combination with divisor==1
+	 * to achieve baud rates up to baud_base*4.
+	 */
+	else if ((port->type == PORT_16C950) &&
+		 baud > (port->uartclk/16))
+		quot = 1;
+
 	else
 		quot = uart_get_divisor(port, baud);
 
@@ -1665,7 +1676,7 @@
 	struct uart_8250_port *up = (struct uart_8250_port *)port;
 	unsigned char cval, fcr = 0;
 	unsigned long flags;
-	unsigned int baud, quot;
+	unsigned int baud, quot, max_baud;
 
 	switch (termios->c_cflag & CSIZE) {
 	case CS5:
@@ -1697,7 +1708,8 @@
 	/*
 	 * Ask the core to calculate the divisor for us.
 	 */
-	baud = uart_get_baud_rate(port, termios, old, 0, port->uartclk/16); 
+	max_baud = (up->port.type == PORT_16C950 ? port->uartclk/4 : port->uartclk/16);
+	baud = uart_get_baud_rate(port, termios, old, 0, max_baud); 
 	quot = serial8250_get_divisor(port, baud);
 
 	/*
@@ -1733,6 +1745,19 @@
 	 */
 	spin_lock_irqsave(&up->port.lock, flags);
 
+	/* 
+	 * 16C950 supports additional prescaler ratios between 1:16 and 1:4
+	 * thus increasing max baud rate to uartclk/4.
+	 */
+	if (up->port.type == PORT_16C950) {
+		if (baud == port->uartclk/4)
+			serial_icr_write(up, UART_TCR, 0x4);
+		else if (baud == port->uartclk/8)
+			serial_icr_write(up, UART_TCR, 0x8);
+		else
+			serial_icr_write(up, UART_TCR, 0);
+	}
+	
 	/*
 	 * Update the per-port timeout.
 	 */

```

run from /usr/src
```

sudo cat 8250c_patch | patch -p0 --dry-run

```
It should inform you that it patched successfully 4 hunks (in my case it was 104 lines off, but still worked).  If all is well, repeat the command without the --dry-run switch.

After compiling the kernel, run the hciattach commands mentioned in my first post.

---

### Post by shizeon on 2007-04-28
Thanks for the quick reply!  I just compiled the 2.6.20 with beyond patches yesterday so going to apply this patch now and see what happens.  Fingers crossed.

---

### Post by shizeon on 2007-04-29
Roner,
  This worked great.   It was finally recognized and all functionality seems to be there.  I googled around and it looks like there were talks about submitting this patch to the kernel, but it was years ago.  Too bad.  If I ever become familiar with the process I will give it a stab.

  I spent a good chunk of time trying to get the audio profile to work though without luck.   By chance, have you gotten the card to stream audio out to a bluetooth headset?

Thanks again,
- Sean

---

### Post by Roner on 2007-04-29
Yes, I did, and submitted a howto just a few hours ago. Check it out [here]("http://ubuntuforums.org/showthread.php?t=426828&highlight=feisty+bluetooth+headset") and let me know how it goes.

---

### Post by shizeon on 2007-04-29
Crazy how in sync we are.   I've tried both the methods in your how-to, however I missed the kernel patch...  I was thinking it was my SCO version on the card.

```
[
root:~# hciconfig hci0 revision
hci0:   Type: UART
        BD Address: 00:02:C7:1C:B6:8F ACL MTU: 340:4 SCO MTU: 64:10
        HCI 15.3
        Chip version: BlueCore02-External
        Max key size: 56 bit
        SCO mapping:  PCM


```

Does your card return a "SCO mapping:  PCM" also?  

From the also docs I was attempting to track down this but not having luck. 

"If it prints "SCO mapping: PCM" then you might permanently change the setting using a command like "pskey mapsco 0" or "bccmd psset -s default 0x1ab 0" using bluez-utils-cvs but this is at your own risk.
"
Thanks again for your help.

---

### Post by Roner on 2007-04-29
I did not have your problem...
```

ron@RonLaptop:~$ hciconfig hci0 revision
hci0:   Type: UART
        BD Address: 00:C0:1B:07:DC:1C ACL MTU: 340:4 SCO MTU: 64:10
        HCI 16.4

```
And this is as far as the info goes. My BT card is CF, not a dongle.

---

### Post by shizeon on 2007-04-29
Okay.  Thanks for checking.  I'm using a Socket CF rev G card.   Will try some more stuff and see if I can get it to work.

---

### Post by shizeon on 2007-04-30
Got it working!  For anyone out there that has a revision G socket CF card and is having problems, here are the steps I took.

[LIST=1]
[*]Follow Roner's kernel patch Instructions on this thread.
[*]Look at Roner's other howto in this thread as it contains a sco patch that also needs to be applied (not specific to socket)
[*]Now the other fun

First run
	```
sudo hciconfig hci0 revision | grep SCO
```
	
If you see 

	SCO mapping:  **PCM**
	
then this might help!	The goal here is to change this to read "SCO mapping: HCI"

Go to [http://www.bluez.org/download.html](http://www.bluez.org/download.html) and download the latest bluez-utils.

Extract and run 
```
	
	./configure --enable-bccmd
	cd tools
	make
	sudo ./bccmd psset --stores psi mapsco 0
	sudo hciconfig hci0 revision | grep SCO

```

Hopefully you now see "SCO mapping: HCI".  If so now continue with Roners how-to at: 
	[http://ubuntuforums.org/showthread.php?t=426828&highlight=feisty+bluetooth+headset](http://ubuntuforums.org/showthread.php?t=426828&highlight=feisty+bluetooth+headset) and it should work.

It appears that you only have to do this setting once and it is then stored on the card.   Will update this if I find anything different over the next couple days.

Note: I have only tested the headset option as I don't have a2dp headpones  


[/LIST]

---

### Post by Roner on 2007-10-25
**UPDATE**

The patch has not yet made its way upstream, and the 8250.c file keeps changing, rendering past patches inoperable.  The attached file works as a patch for the vanilla 2.6.23 kernel, after upgrading it to 2.6.23.1.  To deploy it save it to /usr/src, make sure /usr/src/linux is a symlink to the source directory of the 2.6.23 kernel, and run:

```
sudo tar -xvf 8250.c.diff.tar
sudo patch --dry-run --verbose -p0 -i 8250.c.diff
```

If it reports all is well, run the command again, without the --dry-run switch.  The rest of the guide, with the hciattch command, remains the same.

---

### Post by shizeon on 2007-10-27
Thanks for the patch  Just upgraded to 2.6.23.1 and it worked like a charm.

---

