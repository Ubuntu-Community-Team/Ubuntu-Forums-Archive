---
title: "iPhone won't mount (iOS 4)"
date: 2010-12-05
forum: Hardware
---

### Post by Ryupower on 2010-12-05
Hello,
I just re-installed ubuntu and I updated my iphone to the newest iOS 4 last week. (it's a 3G)

I've tried many things, but it just won't mount. Here is the output from iFuse in the terminal:

xxxxx@ubuntu:~$ ifuse /media/iphone/
ifuse: error while loading shared libraries: libimobiledevice.so.1: wrong ELF class: ELFCLASS32

I upgraded my ubuntu and my packages to the latest stance.

---

### Post by Ryupower on 2010-12-05
bump

---

### Post by duff_bluff on 2010-12-05
Same problem for me, even though this is addressed in other threads I can't seem to get the problem fixed by the solutions offered in them.

---

### Post by Ryupower on 2010-12-06
tried the other thread's solutions and it didn't bring me further. None of them posted that odd error message.

---

### Post by erikduop on 2010-12-06
I am having a hard time with iTunes recognizing my iPhone. It is not the  phone or cable as I took it up to the genius bar and it worked fine up  there. I have tried numerous usb ports and I have the same issue with  all of them. I assume it is iTunes but am unsure what to do to  troubleshoot it. It works about 10% of the time.

---

### Post by Ryupower on 2010-12-06
bump

---

### Post by arepaking on 2010-12-19
I am in the same boat as you folks. 10.04 won't mount it either.

---

### Post by craig100 on 2010-12-19
My iPhone 4 just upgraded to iOS4.2 via iTunes on Win 7 running in VirtualBox on Ubuntu 10.10x64.  Ubuntu itself won't mount it via USB though the Win7 VM sees it ok.

Any clues anyone?

---

### Post by zander1013 on 2010-12-19
i have had problems getting my iphone 4 to mount in itunes too (on a macbook with os x).

the solution was to completely remove itunes including package receipts etc. then download and reinstall it.

---

### Post by xlash on 2011-01-09
Same thing here... just bought an iphone 4 alreay at iOS 4.2.1

Any solutions for mounting it on Ubuntu or getting around that error?

```
/media$ ifuse iphone
ifuse: error while loading shared libraries: libimobiledevice.so.1: wrong ELF class: ELFCLASS32

```

---

### Post by xlash on 2011-01-10
Upgrading libimodiledevice to 1.0.4 fixes the issue for me. On Ubuntu Maverick and older use :

```
sudo add-apt-repository ppa:pmcenery/ppa

```


UPDATE :

It detects the iPhone, it syncs, but nothing appear on the iPhone. however, the space is used!!! I'll investigate later. It's also worth noting that Rhythmbox disabled the Ipod plugin automatically and I had to re-enable it in the Plugins menu.

UPDATE-2:

Seems like libimobiledevice does not work yet for Iphone 4, Ipad, even though iOS 4.2.1 is supported. Their status is : Rhythmbox, gtkpod and Amarok sync with latest libgpod >= 0.7.90. The iPhone 4, iPad and Apple TV do NOT work. [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by zx5000 on 2011-01-19
Fedora 14 (kernel 2.6.35) detects iPhone, sees files, rhythmbox plays tunes.

When will Ubuntu?

---

### Post by gadget6660 on 2011-01-25
Below fixed it for me.
Care of ubuntugeek.com

[http://www.ubuntugeek.com/how-to-get-ios-4-iphone-os-to-sync-with-rhythmbox-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-get-ios-4-iphone-os-to-sync-with-rhythmbox-in-ubuntu-10-04-lucid.html)


1. Open up synaptic

2. Go to the Repositories (Under Settings)

3. Add this source:

ppa:pmcenery/ppa  

(from [https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa))

4. Click Close and then click the Reload button at the top left

5. After it is done reloading search for:

libimobiledevice1

6. It will give you two results, install both.

7. Now after installing, close synaptic and open up the terminal and type in

sudo apt-get dist-upgrade

8. After the upgrade Ubuntu 10.04 will have iOS 4 support
:p

---

### Post by MikeyinLB on 2011-03-06
Just as an aside, the steps above seem to have solved my issues with getting my Polaroid digital camera to be recognized, as well. Prior to this, digiKam would not connect to it, but now it does. Thanks!

---

### Post by Cpierce on 2011-03-07
Thank you Gadget6660, This worked like a charm on my Itouch 4.2

---

### Post by lingenfr on 2011-03-07
> **gadget6660 said:**
> Below fixed it for me.
Care of ubuntugeek.com

[http://www.ubuntugeek.com/how-to-get-ios-4-iphone-os-to-sync-with-rhythmbox-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-get-ios-4-iphone-os-to-sync-with-rhythmbox-in-ubuntu-10-04-lucid.html)


1. Open up synaptic

2. Go to the Repositories (Under Settings)

3. Add this source:

ppa:pmcenery/ppa  

(from [https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa))

4. Click Close and then click the Reload button at the top left

5. After it is done reloading search for:

libimobiledevice1

6. It will give you two results, install both.

7. Now after installing, close synaptic and open up the terminal and type in

sudo apt-get dist-upgrade

8. After the upgrade Ubuntu 10.04 will have iOS 4 support
:p

Are these also the correct instructions for 10.10?

---

### Post by Neiman on 2011-03-29
Not sure if the above posted instructions are for 10.10 (Meerkat) but I tried it anyways and it worked for iPhone 4 (4.3 Firmware)

Rhythmbox can only sync audio and nothing else. Also the above terminal process takes awhile , apparently it goes through every single package replacing files..... seems a lot to just get the iPhone to mount.

---

### Post by BookishBluestocking on 2011-09-09
I tried the above on my iPhone 3gs with 4.2.1 firmware, and it didn't work (Ubuntu 10.04). Anyone have any wisdom?

---

### Post by EdgarGonzalez on 2011-09-11
I'm using Ubuntu 11.04, and neither my iPhone 4 (4.3.1) or my iPod touch (2g) are mounted. I plug them and got not message

I tried using ppa:pmcenery/ppa with no success ([http://www.davidcdean.com/fix-iphone-support-in-ubuntu-11-04-natty-narwhal/](http://www.davidcdean.com/fix-iphone-support-in-ubuntu-11-04-natty-narwhal/))

Any clue?

---

