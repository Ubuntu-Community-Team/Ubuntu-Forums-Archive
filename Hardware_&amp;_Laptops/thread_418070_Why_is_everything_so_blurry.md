---
title: "Why is everything so blurry?"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by liuhuanjim013 on 2007-04-22
I've no idea how to resolve this. Please help me.

---

### Post by barney_1 on 2007-04-22
That's kind of a tough question because I don't see any blurring in the thumbnail you posted.  Is there another monitor that you could try?

Otherwise, what video drivers are you running?  Perhaps you could try reconfiguring X:

Backup xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Reconfigure
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the prompts.  When it auto-detects your video card, try choosing "vesa"

Restart Gnome:
```
sudo /etc/init.d/gdm restart
```

If you can't get back into X restart your computer and at the grub menu choose "recovery mode".  When you get back to the console run this:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
exit
```

---

### Post by liuhuanjim013 on 2007-04-22
thanks barney, it doesn't look that bad because i'm currently using smaller fonts to make it look nicer

the attached picture is the screenshot i took under windows on the same laptop

i'll try your method later and i'll let you know the result, actually i've reinstalled ubuntu several times already

---

### Post by LindsaySlater on 2007-04-22
Hey, I tried this, but I think something went wrong... I am now stuck with a resolution of 640x480, and no easy way to change it back.. did I biff something when I was following the prompts? It did clear up the fuzziness though...

---

### Post by kerry_s on 2007-04-22
> **LindsaySlater said:**
> Hey, I tried this, but I think something went wrong... I am now stuck with a resolution of 640x480, and no easy way to change it back.. did I biff something when I was following the prompts? It did clear up the fuzziness though...

Try this-> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by kerry_s on 2007-04-22
> **liuhuanjim013 said:**
> thanks barney, it doesn't look that bad because i'm currently using smaller fonts to make it look nicer

the attached picture is the screenshot i took under windows on the same laptop

i'll try your method later and i'll let you know the result, actually i've reinstalled ubuntu several times already


Try this-> sudo dpkg-reconfigure fontconfig-config

---

### Post by LindsaySlater on 2007-04-22
This is what I had tried before, and ended up with the fuzzies.. so I followed the instructions posed here, and got a little tiny screen.. now it looks like I have it, the problem appears to be solved! Thanks muchly!

---

### Post by liuhuanjim013 on 2007-04-23
i tried all above, and restarted after each try, none of them worked on my machine :(

---

### Post by tommcd on 2007-04-23
> **liuhuanjim013 said:**
> i tried all above, and restarted after each try, none of them worked on my machine :(

First, find you monitor's horizontal sync and vertical refresh rates in your manual, or the manufacturers website, or google them.
Next, run "sudo dpkg-reconfigure xserver-xorg" again. When you get to the end, where you configure your monitor, choose "advanced". Type in the horizontal sync and vertical refresh rates, then choose the screen resolutions you want by scolling up and down with the arrow keys and select them with the space bar. 
Finish and type "sudo reboot". Hopefully, setting up xorg.conf according to your monitor's specs will improve the situation.
Are the fonts just bad in firefox, or everything? If it is just firefox, then open edit>preferences in firefox and experiment with fonts. Try "monospace" if no other one helps.

---

### Post by skip27 on 2007-04-23
Hi liuhuanjim013,

Sounds like you're not liking the default antialiasing. There's a few things you can try:

Above all else, I would recommend visiting this thread: [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670). This will install the Freetype/Cairo libraries that will give you "Windows-like" font smoothing. It's very impressive, and some argue that it even surpasses the quality of fonts under Windows. However, there are a few other things you can try:

1) Under the Preferences menu, run the 'Font' control panel applet. You'll be able to configure the various types of subpixel rendering, etc. that will adjust the appearance of the fonts. If you're still not content...
2) Go into the console and run 'sudo dpkg-reconfigure fontconfig-config' and follow the instructions. You'll get three prompts: First, whether to use native rendering, autohinting, or nothing. Second, whether to always use subpixel rendering, to automatically determine it, or to never use it. Finally, it will ask if you want to use bitmapped fonts. Assuming you're using MS fonts, you'll probably want to go with the Native/Always/No setup (in that order). Or...
3) Edit your .fonts.conf file in $HOME. If it doesn't exist, create it. Add this:
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```
4) Change the default font in Firefox to something like Bitstream Vera or DejaVu. These fonts were created specifically for the Linux font rendering schemes and should provide far better readability.

