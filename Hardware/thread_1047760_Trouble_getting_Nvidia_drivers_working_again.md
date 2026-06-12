---
title: "Trouble getting Nvidia drivers working again"
date: 2009-01-22
forum: Hardware
---

### Post by jayekaiser on 2009-01-22
I have been running Ubuntu 8.10 with the nvidia 177 drivers on this laptop for about a month now without any problem until recently.

I decided to try the nvidia-180.22 drivers to fix some graphical glitches that I was getting with AWN and compizfusion, however, somewhere in the process, I managed to royally screw up my video hardware settings.

After having problems getting the 180 drivers to work I tried reverting to the 177 drivers, but they would not work any more.

I have tried several methods to get up and running again:
1. Tried using synaptic to remove all nvidia driver files and reinstall them
2. Tried enabling the drivers from the hardware drivers menu (it displays 173, 177, and 180 as options to enable)
3. Tried fixing it with  sudo dpkg-reconfigure xserver-xorg (found through googling)
4. Lastly, I've tried installing/uninstalling through Envyng

Regardless of what I do, I'm getting this on boot up every time:

> Ubuntu is running in low graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure them yourself.

I'm at a loss at this point and will take help from whoever can offer it.  Just let me know if there are any logs or error reports that I need to post here for better information.

(Sorry if the post is long, just trying to be as detailed as possible)

---

### Post by angliski on 2009-01-22
Don't know if this will help. but my install told me that the drivers were installed and activated when I checked the hardwasre drivers, but I only got 800x600.

I went into applications > add/remove >system tools and then typed nividia in the search box. This bought up a list of nvidia drivers and I selected 177 and downloaded it. It installed itself, all i haad to do was reboot.

Hope this helps

Steve

---

### Post by Coinneach on 2009-01-22
thanks angliski .. I was wondering were they were

---

### Post by jayekaiser on 2009-01-22
Thanks for the reply!

If I understand you correctly you're talking about searching for nvidia in a package manager like synaptic?  I've actually installed like that a few times and it hasn't worked, I get the same result as if I use Envyng.

However I did try using the .run script from Nvidia's website for the 173 drivers (couldn't find the 177 drivers) and it gave me errors, I checked the log file and found something interesting:

> echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;	

I'm not sure what to make of this but it seems that I am missing some configuration files which could explain a lot of things.

Anyone recognize what the problem could be?

---

### Post by jayekaiser on 2009-01-23
Is there no one out there that can help me with this?  It's starting to look like my only alternatives are to either do a complete reinstall (which I'd like to avoid because of the hours of work I had to put in getting everything working in the first place) or use vista exclusively.

I've done a lot of searching on this issue and have not found any solutions other than "reinstall the drivers" which is NOT fixing the problem.  I get this message once I boot up every time after reinstalling or uninstalling/installing, regardless of driver version:

> Ubuntu is running in low graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure them yourself.


---

