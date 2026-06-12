---
title: "&quot;Missing resolutions&quot; after installing ati fglrx driver"
date: 2004-11-14
forum: Hardware &amp; Laptops
---

### Post by mausr on 2004-11-14
I installed fglrx driver (thx for wiki & mattyh) and it works fine (glxgears~3000), but I can't use my monitor in 1152*864. (added this resolution to Xfree86-4) (This resolution was ok with the default driver.) I attach my Xfree86-4 file:

---

### Post by claymore on 2004-11-15
I can't really explain why, but I know that I have never been able to get 1152*864 to work in any version of linux with hardware acceleration on my radeon 8500.  Whether that's a limitation of the cards or drivers, I have never heard of a way to get it to work.

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=mausr]I installed fglrx driver (thx for wiki & mattyh) and it works fine (glxgears~3000), but I can't use my monitor in 1152*864. (added this resolution to Xfree86-4) (This resolution was ok with the default driver.) I attach my Xfree86-4 file:[/QUOTE]


Try adding a MODLINE to your monitor section.

Search for the monitor section below: 
```

Section "Monitor"
    Identifier  "IBM G94"
    HorizSync   30 - 95
    VertRefresh 50 - 160
    Option "DPMS"

```

Once you found it take a look right below it and you'll see a nurmerous amount of examples of modlines. 

Let me make an example

```

Section "Monitor"
    Identifier  "IBM G94"
    HorizSync   30 - 95
    VertRefresh 50 - 160
    Option "DPMS"
    Modeline "1152x864@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync

```

That should give you a base line example of what its looking for.

---

### Post by mausr on 2004-11-15
[QUOTE=FLeiXiuS]Try adding a MODLINE to your monitor section.

Once you found it take a look right below it and you'll see a nurmerous amount of examples of modlines. 

Let me make an example

```

Section "Monitor"
    Identifier  "IBM G94"
    HorizSync   30 - 95
    VertRefresh 50 - 160
    Option "DPMS"
    Modeline "1152x864@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync

```

That should give you a base line example of what its looking for.[/QUOTE]

Thanks, good idea! I uncommented the row: Modeline 1152x864@100 (added by fglrx driver) in XF86Config and i can use this resulution again.

---

### Post by MattOnTheNet on 2004-11-16
[QUOTE=mausr]Thanks, good idea! I uncommented the row: Modeline 1152x864@100 (added by fglrx driver) in XF86Config and i can use this resulution again.[/QUOTE]
 I've been following this thread with interest. Could anybody tell me where I can find this "XF86Config-4.txt" document?

---

### Post by mausr on 2004-11-16
[QUOTE=MattOnTheNet]I've been following this thread with interest. Could anybody tell me where I can find this "XF86Config-4.txt" document?[/QUOTE]

You can find here: /etc/X11, but the file hasn't got extension. (Archive it, before you edit.)

---

### Post by HiddenWolf on 2004-11-17
[QUOTE=MattOnTheNet]I've been following this thread with interest. Could anybody tell me where I can find this "XF86Config-4.txt" document?[/QUOTE]
Extentions are so windows. *smile*

txt is notepad. :-)

---

