---
title: "usb controller"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by beacon on 2009-08-26
I have been literally months trying to get ubuntu to boot from a USB flash drive. Most recently I have been trying with Easy Peasy. I no sooner sort out one problem than another arises. I haven't been able to get the create startup disk to copy, as it won't recognise a flash disk when it is in the drive. I noticed on this occasion a symbol, which when I clicked on it, stated that USB controller is disabled. That may have been the problem all along, but how do I enable it? I am still an amateur so hope it isn't too complicated.  Thanks

---

### Post by tommcd on 2009-08-26
> **beacon said:**
> ... I noticed on this occasion a symbol, which when I clicked on it, stated that USB controller is disabled. That may have been the problem all along, but how do I enable it? I am still an amateur so hope it isn't too complicated.  Thanks
Is the USB controller enabled in the computer's BIOS?
Assuming usb is not disabled in the BIOS, then:
Type **lspci -v** in the terminal. You should see entries in lspci about your computer's usb controllers.

Assuming lspci lists your computer's usb controllers, then plug in the usb drive, and then type **lsusb** in the terminal. You should see info indicating that the usb drive has been detected.

If there is no info about the drive in lsusb, then unplug the drive, and type:
```
sudo dmesg -c
```
in the terminal. This will clear the kernel's boot messages. Next, plug in your usb drive, then type **dmesg** in the terminal. You should see something there about your usb drive being detected.

If usb is enabled in the BIOS, and if there is nothing useful in lspci, lsusb, and dmesg, then Ubuntu is not detecting your computer's usb controller, and / or the usb drive you are using. This is highly unlikely though.
Post the output of the commands I listed (lspci, lsusb, dmesg) if you are not sure.

---

### Post by beacon on 2009-08-26
Thanks for the lightning-quick reply tommcd. I have followed instructions. The controller is enabled in the bios. Here is the result of the second command: xxxxx@Ubuntu:~$ lsusb Bus 001 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive Bus 001 Device 002: ID 046e:300e Behavior Tech. Computer Corp.  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  That would seem to be good news in that the USB drive is detected, so I wonder if you have any ideas about why I can't boot from it. I went back to the Easy Peasy iso and tried to copy it to a flash disk and once again found the symbol that the usb controller is disabled. I don't understand why.

---

### Post by tommcd on 2009-08-26
> **beacon said:**
>  Here is the result of the second command: xxxxx@Ubuntu:~$ lsusb Bus 001 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive Bus 001 Device 002:
... so I wonder if you have any ideas about why I can't boot from it.
So it seems that your usb drive is properly detected. This is good news.
In order to boot from a usb drive, the usb drive must be listed as the *first boot device* in the computer's BIOS.
 Boot into the BIOS and verify that the system is set to boot from a usb drive as the first boot device under the boot options in the BIOS menu.

Some older computers do not have the option of booting from usb in the BIOS.

---

### Post by beacon on 2009-08-26
Thanks again. I don't want to take advantage, but perhaps you can help further.  In bios, I have the following:    Boot sequence is       1st boot device: USB CF (whatever that is)        2nd Boot device: CD/DVD-PM-DVDR       3rd boot device: SATA: 3M-Maxtor    Hard disk drives: SATA: 3M-Maxtor (the only choice I am offered)      Removable Drives:  USB: USB CF                      USB: USB MS                      USB: USB SD                      USB: USB SM  Does this help in any way to resolve the problem? I appreciate the help and will try not to trouble you further if nothing comes of this.

---

### Post by beacon on 2009-08-26
Addendum: I obviously don't know how to write the messages. I notice that you are able to put information in paragraphs. That is the way I compose, but it all gets posted as one scrambled piece.

---

### Post by tommcd on 2009-08-26
> **beacon said:**
>  In bios, I have the following:    Boot sequence is       
1st boot device: USB CF (whatever that is)        
2nd Boot device: CD/DVD-PM-DVDR       
3rd boot device: SATA: 3M-Maxtor    Hard disk drives: SATA: 3M-Maxtor (the only choice I am offered)      Removable Drives:  USB: USB CF  USB: USB MS  USB: USB SD   USB: USB SM  Does this help in any way to resolve the problem?
The USB CF means compact flash. That would seem to be the correct choice. The USB MS, SD, and SM must be for other types of removable media, like a SD memory card, for example. Does the computer have a memory card reader or something like that?
For troubleshooting purposes, I suppose you could try using each of the USB options as the first boot device to see if any of them will allow you to boot from the usb flash drive. I would think that USB CF (compact flash) would be the correct one though, but try the others anyway.

What kind of computer is this? Can you post the make and model number of the computer, or the motherboard?

Does the usb flash drive work for other things? For example, can you connect the usb drive to the computer and copy media and files to it?

Have you tried using the usb startup disk creator that already comes with Ubuntu? Just go to: System > Administration > USB Startup Disk Creator to create an ubuntu usb boot disk:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Or have you tried UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
I'm not sure what else you can try.

No problem with asking questions here btw. I am likely to run out of answers soon anyway.

---

### Post by tommcd on 2009-08-26
> **beacon said:**
> Addendum: I obviously don't know how to write the messages. I notice that you are able to put information in paragraphs. That is the way I compose, but it all gets posted as one scrambled piece.
To quote a post, just use the "quote" button on the lower right of each post.
To put stuff in code tags, just use the code tag icon (#) at the top of the message window when you post. 
```
Putting stuff in code tags looks like this.
```
To use quote tags, use the quote icon to the left of the code tag (#) icon.
> A quote looks like this. It will wrap around when it runs to the end of the line.
There are other options at the top of the message window, like **bold type** and *italic* and other stuff.

---

### Post by beacon on 2009-08-28
Thanks very much once again. I appreciate also the help about composing, although I still don't know how to break the message into paragraphs. It looks ok when I type it, but when I go to preview, it is all melded into one.  I'm sorry for the delay. I was waiting for the chap who built the machine to call, but he hasn't kept the appointment. (In any case, I think he has more or less given up.) I believe that I have now tried everything suggested at least once, so I think I am going to have to give up too.  Regards.

---

