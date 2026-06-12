---
title: "Where have my multimedia keys gone?"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by new2linux9 on 2005-12-18
Please can anyone help me,  I have spent the last few days researching but to no avail.  When I first installed ubuntu on my ASUS M5200N all my multimedia keys were working.:D   However, after either getting my webcam or installing skype or some other program some of them no longer function!:confused: This was my origional post:

>  new2linux9
1 Cup of Ubuntu
 
Status: (Online)
Posts: 17
Join Date: Nov 2005
Ubuntu Breezy 5.10 User
	
Default Re: Skype deb Repacked for Hoary and Breezy - 6 Days Ago
Ahh! Didn't realise that this wasn't a good idea or why. I was just desperate to get skype working as it's what I use to communicate with my family. I live in China, they live in England and Italy.

I noticed that I now no longer have hot key control for my volume: Fn + F10 (mute), Fn + F11 (V-), Fn + F12 (V+), email: Fn + F3 and internet: Fn + F4, which I did before. However my hotkeys for brightness Fn + F5 & Fn + F6 and LCD on/off, switch monitor still work. I'm not sure if the hotkey to disable my touchpad, Fn + F9 was working before or not as I didn't use it. Could this be as a result of what I have done here or what I did to get my webcam working:

Quote:
arnieboy
Ubuntu Apprentice Roasters

arnieboy's Avatar

StatusOffline)
Posts: 1,591
Join Date: Mar 2005
Location: Pennsylvania, US
Ubuntu Breezy 5.10 User
Send a message via AIM to arnieboySend a message via Yahoo to arnieboy

Default General - HOWTO: Making ICM532 chipset based webcams work on breezy - 10-14-2005
Some of you probably might have noticed ICM532 chipset based webcams freezing on breezy (for a comprehensive list refer to: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) ) when u turn on gnomemeeting or camorama. Herez the fix for that:
FOLLOW ALL THE STEPS! DONT TAKE SHORTCUTS IF U DONT KNOW WHAT U ARE DOING
U need to do the following first of all:
Code:

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4

now do the following:
Code:

sudo passwd root

and set the root password if u already dont have one
now do the following
Code:

su CC=gcc-3.4 export CC exit CC=gcc-3.4 export CC wget [http://mxhaard.free.fr/spca50x/Downl...0050906.tar.gz](http://mxhaard.free.fr/spca50x/Downl...0050906.tar.gz) tar xvfz spca5xx-20050906.tar.gz cd spca5xx-20050906 make sudo modprobe -r spca5xx

Never mind if the last command above throws up an error. just carry on with the rest of the instructions.
Code:

sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx* sudo make install sudo modprobe spca5xx

Now u should be all set to use ur ICM532 chipset based webcam.

Automatix: Just works!

The real successor to ubuntuguide: [http://doc.gwos.org](http://doc.gwos.org)

Team lead: Tweaker Team (We help maintain the Customization Tips and Tricks Forum and doc.gwos.org)
Last edited by arnieboy : 2 Weeks Ago at 02:02 AM.


So, I have now removed libqt3c102-mt

sudo apt-get remove libqt3c102-mt

reinstalled libqt3-mt, using synaptic manager and re-installed skype using

HTML Code:

[https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29)


by downloading the official version and amending it via the instructions given.

Skype works, however I still cannot get the before mentioned hot keys/ F keys to work?

Any ideas anyone?

Thank you in advance, and thank you kblood for pointing out what I had done. Didn't have a clue what any of it meant before, but I am gradually day by day, getting a bit closer. My Chinese however isn't improving!
Last edited by new2linux9 : 4 Days Ago at 08:02 PM. 

Please note, that I do not want to install another program to fix something that was previously working fine. 

Anybody?  Have I posted this in the right place?  I am still a newbie.
Thank you.

---

