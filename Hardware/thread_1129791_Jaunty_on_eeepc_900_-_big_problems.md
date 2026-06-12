---
title: "Jaunty on eeepc 900 - big problems"
date: 2009-04-19
forum: Hardware
---

### Post by HRH_H_Crab on 2009-04-19
I have installed jaunty netbook remix on an eeepc 900.
I only expected to use this machine for browsing with firefox, and as a terminal, but it is pretty much unusable for either.

The machine has 1GB of RAM and a 900MHz cpu so I think my expectations are fairly reasonable, so I guess I have made a mistake somewhere.

Typing this post in firefox is hell. The machine keeps locking up every 10-15 seconds for about 15-20 seconds. If i try and scroll the machine will lock up and then scroll very quckly when it "wakes". If I close firefox by clicking the window manager "close window" I will get a message telling me the app isnt responding every time I try this - closing a window is enough to kill the machine.

So much for firefox - well what of gnome-terminal?

That is equally frustrating. It cannot hold an ssh session for more than 2 minutes. I am using the stock ath5k drivers in Jaunty.
 
Linux lamma 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Can anyone give me any pointers?
Does this sound like a hardware problem?

---

### Post by thewolfman on 2009-04-19
For Netbooks you need "Easy Peasy" as its designed with Netbooks in mind, it is a Ubuntu variant so you should get on with it okay.

Have a good one!.

---

### Post by stuartmarsden on 2009-04-20
Jaunty is looking like a bit of a disaster on eee pc 900 and probably other netbooks.  The intel driver is a mess and runs like a pig.  Switching to the new UXA rendering improves things a bit but probably not back to where we were in intrepid.  But it is not without problems and has some graphical glitches. 

I am also seeing a problem of losing the session when coming back from sleep.

I may end up going back to intrepid and hope karmic is better.

---

### Post by cyclone5uk on 2009-04-21
Which version of the 900 do you have? Some have two SSD’s (one is slower, the other is faster). If you’ve accidentally installed your OS onto the slower drive that may be what’s causing it.

I did a fresh install of Jaunty on my eeepc 901. Installed fine. I set it up the usual way I’ve done with ubuntu before. Manual install with no swap, and set the 4gb SSD (fast) as / and the 8gb SSD (slow) as /home.

Everything worked straight out of the box including wireless. I used the new ext4 file system and boot seems faster than on Intrepid with ext3.

Firefox 3 flies along quicker than ever (I had major problems with it lagging under Intrepid due to FF3 indexing to the slower SSD). Flash video is playing fine as well.

One thing to be aware of, the 901 has a different processor and chipset to the 900, so it isn’t a direct comparison.

[http://forum.eeeuser.com/viewforum.php?id=43](http://forum.eeeuser.com/viewforum.php?id=43)

This board is specifically for eeepc users who are running Ubuntu. There are already lots of threads about Jaunty.

---

### Post by shobon on 2009-04-21
> **stuartmarsden said:**
> Jaunty is looking like a bit of a disaster on eee pc 900 and probably other netbooks.

I'm using Jaunty on my Aspire One without a problem.

I'd suggest looking into Ubuntu Netbook Remix (UNR). After switching from distro to distro UNR has given me the best of luck.

---

### Post by njwrightmd on 2009-04-25
I updated to jaunty on my eeepc 900 specifically to get the wireless to work.  After installing jaunty, things seem slower on my eeepc, the wireless doesn't work at all despite many attempts at hacking.  And, the last straw, my sansa mp3 player e250 doesn't mount.  I know many people are disappointed in the mp3 players not mounting, and hopefully that bug will be fixed.  I don't think the wireless problems will be fixed, it seems to only affect the 900.  I tried easy peasy but that installation broke my computer, so I'm on standard vanilla ubuntu.  I think I'll re-install intrepid, things worked better on that, and addams kernel can be applied to intrepid so I can use wireless.

---

### Post by snowpine on 2009-04-25
Depending on which model eee 900 you have... it is notorious for having one of the slowest SSD drives on the market, and I think that is what's causing your firefox problems. You need to change your firefox preferences so it caches to ram instead of the SSD drive. Lots of good tutorials on this over at the eeeuser.com forums. That is my suggestion, good luck!

---

### Post by Cyberapoc on 2009-04-26
There is really nothing wrong with its SSD drive or whatever, it doesn't explain the problems you have.

I've used Intrepid on the 900 with no problems. I wanted to have a flying fast and powerful machine though, so I installed the Array.org lean kernel on Linux Mint Fluxbox with ndiswrapper for the wireless (ath5k drivers suck, they are slow and don't connect now and then). It boots faster than my desktop. Tried Mint XFCE based on 8.10 as well, ran fine.

