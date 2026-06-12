---
title: "Sony Vaio VGN-FW35G"
date: 2009-06-12
forum: Hardware
---

### Post by svaens on 2009-06-12
hi all, 

Just bought my new laptop. A Sony Vaio VGN-FW35G. 
Just wanted to post my experiences with this nice little computer. 

Feel:

The other laptop in the house is a Dell XPS. In comparison to that, the Dell seems a bit more sturdy. Especially around the dvd drive tray. The monitor also seems a bit more bendy than the XPS. 

Screen: 

A great size, 1600x900 pixels. Perfect for me because I like a wide screen for fitting things in, as I have eclipse open for development work.
Colors are good. 

Keyboard: 

Nice and snappy, like those macbooks. 

Linux support:

So far seems reasonably ok. 

-----------------------------

Wireless: works out of the box with Ubuntu 9.04 (jaunty). 

------------------------------

Brightness keys:
I needed a fix, which I found here:
[http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/#comment-703](http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/#comment-703)
(i also attach the script here). 

Without this I wasn't able to use the brightness buttons. This script fixed it

-------------------------------------

Sound: Worked, but needs extra configuration. 
I found this here:
[http://vaioubuntu.wordpress.com/tag/alc262/](http://vaioubuntu.wordpress.com/tag/alc262/)
an option you need to put in the /etc/modprobe.d/alsa-base.conf file
options snd-hda-intel model=hippo

This pretty much seemed to work for me. Although, at first, i thought the sound was very low after this change. But now it is quite loud enough. So i'm not sure what is going on there, or if i was imagining it or what. I will keep you all posted if i have further troubles with it. 

What it fix was the jack detection, and gave me headphone volume control in the alsa mixer. 


update!!

Actually, I noticed that while the Volume + and - buttons at the top of the keyboard cause the screen to report changing volume, the volume doesn't actually change. 
Also, the mute button (Fn-F2) doesn't work. 
However, before i'd added this option (model=hippo) it did work. 
So i've fixed one problem, and introduced another.


------------------------------

Battery time:

gives me around 2 hours, with the brightness turned right down, and cpu speed "on demand"

------------------------------


Touchpad
-----------------------------
Works out of the box, but I like to add the syndaemon control of the touchpad. 
This disables the touchpad when typing. This is great for me, as I accidentally touch the touchpad
while typing quite often. That gets very annoying. 
Here's how i've done it 
info found here:
[https://help.ubuntu.com/community/SynapticsTouchpad#hal](https://help.ubuntu.com/community/SynapticsTouchpad#hal)

1. Add this element to the deviceinfo element in the file /etc/hal/fdi/policy/preferences.fdi file

  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>

2. install gsynaptics
(the commands won't work unless you've done the above step

sudo apt-get install gsynaptics

3. Use a command like this:

syndaemon -d -i 2 -t

4. You can set the command to start on session start by adding from 'System->Preferences->Startup Applications.

All in all, a nice machine so far.

---

