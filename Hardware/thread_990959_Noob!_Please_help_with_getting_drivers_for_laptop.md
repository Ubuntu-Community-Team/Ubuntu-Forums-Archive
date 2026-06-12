---
title: "Noob! Please help with getting drivers for laptop"
date: 2008-11-23
forum: Hardware
---

### Post by lash9420 on 2008-11-23
I am a complete noob at Linux and I really wanted to try and install Ubuntu again on my laptop. My graphics and wireless will not work. These are just two thing I have noticed in the short time I have played around with it. There may be other things that need to be installed also. Here's the link to my specs: [[pcworld.com]]("http://www.pcworld.com/shopping/detail/prtprdid,76768659-sortby,retailer/specs.html")

If you can, please walk me through step by step because I know *nothing*about Ubuntu....

1. Where can I download the drivers for everything I need?
2. How do I install the drivers? Especially since I won't have internet...Put them on a flash drive and install them from their?

Thanks soooo much for your help!!

---

### Post by maestrobwh1 on 2008-11-23
So I assume you are getting a desktop but the graphics are just low quality?  

If you do have a desktop:

Go to System in the menu and then look for Hardware or Hardware Manager (can't recall), and then it will ask you for a password.  It might list your wireless device and/or video and offer tot download the firmware for you.  This would be easiest but again you will have to be be hardwired for this method.

Even if you can't hardwire, get to a graphical desktop or see your devices in the hardware manager, you can run 

$ sudo dpkg-reconfigure -phigh xserver-xorg

in a terminal

this reconfigures your video (more or less for sake of an easy explanation)

then you can either reboot (from terminal it would be "sudo reboot" or restart the X xerver by logging out, look at the options button from the login screen and do that.  It MIGHT be fixed.

The link does not give info on the "brand" of hardware you are using.  We can still find out.

If video isn't better and/or wireless wasn't listed in the Hardware Manager:

do

$ lspci 

at a terminal

copy and paste the line about your video controller here (if you do get a desktop).  If you don't get a desktop, you'll have to write it down.  You could also google search and you might get an answer more quickly.  I bet the driver exists withing ubuntu and might even be on your computer.  There are too many ways to go from this depending on what you find out.  You'll either have to post back here or go from info from other posts.

you can do the same for your wireless.  wireless is actually a bit more tricky.  

you have no means of tethering to an Ethernet port for a bit to do this investigating/fixing?

if that is true, you will have to download deb files for graphics on another computer and copy them and use a manual method.  Again, if this is what you end up having to do, post back or research  "install packages with dpkg"

You might find a book useful:  It is called "Ubuntu hacks."  It is more of a quick reference guide and has a little about everything in it.

---

### Post by lash9420 on 2008-11-23
I am using Ubuntu now as I am writing this and the graphics are still all messed up. I tried going and installing the drivers that it said I needed. I entered my username and password and it just pulled up a box that looked like it was going to load but then disappeared... What should I do now? 

So, yes, I am now have wired internet...

My graphics card is a nVIDIA GeForce Go 7150M

a more detailed spec sheet that I found incase you need more information... [[buy.com]]("http://www.buy.com/prod/hp-pavilion-dv6910us-entertainment-notebook-amd-turion-64-x2-tl-60/q/loc/101/208114055.html")
Thank you!

---

### Post by maestrobwh1 on 2008-11-26
Did you go to the menu

System --> Hardware Manager ?

It will ask you for your password.

What do you see once it comes up?  I am assuming you just have some really low resolution right now then.  If you see nVidia in the box, and you check "enable this driver," you will have to reboot to see changes.  You could just restart the x-server, but rebooting for you might be easier.  

If not, open Synaptic from the Menu  --> System  --> Synaptic Package Manager.

If it isn't there, the other package managers are not that intuitive.  While attached to the net, open a terminal and do

sudo apt-get update && sudo apt-get install synaptic

Then you can go to the System Menu and open Synaptic (you'll need to be attached to the net if you have to install anything)

Using the search function from the toolbar at the top, type in "nvidia"  and see if there is a package pertaining to xorg-nvidia installed.  If not, install it and reboot.  If it is, then search the word "restricted" and see if something that looks like "linux-restricted-modules" and/or "ubuntu-restricted-extras" is installed.  If not, install them... match the ones pertaining to your kernel number and type i.e. Intrepid 8.10 would be 2.6.27-7-blah blah -then probably end with "generic" if it is standard intel or amd machine.  If you installed 64 bit, then just use your intuition.  It will refuse to install if you choose the wrong one anyway.

Reboot... if you still have messed up graphics, you'll have to tweak a file.  I'd rather you not have to start doing that and this should just start working with the right package installed.

I subscribed to this topic so I will get a reply when you post.  I am surprised that no one picked up where I left off.

---

### Post by starcannon on 2008-11-26
Go to:
System>Administration>Hardware Drivers
Enable the drivers listed there, this should *almost *certainly solve your graphics driver.
If wifi is still a no go, post back on that, and we'll see what we can do.

---

### Post by maestrobwh1 on 2008-11-27
Thanks for the assist.  I was trying to get him there but it sounded like he did that and the window disappeared and it looked like it didn't take effect.  

I had a similar issue with my broadcom card, and on two reboots, it just started working.  However, I wanted to give him some more information so he didn't need to post back in the event this did not solve his  issue.

---

### Post by lash9420 on 2008-11-29
I talked to someone today that was kind enough to look at it for a sec and he said that it is not a laptop distro... Or that I will need to download more drivers... Hasn't someone had this problem and made a distro with these drivers? Isn't their a distro that already has the drivers needed for my laptop, HP dv6910?

---

### Post by maestrobwh1 on 2008-11-30
Um, I don't think there is a "laptop distro"

Assuming you chose a 32 bit install disk:

Do this form terminal
> 
sudo apt-get install linux-restricted-modules-2.6.27-9-generic linux-restricted-modules-common linux-backports-modules-intrepid-generic **nvidia-glx-177** 

Say yes to all of the things that it might want to install, including perhaps a new kernel linux-image-2.6.27-9-generic

I picked the bold item after a few minutes of searching and I found this:  

[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)

Then for wireless to work, before rebooting do (assuming you are not using **k**ubuntu)

gksudo gedit /etc/modprobe.d/blacklist

and it will open an editor

add these lines at the bottom

blacklist ath_pci
blacklist ath_hal

then save it.

Reboot and see what happens.  Your wireless might/should actually just work after this update

Based on your model of computer, it looks like you have an Atheros 5007 Wireless chipset supported by the built in ath5k driver.

To confirm this, open a terminal and type 

lspci and look for the word "Atheros"

There are a TON of posts and how to's for the Atheros 5007 here.  Just do a search here for "Atheros 5007" if you still have issues because I am at the end of my knowledge base.

---

