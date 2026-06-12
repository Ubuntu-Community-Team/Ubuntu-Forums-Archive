---
title: "Blank screen after boot"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by Matt B on 2008-12-14
Hi,

I recently decided to make the switch to Ubuntu using my laptop, which is a Vye mini-V S18 (I believe it is one of these - [http://www.dabs.com/ProductView.aspx?Quicklinx=4KJM](http://www.dabs.com/ProductView.aspx?Quicklinx=4KJM).)

I had some issues with the Live CD (I couldn't get it to boot from the CD), so I used the Alternate ISO, and all seemed to be working so far. I installed Ubuntu as the only OS (I had recently formatted the machine so had no data to lose) and all was well.

But once I restarted I got the normal Ubuntu splash screen, with the loading bar, then nothing. The laptops monitor just showed a blank screen. I thought this was a bit odd, and so I got a spare LG TFT monitor and plugged it into the VGA port on the side of the Vye - the Ubuntu desktop appeared instantly on the second monitor.

However, having a 17" TFT attached to the laptop rather defeats the idea of a UMPC. So does anyone have any suggestions as to how I could get the laptop's screen working? 

I have looked at the manufacturers website, and they do have what seem to be Linux drivers for the S18 ([http://www.vyepc.com/vyesupport/index.php?path=S18%2FDrivers%2FLinux+unsupported/](http://www.vyepc.com/vyesupport/index.php?path=S18%2FDrivers%2FLinux+unsupported/)) and there are display drivers there - could these help? And how would I go about installing them?

I would really appreciate any suggestions - I am very new to Linux, but am keen to get it working on the Vye. I think the most frustrating part is that all of the hardware seems to be working, including the Bluetooth and Wifi, but just the monitor refuses to display the desktop!

If you need any more information - just let me know.

Thanks in advance,

Matt

---

### Post by miniyak on 2008-12-14
after the bios splash screen¸ grub¸ the boot loader shows up for about 3 seconds with in these seconds press the esc key¸ then see if you load in recovery mode or one of the older kernel versions&#729; If this works for you¸ i have more info

---

### Post by Matt B on 2008-12-15
I can boot into recovery mode but have the same issue - I haven't tried one of the older kernels - from what I can see there are only 2 available?

Anyway - when I try and boot into recovery mode, I can bring up a terminal prompt, but trying to boot into the desktop still presents the same problem.

---

### Post by joff13 on 2008-12-15
hi,

perhaps may be something wrong with x.org. When in grub menu, select the line you want to boot and press **e** for edit the line. at the end add **xforcevesa**

in this way you'll force X.org to use vesa resolution

---

### Post by Matt B on 2008-12-15
Hi joff13,

Thanks for the suggestion - I will give that a try this evening when I get home. Will report back!

Thanks for all your help.

Matt

---

### Post by linux_tech on 2008-12-15
Boot in recovery mode and type

```
sudo /etc/init.d/gdm start
```

or

```
gdm start
```

or 

```
startx 
```

---

### Post by blazemore on 2008-12-16
For those who are interested, I've had a similar problem
I tried booting with the XP disk, and I think it boots, but it displays nothing on the screen or an external monitor.
I think it is an issue with the graphics hardware.

Maybe look in the bios.

I have the same machine.

---

### Post by Matt B on 2008-12-16
> **joff13 said:**
> hi,

perhaps may be something wrong with x.org. When in grub menu, select the line you want to boot and press **e** for edit the line. at the end add **xforcevesa**

in this way you'll force X.org to use vesa resolution

I'm going to describe exactly what I did in case I did it wrong, sorry if this comes off a little silly, but I'm really new to Ubuntu and very keen to get it working. 

So, upon booting I pressed ESC to get to the menu with the different kernel/recovery mode options. I selected the top one and pressed 'e'. I then selected the longest line, pressed 'e' and added xforcevesa at the end. I then booted by pressing 'b', but I still had the same problem - the loading splash screen came up but when the desktop was meant to appear, the screen stayed blank. Pressing Ctrl + Alt + F1 drops me out to a command prompt, which I can see fine. So no joy.


> **linux_tech said:**
> Boot in recovery mode and type

```
sudo /etc/init.d/gdm start
```

or

```
gdm start
```

or 

```
startx 
```

I did these as well.

When I tried the first one at the prompt, it told me it was starting GNOME Desktop Manager, then I got the same blank screen. It makes a 'clunk' noise as well. Again, I can drop out to a prompt by pressing Ctrl+Alt+F1, and can see that fine.

When I tried the second one, exactly the same happens.

And finally, when I try the third one, the same happens, but I get a longer sound. I am guessing this is the desktop startup sound effect.

So no joy there either. 

[QUOTE=blazemore]For those who are interested, I've had a similar problem
I tried booting with the XP disk, and I think it boots, but it displays nothing on the screen or an external monitor.
I think it is an issue with the graphics hardware.

Maybe look in the bios.

I have the same machine. [/QUOTE]

I don't think it is a fault with my hardware, as I can boot windows XP without issue on the machine - it shows the desktop fine. I did have a look in the BIOS and the only option related to Graphics seems to be a setting called 'Graphics Memory', which is currently set to 8MB.

Could it be helped by installing the drivers from the Vye site that I linked to in my first post? If so, how would I go about installing them on Ubuntu (remember I have full access to the desktop through the 2nd monitor)?

Thanks again for all your help!

---

### Post by Matt B on 2008-12-17
Does anyone have any further suggestions?

I'm beginning to think that my display hardware is simply incompatible with the Ubuntu desktop. It's a pity because I know the rest of the hardware seems to be working great, and the Vye is such a good little laptop.

I know that some people have got the display working on the Kohjinsha versions - [this website]("http://www.ultramobilegeek.com/2007/03/kohjinsha-sa1-review.html") suggests that someone had the Live CD of Ubuntu booting up on a Kohjinsha SA1, which I think is the same model as mine (Vye laptops are just re-branded Kohjinshas.)

---

### Post by joff13 on 2008-12-17
hummm....

in the shell go to /var/log/xorg.log
 you'll find all step x.org has done. post it we may find out something

---

### Post by joff13 on 2008-12-17
I didn't know your laptop.. is this correct?
# Screen - 7' TFT 800 x 480 ( WVGA )

it,s a really small screen... as a next step you can try to backup your /etc/X11/xorg.comf file and use the one you can find here
[http://claudio.iannotta.ch/archives/98](http://claudio.iannotta.ch/archives/98)

it is really simple one but may be a start. 
Driver "vesa" 
it might be changed with 
Driver "vga"

But first, see my previews post

---

### Post by Matt B on 2008-12-17
> **joff13 said:**
> I didn't know your laptop.. is this correct?
# Screen - 7' TFT 800 x 480 ( WVGA )

it,s a really small screen... as a next step you can try to backup your /etc/X11/xorg.comf file and use the one you can find here
[http://claudio.iannotta.ch/archives/98](http://claudio.iannotta.ch/archives/98)

it is really simple one but may be a start. 
Driver "vesa" 
it might be changed with 
Driver "vga"

But first, see my previews post

Yes, it has a 7" widescreen display, I think. Very small - in fact the whole laptop is very small! My girlfriend hates it because the keyboard is too cramped for her to type properly!

I will try both your suggestions tonight when I get home. 

Thanks again, fingers crossed!

---

### Post by vikkevest on 2008-12-17
Dont know if it contributes to solving the problem but I had the same problem and you can read of what hardware I have and what I did here:

[http://ubuntuforums.org/showthread.php?t=1013205]("http://ubuntuforums.org/showthread.php?t=1013205")

---

### Post by Matt B on 2008-12-18
I changed my xorg.conf to the one on the site you linked to, and it works! Kind of!

I can now see the login screen on both my laptop screen and the external monitor, however the resolution is completely wrong - much too big. I can only see the very corner of the login screen. But it is a step forward nonetheless! 

Is it possible to edit xorg.conf to force it to display an 800x480 resolution?

Also, when I used the VGA driver, I had the same problem but ended up with a message saying that Ubuntu was running in a low graphics mode, or similar.

So, any ideas?

Thanks so much for all your help - this forum has been more help than all the rest of the internet put together!

---

### Post by Matt B on 2008-12-19
Any ideas? I didn't have a chance to paste the contents of xorg.log into this thread - I will do that tonight.

Was quite pleasing to see that the laptops screen still worked though!

---

### Post by joff13 on 2008-12-19
yes it's possible to specify the resolution
in the section "screen" add something like this: 

```

DefaultDepth     16
SubSection "Display"
	Depth     24
	Modes    "800x600" "640x480"
EndSubSection
SubSection "Display"
	Depth     16
	Modes     "800x600" "640x480"
EndSubSection


```

("800x600" you can leave out or add whatever you need)

should work , but first backup your file
for more info
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

and also, read the comments in xorg.conf, you'll find some command you can try to auto-configure x.org

Cheers

---

### Post by Matt B on 2008-12-20
Thanks so much! This worked great.

I am now using the vesa driver and have the desktop displaying without any problem on my laptop screen.

Thank you all so much for your help.

MAtt

---

