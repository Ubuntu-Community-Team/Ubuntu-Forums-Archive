---
title: "Help!"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by Mohammad Ansarin on 2006-05-29
Hi

I just got my ubuntu from the mailing service (THANK U!) and i try to start it with the live cd, and the ubuntu loader starts and all but after loading when it's sopposed to display something like the welcome screen the screen goes funny and displays a bunch of colorful vertical lines. my vga card is nvidia fx 5500. should i install linux? should i get a new vga card? should i forget linux altogether? ( :( ).

thanks

bye

---

### Post by Pilsner on 2006-05-29
Hello Mohammad.

It is not dangerous to install ubuntu linux 5.10 version. I have no idea what Live cd is for. Is that for "look and try"?

I see here your graphiccard is supported [http://doc.gwos.org/index.php/Nvidia/GeforceFx]("http://doc.gwos.org/index.php/Nvidia/GeforceFx")

Strange.. Well. Maybe you have a very old monitor?

---

### Post by RRS on 2006-05-29
> I have no idea what Live cd is for. Is that for "look and try"?

Exactly, gives you a chance to "test drive" without installing anything to your system to be sure you're comfortable before performing an installation.

It's also a good way to test hardware compatibility beforehand too, which is obviously a good thing in your case.

When you do your actual installation you'll probably need to install the driver for your graphics card. There's plenty of info available in these forums on how.

In the meantime to use the live cd try this:
ctrl-alt-F1,  this should open a terminal screen giving you a command prompt.
@ the prompt;
```
dpkg-reconfigure xserver-xorg
```
This will take you thru a series of setup steps (simple yes/no box's). You can choose the default for most of these.

When it asks for a video card driver select Vesa, this usually works well as a generic default.

When done enter;
```
/etc/init.d/gdm restart
```

This should give you a GUI in a viewable formatt. 

Unfortunatly I don't know of anyway to "save" these settings on the live cd so you'll have to go thru this everytime you run it.

If this works for you it will also work after installation to give you a useable system till you have a chance to install the correct driver for your card.

The live cd will also help find any other potential "bugs" so that when you do your installation you'll be ready to make any other changes needed to get your system fully operational.

Hope this helps and welcome to Ubuntu :)

---

### Post by soapytheclown on 2006-05-30
hey! 
ive had the same problem with like the monitor throwing out like blocks of blue or yellow vertical strips, when trying to run the live cd. I have a Geforce 6600.

i managed to get the 

sudo dpkg-reconfigure xserver-xorg

and run through that setting up the card, but when it comes to doing the gdm restart it says only "root wants to restart gdm"

"su gdm restart" asks for a password, so my question is, does anyone know the password?:confused:?

i really want to try the live cd before installing ubuntu, because i need an easier OS than slackware which is Crazy hard to use :( and i want to see this in action!

\\:D/

THANKS (Y)!

---

