---
title: "dual boot after trying live cd"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by kaporal p. on 2009-03-08
Hello All,

I am using Ubuntu from a live cd. I set it up about 2 weeks ago as dual boot.
When I start the pc with cd in, it offers to choose btwn xp and Ubuntu and with no cd in xp starts automatically, so I think everything is fine with the cd I burned.

Now I would like to install this same set-up for good so I wouldn't need the cd anymore and still keep xp for a while because I'm a newb. Possible? Where do you go from there? I can't find any install options, not even when I boot.

Thanks.

---

### Post by whoop on 2009-03-08
If you run the livecd there should be an icon on the desktop labeled install. Like in the following screenshot:
[http://www.geocities.com/mahyuddin_s/panduan_files/image008.jpg](http://www.geocities.com/mahyuddin_s/panduan_files/image008.jpg)

That will install ubuntu on your hard drive (with dual boot if that is what you want).

---

### Post by kaporal p. on 2009-03-08
There is no such Icon!?

I tried a few things since I got the live cd so maybe I put it somewhere else... could I find it somewhere else if its not on the desktop?

---

### Post by lindsay7 on 2009-03-08
iF Yyou set up a dual boot system, you would not need to start from the cd itself. as you discrib. So something sound strange. If you did install Ubuntu under windows xp or if it is set up as a true dual boot with you hard drive partitions, would not see the install icon on the desktop. This is only there with the live install mode.

---

### Post by kaporal p. on 2009-03-08
When I set-up the live cd, I chose dual boot, that's all I remember. Now, I really do need the cd to get Ubunto going, otherwise, there is no sign of it. Also, if I take the cd out, Ubuntu doesn't work anymore, so I think it's live cd. But then, still no Icon?
I've also never been asked anything about repartitionning.

???

---

### Post by lindsay7 on 2009-03-08
About the only thing that I can think happened is that you did install Ubuntu to your computer either under windows or the dual boot option and somehow the "Grub file" that tells you computer how to start (either windows or Ubuntu) is messed up or missing. This could explain why you get a choice of start options with the cd starting you computer, and why it only starts windows when the cd in not in the drive. In either case (unless you cd is corrupt or bad) the best option would be to uninstall Ubuntu and start fresh.

If you installed under windows you can go to "control Panel" add, remove programs and look for it listed there. If it is there, click on it and uninstall.

If you can try this first, that will at least tell you what the next step would be to fixing this.

---

### Post by kaporal p. on 2009-03-08
Ok! I also think this is the best option! I'll download a new image and start all over. Thanks.

---

### Post by lindsay7 on 2009-03-08
Before you do that, go to the control panel in windows as I suggested and see if the Unbuntu is listed in the add,remove programs menu, and uninstall it if it is there.  I have one other suggestion for you but I think you should look in the control panel because I think Ubuntu is on you computer somewhere and it would be best to find it so that there are no conflicts.

---

### Post by lindsay7 on 2009-03-08
Here is the other suggestion, start windows like normal, put the Ubuntu  disk in the cd drive. click on it or do what ever you would usually do to see the contents of a cd. There should be some options listed. one is install under windows. You will need to be connected to the internet when you do this. If you choose this option Ubuntu will be put on you computer under windows. It will be invisible on you drive except that it will show up as a program like any other windows program. When it finishes installing you should get a dual boout strart up option when you turn you comuter on. You will not have to use the ubuntu disk to start up. 

You may still have a Ubuntu system installed on you system however and it is just taking up space and you can or should remove it if you are happy with ubuntu running under windows. The situation with ubuntu running under windows is that you have to keep window on you machine. A true dual boot would allow for Window to be taken of your maching without disturbing unbuntu.

---

### Post by lindsay7 on 2009-03-08
If you look at you ubuntu disk and you do not see the install under windows option, go to this site and you can download and install,

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by kaporal p. on 2009-03-08
In Ubuntu, when I look at the content of the cd I'm running from, there is a file called _install_, inside this file are 3 other files ; mt86plus, readme.sbm and sbm.bin.

There is no _install under windows_ file

can I do something with these?

---

### Post by lindsay7 on 2009-03-08
Ok, just try the web site I gave you.

---

### Post by lindsay7 on 2009-03-08
Let me know if you get Unbuntu install OK with Wubi.

---

### Post by kaporal p. on 2009-03-14
Installed Wubi

It's perect

thanks

---

