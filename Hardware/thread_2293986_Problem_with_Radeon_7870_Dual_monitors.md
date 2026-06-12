---
title: "Problem with Radeon 7870 /Dual monitors"
date: 2015-09-09
forum: Hardware
---

### Post by Carmine_Esposito on 2015-09-09
I am new to ubuntu and trying to learn how to do this so I can get away from the evil of Windows. 
So I recently tried to install my drivers for my video card and I ended up messing it up and having to reinstall the OS 14.04 x64 bit. So now I ask if there is anyway I can have some direction with this. Furthermore I run two monitors anyway I can get instructions for that as well.

---

### Post by QIII on 2015-09-09
Hello!

Can you describe what you did in your attempt to install the driver?

Did you download it from AMD or did you use the driver in the Ubuntu repository?

---

### Post by Carmine_Esposito on 2015-09-09
I downloaded from the amd website and installed via the .deb files. Than when I restarted it would not boot up at all

---

### Post by QIII on 2015-09-09
I recommend installing from the repository via the additional drivers menu or manually via the terminal.  The driver in the repository is exactly the same proprietary driver as the one from the AMD site that was available at the time the release of Ubuntu was released.  Every 4th and 10th month, AMD makes the driver available to Canonical in time to make sure it is included.  This often happens before the rest of the Linux world has access to the driver.

Please see the ATI wiki in my signature.  It describes how to install it from both the GUI and the command line.  I prefer the command line because it offers feedback you can cut and paste back here if you have problems.  That's in Section 3.1.

Also have a look at Section 5 for how to install the modest hardware acceleration available in the Linux driver.

If either of those sections leaves you scratching your head, we can help you through it if you post your questions back here.

The most common reason for problems is failing to initialize the driver.  Although this is no longer *supposed* to be required, I answer this question often enough to just say do it anyway.

Once the driver is installed, we can work through setting up your monitors correctly in the Catalyst Control Center.

Here, by the way, is my triple monitor setup with the fglrx driver:

[http://imgur.com/XxBXmsL](http://imgur.com/XxBXmsL)

---

### Post by Carmine_Esposito on 2015-09-09
Thank you for your help I have gotten most of it to work the only thing I am having trouble with is I can't seem to figure out how to get my mouse over to the other monitor via going right rather than going left. Any ideas how to fix that?

---

### Post by QIII on 2015-09-09
If you are using Ubuntu (Unity) go to the dash and type "Catalyst".  You should be presented with the choice of the Catalyst Control Center in either Administrative or normal mode.  Choose Administrative and enter your password.

Go to display manager.

[ATTACH=CONFIG]264315[/ATTACH]

Select the "Multi-Display" tab and select "Multi-display desktop with ..."  The fish should be pretty obvious.

Above that, you'll see where my three screens are laid out.  Don't worry that they are not in order.  That's just how the cables are connected to the ports.

You can drag the displays around until you get them in the order you want from left to right.  Take a bit of care to get them lined up, or you can sometimes get odd artifacts.

---

### Post by Carmine_Esposito on 2015-09-09
You have been awesome thank you very much man I appreciate the help

---

### Post by QIII on 2015-09-09
That's what we're here for!

Cheers!

---

