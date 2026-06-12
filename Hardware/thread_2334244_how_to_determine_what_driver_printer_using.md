---
title: "how to determine what driver printer using"
date: 2016-08-17
forum: Hardware
---

### Post by jgw on 2016-08-17
I just installed a new printer.  Here is a link to my problems with the driver: [https://ubuntuforums.org/showthread.php?t=2334137](https://ubuntuforums.org/showthread.php?t=2334137)

I installed the driver with gdebi and then installed the printer from system settings. The printer now seems to be working.  My problem is that, after I was done, I seem to have installed the same printer 2 times.  I choose the last installed as the default printer and tested it.  It seems to be working.  On the other hand, when I goto software & updates/additional drivers I see I am using an Nvidia driver for display (correct) and then:
Unknown:Unknown
This device is not working.
Using Processor microcode firmware for AMD CPUs from amd64-microcode (proprietary)

I have no idea what this is nor where it came from.  So, should I uncheck this unknown thing and, where is the canon driver that I installed?

Thoughts?

Thank you.....................

---

### Post by weatherman2 on 2016-08-17
You won't see the Canon printer driver you installed as an "additional driver" because it wasn't installed as one.  (Nor could you, I believe.)

Just delete one of the printers if you installed it twice.  That won't remove the driver.

I have no idea what the AMD microcode thing is about (I know what CPU microcode is; I don't know what this driver does or why you need it), but I'm fairly confident it has nothing to do with the printer.

---

### Post by jgw on 2016-08-17
Thanks for the reply!

My problem is that I am not even sure that the printer is using the downloaded driver.  I guess I just have to assume that it is.  The microcode thing is strange.  Whatever its there for it also says that its not working, as well as being unknown.  I guess, in the fullness of time?

---

### Post by weatherman2 on 2016-08-17
If you want to see which driver is being used, go into Printers (or whatever on 16.04), right-click on the printer and choose "Properties."

Then see what the text next to "Make and Model" says.

For one of my Canon printers, I installed both the Canon driver and also a newer version of Gutenprint and that driver for another installation of the printer (so I could print with either driver).  For the Canon version, the "Make and Model" says "Canon MX450 series Ver.3.50" .  For the Gutenprint version, it mentions Gutenprint.

If you are using the Canon driver you installed, it should also say something similar to what mine says.  If it mentions Gutenprint, then you are not using the Canon-installed driver.

---

### Post by Bucky Ball on 2016-08-17
Don't fret about the microcode option. Nothing important. Enable it if you want, leave it if you don't. ;)

You should also be able to take a look at the printer via CUPS interface in a web browser. Open a browser and put 'localhost:631' in the address bar then hit enter. That should give you the cups interface and you may be able to see the driver there.

If the printer is working as it should, as mentioned, delete one of the printers you've added and enjoy. If you selected the printer's driver when you were adding the printer, it is using that driver. ;)

* I wasn't aware of it, but as weatherman2 mentions, also this:

[QUOTE=weatherman2]If you want to see which driver is being used, go into Printers (or whatever on 16.04), right-click on the printer and choose "Properties."

Then see what the text next to "Make and Model" says.[/QUOTE]

---

### Post by jgw on 2016-08-18
Thanks for the replies!

I went to the printer properties and the make and model is: Canon MG5700 series Ver.5.20   The '5.20' is the tip off and means that I AM using the proper driver. <G>

Thanks again!!

---

### Post by Bucky Ball on 2016-08-18
All good. Please mark as solved using thread tools at top right (or see second link in my signature) to help others. :)

---

### Post by jgw on 2016-08-19
I thought that I had but it is now!!!  <G>

---

