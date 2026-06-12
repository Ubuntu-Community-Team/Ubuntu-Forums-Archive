---
title: "Anyone have one of the Chinese MD80 clone MiniDV cameras working as a webcam?"
date: 2010-01-27
forum: Hardware
---

### Post by jarthurs on 2010-01-27
I recently bought a cheap Chinese MD80 clone (mine was labeled as a YSB-001) it can record 720x480 30fps video to a MicroSD card. It is apparently also capable of being used as a regular webcam.

lsusb reveals.

Bus 001 Device 004: ID 04fc:0171 Sunplus Technology Co., Ltd

Ubuntu (Karmic) sees it fine as a mass storage device and I can read video files from the MicroSD card, but no luck accessing the webcam side of things.

Regards,
Jason.

---

### Post by Purplecatty on 2010-01-27
> **jarthurs said:**
> I recently bought a cheap Chinese MD80 clone (mine was labeled as a YSB-001) it can record 720x480 30fps video to a MicroSD card. It is apparently also capable of being used as a regular webcam.

lsusb reveals.

Bus 001 Device 004: ID 04fc:0171 Sunplus Technology Co., Ltd

Ubuntu (Karmic) sees it fine as a mass storage device and I can read video files from the MicroSD card, but no luck accessing the webcam side of things.

Regards,
Jason.

You might want to check your camera's setup menu to see if you can switch from "storage" to "Webcam".  

I have cheap Mastonic digital 4.0 megapix camera which is capable running webcam.  It have menu allowing me to switch from "storage" to "webcam" mode.  

So I don't know if your camera have it but dig in and see what you can find.  If your camera have it, set it and check to see if Ubuntu would work with it.

To be honest, All Linuxes works very well with Driverless webcams.  I have Logitech Vision Pro for Mac which is a cross platform webcam that just plug and play, no drivers needed to install.  

There are list of compatible/incompatible webcams on list that you might want to check it out. 

here's the site:  [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

I did have issue with it which is Ubuntu's flaw that it works perfectly fine with Guvcview webcam viewer/recorder.  When I enable Ekigna (similiar to Skype), something screwing up the Linux-uvc driver.  Afterward, Guvcview stopped working.  So did recently installed Xawtv won't work either.  I suspect that linux-uvc needed to be reinstalled.  It's not in Ubuntu repository so have to manually download from website.

Catty

---

### Post by thunderdan on 2010-01-28
Mine came in the mail today. There was a CD with mine with a Word document for a manual. It said to press the mode button while it was plugged into the computer. I got it to work as a webcam on my Windows machine, no problem. Now I'm trying to figure out how to do it with Ubuntu. I have no experience with webcams, though. I'll post more if I get it working.

---

### Post by jarthurs on 2010-01-28
> **thunderdan said:**
> Mine came in the mail today. There was a CD with mine with a Word document for a manual. It said to press the mode button while it was plugged into the computer. I got it to work as a webcam on my Windows machine, no problem. Now I'm trying to figure out how to do it with Ubuntu. I have no experience with webcams, though. I'll post more if I get it working.

Well spotted, I'd kind of glossed over the Chinglish in that part of the manual! Pressing the mode button does indeed take the device out of mass storage mode. 

lsusb now lists it as:

Bus 001 Device 013: ID 04fc:1528 Sunplus Technology Co., Ltd 

so the device ID has changed, unfortunately it doesn't seem to get picked up automatically (as with most of the generic webcams I've used before).

Will keep digging but I'm finding even less for 04fc:1528 than the previous USB ID.

Thanks,
Jason.

---

### Post by rewolff on 2010-02-23
Well searching the internet landed ME on this page :-)

I'm vaguely suspecting it's UVC, so i'll try that. Try prodding me if I don't report back.. :-)

---

### Post by rewolff on 2010-02-24
Update/kick... 

There is mention of "SCPA533" in the firmware. Now the Linux kernel has drivers for the gspca family of chips and a driver called 5xx litterally. (I think there were several different files 508, 564 before that got merged). 

It doesn't work with my current kernel version. I'll have to look into upgrading to the newest kernel.

---

