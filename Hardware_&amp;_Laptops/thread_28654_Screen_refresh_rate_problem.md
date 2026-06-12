---
title: "Screen refresh rate problem"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by themelvin on 2005-04-21
Hello.

I am using Kubuntu 5.04 and have serious problems with screen resolution and refresh rate.
In Windows i use 1024×768 it's a Philips 107P40 monitor that can support 1024×768@100Hz without any problems. In WIndows the refresh rate is set to 90Hz. But in Linux is set to 85Hz and the screen size is a bit different is smaller and slightly moved to right.

I would like to know, how can I change the refresh rate for any resolution, from 800×600 to 1280×1024. And How to move (change position) the screen left, right, up and down.
In Suse there was a software... I only needed to select the refresh rate and zhen the position of the screen and everything was perfect.

Thanks for the help

---

### Post by globalspace on 2005-04-21
[QUOTE=themelvin]Hello.

I am using Kubuntu 5.04 and have serious problems with screen resolution and refresh rate.
In Windows i use 1024×768 it's a Philips 107P40 monitor that can support 1024×768@100Hz without any problems. In WIndows the refresh rate is set to 90Hz. But in Linux is set to 85Hz and the screen size is a bit different is smaller and slightly moved to right.

I would like to know, how can I change the refresh rate for any resolution, from 800×600 to 1280×1024. And How to move (change position) the screen left, right, up and down.
In Suse there was a software... I only needed to select the refresh rate and zhen the position of the screen and everything was perfect.

Thanks for the help[/QUOTE]

hi :)
did you read this one ?
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)

Bye bye

---

### Post by themelvin on 2005-04-21
Hello,

I added these two lines in the MOnitor section:
```

HorizSync 30-107
VertRefresh 50-185
```
But nothing happend.

I' ll download the gtf, compile and post on how it went.

Thanks for the help.

---

### Post by globalspace on 2005-04-21
[QUOTE=themelvin]Hello,

I added these two lines in the MOnitor section:
```

HorizSync 30-107
VertRefresh 50-185
```
But nothing happend.

I' ll download the gtf, compile and post on how it went.

Thanks for the help.[/QUOTE]

yes,
also with me nothing change when i've applied the spec of my monitor... but with gtk all work ok ;)

---

### Post by themelvin on 2005-04-21
YES, it works!!!

At first I made a stupid mistake, I entered a line in device and restarted kde, but the result was an error in line 70 than i ran sudo nano /etc/X11/xorg.conf, deleted the line saved and now it works just perfectly.

But the screen is still a bit moved to right, the right side is cut off. How can i change the position, 1 or 2 pixels to left would be great.

Thanks.

---

### Post by globalspace on 2005-04-21
[QUOTE=themelvin]YES, it works!!!

At first I made a stupid mistake, I entered a line in device and restarted kde, but the result was an error in line 70 than i ran sudo nano /etc/X11/xorg.conf, deleted the line saved and now it works just perfectly.

But the screen is still a bit moved to right, the right side is cut off. How can i change the position, 1 or 2 pixels to left would be great.

Thanks.[/QUOTE]


good news  ;-) 
well sincerely i don't know but in forum i found this one :
[http://www.ubuntuforums.org/showthread.php?t=26418&highlight=monitor+position](http://www.ubuntuforums.org/showthread.php?t=26418&highlight=monitor+position)

hope it's usefull for you  :)

---

### Post by themelvin on 2005-04-21
Hello.

I am not sure that i understand what do I have to do.

My Monitor section says:
```

Section "Monitor"
        Identifier      "PHILIPS 107P"
        Modeline "1024x768_90.00"  100.19  1024 1088 1200 1376  768 769 772 809  -HSync +Vsync

        Option          "DPMS"

```

Now, the xdpyinfo says this:
```

dimensions:    1024x768 pixels (406x305 millimeters)
```

So I have to enter another line in Monitor section and it would be:
```
DisplaySize 406 305
```

Am I right or did I mess something up?

Offtopic, are you from Venice in Italy?

Thanks for the help

---

### Post by globalspace on 2005-04-21
[QUOTE=themelvin]Hello.

I am not sure that i understand what do I have to do.

My Monitor section says:
```

Section "Monitor"
        Identifier      "PHILIPS 107P"
        Modeline "1024x768_90.00"  100.19  1024 1088 1200 1376  768 769 772 809  -HSync +Vsync

        Option          "DPMS"

```

Now, the xdpyinfo says this:
```

dimensions:    1024x768 pixels (406x305 millimeters)
```

So I have to enter another line in Monitor section and it would be:
```
DisplaySize 406 305
```

Am I right or did I mess something up?

Offtopic, are you from Venice in Italy?

Thanks for the help[/QUOTE]


well, i don't know  :-P 
i see in the thread :

>  Modeline "1280x1024@75" 156.43 1280 1312 1904 1936 1024 1043 1056 1076 

the misures is near the modeline ...
sorry but i don't know ... try !  :grin: 

Offtopic :
Yes i come from venice .. Italy  ;-)

---

### Post by themelvin on 2005-04-21
I entered the DisplaySize but it doesn't work :(

My modeline line is different:
Modeline "1024x768_90.00"
And from the other thread:
Modeline "1280x1024@75"

Will set it like this: "1024×768@90" hope it works.

Offtopic: Io so parlare l' italiano ;)

---

### Post by themelvin on 2005-04-21
Nothing has changed. The screen is still a bit on the right side.

Is it possible that something else is wrong?

Thanks

---

### Post by themelvin on 2005-04-21
It's me again:

I don't have these two lines:
```

HorizSync 30.0 - 82.0
 VertRefresh 56.0 - 76.0

```

How do I know which numbers to enter for HorizSync and which for VertRefresh?

Thanks

---

### Post by globalspace on 2005-04-21
[QUOTE=themelvin]It's me again:

I don't have these two lines:
```

HorizSync 30.0 - 82.0
 VertRefresh 56.0 - 76.0

```

How do I know which numbers to enter for HorizSync and which for VertRefresh?

Thanks[/QUOTE]


you'll find it in the specs of your monitor ...
i've found all on my Manual and on the web site ;)

---

### Post by themelvin on 2005-04-22
I looked up in the manual and found this:

SCANNING
• Horizontal scanning 	30 - 97 KHz
• Vertical scanning 	50-160 Hz

I'll enter this numbers in the Monitor section but will also change:
Modeline "1024x768_90.00"  100.19  1024 1088 1200 1376  768 769 772 809  -HSync +Vsync

to

Modeline "1024x768_90.00"  100.19  1024 1088 1200 1376  768 769 772 809  **+**HSync +Vsync

I hope that this helps.

Thank you again.

---

