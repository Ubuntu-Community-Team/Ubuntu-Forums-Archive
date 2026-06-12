---
title: "[SOLVED] Laptop help manually setting up xorg.conf"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by oni5115 on 2008-01-07
I have a Dell XPS m170 (Generation 2) that I have set up to dual boot windows XP and Ubuntu 7.10.  I'm trying to setup my xorg,conf file.  I have a KVM switch that I use at home to connect my laptop to my Dell E228WFP monitor.  I'm just trying to clone the output.

I've tried running nvidia-settings, but it tells me to run nvidia-xconfig.  I run that, but it tells me I am not using the nvidia driver.  In my xorg.conf I have my nvidia geforce go 7800 GTX, marked as nvidia (not nv).  Is that why the settings/config do not work? -edit (found out the installation of XGL was causing this to be broken, uninstalling XGL fixed this problem).

I have been doing a lot of reading on how to manually set up twinview on a laptop but I have a few questions.  For the "ConnectedMonitor" option you can select CRT, DFP, or TV.  In my case I have the laptop monitor.  Would that be DFP-0 by default?  I also have my monitor through the KVM switch, which according to the options is CRT (because it's connected through VGA).  So would that be CRT-0?

I'm trying to specify them exactly, because instructions specific to laptops say to make sure you put the external monitor first, and the laptops LCD second.  Then you put the external monitors info under Monitor to get the proper resolutions, modes, etc. and put the laptop LCD's info under the graphics cards "SecondMonitor____" options.  That way the computer will adjust if you do or don't have the extra monitor hooked up.   (If I understand it all right anyway.)

I guess where I am really stuck is trying to figure out if the LCD is indeed DFP-X and if for some reason it is CRT (why not? the external is...) how to tell the difference between the two.  Not really sure at all where to look to figure it out.

Once i know that I can happily blow up my xconfig until I make it work.  :lolflag:

On a side note, I would just use my Fn+8 key combo to make my laptop to my monitor,which works, but I can't seem to 'undo it'.  Pressing the combo again makes both screens go dark, and then it continues pointing to the external monitor.  Pretty much have to shut down and reboot.  So I figured I'd just turn in TwinView in clone mode... and well... it turned into a learn how to manually configure xorg.conf lesson.

-update  have clone mode working now that I can use the nvidia settings.

---

