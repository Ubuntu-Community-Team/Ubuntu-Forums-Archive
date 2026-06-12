---
title: "Boot Ubuntu 9.04 on a USB device in persistent mode WITHOUT BIOS USB support"
date: 2009-08-13
forum: Hardware
---

### Post by CreativeK1 on 2009-08-13
Goal of this tutorial:[INDENT]     Boot Ubuntu 9.04 on a USB device in persistent mode WITHOUT BIOS USB support
[/INDENT]Intro:[INDENT]     I have searched the web to find a solution and nobody seamed to have THE solution to this problem so I found one myself with bits of information I gathered all around the web. I don't pretend to have 'THE ULTIMATE SOLUTION' but I think I got one that can fit most of computer setups. Since I'm not a GNU/linux guru, I did my best to be as clear as possible. This solution worked well for me so I hope it will for you!
[/INDENT]What you will need:
[INDENT]     -an ubuntu CD ISO(in this case: 9.04 downloaded at [www.ubuntu.com]("http://www.ubuntu.com"))
    -wakepuppy floppy image(wkpup202.zip from [http://www.murga-linux.com/puppy/viewtopic.php?t=7979](http://www.murga-linux.com/puppy/viewtopic.php?t=7979))
    -USB device of your choice(mine was an HDD in a cheap USB case)
    -floppy disk
[/INDENT]   optional(you can build this file yourself if you want):
    [INDENT]     -this file(4GB-casper-rw.zip from [http://www.pendrivelinux.com/downloads/casper-rw/4GB-casper-rw.zip](http://www.pendrivelinux.com/downloads/casper-rw/4GB-casper-rw.zip))
[/INDENT]In which environnement it was achieved:
[INDENT]     -Ubuntu 9.04 installed on my IDE HDD
[/INDENT]Steps:
[INDENT]     1.build your boot floppy
    2.modify the floppy to suit your needs
    3."install"/copy the ubuntu ISO on your USB device[INDENT]         3.1 format your USB device
        3.2 copy the Ubuntu ISO
[/INDENT]4.prepare the USB drive[INDENT]         4.1 copy the marker file
        4.2 copy the casper-rw file
            4.2.x (OPTIONAL) build this file yourself                
[/INDENT]5.boot and enjoy!
[/INDENT]1. BUILD YOUR BOOT FLOPPY
[INDENT]     a.Put your floppy in your floppy drive.
    b.Unzip wkpup202.zip to someplace you will remember.
        (in my case it was my desktop in a folder so you just have to replace my file location by yours)
    c.Open a terminal window(In Ubuntu, you can open a terminal window by selecting Accessories -> Terminal from the Applications menu.)[INDENT]         c.1 Go where you unzipped your file:

            XXXX@XXXX-desktop:~$ cd Desktop
            XXXX@XXXX-desktop:~/Desktop$ cd wakepup
            XXXX@XXXX-desktop:~/Desktop/wakepup$

        c.2 Load the wakepuppy disk image to your floppy:

            XXXX@XXXX-desktop:~/Desktop/wakepup$ dd if=WKPUP202.IMG of=/dev/fd0

                note: WARNING! this command is case-sensitive

        c.3 Wait until it's done!
[/INDENT][/INDENT]2. MODIFY THE FLOPPY TO SUIT YOUR NEEDS
[INDENT]     a.Open Text Editor(In Ubuntu, you can open a Text Editor by selecting Accessories -> Text Editor from the Applications menu.)
    b.Open the file 'autoexec.bat' that you will find on the 'newly created' boot floppy.
    c.You have ONE line to modify:[INDENT]         c.1 find this line:

            LINLD.COM image=%drv%\vmlinuz initrd=%drv%\initrd.gz "cl=%append%"

            replace it with this one:

                LINLD.COM image=%drv%\casper\vmlinuz initrd=%drv%\casper\initrd.gz cl=@config

        c.2 save
[/INDENT]    d.Create a new document[INDENT]         d.1 in this document your wil type:

            boot=casper 
            persistent 
            root=/dev/ram   
            ramdisk_size=1048576  
            devfs=mount,dall

        d.2 save your file on your floppy with the name 'config' (without quotes)
[/INDENT]    e.Your boot floppy is ready
[/INDENT]3. "INSTALL"/COPY THE UBUNTU ISO TO YOUR USB DEVICE
    3.1 FORMAT YOR USB DEVICE:
[INDENT]         a.Plug your USB device.
            a.1 If UBUNTU mounts your drive, unmount it
        b.Make a FAT32 partition and format it
            note: I wrote 'FAT32'! not 'EXT3', not 'EXT2', not 'NTFS'... i wrote 'FAT32'!
[/INDENT]    3.2 COPY THE UBUNTU ISO
        [INDENT]         a. Ubuntu has a pre-installed tool for this: "USB startup disk creator"
            a.1 Open the program(Administration -> USB startup disk creator from the System menu)
        b. Choose an iso file.
        c. Select your USB device.
        d. Make sure to make it 'persistent' by selecting the first "radio" button and specify the size you want/need.
        e. UBUNTU is now on your USB device
[/INDENT]4.PREPARE THE USB DRIVE
    4.1 COPY THE MARKER FILE
    [INDENT]         a.On your boot floppy, there is a file named 'usbflash'. Copy this file to the root of your USB device.
[/INDENT]    4.2 COPY THE CASPER-RW FILE
    [INDENT]         a.Unzip '4GB-casper-rw.zip' in the root of your USB device.
[/INDENT]    4.2.x (OPTIONAL) build this file(4GB-casper-rw.zip) yourself.
        It's what I did.
        [INDENT]         a.Open a terminal window(In Ubuntu, you can open a terminal window by selecting Accessories -> Terminal from the Applications menu.)
            note: my USB device is '/media/disk'. Replace it by your device location.
        b.Type:

            dd if=/dev/zero of=/media/disk/casper-rw bs=1M count=4000

           note:modify the 'count' option with the size in MB you want. I tried 10000 but the maximum size appeared to be 4000

        c.Type:

            mkfs.ext3 /media/disk/casper-rw
[INDENT]            c.1 when it asks: "proceed anyway?" answer 'y'
[/INDENT]        d.You're done!
[/INDENT]5.BOOT AND ENJOY![INDENT]     a.Put your boot floppy in your target computer.
    b.Plug your USB device in your target computer.
    c.Boot your computer with your boot floppy.
    d.That's it! Be happy!
[/INDENT]   note: When Ubuntu loads, it will do 'I don't know what' with your floppy. Don't be scared. Everything will go fine and the floppy will quiet itself during the process. I don't know if it can destroy your bootdisk so I made a copy myself in case something bad happens! You should do the same.
   
REFERENCES:

These are the locations of all useful information that made my adventure a success:
    
    Puppy Linux Discussion Forum : thanks to 'pakt' ([http://www.murga-linux.com/puppy/viewtopic.php?t=7979](http://www.murga-linux.com/puppy/viewtopic.php?t=7979))
    LiveUsbPendrivePersistent wiki : thanks to 'arky' ([https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent))
    Ubuntu Forums : thanks to 'romkeris' and 'mickeyWD' ([http://ubuntuforums.org/showthread.php?t=573508&page=2](http://ubuntuforums.org/showthread.php?t=573508&page=2))
    Ubuntu Forums : thanks to 'bcw' and 'awander@verrex.com' ([http://ubuntuforums.org/showthread.php?t=244918](http://ubuntuforums.org/showthread.php?t=244918))
    USB Ubuntu 9.04 Persistent install (Windows) : thanks to 'Pendrivelinux.com team' ([http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/))
    LiveCDPersistence help : thanks to 'Sebastian' ([https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence))

---

