---
title: "Setting Wacom CTL460 bamboo pen buttons - help needed."
date: 2010-07-22
forum: Hardware
---

### Post by ravinderw on 2010-07-22
Hello All,

I've just started using Ubuntu and have slowly been getting it to become my primary OS, though I still dual boot with XP.

I have followed the instructions to setup my Wacom CTL460 Bamboo with my Ubuntu 10.04 install. I'm running Kernel 2.6.32.22-generic with GNOME 2.30.0, well that's what system monitor reports.

How can I change the rocker button settings on the pen? I would like to have one position set as ctrl and the second as shift+ctrl+e, if possible. At the moment they give me middle mouse button and right mouse button, which I don't really like.

I've tried searching and not been able to find an answer.

Thanks.

---

### Post by Favux on 2010-07-22
Hi ravinderw,

Welcome to Ubuntu forums!

There are a cpl of ways to do that.  Probably the most flexible way is a xsetwacom start up script.  See the xsetwacom-scripts attached to the bottom of the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Since you have the Pen remove all sections but the stylus one.  Then you can experiment with the xsetwacom commands in a terminal.  Not sure the stylus buttons will do that.  If you had tablet buttons (the pad) you could do that for sure.  But you can pattern after the pad commands in the script and try.

Hope this helps.

---

### Post by ravinderw on 2010-07-22
Hello All and Favux,

Thanks to Favux advice, I have managed to get the buttons on my Wacom  CTL-460 working the way that I wanted to.

For the sake of completeness and if anyone stumbles onto this thread,  I'll note what I did. I apologise if this is at too basic a level, but  I'm a real newbie with Ubuntu and Linux as a whole.

I went to Favux's post  [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1) and  downloaded the Favux_Sample_Bamboo-P&T_xsetwacom-scripts.tar.gz file  as suggested.

Double clicking the file mounted the archive into nautilus.

I dragged the Favux_wacom.conf-.xsetwacom.sh to my desktop.

I then went to a terminal and typed xinput --list and got the id for my  stylus. In my case it was 10.

So I changed the contents of the Favux_wacom.conf-.xsetwacom.sh to

xsetwacom set 10 Button2 "key ctrl"  # the default is right mouse click
xsetwacom set 10 Button3 "key 2"  # the default is middle mouse click

This sets the rocker to the ctrl key in the forward position and the  number 2 key in the back position. I couldn't work out how to set it to  SHIFT+CTRL+E, as that would all me to fit the image to window in GIMP,  so what I did is change the GIMP keyboard shortcut to 2.

Then following Favux's advice, I saved it as .xsetwacom.sh to my home  directory. I right clicked on the file and in Properties, in the  Permission tab, check Execute as program. Then went to  System->Preferences->Startup Applications and click on add and for  the command wrote sh /home/home/.xsetwacom.sh 

I have to say that Favux_wacom.conf-.xsetwacom.sh script is quite  complex and probably does a lot of really nice things. However, at the  moment my CTL460 seems to be working way I want and I only want to  control the button functionality.

I hope this is not too basic for the forum.

Many thanks to Favux!

---

### Post by ravinderw on 2010-07-22
Just a quick follow up.

I unplugged the Wacom tablet and then plugged it into a different usb port, I found that the buttons reverted back to the defaults.

I found that the plugging into the different usb port changes the id number of the Wacom tablet. I had to update the script with the new id number and all worked again.

---

### Post by Favux on 2010-07-22
Hi ravinderw,

I'm glad you got things working.  If you are hot plugging the tablet to different ports probably the best thing is to use the "Device names" with the quotes.  That way you'll avoid the changing ID numbers.

---

