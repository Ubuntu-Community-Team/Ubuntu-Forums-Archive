---
title: "external hard drive mess"
date: 2010-04-02
forum: Hardware
---

### Post by KarenAK on 2010-04-02
My media folder looks like this:

[IMG]http://i107.photobucket.com/albums/m312/KarenAK/Temp/MediaFolder.png[/IMG]

I have 2 external hard drives in use, HD1 and USB-HDD-2, the WD was connected once for backup purposes but is still listed here.

And why is the cdrom listed twice ?


How can I

1. rename the hard drives
2. fix this list so it only shows the actual devices available 
3. avoid this in future 


Thanks in advance for any help :-)

---

### Post by KarenAK on 2010-04-02
I managed question no. 1 - more or less

I unmounted / mounted the hard drives to the mount points I want (namely HD-1 and HD-2) 

[IMG]http://i107.photobucket.com/albums/m312/KarenAK/Temp/MediaFolder1.png[/IMG]


However, in "Places" HD-2 is still listed as USB-HDD-2.....where do I change that ? Or should it have done so automatically ?

How do I get rid of the old, unwanted ones ? They are not listed in mtab and the rm -R command doesn't work, says "No such file / directory"

Help ? Anyone ?


:-k

---

### Post by IcarusR on 2010-04-02
I believe Ubuntu will automatically mount usb drives to a directory called whatever the drive label is.
IE I have an external usb drive that has label of "DRIVE-N-GO" so it is auto-mounted to /media/DRIVE-N-GO & appears in Places & Nautilus as DRIVE-N-GO.
If you want a drive mounted to a different name then use gparted to change it's label.

The directory /media is a system directory, so to remove any of its contents you need to do so as 'sudo'. 
But the contents should be irrelevant (if you do as above) as you will not see any of it unless a drive is mounted as one of them.

---

