---
title: "Another Wacom Thread (Karmic)"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by jarame on 2009-11-01
So I have upgraded to 9.10, ran into a wireless issue but that was resolved after downloading and installing wireless adapter drivers. The issue I'm having right now is this:
[FONT=Courier New]
[/FONT][CENTER][FONT=Courier New]After upgrading to Ubuntu 9.10 Karmic Koala I read the terminal to see what exactly was going on. In the terminal during the upgrade I read something along the lines of "some packages have been rendered obsolete." I thought it wouldnt affect anything I really needed, so I booted up Gimp, plugged in my Wacom tablet, and came to realize that there aren't any drivers installed for my tablet anymore. I've been looking around but I cannot find any Karmic Koala Wacom drivers.[/FONT]

[LEFT]Any help?
[/LEFT]
[/CENTER]

---

### Post by Favux on 2009-11-01
Hi jarame,

The default linuxwacom packages for Karmic are version 0.8.4-1.  Both xserver-xorg-input-wacom & wacom-tools should be available through Synaptic Package Manager.  Just have it install them and reboot.

---

### Post by jarame on 2009-11-01
> **Favux said:**
> Hi jarame,

The default linuxwacom packages for Karmic are version 0.8.4-1.  Both xserver-xorg-input-wacom & wacom-tools should be available through Synaptic Package Manager.  Just have it install them and reboot.

They're all installed but still no dice. I've reinstalled and everything, checked the [FONT=Courier New]Extended Input Devices [/FONT][FONT=Verdana]in Gimp[/FONT] and my wacom tablet isnt even showing up in the drop down menu. Idk what else to look up or ask.

But thanks for the help

---

### Post by Favux on 2009-11-01
Hi jarame,

Sure, not a problem.  What Wacom tablet do you have?  Is it a usb tablet or what?

If you enter in a terminal:
```
lsmod
```
do you see 'wacom' in the output?

---

### Post by jarame on 2009-11-01
> **Favux said:**
> Hi jarame,

Sure, not a problem.  What Wacom tablet do you have?  Is it a usb tablet or what?

If you enter in a terminal:
```
lsmod
```do you see 'wacom' in the output?


Sorry for the late reply. I have a usb Wacom Bamboo tablet. This is the result of the command line you told me to try:

```
jarame@ubuntu:~$ lsmod
Module                  Size  Used by
usbhid                 38208  0 
wacom                  22276  0 
```I didnt copy of all the things that we arent looking for in this code.

---

### Post by Favux on 2009-11-01
Hi jarame,

OK, the linuxwacom usb kernel driver/module wacom.ko is being loaded.

Let's see if your tablet is recognized.  In a terminal enter:
```
dmesg | grep [Ww]acom
```
The output should contain some lines with wacom in it.

How new is your Bamboo?  What's it's model number?

---

### Post by jarame on 2009-11-01
```
jarame@ubuntu:~$ dmesg | grep [Ww]acom
[16876.424776] input: Wacom Bamboo as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input7
[16876.453093] usbcore: registered new interface driver wacom
[16876.453102] wacom: v1.51:USB Wacom Graphire and Wacom Intuos tablet driver

```

it's almost a year old. Model #: MTE-450A

---

### Post by Favux on 2009-11-01
Hi jarame,

It sure looks like everything should work now.  Does it work in Windows?  To rule out a hardware failure like a broken stylus tip.

To set up in Gimp see near the bottom of this [wiki]("https://help.ubuntu.com/community/Wacom").

If you want to use wacomcpl see the modified .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by jarame on 2009-11-01
> **Favux said:**
> Hi jarame,

It sure looks like everything should work now.  Does it work in Windows?  To rule out a hardware failure like a broken stylus tip.

To set up in Gimp see near the bottom of this [wiki]("https://help.ubuntu.com/community/Wacom").

If you want to use wacomcpl see the modified .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

Yes everything works correctly now, thank you very much for your time and help :] and again I am very sorry for replying late

---

### Post by SaintDanBert on 2009-11-01
> **jarame said:**
> 
Yes everything works correctly now, thank you very much for your time and help :] and again I am very sorry for replying late


Aaarrrggghhh!?!?

This thread died leaving me feeling that I missed "the miracle."
What did you do so that things work correctly now? What was not
quite right that suddenly became corrected?

Thanks,
~~~ 0;-Dan
... another wacom tablet guy ...

---

### Post by jarame on 2009-11-01
> **SaintDanBert said:**
> Aaarrrggghhh!?!?

This thread died leaving me feeling that I missed "the miracle."
What did you do so that things work correctly now? What was not
quite right that suddenly became corrected?

Thanks,
~~~ 0;-Dan
... another wacom tablet guy ...

oh, I upgraded to Ubuntu 9.10 from 9.04 and in the terminal during the upgrade it said some of my drivers/software packages are now obsolete. And the wacom drivers were included. Just read what Favux told me to do. Some how just checking to see if my wacom tablet is registered got it to work. So any terminal commands he told me to enter you should try them. or I can post them in order for you in a PM

~Glad to help, and thankful to be helped~
~Jarame

---

### Post by Favux on 2009-11-01
Hi jarame,

Great!  Glad it's working.  You're welcome.


Hi SaintDanBert,

What problems are you having with your Wacom tablet?

---

### Post by jarame on 2009-11-01
> **Favux said:**
> Hi jarame,

Great!  Glad it's working.  You're welcome.


Hi SaintDanBert,

What problems are you having with your Wacom tablet?

Would you be able to help get Photoshop working? Or is that out of your range of expertise? I'd really like to have it working

---

### Post by Favux on 2009-11-01
Hi jarame,

Sorry
> Or is that out of your range of expertise?
Yep.

I gather CS3 is relatively easy to get going in Wine but CS4 is fairly touchy.  Some claim to have it working.  There's several threads on that.  One was active recently.

---

### Post by jarame on 2009-11-01
> **Favux said:**
> Hi jarame,

Sorry

Yep.

I gather CS3 is relatively easy to get going in Wine but CS4 is fairly touchy.  Some claim to have it working.  There's several threads on that.  One was active recently.

Oh, okay that works. I shall go look it up. Thank you!

---

