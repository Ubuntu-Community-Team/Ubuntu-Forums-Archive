---
title: "Epson scanner needs to be replugged to work"
date: 2014-03-11
forum: Hardware
---

### Post by BobvanderPoel on 2014-03-11
I've had this scanner, Epson Perfection V30, for a number of years and it's always been just fine. On my latest computer it's giving me headaches.

Yes, I have the proper epson drivers from [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and, yes the scanner works fine if I plug the USB in (this means I turn the scanner on, pull the usb plug from the scanner, and then plug it back in).

But, if I just turn the scanner on the system will not "find" it. Actually, I think it is finding the scanner fine. The scanner makes a few seeking noises (which it always does) and my /var/log/syslog file tells me that it's there:

```

Mar 11 15:06:27 Mellowood kernel: [363747.832180] usb 3-14: new high-speed USB device number 19 using xhci_hcd
Mar 11 15:06:28 Mellowood kernel: [363747.851412] usb 3-14: New USB device found, idVendor=04b8, idProduct=0131
Mar 11 15:06:28 Mellowood kernel: [363747.851421] usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Mar 11 15:06:28 Mellowood kernel: [363747.851427] usb 3-14: Product: EPSON Scanner
Mar 11 15:06:28 Mellowood kernel: [363747.851432] usb 3-14: Manufacturer: EPSON
Mar 11 15:06:28 Mellowood kernel: [363747.851666] usb 3-14: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
Mar 11 15:06:28 Mellowood kernel: [363747.851677] usb 3-14: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
Mar 11 15:06:28 Mellowood kernel: [363747.904111] WARNING! power/level is deprecated; use power/control instead
Mar 11 15:06:28 Mellowood colord: Device added: sysfs-EPSON-EPSON_Scanner

```

But, running xsane just times out with a "scanner not found" message.

If I leave the scanner on for awhile and try again, it's the same story. Plug plug and insert .. all is well.

I recall a long time ago I needed to change a file ... something about a lamp delay, but I can't find anything like that to twiddle with.

Suggestions?

---

### Post by helourx on 2014-05-14
I've tried everything what I've found on the web (disabling autosuspend USB, etc.) 
Only ONE solution works for me. It is the "reactivating USB port".

Here is my script which needs root privileges. If you want to run it without password you can set proper SUDOers line for it.

```

#!/bin/bash

# Retrieved from "lsusb" command:
# Bus 003 Device 007: ID **04b8:014a** Seiko Epson Corp.
IDVendor=04b8
IDProduct=014a

for x in /sys/bus/usb/devices/*; do 
    if [ "$IDVendor" == "$(cat "$x/idVendor" 2>/dev/null)" -a "$2" == "$(cat "$x/IDProduct" 2>/dev/null)" ]; then
        echo 0 > $x/authorized
        sleep 1
        echo 1 > $x/authorized
    fi
done

```

---

### Post by BobvanderPoel on 2014-06-30
Sorry to be so late with a reply on this. But, I can confirm that the solution DOES WORK.

Thanks.

Now, I'm wondering if I should just create a script to run this to actually run xsane? Not sure how to go about adding the right privilege to run a script as root (dark recesses of my brain tell me it's not that easy ... )

BTW, one does need to check the IDProduct line and set it properly. In my case (Perfection V30) it's 0131.

I've been thinking all along that it was a motherboard/device error. But, perhaps its the system software?

---

### Post by david_stewart2 on 2014-07-01
I have the same problem with Epson V370 printer and Microsoft Mouse.  I have noticed with the scanner that when I unplug it and replug it in that device no inrements up.  The scanner will now work for both simple scane & linux scanner.  Close the program down and to get the scanner to work have to unplug and plug in again.  This also applied to my mouse but this would stay operational until the next start up.  I ran modprobe -r floppy and the mouse is now operational for 95% start up.  This is on a Acer V5-573G the old desk top has no problems.  I think the USB port is going to sleep.  Running Utopic 64 bit on both machines.

---

### Post by helourx on 2014-07-11
> **BobvanderPoel said:**
> Sorry to be so late with a reply on this. But, I can confirm that the solution DOES WORK.

