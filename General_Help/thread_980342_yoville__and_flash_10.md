---
title: "yoville  and flash 10"
date: 2008-11-12
forum: General Help
---

### Post by sigurnjak on 2008-11-12
As of recently my wife cannot play yoville on facebook in ubuntu . it seems there is a problem with linux flash 10 and yoville as a game . I tried pclos with flash 9 and is fine . is there a way to roll back flash to version 9 and or for someone to post link for download nonfree plash 9 deb package .

---

### Post by trendal.toews on 2008-11-12
sudo apt-get remove flashplugin-nonfree

---

### Post by trendal.toews on 2008-11-12
> **KatmanHH said:**
> sudo apt-get remove flashplugin-nonfree

That uninstalls it but not sure if you can get version 9 or not.  I couldn't find it.

---

### Post by sigurnjak on 2008-11-12
Yes i know how to remove existing package . Question is more where do i get version 9 to install instead? I would still need flash for firefox anyway . It is a bit hard to find , eh !

Thanks for speedy  reply !:)

---

### Post by trendal.toews on 2008-11-12
I'm not sure but check out this page. [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791&sliceId=2)

Here is the download link, it is a .tar.gz      [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791&sliceId=2)

Edit: my bad HERE is the .tar.gz         [http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz](http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz)

---

### Post by sigurnjak on 2008-11-13
A new day and a fresh mind yield new results !
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

All the flash one could ask for ! Hope this helps someone too !

---

### Post by Omgee on 2008-12-14
> **sigurnjak said:**
> A new day and a fresh mind yield new results !
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

All the flash one could ask for ! Hope this helps someone too !

Were you able to get Yoville to work with any of these? When I revert to Flash Player v9, I just get a message saying I need Flash Player 9 to access Yoville, but when I upgrade to 10, I, too, can't get in. Did you ever find a workaround, or is this just a lost cause?

Edit: Ugh, nevermind, I got it to work with the Adobe version 9 quoted a couple of posts back, but it's virtually unplayable. Works fine in Windows with Flash Player 10, but unfortunately, it's too glitched to bother with in Ubuntu at this point.

---

### Post by sigurnjak on 2008-12-14
My wife plays it all the time without any glitches . did you first completely remove flash 10  and then installed flash 9 with browser closed . Thats how i did it and yo ville , you tube  and joost work just fine .

---

### Post by tylerlekang on 2008-12-14
How do I install flashplayer 9 from the tar.gz file?

---

### Post by sigurnjak on 2008-12-14
I have no idea , but i was able to find  . deb and that was a breeze.

---

### Post by RX8volution on 2008-12-19
THANK YOU!  ... andYahtzee!

  I ran the remove command [sudo apt-get remove flashplugin-nonfree]; then downloaded and installed (double-click and let the packager install it)

I run an x86/32-bit architecture so this plugin appears to work OK.
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.152.0ubuntu1~hardy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.152.0ubuntu1~hardy1_i386.deb)

The only complaint is that Yoville does "kick you out" every time you try and change location... possibly an independent issue from the player version.

Cheers.

---

### Post by RX8volution on 2008-12-19
I stand corrected.  YoVille loads but when you try go to outside the "apartment"... it just hangs on "loading room" or some message like that forever (then locks up the browser and dies).

I'm going to try different versions of the 9.x Flash client

---

### Post by sigurnjak on 2008-12-19
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb)

This version does not seem to give any problems . She can go anywhere , factory , store , etc . I hope  this helps .

---

### Post by RX8volution on 2008-12-19
Friggin' figures, the only version I DID NOT TRY... haha.  SUch is life.

---

### Post by sigurnjak on 2008-12-19
ROFL:lolflag:):P

---

### Post by RX8volution on 2008-12-19
Here's a problem... "download failed"
  The Flash plugin is NOT installed.

Apparently that file is no longer on macromedia's site... anyone have the original file and can figure out how to get it installed???

Thanks.

---

