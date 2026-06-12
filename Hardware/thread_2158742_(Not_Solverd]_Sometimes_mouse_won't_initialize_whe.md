---
title: "(Not Solverd] Sometimes mouse won't initialize when desktop appears"
date: 2013-06-30
forum: Hardware
---

### Post by WB0HYQ on 2013-06-30
I am using Ubuntu 12.04LTS and when I boot up the computer I run around a 3 in 1 chance that the mouse will remain frozen in place at the center of the screen.  So far, my only solution I have found was to open a Terminal (the keyboard works fine) and execute a shutdown/reboot.

I am wondering if there is a more elegant procedure to kickstart the mouse into action.  The mouse is a HP M-S48 (both it and the keyboard use PS2 inputs).  I was thinking of something like reinitializing the driver from a Terminal.  Is that possible?

Bill

---

### Post by WB0HYQ on 2013-06-30
A hundred and eight people have seen this and not a single one can even offer a hint of what I can do to solve this?  Hard to believe, since the ***is ***the hardware panel of the forum.

Bill

---

### Post by WB0HYQ on 2013-07-01
Anybody?  Come on, take a stab at it and help a guy out.

Bill

---

### Post by WB0HYQ on 2013-07-01
Bump

---

### Post by WB0HYQ on 2013-07-02
This is absurd.  I would have thought that a simple mouse problem would bring at least one offer of help.  I am assuming that it is seen as some sort of device, does that mean '/dev/something' or is it just a driver?  Can the device be reinitialized without having to reboot the machine?  Come on; give a hand here.

Bill

---

### Post by Iowan on 2013-07-02
Any advice I could give would be a blind guess - probably less useful than the responses you've received... but just to let you know your thread is not invisible.
I also have an HP mouse - M/N M-S69. It seems to cause no issues - even though connected through a 4-port KVM. (Monitor is another story.)
On my 12.04 system, there is a /dev/input directory with files *mice* and *mouse0*.

Found this in a help file:
```
Check that the mouse was recognized by your computer
Type Ctrl+Alt+t to open the Terminal.
In the terminal window, type xsetpointer -l | grep Pointer, exactly as it appears here, and press Enter.
A short list of mouse devices will appear. Check that at least one of the items says [XExtensionPointer] next to it, and that one of the [XExtensionPointer] items has the name of the mouse to the left of it.
If there is no entry that has the name of the mouse followed by [XExtensionPointer], then the mouse was not recognized by your computer. If the entry exists, your mouse was recognized by your computer. In this case you should check that the mouse is plugged in and in working condition.
```

---

### Post by WB0HYQ on 2013-07-03
Thanks for the reply.  I had about given up.  I thought at first that my 4-port KVM might be causing the problem but then I isolated the computer from the KVM and then used a direct connection.  It would still fail to initialize at times, so I went back to the KVM since I tend to switch between computers depending on what task I'm currently doing.

My Ubuntu box is not up at the moment, but I will try the informational call in the morning and see what it says.  Your procedure might show (when the mouse is working) the necessary information and not show it when the mouse is frozen.  That is good to know.  What I am after is what to do if '[extensionpointer]' doesn't appear.  There has to be some command I can issue that will electronically kick the mouse driver and make it re-assess the hardware (maybe access some sort of CONF file and restart it.

At least I now know my posts are being *read *(despite the over 200 reads indicated).

Bill

---

### Post by Bucky Ball on 2013-07-03
No one posted because no-one could help or had suggestions. Harrassing people for that is not going to help you, just the opposite. Please bump once in 24 hours, no sooner.

My wife bought a wireless mouse the other day that had me stumped. Then I realised it was a really cool power saving mouse that switches itself off when it hasn't been used in awhile (45 seconds?) to save battery (and a good thing, too). Click the scroll wheel and away it goes, back to life. Just a thought ...

---

### Post by WB0HYQ on 2013-07-03
> **Bucky Ball said:**
> No one posted because no-one could help or had suggestions. Harrassing people for that is not going to help you, just the opposite. Please bump once in 24 hours, no sooner....

I don't think the term 'harassment' enters into the situation here.  I've harassed nobody at all.  I simply made a couple of comments that after over 200 people have viewed this thread in a HARDWARE panel it was surprising that nobody had said a thing.  As for bumping, I am a member of a LOT of forums and bumping rules vary greatly between them.  I will take your advice into consideration. Is there an etiquette thread that I can read?

 Thanks for stopping by.

Bill

---

### Post by Bucky Ball on 2013-07-03
The CoC can be found here:

[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

You would have read the CoC when you joined the forum. It has been trimmed down recently. 

The Ubuntu CoC can be found here:

[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)

Bumping is not referenced in there but twenty four hours is the generally accepted rule forum wide. Of course, you could provide further information within this time which would do the same job; for instance, if you try something new and it fails or you make a minor breakthrough or think of something relevant post it. ;)

---

### Post by WB0HYQ on 2013-07-03
@BuckyBall:  Apparently, you don't accept PM's.  I tried three times to send one, but it simply disappeared from my outbox.  That is neither here nor there as our conversation does not solve my problem.

Bill

---

### Post by WB0HYQ on 2013-07-03
Now, to get back on track...

The data produced by the 'xsetpointer -l' command was this:

```

xsetpointer -l
2: "Virtual core pointer"    [XPointer]
3: "Virtual core keyboard"    [XKeyboard]
4: "Virtual core XTEST pointer"    [XExtensionPointer]
5: "Virtual core XTEST keyboard"    [XExtensionKeyboard]
6: "Power Button"    [XExtensionKeyboard]
7: "Power Button"    [XExtensionKeyboard]
8: "AT Translated Set 2 keyboard"    [XExtensionKeyboard]
9: "ImPS/2 Generic Wheel Mouse"    [XExtensionPointer]

```

So, this tells me that in this instance of booting up the mouse was found and set up properly.

I have found that over the last seven boots that if I am moving the mouse as the desktop appears that it will continue to move afterwards and not freeze.  Of course, this could just be the law of averages and it will still freeze at some time, but I am hopeful that I have found a way to counter the freezups.

Bill

---

### Post by WB0HYQ on 2013-07-06
Well, I'm going to have to give up on this and just keep on rebooting and hope that the mouse will work.  Thanks to those that responded.

Bill

---

