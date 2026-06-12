---
title: "Logitech G13 Advanced Gamepad"
date: 2009-08-29
forum: Hardware
---

### Post by mad_max0204 on 2009-08-29
I have 9.04 64bit running and I'm trying to get this awesome gadget to work.
There is only one guide I found for g13 under linux and it doesnt do it for me. I plug it in and screen lits with nothing written on it. I managed to get G13 written on the screen when I plugged it in but thats it. No keys work, you cant change backlit color and I dont know how to get it to work.
The site that has something written about it is [http://forums.logitech.com/logitech/board/message?board.id=gserieskeyboards&thread.id=592]("THIS ONE") and there is a link to driver and no good explanation.

Any help is appreciated.

Thanks

---

### Post by mad_max0204 on 2009-08-30
bump

---

### Post by mad_max0204 on 2009-08-31
bumpy bump

---

### Post by Larissa on 2009-09-22
Hey mad,

This may help you:
[http://www.nexoid.at/g13/](http://www.nexoid.at/g13/)

Life's Good

---

### Post by mad_max0204 on 2009-09-24
Ya man I tried that.
I'm affraid that doesnt work either.
Maybe has something to do with 64bit system.
I even sent mail to the guy who wrote those drivers.
No answer still.

---

### Post by GalloGlas on 2009-11-27
That driver simply does not work.  It has anything to do with 64 bit OS.   

I called Logitech and they said that they will never support Linux because of licensing agreements... whatever that means.   ;)


Edit: they also said that using that unsupported driver could void my warranty.  Like they'd be able to tell.  If it were REALLY the case, makes me wonder why they don't take that thread on their BB.

---

### Post by ntc490 on 2009-12-09
I worked with Peter a while back on his driver (the site referenced above).  We worked out a couple of kinks and got the driver working with a terminal or X windows.  The problems don't have anything to do with 64 bit kernels.

I am a software engineer with a lot of Linux Kernel experience, but I decided to write a solution in userspace in hopes it would be more portable and easier to install and configure.  It was definitely a little easier to develop, although it was actually pretty easy since I leveraged much of the work Peter had done so far as USB code goes.

I wrote some "C", Cython, and Python code that leverages libusb-1.0 and libxtest.  Think I got some of those ideas from Peter, too, if I remember.  The whole solution works from usermode and allows you to write text or graphics to the LCD, read all the buttons, set LED colors, etc.  The code interprets the joystick also, but I don't currently do anything with it.

You can configure "macros" that include any keyboard event - including alt and ctrl key combos - using an ini style file.  You can make keys repeat or not, set the macro replay rate, and a few things like that.  It's really handy for emacs and repetitive shell commands and such.  I have even created large macros that edit multiple system config files with vi.

Am planning to post the code as open source.  Need to find a low-maintenance home for it.

---

### Post by Larissa on 2009-12-11
Hey ntc490,

Define "low-maintenance home" :)

Lari

---

### Post by ntc490 on 2009-12-13
Low-maintenance means one I don't have to pay for or worry about.  I sent a snapshot to the owner of [http://www.nexoid.at/g13/](http://www.nexoid.at/g13/) and he has offered to post it along with his work.  

Have considered freshmeat.net or something.  Actually just checked and there is a project on sourceforge called g13.  Don't see any files though.

---

### Post by mad_max0204 on 2009-12-16
This is some great news there ntc490.
I would like to see that project come to life.
If there are any news please post here and let us know.

Thanks

Max

---

### Post by Larissa on 2009-12-24
Any news yet, ntc490?

---

### Post by ntc490 on 2009-12-30
Haven't heard back.  Peter does seem pretty busy.  Anyone want to try it out?  I can probably email a tarball or something.

---

### Post by wilber85 on 2010-01-27
Peter said he was no longer answering emails regarding the driver.  Hopefully someone else will pick up the project and be more successful.  

I would like to see what you have ntc.  Sent you a PM.

---

### Post by Rayve on 2010-01-28
Anything new on this one?  Can you maybe put it up on sourceforge?

---

### Post by Rayve on 2010-04-16
Wanted to bump this in case anyone else was still looking - I managed to get the int vs. size_t errors to go away so it now makes properly.  Anyone have any other ideas?

