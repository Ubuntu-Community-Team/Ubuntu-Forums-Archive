---
title: "Acer Travelmate C110"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by andrewsawyer on 2005-08-26
Hi all,

I have been using Ubuntu as my primary OS, and it is the only one installed on my laptop - I got rid of Windows a good while ago - yeah!!!

However, I am having some problems with laptop/tablet pc specific issues and I am hoping someone might be able to help.

I have an Acer Travelmate C110 Tablet PC, however I can't get the touchscreen to work.  Nor can I get the soft-keys around the screen or the ones above the F-keys to work.

I have found [This url](http://hardware.mcse.ms/archive57-2005-4-178945.html) so I can only assume it is all possible, but it just seems beyond me.  Has anyone else had these problems, and managed to fix them, or does anyone know of a good tutorial I might be able to take a look at?

Oh, finally with reference to the second post on that link, I have tried:

/etc/init.d/setkeycodes with contents:
#scroll up
setkeycodes 68 103
#scroll down
setkeycodes 69 108
#enter (dot)
setkeycodes 67 28

then doing "update-rc.d setkeycodes start 99 5 ."

however it doesn't seem to do anything.  Should I be doing something after this?

Any suggestions or advise would of course be very much appreciated.

---

