---
title: "Screen Refresh Rate"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by sv452 on 2007-02-26
hi all,

i have a small problem - i have a nvidia geforce fx5600 xt and an old 14" Tatung CM14 AR.

i installed the nvidia drivers properly and everything went perfect except now when i get to logon screen everything is pulls skew cause screen refresh rate can't go more than 60Hz... and when i check my xorg.log it says it uses the default 1024x768@75Hz but my screen can't do that - i do see that 1024x768@60Hz is in the list.

my question how do i go about getting it to use 60 and not 75??? somewhere i knew when at login screen u could do a key combination and "+" or "-" and it will cycle thru the choices.

i did try using dpkg-reconfigure xorg and the rest where u tell it what u want but nothing changes in my xorg.conf!! i also tried doing the whole modeline with the modeline generators but that didn't work either. i don't know more info about my screen except it does 60Hz or it totaly goes wonky.

i don't have my xorg.conf since it is on my home pc and i am @ work.

please i need some help since this is going to drive me nuts!!

:confused:

---

### Post by louis_nichols on 2007-02-26
There is an app for adjusting the screen resolution under System>Preferences.

Now, depending on what driver you use, the refresh rate might be reported incorrectly. Info [here]("http://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver#Why_is_the_refresh_rate_not_reported_correctly_by_utilities_that_use_the_XRandR_X_extension_.28e.g..2C_the_GNOME_.22Screen_Resolution_Preferences.22_panel.2C_.60xrandr_-q.60.2C_etc.29.3F"). The nvidia site has this info too, but this is the first site I found googling about it.

---

### Post by sv452 on 2007-02-26
thanx for the swift reply ....

i wouldn't mind using the app in the gui except i can't see nothing - it almost looks like on when u have a scrambled channel where u can't se nothing - so i am really lost regarding what to do ...

:O(

EDIT
i also have a onboard geforce 2 mx ????
and i only have 1 screen ...

EDIT2
Please note i think i posted this in the wrong section of the forum ... can we please move it ... my bad, sorry - :D

---

