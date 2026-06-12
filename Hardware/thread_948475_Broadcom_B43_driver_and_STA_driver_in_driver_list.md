---
title: "Broadcom B43 driver and STA driver in driver list?"
date: 2008-10-15
forum: Hardware
---

### Post by steelmaverick on 2008-10-15
I have a laptop using the Broadcom B43 wireless driver, and it works perfectly.

Now, recently while doing updates, a new driver popped up, the Broadcom STA driver. It says that it is also a driver.

So, my question for you is: What is the STA driver, and is it better? Should I upgrade to it? 

Just asking ahead of time so i dont do something unnecessary and end up spending time to put it back.

---

### Post by nuclearfall on 2008-10-15
I just upgraded to the STA driver.  So far the only noticeable difference is that my wireless rate is 54 Mb/s and not 1 Mb/s.  That's enough for me to stick with it, at least until something goes horribly wrong.

---

### Post by Nostalos on 2008-10-15
STA is the proprietary Driver from Broadcom and works even better so far than B43.

I have been using the same Dell D610 since gutsy.   I started out with the bcm43xx-fwcutter and firmware.   It worked, but range was severely limited due to a bug that did not downgrade my bandwidth appropriatly automatically.  So in order to use my laptop in the front room of my house I had to manually set the card to 1Mbps.

As I upgraded I moved to the B43 driver.  Worked quite well.  was able to get 40% signal strength in the same room and did not have to muck with it manually.

Now with Ibex I have moved to the STA driver.  I now get 75% signal strength in the same room and can now actually take my laptop into my garage which is another 15Ft away and another wall.

STA Driver FTW.

---

### Post by steelmaverick on 2008-10-15
> **Nostalos said:**
> STA is the proprietary Driver from Broadcom and works even better so far than B43.

I have been using the same Dell D610 since gutsy.   I started out with the bcm43xx-fwcutter and firmware.   It worked, but range was severely limited due to a bug that did not downgrade my bandwidth appropriatly automatically.  So in order to use my laptop in the front room of my house I had to manually set the card to 1Mbps.

As I upgraded I moved to the B43 driver.  Worked quite well.  was able to get 40% signal strength in the same room and did not have to muck with it manually.

Now with Ibex I have moved to the STA driver.  I now get 75% signal strength in the same room and can now actually take my laptop into my garage which is another 15Ft away and another wall.

STA Driver FTW.

Alright, I think I'll give it a shot.

BTW, just for my own purposes, before my wireless card was labeled wlan0, now its eth2. I know it doesn't really make a difference to the computer, but how can I relabel it wlan0?

---

### Post by the_maplebar on 2008-10-15
> **nuclearfall said:**
> I just upgraded to the STA driver.  So far the only noticeable difference is that my wireless rate is 54 Mb/s and not 1 Mb/s.  That's enough for me to stick with it, at least until something goes horribly wrong.

SWEET!!!  I just upgraded my kernel.  Guess I will try switching drivers now :)

---

### Post by the_maplebar on 2008-10-15
I just did a quick little test after changing my drivers.  Just a note, I did have to play around with reconfiguring my wifi after upgrading, but it's working now.

I recently copied a DVD iso over my local wifi network in 100mb chunks using SCP.  Speeds peeked at 16Mbps and dropped to 1Mbps at times with the B43 driver.  For a quick test I copied 20 10MB files and 1 100MB file using the STA driver.  Speeds peeked at 27Mbps and he lowest they dropped to was 20Mbps.

Looks like an improvement to me.

---

### Post by linux4life88 on 2008-10-15
I just installed this new driver and the speed difference is amazing. Before I had a strength of 55% to 65% now in that same room I have 80% to 100%.

---

### Post by ivomans on 2008-10-20
> **the_maplebar said:**
> ...  Just a note, I did have to play around with reconfiguring my wifi after upgrading, but it's working now. ...

I tried switching from B43 to STA but could not get a working connection anymore. I'm back on B43 now. What reconfiguration is required to get it working?

---

### Post by Ayuthia on 2008-10-20
> **ivomans said:**
> I tried switching from B43 to STA but could not get a working connection anymore. I'm back on B43 now. What reconfiguration is required to get it working?

Did you disable the b43 driver?  You might also have to blacklist the b43 and ssb driver to get the wl (STA) driver to work.

---

### Post by sergiom99 on 2008-10-20
this seems to be the "official" thread:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by ivomans on 2008-10-20
> **Ayuthia said:**
> Did you disable the b43 driver?  You might also have to blacklist the b43 and ssb driver to get the wl (STA) driver to work.

After all I did a couple of things:

