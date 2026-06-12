---
title: "Ubuntu Live Cd Doesn't Load on my HPTX1000z Tablet Convertible"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Ulti2001 on 2007-05-14
Hey Guys,
   I just recently bought a HP TX1000z Tablet PC. Problem was it already came with Vista.

However, I read some tutorials and found out i can shrink the hard drive and make it in a ubuntu hard drive

So for my 120 Gig Hard Drive I split it like so

80 Gigs for my Windows Vista (I Hate this But Have to Use it) (Was only able to shrink 50 Gigs)
20 Gig for Ubuntu 7.07
30 Gigs for Fat32 System (Shared Drive)

Then I proceeded to install Ubuntu 7.07 by placing it in the CD-ROM DRIVE

First on LOAD UP this error popped up concerning
[0.00800 Something Something Popped Up] Went Away way too fast to get the whole error]

Firmware Helper [6347] Error Loading /lib/firmware/bcm45xx_microcodes.fw for device 
  '/class/firmware/0000:0300.0' with driver 'unknown'
Firmware Helper [6375] Error Loading /lib/firmware/bcm45xx_microcodes.fw for device 
  '/class/firmware/0000:0300.0' with driver 'unknown'
Firmware Helper [6383] Error Loading /lib/firmware/bcm45xx_microcodes.fw for device 
  '/class/firmware/0000:0300.0' with driver 'unknown'
 Then Says Okay
and Hangs up in Configuring Network Interfaces

So i read more online and found out that Ctrl + C will skip the network interfaces so that what i did

Then it loaded all the way until it was about to load the screen then showed a black screen after showing some weird images that looked like pressure points all over the screen (Only reason i said this is because it a touch screen with not active digitizer) 

I will be looking online but can someone tell me what to do 

I installed the i386 version. I didn't want the 64 bit version

Here are the specs of my comp

AMD Turion 64 X2 2.0 Gigz
2 Gigs RAM
NVidia Go 6150 Graphics Card
120 Gigs harddrive space

Is this a problem with vista that causing this?!?!? I hate vista but don't want to format my computer to get linux on it. 

Thanks for any help guys. Much Help Appreciated.

---

### Post by Ulti2001 on 2007-05-14
Update:

Good News Guys, I changed my mind about the live cd and decided to go to the alternate text based installation. This seemed to work. Another change was no using the wireless and connecting the broadband line to my laptop

Crossing my fingers hope this works

I will probably put a tutorial about this installation once i get everything loaded

Now i also noticed that it thought my graphic card was a network card when it was looking for a network card to connect to. (Nvida was the maker) So lets hope i can find drivers or this 

I will try to solve this problem and place a fix on it for all the hp tx1000z users out there

---

### Post by Shaydog on 2007-06-17
Hi, I'm experiencing a similar error.  I recently got a tx1000z that I dual booted Ubuntu on.  After the installation, I removed the CD and rebooted, and now all I get is a black screen when I try to boot into Ubuntu.  Were you ever able to figure out the cause, or find a workaround?  Is anyone getting a smilar error?

Would appreciate any assistance.

Thanks!

---

### Post by Wattos on 2007-06-17
well, try waiting a bit, Ubuntu might eventually load up. I am having exactly the same problem. Instead of a splash screen (ubuntu loading) i get a black screen. I have found a work around whih seems very strange. If I connect another monitor to my laptop, while booting I press the switch monitor key on my laptop and then switch back, i get the splash screen. 

There  also might be a driver issue. the open source nvidia drivers do not work on my laptp (8600M) so what i had to do is to boot on failsafe and then type:

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
cat /etc/X11/xorg.conf | sed 's/nv/vesa/' > /etc/X11/xorg.conf

This will enable the vesa driver. Then type :

init 3

and see if you get gnome. If you do, restart and boot up normally. If your screen turns black, wait some time, and hopefully youll get te ubuntu login screen

---

### Post by Shaydog on 2007-06-20
I did try that but it left me with an empty xorg.conf file.  Waiting for Ubuntu to load didn't do anything, as I was still left with a black screen.  I also tried changing my driver from "nv" to "vesa" but that didn't seem to do anything.

I'm having trouble finding the HorizSync and VertRefresh values for the WXGA monitor as well, so I haven't tried changing those yet.

This is getting to be a bigger challenge than I thought....

---

### Post by Shaydog on 2007-06-20
I also tried the text installer myself but it didn't change the blank screen problem.   I also cannot hear the login sounds (I believe they should be drums, right?) as other people who are having a similar problem claim to be able to.

---

