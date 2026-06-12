---
title: "Palm Pilot sync usb/serial adapter &quot;Identifying user&quot;"
date: 2010-12-20
forum: Hardware
---

### Post by linuxnovo on 2010-12-20
I have an old Palm Pilot with a serial cradle which I am attempting to sync with a computer running ubuntu which does not have a serial port.  I am using a usb/serial adapter.  

I plug in the serial cradle connected to the usb/serial adapter and issue "dmesg" command:

984.764044] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  984.932410] usb 2-1: configuration #1 chosen from 1 choice
[  985.331762] USB Serial support registered for ch341-uart
[  985.331810] ch341 2-1:1.0: ch341-uart converter detected
[  985.345796] usb 2-1: ch341-uart converter now attached to ttyUSB0
[  985.345835] usbcore: registered new interface driver ch341

The device we are looking for is /dev/ttyUSB0  via usb 2-1

Set the permissions so anyone can read and write this device:

sudo chmod 666 /dev/ttyUSB0

set PILOTPORT to /dev/ttyUSB0

 export PILOTPORT=/dev/ttyUSB0

(This command may not be necessary at all)

Make the symbolic link:

sudo ln -s /dev/ttyUSB0 /dev/pilot

try sync with pilot-xfer:


master@master-desktop:~$ sudo pilot-xfer -p /dev/pilot -l

   Listening for incoming connection on /dev/pilot... connected!


   Error read system info on /dev/pilot
master@master-desktop:~$ 

On the palm pilot display:

"Identifying user"

There is a link from several years ago with an exactly similar situation without a solution:

[http://lists.pilot-link.org/pipermail/pilot-link-general/2008-March/003333.html](http://lists.pilot-link.org/pipermail/pilot-link-general/2008-March/003333.html)

On Tue, Mar 18, 2008 at 1:03 PM, Tom Cada <thomas.cada at gmail.com> wrote:
> I am running into problems running any of the palm-link utilities. I
>  have created the /dev/pilot link to /dev/ttyUSB0, and set the
>  propertied to rw for all users of /dev/ttyUSB0.
>
>  I press the hotsync button on the Palm cradle and start pilot-xfer and
>  get the following:
>
>  tom at speedy:~> pilot-xfer -p /dev/pilot -b palm
>
>    Listening for incoming connection on /dev/pilot... connected!
>
>
>    Error read system info on /dev/pilot
>  tom at speedy:~>
>
>  The Palm IIIc displays a message "Identifying user" and after a few
>  moments disconnects  and then palm-xfer ends with the error.
>
>  I can transfer data using kpilot so I know my setup will work.
>
>  TIA for any comments or suggestions... Tom.
>

Further to this, I should have mentioned that I am connecting the
serial cable from the Palm cradel to the USB port using a RS232 to USB
converter. If I connect the serial Palm cable to the serial port on my
old laptop, then the Pilot-Link tools work fine.

As mentioned above, I can sync using the RS232-USB converter with
Kpilot. Very  strange???

I am using a MCT U232 converter which is nicely detected by the kernel

usb 2-7: new full speed USB device using ohci_hcd and address 66
usb 2-7: new device found, idVendor=0711, idProduct=0230
usb 2-7: new device strings: Mfr=1, Product=2, SerialNumber=3
usb 2-7: Product: USB Ver1.2 Device
usb 2-7: Manufacturer: USB-RS232 Interface Converter
usb 2-7: SerialNumber: 132168
usb 2-7: configuration #1 chosen from 1 choice
mct_u232 2-7:1.0: MCT U232 converter detected
usb 2-7: MCT U232 converter now attached to ttyUSB0

Let me know if you need anything further or if you want me to do any
testing for you.

Tom.

Any suggestions would be most helpful: linuxnovo

---

