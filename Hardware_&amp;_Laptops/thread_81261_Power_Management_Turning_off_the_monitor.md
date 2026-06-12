---
title: "Power Management: Turning /off/ the monitor?"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by jrronimo on 2005-10-24
Is there a way to get the monitor to actually turn 'off' on a laptop? Currently, the screen blanks, but it's still powered. I don't know about other laptop users, but this is bad for me in two ways:

1. SO. MUCH. HEAT. My inverter runs very warm and being on for hours does NOT help at all.

2. Wasted battery power!

#1 is a problem all the time. Sometimes I just want my laptop to be on but not active -- if I'm chatting but don't want to be 'there', or if I go to another room or something.

#2 is a problem some of the time -- I've been using my laptop as my MP3 player ever since my iPod ate it, which usually means I put on some songs and toss the lappy in my laptop backpack and go to school. With the monitor on the whole time, it's just a complete waste of electricity. Also, it gets warm, but, well, see #1.

I know some people don't want this behavior because they are worried about burning their inverter out due to constant power-ups/offs, but, well, that's a risk I'm prepared to take. Perhaps it could be an a setting somewhere where a user chooses to or not to have this behavior.

---

### Post by nocturn on 2005-10-24
It is not default behavior.

It's a bug (unknown cause) on some laptops, including mine (HP Pavilion ZV5474EA).  My Dell laptop at work powers down the LCD with the LiveCD fine.

I have a Bugreport open here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=13163](https://bugzilla.ubuntu.com/show_bug.cgi?id=13163)

---

### Post by bryan986 on 2005-10-24
If you open xscreensaver and goto the Advanced tab, there are some nice options

You cant turn it off manually, but you can select it to standby/suspend/turnoff the monitor after a few minutes

Turn off actually does turn off the monitor as far as I can tell...unless I am mistaken

---

### Post by techflat on 2005-11-03
Hi there.
I had the same problem you had only in a desktop...

I was kind of :confused: and ](*,) but with a little pathience I found out that there is a line in the xorg.conf (/ets/X11/xorg.conf) that was missing for me

Probably because I installed some ati drivers that modified my xorg.conf.

So, what I did was to insert this line
    Option      "DPMS"       inside ( Section "Monitor" )

something like this:

Section "Monitor"
    Identifier  "VP191b"
    Option      "DPMS"
(...)
EndSection



This worked for me, hopefully it'll work for you too.

---

### Post by jrronimo on 2005-11-03
[QUOTE=techflat]Hi there.
I had the same problem you had only in a desktop...

I was kind of :confused: and ](*,) but with a little pathience I found out that there is a line in the xorg.conf (/ets/X11/xorg.conf) that was missing for me

Probably because I installed some ati drivers that modified my xorg.conf.

So, what I did was to insert this line
    Option      "DPMS"       inside ( Section "Monitor" )

something like this:

Section "Monitor"
    Identifier  "VP191b"
    Option      "DPMS"
(...)
EndSection



This worked for me, hopefully it'll work for you too.[/QUOTE]


Examining my xorg.conf shows that I do indeed have that already:

```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
Endsection

```

I've tried fiddling with the screensaver settings, but the screen is always powered. :(

---

### Post by techflat on 2005-11-03
that sux...

You could try

xset dpms force off

If that doesn't work for you, I'm guessing your problem isn't in the xscreensaver configuration. (just a guess, cause I think it would be the same as the xscreensaver turning of you computer.)

---

### Post by jrronimo on 2005-11-03
Yep, all that does is blank the screen, but the screen is still lit -- i.e., the backlight is still on.

---

### Post by Copter on 2005-11-06
same goes here on LG GS50. when i close the lid, backlight is off but still dont know how to turn it off from the konsole // via screensaver

copter :]

---

### Post by bschuteker on 2006-01-24
[QUOTE=jrronimo]Yep, all that does is blank the screen, but the screen is still lit -- i.e., the backlight is still on.[/QUOTE]


I have the same problem. I have a Dell D800 and I am currently working in Iraq. I leave the computer on at night so that my Wife can IM me if she needs to. It sits right next to my bed so In windows I just set power management to blank the screen after 1 minute. When I go to Ubuntu screen saver options under advanced I have 3 options. Standby, Suspend, Off, they all do the same thing the screen goes blank but the backlight stays on. This is actually rather bright in a very dark room and I also worry about the life of the backlight. 

Thanks in advance,

Bill

---

### Post by skindurica on 2006-03-21
Edit: **/etc/X11/xorg.conf**

Add to 
**Section "ServerLayout"**
**Option "OffTime" "3"**
3=minutes
(other options might be: "SuspendTime" and "StandbyTime" which i did not test)

Save
Hit "ctrl+alt+backspace" to/or restart xserver

I found out about this on gentoo wiki.

---

### Post by ubmac on 2007-01-21
Same problem in a "Trident Microsystems CyberBlade i1"

---

