---
title: "Ubuntu 11.10 on Lenovo Thinpad Edge e420s"
date: 2011-12-23
forum: Hardware
---

### Post by Alcareru on 2011-12-23
I have just recently acquired a Lenovo Thinpad Edge e420s. It was my choices because I suspected it might work well with linux and for the most of it this truly seems to be the case. The only real issue with it is that when ever it has been idle for a moment the screen dimms out as expected. It however is very annoying that the brightness is not reset back to what it was if I start using the laptop again (touch the pad or press any key). I need to adjust the brightness and then it is reset (only one click is required and the direction of adjustment doesn't matter). If anyone has ideas on how to address this issue I'd very much appreciate it.

Ok, another annoyance is that the middle button on the mouse isn't working and I have not yet tested everything (I'd be very much surprised to find out that the fingerprint reader would actually work).

---

### Post by greenpeace on 2012-01-19
Hi, 

I also have one of these laptops, and I have just dual booted it.  I'm really quite content with the way ubuntu 11.10 works on it apart from a couple of small-ish complaints.

1. the screen dimming thing - just as you describe.

2. the switchable graphics... I've spent a lot of time looking into this, and I can't force the laptop to use the discrete GPU... any ideas?

3. the fans are on a lot of the time (they are hardly ever on on Windows) and the power consumption is very poor... (2hours from full charge - windows gives 4+ hours).  Though I do think that this is related to point 2 above.

Any ideas on these things? 

With regards to your other points:

the middle button on the mouse works for me (out of the box)... Hope you get to the bottom of it!

Also, I followed the guide below[1] to get the fingerprint thing working... it worked fine, but looked ugly on the page so I have taken it off.

[1][https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)


cheers, 
gp

---

### Post by greenpeace on 2012-01-20
regarding point 3 above: 
I have stumbled upon this applet which has improved my battery life by an hour or so:

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

hth

---

### Post by Alcareru on 2012-04-07
I had sort of forgotten all about this post and as I'm now checking what I originally wrote, there's at least one thing different. I no longer experience any problems with the screen dimness. I don't remember if I found some fix for it or was it some kernel updated or smthn that fixed it. greenpeace, can you confirm do you still have problems with that? Also the middle button somewhat works. It just don't do what I'd expect it to. The things I'd like it to do are:
1) Open links in new tabs on browser (well this is more like expected behaviour, I really don't care about it so much).
2) ctrl/alt+middle mouse button drag to resize windows
Right now it seems to copy/paste text, which I found totally useless.

I must say that I don't have any external GPUs, only integrated Intel, so that's at least one thing we have different in our hardware configurations. And I'm obviously unable to aid you there.

Relating to the Intel graphics I have however stumbled upon a limitation/bug/problem. I can not use the external HDMI connection. Attached displays seems to get recognized just fine, but the colors are crazy (it seems a lot like the contrast would be insanely high) and the desktop is not properly sized to fit in to the detected screen.

And thanks for the tip about improving battery life. I'll be sure to check it out.

---

### Post by eskararriba on 2012-04-09
I just got my new e420s today, so far the only problem I&#7743; experiencing is a really slow wi-fi connection. 
 
regarding the energy-saving options, I read some about thinkfan and tlp have you checked that? 
[http://thinkwiki.de/Thinkfan](http://thinkwiki.de/Thinkfan)
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)
[https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management](https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management)

hope this helps

---

