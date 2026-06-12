---
title: "Asus VW161D Display and Dell Mini (Ubuntu)"
date: 2009-02-27
forum: Hardware
---

### Post by vickoxy on 2009-02-27
Hi,
i am student so i write a lot.This display is very affordable so i was thinking to buy it. Can anyone tell me do i need any adpter and does Dell Mini automatically adjust/support this resolution (1366x768) or i have to install some drivers (i have Ubuntu 8.04).
[http://www.asus.com/products.aspx?modelmenu=2&model=2223&l1=10&l2=152&l3=662&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2223&l1=10&l2=152&l3=662&l4=0)
[http://www.amazon.de/exec/obidos/ASIN/b001awb830/geizhals1-21/ref=nosim?m=A3JWKAKR8XB7XF](http://www.amazon.de/exec/obidos/ASIN/b001awb830/geizhals1-21/ref=nosim?m=A3JWKAKR8XB7XF)

---

### Post by vickoxy on 2009-03-02
Finally i ordered this display:
[http://geizhals.at/a387523.html](http://geizhals.at/a387523.html)

I am going to use this monitor as my main display on Dell Mini 9 (Ubuntu 8.04) when it´s plugged in. Can anyone tell me how well functions external diplay on Ubuntu (resolution settings, standby...). I am  newbie with linux, so i am little bit affraid and don´t know what to expect...

---

### Post by Menthu_Rae on 2009-03-05
Hey dude,

I feel sorry for you seeing nobody replied to your dell topic or this one! Anyway I have the same monitor :)

I don't have a Dell Mini, but I do have an Asus EeePC 901 running Ubuntu 8.04. The EeePC has an Intel 945GM graphics chipset. Not sure what your "Dell Mini" is running?

The way I got the external display to work for me was:

Edit xorg.conf...

```
sudo gedit /etc/X11/xorg.conf
```

Look for this section, and add the part in bold underline...

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection	"Display"
		Modes	"1366x768" "1360x768" "1024x600"
		**_Virtual	2048 2048_**
	EndSubSection
EndSection

```

Now save the changes and close gedit... restart x with:

```
control + alt + backspace
``` on your keyboard.

Log back in again, and now you should be able to turn it on with:

```
xrandr --output LVDS --auto --pos 0x0 --output VGA --mode 1360x768 --below LVDS
```

and off with:

```
xrandr --output LVDS --auto --output VGA --off
```

Let me know how that goes for you :)

BTW, I made it "easy" to do by right clicking --> editing the applications menu and adding 2 items with the above code as the command. So now I just go apps > system tools > VGA on and VGA off when I want it on/off.

Also FWIW, I found my computer didn't like booting up with the external display attached! If I attach it after booting and use xrandr, it's all good - but if it's attached when I boot, everything goes weird.

---

### Post by vickoxy on 2009-03-05
Menthu_Rae, thanks for answer. I am still waiting for my display to come, but i will post my experience....

Btw, i found here some suggestions how it works-i don´t know if it would function on my dell mini:
[http://www.ubuntumini.com/2008/10/mailbag.html](http://www.ubuntumini.com/2008/10/mailbag.html)

Notice: **Gunn** explains how to run on/off display whitout terminal... as i am novice in linux, this sounds nice to me

---

### Post by vickoxy on 2009-03-11
Today came my ney display-an its working out of the box :D. After start up Dell Mini adjust Screen Resolution to 1366X768 and it works just fine...
Refresh rate is 60GHz. I don know what that means but i read that lot of people want to change that. Is it important or not (i can not choose any other option)?

---

### Post by vickoxy on 2009-03-11
One question, though: i made in setup battery (or energy setup-i use german ersion "energieverwaltung") that my dell mini doesn´t go to slep ever. Still it goes after some time. Is there some other way to make this setups? And when i close up mini display it shut itself automatically (big display is active) - that is i suppose normal?

---

