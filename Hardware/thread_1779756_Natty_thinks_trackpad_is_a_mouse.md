---
title: "Natty thinks trackpad is a mouse"
date: 2011-06-10
forum: Hardware
---

### Post by ferrettsyl on 2011-06-10
I'm not able to enable the multitouch functionality of my trackpad under ubuntu 11.04, using Unity (I know it exists in the hardware, because it worked in Win7). When I go into mouse preferences the trackpad tab is missing, and GPointer Device Settings identifies my "mouse" as a "PS/2 Logitech Wheel Mouse", and provides no help getting things to work.

Output from xinput list:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse               	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; WebCam SCB-0385N                        	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

Is there a way I can get ubuntu to recognize my trackpad as a trackpad? I've tried things with synclient but it just says "Couldn't find synaptics properties. No synaptics driver loaded?" for everything. I tried installing packages like gsynaptics, to no avail (possibly because those are for gnome?)

This isn't a major problem, but I'd really like to be able to scroll on the trackpad instead of having to click and drag the scroll bar. I'd be fine with either two-finger scrolling or edge scrolling. My google-fu has failed, and I'd be very grateful if anyone can help me solve this.

I'm using a Samsung netbook, model NP-NC110.

Thanks!

---

### Post by Psycho67 on 2011-08-25
I apologize for bumping this thread, but I have the exact same problem currently.  Have any solutions been found?

---

### Post by ferrettsyl on 2011-08-25
I never found anything. Fortunately I have a main laptop that works just fine, but it's irritating whenever I use my netbook.

---

### Post by mjjw on 2011-11-05
I had this exact same issue which drove me crazy until I installed the kernel from Oneiric into Natty (I didn't get on with Oneiric so I want to stick to Natty until the next LTS comes along).

Here's what I did, I now have working touchpad on NC110-A03 under Natty

[http://ubuntuforums.org/showthread.php?p=11428719#post11428719](http://ubuntuforums.org/showthread.php?p=11428719#post11428719)

---

