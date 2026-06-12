---
title: "Screen Doesn't Dim"
date: 2008-11-15
forum: Hardware
---

### Post by malfist on 2008-11-15
I can't get my screen to dim when I unplug my laptop. It shows the brightness bar, and it decreases, but the brightness of the lappy's screen doesn't dim. Anyone know how to fix this?

---

### Post by blackened on 2008-11-15
What make/model laptop are you using? With hardware issues like these it always essential for you to include hardware specs in order to get any kind of meaningful reply.

---

### Post by malfist on 2008-11-15
Sorry, it's a Gateway C-140X. It uses some sort of integrated intel graphics card that supports 3D. How do I find out it's make?

---

### Post by blackened on 2008-11-15
```
lspci | grep Display
```

---

### Post by malfist on 2008-11-15
```

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

---

### Post by blackened on 2008-11-15
Post the output of
```
xrandr
```

---

### Post by malfist on 2008-11-16
```

jerome@ubuntu-lappy:~$ zrandr
Xreen 0: minimum 320 x 200. current 1280 x 768, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x768+0+0 (neormal left inverted right x axis y axis) 305 x 183mm
    1280x768    60.0*+
    1024x768    60.0
    800x600     60.3
    640x480     59.9

```

My Xorg.conf is empty too...

---

### Post by blackened on 2008-11-16
You might be able to switch the backlight control to restore your function keys. Getting it to work on ac adapter is gonna take a little more work.
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

---

### Post by malfist on 2008-11-16
That fixed it!

edit: it doesn't stick after a reboot

---

### Post by blackened on 2008-11-16
> **malfist said:**
> That fixed it!

edit: it doesn't stick after a reboot

Yeah, I added it to System->Preferences->Sessions so it would run that command at startup.

---

### Post by malfist on 2008-11-16
gnome-power-manager crashes now when I unplug my laptop, and then I can't adjust the brightness through the keys...

---

### Post by mdc4115 on 2008-11-16
i'm having the same problem. i've got the same stuff as ^ just a different gateway model.

lspci | grep Display
```

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

xrandr
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9 

```

> **malfist said:**
> gnome-power-manager crashes now when I unplug my laptop, and then I can't adjust the brightness through the keys...
its not really crashing it is just taking its time to slowly make the brightness go down. but this needs a fix.

---

### Post by chazdraves on 2008-11-16
Same problem on Gateway T6330u. Everything else works great - volume buttons and all, but I cannot turn down from full brightness (which is painfully bright even without the battery concerns). The above solution does work, but if the screen gets turned down to minimum brightness (or if Ubuntu fades the screen down) the backlight will not turn back on without re-running that code (which is hard to do without a backlight).

Anyone know of a good fix for this? It must be Gateway-specific.

Thanks, all!
- Chaz

---

### Post by blackened on 2008-11-16
> **chazdraves said:**
> Anyone know of a good fix for this? It must be Gateway-specific.

It's not, it happens on my Sony laptop.

Ok so, here's the story: after much toying with this I've come up with a better, but somewhat limited solution.

First off a question: did your backlight function keys work before the xrandr command was issued? If they didn't, then this may not be the kinda-sorta magic pill you're hoping for. Changing the backlight control to native doesn't crash power manager over on my end, but since it does for you the xrandr command isn't gonna cut it. So on with the sorta fix.

What we're gonna do is write some scripts for acpi to use when you plug and unplug the ac adapter.

```
gksudo gedit /etc/acpi/ac.d/99-backlight.sh
```

This will open a blank document in gedit. You will need to add this to the blank document:
```
#!/bin/bash
if on_ac_power; then
setpci -s 00:02.0 F4.B=FF
else
setpci -s 00:02.0 F4.B=**80**
fi
```

The last two characters in the next to last line (the bold 80) are the hex code for the percentage of brightness when on battery power. Adjust this to your liking (it's set for 50% right now {255/2=~128=0x80}).

Now we make it executable:
```
sudo chmod +x /etc/acpi/ac.d/99-backlight.sh
```

Now we copy it to the other three applicable events:
```
sudo cp /etc/acpi/ac.d/99-backlight.sh /etc/acpi/battery.d
sudo cp /etc/acpi/ac.d/99-backlight.sh /etc/acpi/start.d
sudo cp /etc/acpi/ac.d/99-backlight.sh /etc/acpi/resume.d