Thanks.

Now, I'm wondering if I should just create a script to run this to actually run xsane? Not sure how to go about adding the right privilege to run a script as root (dark recesses of my brain tell me it's not that easy ... )

BTW, one does need to check the IDProduct line and set it properly. In my case (Perfection V30) it's 0131.

I've been thinking all along that it was a motherboard/device error. But, perhaps its the system software?

Solution is very simple ;). Please follow steps below:

1. Create **executable** bash script **reconnect_scanner_usb** (You don't need the .sh extension) with correct **IDVendor** & **IDProduct** of your scanner:
```
#!/bin/bash
#

# Retrieved from "lsusb" command:
# Bus 003 Device 007: ID 04b8:014a Seiko Epson Corp.
IDVendor=*04b8*
IDProduct=*014a*

for x in /sys/bus/usb/devices/*; do 
    if [ "$IDVendor" == "$(cat "$x/idVendor" 2>/dev/null)" -a "$2" == "$(cat "$x/IDProduct" 2>/dev/null)" ]; then
    echo 0 > $x/authorized
    sleep 1
    echo 1 > $x/authorized
    fi
done

```
2. Add next line into **/etc/sudoers** file (You need root's privileges) where **user** is your username:
```
*user*    ALL=(ALL) NOPASSWD: /*path-to-script*/reconnect_scanner_usb
```

3. Create startup sript (You can associate it with an icon. It depends on your desktop - GNOME/KDE)
```
sudo /*path-to-script*/reconnect_scanner_usb; xsane
```

---

### Post by BobvanderPoel on 2014-07-11
Thanks again. This sudo stuff is a complete mystery to me :)

However, I do have it working well enough (with the above stuff) to be a happy camper.

Here's what I've done:

 1. Create a script (with the reset code). I've name it "reset-scanner-bin" and placed it in /home/bob/bin. Set as executable.

 2. Mark this in /etc/sudoers. Use the proper program to modify this file: visudo. So, you need to issue a command to edit "sudo visudo". Add the line:

   bob ALL=(ALL) NOPASSWD: /home/bob/bin/reset-scanner-bin

3. Create a calling script, again make it executable. In my /home/bob/bin I have "reset-scanner" with a single line:

    sudo /home/bob/bin/reset-scanner-bin

Now, when my scanner doesn't work I can type "reset-scanner" and all's well.

I could do a few other things:

 1. Call up reset-scanner-bin from the command line. But, I need to do this with a preceeding sudo. And, since root doesn't have my path I would need to add that. So, "sudo /home/bob/bin/reset-scanner-bin" also works. No password.

 2. Put the script in a path that root knows about. But, still need to add the sudo.

I leave my scanner on, so I really only need to do this on occasion. Probably after a power cycle, but I'm not sure. I might just put the "xsane" command on the line like you suggested and be done with the problem. 

After working though this a few times it seems to make sense :)

Of course, the $64 question is: why is this needed at all. Used to work just fine for many years!

---

### Post by helourx on 2014-07-14
This second solution is better because **don't change**(increase) **Bus: Device** number, but you need compile simple file.

1. Compile .c code below with command: gcc -o usbreset usbreset.c:
```
/* usbreset -- send a USB port reset to a USB device */
#include <stdio.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <linux/usbdevice_fs.h>

int main(int argc, char **argv)
{
const char *filename;
int rc, fd;

    if (argc != 2) {
        fprintf(stderr, "Usage: usbreset device-filename\n");
        return 1;
        }
        
    filename = argv[1];
    fd = open(filename, O_WRONLY);
    if (fd < 0) {
        perror("Error opening output file");
        return 1;
        }

    printf("Resetting USB device %s\n", filename);
    rc = ioctl(fd, USBDEVFS_RESET, 0);
    if (rc < 0) {
        perror("Error in ioctl");
        return 1;
        }
        
    printf("Reset successful\n");

    close(fd);
    return 0;
}
```

2. Copy binary file usbreset to /usr/bin/ directory:
```
sudo cp usbreset /usr/bin/
```

