---
title: "Asus a8jr hotkeys"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by fotzlapen on 2007-10-03
Heya!

I'm having major issues with my asus a8jr acpi functions.  I'm running from a clean install of Gutsy.  My first problem is that my laptop has 2 hotkeys (Fn-F5 and Fn-F6) for screen brightness.  The one that turns the brightness down works fine but the one that turns the brightness up doesn't work.

I read through this post:

[https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch)

And found that using xev the keypress for Fn-F6 doesn't register at all.  Which really leaves me at a loss.  The best I can think to do is make some scripts that will write straight to the /proc/acpi/asus/brn socket.  But these still won't work with the hotkeys if they don't register any value at all in xev.  Does anyone have any ideas about what could cause this?

Also having issus with suspend and hibernate, but that needs some more investigation.

Cheers!

---

### Post by pilotet on 2007-10-19
Hi!
I have a A8Jr with Gusty too.
Just add the brightness control to your panel.

Can you use the 1440x900 resolution?
It's the only problem I have.

Cheers.

---

### Post by kentborg on 2007-10-19
I am running Gutsy on a Panasonic W4, and I am having the same problem: apcid doesn't seem to see my hotkey presses at all.  When I boot back to Feisty and it works there.

Tried running "acpid -d -d -d -d" by hand and I get no output when I press the hot keys.  Nothing shows up in /var/log/acpid either.

Suggestions anyone?

Thanks,

-kb

---

### Post by kentborg on 2007-10-20
Fixed it.  I booted into Feisty and compared lsmod output.

Turns out Gutsy doesn't load the pcc_acpi module.  I added it to /etc/modules.

Seems like a Gutsy bug...

-kb

---

### Post by fredylee on 2007-10-21
> **pilotet said:**
> Hi!
I have a A8Jr with Gusty too.
Just add the brightness control to your panel.

Can you use the 1440x900 resolution?
It's the only problem I have.

Cheers.

The laptop as mine...
The highest resolution I can have is 1280X800
I Cann´t open special Desktop Effect

How is your Webcam ?
Is it work? That´s the most important problem I have so far

---

### Post by pilotet on 2007-10-22
Hi fredylee!
Could you post your xorg.conf?

In order to use Extra Special effects you have to install the ATI drivers.
Here I post you the method that has worked for me:
1. 
      sudo apt-get update
      sudo apt-get install linux-restricted-modules-generic restricted-manager


2. System > Restricted drivers
3. Enable the ATI drivers
4. Don't reboot and install all Compiz Fusion extras with:
5. sudo apt-get install xserver-xgl
6.
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
7. Reboot

Now I'm going to test the webcam

---

### Post by fredylee on 2007-10-22
> **pilotet said:**
> Hi fredylee!
Could you post your xorg.conf?

In order to use Extra Special effects you have to install the ATI drivers.
Here I post you the method that has worked for me:
1. 
      sudo apt-get update
      sudo apt-get install linux-restricted-modules-generic restricted-manager


2. System > Restricted drivers
3. Enable the ATI drivers
4. Don't reboot and install all Compiz Fusion extras with:
5. sudo apt-get install xserver-xgl
6.
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
7. Reboot

Now I'm going to test the webcam

Hey, many thanks for your instruction, It works perfectly...
How to get the xorg.conf file ?
I donn't know where it is...
How is your webcam?
The device number of my webcam is Bus 003 Device 002: ID 174f:aa11 
How about yours ?

---

### Post by fredylee on 2007-10-22
Hey This is my xorg.conf
Hope it helps.

---

### Post by pilotet on 2007-10-22
Hi!
In which file do you see this information?

---

### Post by pilotet on 2007-10-22
Hi fredylee!
Your conf has worked fine for me!

Tell me if you want to post some file here.

Thank you!

---

### Post by fredylee on 2007-10-22
What's the device number of your webcam ?
 

input lsusb in ternimal....

My webcam is in a very strange code so I can't find the driver for it...

---

### Post by fotzlapen on 2007-10-28
> **pilotet said:**
> Hi!
I have a A8Jr with Gusty too.
Just add the brightness control to your panel.

Can you use the 1440x900 resolution?
It's the only problem I have.

Cheers.
My native res is 1280x800.  I don't think theres an a8jr with a higher res.

Thanks Kentborn, I'll have a go at that!

---

### Post by Mr.Mechano on 2008-01-08
The function key Fn-F1 suspend to ram works perfectly installing the ATI drivers downloaded from ATI/AMD website.

I downloaded the latest drivers for X1900 graphic card, removed the Gutsy non-free drivers and started the ATI installer.

Now the system suspend and resume perfectly. Sometimes the internal ipw3945 card wakeup with off radio and wifi network connection is down, but it's sufficient to switch radio on with its key and enable network again.

This lapto is awesome with Linux, everything work: wifi, webcam, irda, bluetooth, modem, ATI X2300 card, the built-in SD MMC MS drive, suspension in ram, the only function I didn't try was the hibernate on disk.

---

### Post by gloval on 2008-01-25
hi, i am a newbie when it comes to linux, how do you install the driver for the ati?

---

### Post by Snyde on 2008-01-25
Hi,

One of my problem is exactly the same as the one described in the very first message of that post.My configuration is Ubuntu Gutsy running on an ASUS A8Js. So the following keys are not working for me:
- Fn+F1 (sleep mode, send my computer to sleep but doesn't wake it back up)
- Fn+F2 (wireless / bluetooth switch, even if both works fine)
- Fn+F6 (doesn't increase screen brightness, even if the Fn+F5 hotkey for decreasing it works perfect)

and while we are at it I don't even know whether my built-in webcam works or not, where do I check this out, is there a configuration panel somewhere?


Thanks in advance for your answers. Hope my registration on this US-based forum will be up to my expectations, I have been waiting for answers (any answers) from a French forum for a week now :-/.

Best Regards to you all Ubuntu creators and support crew, your dedication is appreciated, Keep up the great work.

---