[http://forums.logitech.com/t5/G-Series-Keyboards/Does-the-G13-work-with-Linux/m-p/442700#M11409](http://forums.logitech.com/t5/G-Series-Keyboards/Does-the-G13-work-with-Linux/m-p/442700#M11409)

---

### Post by Miscni on 2010-04-27
Hi Rayve

I was looking over some of that info you have posted, here and on Logitech's Site.

But I also came across this site here : [http://wiki.jarfil.net/Logitech_G13 ]("http://wiki.jarfil.net/Logitech_G13")

I know it is not much, but I may have a Idea, if somebody could be so kind to answer me some questions about the code.

I cannot garante anything, but I would like to try.

My code problem is:
If I add this here to the Terminal
```

lsusb

```

and then I get the this code 
```

Bus 007 Device 002: ID 046d:c21c Logitech, Inc. G13 Advanced Gameboard

```

and if you compare my code, with the code, from the link, I have add, then the next code, would not work. But I am trying to see, what I can make out of it, but I am still pretty new to Ubuntu, But I will try my best, because I need to get my G13 to work

---

### Post by Miscni on 2010-04-27
But then I tried this code here in the terminal.

```
dmesg | grep C21C
```

I get this answer out from the terminal
```
[    1.694089] generic-usb 0003:046D:C21C.0001: hiddev96,hidraw0: USB HID v1.11 Device [G13] on usb-0000:00:1d.1-1/input0

```

after that I used this code.
```
sudo xxd -ps -c 9 /dev/hidraw0

```

But after this code is being add, then the terminal just stands there.
The Terminal is busy with something, and I cant see what. But I'll keep you updated.

Cheers

---

### Post by Miscni on 2010-04-28
I figured out, why the terminal was doing nothing, it was waiting for the raw codes, to be shown. That means, I had to push everybutton, so it could see the commands, but after pushing all the buttons etc. I still had problems with the terminal, it didn't stop recording.

But as shown at the link early'r on my thread, I was actually possibul for me, to see all the the raw codes. 

But I can't figure out, how to get that "hidraw0" - file or how to open it.

---

### Post by darkenvy6 on 2010-07-05
resurrect bump.... further development?

---

### Post by Luomu on 2010-08-19
> **darkenvy6 said:**
> resurrect bump.... further development?There is a new userspace driver (aka not kernel module) that worked for me out of the box: [http://www.nexoid.at/g13/](http://www.nexoid.at/g13/)

It is only a few days old so not perfect, but keys work and they can be rebound :)

---

### Post by efflandt on 2010-09-22
[http://www.nexoid.at/g13/](http://www.nexoid.at/g13/) works for me in 64-bit Lucid for a little while, then exits with:

Error while reading keys: -9
Stopping daemon

For libusb1 I used Synaptic to install **libusb-1.0.0-dev**.  For boost I installed **libboost1.40-dev** (or should it be libboost1.40-all-dev?).

Apparently there is no "g++" by default so I did **cd /usr/bin** then **sudo ln -s g++-4.4 g++** to symlink it to the simple name.  Then **sudo make all** worked in g13-userspace directory (which I had put in /usr/src).  Then I was able to **sudo ./g13** and it changed the G13 LCD to blue with a "linux inside" logo and some sort of unidentified critter (ram or bear?).  I was able to change LCD color to red, and assign a key which worked in a terminal, before the daemon stopped.

Instructions say "If you run udev, copy the file 91-g13.rules to /etc/udev/rules.d/ to make sure you have write access as the user that runs g13.", but there is no clue what that rules file should contain (not included with sources) to run g13 as a normal user.

So I don't know if it is eventually dying due to a permissions issue somewhere or something else.

---

### Post by Miscni on 2010-10-04
Well I tryed what you suggested. on Ubuntu 10.04.

I used Synaptic and install : **libusb-1.0.0-dev , ****libboost1.40-dev and **[B]g++

[/B]After that I went to the terminal, and tryed to get Permissions to work.
When that was done, I tryed to **sudo ./g13 , **and the display turn blue for me as well, and with the "Linux Inside" logo.

but I got 1 error, from the terminal: ```
Could not find an uinput device
```

But I have no problem, to change the color in the display, but I cant figure out, how to add the keys, and besides that, I cant find that file, that the Instructions writes about: "91-g13.rules"

I am not very good a Ubuntu. But I try my best, to learn as much as I can.

---

### Post by fatbotgw on 2010-10-29
> **Miscni said:**
> Well I tryed what you suggested. on Ubuntu 10.04.

I used Synaptic and install : **libusb-1.0.0-dev , ****libboost1.40-dev and **[B]g++

[/B]After that I went to the terminal, and tryed to get Permissions to work.
When that was done, I tryed to **sudo ./g13 , **and the display turn blue for me as well, and with the "Linux Inside" logo.

but I got 1 error, from the terminal: ```
Could not find an uinput device
```

But I have no problem, to change the color in the display, but I cant figure out, how to add the keys, and besides that, I cant find that file, that the Instructions writes about: "91-g13.rules"

I am not very good a Ubuntu. But I try my best, to learn as much as I can.


I got the same error...you need to install "mouseemu" for the /dev/uinput to show up.  After that I had to "chmod 777 /dev/uinput" to fix the permissions.

---

### Post by shakka_z on 2010-12-11
My Logitech G13 works well with Ubuntu 10.04 LTS and I play World of Warcraft via wine 1.3.8.

This blog has a guide to install and compile the source code:
   [http://crap.linuxfusion.net/?p=185](http://crap.linuxfusion.net/?p=185)

The G13 lights are green and the LCD shows the "Linux Inside" and GNU logo. Alls keys work with WOW and can be defined via the game.

But..., the thumb-stick moves the pointer on my desktop like my mouse but is not recognised by the game. I guess it might work if we remap the the stick with WASD keys or the arrow keys.

---

### Post by ohav on 2011-01-17
> **shakka_z said:**
> 

But..., the thumb-stick moves the pointer on my desktop like my mouse but is not recognised by the game. I guess it might work if we remap the the stick with WASD keys or the arrow keys.

I would also like to know, how to bind the stick to the awsd or arrow keys?

---

### Post by ohav on 2011-01-19
> **ohav said:**
> I would also like to know, how to bind the stick to the awsd or arrow keys?


solved it by using qjoypad

---

### Post by Hamms on 2011-01-28
I know I'm resurrecting a long-dead thread, but I have a question to add. I'd really love two extra features:

1) The ability to bind lua (or bash) scripts to keypresses. I'm using the guide at [http://crap.linuxfusion.net/?p=185](http://crap.linuxfusion.net/?p=185) and it works great, but it only provides for a mapping of gamepad keys to keyboard keys, and I'd really like to do more.

2) "Sticky" keys. I want to press a button on my keypad and have it hold down "w", then release when I press it again. I might be able to accomplish this if I get (1) working, but it is something of an independent desire.

Anyone have any ideas?

---

### Post by supernoob123 on 2011-03-04
ok i am a complete noob.  i dont know how any of these commands work or what they mean because i was a point and click windows user.

  i tried "http://crap.linuxfusion.net/?p=185"  and typed in those commands after i downloaded that program and i figured out how to enter cd g13 so "tar xvfj g13.tar.bz2" command worked but then when i typed (not copy/paste) "sed -i &#8220;s/BTN_THUMB2/BTN_EXTRA/g&#8221; g13.c " in the terminal and pressed enter and it didnt do anything.

so then i typed "make" and a whole bunch of jibberish popped up with a whole bunch of errors and thought maybe its suppose to say that stuff.
i then unplugged the g13 and typed "insmod g13.ko" into the terminal and it said
"insmod g13.ko not found"
so now i am really confused and though ok... its suppose to say that? 
and typed 
"rmmod usbhid; modprobe usbhid quirks=0x046d:0xc21c:0×4"
and it said "Removing 'usbhid': Operation not permitted"
so then i plugged in the g13 and nothing happend...
oh gawd im so confused because i literally never used linux before today.
i usually catch on these things quick but ubuntu which i just put on here today is like so confusing! O_O_O_O i feel like going back to windows xp >_< but i dont want to because i just need to learn this new OS i guess.
so anyone please help meeee!!! also i forgot to mention that i am running ubuntu 64bit is that why it wont work?
i really dont want to sell my g13 but i dont want to go back to windows ever! :D ubuntu is just so nice

---

### Post by supernoob123 on 2011-03-04
u know what... im not getting rid of my beloved g13.  i gave up on ubuntu. its great for what it is but ubuntu will always be a 'tool' in my book...to recover data or to clean a virus laden pc.  ubuntu pretty as it is, just lacks usability, therefore i trashed ubuntu for win 7.   sigh.....   linux has so much potential its a pitty it will never prosper bcuz of licensing issues

---

### Post by emorphous on 2011-03-07
I tried following the instructions at [http://crap.linuxfusion.net/?p=185]("http://crap.linuxfusion.net/?p=185") but had the similar problems as Supernoob (there's no g13.ko and "make" didn't create one).  So I abandoned that line of thinking and went to the original.

Following the loose instructions from [http://www.nexoid.at/g13/]("http://www.nexoid.at/g13/") and the trials and tribulations of posters here, I was able to get as fas as having a G13 show me Green text with "Linux Inside".  However, I was unable to figure out how to change settings, including changing the color to red (as others seem to be able to do).

My keys don't appear to do anything, but I know its semi-working because my thumb stick moves my mouse.  However, it moves it sporadically and after I use it for a second, Ubuntu logs out.  So I'm guessing its keybound to something unpleasurable (or Ubuntu reeeeally didn't like what those keys were doing).

This is exactly what I did:

[LIST]
[*]Installed libusb1 and boost using Synaptic.
[*]Installed mouseemu for uinput.
[*]Ran chmod 777 for /dev/uinput and the usb location for my G13.
[*]Uncompressed the tarball from [www.nexoid.at/g13]("http://www.nexoid.at/g13/").
[*]ran make in the new directory.
[*]Copied 91-g13.rules to /etc/udev/rules.d/ and ran chmod 777 on it.
[*]ran ./g13
[/LIST]

That's where my G13 display turned green with the "linux inside" + ram logo.  I'm apparently too dumb to figure out how to send commands to the daemon though.

I then installed QJoyPad 4.1 to fix my keys.  But I can't figure out how to configure my G13 in there.  I'm thinking QJoyPad isn't finding my G13 without a little help.  I'm not sure how to give it that help.

Anyone get farther than me, and can share some pointers?  I'm relatively new to Linux and I'm running Ubuntu 10.10.

> u know what... im not getting rid of my beloved g13. i gave up on ubuntu. its great for what it is but ubuntu will always be a 'tool' in my book...to recover data or to clean a virus laden pc. ubuntu pretty as it is, just lacks usability, therefore i trashed ubuntu for win 7. sigh..... linux has so much potential its a pitty it will never prosper bcuz of licensing issues
Yes, Linux has its drawbacks when it comes to software and hardware compatibility.  But the more experience you get with Linux, the easier you find it to work around those problems.  I'm literally down to just this problem after about a week of trying.  One special piece of hardware that just doesn't want to install properly.  I think its a fair trade off for all the benefits of Linux!

Now the only problem is I'm addicted to my video games and I use my G13 for those ;)  so without a working G13 I do have to reboot into Windows for a majority of my time.  But anytime I'm not playing games, I am happy to be in Linux.

---

### Post by Kyterra on 2011-03-16
I am also working on this project...

In  the terminal screen, I run ./g13 (running w/ or w/o sudo seems to make  no difference, /dev/uinput is set to 777) and it detects the G13.  It  reports
```
Kernel driver detached
Found 1 G13s
```I  managed to get evtest to work (once I noticed which event was generated  when running ./g13).  The initial output is as follows:
```
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x46d product 0xc21c version 0x1
Input device name: "G13"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 1 (Esc)
    Event code 2 (1)
    Event code 3 (2)
    // all 200+ codes
    Event code 289 (ThumbBtn)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value 128
      Min     0
      Max   255
    Event code 1 (Y)
      Value 129
      Min     0
      Max   255
Testing ... (interrupt to exit)
```The  only input registered from the G13 during the evtest is the  thumbstick.  It reports the timestamp, type 3 (Absolute), and then code 0  or 1 with X, Y values.




I have found that while the daemon is running, when I type
```
echo "rgb 100 0 0" > /tmp/g13-0
```The line is inserted into the /tmp/g13-0 file.


The display remains green with the "linux inside" logo, g13 letters, and the image.

The  terminal running the ./g13 will print a number when a key on the g13 is  depressed (G1 prints a 0, G2 prints a 1, etc up to G8 which prints a  7).  Keys G9 through G22 and the two thumb buttons produce nothing in  the terminal window.


Feels like I'm getting closer.

---

### Post by emorphous on 2011-03-17
Cool Kyterra!  That seems exactly like what I've gotten, except I didn't get into testing it as well as you did.

I'm sad to say I'm probably not going to be able to get the next step though.  I'm just not smart enough for that haha.  I blame long time Windows use.

---

### Post by Kyterra on 2011-03-17
I've managed to get the original author, ecraven, to look into this issue on 10.10.  You can follow the thread on the Logitech forums here: [http://forums.logitech.com/t5/G-Series-Gaming-Keyboards/Does-the-G13-work-with-Linux/td-p/286903](http://forums.logitech.com/t5/G-Series-Gaming-Keyboards/Does-the-G13-work-with-Linux/td-p/286903)

---

### Post by Miscni on 2011-04-07
Kyterra, I was wondering if you have had some time, to look over the code, that ecraven has made, or maybe somebody else on this thread has.

Cheers

---

### Post by Hamms on 2011-04-11
Has anyone working on this thought about getting the device recognized in wine, or even setting up some kind of virtual device that wine can recognize and to which we can feed the /dev/usb/hiddev data? That would enable us to use the (rather nice) set of tools that Logitech provided for this device.

---

### Post by cystacae on 2011-04-15
I am new to Linux as my main OS, and completely new to ubuntu.  I an running 11.4 Natty and so far I have managed to iron it out to the way I want it.  Only problem is this G13 issue and no one has fully developed a nice driver set/mod set for this except I did run across some person trying to get a g13 driver support within the kernel.  Looks like that idea is dead and he hasn't posted stuff recently at all.  His driver set definitely is much larger than the userspace and looks to have more involved with it.  If you'd like to look into it for those program savy people we may be able to tackle this problem.  The addy is [http://g13.sourceforge.net/](http://g13.sourceforge.net/) and it is dev'd or was dev'd by Rick L. Vineyard Jr.  Unfortunately, all his links are dead except the svn repositories.  I managed to download all of the packages and if anyone would like I could post these to a download/storage site for you to obtain.  It may be helpful to us as he did have it working in Fedora 12.

---

### Post by Miscni on 2011-04-15
Cystacae. I actaully found that for some time back, I am actaully a follower on that project, but we can both agree on, that nothing new has happend, on that front.

I did mail him, a while back, were i asked him, if it could work on Ubuntu. 

His answer was, that he wasn't sure about it, but I could try. But there was no garanties.

I did tryed at that time to see, if I could get it to work, but since that I am not good at Ubuntu, I gave it up. But I am up for, to give it a second try.

But still thx for giving it, a headsup.

Cheers

---

### Post by Glenadel on 2011-05-17
Here is a quick little fix until we get a good (and easy) driver. If you want to use the G13 on a linux computer and you have another Windows computer you can connect your G13, Keyboard and mouse to the Windows computer, then use the normal G13 software to set it up and then use synergy. It will register the keystrokes and the joystick flawlessly. its kind of a pain but hey it works. lol   \\:D/

ps. and you don't even need to worry about updating anything on your linux box because it doesn't actually have the driver on it lol   :D

pss. To bad the LCD wont work that way  :(

---

### Post by Miscni on 2011-06-07
For those who may be interested, please have a look on this How to.
I was really tired, when I got this to work, but this here works.

I hope it can help all you guys out.

[http://www.youtube.com/watch?v=Xk3TVAs80ZM](http://www.youtube.com/watch?v=Xk3TVAs80ZM)

Cheers

---

### Post by jwcalla on 2011-06-08
BTW there are some other packages out there for the G Series keyboards but there seems to be a mish-mash of partial functionality available so I don't know how suitable they are.  I've been trying to get some more love for my G110 so I don't know what G13 support is like with these other items... but you guys might want to try at least.

- There's a kernel module package called lg4l being developed (available on github).
- There is a configuration program called gnome15 (gnome15.org) that attempts to interface with a daemon or driver.
- There is the g15daemon project (g15tools.com) that I'm sure everyone knows about (the one in the repos is a bit stale).

The kernel driver allowed me to change my backlight (LED) colors, but I have no idea how to program my G keys.  The g15daemon allowed me to program my G keys, but there was an insane memory leak (could have just been my compile).

I guess you folks know about these other items but I didn't see them mentioned in the thread so I figured I'd bring it up.

(PS: Those comments by Logitech, if true, absolutely tick me off.)

---

### Post by Miscni on 2011-06-08
Hey jwcalla

If you are refering to the G15tools website. then I have tried them. Had alot of problems with those, both with the compiling and setup feature,even tryed there forum, but my post never came on, but I found alot of spampost on that site, that gets on site, all the time. But besides that.

I am willing to give it another shot. But also you are refering to other packages, which others, can you please provide some links etc.

And by the way, G110, and G13 are to different things. Sure they both use the deamon pack. And alot of the scancodes, has some likeness. But I am sure, that you already knew that :)

Just so everybody knows, the difference between those to product, here are some pictures, that I have provided.

G110 picture here: [http://www.pcgameshardware.com/screenshots/medium/2009/12/Logitech_G110_Gaming_Tastatur_Keyboard_04.JPG](http://www.pcgameshardware.com/screenshots/medium/2009/12/Logitech_G110_Gaming_Tastatur_Keyboard_04.JPG)

G13 Picture here: [http://www.logitech.com/assets/17680/17680.png](http://www.logitech.com/assets/17680/17680.png)

And if I can get it to work, then I am willing to make a walkthrough, that can be shown on youtube. Because as long it can help other Ubuntu users, then it is always a pleasure.


And about the comments from Logitech, then please have a look at this here.
[http://forums.logitech.com/t5/G-Series-Gaming-Keyboards/Does-the-G13-work-with-Linux/td-p/286903](http://forums.logitech.com/t5/G-Series-Gaming-Keyboards/Does-the-G13-work-with-Linux/td-p/286903)

The funny thing about that thread is, it started all the way back in 2008. And no Logitech Support was on that thread.

But the same day, after I add my link to the youtube walkthrough, it is like a magican was around the logitechforum, because then there was a Logitech Supporter, that was trying to be smart. And even though he tries his best, he made a very big bummer.

He is refering to, that Logitech only support PC and MAC, and that got me to wonder alot, because a PC computer, doesn't need to use Windows. (That is actaully his last post on side 5).

Me and another person in there, were trying to get this support to answer, a very simpel question, that we didn't get a answer on. And that was, why doesn't logitech support Linux. And off the record here, my teori it is because Logitech is not allowed to do that, but by how, I cant answer. But I am detirment to find some answers, because I dont think it is fair for Linux.

Cheers all

---

### Post by jwcalla on 2011-06-08
> **Miscni said:**
> Hey jwcalla

If you are refering to the G15tools website. then I have tried them. Had alot of problems with those, both with the compiling and setup feature,even tryed there forum, but my post never came on, but I found alot of spampost on that site, that gets on site, all the time. But besides that.

I am willing to give it another shot. But also you are refering to other packages, which others, can you please provide some links etc.


Yeah the G15Tools seem a bit dated or something... and navigating their website to figure out what is going on is pretty difficult.

Here is the GIT for the lg4l kernel module:  [https://github.com/martynsmith/lg4l](https://github.com/martynsmith/lg4l)

I don't know the status of that project or even how the module is intended to be used.

Here's the website of the gnome15 project:  [http://www.gnome15.org/](http://www.gnome15.org/)

There is a forum there if you'd like some more information about it.

---

### Post by jwcalla on 2011-06-08
I think we'd be better off gathering up all the G-peeps here at the Ubuntu forums (there are numerous threads) and then going over to the gnome15.org forum and say, "Hi... we're here.  How can we help?"  Even if we're just testing different configurations, it might be worthwhile.  If all the various G-efforts out there were consolidated into one project we'd be way ahead of Windows by now.

BTW there are some G-projects developed for Windows also, some involving lua scripts and the like.  Maybe we can even ask them for some help because I get the impression that they're pretty smart and understand some of the device specifics.  Here's a forum with smart people (some areas require registration):  [http://www.logitechusers.com/index.php](http://www.logitechusers.com/index.php)

---

### Post by Miscni on 2011-06-09
hey jwcalla 

thx alot for the links, I will see what I can do.

And that reminds me, if you or others need to get in contact with me, then dont be afraid to contact me, on my TS.

Cheers

---

### Post by Miscni on 2011-06-09
And now I am some progress to tell.

From lg4l, I downloaded it, and look over the codes, that seems promissing.
tryed to follow the walkthrough. And that was pretty easy to understand.
But I ran into some problems.

lg4l are giving me this error here:
```
mikker@Miscni:~/Hentede filer/mg13$ make
make -C /lib/modules/2.6.38-8-generic-pae/build M=/home/mikker/Hentede filer/mg13
make[1]: Går til katalog '/usr/src/linux-headers-2.6.38-8-generic-pae'
make[1]: *** Ingen regel til at skabe mål 'filer/mg13'. Stop.
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [default] Fejl 2
```

So I went to the website, and added a issue, that I hope, the will see, and maybe give a helping hand to explain, how to fix this.

Tryed out the lg4l from this site : [https://github.com/martynsmith/lg4l](https://github.com/martynsmith/lg4l)
And I have reportet a issue : [https://github.com/martynsmith/lg4l/issues](https://github.com/martynsmith/lg4l/issues)

When that was done, I went over to [http://www.gnome15.org](http://www.gnome15.org). 
And I had alook on the drivers section for G-Keyboard/G-Gamepads. And that was after my eyes, almost to good, to be true. But very promissing.
Link here : [http://www.gnome15.org/index.php?option=com_content&view=article&id=7&Itemid=31](http://www.gnome15.org/index.php?option=com_content&view=article&id=7&Itemid=31)

I Downloaded the packages from here: [http://www.gnome15.org/index.php?option=com_content&view=article&id=9&Itemid=2](http://www.gnome15.org/index.php?option=com_content&view=article&id=9&Itemid=2)

I follow the instructions on the website, and they are pretty forward, and easy to understand, when you are using the terminal, so for showing that. I get a Thumbs up from me.

After I installed it, I rebooted the computer, and the Gnome15 window showed up, but already there, I was getting problems.
I tryed to look over the forum, and to find a selution. And I found this here [http://www.gnome15.org/index.php?option=com_kunena&func=view&catid=2&id=33&Itemid=7](http://www.gnome15.org/index.php?option=com_kunena&func=view&catid=2&id=33&Itemid=7)

I do know, it was for G15, but the error also accuried for me in G13. So I have added in all the Errors that I could find, and then we just need to wait and see.

But I think we have 2 others on the block, that are makeing something really good, so I will keep my eye on them.

As far as it goes for g15tools.com, I dont know, if they are doing anything anymore, but I still see alot of spammers etc. But I have tryed to send the Webmaster a mail, and is hopeing for a reply, in the near future.

But if anyboy else, if getting some progress, then please let me know, would very much help out, if it is possibul.

Cheers

---

### Post by jwcalla on 2011-06-09
Miscni,

I have had some problems building the latest version of the lg4l package as well.  I think they made some kernel-specific changes that maybe aren't compatible with other kernel versions. (I'm still on 2.6.35 but I see you have 2.6.38 and I think they have code updates for that kernel so there might be other issues.)

One thing you might want to do is go to the fork graph here:  [https://github.com/ali1234/lg4l/network](https://github.com/ali1234/lg4l/network)

And then hover over the various versions to see if something seems more applicable.  Maybe you can download the April 14 version and see if you can get that running... and if so, keep trying the next version until you find one that doesn't work.

---

### Post by loshar on 2011-07-02
Hello all,

I wanted to get some experience using libusb and uinput to create my own small usb device using an arduino.  I had a G13 and also wanted to get that to work so I took the time to write a small application that emulates some of the functionality of the G13 drivers for windows.

You can find the source on github at: [https://github.com/ghedlund/ug13](https://github.com/ghedlund/ug13)
Link to the git repository: [EMAIL="git@github.com:ghedlund/ug13.git"]git://github.com/ghedlund/ug13.git[/EMAIL]

Below is part of the README file (please read the full README file - it contains all the information you need to get started.)

I've been using this to play WoW for a week and have had no issues.

Hope someone else will find this useful.

Cheers!

```

= ug13: Userspace G13 Tool =

Small application to emulate some of the functionality of the G13 drivers on 
windows.  Uses libusb-1.0 for communication with the G13 and uinput for key 
event injection.

== Features ==

 * Uses libusb-1.0 asynchronous communication to allow continuous LCD display
   updates while processing key events.  Current update freq is approx 25Hz.
 * Separate key mappings and led colors for M1, M2, M3 modes.  Mode led is
   updated to show current mode.
 * Can map key actions for both key press and release events on the following 
 keys: 
  - G1-G22
  - T1-T2
      Left-thumb and bottom-thumb
  - AS
      Analog stick press
  - AT, AR, AB, AL
    Fired when analog stick is at full: top, right, bottom, left respectivly
  - M1, M2, M3
      M1-M3 will switch mode.  Events can be setup as well but not very 
      useful.
  - No macro recording support (MR) yet
 * Key map is loaded from an xml configuration file.  See keyprofile.xsd for 
 information about the format and default_profile.xml for an example.
 * Simple plug-in system for controlling LCD display.  See plugins/countdown.cpp
 for an example plugin implementing a simple timer.

== Requirements ==

 * libusb-1.0
 * libxerces-c-dev
 * xsd-cxx (xml -> c++ data binding)
 * uinput kernel module (sudo modprobe uinput)

== Compiling ==

 * type 'make'
 
This should create the following files:

 * lib/libug13.so
 * ug13
 * plugins/<plugin>.so
 
== Running ==

 * type 'LD_LIBRARY_PATH="lib" ./ug13 <xml file>'

```

---

### Post by Doc_Smimble on 2011-07-10
Hi Ioshar

First of all, **A BIG THANKS** for this program. 
Keys, Leds, Analog stick works perfect but i  had a problem with the lcd display.
It shows me only the rgb color,  nothing more (no text or symbols).
What did i must do to show the countdown plugin on my lcd ?
compile process runs without problems.

Sorry for my english, i do my best to make it better.

Thanks for help
Doc.

---

### Post by wakabakalaka on 2011-07-12
Tried to compile the code Ioshar, came across an error though:

g++ -g -c -Wall -fPIC -Isrc src/ug13.cpp -o src/ug13.o
In file included from src/ug13.cpp:36:
src/keyprofile.h:45:2: error: #error XSD runtime version mismatch
src/keyprofile.h:58:37: error: xsd/cxx/xml/char-utf8.hxx: No such file or directory
make: *** [src/ug13.o] Error 1

The only version I can find in synaptic is 3.2.0.1-1

I'm still running ubuntu 9.10 though :P could that be the reason?

Will be upgrading soon though so will try again

EDIT: upgraded to 10.04 still have the same problem :(

EDIT: so I went around and changed all references to this char-utf8.hxx to string.hxx, I guess I probably shouldn't do that but I didn't really have any other ideas.

So that fixed _that_ problem, then I got:

j@Yuuko:~/Desktop/ghedlund-ug13-fd37c83$ make
g++ -g -c -Wall -fPIC -Isrc src/ug13.cpp -o src/ug13.o
g++ -g -c -Wall -fPIC -Isrc src/keyprofile.cpp -o src/keyprofile.o
g++ -g -c -Wall -fPIC -Isrc src/xmlutils.cpp -o src/xmlutils.o
src/xmlutils.cpp: In function &#8216;int xml_keytype_to_input_keytype(KeyType)&#8217;:
src/xmlutils.cpp:278: error: &#8216;KEY_RFKILL&#8217; was not declared in this scope
src/xmlutils.cpp:367: error: &#8216;KEY_10CHANNELSUP&#8217; was not declared in this scope
src/xmlutils.cpp:368: error: &#8216;KEY_10CHANNELSDOWN&#8217; was not declared in this scope
src/xmlutils.cpp:416: error: &#8216;KEY_CAMERA_FOCUS&#8217; was not declared in this scope
src/xmlutils.cpp:417: error: &#8216;KEY_WPS_BUTTON&#8217; was not declared in this scope
src/xmlutils.cpp:418: error: &#8216;KEY_TOUCHPAD_TOGGLE&#8217; was not declared in this scope
src/xmlutils.cpp:419: error: &#8216;KEY_TOUCHPAD_ON&#8217; was not declared in this scope
src/xmlutils.cpp:420: error: &#8216;KEY_TOUCHPAD_OFF&#8217; was not declared in this scope
make: *** [src/xmlutils.o] Error 1

So I went and commented out all those lines, after that it compiled and I could actually get the program to run! :D

When I run the program the g13 turns red, but then on my console I get this:

ug13 version 1 (Works for me!)
Userspace tool for the Logitech G13 Advanced Gameboard
******************************************************
Found plugin 'McTimer' at plugins/countdown.so
Loading key profile at default_profile.xml
Loaded profile: My Profile
Looking for G13 devices...
Found device at bus: 2 address: 9
Could not open uinput device
Could not create uinput device

uinput is indeed loaded and I set write access using chmod (the rule file is also in there but anyway...)

---

### Post by loshar on 2011-07-15
I am using Ubuntu 11.04 - so I suspect that's the reason for the xsd-cxx version mis-match and the missing key defines.

The version difference may also be the reason for uinput not opening correctly.  The application looks for the uinput device node at /dev/uinput.  Is it possible that the uinput device node is at a different location?  If so - changing line 86 of ug13.cpp should fix.

If you don't have anything displayed on the lcd - reboot with the G13 plugged in and then run the ug13 program again.  I think there may be a step missing when initializing the lcd - I'm looking into this issue.

---

### Post by wakabakalaka on 2011-07-16
Got it to work!

Actually after I fixed compilation errors (by butchering the code :( sorry...) the reason it wasn't finding uinput is that I had tried a different g13 kernel driver earlier (at least I think that's the reason) - so on a new reboot this morning it seemed to work.

LCD is still off but haven't tried plugging it in before starting my PC.

At least pressing some of the keys results in output! Thanks dude :)

---

### Post by loshar on 2011-07-24
After a little digging, a found a solution to the LCD display issue.  Apparently, the usbhid module needs to have a 'quirk' added for the G13.

To do this manually, run the following command:
 
 sudo rmmod usbhid; sudo modprobe usbhid quirks=0x046d:0xc21c:0x4

Then unplug and plug in your device.   You should see the 'G13' logo displayed now.
 
 To make the fix permanent, edit the file /etc/default/grub and edit/add the line
 
 GRUB_CMDLINE_LINUX="usbhid.quirks=0x046d:0xc21c:0x4"
 
 Then run the command:
 
 sudo update-grub

I'll add this to the readme in my next update.

Cheers.

---

### Post by Doc_Smimble on 2011-07-24
Hi loshar,

great to see some progress in this project.
but i saw every time after plugged-in the usbcable the g15 logo.
That was not for me a problem. 
The only thing what still not working is writing some text on the lcd, after the "g15 logo". 

But what i can say is that when i use the follow programs from the g15tools project: 
"g15tools/trunk/g15daemon/g15daemon/" and the 
"/g15tools/trunk/g15composer"
i still got the lcd working.
Can you migrate some code from that in your project ?

Thanks Doc.

---

### Post by loshar on 2011-07-24
Strange - things are working consistent for me after I placed the 'quirks' argument in the /etc/default/grub file.

Just want to make sure, you said you see a 'g15' logo?  On your G13 - you should see the word 'G13' in big, bold letters when you plug in the device and no driver has been loaded.  If you see anything else it means that you have another driver using the LCD screen and the ug13 program will not be able to write to it...

I do not have a G15 myself so I have not tested what happens when you try to run the G15 tools and the ug13 program at the same time.  My guess is that the G15 tools will have taken control of the device already if you are running both.

---

### Post by wakabakalaka on 2011-07-25
Hi loshar,

I'm trying to emulate a half keyboard from:

[http://forums.logitech.com/t5/G-Series-Gaming-Keyboards/Lua-example-polling/td-p/410166](http://forums.logitech.com/t5/G-Series-Gaming-Keyboards/Lua-example-polling/td-p/410166)

which basically, when you press (and keep pressed) one of the click buttons next to the small joystick, it switches the G13 into a different mode.

When you release that button (or G-key), the mode switches back to M1 say.


Is it possible to do this with your driver?


One of the first steps would be to be able to assign a G-key to switch one of the M-modes, I tried mapping one of the G-keys to switch to M1/M2/M3 but it said key not recognised :/ (I tried "M1" and "M1key")

---

### Post by Doc_Smimble on 2011-07-25
Hi loshar,

sorry it was my mistake i mean i saw the g13 Logo on my g13 Keyboard. 
After that i use the temporary rmmod,modprobe step and started your program but it shows me nothing (for example some text on the Lcd) except the rgb-color on the Lcd.
I'm totally agree with you, that both programs g15tools and ug13 cant be run at the same time. 
i just say it, because the Lcd Text works perfect under the g15tools, 
but they had some problems with recognize the Keys.
And my hope was, it could be help you to fix the Lcd Text problem when you look at the code of the g15tools. 

Now my results are: 
ug13 = keys,leds works, except lcd (for me)
g15tools = lcd works, except keys,leds. 

Thanks Doc.

---

### Post by Doc_Smimble on 2011-08-01
Hi Guys

Please check out ecravens new update for his g13 driver.
[https://github.com/ecraven/g13](https://github.com/ecraven/g13)
i played a little bit with his basic shell script
the results are here:
[https://github.com/Doc-Smimble/g13-addons](https://github.com/Doc-Smimble/g13-addons)

Thanks Doc

---

### Post by tanktarta on 2011-08-22
Hey,

I was doing a little searching in order to publicise the latest release release of Gnome15, and stumbled on this thread.

Version 0.7.1 now has fairly good G13 support (for everything except the joystick - I am working on that). The best driver to use is "g15direct", which is based on a modified libg15 (i.e. g15tools). Packages are available for all components on Ubuntu 10.04 up to 11.04. 

Feel free to drop by [http://www.gnome15.org]("http://www.gnome15.org") and report if it works for you :)


Brett

---

### Post by Miscni on 2011-08-22
> **Doc_Smimble said:**
> Hi Guys

Please check out ecravens new update for his g13 driver.
[https://github.com/ecraven/g13](https://github.com/ecraven/g13)
i played a little bit with his basic shell script
the results are here:
[https://github.com/Doc-Smimble/g13-addons](https://github.com/Doc-Smimble/g13-addons)

Thanks Doc

Doc

Just a curious question, have you gotten ecravens new update to work?
Because I just posted my errors on [https://github.com/ecraven/g13](https://github.com/ecraven/g13) and some ideas to.

I have been contacted by a couple of people on my TS, who has have gotten the same errors like me, so I really hope, we can get this here to work.

Cheers

---

### Post by Doc_Smimble on 2011-08-23
> **Miscni said:**
> Doc

Just a curious question, have you gotten ecravens new update to work?
Because I just posted my errors on [https://github.com/ecraven/g13](https://github.com/ecraven/g13) and some ideas to.

I have been contacted by a couple of people on my TS, who has have gotten the same errors like me, so I really hope, we can get this here to work.

Cheers
Hi Miscni

First of all please checkout that no other programs like g15-tools,etc runs at the same time in the background.
Your write this: [I]"When I type ./g13 starcraft2.bind or war.bind etc, I get this errors here:
Invalid LCD data size 352, should be 960
Invalid LCD data size 4294967295, should be 960"[/I]
Please start only the program like this "./g13" nothing more.
after that you must see the gnu logo on your g13 devices.[FONT=monospace]
[/FONT]ecraves writes: The daemon creates a pipe at /tmp/g13-0, [FONT=monospace]
[/FONT]you can send commands via that pipe (e.g. by running "echo "rgb 0 255 0" > /tmp/g13-0")
One way to use the bind files is this:
echo "$(cat starcraft2.bind)" > /tmp/g13-0
[FONT=Verdana]
[/FONT]You write this:* "I also looked over your code in g13.cc, and under line 647, I found this here  "map = KEY_A;"*
Thats ok, the KEY_A binds automatic all not reserved keys.
This is a function demo, to give you feedback that all your keys of the g13 working.
You can disable this with writing the follow code:
"map[i] = 0;"
[FONT=Verdana]
Hope it helps you.

Thanks Doc.
[/FONT]

---

### Post by Miscni on 2011-08-23
Doc Thx for the info.

It worked, plus I am trying to make a new video guide, so it can help others.

Mainly reason why I am makeing this guide, is that not many people are so much into commandcode in terminal etc. 

I am aware of. that it seems a little bit ridiculous, but after I had my first video from Ecraven, I get more and more support requests. So I just try to do my best to help out everybody.

And about the code line I wrote, let us just skip that part. (mybad, and I am sorry for that). I didn't understand the cat-commands, before you were so polite to add in your thread, and I thank you for that.

I will let you know, how it turns out.

Cheers and many thanks

---

### Post by Doc_Smimble on 2011-08-24
Hi Guys,

@Miscni check your pm´s

adding the bash-script "g13_sysmon.sh" to my g13 repro. 
Link: [https://github.com/Doc-Smimble/g13-addons](https://github.com/Doc-Smimble/g13-addons)
My next Script will be an APC (American Power Conversion) USV Bashscript (shows the output of apcaccess on your g13) with Battery Symbols.

Thanks Doc

---

### Post by Jim Gupta on 2011-09-24
I've been waiting for some type of driver/interface that I like.  Unfortunately, no one has made one that I'm happy with.

The ecraven driver (from [https://github.com/ecraven/g13](https://github.com/ecraven/g13)) gave me enough info to create a driver and a UI that is similar to the windows one.

I have started a project to create a UI and driver to my liking.  If it works for you as well, then great.

My project is at [http://code.google.com/p/linux-g13-driver/](http://code.google.com/p/linux-g13-driver/) where you can download the source and compile the driver (simple to do).

If you want to send me (constructive) tips or advice please feel free, especially if you understand how to write to the LCD.

Here's what my UI currently looks like:


[IMG]http://i53.tinypic.com/2na679u.jpg[/IMG]

---

### Post by wakabakalaka on 2011-09-25
Hi Jim, does your project support changing M mode by pressing a G key?

By that I mean say you press G1 and it swaps the G13 from M1 to M2 (so the colour changes and the layout changes).

I'm trying to emulate the half qwerty keyboard but it isn't convenient to have to press the M keys to change M mode, rather pressing one of the G keys or click buttons to change mode would be much more convenient.

---

### Post by Jim Gupta on 2011-09-25
Hi Waka,

To change modes/keybindings, you push one of the 4 little buttons below the LCD screen.  The windows support for changing bindings was to press M1-M4, which I found inconvenient.

You shouldn't have to emulate the half keyboard.  That's the default configuration.  You can map any G13 key to any key on your keyboard and (if you create a macro) make them auto-repeat.

As far as switching bindings (bindings define which color shows up on LCD) by pressing G1 (or any Gkey), that isn't supported and I'll keep that in mind.  Maybe it would be best to report that as an issue ([http://code.google.com/p/linux-g13-driver/issues/list](http://code.google.com/p/linux-g13-driver/issues/list)) and put "Enhancement Request: Make any key be able to switch bindings"

- Jim

---

### Post by Keith_Beef on 2012-03-07
Impressive looking GUI, I wonder how usable this G13 controller is now... I have been looking at something like this to use for Oolite, Flight gear, maybe some other games and also for CAD software and GIMP.

How does usablity and configuration compare to, for example, the Belkin or Razer Nostromo Gaming Keypad?

K.

---

### Post by Kyterra on 2012-03-29
I just wanted to say thanks a million for your work in creating this driver and the configuration GUI. It works great in Ubuntu 11.10 64bit. I hope you'll keep it working for future versions of Ubuntu, including the upcoming 12.04!

Thanks again.

---