I hope this helps.

---

### Post by liuhuanjim013 on 2007-04-23
thanks guys! everything looks crystal clear now!

i followed the thread skip27 suggested
[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

then i viewed all the fonts and finally i found arial works perfectly on my laptop

thanks again everyone!

---

### Post by ubnewbie2 on 2007-04-27
> **skip27 said:**
> Hi liuhuanjim013,

Sounds like you're not liking the default antialiasing. There's a few things you can try:

Above all else, I would recommend visiting this thread: [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670). This will install the Freetype/Cairo libraries that will give you "Windows-like" font smoothing. It's very impressive, and some argue that it even surpasses the quality of fonts under Windows. However, there are a few other things you can try:

1) Under the Preferences menu, run the 'Font' control panel applet. You'll be able to configure the various types of subpixel rendering, etc. that will adjust the appearance of the fonts. If you're still not content...
2) Go into the console and run 'sudo dpkg-reconfigure fontconfig-config' and follow the instructions. You'll get three prompts: First, whether to use native rendering, autohinting, or nothing. Second, whether to always use subpixel rendering, to automatically determine it, or to never use it. Finally, it will ask if you want to use bitmapped fonts. Assuming you're using MS fonts, you'll probably want to go with the Native/Always/No setup (in that order). Or...
3) Edit your .fonts.conf file in $HOME. If it doesn't exist, create it. Add this:
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```
4) Change the default font in Firefox to something like Bitstream Vera or DejaVu. These fonts were created specifically for the Linux font rendering schemes and should provide far better readability.

I hope this helps.


I tried these things too, and though the fonts are clearer now, they are still not as clear as when I boot into Mandriva/KDE. 

There is definitely something going wrong with the rendering because the fonts shift and change size as you adjust the smoothing/anti-aliasing settings.

...and Firefox seems to suffer worse than most apps, even when using the same fonts.

Bottom line, I use Windows at work, and, until recently, Mandriva at home, and none have ever given me the eyestrain I am getting from Ubuntu (Feisty).

How can Feisty look different to Mandriva, if they are both using the same xorg/KDE/gnome ?  I am tempted to install Debian, just to see if it has the same problem.

---

### Post by liuhuanjim013 on 2007-04-27
I felt exactly as you do until a few days ago. Have you tried all the fonts? Things definitely work out on my Ubuntu now.

Actually I'm running GNOME on KUBUNTU.

---

### Post by ubnewbie2 on 2007-04-27
Well, I am encouraged that some people have been able to get it looking well enough.  I am still experimenting.

---

### Post by LindsaySlater on 2007-05-21
Well, This topic is old, but it describes previous troubles... I decided after a while of trying to figure this issue out that i could live with a small screen (800X600, and not using the entire display area).. Well, I love Ubuntu, and I'm feeling more confident about messing around... All evening I've been playing around with the Xorg config files, trying to get a setting I like... The only time the entire screen is in use is by choosing NeoMagic in the display options (I do have a NeoMagic card) and then I still only have 800X600 resolution... It's not just the fonts that are blury  but everything... Is there a fix, or should I get a new laptop?

---

### Post by matthew871 on 2007-07-01
It's blurry because Linux or GNOME likes blurry fonts. It's apparently made by people who have bad vision and cannot see well and cannot afford eye glasses. 

If you take a screenshot of a Linux screen and put it into a picture editor and blow it up you see that there are greys of pixels around the main black pixels of the font letters and that's just how Linux likes to be apparently, because I've found that installing Microsoft free fonts on this here Linux has not looked as good as it does in XP, etc. Cause if you blow up an XP screenshot and look at the fonts, typically they will be very sharp, just black-color for the pixels of all the fonts, and none of that hinting or dithering or whatever it is that causes blurring just like stinky Macintoshes.

---

