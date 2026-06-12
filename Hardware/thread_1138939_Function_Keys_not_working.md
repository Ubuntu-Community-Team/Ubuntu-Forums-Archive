---
title: "Function Keys not working"
date: 2009-04-26
forum: Hardware
---

### Post by riskyayush on 2009-04-26
Hi, 
I am using Intrepid on my Toshiba Satellite L305.

The issue with my laptop is that all the function keys are not working. Do I need to change some setting or will it never work with Ubuntu?

Thanx

---

### Post by KhurramM on 2009-04-26
Try out:

System > Preferences > Keyboard

Check that the LAYOUT and KEYBOARD MODELS are correct, as specific to your hardware.

Adios

---

### Post by riskyayush on 2009-04-26
> **KhurramM said:**
> Try out:

System > Preferences > Keyboard

Check that the LAYOUT and KEYBOARD MODELS are correct, as specific to your hardware.

Adios
I dont have the same model as mine, but I do have a Toshiba S3000. Still no function keys.

---

### Post by swinky on 2009-05-07
I've got a Toshiba Satellite L305-S5891, and my function keys don't work, either. I've done a *ton* of independent research on my laptop and have come to the conclusion that, for one reason or another, Ubuntu doesn't realize that the function key (fn) is being pressed at all. I don't know how to fix that.

I ended up developing my own workaround for it. Instead of using the fn key I use the super (Windows) key, so for example for brightness down, usually fn+F6, I now press super+F6 and achieve the same result.

The workaround is definitely some effort, but the basics is that you install xbindkeys (which allows you to bind key combinations to different actions) and keytouch (which installs acpi related programs, I think, that interface with the brightness events.) 

The steps are:
[LIST=1]
[*]Change keyboard settings to allow use of the super key, using xmodmap
[*]Use xbindkeys to map super+F keys to desired commands. For example, the command for brightness is acpi_fakekey [keycode]. You can install the lineakd package and use evtest to figure out what the keycode that changes brightness is.
[*]Set xbindkeys to run (as root) when the computer boots. You have to start it as root because acpi_fakekey has to have root privileges.
[/LIST]

I wrote a more in-depth blog post about it which can be found at [http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html]("http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html"). Admittedly the directions are a little rough, I wrote it while exhausted (I had spent the previous three or so hours trying to finish my workaround), and am working on making it a little easier to follow, especially for those who have slightly different models of L305s.

---

