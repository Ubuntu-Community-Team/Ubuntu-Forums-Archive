---
title: "HP 2600n color laser drivers"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by AllanP on 2006-01-14
Well it looks like the HP 2600n is the only color printer not supported by HP for Linux. Do I have to go to that other OS to use it or take it back. I was able to find a foomatic whatever that is that's supposed to work but alas I found it too complicated for this aging gray matter. Anyone out there have an easy step by step way of getting this printer to work?

---

### Post by yoki on 2006-06-14
I was looking for a driver when I saw your post here few minutes ago.  I found this site 
[http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/) and used their driver and it works.   Just follow their instructions and it will work.

---

### Post by MilesTEG1 on 2006-10-09
Hello,
I intend to replace my epson stylus color 760 (ink jet) by a laser color, and the HP 2600n seems to be a good idea, no ?

So I search on the net to know if this laser printer is supported on ubuntu.
I don't found anything good for this, until I went here.

My question is : does this drivers founded [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/) allow to print in color ?
And does the printing results are good ? like a print from windows ??

Thanks
++
Miles

---

### Post by AllanP on 2006-10-09
I gave up on trying to print color and boot Windows if I ever need color; which isn't that often. I'm not saying it can't be done; just that I couldn't get it to print color. It's fine in B&W.

Regards, Allan

---

### Post by MilesTEG1 on 2006-10-10
Hello,
So you cannot print in color with this driver : [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/) ???

That's not so good... I would buy this printer...

---

### Post by JackDog on 2006-12-27
> **MilesTEG1 said:**
> Hello,
So you cannot print in color with this driver : [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/) ???

That's not so good... I would buy this printer...

After using this driver and countless other fixes, I would highly recommend that no one buy this printer. You can get the colors "mostly" right but they are no where near the quality of the windows drivers. The resolution was also not nearly as good. I tested this hosted on an Edgy box on my LAN with 4 Linux clients and 1 windowsXP client. There was no comparison, stay away from this printer if you use linux clients.

---

### Post by MilesTEG1 on 2006-12-28
> **JackDog said:**
> After using this driver and countless other fixes, I would highly recommend that no one buy this printer. You can get the colors "mostly" right but they are no where near the quality of the windows drivers. The resolution was also not nearly as good. I tested this hosted on an Edgy box on my LAN with 4 Linux clients and 1 windowsXP client. There was no comparison, stay away from this printer if you use linux clients.
Ok thanks.
In any case, I have wanted to buy a Dell 3110cn for a few months...

---

### Post by JackDog on 2006-12-28
> **MilesTEG1 said:**
> Ok thanks.
In any case, I have wanted to buy a Dell 3110cn for a few months...

Little OT, But thought I would follow up on this...

I took the 2600 (to Sams Club - $299) back and got a 2605 (at Costco $429). Worked perfectly right out of the box. Colors are correct and the DPI can be set to the max. I have not tried advanced features, mainly because I do not really need them. The printer is hooked up via cat6 and shared over jetdirect on the network. I need to figure out how to update the wiki for ubuntu printer support.

I called Dell about the 3110cn and they verified with tech that the printer does indeed print on well from linux clients. The 3110cn is probably  a better deal for the PPM and the toner prices however I did not feel like fooling with it in the event it was subpar like so many other printers in linux.

---

### Post by deangl on 2006-12-30
I was able to use this tip from [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)
to get the color printing working on my 2600n for the Print Test Page.

To get color edit the file /etc/cups/ppd/<printer-name>.ppd and change the configuration item "FoomaticRIPCommandLine" to "foo2hp2600-wrapper -c %A" (note the -c which is what you have to add manually)

I am still testing the color printing from other apps.

Dale    :-)

---

### Post by JackDog on 2006-12-31
> **deangl said:**
> I was able to use this tip from [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)
to get the color printing working on my 2600n for the Print Test Page.

To get color edit the file /etc/cups/ppd/<printer-name>.ppd and change the configuration item "FoomaticRIPCommandLine" to "foo2hp2600-wrapper -c %A" (note the -c which is what you have to add manually)

I am still testing the color printing from other apps.

Dale    :-)

I had this fix working as well however the colors were faded and the photos I printed were grainy on the 2600n. By contrast, when I printed from windows it looked great. When you print with the 2600n or the 2605dn, the pictures should not be grainy at all and the printed photos are frame able. 

The frustration I had is that people said the 2600n worked, however it only mostly worked. Maybe you got it to work perfectly, its hard to tell unless you can perform a side by side comparison. I thought it worked at first too. Try printing a colorful with texture in linux and in windows and compare them on the 2600n. 

