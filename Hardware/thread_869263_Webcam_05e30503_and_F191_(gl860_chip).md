---
title: "Webcam 05e3:0503 and F191 (gl860 chip)"
date: 2008-07-24
forum: Hardware
---

### Post by nol_faich on 2008-07-24
Welcome and sorry for that thread change but the previous one is no more writable.

New version online (n7b).
Corrected for the black bar.
The install script now tries to guess your driver. Please report wether it is OK or not (in that case, I would like your lshal).

---

### Post by soro2005 on 2008-07-24
Ok, this seems to be our new thread (Coming from [here](http://ubuntuforums.org/showthread.php?t=581307&page=29)).

0.2n7b seems to start most of the time with the right side up at 800x600, but I've also had it upside down again. Attached is a syslog with first a start that was with the right side up, then one with the upside down. I certainly don't see a pattern there, but you know what to look for.

1280 and 1600 now seem to consistently start with the small gray images inside the big one. I've had one 1600x1400 with a full image in correct orientation, though.

Sorry it's such a drag. But thanks again for your work on this.

Oh, the install script was still asking me which flavor to install. My lshal is:
system.hardware.product = 'S37S' (string)

---

### Post by nol_faich on 2008-07-24
There is still no automatic choice. At the beginning of the install script, there a line like "Did you use the X ?". I have two reports about that, one is ok and the other one bad with barebone Asus (I still not have the lshal to search what filed can be interesting).
The orientation received from the webcam is not the origin of upside down or right up images. It is so as big size which are working or not.

POST-IT
If you have an image in big size, I need a PNG (not JPG) screenshot of :
mplayer tv:// -tv driver=v4l2:width=1280:height=1024:fps=10:outfmt=y8:device=/dev/video0
I also need an image of "camorama -x 800 -y 600" and "camorama -x 800 -y 640"

At the beginiing of the install script, there is a line "Did you use the X ?" If X is not the good version of your driver or if there is no X, please tell me which driver flavor works for you and send me your "lshal".

I still need a Windows log of light source change.

---

### Post by hulkie on 2008-07-25
Hey,

glad I found you guys again. I did a 
$lshal | grep "system.hardware.product"
as somebody suggested and for me that returned "Z37S". The suggested driver was "a" by the install script, but the "c" version is what works best for me. I also made a movie of a 1600x1200 sequence with the 7-version (not 7b). The initial movie was 30 seconds long but the appearance did not change. The same grey images were visible all the time ( a normal reset takes 9 seconds (with the 7b driver even only 5)). Changing the colour space to y8 was not possible as this crashed mplayer.

Then, I went back to vmware and tried capturing a log of a flip at 1280x960 and to my surprise, 1280x960 is not even an option in the webcam software; it is 1280x1024 as you said. This brings me to color spaces; I can choose with yawcam which colour space to use and in RGB24, the maximum resolution is 640x480! For YUY2 there are additional sizes of 800x600, 1280x1024 and 1600x1200. Perhaps this could explain why we are getting grey images and of too small a size? I also attached a png image (which I posterised to half the amount of gray scales to reduce its size). In it, I wave my hand from the right side of the image to the left side (as I am upside down for me it was also from right to left). Thus, the images at the top row, are earlier in time then the lower ones.

Finally, in vmware, as I said, I tried to log the flip at the higher resolutions (in yuy2) but I did not get an image (as I mentioned earlier). Thus, I tried with some other free webcam softwares and some of them shut the webcam down when I tried these resolutions stating that there were too many error received to proceed. None of the 6 softs I tried were able to show me in the higher resolutions. This is strange as I really think it worked in the beginning. Anyway, the 800x600 works perfectly now without the blinking white line, so only 2 more resolutions to go!

Hulkie.

---

### Post by nol_faich on 2008-07-25
Happy to see you, my PM was not useful :)

The command line I use to watch the raw data is :
> mplayer tv:// -tv driver=v4l2:width=1280:height=1024:fps=10:outfmt=y8:device=/dev/video0 -vo x11

There is NO space between the "y" and "8" of "outfmt". What is helpful is an image which contains blue, red and white surfaces.
If you have another video device, it may be video1 instead of video0.

Are the colors good in 800x600 ?
The B&W is probably due to the one byte shift between the lines, in that case the debayerization yields to almost full B&W images. Just for fun, I can try to correct this, that release could named 0.2bee.

The logs in big sizes are difficult because of the cumbersome amount of data to write. I didn't know that you have 1280x1024 because no logs show such image size, the sizes "relog" identify have often no meaning above 640x480.

---

### Post by nol_faich on 2008-07-25
0.2n7bee is online.
The 0.2l2 also, it is a previous version, if you find the orientation of the image is more stable than with the actual driver, please tell me.

---

### Post by nol_faich on 2008-07-26
@ Hulkie : could you use the monusb script while you watch the webcam with WMWARE ? Far less data are logged compared to SniffUSB so that we may have better quality logs. You just have to watch at 640x480, 800x600, 1280x1024 and 1600x1200. Once you have an image you stop the Windows' viewer and you change to the next resolution. Once done, you kill the monusb script, execute the command line explained by monusb and send me the file after compression.

---

### Post by hulkie on 2008-07-28
Hey,

I finally found the time to test some more. I uploaded the monusb logs you asked for. I did them all for yuy colour space as there I could go to the larger resolutions. They are performed with the last bee release. Interestingly, I once obtained a coloured slanted image as you see in the third snapshot, but the offset from line to line has increased, not decreased. 

Just as a side note, cheese never worked for me as it seems to default to the largest possible resolution; but by changing all the larger possible resolutions in the v4l.c source code it works as well! Therefore, as for me, everything seems to work perfectly up to this resolution (the colour and the orientation is perfect for me up to 800x600, no issues whatsoever), I think I will try to create a version where all debug output is switched off and the time outs are reduced to a minimum... The fps for the moment is around 6 fps for 800x600, and I would like to get that higher if it is possible. I seem to remember that it was around 25fps before, perhaps I just need to restart the computer.. What are the fps that other people obtain typically?

I will try to do the missing logs tomorrow.
Hulkie.

---

### Post by blazercist on 2008-07-28
Hey everybody I'm back I see we have a nice new thread.

I just tested out the 0.2n7bee version and heres what happened:  

1. camorama starts in less than 10 seconds !!! :)
2. camorama defaults to 800x600, the image is oddly colored and upside down.
3. I can change camorama to "small" image size and the image is correct orientation and color but only 80x60 pixels
4. I can change camorama to "large" (1600x1200) size but it is oddly colored and it is slanted.

If I switch back and forth a few times from small to medium it eventually gives a clear picture with correct colors and orientation so I think its something with the initialization of the camera.  Tell me which logs to send and I will send them.

I'm attaching a pic of 1600x1200

---

### Post by nol_faich on 2008-07-28
Nice to see you again Blazercist. The version "bee" was intended to have colored small images in the big size images but that does not work according to the Hulkie caps. Without the "bee" version, you should have had a good picture!
Can you suppress the lines 568 to 578 (included) in the gl860-bayer.c file (these lines begin with #if and ends with #endif), change the "960" to "1024" on line 448 in gl860-v4l.c and recompile the driver. If you achieve good pictures in big sizes, please takes snapshots. Thx

@Hulkie : Quite strangely, there is less differences between 640/800 and 1280/1600 than before with your logs. I will analyse further tomorrow.

---

### Post by nol_faich on 2008-07-29
@ Hulkie : there is a n7 just for you, can you test it (just try to see the four image sizes). This version may evolve with the addition of delay as in the normal version.

---

### Post by blazercist on 2008-07-29
> **nol_faich said:**
> 
Can you suppress the lines 568 to 578 (included) in the gl860-bayer.c file (these lines begin with #if and ends with #endif), change the "960" to "1024" on line 448 in gl860-v4l.c and recompile the driver. If you achieve good pictures in big sizes, please takes snapshots. Thx


Nol, Do you mean to do this for the bee version?

And also when you say "without the bee version"  you mean 0.2n7b? (0.2n7b seems to work best out of the 0.2n7 series)

---

### Post by nol_faich on 2008-07-30
@ Blazercist : Yes without the n7bee is with the n7b. One of the differences is that I tried to untilt the small images in big ones. As your images were good (not tilted), the n7bee force them to be tilted and this changes colors.
This is why you need to suppress the untilting part.
If you have a good image, please try to get a raw data snapshot (to set the driver in raw data mode, use mplayer, [http://ubuntuforums.org/showpost.php?p=5457817&postcount=5](http://ubuntuforums.org/showpost.php?p=5457817&postcount=5)), at least one part of the image has to be white, if there is also a blue part and a red part, it is better. I the raw data image seems black, you can try the shakedown script and stop it when you have set the brightness to the middle value.

---

### Post by hulkie on 2008-07-30
Hello,

I tried my private driver :) and I tried to make some movies. There is one in attachment for 1280x1024 done with mencoder and y8 colorspace. This movie is pretty identical for the other resolutions as well; 640x480 and 800x600 also show the same behavior, so there it is definitely worse for the lower resolutions. In camorama, it's the same, but here the colours change every few seconds.  However, for the larger resolutions, I do get enough pixels for the 1280x1024 and 1600x1200 image (not many smaller images) although this image is shifting, upside down and with wrong colors.. I added two screenshots from mplayer (For those who do not know how to do this (like me), you first need to add vf-add=screenshot to the file ~/.mplayer/conf, after which you can take a screenshot from the command-line mplayer by pressing 's') to show, what is happening at 1600x1200 as this movie would not compress enough to fit. Finally, I added a screenshot with camorama for 1600x1200, showing the strange colors but otherwise enough unique pixels in the image. In the syslog I get a bunch of these overflow messages:

[16481.708177] gl860: Frame buffer overflow (1921876/1920000)!
[16481.808008] gl860: Frame buffer overflow (1921838/1920000)!
[16481.907839] gl860: Frame buffer overflow (1921600/1920000)!
[16482.007653] gl860: Frame buffer overflow (1921600/1920000)!
[16482.107495] gl860: Frame buffer overflow (1921687/1920000)!
[16482.207335] gl860: Frame buffer overflow (1921877/1920000)!
[16482.307160] gl860: Frame buffer overflow (1921876/1920000)!
[16482.410918] gl860: Frame buffer overflow (1921876/1920000)!
[16482.510746] gl860: Frame buffer overflow (1921876/1920000)!
[16482.610571] gl860: Frame buffer overflow (1921877/1920000)!
[16482.710405] gl860: Frame buffer overflow (1921731/1920000)!

For 800x600 I also get a lot of overflow warnings. In any case, for the larger resolutions, I thinks we are getting closer, we now obtain the right amount of pixels (more or less) for the larger resolutions.

Just a question, the movies with y8. Are they supposed to be grey, i.e. are they before the bayer interpolation?

Hulkie.

P.S: Oh yes, I forgot to mention the previous time that those logs for the higher resolutions did not result in a valid image. As stated before, I am not capable of getting images through vmware larger than 800x600.. I just halted the logging after several seconds...

Another remark: the driver now suggests correctly to use the 'c' version.

---

### Post by nol_faich on 2008-07-30
Do the images are always like the screenshots or sometimes is  it scrambled or with small pictures. If you have "good" images in big size and you revert the driver to the n7b, does the issue for big size appears again ?
The problem of shifts is that we have no more end-of-image marker and so no more sync. It should be RGB, as in the bright zones, it is white, not darker with regularly spaced white dots.
The y8 mode allows you to have raw data from the webcam, these data are a single value between 0 and 255 for each pixel, that is why the image is in B&W.
I will look at what is wrong in small size and is different in big size from the previous work.

EDIT : I had seen the movies, the no more sync for all sizes ? What happend when you are in rgb24 instead of y8? What about their color in rgb24? I upload a a corrected version for color (no more tilt).

---

### Post by nol_faich on 2008-07-30
@ Blazercist : could you try the version "only_for_hulkie_ok". It is done from what should be a "b" driver but as the "c" worked also for him, maybe that "b" ca work also for you.

---

### Post by blazercist on 2008-07-30
snope nol doesnt work for me weird colors and orientation and horizontal sync is off
/

---

### Post by vancedus on 2008-07-30
I'm sorry to interupt but I am really new to Linux and I can't figure out how to install the driver once I've downloaded it.  Please help.  Thank you!

---

### Post by nol_faich on 2008-07-31
@ Vancedus : Welcome! Just type ./install and choose your driver version depending on your laptop model (a list willl be displayed).
If your laptop is not in the list you will have to try each version. Once you tried a non suitable version :
* run again ./install until deinstallation of the previous driver
* when the script propose you to restart your computer, answer "yes"
* Restart after some seconds
* run ./install and choose another driver.
If there you find the good driver flavour for your hardware, please tell me which version do you need and post the result of the commandline "lshal".

@ Blazercist : do you still have small images or scrambled images ? If you only have weird images but in good size

---

### Post by blazercist on 2008-07-31
Nol, the image in 800x600 is correct size just weird color and orientation but im at work now and I don't remember if the large size was the same...  I'll check when I get home.

---

### Post by vancedus on 2008-07-31
I'm sorry, but where do I type the ./install?  Thanks for the help.

---

### Post by soro2005 on 2008-07-31
> **vancedus said:**
> I'm sorry, but where do I type the ./install?  Thanks for the help.

You download the driver, extract it, open a terminal inside the directory to which you have extracted the driver, and execute the script install.sh that you can find among the file you have extracted by typing
```
./install.sh
``` into the terminal.

It is not a command or anything, it is the instruction to execute the script install.sh, meaning that you have to navigate to the correct directory first (using cd, for instance).

You may want to read up on some of the basics before you venture into this kind of things which will probably not break your system, but may leave you in serious disarray. :-)

---

### Post by nol_faich on 2008-07-31
@ Hulkie : is that kind of image you describe as blueish? How long did you wait before making the snapshot? Due to the big image size, secons seconds may be unsufficient for the webcam to do its whitebalance.

---

### Post by hulkie on 2008-08-01
Hey, I tried the for_hulkie_ok and now the tilting is gone for the larger resolutions and camorama, so that is ok now. However, the sync is gone for all resolutions as you saw in the movie. But, the images do have the correct resolution and are not tilted anymore. The colors they flicker all the time but I have the impression (or I would like to believe.. ;) ) that the color only changes when the images start moving. This would make sense I believe as the 'red' intensities are interpreted as 'green' intensities after a pixel shift, giving completely different colours... Therefore, I would say that we only need to fix the sync issue to obtain correct images! 

Concerning the blueish images, that was a while back when I sometimes obtained a stable image and in that case, my ear remained blue for let's say 10-20 seconds..

In rgb24-mode I obtain a movie as shown in attachment with mencoder. I have a red t-shirt on and a white sheet of paper in my hand. For larger frequencies the image 'translation' and frequency is slower..

Anyway, hope this helps and I'll get back in a week.
Hulkie.

---

### Post by nol_faich on 2008-08-01
You're right about the color issue, it is due to the shifts. I will adapt these logs to make a "c" and "a" version, I will also add delays where the wWindows driver makes it.
Have a good holiday (I suppose), bonnes vacances.

---

### Post by nol_faich on 2008-08-01
There is a version 0.2n7c online. It has a byte sent to the webcam which is different. Is there a difference between n7b and n7c?

---

### Post by blazercist on 2008-08-02
Hey nol, 0.2n7c works really good, great color and 30fps steady in 800x600, the image is upside down in 1600x1200 and weird colors but its not slanted and the vertical/horizontal sync is good.

---

### Post by nol_faich on 2008-08-02
@ Blazercist : Could you post screenshot with the weird colors ?

@ all : there is a lack of data in the Windows logs used to make the driver. 
I tried to correct this with the lastest Hulkie's logs, please try the n7d online.

---

### Post by blazercist on 2008-08-03
> **nol_faich said:**
> @ Blazercist : Could you post screenshot with the weird colors ?

@ all : there is a lack of data in the Windows logs used to make the driver. 
I tried to correct this with the lastest Hulkie's logs, please try the n7d online.

Well Nol, I made a little mistake only 800x600 is nice and pretty and all the rest look like the pictures I'm uploading, 640x480 is **_sometimes_** with the right colors and orientation but still with the garble at bottom.

1600x1200                640x480

---

### Post by nol_faich on 2008-08-03
Online there is a n7e which is a theoretical adaptation from "b" version to "a" and "c".
I hope it is better than the n7c.

Soro2005 : can you run WMWARE and make logs with the "monusb" script ? Hulkie logs only applied to him and fret_saw. There is maybe missing stuff in the logs for "a" version.

---

### Post by blazercist on 2008-08-03
for me with 0.2n7e its worse 1600x1200 800x600 640x480 images attached in order

---

### Post by nol_faich on 2008-08-03
On line there is a n7e2, I adjust some delays according to Hulkie logs. I'm waiting for new logs from Soro2005 and maybe other people. If the small images reappear, it means that I removed mandatory data from a/c version compared to b. But I don't know what is missing since I have no usbmon logs for a/c.

@ Blazercist : have you tried the "b" flavour ? It seems that for C90 the driver may be "b" or "c". Hulkie is "b", maybe you are also "b".

---

### Post by soro2005 on 2008-08-04
Hey nol,

Sorry for the delay. I'm not at home, which, on the positive side, means that I was able to get my hand on an XP disc.

I've tried to use the webcam with vmware, but get "bandwidth exceeded" and no image whatsoever. Will try to see whether I can get it going, but so far no luck.

I'll look into producing some logs. In the meantime a screenshot of 0.2n7e2 which I have made with cheese. It's very unstable, and the color chanels seems to be not overlaid correctly.

Also, perhaps you're interested in knowing that the last version that works quite well and stable here, although only in 800x600 and lower, is 0.2m-expe.

Back later with more detail.

---

### Post by nol_faich on 2008-08-05
I got logs for the "a" version made with virtualbox. There is some difference with the "c" I didn't spot before, I will correct that in 10h. If you want to make logs, it will allow to confirm that changes ut I don't think they are usefull eventually.

---

### Post by nol_faich on 2008-08-05
n7o is online. It is made from logs for a/b. Version "c" is derived from them. In the dmesg there is a new probed data, it may allow to know whether the "a" or "c" version is needed. Maybe this will allow with the first probe the automatical version identification.
Please let me know which value has "probe 2" in dmesg and whether the different size work.

---

### Post by blazercist on 2008-08-05
Hey Nol! I tried, n70.  Versions a,b, and c all work in 640x480 and 800x600 ! All the options in camorama work, color, white balance, contrast, etc. EXCEPT for Hue.  Version "a" gives me upside-down blueish tinted images SOMETIMES.  "b" and "c" are the most reliable for me.  The only problem that I can see in 640x480 and 800x600 is that the framerate is very low 5-7fps.  

Heres something cool, version "c" gives me an image in BOTH 1600x1200 and 1680x1050 (my laptop's native resolution)  the only problem is that the image is upside-down and blueish tinted.

Version "b" also gives me an upside blueish tinted image in 1600x1200 but only a garbled image in 1680x1050.


Occassionally, in both versions "b" and "c" if I exit camorama and restart camorama quickly I get either the upside-down blueish image or just and upside-down image with the correct colors.

```
dmesg | grep probe
```

gl860: probe 2=d8

---

### Post by soro2005 on 2008-08-06
This time, I agree on almost all counts with blazercist. a, b and c give some result this time, b and c are clearly more stable than a. This means mainly that the higher resolutions (1280x960 and 1600x400) initialize with an intact image, albeit upside down and with a slight blue tint. 

```
gl860: probe 1= 0
gl860: probe 2=d8
```

I would really like to give you my logs if that's any good for you, but as I say, so far I get only some bandwidth exceeded error from Windows on the USB port the camera uses. That's with both Vmware and Virtualbox. If anyone knows how to solve this... I'm not sure I'm using the correct driver, but I'm away from home and have been trying to get one off the Asus website. I will see whether the one that came with the computer works any better. But that's going to take some time.

---

### Post by nol_faich on 2008-08-06
If I understand well the images are upside down for each size. EDIT : I did not understand.
Can I have a screenshot of the blueish image. Does the blueishness of the image evolves within the first 20 seconds ?

@ Soro2005 : quite strangely, your probe1/2 pair is what I think to be that of "b"/"c". The French S37S owner who made the logs has a different probe2. If I remember you can't rotate your webcam so it has a front or back screen view, am I right ? In that case, you don't have the same webcam on a same laptop. I am waiting for reports from French S37S owners.

---

### Post by hulkie on 2008-08-06
Hey,

the o version is a big improvement over the version before (where I got scrambled images for all sizes). Now, up to 800x600 everything is stable again and for the larger sizes, everything is blue and upside down again (I got the small grey images only the first time). No more sync issues. I attached a blueish image (in the image, the walls should be orange-red, which they are in 800x600 as you can see, no evolution over time (+-2 minutes)). I also attached a screenshot from mplayer in y8 mode. There I am holding a blue book and a red duck. Hope it helps. Perhaps a horizontal shift off all the pixels would solve it (as perhaps the red and blue pixels are swapped, the green trees remain green in the image..).

Concerning the syslog output: when I got the grey images, the message: Iso frame 15 of USB has error -71 appeared (but only 1 time strangely enough, nevertheless maybe a cue to reinitialise the webcam?) Next to this, the probe output was:
gl860: probe 1= 0
gl860: probe 2=d8
gl860: probe 2=d8

Hulkie.

---

### Post by nol_faich on 2008-08-06
@ all : If in big size the images are mirrored and flipped, does the color is OK ? Use the shakedown script to make that, it is the easiest way. I think that this will not make any change but we never know.
I will add an hrz/vrt shift and invert the image if necessary.

Does the framerate is low for every body in small sizes ?

Does the startup time is OK ?

---

### Post by soro2005 on 2008-08-06
> @ all : If in big size the images are mirrored and flipped, does the color is OK ? Use the shakedown script to make that, it is the easiest way. I think that this will not make any change but we never know.
I will add an hrz/vrt shift and invert the image if necessary.

No, the color is very blue. Also, if I start the camera in 1600x1200 (upside down) and use the shakedown script, the script does not flip the image in any direction.

My framerates seem to be okay in all sizes. In fact, the camera seems very reactive, also with regard to adjusting to light changes. (How do I get the numeric value for the framerate?) The startup time is also very good across the board (4 or 5 seconds perhaps).

It seems that I have a different camera, then, than the French one with an S37S. I cannot turn mine backward. The "b/c" modes of the 0.2n7o definitely work way better than the "a" mode.

I also have to agree with hulkie and would even go as far as to say that this is the best version ever. Other than large resolutions being upside down and blueish, and an occasional false start with small gray frames inside the big one (very seldom now it seems), it looks like you're getting there. Thanks again for your work!

---

### Post by Jack Malmostoso on 2008-08-06
> **soro2005 said:**
> (How do I get the numeric value for the framerate?) 

Camorama shows this value at the bottom of its window.

---

### Post by soro2005 on 2008-08-06
> **Jack Malmostoso said:**
> Camorama shows this value at the bottom of its window.

Stupid me! Too bad the lower bottom is outside of the viewable area here unless I start it in really low resolutions. :) Well, I guess I can hide the adjustments.

---

### Post by Jack Malmostoso on 2008-08-06
You can easily move the window waaaay out of the boundaries of the screen by pressing Alt+F7 (in Gnome) and look at the fps value even for high resolutions :)

---

### Post by soro2005 on 2008-08-06
> **Jack Malmostoso said:**
> You can easily move the window waaaay out of the boundaries of the screen by pressing Alt+F7 (in Gnome) and look at the fps value even for high resolutions :)

There's some edge resistance at the upper limit which I've never been able to overcome. I should look into my compiz settings.

---

### Post by nol_faich on 2008-08-06
Hi Jack!
Thanks for your trick. It works by typing Alt+F7 and not using the top left menu in the titlebar.


A new release is available. I made an error in the mirroring and flipping setting for all sizes. I correct it and make a change in the color for big sizes. I do not revert the image actually in big size.
With that version i just want to know if the color is good and if the mirror/flip settings work.
I am working on automatical driver guessing and reversion of the image in big size.

---

### Post by blazercist on 2008-08-06
Weird, I just tried 0.2n7o2, now all my images are upside down in all resolutions, 1680x1050 has become garbled again. 1600x1200 is still upside and blue.

Also, now when I start camorama the image is dark, if I bring my hand close to the camera it gets lighter, the closer I bring my hand the lighter it gets. If I take my hand away it gets dark again.  If I change the contrast so its not too dark when I'm sitting normally it still does this "lighter/darker" thing but not as much.

FPS is now 30fps which is very good.

I got these same results with "a", "b" and "c"

---

### Post by nol_faich on 2008-08-06
Is the new onlined n7o3 better for color and orientation ?

EDIT : Oops, now online...

---

### Post by nol_faich on 2008-08-06
I add an experimental version with autodetection, flip/mirror in big sizes and color correction.
I test the autodetection with my webcam, it is OK. However I had to modify lot of stuff and I hoipe it is also OK for you.
Good luck

NB : the file 0503a is replaced by 0503his (for Hulkie, Iceman, Soro, the main loggers and helpers for the progress of the a/c version).

---

### Post by soro2005 on 2008-08-07
p_experimental2 works here only for the smaller sizes. 1280x960 and 1600x1200 are garbled, upside down, and small gray frames inside the big one.

0.2n7o3 works only up to a resolution of 640x480. Higher resolutions are garbled in all the habitual ways. The best one for me here seems to be 0.2n7o, type b so far.

---

### Post by nol_faich on 2008-08-07
And if try again the n7o, is it better than n7o3 and experimental ?
Also, can you tell me which version is used in your dmesg when you use the experimental driver ("dmesg | grep Version").

EDIT : new experimental online. Autodetection corrected for "sim" version, temporary no more corrections for big sizes.
Just try to see if you get an image in all sizes.

---

### Post by soro2005 on 2008-08-07
I get the Iceman version, it seems.

gl860: probe 1= 0
gl860: probe 2=d8

And yes, 0.2n7o is better than the last two, but only flavour b and/or c (it's a little inconsistent). The a one which I traditionally used was not so brilliant.

---

### Post by nol_faich on 2008-08-07
@ Soro2005 :
Iceman is "a". I just noticed that unfortunately everybody seems to have a probe2 to d8. The automatical driver guess does not work. In fact I ask for the orientation of the webcam because a/c have not the same value, however at startup, value are identical. What a shame!
You have to do 'sudo rmmod gl860' and then 'sudo modprobe pilote="hs"' to force the driver when you install the experimental flavour. It is a sad news.
The only difference between the n7o and n7o3 are the color inversion and a different mirror/flip.

Can you try the n7o_soro to be installed with "./install hs" (the argument hs forces the flavour). Is it closer to n7o and are the color OK in big sizes. I removed the orientation change stuff.

Have you a Msn adress to send me in private mail ?

---

### Post by soro2005 on 2008-08-07
Nol, I've sent you a pm.

The n7o_soro version isn't as good as n7o, which is unsurpassed. Only that, most of the time, the big resolutions start upside down and a little blue.

---

### Post by hulkie on 2008-08-08
Hello,

I tried the o3 version and the lower resolutions are just fine. But the larger resolutions gave me the grey images again, not the upside down blueish one...

Hulkie

---

### Post by nol_faich on 2008-08-08
@ Hulkie : Can you try the n7o_soro by installing it with "./install hs" (it is mandatory) ?
Also, have you a Msn address for IM ?

@ Soro/Hulkie : I will have plenty of time in 6h.

---

### Post by nol_faich on 2008-08-09
New release on SF (q1).
To test in big sizes (but no shakedown!).
There is a LED issue, but that point apart, it should be OK. I will work on it tomorrow.

EDIT : q2 online, theoretically LED issue corrected + add the hue support with colour/BW/negative/R and B layer inverted.
The traces are reduced : no more overflow logged, no more -71/-75 error and no more "Demande de la taille : etc" also.

@ Hulkie : Could you make "monusb/WMware" logs for each setting where you change the value several times 10s after the viewer is started. I need such logs while you are in 640x480 and 1280x1024. It is to control if delays are the sames for both sizes between usb transfers.

---

### Post by soro2005 on 2008-08-09
The LED is on again. :)

On a different note, and sitting out here with very little light, I have come to the appreciation that the amount of light available seems to play into whether the image starts upside down/blueish or straight up. With very little light, I seem to be getting the upside down thing even at the lower resolutions. That's with the driver version that worked very reliably earlier today, with daylight. Also with q2.

I also get a very low frame rate with little light.

---

### Post by nol_faich on 2008-08-10
It was not so hard the LED issue, I executed some instructions for "a" version and right after the ones for the b/c. This mistake happened when I changed the driver structure to take into account the driver (non-working) autodetection.
The light is also important for the framerate with my webcam, it ranges from 4,5fps in low light to 25fps in day light.

But I have no explaination for the orientation issue. One possible thing is that the orientation probe does not return for you that value (because you can't rotate the webcam enough) but the light level.
Please verify that the issue depends on light level and if it is confirmed, make a monusb log (no virtualbox needed) in daylight and another one in low light.
Also does the orientation change in low light (ie the image is upside down at the start and OK after) ?

---

### Post by nol_faich on 2008-08-10
q3 online, the correction for big is now applied to b/c flavours.

---

### Post by soro2005 on 2008-08-10
Works nice here, but that's hardly a surprise, I guess.

I will check out the light issue when it gets dark. At the moment, everything starts right side up. Last night, it was sometimes upside down, and sometimes correct, so I didn't get the impression that there was some "night switch" in play there. But I will post the logs tonight.

Finally: The "c" flavor of q3 works just as smoothly as the "a" flavor here, or perhaps even better. Perhaps, that's good news and you can save some of the probing and selecting there?

---

### Post by hulkie on 2008-08-10
Hey Nol! You did it!

the 1280x1024 and 1600x1200 version are working correctly. Right side up and with good colours! 

However, sometimes I still get the little grey images (2 out of 5 on 1280 and 1 out of 4 for 1600), but I did not get the upside down blueish image again, so I suppose that when things are initialised correctly, the image is perfect. So as you suggested, I also believe that extra logs are needed to define the appropriate timeouts between the different control sequences. Once you nail that, I think we're there. I will try and do some tomorrow on the train.

Hulkie.

P.S. I don't have msn, but a gmail account, would that do?

---

### Post by soro2005 on 2008-08-10
So here comes my twilight testing. I am actually quite positive that there is something there. I can currently reproduce it any number of times, it seems. It is with driver version q3 and both flavors a and c.

With low natural light, I get blueish upside down and from your monusb script the output "night".

If I take a lamp and shine it into my face, the camera starts right side up, and monusb yields what below you can find as "day".

---

### Post by nol_faich on 2008-08-11
@ Soro2005 : At first look the your orientation probe is "50" in night/day files, that is bad because of not any difference between night/day probe and so maybe the received data are corrupted. However, this "50" is quite crazy as your usual probe is "d8" (50 is the one of the "c" flavour). Have you made the logs with the same driver flavour or which one did you use? I would like you to use the "a" flavour, because it is your natural one.

@ Hulkie : I'm waiting! i will study for gmail.

---

### Post by nol_faich on 2008-08-11
q4 online :
* fix for driver flavour at restart of the computer which was not good if you are "c" or "ms"
* fix for a trouble with big size and flavour "sim"

---

### Post by soro2005 on 2008-08-11
Sorry, that was with flavor "c" last night. Here it comes with "a", but tonight, and regardless of the flavor, I get the upside down only at 1600x1200. Not much difference in the logs there, either. But I still believe it flips over more often when it is dark.

---

### Post by nol_faich on 2008-08-12
Yes, no big differences, the orientation probe is the same for both files. 
Interestingly, the probe is "d8" with "a" instead of "50" with "c". That means the orientation probe value is defined by the driver, not by the hardware and that explained why all devices have a "d8" at the startup instead of the d8/50 received when the webcam is working.
Can you grab a raw data image with mplayer in night and day?

---

### Post by soro2005 on 2008-08-12
> **nol_faich said:**
> Can you grab a raw data image with mplayer in night and day?

I could, but for whatever reason the mplayer stream is virtually black already in daylight. So you won't see anything. It starts up more or less okay, but then gets extremely dark in no time. :confused:

With q4, by the way, the only thing I get on starting camorama is "Unable to capture image".

---

### Post by nol_faich on 2008-08-12
q5 online, issue with a/c flavour theoretically resolved.

For the brightness and mplayer :
cd /sys/class/video4linux/video0   (or 1 if video is taken by another device)
echo 60000 > brightness

---

### Post by blazercist on 2008-08-12
Nol q5 works in EVERY RESOLUTION 640x480, 800x600, 1680x1050, 1600x1200

the color and orientation are perfect and the camera starts quickly.

the large resolutions (over 800x600) are a little slow (~10fps) but that is expected.

NOL YOU SIR ARE A GENIUS AND I THANK YOU VERY VERY VERY VERY VERY VERY VERYV ERY VERYV VERYVEVERYERVERYVERY MUCH!

---

### Post by nol_faich on 2008-08-12
Thanks :) and you can also thank Hulkie, Soro2005 and Iceman (from other forum) for their last logs who help a lot, but it seems that it is not finish yet.
1) In low light the image may be inverted and blueish.
2) there is a risk of freeze from viewer to system, it seems to be dependant on hardware as only some people report that.
EDIT : not "some people" but only one tester reports me that and its system is not stable and has still frozen without the webcam. However I already locks two times out of many tries and i have still no explaination.

---

### Post by Jan Olieboer on 2008-08-13
Hi Nol,

I've been testing the q5 release, using the c-version for my C90S, and it is brilliant!! Works in all (available) resolutions, is stable and responsive! No more buffer overflows or whatever message in syslog/messages. Fantastic piece of work! Does start sometimes upside down, but that is quickly resolved with an echo 0 to h/vflip to get the orientation right. Tested it on Skype, Ekiga, Camorama and aMSN and it works great! Many many thanks!

Cheers,
Jan Olieboer.

---

### Post by nol_faich on 2008-08-14
@ Olieboer : Hi !
I no more log overflow and error -71/-75 which are the most common things because it is no more useful.
What you say about the upside down images is quite interesting. When you had upside down images, did it look like blueish [http://ubuntuforums.org/showpost.php?p=5563379&postcount=63](http://ubuntuforums.org/showpost.php?p=5563379&postcount=63) ? (if you don't know, wear something red (or blue) and you will see it becomes blue (or red) if there is the color trouble)

@ Soro2005 : can you confirm that the echo 0 to hflip and vflip solve the trouble ?

---

### Post by soro2005 on 2008-08-14
> **nol_faich said:**
> 
@ Soro2005 : can you confirm that the echo 0 to hflip and vflip solve the trouble ?

Nol, not really. It's just started upside down, and I could, indeed turn it over. Interestingly, by echoing "1" to vflip. Normally, vflip does the horizontal mirroring here (is that correct, by the way?). So I get the impression that it's turned right side up because there is some re-initiation on change of parameter, and not because the change of parameter itself corrects the error.

I did also briefly try it out last night with the low light which normally seems to trigger the wrong orientation here. Echoing 1 to the two files did not have any effect when the image had started blueish and upside down. I will do some more testing tonight.

May it be that all of this goes away if you just give the driver a tad more timeout while waiting for the camera?

---

### Post by etfloyd on 2008-08-16
I get the upside-down image from time to time as well testing with Camorama.  Either stopping and restarting Camorama, or echo 1 > hflip will usually set it right.  (Yes, hflip. hflip and vflip are reversed in effect. Poking a 1 or 0 in hflip reverses the image vertically, and vflip reverses horizontally.) 

I have also noticed a peculiar sort of "threshold" effect with some of the Camorama controls, particularly Contrast and Hue.  Slide the control and watch the numbers on the left as you cross from 63 to 64, from 127 to 128, and from 191 to 192. On mine, I see a sudden change on each of those crossings. It's particularly startling on the Hue slider where the image actually reverses to negative between 64 and 127 and then hops back to positive image.  This may point to some kind of "endian" problem?

Edit: Also, MPlayer finds the device but Skype doesn't.

Anyway, please keep up the good work.  It's almost there.
--
E. Floyd, C90S, 05e3:0503, q5-c, Hardy 64-bit.

---

### Post by nol_faich on 2008-08-16
Hi Etfloyd!
Hflip and vflip are inverted and this is corrected in the last version. 
The threesold effects are normal, most of the settings does not have 256 possible values. The contrast settings with your webcam has only 4 values. I thought about changing the way sliders are managed, but don't do it yet.
What you say about color trouble correction is quite interesting. It could confirm that the flips are the origin of the trouble.
I just remembered that on contrary to other 0503 or f191, I am not able to identify the default settings initialisation. Only some settings but not all and one has not exactly the same sequence it must have. Maybe the bad step is when I make settings.
Can you run the webcam with WMware or run Windows. It may help.

EDIT : q6 online. I add delay between the initialisation sequence and the settings step, I hope it fix the start in low/day light condition. Please test for all sizes and in low/day light.
The install script has changed. (Choose compile the driver and semi automatic installation)

---

### Post by soro2005 on 2008-08-16
Nol: Sorry for earlier today, I wasn't sitting at the computer. q6 works great for me, and in one exact way, I would say it is a very decisive improvement over what we had earlier: The 1600x1200 yields a much better contrast/brightness than what was before, and also than the current 800x600. I've attached two shots with the exact same light conditions. I haven't put my fingers on the contrast sliders etc. I think this is what the driver comes up with spontaneously. Those shots are taken in not precisely bright light. I can't test with daylight at the moment.

If I switch of a few lamps, I still get the upside-down quite often (large resolutions). But I think it's also better, b/c I don't think I've seen the gray small frames with q6.

---

### Post by nol_faich on 2008-08-17
I add 1/3 second before applying the settings, I suppose this helps the webcam to be ready to be set.
What will be interesting is Windows logs with some default settings modified and size changes made in low/day light. This could help to know how the settings are done during the initialization since the instructions to set parameters seem not to be the same while the webcam is running or being initialized.

Before having these logs, one thing can be done :
in the function "dev_0503his_camera_settings" from 503his, add "return 0;" before "dev->doNotDisturb=1;" (in the beginning of the function).
The driver will only do the initialization sequence (no more settings applied), it must be interesting to see what happend in low and day light about the right up/upside down images.

---

### Post by soro2005 on 2008-08-17
> **nol_faich said:**
> Before having these logs, one thing can be done :
in the function "dev_0503his_camera_settings" from 503his, add "return 0;" before "dev->doNotDisturb=1;" (in the beginning of the function).
The driver will only do the initialization sequence (no :more settings applied), it must be interesting to see what happend in low and day light about the right up/upside down images.

If I do this, I get relatively good colors througout, although perhaps a little dark. Hard to tell as it's not particularly bright at the moment. I have the impression that the camera tries to adjust all the time to the light conditions, to the result that it pumps a little, or flickers. It's a low amplitude flicker, but a flicker.

More importantly: Of all things, the LOW resolutions are upside down! The high resolutions (1600x1200 and 1280x1024) are with the right side up.

---

### Post by nol_faich on 2008-08-20
@ Soro2005: do you know if you are able to run Windows to make logs ?

---

### Post by nol_faich on 2008-08-24
I got some logs, I study them. To be continued.

---

### Post by nol_faich on 2008-08-27
Work in progress.

@ Hulkie : if you can make Windows logs, it will be useful as the logs made by Iceman are made with the "a"-like Windows driver which is software-limited for permitted settings. With your "b"-like Windows driver, we have not this limitation.

---

### Post by nol_faich on 2008-08-30
Version r1 online, for test with "a" flavour and maybe also the "c".
To install "a" or "c" use "./install a or c" in order to avoid some installation questions.
To test in day and night condition. It does not need a restart of the computer.

---

### Post by nol_faich on 2008-08-31
Version r2 online. It is stable in dark and normal light.
As there will be no more big improvements in the driver, a mailing has been created on the sourgeforge project page so you can have informations about changes.

---

### Post by soro2005 on 2008-09-01
Time to say Thanks!

---

### Post by nol_faich on 2008-09-02
@ Hulkie : your logs are still welcome to understand how some settings must be ordered or delayed.

---

### Post by HoellP on 2008-10-27
Hey Nol, I'm just bringing the discussion over here as you suggested.
As said before, camorama works just fine, 30 fps, great picture, and the settings change according to my input, there are no errors on the terminal.

Next is cheese. When started from the terminal it gets spammed with the message "FIXME add rgb24 -> yuv420 conversion" as long as cheese is running, which suggests the same as you already said. But I have no clue where I can change anything like that. I tried gstreamer-properties, but there is nowhere I can change the colorspace. So cheese is just a green picture, but nothing else. The pictureoutput is green as well.

Gstreamer-properties: With v4l2 I get the same green picture as in cheese with the same error message spammed to the terminal. When I switch to v4l I get a window with the error "Video for Linux (v4l): Could not negotiate format" and in the error "gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not negotiate format [gstbasesrc.c(2426): gst_base_src_start (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc2:
Check your filtered caps, if any]" in the terminal.

Xawtv has vertical stripes in the previewpicture and poor quality. When I take an image, the quality is good, the same as with camorama, but the picture is upside-down.

This is as much as I know by now. I'm using Intrepid 64bit with latest updates. I can't try an older kernel because I need the system and installing an unsupported kernel on this machine is not an option, I'm sorry.

<-

---

### Post by BUGabundo on 2008-10-27
As requested on LP bug #215604

My images are all fine, no upside down.

This room as enough light, but how can I check the frame rate?

On gstreamer-properties how can I create another colorspace. besides te v4l2src device="/dev/video0" ?

---

### Post by BUGabundo on 2008-10-27
from xawtv i get this:
$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-7-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

---

### Post by HoellP on 2008-10-27
I get the exact same message from xawtv...
<-

---

### Post by nol_faich on 2008-10-27
Related to blueish images :
- do the images were also upside down or not ?
- do you get good (non blueish) image with the soft which already yields to blueish images ?

---

### Post by HoellP on 2008-10-29
Sorry, that the answer took so long, but I was totally beat from work the last days...

I never experienced a blueish image, the only color was the bright green one in Cheese and Skype.
In every tool I tried, there was not one option that changed anything at the image at all. It either worked right after installing, or not at all.
If you need more info, please be more specific.

Edit: I tried switching the videoplugin in ekiga, and experienced the complete opposite of you. It works well enough with V4L but crashes with V4L2. The funny thing is, in gstreamer-properties none of the 2 works, and camorama still works without setting anything.
<-

---

### Post by nol_faich on 2008-10-29
Hi!

Thanks for your answer. Is there any trace left in the terminal before any soft crashes?
Camorama only uses v4l if it has not evolved. Could you try with aMsn, MPlayer and VLC?

---

### Post by BUGabundo on 2008-10-29
if u guys need me to had new tests, let me know.

---

### Post by nol_faich on 2008-10-29
Hi BUGabundo! Could you answer all these questions and make the test please?

Related to blueish images :
- do the images were also upside down or not ?
- do you get good (non blueish) image with the soft which already yields to blueish images ?

Did you ever get upside down images with colors OK?

Could you try the driver with aMsn, MPlayer and VLC? (launch them in a terminal to have the traces in case of trash)

---

### Post by BUGabundo on 2008-10-30
> **nol_faich said:**
> Hi BUGabundo! Could you answer all these questions and make the test please?

I already did, on the LP ticket.

> **nol_faich said:**
> Related to blueish images :
- do the images were also upside down or not ?

The images never showed up side down in any soft.

> **nol_faich said:**
> - do you get good (non blueish) image with the soft which already yields to blueish images ?

camorama shows perfect images.
xawtv shows some vertical lines.
ekiga image is blueish.
skype, cheese, gstream-prop all show green screens

> **nol_faich said:**
> Did you ever get upside down images with colors OK?

I never got upside down images. Not sure if it is software or hardware, but my cam used (on kernel 2.6.26 with manually compiled kernel) to detect it vertical rotation.

> **nol_faich said:**
> Could you try the driver with aMsn, MPlayer and VLC? (launch them in a terminal to have the traces in case of trash)
How do I select it from VLC? both v4l and v4l2 fail to start.

---

### Post by nol_faich on 2008-10-30
If the blueish images are right up, that means the rgb24 is read as bgr24 by Ekiga, so another colorspace issue beside Cheese not understanding the rgb24.
I got some piece of code to convert from rgb24 to i420 for Cheese.
The command line to use the webcam with VLC is the (awful) README file.

I think I will try to finish as soon as possible the gspca version because i do not convert the image, I just give to a library the image bytes and the format (Bayer for our webcam). Resizing and change of colorspace is done by the library. This may help to solve for all troubles.
One think you can try with Ekiga is to change the hue to the max value, i set the inversion of Red and Blue channels in the pictures. Use Camorama, set the hue to the max, you should see the inverted colors, close camorama and start Ekiga. If Ekiga does not set parameters itself, thre webcam will restart with the changed hue.

@ all : do you tried to test the "2.6.20-27" release. It should compile with all kernel between 2.6.20 and 27. I would like you to test it to keep only one driver tarball instead the one for new and old kernel

---

### Post by BUGabundo on 2008-10-30
> **nol_faich said:**
> 
One think you can try with Ekiga is to change the hue to the max value, i set the inversion of Red and Blue channels in the pictures. Use Camorama, set the hue to the max, you should see the inverted colors, close camorama and start Ekiga. If Ekiga does not set parameters itself, thre webcam will restart with the changed hue.

Doing this it works, and I get perfect image on both programs (after hue ajust)

---

### Post by nol_faich on 2008-10-30
OK ! Now the only really missing thing is the test of the 2.6.20-27 release.

Camorama : rgb24 OK
Cheese : rgb24 not managed
Ekiga : rgb24 read as bgr24

It seems to me they is a possibility to get the name of soft requesting for images, i could use that to correct the colorspace. If this really exists, i will have just to find out how this works. Any help welcome!

---

### Post by soro2005 on 2008-10-31
Hey Nol,

Good you're still at it. :-D

I've upgraded to Intrepid 64 bit, and I can confirm that the 2.6.20-27 driver installs, and that Cheese yields a green image. Unfortunately, Skype also yields a green image. That's a real shame. :(

Let me know if there's anything to test.

---

### Post by nol_faich on 2008-11-01
@ Soro : Hi! Is there some traces for Skype to understand what happens ?

@ BUGabundo & Paul : Have you Windows or a working VMware/VirtualBox ? In that case I would you to reply me with the file "gl860.inf" in attachment. Maybe you could help me to finish to establish the good sequence for the initial setting of parameters.
BUGabundo you are only concerned if "dmesg | grep Version" tells you use the "Hulkie" version of the gl860 driver.

@ All : I looked at what is the yuv420 requested by Cheese and it is unclear, there is 4 video format under this name!
The change to a gspca version of the driver is less easy that what I thought. With the gspca driver, the video format for the output is managed by a third part, this is more flexible and must allow more formats to be used.

---

### Post by soro2005 on 2008-11-01
There are two things that happen with Skype. First, it seems that the driver causes Skype to throw a floating point exception with this dmesg trace:
```
[11117.876905] gl860: Genesys USB2.0 - GL860 based webcam found.
[11117.876907] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[11119.764170] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[11119.765436] usbcore: registered new interface driver usb_gl860_driver
[11119.765670] gl860: v0.3.0 : Genesys gl860 USB Video Camera
[11133.900685] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14423): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f9cb94) on /dev/video0
[11133.900722] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14423): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f9cb94) on /dev/video0
[11133.900729] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14423): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f9cb94) on /dev/video0
[11133.900736] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14423): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f9cb94) on /dev/video0
[11133.900743] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14423): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f9cb94) on /dev/video0
[11133.900749] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14423): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f9cb94) on /dev/video0
[11133.900781] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14423): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f9cb94) on /dev/video0
[11133.900807] skype.real[14423] trap divide error ip:f6e876ae sp:f5f9ce00 error:0 in libv4l1.so.0[f6e85000+4000]
[11159.423077] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14437): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f2fb94) on /dev/video0
[11159.423126] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14437): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f2fb94) on /dev/video0
[11159.423136] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14437): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f2fb94) on /dev/video0
[11159.423144] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14437): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f2fb94) on /dev/video0
[11159.423153] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14437): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f2fb94) on /dev/video0
[11159.423161] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14437): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f2fb94) on /dev/video0
[11159.423169] compat_ioctl32: VIDIOC_ENUM_FRAMESIZESioctl32(skype.real:14437): Unknown cmd fd(11) cmd(c02c564a){t:'V';sz:44} arg(f5f2fb94) on /dev/video0
[11159.423198] skype.real[14437] trap divide error ip:f6e1a6ae sp:f5f2fe00 error:0 in libv4l1.so.0[f6e18000+4000]
```

This happens often, but not always. I haven't been able to identify a pattern. If Skype starts, the only video I get is a green screen, and the trace in the terminal is the same as with Cheese:
```
FIXME add rgb24 -> yuv420 conversion
```

---

### Post by soro2005 on 2008-11-01
Now this is shocking: I've installed the Hardy Skype packages from the Medibuntu repository in my 64 bit Ibex (downgraded, or forward ported if you will), and the webcam seems to work. With colors and everything.

Here some trace:
```
Skype V4L2: Failed to change capture framerate (15)
Starting the process...
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280
```

---

### Post by nol_faich on 2008-11-02
New release online, I've added the support for the VIDIOC_ENUM_FRAMESIZES ioctl command. Hopefully it will fix the issue with Skype.

Can you try to change the default colorspace of the driver to YUYV and launch Cheese to see if it is OK? (line 407 of gl860-v4l.c)

---

### Post by soro2005 on 2008-11-02
The Skype crasher seems to be gone. If I'm doing it right, the change of the default color space doesn't do a thing. I've changed line 407 from
```
dev->vsettings.palette = WCAM_PALETTE_RGB24;
```
to
```
dev->vsettings.palette = WCAM_PALETTE_YUYV;
```
and then recompiled, without rebooting or doing any further steps. The image is still all green in Cheese and in Skype (Intrepid Skype).

---

### Post by nol_faich on 2008-11-03
New release online, 2.6.27a.

Cheese : OK
Skype : OK
Ekiga : vertical stripes
aMsn : not tested (please report)
Camorama  :OK

---

### Post by ricoderks on 2008-11-07
Hi,

I'am trying to install, but the script stops. I think I'am missing v4l2-ioctl.h, but don't know to install it. Can you help me?
*****************************************************************************
 1/8) [Kernel headers for current kernel installed]

 2/8) [Make is present]
*****************************************************************************
 3/8) [No old module...] Nothing to do

 4/8) [Clean up from previous compilations]
 $ make -f Makefile.standalone clean
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/ricoderks/Temp/nvgl clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CLEAN   /home/ricoderks/Temp/nvgl/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
*****************************************************************************
 5/8) [Source code generation...]
 6/8) [Compiling driver...]
 $ make -f Makefile.standalone driver
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/ricoderks/Temp/nvgl modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/ricoderks/Temp/nvgl/gl860-usb.o
  CC [M]  /home/ricoderks/Temp/nvgl/gl860-dev.o
  CC [M]  /home/ricoderks/Temp/nvgl/gl860-v4l.o
/home/ricoderks/Temp/nvgl/gl860-v4l.c:43:30: error: media/v4l2-ioctl.h: No such file or directory
/home/ricoderks/Temp/nvgl/gl860-v4l.c:105: error: ‘V4L2_CID_POWER_LINE_FREQUENCY’ undeclared here (not in a function)
/home/ricoderks/Temp/nvgl/gl860-v4l.c:143: error: ‘V4L2_CID_SHARPNESS’ undeclared here (not in a function)
/home/ricoderks/Temp/nvgl/gl860-v4l.c:152: error: ‘V4L2_CID_BACKLIGHT_COMPENSATION’ undeclared here (not in a function)
/home/ricoderks/Temp/nvgl/gl860-v4l.c: In function ‘v4l_gl860_do_ioctl’:
/home/ricoderks/Temp/nvgl/gl860-v4l.c:1432: error: ‘V4L2_PIX_FMT_SGBRG8’ undeclared (first use in this function)
/home/ricoderks/Temp/nvgl/gl860-v4l.c:1432: error: (Each undeclared identifier is reported only once
/home/ricoderks/Temp/nvgl/gl860-v4l.c:1432: error: for each function it appears in.)
/home/ricoderks/Temp/nvgl/gl860-v4l.c:1432: warning: assignment makes integer from pointer without a cast
/home/ricoderks/Temp/nvgl/gl860-v4l.c: In function ‘v4l_gl860_register_video_device’:
/home/ricoderks/Temp/nvgl/gl860-v4l.c:1975: error: ‘struct video_device’ has no member named ‘parent’
/home/ricoderks/Temp/nvgl/gl860-v4l.c:1975: warning: statement with no effect
make[2]: *** [/home/ricoderks/Temp/nvgl/gl860-v4l.o] Error 1
make[1]: *** [_module_/home/ricoderks/Temp/nvgl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [driver] Error 2

---

### Post by soro2005 on 2008-11-07
For some reason, the install script seems to be a little iffy when run from a location that's deeply nested inside your directory structure. Something like that. Try moving the entire nvgl folder to the root of your home directory, and try it from there.

---

### Post by ricoderks on 2008-11-08
Hi,

Your suggestion didn't work. I also tried looking for v4l2-ioctl.h, but I can't find this file on my system. How can I install this file?

Cheers, RICO

---

### Post by nol_faich on 2008-11-08
@Ricoderks
Hi Ricoderks!

The trouble is that your kernel is between the 2.6.27 and the 2.6.24.
I use another driver as base for this driver and it should be OK up to 2.6.24. The new should be OK with 2.6.27 and maybe later 2.6.26.x.
Have you the possibility to upgrade your kernel ?
If not, there is some part of the driver which test the kernel version. You should try to change these tests to 2.6.25 instead of 2.6.24.
Some 2.6.24 are mandatory, so you shall not change all of them, the ONLY ones I added to compile with 2.6.27 kernel are :
gl840-v4l.c line 12, 51, 1938


@all : the interaction between driver, libv4l and Cheese/Skype/etc is not as I understood at first sight. I have some ideas to test. If you have a msn address or a jabber one to send me in private mail in order to make live tests, it could be very helpful as most of work is supported by Soro.

---

### Post by ricoderks on 2008-11-10
Hi Nol,

When I have some more time I'll try a kernel update. I don't feel confident enough to quickly do this. Thanks for your help. I'll let you know how it went.

Cheers,RICO

---

### Post by nol_faich on 2008-11-10
OK, otherwise try the 2.6.26 with the changes in the three lines as explained.

---

### Post by Pander on 2008-11-18
Can someone get this into repository of Ubuntu Interpid so it will be available for all users?

I have Ubuntu with kernel 2.6.27.7 and still it is not working :S

Please, see [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/215604](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/215604)

---

### Post by soro2005 on 2008-11-19
As far as I understand, this is not going to make it into any repository until it makes it into upstream. So there's really no point in insisting. It either comes with the other kernel modules, or it doesn't. You can write Master Thorvalds about it. Well, Nol might take care of it once he's confident it's stable enough.

For the moment, this driver here works great with a couple of caveats. Some of the problems in Intrepid are because of the entire system handling video streams differently. You can see the forums aflush with regressions with all sorts of webcams. As for this driver here, it currently works better than ever with skype and cheese, with camorama some trick is needed, and ekiga is no good. If I go to gstreamer-properties and test it from there, I also get an excellent image.

Now, everybody please recognize that Nol has gone out of his way to keep up with the Intrepid release although, as far as I understand, he himself uses Mandriva with an older kernel. Folks have other things to do then to upgrade their systems because somebody else needs it. Nobody's getting paid for this. No reason to get pushy. Better chip in and help out. It's been our decision to buy a part whose manufacturer doesn't seem to care a lot...

Also, what exactly is not working, and with what camera? [This one](http://downloads.sourceforge.net/gl860/gl860_2.6.27a.tgz?modtime=1225676882&big_mirror=0)'s the one that should install and work.

---

### Post by nol_faich on 2008-11-19
@ Pander
I answered on Launchpad. The address of the SourceForge repository is in my signature to be always available.

Thanks for your answer Soro!
Two precisions here about what you said Soro. Apart these two points, you are all right.

1) I don't think we always choose the hardware.
My first laptop was out of order and I bought a new one, the one with the 0x0503:f191 webcam. That webcam is not really what I expected as I read that the Asus F5R's webcam works with an exerimental driver for the Syntek webcams. When I tried that driver it did nothing and I discovered that my Asus F5RL (so not the F5R) had not the expected webcam (Phew! Ethernet and WIFI use an experimental driver also and I don't want to imagine if they did not work...). The actual driver is inherited for the Syntek driver because it looks to me easy to understand its structure.

2) Mandriva/Ubuntu
I'm running Ubuntu Feisty on my new laptop. When I bought it I tried Gutsy and I was unable to get a X session because X crashed so that I prayed and tried Feisty which was OK. The Gutsy issue and several issues when I upgraded from Breezy to Feisty made that I urge not me to use Hardy or Ibex. Instead I downloaded Hardy and Mandriva (to test another distro). As I had troubles with the Hardy's CD, I installed Mandriva.
The drawback of that is I have the webcam with the new laptop running Feisty (2.6.17) and the laptop without webcam running Mandriva. So I was just able to compile the driver but not test it. When the PhD will be over, I will upgrade because I will not care about the issues.

---

### Post by BUGabundo on 2008-12-05
I've tested gl860_2.6.27b.tgz on Linux 2.6.28-2-ub-generic #1 SMP Tue Dec 2 17:30:53 UTC 2008 x86_64 GNU/Linux and it works so far.
Camorama is great, ekiga is a bit without collor, cheese Version: 2.24.1-0ubuntu2 works too, Multimedia System Selector OK.

You can see it at work here: [http://blubug.bugabundo.net:65006/](http://blubug.bugabundo.net:65006/)

I just needed to pull the HUE to max.

---

### Post by nol_faich on 2008-12-05
I'm a little bit confused. There is no so many trouble finally?

---

### Post by soro2005 on 2008-12-06
Camorama is fine now as well, without preloading any library. But I'm not sure it's not because of the libv4l which I don't have from the distribution repository, but from the ppa. The version I'm running is 0.5.7-1.

I'm just sitting here in extremely low light and am getting the impression that the image quality is superb today. Could hardly be better. And my CPU and GPU are at a remarkably low activity.

So get your PhD done, and then see where we stand. My guess is it's getting dramatically better.

Ekiga is still the same. (Gray, striped, and with a green lower and upper margin).

---

### Post by nol_faich on 2008-12-06
Thanks Soro :)

Dissertation on the 15th. I'm "beamering" it.

---

### Post by soro2005 on 2008-12-06
I think they don't say "beamer" in English. :D Good luck!

*edit* Oh, you mean you're using latex instead of ppt? That's cool!

---

### Post by BUGabundo on 2008-12-07
> **nol_faich said:**
> There is no so many trouble finally?

I would think so.
Other then some excessive CPU hogging, the webcam works fine for me (minor some color discoloration, but even that is ajustable).

So if so more users can test it, I guess its almost ready for submission to kernel.

---

### Post by nol_faich on 2008-12-07
Could you post an image with the color issue?

About the Kernel submission, there is a risk of system freeze in big sizes for an unknown reason. I progress in the understanding of the driver but I still did not find any reason to the freeze. Because of this, and because there is actually no way to identify automatically the flavour, the inclusion in the kernel is not so good. In one week, I think I will request anybody with the 0503 "c"/"his" to make tests by sending a data sequence dedicated to the "sim" version and seeing what happened in the syslog traces. Unfortunately, the "sim" users are far more less numerous than the "c"/"his" so you will have to do the tests to have usefull information.
I may also write to the libv4l maintainer to tell him what may be interesting for the webcams (mainly the possibility to make libv4l revert the images when the webcam is turned upside down, eventually to change the colorspace on the fly to make red/blue channel swapping, cropping management).

---

### Post by BUGabundo on 2008-12-09
when u need extra testing let me know.
Just provide all baby steps so I wont miss something.

Fixing the HUE would be great.
You can see my webcam live stream at [http://blubug.bugabundo.net:65006/](http://blubug.bugabundo.net:65006/)

---

### Post by nol_faich on 2008-12-09
I tried several times to watch your webcam these last days but nether succeeded. Either the address was unreachable, either it finds but nothing happens.
A post with an image at minimum and maximum hue would be helpful.

---

### Post by BUGabundo on 2008-12-09
Sorry about that Nol.
I know how it is, since this is my laptop webcam, it works when the laptop is Online, and bypass a Router/NAT/Firewall.

I'll take a few pics and post them online.

---

### Post by BUGabundo on 2008-12-09
Pics:
1st pic from cheese without changes (HUE is fine):
[http://fileland.bugabundo.net/fotos/Linux/webcam/Webcam-1228853917.png.php](http://fileland.bugabundo.net/fotos/Linux/webcam/Webcam-1228853917.png.php)

2nd pic from ekiga without HUE correction, is bluish:
[http://fileland.bugabundo.net/fotos/Linux/webcam/ekiga-snap-2008_12_09-201747.png.php](http://fileland.bugabundo.net/fotos/Linux/webcam/ekiga-snap-2008_12_09-201747.png.php)

3rd pic from camorana before changing HUE, its OK:
[http://fileland.bugabundo.net/fotos/Linux/webcam/Webcam-1228853917.png.php](http://fileland.bugabundo.net/fotos/Linux/webcam/Webcam-1228853917.png.php)

4th pic from camorana after changing HUE to show ok on webcam-server and ekiga:
[http://fileland.bugabundo.net/fotos/Linux/webcam/Webcam-1228853945.png.php](http://fileland.bugabundo.net/fotos/Linux/webcam/Webcam-1228853945.png.php)

last pic from ekiga with HUE fixed:
[http://fileland.bugabundo.net/fotos/Linux/webcam/ekiga-snap-2008_12_09-202233.png.php](http://fileland.bugabundo.net/fotos/Linux/webcam/ekiga-snap-2008_12_09-202233.png.php)

All pics at: [http://fileland.bugabundo.net/fotos/Linux/webcam](http://fileland.bugabundo.net/fotos/Linux/webcam)

---

### Post by nol_faich on 2008-12-09
Thanks for the pics, this is now far more clear to me. The issue is known.
The rgb24 is red/green/blue byte ordered but some applications read it as blue/green/red so that the blue and red channels are swapped.
The purpose of the hue setting is to allow a correction for that concern (your webcam has no real hue setting, so I add B&W, negative and red/blue inversion).
With my laptop Camorama and VLC work in v4l1 but one is OK and the other inverts color.
Which driver are you using with Ekiga : v4l or v4l2 ? It seems that v4l2 is OK with colors, maybe because they prefer other formats like YUYV and so on... However they may be heavy issue in v4l2 now with Ekiga.

---

### Post by BUGabundo on 2008-12-09
> **nol_faich said:**
> 
The rgb24 is red/green/blue byte ordered but some applications read it as blue/green/red so that the blue and red channels are swapped.


now that i know what to look for, I can instruct webcam-server to swap it with the parameter -x

how can i tell what version of v4l am I using?

---

### Post by nol_faich on 2008-12-09
In Preferences/Device/Video device (translated from french names), you can choose a plugin (for me it either "picture", "v4l" or "v4l2").

---

### Post by BUGabundo on 2008-12-10
System->Preferenmces->Multimedia Systems Selector->Video
I have Test, v4l and v4l2.
v4l2 was the selected one, and v4l failed to work.

---

### Post by nol_faich on 2008-12-10
Ok. in the file base_gl860.h, there is 2 lines about STK_DEV.
One is commented (// ...) and the other not. Could you comment in the presently defined STK_DEV (add // at the start) and commented out the other line (remove the //).
Make a new installation of the driver, you will have traces in the syslog.
I would like you to launch Ekiga, wait some seconds after having an image (e.g. 5s), close it and post the "grep gl860 /var/log/syslog".
It will tell us what was exchanged between Ekiga and the driver.

---

### Post by BUGabundo on 2008-12-11
after this change ekiga no longer can use the webcam. cheese, webcam-server, system Multimedia test, all seem to work fine.

I did not reboot after the new module was compiled

---

### Post by BUGabundo on 2008-12-11
attaching syslog

---

### Post by nol_faich on 2008-12-11
OK

If Ekiga is the first application you launched after the reinstallation, Ekiga asked for RGB24 in v4l et its v4l is the BGR24 of Camorama.
You can come back to the previous driver by swapping the comment of the STK_DEV.

---

### Post by BUGabundo on 2008-12-12
> **nol_faich said:**
> OK

If Ekiga is the first application you launched after the reinstallation, Ekiga asked for RGB24 in v4l et its v4l is the BGR24 of Camorama.

yes, ekiga was the 1st. then i tried a few others just to make sure it was working.

Reverting driver now.

---

### Post by nol_faich on 2008-12-13
Are you sure whether Ekiga is in v4l2 because Ekiga "speaks" v4l to the driver!

---

### Post by BUGabundo on 2008-12-15
> **nol_faich said:**
> Are you sure whether Ekiga is in v4l2 because Ekiga "speaks" v4l to the driver!

i have no idea how to check that.

---

### Post by nol_faich on 2008-12-16
I have no idea! Could you try to set v4l and report the traces by enabling STK_DEV once more time?

---

### Post by Jack Malmostoso on 2008-12-20
> **BUGabundo said:**
> i have no idea how to check that.

You should launch ```
$ gstreamer-properties
``` and make sure that as video input v4l2 is selected.
Also, check in the Ekiga preferences.

---

### Post by nol_faich on 2008-12-22
I installed Ibex to make tests but I had to revert to Feisty : not able to get multi-desktop, ethernet and wifi working! I hope to solve for these issues before the end of the year. However kind of "good" news: Ekiga froze the system after some seconds use, so I should be able to reproduce it. :popcorn:

---

### Post by BUGabundo on 2008-12-22
[QUOTE=nol_faich;6416329]not able to get multi-desktop, ethernet and wifi working!/QUOTE]

that was some **really** bad luck.
Hope u filed bugs against them all.
If you can, try Jaunty 9.04 alpha.

Latest kernel 2.6.28-3 works with your driver.

---

### Post by nol_faich on 2008-12-23
I discovered I am lucky enough to have a special chip part of a special wifi device together with a mistake in a configuration file for my wifi LED.
Now the wifi isue is solved and the multi-desktop also (even if i don't understand why).
The next big step will be the restart after having updated my whole system.

---

### Post by nol_faich on 2008-12-29
My system is now working. I began tests with Ekiga in order to know why the system may freeze.
I still do not have discovered the reason but I can reduce the frequency. I will also write to the libv4l maintainer to see what could be done for the webcam to be usable without the driver having to decode by its own the images.

---

### Post by blazercist on 2008-12-29
I'm now happily using your driver on a fresh install of ArchLinux.  Install was a breeze I just chose "c" and that was it.  Works like a charm, thanks again Nol.

---

### Post by BUGabundo on 2008-12-29
just to let you guys know it works great with the latest jaunty kernel

$ uname -a
Linux blubug 2.6.28-4-generic #5-Ubuntu SMP Fri Dec 26 22:48:55 UTC 2008 x86_64 GNU/Linux

---

### Post by nol_faich on 2008-12-30
@BUGabundo : Thanks for the information. After some modification to be usable with 2.6.25 and 26 and 27, it is pleasant that the driver is OK with 2.6.28.

@Blazercist : Nice to see you again, thanks.

@ all : I will try as soon as possible a modified version of lib4vl2 to make a proof of concept of red-blue channel swap and/or 180° image rotation on the fly. If OK, I will propose that to the libv4l maintainer and the driver will have no more decoding to do with the usual applications. Only Ekiga will still be a problem because of its nasty not 4/3 image format.

---

### Post by nol_faich on 2009-01-02
Happy new [S]kernels[/S] [S]drivers[/S] year !

Some news about the driver migration to libv4l. 
A driver shall not do decode the images, it gets images and that's all because such a CPU consumming task is not suitable for the kernel. This is what I would like to achieve with the future drivers because libv4l is intended for image decoding. Moreover the issues with Ekiga seem to originate the decoding stage, so to put it out the kernel is also good.

The missing tasks to be done by libv4l are :
- swap if necessary the red and blue channels for v4l1 application with color issue
- 180 degree rotation of the image when the webcam informs the driver that the image is upside down because of the rotation of the webcam (or inclination of the screen)
- a third task is the addition of a black padding when the requested size does not respect the width/height ratio.

I wrote to Hans de Goede, the libv4l maintainer.

About the red & blue swap:
Camorama is likely wrong with RGB management because the v4l1's RGB palette has to use colors encoded in the BGR order(the order in BMP images). For quite a very weird, strange, astonish and non-understandable reason, Camorama uses the RGB palette and consider reading colors encoded in the RGB order. As the color error is due to a wrong implementation, libv4l won't correct this. However I thought that Camorama was right with colors, so I will correct this in the existing drivers.

About rotation:
The safer way to manage that may be the addition of a new webcam setting in the v4l2 norm. Libv4l would have to read the setting value on a regular basis to know whether the image has to be rotated or not

About black padding:
I don't know enough of libv4l to actually know what it can do, I'm studying this.

Nothing is actually implemented. Beside that, I made tests with a lightened version of the driver (no image decoding) and this fails with Camorama, Ekiga(v4l2) and aMsn but is OK with Skype and Cheese. I think it is because they do not ask for which palette they accept and refuse the raw webcam data, for aMsn it seems to be because of a truncated -but allowed- implementation of v4l2 not managed by libv4l.

---

### Post by soro2005 on 2009-01-02
Happy new year also to you, Dr. Nol! :-({|=

---

### Post by nol_faich on 2009-01-05
@Soro : Thanks Soro !

@ All :
Some news, I patched libv4l_0.5.7 to manage the rotation of the webcam and I achieve the driver working with Camorama(v4l1), Ekiga (v4l1&2), Skype and Cheese. aMsn still does not get any image, maybe a work around in libv4l is needed for.
I will also add a work around in the driver to allow to swap blue and red channels.
Once done and the patch accepted, the driver with no more decoding will be released.

After that, I will make a test version with the hope to identify automagically when a webcam is 1,3MP or 2MP (Only the "ms" and "sim" user are concerned by these tests).

---

### Post by BUGabundo on 2009-01-24
FYI gl860+libv4lc is working great with latest kernel
$ uname -a
Linux blubug 2.6.28-5-generic #15-Ubuntu SMP Fri Jan 23 01:16:33 UTC 2009 x86_64 GNU/Linux


UPDATE
gl860_gl860_libv4lc will stop responding if I test the webcam with v4l, but works great with v4l2

---

### Post by BUGabundo on 2009-01-26
i should test stuff better before saying they are ok:

flash will not work with that version, and camorana shows a really strange image.
Had to revert to older version

need to test newest version without v4l

---

### Post by nol_faich on 2009-01-26
Thanks for testing!

I'm preparing a new with explanations on how it has to be used and what the caveats.
Could you try ASAP the gl860_test_msc with flash and xawtv? It is a debug version for test purpose but you can use it.
I need the 'dmesg | grep gl860'.

---

### Post by nol_faich on 2009-01-26
Last version with v4l here : [http://downloads.sourceforge.net/gl860/gl860_libv4l_0.5.8a.tgz?use_mirror=](http://downloads.sourceforge.net/gl860/gl860_libv4l_0.5.8a.tgz?use_mirror=)

---

### Post by BUGabundo on 2009-01-27
> **nol_faich said:**
> Last version with v4l here : [http://downloads.sourceforge.net/gl860/gl860_libv4l_0.5.8a.tgz?use_mirror=](http://downloads.sourceforge.net/gl860/gl860_libv4l_0.5.8a.tgz?use_mirror=)

this is what i got from canorama with your link

[http://fileland.bugabundo.net/fotos/Webcam/Webcam-1233056421.png.php](http://fileland.bugabundo.net/fotos/Webcam/Webcam-1233056421.png.php)

ekiga is okay... actually i think the quality of it improved

---

### Post by nol_faich on 2009-01-27
It really looks like you do not use the v4l1 compatibility layer. Do you have used the LD_PRELOAD to launch camorama? (see the README file)
If yes, force the use of the PRELOAD by typing LD_PRELOAD=.... camorama.
With the libv4l, all applications using v4l1 are no more working properly with the driver, they need to be used with a compatibility layer which translates v4l1 functions to v4l2.

For example, if you set Ekiga to use v4l2 you just have to type "ekiga" to launch it.
In you set it to use v4l1, you should use "LD_PRELOAD=... ekiga".

The reason of this is that ye olde v4l1 does not understand many image formats in such a way that the raw data format from the webcam is unknown. As the driver makes no more decoding, the v4l1 applications can't cope with the raw data and the conversion must be done by something else: the libv4l.
The advantage is that the kernel as less job to do (Ekiga is now for me quite stable since I use this driver). Also it is easier to make an application as you do not have anymore to worry about whether your application is able to manage an image format.


Can you make test with Xawtv and flash? I need the traces in the dmesg.

---

### Post by BUGabundo on 2009-01-27
xawtv its just black, same with flash on [http://ustream.tv](http://ustream.tv)

will try as mention on README later. do i need to install that v4l module too?


$ dmesg | grep gl860
[   23.359630] gl860: Genesys USB2.0 webcam driver startup
[   23.359716] gl860: Release: 0103
[   23.359774] gl860: Number of interfaces : 1
[   23.359834] gl860: Forcage du pilote
[   23.359890] gl860: Version Hulkie/Iceman/Soro (c)
[   23.359947] gl860: Genesys USB2.0 - GL860 based webcam found.
[   23.360019] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[   25.244167] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[   25.244273] usbcore: registered new interface driver usb_gl860_driver
[   25.244356] gl860: v0.3.0 : Genesys gl860 USB Video Camera
[ 9242.940033] gl860: usb_gl860_exit: Genesys USB2.0 webcam driver shutdown
[ 9242.940041] usbcore: deregistering interface driver usb_gl860_driver
[ 9242.940066] gl860: Genesys USB2.0 Camera disconnected
[ 9242.940091] gl860: Genesys USB2.0 Camera release resources video device /dev/video0
[ 9243.001940] gl860: Genesys USB2.0 webcam driver startup
[ 9243.001973] gl860: Release: 0103
[ 9243.001976] gl860: Number of interfaces : 1
[ 9243.001978] gl860: Forcage du pilote
[ 9243.001980] gl860: Version Hulkie/Iceman/Soro (c)
[ 9243.001982] gl860: Genesys USB2.0 - GL860 based webcam found.
[ 9243.001985] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[ 9244.956616] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[ 9244.956669] usbcore: registered new interface driver usb_gl860_driver
[ 9244.956673] gl860: v0.4.0 : Genesys gl860 USB Video Camera
[ 9330.960891] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 9330.960906] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 9330.960909] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9330.960912] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9330.960914] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9330.960917] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9330.960919] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 9330.960922] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9330.960924] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9330.960926] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9330.960928] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9330.960931] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 9330.960933] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9330.960935] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9330.960938] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9330.960940] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9330.960942] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 9330.960944] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9330.960947] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9330.960949] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9330.960951] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9330.961825] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 9330.961829] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 9330.961835] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 9330.961837] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 9330.961854] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9330.961856] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.961858] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9330.961860] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.961862] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9330.961864] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9330.961866] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9330.961868] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.961893] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9330.961894] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.961897] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9330.961899] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.961901] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9330.961902] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9330.961905] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9330.961906] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.961920] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9330.961922] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.961924] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9330.961926] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.961928] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9330.961930] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9330.961932] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9330.961934] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.961947] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9330.961949] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.961951] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9330.961953] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.961955] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9330.961956] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9330.961958] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9330.961960] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.961985] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9330.961987] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.961989] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9330.961991] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.961993] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9330.961995] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9330.961997] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9330.961998] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.962013] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9330.962015] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962017] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9330.962018] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962020] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9330.962022] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9330.962024] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9330.962026] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962039] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9330.962040] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962042] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9330.962044] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962046] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9330.962048] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9330.962050] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9330.962052] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962065] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9330.962067] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962069] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9330.962070] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962072] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9330.962074] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9330.962076] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9330.962078] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962101] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9330.962103] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.962105] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9330.962107] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.962109] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9330.962110] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9330.962112] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9330.962114] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.962128] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9330.962130] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962132] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9330.962134] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962136] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9330.962137] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9330.962139] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9330.962141] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962155] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9330.962156] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962159] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9330.962160] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962162] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9330.962164] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9330.962166] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9330.962168] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962181] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9330.962183] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962185] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9330.962187] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962189] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9330.962190] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9330.962193] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9330.962194] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962214] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9330.962216] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.962218] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9330.962219] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.962221] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9330.962223] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9330.962225] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9330.962227] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9330.962240] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9330.962242] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962244] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9330.962246] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962248] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9330.962250] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9330.962252] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9330.962253] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9330.962266] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9330.962268] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962270] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9330.962272] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962274] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9330.962276] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9330.962278] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9330.962280] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9330.962292] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9330.962294] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962296] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9330.962298] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962300] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9330.962302] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9330.962304] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9330.962306] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.962322] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9330.962334] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9330.962344] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9330.962354] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9330.963690] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9330.963692] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.963695] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9330.963697] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.963699] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9330.963701] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9330.963703] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9330.963705] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9330.963710] gl860: VIDIOC_S_FMTe >> BA81 [1600x1200]
[ 9330.963712] gl860: VIDIOC_S_FMTs << BA81 [1600x1200]
[ 9333.354621] gl860: Frame buffer overflow (1920501/1920000)!
[ 9333.558661] gl860: Frame buffer overflow (1920137/1920000)!
[ 9333.750672] gl860: Frame buffer overflow (1920190/1920000)!
[ 9333.922676] gl860: Frame buffer overflow (1921590/1920000)!
[ 9335.682654] gl860: Frame buffer overflow (1921553/1920000)!
[ 9336.799207] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 9336.799224] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 9336.799228] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9336.799231] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9336.799234] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9336.799237] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9336.799241] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 9336.799244] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9336.799247] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9336.799250] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9336.799253] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9336.799257] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 9336.799260] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9336.799263] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9336.799266] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9336.799269] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9336.799272] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 9336.799275] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9336.799278] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9336.799281] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9336.799284] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9336.799711] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 9336.799716] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 9336.799720] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 9336.799723] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 9336.799740] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9336.799742] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.799745] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9336.799748] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.799750] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9336.799753] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9336.799756] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9336.799758] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.799785] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9336.799787] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.799790] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9336.799793] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.799795] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9336.799798] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9336.799800] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9336.799803] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.799823] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9336.799825] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.799828] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9336.799831] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.799834] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9336.799836] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9336.799839] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9336.799841] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.799859] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9336.799862] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.799864] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9336.799867] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.799870] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9336.799872] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9336.799875] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9336.799877] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.799903] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9336.799905] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.799908] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9336.799910] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.799913] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9336.799915] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9336.799918] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9336.799930] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.799953] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9336.799958] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.799961] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9336.799963] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.799966] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9336.799971] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9336.799974] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9336.799976] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.800004] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9336.800006] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800009] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9336.800012] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800016] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9336.800019] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9336.800021] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9336.800024] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800048] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9336.800050] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800053] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9336.800057] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800060] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9336.800062] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9336.800065] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9336.800067] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800097] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9336.800099] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.800102] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9336.800105] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.800107] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9336.800110] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9336.800113] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9336.800115] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.800134] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9336.800136] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.800139] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9336.800141] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.800144] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9336.800146] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9336.800149] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9336.800151] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.800169] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9336.800171] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800174] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9336.800177] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800179] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9336.800182] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9336.800184] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9336.800187] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800204] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9336.800207] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800210] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9336.800212] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800215] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9336.800217] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9336.800220] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9336.800222] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800249] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9336.800252] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.800255] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9336.800257] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.800260] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9336.800262] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9336.800265] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9336.800267] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.800287] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 9336.800289] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.800292] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 9336.800294] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.800297] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 9336.800299] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 9336.800302] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 9336.800304] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 9336.800323] gl860: VIDIOC_TRY_FMTe >> RGB3 [1280x1024]
[ 9336.800326] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800329] gl860: VIDIOC_TRY_FMTe >> BGR3 [1280x1024]
[ 9336.800331] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800334] gl860: VIDIOC_TRY_FMTe >> BA81 [1280x1024]
[ 9336.800336] gl860: VIDIOC_TRY_FMTs << BA81 [1280x1024]
[ 9336.800339] gl860: VIDIOC_TRY_FMTe >> GBRG [1280x1024]
[ 9336.800342] gl860: VIDIOC_TRY_FMTs << GBRG [1280x1024]
[ 9336.800360] gl860: VIDIOC_TRY_FMTe >> RGB3 [1600x1200]
[ 9336.800362] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800365] gl860: VIDIOC_TRY_FMTe >> BGR3 [1600x1200]
[ 9336.800367] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800370] gl860: VIDIOC_TRY_FMTe >> BA81 [1600x1200]
[ 9336.800372] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 9336.800375] gl860: VIDIOC_TRY_FMTe >> GBRG [1600x1200]
[ 9336.800377] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 9336.800400] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 9336.800416] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 9336.800431] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 9336.800445] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 9336.887071] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 9336.887074] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.887076] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 9336.887077] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.887079] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 9336.887080] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 9336.887081] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 9336.887083] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 9336.887086] gl860: VIDIOC_S_FMTe >> BA81 [640x480]
[ 9336.887088] gl860: VIDIOC_S_FMTs << BA81 [640x480]
[ 9337.437629] gl860: Frame buffer overflow (307271/307200)!
[ 9337.501635] gl860: Frame buffer overflow (307324/307200)!
[ 9337.569636] gl860: Frame buffer overflow (307975/307200)!
[ 9337.637631] gl860: Frame buffer overflow (307898/307200)!
[ 9337.705630] gl860: Frame buffer overflow (308484/307200)!
[ 9337.769637] gl860: Frame buffer overflow (307514/307200)!
[ 9338.137627] gl860: Frame buffer overflow (307910/307200)!
[ 9338.217626] gl860: Frame buffer overflow (307217/307200)!
[ 9338.297635] gl860: Frame buffer overflow (307219/307200)!
[ 9338.749631] gl860: Frame buffer overflow (307377/307200)!
[ 9339.229641] gl860: Frame buffer overflow (308878/307200)!
[ 9339.301641] gl860: Frame buffer overflow (307839/307200)!
[ 9339.373640] gl860: Frame buffer overflow (307839/307200)!
[ 9352.594691] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 9352.594698] gl860: VIDIOCSWIN : (x,y)=(0,0) [800x600] Flags=0
[ 9355.017643] gl860: Frame buffer overflow (481599/480000)!
[ 9355.089641] gl860: Frame buffer overflow (481359/480000)!
[ 9355.161636] gl860: Frame buffer overflow (480799/480000)!
[ 9355.316052] gl860: VIDIOCGWIN : (x,y)=(0,0) [800x600] Flags=0
[ 9355.800125] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 9355.892304] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[12633.502903] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[12633.502926] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[12633.502930] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[12633.502933] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[12633.502936] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[12633.502939] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[12633.502943] gl860: VIDIOC_ENUM_FMT : 1=BA81
[12633.502946] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[12633.502949] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[12633.502952] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[12633.502955] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[12633.502958] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[12633.502961] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[12633.502964] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[12633.502967] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[12633.502970] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[12633.502974] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[12633.502976] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[12633.502979] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[12633.502982] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[12633.502986] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[12633.503133] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[12633.503137] gl860: VIDIOC_ENUM_FMT : 1=BA81
[12633.503140] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[12633.503142] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[12635.929574] gl860: VIDIOC_TRY_FMTe >> YUYV [384x288]
[12635.929579] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[12635.929585] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[12635.929589] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[12636.552046] gl860: Frame buffer overflow (308000/307200)!
[12637.280052] gl860: Frame buffer overflow (307500/307200)!
[12637.852043] gl860: Frame buffer overflow (307360/307200)!
[12638.424048] gl860: Frame buffer overflow (308480/307200)!
[12638.496041] gl860: Frame buffer overflow (307840/307200)!
[12638.669045] gl860: VIDIOC_TRY_FMTe >> RGB3 [384x288]
[12638.669050] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[12638.669053] gl860: VIDIOC_TRY_FMTe >> BGR3 [384x288]
[12638.669056] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[12638.669058] gl860: VIDIOC_TRY_FMTe >> BA81 [384x288]
[12638.669061] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[12638.669064] gl860: VIDIOC_TRY_FMTe >> GBRG [384x288]
[12638.669066] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[12638.669072] gl860: VIDIOC_S_FMTe >> BA81 [640x480]
[12638.705030] gl860: VIDIOC_S_FMTs << BA81 [640x480]
[12639.359048] gl860: Frame buffer overflow (307505/307200)!
[12641.119050] gl860: Frame buffer overflow (308479/307200)!
[12641.191048] gl860: Frame buffer overflow (307839/307200)!
[12764.843923] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[12764.843927] gl860: VIDIOC_ENUM_FMT : 1=BA81
[12764.843929] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[12764.843930] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[12764.843933] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[12764.843935] gl860: VIDIOC_S_FMTe >> BGR3 [640x480]
[12764.843936] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[12765.495069] gl860: Frame buffer overflow (307840/307200)!
[12767.275063] gl860: Frame buffer overflow (308193/307200)!
[12767.343086] gl860: Frame buffer overflow (307840/307200)!
[12767.484879] gl860: VIDIOC_G_FMT : GBRG [640x480]
[12767.484886] gl860: VIDIOC_S_FMTe >> GBRG [160x120]
[12767.521036] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[12768.168064] gl860: Frame buffer overflow (307251/307200)!
[12769.900024] gl860: Frame buffer overflow (307276/307200)!
[12769.968083] gl860: Frame buffer overflow (307840/307200)!
[12786.517972] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[12786.517978] gl860: VIDIOC_ENUM_FMT : 1=BA81
[12786.517982] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[12786.517984] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[12786.517989] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[12786.517992] gl860: VIDIOC_S_FMTe >> BGR3 [640x480]
[12786.517994] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[12787.171068] gl860: Frame buffer overflow (307247/307200)!
[12788.931065] gl860: Frame buffer overflow (308480/307200)!
[12789.003063] gl860: Frame buffer overflow (307840/307200)!
[12789.140069] gl860: VIDIOC_G_FMT : GBRG [640x480]
[12789.140073] gl860: VIDIOC_S_FMTe >> GBRG [160x120]
[12789.177036] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[12789.820064] gl860: Frame buffer overflow (307487/307200)!
[12791.600088] gl860: Frame buffer overflow (308480/307200)!
[12791.672086] gl860: Frame buffer overflow (307840/307200)!
[12793.835042] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[12793.835048] gl860: VIDIOC_ENUM_FMT : 1=BA81
[12793.835051] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[12793.835054] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[12793.835060] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[12793.835063] gl860: VIDIOC_S_FMTe >> BGR3 [640x480]
[12793.835066] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[12796.219088] gl860: Frame buffer overflow (308017/307200)!
[12796.291081] gl860: Frame buffer overflow (307840/307200)!
[12796.428043] gl860: VIDIOC_G_FMT : GBRG [640x480]
[12796.428048] gl860: VIDIOC_S_FMTe >> GBRG [320x240]
[12796.464025] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[12798.890087] gl860: Frame buffer overflow (308480/307200)!
[12798.962082] gl860: Frame buffer overflow (308033/307200)!
[12799.096030] gl860: VIDIOC_G_FMT : GBRG [640x480]

---

### Post by nol_faich on 2009-01-27
The only thing you need and is maybe not installed is libv4l. More informations in the README file.

---

### Post by nol_faich on 2009-01-27
The webcam works with the Flash plugin, I test it with this site :
[http://www.mini-jeu-gratuit.fr/webcam/jouer+the+night+of+the+ninja-307.php](http://www.mini-jeu-gratuit.fr/webcam/jouer+the+night+of+the+ninja-307.php)

Flash version <= 9 is v4l1 so the browser needs to be launch with LD_PRELOAD.

Flash 10 uses v4l2 so there must be not any trouble with it.

---

### Post by BUGabundo on 2009-01-28
i'm using Adobe Flash 64bits plugin... no idea what it uses.
with the old driver (pure v4l2) it works great
[http://bambuser.com/channel/BUGabundo](http://bambuser.com/channel/BUGabundo) here are a few

---

### Post by BUGabundo on 2009-01-28
I find the README a bit too much confuse... but then again, I have one of my last exams today, so I dont have much space left in my brain. If you are usually on IRC (freenode) let me know (ping BUGabundo)

---

### Post by BUGabundo on 2009-01-30
Already sent this to nol, but it goes so everyone else can read it:

Comments between  []

$ xsane
Killed
[froze while aquiring image]

$ camorama -D --width=640 --height=480

VIDIOCGCAP
device name = gl860
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 1600
max height = 1200
min width = 640
min height = 480

VIDIOCGWIN
x = 0
y = 0
width = 640
height = 480
chromakey = 0
flags = 32767

VIDIOCGWIN
x = 0
y = 0
width = 640
height = 480
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 35840
hue = 0
colour = 39321
contrast = 0
whiteness = 0
colour depth = 24
24bit RGB

VIDIOCGMBUF
mb.size = 15360000
mb.frames = 2
mb.offset = 7680000
update_tooltip called
tip - acap off
** Message: SET PIC
** Message: SET PIC
update_tooltip called
tip - acap off
dir now = /home/bugabundo/Webcam_Pictures
file now = Webcam

(camorama:13126): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GnomeAppBar'

(camorama:13126): GnomeUI-CRITICAL **: gnome_appbar_push: assertion `GNOME_IS_APPBAR(appbar)' failed

[image shows those 3 side-by-side gray images]


$ camorama -D -R --width=640 --height=480
gah!

VIDIOCGCAP
device name = gl860
device type = 1
# of channels = 1
# of audio devices = 0
max width = 1600
max height = 1200
min width = 640
min height = 480

VIDIOCGWIN
x = 0
y = 0
width = 640
height = 480
chromakey = 0
flags = 32767

VIDIOCGWIN
x = 0
y = 0
width = 640
height = 480
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 35840
hue = 0
colour = 39168
contrast = 0
whiteness = 0
colour depth = 24
24bit RGB
using read()
update_tooltip called
tip - acap off
** Message: SET PIC
** Message: SET PIC
update_tooltip called
tip - acap off

[image shows those 3 side-by-side gray images]



$ LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so camorama
ERROR: ld.so: object '/usr/local/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
[This PATH doesnt exist.

So I searched for the correct one:
$ mlocate v4l1compat.so
/usr/lib/libv4l/v4l1compat.so
/usr/lib32/libv4l/v4l1compat.so
]

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
[This works OKAY]

$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so camorama
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
[This one fails]


$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so mplayer tv:// -tv driver=v4l:width=640:height=480:fps=10:hue=-99:brightness=0:outfmt=rgb24:device=/dev/video0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: gl860
 Capabilites: capture
 Device type: 1
 Supported sizes: 640x480 => 1600x1200
 Inputs: 1
 0: Webcam:  (tuner:0, norm:pal)
Using input 'Webcam'
Selected input hasn't got a tuner!
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: BGR 24-bit)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using BGR 24-bit as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xf86610]SwScaler: using unscaled bgr24 -> yuv420p special converter
VO: [xv] 640x480 => 640x480 Planar YV12
Selected video codec: [rawbgr24] vfm: raw (RAW BGR24)
==========================================================================
Audio: no sound
Starting playback...
 MJP: returning! 0%  4%  0.0% 0 0
GNOME screensaver enabled

Exiting... (Quit)

[Works okay, but image is too slow]



$ clear; xawtv

This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.28-6-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
v4l2: waiting for a free buffer
^C
[xawtv freezes both with and without preload]



$ mplayer tv:// -tv driver=v4l2:width=640:height=480:fps=10:outfmt=rgb24:device=/dev/video0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Genesys gl860 USB Video Camera
 Capabilites:  video capture  read/write  streaming
 supported norms: 0 = webcam;
 inputs: 0 = USB;v4l2: ioctl get input failed: Invalid argument

 Current input: 1
 Current format: RGB24
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Cannot find codec matching selected -vo and video format 0x47524247.
Read DOCS/HTML/en/codecs.html!
==========================================================================

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)




$ mencoder tv:// -tv driver=v4l2:width=640:height=480:fps=10:outfmt=rgb24:device=/dev/video0 -nosound -ovc lavc -o out.avi
MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Genesys gl860 USB Video Camera
 Capabilites:  video capture  read/write  streaming
 supported norms: 0 = webcam;
 inputs: 0 = USB;v4l2: ioctl get input failed: Invalid argument

 Current input: 1
 Current format: RGB24
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
[V] filefmt:9  fourcc:0x47524247  size:640x480  fps:10.00  ftime:=0.1000
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Cannot find codec matching selected -vo and video format 0x47524247.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...



[Flash doesnt work. just records a black image.]


$ dmesg | grep gl860
[ 4085.229292] gl860: Genesys USB2.0 webcam driver startup
[ 4085.229323] gl860: Release: 0103
[ 4085.229326] gl860: Number of interfaces : 1
[ 4085.229328] gl860: Forcage du pilote
[ 4085.229330] gl860: Version Hulkie/Iceman/Soro (c)
[ 4085.229332] gl860: Genesys USB2.0 - GL860 based webcam found.
[ 4085.229334] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[ 4087.161112] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[ 4087.161166] usbcore: registered new interface driver usb_gl860_driver
[ 4087.161171] gl860: v0.4.0 : Genesys gl860 USB Video Camera
[ 4381.111078] gl860: VIDIOCSPICT : palette=1 (r24=4 r32=5 uy=9 yu=8)
[ 4381.111100] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4381.622609] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4382.584776] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4382.678353] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4382.689826] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4382.709291] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4382.820604] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4382.919211] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4408.438122] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4408.464833] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4464.542402] gl860: VIDIOCSPICT : palette=1 (r24=4 r32=5 uy=9 yu=8)
[ 4464.542432] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4464.708853] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4464.785378] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4464.808168] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4464.818508] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4464.853189] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4465.295137] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4465.314365] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4469.886062] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4469.913215] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4474.114353] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4474.141842] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4475.926911] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4519.976899] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 4519.976931] gl860: VIDIOCSWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4522.298093] gl860: Frame buffer overflow (307840/307200)!
[ 4522.596041] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4523.280937] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4523.373243] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4658.010844] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 4658.010876] gl860: VIDIOCSWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4660.334088] gl860: Frame buffer overflow (307840/307200)!
[ 4660.628038] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=0
[ 4661.023483] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4661.023581] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4689.916561] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 4689.916567] gl860: VIDIOCSWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4692.263101] gl860: Frame buffer overflow (481600/480000)!
[ 4692.568045] gl860: VIDIOCGWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4692.808064] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4692.808139] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4902.987903] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 4902.987910] gl860: VIDIOCSWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4905.339131] gl860: Frame buffer overflow (480396/480000)!
[ 4905.668035] gl860: VIDIOCGWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4906.045936] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4906.046045] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4915.067912] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 4915.067970] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 4915.068039] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 4915.068044] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 4915.068047] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 4915.068050] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 4915.068053] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 4915.068057] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 4915.068060] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 4915.068063] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 4915.068067] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 4915.068070] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 4915.068074] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 4915.068077] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 4915.068080] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 4915.068083] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 4915.068086] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 4915.068090] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 4915.068093] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 4915.068096] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 4915.068100] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 4915.068103] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 4915.068249] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 4915.068253] gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[ 4915.068256] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 4915.068259] gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[ 4915.068262] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 4915.068265] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 4915.068268] gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[ 4915.068271] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 4915.068274] gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[ 4915.068277] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 4915.068280] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 4915.068282] gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[ 4915.068285] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 4915.068289] gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[ 4915.068291] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 4915.068294] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 4915.068297] gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[ 4915.068300] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 4915.068303] gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[ 4915.068306] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 4915.068345] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 4915.068365] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 4915.068367] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4915.068371] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 4915.068373] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4915.068376] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 4915.068379] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 4915.068382] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 4915.068384] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4915.068388] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 4915.068391] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4915.068394] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 4915.068397] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4915.068400] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 4915.068402] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 4915.068405] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 4915.068408] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4915.068415] gl860: VIDIOC_S_FMTe >> BA81 [800x600]
[ 4915.068418] gl860: VIDIOC_S_FMTs << BA81 [800x600]
[ 4917.426129] gl860: Frame buffer overflow (481599/480000)!
[ 4917.728047] gl860: VIDIOCGWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4917.728058] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 4917.728061] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4917.728064] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 4917.728066] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4917.728069] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 4917.728072] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 4917.728074] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 4917.728077] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4917.728080] gl860: VIDIOC_TRY_FMTe >> RGB3 [800x600]
[ 4917.728083] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4917.728085] gl860: VIDIOC_TRY_FMTe >> BGR3 [800x600]
[ 4917.728088] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4917.728090] gl860: VIDIOC_TRY_FMTe >> BA81 [800x600]
[ 4917.728093] gl860: VIDIOC_TRY_FMTs << BA81 [800x600]
[ 4917.728095] gl860: VIDIOC_TRY_FMTe >> GBRG [800x600]
[ 4917.728098] gl860: VIDIOC_TRY_FMTs << GBRG [800x600]
[ 4938.500595] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 4938.500601] gl860: VIDIOCSWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4940.804162] gl860: Frame buffer overflow (480787/480000)!
[ 4941.184040] gl860: VIDIOCGWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4941.522521] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4941.522629] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4968.241580] gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=7FFF
[ 4968.241586] gl860: VIDIOCSWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4970.574156] gl860: Frame buffer overflow (481082/480000)!
[ 4970.872042] gl860: VIDIOCGWIN : (x,y)=(0,0) [800x600] Flags=0
[ 4971.241739] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 4971.241849] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 5241.307890] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5241.307948] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5241.308515] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5241.308520] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.308524] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.308527] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.308530] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.308534] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5241.308537] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.308540] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.308543] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.308546] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.308549] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5241.308552] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.308555] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.308558] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.308561] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.308564] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5241.308567] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.308570] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.308573] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.308576] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.308667] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5241.308670] gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[ 5241.308673] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.308676] gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[ 5241.308678] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.308681] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5241.308684] gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[ 5241.308686] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5241.308689] gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[ 5241.308691] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 5241.308694] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5241.308697] gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[ 5241.308699] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.308702] gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[ 5241.308704] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.308707] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5241.308710] gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[ 5241.308712] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.308715] gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[ 5241.308717] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.609550] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5241.609558] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5241.609570] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5241.609574] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.609577] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.609580] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.609583] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.609587] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5241.609590] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.609593] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.609596] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.609599] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.609602] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5241.609605] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.609608] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.609611] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.609614] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.609618] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5241.609620] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.609623] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.609626] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.609629] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.609706] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5241.609710] gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[ 5241.609712] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.609715] gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[ 5241.609718] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.609721] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5241.609723] gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[ 5241.609725] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5241.609728] gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[ 5241.609731] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 5241.609733] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5241.609736] gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[ 5241.609738] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.609741] gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[ 5241.609744] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.609747] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5241.609749] gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[ 5241.609752] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.609754] gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[ 5241.609757] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.671839] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5241.671847] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5241.671858] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5241.671862] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.671866] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.671869] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.671872] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.671876] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5241.671879] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.671882] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.671885] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.671888] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.671891] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5241.671894] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.671897] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.671900] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.671903] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.671906] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5241.671909] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5241.671912] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5241.671915] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5241.671918] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5241.672004] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5241.672007] gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[ 5241.672010] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.672013] gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[ 5241.672015] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.672018] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5241.672021] gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[ 5241.672023] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5241.672026] gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[ 5241.672029] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 5241.672031] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5241.672034] gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[ 5241.672037] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.672039] gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[ 5241.672042] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5241.672045] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5241.672047] gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[ 5241.672050] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5241.672053] gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[ 5241.672055] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5365.301456] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 5365.301464] gl860: VIDIOCSWIN : (x,y)=(0,0) [640x480] Flags=0
[ 5365.920167] gl860: Frame buffer overflow (308000/307200)!
[ 5366.648174] gl860: Frame buffer overflow (307604/307200)!
[ 5367.612176] gl860: Frame buffer overflow (308479/307200)!
[ 5367.912918] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 5367.912923] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 5367.912927] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 5367.912931] gl860: VIDIOCSPICT : palette=4 (r24=4 r32=5 uy=9 yu=8)
[ 5378.105987] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5378.106055] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5378.106118] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5378.106123] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5378.106126] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5378.106129] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5378.106132] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5378.106136] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5378.106138] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5378.106141] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5378.106144] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5378.106147] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5378.106150] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5378.106153] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5378.106156] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5378.106159] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5378.106162] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5378.106165] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5378.106167] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5378.106170] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5378.106173] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5378.106176] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5378.106327] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5378.106330] gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[ 5378.106333] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106336] gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[ 5378.106338] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5378.106341] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5378.106343] gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[ 5378.106346] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5378.106349] gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[ 5378.106351] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 5378.106354] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5378.106357] gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[ 5378.106359] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106362] gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[ 5378.106364] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5378.106367] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5378.106369] gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[ 5378.106372] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106375] gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[ 5378.106377] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5378.106629] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 5378.106632] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106635] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 5378.106637] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106640] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 5378.106642] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5378.106644] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 5378.106647] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106651] gl860: VIDIOC_TRY_FMTe >> RGB3 [640x480]
[ 5378.106653] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106656] gl860: VIDIOC_TRY_FMTe >> BGR3 [640x480]
[ 5378.106658] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106660] gl860: VIDIOC_TRY_FMTe >> BA81 [640x480]
[ 5378.106663] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5378.106665] gl860: VIDIOC_TRY_FMTe >> GBRG [640x480]
[ 5378.106667] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5378.106673] gl860: VIDIOC_S_FMTe >> BA81 [640x480]
[ 5378.106676] gl860: VIDIOC_S_FMTs << BA81 [640x480]
[ 5380.403187] gl860: Frame buffer overflow (308479/307200)!
[ 5440.952379] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5440.952401] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5440.952405] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5440.952408] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5440.952411] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5440.952414] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5440.952418] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5440.952421] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5440.952424] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5440.952427] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5440.952430] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5440.952433] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5440.952436] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5440.952439] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5440.952442] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5440.952445] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5440.952448] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5440.952450] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5440.952453] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5440.952456] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5440.952459] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5440.952572] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5440.952575] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5440.952578] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5440.952580] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5442.541843] gl860: VIDIOC_TRY_FMTe >> YUYV [384x288]
[ 5442.541848] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5442.541854] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[ 5442.541858] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5444.868184] gl860: Frame buffer overflow (307840/307200)!
[ 5445.168041] gl860: VIDIOC_TRY_FMTe >> RGB3 [384x288]
[ 5445.168046] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5445.168049] gl860: VIDIOC_TRY_FMTe >> BGR3 [384x288]
[ 5445.168051] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5445.168054] gl860: VIDIOC_TRY_FMTe >> BA81 [384x288]
[ 5445.168056] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5445.168059] gl860: VIDIOC_TRY_FMTe >> GBRG [384x288]
[ 5445.168061] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5445.168067] gl860: VIDIOC_S_FMTe >> BA81 [640x480]
[ 5445.205022] gl860: VIDIOC_S_FMTs << BA81 [640x480]
[ 5447.480192] gl860: Frame buffer overflow (307615/307200)!
[ 5542.436505] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5542.436532] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5542.436561] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5542.436564] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.436565] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.436567] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.436568] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.436570] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5542.436572] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.436573] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.436575] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.436576] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.436578] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5542.436579] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.436581] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.436582] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.436584] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.436585] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5542.436586] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.436588] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.436589] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.436591] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.436678] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5542.436680] gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[ 5542.436681] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5542.436683] gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[ 5542.436684] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5542.436686] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5542.436687] gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[ 5542.436688] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5542.436690] gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[ 5542.436691] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 5542.436692] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5542.436694] gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[ 5542.436695] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5542.436696] gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[ 5542.436698] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5542.436699] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5542.436700] gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[ 5542.436702] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5542.436703] gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[ 5542.436704] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5542.491797] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5542.491804] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5542.491815] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5542.491818] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.491820] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.491823] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.491825] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.491828] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5542.491830] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.491832] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.491834] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.491836] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.491839] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5542.491841] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.491843] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.491845] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.491847] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.491850] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5542.491852] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.491854] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.491856] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.491858] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.491935] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5542.491938] gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[ 5542.491940] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5542.491942] gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[ 5542.491944] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5542.491946] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5542.491948] gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[ 5542.491950] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5542.491952] gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[ 5542.491954] gl860: VIDIOC_TRY_FMTs << BA81 [1600x1200]
[ 5542.491956] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5542.491957] gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[ 5542.491959] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5542.491961] gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[ 5542.491963] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5542.491965] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5542.491967] gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[ 5542.491969] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5542.491971] gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[ 5542.491973] gl860: VIDIOC_TRY_FMTs << GBRG [1600x1200]
[ 5542.491981] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5542.491983] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5542.491986] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.491988] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.491990] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.491992] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.493024] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5542.493027] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.493030] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.493033] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.493035] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.493038] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5542.493041] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.493043] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.493045] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.493048] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.493051] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5542.493053] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5542.493056] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5542.493058] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5542.493061] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5542.493130] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5542.493133] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5542.493136] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5542.493138] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5542.958938] gl860: VIDIOC_TRY_FMTe >> YUYV [384x288]
[ 5542.958942] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5542.958946] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[ 5542.958948] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5543.611220] gl860: Frame buffer overflow (307591/307200)!
[ 5545.247226] gl860: Frame buffer overflow (307905/307200)!
[ 5545.541050] gl860: VIDIOC_TRY_FMTe >> RGB3 [384x288]
[ 5545.541054] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5545.541058] gl860: VIDIOC_TRY_FMTe >> BGR3 [384x288]
[ 5545.541060] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5545.541063] gl860: VIDIOC_TRY_FMTe >> BA81 [384x288]
[ 5545.541065] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5545.541068] gl860: VIDIOC_TRY_FMTe >> GBRG [384x288]
[ 5545.541070] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5545.541076] gl860: VIDIOC_S_FMTe >> BA81 [640x480]
[ 5545.577036] gl860: VIDIOC_S_FMTs << BA81 [640x480]
[ 5547.856219] gl860: Frame buffer overflow (307422/307200)!
[ 5568.134316] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5568.134340] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5568.134345] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5568.134348] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5568.134351] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5568.134355] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5568.134358] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5568.134361] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5568.134364] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5568.134367] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5568.134370] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5568.134373] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5568.134376] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5568.134379] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5568.134382] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5568.134385] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5568.134388] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5568.134391] gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[ 5568.134393] gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[ 5568.134396] gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x1024]
[ 5568.134399] gl860: VIDIOC_ENUM_FRAMESIZES : 3=[1600x1200]
[ 5568.134517] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5568.134520] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5568.134523] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5568.134525] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5568.558562] gl860: VIDIOC_TRY_FMTe >> YUYV [384x288]
[ 5568.558566] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5568.558570] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[ 5568.558573] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5570.839219] gl860: Frame buffer overflow (308480/307200)!
[ 5571.140054] gl860: VIDIOC_TRY_FMTe >> RGB3 [384x288]
[ 5571.140058] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5571.140062] gl860: VIDIOC_TRY_FMTe >> BGR3 [384x288]
[ 5571.140064] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5571.140067] gl860: VIDIOC_TRY_FMTe >> BA81 [384x288]
[ 5571.140069] gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[ 5571.140072] gl860: VIDIOC_TRY_FMTe >> GBRG [384x288]
[ 5571.140074] gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[ 5571.140080] gl860: VIDIOC_S_FMTe >> BA81 [640x480]
[ 5571.176033] gl860: VIDIOC_S_FMTs << BA81 [640x480]
[ 5573.459220] gl860: Frame buffer overflow (308313/307200)!
[ 5615.289733] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5615.289869] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5615.289903] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5615.289906] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5615.289909] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5615.289927] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5615.289930] gl860: VIDIOC_S_FMTe >> RGB3 [640x480]
[ 5615.289933] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5617.627234] gl860: Frame buffer overflow (308480/307200)!
[ 5617.940064] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5617.940073] gl860: VIDIOC_S_FMTe >> RGB3 [640x480]
[ 5617.976035] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5620.271234] gl860: Frame buffer overflow (307432/307200)!
[ 5620.561099] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5620.561103] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[ 5620.597049] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5622.888229] gl860: Frame buffer overflow (308480/307200)!
[ 5623.180047] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5623.180053] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[ 5623.216040] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5625.543234] gl860: Frame buffer overflow (307840/307200)!
[ 5625.848077] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5625.848094] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5625.848097] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5679.754442] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5679.754584] gl860: VIDIOC_ENUM_FMT : 0=GBRG
[ 5679.790305] gl860: VIDIOC_ENUM_FMT : 1=BA81
[ 5679.790310] gl860: VIDIOC_ENUM_FMT : 2=RGB3
[ 5679.790314] gl860: VIDIOC_ENUM_FMT : 3=BGR3
[ 5679.790337] gl860: VIDIOC_G_FMT : RGB3 [640x480]
[ 5679.790340] gl860: VIDIOC_S_FMTe >> RGB3 [640x480]
[ 5679.790344] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5682.101229] gl860: Frame buffer overflow (307590/307200)!
[ 5682.393292] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5682.393301] gl860: VIDIOC_S_FMTe >> RGB3 [640x480]
[ 5682.436038] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5684.707232] gl860: Frame buffer overflow (308126/307200)!
[ 5684.992104] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5684.992109] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[ 5685.028036] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5687.319244] gl860: Frame buffer overflow (308480/307200)!
[ 5687.612047] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5687.612053] gl860: VIDIOC_S_FMTe >> GBRG [640x480]
[ 5687.648035] gl860: VIDIOC_S_FMTs << GBRG [640x480]
[ 5689.967237] gl860: Frame buffer overflow (308480/307200)!
[ 5690.260084] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5690.260094] gl860: VIDIOC_G_FMT : GBRG [640x480]
[ 5690.260097] gl860: VIDIOC_G_FMT : GBRG [640x480]

---

### Post by nol_faich on 2009-01-30
Rethanks, it would rather have better I check this forum before my mail :(.


*** IMPORTANT ***

@all : Does anyone is using the "sim" version (dmesg | grep "gl860.*ersion" to know that).
I need tests with that driver version. There is some chance we can identify automatically the driver to use and no more asking if you are 1,3 ou 2MP.

---

### Post by BUGabundo on 2009-01-30
$ dmesg | grep "gl860.*ersion"
[   21.792832] gl860: Version Hulkie/Iceman/Soro (c)

2.0MPx

about flash, it failed
will try webcam streaming after lunch.

last time i tried it, i got a memory leak, and had to kill -9 it

---

### Post by nol_faich on 2009-01-30
Which flash version? (<=9 needs LD_PRELOAD, 10 needs nothing (in firefox: about:plugins))

---

### Post by BUGabundo on 2009-01-30
version 10...
from labs.adobe.com 
its the 64 bits version
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)


Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by BUGabundo on 2009-01-30
as soon as i check [http://localhost:65005/](http://localhost:65005/)
I get a memory leak on webcam-server -p 65005

 9483  17104      0         30K 678.8M 588.2M 65536K 68416K  15% webcam-server

---

### Post by nol_faich on 2009-01-30
The test driver version for libv4l enables traces in the syslog (= dmesg).
Can you make tests for flash and your webcam server.
I need the dmesg | grep gl860 with well identified traces sections for flash and the webcam sever.

Do you test the webcam server with LD_PRELOAD?

---

### Post by BUGabundo on 2009-01-30
> **nol_faich said:**
> Do you test the webcam server with LD_PRELOAD?

no i didnt.





/me is thinking of going back to old driver! plain v4l2 worked so well! flash OK, webcam-server OK, cheese OK... lolol see the trend here?

do we really need v4l?

---

### Post by nol_faich on 2009-01-30
I understand you.

Libv4l is a good thing because a driver shall not decode an image and an application shall not handle every image format and make basic operations (rotation, resizing for example) on it by itself. A layer between the driver and the application eases the developpment of the drivers and the applications.

However, application are quite a big mess and libv4l is in developpement and not fully working so there is a lot of issues (and I don't include the v4l1 applications needing the LD_PRELOAD!).
Theoretically, the driver should say it supports only the bayer image format from the sensor but in order to be working with some applications, I need to add another bayer scheme support and tell I support RGB24/BGR24 which is false. Also I tell to applications that I'm defaulted to BGR24 because camorama does not request any image format and refuse all other image formats. So I'm telling it I'm in BGR24 and it is happy and requests images.

The gl860 using libv4l is actually only a test version and is not intended to be the main release until it is fully functional.

To have your traces with your webcam server and flash would be helpful for me.

---

### Post by soro2005 on 2009-01-30
> **nol_faich said:**
> 
To have your traces with your webcam server and flash would be helpful for me.

I'm also using the 64bit version of the Flash player, and it comes out just as a black window. Blue light on. Trace attached. Cheese and Skype work nicely, Camorama displays one row of three small gray images. This is with libv4l_0.5.8a.

---

### Post by nol_faich on 2009-01-31
Thanks Soro!
It seems to me that the issue with Flash is that it refuses images not in the size and format it requested.
Flash is OK with RGB 640x480, Bayer GBRG 160x120 and Bayer GBRG 320x240.
The driver feeds applications and libv4l only with Bayer GBRG or BGGR 640x480.
I'm wondering why the libv4l didn't convert Bayer to RGB and tell to Flash it is RGB as Flash requested.
With camorama, it is a mising LD_PRELOAD.

---

### Post by BUGabundo on 2009-01-31
trace from webcam-server

---

### Post by BUGabundo on 2009-01-31
$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so webcam-server -p 65005

---

### Post by nol_faich on 2009-02-02
About the gl860 with libv4l, if an application makes use of VIDIOCGWIN or VIDIOCSPICT according to the dmesg, that means the application is using V4L1 and needs to be launched with the 'LD_PRELOAD=... application'.
Such traces look like that:
gl860: VIDIOCGWIN : (x,y)=(0,0) [640x480] Flags=X
gl860: VIDIOCSPICT : palette=X (r24=4 r32=5 uy=9 yu=8)

---

### Post by nol_faich on 2009-02-03
@all (new test for ALL flavors)

Could you test [http://downloads.sourceforge.net/gl860/gl860_test4.tgz?use_mirror=](http://downloads.sourceforge.net/gl860/gl860_test4.tgz?use_mirror=) ?

Install it : ./install
Try to see an image, if OK this driver sets properly automatically the flavour to use. 
Please report the result of 'dmesg| grep gl860'.

---

### Post by soro2005 on 2009-02-03
> **nol_faich said:**
> @all (new test for ALL flavors)

Could you test [http://downloads.sourceforge.net/gl860/gl860_test4.tgz?use_mirror=](http://downloads.sourceforge.net/gl860/gl860_test4.tgz?use_mirror=) ?

Install it : ./install
Try to see an image, if OK this driver sets properly automatically the flavour to use. If the driver flavour is not good, I need to know which one you need and the 'dmesg| grep gl860'.

Works here! But I'm sure that's not really a surprise for you. :D

Btw.: I lately get relatively many starts with the image turned upside down. Mainly in Skype. In Cheese, the image often starts upside down and then quickly flips over.

Talking about ~20% of the starts in Skype, perhaps less. It's not a problem b/c I just shut down the image and start it again, and that normally works. Just so you know.

---

### Post by nol_faich on 2009-02-04
Is it only for that test version? I know I need to clean it from some tests and add more comments to the install, but i don't think there is a relation with upsidedowness.

---

### Post by soro2005 on 2009-02-04
No, it's not only for the test version. It's been doing it on occasion since Ubuntu Intrepid or longer. But lately, it happens a little more often here. I actually think that the frequency has to do with something other than the driver. But perhaps there's a delay or something that could be increased a little. Don't know whether others have the same issue...

---

### Post by nol_faich on 2009-02-06
If I remember this issue was previously solved by delaying the beginning of the setting initialisation sequence. Maybe it is to delay of 1-2 images. I cannot look at that yet. If you want to, this must done at the end of gl860-dev.c (if _0503HS_ or _0503A_ then if an image counter is higher (or equal?) to smth then the setting initialisation function in gl860-dev-0503his.c is called).

---

### Post by BUGabundo on 2009-02-06
Where is what I already sent to nol


Cheese works okay. image seem a bit slow when on video. webcam flip 180º isnt detected
camorama  only works with $ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so and the image is fliped!

VLC: i couldnt make it open the webcam, both with v4l and v4l2
It would seem that it locks the device, and wont let go, or show anything

webcam-server works with PRELOAD too


Skype doesnt enable the webcam with and without PRELOAD

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
Skype V4L2: Could not find a suitable capture format
Skype V4L2: Could not find a suitable capture format
Starting the process...
Skype Xv: Xv ports available: 31
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 281
Skype Xv: No suitable overlay format found
Aborted (core dumped)


dmesg after drive install:
Feb  4 18:04:16 blubug kernel: [25666.756025] usb 2-2: new low speed USB device using uhci_hcd and address 2
Feb  4 18:04:16 blubug kernel: [25666.967017] usb 2-2: configuration #1 chosen from 1 choice
Feb  4 18:04:17 blubug kernel: [25667.401341] usbcore: registered new interface driver hiddev
Feb  4 18:04:17 blubug kernel: [25667.414256] input: HID 062a:0001 as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input9
Feb  4 18:04:17 blubug kernel: [25667.440062] generic-usb 0003:062A:0001.0001: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:1a.1-2/input0
Feb  4 18:04:17 blubug kernel: [25667.440076] usbcore: registered new interface driver usbhid
Feb  4 18:04:17 blubug kernel: [25667.440078] usbhid: v2.6:USB HID core driver
Feb  4 18:04:53 blubug kernel: [25704.364046] gl860: usb_gl860_exit: Genesys USB2.0 webcam driver shutdown
Feb  4 18:04:53 blubug kernel: [25704.364051] usbcore: deregistering interface driver usb_gl860_driver
Feb  4 18:04:53 blubug kernel: [25704.364077] gl860: Genesys USB2.0 Camera disconnected
Feb  4 18:04:53 blubug kernel: [25704.364093] gl860: Genesys USB2.0 Camera release resources video device /dev/video0
Feb  4 18:04:53 blubug kernel: [25704.413346] Linux video capture interface: v2.00
Feb  4 18:04:53 blubug kernel: [25704.415845] gl860: Genesys USB2.0 webcam driver startup
Feb  4 18:04:53 blubug kernel: [25704.415867] gl860: Release: 0103
Feb  4 18:04:53 blubug kernel: [25704.415869] gl860: Number of interfaces : 1
Feb  4 18:04:53 blubug kernel: [25704.415870] gl860: Version Hulkie/Iceman/Soro (c)
Feb  4 18:04:53 blubug kernel: [25704.415871] gl860: Genesys USB2.0 - GL860 based webcam found.
Feb  4 18:04:53 blubug kernel: [25704.415872] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
Feb  4 18:04:55 blubug kernel: [25706.428131] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
Feb  4 18:04:55 blubug kernel: [25706.428186] usbcore: registered new interface driver usb_gl860_driver
Feb  4 18:04:55 blubug kernel: [25706.428191] gl860: v0.4.0 : Genesys gl860 USB Video Camera

---

### Post by BUGabundo on 2009-02-06
Here is nol reply



> Cheese works okay. image seem a bit slow when on video. webcam flip 180º isnt
> detected
The flip detection need you to patch the libv4l with the patch included in the
tarball. No image decoding means also no returning when needed. This patch is
one of the two solutions tried for this with the libv4l maintainer.


> camorama  only works with $ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so and the
> image is fliped!
?????????????????????????????????????
The image is flipped ???? You mean flipped and with good colors (camorama swaps
the red and blue but when the image is upside down, red and blue are also
swapped so that swapping from swapped red and blue make the color be correct).


> VLC: i couldnt make it open the webcam, both with v4l and v4l2
> It would seem that it locks the device, and wont let go, or show anything
> Only work in v4l1. They use f***ing alias for colorspace. The command line in
the README is ok for me with the preload.


> Skype doesnt enable the webcam with and without PRELOAD
Skype is v4l2 (so no preload and I have no trouble with it). To help to
understand the issue, the dmesg is important as I trace in it the image format
negociation.

I looked at the Xwatv code, but it is quite more hard than the one of VLC and I
still don't understand whait is wrong with it.

---

### Post by BUGabundo on 2009-02-06
> **BUGabundo said:**
> 
The flip detection need you to patch the libv4l with the patch included in the
tarball. No image decoding means also no returning when needed. This patch is
one of the two solutions tried for this with the libv4l maintainer.


I'll be needing a bit more help doing this, ok?


> **BUGabundo said:**
> 
> camorama  only works with $ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so and the
> image is fliped!
?????????????????????????????????????
The image is flipped ???? You mean flipped and with good colors (camorama swaps
the red and blue but when the image is upside down, red and blue are also
swapped so that swapping from swapped red and blue make the color be correct).


Its vertically flipped (aka upsidedown)


> **BUGabundo said:**
> 
> VLC: i couldnt make it open the webcam, both with v4l and v4l2
> It would seem that it locks the device, and wont let go, or show anything
> Only work in v4l1. They use f***ing alias for colorspace. The command line in
the README is ok for me with the preload.



> **BUGabundo said:**
> 
> Skype doesnt enable the webcam with and without PRELOAD
Skype is v4l2 (so no preload and I have no trouble with it).
Well, Skype mention it detects a webcam, but once I test it, I just get a black window.

---

### Post by nol_faich on 2009-02-06
Flip detection : download libv4l sources (link in the README file), untar the sources, go to the directory where libv4l sources are installed in (=not in the libv4l directory, but its parent).
patch -p0 < path/to/webcam/driver/sources/file.diff
You compile the sources of libv4l just they tell in its README

Skype : dmesg | grep gl860. All image format/size requests are logged, these traces are mandatory to understand why an application this does not work. Also launch Skype in command line, it can print out some usefull error message.

---

### Post by BUGabundo on 2009-02-06
€ (7*$) skype
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
Skype V4L2: Could not find a suitable capture format
Skype V4L2: Could not find a suitable capture format
Starting the process...
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280
Skype Xv: No suitable overlay format found
Aborted (core dumped)



[   18.228114] gl860: Genesys USB2.0 webcam driver startup
[   18.228212] gl860: Release: 0103
[   18.228285] gl860: Number of interfaces : 1
[   18.228363] gl860: Version Hulkie/Iceman/Soro (c)
[   18.228441] gl860: Genesys USB2.0 - GL860 based webcam found.
[   18.228521] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[   20.108185] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[   20.108295] usbcore: registered new interface driver usb_gl860_driver
[   20.108378] gl860: v0.4.0 : Genesys gl860 USB Video Camera
[17061.200047] gl860: Genesys USB2.0 Camera disconnected
[17061.200066] gl860: Genesys USB2.0 Camera release resources video device /dev/video0
[17069.202191] gl860: Release: 0103
[17069.202192] gl860: Number of interfaces : 1
[17069.202193] gl860: Version Hulkie/Iceman/Soro (c)
[17069.202194] gl860: Genesys USB2.0 - GL860 based webcam found.
[17069.202195] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[17071.044075] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[17071.044240] Modules linked in: usbhid nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc acpi_cpufreq xfs coretemp sbp2 ppdev parport_pc lp parport joydev pcspkr psmouse serio_raw arc4 sdhci_pci sdhci ecb ricoh_mmc iTCO_wdt iTCO_vendor_support gl860 compat_ioctl32 videodev v4l1_compat iwlagn iwlcore lbm_cw_mac80211 btusb lbm_cw_cfg80211 snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc nvidia(P) video output asus_laptop led_class intel_agp ohci1394 ieee1394 sky2 ehci_hcd uhci_hcd fbcon tileblit font bitblit softcursor fuse
[17096.464473] gl860: Genesys USB2.0 Camera disconnected
[17096.464485] gl860: Genesys USB2.0 Camera release resources video device /dev/video0
[17099.996246] gl860: Release: 0103
[17099.996247] gl860: Number of interfaces : 1
[17099.996249] gl860: Version Hulkie/Iceman/Soro (c)
[17099.996249] gl860: Genesys USB2.0 - GL860 based webcam found.
[17099.996251] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[17101.844068] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[27109.910829] gl860: VIDIOC_S_FMTe >> YU12 [320x240]
[27109.910834] gl860: VIDIOC_S_FMTs << refusé
[27109.910838] gl860: VIDIOC_S_FMTe >> YUYV [320x240]
[27109.910841] gl860: VIDIOC_S_FMTs << refusé
[27109.910844] gl860: VIDIOC_S_FMTe >> UYVY [320x240]
[27109.910846] gl860: VIDIOC_S_FMTs << refusé
[27109.910849] gl860: VIDIOC_S_FMTe >> YU12 [320x240]
[27109.910852] gl860: VIDIOC_S_FMTs << refusé
[27109.910854] gl860: VIDIOC_S_FMTe >> YU12 [324x248]
[27109.910857] gl860: VIDIOC_S_FMTs << refusé
[27109.910859] gl860: VIDIOC_S_FMTe >> YU12 [352x288]
[27109.910861] gl860: VIDIOC_S_FMTs << refusé
[27109.910864] gl860: VIDIOC_S_FMTe >> YU12 [160x120]
[27109.910866] gl860: VIDIOC_S_FMTs << refusé
[27109.910869] gl860: VIDIOC_S_FMTe >> YU12 [176x144]
[27109.910871] gl860: VIDIOC_S_FMTs << refusé
[27109.910874] gl860: VIDIOC_S_FMTe >> YU12 [640x480]
[27109.910876] gl860: VIDIOC_S_FMTs << refusé
[27109.910879] gl860: VIDIOC_S_FMTe >> YU12 [1024x576]
[27109.910881] gl860: VIDIOC_S_FMTs << refusé
[27109.910884] gl860: VIDIOC_S_FMTe >> YUYV [320x240]
[27109.910886] gl860: VIDIOC_S_FMTs << refusé
[27109.910889] gl860: VIDIOC_S_FMTe >> YUYV [324x248]
[27109.910891] gl860: VIDIOC_S_FMTs << refusé
[27109.910894] gl860: VIDIOC_S_FMTe >> YUYV [352x288]
[27109.910896] gl860: VIDIOC_S_FMTs << refusé
[27109.910899] gl860: VIDIOC_S_FMTe >> YUYV [160x120]
[27109.910901] gl860: VIDIOC_S_FMTs << refusé
[27109.910904] gl860: VIDIOC_S_FMTe >> YUYV [176x144]
[27109.910906] gl860: VIDIOC_S_FMTs << refusé
[27109.910909] gl860: VIDIOC_S_FMTe >> YUYV [640x480]
[27109.910911] gl860: VIDIOC_S_FMTs << refusé
[27109.910914] gl860: VIDIOC_S_FMTe >> YUYV [1024x576]
[27109.910916] gl860: VIDIOC_S_FMTs << refusé
[27109.910919] gl860: VIDIOC_S_FMTe >> UYVY [320x240]
[27109.910921] gl860: VIDIOC_S_FMTs << refusé
[27109.910924] gl860: VIDIOC_S_FMTe >> UYVY [324x248]
[27109.910926] gl860: VIDIOC_S_FMTs << refusé
[27109.910928] gl860: VIDIOC_S_FMTe >> UYVY [352x288]
[27109.910931] gl860: VIDIOC_S_FMTs << refusé
[27109.910933] gl860: VIDIOC_S_FMTe >> UYVY [160x120]
[27109.910936] gl860: VIDIOC_S_FMTs << refusé
[27109.910938] gl860: VIDIOC_S_FMTe >> UYVY [176x144]
[27109.910940] gl860: VIDIOC_S_FMTs << refusé
[27109.910943] gl860: VIDIOC_S_FMTe >> UYVY [640x480]
[27109.910945] gl860: VIDIOC_S_FMTs << refusé
[27109.910948] gl860: VIDIOC_S_FMTe >> UYVY [1024x576]
[27109.910950] gl860: VIDIOC_S_FMTs << refusé

---

### Post by nol_faich on 2009-02-06
Here is my sequence with Skype 2.0.0.72.

[  237.185902] Genesys gl860: VIDIOC_G_FMT : RGB3 [640x480]
[  237.186021] Genesys gl860: VIDIOC_G_FMT : RGB3 [640x480]
[  237.186099] Genesys gl860: VIDIOC_ENUM_FMT : 0=GBRG
[  237.186104] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  237.186108] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  237.186112] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  237.186116] Genesys gl860: VIDIOC_ENUM_FMT : 1=BA81
[  237.186118] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  237.186122] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  237.186125] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  237.186128] Genesys gl860: VIDIOC_ENUM_FMT : 2=RGB3
[  237.186131] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  237.186135] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  237.186138] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  237.186141] Genesys gl860: VIDIOC_ENUM_FMT : 3=BGR3
[  237.186144] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  237.186147] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  237.186151] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  237.186320] Genesys gl860: VIDIOC_ENUM_FMT : 0=GBRG
[  237.186323] Genesys gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[  237.186326] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  237.186329] Genesys gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[  237.186332] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [1280x960]
[  237.186335] Genesys gl860: VIDIOC_ENUM_FMT : 1=BA81
[  237.186338] Genesys gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[  237.186341] Genesys gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[  237.186344] Genesys gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[  237.186348] Genesys gl860: VIDIOC_TRY_FMTs << BA81 [1280x960]
[  237.186351] Genesys gl860: VIDIOC_ENUM_FMT : 2=RGB3
[  237.186353] Genesys gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[  237.186356] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  237.186359] Genesys gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[  237.186362] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [1280x960]
[  237.186366] Genesys gl860: VIDIOC_ENUM_FMT : 3=BGR3
[  237.186368] Genesys gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[  237.186371] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  237.186375] Genesys gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[  237.186378] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [1280x960]
[  248.850689] Genesys gl860: VIDIOC_G_FMT : RGB3 [640x480]
[  248.852244] Genesys gl860: VIDIOC_G_FMT : RGB3 [640x480]
[  248.853460] Genesys gl860: VIDIOC_ENUM_FMT : 0=GBRG
[  248.854891] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  248.856109] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  248.857303] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  248.858511] Genesys gl860: VIDIOC_ENUM_FMT : 1=BA81
[  248.859504] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  248.860714] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  248.861906] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  248.863103] Genesys gl860: VIDIOC_ENUM_FMT : 2=RGB3
[  248.864122] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  248.865302] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  248.866481] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  248.867221] Genesys gl860: VIDIOC_ENUM_FMT : 3=BGR3
[  248.867956] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 0=[640x480]
[  248.869177] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 1=[800x600]
[  248.870362] Genesys gl860: VIDIOC_ENUM_FRAMESIZES : 2=[1280x960]
[  248.871652] Genesys gl860: VIDIOC_ENUM_FMT : 0=GBRG
[  248.872756] Genesys gl860: VIDIOC_TRY_FMTe >> GBRG [48x32]
[  248.872769] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.875037] Genesys gl860: VIDIOC_TRY_FMTe >> GBRG [100000x100000]
[  248.875048] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [1280x960]
[  248.877458] Genesys gl860: VIDIOC_ENUM_FMT : 1=BA81
[  248.878461] Genesys gl860: VIDIOC_TRY_FMTe >> BA81 [48x32]
[  248.878471] Genesys gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[  248.880719] Genesys gl860: VIDIOC_TRY_FMTe >> BA81 [100000x100000]
[  248.880729] Genesys gl860: VIDIOC_TRY_FMTs << BA81 [1280x960]
[  248.883133] Genesys gl860: VIDIOC_ENUM_FMT : 2=RGB3
[  248.884200] Genesys gl860: VIDIOC_TRY_FMTe >> RGB3 [48x32]
[  248.884211] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.886444] Genesys gl860: VIDIOC_TRY_FMTe >> RGB3 [100000x100000]
[  248.886454] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [1280x960]
[  248.888836] Genesys gl860: VIDIOC_ENUM_FMT : 3=BGR3
[  248.889842] Genesys gl860: VIDIOC_TRY_FMTe >> BGR3 [48x32]
[  248.889852] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.892084] Genesys gl860: VIDIOC_TRY_FMTe >> BGR3 [100000x100000]
[  248.892094] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [1280x960]
[  248.894531] Genesys gl860: VIDIOC_TRY_FMTe >> RGB3 [320x240]
[  248.894542] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.896577] Genesys gl860: VIDIOC_TRY_FMTe >> BGR3 [320x240]
[  248.896582] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.897628] Genesys gl860: VIDIOC_TRY_FMTe >> BA81 [320x240]
[  248.897633] Genesys gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[  248.898674] Genesys gl860: VIDIOC_TRY_FMTe >> GBRG [320x240]
[  248.898678] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.899716] Genesys gl860: VIDIOC_TRY_FMTe >> RGB3 [361x297]
[  248.899721] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.900783] Genesys gl860: VIDIOC_TRY_FMTe >> BGR3 [361x297]
[  248.900788] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.901829] Genesys gl860: VIDIOC_TRY_FMTe >> BA81 [361x297]
[  248.901834] Genesys gl860: VIDIOC_TRY_FMTs << BA81 [640x480]
[  248.902864] Genesys gl860: VIDIOC_TRY_FMTe >> GBRG [361x297]
[  248.902869] Genesys gl860: VIDIOC_TRY_FMTs << GBRG [640x480]
[  248.902875] Genesys gl860: VIDIOC_S_FMTe >> BA81 [640x480]
[  248.902879] Genesys gl860: VIDIOC_S_FMTs << BA81 [640x480]

Your Skype does not ask for which format the driver support and try a bunch of non supported formats in a such a way that at the end of negociation sequence not any things were accepted by the driver and no images are seen.
Which version Skype are you using?

---

### Post by BUGabundo on 2009-02-06
> **nol_faich said:**
> Which version Skype are you using?

$ apt-cache policy skype
skype:
  Installed: 2.0.0.72-1
  Candidate: 2.0.0.72-1
  Version table:
 *** 2.0.0.72-1 0
        100 /var/lib/dpkg/status
     2.0.0.72-0medibuntu4 0
        500 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages

---

### Post by nol_faich on 2009-02-06
2.0.0.72-0medibuntu4 also on my laptop but the installed version is also this one, not a 2.0.0.72-1 as you.
This is quite crazy that such a small difference make Skype to work or not. Morevoer my Skype is getting images in Bayer BA81 although your Skype does not request for such an image format.
Which libv4l are you using, maybe it plays a far more active role than what I thought? (me: libv4l-0.5.8)

---

### Post by BUGabundo on 2009-02-06
> **nol_faich said:**
> 
Which libv4l are you using, maybe it plays a far more active role than what I thought? (me: libv4l-0.5.8)

$ apt-cache policy libv4l-0
libv4l-0:
  Installed: 0.5.8-1
  Candidate: 0.5.8-1
  Version table:
 *** 0.5.8-1 0
        500 [ftp://darkstar.ist.utl.pt](ftp://darkstar.ist.utl.pt) jaunty/main Packages
        500 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status

---

### Post by nol_faich on 2009-02-07
The different ways used by applications to negociate their image format and size, besides the difference between 32bits and 64bits are really boring.

Instead of trying to get all applications working with the help of libv4l, I will rather work on a merged driver (2.6.26+2.6.27+libv4l) including with the automatical sensor (then driver version) detection. The default behaviour will be "without libv4l". Libv4l will be an option.
This, there is only one driver and one can choose whether it uses libv4l to reduce the kernel load or not.

---

### Post by BUGabundo on 2009-02-07
> **nol_faich said:**
> I will rather work on a merged driver (2.6.26+2.6.27+libv4l) including with the automatical sensor (then driver version) detection.

dont forget 2.6.28 and .29

> **nol_faich said:**
>  The default behaviour will be "without libv4l". Libv4l will be an option.
This, there is only one driver and one can choose whether it uses libv4l to reduce the kernel load or not.
For me is as good. i dont seem to need it... 
since it works, and u dont have as much work, its fine for me.

Thanks

---

### Post by nol_faich on 2009-02-08
"2.6.27" is a bad name as the driver is OK for 2.6.28. With only one release, it is no more usefull to name it after the kernel version.

However without libv4l I got two system freezes with aMSN today so I think the driver will be defaulted to use libv4l.

---

### Post by macogw on 2009-02-09
The new one works great for photos in Cheese, but for videos...about 3 (random) seconds of the 15-20 seconds that I had it on were caught.  And it started upside down.  Getting it initialized to video mode also seemed to require quite a long time of staring at solid black output.

---

### Post by nol_faich on 2009-02-09
Hi!
Do the upside down images have red and blue swapped?
About the video, this is managed by Cheese, not the driver. If you are using Cheese in the biggest size (the default one for Cheese), it needs some seconds to be initialized. Also the framerate can be low (<10fps) in poorly lit condition, so a too high framerate and less images than expected may lead to a shortened video.
I'm not a fan of Cheese, I find it to slow and I have a screen refreshing issue when I change a setting.

---

### Post by nol_faich on 2009-02-10
I changed the delay between each USB commands sent, does this solve for upside down issue?

Driver is here: [http://downloads.sourceforge.net/gl860/gl860_2.6.27c.tgz?use_mirror=](http://downloads.sourceforge.net/gl860/gl860_2.6.27c.tgz?use_mirror=)

---

### Post by BUGabundo on 2009-02-16
just in case this is useful for comparation to anyone

$ v4l-info 
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "gl860"
	card                    : "Genesys gl860 USB Video Camera"
	bus_info                : "usb-0000:00:1d.7-6"
	version                 : 0.3.0
	capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards
    VIDIOC_ENUMSTD(0)
	index                   : 0
	id                      : 0x0 []
	name                    : "webcam"
	frameperiod.numerator   : 0
	frameperiod.denominator : 0
	framelines              : 0

inputs
    VIDIOC_ENUMINPUT(0)
	index                   : 0
	name                    : "USB"
	type                    : CAMERA
	audioset                : 0
	tuner                   : 0
	std                     : 0x0 []
	status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
	index                   : 0
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "uyvy"
	pixelformat             : 0x59565955 [UYVY]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
	index                   : 1
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "yuyv"
	pixelformat             : 0x56595559 [YUYV]
    VIDIOC_ENUM_FMT(2,VIDEO_CAPTURE)
	index                   : 2
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "rgb8"
	pixelformat             : 0x20203859 [Y8  ]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
	type                    : VIDEO_CAPTURE
	fmt.pix.width           : 640
	fmt.pix.height          : 480
	fmt.pix.pixelformat     : 0x33424752 [RGB3]
	fmt.pix.field           : NONE
	fmt.pix.bytesperline    : 1920
	fmt.pix.sizeimage       : 921600
	fmt.pix.colorspace      : SRGB
	fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
	id                      : 9963776
	type                    : INTEGER
	name                    : "Brightness"
	minimum                 : 0
	maximum                 : 65280
	step                    : 1
	default_value           : 0
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
	id                      : 9963777
	type                    : INTEGER
	name                    : "Contrast"
	minimum                 : 0
	maximum                 : 65280
	step                    : 1
	default_value           : 32512
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
	id                      : 9963778
	type                    : INTEGER
	name                    : "Saturation"
	minimum                 : 0
	maximum                 : 65280
	step                    : 1
	default_value           : 65280
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+3)
	id                      : 9963779
	type                    : INTEGER
	name                    : "Palette"
	minimum                 : 0
	maximum                 : 65280
	step                    : 1
	default_value           : 0
	flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+0)
	id                      : 134217728
	type                    : INTEGER
	name                    : "Light Source"
	minimum                 : 0
	maximum                 : 2
	step                    : 1
	default_value           : 0
	flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "gl860"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 1600
	maxheight               : 1200
	minwidth                : 80
	minheight               : 60

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "Webcam"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 35840
	hue                     : 0
	colour                  : 39321
	contrast                : 0
	whiteness               : 0
	depth                   : 24
	palette                 : RGB24

buffer
    VIDIOCGFBUF
	base                    : (nil)
	height                  : 0
	width                   : 0
	depth                   : 0
	bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 640
	y                       : 640
	width                   : 640
	height                  : 480
	chromakey               : 0
	flags                   : 0


$ v4l-conf 
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1280x800, depth=24, bpp=32, bpl=5120, base=unknown
/dev/video0 [v4l2]: no overlay support

---

### Post by BUGabundo on 2009-02-17
i suspect the new driver is breaking my hibernate

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329254](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329254)


Feb 17 01:17:00 blubug kernel: [15006.664032] usb 6-6: reset high speed USB device using ehci_hcd and address 3
Feb 17 01:17:00 blubug kernel: [15006.920029] usb 7-1: reset full speed USB device using uhci_hcd and address 2
Feb 17 01:17:00 blubug kernel: [15007.252030] usb 1-1: reset full speed USB device using uhci_hcd and address 2
Feb 17 01:17:00 blubug kernel: [15007.407241] gl860: Release: 0103
Feb 17 01:17:00 blubug kernel: [15007.407242] gl860: Number of interfaces : 1
Feb 17 01:17:00 blubug kernel: [15007.407243] gl860: Forcage du pilote
Feb 17 01:17:00 blubug kernel: [15007.407245] gl860: Version Hulkie/Iceman/Soro (c)
Feb 17 01:17:00 blubug kernel: [15007.407245] gl860: Genesys USB2.0 - GL860 based webcam found.
Feb 17 01:17:00 blubug kernel: [15007.407246] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
Feb 17 01:17:00 blubug kernel: [15010.424063] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
Feb 17 01:17:00 blubug kernel: [15010.424230] PM: resume devices took 8.112 seconds
Feb 17 01:17:00 blubug kernel: [15010.424235] ------------[ cut here ]------------
Feb 17 01:17:00 blubug kernel: [15010.424236] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x7c/0x80()
Feb 17 01:17:00 blubug kernel: [15010.424237] Component: resume devices
Feb 17 01:17:00 blubug kernel: [15010.424238] Modules linked in: usbhid nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc acpi_cpufreq input_polldev xfs coretemp sbp2 ppdev parport_pc lp parport joydev psmouse serio_raw ricoh_mmc arc4 ecb sdhci_pci sdhci gl860 compat_ioctl32 videodev v4l1_compat snd_hda_intel snd_pcm_oss snd_mixer_oss btusb iwlagn iwlcore lbm_cw_mac80211 snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device pcspkr iTCO_wdt iTCO_vendor_support lbm_cw_cfg80211 snd soundcore snd_page_alloc nvidia(P) intel_agp video output asus_laptop led_class iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 iptable_mangle iptable_filter ip_tables x_tables ohci1394 ieee1394 sky2 ehci_hcd uhci_hcd fbcon tileblit font bitblit softcursor fuse
Feb 17 01:17:00 blubug kernel: [15010.424272] Pid: 15791, comm: s2ram Tainted: P           2.6.28-7-generic #20-Ubuntu
Feb 17 01:17:00 blubug kernel: [15010.424273] Call Trace:
Feb 17 01:17:00 blubug kernel: [15010.424278]  [<ffffffff8024d857>] warn_slowpath+0xb7/0xf0
Feb 17 01:17:00 blubug kernel: [15010.424280]  [<ffffffff8026a368>] ? down_trylock+0x38/0x50
Feb 17 01:17:00 blubug kernel: [15010.424282]  [<ffffffff8024df70>] ? try_acquire_console_sem+0x10/0x40
Feb 17 01:17:00 blubug kernel: [15010.424285]  [<ffffffff802595b6>] ? lock_timer_base+0x36/0x70
Feb 17 01:17:00 blubug kernel: [15010.424288]  [<ffffffff8067f320>] ? printk+0x67/0x6f
Feb 17 01:17:00 blubug kernel: [15010.424291]  [<ffffffff8040baa7>] ? kobject_put+0x27/0x60
Feb 17 01:17:00 blubug kernel: [15010.424295]  [<ffffffff804a96b5>] ? put_device+0x15/0x20
Feb 17 01:17:00 blubug kernel: [15010.424297]  [<ffffffff804b169a>] ? dpm_complete+0x18a/0x1a0
Feb 17 01:17:00 blubug kernel: [15010.424299]  [<ffffffff8027cf1c>] suspend_test_finish+0x7c/0x80
Feb 17 01:17:00 blubug kernel: [15010.424301]  [<ffffffff8027d004>] suspend_devices_and_enter+0xe4/0x180
Feb 17 01:17:00 blubug kernel: [15010.424303]  [<ffffffff8027d2b9>] enter_state+0xe9/0x120
Feb 17 01:17:00 blubug kernel: [15010.424305]  [<ffffffff8027d3aa>] state_store+0xba/0x100
Feb 17 01:17:00 blubug kernel: [15010.424307]  [<ffffffff8040b947>] kobj_attr_store+0x17/0x20
Feb 17 01:17:00 blubug kernel: [15010.424310]  [<ffffffff80344185>] sysfs_write_file+0xc5/0x140
Feb 17 01:17:00 blubug kernel: [15010.424313]  [<ffffffff802e4bfb>] vfs_write+0xcb/0x130
Feb 17 01:17:00 blubug kernel: [15010.424315]  [<ffffffff802e4d50>] sys_write+0x50/0x90
Feb 17 01:17:00 blubug kernel: [15010.424317]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Feb 17 01:17:00 blubug kernel: [15010.424318] ---[ end trace 2db6251bec3c2440 ]---
Feb 17 01:17:00 blubug kernel: [15010.424346] PM: Finishing wakeup.
Feb 17 01:17:00 blubug kernel: [15010.424347] Restarting tasks ... done.
Feb 17 01:17:00 blubug kernel: [15010.729652] sky2 eth0: enabling interface

---

### Post by nol_faich on 2009-02-17
The webcam was active when you start to hibernate?

---

### Post by BUGabundo on 2009-02-17
> **nol_faich said:**
> The webcam was active when you start to hibernate?

nope

---

### Post by nol_faich on 2009-02-17
Can you reproduce the issue?
If yes: unload the driver, hibernate, resume. Is there still the issue? If yes, the driver is not guilty.
I made two hibernations with my 32bits 2.6.27: no error in the dmesg.

---

### Post by BUGabundo on 2009-02-18
i unloaded the driver, rebooted, and then tried it again.
suspend and resume work;
hibernate will fail, and wake in a few sec.

Feb 18 02:26:47 blubug kernel: [21442.513954] PM: Syncing filesystems ... done.
Feb 18 02:26:47 blubug kernel: [21442.589665] PM: Preparing system for mem sleep
Feb 18 02:26:47 blubug kernel: [21442.589669] Freezing user space processes ... (elapsed 0.00 seconds) done.
Feb 18 02:26:47 blubug kernel: [21442.590524] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Feb 18 02:26:47 blubug kernel: [21442.590560] PM: Entering mem sleep
Feb 18 02:26:47 blubug kernel: [21442.590574] Suspending console(s) (use no_console_suspend to debug)
Feb 18 02:26:47 blubug kernel: [21442.696044] gl860: Genesys USB2.0 Camera disconnected
Feb 18 02:26:47 blubug kernel: [21442.696094] gl860: Genesys USB2.0 Camera release resources video device /dev/video0
Feb 18 02:26:47 blubug kernel: [21443.460764] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Feb 18 02:26:47 blubug kernel: [21443.460963] sd 0:0:0:0: [sda] Stopping disk
Feb 18 02:26:47 blubug kernel: [21444.088770] ricoh-mmc: Suspending.
Feb 18 02:26:47 blubug kernel: [21444.088777] ricoh-mmc: Controller is now re-enabled.
Feb 18 02:26:47 blubug kernel: [21444.088822] ACPI handle has no context!
Feb 18 02:26:47 blubug kernel: [21444.088827] sdhci-pci 0000:07:01.1: PCI INT B disabled
Feb 18 02:26:47 blubug kernel: [21444.088831] ACPI handle has no context!
Feb 18 02:26:47 blubug kernel: [21444.109052] ACPI handle has no context!
Feb 18 02:26:47 blubug kernel: [21444.124043] sky2 eth0: disabling interface
Feb 18 02:26:47 blubug kernel: [21444.125464] ACPI handle has no context!
Feb 18 02:26:47 blubug kernel: [21444.125469] ACPI handle has no context!
Feb 18 02:26:47 blubug kernel: [21444.156170] ahci 0000:03:00.0: PCI INT A disabled
Feb 18 02:26:47 blubug kernel: [21444.188074] NVRM: RmPowerManagement: 4
Feb 18 02:26:47 blubug kernel: [21444.332150] ata6: port disabled. ignoring.
Feb 18 02:26:47 blubug kernel: [21444.332195] ata_piix 0000:00:1f.1: PCI INT A disabled
Feb 18 02:26:47 blubug kernel: [21444.332289] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Feb 18 02:26:47 blubug kernel: [21444.348061] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Feb 18 02:26:47 blubug kernel: [21444.348094] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Feb 18 02:26:47 blubug kernel: [21444.348125] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Feb 18 02:26:47 blubug kernel: [21444.380058] HDA Intel 0000:00:1b.0: PCI INT A disabled
Feb 18 02:26:47 blubug kernel: [21444.380108] ACPI handle has no context!
Feb 18 02:26:47 blubug kernel: [21444.396077] ehci_hcd 0000:00:1a.7: PCI INT C disabled
Feb 18 02:26:47 blubug kernel: [21444.412071] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Feb 18 02:26:47 blubug kernel: [21444.412103] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Feb 18 02:26:47 blubug kernel: [21444.412201] PM: suspend devices took 1.824 seconds
Feb 18 02:26:47 blubug kernel: [21444.412555] ACPI: Preparing to enter system sleep state S3
Feb 18 02:26:47 blubug kernel: [21444.413967] Disabling non-boot CPUs ...
Feb 18 02:26:47 blubug kernel: [21444.416361] CPU 1 is now offline
Feb 18 02:26:47 blubug kernel: [21444.416363] SMP alternatives: switching to UP code
Feb 18 02:26:47 blubug kernel: [21444.531273] CPU0 attaching NULL sched-domain.
Feb 18 02:26:47 blubug kernel: [21444.531276] CPU1 attaching NULL sched-domain.
Feb 18 02:26:47 blubug kernel: [21444.536322] CPU0 attaching NULL sched-domain.
Feb 18 02:26:47 blubug kernel: [21444.536511] CPU1 is down
Feb 18 02:26:47 blubug kernel: [21444.536511] Back to C!
Feb 18 02:26:47 blubug kernel: [21444.536511] Enabling non-boot CPUs ...
Feb 18 02:26:47 blubug kernel: [21444.536511] SMP alternatives: switching to SMP code
Feb 18 02:26:47 blubug kernel: [21444.648459] Booting processor 1 APIC 0x1 ip 0x6000
Feb 18 02:26:47 blubug kernel: [21444.531135] Initializing CPU#1
Feb 18 02:26:47 blubug kernel: [21444.531135] Calibrating delay using timer specific routine.. 4788.03 BogoMIPS (lpj=9576076)
Feb 18 02:26:47 blubug kernel: [21444.531135] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 18 02:26:47 blubug kernel: [21444.531135] CPU: L2 cache: 3072K
Feb 18 02:26:47 blubug kernel: [21444.531135] CPU: Physical Processor ID: 0
Feb 18 02:26:47 blubug kernel: [21444.531135] CPU: Processor Core ID: 1
Feb 18 02:26:47 blubug kernel: [21444.736605] CPU1: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
Feb 18 02:26:47 blubug kernel: [21444.736640] CPU0 attaching NULL sched-domain.
Feb 18 02:26:47 blubug kernel: [21444.740014] Switched to high resolution mode on CPU 1
Feb 18 02:26:47 blubug kernel: [21444.752787] CPU0 attaching sched-domain:
Feb 18 02:26:47 blubug kernel: [21444.752789]  domain 0: span 0-1 level MC
Feb 18 02:26:47 blubug kernel: [21444.752791]   groups: 0 1
Feb 18 02:26:47 blubug kernel: [21444.752794] CPU1 attaching sched-domain:
Feb 18 02:26:47 blubug kernel: [21444.752795]  domain 0: span 0-1 level MC
Feb 18 02:26:47 blubug kernel: [21444.752796]   groups: 1 0
Feb 18 02:26:47 blubug kernel: [21444.757012] CPU1 is up
Feb 18 02:26:47 blubug kernel: [21444.757014] ACPI: Waking up from system sleep state S3
Feb 18 02:26:47 blubug kernel: [21444.777831] ACPI: EC: non-query interrupt received, switching to interrupt mode
Feb 18 02:26:47 blubug kernel: [21444.817944] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Feb 18 02:26:47 blubug kernel: [21444.817962] pcieport-driver 0000:00:01.0: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.817972] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 18 02:26:47 blubug kernel: [21444.817975] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.818012] usb usb1: root hub lost power or was reset
Feb 18 02:26:47 blubug kernel: [21444.818046] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 18 02:26:47 blubug kernel: [21444.818049] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.818085] usb usb2: root hub lost power or was reset
Feb 18 02:26:47 blubug kernel: [21444.832032] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb 18 02:26:47 blubug kernel: [21444.832037] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.848061] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100102)
Feb 18 02:26:47 blubug kernel: [21444.848079] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 18 02:26:47 blubug kernel: [21444.848085] HDA Intel 0000:00:1b.0: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944340] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Feb 18 02:26:47 blubug kernel: [21444.944394] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944433] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
Feb 18 02:26:47 blubug kernel: [21444.944450] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
Feb 18 02:26:47 blubug kernel: [21444.944495] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944539] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Feb 18 02:26:47 blubug kernel: [21444.944591] pcieport-driver 0000:00:1c.3: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944623] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x9 (was 0x1fff1, writing 0xd001d001)
Feb 18 02:26:47 blubug kernel: [21444.944639] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Feb 18 02:26:47 blubug kernel: [21444.944689] pcieport-driver 0000:00:1c.4: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944703] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb 18 02:26:47 blubug kernel: [21444.944707] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944759] usb usb3: root hub lost power or was reset
Feb 18 02:26:47 blubug kernel: [21444.944776] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Feb 18 02:26:47 blubug kernel: [21444.944781] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944839] usb usb4: root hub lost power or was reset
Feb 18 02:26:47 blubug kernel: [21444.944855] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb 18 02:26:47 blubug kernel: [21444.944860] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.944913] usb usb5: root hub lost power or was reset
Feb 18 02:26:47 blubug kernel: [21444.960032] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb 18 02:26:47 blubug kernel: [21444.960038] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.960129] pci 0000:00:1e.0: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.960192] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb 18 02:26:47 blubug kernel: [21444.960195] ata_piix 0000:00:1f.1: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.961232] ata6: port disabled. ignoring.
Feb 18 02:26:47 blubug kernel: [21444.976059] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Feb 18 02:26:47 blubug kernel: [21444.976093] ahci 0000:00:1f.2: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21444.976178] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xd0100000)
Feb 18 02:26:47 blubug kernel: [21444.976260] NVRM: RmPowerManagement: 5
Feb 18 02:26:47 blubug kernel: [21445.316071] ata3: SATA link down (SStatus 0 SControl 300)
Feb 18 02:26:47 blubug kernel: [21445.436056] ata2: SATA link down (SStatus 0 SControl 300)
Feb 18 02:26:47 blubug kernel: [21445.672106] ahci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb 18 02:26:47 blubug kernel: [21445.672115] ahci 0000:03:00.0: setting latency timer to 64
Feb 18 02:26:47 blubug kernel: [21445.705079] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Feb 18 02:26:47 blubug kernel: [21445.705174] sky2 eth0: enabling interface
Feb 18 02:26:47 blubug kernel: [21445.776656] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fbffe800-fbffefff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Feb 18 02:26:47 blubug kernel: [21445.796071] sdhci-pci 0000:07:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 18 02:26:47 blubug kernel: [21445.796075] sdhci-pci 0000:07:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
Feb 18 02:26:47 blubug kernel: [21445.797086] ricoh-mmc: Resuming.
Feb 18 02:26:47 blubug kernel: [21445.797093] ricoh-mmc: Controller is now disabled.
Feb 18 02:26:47 blubug kernel: [21445.797229] sd 0:0:0:0: [sda] Starting disk
Feb 18 02:26:47 blubug kernel: [21446.012043] ata4: SATA link down (SStatus 0 SControl 300)
Feb 18 02:26:47 blubug kernel: [21446.228356] ata5.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Feb 18 02:26:47 blubug kernel: [21446.228358] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Feb 18 02:26:47 blubug kernel: [21446.260293] ata5.00: configured for UDMA/33
Feb 18 02:26:47 blubug kernel: [21448.048034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 18 02:26:47 blubug kernel: [21448.054086] ata1.00: configured for UDMA/133
Feb 18 02:26:47 blubug kernel: [21448.068088] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Feb 18 02:26:47 blubug kernel: [21448.068115] sd 0:0:0:0: [sda] Write Protect is off
Feb 18 02:26:47 blubug kernel: [21448.068118] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 18 02:26:47 blubug kernel: [21448.068150] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 02:26:47 blubug kernel: [21449.116034] usb 7-6: reset high speed USB device using ehci_hcd and address 3
Feb 18 02:26:47 blubug kernel: [21449.372031] usb 1-1: reset full speed USB device using uhci_hcd and address 2
Feb 18 02:26:47 blubug kernel: [21449.692030] usb 5-1: reset full speed USB device using uhci_hcd and address 2
Feb 18 02:26:47 blubug kernel: [21450.119457] Registered led device: iwl-phy0::radio
Feb 18 02:26:47 blubug kernel: [21450.119485] Registered led device: iwl-phy0::assoc
Feb 18 02:26:47 blubug kernel: [21450.119497] Registered led device: iwl-phy0::RX
Feb 18 02:26:47 blubug kernel: [21450.119509] Registered led device: iwl-phy0::TX
Feb 18 02:26:47 blubug kernel: [21450.170815] gl860: Release: 0103
Feb 18 02:26:47 blubug kernel: [21450.170816] gl860: Number of interfaces : 1
Feb 18 02:26:47 blubug kernel: [21450.170817] gl860: Forcage du pilote
Feb 18 02:26:47 blubug kernel: [21450.170818] gl860: Version Hulkie/Iceman/Soro (c)
Feb 18 02:26:47 blubug kernel: [21450.170819] gl860: Genesys USB2.0 - GL860 based webcam found.
Feb 18 02:26:47 blubug kernel: [21450.170820] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
Feb 18 02:26:47 blubug kernel: [21453.188059] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
Feb 18 02:26:47 blubug kernel: [21453.188274] PM: resume devices took 8.412 seconds
Feb 18 02:26:47 blubug kernel: [21453.188280] ------------[ cut here ]------------
Feb 18 02:26:47 blubug kernel: [21453.188281] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x7c/0x80()
Feb 18 02:26:47 blubug kernel: [21453.188282] Component: resume devices
Feb 18 02:26:47 blubug kernel: [21453.188283] Modules linked in: isofs udf crc_itu_t prism2_usb(C) binfmt_misc acpi_cpufreq input_polldev xfs gl860 compat_ioctl32 videodev v4l1_compat coretemp sbp2 ppdev parport_pc lp parport joydev pcspkr psmouse serio_raw arc4 ecb snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm ricoh_mmc snd_seq_dummy iwlagn snd_seq_oss snd_seq_midi iwlcore lbm_cw_mac80211 snd_rawmidi snd_seq_midi_event sdhci_pci sdhci iTCO_wdt iTCO_vendor_support btusb lbm_cw_cfg80211 snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc nvidia(P) video output asus_laptop led_class intel_agp ohci1394 ieee1394 sky2 ehci_hcd uhci_hcd fbcon tileblit font bitblit softcursor fuse
Feb 18 02:26:47 blubug kernel: [21453.188312] Pid: 16195, comm: s2ram Tainted: P         C 2.6.28-7-generic #20-Ubuntu
Feb 18 02:26:47 blubug kernel: [21453.188314] Call Trace:
Feb 18 02:26:47 blubug kernel: [21453.188318]  [<ffffffff8024d857>] warn_slowpath+0xb7/0xf0
Feb 18 02:26:47 blubug kernel: [21453.188321]  [<ffffffff8026a368>] ? down_trylock+0x38/0x50
Feb 18 02:26:47 blubug kernel: [21453.188323]  [<ffffffff8024df70>] ? try_acquire_console_sem+0x10/0x40
Feb 18 02:26:47 blubug kernel: [21453.188326]  [<ffffffff802595b6>] ? lock_timer_base+0x36/0x70
Feb 18 02:26:47 blubug kernel: [21453.188329]  [<ffffffff8067f320>] ? printk+0x67/0x6f
Feb 18 02:26:47 blubug kernel: [21453.188332]  [<ffffffff8040baa7>] ? kobject_put+0x27/0x60
Feb 18 02:26:47 blubug kernel: [21453.188335]  [<ffffffff804a96b5>] ? put_device+0x15/0x20
Feb 18 02:26:47 blubug kernel: [21453.188338]  [<ffffffff804b169a>] ? dpm_complete+0x18a/0x1a0
Feb 18 02:26:47 blubug kernel: [21453.188340]  [<ffffffff8027cf1c>] suspend_test_finish+0x7c/0x80
Feb 18 02:26:47 blubug kernel: [21453.188342]  [<ffffffff8027d004>] suspend_devices_and_enter+0xe4/0x180
Feb 18 02:26:47 blubug kernel: [21453.188344]  [<ffffffff8027d2b9>] enter_state+0xe9/0x120
Feb 18 02:26:47 blubug kernel: [21453.188346]  [<ffffffff8027d3aa>] state_store+0xba/0x100
Feb 18 02:26:47 blubug kernel: [21453.188348]  [<ffffffff8040b947>] kobj_attr_store+0x17/0x20
Feb 18 02:26:47 blubug kernel: [21453.188351]  [<ffffffff80344185>] sysfs_write_file+0xc5/0x140
Feb 18 02:26:47 blubug kernel: [21453.188354]  [<ffffffff802e4bfb>] vfs_write+0xcb/0x130
Feb 18 02:26:47 blubug kernel: [21453.188356]  [<ffffffff802e4d50>] sys_write+0x50/0x90
Feb 18 02:26:47 blubug kernel: [21453.188358]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Feb 18 02:26:47 blubug kernel: [21453.188359] ---[ end trace 66bafd5e6603a6e8 ]---
Feb 18 02:26:47 blubug kernel: [21453.188388] PM: Finishing wakeup.
Feb 18 02:26:47 blubug kernel: [21453.188389] Restarting tasks ... done.
Feb 18 02:26:56 blubug kernel: [21462.409458] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Feb 18 02:26:56 blubug kernel: [21462.409463] PM: Marking nosave pages: 00000000bffb0000 - 0000000100000000
Feb 18 02:26:56 blubug kernel: [21462.415265] PM: Basic memory bitmaps created
Feb 18 02:26:56 blubug kernel: [21462.534757] Syncing filesystems ... done.
Feb 18 02:26:56 blubug kernel: [21462.596617] Freezing user space processes ... (elapsed 0.00 seconds) done.
Feb 18 02:26:56 blubug kernel: [21462.597705] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Feb 18 02:26:56 blubug kernel: [21462.597892] s2disk[16640]: segfault at 0 ip 0000000000000000 sp 00007fff7b84f508 error 14 in s2disk[400000+8000]
Feb 18 02:26:56 blubug kernel: [21462.597917] Core dump to |/usr/share/apport/apport pipe failed
Feb 18 02:26:56 blubug kernel: [21462.621563] PM: Basic memory bitmaps freed
Feb 18 02:26:56 blubug kernel: [21462.621565] Restarting tasks ... done.
Feb 18 02:27:45 blubug kernel: [21511.093929] Core dump to |/usr/share/apport/apport pipe failed

---

### Post by nol_faich on 2009-02-18
If the unload module is reload at the resume time, maybe you should try to unload it, remove gl860 from /etc/modules and make a new test.
I looked at in gspca drivers what was done with suspend and it look like there is only the possibility to stop the driver and resume it later so I don't think that does anything if the driver is not active while hibernating.

---

### Post by BUGabundo on 2009-02-18
do i need to reboot after changing the modules?

---

### Post by nol_faich on 2009-02-18
I don't think. Try and if it is reload at resume time then reboot.

---

### Post by BUGabundo on 2009-02-19
oops, forgot to post an update:
after some debug, the prob i mention doesnt appear to have a root cause with the webcam driver.

---

### Post by nol_faich on 2009-03-10
Hi all!

There is a "new" version online (the script shakedown may be not working always properly).
I would like you to test it and tell if the README is understandable.

This version supports a "don't care about libv4l"(default)/"only-libv4l" working mode, the autodetection of flavour to use (not used if you have a previous installation of the driver), a tool to change webcam settings outside an application and a parameter for webcam image grabbers to skip the first images at the webcam startup and so grab the image when the webcam is fully initialized.

---

### Post by BUGabundo on 2009-03-10
downloading now

---

### Post by soro2005 on 2009-03-10
Camorama works great, but gstreamer (and consequently cheese) segfaults and skype yields a black image. :-( Ubuntu 8.10 64bit.

---

### Post by nol_faich on 2009-03-11
Hi, thanks for the test!

I enabled traces in this release:
[http://downloads.sourceforge.net/gl860/gl860_2.6.28d9.tgz?use_mirror=](http://downloads.sourceforge.net/gl860/gl860_2.6.28d9.tgz?use_mirror=)
Could you test it with applications launched in command line and report the 'dmesg | gl860' + console traces.

---

### Post by BUGabundo on 2009-03-12
with the previous version (gl860_2.6.28d7) cheese was core dumping. will download the new one, and test it.
if it crashes i'll file a bug... camorama was working ok, and a bit faster it seemed

---

### Post by BUGabundo on 2009-03-12
still seg faulting... not sure its about the driver or not.
filed here [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/341618](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/341618)

btw the driver works ok with $ uname -a
Linux blubug 2.6.28-9-generic #29-Ubuntu SMP Sun Mar 8 02:02:39 UTC 2009 x86_64 GNU/Linux

---

### Post by BUGabundo on 2009-03-12
@Nol im getting "v4lconvert_convert()" errors.
please see bug 341624 and 341618

attaching traces there

---

### Post by soro2005 on 2009-03-12
Here's the terminal trace, and attached the corresponding dmesg output. As you can see, cheese/gstreamer segfaults, skype yields an all black video window.
```
/nvgl$ cheese

(cheese:22527): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:22527): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:22527): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
Segmentation fault

(clipped)

/nvgl$ skype
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Skype V4L2: Failed to change capture framerate (15)
Skype V4L2: Failed to change capture framerate (15)
Starting the process...
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280
```

---

### Post by nol_faich on 2009-03-12
It seems that there is an issue with libv4l, Camorama does not use it unless it has been changed to use v4l2. But Cheese is in v4l2 and may use libv4l. However the strange thing is that the requested image format is RGB24 and that the driver is defaulted to do the conversion on is own and so do not really need a conversion by libv4l...
Libv4l can be set to enable traces, but I will look at this to explain how get these logs.

---

### Post by nol_faich on 2009-03-12
To have a log, create an environmental variable named LIBV4L2_LOG_FILENAME with the path to the log.

LIBV4L2_LOG_FILENAME=/home/XXX/libv4l.log
export LIBV4L2_LOG_FILENAME
cheese
Then later try camorama. Camorama is a reference source.


The logs from libv4l and the 'dmesg | grep gl860' will help to understand what happens.

---

### Post by BUGabundo on 2009-03-13
attached the log... changed the ext so the forum would upload

---

### Post by BUGabundo on 2009-03-13
I'm documenting the libv4lbug on [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/341624](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/341624)

---

### Post by nol_faich on 2009-03-13
Libv4l seems to crash while converting from RGB24 (RGB3) to YU12.
This explains why Camorama is OK (asks RGB24) but Cheese crashes (asks YU12 but libv4l requests my driver to provide RGB24 and convert it to YU12).
Thanks for the log.

---

### Post by nol_faich on 2009-03-15
IF YOU USED THE gl860_2.6.28e, REPLACE IT WITH gl860_2.6.28e2 (the driver version nickname is badly formed after the install, this prevent the driver to be usable) AND REMOVE THE gl860 line in the file /etc/modprobe.d/options. 

The segfault with cheese is resolved with the last available driver version ([http://downloads.sourceforge.net/gl860/gl860_2.6.28e2.tgz](http://downloads.sourceforge.net/gl860/gl860_2.6.28e2.tgz)).

@Soro: I spotted the origin of the issue with Cheese while downsizing, it is corrected.

---

### Post by soro2005 on 2009-03-15
Great, seems to work very smoothly here. I also see that the startup in several programs seems to be quicker. Among them skype and the flash plugin. In Skype: a second and a half of nothing happening --> blue led comes on for one second --> picture. Before, I think I had the led going on and off at least twice before the picture came.

I currently don't see any problems here. I'll observe.

*edit*: Wow, even Ekiga seems to work fairly well now. I've played hard with Cheese for several minutes, switching on and off all the effects what before would have lead to bad starts and scrambled images. Now, it's all perfect. Amazing!

---

### Post by nol_faich on 2009-03-18
Thanks Soro for this nice report!

---

### Post by nol_faich on 2009-04-14
New test version here 
[https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.28g.tgz&a=41768032](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.28g.tgz&a=41768032)
Most of the changes are a better v4l and v4l2 management and also code source cleaning.
Please test that proposed settings are working with your webcam.
VLC used in v4l2 (command line in the README) is quite a good tool to change settings (use the equalizer="Extended settings" and "v4l2 controls").

---

### Post by BUGabundo on 2009-04-15
The previous version had some trouble with cheese!
If I started recording, then stopped and again initiated recording the 2nd video would have trouble!
I filmed a presentation i did two weeks ago, and the entire 2nd part is rubbish now.
I tested yesterday again to try to find the  bug, and found it was related to using higher resolutions (>800x600) in cheese.

Also Flash would have trouble with restarting recording... but thats Flash, not much we can do.


I'll download the new version and test it with the latest kernel on Jaunty.

Thanks so much for all your work, Nol

---

### Post by nol_faich on 2009-04-15
I'm waiting for your input. Enabling the traces in the driver will be very useful if this version is not better than the previous one.

---

### Post by BUGabundo on 2009-04-15
webcam stop working with gl860_2.6.28g
both cheese and camorama fail to detect it! :(

---

### Post by nol_faich on 2009-04-16
In base_gl860.h, there is two lines defining "STK_DEV", one is commented in and the other out. Swap the comments and recompile the driver.
With the traces in /var/log/syslog I shpuld be able to understand what happens.

---

### Post by BUGabundo on 2009-04-16
strangest thing, after reboot it works
i never required to do that before!

---

### Post by nol_faich on 2009-04-16
Phew. It sounds better if it works :).
I think the issue is related to the change of some functions in the module. Sometimes I saw this when the driver was restarted, traces said that no more existing functions was not present, the next time it was good. Until this test release, I don't remember any change in public function, this is why there was not such an issue.
Could you tell me about Flash and Cheese if the issue you had as still present? Also could you play with all settings with VLC in v4l2 to know if this are rightly managed ?

---

### Post by BUGabundo on 2009-04-16
Cheese is good, so is VLC (great quality image too).

Flash seem something is wrong: [http://www.ustream.tv/recorded/1390425](http://www.ustream.tv/recorded/1390425)

and here its always black, and has been for a few versions. it used to work [http://bambuser.com/channel/BUGabundo/broadcast/113417](http://bambuser.com/channel/BUGabundo/broadcast/113417)


strace from logs attached.

---

### Post by nol_faich on 2009-04-16
In order to get useful traces, you need to enable traces in the driver with the change in base_gl860.h. It allows to see the negociation for pixel format andimage size between applications/libv4l and the driver. This part is generally the reason of failures.

---

### Post by BUGabundo on 2009-04-16
> **nol_faich said:**
> In order to get useful traces, you need to enable traces in the driver with the change in base_gl860.h.

ok

---

### Post by BUGabundo on 2009-04-16
debug changed, compiled and installed.
just to be sure, i'll test *after* reboot

---

### Post by nol_faich on 2009-04-16
OK, I wait.


New install script in this release: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.28g2.tgz&a=28921530](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.28g2.tgz&a=28921530)
Use "./install -t" to enable traces.

---

### Post by soro2005 on 2009-04-16
Works fine here it seems. After a restart, that is. I'll be observing.

---

### Post by BUGabundo on 2009-04-17
cheese works great, and so does camorana
ekiga coredumped [https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/362804](https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/362804)

skype works
Flash on ustream works too [http://www.ustream.tv/recorded/1394730](http://www.ustream.tv/recorded/1394730)



EDIT: some how flash stop capturing after I sent this :( i'll see whats up

EDIT2: 2 weeks i captured 4h of video of one of my FOSS presentations.
1st part was fine, at the interval I stopped cheese capture, and started recording the 2nd part after the break.

video 1 is OK, video 2 just gives me all this errors:
```
Too many video packets in the buffer: (4096 in 32016066 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.3 V:   2.6 A-V: -2.248 ct: -0.223  68/ 68 14%  2%  0.0% 0 0 

```
is it the driver or cheese? and can i ever rebuild that video?

---

### Post by nol_faich on 2009-04-17
What is this log file? Does it is related to the Cheese issue? 

The other trace is very likely related to Cheese or the codec used. The end of traces show nothing special: the driver releases video in 320x240 BGR3 (BGR 24bits). It seems that the trace is stopped before Cheese has been stop because there is no "STREAMOFF".
The webcam LED was switched on I suppose

Please retry Ekiga and extract its traces or tell the Ekiga start/end time in the traces.

---

### Post by BUGabundo on 2009-04-17
i should have opened several posts, instead of just one!

the attached log is a grep gl860 of /var/log/messages after using all those apps.

I cant run ekiga 'cause it coredumping and I've reported it upstream

Do u need more tests?

---

### Post by nol_faich on 2009-04-17
Log with traces if they are missing for Ekiga and Flash.
Can you reproduce the issue with Cheese and video and provide log with traces?

---

### Post by Jack Malmostoso on 2009-04-18
Hi Nol, I can't seem to compile the driver for 2.6.29:```
jack@vasquez:~/Desktop/nvgl$ ./install 

Sources newer than the module => compilation
*****************************************************************************
 1/6) [Kernel headers for current kernel installed]

 2/6) [Make is present]
*****************************************************************************
 3/6) [No old module...] Nothing to do

 4/6) [Clean up from previous compilations]
 $ make clean
make -C "/lib/modules/2.6.29-1-amd64/build"    SUBDIRS="/home/jack/Desktop/nvgl" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-1-amd64'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-1-amd64'
*****************************************************************************
 5/6) [Source code generation...]
 6/6) [Compiling driver...]
 $ make driver
make -C "/lib/modules/2.6.29-1-amd64/build"    SUBDIRS="/home/jack/Desktop/nvgl" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-1-amd64'
  CC [M]  /home/jack/Desktop/nvgl/gl860-main.o
  CC [M]  /home/jack/Desktop/nvgl/gl860-usb.o
  CC [M]  /home/jack/Desktop/nvgl/gl860-dev.o
  CC [M]  /home/jack/Desktop/nvgl/gl860-v4l.o
/home/jack/Desktop/nvgl/gl860-v4l.c: In function &#8216;v4l_gl860_register_video_device&#8217;:
/home/jack/Desktop/nvgl/gl860-v4l.c:2013: warning: assignment from incompatible pointer type
/home/jack/Desktop/nvgl/gl860-v4l.c: At top level:
/home/jack/Desktop/nvgl/gl860-v4l.c:2064: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
make[4]: *** [/home/jack/Desktop/nvgl/gl860-v4l.o] Error 1
make[3]: *** [_module_/home/jack/Desktop/nvgl] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-1-amd64'
make: *** [driver] Error 2

```

Halp?

---

### Post by nol_faich on 2009-04-18
Hello!

2.6.28 was a dream, no changes in functions.

I made a correction here : [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29a.tgz&a=5743206](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29a.tgz&a=5743206)
I hope it is good...

In order to avoid that awful maintenance, I made a gspca version of the driver to use their framework because my work is limited to exchange data with the webcam and set/get parameter values so that I have far less maintenance but this framework works in v4l2 so that you need a special way to launch v4l1 applications. Moreover that framework seems a little bit constraining and some v4l2 applications do not work. I need to study that but it's a shame, gspca is in the kernel so that being included in gspca will make the life easier for everybody.

---

### Post by soro2005 on 2009-04-18
The last one (29a) is also good here. :-) Still have to insert it manually after compiling, with ```
sudo modprobe gl860
```

---

### Post by nol_faich on 2009-04-19
Hi Soro, you are still 2.6.28? Without the modprobe the driver is not active?

@ all : I would like to know which applications you use with the webcam and whether they are v4l1 or v4l2 (to know that, launch the app and while the webcam is streaming use the "cmd-gl860" provided with the driver: "cmd-gl860 i" and look at the "Is streaming" line). I would like to assess the use of v4l1 vs v4l2.
If an application you want to use does not work, please install the driver with "./install -t" to enable traces and try that application. I need "grep gl860 /var/log/syslog", the name of the application, your kernel version and 32 or 64 bits.

---

### Post by Jack Malmostoso on 2009-04-19
Hey Nol,
thanks for trying a fix but it did not work:```
jack@vasquez:~/Desktop/nvgl$ ./install 

Sources newer than the module => compilation
*****************************************************************************
 1/6) [Kernel headers for current kernel installed]

 2/6) [Make is present]
*****************************************************************************
 3/6) [No old module...] Nothing to do

 4/6) [Clean up from previous compilations]
 $ make clean
make -C "/lib/modules/2.6.29-1-amd64/build"    SUBDIRS="/home/jack/Desktop/nvgl" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-1-amd64'
  CLEAN   /home/jack/Desktop/nvgl/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-1-amd64'
*****************************************************************************
 5/6) [Source code generation...]
 6/6) [Compiling driver...]
 $ make driver
make -C "/lib/modules/2.6.29-1-amd64/build"    SUBDIRS="/home/jack/Desktop/nvgl" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-1-amd64'
  CC [M]  /home/jack/Desktop/nvgl/gl860-main.o
  CC [M]  /home/jack/Desktop/nvgl/gl860-usb.o
  CC [M]  /home/jack/Desktop/nvgl/gl860-dev.o
  CC [M]  /home/jack/Desktop/nvgl/gl860-v4l.o
/home/jack/Desktop/nvgl/gl860-v4l.c: In function &#8216;v4l_gl860_ioctl&#8217;:
/home/jack/Desktop/nvgl/gl860-v4l.c:1992: error: &#8216;inode&#8217; undeclared (first use in this function)
/home/jack/Desktop/nvgl/gl860-v4l.c:1992: error: (Each undeclared identifier is reported only once
/home/jack/Desktop/nvgl/gl860-v4l.c:1992: error: for each function it appears in.)
/home/jack/Desktop/nvgl/gl860-v4l.c: In function &#8216;v4l_gl860_register_video_device&#8217;:
/home/jack/Desktop/nvgl/gl860-v4l.c:2024: warning: assignment from incompatible pointer type
/home/jack/Desktop/nvgl/gl860-v4l.c: At top level:
/home/jack/Desktop/nvgl/gl860-v4l.c:2081: error: conflicting types for &#8216;v4l_gl860_fops&#8217;
/home/jack/Desktop/nvgl/gl860-v4l.c:60: error: previous declaration of &#8216;v4l_gl860_fops&#8217; was here
/home/jack/Desktop/nvgl/gl860-v4l.c:2088: warning: initialization from incompatible pointer type
make[4]: *** [/home/jack/Desktop/nvgl/gl860-v4l.o] Error 1
make[3]: *** [_module_/home/jack/Desktop/nvgl] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-1-amd64'
make: *** [driver] Error 2

```

As for moving the bulk of the driver in gspca, I believe it is a good idea. It's not really healthy for you to run after each kernel version, plus as far as I can tell you mostly figured out the various versions available of the cam.
Also, the more people can easily access the driver, the more feedback you'll get.

Thanks for your help :)

---

### Post by nol_faich on 2009-04-19
New try here : [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29b.tgz&a=9312649](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29b.tgz&a=9312649)

---

### Post by soro2005 on 2009-04-19
> **nol_faich said:**
> Hi Soro, you are still 2.6.28? Without the modprobe the driver is not active?

I am still using Intrepid Ibex (2.6.27). I've just chimed in to let you know that nothing is broken here. :D

I thought that my problem was the same one as Bugabundo's who says he has to reboot the computer after running the install script. Same here, only that the modprobe does the job as well. The install script finishes normal, but it throws this error on the way:
```
insmod: error inserting 'gl860.ko': -1 Unknown symbol in module
```

---

### Post by nol_faich on 2009-04-19
The error message comes the first time, not each time you use the install script? This was the message I had when making changes in some function names. For an unknown reason, the driver search for old function names and the next time is good if I remeber.

---

### Post by Jack Malmostoso on 2009-04-19
Hey Nol, thanks, the new 2.6.29b version compiles and works just fine.
I had to reboot after modprobing the module because /dev/video0 was not created, but this is probably udev's fault.

Thanks :)

---

### Post by nol_faich on 2009-04-19
Perfect!

Maybe you add the conflict between old driver and new one because of the change in the name some functions.

I uploaded the gspca version. Can you test it? It's OK with my webcam. With 0503's family the basic gspca start sequence cannot match the one sniffed with Windows. Despite of that, I would like to know if it work. The driver is here: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29b.tgz&a=86682547](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29b.tgz&a=86682547)
I made basic intructions in the README (you have to get the gspca -300Mo disk place required once untared and drivers compiled-, copy the driver in the gspca directory, compile the drivers and unload some modules and replace them with the newly generated). After reboot, your system modules are left untouched. The newly compiled are not installed, this is just for test.

Thanks

---

### Post by Jack Malmostoso on 2009-04-20
Hmmm there are some errors. The compilation seems fine, but when I have to load the modules:```
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ sudo modprobe -r gl860
[sudo] password for jack: 
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ sudo modprobe -r videodev
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ sudo modprobe -r v4l1-compat
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ lsmod | grep gl860
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ lsmod | grep video
video                  19972  0 
output                  3328  1 video
thermal_sys            13104  4 video,thermal,processor,fan
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ sudo insmod v4l/v4l1-compat.ko
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ sudo insmod v4l/videodev.ko
insmod: error inserting 'v4l/videodev.ko': -1 Unknown symbol in module
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ sudo insmod v4l/gspca_main.ko
insmod: error inserting 'v4l/gspca_main.ko': -1 Unknown symbol in module
jack@vasquez:~/Desktop/gspca-5a9a52f1277e$ sudo insmod v4l/gspca_gl860.ko
insmod: can't read 'v4l/gspca_gl860.ko': No such file or directory
```

Shouldn't I modify some Makefile somewhere?

---

### Post by nol_faich on 2009-04-20
In the dmesg there is traces with missing functions. I need them.
Can you make a surch for gspca_gl860.ko. It should be in v4l but it seems to be absent.
Are you sure the driver sources has been copied in the gspca subdirectory ?

---

### Post by Jack Malmostoso on 2009-04-23
Hey Nol, I have tried again and it does not work. The original gspca tarball compiles just fine, but when I copy your Makefile and Kconfig into gspca-cc5074187cb7/linux/drivers/media/video/gspca/ I get:```
jack@vasquez:~/Desktop/gspca-cc5074187cb7$ make
make -C /home/jack/Desktop/gspca-cc5074187cb7/v4l 
make[1]: Entering directory `/home/jack/Desktop/gspca-cc5074187cb7/v4l'
No version yet, using 2.6.29-1-amd64
make[1]: Leaving directory `/home/jack/Desktop/gspca-cc5074187cb7/v4l'
make[1]: Entering directory `/home/jack/Desktop/gspca-cc5074187cb7/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.29
Unmatched endmenu at ../linux/drivers/media/Kconfig:139
make[1]: Leaving directory `/home/jack/Desktop/gspca-cc5074187cb7/v4l'
make[1]: Entering directory `/home/jack/Desktop/gspca-cc5074187cb7/v4l'
Makefile:210: *** target file `all' has both : and :: entries.  Stop.
make[1]: Leaving directory `/home/jack/Desktop/gspca-cc5074187cb7/v4l'
make: *** [all] Error 2
```

Ideas on how to fix this?

---

### Post by nol_faich on 2009-04-23
I apologize, I included wrong file versions in the tarball.
Corrected release here: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29c.tgz&a=43026864](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29c.tgz&a=43026864)

---

### Post by Jack Malmostoso on 2009-04-24
Hey Nol, thanks for the new version.
It compiled correctly and I could load the gspca modules. However, no luck in getting an image in camorama.
Here is dmesg:```
jack@vasquez:~/Desktop/gspca-cc5074187cb7$ dmesg | grep gl860
[   13.037703] calling  gl860_init+0x0/0x213 [gl860] @ 1613
[   13.048320] Genesys gl860: Genesys USB2.0 webcam driver startup
[   13.053566] Genesys gl860: Release: 0103
[   13.058722] Genesys gl860: Number of interfaces : 1
[   13.676110] Genesys gl860: probe 1=ff
[   13.686605] Genesys gl860: probe 2=26
[   13.800857] Genesys gl860: probe 2=26
[   13.800859] Genesys gl860: Version Malmostoso (ms) v2.6.28g
[   13.800861] Genesys gl860: GL860 based webcam found.
[   13.800862] Genesys gl860: Product ID 0x0503 - 2.0M WebCam
[   15.508125] Genesys gl860: Camera is now controlling video device /dev/video0
[   15.513540] usbcore: registered new interface driver usb_gl860_driver
[   15.519002] initcall gl860_init+0x0/0x213 [gl860] returned 0 after 2412769 usecs
[  255.966183] Genesys gl860: usb_gl860_exit: Genesys USB2.0 webcam driver shutdown
[  255.966190] usbcore: deregistering interface driver usb_gl860_driver
[  255.966221] Genesys gl860: Genesys USB2.0 Camera disconnected
[  255.966246] Genesys gl860: Camera release resources video device /dev/video0
[  723.752654] calling  sd_mod_init+0x0/0x44 [gspca_gl860] @ 18104
[  724.259533] gl860: probe 1=ff
[  724.264530] gl860: probe 2=26
[  724.264534] gl860: probe 2 undecided (32/0)
[  724.264537] gl860: *  1.3Mpixels -> set the 'sa' flavour
[  724.264539] gl860: *  2.0Mpixels -> set the 'ms' flavour
[  724.264542] gl860: Version Malmostoso (ms) 0.04.18 (GSPCA)
[  724.264546] gl860: Camera is now controlling video device /dev/video0
[  725.893183] usbcore: registered new interface driver gl860
[  725.893187] gl860: registered
[  725.893296] initcall sd_mod_init+0x0/0x44 [gspca_gl860] returned 0 after 2090450 usecs
```
And here is the output of camorama:```
jack@vasquez:~/Desktop/gspca-cc5074187cb7$ camorama -D

VIDIOCGCAP
device name = USB 2.0 PC Camera
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 1600
max height = 1200
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 0
hue = 0
colour = 32896
contrast = 0
whiteness = 33288
colour depth = 8

VIDIOCGMBUF
mb.size = 7684096
mb.frames = 4
mb.offset = 1921024
update_tooltip called
tip - acap off
** Message: SET PIC
** Message: SET PIC
update_tooltip called
tip - acap off
Unable to capture image (VIDIOCSYNC)
```

Hope this helps, let me know if you need more info!

---

### Post by nol_faich on 2009-04-24
All is OK. I just need to make some minor changes to autodetection. However I miss informations for test.
The issue is that Camorama is v4l1 despite gspca is v4l2. You need to test with Cheese, Ekiga or Skype. For v4l1 applications, you need to use a dedicated command line.
Please try with a v4l2 application and test all sizes and all settings with the help of cmd-gl860.

EDIT: new release [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_0.04.25.tgz&a=56921037](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_0.04.25.tgz&a=56921037)
(I did not try to compile it because I'm on my laptop, I hope it is OK)

---

### Post by Jack Malmostoso on 2009-04-25
All clear!
It works fine in Cheese (all sizes), I get a green screen in Skype and it does not work at all in Ekiga.
Also, cmd-gl860 changes all settings perfectly.

I have tried capturing a video with Cheese but I can't record (the image disappears and an empty video file is created).

---

### Post by BUGabundo on 2009-04-25
> **Jack Malmostoso said:**
> ...it does not work at all in Ekiga.

that would be [https://bugs.launchpad.net/bugs/362804](https://bugs.launchpad.net/bugs/362804)

i'm adding new logs to it right now!

@nol what is the latest driver version to use as somewhat stable but still testing?

---

### Post by BUGabundo on 2009-04-25
@nol on a different note: would have any interest in running a PPA with two branchs, one for stable and one for testing with the driver?

it would be much more useful and easy for users to just have a source entry and always be update, as also easily track installed version.

maybe @maco could help you with start packaging for the PPA if you arent sure how to do it. 

what do you think?

---

### Post by nol_faich on 2009-04-25
Latest release [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29e.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29e.tgz)
It should fix the scrambled image issue.
I also changed the traces at startup in syslog.

Latest gspca release : 
[https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29e.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29e.tgz)

@ Bugabundo:
The PPA seems to me very interesting. I will dig a little bit more into this.
Can you test the gspca release ? (instructions in the README)

---

### Post by Jack Malmostoso on 2009-04-26
Hi Nol, tested last version of gspca. Same results as before: cheese works, skype gives me a green window and ekiga gives an error, complaining about color profiles.
dmesg:```
jack@vasquez:~$ dmesg | grep gl860
[   13.059268] calling  gl860_init+0x0/0x213 [gl860] @ 1550
[   13.064826] Genesys gl860: Genesys USB2.0 webcam driver startup
[   13.070343] Genesys gl860: Release: 0103
[   13.075793] Genesys gl860: Number of interfaces : 1
[   13.684512] Genesys gl860: probe 1=ff
[   13.694889] Genesys gl860: probe 2=26
[   13.812888] Genesys gl860: probe 2=26
[   13.818457] Genesys gl860: Version Malmostoso (ms) v2.6.28g
[   13.823929] Genesys gl860: GL860 based webcam found.
[   13.829310] Genesys gl860: Product ID 0x0503 - 2.0M WebCam
[   15.468122] Genesys gl860: Camera is now controlling video device /dev/video0
[   15.473648] usbcore: registered new interface driver usb_gl860_driver
[   15.479179] initcall gl860_init+0x0/0x213 [gl860] returned 0 after 2357760 usecs
[  567.780853] Genesys gl860: usb_gl860_exit: Genesys USB2.0 webcam driver shutdown
[  567.780858] usbcore: deregistering interface driver usb_gl860_driver
[  567.780887] Genesys gl860: Genesys USB2.0 Camera disconnected
[  567.780915] Genesys gl860: Camera release resources video device /dev/video0
[  742.715950] calling  sd_mod_init+0x0/0x44 [gspca_gl860] @ 18861
[  743.236432] Genesys gl860: probe 1=ff
[  743.236438] Genesys gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[  743.241429] Genesys gl860: probe 2=26
[  743.241433] Genesys gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29e (GSPCA)
[  743.241437] Genesys gl860: Camera is now controlling video device /dev/video0
[  744.868166] usbcore: registered new interface driver Genesys gl860
[  744.868170] Genesys gl860: registered
[  744.868277] initcall sd_mod_init+0x0/0x44 [gspca_gl860] returned 0 after 2101864 usecs
```

---

### Post by nol_faich on 2009-04-26
Hi Jack! Can you tell me more about Ekiga issue ? It does not look like the issue of Bugabundo.
About the empty video with Cheese:
- is it only for gspca driver?
- when you try to start the video, is the webcam LED switched on?
- Does Cheese logs something about this issue?

---

### Post by nol_faich on 2009-04-26
New releases :
gl860 (stand alone) [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29f.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gl860_2.6.29f.tgz) (fix about traces at startup and driver version overriding)
gl860 (GSPCA) [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29f.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29f.tgz) (allow options in command line for the gspca driver)

---

### Post by nol_faich on 2009-04-27
EDIT : THIS DRIVER SEGFAULTS with Ubuntu8.10
"New" gspca driver : [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29g.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29g.tgz)

This version does not need to get the gspca sources and compile them.
Just use "./install" to compile and load the required modules.
The install script left your system untouched after the restart of your laptop.

---

### Post by Jack Malmostoso on 2009-05-05
Hey Nol,

here is what I get with the latest version (2.6.29g) of the gspca driver:```
jack@vasquez:~/Desktop/gspcav2$ ./install 
make -C "/lib/modules/2.6.29-2-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-2-amd64'
  CLEAN   /home/jack/Desktop/gspcav2/.tmp_versions
  CLEAN   /home/jack/Desktop/gspcav2/Module.symvers
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-2-amd64'
make -C "/lib/modules/2.6.29-2-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-2-amd64'
  CC [M]  /home/jack/Desktop/gspcav2/gl860.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-sysfs.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-f191.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503ms.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503sa.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503his.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jack/Desktop/gspcav2/gspca_gl860.mod.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-2-amd64'
sudo rmmod gspca_gl860 2>/dev/null
[sudo] password for jack: 
sudo insmod /lib/modules/2.6.29-2-amd64/kernel/drivers/media/video/gspca/gspca_main.ko 2>&1 | grep -v 'File exists'
insmod: error inserting '/lib/modules/2.6.29-2-amd64/kernel/drivers/media/video/gspca/gspca_main.ko': -1 Unknown symbol in module
sudo insmod gspca_gl860.ko
insmod: error inserting 'gspca_gl860.ko': -1 Unknown symbol in module
```This is the dmesg output:```
jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[  844.677480] gspca_gl860: Unknown symbol gspca_frame_add
[  844.677549] gspca_gl860: Unknown symbol gspca_debug
[  844.677751] gspca_gl860: Unknown symbol gspca_disconnect
[  844.677853] gspca_gl860: Unknown symbol gspca_resume
[  844.677919] gspca_gl860: Unknown symbol gspca_dev_probe
[  844.677990] gspca_gl860: Unknown symbol gspca_suspend
```

---

### Post by dr_psikick on 2009-05-05
Really thanks for the 2.6.29f release is the first that works with my laptop.
Great work and thanks once again for all your effort.

---

### Post by BUGabundo on 2009-05-06
AFAIK nol already knows this 'cause i triaged it with him last week.
I had to revert to an older driver version for webcam to work.

---

### Post by nol_faich on 2009-05-06
Hi Jack!

As the gspca_main driver is not loaded, gspca_gl860 cannot be loaded.
Can you report the error about gspca_main ?
There is some risk of segfault and reboot needed to clear the situation with the gspca driver. There is also such an issue if the webcam is disconnected from USB while streaming (eg when I turn my webcam, sometimes it is disconnected because of some electrical contact issue).
The driver compiled from the latest gspca sources is OK.

---

### Post by Jack Malmostoso on 2009-05-07
Hey Nol,
indeed if I load gspca_main before compiling the module it all works fine:```
jack@vasquez:~$ sudo modprobe gspca_main 
jack@vasquez:~/Desktop/gspcav2$ ./install 
make -C "/lib/modules/2.6.29-2-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-2-amd64'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-2-amd64'
make -C "/lib/modules/2.6.29-2-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-2-amd64'
  CC [M]  /home/jack/Desktop/gspcav2/gl860.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-sysfs.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-f191.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503ms.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503sa.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503his.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jack/Desktop/gspcav2/gspca_gl860.mod.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-2-amd64'
sudo rmmod gspca_gl860 2>/dev/null
sudo insmod /lib/modules/2.6.29-2-amd64/kernel/drivers/media/video/gspca/gspca_main.ko 2>&1 | grep -v 'File exists'
sudo insmod gspca_gl860.ko
```However when I start cheese I get:```
jack@vasquez:~/Desktop/gspcav2$ cheese 
** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

libv4l2: error turning on stream: Input/output error
libv4l2: error dequeuing buf: Invalid argument
```
Dmesg says:```

jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[   13.310808] calling  gl860_init+0x0/0x213 [gl860] @ 1583
[   13.352452] Genesys gl860: Genesys USB2.0 webcam driver startup
[   13.381114] Genesys gl860: Release: 0103
[   13.392646] Genesys gl860: Number of interfaces : 1
[   14.264215] Genesys gl860: ctrl transfer failed -110 [p40 r1 v0040 i0000 lg0]
[   14.323462] Genesys gl860: probe 1=ff
[   14.329037] Genesys gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[   14.339465] Genesys gl860: probe 2=26
[   14.345015] Genesys gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29f
[   15.956117] Genesys gl860: Camera is now controlling video device /dev/video0
[   15.961782] usbcore: registered new interface driver usb_gl860_driver
[   15.967354] initcall gl860_init+0x0/0x213 [gl860] returned 0 after 2588698 usecs
[  125.457039] Genesys gl860: usb_gl860_exit: Genesys USB2.0 webcam driver shutdown
[  125.457045] usbcore: deregistering interface driver usb_gl860_driver
[  125.457073] Genesys gl860: Genesys USB2.0 Camera disconnected
[  125.457098] Genesys gl860: Camera release resources video device /dev/video0
[  163.919229] calling  sd_mod_init+0x0/0x1d7 [gspca_gl860] @ 5372
[  163.919294] gspca_gl860: driver startup
[  164.460583] gspca_gl860: probe 1=ff
[  164.460587] gspca_gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[  164.465583] gspca_gl860: probe 2=26
[  164.465587] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29f (GSPCA)
[  164.465591] gspca_gl860: Camera is now controlling video device /dev/video0
[  166.118738] usbcore: registered new interface driver gspca_gl860
[  166.118742] gspca_gl860: driver registered
[  166.118853] initcall sd_mod_init+0x0/0x1d7 [gspca_gl860] returned 0 after 2148046 usecs
```And this is /dev/video0:```
jack@vasquez:~/Desktop/gspcav2$ ls -l /dev/video0 
crw-rw----+ 1 root video 81, 0 2009-05-07 08:19 /dev/video0
jack@vasquez:~/Desktop/gspcav2$ groups
jack dialout cdrom floppy audio src video plugdev netdev powerdev pulse kvm vboxusers usb
```

---

### Post by nol_faich on 2009-05-07
All seems OK in the dmesg. Does the webcam LED switch on ?
The gspca version has no really traces if I remember correctly, I will upload a version with traces this week-end (there must be traces a la gl860 commented in but it is not the same instruction for gspca). If you see commented in "DPROBE" (or "D_PROBE") in the gl860_dev_503ms.c, you can comment them out and looks at the dmesg to know which functions are called.

---

### Post by nol_faich on 2009-05-08
@ Malmostoso : release with traces activated at [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29h.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29h.tgz)

@ dr_psikick : Thanks for your comment :)

---

### Post by Jack Malmostoso on 2009-05-12
Hey Nol,
in release 2.6.29h there is no "install" script. I tried copying an older one, but it does not work at all.
Can you check this?
Thanks!

---

### Post by nol_faich on 2009-05-13
Things were missing !
New release here: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29h2.tgz&a=486477](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29h2.tgz&a=486477)

---

### Post by Jack Malmostoso on 2009-05-14
Still nothing. It compiles (you forgot gspca.h, but I took it from version "g") but then:```

jack@vasquez:~/Desktop/gspcav2$ sudo modprobe gspca_main 
jack@vasquez:~/Desktop/gspcav2$ ./install 
make -C "/lib/modules/2.6.30-rc4-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-rc4-amd64'
  CLEAN   /home/jack/Desktop/gspcav2/.tmp_versions
  CLEAN   /home/jack/Desktop/gspcav2/Module.symvers
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-rc4-amd64'
make -C "/lib/modules/2.6.30-rc4-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-rc4-amd64'
  CC [M]  /home/jack/Desktop/gspcav2/gl860.o
/home/jack/Desktop/gspcav2/gl860.c: In function &#8216;sd_probe&#8217;:
/home/jack/Desktop/gspcav2/gl860.c:522: warning: &#8216;gspca_dev&#8217; may be used uninitialized in this function
  CC [M]  /home/jack/Desktop/gspcav2/gl860-sysfs.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-f191.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503ms.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503sa.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503his.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jack/Desktop/gspcav2/gspca_gl860.mod.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-rc4-amd64'
sudo rmmod gl860 2>/dev/null
sudo rmmod gspca_gl860 2>/dev/null
sudo insmod /lib/modules/2.6.30-rc4-amd64/kernel/drivers/media/video/gspca/gspca_main.ko 2>&1 | grep -v 'File exists'
sudo insmod gspca_gl860.ko
insmod: error inserting 'gspca_gl860.ko': -1 Unknown symbol in module
```

---

### Post by nol_faich on 2009-05-15
What does the dmesg tell ?
There unknown symbol is logged there.
The compilation warning seems to be quite dangerous. I have to analyze that.

---

### Post by Jack Malmostoso on 2009-05-16
> **nol_faich said:**
> What does the dmesg tell ?
There unknown symbol is logged there.

Sorry Nol, didn't even cross my mind to check in dmesg.
Here is the output:```
jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[  291.771322] gspca_gl860: disagrees about version of symbol usb_register_driver
[  291.771329] gspca_gl860: Unknown symbol usb_register_driver
[  291.771406] gspca_gl860: disagrees about version of symbol gspca_frame_add
[  291.771410] gspca_gl860: Unknown symbol gspca_frame_add
[  291.771565] gspca_gl860: disagrees about version of symbol usb_control_msg
[  291.771568] gspca_gl860: Unknown symbol usb_control_msg
[  291.771645] gspca_gl860: disagrees about version of symbol usb_deregister
[  291.771648] gspca_gl860: Unknown symbol usb_deregister
[  291.771751] gspca_gl860: disagrees about version of symbol gspca_disconnect
[  291.771755] gspca_gl860: Unknown symbol gspca_disconnect
[  291.771838] gspca_gl860: disagrees about version of symbol gspca_resume
[  291.771842] gspca_gl860: Unknown symbol gspca_resume
[  291.771918] gspca_gl860: disagrees about version of symbol gspca_dev_probe
[  291.771921] gspca_gl860: Unknown symbol gspca_dev_probe
[  291.772004] gspca_gl860: disagrees about version of symbol gspca_suspend
[  291.772008] gspca_gl860: Unknown symbol gspca_suspend
```
I bet you're learning a lot about kernel programming :)

---

### Post by nol_faich on 2009-05-16
Unfortunately there is so many things to learn...

I got this message when trying to use gpsca_gl860 compiled from full v4l sources with the gspca_main released with the kernel. You seems to have also an issue with the usb part.
The install script unloads the gl860 drivers (standalone or gspca), load /lib/modules/2.6.30-rc4-amd64/kernel/drivers/media/video/gspca/gspca_main.ko and the gspca_gl860 driver.
As you preload gspca_main and there is a "2>/dev/null" for the load of gspca_main.ko, it may be possible that these are not the same gpsca_main so that there is a compliance issue.
Can you "modprobe -r gspca_main" and "insmod /lib/modules/2.6.30-rc4-amd64/kernel/drivers/media/video/gspca/gspca_main.ko" to check for an error ?

---

### Post by Jack Malmostoso on 2009-05-17
Wow Nol, bingo!
```
jack@vasquez:~$ sudo insmod /lib/modules/2.6.30-rc4-amd64/kernel/drivers/media/video/gspca/gspca_main.ko 
insmod: error inserting '/lib/modules/2.6.30-rc4-amd64/kernel/drivers/media/video/gspca/gspca_main.ko': -1 Unknown symbol in module
jack@vasquez:~$ dmesg | grep gspca
[  178.598499] gspca_main: Unknown symbol video_ioctl2
[  178.598949] gspca_main: Unknown symbol video_devdata
[  178.599288] gspca_main: Unknown symbol video_unregister_device
[  178.599431] gspca_main: Unknown symbol video_register_device
```

However when invoked with modprobe it works, and dmesg says:```
jack@vasquez:~$ dmesg | grep gspca
[  274.870156] calling  gspca_init+0x0/0x22 [gspca_main] @ 4648
[  274.870161] gspca: main v2.5.0 registered
[  274.870169] initcall gspca_init+0x0/0x22 [gspca_main] returned 0 after 4 usecs
```

---

### Post by nol_faich on 2009-05-17
From "gspca_main.ko" issue, it seems that "videodev" is missing.
When using modprobe, I think you that the module dependencies are loaded. Insmod does not do that.
Can you try a:
- "sudo modprobe videodev"
- "sudo insmod ... gspca_main.ko"
- if no unkown symbol, "sudo insmod gspca_gl860.ko"

---

### Post by Jack Malmostoso on 2009-05-17
Hey Nol, you were right, if I preload videodev I can insert gspca_main without errors. However, gspca_gl860 still gives me the same error as above:```
jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[  291.771322] gspca_gl860: disagrees about version of symbol usb_register_driver
[  291.771329] gspca_gl860: Unknown symbol usb_register_driver
[  291.771406] gspca_gl860: disagrees about version of symbol gspca_frame_add
[  291.771410] gspca_gl860: Unknown symbol gspca_frame_add
[  291.771565] gspca_gl860: disagrees about version of symbol usb_control_msg
[  291.771568] gspca_gl860: Unknown symbol usb_control_msg
[  291.771645] gspca_gl860: disagrees about version of symbol usb_deregister
[  291.771648] gspca_gl860: Unknown symbol usb_deregister
[  291.771751] gspca_gl860: disagrees about version of symbol gspca_disconnect
[  291.771755] gspca_gl860: Unknown symbol gspca_disconnect
[  291.771838] gspca_gl860: disagrees about version of symbol gspca_resume
[  291.771842] gspca_gl860: Unknown symbol gspca_resume
[  291.771918] gspca_gl860: disagrees about version of symbol gspca_dev_probe
[  291.771921] gspca_gl860: Unknown symbol gspca_dev_probe
[  291.772004] gspca_gl860: disagrees about version of symbol gspca_suspend
[  291.772008] gspca_gl860: Unknown symbol gspca_suspend
```DO you have an idea which module I should preload? I will try some out, see if I can find it myself :)

---

### Post by Jack Malmostoso on 2009-05-17
Ok, more weirdness. First of all, I am using 2.6.30-rc because 2.6.29 is almost not bootable on my laptop. Not sure why.
Anyway, upgraded to the latest 2.6.30-rc5 in Debian and I modprobed videodev and gspca_main. Then I ran the install script, and here is the output:```
jack@vasquez:~/Desktop/gspcav2$ ./install 
make -C "/lib/modules/2.6.30-rc5-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
make -C "/lib/modules/2.6.30-rc5-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
  CC [M]  /home/jack/Desktop/gspcav2/gl860.o
/home/jack/Desktop/gspcav2/gl860.c: In function &#8216;sd_probe&#8217;:
/home/jack/Desktop/gspcav2/gl860.c:522: warning: &#8216;gspca_dev&#8217; may be used uninitialized in this function
  CC [M]  /home/jack/Desktop/gspcav2/gl860-sysfs.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-f191.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503ms.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503sa.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503his.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jack/Desktop/gspcav2/gspca_gl860.mod.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
sudo rmmod gl860 2>/dev/null
sudo rmmod gspca_gl860 2>/dev/null
sudo insmod /lib/modules/2.6.30-rc5-amd64/kernel/drivers/media/video/gspca/gspca_main.ko 2>&1 | grep -v 'File exists'
sudo insmod gspca_gl860.ko
./install: line 14:  4682 Killed                  sudo insmod gspca_gl860.ko
jack@vasquez:~/Desktop/gspcav2$ 
Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741692] Oops: 0000 [#1] SMP 

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741697] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlan0/statistics/collisions

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741932] Stack:

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741941]  00000000ffffffed ffffffffa06309d8 ffffffffa06309d8 0000000000000000

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741948]  0000000000000000 ffffffff803d3bde ffff88007c57e030 ffffffffa06309d8

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741957] Call Trace:

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741960]  [<ffffffff803e4b8f>] ? usb_probe_interface+0xfc/0x14c

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741969]  [<ffffffff803d3bde>] ? driver_probe_device+0x8d/0x128

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741977]  [<ffffffff803d3cc8>] ? __driver_attach+0x4f/0x6f

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741983]  [<ffffffff803d3c79>] ? __driver_attach+0x0/0x6f

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741989]  [<ffffffff803d3558>] ? bus_for_each_dev+0x43/0x74

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.741995]  [<ffffffff803d2f26>] ? bus_add_driver+0xae/0x1de

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742001]  [<ffffffff803d3f39>] ? driver_register+0xa7/0x10e

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742012]  [<ffffffffa0080000>] ? sd_mod_init+0x0/0x1d8 [gspca_gl860]

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742023]  [<ffffffffa00801b1>] ? sd_mod_init+0x1b1/0x1d8 [gspca_gl860]

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742033]  [<ffffffff8020a06e>] ? do_one_initcall+0x6d/0x195

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742040]  [<ffffffff8030ef4a>] ? sysfs_addrm_finish+0x1d/0x219

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742047]  [<ffffffff8030eb51>] ? __sysfs_add_one+0x2b/0x84

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742007]  [<ffffffff803e4951>] ? usb_register_driver+0x7e/0xdf

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742053]  [<ffffffff80357329>] ? __bitmap_weight+0x3a/0x7e

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742061]  [<ffffffff802b035f>] ? __vunmap+0x9b/0xac

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742068]  [<ffffffff80266995>] ? load_module+0x13f4/0x1556

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742076]  [<ffffffff80266995>] ? load_module+0x13f4/0x1556

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742083]  [<ffffffff80285a68>] ? marker_update_probe_range+0x21/0x23d

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742090]  [<ffffffff80227e42>] ? default_spin_lock_flags+0x5/0xb

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742104]  [<ffffffff80258299>] ? notifier_call_chain+0x29/0x4c

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742112]  [<ffffffff803529c1>] ? __up_read+0x13/0x8e

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742117]  [<ffffffff80258553>] ? __blocking_notifier_call_chain+0x51/0x5f

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742124]  [<ffffffff80266b97>] ? sys_init_module+0xa0/0x1bf

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742131]  [<ffffffff8020fa42>] ? system_call_fastpath+0x16/0x1b

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742098]  [<ffffffff8048ba71>] ? _spin_lock_irqsave+0x1e/0x27

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742138] Code: 84 ff ff 53 49 c7 c0 40 1f 63 a0 b9 28 0a 00 00 48 c7 c2 10 cb 62 a0 e8 0b 9b ff ff 85 c0 89 c3 78 1e f6 05 d0 c5 ff ff 02 74 15 <8b> 34 25 9c 01 00 00 48 c7 c7 6f d2 62 a0 31 c0 e8 5a ac e6 df 

Message from syslogd@vasquez at Sun May 17 22:14:01 2009 ...
vasquez kernel: [  192.742211] CR2: 000000000000019c
```The module is however inserted, and cheese shows an image just fine!
Skype, on the other hand, still shows a green box.
In dmesg I get these two lines repeated a million times:```
jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[  303.104037] gspca_gl860: dev_0503ms_camera_settings [fini]
[  303.169028] gspca_gl860: dev_0503ms_camera_settings [ini]
```plus these lines here and there:```
[  335.165196] gspca_gl860: dev_0503ms_post_unset_alt [ini]
[  335.324024] gspca_gl860: dev_0503ms_post_unset_alt [fini]
[  363.797789] gspca_gl860: dev_0503ms_init_pre_alt [ini]
[  366.196030] gspca_gl860: dev_0503ms_camera_settings [ini]
[  366.412107] gspca_gl860: dev_0503ms_camera_settings [fini]
[  366.412113] gspca_gl860: dev_0503ms_init_pre_alt [fini]
[  335.165196] gspca_gl860: dev_0503ms_post_unset_alt [ini]
[  335.324024] gspca_gl860: dev_0503ms_post_unset_alt [fini]
[  363.797789] gspca_gl860: dev_0503ms_init_pre_alt [ini]
[  366.196030] gspca_gl860: dev_0503ms_camera_settings [ini]
[  366.412107] gspca_gl860: dev_0503ms_camera_settings [fini]
[  366.412113] gspca_gl860: dev_0503ms_init_pre_alt [fini]

```Hope this helps, I will try again booting 2.6.29 and if I get it up and running I'll do tests there too!

---

### Post by Jack Malmostoso on 2009-05-17
Lucky evening, 2.6.29 came up immediately!
So, here is dmesg right after installation of version 2.6.29h2:```
jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[   13.678778] calling  gl860_init+0x0/0x213 [gl860] @ 1547
[   13.716999] Genesys gl860: Genesys USB2.0 webcam driver startup
[   13.717030] Genesys gl860: Release: 0103
[   13.717031] Genesys gl860: Number of interfaces : 1
[   14.295421] Genesys gl860: probe 1=ff
[   14.300734] Genesys gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[   14.708180] Genesys gl860: ctrl transfer failed -110 [pc0 r2 v6000 i800a lg1]
[   14.713787] Genesys gl860: probe 2=40
[   14.824932] Genesys gl860: probe 2=26
[   14.830420] Genesys gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29f
[   16.436121] Genesys gl860: Camera is now controlling video device /dev/video0
[   16.441735] usbcore: registered new interface driver usb_gl860_driver
[   16.447388] initcall gl860_init+0x0/0x213 [gl860] returned 0 after 2697466 usecs
[  169.512375] Genesys gl860: usb_gl860_exit: Genesys USB2.0 webcam driver shutdown
[  169.512382] usbcore: deregistering interface driver usb_gl860_driver
[  169.512412] Genesys gl860: Genesys USB2.0 Camera disconnected
[  169.512438] Genesys gl860: Camera release resources video device /dev/video0
[  169.684421] calling  sd_mod_init+0x0/0x1d7 [gspca_gl860] @ 5498
[  169.684521] gspca_gl860: driver startup
[  170.187465] gspca_gl860: probe 1=ff
[  170.187470] gspca_gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[  170.192598] gspca_gl860: probe 2=26
[  170.192603] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29h2 (GSPCA)
[  171.808027] gspca_gl860: dev_0503ms_init_at_startup [fini]
[  171.809708] gspca_gl860: Camera is now controlling video device /dev/video0
[  171.809742] usbcore: registered new interface driver gspca_gl860
[  171.809747] gspca_gl860: driver registered
[  171.809854] initcall sd_mod_init+0x0/0x1d7 [gspca_gl860] returned 0 after 2075597 usecs
```
but neither cheese nor skype show an image... and dmesg reports nothing. /dev/video0 is created with the correct permissions. Cheese says:```
jack@vasquez:~$ cheese

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

libv4l2: error turning on stream: Input/output error
libv4l2: error dequeuing buf: Invalid argument
```
Hope this helps...

---

### Post by nol_faich on 2009-05-17
All is to be OK in dmesg.
If you can't have an image, there is a possible reason I experienced but not understood :(.
System calls the probe function of gspca_gl860 which calls the probe function is gspca_main which calls initialisation functions in gspca_gl860. The first initialisation function is the one gessing the sensor and subdriver to use, it also assigns start/stop functions wrt to sensor.
I discovered that functions are well assigned, but it is as if gspca_main was not aware of functions assigned. I fixed that using a fake initialisation function but it seems that you get a worse case as gspca_main never know function to use to start or stop the webcam.
With my tests using the gspca_main from synaptic'ed kernel (not the one obtained compiling the v4l sources), it is worse as gspca_main does not allocate memory and some toher things so that I segfault.
I have to read again sources to understand how this can happened... (why it is OK with compiled v4l and not with still existing gspca_main???)

It may be interesting to know what happens if you get the v4l sources and compile the driver using informations  in the README file.


I spotted the compilation warning and I will fix it tomorrow. Lines 516 and 517 must be inverted.

About messages "...[ini]" and "...[fini]", these messages are traces I added because you were able to compile the driver but you did not get any images. Traces were to know if functions were called or not.

---

### Post by nol_faich on 2009-05-18
No more warning at compilation. 
[https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29h3.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.29h3.tgz)

---

### Post by Jack Malmostoso on 2009-05-19
Hi Nol, thanks for the new version.
2.6.29, same as above:```
jack@vasquez:~/Desktop/gspcav2$ ./install 
make -C "/lib/modules/2.6.29-2-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-2-amd64'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-2-amd64'
make -C "/lib/modules/2.6.29-2-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-2-amd64'
  CC [M]  /home/jack/Desktop/gspcav2/gl860.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-sysfs.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-f191.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503ms.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503sa.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503his.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jack/Desktop/gspcav2/gspca_gl860.mod.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-2-amd64'
sudo rmmod gl860 2>/dev/null
[sudo] password for jack: 
sudo rmmod gspca_gl860 2>/dev/null
sudo insmod /lib/modules/2.6.29-2-amd64/kernel/drivers/media/video/gspca/gspca_main.ko 2>&1 | grep -v 'File exists'
sudo insmod gspca_gl860.ko
jack@vasquez:~/Desktop/gspcav2$ ls -al /dev/video0 
crw-rw----+ 1 root video 81, 0 2009-05-19 17:03 /dev/video0
jack@vasquez:~/Desktop/gspcav2$ cheese 

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** Message: Error: Stream contains no data.
gsttypefindelement.c(853): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

libv4l2: error turning on stream: Input/output error
libv4l2: error dequeuing buf: Invalid argument
jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[   13.247764] calling  gl860_init+0x0/0x213 [gl860] @ 1589
[   13.293721] Genesys gl860: Genesys USB2.0 webcam driver startup
[   13.304225] Genesys gl860: Release: 0103
[   13.309450] Genesys gl860: Number of interfaces : 1
[   13.868533] Genesys gl860: probe 1=ff
[   13.874056] Genesys gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[   13.884527] Genesys gl860: probe 2=26
[   13.889831] Genesys gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29f
[   15.576118] Genesys gl860: Camera is now controlling video device /dev/video0
[   15.581763] usbcore: registered new interface driver usb_gl860_driver
[   15.587311] initcall gl860_init+0x0/0x213 [gl860] returned 0 after 2279379 usecs
[  223.630869] Genesys gl860: usb_gl860_exit: Genesys USB2.0 webcam driver shutdown
[  223.630876] usbcore: deregistering interface driver usb_gl860_driver
[  223.630906] Genesys gl860: Genesys USB2.0 Camera disconnected
[  223.630932] Genesys gl860: Camera release resources video device /dev/video0
[  223.836171] calling  sd_mod_init+0x0/0x1d7 [gspca_gl860] @ 5260
[  223.836265] gspca_gl860: driver startup
[  224.343458] gspca_gl860: probe 1=ff
[  224.343463] gspca_gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[  224.348459] gspca_gl860: probe 2=26
[  224.348463] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29h3 (for GSPCA)
[  224.348467] gspca_gl860: dev_0503ms_init_at_startup [ini]
[  225.960027] gspca_gl860: dev_0503ms_init_at_startup [fini]
[  225.961704] gspca_gl860: Camera is now controlling video device /dev/video0
[  225.961737] usbcore: registered new interface driver gspca_gl860
[  225.961742] gspca_gl860: driver registered
[  225.961850] initcall sd_mod_init+0x0/0x1d7 [gspca_gl860] returned 0 after 2075839 usecs
```

---

### Post by Jack Malmostoso on 2009-05-19
And this is 2.6.30-rc5:```
jack@vasquez:~/Desktop/gspcav2$ sudo modprobe videodev 
jack@vasquez:~/Desktop/gspcav2$ sudo modprobe gspca_main 
jack@vasquez:~/Desktop/gspcav2$ ./install 
make -C "/lib/modules/2.6.30-rc5-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
  CLEAN   /home/jack/Desktop/gspcav2/.tmp_versions
  CLEAN   /home/jack/Desktop/gspcav2/Module.symvers /home/jack/Desktop/gspcav2/Module.markers /home/jack/Desktop/gspcav2/modules.order
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
make -C "/lib/modules/2.6.30-rc5-amd64/build"    SUBDIRS="/home/jack/Desktop/gspcav2" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
  CC [M]  /home/jack/Desktop/gspcav2/gl860.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-sysfs.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-f191.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503ms.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503sa.o
  CC [M]  /home/jack/Desktop/gspcav2/gl860-dev-0503his.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jack/Desktop/gspcav2/gspca_gl860.mod.o
  LD [M]  /home/jack/Desktop/gspcav2/gspca_gl860.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-rc5-amd64'
sudo rmmod gl860 2>/dev/null
sudo rmmod gspca_gl860 2>/dev/null
sudo insmod /lib/modules/2.6.30-rc5-amd64/kernel/drivers/media/video/gspca/gspca_main.ko 2>&1 | grep -v 'File exists'
sudo insmod gspca_gl860.ko
jack@vasquez:~/Desktop/gspcav2$ skype 
ALSA lib ../../../src/pcm/pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib ../../../src/pcm/pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib ../../../src/pcm/pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Starting the process...
Skype Xv: Xv ports available: 17
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 79
jack@vasquez:~/Desktop/gspcav2$ dmesg | grep gl860
[  187.192648] calling  sd_mod_init+0x0/0x1d7 [gspca_gl860] @ 5412
[  187.192655] gspca_gl860: driver startup
[  187.707483] gspca_gl860: probe 1=ff
[  187.707487] gspca_gl860: discriminating 'ms'(OV2640) and 'sa'(OV9655) subdriver
[  187.712614] gspca_gl860: probe 2=26
[  187.712619] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms) v2.6.29h3 (for GSPCA)
[  187.712623] gspca_gl860: dev_0503ms_init_at_startup [ini]
[  189.325026] gspca_gl860: dev_0503ms_init_at_startup [fini]
[  189.326713] gspca_gl860: Camera is now controlling video device /dev/video0
[  189.326748] usbcore: registered new interface driver gspca_gl860
[  189.326753] gspca_gl860: driver registered
[  189.326767] initcall sd_mod_init+0x0/0x1d7 [gspca_gl860] returned 0 after 2084081 usecs
[  197.812143] gspca_gl860: dev_0503ms_init_pre_alt [ini]
[  200.724024] gspca_gl860: dev_0503ms_init_pre_alt [fini]
[  201.463066] gspca_gl860: dev_0503ms_post_unset_alt [ini]
[  201.616028] gspca_gl860: dev_0503ms_post_unset_alt [fini]
[  203.704381] gspca_gl860: dev_0503ms_init_pre_alt [ini]
[  206.324025] gspca_gl860: dev_0503ms_init_pre_alt [fini]
[  229.875922] gspca_gl860: dev_0503ms_post_unset_alt [ini]
[  230.040018] gspca_gl860: dev_0503ms_post_unset_alt [fini]
[  254.605185] gspca_gl860: dev_0503ms_init_pre_alt [ini]
[  257.192024] gspca_gl860: dev_0503ms_init_pre_alt [fini]
[  266.185824] gspca_gl860: dev_0503ms_post_unset_alt [ini]
[  266.337030] gspca_gl860: dev_0503ms_post_unset_alt [fini]
[  289.036935] gspca_gl860: dev_0503ms_init_pre_alt [ini]
[  291.668025] gspca_gl860: dev_0503ms_init_pre_alt [fini]
[  296.227492] gspca_gl860: dev_0503ms_post_unset_alt [ini]
[  296.384028] gspca_gl860: dev_0503ms_post_unset_alt [fini]
```
This is what I get in cheese:

[[IMG]http://img413.imageshack.us/img413/1626/20090519171031.th.jpg[/IMG]](http://img413.imageshack.us/my.php?image=20090519171031.jpg)

And in Skype I only get a green screen. In the output you can see three lines when I start the camera in Skype.

Nol, if you're still up for it, maybe I can send you my laptop and you try to fix things directly with the hardware at hand, what do you think?

---

### Post by nol_faich on 2009-05-21
Hi Jack,

I progress with gspca, I no more need fake functions at probe time.
I will now investigate the issues with the driver using the available gspca_main instead of the one compiled from v4l sources.

About Skype, I need to know the libv4l's log you get typing this in a terminal (there may be also an interesting trace from cheese in the console):

LIBV4L2_LOG_FILENAME=/home/jack/libv4l.log
skype

The libv4l's log file may also be interesting for issue with 2.6.29 kernel.

I think that some ssh may also be OK for tests if we does not achieve something good.

---

### Post by nol_faich on 2009-05-21
I found the reason of issue: the webcam data structure in gspca.h has changed with each kernel version. So the driver needs to be compiled with the gspca.h used for gspca_main else gspca_main is not able to read properly the data about webcam.
On saturday, I will make a new release.

---

### Post by nol_faich on 2009-05-22
@ ALL

New release is here: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30a.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30a.tgz)

The installation is easy and left your system untouched after reboot.
Decompress the tarball and type ./install
This release is working with 05e3:f191 and should work with 05e3:0503 "ms".
I need test with other flavours.

First test:
LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so camorama

Please try small, mean and large image sizes.
If you have v4l2ucp, you can test all settings with it.

[s]Second test (if you don't have v4l2ucp):
LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so vlc v4l:// :v4l-vdev="/dev/video0"
and tests all settings with "v4l2 controls" in VLC's "extended settings".[/s]

---

### Post by Jack Malmostoso on 2009-05-23
Hi Nol, thanks for the new version.
The driver compiles fine under 2.6.30-rc5 and works fine in Ekiga (3.2.1) and Cheese:

[[IMG]http://img14.imageshack.us/img14/6941/ekiga.th.png[/IMG]](http://img14.imageshack.us/my.php?image=ekiga.png)

[[IMG]http://img10.imageshack.us/img10/226/20090523084435.th.jpg[/IMG]](http://img10.imageshack.us/my.php?image=20090523084435.jpg)

Images are a bit on the blue side, but maybe it's the light in my room, not sure.
Camorama on the other hand behaves funny. Small images appear but with all the wrong colors:

[[IMG]http://img33.imageshack.us/img33/184/webcam1243061033.th.png[/IMG]](http://img33.imageshack.us/my.php?image=webcam1243061033.png)

and larger images don't appear at all:

[[IMG]http://img10.imageshack.us/img10/2943/webcam1243060981.th.png[/IMG]](http://img10.imageshack.us/my.php?image=webcam1243060981.png)

Output:

```
jack@vasquez:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama -D

VIDIOCGCAP
device name = USB 2.0 PC Camera
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 1600
max height = 1200
min width = 640
min height = 480

VIDIOCGWIN
x = 0
y = 0
width = 1600
height = 1200
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 0
hue = 0
colour = 32896
contrast = 0
whiteness = 33288
colour depth = 24
24bit RGB

VIDIOCGMBUF
mb.size = 67108864
mb.frames = 4
mb.offset = 16777216
update_tooltip called
tip - acap off
** Message: SET PIC
** Message: SET PIC
update_tooltip called
tip - acap off
```

Dmesg doesn't seem to give anything interesting:```
jack@vasquez:~$ dmesg | grep gl860
[  320.253948] calling  sd_mod_init+0x0/0x1de [gspca_gl860] @ 4885
[  320.253953] gspca_gl860: driver startup - v2.6.30a (for GSPCA)
[  320.759468] gspca_gl860: probe 1=ff
[  320.759472] gspca_gl860: probing for sensor OV2640 or OV9655
[  320.764348] gspca_gl860: probe 2= 0
[  320.872969] gspca_gl860: probe 2= 0
[  320.980847] gspca_gl860: probe 2= 0
[  321.088972] gspca_gl860: probe 2= 0
[  321.196850] gspca_gl860: probe 2= 0
[  321.304849] gspca_gl860: probe 2= 0
[  321.412846] gspca_gl860: probe 2= 0
[  321.521847] gspca_gl860: probe 2= 0
[  321.628857] gspca_gl860: probe 2= 0
[  321.736854] gspca_gl860: probe 2= 0
[  321.844855] gspca_gl860: probe 2= 0
[  321.953857] gspca_gl860: probe 2= 0
[  322.060981] gspca_gl860: probe 2= 0
[  322.168861] gspca_gl860: probe 2= 0
[  322.276987] gspca_gl860: probe 2= 0
[  322.384861] gspca_gl860: probe 2= 0
[  322.492863] gspca_gl860: probe 2= 0
[  322.600864] gspca_gl860: probe 2= 0
[  322.708866] gspca_gl860: probe 2= 0
[  322.816987] gspca_gl860: probe 2= 0
[  322.924867] gspca_gl860: probe 2= 0
[  323.032869] gspca_gl860: probe 2= 0
[  323.141992] gspca_gl860: probe 2= 0
[  323.248871] gspca_gl860: probe 2= 0
[  323.356997] gspca_gl860: probe 2= 0
[  323.464875] gspca_gl860: probe 2= 0
[  323.572876] gspca_gl860: probe 2= 0
[  323.681001] gspca_gl860: probe 2= 0
[  323.788877] gspca_gl860: probe 2= 0
[  323.896879] gspca_gl860: probe 2= 0
[  324.004879] gspca_gl860: probe 2= 0
[  324.108037] gspca_gl860: no relevant sensor answer (00=31/FF=0)
[  324.108042] gspca_gl860: *  1.3Mpixels -> set the 'sa' flavour
[  324.108045] gspca_gl860: *  2.0Mpixels -> set the 'ms' flavour
[  324.108048] gspca_gl860: Trying 'ms'
[  324.108051] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms)
[  325.733618] gspca_gl860: Camera is now controlling video device /dev/video0
[  325.733658] usbcore: registered new interface driver gspca_gl860
[  325.733663] gspca_gl860: driver registered
[  325.733676] initcall sd_mod_init+0x0/0x1de [gspca_gl860] returned 0 after 5351282 usecs
[ 1737.133956] gspca_gl860 2-6:1.0: no reset_resume for driver gspca_gl860?
[ 1739.907482] gspca_gl860: probe 1=ff
[ 1739.907485] gspca_gl860: probing for sensor OV2640 or OV9655
[ 1739.912357] gspca_gl860: probe 2=26
[ 1739.912360] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms)
[ 1741.505675] gspca_gl860: Camera is now controlling video device /dev/video0
```

At 1737 I suspended to ram the laptop.
Skype keeps on giving the green window, and I found this:

[http://osdir.com/ml/linux.drivers.spca50x.devel/2008-05/msg00029.html](http://osdir.com/ml/linux.drivers.spca50x.devel/2008-05/msg00029.html)

Not sure if it helps or not.

---

### Post by nol_faich on 2009-05-23
Colors in Camorama are OK! It inverts blue and red because of a conception mistake. Using libv4l2 the Bayer images are translated to the image format required by Camorama but Camorama does not read it on a suitable manner.
If you set the hue to the max, red and blue are swapped.
The image conversion by the standalone driver is also wrong.
---------------------------------
About Skype, there is likely an image size and/or format issue so that I need to know what is asked by skype. Therefore I need the libv4l's log and skype's traces you get typing this in a terminal:

LIBV4L2_LOG_FILENAME=/home/jack/libv4l.log
export LIBV4L2_LOG_FILENAME
skype

I would also like to know if the non gspca driver is working (install with "./install -t" to enable traces in dmesg).
----------------------------------
Does Cheese is also unable to display big sizes with the gspca_gl860?
If it is as with my laptop, Cheese proposes two size, the lowest and the biggest. does the biggest is also wrong?

Two things are hurting me gspca:
- I can't no more set the alternate setting (USB has several of it with different capabilities, only one is able to get image with big size so that the issue is maybe related to that)
- The Windows logged sequence of data sent and webcam switched on is no more respected because gspca does not allowed to switch on in the middle of data sent.

---

### Post by Jack Malmostoso on 2009-05-23
So, I cannot get the log with skype. Not sure why, but it does not even create the file. Hooray for closed source software, I guess.
As for cheese, it works at 640x480, but all higher sizes (800x600, 1280x960, 1600x1200) are garbled. The HUGE log I attach here is taken like this: open cheese, change to 800x600, change to 1280x960, change to 1600x1200, close cheese:```
libv4l2: open: 25
request == VIDIOC_QUERYCAP
result == 0
request == VIDIOC_ENUMINPUT
result == 0
request == VIDIOC_ENUMINPUT
result == -1 (Invalid argument)
request == VIDIOC_ENUMSTD
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_G_STD
result == 0
request == VIDIOC_G_INPUT
result == 0
request == VIDIOC_ENUM_FMT
  index: 0, description: GBRG
result == 0
request == VIDIOC_ENUM_FMT
  index: 1, description: RGB3
result == 0
request == VIDIOC_ENUM_FMT
  index: 2, description: BGR3
result == 0
request == VIDIOC_ENUM_FMT
  index: 3, description: YU12
result == 0
request == VIDIOC_ENUM_FMT
  index: 4, description: YV12
result == 0
request == VIDIOC_ENUM_FMT
  index: 5, description: 
result == -1 (Invalid argument)
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: YU12result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: YU12 640x480
  field: 1 bytesperline: 640 imagesize460800
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: YU12 1600x1200
  field: 1 bytesperline: 1600 imagesize2880000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: YV12result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: YV12 640x480
  field: 1 bytesperline: 640 imagesize460800
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: YV12 1600x1200
  field: 1 bytesperline: 1600 imagesize2880000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: BGR3result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: BGR3 640x480
  field: 1 bytesperline: 1920 imagesize921600
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: BGR3 1600x1200
  field: 1 bytesperline: 4800 imagesize5760000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: RGB3result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: RGB3 640x480
  field: 1 bytesperline: 1920 imagesize921600
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: RGB3 1600x1200
  field: 1 bytesperline: 4800 imagesize5760000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_G_FMT
  pixelformat: GBRG 640x480
  field: 1 bytesperline: 640 imagesize307200
  colorspace: 8, priv: 0
result == 0
VIDIOC_S_FMT app requesting: YU12
VIDIOC_S_FMT converting from: GBRG
request == VIDIOC_S_FMT
  pixelformat: YU12 1600x1200
  field: 1 bytesperline: 1600 imagesize2880000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_G_PARM
result == 0
request == VIDIOC_REQBUFS
  count: 2 type: 1 memory: 1
result == 0
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 0, seen by app at: 0x7f40caab2000
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 1, seen by app at: 0x7f40cbab2000
libv4l2: mapped buffer 0 at 0x7f40ca8dd000
libv4l2: mapped buffer 1 at 0x7f40ca708000
request == VIDIOC_QBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMON
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMOFF
result == 0
libv4l2: v4l2 fake buffer munmap 0x7f40caab2000, 16777216
libv4l2: v4l2 fake buffer munmap 0x7f40cbab2000, 16777216
libv4l2: unmapped buffer 0
libv4l2: unmapped buffer 1
libv4l2: close: 25
libv4l2: open: 31
request == VIDIOC_QUERYCAP
result == 0
request == VIDIOC_ENUMINPUT
result == 0
request == VIDIOC_ENUMINPUT
result == -1 (Invalid argument)
request == VIDIOC_ENUMSTD
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_G_STD
result == 0
request == VIDIOC_G_INPUT
result == 0
request == VIDIOC_ENUM_FMT
  index: 0, description: GBRG
result == 0
request == VIDIOC_ENUM_FMT
  index: 1, description: RGB3
result == 0
request == VIDIOC_ENUM_FMT
  index: 2, description: BGR3
result == 0
request == VIDIOC_ENUM_FMT
  index: 3, description: YU12
result == 0
request == VIDIOC_ENUM_FMT
  index: 4, description: YV12
result == 0
request == VIDIOC_ENUM_FMT
  index: 5, description: 
result == -1 (Invalid argument)
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: YU12result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: YU12 640x480
  field: 1 bytesperline: 640 imagesize460800
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: YU12 1600x1200
  field: 1 bytesperline: 1600 imagesize2880000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: YV12result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: YV12 640x480
  field: 1 bytesperline: 640 imagesize460800
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: YV12 1600x1200
  field: 1 bytesperline: 1600 imagesize2880000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: BGR3result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: BGR3 640x480
  field: 1 bytesperline: 1920 imagesize921600
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: BGR3 1600x1200
  field: 1 bytesperline: 4800 imagesize5760000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_ENUM_FRAMESIZES
  index: 0 pixelformat: RGB3result == -1 (Invalid argument)
request == VIDIOC_TRY_FMT
  pixelformat: RGB3 640x480
  field: 1 bytesperline: 1920 imagesize921600
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_TRY_FMT
  pixelformat: RGB3 1600x1200
  field: 1 bytesperline: 4800 imagesize5760000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_G_FMT
  pixelformat: GBRG 1600x1200
  field: 1 bytesperline: 1600 imagesize1920000
  colorspace: 8, priv: 3
result == 0
VIDIOC_S_FMT app requesting: YU12
VIDIOC_S_FMT converting from: GBRG
request == VIDIOC_S_FMT
  pixelformat: YU12 640x480
  field: 1 bytesperline: 640 imagesize460800
  colorspace: 8, priv: 0
result == 0
request == VIDIOC_G_PARM
result == 0
request == VIDIOC_REQBUFS
  count: 2 type: 1 memory: 1
result == 0
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 0, seen by app at: 0x7f40caab2000
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 1, seen by app at: 0x7f40cbab2000
libv4l2: mapped buffer 0 at 0x7f40d628a000
libv4l2: mapped buffer 1 at 0x7f40d623f000
request == VIDIOC_QBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMON
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMOFF
result == 0
libv4l2: v4l2 fake buffer munmap 0x7f40caab2000, 16777216
libv4l2: v4l2 fake buffer munmap 0x7f40cbab2000, 16777216
libv4l2: unmapped buffer 0
libv4l2: unmapped buffer 1
libv4l2: close: 31
libv4l2: open: 31
request == VIDIOC_QUERYCAP
result == 0
request == VIDIOC_ENUMINPUT
result == 0
request == VIDIOC_ENUMINPUT
result == -1 (Invalid argument)
request == VIDIOC_ENUMSTD
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_G_STD
result == 0
request == VIDIOC_S_INPUT
result == 0
request == VIDIOC_G_FMT
  pixelformat: GBRG 640x480
  field: 1 bytesperline: 640 imagesize307200
  colorspace: 8, priv: 0
result == 0
VIDIOC_S_FMT app requesting: YU12
VIDIOC_S_FMT converting from: GBRG
request == VIDIOC_S_FMT
  pixelformat: YU12 800x600
  field: 1 bytesperline: 800 imagesize720000
  colorspace: 8, priv: 1
result == 0
request == VIDIOC_G_PARM
result == 0
request == VIDIOC_REQBUFS
  count: 2 type: 1 memory: 1
result == 0
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 0, seen by app at: 0x7f40caab2000
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 1, seen by app at: 0x7f40cbab2000
libv4l2: mapped buffer 0 at 0x7f40d625f000
libv4l2: mapped buffer 1 at 0x7f40cf928000
request == VIDIOC_QBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMON
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMOFF
result == 0
libv4l2: v4l2 fake buffer munmap 0x7f40caab2000, 16777216
libv4l2: v4l2 fake buffer munmap 0x7f40cbab2000, 16777216
libv4l2: unmapped buffer 0
libv4l2: unmapped buffer 1
libv4l2: close: 31
libv4l2: open: 31
request == VIDIOC_QUERYCAP
result == 0
request == VIDIOC_ENUMINPUT
result == 0
request == VIDIOC_ENUMINPUT
result == -1 (Invalid argument)
request == VIDIOC_ENUMSTD
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_G_STD
result == 0
request == VIDIOC_S_INPUT
result == 0
request == VIDIOC_G_FMT
  pixelformat: GBRG 800x600
  field: 1 bytesperline: 800 imagesize480000
  colorspace: 8, priv: 1
result == 0
VIDIOC_S_FMT app requesting: YU12
VIDIOC_S_FMT converting from: GBRG
request == VIDIOC_S_FMT
  pixelformat: YU12 1280x960
  field: 1 bytesperline: 1280 imagesize1843200
  colorspace: 8, priv: 2
result == 0
request == VIDIOC_G_PARM
result == 0
request == VIDIOC_REQBUFS
  count: 2 type: 1 memory: 1
result == 0
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 0, seen by app at: 0x7f40caab2000
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 1, seen by app at: 0x7f40cbab2000
libv4l2: mapped buffer 0 at 0x7f40cf872000
libv4l2: mapped buffer 1 at 0x7f40ce692000
request == VIDIOC_QBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMON
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMOFF
result == 0
libv4l2: v4l2 fake buffer munmap 0x7f40caab2000, 16777216
libv4l2: v4l2 fake buffer munmap 0x7f40cbab2000, 16777216
libv4l2: unmapped buffer 0
libv4l2: unmapped buffer 1
libv4l2: close: 31
libv4l2: open: 31
request == VIDIOC_QUERYCAP
result == 0
request == VIDIOC_ENUMINPUT
result == 0
request == VIDIOC_ENUMINPUT
result == -1 (Invalid argument)
request == VIDIOC_ENUMSTD
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == 0
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_QUERYCTRL
result == -1 (Invalid argument)
request == VIDIOC_G_STD
result == 0
request == VIDIOC_S_INPUT
result == 0
request == VIDIOC_G_FMT
  pixelformat: GBRG 1280x960
  field: 1 bytesperline: 1280 imagesize1228800
  colorspace: 8, priv: 2
result == 0
VIDIOC_S_FMT app requesting: YU12
VIDIOC_S_FMT converting from: GBRG
request == VIDIOC_S_FMT
  pixelformat: YU12 1600x1200
  field: 1 bytesperline: 1600 imagesize2880000
  colorspace: 8, priv: 3
result == 0
request == VIDIOC_G_PARM
result == 0
request == VIDIOC_REQBUFS
  count: 2 type: 1 memory: 1
result == 0
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 0, seen by app at: 0x7f40caab2000
request == VIDIOC_QUERYBUF
result == 0
libv4l2: Fake (conversion) mmap buf 1, seen by app at: 0x7f40cbab2000
libv4l2: mapped buffer 0 at 0x7f40ce5e9000
libv4l2: mapped buffer 1 at 0x7f40ce414000
request == VIDIOC_QBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_STREAMON
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
request == VIDIOC_DQBUF
result == 0
request == VIDIOC_QBUF
result == 0
```

---

### Post by nol_faich on 2009-05-23
From the log file with Cheese, all seems to be OK, so the driver is guilty and more likely gspca. The three missing sizes are using a different "altsetting" from the 640x480. I guess the USB communication is oddly initialized by gspca.
In the attachement, there is a script to log USB transfers and a c++ file to compile (command line to use at the very begin of file) to provide relevant data. Please start monusb (./monusb) , start cheese, try all sizes, ctrl+c to stop monusb, execute the command line given by monusb and run relogL (use "relogL ecoute > cheese_ms.c") to provide cheese_ms.c. From this file, I will know if there is the altsetting issue.
-------------------------------------------------
If there is no log with Skype, this could mean it works in v4l1, not in v4l2.
Have you tried to launch it with:
LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so skype
-------------------------------------------------
A funky thing, to test settings with vlc (ctrl+e or tools/extended settings/v4l2 controls), launch it with the preloading (theoretically only to get v4l applications working) specifying vlc to use v4l2:
LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so vlc v4l2:// :v4l2-vdev="/dev/video0"

---

### Post by BUGabundo on 2009-05-23
```

:~/temp/gspca_gl860$ ./install 
make -C "/lib/modules/2.6.30-5-generic/build"    SUBDIRS="/home/bugabundo/temp/gspca_gl860" clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-5-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-5-generic'
make -C "/lib/modules/2.6.30-5-generic/build"    SUBDIRS="/home/bugabundo/temp/gspca_gl860" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-5-generic'
  CC [M]  /home/bugabundo/temp/gspca_gl860/gl860.o
  CC [M]  /home/bugabundo/temp/gspca_gl860/gl860-sysfs.o
  CC [M]  /home/bugabundo/temp/gspca_gl860/gl860-dev-f191.o
  CC [M]  /home/bugabundo/temp/gspca_gl860/gl860-dev-0503ms.o
  CC [M]  /home/bugabundo/temp/gspca_gl860/gl860-dev-0503sa.o
  CC [M]  /home/bugabundo/temp/gspca_gl860/gl860-dev-0503his.o
  LD [M]  /home/bugabundo/temp/gspca_gl860/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/bugabundo/temp/gspca_gl860/gspca_gl860.mod.o
  LD [M]  /home/bugabundo/temp/gspca_gl860/gspca_gl860.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-5-generic'
sudo modprobe gspca_main
WARNING: All config files need .conf: /etc/modprobe.d/linux-wlan-ng, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
sudo insmod gspca_gl860.ko
bugabundo@blubug:~/temp/gspca_gl860$ uname -a
Linux blubug 2.6.30-5-generic #6-Ubuntu SMP Mon May 11 20:46:57 UTC 2009 x86_64 GNU/Linux
:~/temp/gspca_gl860$ 

```

cheese works, vlc doesnt
```
$ vlc 
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000369] main interaction debug: thread started
[00000369] main interaction debug: thread 140487883757904 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000371] main input debug: Creating an input for 'Media Library'
[00000371] main input debug: Input is a meta file: disabling unneeded options
[00000371] main input debug: `file/xspf-open:///home/bugabundo/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/bugabundo/.local/share/vlc/ml.xspf'
[00000371] main input debug: creating access 'file' path='/home/bugabundo/.local/share/vlc/ml.xspf'
[00000372] main access debug: looking for access module: 3 candidates
[00000372] access_file access debug: opening file `/home/bugabundo/.local/share/vlc/ml.xspf'
[00000372] main access debug: using access module "access_file"
[00000372] main access debug: TIMER module_Need() : 0.905 ms - Total 0.905 ms / 1 intvls (Avg 0.905 ms)
[00000377] main stream debug: Using AStream*Stream
[00000377] main stream debug: pre-buffering...
[00000377] main stream debug: received first data for our buffer
[00000371] main input debug: creating demux: access='file' demux='xspf-open' path='/home/bugabundo/.local/share/vlc/ml.xspf'
[00000378] main demux debug: looking for demux module: 1 candidate
[00000378] playlist demux debug: using XSPF playlist reader
[00000378] main demux debug: using demux module "playlist"
[00000378] main demux debug: TIMER module_Need() : 0.525 ms - Total 0.525 ms / 1 intvls (Avg 0.525 ms)
[00000371] main input debug: `file/xspf-open:///home/bugabundo/.local/share/vlc/ml.xspf' successfully opened
[00000393] main xml debug: looking for xml module: 2 candidates
[00000393] main xml debug: using xml module "xml"
[00000393] main xml debug: TIMER module_Need() : 0.829 ms - Total 0.829 ms / 1 intvls (Avg 0.829 ms)
[00000378] playlist demux debug: parsed 0 tracks successfully
[00000393] main xml debug: removing module "xml"
[00000371] main input debug: EOF reached
[00000371] main input debug: control type=1
[00000378] main demux debug: removing module "playlist"
[00000372] main access debug: removing module "access_file"
[00000371] main input debug: TIMER input launching for 'Media Library' : 4.389 ms - Total 4.389 ms / 1 intvls (Avg 4.389 ms)
[00000395] main preparser debug: thread started
[00000395] main preparser debug: waiting for thread initialization
[00000395] main preparser debug: thread 140487869028688 (preparser) created at priority 0 (playlist/thread.c:79)
[00000396] main fetcher debug: thread started
[00000396] main fetcher debug: waiting for thread initialization
[00000396] main fetcher debug: thread 140487846431056 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000370] main playlist debug: thread started
[00000370] main playlist debug: waiting for thread initialization
[00000370] main playlist debug: rebuilding array of current - root Playlist
[00000370] main playlist debug: rebuild done - 0 items, index -1
[00000370] main playlist debug: thread 140487838038352 (playlist) created at priority 0 (playlist/thread.c:117)
[00000397] main interface debug: looking for interface module: 1 candidate
[00000397] main interface debug: using interface module "hotkeys"
[00000397] main interface debug: TIMER module_Need() : 0.251 ms - Total 0.251 ms / 1 intvls (Avg 0.251 ms)
[00000397] main interface debug: thread started
[00000397] main interface debug: thread 140487829645648 (interface) created at priority 0 (interface/interface.c:168)
[00000399] main interface debug: looking for interface module: 1 candidate
[00000399] main interface debug: using interface module "inhibit"
[00000399] main interface debug: TIMER module_Need() : 9.693 ms - Total 9.693 ms / 1 intvls (Avg 9.693 ms)
[00000399] main interface debug: thread started
[00000399] main interface debug: thread 140487819143504 (interface) created at priority 0 (interface/interface.c:168)
[00000401] main interface debug: looking for interface module: 1 candidate
[00000401] main interface debug: using interface module "screensaver"
[00000401] main interface debug: TIMER module_Need() : 0.216 ms - Total 0.216 ms / 1 intvls (Avg 0.216 ms)
[00000401] main interface debug: thread started
[00000401] main interface debug: thread 140487808641360 (interface) created at priority 0 (interface/interface.c:168)
[00000403] main interface debug: looking for interface module: 22 candidates
[00000403] main interface debug: using interface module "signals"
[00000403] main interface debug: TIMER module_Need() : 0.181 ms - Total 0.181 ms / 1 intvls (Avg 0.181 ms)
[00000403] main interface debug: thread started
[00000403] main interface debug: thread 140487789746512 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000405] main interface debug: looking for interface module: 4 candidates
[00000405] main interface debug: using interface module "qt4"
[00000405] main interface debug: TIMER module_Need() : 145.465 ms - Total 145.465 ms / 1 intvls (Avg 145.465 ms)
[00000405] main interface debug: thread started
[00000405] main interface debug: thread 140487710595408 (interface) created at priority 0 (interface/interface.c:168)
[00000405] qt4 interface debug: Error while initializing qt-specific localization
[00000405] qt4 interface debug: Initialization of Capture device panel
[00000405] qt4 interface debug: Enter Key pressed
[00000405] qt4 interface debug: New item: v4l2://
[00000405] qt4 interface debug: New Option: :v4l2-dev=/dev/video0
[00000405] qt4 interface debug: New Option: :v4l2-adev=
[00000405] qt4 interface debug: New Option: :v4l2-standard=0
[00000370] main playlist debug: adding item `v4l2://' ( v4l2:// )
[00000370] main playlist debug: rebuilding array of current - root Playlist
[00000370] main playlist debug: rebuild done - 1 items, index -1
[00000370] main playlist debug: starting new item
[00000370] main playlist debug: processing request item v4l2:// node null skip 0
[00000370] main playlist debug: resyncing on v4l2://
[00000370] main playlist debug: v4l2:// is at 0
[00000370] main playlist debug: creating new input thread
[00000408] main input debug: Creating an input for 'v4l2://'
[00000408] main input debug: thread started
[00000408] main input debug: waiting for thread initialization
[00000408] main input debug: `v4l2://' gives access `v4l2' demux `' path `'
[00000408] main input debug: creating demux: access='v4l2' demux='' path=''
[00000409] main demux debug: looking for access_demux module: 1 candidate
[00000409] v4l2 demux debug: ALSA input support available
[00000409] v4l2 demux debug: Trying direct kernel v4l2
[00000409] v4l2 demux debug: opening '/dev/video0' as video
[00000409] v4l2 demux debug: V4L2 device: USB 2.0 PC Camera using driver: gspca_gl860 (version: 2.5.0) on usb-0000:00:1d.7-6
[00000409] v4l2 demux debug: the device has the capabilities: (X) Video Capure, ( ) Audio, ( ) Tuner
[00000409] v4l2 demux debug: supported I/O methods are: (X) Read/Write, (X) Streaming, ( ) Asynchronous
[00000409] v4l2 demux debug: video input 0 (gspca_gl860) has type: External analog input *
[00000409] v4l2 demux debug: device codec GBRG (GBRG) not supported as access_demux
[00000409] v4l2 demux debug: Extended control API supported by v4l2 driver
[00000409] v4l2 demux debug: Available control: Brightness (980900)
[00000409] v4l2 demux debug:     integer control
[00000409] v4l2 demux debug:     valid values: 0 to 128 by steps of 4
[00000409] v4l2 demux debug:     default value: 70
[00000409] v4l2 demux debug:     current value: 70
[00000409] v4l2 demux debug: Available control: Contrast (980901)
[00000409] v4l2 demux debug:     integer control
[00000409] v4l2 demux debug:     valid values: 0 to 3 by steps of 1
[00000409] v4l2 demux debug:     default value: 0
[00000409] v4l2 demux debug:     current value: 0
[00000409] v4l2 demux debug: Available control: Hue (980903)
[00000409] v4l2 demux debug:     integer control
[00000409] v4l2 demux debug:     valid values: 0 to 1 by steps of 1
[00000409] v4l2 demux debug:     default value: 0
[00000409] v4l2 demux debug:     current value: 0
[00000409] v4l2 demux debug: Available control: Gamma (980910)
[00000409] v4l2 demux debug:     integer control
[00000409] v4l2 demux debug:     valid values: 0 to 2 by steps of 1
[00000409] v4l2 demux debug:     default value: 0
[00000409] v4l2 demux debug:     current value: 0
[00000409] v4l2 demux debug: Available control: Mirror (980914)
[00000409] v4l2 demux debug:     boolean control
[00000409] v4l2 demux debug:     default value: 0
[00000409] v4l2 demux debug:     current value: 0
[00000409] v4l2 demux debug: Available control: Flip (980915)
[00000409] v4l2 demux debug:     boolean control
[00000409] v4l2 demux debug:     default value: 0
[00000409] v4l2 demux debug:     current value: 0
[00000409] v4l2 demux debug: Available control: 50Hz (980918)
[00000409] v4l2 demux debug:     boolean control
[00000409] v4l2 demux debug:     default value: 1
[00000409] v4l2 demux debug:     current value: 1
[00000409] v4l2 demux debug: Available control: Sharpness (98091b)
[00000409] v4l2 demux debug:     integer control
[00000409] v4l2 demux debug:     valid values: 0 to 40 by steps of 1
[00000409] v4l2 demux debug:     default value: 20
[00000409] v4l2 demux debug:     current value: 20
[00000409] v4l2 demux debug: Available control: Backlight (98091c)
[00000409] v4l2 demux debug:     integer control
[00000409] v4l2 demux debug:     valid values: 0 to 64 by steps of 2
[00000409] v4l2 demux debug:     default value: 0
[00000409] v4l2 demux debug:     current value: 0
[00000409] v4l2 demux warning: Could not select any of the default chromas; attempting to open as MPEG encoder card (access)
[00000409] v4l2 demux debug: opening '(null)' as audio
[00000408] main input debug: thread 140487532636496 (input) created at priority 10 (input/input.c:370)
[00000405] qt4 interface debug: Updating the stream status: 3
[00000409] v4l2 demux debug: opened adev=`hw' stereo 48000Hz
[00000409] v4l2 demux debug: new audio es 2 channels 48000Hz
[00000408] main input debug: selecting program id=0
[00000405] qt4 interface debug: New Event: type 1108
[00000409] main demux debug: using access_demux module "v4l2"
[00000409] main demux debug: TIMER module_Need() : 465.250 ms - Total 465.250 ms / 1 intvls (Avg 465.250 ms)
[00000412] main decoder debug: looking for decoder module: 30 candidates
[00000412] araw decoder debug: samplerate:48000Hz channels:2 bits/sample:16
[00000412] main decoder debug: using decoder module "araw"
[00000412] main decoder debug: TIMER module_Need() : 94.976 ms - Total 94.976 ms / 1 intvls (Avg 94.976 ms)
[00000412] main decoder debug: thread started
[00000412] main decoder debug: thread 140487306508624 (decoder) created at priority 5 (input/decoder.c:217)
[00000408] main input debug: `v4l2://' successfully opened
[00000405] qt4 interface debug: New Event: type 1103
[00000405] qt4 interface debug: Updating the stream status: 3
[00000408] main input debug: control type=1
[00000412] main decoder debug: no aout present, spawning one
[00000439] main audio output debug: looking for audio output module: 4 candidates
[00000439] alsa audio output debug: opening ALSA device `default'
[00000439] main audio output debug: thread started
[00000439] main audio output debug: thread 140487222610256 (aout) created at priority 15 (alsa.c:687)
[00000439] main audio output debug: using audio output module "alsa"
[00000439] main audio output debug: TIMER module_Need() : 452.491 ms - Total 452.491 ms / 1 intvls (Avg 452.491 ms)
[00000439] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000439] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000439] main audio output debug: no need for any filter
[00000439] main audio output debug: looking for audio mixer module: 3 candidates
[00000439] main audio output debug: using audio mixer module "float32_mixer"
[00000439] main audio output debug: TIMER module_Need() : 23.293 ms - Total 23.293 ms / 1 intvls (Avg 23.293 ms)
[00000439] main audio output debug: input 's16l' 48000 Hz Stereo frame=1 samples/4 bytes
[00000439] main audio output debug: filter(s) 's16l'->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[00000441] main audio output debug: looking for audio filter module: 24 candidates
[00000441] main audio output debug: using audio filter module "converter_float"
[00000441] main audio output debug: TIMER module_Need() : 118.613 ms - Total 118.613 ms / 1 intvls (Avg 118.613 ms)
[00000439] main audio output debug: found a filter for the whole conversion
[00000439] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000473] main audio output debug: looking for audio filter module: 24 candidates
[00000473] main audio output debug: using audio filter module "bandlimited_resampler"
[00000473] main audio output debug: TIMER module_Need() : 0.380 ms - Total 0.380 ms / 1 intvls (Avg 0.380 ms)
[00000439] main audio output debug: found a filter for the whole conversion
[00000439] main audio output warning: PTS is out of range (311558), dropping buffer
[00000439] main audio output warning: PTS is out of range (300684), dropping buffer
[00000439] main audio output warning: PTS is out of range (299280), dropping buffer
[00000439] main audio output warning: PTS is out of range (289049), dropping buffer
[00000439] main audio output warning: PTS is out of range (279144), dropping buffer
[00000439] main audio output warning: PTS is out of range (268920), dropping buffer
[00000439] main audio output warning: PTS is out of range (259031), dropping buffer
[00000439] main audio output warning: PTS is out of range (248806), dropping buffer
[00000439] main audio output warning: PTS is out of range (238895), dropping buffer
[00000439] main audio output warning: PTS is out of range (228655), dropping buffer
[00000439] main audio output warning: PTS is out of range (218754), dropping buffer
[00000439] main audio output warning: PTS is out of range (208523), dropping buffer
[00000439] main audio output warning: PTS is out of range (198624), dropping buffer
[00000439] main audio output warning: PTS is out of range (188394), dropping buffer
[00000439] main audio output warning: PTS is out of range (178511), dropping buffer
[00000439] main audio output warning: PTS is out of range (168280), dropping buffer
[00000439] main audio output warning: PTS is out of range (158356), dropping buffer
[00000439] main audio output warning: PTS is out of range (148131), dropping buffer
[00000439] main audio output warning: PTS is out of range (138311), dropping buffer
[00000439] main audio output warning: PTS is out of range (138085), dropping buffer
[00000439] main audio output warning: PTS is out of range (128181), dropping buffer
[00000439] main audio output warning: PTS is out of range (116687), dropping buffer
[00000439] main audio output warning: PTS is out of range (104970), dropping buffer
[00000439] main audio output warning: PTS is out of range (95054), dropping buffer
[00000439] main audio output warning: PTS is out of range (84950), dropping buffer
[00000439] main audio output warning: PTS is out of range (74367), dropping buffer
[00000439] main audio output warning: PTS is out of range (64462), dropping buffer
[00000439] main audio output warning: PTS is out of range (54330), dropping buffer
[00000439] main audio output warning: PTS is out of range (44205), dropping buffer
[00000439] main audio output warning: PTS is out of range (27110), dropping buffer
[00000439] main audio output warning: PTS is out of range (5798), dropping buffer
[00000439] main audio output warning: PTS is out of range (31380), dropping buffer
[00000439] main audio output warning: PTS is out of range (21272), dropping buffer
[00000439] main audio output warning: PTS is out of range (3526), dropping buffer
[00000439] main audio output warning: PTS is out of range (-6727), dropping buffer
[00000439] main audio output warning: PTS is out of range (-16654), dropping buffer
[00000439] main audio output warning: PTS is out of range (-26762), dropping buffer
[00000439] main audio output warning: PTS is out of range (-37013), dropping buffer
[00000370] main playlist debug: incoming request - stopping current input
[00000370] main playlist debug: dying input
[00000408] main input debug: control type=0
[00000408] main input debug: control: stopping input
[00000409] main demux debug: removing module "v4l2"
[00000412] main decoder debug: removing module "araw"
[00000412] main decoder debug: thread ended
[00000412] main decoder debug: thread 140487306508624 joined (input/decoder.c:248)
[00000412] main decoder debug: killing decoder fourcc `araw', 0 PES in FIFO
[00000441] main audio output debug: removing module "converter_float"
[00000473] main audio output debug: removing module "bandlimited_resampler"
[00000405] qt4 interface debug: Updating the stream status: 8
[00000439] main audio output debug: thread ended
[00000439] main audio output debug: thread 140487222610256 joined (alsa.c:742)
[00000439] main audio output debug: removing module "alsa"
[00000439] main audio output debug: removing module "float32_mixer"
[00000408] main input debug: thread ended
[00000370] main playlist debug: dead input
[00000408] main input debug: thread 140487532636496 joined (playlist/engine.c:244)
[00000408] main input debug: TIMER input launching for 'v4l2://' : 565.512 ms - Total 565.512 ms / 1 intvls (Avg 565.512 ms)
[00000370] main playlist debug: starting new item
[00000370] main playlist debug: processing request item v4l2:// node Playlist skip 0
[00000370] main playlist debug: resyncing on v4l2://
[00000370] main playlist debug: v4l2:// is at 0
[00000370] main playlist debug: creating new input thread
[00000474] main input debug: Creating an input for 'v4l2://'
[00000474] main input debug: thread started
[00000474] main input debug: waiting for thread initialization
[00000474] main input debug: `v4l2://' gives access `v4l2' demux `' path `'
[00000474] main input debug: creating demux: access='v4l2' demux='' path=''
[00000475] main demux debug: looking for access_demux module: 1 candidate
[00000475] message demux warning: message queue overflowed
[00000475] v4l2 demux debug: ALSA input support available
[00000475] v4l2 demux debug: Trying direct kernel v4l2
[00000475] v4l2 demux debug: opening '/dev/video0' as video
[00000475] v4l2 demux debug: V4L2 device: USB 2.0 PC Camera using driver: gspca_gl860 (version: 2.5.0) on usb-0000:00:1d.7-6
[00000475] v4l2 demux debug: the device has the capabilities: (X) Video Capure, ( ) Audio, ( ) Tuner
[00000475] v4l2 demux debug: supported I/O methods are: (X) Read/Write, (X) Streaming, ( ) Asynchronous
[00000475] v4l2 demux debug: video input 0 (gspca_gl860) has type: External analog input *
[00000475] v4l2 demux debug: device codec GBRG (GBRG) not supported as access_demux
[00000475] v4l2 demux debug: Extended control API supported by v4l2 driver
[00000475] v4l2 demux debug: Available control: Brightness (980900)
[00000475] v4l2 demux debug:     integer control
[00000475] v4l2 demux debug:     valid values: 0 to 128 by steps of 4
[00000475] v4l2 demux debug:     default value: 70
[00000475] v4l2 demux debug:     current value: 70
[00000475] v4l2 demux debug: Available control: Contrast (980901)
[00000475] v4l2 demux debug:     integer control
[00000475] v4l2 demux debug:     valid values: 0 to 3 by steps of 1
[00000475] v4l2 demux debug:     default value: 0
[00000475] v4l2 demux debug:     current value: 0
[00000475] v4l2 demux debug: Available control: Hue (980903)
[00000475] v4l2 demux debug:     integer control
[00000475] v4l2 demux debug:     valid values: 0 to 1 by steps of 1
[00000475] v4l2 demux debug:     default value: 0
[00000475] v4l2 demux debug:     current value: 0
[00000475] v4l2 demux debug: Available control: Gamma (980910)
[00000475] v4l2 demux debug:     integer control
[00000475] v4l2 demux debug:     valid values: 0 to 2 by steps of 1
[00000475] v4l2 demux debug:     default value: 0
[00000475] v4l2 demux debug:     current value: 0
[00000475] v4l2 demux debug: Available control: Mirror (980914)
[00000475] v4l2 demux debug:     boolean control
[00000475] v4l2 demux debug:     default value: 0
[00000475] v4l2 demux debug:     current value: 0
[00000475] v4l2 demux debug: Available control: Flip (980915)
[00000475] v4l2 demux debug:     boolean control
[00000475] v4l2 demux debug:     default value: 0
[00000475] v4l2 demux debug:     current value: 0
[00000475] v4l2 demux debug: Available control: 50Hz (980918)
[00000475] v4l2 demux debug:     boolean control
[00000475] v4l2 demux debug:     default value: 1
[00000475] v4l2 demux debug:     current value: 1
[00000475] v4l2 demux debug: Available control: Sharpness (98091b)
[00000475] v4l2 demux debug:     integer control
[00000475] v4l2 demux debug:     valid values: 0 to 40 by steps of 1
[00000475] v4l2 demux debug:     default value: 20
[00000475] v4l2 demux debug:     current value: 20
[00000475] v4l2 demux debug: Available control: Backlight (98091c)
[00000475] v4l2 demux debug:     integer control
[00000475] v4l2 demux debug:     valid values: 0 to 64 by steps of 2
[00000475] v4l2 demux debug:     default value: 0
[00000475] v4l2 demux debug:     current value: 0
[00000475] v4l2 demux warning: Could not select any of the default chromas; attempting to open as MPEG encoder card (access)
[00000475] v4l2 demux debug: opening '(null)' as audio
[00000474] main input debug: thread 140487532636496 (input) created at priority 10 (input/input.c:370)
[00000405] qt4 interface debug: Updating the stream status: 3
[00000475] v4l2 demux debug: opened adev=`hw' stereo 48000Hz
[00000475] v4l2 demux debug: new audio es 2 channels 48000Hz
[00000474] main input debug: selecting program id=0
[00000475] main demux debug: using access_demux module "v4l2"
[00000475] main demux debug: TIMER module_Need() : 24.286 ms - Total 24.286 ms / 1 intvls (Avg 24.286 ms)
[00000476] main decoder debug: looking for decoder module: 30 candidates
[00000476] araw decoder debug: samplerate:48000Hz channels:2 bits/sample:16
[00000476] main decoder debug: using decoder module "araw"
[00000476] main decoder debug: TIMER module_Need() : 0.257 ms - Total 0.257 ms / 1 intvls (Avg 0.257 ms)
[00000476] main decoder debug: thread started
[00000476] main decoder debug: thread 140487231002960 (decoder) created at priority 5 (input/decoder.c:217)
[00000405] qt4 interface debug: New Event: type 1108
[00000474] main input debug: `v4l2://' successfully opened
[00000405] qt4 interface debug: New Event: type 1103
[00000405] qt4 interface debug: Updating the stream status: 3
[00000474] main input debug: control type=1
[00000476] main decoder debug: no aout present, spawning one
[00000477] main audio output debug: looking for audio output module: 4 candidates
[00000477] alsa audio output debug: opening ALSA device `default'
[00000477] main audio output debug: thread started
[00000477] main audio output debug: thread 140487306508624 (aout) created at priority 15 (alsa.c:687)
[00000477] main audio output debug: using audio output module "alsa"
[00000477] main audio output debug: TIMER module_Need() : 746.501 ms - Total 746.501 ms / 1 intvls (Avg 746.501 ms)
[00000477] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000477] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000477] main audio output debug: no need for any filter
[00000477] main audio output debug: looking for audio mixer module: 3 candidates
[00000477] main audio output debug: using audio mixer module "float32_mixer"
[00000477] main audio output debug: TIMER module_Need() : 0.215 ms - Total 0.215 ms / 1 intvls (Avg 0.215 ms)
[00000477] main audio output debug: input 's16l' 48000 Hz Stereo frame=1 samples/4 bytes
[00000477] main audio output debug: filter(s) 's16l'->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[00000478] main audio output debug: looking for audio filter module: 24 candidates
[00000478] main audio output debug: using audio filter module "converter_float"
[00000478] main audio output debug: TIMER module_Need() : 0.164 ms - Total 0.164 ms / 1 intvls (Avg 0.164 ms)
[00000477] main audio output debug: found a filter for the whole conversion
[00000477] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000479] main audio output debug: looking for audio filter module: 24 candidates
[00000479] main audio output debug: using audio filter module "bandlimited_resampler"
[00000479] main audio output debug: TIMER module_Need() : 0.198 ms - Total 0.198 ms / 1 intvls (Avg 0.198 ms)
[00000477] main audio output debug: found a filter for the whole conversion
[00000477] main audio output warning: PTS is out of range (449187), dropping buffer
[00000477] main audio output warning: PTS is out of range (439248), dropping buffer
[00000477] main audio output warning: PTS is out of range (438033), dropping buffer
[00000477] main audio output warning: PTS is out of range (427972), dropping buffer
[00000477] main audio output warning: PTS is out of range (417791), dropping buffer
[00000477] main audio output warning: PTS is out of range (407879), dropping buffer
[00000477] main audio output warning: PTS is out of range (397802), dropping buffer
[00000477] main audio output warning: PTS is out of range (387724), dropping buffer
[00000477] main audio output warning: PTS is out of range (377607), dropping buffer
[00000477] main audio output warning: PTS is out of range (367462), dropping buffer
[00000477] main audio output warning: PTS is out of range (357316), dropping buffer
[00000477] main audio output warning: PTS is out of range (347354), dropping buffer
[00000477] main audio output warning: PTS is out of range (347219), dropping buffer
[00000477] main audio output warning: PTS is out of range (335477), dropping buffer
[00000477] main audio output warning: PTS is out of range (325240), dropping buffer
[00000477] main audio output warning: PTS is out of range (315441), dropping buffer
[00000477] main audio output warning: PTS is out of range (315209), dropping buffer
[00000477] main audio output warning: PTS is out of range (305335), dropping buffer
[00000477] main audio output warning: PTS is out of range (295272), dropping buffer
[00000477] main audio output warning: PTS is out of range (285023), dropping buffer
[00000477] main audio output warning: PTS is out of range (275098), dropping buffer
[00000477] main audio output warning: PTS is out of range (264852), dropping buffer
[00000477] main audio output warning: PTS is out of range (254934), dropping buffer
[00000477] main audio output warning: PTS is out of range (244837), dropping buffer
[00000477] main audio output warning: PTS is out of range (234568), dropping buffer
[00000477] main audio output warning: PTS is out of range (224622), dropping buffer
[00000477] main audio output warning: PTS is out of range (214521), dropping buffer
[00000477] main audio output warning: PTS is out of range (204286), dropping buffer
[00000477] main audio output warning: PTS is out of range (194330), dropping buffer
[00000477] main audio output warning: PTS is out of range (184239), dropping buffer
[00000477] main audio output warning: PTS is out of range (173980), dropping buffer
[00000477] main audio output warning: PTS is out of range (164148), dropping buffer
[00000477] main audio output warning: PTS is out of range (163902), dropping buffer
[00000477] main audio output warning: PTS is out of range (153985), dropping buffer
[00000477] main audio output warning: PTS is out of range (143861), dropping buffer
[00000477] main audio output warning: PTS is out of range (133687), dropping buffer
[00000477] main audio output warning: PTS is out of range (122775), dropping buffer
[00000477] main audio output warning: PTS is out of range (112860), dropping buffer
[00000477] main audio output warning: PTS is out of range (102606), dropping buffer
[00000477] main audio output warning: PTS is out of range (92770), dropping buffer
[00000477] main audio output warning: PTS is out of range (92527), dropping buffer
[00000477] main audio output warning: PTS is out of range (82610), dropping buffer
[00000477] main audio output warning: PTS is out of range (72353), dropping buffer
[00000477] main audio output warning: PTS is out of range (62448), dropping buffer
[00000477] main audio output warning: PTS is out of range (52208), dropping buffer
[00000477] main audio output warning: PTS is out of range (42288), dropping buffer
[00000477] main audio output warning: PTS is out of range (32195), dropping buffer
[00000477] main audio output warning: PTS is out of range (21958), dropping buffer
[00000477] main audio output warning: PTS is out of range (11948), dropping buffer
[00000477] main audio output warning: PTS is out of range (-2482), dropping buffer
[00000477] main audio output warning: PTS is out of range (-12596), dropping buffer
[00000477] main audio output warning: PTS is out of range (-22711), dropping buffer
[00000477] main audio output warning: PTS is out of range (-32984), dropping buffer
[00000001] main libvlc debug: removing all interfaces
[00000405] qt4 interface debug: Quitting the Qt4 Interface
[00000405] qt4 interface debug: Destroying the main interface
[00000370] main playlist debug: incoming request - stopping current input
[00000370] main playlist debug: dying input
[00000474] main input debug: control type=0
[00000474] main input debug: control: stopping input
[00000475] main demux debug: removing module "v4l2"
[00000476] main decoder debug: removing module "araw"
[00000476] main decoder debug: thread ended
[00000476] main decoder debug: thread 140487231002960 joined (input/decoder.c:248)
[00000476] main decoder debug: killing decoder fourcc `araw', 0 PES in FIFO
[00000478] main audio output debug: removing module "converter_float"
[00000479] main audio output debug: removing module "bandlimited_resampler"
[00000405] qt4 interface debug: Destroying the Dialog Provider
[00000477] main audio output debug: thread ended
[00000477] main audio output debug: thread 140487306508624 joined (alsa.c:742)
[00000477] main audio output debug: removing module "alsa"
[00000477] main audio output debug: removing module "float32_mixer"
[00000474] main input debug: thread ended
[00000370] main playlist debug: dead input
[00000474] main input debug: thread 140487532636496 joined (playlist/engine.c:244)
[00000474] main input debug: TIMER input launching for 'v4l2://' : 57.716 ms - Total 57.716 ms / 1 intvls (Avg 57.716 ms)
[00000405] main interface debug: thread ended
[00000405] main interface debug: thread 140487710595408 joined (interface/interface.c:188)
[00000405] main interface debug: removing module "qt4"
[00000403] main interface debug: thread ended
[00000403] main interface debug: thread 140487789746512 joined (interface/interface.c:188)
[00000403] main interface debug: removing module "signals"
[00000401] main interface debug: thread ended
[00000401] main interface debug: thread 140487808641360 joined (interface/interface.c:188)
[00000401] main interface debug: removing module "screensaver"
[00000399] main interface debug: thread ended
[00000399] main interface debug: thread 140487819143504 joined (interface/interface.c:188)
[00000399] main interface debug: removing module "inhibit"
[00000397] main interface debug: thread ended
[00000397] main interface debug: thread 140487829645648 joined (interface/interface.c:188)
[00000397] main interface debug: removing module "hotkeys"
[00000001] main libvlc debug: removing all services discovery tasks
[00000001] main libvlc debug: removing playlist
[00000370] main playlist debug: saving Media Library to file /home/bugabundo/.local/share/vlc/ml.xspf
[00000370] main playlist debug: looking for playlist export module: 1 candidate
[00000370] main playlist debug: using playlist export module "export"
[00000370] main playlist debug: TIMER module_Need() : 0.566 ms - Total 0.566 ms / 1 intvls (Avg 0.566 ms)
[00000370] main playlist debug: removing module "export"
[00000395] main preparser debug: thread ended
[00000395] main preparser debug: thread 140487869028688 joined (playlist/engine.c:521)
[00000396] main fetcher debug: thread ended
[00000396] main fetcher debug: thread 140487846431056 joined (playlist/engine.c:523)
[00000370] main playlist debug: thread ended
[00000370] main playlist debug: thread 140487838038352 joined (libvlc.c:993)
[00000395] main preparser debug: Destroyed
[00000396] main fetcher debug: Destroyed
[00000370] main playlist debug: Destroyed
[00000001] main libvlc debug: removing interaction
[00000369] main interaction debug: thread ended
[00000369] main interaction debug: thread 140487883757904 joined (interface/interaction.c:400)
[00000001] main libvlc debug: removing all video outputs
[00000001] main libvlc debug: TIMER ML Load : Total 6.016 ms / 1 intvls (Avg 6.016 ms)
[00000001] main libvlc debug: TIMER Items array build : Total 0.162 ms / 2 intvls (Avg 0.081 ms)
[00000001] main libvlc debug: TIMER ML Dump : Total 33.551 ms / 1 intvls (Avg 33.551 ms)
[00000001] main libvlc debug: removing stats
[00000001] main libvlc debug: removing module "memcpymmxext"
[00000001] main libvlc debug: opening config file (/home/bugabundo/.config/vlc/vlcrc)
[00000001] main libvlc debug: opening config file (/home/bugabundo/.config/vlc/vlcrc)
[00000001] main libvlc debug: writing plugins cache /home/bugabundo/.cache/vlc/plugins-04081e.dat

```

Camorama too
```
$ camorama -D

VIDIOCGCAP
device name = USB 2.0 PC Camera
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 1600
max height = 1200
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 35839
hue = 0
colour = 0
contrast = 0
whiteness = 0
colour depth = 8

VIDIOCGMBUF
mb.size = 7684096
mb.frames = 4
mb.offset = 1921024
update_tooltip called
tip - acap off
** Message: SET PIC
update_tooltip called
tip - acap off
Unable to capture image (VIDIOCSYNC)

```

even with preload
```
$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so camorama
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

---

### Post by nol_faich on 2009-05-23
New release: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30b.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30b.tgz)

If an application is not working, test it with preload:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so my_app

Tested by Bugabundo with 2.6.30-64bits.

Cheese OK (except 1280x1024)
Skype/Camorama/VLC require preload.


If red and blue are inverted in the images, set hue to max.

---

### Post by nol_faich on 2009-05-25
Update: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30c.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30c.tgz)

---

### Post by Jack Malmostoso on 2009-05-25
Hey Nol, excellent news!
Version 2.6.30c works 100% with Cheese (all sizes are correctly detected), and now I have installed the package I needed to make skype work (lib32v4l-0).
Preloading v4l1compat.so does indeed make skype work just fine!

If you need some particular output, please let me know so that I can take it for you!
T-H-A-N-K-Y-O-U!

---

### Post by nol_faich on 2009-05-26
BUGabundo disserves the thanks too for the hours spent to make tests and logs!

---

### Post by BUGabundo on 2009-05-26
> **nol_faich said:**
> BugAbundo disserves the thanks too for the hours spent to make tests and logs!

No need to thank me. All your work is helping me too, to have an working webcam.

*just try to respect the case sensitive of the nick ;)*

---

### Post by BUGabundo on 2009-05-26
btw Nol are u subbed to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604) ?

---

### Post by nol_faich on 2009-05-27
No, I wasn't.

@ BUGabundo, Jack
Could you tell me if the gspca.h file part of your kernel headers if zero byte or not for each kernel version you installed?
With the generic headers of 2.6.27-11, this file is null, this is why I included the gspca.h for 2.6.27/28/29/30.

I will ask for tests to some tester for the 'sa' gspca version, if this version is OK as seems to be the last 2.6.30, I will submit the driver to gspca maintainer and standalone driver developpment will be canceled.

---

### Post by Jack Malmostoso on 2009-05-27
Hey Nol,

here is the output you requested:```
jack@nostromo:~$ ls -al /usr/src/linux-headers-2.6.29-2-amd64/include/config/usb/gspca.h
-rw-r--r-- 1 root root 0 2009-05-17 17:45 /usr/src/linux-headers-2.6.29-2-amd64/include/config/usb/gspca.h

jack@vasquez:~$ ls -al /usr/src/linux-headers-2.6.30-rc5-amd64/include/config/usb/gspca.h 
-rw-r--r-- 1 root root 0 2009-05-18 05:36 /usr/src/linux-headers-2.6.30-rc5-amd64/include/config/usb/gspca.h

```

All files are empty.

---

### Post by nol_faich on 2009-05-27
Thanks Jack. This is weird that this file is empty.

Have you tried the gspca driver with the 2.6.29 kernel?

---

### Post by BUGabundo on 2009-05-27
```
$  ls -al /usr/src/linux-headers-2.6.30-6-generic/include/config/usb/gspca.h
-rw-r--r-- 1 root root 0 2009-05-22 07:59 /usr/src/linux-headers-2.6.30-6-generic/include/config/usb/gspca.h

```

zero bytes too

---

### Post by Jack Malmostoso on 2009-05-28
> **nol_faich said:**
> Have you tried the gspca driver with the 2.6.29 kernel?

No, I uninstalled it since it just didn't work with my laptop.
However I have tested 2.6.30-rc7 and it works just fine!
I hope your driver will make it soon in the kernel (2.6.32, maybe?)!

---

### Post by nol_faich on 2009-05-28
@ BUGabundo: I find something which could explain the upside down and blue image you got although this should be solved. The tarball is in the attachment.
Btw, as you have several PPA, do you which files I had to add to my sources to make a proper deb package able to run the installation script?

@ Jack: If it is as it used to be, 2.6.31 will require changes (hopefully limited for the gspca!) and 2.6.32 will be OK. The thing that threatens me is in the change done for 2.6.29: it seems that there is a special structure for v4l2 devices which is still not used, I am wondering how deep will be the changes when the new structure will be on duty.

---

### Post by nol_faich on 2009-05-28
New release: [https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30e.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_gl860_2.6.30e.tgz)

Sorry I hurried up to watch a movie and forget to introduce this release:
- fix for compilation with gspca framework and kernel 2.6.28
- include the changes in the gspca_gl860_2.6.30d.tgz.

---

### Post by Jack Malmostoso on 2009-05-28
Version 2.6.30e works fine with 2.6.30-rc7.

---

### Post by BUGabundo on 2009-05-29
> **nol_faich said:**
> @ BUGabundo: Btw, as you have several PPA, do you which files I had to add to my sources to make a proper deb package able to run the installation script?

Nol your best source of information is [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

I've never created a PPA of my own, so I cant help you much there.
Maybe maco can? she is a bit more experienced then me with this.

---

### Post by nol_faich on 2009-05-29
Hi BUGabundo!

It's a shame, I've read this as well as deb packaging but some files ready to be modified is likable. :)

To test the fix for upsuide-down images, you need to do that in poorly lit conditions as upside-down image does not happend in daylight.

---

### Post by Jack Malmostoso on 2009-05-29
Nol, your best bet would be to learn about the DKMS infrastructure.
However, I'd just go for the merge in the main kernel tree.

[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)

---

### Post by BUGabundo on 2009-05-29
Nol great news.
[http://identi.ca/notice/4692172](http://identi.ca/notice/4692172)
Steve Conklin ([https://launchpad.net/~sconklin](https://launchpad.net/~sconklin)) wants to talk to you to get the driver upstreamed.
So I guess you guys need to talk to each other. I've asked maco to ask him to come here, or you can got to bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604) and comment on it, since he is now the assigne person to handle the bug.

---

### Post by BUGabundo on 2009-05-31
Nol latests version doesnt rotate the image when rotating the cam, both on good light and bad conditions.

both cheese, camorana, flash

---

### Post by nol_faich on 2009-05-31
@ BUGabundo
Please try with the attached version.

@ Jack
Can you test that version too? This should be the submitted version. Retest all settings with:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc v4l2:// :v4l2-vdev="/dev/video0"
(boolean settings should not work because of an issue in VLC)

---

### Post by Jack Malmostoso on 2009-06-01
Hey Nol, tested version "f" and it works in cheese and skype. However, I cannot use vlc (with or without preloading) and camorama (it ignores the preloading).
Not sure why, to be honest.

I think basic support is there, and at this point it's quite a lot!

---

### Post by nol_faich on 2009-06-01
Is that right?
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc v4l2:// :v4l2-vdev="/dev/video0" 
does not work but there is no preload error
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama   causes a preload error

vlc requires the preload in v4l2 although it is intended for v4l1...

What about that?
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc v4l:// :v4l-vdev="/dev/video0"

---

### Post by nol_faich on 2009-06-01
For the sake of "ar", "tar", "wc -c", "head -c" and "vi -c", a debian package. This compile the driver in /tmp and the install is deleted after a reboot. The package does not perform cleaning on deinstallation.

---

### Post by nol_faich on 2009-06-01
And a new with deinstall (the deisntall unloads gspca_gl860 -if not in use!- and try to load the stand alone driver gl860).

---

### Post by Jack Malmostoso on 2009-06-02
Hey Nol, I am an IDIOT. I was preloading the 32bit version of the library. God I'm stOOpid.

It all works just fine, VLC and Camorama alike.
So so sorry about that :)

---

### Post by nol_faich on 2009-06-02
Everybody makes mistake ;)

---

### Post by BUGabundo on 2009-06-10
Nol your Deb is a bit of a mess.
since it is installed on /tmp after reboot the apt db gets unstable and wont work.
i had to manually delete it from the DB so i could use apt

---

### Post by BUGabundo on 2009-06-10
btw what is the last stable or testing version? the -f has not install, and -e is very old, although its working ok

---

### Post by nol_faich on 2009-06-11
SF is up to date.

If you still want to test the gspca version, it is in the test package. Use ./install_gspca to install "permanently" it.
What is to be checked with the "his" flavour is the image upside down issue. If the issue occurs, it is important for me to know how long it lasts (does it resolves itself after some seconds ?), if the color are OK (blue and red not inverted), whether the webcam is rotated or not, whether this is reproducible or not, whether a setting change changes something or not.

---

### Post by BUGabundo on 2009-06-13
been testing the latest version of SF and am having some trouble with rotating cam.
sometimes it starts inverted and wont fix it self, other starts ok, but then start to jump up side down and back
here is a video with it
[http://www.ustream.tv/myvideos/1/1651425](http://www.ustream.tv/myvideos/1/1651425)

---

### Post by nol_faich on 2009-06-15
After several tests with BUGabundo, I came to the conclusion the issue is due to hardware. When the webcam ("his" flavour) is rotated to look backwards, the orientation sensor is unstable so that sometimes the webcam tells the driver the image is normal although it is up side down. There is not such an issue when the webcam is looking onwards.

---

### Post by nol_faich on 2009-06-24
Some news.
A new function should be added to the GSPCA framework to fix a glitch in the gl860 driver for GSPCA. Once done, I will ask you to test the driver and if this is fine, the driver will be submitted and so should enter the kernel when this gspca version is merged with the kernel.

---

### Post by nol_faich on 2009-06-28
The modified driver is here:
[S][https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_v4l_gl860_2.6.30j.tgz](https://sourceforge.net/project/downloading.php?group_id=229562&filename=gspca_v4l_gl860_2.6.30j.tgz)[/S]
At the bottom of this post

To install, you must:
- remove the gl860 and/or the gspca_gl860 line in /etc/modules
- once done, reboot if you had the line "gspca_gl860"
- download the driver
- untar it
- type ./inst_gspca

The install download the V4L sources (4,1MB), add the gspca_gl860 files and compiled the whole V4L from sources (requires 260MB and 10-20 minutes).

Test ALL possible SIZES with Cheese (1280x1024 may fails because of Cheese) or preload+Camorama. Change the size AS SOON AS you get an image. After the last size stop the application.

After the test, I would like to post the "dmesg | grep gspca".

Once done, use:
sudo rmmod v4l/gspca_gl860.ko
sudo rmmod v4l/gspca_main.ko
sudo rmmod v4l/videodev.ko
sudo rmmod v4l/v4l1-compat.ko
sudo modprobe v4l1-compat
sudo modprobe videodev
then   sudo modprobe gl860    or   sudo modprobe gspca_gl860 depending on your driver

Add again the lines you removed in /etc/modules

Thanks

---

### Post by Jack Malmostoso on 2009-07-04
Hi Nol, sorry for the delay. The build fails with:```
CC [M]  /home/jack/Desktop/gspca/gspca-c218eabb04dc/v4l/gl860.o
/home/jack/Desktop/gspca/gspca-c218eabb04dc/v4l/gl860.c:433: error: unknown field 'start0' specified in initializer
/home/jack/Desktop/gspca/gspca-c218eabb04dc/v4l/gl860.c:446: error: unknown field 'start0' specified in initializer
/home/jack/Desktop/gspca/gspca-c218eabb04dc/v4l/gl860.c:459: error: unknown field 'start0' specified in initializer
/home/jack/Desktop/gspca/gspca-c218eabb04dc/v4l/gl860.c:472: error: unknown field 'start0' specified in initializer
```
Can you fix this?

---

### Post by Jack Malmostoso on 2009-07-05
```
jack@vasquez:~/Desktop/gspca/gl860$ sudo grep gspca /var/log/syslog 
Jul  5 12:51:23 vasquez kernel: [   11.247772] calling  gspca_init+0x0/0x22 [gspca_main] @ 1783
Jul  5 12:51:23 vasquez kernel: [   11.253187] gspca: main v2.5.0 registered
Jul  5 12:51:23 vasquez kernel: [   11.258494] initcall gspca_init+0x0/0x22 [gspca_main] returned 0 after 5179 usecs
Jul  5 12:51:23 vasquez kernel: [   11.370929] calling  sd_mod_init+0x0/0x1de [gspca_gl860] @ 1783
Jul  5 12:51:23 vasquez kernel: [   11.376397] gspca_gl860: driver startup - v2.6.30f (for GSPCA)
Jul  5 12:51:23 vasquez kernel: [   11.381875] gspca: probing 05e3:0503
Jul  5 12:51:23 vasquez kernel: [   11.959480] gspca_gl860: probe 1=ff
Jul  5 12:51:23 vasquez kernel: [   11.965185] gspca_gl860: probing for sensor OV2640 or OV9655
Jul  5 12:51:23 vasquez kernel: [   11.975478] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.084857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.201104] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.305853] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.417984] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.532850] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.644979] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.752861] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.864854] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   12.973852] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.084857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.196982] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.309857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.420858] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.532857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.644858] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.756857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.868857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   13.981857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.092857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.204855] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.316983] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.428858] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.540857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.652857] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.765980] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.876853] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   14.988859] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   15.096983] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   15.208858] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   15.316859] gspca_gl860: probe 2= 0
Jul  5 12:51:23 vasquez kernel: [   15.420026] gspca_gl860: no relevant sensor answer (count: #00=31/#FF=0)
Jul  5 12:51:23 vasquez kernel: [   15.422954] gspca_gl860: * 1.3Mpixels -> set the 'sa' flavour
Jul  5 12:51:23 vasquez kernel: [   15.425781] gspca_gl860: * 2.0Mpixels -> set the 'ms' flavour
Jul  5 12:51:23 vasquez kernel: [   15.428602] gspca_gl860: To set a flavour, ask your admin to add that line to /etc/modprobe.d/options:
Jul  5 12:51:23 vasquez kernel: [   15.431550] gspca_gl860: options gspca_gl860 pilote="ms" or "sa"
Jul  5 12:51:23 vasquez kernel: [   15.434507] gspca_gl860: If a 'options gspca_gl860' line is already there, change the 'pilote' value or add 'pilote="ms" or "sa"' to that line
Jul  5 12:51:23 vasquez kernel: [   15.440680] gspca_gl860: #00 > #FF -> Trying 'ms'
Jul  5 12:51:23 vasquez kernel: [   15.443768] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms)
Jul  5 12:51:23 vasquez kernel: [   17.049695] gspca: probe ok
Jul  5 12:51:23 vasquez kernel: [   17.052858] gspca_gl860: Camera is now controlling video device /dev/video0
Jul  5 12:51:23 vasquez kernel: [   17.056059] usbcore: registered new interface driver gspca_gl860
Jul  5 12:51:23 vasquez kernel: [   17.059218] gspca_gl860: driver registered
Jul  5 12:51:23 vasquez kernel: [   17.062320] initcall sd_mod_init+0x0/0x1de [gspca_gl860] returned 0 after 5552648 usecs
Jul  5 13:18:21 vasquez kernel: [ 1643.608014] usbcore: deregistering interface driver gspca_gl860
Jul  5 13:18:21 vasquez kernel: [ 1643.608127] gspca: disconnect complete
Jul  5 13:18:21 vasquez kernel: [ 1643.608148] gspca_gl860: driver deregistered
Jul  5 13:18:21 vasquez kernel: [ 1643.625379] gspca: main deregistered
Jul  5 13:26:58 vasquez kernel: [ 2161.132314] gspca_gl860: Unknown symbol gspca_frame_add
Jul  5 13:26:58 vasquez kernel: [ 2161.132445] gspca_gl860: Unknown symbol gspca_debug
Jul  5 13:26:58 vasquez kernel: [ 2161.132757] gspca_gl860: Unknown symbol gspca_disconnect
Jul  5 13:26:58 vasquez kernel: [ 2161.132892] gspca_gl860: Unknown symbol gspca_resume
Jul  5 13:26:58 vasquez kernel: [ 2161.133042] gspca_gl860: Unknown symbol gspca_dev_probe
Jul  5 13:26:58 vasquez kernel: [ 2161.133180] gspca_gl860: Unknown symbol gspca_suspend
Jul  5 13:27:29 vasquez kernel: [ 2191.485103] gspca_main: Unknown symbol video_ioctl2
Jul  5 13:27:29 vasquez kernel: [ 2191.485554] gspca_main: Unknown symbol video_devdata
Jul  5 13:27:29 vasquez kernel: [ 2191.485893] gspca_main: Unknown symbol video_unregister_device
Jul  5 13:27:29 vasquez kernel: [ 2191.486038] gspca_main: Unknown symbol video_register_device
Jul  5 13:40:23 vasquez kernel: [ 2966.090526] calling  gspca_init+0x0/0x22 [gspca_main] @ 27436
Jul  5 13:40:23 vasquez kernel: [ 2966.090533] gspca: main v2.6.0 registered
Jul  5 13:40:23 vasquez kernel: [ 2966.090539] initcall gspca_init+0x0/0x22 [gspca_main] returned 0 after 3 usecs
Jul  5 13:40:23 vasquez kernel: [ 2966.117269] calling  sd_mod_init+0x0/0x1de [gspca_gl860] @ 27439
Jul  5 13:40:23 vasquez kernel: [ 2966.117276] gspca_gl860: driver startup - v2.6.30k (for GSPCA)
Jul  5 13:40:23 vasquez kernel: [ 2966.117305] gspca: probing 05e3:0503
Jul  5 13:40:24 vasquez kernel: [ 2966.647501] gspca_gl860: probe 1=ff
Jul  5 13:40:24 vasquez kernel: [ 2966.647506] gspca_gl860: probing for sensor OV2640 or OV9655
Jul  5 13:40:24 vasquez kernel: [ 2966.652500] gspca_gl860: probe 2=26
Jul  5 13:40:24 vasquez kernel: [ 2966.652504] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms)
Jul  5 13:40:26 vasquez kernel: [ 2968.293615] gspca: probe ok
Jul  5 13:40:26 vasquez kernel: [ 2968.293620] gspca_gl860: Camera is now controlling video device /dev/video0
Jul  5 13:40:26 vasquez kernel: [ 2968.293658] usbcore: registered new interface driver gspca_gl860
Jul  5 13:40:26 vasquez kernel: [ 2968.293663] gspca_gl860: driver registered
Jul  5 13:40:26 vasquez kernel: [ 2968.293678] initcall sd_mod_init+0x0/0x1de [gspca_gl860] returned 0 after 2125381 usecs
Jul  5 13:40:26 vasquez kernel: [ 2968.439798] gspca: hald-probe-vide open
Jul  5 13:40:26 vasquez kernel: [ 2968.439802] gspca: open done
Jul  5 13:40:26 vasquez kernel: [ 2968.440520] gspca: hald-probe-vide close
Jul  5 13:40:26 vasquez kernel: [ 2968.440523] gspca: close done
Jul  5 13:41:05 vasquez kernel: [ 3007.527681] gspca: cheese open
Jul  5 13:41:05 vasquez kernel: [ 3007.527689] gspca: open done
Jul  5 13:41:05 vasquez kernel: [ 3007.529644] gspca: cheese close
Jul  5 13:41:05 vasquez kernel: [ 3007.529649] gspca: close done
Jul  5 13:41:05 vasquez kernel: [ 3007.583941] gspca: cheese open
Jul  5 13:41:05 vasquez kernel: [ 3007.583949] gspca: open done
Jul  5 13:41:05 vasquez kernel: [ 3007.585829] gspca: frame alloc frsz: 1920000
Jul  5 13:41:05 vasquez kernel: [ 3007.586313] gspca: reqbufs st:0 c:2
Jul  5 13:41:05 vasquez kernel: [ 3007.586389] gspca: mmap start:a7d57000 size:1921024
Jul  5 13:41:05 vasquez kernel: [ 3007.586506] gspca: mmap start:a7b82000 size:1921024
Jul  5 13:41:05 vasquez kernel: [ 3007.586619] gspca: use alt 1 ep 0x81
Jul  5 13:41:05 vasquez kernel: [ 3007.588853] gspca: init transfer alt 1
Jul  5 13:41:05 vasquez kernel: [ 3007.588859] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:41:08 vasquez kernel: [ 3011.020138] gspca: stream on OK GBRG 1600x1200
Jul  5 13:41:09 vasquez kernel: [ 3011.737942] gspca: kill transfer
Jul  5 13:41:09 vasquez kernel: [ 3011.908343] gspca: stream off OK
Jul  5 13:41:09 vasquez kernel: [ 3011.909132] gspca: cheese close
Jul  5 13:41:09 vasquez kernel: [ 3011.909135] gspca: frame free
Jul  5 13:41:09 vasquez kernel: [ 3011.909543] gspca: close done
Jul  5 13:41:10 vasquez kernel: [ 3012.683012] gspca: cheese open
Jul  5 13:41:10 vasquez kernel: [ 3012.683019] gspca: open done
Jul  5 13:41:10 vasquez kernel: [ 3012.794577] gspca: frame alloc frsz: 1920000
Jul  5 13:41:10 vasquez kernel: [ 3012.795048] gspca: reqbufs st:0 c:2
Jul  5 13:41:10 vasquez kernel: [ 3012.795111] gspca: mmap start:9fe2b000 size:1921024
Jul  5 13:41:10 vasquez kernel: [ 3012.795223] gspca: mmap start:9fc56000 size:1921024
Jul  5 13:41:10 vasquez kernel: [ 3012.795334] gspca: use alt 1 ep 0x81
Jul  5 13:41:10 vasquez kernel: [ 3012.797199] gspca: init transfer alt 1
Jul  5 13:41:10 vasquez kernel: [ 3012.797203] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:41:13 vasquez kernel: [ 3015.641162] gspca: stream on OK GBRG 1600x1200
Jul  5 13:41:49 vasquez kernel: [ 3051.439984] gspca: kill transfer
Jul  5 13:41:49 vasquez kernel: [ 3051.612032] gspca: stream off OK
Jul  5 13:41:49 vasquez kernel: [ 3051.612924] gspca: cheese close
Jul  5 13:41:49 vasquez kernel: [ 3051.612926] gspca: frame free
Jul  5 13:41:49 vasquez kernel: [ 3051.613233] gspca: close done
Jul  5 13:43:54 vasquez kernel: [ 3177.175408] gspca: cheese open
Jul  5 13:43:54 vasquez kernel: [ 3177.175415] gspca: open done
Jul  5 13:43:54 vasquez kernel: [ 3177.177507] gspca: cheese close
Jul  5 13:43:54 vasquez kernel: [ 3177.177513] gspca: close done
Jul  5 13:43:55 vasquez kernel: [ 3177.188720] gspca: cheese open
Jul  5 13:43:55 vasquez kernel: [ 3177.188728] gspca: open done
Jul  5 13:43:55 vasquez kernel: [ 3177.190063] gspca: frame alloc frsz: 1920000
Jul  5 13:43:55 vasquez kernel: [ 3177.190539] gspca: reqbufs st:0 c:2
Jul  5 13:43:55 vasquez kernel: [ 3177.190608] gspca: mmap start:f4fc4000 size:1921024
Jul  5 13:43:55 vasquez kernel: [ 3177.190722] gspca: mmap start:f4def000 size:1921024
Jul  5 13:43:55 vasquez kernel: [ 3177.190835] gspca: use alt 1 ep 0x81
Jul  5 13:43:55 vasquez kernel: [ 3177.193237] gspca: init transfer alt 1
Jul  5 13:43:55 vasquez kernel: [ 3177.193242] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:43:58 vasquez kernel: [ 3180.417174] gspca: stream on OK GBRG 1600x1200
Jul  5 13:43:58 vasquez kernel: [ 3181.057729] gspca: kill transfer
Jul  5 13:43:59 vasquez kernel: [ 3181.232026] gspca: stream off OK
Jul  5 13:43:59 vasquez kernel: [ 3181.232763] gspca: cheese close
Jul  5 13:43:59 vasquez kernel: [ 3181.232766] gspca: frame free
Jul  5 13:43:59 vasquez kernel: [ 3181.233175] gspca: close done
Jul  5 13:43:59 vasquez kernel: [ 3181.757551] gspca: cheese open
Jul  5 13:43:59 vasquez kernel: [ 3181.757556] gspca: open done
Jul  5 13:43:59 vasquez kernel: [ 3181.818124] gspca: frame alloc frsz: 1920000
Jul  5 13:43:59 vasquez kernel: [ 3181.818401] gspca: reqbufs st:0 c:2
Jul  5 13:43:59 vasquez kernel: [ 3181.818436] gspca: mmap start:f4002000 size:1921024
Jul  5 13:43:59 vasquez kernel: [ 3181.818508] gspca: mmap start:eae29000 size:1921024
Jul  5 13:43:59 vasquez kernel: [ 3181.818570] gspca: use alt 1 ep 0x81
Jul  5 13:43:59 vasquez kernel: [ 3181.820431] gspca: init transfer alt 1
Jul  5 13:43:59 vasquez kernel: [ 3181.820434] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:44:02 vasquez kernel: [ 3184.832137] gspca: stream on OK GBRG 1600x1200
Jul  5 13:44:12 vasquez kernel: [ 3195.026442] gspca: kill transfer
Jul  5 13:44:13 vasquez kernel: [ 3195.201029] gspca: stream off OK
Jul  5 13:44:13 vasquez kernel: [ 3195.201921] gspca: cheese close
Jul  5 13:44:13 vasquez kernel: [ 3195.201924] gspca: frame free
Jul  5 13:44:13 vasquez kernel: [ 3195.202227] gspca: close done
Jul  5 13:44:13 vasquez kernel: [ 3195.354285] gspca: cheese open
Jul  5 13:44:13 vasquez kernel: [ 3195.354290] gspca: open done
Jul  5 13:44:13 vasquez kernel: [ 3195.437834] gspca: frame alloc frsz: 1228800
Jul  5 13:44:13 vasquez kernel: [ 3195.438092] gspca: reqbufs st:0 c:2
Jul  5 13:44:13 vasquez kernel: [ 3195.438139] gspca: mmap start:f4e3a000 size:1228800
Jul  5 13:44:13 vasquez kernel: [ 3195.438207] gspca: mmap start:f40ab000 size:1228800
Jul  5 13:44:13 vasquez kernel: [ 3195.438264] gspca: use alt 1 ep 0x81
Jul  5 13:44:13 vasquez kernel: [ 3195.440129] gspca: init transfer alt 1
Jul  5 13:44:13 vasquez kernel: [ 3195.440132] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:44:16 vasquez kernel: [ 3198.321142] gspca: stream on OK GBRG 1280x960
Jul  5 13:44:20 vasquez kernel: [ 3202.477399] gspca: kill transfer
Jul  5 13:44:20 vasquez kernel: [ 3202.649026] gspca: stream off OK
Jul  5 13:44:20 vasquez kernel: [ 3202.649638] gspca: cheese close
Jul  5 13:44:20 vasquez kernel: [ 3202.649641] gspca: frame free
Jul  5 13:44:20 vasquez kernel: [ 3202.649836] gspca: close done
Jul  5 13:44:20 vasquez kernel: [ 3202.793866] gspca: cheese open
Jul  5 13:44:20 vasquez kernel: [ 3202.793871] gspca: open done
Jul  5 13:44:20 vasquez kernel: [ 3202.876406] gspca: frame alloc frsz: 480000
Jul  5 13:44:20 vasquez kernel: [ 3202.876503] gspca: reqbufs st:0 c:2
Jul  5 13:44:20 vasquez kernel: [ 3202.876544] gspca: mmap start:f4ef0000 size:483328
Jul  5 13:44:20 vasquez kernel: [ 3202.876565] gspca: mmap start:f4e7a000 size:483328
Jul  5 13:44:20 vasquez kernel: [ 3202.876585] gspca: use alt 1 ep 0x81
Jul  5 13:44:20 vasquez kernel: [ 3202.878485] gspca: init transfer alt 1
Jul  5 13:44:20 vasquez kernel: [ 3202.878487] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:44:23 vasquez kernel: [ 3205.428142] gspca: stream on OK GBRG 800x600
Jul  5 13:44:29 vasquez kernel: [ 3211.237438] gspca: kill transfer
Jul  5 13:44:29 vasquez kernel: [ 3211.401017] gspca: stream off OK
Jul  5 13:44:29 vasquez kernel: [ 3211.401348] gspca: cheese close
Jul  5 13:44:29 vasquez kernel: [ 3211.401351] gspca: frame free
Jul  5 13:44:29 vasquez kernel: [ 3211.401439] gspca: close done
Jul  5 13:44:29 vasquez kernel: [ 3211.692105] gspca: cheese open
Jul  5 13:44:29 vasquez kernel: [ 3211.692110] gspca: open done
Jul  5 13:44:29 vasquez kernel: [ 3211.775531] gspca: frame alloc frsz: 307200
Jul  5 13:44:29 vasquez kernel: [ 3211.775634] gspca: reqbufs st:0 c:2
Jul  5 13:44:29 vasquez kernel: [ 3211.775684] gspca: mmap start:f4f1b000 size:307200
Jul  5 13:44:29 vasquez kernel: [ 3211.775704] gspca: mmap start:f4ed0000 size:307200
Jul  5 13:44:29 vasquez kernel: [ 3211.775724] gspca: use alt 3 ep 0x81
Jul  5 13:44:29 vasquez kernel: [ 3211.777563] gspca: init transfer alt 3
Jul  5 13:44:29 vasquez kernel: [ 3211.777567] gspca: isoc 32 pkts size 2048 = bsize:65536
Jul  5 13:44:32 vasquez kernel: [ 3214.384140] gspca: stream on OK GBRG 640x480
Jul  5 13:44:53 vasquez kernel: [ 3235.832919] gspca: kill transfer
Jul  5 13:44:53 vasquez kernel: [ 3236.008037] gspca: stream off OK
Jul  5 13:44:53 vasquez kernel: [ 3236.008274] gspca: cheese close
Jul  5 13:44:53 vasquez kernel: [ 3236.008277] gspca: frame free
Jul  5 13:44:53 vasquez kernel: [ 3236.008336] gspca: close done
Jul  5 13:45:12 vasquez kernel: [ 3254.304756] gspca: cheese open
Jul  5 13:45:12 vasquez kernel: [ 3254.304764] gspca: open done
Jul  5 13:45:12 vasquez kernel: [ 3254.306802] gspca: cheese close
Jul  5 13:45:12 vasquez kernel: [ 3254.306808] gspca: close done
Jul  5 13:45:12 vasquez kernel: [ 3254.391772] gspca: cheese open
Jul  5 13:45:12 vasquez kernel: [ 3254.391779] gspca: open done
Jul  5 13:45:12 vasquez kernel: [ 3254.393759] gspca: frame alloc frsz: 1920000
Jul  5 13:45:12 vasquez kernel: [ 3254.396468] gspca: reqbufs st:0 c:2
Jul  5 13:45:12 vasquez kernel: [ 3254.396575] gspca: mmap start:b4e6e000 size:1921024
Jul  5 13:45:12 vasquez kernel: [ 3254.396712] gspca: mmap start:b4c99000 size:1921024
Jul  5 13:45:12 vasquez kernel: [ 3254.396830] gspca: use alt 1 ep 0x81
Jul  5 13:45:12 vasquez kernel: [ 3254.398798] gspca: init transfer alt 1
Jul  5 13:45:12 vasquez kernel: [ 3254.398803] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:45:15 vasquez kernel: [ 3257.559362] gspca: stream on OK GBRG 1600x1200
Jul  5 13:45:16 vasquez kernel: [ 3258.278392] gspca: kill transfer
Jul  5 13:45:16 vasquez kernel: [ 3258.445015] gspca: stream off OK
Jul  5 13:45:16 vasquez kernel: [ 3258.445640] gspca: cheese close
Jul  5 13:45:16 vasquez kernel: [ 3258.445643] gspca: frame free
Jul  5 13:45:16 vasquez kernel: [ 3258.445949] gspca: close done
Jul  5 13:45:17 vasquez kernel: [ 3259.356373] gspca: cheese open
Jul  5 13:45:17 vasquez kernel: [ 3259.356379] gspca: open done
Jul  5 13:45:17 vasquez kernel: [ 3259.468991] gspca: frame alloc frsz: 307200
Jul  5 13:45:17 vasquez kernel: [ 3259.469102] gspca: reqbufs st:0 c:2
Jul  5 13:45:17 vasquez kernel: [ 3259.469170] gspca: mmap start:b418d000 size:307200
Jul  5 13:45:17 vasquez kernel: [ 3259.469193] gspca: mmap start:b4142000 size:307200
Jul  5 13:45:17 vasquez kernel: [ 3259.469215] gspca: use alt 3 ep 0x81
Jul  5 13:45:17 vasquez kernel: [ 3259.471039] gspca: init transfer alt 3
Jul  5 13:45:17 vasquez kernel: [ 3259.471042] gspca: isoc 32 pkts size 2048 = bsize:65536
Jul  5 13:45:20 vasquez kernel: [ 3262.252107] gspca: stream on OK GBRG 640x480
Jul  5 13:45:25 vasquez kernel: [ 3267.264424] gspca: kill transfer
Jul  5 13:45:25 vasquez kernel: [ 3267.440016] gspca: stream off OK
Jul  5 13:45:25 vasquez kernel: [ 3267.440196] gspca: cheese close
Jul  5 13:45:25 vasquez kernel: [ 3267.440198] gspca: frame free
Jul  5 13:45:25 vasquez kernel: [ 3267.440255] gspca: close done
Jul  5 13:45:25 vasquez kernel: [ 3267.600294] gspca: cheese open
Jul  5 13:45:25 vasquez kernel: [ 3267.600299] gspca: open done
Jul  5 13:45:25 vasquez kernel: [ 3267.688254] gspca: frame alloc frsz: 480000
Jul  5 13:45:25 vasquez kernel: [ 3267.688386] gspca: reqbufs st:0 c:2
Jul  5 13:45:25 vasquez kernel: [ 3267.688443] gspca: mmap start:b4162000 size:483328
Jul  5 13:45:25 vasquez kernel: [ 3267.688471] gspca: mmap start:b40ec000 size:483328
Jul  5 13:45:25 vasquez kernel: [ 3267.688499] gspca: use alt 1 ep 0x81
Jul  5 13:45:25 vasquez kernel: [ 3267.690386] gspca: init transfer alt 1
Jul  5 13:45:25 vasquez kernel: [ 3267.690389] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:45:28 vasquez kernel: [ 3270.484085] gspca: stream on OK GBRG 800x600
Jul  5 13:45:35 vasquez kernel: [ 3277.554294] gspca: kill transfer
Jul  5 13:45:35 vasquez kernel: [ 3277.756023] gspca: stream off OK
Jul  5 13:45:35 vasquez kernel: [ 3277.756333] gspca: cheese close
Jul  5 13:45:35 vasquez kernel: [ 3277.756336] gspca: frame free
Jul  5 13:45:35 vasquez kernel: [ 3277.756422] gspca: close done
Jul  5 13:45:35 vasquez kernel: [ 3277.940760] gspca: cheese open
Jul  5 13:45:35 vasquez kernel: [ 3277.940765] gspca: open done
Jul  5 13:45:35 vasquez kernel: [ 3278.024558] gspca: frame alloc frsz: 307200
Jul  5 13:45:35 vasquez kernel: [ 3278.024657] gspca: reqbufs st:0 c:2
Jul  5 13:45:35 vasquez kernel: [ 3278.024735] gspca: mmap start:b418d000 size:307200
Jul  5 13:45:35 vasquez kernel: [ 3278.024755] gspca: mmap start:b4142000 size:307200
Jul  5 13:45:35 vasquez kernel: [ 3278.024776] gspca: use alt 3 ep 0x81
Jul  5 13:45:35 vasquez kernel: [ 3278.026626] gspca: init transfer alt 3
Jul  5 13:45:35 vasquez kernel: [ 3278.026629] gspca: isoc 32 pkts size 2048 = bsize:65536
Jul  5 13:45:38 vasquez kernel: [ 3280.965080] gspca: stream on OK GBRG 640x480
Jul  5 13:45:44 vasquez kernel: [ 3286.691397] gspca: kill transfer
Jul  5 13:45:44 vasquez kernel: [ 3286.869046] gspca: stream off OK
Jul  5 13:45:44 vasquez kernel: [ 3286.869292] gspca: cheese close
Jul  5 13:45:44 vasquez kernel: [ 3286.869295] gspca: frame free
Jul  5 13:45:44 vasquez kernel: [ 3286.869350] gspca: close done
Jul  5 13:45:44 vasquez kernel: [ 3287.026980] gspca: cheese open
Jul  5 13:45:44 vasquez kernel: [ 3287.026985] gspca: open done
Jul  5 13:45:44 vasquez kernel: [ 3287.111398] gspca: frame alloc frsz: 1228800
Jul  5 13:45:44 vasquez kernel: [ 3287.111671] gspca: reqbufs st:0 c:2
Jul  5 13:45:44 vasquez kernel: [ 3287.111725] gspca: mmap start:b40ac000 size:1228800
Jul  5 13:45:44 vasquez kernel: [ 3287.111800] gspca: mmap start:aaf6c000 size:1228800
Jul  5 13:45:44 vasquez kernel: [ 3287.111860] gspca: use alt 1 ep 0x81
Jul  5 13:45:44 vasquez kernel: [ 3287.113747] gspca: init transfer alt 1
Jul  5 13:45:44 vasquez kernel: [ 3287.113751] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:45:48 vasquez kernel: [ 3290.481105] gspca: stream on OK GBRG 1280x960
Jul  5 13:45:55 vasquez kernel: [ 3297.442422] gspca: kill transfer
Jul  5 13:45:55 vasquez kernel: [ 3297.605014] gspca: stream off OK
Jul  5 13:45:55 vasquez kernel: [ 3297.605614] gspca: cheese close
Jul  5 13:45:55 vasquez kernel: [ 3297.605617] gspca: frame free
Jul  5 13:45:55 vasquez kernel: [ 3297.605816] gspca: close done
Jul  5 13:45:55 vasquez kernel: [ 3297.785303] gspca: cheese open
Jul  5 13:45:55 vasquez kernel: [ 3297.785308] gspca: open done
Jul  5 13:45:55 vasquez kernel: [ 3297.868832] gspca: frame alloc frsz: 1920000
Jul  5 13:45:55 vasquez kernel: [ 3297.869292] gspca: reqbufs st:0 c:2
Jul  5 13:45:55 vasquez kernel: [ 3297.869348] gspca: mmap start:b4003000 size:1921024
Jul  5 13:45:55 vasquez kernel: [ 3297.869450] gspca: mmap start:aaec3000 size:1921024
Jul  5 13:45:55 vasquez kernel: [ 3297.869536] gspca: use alt 1 ep 0x81
Jul  5 13:45:55 vasquez kernel: [ 3297.871394] gspca: init transfer alt 1
Jul  5 13:45:55 vasquez kernel: [ 3297.871397] gspca: isoc 32 pkts size 3072 = bsize:98304
Jul  5 13:45:59 vasquez kernel: [ 3301.412087] gspca: stream on OK GBRG 1600x1200
Jul  5 13:46:03 vasquez kernel: [ 3305.396668] gspca: kill transfer
Jul  5 13:46:03 vasquez kernel: [ 3305.561069] gspca: stream off OK
Jul  5 13:46:03 vasquez kernel: [ 3305.561989] gspca: cheese close
Jul  5 13:46:03 vasquez kernel: [ 3305.561992] gspca: frame free
Jul  5 13:46:03 vasquez kernel: [ 3305.562294] gspca: close done
Jul  5 13:46:03 vasquez kernel: [ 3305.699186] gspca: cheese open
Jul  5 13:46:03 vasquez kernel: [ 3305.699191] gspca: open done
Jul  5 13:46:03 vasquez kernel: [ 3305.787714] gspca: frame alloc frsz: 307200
Jul  5 13:46:03 vasquez kernel: [ 3305.787803] gspca: reqbufs st:0 c:2
Jul  5 13:46:03 vasquez kernel: [ 3305.787861] gspca: mmap start:b418d000 size:307200
Jul  5 13:46:03 vasquez kernel: [ 3305.787881] gspca: mmap start:b4142000 size:307200
Jul  5 13:46:03 vasquez kernel: [ 3305.787902] gspca: use alt 3 ep 0x81
Jul  5 13:46:03 vasquez kernel: [ 3305.789733] gspca: init transfer alt 3
Jul  5 13:46:03 vasquez kernel: [ 3305.789736] gspca: isoc 32 pkts size 2048 = bsize:65536
Jul  5 13:46:06 vasquez kernel: [ 3308.793086] gspca: stream on OK GBRG 640x480
Jul  5 13:46:09 vasquez kernel: [ 3311.643692] gspca: cheese close
Jul  5 13:46:09 vasquez kernel: [ 3311.643698] gspca: kill transfer
Jul  5 13:46:09 vasquez kernel: [ 3311.832021] gspca: stream off OK
Jul  5 13:46:09 vasquez kernel: [ 3311.832028] gspca: frame free
Jul  5 13:46:09 vasquez kernel: [ 3311.832136] gspca: close done
```

---

### Post by nol_faich on 2009-07-05
A new function replaced the previously added one.

---

Jack please test this tarball. I made some changes, I would like you to confirm these changes are fine.

---

### Post by Jack Malmostoso on 2009-07-08
Hi Nol,
I have tried the latest version and it works fine. Here is the results after the Cheese testing:```
jack@vasquez:~/Desktop$ dmesg | grep gl860
[ 1990.300684] calling  sd_mod_init+0x0/0x1de [gspca_gl860] @ 30285
[ 1990.300690] gspca_gl860: driver startup - version 0.9
[ 1990.807513] gspca_gl860: probe 1=ff
[ 1990.807518] gspca_gl860: probing for sensor OV2640 or OV9655
[ 1990.812383] gspca_gl860: probe 2= 0
[ 1990.920884] gspca_gl860: probe 2= 0
[ 1991.028888] gspca_gl860: probe 2= 0
[ 1991.137018] gspca_gl860: probe 2= 0
[ 1991.244896] gspca_gl860: probe 2= 0
[ 1991.352896] gspca_gl860: probe 2= 0
[ 1991.460896] gspca_gl860: probe 2= 0
[ 1991.568896] gspca_gl860: probe 2= 0
[ 1991.676901] gspca_gl860: probe 2= 0
[ 1991.784900] gspca_gl860: probe 2= 0
[ 1991.893901] gspca_gl860: probe 2= 0
[ 1992.001022] gspca_gl860: probe 2= 0
[ 1992.109284] gspca_gl860: probe 2= 0
[ 1992.217901] gspca_gl860: probe 2= 0
[ 1992.324903] gspca_gl860: probe 2= 0
[ 1992.432909] gspca_gl860: probe 2= 0
[ 1992.541035] gspca_gl860: probe 2= 0
[ 1992.648906] gspca_gl860: probe 2= 0
[ 1992.752913] gspca_gl860: probe 2= 0
[ 1992.861909] gspca_gl860: probe 2= 0
[ 1992.969045] gspca_gl860: probe 2= 0
[ 1993.076917] gspca_gl860: probe 2= 0
[ 1993.186041] gspca_gl860: probe 2= 0
[ 1993.294045] gspca_gl860: probe 2= 0
[ 1993.400922] gspca_gl860: probe 2= 0
[ 1993.509917] gspca_gl860: probe 2= 0
[ 1993.616922] gspca_gl860: probe 2= 0
[ 1993.725927] gspca_gl860: probe 2= 0
[ 1993.834050] gspca_gl860: probe 2= 0
[ 1993.941926] gspca_gl860: probe 2= 0
[ 1994.049925] gspca_gl860: probe 2= 0
[ 1994.153032] gspca_gl860: no relevant sensor answer (count: #00=31/#FF=0)
[ 1994.153037] gspca_gl860: * 1.3Mpixels -> set the 'sa' flavour
[ 1994.153040] gspca_gl860: * 2.0Mpixels -> set the 'ms' flavour
[ 1994.153043] gspca_gl860: To set a flavour, ask your admin to add that line to /etc/modprobe.d/options:
[ 1994.153047] gspca_gl860: options gspca_gl860 pilote="ms" or "sa"
[ 1994.153050] gspca_gl860: If a 'options gspca_gl860' line is already there, change the 'pilote' value or add 'pilote="ms" or "sa"' to that line
[ 1994.153055] gspca_gl860: #00 > #FF -> Trying 'ms'
[ 1994.153058] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms)
[ 1995.750666] gspca_gl860: Camera is now controlling video device /dev/video0
[ 1995.750711] usbcore: registered new interface driver gspca_gl860
[ 1995.750716] gspca_gl860: driver registered
[ 1995.750730] initcall sd_mod_init+0x0/0x1de [gspca_gl860] returned 0 after 5322295 usecs

``````
jack@vasquez:~/Desktop$ sudo grep gspca /var/log/syslog
Jul  8 22:32:24 vasquez kernel: [ 1989.873586] gspca: main deregistered
Jul  8 22:32:25 vasquez kernel: [ 1990.276442] calling  gspca_init+0x0/0x22 [gspca_main] @ 30282
Jul  8 22:32:25 vasquez kernel: [ 1990.276449] gspca: main v2.6.0 registered
Jul  8 22:32:25 vasquez kernel: [ 1990.276456] initcall gspca_init+0x0/0x22 [gspca_main] returned 0 after 3 usecs
Jul  8 22:32:25 vasquez kernel: [ 1990.300684] calling  sd_mod_init+0x0/0x1de [gspca_gl860] @ 30285
Jul  8 22:32:25 vasquez kernel: [ 1990.300690] gspca_gl860: driver startup - version 0.9
Jul  8 22:32:25 vasquez kernel: [ 1990.300716] gspca: probing 05e3:0503
Jul  8 22:32:25 vasquez kernel: [ 1990.807513] gspca_gl860: probe 1=ff
Jul  8 22:32:25 vasquez kernel: [ 1990.807518] gspca_gl860: probing for sensor OV2640 or OV9655
Jul  8 22:32:25 vasquez kernel: [ 1990.812383] gspca_gl860: probe 2= 0
Jul  8 22:32:25 vasquez kernel: [ 1990.920884] gspca_gl860: probe 2= 0
Jul  8 22:32:25 vasquez kernel: [ 1991.028888] gspca_gl860: probe 2= 0
Jul  8 22:32:25 vasquez kernel: [ 1991.137018] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1991.244896] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1991.352896] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1991.460896] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1991.568896] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1991.676901] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1991.784900] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1991.893901] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1992.001022] gspca_gl860: probe 2= 0
Jul  8 22:32:26 vasquez kernel: [ 1992.109284] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.217901] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.324903] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.432909] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.541035] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.648906] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.752913] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.861909] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1992.969045] gspca_gl860: probe 2= 0
Jul  8 22:32:27 vasquez kernel: [ 1993.076917] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.186041] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.294045] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.400922] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.509917] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.616922] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.725927] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.834050] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1993.941926] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1994.049925] gspca_gl860: probe 2= 0
Jul  8 22:32:28 vasquez kernel: [ 1994.153032] gspca_gl860: no relevant sensor answer (count: #00=31/#FF=0)
Jul  8 22:32:28 vasquez kernel: [ 1994.153037] gspca_gl860: * 1.3Mpixels -> set the 'sa' flavour
Jul  8 22:32:28 vasquez kernel: [ 1994.153040] gspca_gl860: * 2.0Mpixels -> set the 'ms' flavour
Jul  8 22:32:28 vasquez kernel: [ 1994.153043] gspca_gl860: To set a flavour, ask your admin to add that line to /etc/modprobe.d/options:
Jul  8 22:32:28 vasquez kernel: [ 1994.153047] gspca_gl860: options gspca_gl860 pilote="ms" or "sa"
Jul  8 22:32:28 vasquez kernel: [ 1994.153050] gspca_gl860: If a 'options gspca_gl860' line is already there, change the 'pilote' value or add 'pilote="ms" or "sa"' to that line
Jul  8 22:32:28 vasquez kernel: [ 1994.153055] gspca_gl860: #00 > #FF -> Trying 'ms'
Jul  8 22:32:28 vasquez kernel: [ 1994.153058] gspca_gl860: 05e3:0503 OV2640 2.0M: subdriver Malmostoso (ms)
Jul  8 22:32:30 vasquez kernel: [ 1995.750661] gspca: probe ok
Jul  8 22:32:30 vasquez kernel: [ 1995.750666] gspca_gl860: Camera is now controlling video device /dev/video0
Jul  8 22:32:30 vasquez kernel: [ 1995.750711] usbcore: registered new interface driver gspca_gl860
Jul  8 22:32:30 vasquez kernel: [ 1995.750716] gspca_gl860: driver registered
Jul  8 22:32:30 vasquez kernel: [ 1995.750730] initcall sd_mod_init+0x0/0x1de [gspca_gl860] returned 0 after 5322295 usecs

```

I haven't had time to do the test in Windows. Do you still need them?

---

### Post by nol_faich on 2009-07-08
Thanks for the tests.
I need your logs with Windows Jack because they are very valuable. Your Windows driver is the only one able to discriminate every sensor.
In the logs you've just posted you can see a bunch of "probe2=0", this means that your sensor did not answer when I asked it to give its ID.
From is 0's answers I deduce it is your flavour to use but this is very tricky. Logs should fix this. 
I changed the driver numbering scheme, it is in 0.9, so nobody has to expect the driver is performing perfectly. Take your time to do these logs.


@ BUGabundo
Special test script for 2.6.31.

---

### Post by BUGabundo on 2009-07-10
Nol the last version u gave me, wont persist cross reboots! what needs to change? dont want to compile it on every boot :(

---

### Post by nol_faich on 2009-07-10
sudo cp gspca_gl860.ko  /lib/modules/$(uname -r)/kernel/drivers/media/video
sudo depmod -a          /lib/modules/$(uname -r)/kernel/drivers/media/video

Add gspca_gl860 to /etc/modules.

I submitted the driver to GSPCA maintainer. I have a lot of "grammatical" corrections to do.

---

### Post by BUGabundo on 2009-07-12
> **nol_faich said:**
> sudo cp gspca_gl860.ko  /lib/modules/$(uname -r)/kernel/drivers/media/video
sudo depmod -a          /lib/modules/$(uname -r)/kernel/drivers/media/video
Add gspca_gl860 to /etc/modules.

this doesnt work. after reboot i have no /dev/video0 :(

---

### Post by nol_faich on 2009-07-13
Oops

sudo depmod -a /lib/modules/$(uname -r)/kernel/drivers/media/video/gspca_gl860.ko

---

### Post by BUGabundo on 2009-07-13
> **nol_faich said:**
> 
sudo depmod -a /lib/modules/$(uname -r)/kernel/drivers/media/video/gspca_gl860.ko

no output, so I tried to load it:
$ sudo modprobe -v gspca_gl860
WARNING: All config files need .conf: /etc/modprobe.d/linux-wlan-ng, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
insmod /lib/modules/2.6.31-2-generic/kernel/drivers/media/video/gspca_gl860.ko pilote="" 
FATAL: Error inserting gspca_gl860 (/lib/modules/2.6.31-2-generic/kernel/drivers/media/video/gspca_gl860.ko): Invalid module format

any tips?

---

### Post by nol_faich on 2009-07-13
Maybe the v4l used by GSPCA is somewhat different from the one of your kernel. Try the last "load_gspca" you modified to see if you can load the driver. If yes, the videodev, gspcamain and so on may be slightly different...

---

### Post by nol_faich on 2009-08-23
New driver version for tests. The tarball content is a load script (load_gspca2) and a patch applied by the script. You need an internet connexion to do the test because a tarball is downloaded to get v4l sources.
Load_gspca2 explains what to test at the of driver load.

---

### Post by BUGabundo on 2009-08-24
$ dmesg | grep gl860 
[ 9330.475455] gspca_gl860: driver startup - version 0.9c
[ 9331.023577] gspca_gl860: probe 1= 0
[ 9331.023581] gspca_gl860: 05e3:0503 MI2020 2.0M: subdriver Hulkie/Iceman/Soro (his)
[ 9334.014676] gspca_gl860: Camera is now controlling video device /dev/video0
[ 9334.014715] usbcore: registered new interface driver gspca_gl860
[ 9334.014720] gspca_gl860: driver registered


all testes worked but LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama -x 1280 -y 960
had to ajust HUE on first start
VLC was upside down

---

### Post by johnaaronrose on 2009-09-20
BUGabundo & Nol,

I have a webcam -5e3:0503 on a Medion 2320. I compiled using load_gspca from the FINAL.tgz. I used the command 'sudo depmod -a          /lib/modules/$(uname -r)/kernel/drivers/media/video' and also got no /dev/video0. I then noticed your post about this result and used 'sudo depmod -a          /lib/modules/$(uname -r)/kernel/drivers/media/video/gspca_gl860.ko' as per Nol's subsequent post. I rebooted and no /dev/video0.

I have 2 questions:
1. How do I recover /dev/video0? I Googled and found (for Suse) a message stating to use chmod u+x MAKEDEV followed by ./MAKEDEV. I haven't dared try that. Does that work for Ubuntu, specifically Hardy.
2. Cheese still doesn't display for the webcam. It displays the same as before i.e. a number of coloured rectangles. Could this be because I used the FINAL.tgz attached by Nol in an earlier post (i.e. is there a later version)? I'm using Hardy with kernel 2.6.24-4. Or do I have to upgrade to Jaunty?

---

### Post by johnaaronrose on 2009-09-20
More info - result of dmesg|grep gl860:
[   36.633373] gspca_gl860: Unknown symbol gspca_frame_add
[   36.633430] gspca_gl860: Unknown symbol gspca_debug
[   36.633609] gspca_gl860: Unknown symbol gspca_disconnect
[   36.633668] gspca_gl860: Unknown symbol gspca_resume
[   36.633721] gspca_gl860: Unknown symbol gspca_dev_probe
[   36.633781] gspca_gl860: Unknown symbol gspca_suspend
[   38.248196] gspca_gl860: Unknown symbol gspca_frame_add
[   38.248255] gspca_gl860: Unknown symbol gspca_debug
[   38.248436] gspca_gl860: Unknown symbol gspca_disconnect
[   38.248496] gspca_gl860: Unknown symbol gspca_resume
[   38.248551] gspca_gl860: Unknown symbol gspca_dev_probe
[   38.248609] gspca_gl860: Unknown symbol gspca_suspend

Is FINAL.tgz install not compatible with Hardy & kernel 2.6.24-24-generic?

---

### Post by johnaaronrose on 2009-09-20
I've just done a clean install of jaunty with updates. I've run load_gspca (from gspca_final). It compiled & modprobed gspca_gl860.ko OK. Camorama displays a window stating 'Unable to capture image'. Cheese displays photo (i.e. webcam view) OK except that it's very light in colour and thus difficult to make out, for both 1280x960 & 640x480 sizes. Is there a newer version of the driver which gives realistic colour contrast? PS kernel version is 2.6.28-15-generic.

---

### Post by nol_faich on 2009-09-20
Hi!

The issue with camorama is known, GSPCA is intended to be used with V4L2 and camorama is a V4L1 application.
To use a V4L1 application such as camorama:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
(note that you also need to set "palette"/"hue" to the max with camorama)

v4l2ucp allows you to change settings while cheese is working. You can find it here [http://www.debian-multimedia.org/pool/main/v/v4l2ucp/v4l2ucp.php](http://www.debian-multimedia.org/pool/main/v/v4l2ucp/v4l2ucp.php) if you distro does not have it. If you miss color, "saturation" may be the reason.

---

### Post by nol_faich on 2009-09-20
@All : the GSPCA driver version is now part V4L and will appear in 2.6.32.

A driver is there : [http://launchpadlibrarian.net/32125266/gspca_gl860e2.tgz](http://launchpadlibrarian.net/32125266/gspca_gl860e2.tgz)
To test it, use "./load3b".
To install the driver ".load3b _i".
The install step downloads the V4L sources, compile the driver, copy files in /lib/modules and update the list of modules to load at startup.

---

### Post by johnaaronrose on 2009-09-21
Nol,

Thanks for your post re Camorama & setting hue etc for Cheese. I downloaded the i386 2.0.0.0 deb package & tried to install it.  The package installer displayed "Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.5.2)". However, according to Synaptic, libqtcore4 4.5 is already installed. Any suggestions?

---

### Post by johnaaronrose on 2009-09-21
Please retract previos post. Version 1.2-0.1 of v4l2ucp works fine.

---

### Post by soro2005 on 2009-10-22
Nol,

Now that we're close to the Karmic release, would you mind posting here or elsewhere where to find the current version of the gspca driver, and how to install it permanently? As far as I understand, Karmic users will still have to install it manually. Thanks!

---

### Post by nol_faich on 2009-10-27
Hi, an install script is there :
[http://launchpadlibrarian.net/34343070/gspca_gl860_2.tgz](http://launchpadlibrarian.net/34343070/gspca_gl860_2.tgz)

If you have Karmic (or a kernel >= 2.6.31), "./inst_gl860 -m" should load, compile and install the driver.

For 2.6.30 users, "./inst_gl860 -i". However for this kernel, the driver requires a suitable videodev so it compiles it. As over webcam drivers and (I guess) TV tuner depend on it, they need to be compiled again to be compliant with that new videodev...
Plug or use these video equipments, get the modules you have to compile together with the driver using :
lsmod | grep "^videodev" (ex.: "videodev               41344  2 gspca_main,uvcvideo")
These modules may be used by other drivers so get them with :
lsmod | grep "^DEPENDENCY" (ex.: lsmod | grep "^gspca_main")
Remove config32 and config64 to compile all the V4L modules and peek and choose the ones you need for other equipments. Install Karmic may be easier unless you use only this webcam...

Otherwise :
Stand-alone driver (<=2.6.29) : [http://sourceforge.net/projects/gl860/files/gl860/2009%20june%2011/gl860_2.6.29f.tgz/download](http://sourceforge.net/projects/gl860/files/gl860/2009%20june%2011/gl860_2.6.29f.tgz/download)

---

### Post by Xaikon on 2009-10-31
Hi,

I have a 0503 Genesys Logic, Inc webcam. Today I just installed Ubuntu 9.10 and I tried to set up my webcam without success. I think I tried with each one script/package that you have linked from this thread but without luck.

The thing is that it worked just fine with Ubuntu 9.04. Specifically, I used this one [http://ubuntuforums.org/attachment.php?attachmentid=120079&d=1246826499](http://ubuntuforums.org/attachment.php?attachmentid=120079&d=1246826499)

But when I execute that script now, this error appears:

/home/nadia/Descargas/gspca_final/gspca-c218eabb04dc/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/home/nadia/Descargas/gspca_final/gspca-c218eabb04dc/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/nadia/Descargas/gspca_final/gspca-c218eabb04dc/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/home/nadia/Descargas/gspca_final/gspca-c218eabb04dc/v4l'
make: *** [all] Error 2
sudo rmmod gl860
sudo rmmod gspca_gl860
sudo rmmod gspca_main
sudo rmmod videodev
ERROR: Module videodev does not exist in /proc/modules
sudo rmmod v4l1-compat
ERROR: Module v4l1_compat does not exist in /proc/modules
sudo modprobe i2c-core
FATAL: Module i2c_core not found.
sudo insmod v4l/v4l1-compat.ko
insmod: can't read 'v4l/v4l1-compat.ko': No such file or directory

And with most of the other scripts I executed the problem is the same or really similar. It seems to be a compilation problem I guess...

On the other hand, I also downloaded this one [http://ubuntuforums.org/attachment.php?attachmentid=126459&d=1251385707](http://ubuntuforums.org/attachment.php?attachmentid=126459&d=1251385707) ([gspca_gl860g.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=126459&d=1251385707")) and it seemed to work:

make[1]: se sale del directorio `/home/nadia/Descargas/gspca_gl860g/gspca-c9f3938870ab/v4l'
sudo rmmod gl860
sudo rmmod gspca_gl860
sudo rmmod gspca_main
sudo rmmod videodev
ERROR: Module videodev does not exist in /proc/modules
sudo rmmod v4l1-compat
ERROR: Module v4l1_compat does not exist in /proc/modules
sudo modprobe i2c-core
FATAL: Module i2c_core not found.
sudo insmod v4l/v4l1-compat.ko
sudo insmod v4l/videodev.ko
sudo insmod v4l/gspca_main.ko
sudo insmod v4l/gspca_gl860.ko
Install OK
Please test (depending on your hardware) :
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama -x 640 -y 480
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama -x 800 -y 600
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama -x 1280 -y 960 (or 1024 for 'his')
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama -x 1600 -y 1200
 AND
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc v4l2:// :v4l2-vdev="/dev/video0"
test ALL driver settings (brightness, and so on) using 'extended options'/'V4L2 controls'
Boolean settings (flip, mirror, freq50) may fail

But with camorama didn't work and with cheese something weird happened. With skype it didn't work either.

I am basically interested in using the webcam with skype to let my parents see my face from time to time since I'm living abroad :D

Just let me know if you need more information to figure out what the problem could be.

Thanks!
Xaikon

---

### Post by nol_faich on 2009-11-02
Hi Xaikon,

the old scripts compile the whole V4L and this is not suitable (it is long and compilation may fail because of differencies between the kernel used for V4L and the installed one).

Could you report the result of the [http://launchpadlibrarian.net/34343070/gspca_gl860_2.tgz](http://launchpadlibrarian.net/34343070/gspca_gl860_2.tgz) script. It compiles only what is needed, no other things so the compilation error won't happen. As you have a 9.10, you may try "./inst_gl860 -m" to compile and install the driver.

If you have a trouble with Camorama or Skype or any other application, please:
- report "grep gl860 /var/log/syslog"
- report the result of the command line "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so application"
- a JPG screenshot if a strange image is appearing.

---

### Post by padapada on 2009-11-03
Camorama result is perfect, but the defaults in Skype make it look blueish.

I used: LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Skype does not allow me to change the hue value, can I communicate the value through a config file or environment variable?

Patrick,

---

### Post by nol_faich on 2009-11-03
Camorama has a major trouble, it swaps blue and red colors.
In order to have the right colors you need to set "hue" to the max, 
but most applications do not required to have the value set to the max.
If you do not have to use Camorama, set hue to max and reset it to the min before leaving it so that other applications have no trouble with the color.
I should warn about that in the install script.

---

### Post by Xaikon on 2009-11-03
Hi Nol_faich,

Thank you very much. I executed the script you said. This is the output:

make -C "/lib/modules/2.6.31-14-generic/build"    SUBDIRS="/home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860" modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gl860.o
  CC [M]  /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gl860-mi1320.o
  CC [M]  /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gl860-mi2020.o
  CC [M]  /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gl860-ov2640.o
  CC [M]  /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gl860-ov9655.o
  LD [M]  /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gspca_gl860.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gspca_gl860.mod.o
  LD [M]  /home/nadia/Descargas/gspca_gl860_2/gspca-dab86a1af599/linux/drivers/media/video/gspca/gl860/gspca_gl860.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'
sudo rmmod gspca_gl860
sudo modprobe gspca_main
sudo insmod gspca_gl860.ko
insmod: error inserting 'gspca_gl860.ko': -1 Unknown symbol in module

After that, I try to execute camorama and I receive this error:
Could not connect to video device (/dev/video0)

Output of "grep gl860 /var/log/syslog":
Nov  3 10:06:17 nadia-laptop kernel: [   13.060429] gspca_gl860: driver startup - version 0.9d10
Nov  3 10:06:17 nadia-laptop kernel: [   13.184045] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 10:06:17 nadia-laptop kernel: [   13.217553] gspca_gl860: probe=0x00
Nov  3 10:06:17 nadia-laptop kernel: [   13.258428] gspca_gl860: probe=0x00
Nov  3 10:06:17 nadia-laptop kernel: [   13.293428] gspca_gl860: probe=0x00
Nov  3 10:06:17 nadia-laptop kernel: [   13.329553] gspca_gl860: probe=0x00
Nov  3 10:06:17 nadia-laptop kernel: [   13.329556] gspca_gl860: Not any 0xff -> MI2020
Nov  3 10:06:17 nadia-laptop kernel: [   13.329559] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 10:06:18 nadia-laptop kernel: [   16.401110] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 10:06:18 nadia-laptop kernel: [   16.401145] usbcore: registered new interface driver gspca_gl860
Nov  3 10:06:18 nadia-laptop kernel: [   16.401148] gspca_gl860: driver registered
Nov  3 10:18:51 nadia-laptop kernel: [  689.993996] gspca_gl860 2-6:1.0: no reset_resume for driver gspca_gl860?
Nov  3 10:18:51 nadia-laptop kernel: [  690.944033] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 10:18:51 nadia-laptop kernel: [  690.977494] gspca_gl860: probe=0x00
Nov  3 10:18:51 nadia-laptop kernel: [  691.009494] gspca_gl860: probe=0x00
Nov  3 10:18:51 nadia-laptop kernel: [  691.041494] gspca_gl860: probe=0x00
Nov  3 10:18:51 nadia-laptop kernel: [  691.073494] gspca_gl860: probe=0x00
Nov  3 10:18:51 nadia-laptop kernel: [  691.073496] gspca_gl860: Not any 0xff -> MI2020
Nov  3 10:18:51 nadia-laptop kernel: [  691.073498] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 10:18:51 nadia-laptop kernel: [  694.032073] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 10:18:51 nadia-laptop kernel: [  694.032210] Modules linked in: binfmt_misc bridge stp bnep ppdev snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep arc4 ecb snd_pcm_oss snd_mixer_oss iwlagn iwlcore snd_pcm snd_seq_dummy i2c_viapro iptable_filter snd_seq_oss snd_seq_midi ip_tables hwmon_vid gspca_gl860 snd_rawmidi snd_seq_midi_event coretemp snd_seq snd_timer snd_seq_device gspca_main joydev mac80211 x_tables videodev snd soundcore snd_page_alloc asus_laptop ricoh_mmc sdhci_pci sdhci v4l1_compat btusb lp cfg80211 psmouse serio_raw led_class parport dm_raid45 xor ohci1394 ieee1394 sky2 video output intel_agp agpgart
Nov  3 10:20:29 nadia-laptop kernel: [   12.637500] gspca_gl860: driver startup - version 0.9d10
Nov  3 10:20:29 nadia-laptop kernel: [   12.749363] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 10:20:29 nadia-laptop kernel: [   12.783939] gspca_gl860: probe=0x00
Nov  3 10:20:29 nadia-laptop kernel: [   12.818556] gspca_gl860: probe=0x00
Nov  3 10:20:29 nadia-laptop kernel: [   12.853431] gspca_gl860: probe=0x00
Nov  3 10:20:29 nadia-laptop kernel: [   12.885554] gspca_gl860: probe=0x00
Nov  3 10:20:29 nadia-laptop kernel: [   12.885558] gspca_gl860: Not any 0xff -> MI2020
Nov  3 10:20:29 nadia-laptop kernel: [   12.885561] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 10:20:29 nadia-laptop kernel: [   16.044103] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 10:20:29 nadia-laptop kernel: [   16.044140] usbcore: registered new interface driver gspca_gl860
Nov  3 10:20:29 nadia-laptop kernel: [   16.044142] gspca_gl860: driver registered
Nov  3 10:51:17 nadia-laptop kernel: [ 1030.621987] gspca_gl860 2-6:1.0: no reset_resume for driver gspca_gl860?
Nov  3 10:51:17 nadia-laptop kernel: [ 1031.628033] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 10:51:17 nadia-laptop kernel: [ 1031.661486] gspca_gl860: probe=0x00
Nov  3 10:51:17 nadia-laptop kernel: [ 1031.693486] gspca_gl860: probe=0x00
Nov  3 10:51:17 nadia-laptop kernel: [ 1031.725486] gspca_gl860: probe=0x00
Nov  3 10:51:17 nadia-laptop kernel: [ 1031.757486] gspca_gl860: probe=0x00
Nov  3 10:51:17 nadia-laptop kernel: [ 1031.757488] gspca_gl860: Not any 0xff -> MI2020
Nov  3 10:51:17 nadia-laptop kernel: [ 1031.757490] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 10:51:17 nadia-laptop kernel: [ 1034.716071] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 10:51:17 nadia-laptop kernel: [ 1034.716209] Modules linked in: binfmt_misc bridge stp bnep ppdev snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss arc4 snd_mixer_oss ecb snd_pcm iwlagn snd_seq_dummy snd_seq_oss iwlcore joydev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq i2c_viapro mac80211 hwmon_vid coretemp snd_timer gspca_gl860 snd_seq_device sdhci_pci gspca_main asus_laptop iptable_filter psmouse ip_tables sdhci snd soundcore snd_page_alloc videodev led_class ricoh_mmc lp btusb serio_raw cfg80211 v4l1_compat x_tables parport dm_raid45 xor video output ohci1394 ieee1394 sky2 intel_agp agpgart
Nov  3 10:53:47 nadia-laptop kernel: [   12.820567] gspca_gl860: driver startup - version 0.9d10
Nov  3 10:53:47 nadia-laptop kernel: [   12.933028] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 10:53:47 nadia-laptop kernel: [   12.966204] gspca_gl860: probe=0x00
Nov  3 10:53:47 nadia-laptop kernel: [   12.997429] gspca_gl860: probe=0x00
Nov  3 10:53:47 nadia-laptop kernel: [   13.029554] gspca_gl860: probe=0x00
Nov  3 10:53:47 nadia-laptop kernel: [   13.061437] gspca_gl860: probe=0x00
Nov  3 10:53:47 nadia-laptop kernel: [   13.061441] gspca_gl860: Not any 0xff -> MI2020
Nov  3 10:53:47 nadia-laptop kernel: [   13.061443] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 10:53:47 nadia-laptop kernel: [   16.169109] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 10:53:47 nadia-laptop kernel: [   16.169143] usbcore: registered new interface driver gspca_gl860
Nov  3 10:53:47 nadia-laptop kernel: [   16.169145] gspca_gl860: driver registered
Nov  3 13:35:02 nadia-laptop kernel: [   12.478622] gspca_gl860: driver startup - version 0.9d10
Nov  3 13:35:02 nadia-laptop kernel: [   12.597038] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 13:35:02 nadia-laptop kernel: [   12.629540] gspca_gl860: probe=0x00
Nov  3 13:35:02 nadia-laptop kernel: [   12.661419] gspca_gl860: probe=0x00
Nov  3 13:35:02 nadia-laptop kernel: [   12.693415] gspca_gl860: probe=0x00
Nov  3 13:35:02 nadia-laptop kernel: [   12.729541] gspca_gl860: probe=0x00
Nov  3 13:35:02 nadia-laptop kernel: [   12.729545] gspca_gl860: Not any 0xff -> MI2020
Nov  3 13:35:02 nadia-laptop kernel: [   12.729547] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 13:35:03 nadia-laptop kernel: [   15.904098] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 13:35:03 nadia-laptop kernel: [   15.904130] usbcore: registered new interface driver gspca_gl860
Nov  3 13:35:03 nadia-laptop kernel: [   15.904139] gspca_gl860: driver registered
Nov  3 16:05:33 nadia-laptop kernel: [   12.905676] gspca_gl860: driver startup - version 0.9d10
Nov  3 16:05:33 nadia-laptop kernel: [   13.032028] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 16:05:33 nadia-laptop kernel: [   13.077534] gspca_gl860: probe=0x00
Nov  3 16:05:33 nadia-laptop kernel: [   13.117415] gspca_gl860: probe=0x00
Nov  3 16:05:33 nadia-laptop kernel: [   13.153546] gspca_gl860: probe=0x00
Nov  3 16:05:33 nadia-laptop kernel: [   13.185415] gspca_gl860: probe=0x00
Nov  3 16:05:33 nadia-laptop kernel: [   13.185418] gspca_gl860: Not any 0xff -> MI2020
Nov  3 16:05:33 nadia-laptop kernel: [   13.185421] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 16:05:34 nadia-laptop kernel: [   16.269128] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 16:05:34 nadia-laptop kernel: [   16.269155] usbcore: registered new interface driver gspca_gl860
Nov  3 16:05:34 nadia-laptop kernel: [   16.269158] gspca_gl860: driver registered
Nov  3 18:57:24 nadia-laptop kernel: [   12.640213] gspca_gl860: driver startup - version 0.9d10
Nov  3 18:57:24 nadia-laptop kernel: [   12.773029] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 18:57:24 nadia-laptop kernel: [   12.805543] gspca_gl860: probe=0x00
Nov  3 18:57:24 nadia-laptop kernel: [   12.845551] gspca_gl860: probe=0x00
Nov  3 18:57:24 nadia-laptop kernel: [   12.877541] gspca_gl860: probe=0x00
Nov  3 18:57:24 nadia-laptop kernel: [   12.909539] gspca_gl860: probe=0x00
Nov  3 18:57:24 nadia-laptop kernel: [   12.909543] gspca_gl860: Not any 0xff -> MI2020
Nov  3 18:57:24 nadia-laptop kernel: [   12.909546] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 18:57:24 nadia-laptop kernel: [   16.156115] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 18:57:24 nadia-laptop kernel: [   16.156147] usbcore: registered new interface driver gspca_gl860
Nov  3 18:57:24 nadia-laptop kernel: [   16.156150] gspca_gl860: driver registered
Nov  3 21:03:13 nadia-laptop kernel: [   12.714723] gspca_gl860: driver startup - version 0.9d10
Nov  3 21:03:13 nadia-laptop kernel: [   12.828059] gspca_gl860: probing for sensor MI2020 or OVXXXX
Nov  3 21:03:13 nadia-laptop kernel: [   12.861534] gspca_gl860: probe=0x00
Nov  3 21:03:13 nadia-laptop kernel: [   12.893533] gspca_gl860: probe=0x00
Nov  3 21:03:13 nadia-laptop kernel: [   12.925536] gspca_gl860: probe=0x00
Nov  3 21:03:13 nadia-laptop kernel: [   12.957535] gspca_gl860: probe=0x00
Nov  3 21:03:13 nadia-laptop kernel: [   12.957539] gspca_gl860: Not any 0xff -> MI2020
Nov  3 21:03:13 nadia-laptop kernel: [   12.957541] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Nov  3 21:03:14 nadia-laptop kernel: [   16.105140] gspca_gl860: Camera is now controlling video device /dev/video0
Nov  3 21:03:14 nadia-laptop kernel: [   16.105161] usbcore: registered new interface driver gspca_gl860
Nov  3 21:03:14 nadia-laptop kernel: [   16.105164] gspca_gl860: driver registered
Nov  3 22:06:56 nadia-laptop kernel: [ 3838.222447] usbcore: deregistering interface driver gspca_gl860
Nov  3 22:06:56 nadia-laptop kernel: [ 3838.222595] gspca_gl860: driver deregistered
Nov  3 22:06:56 nadia-laptop kernel: [ 3838.252740] gspca_gl860: disagrees about version of symbol gspca_frame_add
Nov  3 22:06:56 nadia-laptop kernel: [ 3838.252746] gspca_gl860: Unknown symbol gspca_frame_add
Nov  3 22:06:56 nadia-laptop kernel: [ 3838.253595] gspca_gl860: disagrees about version of symbol gspca_dev_probe
Nov  3 22:06:56 nadia-laptop kernel: [ 3838.253598] gspca_gl860: Unknown symbol gspca_dev_probe


I also executed "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" and "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama" but none of the applications detected the webcam.


Just tell me if you need more info.
Jordi

---

### Post by nol_faich on 2009-11-03
I'm surprised by your log because there is a lot of driver registration and only one deregistration at the end. However it seems that the "-m" is not working. EDIT : I browsed the kernel sources and the driver is not compliant with the 2.6.31 GSPCA :(.

Please try "./inst_gl860 -t". This will compile the suitable modules and load them. With this solution, you will need to compile the other video drivers you are using of you use other video devices.

---

### Post by Xaikon on 2009-11-04
Hi,

I executed "./inst_gl860 -t" and the blue light of my webcam turned on! Then I executed Skype:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and the webcam worked! :D

Thank you very much!
Xaikon

---

### Post by nol_faich on 2009-11-05
Good!
After reboot you won't get the webcam working because the driver is not installed in the /lib directory. Use "./inst_gl860 -i" to install it.
Please note that the webcam driver needs to be compiled again after each kernel version change.
Maybe you can use Skype without the LD_PRELOAD. x86 32bits does not requires it. Theoretically, recent applications should not required the LD_PRELOAD but it seems 64 bits in not as fitted to V4L2 as 32 bits.

---

### Post by minj on 2009-11-14
```
$ uname -r
2.6.31-15-generic
$ lsusb
Bus 002 Device 004: ID 05e3:0503 Genesys Logic, Inc.
$ tar xf gspca_gl860_2.tgz
$ cd gspca_gl860_2
$ ./inst_gl860 -m
dab86a1af599.tar.gz does not exist, I'm trying to download it (5MB)

--2009-11-15 03:26:55--  http://linuxtv.org/hg/~jfrancois/gspca/archive/dab86a1af599.tar.gz
Resolving proxy.myisp.com... x.x.x.x
Connecting to proxy.myisp.com|x.x.x.x|:8080... connected.
Proxy request sent, awaiting response... 500 Internal Server Error
2009-11-15 03:26:55 ERROR 500: Internal Server Error.

Fail to download gspca sources
```

:confused:

---

### Post by nol_faich on 2009-11-15
I changed the install file, please use this one : [http://launchpadlibrarian.net/35726436/gspca_gl860_3.tgz](http://launchpadlibrarian.net/35726436/gspca_gl860_3.tgz)

---

### Post by minj on 2009-11-15
```
sudo modprobe i2c-core
FATAL: Module i2c_core not found.
```

Vlc is ok, Skype on the other hand shows static.

I am using amd64 Ubuntu Karmic in case that's relevant

---

### Post by nol_faich on 2009-11-15
You have to use the LD_PRELOAD with Skype (like with VLC). If you have any trouble with an application, try wth the LD_PRELOAD.

---

### Post by soro2005 on 2009-11-18
Also, since Skype is a 32 bit application, you need to preload the 32 bit libraries if you are on a 64 bit OS. Like so:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```
I start it like this to get the avatars etc:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins/ skype
```

---

### Post by nol_faich on 2009-11-18
Thanks for the comment.
"skype" looks really small compared to "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins/" :)

---

### Post by Jack Malmostoso on 2009-12-03
And everyone please make a GREAT applause to nol, for gl860 made it into the mainline kernel!

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=4f7cb8837cec65ade18b0e2655292fd98040234e](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=4f7cb8837cec65ade18b0e2655292fd98040234e)

Bien fait mon ami!

Now pester your distro maintainer to enable the driver by default!

---

### Post by nol_faich on 2009-12-04
Hello!

Today I have quite a weird end of day because of drivers :
- gspca_gl860 is officially part of the kernel
- while refuelling a rented car in a highway gas station, Mikko Hirvonen was doing the same on the other side of the petrol pump (likely together with his co-driver).

What a day! :)

---

### Post by johnaaronrose on 2009-12-05
Jack,
I looked at the URL page you specified. I wasn't able to figure out the kernel version that gl860 is fixed in. Which version is it?

---

### Post by nol_faich on 2009-12-05
The driver is now part of 2.6.32. It was only part of 2.6.31 development kernel up to now. All Linux based on 2.6.32 and higher manage the webcam.

The included driver is not in its last version but only the flip and mirror are missing for 0V2640.

---

### Post by nol_faich on 2010-01-03
Happy new year to everybody!

Please read this (too tired to reproduce the text here):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604/comments/132](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604/comments/132)

Jack: changes are not related to your sensor

Soro2005, BugAbundo, Blazercist (if you are still there) you are concerned.

---

### Post by soro2005 on 2010-01-04
Nol: Looks very good here, great. I have the V4L2 controls in vlc, and other than mirror and flip, all of them seem to be working like a charm. Is there a way to install the driver permanently? I'm using the 2.6.31 kernel, 64 bit.

---

### Post by nol_faich on 2010-01-04
Great, change the line #111 of load3b to:

patch -p0 < ../patch_mi20.diff

./load3b -i

This version requires still some tests. I have the webcam and the driver performs better but I'm not satisfied with some things compared to the Windows driver.

---

### Post by soro2005 on 2010-01-05
Excellent, thanks. Works nicely so far. I'll keep observing and report back if there's anything.

---

### Post by Jack Malmostoso on 2010-01-16
I have tested the latest 2.6.33-rc4 and the driver included in this version is 100% working, with the image in the correct position.
I had to upgrade because of horrible flickering problems with my Intel video chipset, if you have similar problems you might want to give it a shot as well.

---

### Post by nol_faich on 2010-01-17
Hi Jack,
theoretically, you should start the webcam quicker than with older versions. Is that right?

---

### Post by Jack Malmostoso on 2010-01-18
I've never timed it to be honest so it's hard to say.
It's definitely alright, no noticeable delay really.

---

### Post by riddix on 2010-03-05
Hey guys,

i've updated the kernel of my ubuntu 9.10 to 2.6.32 but the webcam still dont work,... what needs to be done to get it running?

thanks rid

---

### Post by BUGabundo on 2010-03-06
I havent had much luck contacting Nol, so I hope someone in this thread can help me:
I want to make my webcam run in flash (tried both 32 and 64bits) with any of my browsers, in Lucid.

Any hints appreciated.
Thanks in advance.

---

### Post by nol_faich on 2010-03-09
@BUGabundo : Hi! Have you tried with LD_PRELOAD, it seems to me it is mandatory in 64bits.

@riddix : Hi! Have you tried the webcam with Cheese ?
Also please show the result of  "grep gl860 /var/log/syslog".

---

### Post by BUGabundo on 2010-03-10
> **nol_faich said:**
> @BUGabundo : Hi! Have you tried with LD_PRELOAD, it seems to me it is mandatory in 64bits.

i tried preload without luck, so i went to try flashcam

but since flashcam vloop is to old for my kernel, i had to fetch both flashcam and vloop from trunk and compile.

I did manage to get it work once for a few seconds, but all other attempts lead to black, green, or no cam identification!

if you have any tips, or need any logs, please let me know. thanks in advance

---

### Post by nol_faich on 2010-03-10
Stupid question: do you start your browser with LD_PRELOAD?

---

### Post by BUGabundo on 2010-03-10
> **nol_faich said:**
> Stupid question: do you start your browser with LD_PRELOAD?

you are so nice to me :D

 LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so firefox-3.7
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by hormone on 2010-03-10
Hi All,

I've been using Nol's drivers for this device for some time now without issue (thank-you for your work Nol, I'm looking forward to not having to re-compile at every kernel upgrade from Lucid onwards). Since upgrading to Karmic I've been compiling the driver with ./inst_gl860 -m and had success with both Cheese and Skype (except for the flip function)

Since upgrading to kernel 2.6.31-20 I've had problems. The camera works in Cheese, but in Skype, when I use the test function, the blue LED turns on but I get no video.

Here is the output of:'grep gl860 /var/log/syslog'

> Mar 11 09:27:15 andy-laptop kernel: [   10.191112] gspca_gl860: driver startup - version 0.9d10
Mar 11 09:27:15 andy-laptop kernel: [   10.300084] gspca_gl860: probing for sensor MI2020 or OVXXXX
Mar 11 09:27:15 andy-laptop kernel: [   10.333517] gspca_gl860: probe=0x00
Mar 11 09:27:15 andy-laptop kernel: [   10.365519] gspca_gl860: probe=0x00
Mar 11 09:27:15 andy-laptop kernel: [   10.446026] gspca_gl860: probe=0x00
Mar 11 09:27:15 andy-laptop kernel: [   10.477400] gspca_gl860: probe=0x00
Mar 11 09:27:15 andy-laptop kernel: [   10.477403] gspca_gl860: Not any 0xff -> MI2020
Mar 11 09:27:15 andy-laptop kernel: [   10.477405] gspca_gl860: 05e3:0503 sensor MI2020 (2.0M)
Mar 11 09:27:17 andy-laptop kernel: [   13.548115] gspca_gl860: Camera is now controlling video device /dev/video0
Mar 11 09:27:17 andy-laptop kernel: [   13.548154] usbcore: registered new interface driver gspca_gl860
Mar 11 09:27:17 andy-laptop kernel: [   13.548158] gspca_gl860: driver registered


When I do 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' I get (looping):

> X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 

I re-installed the Skype .deb but there is no change. I'm quite new to Linux so I'm not sure what else to do. HELP!!

---

### Post by usebau on 2010-03-11
Hey,

i installed the driver and it worked with cheese. Skype give me a green screen. The LD:PRELOAD get ignored by my system.
64 bit ubuntu actual version and kernel.
```

LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/local/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

greetz 
usebau

---

### Post by nol_faich on 2010-03-11
@Hormone: the solution is   export XLIB_SKIP_ARGB_VISUALS=1

echo -e '#!/bin/bash\nexport XLIB_SKIP_ARGB_VISUALS=1\nenv LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' > ~/skype.sh
chmod u+x ~/skype.sh

Start Skype with   ~/skype.sh

@BUGabundo: since I said to a hotliner I could not remove my laptop battery and noted eventually I forgot to unlock it, I think stupid questions need to be asked :)
Another stupid question : does /usr/lib32/libv4l/v4l1compat.so exist ?

@Usebau: Does /usr/local/lib/libv4l/v4l1compat.so exist ?

---

### Post by hormone on 2010-03-11
@Nol:

Awesome, thank-you.:KS

---

### Post by usebau on 2010-03-12
> **nol_faich said:**
> Does /usr/local/lib/libv4l/v4l1compat.so exist ?

Doesn't exists, same with /usr/lib/libv4l/v4l1compat. But libv4l-0 is installed. What i have to do and how?

usebau

---

### Post by soro2005 on 2010-03-12
> **usebau said:**
> Doesn't exists, same with /usr/lib/libv4l/v4l1compat. But libv4l-0 is installed. What i have to do and how?

usebau

On a 64 bit system, you have to preload /usr/lib32/libv4l/v4l1compat.so

Mind the lib32. Skype is a 32 bit application, so it needs the 32 bit library.

You may have to install lib32v4l-0 first:
```
sudo apt-get install lib32v4l-0
```

---

### Post by usebau on 2010-03-12
@soro thank you. skype with video worked.

usebau

---

### Post by usebau on 2010-03-23
The gl860_install doesnt work anymore, because the sources are on the webserver are deleted.

> Search for GSPCA last version hash
--2010-03-23 10:24:28--  [http://linuxtv.org/hg/~jfrancois/gspca/shortlog/tip](http://linuxtv.org/hg/~jfrancois/gspca/shortlog/tip)
Resolving linuxtv.org... 130.149.80.248
Connecting to linuxtv.org|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-23 10:24:28 ERROR 404: Not Found.

./inst_gl860: line 73: No access to  [http://linuxtv.org/hg/~jfrancois/gspca/shortlog/tip:](http://linuxtv.org/hg/~jfrancois/gspca/shortlog/tip:) No such file or directory
**********************************************************
.tar.gz does not exist, I'm trying to download it (5MB)

--2010-03-23 10:24:28--  [http://linuxtv.org/hg/~jfrancois/gspca/archive/.tar.gz](http://linuxtv.org/hg/~jfrancois/gspca/archive/.tar.gz)
Resolving linuxtv.org... 130.149.80.248
Connecting to linuxtv.org|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-23 10:24:29 ERROR 404: Not Found.

Fail to download gspca sources


Can you plz reup them?

---

### Post by nol_faich on 2010-03-24
There have been some changes about gspca repository, in the attachment is the suitable install script ("./inst_gl660 -t"  to test   and "./inst_gl860 -i"  to install).

---

### Post by soro2005 on 2010-03-31
Should the last script work on 64bit systems as well? Throwing some error here, something about i2c_core not found, then
```
insmod: can't read 'v4l/v4l1-compat.ko': No such file or directory
```

---

### Post by nol_faich on 2010-03-31
Hi Soro!

How did it behave with the previous script ? (same error but driver compiled?)

---

### Post by soro2005 on 2010-03-31
> **nol_faich said:**
> Hi Soro!

How did it behave with the previous script ? (same error but driver compiled?)

With the previous script, the error about i2c_core not found is the same, but v4l/v4l1-compat.ko is inserted correctly, and from there it goes without further errors.

---

### Post by nol_faich on 2010-04-07
Well, I'm still in 32bits but I will look at that this week end.

---

### Post by nol_faich on 2010-04-11
Soro, what happens if you comment in the lines #127 and 128:
```
#echo sudo insmod v4l/v4l1-compat.ko
#sudo insmod v4l/v4l1-compat.ko &&
```

---

