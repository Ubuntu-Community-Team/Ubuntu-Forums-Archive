---
title: "Two finger scroll on touchpad in Jaunty"
date: 2009-04-16
forum: Hardware
---

### Post by netJackDaw on 2009-04-16
Hi!
I have a new laptop and I want to make two finger scroll work like in Mac OS X. How do I do this in Jaunty. Any suggestions?

---

### Post by Windsurfer619 on 2009-04-16
It depends on the make of your touchpad (if it can even support it). 

Also, search :)
[http://ubuntuforums.org/showthread.php?t=582707](http://ubuntuforums.org/showthread.php?t=582707)

---

### Post by netJackDaw on 2009-04-17
The thing is though that many (most) articles refer to changes in xorg.conf. I have had my share of editing xorg.conf and now I see that much of the configuration of periferals is moved out of xorg.conf in favour of hal. Tried to make a fdi-file for the touchpad but it does not seem to have any effect.

...and honestly I would like to have a GUI front end to handle all this for me. The Touchpad applet in System preferences only handles a fraction of the settings available...

...and what happens in an environment with several users if you edit xorg.conf? All get the same settings which isn't always the best.

Where are the settings stored anyway. Because I have a working Touchpad! No settings in xorg.conf?

(I'm not asking you all these questions Windsurfer619, just want to get it said.)

---

### Post by Windsurfer619 on 2009-04-17
Woah.
I just tried two-finger scrolling. It works.  I had just upgraded to jaunty, and I haven't made any changes to my xorg, other than my video stuff.
Now, how do I turn this off? I don't want it :S

---

### Post by netJackDaw on 2009-04-19
Maybe it's a case of what you are used to. Hope you can change it back... Did you change it through Preferences->Touchpad (gsynaptics)? If that is the case then I am really disappointed, because in that case it seems like someone decided to hide preferences that are not supported.

If you hide unsupported preferences: TELL IT to the user! Do not hide it! The best would be to gray out unsupported prefs.

Maybe we should compare screen shots of this to be sure....

---

### Post by cajunlibra on 2009-04-25
I have Jaunty installed, not as an upgrade from Intrepid.  The following is my entire xorg.conf:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```


How do I make this work? In XP, it shows the driver for ALPS installed. Under intrepid, I was using the synaptics driver according to my xorg.conf.

I added the usual section mentioned in other posts but it didn't do anything. I couldn't even get GSynaptics to open eventhough I followed the directions in the pop-up error. I got the error again even after making the change and rebooting.

I have a Dell Precision M20 Laptop.

---

### Post by herculea8n1982 on 2009-04-26
I am in the same situation xorg.conf says that most settings aren't there anymore (if I manually add the section for synaptics it doesn't work) - I really want to use gsynaptics because my touchpad is too sensitive it's driving me crazy.

---

### Post by cajunlibra on 2009-04-26
Do you have a problem with a dust particle moving your cursor while typing? THat happens to me all the time and I end up with gibberish typed all over the place.


Yesterday, it did seem to work on Twitterfox if I pressed my finger tightly against the touchpad.

---

### Post by austin512 on 2009-04-26
after i installed gsynaptics, i followed the directions here to enable shmconfig, and then scrolling worked fine

[https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig")

---

### Post by cajunlibra on 2009-04-27
This worked for me although not how I expected. Virtual scrolling allows me to scroll by sliding my finger on the right side of the touchpad like some laptops already offer.

---

### Post by VladNistor on 2009-04-28
I just discovered this feature by accident in Jaunty. I didn't have to install anything.
My laptop is HP Compaq 6720s (has Synaptics) and has the virtual scroll on the right which I've always used, but I kinda like 2 finger scrolling.

---

### Post by damis648 on 2009-04-28
Here is my mini-tutorial on two-finger scrolling for those that do not have it. I will assume you are using Jaunty for this, this would be slightly different for Intrepid and much different for Hardy.

**_Introduction_**
This is a quick 5-minute guide and is *by no means extensive*. This particular guide for Jaunty will modify a single HAL settings file to pass options to X in order for the two finger scrolling to work.

**_Step One: Determine Your Brand of Trackpad_**

Start out by opening and terminal and executing the following:
```
synclient -m 10
```

That will show console output of your trackpad's input, something like this:
```
 time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
  44.059   430  416  64 1  0  0 0 0 0 0  00000000   0  0  0   0   0
```
which will constantly scroll so long as you are touching the trackpad. Start by focusing on the f and the z axes. Touch one finger to the trackpad. The f axis should jump to one while you are touching the trackpad with one finger, and the z axis will rise. Note the ballpark for z, you may or may not need it later. Now take your finger off and touch two fingers. This is where we determine your brand of trackpad. One of two things will happen: Either the f value will be 2, which means you are using a Synaptics trackpad which fully supports multitouch. Skip to step 2A. If f doesn't change to 2, you most likely have an Alps trackpad. Have a look at axis z. Between one and two fingers, this axis should dramatically increase when two fingers are placed on the trackpad. This is a pressure value that we will use to simulate two fingers. Take note of the ballpark two fingers gives you, we need to know at what pressure to emulate two fingers. Do not make it impossibly high, nor so low that it constantly triggers scrolling. I will be using 100, as that is an acceptable value for me, a friend of mine has a laptop where 85 is enough to trigger it. Head to step 2B for setting up two finger scrolling. 

-----------------------------------------

**_Step 2A: Synaptics_**

For those of you with a Synaptics trackpad, open a terminal and execute the following:
```
cd /usr/share/hal/fdi/policy/20thirdparty/
sudo cp 11-x11-synaptics.fdi 11-x11-synaptics.fdi.bak
gksudo gedit 11-x11-synaptics.fdi
```
The second command was simply to back up your trackpad config incase something goes awry. 
In the newly opened gedit window, you will see quite a short document. Find the line
```
<merge key="input.x11_driver" type="string">synaptics</merge>
```
and underneath it, paste in:
```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
```
and then save and close. Simply reboot, and you should be happily scrolling with two fingers. :guitar:

**_Step 2B: Alps_**
This step is the same as above with a single except that where I ask you to paste in
```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
```
, I need you to paste in an extra line with it:
```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
<merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">100</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
```
Simply follow step 2A with this block instead, however where you see '100' in the new line, change that value to the z axis value for two fingers that we found in step one. 

**_Conclusion_**

Any X11 option for the trackpad can be passed through here, in the form of
```
<merge key="input.x11_options.OptionName" type="string">Value</merge>
```
So feel free to mess around with the options if you need extra options for you trackpad such as speed and all.:popcorn:

Cheers, hope this was useful.

---

### Post by LebanonDore on 2009-04-29
Thanks damis648!  Your guide worked like a charm.

---

### Post by cajunlibra on 2009-04-30
It didn't work for me. Instead of the 2-finger scroll, any touch was a scroll.  I'll just stick w/ the virtual scroll on the side of the keypad.

Thanks though.

---

### Post by herculea8n1982 on 2009-05-09
> **austin512 said:**
> after i installed gsynaptics, i followed the directions here to enable shmconfig, and then scrolling worked fine

[https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig")

thanks for that you have saved me from going crazy. i love touchpad tapping to click, but it was so damned sensitive it was unusable. cheers!!! :biggrin:

edit: yeah the extra 8 in my username is a direct result of that lol.

---

### Post by myq on 2009-05-17
`

---

### Post by cajunlibra on 2009-05-17
I just settled on VirtualScroll for mine. It works well both axes.

---

### Post by myq on 2009-05-17
Hi, I'm running Ubuntu 9.04 (Jaunty), not from a fresh install, but by upgrading one version at a time from 7.10.  I enabled SHMConfig, then followed damis648's instructions exactly.  I have an Alps touchpad, and I set the MinZ to 85.  I restarted, but it's not working. :(

I've checked that I'm definitely meeting the MinZ using synclient.  Help would be greatly appreciated.  Any suggestions?

---

### Post by gombihu on 2009-09-01
> **myq said:**
> Hi, I'm running Ubuntu 9.04 (Jaunty), not from a fresh install, but by upgrading one version at a time from 7.10.  I enabled SHMConfig, then followed damis648's instructions exactly.  I have an Alps touchpad, and I set the MinZ to 85.  I restarted, but it's not working. :(

I've checked that I'm definitely meeting the MinZ using synclient.  Help would be greatly appreciated.  Any suggestions?


It just works for me. I neither have configuration in xorg.conf, or 11-x11.synpatics.fdi Dunno how, but I'm happy:)

---

### Post by gombihu on 2009-09-02
> **gombihu said:**
> It just works for me. I neither have configuration in xorg.conf, or 11-x11.synpatics.fdi Dunno how, but I'm happy:)

And the "best" thing: It doesn't work on my brand new Asus laptop, but it works on my old T42...:confused:

---

### Post by katie24 on 2009-10-18
Damis--thanks for the tutorial.  I'm a complete noob and have been using Jaunty now for about a month.  Your instructions worked on my new Dell Studio 1555. I used the synaptics instructions first (I thought that's what my computer had) and those didn't work.  So I tried the other set of directions and those worked.  Happy Day!  I have two finger scrolling!

---

### Post by katie24 on 2009-10-18
Easy come...easy go...after a couple of reboots it stoppped working.  I copied my original file back and now I'm back to regular ole trackpad :sad:

---

