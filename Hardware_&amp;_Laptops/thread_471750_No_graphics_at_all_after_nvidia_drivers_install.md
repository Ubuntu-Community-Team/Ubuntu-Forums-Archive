---
title: "No graphics at all after nvidia drivers install"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by ScottMac on 2007-06-12
I have a very strange problem! 

i installed the Nvidia drivers using envy, which worked fine. it then asked me to reboot, but when ubuntu finished shutting down the graphics just stopped. At first i thought it was the monitor but it works fine with another computer. When i turn the monitor on while connected to my computer it says that it isnt receiving any input signals.  The PC starts up fine but the screen remains off, ie no signal. The video card seems to be doing nothing...

i think the drivers might have done something to the graphics card but my opinion isnt worth much

My specs: 
AMD athlon 1GHz
385 megs ram
geforce 2 mx400

any help would be greatly appreciated

---

### Post by stchman on 2007-06-12
> **ScottMac said:**
> I have a very strange problem! 

i installed the Nvidia drivers using envy, which worked fine. it then asked me to reboot, but when ubuntu finished shutting down the graphics just stopped. At first i thought it was the monitor but it works fine with another computer. When i turn the monitor on while connected to my computer it says that it isnt receiving any input signals.  The PC starts up fine but the screen remains off, ie no signal. The video card seems to be doing nothing...

i think the drivers might have done something to the graphics card but my opinion isnt worth much

My specs: 
AMD athlon 1GHz
385 megs ram
geforce 2 mx400

any help would be greatly appreciated

Are you running Feisty?

Go to recovery mode and uninstall the nvidia drivers usinf envy by typing:

envy -t

Then enable the restricted nvidia drivers.

---

### Post by ScottMac on 2007-06-13
thanks for replying stchman.

it seems that my video card died randomly at the same time i installed the nvidia drivers using envy!! talk about coincidence :) i think this is the case because i booted from my ubuntu hard drive using another computer and the graphics work normally. Also if i fiddle with the video card video comes back for a while but then goes dead again. it must just be that its quite an old video card and has seen alot of physical wear and tear.

 Envy actually works really well. it solved my resolution and refresh rate problems! I recommend envy to anyone with driver and resolution problems.

---

