---
title: "Cursor moves by itself"
date: 2008-05-08
forum: Hardware
---

### Post by TracyO on 2008-05-08
Hi there,

I have been really happy with Ubuntu, but one of the things I noticed when I started using it last fall was that the cursor occasionally jumps without provocation.  For example, if my cursor is sitting over "but one of the things" it will jump to it, making me type "buking me typet one of the things..."  This would happen without touching the mouse, just randomly.  However it was never often enough for me to be concerned about.

Two days ago, I just got a Dell 1525 laptop with Ubuntu 7.10 already installed (haven't updated yet...waiting to see what happens with Firefox), and it is doing this really badly.  To type an email or even this message is really frustrating.  I've moved the cursor away to an area of nothing to click on, but I still lose it.  I checked the settings of the touchpad, and they're on low sensitivity.  Has anyone else encountered this problem or know how to fix it?

Thank you.

---

### Post by wannadumpwindows on 2008-05-08
Are the palms of your hands or thumbs or something maybe touching the touchpad? I had this same problem, and I was extremely angry with Ubuntu over it for about 2 months. Then one day I finaly noticed what was going on. The very bottom of my palms were hitting the touchpad every once in a while while typing. I swore up and down that it was the O/S too. But it wasn't. And it happening on two different computers, I'd be willing to guess that it's the same problem for you. There are some tutorials around about how to disable the touchpad while you're typing. It's really simple. Give this link a shot . . .

[http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html]("http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html")

---

### Post by TracyO on 2008-05-08
Thanks for the link.  I guess I'll start monitoring myself a little closer to see if it is me before I change the touchpad.  

What would the first option of the link you gave me do?  Is it that I could manually turn off the touchpad and turn it back on? Does it turn out to be a keyboard shortcut?

It just did it again, but I swear my hand is not anywhere near the touchpad.  I'll keep monitoring for the time being.

Thank you so much.
Tracy

---

### Post by wannadumpwindows on 2008-05-08
I'm not saying that's the only thing it could be by any means, just the most simple first solution to test. That first option just allows the mouse to use "options". That's the best way I can think to explain it. Allows outside tools to configure how the mouse works I suppose. It looks a little daunting, but editing your xorg in the first part there is really easy, it just looks like something tough. It's really not. But yeah, keep an eye on it, it might be something easier than you think.

Edit: The last part allows you to turn the touch pad off if you want to, but if you're going to try it, make sure you know the keys to navigate the desktop manually first. Otherwise, you'll spend some time trying to guess. You shouldn't need to bother with it though.

---

### Post by keylime on 2008-05-08
If you have a Synaptic touchpad, there is a way to slow the sensitivity down some via a daemon entry.

Enter into System -> Preferences -> Sessions.

After that click on Add.

Type in as follows:
Syndaemon
syndaemon -i 1 -d
To have the delay of the touchpad to prevent accidental touching.

Hit ok, and make sure the checkmark is enabled. Reboot and you should be golden.

---

### Post by TracyO on 2008-05-08
Thanks,again Wannadumpwindows.  I may message you again in the future if I still need some help.

Keylime, I'll give it a try.  I can't reboot right now, but I'll let you know how it goes.

Take care you two!

---

### Post by wannadumpwindows on 2008-05-08
No problem, don't be afraid to ask! Good luck in your Ubuntu adventures.:)

---

### Post by webbina11 on 2010-07-24
I am also running A Dell Inspiron and for several weeks the Logitech Wireless USB 2.0 TrackBall Mouse and Keyboard worked well. The Wireless connect point was connected to the Dell via a USB Hub. 
Then without warning, the cursor started moving on its own or not releasing an icon if changing between icons. My Touchpad also stopped working. When shutting down I would get a message stating SOMETHING could not close because it was still in use, although nothing I knew of was active. I did everything that has been suggested with no luck. Dell suggested I RUN MSCONFIG STARTUP and disable everything and reboot. This brought [ Eyelid Pustules ](http://acne.webbina.com/pustules.php) back my touchpad use. [I then enabled things that I needed or knew were not a conflict]("http://acne.webbina.com/pustules.php"). While this was informative it did not pinpoint the problem. When I reinstalled the USB Hub with the wireless access point attached the problem reappeared.
Isolating the mouse problem, I went back to the [ papules ](http://acne.webbina.com/papules.php) Wired Keyboard via USB hub and the Wiresless mouse and so far so good. The Wired Keyboard and Wireless access point are now in seperate ports on the USB hub.
It seemed to be a conflict between the two wireless devices and the touchpad.

---

### Post by jerrykenny on 2010-07-25
Synaptics and Alps touchpads used to be pretty mad . . . . their drivers are now in the kernel ( i think) and should be pretty mature.

Prior to having udev i used to go into the xorg.conf file and try EVERY permutation possible to get some sense of them.

I definitely disabled the "tap-to-click" option here, and you can probably do this from your users prefences/ settings.

I used to carry around a usb mouse and plug it instead, the keypad was so annoying.

---

