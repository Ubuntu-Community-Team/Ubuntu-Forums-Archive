---
title: "Howto: Install Nvidia 8800 in Ubuntu 8.04"
date: 2008-07-30
forum: Hardware
---

### Post by Klingstedt on 2008-07-30
Hi everyone!
I was having some problems after screwing up my xorg.conf so my xserver didn't quite like me, but after alot of testing that didn't go as planed i succeeded and would like to share my solution with those who have the same problem! This mioght not be the best solution but it worked out for me so i'll give it a shot!

Forst off I installed Envyng, and you can find it here:
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

After that I started envy in terminal using:
```
sudo envyng -t
```

selecting option number 2 and ENTER

When the process is done, I exited Envy and installed nvidia-settings using:
```
sudo apt-get install nvidia-settings
```

**WARNING** Always make a backup before removing xorg.conf
To do that use:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pre-nv
```

When I had backed up my xorg.conf, I removed my xorg.conf completely by typing following in terminal:
```
sudo rm /etc/X11/xorg.conf
```

To do that use:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pre-nv
```

and after that using nvidia-xconfig to create a healthy and new xorg.conf
```
sudo nvidia-xconfig
```

Now lets install the driver using envy again.

Press CTRL+ALT+F1, that will put you in a terminal window without GUI.
Login with your ordinary login.
Close the GUI window that's still running in CTRL+ALT+F7 by typing:
```
sudo /etc/init.d/gdm stop
```

Now start envy again.
```
sudo envyng -t
```

choose option 5 this time, allowing you to manually install the driver.
now choose option nr 2, NVIDIA
and when the next options pops up choose the one that says (latest) at the end, probobly option nr. 1

Envy should start installing the necessary things tomak your xserver look healty again, hopefully.

when this is done you will get an option to reboot your computer, type in y and press enter to do that.

HOPEFULLY your xserver is repaired and up and running as it should.

NOTE
The first part can also be done in CTRL+ALT+F1 if you can't access your xserver at all!

Please let me know if this works for you too or if you have other comments on the guide!
Thank you!

---

### Post by Cresho on 2008-07-30
all you need to do is go into system->administration->hardware drivers tick "nvidia accelerated graphcis driver)  it installs and you reboot.

your done.  then you "sudo apt-get install nvidia-settings" and in system->prefference->sessions, you make new "nvidia" and you place this command for startup "nvidia-settings --load-config-only".  This will autoload nvidia saved settings.

i have an 8800gt bfg oc.  If you want to use the latest and the greatest drivers, download it from nvidia and install it from grub start recovery but this is another type of animal way of installing.

NOW  if you want antiliasing and smooth 200mhz silk smooth speed, follow my tutorial.

[http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing](http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing)

---

### Post by Klingstedt on 2008-07-31
> **Cresho said:**
> all you need to do is go into system->administration->hardware drivers tick "nvidia accelerated graphcis driver)  it installs and you reboot.

your done.  then you "sudo apt-get install nvidia-settings" and in system->prefference->sessions, you make new "nvidia" and you place this command for startup "nvidia-settings --load-config-only".  This will autoload nvidia saved settings.

i have an 8800gt bfg oc.  If you want to use the latest and the greatest drivers, download it from nvidia and install it from grub start recovery but this is another type of animal way of installing.

NOW  if you want antiliasing and smooth 200mhz silk smooth speed, follow my tutorial.

[http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing](http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing)

The thing is that I tried doing that several times and the nvidia-glx-new driver messed up my xorg.conf.
When I first installed Ubuntu that was the first thing I did and succeded and everything was fine but when I couldn't get WoW and some other things working I tried to install the driver from Nvidia's homepage and that was a big misstake and could just reinstall nvidia-glx-new to make the problem go away. So I did all the things above and now it works again :)

---

### Post by Xenoguy on 2008-07-31
I've got an 8800 and i've had similar bad experiences loading the driver from the nvidia site.  you can get it working if you go through the install logs and fix the problems it mentions, i think it was just a matter of deleting some links.  but the next time a new kernel comes out you end up running the installer again, so its a real hassle.  once you've borked your xorg.conf you get all kinds of wonderful black screens and system hangs.  been down that road a few times.

Best way to get some newer nvidia drivers, is to enable the 3rd party repositories in synaptic package manager, as well as enabling hardy-proposed.

once you've enabled those 2, reload the package data in synaptic, and use the package manager gui to install envyng.

