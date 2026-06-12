---
title: "Laptop monitor 0 brightness after 11.04 upgrade"
date: 2011-08-02
forum: Hardware
---

### Post by dragancla on 2011-08-02
As I said in the title, after upgrading from 10.10 to 11.04 on my Acer Aspire 5336, my laptop monitor dims so bad that even after I turn off the light I still can only see bits of the screen; heh, at first I thought my monitor was completely broken but then I heard the login sound after randomly typing in my password :-)

Anyway, I've tried everything. I can't see enough of the screen to change the brightness from Power Management and the FN+ left/right don't work.

Now for the wierd parts:
-if I log in on a previous kernel, screen works again;
-if I plug in my desktop monitor, it works perfectly;
-I downloaded gDDCcontrol and it tells me "No monitor supporting DDC/CI available. If your graphics card need it, please check all the required kernel modules are loaded."

I will have to bet that my Intel drivers are unsupported in this version? And if so, does anyone know if there are any drivers for my (integrated) graphics card supported in 11.04 or am I doomed to forever log in on a previous kernel?

Thanks for your time :)

---

### Post by dragancla on 2011-08-02
Actually, after a bit more noob testing, I noticed that the laptop brightness is just fine, just that the monitor leds just don't work. If i turn off the light in the room I can't see nothing on the laptop screen, but if I illuminate it with a flashlight I can just about see the upper bar and mouse cursor and such.

Any ideas?

---

### Post by dragancla on 2011-08-03
I'm fairly new to this forum, hope I don't break any rules when i say: BUMP!

---

### Post by dragancla on 2011-08-05
Bump once again!

---

### Post by dragancla on 2011-08-07
And again...

---

### Post by steph2 on 2011-09-08
same thing  11.04 no screen  10.10 just fine  i did use ext monitor and tried to install updates but that didnt help.

Hope someone can help   please  i love unity  on my tower.

still fairly new to linux it works so much better then windows 7.

I did get a few things done but with the help of a few guides, some guidance here would really help.  thanks in advance.

---

### Post by foresthill on 2011-09-08
If you happen to be running a laptop with an Intel® GMA 4500M graphics chip, there are several fixes in this thread:

[http://ubuntuforums.org/showthread.php?t=1741556&page=4](http://ubuntuforums.org/showthread.php?t=1741556&page=4)

Or you can just stick with 10.10, which is what I am currently doing, since there appears to be zero progress by the developers at fixing the problem, since it is still present in the 11.10 beta. :sad:

---

### Post by dragancla on 2011-09-22
Sorry I left this thread unattended for so long :) I'll check the link you gave me tonight as of now I'm not at home, and I'll come back with test results :>

---

### Post by dragancla on 2011-09-24
It worked! :D

And it was retardedly easy as well. Here's what you gotta do!

Open Terminal and type:

**[SIZE=2]lspci | grep VGA[/SIZE] **(VGA has to be in capital letters)

and you should see this:

[SIZE=2]**00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)** [/SIZE]

where [FONT=&quot]00:02.0[/FONT] is the device address of the video card. Replace it with whatever you have in the commands below.

[SIZE=2]**gksu gedit /usr/local/bin/set-brightness**[/SIZE]

and type in, while replacing the 00:02.0 to match yours:
[SIZE=2][B]
#!/bin/sh -e  
setpci -s 00:02.0 F4.B=00  
exit 0 [/B][/SIZE]

Save the file. Now type:

 [SIZE=2]**sudo chmod +x /usr/local/bin/set-brightness**[/SIZE]

and test the script; your screen should be at 100% brightness:
[B]
[SIZE=2]sudo set-brightness[/SIZE][/B]

Now, to run it on boot, type in:

[SIZE=2]**gksu gedit /etc/rc.local **[/SIZE]

Add this line:
[B]
[SIZE=2]/usr/local/bin/set-brightness [/SIZE][/B]

before

[SIZE=2]**exit 0 **
[/SIZE] 
and save the file. Now, to make it set the brightness properly after every suspension or hibernation, run these commands:

[B][SIZE=2]gksu gedit /etc/pm/sleep.d/00_set-brightness [/SIZE]
[/B] 
This should open a file and copy-paste this in there:
[B]
[SIZE=2]#!/bin/sh -e  
case $1 in    
    thaw|resume) /usr/local/bin/set-brightness ;; 
esac  
exit 0 [/SIZE][/B]

Run:
[SIZE=2]
[/SIZE][SIZE=2]**sudo chmod +x /etc/pm/sleep.d/00_set-brightness **[/SIZE]

Now the brightness will be set properly after suspension or hibernation.

There you go :) All this information was taken from:
[http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html](http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html)

Post your comments regarding what errors you've encountered below :)
Cheers!

---

### Post by foresthill on 2011-09-24
Worked for me too, at least the first part. Unfortunately I get a black screen that won't go away without a reboot when I come out of suspend. 

I find that too annoying to deal with, so I'm back to 10.10 for the umpteenth time.

---

