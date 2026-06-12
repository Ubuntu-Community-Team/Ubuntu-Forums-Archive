---
title: "Getting ATI Video Card to work on HDTV"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by pyrotecha on 2008-02-24
I have a 42" Samsung HDTV ( I believe the model is HP-S4358 ) and after numerous attempts at every guide possible that I found (and having them all fail on me) I finally decided to try something to see if it would work. I've tryed playing around with the .conf file and pretty much any other "HowTo" out there. This was easier than anything I could find. Here it goes:

1. Go to System>Administration>Synaptic Package Manager
     a) Do a search for Wine and install the package

2. Go to the ENVY website and download and install ENVY
     a) Url: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
     b) Click on "Get Envy New"
     c) Install it

3. Go to the ATI website and download the driver
     a) Url: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
     b) Click on Vista 32 or 64 (depending on your version of Ubuntu
     c) Find your card and click go
     d) Under Option 1 click on "Catalyst Software Suite"
     e) Save it to wherever (just remember where it is)

4. Back on Ubuntu click on Applications>Wine>Configure Wine
     a) Make sure "Windows Version" on the bottom is set to Vista
     b) Click Apply and OK

5. Install the Catalyst Software Suite
     a) Right click on the file that you downloaded and click on "Open With Other Application"
     b) Scroll all the way down to "Wine Windows Emulator"
     c) Click "Open" and install it
     ***Note*** It looks like nothing has happened yet, but just wait.

6. Go to Applications>System Tools>Envy
     a) Click the "Install ATI Driver" radial button
     b) Click "Apply"

7. After it installs the drivers and stuff it's probably going to ask you to restart.
     a) Go ahead and restart
     b) When Ubuntu loads back up again, you'll probably see that the resolution has changed (it did for me)
     c) Log in and click on Applications>Accessories and you'll see the ATI Catalyst Control Center
     d) Click on that and set it up like you would normally
     e) Restart and you're good.
     f) Enjoy!

---

### Post by pyrotecha on 2008-02-24
Bump for anyone who may have not seen this.

---