### Post by sigurnjak on 2008-12-20
[http://www.mediafire.com/?mzdmzymozco](http://www.mediafire.com/?mzdmzymozco)

i hope i got it right

P.S. i just tried link i gave you earlier and it works as well .

---

### Post by RX8volution on 2009-01-18
Ya, but the .deb file still tries to go out to Adobe's site and pull the content to install... which is apparently missing :(

---

### Post by coolnezz on 2009-07-26
my solution to this problem... just click or copy paste this to your browser...

[http://apps.facebook.com/yoville/index.php?autologin=1&id=all](http://apps.facebook.com/yoville/index.php?autologin=1&id=all)


hope it works for you!

---

### Post by gwyndyn on 2009-07-26
> **coolnezz said:**
> my solution to this problem... just click or copy paste this to your browser...

[http://apps.facebook.com/yoville/index.php?autologin=1&id=all](http://apps.facebook.com/yoville/index.php?autologin=1&id=all)


hope it works for you!

That link works beautifully. Thanks so much!

---

### Post by Trespasser on 2009-07-26
I found a flash fix for YoVille. Works just fine. Sound works too...

[https://launchpad.net/~thielmann/+archive/ppa/+sourcepub/389870/+listing-archive-extra](https://launchpad.net/~thielmann/+archive/ppa/+sourcepub/389870/+listing-archive-extra)

Yes, my wife loves these games. Glad I finally found an acceptable solution. This is in Jaunty.

Hope it works for you.

Later...

---

### Post by gspawn69 on 2009-08-04
Also, for whatever reason, Yoville works just fine if you access it through the Seamonkey web browser. I think it's a problem involving a combination of flash and Firefox. :P

---

### Post by Arup on 2009-08-04
Works here with flash 10x64 latest.

---

### Post by gspawn69 on 2009-08-04
I have the latest flash update from Adobe and the latest Firefox, and Yoville still doesn't work. But for some reason, it works with Seamonkey. I don't know why but...

Also, I use 32-bit Ubuntu.

---

### Post by sigurnjak on 2009-08-04
I just tried that flash beta and can log in just fine . Thank a lot guys !

---

### Post by bronxbomberz41 on 2009-08-08
I just installed the latest flash update this morning and it still doesn't work for anything that uses flash in firefox right now.  a little help would be appreciated.

---

### Post by sigurnjak on 2009-08-08
Remove your current flash completely  and install one that matches your CPU from here :
[https://launchpad.net/~thielmann/+archive/ppa/+sourcepub/389870/+listing-archive-extra](https://launchpad.net/~thielmann/+archive/ppa/+sourcepub/389870/+listing-archive-extra)

It works like a charm !

---

### Post by bronxbomberz41 on 2009-08-08
> **sigurnjak said:**
> Remove your current flash completely  and install one that matches your CPU from here :
[https://launchpad.net/~thielmann/+archive/ppa/+sourcepub/389870/+listing-archive-extra](https://launchpad.net/~thielmann/+archive/ppa/+sourcepub/389870/+listing-archive-extra)

It works like a charm !

So i did this and I selected the amd64 package as i have an amd TurionX2 processor (the sticker on the my computer even has a little 64!) but it said it was not the right architecture type.  I used the i386.deb file and it worked.  Little confused why the amd package didn't work but thank you

---

### Post by sigurnjak on 2009-08-08
are you using 32 bit ubuntu

---

### Post by bronxbomberz41 on 2009-08-11
Yes it appears that I do....an oversight on my part.

---

### Post by x-shaney-x on 2009-09-12
Anyone come up with a satisfactory solution for this?
I've tried again with latest 3.5.x firefox and same problem.
Yoville runs now but inventory is missing and can only view first 3 messages in my inbox plus one or two other niggles.

As has been mentioned before it works in seamonkey (and konqueror) but I can't get it working properly in firefox or opera.

For now I have a shortcut in my menu to open konqueror with yoville as the home page.
Tho it's a bit flaky at times if I'm logged into facebook in firefox at the same time.

<EDIT>
Turns out with the beta flashplayer linked in this thread, yoville works perfectly.
Unfortunately, a lot of other flash content on facebook (such as farkle) is no longer working, sayin flash needs upgrading <sigh>

---

### Post by Trespasser on 2009-10-23
Hi everyone,
I've found another fix for YoVille for you to try. BTW, it works for both Jaunty and Karmic (this is 32 bit of course...can't say for 64).

First, run this in Terminal (it's a link for flash 9 provided by someone earlier in this thread)....

wget [http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz](http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz)

tar xvfz install_flash_player_9.tar.gz

cd install_flash_player_9_linux

sudo mv libflashplayer.so /usr/lib/firefox-addons/plugins

Now run this ...

wget [http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz](http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz)

tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz

cd flashplugin-nonfree-pulse-0.1~000

sudo apt-get install libpulse-dev

make

sudo make install

The file libflashsupport.so will be compiled and installed at /usr/lib. Be sure to keep a copy of both libflashplayer.so and libflashsupport.so should you decide to install Karmic when it is released (no need to recompile libflashsupport.so).
 
I found the above info about libflashsupport.so from this site...

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

That's it. YoVille should load fine along with Farm Town, FarmVille, etc..

Hope it works for you as it does for me (or should I say my wife...:)).

---

### Post by sigurnjak on 2009-10-23
Thank you !  No more Wine + Firefox  !

You rock !:guitar::popcorn:

---

### Post by sigurnjak on 2009-12-31
Hi Trespasser ! 
I switched to 64 bit Karmic and i am back to same problem .
When i tried to make flash  pulse i got this :
andrey@ubuntu:~/flashplugin-nonfree-pulse-0.1~000$ make
cc -shared -O0 -Wall -Wextra -W `pkg-config --cflags libpulse` -g `pkg-config --libs libpulse` flashsupport.c -o libflashsupport.so
/usr/bin/ld: /tmp/cc9OLOQd.o: relocation R_X86_64_32 against `.bss' can not be used when making a shared object; recompile with -fPIC
/tmp/cc9OLOQd.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libflashsupport.so] Error 1

Is there a way to make this for 64 bit ?

---

### Post by nwchick on 2010-01-16
try removing "swfdec" from firefox using synaptic pkg mgr. Find it in the list, and mark it for complete removal. Click on the check to apply chgs, then retry. No restart necessary. ...I had the same problem with farmville (another zynga game), and once I completely uninstalled it, I was able to play. Note that I had installed adobe's version of flash before I took out swfdec....apparently it wreaks havoc with facebook flash games.

Best of luck to you....

---

### Post by brooke1982 on 2010-02-24
I tryed that but it keeps telling me that  i have a broken something y does it not work

---

### Post by brooke1982 on 2010-02-24
were do i find swfdec  at

---

### Post by x-shaney-x on 2010-02-24
Try the new flash beta from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
All flash, including yoville is working fine for me now.

---

### Post by brooke1982 on 2010-02-25
i do not know how you guys are downloading this stuff but everytime i try to download something pops up saying for read only how do you do it i like widow vista better

---

### Post by sigurnjak on 2010-03-02
You may have some permission problem there . If you are going to move stuff to and from root directory you need to do it as root . That is one of the safety  features that makes Linux safer than MS products .

As for that new flash , it works great . Thank you! 
Now i think Yoville is one buggy game , since i get sound everywhere  except in Yoville  , but we can live with that .

---

### Post by KlinerDraken on 2010-06-12
I got a flash update today and now YoVille works for me

using chromium 5.0.375.70 on Ubuntu 10.04

---

