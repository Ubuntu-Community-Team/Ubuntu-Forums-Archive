---
title: "Putting Ubuntu on HP's tx2500z..."
date: 2008-12-16
forum: Hardware
---

### Post by atravnicgeheim on 2008-12-16
...and is the installation idiot and bullet proof? 

I've scoured Ubuntu-focused forums and chat rooms to see what problems folks are running into installing 8.04 or 8.10 on HP's tx2500z. The verdict seems mixed, but scary enough to give me pause. Nonetheless, I just ordered one of them--won't get built until later this December--and would much rather have Ubuntu on it than Vista. 

So my question is, have things stabilized to the point where its safe for a total Ubuntu and Linux novice like me (if it involves using terminal or installing drivers I'm totally lost) to go ahead or should I not chance it? Also, I'd like to be able to boot into both Ubuntu and Vista. Does that complicate things unecessarily?

And, finally, would I be better off going with Dell's Inspiron Mini 12 (not the same class of machine as the tx2500z I realize) with Ubuntu already installed?

Thank you folks for any help you can offer.

...Fred

---

### Post by albinootje on 2008-12-16
> **atravnicgeheim said:**
> 
So my question is, have things stabilized to the point where its safe for a total Ubuntu and Linux novice like me (if it involves using terminal or installing drivers I'm totally lost) to go ahead or should I not chance it? Also, I'd like to be able to boot into both Ubuntu and Vista. Does that complicate things unecessarily?


Dual-boot installations (Windows/Linux) have become much easier the last few years in Ubuntu. The partitioning part in the installation has a nice and well working resizing tool since a while.

One thing to remember for the future (after having a dual-boot installation) is Microsoft's patent on overwriting bootloaders without asking. So if you reinstall Windows in the future, don't panic if you don't see Linux in the boot-menu anymore, just read this :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Favux on 2008-12-17
Hi atravnicgeheim,

There are a bunch of us TX2000 and TX2500 users on the forum.  We've got just about everything working, including the wacom tablet.  Do you know if the z's multitouch is wacom?  If so there should be good help getting it going, but I doubt the linuxwacom driver will support multitouch when you first install.

I'd be interested in hearing about the machine.

---

### Post by atravnicgeheim on 2008-12-17
I'd like to thank albinootje and Favux for their advice. But I would like to re-emphasize that, unless installation is turn-key and works right out of the box for me, I won't be able to handle it. I simply won't be able to tweak it the way I have seen others here do. So what I'm looking for is an unequivocal YES, it works like a charm out of the box, or a NO, you will need to massage it. If the latter is the case, I'd just as soon go to Dell and get a lesser machine with Ubuntu pre-installed. 

Based on your experience, what is your opinion. And thanks again.

...Fred

---

### Post by Favux on 2008-12-17
Hi atravnicgeheim,

Based on:
> So what I'm looking for is an unequivocal YES, it works like a charm out of the box, or a NO, you will need to massage it. If the latter is the case, I'd just as soon go to Dell and get a lesser machine with Ubuntu pre-installed.
unfortunately I would have to recommend going to Dell, unless HP starts preinstalling linux.  You should be able to install Ubuntu from the install CD and have a working laptop, but you would be missing a few features, including the wacom tablet (except perhaps the stylus).  At least that is my guess until you get a report from someone with your model.

But I think you are making too much of having to do some tweaks and using terminal, etc..  It's not as difficult or scary as it seems at first.  Besides it is a great way to start learning linux.  I think you've worked yourself up to a "mental block" regarding how difficult it would be.

---

### Post by atravnicgeheim on 2008-12-17
> **Favux said:**
> Hi atravnicgeheim,

Based on:
 unless HP starts preinstalling linux. Fat chance, they don't even know what Ubuntu is.

  You should be able to install Ubuntu from the install CD and have a working laptop, but you would be missing a few features, including the wacom tablet (except perhaps the stylus).  At least that is my guess until you get a report from someone with your model.

But I think you are making too much of having to do some tweaks and using terminal, etc..  It's not as difficult or scary as it seems at first.  Besides it is a great way to start learning linux.  I think you've worked yourself up to a "mental block" regarding how difficult it would be.

Very delicately put. I have struggled with it, even got advice from colleagues, but haven't been able even to get a downloaded software package installed. I'm no Windows fan, but that process is easier in Windows. 

Also, there is a lot going on in my life right now (surgery, serious car accident, Christmas, relatives coming to visit), so I've had to accord "tinkering" a low priority.

Thank you for addressing my Ubuntu fixation. I got a kick out of it.

---

### Post by Favux on 2008-12-17
Well, I have had a tad bit of experience.  I have a sister who has/had a "block" regarding any computer.  But then course work forced her to get a laptop (which I picked out for her).  So after 5 years of constant hand holding, 3 weeks ago she upgraded her RAM modules by herself!  Breakthrough!  Ok, so I was on the phone through the whole thing.  Still it's the concept.

---

### Post by atravnicgeheim on 2008-12-18
The question was asked does the tablet part of the tx2500z uses Wacom. 

Not sure if the below answers the question, but it's all that's available on the tx2500z web page. Since the below HP blurb doesn't mention Wacom, and since the Wacom technology seems to be a problem, does this mean the touch screen functionality may actually work under Ubuntu?

Thanks a bunch.          ...Fred

............................................

 	**  12.1" diagonal WXGA High-Definition HP BrightView Widescreen (1280 x 800) w/Integrated Touch-screen**

     *[I][I]	HP gives mobile computing a whole new twist with this small, lightweight notebook featuring an innovative, high-definition display that opens for classic notebook use, twists for presentations and folds flat for use like a slate. Use your finger to quickly and easily select photos or music tracks in HP QuickPlay. Navigate your favorite website as you use the pad of your finger to scroll on the screen. Control your favorite games with the touch of your finger. The included pen conveniently recharges while you write on your tx2000. It is battery-less, so you never have to change out a battery. Erasing notes on your screen is as easy as erasing notes with a pencil - just flip the pen over and erase! Use Windows Journal to take notes as you would on notebook paper - you can even search the handwritten text by writing the word or phrase with the eraser pen. The tx2000 automatically converts handwriting into typed text - take notes in Windows Journal and select the text you want to convert. It's that simple. Bring images and movies to life with HP's BrightView technology! BrightView technology improves the contrast and clarity of your notebook display screen. DISCLAIMERS: High-Definition content (e.g. WMV HD files) is required to view high-definition images. Most current DVDs do not provide high-definition images. *[/I][/I]

---

### Post by cak3 on 2009-01-27
Its a bit late, but I ran across this while looking for instructions for getting the tablet functionality working, but I would just like to point out that I am running Intrepid on a tx2500z, and I had no issues getting it working (there are even proprietary drivers for the ATI card). The only issue, aside from the table functionality (which I have not attempted to get working yet) is that I had trouble connecting to WPA2 Enterprise networks, but I got that working (see [http://ubuntuforums.org/showthread.php?p=6626893#post6626893](http://ubuntuforums.org/showthread.php?p=6626893#post6626893) )

So, 8.10 plays quite nicely with this particular HP at least.

---

### Post by Favux on 2009-01-27
Hi cak3,

I agree, the TX2500 works great with a little tweaking.  I will confess back in December I was confusing the model atravnicgeheim was planning on getting with the TX2z.  The TX2z has the N-Trig digitizer with multi-touch (pretty cool).  But the main thing is he wanted the install disk to just install and afterwards have everything working without tweaking.

By the way the "ccmp" deletion with switching to WICD.  Interesting idea.  I tried WICD before learning the gconf editor thing.  Maybe you've explained why I couldn't get WICD to work.

---

### Post by cak3 on 2009-02-05
If you try it and it works for you too, I would like to know, just to make sure the solution was not specific to me.

Ironically, I got the idea from your post ([http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)). Since it was apparently the network manager that was adding the erronneus entries, I figured using an alternative might work, and somebody had suggested WICD. It just doesn't re-add the ccmp.

---

### Post by Favux on 2009-02-05
Hi cak3,

Sounds like a good idea and well worth trying from an educational point of view.  Finding out if the solution generalizes would be useful.

However wireless is working great.  Given how long I was without (and tethered by an ethernet cable), I hope you'll understand why I choose not to experiment!

Sorry.

---

### Post by cak3 on 2009-02-05
Heh, thats fine. I understand perfectly, since I spent a while on it myself.

---

