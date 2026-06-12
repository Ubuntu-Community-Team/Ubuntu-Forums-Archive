---
title: "Is there any other alternative to a laptop in a vehicle?(little off topic)"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by HgBoy on 2007-06-06
I am going to be using a DIY fuel management system that requires a laptop to tune the system. I would only be using the laptop for this purpose, running linux too so it wouldnt have to be anything fancy at all. my question is, are there any other alternatives to the laptop. Ideally, something a little more compact so I dont have to find a spot for a laptop in my cars interior. I have been looking into mini-atx motherboards, but dont think I need anything more advanced than something to hold ubuntu with a serial port. does anyone know if something that simple exists?

---

### Post by t4thfavor on 2007-06-07
Try a search for Car pc or voom pc on google, you would have to install a screen somewhere, but you could also do remote management via ssh, and wifi. 


I know there are several pc's that have decent specs, and fit in a small fanless sealed box perfect for hiding under the seat, or in the trunk of a car. 

Also you could try the same searches on Ebay.

---

### Post by 444 on 2007-06-07
Gumstix is as small as it gets. Well I doubt it'll run Ubuntu but it'll run Linux. Otherwise you'll have to go with some sort of (mini) ITX motherboard perhaps?

---

### Post by HgBoy on 2007-06-07
The gumstix website is a little blurry on the details, but it seems i can get one with a serial port or two. I am not familiar with flash memory though. I assume this replaces the HD, but does it perform in a similar manner? Also, the small versions of linux (puppy, damn small, etc.) being run from a live cd/jump drive store changes made to programs and settings?

---

### Post by 444 on 2007-06-07
I think Flash chips do 33MB/s, about the speed of an older laptop drive, but once you get into multiple io they are way faster than any hard drive.

Live-cd distros can't store data, well unless you have a harddrive in there too to store stuff on. Live-usb distros theoretically can, I'm not sure if they actually do so though.

---

### Post by HgBoy on 2007-06-07
Ok. The gumstix seem like a good idea. Has anyone ever actually used one? the fastest available with a lcd hookup and serial ports(my two main requirements) has a 400 mhz processor with 128 MB of memory. I dont know if this will be enough to run what I plan on using. The tuning software itself isn't too complex, but I need something powerful enough to power the display, preferably with a car pc frontend of some sort. Will the gumstix be able to bear this type of load?

---

### Post by 444 on 2007-06-08
Load? For just a plain GUI? Did I tell you I was running Firefox on my 266mhz main pc a couple years ago? Speed is not much of an issue for just a plain graphical interface.

There are only two issues with gumstix, lotsa commandline work and it's not an x86 chip, so whatever software you're using needs to be open source so you can recompile it for the ARM cpu that it has.

---

### Post by t4thfavor on 2007-06-08
I am not sure, but is there a gumstix that has keyboard inputs? or is that not something you want? I would check myself, but I am on dialup. Also the gumstix is extremely tiny, is it nessicary to go that small? it will probably cost more money than an x86 based mini-itx pc especially when factoring in the time it will take to set up the dev environment for cross compiling (I did it for wrt54g). I would suggest the mini-itx since you can actually do the work on it, with a real monitor, keyboard, and mouse. 

As for flash, I have ran a desktop off a usb key, a cf card, and an sd card. I am currently runinng Ubuntu on a soekris board ([www.soekris.com](www.soekris.com)) which is using cf, and it runs pretty fast boots in about 30 sec or so. Also in a car, vibration on a fanless/diskless system will be alot less of a problem. 

I hope I have helped you make the decision.
Good luck!

---

### Post by HgBoy on 2007-06-08
So, suppose I go with a mini-itx board, what type of screens will I be aqble to use as a functional monitor? Will any color LCD anel work, or does it require video capabilities? What about graphical displays/character displays?

---

### Post by 444 on 2007-06-08
I think most ITX boards would have standard VGA port so if the LCD has that then great. As for special LCD connectors instead of VGA, that might be a problem, I'm pretty sure only some, if any, support those.

I would assume character displays would connect via serial/usb instead of vga.

