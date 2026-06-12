---
title: "Resolution Help"
date: 2008-10-12
forum: General Help
---

### Post by sjrf on 2008-10-12
Greetings,

I was happy when I received my Ubuntu cd last week, as my Windows partition was extremely messed up, and I had been wanting to repartition my hard drive with Ubuntu. The computer that I have did not come with a cd drive, so I purchased an external cd drive that just plugs into the usb. However, it's not recognized as a cd drive (while restarting the computer, and setting the boot order to boot from cd), so I booted up Windows and the cd did run and opened up the Ubuntu installation cd, which actually gave me an option to make a driver for the external cd drive, so that I could install it that way, so I rebooted, and was able to choose between Ubuntu or Windows this time, so I chose Ubuntu.

I was really pleased with it once I was finished installing it. However, the Ubuntu screen resolution didn't fit my monitor's, as the left side of the screen was actually being cut off, leaving a rather large black line to the right. So after a bit of excavating, I came across the application that would change my screen resolution. I accidentally clicked on the wrong resolution (the lowest one), and pressed the ok button, which made the bottom of the screen now cut off by half, so I couldn't see past the top of the screen resolution bar. So I had to resort to using tab, enter, and arrow keys to make my way around, completely oblivious to what I was changing, but I thought it couldn't get much worse. Well I actually did change the resolution back to the largest size (the correct one for my monitor), but accidentally changed the orientation to upside down in the process. 

The screen then changed to a black background, but had two very small upside down Ubuntu desktop screens which I assumed was because of the two screens you can switch from. Anyways, I couldn't move my mouse or press any buttons, so I rebooted to see if it would change anything. Well, after logging in, my screen is completely that beige default color that Ubuntu is installed in, and there are absolutely no visible menus or windows. I've pressed many buttons to see if anything would happen, but to no avail. I've tried inserting the Ubuntu cd back into the external cd drive, but it isn't read anymore.

I would really appreciate any information or help with my problem, thank you.

---

### Post by matey3 on 2008-10-13
I found in another thread;
you do an Alt F2 then put this line in it to reconfig the display:
 gksu displayconfig-gtk
I changed the video card model to no avail but when I change my screen from generic back to Acer (or whatever brand u have) it gave me a lit of higher resolution to choose from but got to log off and back in.
good luck

oh BTW I didnt click on the Test the 1st time so it did not work. so make sure to run the test and accept the new settings then you can go to the system-preference-screen resolution to change it.

---