Best of luck.

---

### Post by bennachie on 2009-04-26
One of my computers is an eeePC 4G. While it had been running well with Jaunty Beta (vanilla edition) I thought that I should try installing NBR. The result was pretty disappointing. The desktop GUI was dreadfully slow (like swimming through treacle) and the installation chewed up more disk space than the vanilla beta had. I have now completed a fresh install of the vanilla release, and normal service has been resumed. The GUI is clean and fast, and all the applications launch and respond quickly.

So far as I can see, the only advantages of the NBR version are that the installation screens fit more tidily into the (limited) screen real estate, and applications have marginally more of that real estate available to them. Frankly, those advantages don't seem to outweigh the performance disadvantages.

I don't have an eeePC 900 to try, but the vanilla version of Jaunty is just great so far as I am concerned. Almost everything works straight out of the box (just remember to cancel desktop effects, so that you don't lose access to the alt-click-drag workaround for the inevitable application preference panes that don't respect the boundaries of the small screen - NBR has the same problem anyway).

---

### Post by aldreis on 2009-04-26
> **bennachie said:**
> (just remember to cancel desktop effects, so that you don't lose access to the alt-click-drag workaround for the inevitable application preference panes that don't respect the boundaries of the small screen - NBR has the same problem anyway).

You could try this:

```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

It'll disable that utterly annoying upper constrain. ;)

---

### Post by hojjan on 2009-05-02
Might be a bit late, but I have a solution.

I installed UNR 9.04 on my Eee 900 16G just 30 minutes ago, and was experiencing the exact same thing. I looked around a bit, and found that there's a simple kernel fix for this annoying bug detailed here:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349314](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349314)

To get and install:

```

