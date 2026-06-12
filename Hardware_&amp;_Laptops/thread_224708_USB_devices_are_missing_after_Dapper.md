---
title: "USB devices are missing after Dapper"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by Books on 2006-07-28
I upgraded to Dapper (Kubuntu) from Breezy and noticed that my Epson Stylus 2200 wouldn't print, like it wasn't there. It still prints under windows so the connection is ok. It worked fine under Breezy.

I typed in lsusb and got this:

```
lsusb -vv

Bus 001 Device 002: ID 04b8:0007 Seiko Epson Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x04b8 Seiko Epson Corp.
  idProduct          0x0007
  bcdDevice            1.00
  iManufacturer           1
  iProduct                2
  iSerial                 3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```

I think ALL USB devices might be missing. I only have the printer to test, but /dev/ttyUSB* is missing from the menu, and isn't there supposed to be a section under Root called "/usb"? It isn't there.

Thank you!

---

### Post by jonrkc on 2006-07-28
The "operation not permitted" messages would suggest to me that it's a ownership/permissions problem.  I don't know what files may have the wrong settings (or at least wrong as far as detection is concerned).  

I couldn't get my HP Deskjet working last week (it worked OK previously under Dapper) and I used the KDE printer tool to reinstall it; now it works.  The problem there, I think, was wrong ownership of some files.  

Wish I could be more specific.  My suggestion is to try the KDE printer tool and see what it turns up.  You ought to get some good clues from what it shows, at least, and it might be able to fix this problem.

As for a "usb" directory under /root--I don't have that on my system....

---

### Post by Books on 2006-07-28
Thanks! You might be right. I'm not sure how to go about checking permissions, or what files would be effected.

I tried the *mtink* Epson printer utility and it gave the following...
[I]Error
No access to printer device file.
Please make sure that mtink has enough right for accessing the device files.
Refer also to the documentation.[/I]

I did some searching and found some posts about /dev/usblp0 . It has file permissions set to "-rw-rw----" What does this mean and is this the problem?

Thank you!

---

### Post by Books on 2006-07-28
I tried 'sudo chmod 666 /dev/usblp0' but it still isn't showing the printer.

---

### Post by jonrkc on 2006-07-28
"rw-" means read and write privileges, but not execute/search etc. privilege.  If you look in a file manager (Nautilus, Konqueror, gnome-commander, etc.) with the display set to "long" listings so it shows more than just file name and date and couple of other things--you can see the permissions for any file.  It also shows the user and group owning the file.  I looked up /dev/usblp0 on my system and it is set to the same permissions as yours; the owner is root, and the group is lp.  The group ID may be the clue here.  If your group ID isn't "lp" then the printer driver probably doesn't have access to that device.  

You can change the group ID (acting as root when you do it) but if you go making lots of changes to permissions and ownership, trouble will follow, as many programs and routines expect to find a certain setup their configuration tells them to find--and will refuse to work if those things aren't just right.

If you do have access to the KDE utilities, I still think the best thing right now would be to use the printer setup utility there to check on this.  I don't feel right about suggesting changing ownership and/or permissions unless you're somewhat experienced with that and also willing and able to take the consequences if there's a slip-up.  :)

I think you found something in your search that's pointing you toward the solution of the problem, though.

---

### Post by jonrkc on 2006-07-28
> **Books said:**
> I tried 'sudo chmod 666 /dev/usblp0' but it still isn't showing the printer.I don't think the permissions are at fault, but ownership may be; your permissions were the same as mine.  I'm assuming my system uses the same device--which may be a pretty shaky assumption.

What are the user and group for your /dev/usblp0?  If they're root:root, then I'll bet that's the problem; if they're root:lp then it probably isn't.

You could try changing mode to 777 for a test; that makes the device world-readable-writable-executable, which is usually considered a very bad practice, esp. if you're on a network.  You could change back to 330 (the original setting) after your test, though.  But I'd check the name of the group first.

---

### Post by Books on 2006-07-28
> **jonrkc said:**
> I don't think the permissions are at fault, but ownership may be; your permissions were the same as mine.  I'm assuming my system uses the same device--which may be a pretty shaky assumption.

What are the user and group for your /dev/usblp0?  If they're root:root, then I'll bet that's the problem; if they're root:lp then it probably isn't.

