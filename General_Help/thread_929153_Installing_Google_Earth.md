---
title: "Installing Google Earth"
date: 2008-09-24
forum: General Help
---

### Post by moonguide on 2008-09-24
I installed Ubuntu for the first time last week. I have an AMD Athlon XP 2100+ processor with 1 Gb of RAM and an NVIDIA GeForce2 MX/MX 400 video card.

I downloaded the latest version of Google Earth (4.3), followed some instructions I found on the web (don't remember where) and installed if as follows:

sudo sh GoogleEarthLinux.bin

I didn't see the warning about not starting Google Earth from the button at the end of the install and went ahead and started it, forgetting that it would be running with root privileges. I visited a number of places, setting place marks as I went. At some point GE froze. I could still move the mouse to other windows, but after a short time, they froze. I was unable to exit the programs or switch to a terminal screen. I had to power cycle the machine to get it running again.

Once I recovered from that problem I tried running GE again. The splash screen displayed and the program window opened, but the star field did not move and the earth did not appear. I went looking on the web for folks with similar experiences and found the warning about not running it at the end of the install. I found another instruction on how to uninstall it, did so, and then tried re-installing it the "right" way. Same result -- program window but no earth. I uninstalled it again and found that there is a package for it, so installed it once again with apt-get. Same problem.

Further Googling led me to medibuntu and how to install GE with Synaptic. I un-installed the previous version and tried installing with Synaptic. I now have a new problem -- no indication that GE was installed anywhere on the machine.

Any ideas on where to go next with my troubleshooting will be greatly appreciated.

---

### Post by Thingymebob on 2008-09-25
if you have installed with medibuntu then you should be able to type googleearth in a terminal and it will launch.

You can add it to your menu by
System>Preferences>Main Menu
 Select the category you want it to appear in then click 'New Item'
Set the following:
*Type: Application
*Name: Google Earth
*Command: googleearth

Click the springboard icon to change the icon (the google earth icon should be in /usr/share/pixmaps)

OK - and you're done.

---

### Post by hyper_ch on 2008-09-25
just use medibuntu to install GE

---

### Post by moonguide on 2008-09-25
> **Thingymebob said:**
> if you have installed with medibuntu then you should be able to type googleearth in a terminal and it will launch.

You can add it to your menu by
System>Preferences>Main Menu
 Select the category you want it to appear in then click 'New Item'
Set the following:
*Type: Application
*Name: Google Earth
*Command: googleearth

Click the springboard icon to change the icon (the google earth icon should be in /usr/share/pixmaps)

OK - and you're done.

OK. I expected to find the icon either on the desktop, or in the Applications menu, or both. I didn't know I had to add it myself.

I successfully launched the program from at terminal window, and also successfully installed it in the Application/Network menu, where it also launches successfully.

However, it still does not function correctly. I still only get the star field and no earth. The "Fly To" box accepts an address, but nothing happens when I click on the magnifying glass. It does exit correctly when I click on either the File/exit menu item, or the x in the upper right hand corner of the window. Various other parts of the GUI work as far as they go -- I can hide the sidbar, look at the Find Businesses an Directions tabs, but of course, there's nothing for them to do.

So, what sort of problem do I have, and where should I look next to get it working correctly?

Thanks for the pointers.

---

### Post by moonguide on 2008-09-25
Thanks, hyper_ch. I did use medibuntu, and as in my other reply, have partial success.

---

### Post by Thingymebob on 2008-09-26
Google earth may not be logging on to the server,
Does it successfully connect when you start it? You should get a message something like
"Performing Google Earth server Login"

When you start from the terminal do you get any errors in the terminal window?

Also Compiz causes problems with my google earth, so i normally switch to metacity when using it.

You can do this with
metacity --replace 
in a terminal

then
compiz --replace
when you're done,

alternatively you can install fusion-icon from the repositories which will give an icon in your notification area, you can switch between wms from there

---

### Post by Sycron on 2008-09-26
I ahve too problems with google earth and compzi fusion.

---

### Post by moonguide on 2008-09-30
> **Thingymebob said:**
> Google earth may not be logging on to the server,
Does it successfully connect when you start it? You should get a message something like
"Performing Google Earth server Login"

That sounds like it may be the problem. I do not get that message when I start the program. On my XP laptop, The image of the earth shows up first, then a message about "My Places", but no messages on my Ubuntu desktop.

> 
When you start from the terminal do you get any errors in the terminal window?

No. I don't get any messages in the terminal window.

> 
Also Compiz causes problems with my google earth, so i normally switch to metacity when using it.

You can do this with
metacity --replace 
in a terminal

then
compiz --replace
when you're done,

I tried those, and had to restart X with <ctrl><alt><bksp>. Should I have done those with sudo?

> 
alternatively you can install fusion-icon from the repositories which will give an icon in your notification area, you can switch between wms from there

That worked. I have the ability, with fusion-icon, to switch between Metacity and Compiz.

I'm now using Metacity. I tried Google Earth, but still get the same results. I'm thinking your observation that I'm not connecting to the GE server makes the most sense. How do I figure out why that's not working?

Thanks for your help.

---

### Post by dcstar on 2008-09-30
> **hyper_ch said:**
> just use medibuntu to install GE

Or use the googleearth-package package provided in the repositories.

---

### Post by Sycron on 2008-10-01
Good luck, and keep us posted if doesn't work.

---

### Post by moonguide on 2008-10-01
It turns out that the problem was ownership and permissions related. I was encouraged to run strace when I started googleearth. That showed:

stat64("/home/rsteff/.config/Google/GoogleEarthPlus.conf", 
{st_mode=S_IFREG|0600, st_size=676, ...}) = 0
open("/home/rsteff/.config/Google/GoogleEarthPlus.conf", 
O_RDONLY|O_LARGEFILE) = -1 EACCES (Permission denied)

I discovered that .config/Google was owned by root:root, as was the file within it. I tried just changing the ownership of both to rsteff:rsteff, but that was not enough. I renamed GoogleEarthPlus.conf so that it would look to the program as if it did not exist. The program created a new copy and started normally.

Thanks to all for your ideas.

---

