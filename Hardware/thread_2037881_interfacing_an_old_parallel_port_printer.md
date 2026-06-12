---
title: "interfacing an old parallel port printer"
date: 2012-08-05
forum: Hardware
---

### Post by Sleepy-zz-John on 2012-08-05
Hi,  I've dug out an old Amstrad LQ3500di parallel port printer and I'm trying to get it to print via a USB to parallel port interface showing as 
```
Bus 003 Device 005: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
``` 
I've used sudo system-config-printer to add this printer combination as an Epson LQ-500 Foomatic/epson (recommended) which I believe is a near equivalent from a driver point of view,  and Device URI is showing as 

serial:/dev/ttyUSB1

Printer State shows as Idle,  and when I press the "Print Test Page" button,  I see "Submitted  - Test page submitted as job XX",  but no sign of life from the printer at all.  

Earlier today I managed to get my USB interface and printer combination to successfully print a test page in Windows XP,  so I don't think there can be any hardware problem with my setup.  In that case I used Windows' driver for an Epson LQ-550

In my Oneiric I've also tried setting my printer combination as Epson LQ-570+ Foomatic/epson (recommended),  and equally got a "Submitted  - Test page submitted as job XX" window show up,  but still no sign of life out of the printer. 

So now I'm afraid I'm stuck.  Any ideas what else I could try or check?

---

### Post by anewguy on 2012-08-06
You're going to need to get that associated to lp0 somehow instead of the usb device.  I did a search of the net and some things did show up, including an old post in this forum.  It deals with the same adapter but a different printer, but none the less helps get you to having lp0.  You apparently have the printer and driver installed, so you won't have to do that part of things (unless you want to back out what you've done and follow this completely):

 January 6th, 2010    #15  
thodges999 
Just Give Me the Beans!

 

Join Date: Dec 2006
Location: United Kingdom
Beans: 46 
Ubuntu 10.04 Lucid Lynx  Re: [SOLVED] USB Parallel Printer Cable Setup 

--------------------------------------------------------------------------------

Quote:
Originally Posted by UsedBits  
What? What worked to get your no name connector to connect the parallel printer through a USB port?

I tried the uriarallel:/dev/usb/lp0, but it didn't work. Would someone walk through all of the steps to make this technique work, i.e. steps to configure a printer with this trick? 

What worked for me was as follows;
1. Select System, Admin, Printing from the menu
2. Press New and when the dialogue box comes up for New Printer press forward and then select your printer (HP LJ4 in my case). I know this will not be for a USB connection but we'll fix that later.
3. Once you have selected your printer driver press Apply and when asked if you want to print a test page select No.
4. Now you have your printer driver installed you should see it in the Printer Configuration window. Right click on it and select properties.
5. Change the Device URL to parallel:/dev/usb/lp0 and press Apply.

Thats it and it worked for me and others. If this fails please post the results of running lsusb in Terminal. 

<<<<<<<  end of copied post  >>>>>>
 
What I'm not certain of is whether or not the device link is still the same now since the above was written for an old version of Ubuntu.  I'm not in linux right now so I can't check that at this moment.  I'll come back and edit this when I get linux booted again.

---

### Post by Sleepy-zz-John on 2012-08-06
Thanks for looking into this and searching, anewguy.

As far as I can see,  all I needed to do was go straight to UsedBits' step 5 and change my Device URI entry there to parallel:/dev/usb/lp0  so that's what I've now tried.

Afraid this looks like a step backwards,  though,  'cos now my Printer State shows as

"Processing - Printer not connected; will retry in 30 seconds"

In contradiction to that,  when I press "Print Test Page"  I still get the same little "submitted" window showing up saying "Test page submitted as job XX"  and the printer remains stubbornly silent as before.  It seems as if "Printer Properties" doesn't really need any backward confirmation from my parallel port converter or from my printer and is quite happy to dispatch print jobs into a black hole.

Step 5 didn't cause any change to my lsusb output (apart from a Device number change after I unplugged and replugged my converter's USB lead) and I'm not clear what change to expect there.

So stuck again,  unfortunately!     Any further suggestions?

  Tks

---

### Post by HermanAB on 2012-08-06
Looks like you are poking in the dark.

What you should do is look at /dev and see what the device name is:
$ ls /dev

and
$ ls /dev/usb

or whatever. Poke around in /dev and figure it out.

---

### Post by lkraemer on 2012-08-07
Read this (Posting #2) at:
[http://ubuntuforums.org/showthread.php?t=1903404&highlight=usb+parallel](http://ubuntuforums.org/showthread.php?t=1903404&highlight=usb+parallel)

Then post what devices you find, on your system.

Larry

---

