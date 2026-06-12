---
title: "Voyager LG Can't see USB Storage Device"
date: 2009-04-23
forum: Hardware
---

### Post by JoseTaurus on 2009-04-23
I can't see the USB mass storage device in Ubuntu Jaunty RC
I don't know how to work bitpim.
I plug in the phone and click find phone it dosn't work. I turn the phone in USB mass storage device mode and it takes forever and the OS dosn't recognize it.
Someone help?:(

---

### Post by JoseTaurus on 2009-04-25
bump,
I guess noone knows the answer.
Ill just go back to windows in a few days after backing up data.
This os is great, but since my phone dosn't work. whats the point? I shouldve just stayed on Vista where everything worked just fine. It may not be the most secure os, but it works fine with devices

---

### Post by JoseTaurus on 2009-04-26
ahahaha!
For anyone who has trouble with this phone.
I messed with Bitpim and I configured the port to USB Phone and it worked.
Seems by default Ubuntu thinks its a modem XD ahaha!

I got the phone to work in ubuntu XD. yay Ill stay on the OS

---

### Post by e.m.fields on 2009-11-03
> **JoseTaurus said:**
> ahahaha!
For anyone who has trouble with this phone.
I messed with Bitpim and I configured the port to USB Phone and it worked.
Seems by default Ubuntu thinks its a modem XD ahaha!

I got the phone to work in ubuntu XD. yay Ill stay on the OS

JoseTaurus!
Can you please tell us how to do this? Thanks!

---

### Post by cforput on 2010-04-21
I am about to set up BitPim again. I had it working once but on Hardy. I am now on Karmic. Here are the directions I wrote up when I did it the first time.Some of it was cut and pasted from other posts and some of it I documented as I went through the processes. No guarantees that this will work.

BITPIM Directions

How to get BitPim to detect your cellphone in Ubuntu*Linux
31 08 2008 

Preparation
I have always used bitpim in windows, because for some reason I could never get it to detect my phone in Ubuntu Linux, the program would run fine, it would just ‘fail’ to detect the phone. I recently found a way to get bitpim to detect my phone (a Verizon Wireless LG VX8350 ) in Ubuntu.

What you need:
Ubuntu 
Your cellphone 
A usb cable that connects your cellphone to a computer. 
double check that your phone is supported, check this site, under the dropdown ‘phones’ for more info: [http://www.bitpim.org/help/](http://www.bitpim.org/help/) 

Installation
1.Download latest official release from [http://www.bitpim.org](http://www.bitpim.org)
2.Select the DEB version
3.As of this writing, only a i386 version is available
  1.Open a terminal
  2.Navigate to the folder that contains the BitPim file you just        downloaded
  3.Enter the command: sudo dpkg --force-architecture -i bitpim_1.0.6_i386.deb (note: make sure you use the actual name of the bitpim.deb file that you downloaded)
4.Enter your password

Setting Up An Icon
The BitPim deb doesn’t create an icon for our menu. However, the command is simply bitpim, so we can create a menu entry.
1.Download the BitPim Icon here: [http://polygon89.files.wordpress.com/2008/08/bitpim.png](http://polygon89.files.wordpress.com/2008/08/bitpim.png)
2.Open up the terminal (Applications > Accessories > Terminal ) and then type cd ~/Desktop
3.sudo cp bitpimRose.png /usr/share/pixmaps/ (This will copy the picture file into a folder that is used mostly for icons)
4.Enter your password
5.Go to System > Preferences > Main Menu
6.Click on “Accessories” 
7.Click on the “New Item” button
8.In the box that pops up enter “BitPim” under Name
9.Enter “bitpim” for the Command (must be lower case)
10.For Description, enter “PIM that interfaces with your cellphone” 
11.Click on the spring icon
12.In the file chooser dialog enter /usr/share/pixmaps/ in the address bar above the icons and press enter
13.Scroll down until you find ‘bitpimRose.png’ and select it
14.Click on OK save the selected Icon
15.Click on OK to create the new menu item for BitPim with the Rose icon
16.Test the new item you just created
  1.Click on Applications 
  2.Scroll down to accessories (or the locations where you added the new item)
  3.Highlight the BitPim Rose
  4.Click on OK
  5.If everything was set up correctly, BitPim will start up.

Detecting Your Phone
Now, we need to install a program to make it so Ubuntu detects and sets correct permissions to your cellphone when you plug it in.

1.Download this file to your desktop: 
[http://www.2shared.com/file/3855553/ebd8bf81/MoPOL_0_0_2tar.html](http://www.2shared.com/file/3855553/ebd8bf81/MoPOL_0_0_2tar.html)
2.When it is finished downloading, right click the file, and select “extract here”
3.Open up a terminal session
4.cd ~/Desktop
5.cd Mobile-Phones-on-Linux
6.chmod +x setup.sh
7../setup.sh
8.Enter 1 to setup Hot-plugging
9.Enter 1 for LG phones
10.Reboot your computer
11.Plug in your phone using the USB cable
12.DO NOT sync data. Just press the clear key
13.Start BitPim
  1.Open Terminal
  2.Enter sudo bitpim
  3.Enter your password
14.Click on the silver phone icon
After your computer has restarted, now your phone should be detected. Plug in your phone, and start BitPim. (Using the menu entry we just created, Applications > Accessories > Bitpim ) Once it has started up,* click the Icon of the silver cellphone on the right hand side with the magnifing glass to start the detection process. If all goes well, it should detect your cellphone and ask you to name it. if it does, then congratulatons! everything worked. If it didn’t work, you might want to check the helpfile or the bitpim wiki ([http://www.bitpim.org/help/](http://www.bitpim.org/help/)) for help and to see if your phone is supported

Reinstalling BitPim
If you need to reinstall BitPim
1.Uninstall per normal process (no info available on how to do this as of the writing of this document)
2.Make sure you delete all the files in the user/.bitpim-files folder (leave the folder in place).

---