3. Create executable bash script: /path-to-script/reset_usb (You don't need .sh extension):
```
#!/bin/bash
#

# Retrieved from "lsusb" command:
# Bus 003 Device 007: ID 04b8:014a Seiko Epson Corp.
IDVendor=04b8
IDProduct=014a

# You need add line like this into sudoers file:
# user    ALL=(ALL) NOPASSWD: /path-to-script/reset_usb
# where 'user' is name of user which runs script

line=`lsusb|grep $IDVendor:$IDProduct`
bus=`echo $line|awk '{print $2}'`
dev=`echo $line|awk '{print $4}'|sed 's/:$//'`
usbreset /dev/bus/usb/$bus/$dev
```

4. Add next line into /etc/sudoers file (You need root's privileges):
```
user    ALL=(ALL) NOPASSWD: /path-to-script/reset_usb
```

5. Create xsane startup sript (You can associate it with an icon. It depends on your desktop - GNOME/KDE)
```
sudo /path-to-script/reset_usb; xsane
```



> Of course, the $64 question is: why is this needed at all. Used to work just fine for many years!
1. Default Delay Times for Power Management for EPSON Products.
This product will enter sleep mode after a period of nonuse. The time  interval has been set at the factory to the product meets Energy Star  Standards of energy effiency, and cannot be modified by the consumer.
2. It seems to be the long-standing xHCI clear halt bug in the kernel.

---

### Post by tgalati4 on 2014-07-14
Install acpitool and examine the power status of your USB ports:

```
sudo apt-get install acpitool
acpitool -w
man acpitool
```

---

### Post by helourx on 2014-07-16
This my newer script (with usb rebind) is better than first one  (which uses usb reauthorizing) I've posted because doesn't increases device number like the first one. 
```
#!/bin/bash
#

# Retrieved from "lsusb" command:
# Bus 003 Device 005: ID 04b8:014a Seiko Epson Corp.
IDVendor=04b8
IDProduct=014a

for x in /sys/bus/usb/devices/*; do 
    if [ "$IDVendor" == "$(cat "$x/idVendor" 2>/dev/null)" -a "$2" == "$(cat "$x/IDProduct" 2>/dev/null)" ]; then
    bus_port=`basename $x`
    echo "$bus_port" > /sys/bus/usb/drivers/usb/unbind
    sleep 1
    echo "$bus_port" > /sys/bus/usb/drivers/usb/bind
    fi
done
```

---

### Post by BobvanderPoel on 2014-07-16
Not sure what this proves? BTW, this is on a desktop ... reading the acpitool it seems it's more to do with laptops?
And, whether the scanner is working or not, it seems to have the same output. 

acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. RP01	  S4	*disabled  pci:0000:00:1c.0
  2. PXSX	  S4	*disabled
  3. RP04	  S4	*disabled  pci:0000:00:1c.3
  4. PXSX	  S4	*disabled  pci:0000:02:00.0
  5. GLAN	  S4	*enabled   pci:0000:00:19.0
  6. EHC1	  S4	*disabled
  7. EHC2	  S4	*disabled
  8. XHC	  S4	*enabled   pci:0000:00:14.0
  9. HDEF	  S4	*disabled  pci:0000:00:1b.0
  10. PEG0	  S4	*disabled
  11. PEGP	  S4	*disabled
  12. PEG1	  S4	*disabled
  13. PEG2	  S4	*disabled
  14. PWRB	  S3	*enabled

---

### Post by BobvanderPoel on 2014-07-16
You're revised script is better in more than one way! The old one also created a problem with emacs: Got a "can't save to x clipboard" after running. This doesn't seem to have that problem. Also (and I'm not sure exactly about this!) but it seemed to cause a problem with the audio output selection. Anyway, tried it and it seems just fine.

Still not sure exactly what is going on with the scanner though. If it's in a "not working" state running xsane will cause a search for the scanner and it does do a seek of the image head. Then, about a minute later, it returns with a "device not found". 

Anyway, now I can run the script and all's fine.

Best.

---

