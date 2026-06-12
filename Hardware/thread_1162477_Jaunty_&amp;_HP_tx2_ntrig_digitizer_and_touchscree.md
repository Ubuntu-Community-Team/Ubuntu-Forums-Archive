---
title: "Jaunty &amp; HP tx2 ntrig digitizer and touchscreen"
date: 2009-05-17
forum: Hardware
---

### Post by techphets on 2009-05-17
Hi, 

I installed Ubuntu 9.04 Jaunty on an HP tx2 laptop/tablet convertible. 

Sound and video took a bit of work but are working properly. 

The ntrig stylus location tracks properly and touching the screen left-clicks.  I am not yet able to right-click or use compositing with the stylus.  

I've read references to Rene Mayrhofer's [blog entry]("http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77") discussing Ubuntu Intrepid 8.10 and Dell Latitude XT tablet setup.  It refers to a hack which seems to help with tracking the stylus, something which already works on my system. 

I would like to enable: 

 * right-clicking
 * compositing with stylus
 * screen rotation 
 * touch 

in that order. 

Starting with right-clicking, my xorg.conf file does not have the  "ServerLayout" section which Rene states should already be there.  It also has no information on input devices.  The comments state that config settings which could be done previously in this file are now automatically configured by the server and settings here are ignored.  Does Jaunty recognize input devices here? 

When I run the wacom control panel, wacomcpl, no devices are detected. 

Any ideas on what I should try? 

Thanks!

---

### Post by techphets on 2009-05-17
By adding the "stylus" section from the code listed [here]("http://ubuntuforums.org/showthread.php?t=1038898") I was able to get the right-click to work (only when the pen is actually touching the screen). 

I tried adding the "touch" section but the results are the same with or without it: 

When I touch the screen the cursor moves to the top-left corner.  I would like to disable touch all-together so that I can write on the screen without disruption.... This is now my primary goal. 

I did not see anything about the trackpad in xorg.conf.  Since the trackpad is working I left it out but I am curious where that configuration is stored now if not in xorg.conf. 

Thanks again.

---

### Post by Favux on 2009-05-17
Hi techphets,

With the 0.8.2-2 linuxwacom drivers that come "native" with Jaunty (specially patched to support Xserver 1.6 and HAL) you are supposedly not suppose to use xorg.conf.  You are suppose to use the HAL/.fdi method.

You could compile linuxwacom starting with 0.8.3-2 and up, since 0.8.3-2 is the first to support Xserver 1.6 and then use xorg.conf.  You'd want to use the newest patch by Rafi Rubin which is linked on post #136 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=14](http://ubuntuforums.org/showthread.php?t=1038898&page=14)  And read the posts that follow.

So basically Jaunty isn't quite ready for N-trig yet.  Not without some work.  You might want to get together with Keeper of the Keys and glurgle.  Maybe glurgle is going to post a HOW TO shortly.

Good luck!

---

### Post by theverant on 2009-05-19
Just got this tablet.  Didn't even bother booting Vista and went ahead with a regular 9.04 install (netbook remix busybox'd on live boot or straight install). Eager to get everything (as much as possible) working.  Is there a complete setup HOWTO, such is available for Macbook?

Is NTrig for touch, and Wacom for pen?  Is it possible to use a regular Wacom pen, so that I have eraser function, and a larger stylus?  Is it possible to just disable touch for now, until it is working properly?

What are you guys finding for battery life?

---

### Post by cbrahm on 2009-05-20
Hi Guys,
I have the HP TX2-1080 (same as the TX2z) that comes with the N-Trig digitizer+touchscreen  and my question is, since there is no "The N-Trig Project", how can we know if the wacom driver will fit 100% with the N-Trig?

I installed Jaunty, and It works out of the box. But so far I can't disable touch, so I can't write freely because when I touch the screen with my hand the pointer goes to the top left corner.

I know there is an issue with names so wacomcpl would not work even with a wacom product, but since there is absolutely NO WACOM at all in my laptop (lshal or lspci or  dmesg will never report any wacom ino, actually the N-tring identify itself as "HID 1b96:0001") will I ever be able to calibrate it under jaunty?

I have until today to return it so if someone can tell me what to do (would love to keep it) I'll really apreciate it.

regards
Cristobal

---

### Post by Favux on 2009-05-20
Hi cbrahm,

The linuxwacom names HAL isn't returning are stylus, eraser, touch.  Instead of stylus it will say something like "HID 1b96:0001" and for eraser "HID 1b96:0001 eraser".  So first we came up with a script to get around it, then we realized we could just rename things, and finally we figured out a .fdi that parsed the names correctly.  See Jaunty Users near the top:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by gorg0th on 2009-06-08
"I installed Ubuntu 9.04 Jaunty on an HP tx2 laptop/tablet convertible. 

Sound and video took a bit of work but are working properly."

Could you point me to which settings were required to get the sound working?  I also have the tx2 and also with jaunty, but as yet I haven't managed to get teh sound working reliably.

---

### Post by Favux on 2009-06-08
Hi gorg0th,

Welcome to Ubuntu!

See exophobes' post #72 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=8](http://ubuntuforums.org/showthread.php?t=1038898&page=8)

Good luck!

---

