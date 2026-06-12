---
title: "Dell Inspiron 1100 - Installation Ubuntu 6.06 Desktop"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by candtalan on 2006-09-14
My hardware detail - 512 MB RAM, bios A32.

After initial searches and trying many guessed boot options without success, I found the information necessary on the Ubuntu forums (note 1). 

After the file edit process, which was not difficult even for me as someone who has avoided use of command line, things did display correctly, and I am most grateful for the information referenced above.

I am not new to linux but I still find I am unsure of many non gui actions, and other people  even less confident than myself might find this summary useful.

I was also happy to see that the immediate subsequent install from the edited running live cd ubuntu system was also correct in its screen display and needed no further editing of files.

A forum posting on June 5th, 2006 by ssnitily included the following:

===================
Default Installing on a Dell Inspiron 1100
It's well known that the installation resolution for this laptop is incorrect and is locked at 640x480. Since the default installer for 6.06 involves booting and running a GUI and these installation screens are much larger than this it's very difficult to install as you can't see what you are tabbing to and can't click on any buttons as they are well bellow the viewable area on the screen.
===================
My Comment: as it happens, this described the problem I had.
====================
The response on June 6th, 2006 from durableapostle was on the button:

====================
Default Re: Installing on a Dell Inspiron 1100
I had the EXACT same problem. Here's what I did:

1) In a terminal window type: sudo gedit /etc/X11/xorg.conf

2) Change your data to what I have below (actually, add this info, <i>in addition to</i> what you already have):

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Dell 1024x768 Laptop Display Panel"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
Option "dpms"
EndSection

and in Section Screen, change the monitor line to read

Monitor "Monitor0"

3) Save, close gedit, and then restart the x drive (crtl, alt, backspace). It should work.

4) Now, this is the part where you'll need help elsewhere... After a hard restart, this will probably go back to the small screen. You'll need to configure things so that this loads earlier in the startup sequence. I had a friend help w/ this... sorry, I don't know how he did it. Ask around the forums. At least you'll be able to easily fix it every time until you can get help with the part I can't help you with.
=======================

My comment: I had a little uncertainty about the above point 2) because I could see that some lines were obvious additions and one seemed to be replacement.
I  found that point 4) was not relevant to my need to run the live CD and then do an install to hard drive.
=======================

Final Summary:
With this hindsight I would now slightly re-word the posting from  durableapostle to read as follows:
1) In a terminal window type: sudo gedit /etc/X11/xorg.conf

2) Change your data to what I have below
Section "Monitor"
        Identifier      "Monitor0"
VendorName "Monitor Vendor"
ModelName "Dell 1024x768 Laptop Display Panel"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
        Option          "DPMS"
EndSection

and in Section "Screen", change the monitor line to read

Monitor "Monitor0"

3) Save, close gedit, and then restart the X server (crtl, alt, backspace). It should work.

4)If you want to continue to install, double click the Install icon on the desktop, and proceed. My experience was that the installation adopted the current xorg.conf values.

====================
Note 1:
[http://www.ubuntuforums.org/showthread.php?t=190022&highlight=inspiron+1100](http://www.ubuntuforums.org/showthread.php?t=190022&highlight=inspiron+1100)

HTH
alan c

---

### Post by candtalan on 2006-09-15
> **candtalan said:**
> My hardware detail - 512 MB RAM, bios A32.
After initial searches and tr.......
(snipped).......
alan c

I also use kubuntu and had a little more complication trying to do a similar thing as this for Kubuntu Desktop. I think this was because gedit was not available (live cd), or the text editor kate was not coming up in a terminal with sudo, or something like this. 

If anyone is using both Ubuntu and Kubuntu (I do - for demonstrations), and or can help with a Kubuntu specific way to use a -newbie friendly- process equivalent to the Ubuntu related
sudo gedit /etc/X11/xorg.conf
I would be grateful.

I cannot yet rub two sticks properly with vi, and I ended up brutally using chmod 777 on the file, and using kate, with a number of intermediate stages. Very messy particularly for newbies who are stuck with a small display at low res. (It did all work ok finally though, and I am installing kubuntu also now)

tia
alan c

---

### Post by chantrelle on 2006-09-16
My Hardware 
Inspiron 1100
Bios A32
RAM 256 MB
20 Gig HD 
Win XP

So the question is, why is it that the everytime that I go to try and load the CD that I've burned from the download, it refuses to recognize what is on it.  I've tried the following:

Multiple downloads of DD 6.06

Multiple burns to CD using different combos for ISO, with the suggested program CD Burner XP Pro.   I've tried Joilet, and ISO 1, but not ISO 2.  I've also set it to be bootable with Win XP standards.

The question I am coming to is whether there is something other than redirecting the BIOS to boot off the CD Drive.   Is there another setting that needs to be altered?  Or do I need to adjust the speed?  Use ISO 2 for the burn?  

Rather baffled, but it's a Dell so I'm showing some patience.

Thanks,

Liam

---

### Post by candtalan on 2006-09-20
> **candtalan said:**
> I also use kubuntu and had a little more complication trying to do a similar thing as this for Kubuntu Desktop. I think this was because gedit was not available (live cd), or the text editor kate was not coming up in a terminal with sudo, or something like this. 

If anyone is using both Ubuntu and Kubuntu (I do - for demonstrations), and or can help with a Kubuntu specific way to use a -newbie friendly- process equivalent to the Ubuntu related
sudo gedit /etc/X11/xorg.conf
I would be grateful.

I cannot yet rub two sticks properly with vi, and I ended up brutally using chmod 777 on the file, and using kate, with a number of intermediate stages. Very messy particularly for newbies who are stuck with a small display at low res. (It did all work ok finally though, and I am installing kubuntu also now)

tia
alan c


I have now had more time to look at this and have found a method which seems ok. I am not sure if it is the best method though, but it works:

using a terminal window
sudo chmod 777 /etc/X11/xorg.conf

(note the upper case X)
this removes restrictions protecting the file xorg.conf and allows it to be edited.

I then edited the file (using kate) as detailed earlier in this thread and restarted the xserver display with control-alt-backspace.

As it happens, I wanted something to help with doing this procedure at any time I used the Kubuntu 6.06 desktop (live) cd in this machine - say, for demonstrations.

So after editing the xorg.conf file I copied it to a usb stick as
xorg.conf

The edited copy of xorg.conf file resided in the usb stick and could be seen as

/media/sda1/xorg.conf
because the usb stick was automounted as sda1 onto directory /media

I then used kate editor to create a new file containing the two lines
sudo chmod 777 /etc/X11/xorg.conf
cp /media/sda1/xorg.conf /etc/X11

and for convenience I saved this also onto the usbstick, say, as inspiron1100-fix-kubuntu

Now, after booting with the live cd I can insert the usb stick, and copy the two lines of text into a terminal, and press return. 
Then restart the xserver. More convenient than editing the file again etc.

---