You could try changing mode to 777 for a test; that makes the device world-readable-writable-executable, which is usually considered a very bad practice, esp. if you're on a network.  You could change back to 330 (the original setting) after your test, though.  But I'd check the name of the group first.

Hi! I changed /dev/usblp0 back to the original permissions. When I had changed it to 777 it still wouldn't print.

Here are my settings...

/dev/usblp0
"-rw-rw----"
owner: root
group: lp

/etc/cups/printers.conf
"-rw-------"
owner: cupsys
group: lp

/etc/cups/ppd/EpsonStylusPhoto2200.ppd
"-rw-r--r--"
owner: cupsys
group: lpadmin

I don't know if it makes a difference, but I upgraded to Dapper from Breezy using the Updater instead of re-installing clean from the CD. Maybe something carried over that wasn't supposed to?

Thank you!

---

### Post by jonrkc on 2006-07-28
> **Books said:**
> Hi! I changed /dev/usblp0 back to the original permissions. When I had changed it to 777 it still wouldn't print.

Here are my settings...

/dev/usblp0
"-rw-rw----"
owner: root
group: lp

/etc/cups/printers.conf
"-rw-------"
owner: cupsys
group: lp

/etc/cups/ppd/EpsonStylusPhoto2200.ppd
"-rw-r--r--"
owner: cupsys
group: lpadmin

I don't know if it makes a difference, but I upgraded to Dapper from Breezy using the Updater instead of re-installing clean from the CD. Maybe something carried over that wasn't supposed to?

Thank you!
From the forums I get the impression upgrading from Breezy to Dapper has been working very well.  So it may not be too likely that the problem lies there. 

Are you using CUPS for your printing?  (Probably so.)  Have you tried taking a look at /var/log/syslog and at /var/log/dmesg and maybe /var/log/messages to see if they shed any light?  

I'm still thinking about the message that mentioned rights.  I would just about bet that somehow, somewhere, one or more files have the wrong permissions, ownership, or both.  Sometimes I've found error messages in the logs with "unable to..." "couldn't write to..." or the like, that have helped find an answer.  

Since the Epson's a USB device that should be safely hotpluggable, you might try (with it turned on) unplugging it and plugging it back in and then looking at /var/log/dmesg to see what it reports about that operation.  But it sounds like the problem is that the software needed to actually run the printer is running up a permissions/ownership barrier, rather than anything to do with initialization.

The gnome-cups-manager utility is useful, too.  It will show the status of the printer, offer to send a test page, etc.  Since your error messages are saying that the Epson software can't get printer status, it stands to reason that gnome-cups-manager probably won't be able to, either.  But it's worth a try to see what the gnome utility reports.

---

### Post by Books on 2006-07-28
> **jonrkc said:**
> From the forums I get the impression upgrading from Breezy to Dapper has been working very well.  So it may not be too likely that the problem lies there. 

Are you using CUPS for your printing?  (Probably so.)  Have you tried taking a look at /var/log/syslog and at /var/log/dmesg and maybe /var/log/messages to see if they shed any light?  

I'm still thinking about the message that mentioned rights.  I would just about bet that somehow, somewhere, one or more files have the wrong permissions, ownership, or both.  Sometimes I've found error messages in the logs with "unable to..." "couldn't write to..." or the like, that have helped find an answer.  

Since the Epson's a USB device that should be safely hotpluggable, you might try (with it turned on) unplugging it and plugging it back in and then looking at /var/log/dmesg to see what it reports about that operation.  But it sounds like the problem is that the software needed to actually run the printer is running up a permissions/ownership barrier, rather than anything to do with initialization.

The gnome-cups-manager utility is useful, too.  It will show the status of the printer, offer to send a test page, etc.  Since your error messages are saying that the Epson software can't get printer status, it stands to reason that gnome-cups-manager probably won't be able to, either.  But it's worth a try to see what the gnome utility reports.


Thank you so much for your help. I tried the gnome-cups-manager and sent a test page to the printer. It is reporting "Epson Stylus Photo 2200 ready" and said "Letter test page has been sent to EpsonStylusPhoto2200", but nothing happens. Basically the same thing that the KDE print manager does.