### Post by nema.arpit on 2009-06-10
@Favux
Isn't exophobes' post for 8.10 Intrepid??
I tried it anyways,but could not really see any change...
My sound worked from the start,except for a Major glitch: whenever you increase the volume too high, the speakers automatically mute themselves,a pc speaker beep brings it back, but the volume is simply too low. In windows the same speakers are pretty loud.(my problem is same as that of Vincent_Lin in post [http://ubuntuforums.org/showthread.php?t=995885&page=2&highlight=tx2z](http://ubuntuforums.org/showthread.php?t=995885&page=2&highlight=tx2z)) {**@gorg0th** you might wanna try the beep trick.}

Also the rotate script did not work good for me.On executing the script using "sudo sh" command my screen rotated and got stuck there,that too at half the screen height.

The xorg.conf update did not help any either : my touch still not working correctly,the cursor jumps to top right corner whenever I touch the screen(My stylus worked from the start too).

**P.s.:I am an absolute newbie at linux so please do tell me if I am doing something wrong.**
Can anyone help me out?

---

### Post by Vincent_Lin on 2009-06-10
Hi Nema-arpit,

I have the same sound problem on my tx2z as you are experiencing(you mentioned it in your post).  My way of solving it was to disable pulseaudio.  It is doable in 9.04 by simply issuing the command in a terminal window:

sudo apt-get remove pulseaudio

Then you can turn on the volume as loud as you like.

This only works in 9.04, as it seems to me, pulseaudio in 8.10 is more "integrated" into gnome desktop that prevents me from removing single pulseaudio package only without removing gnome as well.

But, there is always a but.

When I looked at my installed package via synaptic while trying to find the correct package name to write this reply, I saw pulseaudio is listed as installed.  And my sound is still working fine. 

So, what actually happened, is really beyond me.  

Good luck!

Vincent

---

### Post by nema.arpit on 2009-06-10
Thx Vincent,even tho i did not try your solution.
What I did do was follow Favux's suggestion,only with a bit of modification( interestingly by Favux him/her self.I wonder why he/she did not mention in his post on this thread)
Just go thru this thread :[http://ubuntuforums.org/showthread.php?t=1183118](http://ubuntuforums.org/showthread.php?t=1183118)

---

### Post by Favux on 2009-06-30
Hi everyone,

Ayuthia has figured out how to get the stylus and touch working in Jaunty for the TX2z and the Dell XT.  You have to use a xorg.conf for it to work.  See Appendix 2 here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  to pick up the xorg.conf.  There is a link to Ayuthia's instructions and deb.s there also.

---

### Post by antispin on 2009-07-05
I purchased a tx2-1244ca on Saturday and have been setting up Jaunty on it. THANKS to Favux, Ayuthia, idyllictux and other contributors for all of your work on this. The result:

- Sound works fine. I disabled PulseAudio using instructions here: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

- Video works fine. I am using the "fglrx" driver with desktop effects disabled. As noted by Favux, rotation and Compiz won't work at the same time with fglrx.

- Stylus worked out of the box (but not pen button)

- I used the instructions pointed to by Favux above to get the pen button and touch working. I also got rotation working using method #3. The rotation button on the bevel won't work, sadly :( I don't know if there's a rotation signal being sent from the hinge on this model -- it didn't work in Vista so I didn't try the method suggested in the thread.

What I noticed:

- on rotation, the calibration is sometimes off initially but corrects itself as soon as you switch applications. The mouse pointer also sometimes doesn't rotate initially, but again fixed itself when you switch apps.
- touch only works for selecting things. I cannot click or right-click using touch.

Personally, I think this setup will work for me. It would be nice if I could use the buttons on the bevel, and better touch support (multi-touch?) would be great, but I don't need those right now.

Oh, and my boot time is now 3x faster than it was under Vista :D Thanks for saving me from Microsoft, folks!

---

### Post by Favux on 2009-07-05
Hi antispin,

Welcome to Ubuntu!

Great job with getting stylus, touch and rotation working!

I don't know if it is possible to get touch to "click".  In the stylus section of xorg.conf:
```
	Option		"Button1"	"1"
```
is default.  Where Button1 is the stylus tip and 1 is the left mouse click.  3 would be a right click.  I don't think it would do anything adding it to the touch section, because touch probably doesn't accept the Button option.  The same probably applies to the Threshold option.

It may be worth trying but the worse case scenario is that it would break X.  So if you want to try it back up your xorg.conf and be prepared to reinstall it from the command line.  If you want to try it and need the commands let me know.

Another possibility is that the Capacity option isn't sensitive enough.  This is a touch option and Capacity can be between -1 to 5.
```
	Option		"Capacity"	"number"
```
You would just try each number in turn and see if you notice any difference.

---

### Post by antispin on 2009-07-06
Well, I've been using Ubuntu since 4.10 and started off on Slackware many years ago :D the level of hardware support I am seeing in Linux now though, thanks to Ubuntu, is frankly amazing. 

I never would have expected to get this tablet PC working so well on Linux.

I find I *can* left-click using touch, but it's very hit-and-miss. Thanks for your suggestions -- I am going to try them soon when I have a little more time and will report back.

---

### Post by Favux on 2009-07-06
Hi antispin,

I suspected you were a veteran and that the post #1 was misleading.  So maybe welcome to Ubuntu forums?

Yes some talented folks working on it.  Hopefully Rafi Rubin's patches will be taken up by the LWP like his kernel HID stuff has been by the kernel folks.  With MPX and other mult-touch stuff supposedly scheduled for the next few versions of Xserver you can hope for experimental stuff available for Kharmic and production stuff for 10.4.

---

### Post by Nimless on 2009-07-06
Hi,

I have a dell latitude XT and ubuntu 9.04, digitizer it's the same from N-Trig.

Everything works but the touch screen miss "taps" sometime . ( finger taps )

Any idea why?

---

### Post by Favux on 2009-07-06
Hi Nimless,

Welcome to Ubuntu!

No I don't know why it's missing taps.  Antispin is looking into it.  See my post #14 above.  You might want to start with the Capacity option.

If you're not using the xorg.conf I posted on the Rotation HOW TO maybe you could post yours and we could take a look?

Maybe Ayuthia's encountered this and has already investigated it.

---

### Post by Nimless on 2009-07-06
> **Favux said:**
> Hi Nimless,

Welcome to Ubuntu!

No I don't know why it's missing taps.  Antispin is looking into it.  See my post #14 above.  You might want to start with the Capacity option.

If you're not using the xorg.conf I posted on the Rotation HOW TO maybe you could post yours and we could take a look?

Maybe Ayuthia's encountered this and has already investigated it.

Hi!

Thanks for answering.

I'm using the xorg.conf you posted, also this behaviour with kernel 2.6.30 and up appears ALWAYS, but with the modified 2.6.28.13 by Ayuthia it appears only "AFTER" i've tapped the screen with the stylus, after a fresh boot touch taps works flawlessly.

Seems to me the stylus breaks something and Ayuthia patches are really close to get touch working :)

---

### Post by Favux on 2009-07-06
Hi Nimless,

OK, good to know it does work for a Dell XT.  Thank you.  It would be good to see what your other xorg.conf sections look like if you get the chance.  I too think Ayuthia did amazing work.  That seems to indicate the kernel support in 2.6.30 (and up, and 2.6.29?) isn't enough, the wacom drivers need some work beyond Rafi's n-trig.patch for identification.

We had to add:
```
	Option		"Touch"		"on"
```
to get touch working, even though that should be default.  So try adding just under it:
```
	Option		"Capacity"		"3"
```
Where 3 is default for a capacitive touch device.  I think the n-trig should be treated as one.  Then try varying the number to see if you can get more sensitivity and if that makes a difference.  Since the n-trig doesn't quite behave like a wacom even with the patches be sure to have xorg.conf backed up and be prepared for breakage.

---

### Post by Nimless on 2009-07-06
I tried with the capacity option, doesn't seem to be doing anything at all, i also tried with xsetwacom set touch Capacity *number* .

Here is my Xorg.Conf


EDIT : i tried something checking all the wacom parameters before and after "stylus usage" and nothing changed in Suppress,Capacity,ClickForce...etc, but i tried something else

```
 rmmod usbhib && modprobe usbhid && /etc/init.d/gdm restart 
```

set touch tapping working again, so to me it appears as confirmed that the stylus breaks something in the usbhid.

It seems pretty strange also that it works flawlessly only with this particular patched kernel and not even with the 2.6.31-rc1 kernel...

---

### Post by Favux on 2009-07-06
Hi Nimless,

I doubt this will make a difference but give it a shot anyway.  Possibly putting stylus before touch may change behavior, so you could try that too.

---

### Post by Nimless on 2009-07-06
> **Favux said:**
> Hi Nimless,

I doubt this will make a difference but give it a shot anyway.  Possibly putting stylus before touch may change behavior, so you could try that too.

Not working, but thanks for trying :p

---

### Post by Favux on 2009-07-06
Hi Nimless,

I figured, oh well.  So now we can try some strange stuff like the buttons thing.  It shouldn't work but n-trig is a little different so maybe.  I wish I understood why Rafi had some of the stuff he does in his xorg.conf.  We could also look at the supress option.

By the way the xorg.conf I was referring to is at the bottom of this HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  Appendix 2 talks a little about using it.

I PM'd Ayuthia.  Hopefully he'll add something.

---

### Post by Favux on 2009-07-06
Hi Nimless,

> It seems pretty strange also that it works flawlessly only with this particular patched kernel and not even with the 2.6.31-rc1 kernel...
Well given there is a lag time from when Rafi submits his patches to the HID section of the kernel maybe not so surprising.  I know at least his "button" patch was pretty recent.  So maybe some of Ayuthia's patches are a little ahead of the most recent kernel.

Responding to your edit in #21.  So at a minimum you could set up a launcher with?:
```
rmmod usbhib && modprobe usbhid && /etc/init.d/gdm restart
```
And get touch back when you need it?  Crude but if it works, workable.

> it appears as confirmed that the stylus breaks something in the usbhid.
Maybe rather than breaking something there's a "grab" without the expected release.  Which would seem to me to be a coding issue.

---

### Post by Nimless on 2009-07-06
> **Favux said:**
> 
```
rmmod usbhib && modprobe usbhid && /etc/init.d/gdm restart
```
And get touch back when you need it?  Crude but if it works, workable.


Yes but i'm still working on a way to do that without restarting X, the problem when removing usbhid module it's that i lose calibration and recalibrating with xsetwacom doesn't resolve the issue, so i need an X server restart to have it working.

---

### Post by Favux on 2009-07-06
Hi Nimless,

> the problem when removing usbhid module it's that i lose calibration and recalibrating with xsetwacom doesn't resolve the issue, so i need an X server restart to have it working.
Ouch!

Wacomcpl depends on the xsetwacom commands.  But have you looked at it and seen if it works for you?  It will generate a .xinitrc containing all the xsetwacom settings.  See Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Then take a look at the script (by cyberfish) in Section 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  At least some ideas.

---

### Post by Nimless on 2009-07-06
> **Favux said:**
> Hi Nimless,


Ouch!

Wacomcpl depends on the xsetwacom commands.  But have you looked at it and seen if it works for you?  It will generate a .xinitrc containing all the xsetwacom settings.  See Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Then take a look at the script (by cyberfish) in Section 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  At least some ideas.

Yeah i tried that, doesn't work much for what i'm trying....anyway i think i'll have to wait for a patch for my problem with the touch taps...

---

### Post by gorg0th on 2009-07-07
> **Favux said:**
> Hi gorg0th,

Welcome to Ubuntu!

See exophobes' post #72 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=8](http://ubuntuforums.org/showthread.php?t=1038898&page=8)

Good luck!


Super sweet!!  Thanks a ton Favux!

---

### Post by Favux on 2009-07-07
Hi gorg0th,

Great!  You are welcome.  And you caught that in Jaunty that the name changed from alsa-base to alsa-base.conf.  Nice job.


Hi everyone,

So in summary antispin and Nimless are reporting Ayuthia's application of Rafi Rubin's patches to the 2.6.28 kernel work surprisingly well, apparently better than N-trig on 2.6.29, 2.6.30, and 2.6.31!

The xorg.conf also works for the Dell Latitude XT.  Although the ATI Radeon Xpress 1250 apparently "needs" the option "UseFBDev" "true" in the video "Device" Section.

Touch works great following a reboot, but after using the stylus a finger tap (left mouse click) begins to work intermittantly.  We don't know why and our attempts to fix it in xorg.conf haven't born fruit.

So why is this happening?  In the absence of many solid facts I feel free to speculate wildly and so I will.

1) It could be a problem with N-trig in the usb HID part of the kernel.  The code isn't quite releasing the stylus settings after it is used.  If so a patch is needed to fix it.

2) It could be a usb parsing problem.  Again it could be the N-trig part of the usb HID in the kernel.  Or it could be a problem with the wacom.ko (the linuxwacom usb kernel driver).  We could try compiling and substituting a 0.8.3-2 (or up) wacom.ko for the 0.8.2-2 wacom.ko.  We're already doing that for other usb tablets (gali98's HOW TO on post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)) and we know it doesn't break anything.  So worth trying.  Or again a patch could be needed.

