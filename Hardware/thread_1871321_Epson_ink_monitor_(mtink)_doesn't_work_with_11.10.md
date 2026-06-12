---
title: "Epson ink monitor (mtink) doesn't work with 11.10"
date: 2011-10-28
forum: Hardware
---

### Post by Mark Phelps on 2011-10-28
I've been using the Epson Ink Monitor (mtink) app for years now, and it's always worked fine.

The only complication is that you have to add yourself to the lp group in order for the app to access the device -- which I've done.

But now, with 11.10, it no longer works.  Running it from Dash yields nothing at all.

Running it from the terminal, using gksudo, causes the app to open -- but it fails saying "NO access to printer device file".

And, yes, I've confirmed that I have access to the lp group, and I've reboot cold -- several times.

Printing a test page to the printer works fine.

Output of lsusb is the following:

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0a48:5014 I/O Interconnect Mass Storage Device
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 050d:0237 Belkin Components F5U237 USB 2.0 7-Port Hub
Bus 003 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 007 Device 003: ID 04b8:0005 Seiko Epson Corp. Printer
Bus 003 Device 005: ID 050d:0237 Belkin Components F5U237 USB 2.0 7-Port Hub
Bus 005 Device 003: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 005 Device 004: ID 046d:c225 Logitech, Inc. G11/G15 Keyboard / G keys

```

Output of the lsusb -v for the Epson printer is as follows:
```
Bus 007 Device 003: ID 04b8:0005 Seiko Epson Corp. Printer
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04b8 Seiko Epson Corp.
  idProduct          0x0005 Printer
  bcdDevice            1.00
  iManufacturer           1 EPSON
  iProduct                2 USB Printer
  iSerial                 3 MO1P10312160131480
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
Device Status:     0x0001
  Self Powered
```

And, yes, I've also tried escputil -- but this model Epson is not listed in the supported models -- and it doesn't work anyway.   When I run it in the terminal with sudo, I get the error 
```