I looked at /var/log/dmesg, /var/log/syslog and var/log/messages like you suggested and I didn't see any noticable errors... although I don't know if I'd recognize something obviously wrong or not.

I tried using the escputil maintenance utility for Epson printers, and when I use the "status" flag 'escputil -s' it comes back with "Obtaining status requires using a raw device."

This is frustrating... and it worked so well under Breezy. Strange.

---

### Post by jonrkc on 2006-07-29
What happened with your test using gnome-cups-manager is exactly what happened to me day before yesterday.  It turned out I thought I had specified the correct users in the KDE printer utility, where I re-installed my printer after deleting it, to try to get it to work.  But what I had done was specify the correct users, all right -- jon and lp -- but I'd failed to see I'd checked the wrong function and made them DENIED users.  After I cleared that up, the printer worked.  

Since the cups-manager is definitely seeing a working, ready printer, and sending a test page to it, there's little doubt in my mind at this point that it's an ownership issue.  If you do have the KDE print utility aboard, I strongly suggest checking to see that "allowed users" are <your user name> and lp.  I feel just about certain that will fix this.

Hope it works!

---

### Post by Books on 2006-07-29
> **jonrkc said:**
> What happened with your test using gnome-cups-manager is exactly what happened to me day before yesterday.  It turned out I thought I had specified the correct users in the KDE printer utility, where I re-installed my printer after deleting it, to try to get it to work.  But what I had done was specify the correct users, all right -- jon and lp -- but I'd failed to see I'd checked the wrong function and made them DENIED users.  After I cleared that up, the printer worked.  

Since the cups-manager is definitely seeing a working, ready printer, and sending a test page to it, there's little doubt in my mind at this point that it's an ownership issue.  If you do have the KDE print utility aboard, I strongly suggest checking to see that "allowed users" are <your user name> and lp.  I feel just about certain that will fix this.

Hope it works!

How would I check "allowed users" to add <my name> and lp? I don't see that option in Print Manager... is it a menu option I'm missing?

You're definitely on to something. I went to KDE's Print System > Configure Server and it's asking for my user password. I type it in and it won't take it (!) and says "Unable to retrieve configuration file from the CUPS server. You probably don't have the access permissions to perform this operation."

Then I go into Administrator Mode and then click on Print Server > Configure Server. It asks for the root password... which it won't take.

It's definitely a password/permissions problem, but what is going on that it won't take my password. I type in the same password I use to log on and do all sudo commands since installation, and it takes it to get to administrator mode. But then I type in my user password and it won't take it, and root and it won't take it.

Thank you, jonrkc, for helping!

---

### Post by jonrkc on 2006-07-29
I'm really puzzled now, with KDE not accepting your password that you use successfully everywhere else.  I had to go into "administrator mode" to change my mistaken "denied users" to "allowed users," but it took my password without complaint.

At least you know what general territory the problem lies in.  It's not with CUPS or the printer driver but with a permissions/ownership problem.  I think you could start another thread about this problem of KDE not recognizing your password, while other functions readily take it.  I don't think moderators would consider it double-posting, since it's really a separate problem from a printer/USB problem per se.

With a thread title reflecting a password recognition problem, you might get to the heart of the matter.  I hope.

P. S.  You won't see the dialog box for adding/denying users till you achieve adminstrator mode in the print manager thing.  That's why you're not seeing it yet.

---

### Post by Books on 2006-07-30
> **jonrkc said:**
> I think you could start another thread about this problem of KDE not recognizing your password, while other functions readily take it.  I don't think moderators would consider it double-posting, since it's really a separate problem from a printer/USB problem per se.

With a thread title reflecting a password recognition problem, you might get to the heart of the matter.  I hope.

I'll do just that. This might answer some of the other issues I've come across, like not being able to unzip files from partitions other than Home. After the upgrade to Dapper I can't even get sound... although the music player programs think they are sending music to the speakers (just like the printer). Maybe I'll find an answer.

Thank you for all your time! You've been a real help.

---

### Post by jonrkc on 2006-07-30
You're more than welcome; only sorry the issue is still a puzzle.

And if it's any consolation, I don't have sound in Firefox despite my best efforts; it was there under Hoary.  I think I'll just give up on that.

---