3)  What I tend to favor is that it is a problem with the linuxwacom drivers not dealing correctly with the N-trig case.  What I mean is with the Wacom digitizer the stylus etc. is on another usb "by-path" than touch, not on the same one like the N-trig.  Or in HAL terms the "linux.sysfs_path" is the same, not two seperate ones like with the Wacom digitizer.  And the udi is the same, "noserial_if0" for both, not "noserial_if0" for the stylus and "noserial_if1" for touch.  So it really isn't a linuxwacom problem, the drivers need to be modified (oops, another patch) to deal with N-trig being on the same usb path.

If it is 3, what may be happening is that on boot touch works because none of the stylus settings from xorg.conf/.xinitrc have been invoked.  But once the stylus is used settings like Suppress, RawSample, ClickForce, PressCurve, Threshold, and TPCButton are applied, and they in turn  affect touch (since it is on the same usb path).  Now finger tap is intermittant.

If substituting a newer wacom.ko doesn't work it may be those parameters along with Capacity (if it applies to the N-trig digitizer at all) could be adjusted to give a "happy medium" where the stylus works pretty much how you want and finger taps work most of the time.  Which is of course why I favor 3.  But it means someone will have to spend a lot of time experimenting with the settings.

---

### Post by Favux on 2009-07-08
Hi everyone,

