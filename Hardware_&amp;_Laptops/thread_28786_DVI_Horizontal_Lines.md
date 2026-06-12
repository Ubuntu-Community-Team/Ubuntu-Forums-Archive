---
title: "DVI Horizontal Lines"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by Deusiah on 2005-04-21
**SOLUTION: Change 24-bit Colour Depth to 16-bit** 

I'm having a really anoying problems with horizontal lines flasing across my monitor when I use DVI. I have tried changing the refresh rates but to no avail. I tried using a standard analogue connection which worked but was too fuzzy to use.

Does anyone have any idea's for things I can try to fix this?

Thanks

---

### Post by Vache on 2005-04-21
[QUOTE=Deusiah]I'm having a really anoying problems with horizontal lines flasing across my monitor when I use DVI. I have tried changing the refresh rates but to no avail. I tried using a standard analogue connection which worked but was too fuzzy to use.

Does anyone have any idea's for things I can try to fix this?

Thanks[/QUOTE]
 What is your video card and monitor?

A 'fuzzy' picture typically means bad hardware :(

---

### Post by Deusiah on 2005-04-22
Sorry I forgot to mention it.

My graphics card is an ATI Radeon 9800XT and my screen is a Digimate 1916 19". The fuzzyness only occours when I plug-in an analouge cable. I can't get the monitors clock right for some reason,

I know this is not a hardware issue becuase the montior works flawlessly with Windows.

---

### Post by heimo on 2005-04-22
Maybe it's modeline issue - video card demanding too much from monitor. Try setting Monitor HorizSync and VertRefresh to monitors specifications and making sure that the modeline that is used, is within those limits. Some instuctions:

[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")

---

### Post by Deusiah on 2005-04-22
Thanks for your reply,

As I mentioned earlier I have messed with the refresh rates, I have lowered them and set them to the exact manufacturer specification down to the last point three digits.

As for your modeline suggestion, this is one area I have not looked into. From memory all of my modeline are commented out, I use a pretty much defualt fglrxconfig generated xorg.conf file.

I don't really understand the whole Modeline thing, I don't understand what parts refer to what or how to create my own. Do you think this would perhaps solve my issue? What is the purpose of Modelines?

---

### Post by heimo on 2005-04-22
I admit I don't understand the Modelines too well either, but it's about timings of the analog signal. You could try programs like gtf and xvidtune to make your own. But if you already experimented with built-in modelines, this is quite unlikely cause - but still worth trying.
 
I'd also try (just to rule out causes) generic driver like vesa. Also the log file for xorg is a good source of information for troubleshooting.
 
EDIT: Oh, the modeline defines timings, which dictate resolution and refresh rate - and it's in direct relation to VertRefresh, HorizSync and dot / pixel clock. If some of those values go over the cababilities of your graphics card or monitor (or near the limits), you can get bad image quality.
 
HorizSync is typically somewhere in 40-100 kHz, vertical refresh rate 60 - 100 Hz and dot clocks are in megaherz range (typically 100-200 MHz) - that one is the frequency your graphics card uses to send the signal to monitor - vertical refresh rate is the refresh rate we're talking about with resolution [email="1024x768@75Hz"]1024x768@75Hz[/email] for example.

---

### Post by Deusiah on 2005-04-22
Ohh well in that case that's why they were commented out since I'm using DVI. The horizontal lines only appear then but my monitor is too fuzzy to use when using analouge.

A guess the generic driver would be a good test, I'll give it a go. Though if it works I'll be no nearer to fixing my problem so that could be looked upon as a pointless exercise lol.

As for the log files, I doubt I'll find anything interesting in them as I don't think this is an error at all. Just some incompatibility with my graphics card and monitor which I believe can be resolved through some xorg.conf setting.

This sounds like the same problem [http://lists.freedesktop.org/archives/xorg-bugzilla-noise/2005-March/007222.html](http://lists.freedesktop.org/archives/xorg-bugzilla-noise/2005-March/007222.html) though I use 1280x1024.

I don't know if this helps but the lines change colour depending on what bakground they are only. Mostly they are blue when on light backgrounds, when on dark backgrounds they are red. They also seem to tie in with CPU usage. The more there is the worse it gets.

Also when I scroll on a webpage the lines follow it but they do flicker on and off randomly too.

---

### Post by heimo on 2005-04-22
It only happens when you're using analog? Analog with d-sub cable or analog with dvi cable? I'm not trying to be smartass here - I'm just trying to understand this:
[http://suif.stanford.edu/~csapuntz/rv280-linux-dvi.html]("http://suif.stanford.edu/~csapuntz/rv280-linux-dvi.html") 
 
You know - you can send analog signal with DVI cable too. On that link, the problem was too high dot clock and it can be affected altering timings (modeline). xvidtune can do this - but it'd probably be better to check your logfile as there is sometimes also automaticly probed alternative screen modes for your monitor. It's really valuable source of information.

---

### Post by Deusiah on 2005-04-22
Sorry for my ignorance, I assumed DVI was digital only as the name suggests. What I meant to say was this problem only comes into efffect when I am using the DVI port on my monitor.

All this talk of dotclock and reduced blanking interval timings seems rather confusing. I get the impression I have to create a modline with reduced blanking interval timings but have no idea how.

I will take a look at xvidtune and the log file tonight when I get home (at work at the moment ;)).

Thanks for your help!

---

### Post by heimo on 2005-04-22
Hmm.. ok, now I'm beginning to understand. However I'm quite unsure if modeline should have much difference with digital connection, but according those linked pages, it does.
**[font=Arial,Bold][size=1][/size][/font]** 
[b][font=Arial,Bold][size=1]Display modes your monitor supports (according to manual):
[/size][/font][/b][left]```

Resolution Horizontal Frequency (KHz) Vertical Frequency (Hz)
640X350 31.475 70.100 
640X480 31.469 59.940
640X480 37.500 75.000
720X400 31.469 70.087
800X600 37.879 60.317
800X600 46.875 75.000
1024X768 48.363 60.004
1024X768 60.023 75.029
1280X1024 63.981 60.020
1280X1024 79.976 75.024

``` 
 
Try these in your xorg.conf Monitor section:
```

HorizSynd 30-79 
VertRefresh 56-75

``` [font=Arial,Bold][size=1][b]
 [/left]
[/b][/size][/font][left] 
[b][font=Arial,Bold][size=1] [/left]
[/b][/size][/font]

---

### Post by Deusiah on 2005-04-22
Yeah those are the same modes as in my manual.

I have tried:
HorizSynd 63.981
VertRefresh 60.020

and:
HorizSynd 79.976
VertRefresh 75.024

I'll have a go with your suggested setting tonight thanks.

---

### Post by ignavia on 2005-04-22
Deusiah, if your computer's not doing anything, are the lines still there? Mine only appear when something's happening. I'm also not using DVI, just good ol' VGA. I haven't tried changing resolutions or refresh rates... I'm at 75Hz now. I'd hate to drop to 70, but I guess it's not as bad as 60. 70's tolerable. I'm also not giving up my 1600x1200.

---

### Post by Deusiah on 2005-04-22
Well I have lines all the time depending on what application I am using. If a Firefox window has focus they are none stop, if Gnome Terminal has focus they stop even with Firefox full screen in the backround. 

They are CPU usage dependant as well. The more CPU usage the more lines.

---

### Post by ignavia on 2005-04-22
[QUOTE=Deusiah]Well I have lines all the time depending on what application I am using. If a Firefox window has focus they are none stop, if Gnome Terminal has focus they stop even with Firefox full screen in the backround. 

They are CPU usage dependant as well. The more CPU usage the more lines.[/QUOTE]
 Sounds like mine, except it's possible for me to have no lines with FF in front, as long as CPU usage is low.

---

### Post by Deusiah on 2005-04-22
I have finally fixed it! I was messing about with every possible option, turning things on and off and then I found out the problem.

Either my graphics card when it uses DVI or my monitor does not like 24-bit depth. I simply changed this too 16-bit like so.

```
    Subsection "Display"
        Depth       16
``` 

I really hope this fixes your problem ignavia.

Thanks to all who have replied :D

---

### Post by ignavia on 2005-04-22
[QUOTE=Deusiah]I have finally fixed it! I was messing about with every possible option, turning things on and off and then I found out the problem.

Either my graphics card when it uses DVI or my monitor does not like 24-bit depth. I simply changed this too 16-bit like so.

```
    Subsection "Display"
        Depth       16
``` 

Now it works perfectly and I feel like a right idiot, just checking the manual reveals the colour support to be "16.7M Colours".

I really hope this fixes your problem ignavia.

Thanks to all who have replied :D[/QUOTE]
 Just so you know, 16.7 million colors *is* 24-bit. 16-bit is only 65536 colors, which looks like crap with photos or anything with smooth gradients. FWIW, my problem goes away at 60Hz, and it gets less bad as I decrease from 75Hz down to 60. It's also gone at 1280x1024.

---

### Post by Deusiah on 2005-04-23
It's still running in 24-bit, the display looks the same and I have tested it on both photos and gradients. 

This is all of my screen section, as you can see the default depth is still 24, somehow setting the display to 16 stops the problem but still gives me 24-bit depth.

```
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       16
        Modes       "1280x1024"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection
``` 

Anyway, I'm glad you fixed your prob, odd that they weren't related.

---

### Post by heimo on 2005-04-23
[QUOTE=Deusiah]It's still running in 24-bit, the display looks the same and I have tested it on both photos and gradients. 
[/QUOTE]

That's because you still have 'DefaultDepth 24' line and only changed the subsection. It's probably using some fallback default if it can't find subsection for 24-bit depth. But what ever fixes problem, is a good solution.

---

### Post by Deusiah on 2005-04-24
Perhaps that's what's happening but it does seem odd that doing that fixes the problem. I should try setting the defualt depth to 16 to see if I can notice any changes.

---

### Post by heimo on 2005-04-24
[QUOTE=Deusiah]Perhaps that's what's happening but it does seem odd that doing that fixes the problem. I should try setting the defualt depth to 16 to see if I can notice any changes.[/QUOTE]

My quick guess (without rereading this thread) is that without matching subsection some different modeline gets selected, which works better. What I'd do is rename /var/log/Xorg.0.log, start X, close X, rename /var/log/Xorg.0.log to A, change xorg.conf to previous settings, start X, close X, rename /var/log/Xorg.0.log to B and run *diff A B | less *to check what's the difference.

But hey! It's good it works.

---