[http://hplip.sourceforge.net/supported_devices/color_laser.html](http://hplip.sourceforge.net/supported_devices/color_laser.html)

[http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2600n](http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2600n)

[http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2605](http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2605)

---

### Post by deangl on 2007-01-03
Back at it again tonight...
I was setting up a wireless network in my house for printing (don't want to run cable to all the rooms with computers and this network is different than our Internet access - which is only on one system in  public area of the house... enough of that).   I now have the 2600n connected via USB to a Linux (AMD64 running Edgy) system.  I connected the ethernet (RJ45) to a standard Westell wireless router (private net side only).

Things are printing pretty well on the 2600n from both Linux and from WinXP.  I am not sure what changed.
One thing I did do was from the front panel of the 2600n, I did a "Reset to Defaults".  I am not sure if that helped the poor color problem from Linux or not...   Now the Test Pages from Linux look real (before they were very pale and grayish).  I tried printing from Firefox and from GIMP and things look much better.

I don't know if this helps...  Keep us posted on your progress...  and I will do the same...  Not sure that I will be able to get back to this issue until next week...

Good Luck,
Dale    :-)

---

### Post by AllanP on 2007-01-04
I guess I'm doing something wrong but, I can't get the 2600n to print in color. I installed another driver for color and changed the setting to color but, still prints in grey scale. here's a pic of settings:

---

### Post by JackDog on 2007-01-05
> **AllanP said:**
> I guess I'm doing something wrong but, I can't get the 2600n to print in color. I installed another driver for color and changed the setting to color but, still prints in grey scale. here's a pic of settings:

This fix is listed on the wiki. I actually did not need it when working with the 2600n, just switching the option from monochrome to color did it for me.


* To get color edit the file /etc/cups/ppd/<printer-name>.ppd and change the configuration item "FoomaticRIP[CommandLine]("https://wiki.ubuntu.com/CommandLine")" to "foo2hp2600-wrapper -c %A" (note the -c which is what you have to add manually)*

---

### Post by AllanP on 2007-01-05
> **JackDog said:**
> This fix is listed on the wiki. I actually did not need it when working with the 2600n, just switching the option from monochrome to color did it for me.


* To get color edit the file /etc/cups/ppd/<printer-name>.ppd and change the configuration item "FoomaticRIP[CommandLine]("https://wiki.ubuntu.com/CommandLine")" to "foo2hp2600-wrapper -c %A" (note the -c which is what you have to add manually)*

Thanks a lot; that did the trick but, not good quality; will still have to resort to that other ahem!, OS to get quality color printing. I did learn one thing though: I tried different ways to edit the file without success (chmod). I finally was able to edit it by "sudo nautilus". So I learned something anyways which is a bonus. Thanks again.

---

### Post by AllanP on 2007-01-08
Regarding quality: I'm afraid I was a little hasty with my quality comment. Checked on Properties and found that I was in Gray scale. I did some more colour printing and found it to be quite satisfactory. Printing from the web however was a bit confusing and didn't always do the colour; even after "Page setup" in Firefox and "Print background images" checked.

---

### Post by Till Kamppeter on 2007-03-07
You do not need to edit the PPD file to change the color mode. You only need to change the default setting of the "Color Mode" option in the gnome-cups-manager. To get a better output quality try also to set "Bits per Plane" to "2 Bits per Plane".

Note that the gnome-cups-manager only sets personal defaults, so other users will still have the old defaults. For system-wide defaults call the CUPS web interface via [http://localhost:631/](http://localhost:631/), click the "Printers" tab and click "Set printer options" at the entry for your printer. Set the above-mentioned options there and try again.

The problems with color accuracy can also be caused by GhostScript. Install the gs-gpl package and then run

sudo update-alternatives --config gs

and choose "gs-gpl". Are the colors better now?

---

### Post by AllanP on 2007-03-07
> **Till Kamppeter said:**
> You do not need to edit the PPD file to change the color mode. You only need to change the default setting of the "Color Mode" option in the gnome-cups-manager. To get a better output quality try also to set "Bits per Plane" to "2 Bits per Plane".

Note that the gnome-cups-manager only sets personal defaults, so other users will still have the old defaults. For system-wide defaults call the CUPS web interface via [http://localhost:631/](http://localhost:631/), click the "Printers" tab and click "Set printer options" at the entry for your printer. Set the above-mentioned options there and try again.

The problems with color accuracy can also be caused by GhostScript. Install the gs-gpl package and then run

sudo update-alternatives --config gs

and choose "gs-gpl". Are the colors better now?

Actually I had set CUPS to colour and it never worked. I did the -c and it worked fine. I am actually quite satisfied with the colour now for my needs but, I will try your suggestions. I installed the gs-gpl and will try the "2 Bits per Plane"

Wow what a neat web site. All went well except for some reason it didn't communicate with my printer to print a test page.


Thanks for your help.

---