This is from Rafi Rubin replying (5-20-09) to Micheal Krelin who submitted some n-trig patches to LWP's linuxwacom-dev list:  [http://sourceforge.net/mailarchive/forum.php?thread_name=4A1475BE.8050303%40ugcs.caltech.edu&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=4A1475BE.8050303%40ugcs.caltech.edu&forum_name=linuxwacom-devel)
> Most of that patch....work around for quirks that I fixed in the hid-ntrig kernel driver found in 2.6.29 and later. Its actually a result of duplicate usages by the device. Just needed to set the flag to let the hid system know that the duplicates are ok.
More to the point re finger taps:
> Additionally, the N-Trig, at least with the firmware I'm using, sends the coordinates before it identifies which tool is sending them. That seems to interact poorly with the wacom driver. You're welcome to try out reordering the event packets to see if thing improve. Its been on my list of things to try for a while now.


---

### Post by Ayuthia on 2009-07-08
Sorry for not replying sooner.  I have been on holiday/vacation for the past week and have just returned.

I am also having the intermittent issue with the touch portion.  The possible reason why the 2.6.28-13-generic version might be working better than the 2.6.30 version would most likely be because of Rafi Rubin's patch that he submitted a little while back.  It is not part of the 2.6.30 kernel but I think that it might be in 2.6.31.  If I recall correctly, I added the patch before I left.  It made some fixes to the pen and stylus, but there is still the issue when you switch between the two.  The touch does seem to come back if you glide two fingers on the screen though.  I am not for sure why though.

---

### Post by Nimless on 2009-07-09
> **Ayuthia said:**
> Sorry for not replying sooner.  I have been on holiday/vacation for the past week and have just returned.

I am also having the intermittent issue with the touch portion.  The possible reason why the 2.6.28-13-generic version might be working better than the 2.6.30 version would most likely be because of Rafi Rubin's patch that he submitted a little while back.  It is not part of the 2.6.30 kernel but I think that it might be in 2.6.31.  If I recall correctly, I added the patch before I left.  It made some fixes to the pen and stylus, but there is still the issue when you switch between the two.  The touch does seem to come back if you glide two fingers on the screen though.  I am not for sure why though.

Thanks for  your great work Ayuthia,looking forward for updates!

I'm also looking to get my Latitude xt repaired since win 7 screwed up my n-trig firmware :-(

---

### Post by Nimless on 2009-07-10
Ok some news since i got my XT repaired,apparently Windows 7 messed up the device firmware and neither ubuntu or vista could see the device.

Got it repaired super fast with a brand one digitizer from Dell and got dual boot Vista/Ubuntu installed .

On the Vista firmware in /dev/input/by-path there are two event-mouse devices and to have it working you should use /dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse , notice the zero at the end.

On the Windows 7 firmware there is just one event-mouse device,and you should use that one.

Also the problem of the "finger taps" persist on both firmware after using stylus, but apparently as Ayuthia said sliding two fingers on the screen solves the problem o_O

On kernel 2.6.31-rc1 from the ubuntu kernel ppa the problem is persistent.

---

### Post by synace on 2009-07-10
Nimless, so for tx2, the vista firmware for n-trig gives 2 separate events for input? could this solve some of the issues i'm having with accuracy (it's 100% awesome until i use the stylus, then touch stinks).

---

### Post by Nimless on 2009-07-10
> **synace said:**
> Nimless, so for tx2, the vista firmware for n-trig gives 2 separate events for input? 

Yes the Vista firmware gives 2 separate events, i just use one of them in my xorg.conf,not sure what's the other for...

> 
 could this solve some of the issues i'm having with accuracy (it's 100% awesome until i use the stylus, then touch stinks).

Don't think so, i just sent an e-mail to Rafi asking him about this problem, Ayuthia figured out anyway that if you "slide" two fingers over the screen when the problem appears, it goes away.Works for me :-P

---

### Post by synace on 2009-07-10
as it stands, my touch is no longer good. at times (fresh reboot, before bringing stylus to screen), it was perfect! (slightest tap = mouse click).

now, i have to use 2fingers together and/or slightly touch&slide.

can we standardize the solution?

right now i'm using the patched kernel 64bit debs that were provided as well as the custom xorg.conf. i am using fglrx though.

maybe we should make a tx2z page :)

---

### Post by rafiyr on 2009-07-10
Hi, for what it's worth I currently have firmware version: 2.46.6.3.5

I've tried to recreate your problem, but so far have not seen it in normal operation.  Though I've just now seen my digitizer get stuck in pen only mode when I let a virtual machine capture it, and then gave it back to the host.

I do not have a vista installation handy, so it would take some effort to get the vista firmware loaded, but I'll do it, if it comes to that.  As it stands, I only have xp and win7 installed as virtual box images.  And yeah, with vb 3.0.0 (non-ose) I've been able to load firmwares.  Though the win7 firmware didn't actually work the one time I tried it.

I'd appreciate it if some of you would try a few things (independent tests).

1.  xsetwacom set touch touch off; xsetwacom touch touch on

2.  switch consoles away from and back to your xsession.