[LIST]
[*]disable b43
[*]reboot
[*]enable sta
[*]reboot
[*]remove network configuration
[*]try connecting, enter WPA password again
[/LIST]
Repeat last 2 steps a couple of times meanwhile experimenting with 'switch off network' and 'on' again, etc. After about 15 minutes fiddling around with these settings all at a sudden I had a connection again. Not sure what eventually did the trick.

In the end: signal much better, network much faster now. 
Worthwhile to experiment a while!

---

### Post by charles.ccomp on 2009-03-27
Hello, folks.
I've found this thread very instructive, but i still have a problem:
I have a Dell D630 with Dell Wireless 1490 and Intrepid Ibex. Since it came with Broadcom STA driver preinstalled, i've never experienced problems. But i had this stupid idea of installing the Enlightenment (another graphical interface). I've managed to install it, but it did not recognized my wireless. So i've installed ndiswrapper, and for Enlightenment, it worked well! But on Gnome, the wireless went crazy. It started to take ages to connect, and failing authentication (i use WPA). Then, when i uninstall the ndiswrapper and try to use the broadcom sta, it simply doesnt work well. The driver doesnt start up initialized, and i have to start it manually everytime i start the system. But when i go to System -> Administration ->Hardware Drives, the status of the driver is "Activated, but not in Use". I think that maybe its the other driver that i did not fully uninstalled. Anyone knows the way outta this?

---

### Post by costamatrix on 2009-04-27
hi folks.... my problem is the opposite...

i have a HP dv2000 notbook ...
i am using broadcom STA driver, but i want to use airodump and aircrack apps...and i was told, the this app to work, i will have to replace broadcom STA by broadcom 43 version...

is this true?

how do i do this?

---

### Post by smalldog on 2009-05-02
I am using STA for my wireless card 4312. However, it is very strange. I can using WPA2 to build connection with my dd-wrt router but it never success with my Asus router. 
It imply that even though it is using same driver on my laptop, it is depend on the WPA implementation of router render. Honestly, the propriety supplier provide better support but the open source provide even more compatible.

---

### Post by twinkel1961 on 2009-05-06
I guess it has something to do with the update.
The linux-restricted-modules-generic is being held back.

Synaptic reports:
linux-restricted-modules:
  Depends: linux-restricted-modules-generic (=2.6.28.12.16) but 2.6.28.11.15 is to be installed

In a [previous post with a similar situation]("http://ubuntuforums.org/showpost.php?p=3482839&postcount=7") it was suggested to just wait until the linux-restricted-modules is released.

I guess I now understand the meaning of a partial update...:(

---

### Post by ataris_kid on 2009-05-06
> **twinkel1961 said:**
> I guess it has something to do with the update.
The linux-restricted-modules-generic is being held back.

Synaptic reports:
linux-restricted-modules:
  Depends: linux-restricted-modules-generic (=2.6.28.12.16) but 2.6.28.11.15 is to be installed

In a [previous post with a similar situation]("http://ubuntuforums.org/showpost.php?p=3482839&postcount=7") it was suggested to just wait until the linux-restricted-modules is released.

I guess I now understand the meaning of a partial update...:(

I fell into this trap too.. =(

---

### Post by TheWitness on 2009-05-10
> **twinkel1961 said:**
> I guess it has something to do with the update.
The linux-restricted-modules-generic is being held back.

Synaptic reports:
linux-restricted-modules:
  Depends: linux-restricted-modules-generic (=2.6.28.12.16) but 2.6.28.11.15 is to be installed

In a [previous post with a similar situation]("http://ubuntuforums.org/showpost.php?p=3482839&postcount=7") it was suggested to just wait until the linux-restricted-modules is released.

I guess I now understand the meaning of a partial update...:(

You need to take the "SOLVED" out of your tag line, cause you are screwing up Googles search engine.  Every post you make results in a SOLVED hit.  Tisk tisk tisk.

TheWitness
[www.cacti.net](www.cacti.net)

---

### Post by TheWitness on 2009-05-10
I have this problem and the work around for me is to deactivate then reactivate.  Then, all is well.  Waiting on an update, but searching none the less for the solution.

TheWitness

---

### Post by bigmattyd on 2010-06-07
I have a Dell Inspiron 1501 laptop, running Ubuntu 8.10, and the STA driver is better than the B43 on my system.  

The STA gives higher signal strength and speed over the B43.  Also, I was having intermittent losses of connection with the B43 driver.  STA is very solid and unflappable.

Thanks,

Matt

---

### Post by mattjrdn on 2011-09-12
The only problem I have found with the STA drivers is that they don't allow for packet injection. Switching back to B43 drivers.

---

