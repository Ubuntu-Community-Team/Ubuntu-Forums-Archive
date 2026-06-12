---
title: "Vertical screen wrap"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by lingenfr on 2009-01-26
When running from the live CD, everything looked good. Now, after installed, about 1/4 of my bottom taskbar is on top. I have fooled with Appearance and tried changing resolution back and forth, but the wrap occurs in all resolutions. Is there a simple way to fix this? Thanks.

SOLUTION This is no longer a problem. It was fixed with the current driver (10.4)

(quoted from this thread [http://ubuntuforums.org/showthread.php?t=1063875](http://ubuntuforums.org/showthread.php?t=1063875) )

So, I went into Synaptic and found xserver-xorg-video-intel. The installed version was 10.3. I highlighted that package and went to the menu Package>Force Version and selected version 10 and applied. I closed out and prevented it from updating. I rebooted and... YEAH! No more vertical wrap.

---

### Post by utnubuuser on 2009-01-26
HI  --  You should provide a little more info.  Computer model video card, if any, etc.
code in terminal: > lspci

Have you tried  > sudo dpkg-reconfigure xserver-xorg

And it's not just the screen needs adjusting?

---

### Post by lingenfr on 2009-01-26
You are absolutely right, sorry. It is a Toshiba Libretto U100.

lspci

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Yes I did try

sudo dpkg-reconfigure xserver-xorg 

No joy. It may be that the screen needs adjusting, but I can't figure out how.

---

### Post by utnubuuser on 2009-01-26
Found a thread applicable to Feisty..

I assume you're in either 8.04 or 8.10?  Is it using the intel driver?  I've read that there've been some issues with the intel driver in 8.10 and that there is now a new one called  ***-glx-180*** somthing or other.  System>>Administration>>Hardware Drivers

Here's the thread > [http://ubuntuforums.org/showthread.php?t=421967](http://ubuntuforums.org/showthread.php?t=421967)

and a model specific thread:> [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100)

---

### Post by lingenfr on 2009-01-26
Thanks. If you notice, that's my wiki page :) No optional driver comes up when I check restricted drivers. BTW when I do the dpkg reconfigure it is not giving me a chance to select my driver. It goes straight to the keyboard settings. I followed the other thread and associated links. I did not see a good fit. I notice on the screen settings, it has selected a refresh of 54hz which is odd. There is no option to adjust it.

---

### Post by lingenfr on 2009-01-31
I did a fresh install and got some info on the problem. After the install, the screen looked good. After the update, I had the screen wrap problem. It is not a kernel problem as booting with the previous kernel does not solve the problem.I assume it is a driver problem.

---

### Post by Tomatz on 2009-01-31
> **lingenfr said:**
> I did a fresh install and got some info on the problem. After the install, the screen looked good. After the update, I had the screen wrap problem. It is not a kernel problem as booting with the previous kernel does not solve the problem.I assume it is a driver problem.

Open a terminal and type:

```
metacity --replace
```

This will temporarily turn compiz off. Let us know the results.

PS. **dpkg-reconfigure xserver-xorg** is now defunct use **gksu displayconfig-gtk** instead. Although this is a bit drastic at this stage ;)

---

### Post by lingenfr on 2009-01-31
I tired it, no effect.

BTW: gksu displayconfig-gtk did nothing. I put in my password and then nothing.

---

### Post by Tomatz on 2009-02-01
> **lingenfr said:**
> I tired it, no effect.

BTW: gksu displayconfig-gtk did nothing. I put in my password and then nothing.


Maybe a typo? Did you remember the dash?

---

### Post by lingenfr on 2009-02-01
Yes, I copied and pasted from your message. When I run it without the gksu it says command not found.

---

### Post by Tomatz on 2009-02-01
Try installing it first :)

```
sudo apt-get install displayconfig-gtk
```

then

```
gksu displayconfig-gtk
```

Just try changing the resolution with the app first ;)

---

### Post by lingenfr on 2009-02-01
lingenfr@ubuntu:~$ sudo apt-get install displayconfig-gtk
[sudo] password for lingenfr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package displayconfig-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package displayconfig-gtk has no installation candidate

I am still looking, but obviously there is no package by that name in the default repositories.

