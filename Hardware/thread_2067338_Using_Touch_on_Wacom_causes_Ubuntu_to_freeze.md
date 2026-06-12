---
title: "Using Touch on Wacom causes Ubuntu to freeze"
date: 2012-10-06
forum: Hardware
---

### Post by BcRich on 2012-10-06
Hello there,
I'm using Kubuntu 12.04 (but also have the same problem in Ubuntu) with a Wacom Intous 5 Pen and Touch Medium. Occasionally when I'm using the touch feature instead of a mouse Ubuntu just freezes. Then I have to reset my computer, which is a bit hectic cause I lose whatever I haven't saved prior to it freezing. I did not have this problem prior to installing the device and nor have I experienced this problem while using the pen (only experience the problem while using touch). Any assistance would be greatly appreciated.
Thanks.

---

### Post by Favux on 2012-10-06
Hi BcRich,

I think you may be running into this bug:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=ac17300d842f2842eff3a2b2aa3dbac7ebf88a2b](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=ac17300d842f2842eff3a2b2aa3dbac7ebf88a2b)  This fix was committed just before xf86-input-wacom-0.17.0 came out.  Another Intuos5 fix (jumping cursor) was added afterwards so you might want to clone the git repository.

---

### Post by BcRich on 2012-10-06
Hi Favux,
Thanks for your help :)
I'm not quite sure what I need to do with the link u included in your last post, although the part about "hang the box" seems like something I might be experiencing.
is there a driver or something i can download and install to replace the one i'm currently using, or have i totally got it all wrong? :confused:

---

### Post by Favux on 2012-10-06
> is there a driver or something i can download and install to replace the one i'm currently using, or have i totally got it all wrong? 
Nope, you have it correct.  :)

You need to download and compile the xf86-input-wacom tar or clone its git repository and compile that.  Instructions are on the [Linux Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") or the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  With either one you have to do an extra step and patch the xf86-input-wacom source code with the [frankenserver patch]("http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034") so it will work on 12.04's hybrid X Server.

Since we are no longer allowed to update our HOW TOs you have to put them together and update the tar's number yourself.  You should end up with instructions that look like [these instructions]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&sid=5cda13f9f66cbaa69393b634d3d6396e").

---

### Post by BcRich on 2012-10-07
Hi Favux,
Thanks a million that info should keep me busy for a while :)
although I'm not 100% sure if it's the same problem I'm having as in the patching post it says
>  it will cause your system to not start if you have your BambooPT plugged in, or to crash/freeze if you plug it in after it has started. 
This is not really what happens with my system but I'm also not using a BambooPT could this make a difference? My system starts up fine with the tablet already plugged in and I can usually use everything perfectly for quite a while. But sporadically when I'm specifically using the touch feature the entire system will freeze. This problem hasn't occurred when I use the pen and has never prevented me from booting into my system (with the tablet plugged or not).
Do you think it might be the same issue? I'll probably try patching it anyway this evening unless u think it might not be the same problem.
Thanks again for your help, I'm so very grateful!

---

### Post by Favux on 2012-10-07
Hi BcRich,

The frankenserver patch is for a separate issue.  Precise uses a hybrid X Server (1.11/1.12) and the xf86-input-wacom you download or clone isn't compatible with its ABI (application binary interface).  The xf86-input-wacom that is installed by default is already patched by Ubuntu.  That's why you don't have a problem.  But if you compile a new one you need to patch it too, like Ubuntu did.  Otherwise when you plug the tablet in your computer will freeze.

---

### Post by BcRich on 2012-10-07
hmm, so it seems like my issue might not be related to an older version of xf86-input-wacom installed without the patch, is that what you are saying?
Is there a way to find out what version of xf86-input-wacom I have installed, I looked for this file in Synaptic but could not find it?
I used to use a genius pensketch on this same system, but I'm not sure how to remove it's configuration files or if this will even help. Do you think there is any possibility that this might be causing a conflict?
Thanks Favux :)

---

### Post by Favux on 2012-10-07
> hmm, so it seems like my issue might not be related to an older version of xf86-input-wacom installed without the patch, is that what you are saying?
Nope.  You are conflating two separate issues.  One is the Intuos5 bug.  To fix that you need a xf86-input-wacom newer than the default one that comes with Precise, i.e. 0.17.0.  The other is the hybrid X Server issue.  That requires the frankenserver patch for any xf86-input-wacom used in Precise and affects all tablets using the Wacom X driver (xf86-input-wacom or xserver-xorg-input-wacom as Ubuntu calls it).
> Is there a way to find out what version of xf86-input-wacom I have installed, I looked for this file in Synaptic but could not find it?
Yes enter in a terminal:
```
xsetwacom -V
```
or search for xserver-xorg-input-wacom in the Software Center or the Synaptic Package Manager.
> I used to use a genius pensketch on this same system, but I'm not sure how to remove it's configuration files or if this will even help. Do you think there is any possibility that this might be causing a conflict?
There shouldn't be a conflict unless maybe you made a custom .conf file in xorg.conf.d that has some sort of error in it.

---

### Post by BcRich on 2012-10-07
ok now I get it :)
Thanks Favux, that makes perfect sense now!
I do indeed have the old version of xf86-input-wacom after running the command you specified it show I have version 0.14.0
So I'll update, patch and post my results back here.
> There shouldn't be a conflict unless maybe you made a custom .conf file in xorg.conf.d that has some sort of error in it.
There is a custom .conf file in xorg.conf.d which is called 52-tablet-on-evdev.conf but I don't think it has any errors in it here's what it looks like.
```
Section "InputClass"
        Identifier "Graphics tablet mouse"
        MatchIsPointer "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "Grahics tablet pen"
        MatchIsTablet "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "ButtonMapping" "1 2 3"
EndSection

```
This file was made for my genius pensketch here's a discussion about it [http://ubuntuforums.org/showthread.php?t=1989079](http://ubuntuforums.org/showthread.php?t=1989079)

---

### Post by Favux on 2012-10-07
Good, now we're on the same page.  :)

Your 52-tablet-on-evdev.conf won't affect the Intuos5.  The key thing is the matches.  Even if MatchIsTablet picked up the Intuos5, MatchProduct "PF1209" would exclude it.

---

### Post by BcRich on 2012-10-08
YAY! I updated the xf86-input-wacom to 0.17.0 and patched it with the frankenserver patch following the instructions here [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&sid=5cda13f9f66cbaa69393b634d3d6396e](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&sid=5cda13f9f66cbaa69393b634d3d6396e) (nice post by the way Favux). And so far no freezing!!!!
I'll need to test it more to confirm that my problem is totally fixed, but so far everything seems fine :)
Once again Favux you're the supreme grand master of all things Tablet, Wacom and Stylus on these forums :KS:KS:KS:KS:KS
marking this thread as SOLVED! WOOHOO!

---

