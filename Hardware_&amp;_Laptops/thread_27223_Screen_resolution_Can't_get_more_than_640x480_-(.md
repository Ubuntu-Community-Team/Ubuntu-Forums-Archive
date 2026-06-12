---
title: "Screen resolution: Can't get more than 640x480 :-("
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by koschder on 2005-04-15
Well, I am a Linux newbie and don't know much of editing my xorg.conf by hand...

The thing is, I can't seem to get a resolution higher than 640x480, and I have no idea why  :???:   I tried running sudo dpkg-reconfigure xserver-xorg, looked up and entered the correct refresh rates for my monitor, but still only a measly 640x480 res...

I'm attaching my xorg.conf as a .txt file - it would be very sweet if someone could have a look at it and tell me what might be wrong here.

Oh yeah, running Kubuntu 5.04, and both monitor and graphics card are correctly detected.

---

### Post by skwid on 2005-04-15
[QUOTE=koschder]Well, I am a Linux newbie and don't know much of editing my xorg.conf by hand...

The thing is, I can't seem to get a resolution higher than 640x480, and I have no idea why  :???:   I tried running sudo dpkg-reconfigure xserver-xorg, looked up and entered the correct refresh rates for my monitor, but still only a measly 640x480 res...

I'm attaching my xorg.conf as a .txt file - it would be very sweet if someone could have a look at it and tell me what might be wrong here.

Oh yeah, running Kubuntu 5.04, and both monitor and graphics card are correctly detected.[/QUOTE]
 I am not sure but I would probably remove all of the sections except for the 24bit depth section, then remove all resolutions except the one you want to run at.  That's how I do it.

Skwid

---

### Post by heimo on 2005-04-15
I'd try:
```
 
Section "Monitor"
 Identifier "CPD-210EST"
 Option  "DPMS"
 HorizSync  30-70
 VertRefresh  48-120  
EndSection

``` 
 
Some useful information on this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")

---

### Post by koschder on 2005-04-15
[QUOTE=heimo]I'd try:
```
 
 HorizSync  30-70
 VertRefresh  48-120  

``` 
[/quote]
 
Sweet  :)  That did the trick - thanks a bunch, mate! :grin: 

Though that leaves me wondering: Shouldn't these values be automatically written to xorg.conf when I run dpkg-reconfigure xserver-xorg?  :-?

---

### Post by heimo on 2005-04-15
This seems to be common problem, automatic detection not doing its job properly. I had to do manual configuration myself and seems like lots of people have to do it, But it shouldn't go like this. It's possible to autodetect most monitors and set the correct values.

---