---

### Post by Tomatz on 2009-02-01
> **lingenfr said:**
> lingenfr@ubuntu:~$ sudo apt-get install displayconfig-gtk
[sudo] password for lingenfr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package displayconfig-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package displayconfig-gtk has no installation candidate

I am still looking, but obviously there is no package by that name in the default repositories.

Seems intrepid no longer uses any xorg configuration method (IMO stupid):

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/50468](https://answers.launchpad.net/ubuntu/+source/xorg/+question/50468)

To check you are using the correct drivers:

```
sudo apt-get install xserver-xorg-video-intel
```

Hope that helps.

P.s Have you tried changing the screen resolution in ***System, Preferences, Screen Resolution***?

---

### Post by lingenfr on 2009-02-01
Thanks. As referenced in that link, I am also using the intel driver. I checked and I have the latest version. If you read the links referenced in the link you provided, for me it seems like xrandr may be my only hope. I found that it is provided by x11-xserver-utils which for me was already the newest version. I am going to play with that command and see what I can do.

And yes, of course, using the screen resolution tool was the first thing I tried. It offers no choices other than the current ones.

Also, I thought that I would take a screenshot so folks could see what I was talking about. Unfortunately, in the screenshot, it appears correctly. I took a picture with my camera which is not great, but I think you can get the idea. If you look at the bottom taskbar, you will see that about 30% of it is cut off. If you look at the top taskbar you will see that there is additional taskbar above the normal taskbar. It has some horizontal lines, etc. Check above the red button on the top right.

---

### Post by ingrambw on 2009-02-03
I am having the very same problem on my Libretto running Kubuntu 8.10.  Everything was perfect, then on Sunday I did all the updates sense the 22nd through the 1st and now I have the same wrap problem.

---

### Post by lingenfr on 2009-02-03
Yes, I expect we need to open a bug report for the intel driver. I will try and do that tomorrow. If you get there before me, please post a link so I don't post a duplicate.

---

### Post by ingrambw on 2009-02-03
I am pretty new to Kubuntu and Linux in general, and it looks like you have more background information on the problem, so I will defer to you for the ticket submission.

BTW. When I ran the re-configure on xserver.org it did ask if I wanted to use the framebuffer or not, both a yes and no resulted in the same results after a reboot for each.

---

### Post by lingenfr on 2009-02-03
Yes, same results for me, I should have stated that in my previous message. After going through all of the links previously alluded to, last night I deleted the monitors file under my home directory and reboot, no joy. I will post a link to the bug once I have opened the ticket.

---

### Post by Sebjectivist on 2009-02-06
Me also having this problem on libretto U100 :(. tried everything in this thread plus adding modlines to xorg.conf and deleting/editing monitors.xml in ~/.config/

Maybe it's possible to use older intel driver for the time being?

---

### Post by lingenfr on 2009-02-06
I am thinking the same thing. I am going to research how to roll back to the previous version of the driver. I think that I am going to mount my install CD as a repository and see if I can load that driver as it did not have this problem.

---

### Post by lingenfr on 2009-02-08
Solved. Check the first post. Now to wait for an updated/fixed version. Wait for something newer than 10.3

---

### Post by Sebjectivist on 2009-02-10
Sweet as!! thanks to you lingenfr, and to the creators of synaptic/ubuntu :-)

---

### Post by Mckormick on 2009-02-24
I had the same problem on my Libretto U100 after an update - many thanks to the first poster for the fix.

---

### Post by lingenfr on 2009-04-09
This is no longer a problem. It was fixed with the current driver (10.4)

---

### Post by monsieurps on 2010-06-22
Thanks lingenfr for this thread. Atleast I wasn't the only one who was having this problem. But I am seeing the problem on a 64-bit AMD desktop with the Ubuntu version that I installed yesterday (10.04 LTS 32-bit). 
Veritcal screen wrap, with the mouse pointer offset by a few pixels to the north, taskbar partially visible .
The xserver video amd package version is, xserver-xorg-video-amd 2.11.8-4 and the geode package is, xserver-xorg-video-geode 2.11.8-4. Is it possible that the problem lies in the new geode package (and not the intel/amd driver) ?

---

