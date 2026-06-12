---
title: "lockups and ATI reinstall problem"
date: 2012-05-16
forum: Hardware
---

### Post by eulu on 2012-05-16
I have occasional system lockups (12.04x64) so decided to try some troubleshooting... Sometimes it won't lock up for days but then it might lock up twice in one day.. Doesn't seem to be heat related but it's possible.. 

I figured that it could possibly be related to my graphics card because it will sometimes lock up when trying to get back to my desktop while xscreensaver is running..  Other times are when flash video is streaming from within firefox.. It's hard to say much beyond that because I always have a lot going on... 

My video card is an old Radeon X1650 (256MB). It was running fine before with two lcd monitors hooked up, except for these occasional lockups.. 

I have another video card that I tried to install again, an nvidia 7950GT (512MB).. I couldn't get that working well when I first installed ubuntu back in March, so I reinstalled ubuntu 12.04 with this older ATI card back then.. 

I couldn't get the nvidia card working this time either. I tried different driver sets including the latest .53 but it doesn't detect my main monitor properly (calls it a CRT) and only gives me 1024 resolution and my second monitor just has a white screen. After hours of reading suggestions and messing with it, and reading about other similar bugfests, I gave up.

Now I have plugged the ATI card back in, but the max resolution on both screens is now only 1024 instead of the desired 1280. I followed a command I found for uninstalling all nvidia data, but it now appears that no video drivers are installed at all..

I am wondering if it would be a good time/idea to try some ATI proprietary drivers, but I haven't found any instructions yet.. 

Thanks for any advice..

---

### Post by eulu on 2012-05-16
Well I pulled a brilliant move and decided to try some proprietary ATI drivers (via [this link]("http://www.techlw.com/2012/04/install-ati-catalyst-123-drivers-on.html")).. Big mistake.. Couldn't even boot after that. Got a message about running in low graphics mode and couldn't get past it..  Even tried the fail safe graphics mode and it still got stuck there.. 

SO I plugged my nvidia card back in, and guess what? I've got my main lcd detected properly and in 1280. What did I do? I didn't plug my secondary monitor in.. I didn't even screw down the card yet.. I just figured I was going to use the nvidia card to get back in and figure out how to remove the ati drivers.. 

But now my next move will be to plug the other monitor in and see what happens.. This is so magical.

---

### Post by eulu on 2012-05-16
Ok well that was another waste of time. I am amazed by any of you who are happily running multimon with an nvidia card.. Just the mere act of plugging the second monitor in sent the system into flip out mode..

On a better note, this time I found some good instructions [here]("http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu") and my ati card is running normal again with the open source drivers..

My next move will be to try the proprietary drivers with a better method on that page, but not right now.. This stuff is time consuming! *eyes-crossed*

---

### Post by QIII on 2012-05-16
You won't find a usable proprietary driver for that card.  It is no longer supported by ATI except with the legacy driver and that driver will not work with xserver any longer.  That happened in 2008, so you are limited to the open source driver.

---

