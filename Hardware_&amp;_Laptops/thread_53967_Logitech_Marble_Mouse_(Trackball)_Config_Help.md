---
title: "Logitech Marble Mouse (Trackball) Config Help"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by KeplerNiko on 2005-08-02
I recently purchased a Logitech Marble Mouse (it is a **trackball**) for use with my laptop.  I have not been able to get it working in the same ways it functions in 
Windows.

[http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2150,CONTENTID=5003](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2150,CONTENTID=5003)

The normal behavior of the mouse is as follows:
Button 1: Large left-click button.
Button 2: Left-of-center smaller button for scrolling 3 lines DOWN
Button 3: Right-of center smaller button for scrolling 3 lines UP
Button 4: Large right-click button (on right)

Button 1 + Button 4: enable scrolling mode; scroll rate/direction depends on cursor's deviation from center

I've searched Google and messed with my /etc/X11/xorg.conf file countless times.  I've not found one catch-all solution for getting this mouse/trackball working; each person who claims to have gotten it working has done it a different way.

The problem seems to be that button 3 and 4 are viewed as identical by the computer.  When I run and test the buttons in **xev**, buttons 1 and 2 come up fine, but both 3 and 4 register as "Button 3."

Come to think of it, I don't think I've gotten 3 and 4 to function independently of each other yet, though I **have** gotten buttons 2 and 3 to do their respective functions.  I used a guide for a Microsoft Internet Explorer-something mouse (with "Back" and "Forward" internet buttons), and I remapped the controls from Alt-left/right to Up and Down, which was somewhat acceptable.  Unfortunately, the right mouse button also scrolled up.  I was able to accomplish this part through editing of the xmodmap file (don't remember exactly what all it entailed).

Can someone, who has gotten this trackball to work, post their xorg.conf file?  If not, how do I get the right mouse button to be identified separately from the center-of-right scroll button?  How do I assign each individual mouse button a separate function?  How do I get Buttons 1 and 4 to enable "scrolling mode" (something to do with "ChordButton")?

---

### Post by autocrosser on 2005-08-02
I don't know if I can help much--but I have a Logitech Trackman Wheel--I "set" for third button with---

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ChordMiddle"
        Option          "ZAxisMapping"          "4 5"
EndSection

Open your man xorg,conf & see what options you have for the  Option "Chord"

Of course, Logitech Support has this to say---
[http://logitech-en-amr.custhelp.com/cgi-bin/logitech_en_amr.cfg/php/enduser/std_adp.php?p_faqid=72&p_created=1083959151&p_sid=PPnkM1Mh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzImcF9wcm9kcz00LDAmcF9jYXRzPSZwX3B2PTEuNDsyLnUwJnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1MaW51eCBzdXBwb3J0&p_li=&p_topview=1](http://logitech-en-amr.custhelp.com/cgi-bin/logitech_en_amr.cfg/php/enduser/std_adp.php?p_faqid=72&p_created=1083959151&p_sid=PPnkM1Mh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzImcF9wcm9kcz00LDAmcF9jYXRzPSZwX3B2PTEuNDsyLnUwJnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1MaW51eCBzdXBwb3J0&p_li=&p_topview=1)

Typical B.S.--I'd E them a ask why they don't support Linux--- \\:D/

---

### Post by autocrosser on 2005-08-02
OK--on further search results I've found a reference to evdev--I don't know what operatability we have in Unbuntu, but take a look at this--
[http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46)

This "looks" like what you are looking for---

Mine works fine with the xorg.conf I've set-up--so I claim no knowledge as if this "patch" works, but it looks hopefull---

---

### Post by KeplerNiko on 2005-08-02
I see the TrackMan Wheel has "three customizable buttons."  How many buttons are there total, excluding the wheel click--two, or five?  (It looks like just left-click and right-click, plus the wheel.)

I would imagine left-click and right-click worked without any problems from the start.  Ditto for the scroll wheel.  If the trackball does have buttons other than those (can't tell from the pictures), does that xorg.conf file get them working?  Do they function how they should, like they do in Windows?

---

### Post by autocrosser on 2005-08-03
It only has two buttons plus the scroll-wheel press--I set-up both press for "Chord middle" or third button & I can't define the scroll-wheel depress :???:

Works very well for me---I need the "third button" in The Gimp ;-)

---

### Post by byen on 2005-08-30
whoa..just got this mouse...the left click and right click works perfectly...did anyone get the 3 and 4 buttons to work? Can anyone help me here...here is the mouse part of my Xorg:

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"

here is the link of what my mousey looky likey....
[http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2150,CONTENTID=5003](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2150,CONTENTID=5003)
If someone is using the same...can you please post your Xorg-mouse please ...thanks guys.

---

### Post by byen on 2005-08-31
:-( nobody? oh man...has anyone atleast configured a 5 button mouse?...how can i configure other buttons to do custom functions? any sugg?
thank you.

---

