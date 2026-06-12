---
title: "Skype on Thinkpad T43, 9.04"
date: 2009-07-06
forum: Hardware
---

### Post by chloraldo on 2009-07-06
Hi all

Has anyone got Skype working properly on a Thinkpad T43 (T43p)?

It runs and I have sound, but the quality it really bad and there are interruptions making it unusable. The same Laptop (dual boot) has Win XP and it works perfectly so I guess it can't be a hardware issue.

Would really like to be able to use Skype, because that's the main reason why I still use Win.

Thanks for your help

---

### Post by chloraldo on 2009-07-22
any help here? please

---

### Post by Jinnie on 2009-07-24
It works absolutely nice on my T43, after I followed these instructions:
        * killall pulseaudio
        * sudo apt-get remove pulseaudio
        * sudo apt-get install esound
        * sudo rm /etc/X11/Xsession.d/70pulseaudio
        * Reboot system and use the default sound setting in skype.
from this thread:
[http://ubuntuforums.org/showthread.php?t=1127056&page=5](http://ubuntuforums.org/showthread.php?t=1127056&page=5)

But I had no audio before it.

Now the sound quality is real fine.

I also did some of the things mentioned here, before, so it may have also influenced it:
[http://ubuntuforums.org/showpost.php?p=1423407&postcount=16](http://ubuntuforums.org/showpost.php?p=1423407&postcount=16)

GL!

---

### Post by ZaHACKieL on 2009-07-24
Well, Skype is the only program that gives me problems with Ubuntu. My webcam looks funny, like bigger or something like that and If someone has the webcam on and then I send mine, the other webcam freezes, so, I first have to send my webcam and then ask my contact to send. That way, the other webcam works but my local image disappears but I don't care too much about that.

Anyway, that doesn't answer your question, I just wanted to know if you also experience that issue.

About the sounds and interruptions, sometimes I have that stuff, it really depends on where I'm calling to. I haven't tried on windows. Have you tried in both systems with the same contact?

ZL

---

### Post by chloraldo on 2009-08-03
> **Jinnie said:**
> It works absolutely nice on my T43, after I followed these instructions:

snipped



Thanks for that. The sound quality is very good now.

There is still one (big) problem (that I don't have in Windows): Every few minutes a get an interruption of up to 7 or 8 seconds. Both sides don't hear each other anymore for that time.

Any ideas for troubleshooting?

---

### Post by tgalati4 on 2009-08-03
I have skype working under Linux Mint 7 Gloria (based on Jaunty) on a t43p.  I'm not sure what tweaks were performed by those Mint guys, but I have skype working with pulseaudio.  I can listen to music with headphones and talk at the same time.  Skype audio only comes out of one ear, but I haven't tracked the issue yet. (Helps to have the headphones plugged in all the way!) Quality is acceptable.  Similar to several other machines running Ubuntu.

For your interruptions, in a terminal:

sudo apt-get install htop
htop

Now run skype and watch the processor.  Skype uses quite a bit of processing power.  In powersave mode (800 MHz in my case) skype uses ~50% of the CPU.  On my nokia n800 (400 MHz Arm processor) it uses ~65%.  Not much room for browsing or doing anything else.  Use ondemand or performance power mode and see if you get better performance.  If you have other things going on, like beagle/tracker indexing, then that could cause interruptions.

If you are running wireless (t43 laptop), they you could have a wireless issue that is causing problems.  The Intel wireless drivers are OK, but the windows drivers may have some extra tweaks to get better wireless connectivity.  I'm guessing, because I rarely use windows.

Try listening to streamed internet radio or locally-streamed media and see if you get interruptions with simple, one-way media streams.  If so, then you might need to reseat your wireless card.

Check dmesg for errors:

dmesg | more

(spacebar to page forward, q to quit)

---

### Post by Renegade Lisp on 2009-09-18
I've got a T43 too, and I found the solution to the problem of the recurring interruptions. It's a network / WiFi problem. See my blog post about it: [http://bit.ly/YyKfH](http://bit.ly/YyKfH)

---