wget http://people.ubuntu.com/~apw/lp349314-jaunty/linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
wget http://people.ubuntu.com/~apw/lp349314-jaunty/linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
sudo dpkg -i linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
sudo dpkg -i linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
```

Also: Yay, my first post!:)

In case you get errors like some seem to be experiencing below, you can try the graphical way:

[http://people.ubuntu.com/~apw/lp349314-jaunty/](http://people.ubuntu.com/~apw/lp349314-jaunty/)

Go there and get:

linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb 
linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb

Point and click to install, starting with headers. This will probably solve it.

---

### Post by HankB on 2009-05-02
Somehting else you should try is putting your /tmp drive in RAM (tmpfs) as well as your browser cache. 

Also use the noatime mount option for your SSD drives.

Both of these will help stop stalls while the system writes to the excruciatingly slow SSD.

Check out the tweaks here:

[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

(9.04 UNR runs well on my Eee PC 901, but I realize it has different H/W.)

HTH,
hank

---

### Post by rmhainlen on 2009-05-03
fun, so I tried fixing my machine with that nice code and got this error message:

dpkg: dependency problems prevent configuration of linux-headers-2.6.28-11-generic:
 linux-headers-2.6.28-11-generic depends on linux-headers-2.6.28-11; however:
  Package linux-headers-2.6.28-11 is not installed.
dpkg: error processing linux-headers-2.6.28-11-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.28-11-generic

The first promising post about all the issues I am having with jaunty (actually, one issue but 10 hours of googling has failed me) and it doesn't work.  I am guessing its because the kernels I have are:
2.6.24-20-eeepc
2.6.24-21-eeepc

oh well, back to my googling.

---

### Post by FatherDale on 2009-05-04
> **HRH_H_Crab said:**
> I have installed jaunty netbook remix on an eeepc 900.

Can anyone give me any pointers?
Does this sound like a hardware problem?

My guess would be a hardware issue or perhaps a bunged install. I got my 901 a week ago today. Played with xandros for five minutes, then plugged in my NBR flashdrive and blew it away. I've had pretty close to zero issues with it (little annoying things like the hardware shortcut buttons not mapping), great speed, usable.

I tried NBR on my daughter's 701 8G a few weeks ago, and it was a slug -- she begged me to re-install Xandros. Go figure. She's happy... You might try re-installing it. This time, use the manual partitioning, make it all EXT4, and, as someone said further down,  use the 4gb drive as / . Cuz, why not?  :-)

---

### Post by sgosnell on 2009-05-04
Firefox, wireless, and everything else work fine on my 900.  You do need to go into Firefox and change the cache settings.  With the default 256MB setting, it writes to disk far too much, and won't do anything else while it's writing.  I set my cache to 0 and don't have that problem.  Wireless worked out of the box, and I have no issues with it.  As for the ssh problem, I don't use it and have no suggestions.  You might try [this page](https://help.ubuntu.com/community/EeePC/Fixes) for some help, although it's mainly directed toward previous versions.

---

### Post by hojjan on 2009-05-06
> **rmhainlen said:**
> fun, so I tried fixing my machine with that nice code and got this error message:

dpkg: dependency problems prevent configuration of linux-headers-2.6.28-11-generic:
 linux-headers-2.6.28-11-generic depends on linux-headers-2.6.28-11; however:
  Package linux-headers-2.6.28-11 is not installed.
dpkg: error processing linux-headers-2.6.28-11-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.28-11-generic

The first promising post about all the issues I am having with jaunty (actually, one issue but 10 hours of googling has failed me) and it doesn't work.  I am guessing its because the kernels I have are:
2.6.24-20-eeepc
2.6.24-21-eeepc

oh well, back to my googling.

Amended my original post with alternative installation method.

---

### Post by Bearded-flower on 2009-05-10
> **thewolfman said:**
> For Netbooks you need "Easy Peasy" as its designed with Netbooks in mind, it is a Ubuntu variant so you should get on with it okay.

Have a good one!.

NO! not easy peasy
seriously dont do it

---

### Post by markyb86 on 2009-06-22
I have been using jaunty on my EeePC 900 since it hit RC and have had no issues what so ever. I have the model that only has a 4G ssd. I've found its slower with compiz enabled but its 3 clicks and thats out of the question. Easy Peasy right now is only based on Ubuntu 8.10 so if you want a newer OS install Ubuntu 9.04. BTW, dont install netbook remix, the launcher is slow as hell and pointless. Ubuntu's default desktop is very productive and easy to get around.

---

### Post by vroegahh on 2009-07-01
> **hojjan said:**
> Might be a bit late, but I have a solution.

I installed UNR 9.04 on my Eee 900 16G just 30 minutes ago, and was experiencing the exact same thing. I looked around a bit, and found that there's a simple kernel fix for this annoying bug detailed here:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349314](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349314)

To get and install:

```

wget http://people.ubuntu.com/~apw/lp349314-jaunty/linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
wget http://people.ubuntu.com/~apw/lp349314-jaunty/linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
sudo dpkg -i linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
sudo dpkg -i linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb
```Also: Yay, my first post!:)

In case you get errors like some seem to be experiencing below, you can try the graphical way:

[http://people.ubuntu.com/~apw/lp349314-jaunty/]("http://people.ubuntu.com/%7Eapw/lp349314-jaunty/")

Go there and get:

linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb 
linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb

Point and click to install, starting with headers. This will probably solve it.



I fixed this problem with the latest kernel patch. However, after installing the latest updates yesterday the problem came back!!  Reinstalling the patch doesnt work. :(:(

---

### Post by apel_2804 on 2009-07-01
I got same trouble with Jaunty. Finally I installed 8.04.2 LTS and installed the Ubuntu Netbook Remix packages manually. Also added special EEE PC kernel from array.org. Now it's fast and works like a charm. I wrote an How-to for it:

[http://www.tbaumi.de/blog/?p=352](http://www.tbaumi.de/blog/?p=352)

Maybe it's ok for you to use Hardy instead of Jaunty.

---

