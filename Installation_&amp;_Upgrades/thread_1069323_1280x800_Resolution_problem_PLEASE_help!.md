---
title: "1280x800 Resolution problem PLEASE help!"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by bigslick148 on 2009-02-13
Hi All,

I am brand new to Ubuntu, so please bear with me.  I have an Everex Stepnote NM3500W laptop, which likes to display a 1280x800 resolution.

This option is in the resolution choices, but does not work.  I'm simply stuck at : 1600 x 1200

Anybody know what I can do to improve this?  I can cut & paste any log or information that may help you.

Please help!
Thanks!

---

### Post by bigslick148 on 2009-02-13
FYI 

The laptop display adapter is a VIA/S3G UniChrome Pro IGP

---

### Post by crunchfighter on 2009-02-13
I'll ask the easy question: did you try 
System->Preferences->Screen Resolution ?

---

### Post by Taemojitsu on 2009-02-13
you may need proprietary drivers. try installing them and it might fix it.

what's the default resolution? your laptop might scale resolutions in different ways; 'cutting off' the screen sounds like compensating for an incorrect resolution. So what's the one it puts you at in preferences\Screen resolution?

---

### Post by bigslick148 on 2009-02-13
> **crunchfighter said:**
> I'll ask the easy question: did you try 
System->Preferences->Screen Resolution ?

Yes sir, I have.  It is listed, but does not work when selected.

---

### Post by Ericyzfr1 on 2009-02-13
I also have 1280x800 which corresponds to 16:10. You don't have anything listed that would match that?

---

### Post by bigslick148 on 2009-02-13
> **Taemojitsu said:**
> you may need proprietary drivers. try installing them and it might fix it.

what's the default resolution? your laptop might scale resolutions in different ways; 'cutting off' the screen sounds like compensating for an incorrect resolution. So what's the one it puts you at in preferences\Screen resolution?

Ok.. currently it is displaying at 1600x1200

Also, I must note that it does have 1280x800 in the drop down ( I was incorrect in stating that it did not) but when I select it, I cant read anything because the screen is fuzzy & not legible.

---

### Post by bigslick148 on 2009-02-13
> **Ericyzfr1 said:**
> I also have 1280x800 which corresponds to 16:10. You don't have anything listed that would match that?

See above post... I do have it but it does not work.  I'm stuck at 1600x1200 so I can't see the right hand side & bottom of the screen.

---

### Post by Taemojitsu on 2009-02-13
mm it doesn't have a dedicated graphics card... so much for new drivers. You could try calling support from whom you bought it from, if they like Linux (doubtful). There aren't many variables in setting screen resolution, but it's possible the LCD screen is hard to interface with some reason preventing it from sending the right resolution... being blurry sounds like some weird downscaling/upscaling issue... if you can't get the answer here, maybe try hardware support? Either on these forums or if you can find the laptop manufacterer forum.. :/

---

### Post by Ericyzfr1 on 2009-02-13
Did you install from the Live CD? Did you have the right screen resolution then?

---

### Post by bigslick148 on 2009-02-13
> **Ericyzfr1 said:**
> Did you install from the Live CD? Did you have the right screen resolution then?

I did install from the Live CD, but I cannot remember if the resolution was correct at that time.

I guess I could run from the Live CD again & let you know?

---

### Post by Ericyzfr1 on 2009-02-13
Please post it.

---

### Post by bigslick148 on 2009-02-13
> **Ericyzfr1 said:**
> Did you install from the Live CD? Did you have the right screen resolution then?

I just booted from the Live CD and I have the exact same issue.  :(

---

### Post by redroad55 on 2009-02-13
This will bring up the list of supported resolutions for your current setup:

> sudo xrandr -q

then run this command with the desired resolution from the list provided by the command.. For example if 1280x800 is your desired resolution then :

> sudo xrandr -s 1280x800

I had to do this next step to get it to stick for longer than the current session..

exit terminal > go to applications  > system > preferences > screen resolution > the resolution you chose in terminal should be there now > now hit apply > choose keep > then close > that is what worked for me .. Post back with any results and or questions  .. Best to you

---

### Post by bigslick148 on 2009-02-14
> **redroad55 said:**
> This will bring up the list of supported resolutions for your current setup:



then run this command with the desired resolution from the list provided by the command.. For example if 1280x800 is your desired resolution then :



I had to do this next step to get it to stick for longer than the current session..

exit terminal > go to applications  > system > preferences > screen resolution > the resolution you chose in terminal should be there now > now hit apply > choose keep > then close > that is what worked for me .. Post back with any results and or questions  .. Best to you

Thanks for the help, but it just looks all fuzzy & messed up when I go to 1280x800.

Weird....

Why does Windows XP look perfect at 1280x800 but Ubuntu won't work? :confused:

---

### Post by bigslick148 on 2009-02-14
Anybody??? :confused:

---

### Post by redroad55 on 2009-02-14
so when you go to proprietary driver , what does it list ?

---

### Post by bigslick148 on 2009-02-14
> **redroad55 said:**
> so when you go to proprietary driver , what does it list ?

Please let me know how to find it & I will let you know!

---

### Post by redroad55 on 2009-02-14
application > system > admin. > hardware drivers > enter password > copy list of drivers > list back here or enable reccommended video driver if present

---

### Post by bigslick148 on 2009-02-14
> **redroad55 said:**
> application > system > admin. > hardware drivers > enter password > copy list of drivers > list back here or enable reccommended video driver if present

The only thing listed there is my wireless card driver... that is it.

---

### Post by bigslick148 on 2009-02-15
FIXED IT!

Here is how I did it :  

Follow these instructions to the T
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Here is my new xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
	Option    "XaaNoImageWriteRect"
	Option "SWCursor" "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
		Virtual 1280 800
        EndSubSection
EndSection

---

### Post by pgedeon on 2010-12-05
any how to on 10.10?

---

