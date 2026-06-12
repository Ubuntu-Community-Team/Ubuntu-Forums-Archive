---
title: "Ubuntu on HP Pavilion tx 2000 tablet"
date: 2011-08-09
forum: Hardware
---

### Post by Shadi Ramadan on 2011-08-09
Hello!  I recently installed Ubuntu 11.04 on my HP Pavilion tx 2000 tablet.  I was wondering what I have to do to get the same functionality I had with windows vista - i.e. using the pen as a mouse (<- that works actually), being able to write out hand written stuff... and converting it to text...  Also the tablet's screen rotates around and closes so the screen is facing up - on windows the screen image itself is flipped vertically when doing this. On ubuntu it does nothing and you must rotate the tablet.  Also something is wrong with the wireless drivers or something because it detects no networks - and when checking for drivers nothing shows up... (I am currently sharing a wired internet connection with the laptop I'm on now)  I am doing an update... so I will have to see what happens.

If anyone has any helpful input. Please share. :D

Thank you!

Also if you need more info just ask...

-Shadi

---

### Post by Shadi Ramadan on 2011-08-09
Update: Wirless works - The drivers appeared after updating. :)

---

### Post by Favux on 2011-08-09
Hi Shadi,

For rotation you can use one of the rotation methods on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") although I personally use Magic Rotation on my TX2000.  However the wacom X driver (xf86-input-wacom-0.10.11; package xserver-xorg-input-wacom) in Natty has a bug where cw and ccw are reversed so portrait modes don't work correctly.  It has been fixed upstream so you need a newer version.  There is FAQ on the [Magic Rotation]("https://launchpad.net/magick-rotation") site for that or you can use part II. b) on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

You should look at CellWriter and Xournal.  Other than CellWriter there are a few work arounds to convert handwriting to text, but nothing official yet.  Although that's being worked on.

---

### Post by Shadi Ramadan on 2011-08-10
Hello!  I went up and decided to use Magic Rotation -- I went and followed the instructions on [how to fix the cw and ccw]("https://answers.launchpad.net/magick-rotation/+faq/1603") problem and ran into this error:

When pasting and running this line in the terminal:

samy@Samy:~/Desktop/xf86-input-wacom$ ./autogen.sh --prefix=/usr
./autogen.sh: 9: autoreconf: not found

I'm not sure what to do... I tried sudo apt-get install autoreconf but nothing was found.

I'm a very novice programmer and pretty much a noob to Ubuntu, but I would really like to be more involved.  Bear with me :D 

BTW CellWriter looks promising.

Thanks!

Shadi

PS: Anyone need any testers?
PPS: This laptop gets HOT fast.  You think something is blocking the vents? Or does it just get hot..?

---

### Post by Favux on 2011-08-10
Looks like you didn't get autoconf.  The apt-get line is line wrapped into two on the FAQ but it is all one line, get the whole thing:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

sudo apt-get upgrade

```
And it looks like I need to add the new libxinerama-dev to the FAQ.

Definitely blow out the fan with canned air or what not as it does get dirty.  There are a couple of kernel lines we can try also that may help.

---

### Post by ch604 on 2011-09-29
Hello!

Thanks for all the info, I was so glad that most of the tx2000's functions work right out of the box on 11.04! Very useful tips on getting screen rotation to work.

Eee! I'm so excited I don't have to put up with laggy vista anymore!

---

### Post by diasf on 2011-09-29
magick rotation works wonders indeed. (Even better since it automatically calls cellwriter).

Further, a well trained cell writer recognizes my writing better than the windows one. Not for full words tho, only letter by letter, that can be boring. But when i need to write more than a few chars i use either Xournal or the keyboard, so in the end, all good.

Your tablet isn't the amd version right? 
(if it is, and it's cooking, check cpufreqd... I can't boot mine without it, gets up to 105 celsius on boot)

---

### Post by ch604 on 2011-09-30
Excellent tip with cpufreqd. For cellwriter, are you having trouble with only one stroke being entered per character? I can't train for most letters (H, Q, f, etc) because they require me to lift the pen, resetting the input box.

---

### Post by diasf on 2011-09-30
Never noticed that on cellwriter. I just write the stuff on the box and it works, I ignored all details :)

And about cpufreqd, you can do a lot with it. You can consider battery status, running programs, cpu load and not only change the stepping but also run your own scripts when it changes states. It is really powerful.

---

### Post by cep1980 on 2011-10-14
Amazed to find other owners of this laptop!  11.04 everything worked great. Decided to upgrade from 11.04 to 11.10.  Only glitch I've come across hardware wise besides loss of display button functionality is that the sound now only has one output option.  Headphones work but sound still outputs via speakers along with the headphones.  In 11.04 there was an option to switch to analog out which in now missing.  Any simple trick to get that option back?

---

