---
title: "Having Wifi trouble"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by SafariAl on 2008-04-19
Ok first off I'd like to note that I am a complete beginner, and need as much detail as possible.

Anyway, I own a HP dv6000, so yes I have broadcom. I've been through almost every tutorial I can find, and didn't come up with a single solution :(. I've used an offline installer, and nothing happened there. Any solutions, would be appreciated greatly. Thanks again

-Al

---

### Post by thorwood on 2008-04-19
get ndiswrapper (its in synaptic) and use the windows driver

---

### Post by SafariAl on 2008-04-19
ok i have the ndiswrapper installed, now how do i use it :P.

---

### Post by SafariAl on 2008-04-19
Everyone, I've managed to get the blue LED light on, but am not sure what to do next. :confused:

---

### Post by thorwood on 2008-04-20
use this the original thread is [http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321]("http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321") so thank him

Wireless Card Setup
Download and extract the files I have here.
[http://www.darkstang.com/wifi.tar.bz2](http://www.darkstang.com/wifi.tar.bz2)
Now go to System > Administration > Synaptic Package Manager.
While we're here we're going to unlock all our repositories. Go Settings > Repositories. Check all the boxes on the first page except for the CD, and hit close. A window will pop up telling you that you need to reload your packages. Go ahead and close that window, and click reload at the top.
Once that is finished click in the main window and start typing “ndiswrapper”. It will automatically scroll down and find it. Click the box next to “ndiswrapper-utils” and click “Mark for Installation”. Now go ahead and click Apply at the top.
After that is installed open a terminal window. Applications > Accessories > Terminal. Navigate to where you saved the drivers I had you download and extract. Now run the following
Code:

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m

Our wireless driver is now installed but not working just yet. It's currently being blocked by another driver that is trying to run, so we need to block this other driver. Run
Code:

sudo gedit /etc/modprobe.d/blacklist

A text editor will pop up with the blacklist. Go to the end, start a new line, and enter “blacklist bcm43xx” without quotes. Save the file.
Now for some reason ndiswrapper doesn't load automatically when it starts up. So now let's add it to the modules list.
Code:

sudo gedit /etc/modules

Make a new line and add "ndiswrapper".

After a restart your wireless should be working and the light should be glowing blue. Congratulations, you now have a functional wireless card.

Now that you have a functional laptop, lets go ahead and do those updates.

---

