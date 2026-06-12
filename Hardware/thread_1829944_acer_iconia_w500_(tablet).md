---
title: "acer iconia w500 (tablet)"
date: 2011-08-21
forum: Hardware
---

### Post by cylent on 2011-08-21
greetings all.

i tried to install Ubuntu 11.04 on my [iconia tab w500 tablet]("http://acer.us/ac/en/US/content/iconia-tab-w500") ...
now this is a tablet that's keyboard-less. i know there's a version that comes with a keyboard but that defeats the purpose... i might as well get a laptop if i am gonna get one with a keyboard.
i really wanted to the full fledged experience of a simple easy to carry tablet that runs any OS i want...

so i took the plunge and installed 11.04 via usb/cdrom and all went fine. the hardware is all fully detected and works (except for some things which I'll mention later). 

i realize ubuntu 11.04 may not be optimized in any way for a keyboard-less tablet. i can move the mouse around just fine although not accurately with the touch screen...

my current issues are:

there really isn't a system wide onscreen keyboard that even works. sure there are a few to download however each has their own rules and most of them have very small keys to even tap. this is really problem #1 for me. 
on the logon screen you can click on the assistance icon and get a keyboard to enter your password -- its a crappy keyboard with very tiny keys however its there.
in the system though once you're logged in there isn't any!
if you wait for the screen saver to come on and then try to activate your system you're outta luck! there is absolutely no way to get any sort of on screen keyboard via the screen saver lock screen.

then comes the even somewhat serious issue of kinetic scrolling. it doesn't exist in any app. the new style of the scrolls-bars is really great for keyboard and mouse however isn't working so well here! i find myself missing the scroll bar and resizing all the time. its basically a pain in the *** to scroll though any program.

then comes the issue of the screen rotation. 
as you guys know this is a tablet and its supposed to be used in landscape and portrait mode without any drama. of course this is missing because of the accelerometer not being used for this purpose? perhaps its another sensor for the rotation.

so ... if anyone can help with at least the first issue I'd be a very happy Ubuntu tablet user. in the meantime i am gonna to go research kde to see if it has a onscreen keyboard...

---

### Post by rampage_1973 on 2011-08-22
ok here goes, i use an app called onboard it is a resizable keyboard so you can get keys to a decent size. it is in the repos so sudo apt-get install onboard will get it for you, or you can use the ubuntu software manager also.

on the screensaver i disabled the password lock so it would not be required.

i also setup autologin on boot so i do not need a keyboard (although this compromises security)

i have not figured out anything better yet for scrolling, or auto rotate , i can manually rotate using xrandr -o left and back using xrandr -o normal but input is messed up then.

hope this helps you out! i typed this using onboard on my iconia w500

---

### Post by cylent on 2011-08-22
> **rampage_1973 said:**
> ok here goes, i use an app called onboard it is a resizable keyboard so you can get keys to a decent size. it is in the repos so sudo apt-get install onboard will get it for you, or you can use the ubuntu software manager also.

on the screensaver i disabled the password lock so it would not be required.

i also setup autologin on boot so i do not need a keyboard (although this compromises security)

i have not figured out anything better yet for scrolling, or auto rotate , i can manually rotate using xrandr -o left and back using xrandr -o normal but input is messed up then.

hope this helps you out! i typed this using onboard on my iconia w500

thank you very much. 
yes i did find onboard however i was looking for something a bit better.
in fact i loaded up kubuntu and i find it more tablet friendly and it has transparent windows that look cool. unity sounds good on paper but i find it too :redface: ...
i'll take your advise on the xrandr command. hopefully it'll work.

by the way how do u find the tablet performance? a bit sluggish or speedy?

---

### Post by rampage_1973 on 2011-08-23
tablet performance hmmmm, :) actually I am using gnome or regular ubuntu I did not like unity reminded me of everything i hate about macs!

admittedly i have not tried kubuntu in a while maybe i will download the kde packages and just see how it is.

on the performance question it seems "normal" for what it is certain things seem sluggish at times but on average it is a decent tablet/pc.

since I have the docking keyboard I really use it every day as both a laptop and a tablet, it is by no means a powerhouse though.

all in all it seems to run better with ubuntu on it than it did with windows 7 (except for the auto rotation anyway) I am sure in a couple of versions that will be working in ubuntu as well.

also in case you have not found it yet if you want to play with the webcam(s) cheese is a decent program allows taking pictures etc.

ok I am done rambling now!

---

### Post by crock_11 on 2011-09-16
Hi all,
I am looking for an answer to the same issue: I can rotate the display but I can't figure out how to rotate the touch input.

I found the performance in ubuntu about the same as windows but I really want to use ubuntu as my daily driver since it is much more friendly to the limited ram and ssd space.

I'm happy with the 'onboard' keyboard but I had to do a few workaround like rampage mentioned to get around the shortcomings -- like the lock screen.

Currently I'm dual booting Ubuntu off of a 32gb SD card and if I can find a fix to the input rotation I plan to install it on the ssd.  Will let you know if I find something.

================================
Acer W500 with fast ssd:
[64GB MyDigitalSSD mSATA SSD]("http://www.mydigitaldiscount.com/mydigitalssd-64gb-50mm-bullet-proof-msata-ssd")

---

### Post by crock_11 on 2011-09-17
Hey guys I found a solution.  Go to this post and follow the link to download the program Magick Rotation: [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)

I installed it and now when I rotate the display the touch input rotates accordingly, sweet! ):P

================================
Acer W500 with fast ssd:
[64GB MyDigitalSSD mSATA SSD]("http://www.mydigitaldiscount.com/mydigitalssd-64gb-50mm-bullet-proof-msata-ssd")

---

### Post by Omegus on 2013-03-10
Sorry to necrobump this topic but I wonder if anyone gotten the Ubuntu touch system working on the W500 yet.

---

