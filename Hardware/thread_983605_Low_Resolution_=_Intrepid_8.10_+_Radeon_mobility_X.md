---
title: "Low Resolution = Intrepid 8.10 + Radeon mobility X1600 + 24&quot; LCD"
date: 2008-11-15
forum: Hardware
---

### Post by occhiso on 2008-11-15
Hi,

I recently upgraded from Hardy to Intrepid on my laptop.
In Hardy, I had 1920x1200 working on my 24" LCD. I used to use displayconfig-gtk to set this resolution, but this program is omitted in Intrepid.
I have spent the last 2 weeks or so reading through different threads on these forums trying to get my full resolution again, and can't.

So far, the main things I have tried are:
[LIST]
[*] Downloaded the latest drivers from the ATI/AMD site and used them.
[*] Used the standard Ubuntu "Screen resolution" dialogue.
[*] Used xrandr (following [this]("https://wiki.ubuntu.com/X/Config/Resolution"))
[*] Using [this]("http://ubuntuforums.org/showthread.php?t=974439") thread and added the "proposed" updates repository and updated all my drivers, etc.
[/LIST]

Im running out of ideas, and dont like the idea of "downgrading" back to Hardy, but I am considering just to get this resolution.

Any ideas?

INFO:

```
$> lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
```

```
$> xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1280x720       60.0  
   1024x768       85.0     75.0     72.0     70.0     60.0  
   800x600        85.0     75.0     72.0     70.0     60.0     56.0  
   720x480        60.0  
   640x480        85.0     75.0     72.0     60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  

```

[IMG]http://i81.photobucket.com/albums/j230/occhiso/screendump1.png[/IMG]

[IMG]http://i81.photobucket.com/albums/j230/occhiso/screendump2.png[/IMG]

---

### Post by occhiso on 2008-11-17
Bump

Can anyone help me with this?

---