after you get envyng, run it, select nvidia, select the latest driver (173 currently).  if you haven't enabled hardy-proposed, then an earlier driver might show up (169?).  envyng does a great job of installing, fixing your xorg.conf and cleaning up any other conflicting drivers on your system.

Don't touch any other buttons, don't go to the restricted driver manager and enable anything, just do what envyng tells you to do and reboot.

---

### Post by Titan8990 on 2008-07-31
You should **ALWAYS** have the user backup their xorg.conf before having them delete it.

---

### Post by Daelyn on 2008-07-31
> **Titan8990 said:**
> You should **ALWAYS** have the user backup their xorg.conf before having them delete it.

I was just about to say the same. 

**BACK UP XORG.CONF FIRST!**

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pre-nv
```

---

### Post by Cresho on 2008-07-31
hey these are pretty good exiriences you guys posted.  Maybee because I use third party and main server packages, I have no problem.

The guy who posted about nvidia's drivers and reloading the drivers in a kernel change is correct.  The new kernel would need the drivers reinstalled.  It was not a hassle but it does bug me redoing the process.  Of course I had the option of not booting into the new kernel through grub.  always backup your xorg.conf

---

### Post by Cresho on 2008-07-31
> **Klingstedt said:**
> Hi everyone!
I was having some problems after screwing up my xorg.conf so my xserver didn't quite like me, but after alot of testing that didn't go as planed i succeeded and would like to share my solution with those who have the same problem! This mioght not be the best solution but it worked out for me so i'll give it a shot!

Forst off I installed Envyng, and you can find it here:
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

After that I started envy in terminal using:
```
sudo envyng -t
```

selecting option number 2 and ENTER

When the process is done I exited Envy and installed nvidia-settings using:
```
sudo apt-get install nvidia-settings
```

When done i removed my xorg.conf completely by typing following in terminal:
```
sudo rm /etc/X11/xorg.conf
```
and after that using nvidia-xconfig to create a healthy and new xorg.conf
```
sudo nvidia-xconfig
```

Now lets install the driver using envy again.

Press CTRL+ALT+F1, that will put you in a terminal window without GUI.
Login with your ordinary login.
Close the GUI window that's still running in CTRL+ALT+F7 by typing:
```
sudo /etc/init.d/gdm stop
```

Now start envy again.
```
sudo envyng -t
```

choose option 5 this time, allowing you to manually install the driver.
now choose option nr 2, NVIDIA
and when the next options pops up choose the one that says (latest) at the end, probobly option nr. 1

Envy should start installing the necessary things tomak your xserver look healty again, hopefully.

when this is done you will get an option to reboot your computer, type in y and press enter to do that.

HOPEFULLY your xserver is repaired and up and running as it should.

NOTE
The first part can also be done in CTRL+ALT+F1 if you can't access your xserver at all!

Please let me know if this works for you too or if you have other comments on the guide!
Thank you!

ill be using this method but I have a question

your nvidia-settings are not loaded at startup without the command

"system->prefference->sessions, you make new "nvidia" and you place this command for startup "nvidia-settings --load-config-only"."

how does envy handle placing this into sessions?  do a little test. open up your x server collor correction and reduce the brightness to  -1.00 and reboot.  if it still looks like that, then your saved settings are not being saved.  I am curious to see if envy configures the nvidia drivers to autoload at startup (dont forget to reset the brightness after the test is done)

---

### Post by Klingstedt on 2008-07-31
> **Cresho said:**
> ill be using this method but I have a question

your nvidia-settings are not loaded at startup without the command

"system->prefference->sessions, you make new "nvidia" and you place this command for startup "nvidia-settings --load-config-only"."

how does envy handle placing this into sessions?  do a little test. open up your x server collor correction and reduce the brightness to  -1.00 and reboot.  if it still looks like that, then your saved settings are not being saved.  I am curious to see if envy configures the nvidia drivers to autoload at startup (dont forget to reset the brightness after the test is done)

THe answer to your question is, atleast i think it is, that if you make a session with "nvidia-settings --load-config-only" it will load the correct config file for nvidia. So the only thing that has to be done is the thing about the session you mentioned to make that work :)

> **Daelyn said:**
> I was just about to say the same. 

**BACK UP XORG.CONF FIRST!**

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pre-nv
```

Thank you for reminding me i will add that to the howto :)

---

### Post by Titan8990 on 2008-08-02
Check your main article again. You have the steps for backing up xorg.conf **after** you have the user delete it.

---

