---
title: "Text &amp; applications are gigantic on my lower resolution external monitor, DPI issue?"
date: 2016-04-29
forum: Hardware
---

### Post by chris-handwerker on 2016-04-29
[FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]I'm using Ubuntu 14.04 on a macbook with a 2880x1800 retina display and I have a 1920x1080 external monitor connected.[/COLOR][/FONT]

[FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]The problem I'm having is that text and applications on my external monitor are ridiculously gigantic compared to my primary retina display.[/COLOR][/FONT]

[FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]It seems like Ubuntu isn't choosing the correct DPI for my external monitor taking into account its physical size.

I looked for a DPI setting under System Settings -> Displays but I wasn't able to find anything.

Any ideas or is this a bug?[/COLOR][/FONT]

---

### Post by Crimple on 2016-04-29
The settings are the same for whatever monitor you connect to. That means that if you connect to a lower resolution screen you'll have to change the settings accordingly.
Go to System Settings/Displays and slide the *scale for menu and title bars* bar.
You'll have to adjust your browser as well, in Firefox go to *about:config* (type that in the address bar) and change *layout.css.devPixelsPerPx *to a lower value.

---

### Post by chris-handwerker on 2016-04-29
Huh, I got some things looking better by adjusting the *scale for menu and title bars* on my left monitor but it's still not right.

The main issue is that my terminal is set up to use an 16pt font to be readable on my retina display but that ends up being 3x larger when I drag my terminal over to my lower resolution display.

So it seems like that slider isn't adjusting DPI but rather adjusting the scale of GUI elements which leaves out some things such as the font in my terminal.

The main issue is Ubuntu seems to be ignoring the physical size of my displays when coming up with a DPI, is there a setting somewhere to change DPI?

Also I am using Chrome not Firefox.

---

### Post by Crimple on 2016-04-29
Install Unity Tweak Tool from the Software Centre (in case it's not installed already) 
go to *Fonts*
change [I]Text scaling factor

[/I]As to Chrome I can't help but take a look [here]("https://wiki.archlinux.org/index.php/HiDPI#Chromium_.2F_Google_Chrome")

---

### Post by chris-handwerker on 2016-04-29
Ok but that changes the text scaling on all displays so if I make it look right on my lower resolutions display fonts are way too small on my high resolution display.

What I'm really trying to find is a setting to adjust the DPI individually for each monitor.

Really I think Ubuntu (or Unity or whatever) should be taking in to account the physical size of the display and coming up with a correct DPI value automatically but this doesn't seem to be happening.

I found this command,

[FONT=courier new]xrdb -query[/FONT]

Which tells me that the DPI is 96 but... it isn't reporting for which monitor it is using that value for. I wonder if what is going on is that it is using 96 DPI for all my displays which doesn't sound right at all.

The DPI for my 2880x1800 15.4 inch (diagonal) retina at should be 220 DPI. 
The DPI for my 1920x1080 21.5 inch (diagonal) dell monitor should be 102 DPI.

---

### Post by Crimple on 2016-04-29
> **chris-handwerker said:**
> What I'm really trying to find is a setting to adjust the DPI individually for each monitor.
I don't think that's possible, but since I'm not sure I'll be happy if someone else corrects me.

---

### Post by chris-handwerker on 2016-05-02
Hmm, I think this needs to be reported as a bug then. It's simply not scaling my displays correctly. Anyone know where the right place to report this would be?

---

### Post by chris-handwerker on 2016-05-17
So, does anyone know the correct place to report this bug? It's really very broken right now.

For example: [http://imgur.com/elmvFR6](http://imgur.com/elmvFR6)

---

