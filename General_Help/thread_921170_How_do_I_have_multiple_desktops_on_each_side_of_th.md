---
title: "How do I have multiple desktops on each side of the cube?"
date: 2008-09-16
forum: General Help
---

### Post by nuroxs on 2008-09-16
I want to have a different wallpaper for each side of my cube and also have different icons on each side. How do I do that? Is it possible?

---

### Post by yogen on 2008-09-16
> **nuroxs said:**
> I want to have a different wallpaper for each side of my cube and also have different icons on each side. How do I do that? Is it possible?
may be this will help you...for this you need compiz fusion v0.7.6...

[http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/](http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/)

---

### Post by el-mar01 on 2008-09-16
You can't have different Icons on each side of the cube .. only 1 set .. also by activating the wallpaper plugin and disabling Nautilus drawing the desktop you lose the ability to have icons on your desktop.

---

### Post by saggitheman on 2008-11-29
1. Go under System> Preferences > Advanced Desktop Settings
   2. Select Desktop Cube >Appearance > Background images
   3. Desktop Cube
   4. Click New under background images and add all the images you want as background.(Ubuntu Hardy Heron)
   5. Select backround on compiz settings manager (Intrepid Ibex)
   6. Alt + F2 to launch the Run Terminal.
   7. Enter gconf-editor and hit Run.
   8. gconf-editor
   9. Go under apps > nautilus > preference
  10. Nautilus
  11. Deselect ‘Show Desktop’.

Note:
You will notice that you can’t right-click on the desktop.

---

### Post by nmayorga on 2008-12-06
Hi!

I've got compiz fusion installed on an ubunto 8.10 and a couple of problems:

[LIST=1]
[*]I can't name the different desktops (I just can add or remove desktops, but not naming them. They do not even show a generic name like "Desktop 1")
[*]I can't right-click on desktop. I think I've messed it all up with Nautilus and gconf-editor trying to fix the previous issue. What I have now is an icon-less desktop and I can't right-click on it
[/LIST]

I'd appreciate any help.

Thanks in advance,

                      Nacho

---

### Post by ellalan on 2008-12-06
> **nuroxs said:**
> I want to have a different wallpaper for each side of my cube and also have different icons on each side. How do I do that? Is it possible?

In ccsm enable wallpaper plugin.HTH.

---

### Post by eternalnewbee on 2008-12-06
> How do I have multiple desktops on each side of the cube?
You mean "multiple backgrounds";)
Each side only has one desktop.

---

### Post by nmayorga on 2008-12-06
Hullo again,

Maybe this is already known and I'm going to look pretty nerdy but I've restarted the computer and now I can, at least, righ-click on the desktop.

Nevertheless, I've remembered two things: on the one hand, Kubuntu (hardy heron on my laptop) allowed multiple-desktop naming. On the other hand, during a very short period, I managed to do it on this intrepid ibex installation. Can't remember, though, when it went away.

So I still need some help.

Thanks in advance,

                   Nacho

---

### Post by wolke on 2008-12-15
ok, in summary:
nautilus does not support multiple desktop backgrounds, and nautilus cant draw icons on a transparent bg.
so compiz can provide you with multiple bgs, but nautilus cant put your icons or right-clickiness in on top of it. gnome folks are attempting to fix this bug, but it didnt happen yet...

if you turn off show desktop [ ], you lose your icons. if you turn on show desktop, you will lose your multiple bgs.

i made a perl script for toggling icons and multiple bgs live, in case someone finds Desktop icons and multiple bgs useful at different times. 

set up the wallpaper plugin in compiz appropriately, and the toggle will switch between them cleanly. attach a kb binding, and you have something nice, maybe?


desktopIcons [on|off|toggle]

```

#!/usr/bin/perl
use strict;
use warnings;

my $attribute = '/apps/nautilus/preferences/show_desktop';
my $onVal = 'true';
my $offVal = 'false';
my $type = 'boolean';

my $arg = lc shift;

my $val;
if($arg eq 'on'){
  $val = $onVal;
}elsif($arg eq 'off'){
  $val = $offVal;
}elsif($arg eq 'toggle'){
  my $curVal = `gconftool-2 --get $attribute`;
  chomp $curVal;
  if($curVal eq $offVal){
    $val = $onVal;
  }else{
    $val = $offVal;
  }
}else{
  die "Usage: $0 on|off|toggle\n";
}

print `gconftool-2 --set $attribute --type $type "$val"`;
exec 'nautilus -n &';


```

---