### Post by sr20ve on 2010-03-22
This camera is very similar, but it's the fake keychain fob spy cam version.
[http://chucklohr.com/808/]("http://chucklohr.com/808/")
This site has tons of detail on the camera, but unfortunately, they don't hardly mention Linux at all.

Looks like you should be able to get it to work as a webcam using the gspca drivers, but I'm still working on that myself...

---

### Post by wickedwiz on 2010-05-04
I recently purchased a mini cam MD80 clone (MINI DV&#8212;YSB001) and I need some help with it. I inserted the micro sd card. When I first turned it on it flashed the blue light a few times and then it became solid blue. I turned it off and back on and the light turned solid red. Now it won't turn off with the power button:confused:, I have to reset to turn it off. I plug it in to recharge the battery but the red light stays on for hours. I can't see it in my PC even with the driver installed, not even as mass storage. I read somewhere that the mini cam locks if the battery is low, is there a way to unlock it? 
Please help, I waited two weeks for the cam to arrive from china:frown: and now I can't get it to work, it's frustrating....

---

### Post by savitch on 2010-05-06
> **wickedwiz said:**
> I recently purchased a mini cam MD80 clone (MINI DV—YSB001) and I need some help with it. I inserted the micro sd card. When I first turned it on it flashed the blue light a few times and then it became solid blue. I turned it off and back on and the light turned solid red. Now it won't turn off with the power button:confused:, I have to reset to turn it off. I plug it in to recharge the battery but the red light stays on for hours. I can't see it in my PC even with the driver installed, not even as mass storage. I read somewhere that the mini cam locks if the battery is low, is there a way to unlock it? 
Please help, I waited two weeks for the cam to arrive from china:frown: and now I can't get it to work, it's frustrating....

I had the same problem because I tried to turn it on before fully charging the 1st time. You can let it reset by keeping it unplugged until it drains low enough. That can take over a week so I just opened it up and de-soldered/soldered the battery to reset it then it worked fine.

---

### Post by wickedwiz on 2010-05-10
> **savitch said:**
> I had the same problem because I tried to turn it on before fully charging the 1st time. You can let it reset by keeping it unplugged until it drains low enough. That can take over a week so I just opened it up and de-soldered/soldered the battery to reset it then it worked fine.
 
 
Thanx for responding. I haven't charge it for a few days now, I'll wait a couple more and i'll try again......again thanx.

---

### Post by efm on 2010-05-12
Hi everyone,
I purchased MiniDV-YSB004, and I really don't know how to use it. 
I'm using Ubuntu Lucid, and lsusb gives me information about 04fc:0171 Sunplus Technology, Co., Ltd.
It has 3 buttons, Photo-Video, On-Of, and Start-Stop. I've tried to trigger every button, but I haven't managed to use it as Webcam (nor make Linux detect it as 04fc:1528, just like jarthurs did.

I've tried in VirtualBox too, but no success.

Do I need to insert a memory card to use this thing as a webcam? (I don't have memory card at the moment)

thank you,
Faizal

---

### Post by Dilutu on 2010-05-17
With win xp you have to have a card in for it to work as a webcam. With Lucid, it sees it as connected device but I cant get it to work as a webcam

---

### Post by rochey on 2010-05-23
Hello all, i only made an account to hopefully help others who are having problems. I have the MD90 and the red and blue light were on constantly, i left it charging for 15 hours and nothing happened, light stayed on. 
 
I tried resoldering the battery like suggested to no avail.
 
However, whilst resoldering, i found that the camera lense is mounted on a block that plugs into the circuit board. My lense had come loose so i think the lights were just to show that there was an error. I slotted the lense back in and the camera works perfectly. Make sure you slot it in the correct way around as it is accepted both ways. Or you might, as in my case, have the blue light just staying on, with the camera still locked up. 
 
Hopefully my experience will help someone!
 
Thanks all!

---

### Post by asddsaasdds on 2010-05-27
Hey, if you have both blue and red leds glowing, try putting the TAG file on the memory card and then turn it on.


MD80 blue and red glow problem

---

### Post by Bryan55 on 2010-07-09
Anyone had any luck yet getting one of these to work as a webcam?

Bryan.

---

### Post by sawdust1 on 2010-07-20
After charging my MD80 it would not switch on.  The red LED would only light up while holding in the power button.  As soon as the power button is released, the red LED goes off again.  The bluie LED does not come on anymore.
 
I have refitted the lens and tried resetting the camera with no luck.  Any suggestions?

---

### Post by mistypotato on 2010-07-20
Site dedicated to this DV recorder....

[http://www.minidvforum.net/]("http://www.minidvforum.net/")

---

### Post by sawdust1 on 2010-07-21
I cannot seem to open that link?  Am I the only one?

---

### Post by xpacker on 2010-08-08
Was anyone able to get the camera working as a webcam?  I bought one, but I would prefer not to use Windows if possible.

---

### Post by bokaal on 2010-08-17
It looks like support for this device is added in V4L. See this commit: [http://git.linuxtv.org/v4l-dvb.git?a=commitdiff;h=c10ad929a728e24ca92bca1ec9967d311cd014ff](http://git.linuxtv.org/v4l-dvb.git?a=commitdiff;h=c10ad929a728e24ca92bca1ec9967d311cd014ff)

Also see: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/video4linux/gspca.txt;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/video4linux/gspca.txt;hb=HEAD)

---

### Post by pmuzyk on 2010-08-18
I have the same camera (MD80 clone) and I'm currently on Maverick trying to get it to work as a webcam.

I can see that it is being recognised when I poke at usb devices and it even recognises the disk mode and webcam mode. v4l2 doesn't seem to pick up the device as a usb webcam. No stream on /dev/video0.

---

### Post by vanja.krk on 2010-08-24
> **jt1588 said:**
> We are a manufacturer of security & protection products in China, we supply spy pen & watch camera, mini video camera, sport camera, waterproof watch video camera, spy remote control clock, 3D Glasses Mobile Theatre, bluetooth sunglasses camera and so on.
 
Please enter our website [www.jt1588.com]("http://www.jt1588.com"), maybe you willl find what you want.
 
Please feel free to contact me if you have any questions.
sadly, there is no solution for this camera on linux/ubuntu.

---

### Post by ru55377 on 2010-12-04
For those of you still struggling with drivers for the MD80, DVR-D011, or any SPCA1528 webcam there is a simple solution.

Download the latest gspca drivers from [http://moinejf.free.fr/](http://moinejf.free.fr/) the latest test drivers work just fine. As of today these are gspca-2.11.4.tar.gz

Extract the files to a location of your choice, ~/Downloads is fine.
From a terminal run the following commands;
Run the command ```
sudo apt-get install build-essential
```Change path to location of extracted files, i.e.```
cd ~Downloads/gspca_2.11.4
``` To update all the webcam drivers run ```
make
``` Or if only the SPCA1528 driver is required ```
make gspca_spca1528.ko
```Once complete install the driver(s) with the following command as root, ```
sudo make install
```All finished, plug in the webcam, select webcam mode and run an application such as "cheese" to view the webcam output.

---

### Post by Bryan55 on 2010-12-04
Thanks ru55377

This worked for me though there was a couple of typos.
------------------------------------------------------------------------------------------------
Change path to location of extracted files, i.e.     Code:
     cd ~Downloads/gspca_2.11.4 

Should have been  

cd ~/Downloads/gspca-2.11.4
------------------------------------------------------------------------------------------------
Your a gem. 
Bryan.

---

### Post by sa87 on 2010-12-08
prefect, thanks.

worked first try

---

### Post by ssam on 2010-12-25
here is a script to set the time. it finds the camera based on the usb ID, and writes the TAG.TXT file with the current date/time. when you unplug and switch on the camera reads the file and sets the time.

---

### Post by Dilutu on 2011-01-11
Thank you!
I installed on one laptop and a desktop and it works great.Realy good quality for a 17$ cam!!!

---

### Post by cpmman on 2011-01-22
Thanks to ru55377 for the howto and to ssam for the timeset script.  Both work fine and allow the keyfobcam  to be fully used in ubuntu.

---

### Post by ssam on 2011-02-01
works in webcam mode with no extra software in natty (11.04) :-), just plug in, press the play button on the camera, and launch cheese.

---

### Post by Bryan55 on 2011-02-11
If you want to remove the time/date stamp look here.

[http://www.paraglidingforum.com/viewtopic.php?p=238517#238517](http://www.paraglidingforum.com/viewtopic.php?p=238517#238517)

Bryan

---

### Post by md80question on 2011-03-08
@wickedwiz @savitch @rochey

This is my first post and my username says it all, imagine how eager I am to solve this issue ASAP. I bought MD80 three weeks ago, just received the parcel in good packing and all the promised accessories. I bought from eBay, by the way.

Just like wickedwiz and savitch said, I have the same issue. I first turned it on without sd card and tried to check it. It did turn off though but when I plugged in for charging. Now it shows a blue light for a moment and then red with blue light and it remains like that. So I use the reset button, pressing it using a pin to turn if off again and again while am trying the solutions.

By the way, I then tried putting my cellphone micro SD card 2gb and it didn't help though. 

I still can't understand what to exactly do to solve this and am not having such tools to even open this thing. Can anyone please guide? Am really worried about this, guess because I waited more than three weeks, saved money for this item and you know it hurts...

Hope someone care to help, am very new here.

Thanks a lot guys and gals. Take care.

---

### Post by xni on 2011-03-15
Thanks a lot for the information about gspca_spca1528, now after plugging camera I have some lines in dmesg, but it seems that things aren't ok:

```
[ 2220.053789] gspca_spca1528: disagrees about version of symbol gspca_frame_add
[ 2220.053793] gspca_spca1528: Unknown symbol gspca_frame_add (err -22)
[ 2220.054126] gspca_spca1528: disagrees about version of symbol gspca_frame_add
[ 2220.054131] gspca_spca1528: Unknown symbol gspca_frame_add (err -22)
[ 2220.054415] gspca_spca1528: Unknown symbol gspca_dev_probe2 (err 0)
[ 2220.054939] gspca_spca1528: Unknown symbol gspca_dev_probe2 (err 0)
[ 2220.055400] gspca_spca1528: disagrees about version of symbol gspca_frame_add
[ 2220.055404] gspca_spca1528: Unknown symbol gspca_frame_add (err -22)
[ 2220.055829] gspca_spca1528: Unknown symbol gspca_dev_probe2 (err 0)
```

---

### Post by GeoffreyTransom on 2011-06-07
> **ssam said:**
> works in webcam mode with no extra software in natty (11.04) :-), just plug in, press the play button on the camera, and launch cheese.


Me too - took literally 30 seconds. 

I had forgotten how crappy the video is from one of those cameras - in the video I shot as a test, I look nothing like Brad Pitt. I mean, come *awn*...

---

### Post by xcountryfreak on 2011-08-23
I have bought two of these cameras in the last month off ebay.  They both came from Singapore and neither one works.  I would not recommend buying them from ebay right now.  There might be a bad batch of them and the sellers don't seem to test them before shipping.  If you buy it for $10-15 and the seller requires you send it back for a refund you are SOL.  The shipping will cost you another$10-15 so you end up losing $10-15.  
 
Both cameras exhibit the same behavior, once the camera is charged, I turn it on.  The red light flashes once then goes out.  Then blue lights stay on, about 5 of them.  If I hold down the power button for four seconds to turn it off, nothing.  If I press the mode button, nothing.  The only way to turn it off is pressing reset with a paper clip.  If I plug it into the usb port on my laptop, nothing.  The computer does not see it. It will charge off the usb port.  I also tried charging from a charger.  No difference. I put a brand new 8GB micro SD in it.  I tried taking them apart and unsoldering the battery.  No difference.  Don't buy this camera!

---

### Post by matt45 on 2011-08-27
Please help me, on the second code that ru55377 advised (cd...), I get the error saying "no such file or directory" or whatever, i'm very very new to Ubuntu and not very programming savvy at all. I'm pretty sure I'm just typing something wrong. I have the current version of ubuntu so technically it should be working anyway like a few others said?

---

### Post by flavour_jo on 2011-08-28
> **matt45 said:**
> Please help me, on the second code that ru55377 advised (cd...), I get the error saying "no such file or directory" or whatever, i'm very very new to Ubuntu and not very programming savvy at all. I'm pretty sure I'm just typing something wrong. I have the current version of ubuntu so technically it should be working anyway like a few others said?

With the current version 11.04 you don't have to use ru55377 advice any more.

1. Put a correctly formatted sd-card into the camera. 
2. Then Connect the camera to your PC.

If the sd-card isnt correctly formatted remove it from the camera. Reset your camera with a needle and format the sd-card with another cardreader and e.g Gparted as fat32. Then try again starting with #1. Without a sd-card webcam mode does not work!

Open a terminal and type

```
lsusb
```this shows whats connected on usb. There should be a line similar like this.

```
Bus 001 Device 018: ID 04fc:0171 Sunplus Technology Co., Ltd SPCA1527A/SPCA1528 SD card camera (Mass Storage mode)
```The 04fc:0171 Part is the important one. This means your webcam is in mass-storage mode.

now press the mode button once on your camera. Type lsusb again and see the line changing to.
```
Bus 001 Device 019: ID 04fc:1528 Sunplus Technology Co., Ltd SPCA1527A/SPCA1528 SD card camera (webcam mode)
```Now your cam is in webcam mode. Now you can open a webcam programm like cheese, and you should see a live image.

I also tried with skype, but failed. It seems its not supported by skype. 
So for using this webcam with skype, I did a small hack-of-life.

I just open cheese to get a livefeed from the camera on screen. Then I use skype to transmit an area of my screen. I put one over another.

If someone has another, better solution for using this webcam with skype, I would be happy to hear about.

---

### Post by flavour_jo on 2011-08-28
Got the camera to work with skype on Ubuntu 11.04 64bit.

Ensure that libv4l-0 is installed.

On 64 bit just start with:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
```Not tried, but on 32 bit it should look like this

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```and your video should work.

You can also put this call in a shell script in /usr/bin/skype-starter 
```

#!/bin/sh
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype


```make it executable

```
sudo chmod x+a /usr/bin/skype-starter

```And change the links to use skype-starter instead of skype in your ```
/usr/share/applications/skype.desktop
``` file.

```
[Desktop Entry]
Name=Skype
Comment=Skype Internet Telephony
Exec=skype-starter
Icon=skype.png
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;Application;

```It just works fine.

---

