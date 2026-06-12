---
title: "Screen Resolution Problem"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by tctor on 2007-09-06
Hi all.

I am a new user to ubuntu. Its my first time trying out the OS. And have been using it for a week. 
I am blown away by its UI which is far better than windows. 

However, i have a small problem. My laptop (Sony Vaio) has a wide screen (6:19). But ubuntu only display 1024x768 (4:3). 

What should i do to fully utilize the whole screen?
Hope you guys can help me out.

Thanks  
A Proud Ubuntu User.

---

### Post by w4ett on 2007-09-07
You can normally select additional resolutions by reconfiguring your xorg.conf file.  From the terminal:

CODE]sudo dpkg-reconfigure -phigh xserver-xorg[/CODE]

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select your correct video driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.  Then use System >Preferences>Screen Resolution to select your desired resolution and refresh rates.

If you machine uses the Intel video chipset, you will probably need to use the 915 Resolution tweak to obtain the widescreen resolutions:

[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

Good Luck

---

### Post by tctor on 2007-09-07
Thank you very much!!!! You have been a big help!!!
I will try it out tonight!!!!

Thanks !!!

---