BTW, did you look at the gumstix wiki? Check this:
[http://docwiki.gumstix.org/Expansions#60-pin_expansion_boards](http://docwiki.gumstix.org/Expansions#60-pin_expansion_boards)
Serial ports, usb, lcd...

---

### Post by HgBoy on 2007-06-08
I did see that. I have been trying to find out as much as I can about using the gumstix as an actual computer, but the information is a little sparse, and what I can find is extremely technical, so it's a little hard to understand. I know that they require a lot of command line work, but I need the practice with it anyway. And the mini-itx makes me want to go all out and have a complete pc in car dvd/audio player, which diverts from my main focus. Is it possible to use a gumstix to run one program (megatunix, can be found on google), to output to some type of monitor (small in car lcd), and allow me to store and datalog info through megatune. keyboard connections arent too big of an issue, i can use an adapter cable for that.

---

### Post by 444 on 2007-06-08
Yes. See this:
[http://docwiki.gumstix.org/Debian_on_Gumstix](http://docwiki.gumstix.org/Debian_on_Gumstix)
Hopefully that means gtk and other stuff required by megatunix would be precompiled and all you need to compile is megatunix itself.

Looking at megatunix, it looks like it's gonna require a full lcd, a character display would most likely not work unless you chang the megatunix code.

Nothing stopping you from trying to compile it now before you buy the hardware. That way if you hit a snag you'd be able to back out and choose another solution.

---

### Post by HgBoy on 2007-06-08
I found this lcd screen, but it says it will not work for video. Does this mean I can still use it as a monitor?

EDMGRB8KJF

Panasonic EDMGRB8KJF 7.8" Color STN Touchscreen LCD



SPECIFICATIONS:
• 7.8" Color STN Touchscreen LCD [PDF] EDMGRB8KJF 
• Passive Transmissive Color STN Touchscreen
• Effective Display Area: 7.8" Diagonal
• 640 x 480 resolution
• 0.246 x 0.246 mm pixel pitch
• 45:1 contrast ratio
• 80 cd/m2 brightness
• touch_iconIncludes DynaPro four wire resistive touch screen
• Outer Dimensions: 206W x 146H x 7D mm
• Weight: 2 lb (4 lbs shipping weight)
• Power Consumption: 2.2 watts
•
• Use this screen with out the touchscreen also.


APPLICATIONS:
Super PDA, Internet Appliance, Man Machine Interface, Picture Frame, Instrumentation, Home Automation, Embedded Linux

---

### Post by 444 on 2007-06-08
What do you mean 'not work for video'?

---

### Post by HgBoy on 2007-06-08
The company says it has a refresh rate that would not work well with actual videos. upon further investigation, it isn't a very good display. I have found another one for a lot less money that would be well suited for video, etc., but it has the option of serial connectors. I think that means I will be able to connect it using an available serial port on the gumstix, and not have to use the actual lcd connection? I would prefer this route, as I can't get all of the options I would like at the same time, the most limiting of which is the lcd connectivity. The faster motherboards have serial ports, but no flash memory card reader support, at least not that comes with the lcd too.

By the way, thanks for putting up with all of my beginner questions. I've got a lot left to learn still, but these forums are what made it possible for me to get excited about my computer for the first time. (working on learning Python, linux shell, gui apps, and about a million other ideas i have rolling around :))

---

### Post by 444 on 2007-06-08
Ah. Passive LCDs. They suck.

Video over serial sounds silly. Serial is too slow. USB maybe?

---

### Post by HgBoy on 2007-06-08
the only usb offered with the gumsticks seems to be the small type connector (usb type b i think). Can the gumstix even be used for what I'm planning? Or am I expecting too much from it? It seems to work in theory, but I haven't seen many other examples other than people pre-programming them and installing them into robots.

---

### Post by 444 on 2007-06-08
What are you planning again? You mentioned megatunix which seems like it'll work fine with a passive lcd, then you mention video for some reason... If you want to play videos on it then you should probably go with some sort of ITX board for the performance you'll probably need (unless you wanna convert all your videos into a format the gumstix can handle...).

BTW, as long as it's host usb (it is) it'll work with any usb device (that doesn't suck too much electricity), you just need an adapter to plug in the bigger connectors.

---

### Post by HgBoy on 2007-06-08
I apologize for the confusion. I thought the monitor had to be video capable for a GUI to work. So I could use the cheap passive lcd if all I wanted was the megatunix and data logging supported by it? Also, what type of keyboard options could work with this (serial or usb are the only real connection options, bluetooth keyboards are too pricey).

---

### Post by 444 on 2007-06-08
Yeah, passive lcds don't work for fast moving stuff (like live video), they blur. But a some buttons should work fine. BTW, wasn't that a touch screen? Might be useful...

I assume a usb keyboard should work (the verdex board has usb host support), but I'm not sure. Same with serial. If it's just for configuring things you can connect to it using a null serial cable.

---

### Post by HgBoy on 2007-06-08
the keyboard is mainly going to be for the data entry into megatunix, but i might be able to make the touchpad work for that too. I will most likely do all of the source and compiling through my linux box at home. I couldnt imagine compiling code on a 7" screen using a touch keypad....

---

### Post by HgBoy on 2007-06-08
Another downside I just realized is that the verdex boards (usb host compatible) dont have any accessory boards with that feature yet... All available ones have usb client.

---

### Post by HgBoy on 2007-06-08
ignore that last post. I was reading info from an older page. usb host does work.

---

### Post by HgBoy on 2007-06-09
[http://www.youtube.com/watch?v=CLlnJAyzIfQ](http://www.youtube.com/watch?v=CLlnJAyzIfQ)

Here is a link of the megatunix program in action in a cobra. Will a passive type lcd screen work with the animations like the gauges? or will I need an active screen?

---

### Post by 444 on 2007-06-09
It looks like there might be some blurring in those faster bits...

---

### Post by HgBoy on 2007-06-09
That should be my last question. You've been an amazing help. I think I know enough now to get this all assembled and start fiddling around with it. I dont have the fuel system controller built yet, so I should have plenty of time to bone up on my command line and compiling/coding skills. Thanks for the help.

---

