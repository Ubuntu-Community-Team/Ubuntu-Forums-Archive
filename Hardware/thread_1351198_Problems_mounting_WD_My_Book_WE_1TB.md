---
title: "Problems mounting WD My Book WE 1TB"
date: 2009-12-10
forum: Hardware
---

### Post by rosatimr on 2009-12-10
Newbie here.  I have googled for days and can't seem to find the answer to my problem.  Here is the background.  I was running Windows Vista on my desktop at home until I got fed up and decided to go with linux again.  I have a dual boot with Vista and Ubuntu Karmic.  

I have a Western Digital My Book World Edition, 1TB, network hard drive.  About a month ago, the thing wouldn't turn on.  I was kind of annoyed at the whole mionet thing and network drive anyway.  So, assuming that my power supply was bad, I ordered a new enclosure that would interface via usb instead of ethernet.  I didn't do much research prior to ordering the enclosure to simply fix my problem, I guess I was being naive and thought I could just plug it in and bam, I would have a new usb external hard drive.  After that didn't work I got worried.  But when I am running vista, and I plug the drive in, it recognizes that a usb mass storage device has been plugged in but it doesn't show up in my computer.  I can view the device in Computer Management-->Drive Management.  

I have gone through a bunch of hoops trying to mount it on ubuntu.  I was sort of able to mount it but I still can't access the data.  The reason I say sort of is because when I click on the drive from Places, it says "Unable to scan Device for media changes.  Device is not active."  The data is all I am concerned about, however, I would like to be able to use this relatively new drive.  When I use the Disk Utility, it shows my drive set up as a RAID array with this information:

                                    Drive
                                   Unknown Size
                                   Linux Software RAID
                                   Not running

Array Name:-
Home Host: -
Array Size:  -
RAID Type:
Components: 0 Components (3.0 GB each)
State:  Not running, not enough components to start

RAID Component                                     State

3.0 GB RAID Component  (/dev/sde1)          -
107 MB RAID Component (/dev/sde2)          -
1.0 GB RAID Component  (/dev/sd3)            -
996 GB RAID Component (/dev/sd4)            -

I guess my questions are, am I able to convert this network drive to a usb?  And, if so, how do I get this thing to mount properly?  If not, should I just get my data with some sort of data recovery software?

please help.  thanks in advance.


FIXED:  I had some updates that needed a restart and when I restarted, partitions mounted successfully.  I tried so many things I don't even know if I can pinpoint the exact solution.  I'm sure the line I added in my fstab took care of it.

/dev/sde4        /media/mybook2   usbfs    guest,   0 0

---