3.  hexdump /dev/usb/hiddev0 and /dev/usb/hiddev1.  When its working "normally" I have only ever seen input come from hiddev0.  But after windows in the vm broke it, I'm seeing input only from hiddev1.  I think the hiddev nodes copy the event stream before it gets to hid-ntrig, so it seems to continue to show a pretty raw stream even in X with the wacom driver consuming the /dev/input/event* node.

---

### Post by Nimless on 2009-07-10
> **rafiyr said:**
> 
1.  xsetwacom set touch touch off; xsetwacom touch touch on


Doesn't solve the problem for me

> 
2.  switch consoles away from and back to your xsession.


Neither this solves the problem

> 
3.  hexdump /dev/usb/hiddev0 and /dev/usb/hiddev1.  When its working "normally" I have only ever seen input come from hiddev0.  But after windows in the vm broke it, I'm seeing input only from hiddev1.  I think the hiddev nodes copy the event stream before it gets to hid-ntrig, so it seems to continue to show a pretty raw stream even in X with the wacom driver consuming the /dev/input/event* node.

Tried to hexdump /dev/usb/hiddev1 and no output in both cases.

Instead in /dev/usb/hiddev0 in both "faulty" and "normally" mode i get output, even missed "taps" produte output in hexdump but the cursor doesn't move.

---

### Post by synace on 2009-07-11
is there a way to manually issue the effect of the i8042.reset kernel option?

it may be that resetting the i8042 after the digitizer 'goes away' could be a brute force solution.

---

### Post by synace on 2009-07-11
> **Nimless said:**
> Doesn't solve the problem for me


Neither this solves the problem



Tried to hexdump /dev/usb/hiddev1 and no output in both cases.

Instead in /dev/usb/hiddev0 in both "faulty" and "normally" mode i get output, even missed "taps" produte output in hexdump but the cursor doesn't move.

same result here. /dev/usb/hiddev0 shows the slightest tap. but the cursor is not responsive. (nothing on /hiddev1 though)

i HAVE in the past (on a fresh boot) been able to trigger the cursor movement with the slightest tap. not any more. not sure what changed. (been trying a bit too much lately).

this is GOOD news right? if the dev is sending data, it's just not being read by the wacom driver right?

---

### Post by synace on 2009-07-11
> **rafiyr said:**
> Hi, for what it's worth I currently have firmware version: 2.46.6.3.5


how can i determine firmware version?

---

### Post by rafiyr on 2009-07-11
> same result here. /dev/usb/hiddev0 shows the slightest tap. but the cursor is not responsive. 

Can you reproduce the bug in a text console, no X, no wacom driver.

You can use lsinput to more quickly find the event device
[INDENT]lsinput |& grep -iB2 1b96

[/INDENT]Then either hexdump that input node, or use "input-event ##" to watch the device.

If that actually dumps touch events after touch stops working in X, then its the wacom driver.  Otherwise its probably the hid-ntrig driver.  Restarting X should refresh the wacom state.  And you should be able to rmmod hid_ntrig and modprobe it without killing X (works for me, usually).

---

### Post by Nimless on 2009-07-11
> **rafiyr said:**
> Can you reproduce the bug in a text console, no X, no wacom driver.

You can use lsinput to more quickly find the event device
[INDENT]lsinput |& grep -iB2 1b96

[/INDENT]Then either hexdump that input node, or use "input-event ##" to watch the device.

If that actually dumps touch events after touch stops working in X, then its the wacom driver.  Otherwise its probably the hid-ntrig driver.  Restarting X should refresh the wacom state.  And you should be able to rmmod hid_ntrig and modprobe it without killing X (works for me, usually).

Rmmod either wacom or usb_hid doesn't fix the problem, only removing usbhid and restarting X works.