```

Go ahead and test it by unplugging your ac adapter. It should drop the screen brightness to 50%. The problem with this is that if you open a terminal and use xbacklight to check the screen brightness, then it will report 100%. If you use the backlight function keys to lower the brightness from there, then it will treat 50% as 100% and only get darker, not brighter than the 50% we set using setpci. A minor drawback I think, considering I rarely change my backlight setting once on battery power (after it auto-dims).

Hope this helps, sorry it's so long winded, it really doesn't take that long to do though.

---

### Post by chazdraves on 2008-11-16
No, it's not terribly intimidating. I do have the same problem with it not working after unplugging/re-plugging. Also, I had the same problem with the screen showing the brightness indicator without the brightness changing. Does anyone know of a package that can make this work? Your idea sounds to work, but I'd like something in the vein of "works out the box" if possible. Is this a driver problem we're up against?

Thanks, all!
- Chaz

---

### Post by blackened on 2008-11-16
It's a problem with gnome-power-manager. Your only real recourse is to submit a bug report on launchpad (which I would suggest doing anyway). Hopefully it'll be fixed in an update, or at least make it into Jaunty.

---

### Post by chazdraves on 2008-11-16
I guess I'm not concerned about recourse, I'm just curious if there's already a fix for this problem. Someone else must have run into this already...?

- Chaz

---

### Post by malfist on 2008-11-16
Okay, I tried your initial fix, but not the second one and I can tell you, it does not work!

After about 15 minutes of use, the screen starts dimming on battery power, until it is impossible to see. Since gnome-power-manager isn't responding, I can't get the screen to return to brightness. I can do the xsetbacklight 100, and it will flicker to full brightness and drop back down. The only time xsetbacklight works is when it's on native, and the gnome-power-manager is responding in a reasonable time. The only time it respondes reasonably is when it is plugged into AC and has been. If you plug it back up, it takes it a good two or three minutes to begin responding. I will try the second fix later and sumbit a bug report too. This hasn't been working since 7.04, the last time I tried ubuntu on my laptop (I use it on my desktop 100%).

Edit: the screen dimming works in gentoo, mandriva, and fendora as of last year. I'm assuming this is a ubuntu only issue.

---

### Post by chazdraves on 2008-11-17
I just wanted to say "thanks" for the above post. Your idea does seem to work. It's too bad that I still can't control the brightness with either the keys or the app, but at least I can have preset values below the blinding 100% it's been operating at.

If you come up with any other tricks, do let me know!
- Chaz

---

### Post by blackened on 2008-11-17
> **malfist said:**
> Okay, I tried your initial fix, but not the second one and I can tell you, it does not work!

After about 15 minutes of use, the screen starts dimming on battery power, until it is impossible to see. Since gnome-power-manager isn't responding, I can't get the screen to return to brightness. I can do the xsetbacklight 100, and it will flicker to full brightness and drop back down. The only time xsetbacklight works is when it's on native, and the gnome-power-manager is responding in a reasonable time. The only time it respondes reasonably is when it is plugged into AC and has been. If you plug it back up, it takes it a good two or three minutes to begin responding. I will try the second fix later and sumbit a bug report too. This hasn't been working since 7.04, the last time I tried ubuntu on my laptop (I use it on my desktop 100%).

Edit: the screen dimming works in gentoo, mandriva, and fendora as of last year. I'm assuming this is a ubuntu only issue.

I also have the problem of the gnome-power-manager not responding occasionally. I don't have an explanation for it though, as it seems quite random on my end. 

> **chazdraves said:**
> I just wanted to say "thanks" for the above post. Your idea does seem to work. It's too bad that I still can't control the brightness with either the keys or the app, but at least I can have preset values below the blinding 100% it's been operating at.

If you come up with any other tricks, do let me know!
- Chaz

That sucks that you can't use the function keys, but I'm glad at least that the dimming on unplug works for you. I'll make sure to update you if I make any progress on this issue.

---

### Post by Meow27 on 2008-11-17
the devs dont like the vaio FS series :(

im having a similar problem but when i touch the brightness applet, my system freezes for 5 minutes. (if it ever recovers)

---

### Post by chazdraves on 2008-11-17
I wish I could be more help in this matter, but I'm no programmer, and I just don't have that level of technical understanding. As a Windows-convert, I've never had to get involved at this level...

- Chaz

---

### Post by sev(n) on 2008-11-18
I'm having a similar problem with my Dell Inspiron 630m, the function keys worked perfect for me in hardy. Now however, I just press the increase/decrease brightness button once and the indicator pops up and goes all the way down / up. Also after using one of these keys my keyboard stops working. Even when I do manage to get the brightness up my screen dims back to nothing after about 10 minutes. Dim on battery and dim when idle are off in gnome-power-manager

---

### Post by mdc4115 on 2008-11-22
anyone hear anything new on this topic? it would be nice to have my battery last longer. i wish i could help but i don't know any programming yet.

---

### Post by blackened on 2008-11-23
> **Meow27 said:**
> the devs dont like the vaio FS series :(

I'm sure that's not the case. The devs can only do so much given time frames and work load.

> **Meow27 said:**
> 
im having a similar problem but when i touch the brightness applet, my system freezes for 5 minutes. (if it ever recovers)

Did you try setting the backlight control to native or combination? This seems to work well on most Sony models.

> **mdc4115 said:**
> anyone hear anything new on this topic? it would be nice to have my battery last longer. i wish i could help but i don't know any programming yet.

Have you tried my fix from post #14? It won't help with on-the-fly adjustment of your screen brightness, but it should at least get you a static setting based on plugged-in/not plugged-in status.

---

### Post by mdc4115 on 2008-11-23
i tried that and it would take forever to fade down. i guess i can wait until there is a proper fix for it. thanks for all the help though.

---

### Post by ieatfish on 2008-11-24
I was following this: [http://people.freedesktop.org/~hughsient/quirk/quirk-backlight-index.html](http://people.freedesktop.org/~hughsient/quirk/quirk-backlight-index.html)

and had multiple laptop_panel readings.  I did what was listed and now I have no readings.  I removed the blacklist but can't seem to get back to where I was.  I used to be able to use my function keys and have the brightness display come up and show that I was changing it but now nothing happens.  I am on a Gateway T6330U.

edit: Oh, it came back.

---

### Post by chombium on 2008-11-26
> **blackened said:**
> Yeah, I added it to System->Preferences->Sessions so it would run that command at startup.

I've set the command as you suggest on Gateway P-6822, but after reboot the function buttons for brightness control don't work at all, the brightness gauge is not shown, and after a while the screen gets dark.

Any ideas?

btw. The script for brightness control when the adapter is pulled out works great. But I would suggest instead of copying the shell script to the three locations symbolic links to be used.

BR, Jovan

---

### Post by blackened on 2008-11-26
> **chombium said:**
> I've set the command as you suggest on Gateway P-6822, but after reboot the function buttons for brightness control don't work at all, the brightness gauge is not shown, and after a while the screen gets dark.

Any ideas?

I don't have a solution for you. Mine does this sometimes as well, and I have no explanation.

> btw. The script for brightness control when the adapter is pulled out works great. But I would suggest instead of copying the shell script to the three locations symbolic links to be used.

BR, Jovan

Yes, that would work equally well.

---

### Post by Ecologger on 2008-12-12
I would just like to say the command to give native backlight control to function keys works for Gateway T-6836. I might have a fix for the gnome-power-manager not responding check this and see if it works:
> 
kill gnome-power-manager:

```
killall gnome-power-manager
```

open gconf-editor

```
gconf-editor
```

find apps -> gnome-power-manager -> ambient Uncheck "enable"
also apps -> gnome-power-manager -> backlight Uncheck "enable"
close gconf

resart gnome-power-manager

```
gnome-power-manager
```

Not my idea, check out :[http://ubuntuforums.org/showthread.php?p=6357161#post6357161]("http://ubuntuforums.org/showthread.php?p=6357161#post6357161")

Good Luck!

---

### Post by some11 on 2010-03-27
> **blackened said:**
> 
```
#!/bin/bash
if on_ac_power; then
setpci -s 00:02.0 F4.B=FF
else
setpci -s 00:02.0 F4.B=80
fi
```.


Thank you so much for this!
This is what I needed to put the brightness up and down on my Samsung P510 (SHOULD also do R510 too!)
Just need to be able to put it into a script now...Any ideas?
Ive seen this:
[http://www.pastebin.ca/834514](http://www.pastebin.ca/834514)
[http://www.pastebin.ca/834518](http://www.pastebin.ca/834518)
Just dunno how to read 00:02.0 F4.B...

Any ideas?

Thanking you now! (=

---