Cannot open /dev/usb/lp0 read/write: No such file or directory
```

Anyone have any ideas?

---

### Post by alfaus on 2011-10-29
The problem is that cups doesn't use usblp module anymore and mtink needs it. You can load that module manually, then use mtink, and finally unload it.
```
sudo modprobe usblp
mtink
sudo modprobe -r usblp
```

---

### Post by Mark Phelps on 2011-10-29
> **alfaus said:**
> The problem is that cups doesn't use usblp module anymore and mtink needs it. You can load that module manually, then use mtink, and finally unload it.
```
sudo modprobe usblp
mtink
sudo modprobe -r usblp
```

WOW -- thanks!  I'll give this a try and let you know what happens.

---

### Post by Mark Phelps on 2011-10-31
OK it works again, but only when I run it using sudo.  In 11.04, it works when I click on the icon in Dash.  In 11.10, that does nothing at all.  Tried editing the .desktop file to add sudo to the command invocation, but when I saved the file, it disappeared from Dash.  I fixed that by going back into 11.04, creating a new launcher there, with sudo included, and copying that launcher to the 11.10 desktop.

The more I use 11.10, the LESS I like it.

---

### Post by Chough39 on 2011-11-10
I have been having the same problem getting mtink to work with an Epson Stylus C62 and 11.10. Below is a print out from terminal when I use the commands you mention. Perhaps you can tell me what I have or have not done.

gerald@gerald-desktop:~$ sudo modprobe usblp
[sudo] password for gerald: 
gerald@gerald-desktop:~$ mtink
Segmentation fault
gerald@gerald-desktop:~$ 


What is this segmentation fault please?

---

### Post by Chough39 on 2011-11-11
Using the following works.   sudo mtink

---

### Post by exXP on 2011-11-30
> **alfaus said:**
> The problem is that cups doesn't use usblp module anymore and mtink needs it. You can load that module manually, then use mtink, and finally unload it.
```
sudo modprobe usblp
mtink
sudo modprobe -r usblp
```

Alfaus' solution works for me.  It's unfortunate, however, that we have to remove usblp afterwards. I find that if I don't, I can't print from either of my printers! 

This seems to be a CUPS problem rather an Ubuntu one.  Like many others,I find my old Epson C62 very useful, with cheap replacement cartridges.  I used to be able to check the status on Win 7 but that's disappeared lately too.

exXP  (remember XP?)

---

### Post by bluexrider on 2011-11-30
I had an issue with my stylus CX8400 

This is what I did 

Just found a GUI for it too (Stylus Toolbox):

from [http://sourceforge.net/projects/stylus-toolbox/files/](http://sourceforge.net/projects/stylus-toolbox/files/)

you need:
stylus-toolbox_0.2.7-1_all.deb     (Sourceforge)
python-pexpect_2.3-1_all.deb       (From Ubuntu repos)

Once downloaded and installed

1) CREATE A LAUNCHER (doesn't appear to install one by default)

Right click on desktop, then select "Create launcher"

Name :        Ink Level Monitor
Command:    /usr/bin/stylus-toolbox    

(Click Spring box to change Icon)

2) SET UP STYLUS TOOLBOX PREFERENCES

Device port:        /dev/usb/lp0
Model Settings:     (Select model from list)
External Programs:    /usr/bin/escputil


This is the OP from where I found my answer [http://ubuntuforums.org/showthread.php?p=8881517#post8881517](http://ubuntuforums.org/showthread.php?p=8881517#post8881517)

Thats it you now have a working ink monitor with GUI :smile:

---

### Post by exXP on 2011-11-30
I have tried Bluexrider's solution and it appears that it ought to work if can get it pointed to the right device port. The GUI comes up reporting zero levels on all colours. under 'Preferences' I open the Device Port and put /dev/bus/usb/001. At the top of the screen a message reads 'Cannot open /dev/bus/usb/001 read/write : it is a directory'  

Also right-clicking on my desktop only gives me the option of opening a new file or folder  -  not a launcher.

I welcome any suggestions/
ExXP

---

### Post by bluexrider on 2011-11-30
> **exXP said:**
> I have tried Bluexrider's solution and it appears that it ought to work if can get it pointed to the right device port. The GUI comes up reporting zero levels on all colours. under 'Preferences' I open the Device Port and put /dev/bus/usb/001. At the top of the screen a message reads 'Cannot open /dev/bus/usb/001 read/write : it is a directory'  

Also right-clicking on my desktop only gives me the option of opening a new file or folder  -  not a launcher.

I welcome any suggestions/
ExXP

2 suggestions

add yourself to the "lp" usergroup

if its a USB printer then Device port:        "/dev/usb/lp0" should work

---

### Post by arai on 2011-12-01
Dear friends,

I have ubuntu and epson stylus tx121. To see the ink monitor i installed mtink. But i am unable to see the ink monitor please help me.

thank you.

---

### Post by crazy bird on 2011-12-01
There's already a thread with the same question about mtink. Please read this thread and ask your question in that thread. Otherwise there will be a numerous threads on this forum containing the same problem. Link of the other thread: [http://ubuntuforums.org/showthread.php?t=1871321&highlight=mtink](http://ubuntuforums.org/showthread.php?t=1871321&highlight=mtink)

---

### Post by mörgæs on 2011-12-01
Threads merged.

---

### Post by Mark Phelps on 2011-12-01
> **bluexrider said:**
> add yourself to the "lp" usergroup

Ordinarily, this should work. But with Ubuntu 11.10, it does NOT.

I know because I've tried this repeatedly.

You HAVE to use sudo to get mtink to work with 11.10.  If you run it without sudo, you get the segmentation fault.

This did NOT happen with 11.04.

---

### Post by crazy bird on 2011-12-01
-

---

### Post by crazy bird on 2011-12-01
-

---

### Post by exXP on 2011-12-01
Thank you for your response.  Still no success, I regret to say.  I had already added both my accounts to the lp group  (it used to be easier with 'User Groups')  I put in /dev/usb/lp0 but got the same response as before  -  but it still referred to /dev/bus/usb/001, a different file.
exXP

---

### Post by Mark Phelps on 2011-12-01
mtink uses a config file, I think named .mtincrk (or .mtinkrc -- not at my Linux box, so I can't check).  That is a hidden file and I believe it's in your /home directory somewhere.

If you remove that, and you run the program mtinkc (for mtink configuration), it should put up a window where you can choose settings, including the port.

Like with mtink, you may have to use sudo to run mtinkc.

---

### Post by exXP on 2011-12-01
I would be quite happy to use stylus toolbox instead of mtink.  However I haven't yet solved the problem of what to enter for the Device Port.  Everything I've tried so far gives an error message, usually 'No such file' 
Does anyone have any suggestions?  (and,yes, I have included myself in the lp group)
exXP

---

### Post by exXP on 2011-12-02
Answering my own question, the problem seems to be that module usblp is required for both mtink and stylus-toolbox -  and it's been blacklisted.  If it's enabled my printers (laser or ink-jet) won't print.  However both mtink and stylus-toolbox work.  Of the two, I prefer mtink since it shows ink colours.  However usblp has to be disabled afterwards.

Which is what Alfaus said four weeks ago!
I guess I'm a slow learner.
exXP

---

### Post by arai on 2011-12-02
after login using sudo and providing the password i typed mtink then also it shows no ink levels. Here is snapshots

[[IMG]http://img249.imageshack.us/img249/792/screenshotat20111203075.th.png[/IMG]](http://imageshack.us/photo/my-images/249/screenshotat20111203075.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

[[IMG]http://img545.imageshack.us/img545/792/screenshotat20111203075.th.png[/IMG]](http://imageshack.us/photo/my-images/545/screenshotat20111203075.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Please help me to check the ink levels in ubuntu. At present I am having dual boot with xp and I am going to XP to see my ink levels in the Printer.

Please note the printer is powered on, there is paper in the printer.

---

### Post by exXP on 2011-12-03
It all looks very familiar.  Make sure that you are included in the lp group and then check the Alfaus post above (in page 1) It's annoying to have to put in a module and then remove it again, but until there's a better solution, it's quicker than rebooting into XP.
ExXP

---

### Post by mgorovoy on 2012-02-26
> **alfaus said:**
> The problem is that cups doesn't use usblp module anymore and mtink needs it. You can load that module manually, then use mtink, and finally unload it.
```
sudo modprobe usblp
mtink
sudo modprobe -r usblp
```

This solution is working for me, but only if I add sudo in front of mtink as well. To make sure I do not foget to load/unload usblp module, I've added the following function to my .bash_aliases file, so that simply typing mtink command loads the module, executes mtink, and then module is unloaded automagically.

```

function mtink() {
   sudo modprobe usblp
   sudo mtink
   sudo modprobe -r usblp
}

```

---

### Post by Mark Phelps on 2012-02-28
> **mgorovoy said:**
> This solution is working for me, but only if I add sudo in front of mtink as well. 
Make sure that your ID is included in the "lp" group.

I had to add mine before mtink would work for me.

Also, in a similar fashion, I created a launch shortcut that I can click from the desktop that does much the same as your solution.

---

### Post by Tares on 2012-04-06
I know this topic is old, but anyone knows how to get a working ink levels in system-config-printer?

---

### Post by Mark Phelps on 2012-04-06
> **Tares said:**
> I know this topic is old, but anyone knows how to get a working ink levels in system-config-printer?

Please do NOT hijack this thread with questions about something different.  Please start your own thread.

thanks

---

