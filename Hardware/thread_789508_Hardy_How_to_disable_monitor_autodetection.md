---
title: "Hardy: How to disable monitor autodetection?"
date: 2008-05-10
forum: Hardware
---

### Post by ljp37 on 2008-05-10
Does anyone know how to disable monitor autodetection when starting a Gnome session in Hardy?  Briefly: It's overriding my custom xorg.conf with a broken configuration.

The "Screen Resolution" control panel is broken too.  I have a 1920x1200 external monitor,  but the only offered is 1024x768 cloned.  Unchecking the "Clone Screens" checkbox doesn't work: the next time I open the control panel, it's checked again.  Clicking the "Detect Displays" button causes the screen to blank for a second, but it fails to identify the two displays.

Monitor autodetection overrides any changes I make to xorg.conf... so I'm having trouble fixing this configuration problem manually.

And:  Where did the information that used to be in xorg.conf go???  The default produced by dpkg-reconfigure xserver-xorg just says "Configured Video Device" now, and I don't even know which video driver it's using!  [I've since used Xorg -configure to get a more normal xorg.conf]

This is a Toshiba Portege M400, with Intel 945GM graphics (intel or i810 driver)



Anyway, thanks for reading my rant, may your xorg be working better than mine =)

---

### Post by Arthur Archnix on 2008-05-10
[IMG]http://i256.photobucket.com/albums/hh197/ArthurArchnix/relevantinterests.jpg[/IMG]

I'm trying to find documentation about the changes made from Gutsy to Hardy. Video card information is no longer in xorg.conf, so how / where is Hardy determining this information? What file do we edit to make persistent changes? How is xorg.conf read, in what order, and priority?

Something as basic as xorg.conf, I can't believe how hard it is to find some explanation other than "we've made it easier".

---

### Post by starcannon on 2008-05-10
I haven't made much progress here either, I was talking to someone on xchat a few days ago, and he was making progress using the xrandr command, I'll be looking at that myself this week

---

### Post by ljp37 on 2008-05-10
Yeah, I've managed to get 1920x1200 using xrandr*, but it's going to be annoying to issue this command every time I log in.




*[specifically, xrandr --output TMDS-1 --auto]

---

### Post by Arthur Archnix on 2008-05-15
After looking into this at greater length, I believe all you need to do is create an xorg file with the settings you want. When the xserver detects an xorg.conf file it will use that to apply any settings provided, then, it will attempt to automatically detect anything above and beyond that. If you specify all your hardware and settings then there'll be nothing more to detect. 

I do not believe you can completely disable the autodetection, only override it with your own settings.

I learned this by chatting with fedora developer wwoods on #fedora. Though, I may have misunderstood what he was saying to me, so don't hold him responsible for my mistakes.

---

### Post by peterthewolf on 2008-05-15
I tried moving the screen modes from gutsy xorg.conf to hardy - no effect whatsever

---

### Post by MatusZ on 2008-05-15
Have you tried Screen and Graphic center in Gnome??
Worked perfect for me

---

