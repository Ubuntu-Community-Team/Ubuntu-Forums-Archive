---
title: "Screen resolution problems"
date: 2008-07-18
forum: Hardware
---

### Post by vancedus on 2008-07-18
Hi, I am having trouble with getting my screen resolution to match my screen.  When I go into the screen and graphics application and click "detect" it only recognizes 640x480.  I have to tell it I have a different size screen and I can get something close but it is too big.  Thus, when I am at my login screen I can barley see the box.  Can someone help me reset my screen.  Thanks

---

### Post by falcon61102 on 2008-07-18
Sound like you don't have any drivers installed for your video card.

Have you installed current drivers for your card?  Has this been like that since installing Ubuntu?

Also, what kind of video card are you using?

---

### Post by vancedus on 2008-07-18
Hi,  I have the drivers, I think, I can run all the compiz stuff.  I have a GeForce 8400 256Mb.  It hasn't always been like this it just seemed to happen randomly.  Thanks for the help

---

### Post by falcon61102 on 2008-07-18
If you have updated Ubuntu to a new kernal lately, you may have to re-install the drivers.  If you go to System>Adminstration>Hardware Drivers, does it list your nVidia card?

---

### Post by vancedus on 2008-07-23
No if  go to Hardware drivers it doesn't list any, how can I ge them?

---

### Post by falcon61102 on 2008-07-24
Try this: Go to the terminal and run:
```
displayconfig-gtk
```

That should open a GUI window and allow you to view/edit your hardware drivers as well as the settings for them.  See what is listed for you hardware and drivers and if all that information is correct.

---

### Post by vancedus on 2008-07-24
I have tried this in the past, It says I have an NVIDIA driver but when I auto detect my monitor it only gives me the option of 640x480.  Then I have to choose a higher resolution to get it to allow my 1280x800.  Should I have another driver other than NVIDIA?

---

### Post by falcon61102 on 2008-07-24
Are you trying to use the drivers from the nvidia site or the ones through the Snyaptic Package Manager?  

Also, have you tried using Envy to install your drivers?

---

### Post by vancedus on 2008-07-24
yes, I got my drivers through envy.

---

### Post by falcon61102 on 2008-07-24
Have you tried installing nvidia-settings and using that to reconfigure your X-Config so it includes all your refresh rates and resolutions?

---

### Post by vancedus on 2008-07-24
I have installed the nvidia-settings and tried setting up my resolutions from there and it works but the displayconfig doen't seem to recognize it and my login window is still the wrong size. when I click "save to xserver" it tells me that it could not save it because it could not erase the old file.

---

### Post by Cyhawk on 2008-07-24
Try running a terminal and doing..

sudo nvidia-settings
<your admin/root password>

or..
gksudo nvidia-settings

Then you'll be able to save the settings. (require root access to modify that file)

---

### Post by falcon61102 on 2008-07-24
Yeah, that's the way to do it.  You need to run it under sudo to be able to overwrite the other files.  Just like if you were going to edit the file manually, you'd have to use "sudo gedit..."

If just loading the nvidia-settings and saving over the xorg.conf file doesn't work, there is a way you can completely refresh your xorg.conf using nvidia-settings.  Try just setting it to where you want it and then saving over the old X file and see if that works first though.

---

### Post by vancedus on 2008-07-30
perfect guys thank you very much

---

### Post by linux_tech on 2008-07-31
To check screen resolution:
From the main menu, select System -> Preferences -> Screen Resolution dialog.  The installer should have detected and set the screen resolution correctly. Check it and if it's wrong then pick a new screen resolution from the drop-down list.

---

### Post by falcon61102 on 2008-07-31
Glad you got it straight.

---

