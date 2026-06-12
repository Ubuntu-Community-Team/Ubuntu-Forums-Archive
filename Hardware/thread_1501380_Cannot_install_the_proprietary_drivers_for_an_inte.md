---
title: "Cannot install the proprietary drivers for an integrated Nvidia Geforce 6100 GPU."
date: 2010-06-04
forum: Hardware
---

### Post by salvalinux on 2010-06-04
This happened after I took out a Nvidia graphics card from the motherboard.
This still happens until now.
I am using 64 bits Ubuntu 10.04.
The drivers appears to install correctly with the Hardware Drivers program.
The recommended driver nor the 173 on works.
It used to work on Karmic (I do not remember which version of the drivers).
In Failsafe X mode says: Fatal error: No screens found.

---

### Post by pedro_orange on 2010-06-04
> **salvalinux said:**
> This happened after I took out a Nvidia graphics card from the motherboard.
This still happens until now.
I am using 64 bits Ubuntu 10.04.
The drivers appears to install correctly with the Hardware Drivers program.
The recommended driver nor the 173 on works.
It used to work on Karmic (I do not remember which version of the drivers).
In Failsafe X mode says: Fatal error: No screens found.

Can you please describe what happens when you attempt to activate the proprietry drivers? (Eg; The recommended driver) 

At a last ditch chance have you tried installing the drivers using something like envy/jockey or even doing them manually?

---

### Post by salvalinux on 2010-06-04
I use the jockey-gtk program to install the drivers. When I install them in by that program, it installs it successfully.
Since when I try to start in failsafe mode I get a message to look at the Xorg.0.log file.
I am linking the content of this file in here in the case you want to know it: [http://pastebin.com/JC44niXr](http://pastebin.com/JC44niXr)
I also tried issuing this: *"dpkg*-*reconfigure* xserver-xorg" in order to fix that but I got the same error again.

---

### Post by salvalinux on 2010-06-04
Also, this thread should now be named: "Cannot get my integrated Nvidia Geforce 6100 GPU to work with the proprietary drivers.".

---

### Post by pedro_orange on 2010-06-04
Can you please pastebin your xorg.conf. 
It seems that you have no screens configured!

```
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
        Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
        Using a default monitor configuration.
``` 

Now this should be automatic in the newer versions of Ubuntu, but it may not hurt to explicitly tell xorg what screen resolution you wish to run. 
I had issues a few years back with xorg.conf and I found the problem was I was not specifying any compatible resolutions between my monitor / video card.

There are plenty of examples of xorg.conf on the Internet. Do you only have 1 monitor connected?

---

### Post by thewooleymammoth on 2010-10-13
I am having a very similar issue with 10.10. After searching around for a while this was the closest thread i could find. Anyways I ended up renaming my xorg.conf file and then running startx. Started right up. Thought i would throw this up just in case other people were looking and came across this.

here are the commands:
sudo mv /etc/X11/xorg.conf /etc/x11/xorg.conf.old

startx

Good luck

UPDATE**

I cant get effects to work, creating a new xorg.conf switched me back to the generic driver. Trying to get cube to work requires normal or extra effects, this cannot be achieved with the generic driver. Any help appreciated.

---

### Post by thewooleymammoth on 2010-10-13
I am using an aspire 5745g with nvidia 330m and ubuntu 10.10. I solved the problem by changing a setting video card "discreet" setting in my bios. It was set to switchable and is now set to discreet.

---

