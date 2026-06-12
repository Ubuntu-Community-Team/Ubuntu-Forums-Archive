---
title: "ali5451 no sound , help please"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by rev.burner on 2007-02-04
I am fairly new to linux and am having some problems with this laptop , its hostile and uncooperative LOL ..I am running 6.10 . I have ali5451 onboard and it is somewhat recognized under device manager and #lspci command but shows no drivers attached to it at all . If i try to open the volume control or alsamixer i get the error no gstreamer plugin or no such device . I have searched the forums up and down and have had to reinstall twice due to destroying grub trying some things found in the forums and have installed alsa project stuff from other posts and still nuthing notta :( .. Any help will be greatly appreciated on this thing just tell me what commands you need me to run and what to post back with , bummin cuz i am at a total loss .. Thanks in advance ...

---

### Post by ivansv on 2007-02-06
installing linux on some laptops with acpi enabled wipes out the sound. reinstall ubuntu and on the boot start page press F6 for boot options. you will see a line at the bottom of the page with a bunch of parameters, just add acpi=off and press enter. proceed with a normal install and when its finished and you rebootinto ubuntu you'll have sound.
my laptop also has the ali5451 sound module, no problems. if you experiment with other linux oss you will have the same problem if you install with acpi enabled.
these laptops come with windows preinstalled the vendors ship them with an acpi setup for windows and that acpi setup corrupts the sound in linux. it can be fixed but the fix is too complicated for most users.

---

### Post by rev.burner on 2007-02-07
Thanks alot that made the sound work when i loaded the disk as if to reinstall :) I really dont wanna reinstall if i dont have to but i can it'll only be the 3rd time LOL i am sure some ppl have reinstalled more then that .. Is there a write up somewhere as to fix it the hard way ? If you know how or if there is i would appreciate at least trying it as if it doesnt work i will reinstall either way whether because i messed something up or it doesnt work ... But thanks for all that so far WAY COOL !!:guitar:

It worked by just adding that acpi=off into the menu.lst using kernel 2.6.19 but not in 2.6.17 so reinstalling it is and hopefully it will take care of it ... Thanks again ..

---

### Post by ivansv on 2007-02-08
you can google acpi and look around,sourceforge.net has some good write ups on the problem. has to do with the DSDT(differentiated system description table) in the bios and the fix sounds too complicated for me. it all stems from the fact that vendors fix acpi for windows and it does't work on linux. perhaps if we bought laptops with linux preinstalled instead of windows.

---

### Post by frumpus on 2008-01-03
I have exactly the same problem as rev.burner - but ivansv's solution of adding "acpi=off" had absolutely no affect on my 4th install.

I may have been supporting Windows since 3.11, but I am new to Ubuntu and most of the techie solutions just don't make sense.  I've attempted several download/compile but all I really get are errors that don't make sense either.

To be honest I don't know for sure WHAT hardware is inside.  The PC was a gift for keeping a different PC alive long enough for them to get a replacement & it had no HD inside upon arrival.

I can't get help from the defunct manufacturer either.  [Anybody heard of KDS?]

What would really help is total NOOB instructions.  A list of required filed and where to download them, a list of commands or executables that will be used (and a way to ensure they exist/function).

---

