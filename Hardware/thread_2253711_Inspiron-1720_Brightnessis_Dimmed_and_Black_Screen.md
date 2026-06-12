---
title: "Inspiron-1720 Brightnessis Dimmed and Black Screen"
date: 2014-11-21
forum: Hardware
---

### Post by pokedadude on 2014-11-21
Alright so I have a dell Inspiron-1720 with vista and Ubuntu on it, although the problem is I was on Vista for a bit playing Counter Strike Source 
and then out of nowhere it crashed and then vista went to go shutdown and after about a minute of it saying it was shutting down it then started saying 
it was completing a windows update step 3 of 3 or something, so I let it do its thing and shutdown. I still wanted to play Counter Strike 
though so I turned on the computer to be welcomed by NOTHING it was black no curser, no option to enter the bios, although the system was on
 so I pressed all the F1-F12 keys and nothing happened but enter did, (Note I have grub installed so I can choose more easily what OS I want to boot from)
when I pressed it ubuntu started loading up although something was wrong VERY wrong, the brightness was very dim. After about two hours of constant
Google searches and installing/reinstalling drivers I still couldn't find anything, any suggestions would be appreciated.

Also sorry if my format or whatever sucks this is my first time using UbuntuForums ( I made this account just for this problem)

---

### Post by weatherman2 on 2014-11-21
On a  Dell laptop, the F2 key takes you into BIOS Setup.

When you restart the laptop (or power it up) and hit the F2 key a few times, do you get into BIOS Setup?  Is it the proper brightness, or is it too really dark?  

There should also be a function key combo to adjust brightness.  On your Dell, I think it's Fn + Up arrow to bring brightness up.  Does that do anything?

If your screen is really dark even in BIOS Setup, it could be either the screen inverter has burnt out or the LCD screen's backlight has failed (which means you probably need to replace the screen).  Newer laptops use LED screens without inverters, but yours is an LCD with a CCFL bulb inside and needs an inverter.  The inverter is easiest and cheapest to replace if that's the problem, probably the first thing I'd try.

It could **also** be a "lid switch" problem - the laptop has a switch (mechanical on older laptops) that tells the laptop the lid is open or shut; when shut it turns off the screen's backlight.  If the switch is somehow not opening your screen's backlight might not be coming on.

But if the screen is properly bright in BIOS Setup just not in Ubuntu, then there is some other problem.

---

### Post by pokedadude on 2014-11-21
Alright It wasnt f2 to get into bios it was f9 or something (which I tried) and I cant change the brightness via ANYTHING else. 
When I boot it up I dont see a dell splash screen and I dont see the Grub menu. 
I think all I need is a way to enter to the bios without actually rebooting, do you know of ANY way to do that?

---

