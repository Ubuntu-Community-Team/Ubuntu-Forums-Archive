---
title: "ASUS Eee PC 1201N Touchpad"
date: 2010-04-29
forum: Hardware
---

### Post by Hideaki on 2010-04-29
Hello,

I'm trying to get the multi-touch features of the 1201N's touchpad working on 10.04 to no avail. Following the guides made for 9.10 don't seem to render any positive results(I think due to the deprecation of HAL), and it is incredibly annoying not to have the touchpad working properly as whenever more than 1 finger even accidentally touches the pad it causes the mouse to spaz-out uncontrollably and click everywhere.

What exactly is so different about this touchpad, I think synaptics had decent linux support.

---

### Post by Hideaki on 2010-04-30
Can anyone help me? Following some of the old tutorials has now rendered SOME results, but still no gesture support, I just got it to stop freaking out when I touch on more than 2 places.

So far I've created a file at /etc/hal/fdi/policy/11-x11-synaptics.fdi and put this in it:

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">10</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>*
       <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
       <merge key="input.x11_options.TapButton2" type="string">3</merge>
       <merge key="input.x11_options.TapButton3" type="string">2</merge>
   </match>
 </device>
</deviceinfo>

```

I also can't get synclient to work even with that file. It keeps saying "Can't access shared memory area."

---

### Post by kregg on 2010-04-30
I definitely agree with you, Hideaki. I'm having **exactly** same problem. I think it lies in Ubuntu thinking that the touchpad is a normal non-multi-touch trackpad, and so if I place two or more fingers, the cursor is trying to track the cursor, but gets awfully confused between the two or more finger presses.

Anybody got a solution? I'm using Ubuntu 10.04, if that helps...

---

### Post by Hideaki on 2010-04-30
I haven't been able to do much more. I found the name of the touchpad is "SynPS/2 Synaptics", and some other note/netbooks use it, but they all have the same problem and the same solution that doesn't seem to work on Lucid.

Edit: I tried gpointing-device-settings as another thread suggested, and it doesn't seem to do much that the standard ubuntu mouse options can't do. There are options for 2 finger scrolling, but they don't appear to work at all.

---

### Post by kregg on 2010-05-02
Hideaki, I've been trying too, but the 11-x11-synaptics.fdi file basically scrolls based on the pressure of the trackpad, which (in my own opinion) is completely useless and doesn't utilize the second finger.

My guess is that there is not decent drivers that support the trackpad yet, which is a shame. When I have more free time, I will file a bug report, and hopefully it will be fixed in this version of Ubuntu, but most likely (if there is any chance), it'll probably be in the next version of Ubuntu.

I know it's not a Ubuntu specific problem, because *many* other distros suffer from this *exact* same problem :(

---

### Post by Hideaki on 2010-05-03
It's a shame. This and the function keys being iffy are the only 2 things keeping the 1201N from being perfect under Ubuntu.

---

### Post by vluhd on 2010-05-09
> **Hideaki said:**
> It's a shame. This and the function keys being iffy are the only 2 things keeping the 1201N from being perfect under Ubuntu.

Not to mention the wi-fi being borked...

---

### Post by maestrobwh1 on 2010-05-09
> It's a shame. This and the function keys being iffy are the only 2 things keeping the 1201N from being perfect under Ubuntu.

These issues are mostly solved here:

[http://forum.eeeuser.com/viewtopic.php?id=83058&p=5](http://forum.eeeuser.com/viewtopic.php?id=83058&p=5)

Go to post #116  

*bwh1969 is my user name there and am using the same model so if you still have problems: post back here or there.  I suggest there because the site is dedicated to the Asus EEE models.

Granted, the touch pad does not do the cool things it does in Windows yet, but since I never had a touch pad work like that, I am not missing it.  It doesn't work in all windows apps anyway.

The Wifi seems not to completely disable either.  It stops the connection but does not seem to shut the wifi device OFF.

---

### Post by VeeDubb on 2010-05-15
[This thread]("http://ubuntuforums.org/showthread.php?t=1479361") got most of my touchpad features working including 2-finger scrolling and 2 finger right click.

---

### Post by brettdunnam on 2010-08-26
I asked the same question and ended up answering it myself. Here is the solution:
1. Create a file and save it wherever you want with these contents:
```
#!/bin/sh
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```

2. Make it executable with chmod +x
```
sudo chmod +x /path/to/file
```

3. Add the file to Startup Applications in System>Preferences>Startup Applications

That's from my lonely thread: [http://ubuntuforums.org/showthread.php?t=1561311&highlight=1201n+trackpad](http://ubuntuforums.org/showthread.php?t=1561311&highlight=1201n+trackpad)

---

### Post by g01d10x on 2010-10-02
Hey everyone .. I have just finished unboxing the little netbook, and have gone for the ubuntu install as well .. I was really hoping for the two-finger scrolling to work, and wanted to say THANKS VERY MUCH :o)

Cheers from Vancouver !

---

### Post by droggelbecher on 2010-11-30
Hi,I'm new with Linux and created a new file (I called it 'touchpad') on my desktop, but sudo chmod +x /home/myname/desktop/touchpad in the terminal doesn't funktion, there is only "no access on „/home/myname/desktop/touchpad“ and "no such file or direction" after I enter my password. Should I rename the file somehow?

---

### Post by droggelbecher on 2010-12-01
So I mean what is the name of the path exactly, when the file is on the desktop?
Thanks

---

### Post by VeeDubb on 2010-12-02
Linux is case sensitive.

That means you need to use ```
/home/myname/Desktop/touchpad
``` and NOT ```
/home/myname/desktop/touchpad
```

However, it would be better to use a more sensible location like /home/myname/bin/touchpad so you don't clutter your desktop with this sort of thing.

---

