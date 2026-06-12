---
title: "touchpad not working after update on 11.04, Acer aspire 5542g"
date: 2011-04-30
forum: Hardware
---

### Post by branaja on 2011-04-30
hi there!
I had Ubuntu 10.10 and I updated it to 11.04.

Now touchpad isn't working :(

it works well on log in screen and I can click on my username and move it but when I click log in it freezes and can't move mouse using it or click left or right button.

can you please help me?

I'm using Acer aspire 5542g and 64-bit Ubuntu 11.04.

thanks and sorry if thread like this already exists

---

### Post by nems on 2011-05-13
HI!

"SOLVED"? How you solved that issue?

Thanks,
nems

---

### Post by branaja on 2011-05-13
go to terminal, paste this
> gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
and press enter. it should be working but don't use button that disables touchpad (if you have any) !

tell me if it works, and best luck :)

---

### Post by dlogneb on 2011-07-03
Hi,

new to Ubuntu and hoping to install it on my Aspire One D255 netbook.  Running the "test drive" mode of a USB stick and I have absolutely no touchpad control.  I managed to get to the terminal through the keyboard and used gconftool-2 as posted.  No error, but nothing changed. 

Any ideas?  Any help?  Would like to install Ubuntu today, but obivously need to know how to get the trackpad working.

thanks,

Ben

---

### Post by dlogneb on 2011-07-03
ahem.  turned out that the touchpad was disabled through the keyboard.  But still a little strange because I never press that "disable touchpad" key.

In any case, rebooted into windows, mouse didn't work.  Hit fn-f7 and mouse worked, rebooted into Ubuntu -- mouse worked!

mouse=trackpad

---

### Post by hnmohana on 2011-08-22
> **branaja said:**
> go to terminal, paste this

and press enter. it should be working but don't use button that disables touchpad (if you have any) !

tell me if it works, and best luck :)


hey thanx a ton... i had the same problem after running this command it started working....

---

