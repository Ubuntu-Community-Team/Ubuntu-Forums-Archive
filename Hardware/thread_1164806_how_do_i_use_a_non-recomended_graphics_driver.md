---
title: "how do i use a non-recomended graphics driver"
date: 2009-05-20
forum: Hardware
---

### Post by 900donuts on 2009-05-20
just as the title says.

I have a geforce fx 5200 which seems to be supported by both the 173 and 96 drivers. the hardware drivers gui recommends the 173 driver but that one isn't an option for me because the rig I'm working with doesn't have sse support (athlon 800mhz). So what I want to do is use the 96 driver with my geforce fx 5200. I already tried force feeding an 8.10 rig and it freaked any suggestions?

---

### Post by coffeecat on 2009-05-20
Is Hardware Drivers in System > Administration showing both the 173 and 96 drivers, but recommending the 173? You should be able to highlight the 96, click on 'Activate' and reboot to enable the 96 driver.

By the way, it's not clear which version of Ubuntu you're using. I'm going by how things appear in Jaunty. I seem to remember the Hardwire Drivers GUI looked different in Hardy. In Jaunty, I'm offered the 180 and 173 drivers for my 8400GS card, with the 180 recommended. There was a slight problem with the 180 so I did more or less what I just described - activated the 173 driver, rebooted and the problem went away.

---

### Post by thickhead on 2009-05-20
We had this general problem too. We've used the approach on Toshiba and HP laptops. The latest culprits were a GeForce onboard 6100 with a hardy-amd64 dual core desktop server. They all work fine now:

1. Start the system with a Knoppix 5.1.0 or 5.1.1 CD. (We didn't have such luck with the new 6 cd.)
It will probably fire up the graphics just fine on its own. So it is possible!

2. Identify your Ubuntu partition on the Knoppix desktop, and enable writing (right click the icon).

3. Copy /etc/X11/xorg.conf to your Desktop folder in the Ubuntu. (Use the Knoppix root shell for the copy.)
         cp /etc/X11/xorg.conf /media/hdaN/home/myname/Desktop/xorg.conf-knopp

4. Check that all is well with:
          less /media/hdaN/home/myname/Desktop/xorg.conf

5. If you find yourself looking at a text file of X configuration, you're cool. If not, check your typing of step 3.

6. Reboot the Ubuntu, and go to your desktop, where there should be an xorg.conf-knopp file.

7. Open a terminal and:
        sudo cp /home/myname/Desktop/xorg.conf-knopp /etc/X11

8.. Do no harm. Preserve your old, even if stinky xorg.conf :
       cd /etc/X11          #this gets you to where the config lives. 
       mv xorg.conf xorg.conf-todaydate          #this renames your current xorg.conf

9. Oops! we've just moved out our only xorg.conf. Now replace its functionality with a link:
      ln -s /etc/X11/xorg.conf-knopp xorg.conf

    I like this link rather than a copy, so you can easily keep many different named xorg.conf files in the /etc/X11/ and experiment with using each. You don't lose track of which is currently doing the xorg.conf work.

10. Check the link is good:
       less /etc/X11/xorg.conf 
     If you see the xorg.conf-knopp , restart the X-server, with ctrl-alt-backspace, or restart ubuntu.

11.. It worked? It usually does. Celebrate! Knoppix does a fine job of hardware detection and configuration, even in odd onboard installations.

      It didn't? Waaah! Easy download of odd and maybe appropriate missing driver software is often possible for nvidia and ati hardware with ENVY from 
          [http://www.albertomilone.com/](http://www.albertomilone.com/)
      He has easy automated driver installs for most nvidia and ati, but imho they work less reliably with onboard and odd chipsets. 

In summary, you may need knoppix to get a sensible xorg.conf and Envy to get a compatible set of driver software if it isn't already present in Ubuntu. Yes, you can do all this piece at a time but we find these one or two tools usually save a lot of manual tweaking and experiment. 
We appologize for the lack of elegance.

---

### Post by 900donuts on 2009-05-20
I got it to work with 9.04 

DETAILS:
the rig is in my garage and as a result has no internet access so I had to sneaker net everything over to it(I wanted to get tv out working first since there is no place for another vga monitor inside). the rig has an athlon 800mhz slotA (which has no sse support). the first distro I tried on it was xubuntu 8.10 the hardware drivers gui only wanted the 173 driver despite the 96 driver being installed. I tried useing nvidia-xconfig to make it enable the 96 driver but the machine would flip out over config file phrasing. thing moved smoother with 9.04 I installed 96 driver and rebooted. when I checked the hardware drivers gui again there was an option to activate the 96 driver.

the problem now is that it isn't giving me a screen resolution higher than 640x480 stay tuned...:popcorn:

---