Also this problem was persistent on kernel up to 2.6.31 until i applied your patch [http://ofb.net/~rafi/0001-ntrig-tool-separation-and-pen-usages.patch](http://ofb.net/~rafi/0001-ntrig-tool-separation-and-pen-usages.patch).

That patch fixed it, but it comes back when using stylus. So you probably dealed correctly with this problem with this patch, just a little bug remaining. :-P

---

### Post by synace on 2009-07-11
after 
rmmod hid_ntrig
modprobe hid_ntrig

touch doesn't work until i use the stylus.

i'm not sure what happened. i'll probably start over with the patched debs, or build the kernel myself. i'd love to be able to help out to get this working at a quality level so that it's stable when karmic comes around. anythign i can do to help, i'm available.

i have the tx2z.


evtest.c (game-sat.com/~brian/Howtos/evtest.c  compiled w/ gcc):
```

sudo ./evtest /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x1b96 product 0x1 version 0x110
Input device name: "HID 1b96:0001"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 256 (Btn0)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
    Event code 331 (Stylus)
    Event code 333 (Tool Doubletap)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value   7218
      Min        0
      Max     9600
    Event code 1 (Y)
      Value   4669
      Min        0
      Max     7200
    Event code 24 (Pressure)
      Value      0
      Min        0
      Max      256
    Event code 48 (?)
      Value      0
      Min        0
      Max        1
    Event code 49 (?)
      Value      0
      Min        0
      Max        1
    Event code 52 (?)
      Value      0
      Min        0
      Max        1
    Event code 53 (?)
      Value      0
      Min        0
      Max     9600
    Event code 54 (?)
      Value      0
      Min        0
      Max     7200
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)

```

no response on touch or stylus.

a finger tap (light enough to NOT cause cursor movement) with hexdump:
```
sudo hexdump /dev/usb/hiddev0
0000000 0032 000d 0001 0000 0042 000d 0001 0000
0000010 0047 000d 0001 0000 0030 0001 1a6a 0000
0000020 0031 0001 081c 0000 0048 000d 0000 0000
0000030 0049 000d 0000 0000 0032 000d 0001 0000
0000040 0042 000d 0001 0000 0047 000d 0001 0000
0000050 0030 0001 1a6a 0000 0031 0001 081c 0000
0000060 0048 000d 0000 0000 0049 000d 0000 0000
0000070 0032 000d 0001 0000 0042 000d 0001 0000
0000080 0047 000d 0001 0000 0030 0001 1a6a 0000
0000090 0031 0001 081c 0000 0048 000d 0000 0000
00000a0 0049 000d 0000 0000 0032 000d 0001 0000
00000b0 0042 000d 0001 0000 0047 000d 0001 0000
00000c0 0030 0001 1a6a 0000 0031 0001 081c 0000
00000d0 0048 000d 0000 0000 0049 000d 0000 0000
00000e0 0032 000d 0001 0000 0042 000d 0001 0000
00000f0 0047 000d 0001 0000 0030 0001 1a6a 0000
0000100 0031 0001 081c 0000 0048 000d 0000 0000
0000110 0049 000d 0000 0000 0032 000d 0000 0000
0000120 0042 000d 0000 0000 0047 000d 0000 0000
0000130 0030 0001 1a6a 0000 0031 0001 081c 0000
0000140 0048 000d 0000 0000 0049 000d 0000 0000
^C

```
data was sent by the hid, but no cursor movement.

/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse -> ../event8
```

input-events 8
/dev/input/event8
   bustype : BUS_USB
   vendor  : 0x1b96
   product : 0x1
   version : 272
   name    : "HID 1b96:0001"
   phys    : "usb-0000:00:14.5-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

waiting for events
timeout, quitting

```
nothing.. touch, stylus or stylus button.

same for event 9

---

### Post by Ayuthia on 2009-07-12
> **Nimless said:**
> Ok some news since i got my XT repaired,apparently Windows 7 messed up the device firmware and neither ubuntu or vista could see the device.

Got it repaired super fast with a brand one digitizer from Dell and got dual boot Vista/Ubuntu installed .

On the Vista firmware in /dev/input/by-path there are two event-mouse devices and to have it working you should use /dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse , notice the zero at the end.

On the Windows 7 firmware there is just one event-mouse device,and you should use that one.

Also the problem of the "finger taps" persist on both firmware after using stylus, but apparently as Ayuthia said sliding two fingers on the screen solves the problem o_O

On kernel 2.6.31-rc1 from the ubuntu kernel ppa the problem is persistent.

I think that I have found where the code needs to be changed to get the stylus to touch working better.  I am currently using my changes in Gentoo and the touch is now responding immediately after I use the stylus.

I will try to create post a kernel update and supply the patches on Monday.

---

### Post by Ayuthia on 2009-07-12
> **Nimless said:**
> Rmmod either wacom or usb_hid doesn't fix the problem, only removing usbhid and restarting X works.

Also this problem was persistent on kernel up to 2.6.31 until i applied your patch [http://ofb.net/~rafi/0001-ntrig-tool-separation-and-pen-usages.patch](http://ofb.net/~rafi/0001-ntrig-tool-separation-and-pen-usages.patch).

That patch fixed it, but it comes back when using stylus. So you probably dealed correctly with this problem with this patch, just a little bug remaining. :-P

If you look at that patch and try to find this line:
```
if(nd->pen_active && nd->finger_active) {
```
There should be two instances of it.  Change the && to ||:
```
if(nd->pen_active || nd->finger_active) {
```
That should get it to work.

---

### Post by Ayuthia on 2009-07-13
> **synace said:**
> after 
rmmod hid_ntrig
modprobe hid_ntrig

touch doesn't work until i use the stylus.

i'm not sure what happened. i'll probably start over with the patched debs, or build the kernel myself. i'd love to be able to help out to get this working at a quality level so that it's stable when karmic comes around. anythign i can do to help, i'm available.

i have the tx2z.


This almost sounds like it is missing Rafi Rubin's most recent patch.  I recall running into this issue before. 

I was about to update the patched debs with a slight change on the newest patch that was mentioned in my previous posts, but I found that the current kernel is at 2.6.28-13.45 and I just built the changes over 2.6.28-13.44.  I will try to get the updates out sometime on Monday.

---

### Post by Nimless on 2009-07-13
Cool :-D

Going to try it out ! Waiting for your kernel debs when you have time...

Thanks!

---

### Post by Ayuthia on 2009-07-13
> **Nimless said:**
> Cool :-D

Going to try it out ! Waiting for your kernel debs when you have time...

Thanks!

I am still testing it.  I have found that that the touch seems to respond better but if you try using two fingers on the screen, the tap that is associated to it seems to fail.  Of course, it starts working again if you use the stylus once.  

rafiyr, any thoughts on this?  From what I am understanding, that line is only triggered if a single touch is made.  If it is multitouch, it will skip it.  I am going to comment out the check for the multitouch just to see if it responds differently, but I am not for sure if it can be a permanent change since multitouch is most likely going to have different rules.

---

### Post by synace on 2009-07-13
Ayuthia,

I'd like to evaluate the driver as well. Can you point me in the right directions?

Also, I'd like to get the bezel buttons working, so I'll probably need to patch HP-WMI as well.

Ideally, I'd like to see all of the above functional & working in Karmic 9.10.

Did you backport the patches from Stephanie (not sure on the last name) regarding multitouch? I guess everyone's working on the latest kernel to build/test, but ideally, I'd like to backport to Jaunty in the end.

---

### Post by Ayuthia on 2009-07-13
> **synace said:**
> Ayuthia,

I'd like to evaluate the driver as well. Can you point me in the right directions?

Also, I'd like to get the bezel buttons working, so I'll probably need to patch HP-WMI as well.

Ideally, I'd like to see all of the above functional & working in Karmic 9.10.

Did you backport the patches from Stephanie (not sure on the last name) regarding multitouch? I guess everyone's working on the latest kernel to build/test, but ideally, I'd like to backport to Jaunty in the end.

All the patches that I have posted are backported.  I am pretty sure that I have all off them at this time.  I have made one change in hid-ntrig.c (found in linux-2.6.28/drivers/hid/hid-ntrig.c) that differs from what I posted.  It seems to allow the cursor to move with the touch, but the current problem is that once multitouch is enabled, the tap capability is disabled until the stylus is used again.

If this does not help get you started, please let me know.  I am not for sure if I fully understand what part you are wanting to look at.  I think that the issue is with the event handling in hid-ntrig.c where multitouch is enabled.  For some reason, I can't quite figure out how to get the tap to react properly.

---

### Post by Ayuthia on 2009-07-15
Just an update.  I am able to get the touch working fine in Gentoo under the 2.6.30 kernel.  I did have to make some changes to hid-ntrig.c to make it work.  However, for some reason, I cannot get it to work correctly in Ubuntu so I am trying to track down where things differ.

As soon as I have it stable in Ubuntu, I will release the .deb and patches for it.

The current issue (with the patches applied) in Ubuntu is that the touch is always responding unless you use two fingers once.  After that, it works fine until you use the stylus.

---

### Post by Ayuthia on 2009-07-16
Here is the link to the patches and the debs:
[http://ubuntuforums.org/showpost.php?p=7625055&postcount=186](http://ubuntuforums.org/showpost.php?p=7625055&postcount=186)

This will get the touch to respond to the finger better.

At this point, I have not figured out how to get the multitouch to emit an event so the patch in the above link might not be final.  It looks like the driver sends a touch and pen signal out when multitouch occurs instead of the event code that I am expecting (without my patch).  So if I can't find a solution to the multitouch, I might have to change the patch so that it triggers a multitouch response instead of what it is currently doing with my changes.

---

### Post by Nimless on 2009-07-21
> **Ayuthia said:**
> Here is the link to the patches and the debs:
[http://ubuntuforums.org/showpost.php?p=7625055&postcount=186](http://ubuntuforums.org/showpost.php?p=7625055&postcount=186)

This will get the touch to respond to the finger better.

At this point, I have not figured out how to get the multitouch to emit an event so the patch in the above link might not be final.  It looks like the driver sends a touch and pen signal out when multitouch occurs instead of the event code that I am expecting (without my patch).  So if I can't find a solution to the multitouch, I might have to change the patch so that it triggers a multitouch response instead of what it is currently doing with my changes.

Hi!

Thanks Ayuthia,been on vacation for a week, any news about our lovely n-trig touchscreen?:-D

---

### Post by Ayuthia on 2009-07-21
> **Nimless said:**
> Hi!

Thanks Ayuthia,been on vacation for a week, any news about our lovely n-trig touchscreen?:-D

At this point, the touch seems to be working with the new patch.  It does seem that the changes that I made should not mess with the multitouch because the information seems to be reflected in other events also.  The touch does not turn off when the stylus is in use so you still need to turn that off manually.  I am still looking into what can be done to report the multitouch.  There is an event code that is supposed to be triggered when multitouch is active, but I am not getting it.  I can tell when it comes though but I want to see what Rafi Rubin has to say about the multitouch event before I try anything.  

The other part of this is that when we figure out the multitouch info, we will most likely need to either create a new x11 driver for the NTrig or else we need to fork from the linuxwacom because the changes being made this time could affect the Wacom devices.

---

### Post by willdocsx on 2009-08-22
Will ntrig digitizer touchscreen, and screen rotation be included in the final Karmic Koala release? So far I haven't been able to configure the screen rotation and multi-touch in Jaunty. Anyone have a guide or link ready for these? Ayuthia seems to be closest with the mult-touch but where are the actual scripts? Thanks

---

### Post by Favux on 2009-08-22
Hi willdocsx,

Welcome to Ubuntu forums!

So far there isn't multi-touch in Jaunty.  To get your stylus and touch working in Jaunty see Appendix 2 here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  The link for auto-magic rotation is also there, further back up in the Rotation HOW TO.

Ayuthia was closing in on multi-touch but when he investigated Win 7 there were some changes as to where things were located that set him back.  Right now he's investigating Karmic.

---

### Post by wolfgangpauli on 2009-09-07
Hey,

I am trying to get multitouch to work on my hp tx2. Any ideas where to start? I seems like Ayuthia is working on this. Is there a specific thread to look at for example? E.g. one pointing at recent patches? This one? [http://ubuntuforums.org/showpost.php?p=7625055&postcount=186](http://ubuntuforums.org/showpost.php?p=7625055&postcount=186)

Thanks,

Wolfgang

---

### Post by Ayuthia on 2009-09-07
> **wolfgangpauli said:**
> Hey,

I am trying to get multitouch to work on my hp tx2. Any ideas where to start? I seems like Ayuthia is working on this. Is there a specific thread to look at for example? E.g. one pointing at recent patches? This one? [http://ubuntuforums.org/showpost.php?p=7625055&postcount=186](http://ubuntuforums.org/showpost.php?p=7625055&postcount=186)

Thanks,

Wolfgang

At this point, the place to start is with /usr/src/linux/drivers/hid/hid-ntrig.c from the kernel source.  It seems possible to get the two finger touch to work with the Vista firmware, but with the Windows 7 firmware the current source is not able to find the multitouch data.  When you place an additional finger on the screen, it registers that the second finger is there and then quits sending data.

If you just want to study the hid-ntrig.c source and not download the entire kernel source, it can be found in the ntrig-v3.tar.bz2 file from the post that you referenced.  When you extract that package, you can find it under ntrig/drivers/hid/hid-ntrig.c.  

The hid-ntrig.c source reads the data that is coming from the touchscreen and it sends events down to X via linuxwacom.  So if you are able to figure out how the multitouch works, you can then create the events and send it down to linuxwacom.

---

### Post by wolfgangpauli on 2009-09-07
Thanks. Not sure whether I should start a different thread on this, just let me know. I got the kernel source, the n-trig driver tar ball. compiling etc all worked great. However ....

How can I use the vista firmware? I am assuming that I am using the win 7 firmware, because xinput says (proximity: out and buttons: 1-up) whenever there is a second finger on the screen.

Why does wacdump not work? I tried all sorts of devices (mainly with the one in xorg.conf) and it either does not give any output, or fails with WacomOpenTablet: Invalid argument.

All I really need is that if the screen gets touched in two different places at the same time, I want to know the coordinates. For my prof i am working on this "game" in matlab where subjects have to "pick-up" objects that appear at random locations on the screen. Most of the time it is fine, because only one object is touched at a time, but whenever two fingers are on the screen at the same time, it does something pseudoramdom (e.g. set x=0, and y=0)

Thanks for any help!!!

---

### Post by Ayuthia on 2009-09-08
> **wolfgangpauli said:**
> How can I use the vista firmware? I am assuming that I am using the win 7 firmware, because xinput says (proximity: out and buttons: 1-up) whenever there is a second finger on the screen.xinput will not provide the information that you are looking for because hid-ntrig is currently not sending the information over to linuxwacom so X does not know about it.  If you have not installed Windows 7 and currently not using Windows 7 then you are most likely using the Vista firmware.  The best place would be to retrieve the information from /dev/hidraw0 (for Vista) or /dev/hidraw1 (for Windows 7).

> Why does wacdump not work? I tried all sorts of devices (mainly with the one in xorg.conf) and it either does not give any output, or fails with WacomOpenTablet: Invalid argument.I have not tried it, but according to the help, it looks like the code is looking for specific wacom devices so the N-Trig device has not been coded for it.

> All I really need is that if the screen gets touched in two different places at the same time, I want to know the coordinates. For my prof i am working on this "game" in matlab where subjects have to "pick-up" objects that appear at random locations on the screen. Most of the time it is fine, because only one object is touched at a time, but whenever two fingers are on the screen at the same time, it does something pseudoramdom (e.g. set x=0, and y=0)This is a more difficult question to answer.  Part of it is because the linuxwacom driver does not have all the information needed to react to it correctly.  From what I have learned from the Vista firmware, the extra finger is reported by the width and height fields from hid-ntrig.  The width is the X distance from the other finger and the height is the Y distance from the other finger.

Please let me know what language you plan to analyze the data.  If you know python, I can provide an application that might help you figure out where to get your information.

---

### Post by wolfgangpauli on 2009-09-08
Great, thanks. I think I saw that in the n-trig driver. I would just have to do some math to calculate the 2nd finger location based on the x,y distance from the first finger. Unfortunately, I have to write the program in Matlab (for precise timing), but I know python better anyway, so that script you are talking about might be really useful. 

- wolfgangpauli

---

### Post by Ayuthia on 2009-09-08
> **wolfgangpauli said:**
> Great, thanks. I think I saw that in the n-trig driver. I would just have to do some math to calculate the 2nd finger location based on the x,y distance from the first finger. Unfortunately, I have to write the program in Matlab (for precise timing), but I know python better anyway, so that script you are talking about might be really useful. 

- wolfgangpauli

Attached is an app called touch.py.  It is currently pointing to /dev/hidraw0 so if you are not getting any data when you touch the screen you might need to switch it to /dev/hidraw1.  To run the application, you will need sudo privileges because it needs to access /dev (which is protected):
```
sudo python touch.py
```

In order to attach it here, it is a tar.bz2 file.  If you don't know how to extract it:
```
tar -xvjf touch.tar.bz2
```

If you have any questions, feel free to PM me on it.

---

### Post by markginter24 on 2009-09-26
Ayuthia - I tried your python script and found out that my Touchsmart screen is receiving 'input' data (Karmic Koala 2.6.31-11 32bit) but it's not translating to X.  What wacom-tools / xinput-wacom packages do I need to get this working in Karmic.  I followed the directions and Jaunty works - but I really want to get this going in Karmic.

---

### Post by Ayuthia on 2009-09-26
> **markginter24 said:**
> Ayuthia - I tried your python script and found out that my Touchsmart screen is receiving 'input' data (Karmic Koala 2.6.31-11 32bit) but it's not translating to X.  What wacom-tools / xinput-wacom packages do I need to get this working in Karmic.  I followed the directions and Jaunty works - but I really want to get this going in Karmic.

Right now, the documentation for updating the wacom module has not been written up for Karmic.  You will still need to patch the driver but from what we have seen, you will need to download the kernel source (sudo apt-get source linux-image-`uname -r`) and copy drivers/hid/hid-ids.h file over to /lib/modules/`uname -r`/builds/drivers/hid/hid-ids.h so that it will compile.

I hope that helps.  I will try to get something written up, but right now I am out of town so I will try to get it out soon.

EDIT:
Here is a [link]("http://linuxfans.keryxproject.org/?page_id=44") to a guide in getting it installed.

---

### Post by wolfgangpauli on 2009-09-29
Hi, 

Thanks for that python script, it was really helpful (after coming back from a vacation). I was able to write something similar in matlab, please let me know if you are interested in that. Also, I see how the location of the second finger is reported in terms of absolute distance from the first one, which is somewhat of a problem because I can not tell what the exact location is. I.e. is it left or right of the first one, above or below? I was hoping that the fields A-E wouthe ld tell me more, but had no luck so far. I sent an email to n-trig, maybe they know (and maybe they will share their knowledge). Does anybody know what those values represent?

Wolfgang

---

### Post by Ayuthia on 2009-09-29
> **wolfgangpauli said:**
> Hi, 

Thanks for that python script, it was really helpful (after coming back from a vacation). I was able to write something similar in matlab, please let me know if you are interested in that. Also, I see how the location of the second finger is reported in terms of absolute distance from the first one, which is somewhat of a problem because I can not tell what the exact location is. I.e. is it left or right of the first one, above or below? I was hoping that the fields A-E wouthe ld tell me more, but had no luck so far. I sent an email to n-trig, maybe they know (and maybe they will share their knowledge). Does anybody know what those values represent?

Wolfgang

I would love to see the code that you wrote in matlab.  I always find it interesting to see code done in different languages.

As for the second finger, I have not figured out if there is any way to figure that out or not.  It almost seems that the Vista firmware might have been geared towards handling gestures and not an actual coordinate.  I could be wrong about that though.

---

### Post by wolfgangpauli on 2009-09-29
too bad, maybe I'll here from the n-trig people. it is not a serious issue though. Here is my matlab version of your python script.

```
f = fopen('/dev/hidraw0');

while (1) % run forever (until ctrl+c)
    input = fread(f,22,'*ushort');

    if input(7) == 1794
        fprintf('Touch\n')
        fprintf('width: %d\n', input(10))
        fprintf('height: %d\n', input(11))
    elseif input(7) == 257
        fprintf('Stylus--Hoover\n')
        fprintf('Pressure: %d\n', input(10))
    elseif input(7) == 769
        fprintf('Stylus--On-screen\n')
        fprintf('Pressure: %d\n', input(10))
    elseif input(7) == 770
        fprintf('Two-finger\n')
        fprintf('width: %d\n', input(10))
        fprintf('height: %d\n', input(11))
    elseif input(7) == 2
        fprintf('Double-tap\n')
    elseif input(7) == 1
        fprintf('Stylus--Hover off-screen\n')
    elseif input(7) == 1793
        fprintf('Stylus--Button click\n')
    else
        fprintf('unknown\n')
    end

    fprintf('X: %d\n', input(8))
    fprintf('Y: %d\n', input(9))

    pause(.01); % pause for one millisecond
end

fclose(f);
```

---

