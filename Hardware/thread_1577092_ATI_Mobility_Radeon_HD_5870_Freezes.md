---
title: "ATI Mobility Radeon HD 5870 Freezes"
date: 2010-09-18
forum: Hardware
---

### Post by bsautner on 2010-09-18
My super fast ASUS g73j laptop screams with ubuntu - cold boots < 3 seconds. Ubuntu 10 x64 installed perfectly. 

My only problem is that when the screen saver kicks on or I try to remote in using VNC it locks up. 

I've tried enabling third party drivers and using the ATI Catalyst control center with no luck. I just thought I'd start a thread on the topic.

---

### Post by chargersfan420 on 2010-10-07
I seem to be in the same boat.  ATI Mobility Radeon HD 5870 in an Alienware M17x.  In power management, I have it set to "blank screen" when lid closes, and this is enough to cause a lockup.  It would have been nice if they left in the "do nothing" option.

When it locks up, the screen is black but it is lit, so it is not completely off, and both the keyboard and mouse go completely dead.

bsautner, were you able to get anywhere with this problem?  Does your keyboard and mouse go dead too?

---

### Post by bsautner on 2010-10-07
Hi chargersfan420,

So far i've disabled the screen saver, and instead of trying to get VNC to work i'm remoting into my laptop using this command line (which rocks btw). 

ssh -X -C -c blowfish username@machinename "gnome-panel" 

that spawns a gnome session on the target machine over ssh

I dock this laptop into my home entertainment center AVR so my tv is the second monitor. I was getting choppy video playback until i set the monitor resolution to 1024x768, which actually looks good on the TV.  

Sorry, not real solutions except these work arounds. I'm hoping unbutu 10.10 will automagically help or a better driver will come out.

---

### Post by chargersfan420 on 2010-10-08
Good news!  It is fixed.  Here is how I did it:

Note that this fix is pretty Alienware specific, so YMMV.

Booting into Win7, I updated the BIOS but that didn't seem to help.  Next, I updated the vBIOS on the graphics card by downloading a utility from [[COLOR="Red"]Dell's website[/COLOR]]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&ServiceTag=&SystemID=ALW_M17XR2&os=W764&osl=EN").  This utility may or may not check if it is running on a Dell/Alienware, I'm not really sure, but it did check my driver version installed in Win 7 and made me update it before it would do anything.  Then it let me either prepare a flash drive (2 GB or less) or create an ISO image to boot from in order to do the flashing.  I went with the ISO and burned it to a CD.  The ISO is only 8.4 MB.

So, for people not on Alienware, I'd suggest either searching for this update (it claims to be firmware version A01, if that helps) either on the ATI/AMD website, or on your laptop manufacturer's website.

bsautner, if you're unable to get a hold of the ISO, I could create a torrent and arrange some time to seed it for you, if you'd like.

Also, special thanks to the poster of another thread that I can't seem to find again that posted the fix.  And of course, flashing the BIOS/vBIOS is dangerous, attempt at your own risk, blah blah blah.

---

