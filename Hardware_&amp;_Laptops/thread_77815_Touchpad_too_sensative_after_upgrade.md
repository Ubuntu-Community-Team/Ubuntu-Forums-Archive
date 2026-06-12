---
title: "Touchpad too sensative after upgrade"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by bquark on 2005-10-17
I have a Dell Inspiron 6000 which I just upgraded to Breezy. The touchpad has become ultrasensative. If I cross a link in a webpage as I am moving the cursor, the link opens as if I clicked on it. It is quite annoying. I have a similar experience with navigating around menus. I get menu items clicked when I did not intend to. I had not such problems in Hoary.  

I have searched for mouse configuration options and none seems appropriate. 

Mike

---

### Post by John.Michael.Kane on 2005-10-17
type this in terminal
```
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"
```


For any other issues please search the forum before posting, as most issues have been answered..

hope the code above helps, and welcome to ubuntu..

---

### Post by bquark on 2005-10-17
[QUOTE=SD-Plissken]type this in terminal
```
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"
```


For any other issues please search the forum before posting, as most issues have been answered..

hope the code above helps, and welcome to ubuntu..[/QUOTE]

I did search for a fix before posting, and I even found the fix you suggested, except it said it was a fix for drag and drop which was not what I was looking for. Since it did not explain what the fix did, I did not see that it was relevant.

After seeing your reply, I studied the whole thread in some detail and decided it might be the right thing to do, so I tried it. It did work. Thank you. I am still left wondering what that option means.

The scroll bars on my touchpad still do not work which I think is great. They drive me nuts in Windows. If the driver improves I will have to learn how to turn off the scroll bars. ;)

---

### Post by GoodPanos on 2005-10-17
So this *sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"* command, fixes only the *drag and drop* and the *Sensitivity* problems?

---

### Post by John.Michael.Kane on 2005-10-17
I beleave it fixes only the drag and drop and the Sensitivity problems. the other issues might be fixed with the release of drake. sorry..

---

### Post by andrewski on 2006-04-09
1. Specific settings for your touchpad in your xorg.conf could contribute to the sensitivity; if you have any therein, can you reproduce the sensitivity if you take those out?
2. Also, what about turning down the Sensitivity in the Mouse preferences?  That should help if you haven't tried it already.  Kinda a superficial fix, but it's worth mentioning. :P
3. If it suits you, you can [turn off tap-to-click]("http://ubuntuforums.org/showpost.php?p=889122&postcount=2").  This is the first thing I do with my touchpad. :)  Although, I'm assuming this is not suitable for you.

BTW, this has been reported on Launchpad: [https://launchpad.net/distros/ubuntu...ics/+bug/33788]("https://launchpad.net/distros/ubuntu/+source/xorg-driver-synaptics/+bug/33788").
(The other issues have been too; you can search for them.)

For what it's worth, the synaptics driver has gotten a lot of attention for Dapper. For example, the side scrolling works by default. If you're up for upgrading to Dapper, we would love your feedback for how it works thereon.  I think it works much better.

---

### Post by starfire1983 on 2006-04-09
If you want to turn it off by following this guide - [http://www.ubuntuforums.org/showthread.php?t=143095](http://www.ubuntuforums.org/showthread.php?t=143095)

I found an alternative to using the python script though (however it is quite handy). You can install qsynaptics after adding the SHMConfig line, shown in the above link, to your xorg.conf and disable it through that applet. Don't have to muck with xbindkeys or metacity (preferred method if using the script).

---

