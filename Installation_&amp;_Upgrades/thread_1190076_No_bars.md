---
title: "No bars??????"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Chivas619 on 2009-06-17
Ok well sorry if i sound like a noob for asking this well i just installed ubuntu netbook remix on my eee pc 701
It was working ok until i updated using the update managaer and it went completly through and i restarted and when i restarted it there was no bars on top or bottom all i could see was the wallpaper
Plz help what should i do?

---

### Post by Idefix82 on 2009-06-17
What happens if you hit Alt+F2 and type in
```
gnome-panel
```

---

### Post by Chivas619 on 2009-06-17
> **Idefix82 said:**
> What happens if you hit Alt+F2 and type in
```
gnome-panel
```

Nothing it doesnt bring nothing up so i cant type it in

---

### Post by Therion on 2009-06-17
Try **CTRL**+Alt+F2

---

### Post by Chivas619 on 2009-06-17
Ok now it says login then password what do i do

---

### Post by Idefix82 on 2009-06-17
Then press Alt+Ctrl+F2, login with your usual username and password and type in
```
sudo apt-get install --reinstall gnome-panel
```
then type in your password when prompted. This will reinstall the panels and hopefully fix your problems. If everything goes through without errors then restart by typing
```
sudo shutdown -r now
```

---

### Post by Chivas619 on 2009-06-17
Ok i did allthat n i restarted n nothing showed upsamething

---

### Post by izizzle on 2009-06-17
Now try typing in ```
gnome-panel
``` again.

---

### Post by Therion on 2009-06-17
> **Chivas619 said:**
> Ok i did allthat n i restarted n nothing showed upsamething
You're getting a little ahead of us...

Ctrl+Alt+F2
Login using your username and password.
Type in **gnome-panel**
Type in Ctrl+Alt+F7

Hopefully now you'll see your panels.  If not things are going to get icky.

---

### Post by Chivas619 on 2009-06-17
> **izizzle said:**
> Now try typing in ```
gnome-panel
``` again.

Ok i did that n it said to run the help for all list commands

---

### Post by Therion on 2009-06-17
Try using **killall gnome-panel** instead.

---

### Post by Chivas619 on 2009-06-17
> **Therion said:**
> You're getting a little ahead of us...

Ctrl+Alt+F2
Login using your username and password.
Type in **gnome-panel**
Type in Ctrl+Alt+F7

Hopefully now you'll see your panels.  If not things are going to get icky.


Still nothing :(

---

### Post by Chivas619 on 2009-06-17
> **Therion said:**
> Try using **killall gnome-panel** instead.

Nothing for this one either

---

### Post by Chivas619 on 2009-06-17
well if anything doesnt work than i will reinstall ubuntu notebook remix 9.04 
but i need to know what i need to update to get flash player on firefox?

---

### Post by Therion on 2009-06-17
> **Chivas619 said:**
> ... i need to know what i need to update to get flash player on firefox?
Not an update, just open a Terminal and paste in:
```
sudo apt-get install flashplugin-nonfree flashplayer-nonfree
```

---

### Post by Chivas619 on 2009-06-17
> **Therion said:**
> Not an update, just open a Terminal and paste in:
```
sudo apt-get install flashplugin-nonfree flashplayer-nonfree
```
ok kool thanks alot for ur help i kno it didnt help but i apricieate that u tried to help me

---

### Post by raymondh on 2009-06-17
> **Chivas619 said:**
> ok kool thanks alot for ur help i kno it didnt help but i apricieate that u tried to help me

and should you decide, also install

```
sudo apt-get install ubuntu-restricted-extras
```

which will load the necessary codecs to play media files that require restricted, non-free formats.

That is if you don't have them yet :)

Good luck.

---

### Post by Chivas619 on 2009-06-17
thanks

---

### Post by Therion on 2009-06-17
> **Chivas619 said:**
> ok kool thanks alot for ur help i kno it didnt help but i apricieate that u tried to help me
If if makes you feel any better I had the same problem just the other day (running Karmic Alpha-2) and had to reinstall.  
But then I reinstall about as often as most people change their socks.

---

### Post by Chivas619 on 2009-06-17
realy wow that sucks yea this is the third time for me so i gues we the same o well im just using it for the internet

---

### Post by GeorgeVita on 2009-06-17
Hi,

> **GeorgeVita said:**
> Just in case you miss the panels again...
1. right click on background
2. click on **create launcher**
3. type **xterm** to name
4. type **xterm** to command
5. click **ok**
6. double click on xterm (icon created above)
7. type **desktop-switcher** and press enter
8. choose **Ubuntu Netbook Desktop** and **Apply**

The above creates a shortcut to have access to a terminal window and then run the switcher from terminal.


Regards,
George

---

### Post by Punk Fetish on 2009-06-17
It is also possible that the panels are still there and you do not see them.

your screen config could have screwed up and now you dont see the top and lower halves of the screen in your monitor?

or perhaps you used the arrows at the sides and they are only hidden.

just a thought

Regards

---

### Post by bostonaholic on 2009-07-20
> **Idefix82 said:**
> Then press Alt+Ctrl+F2, login with your usual username and password and type in
```
sudo apt-get install --reinstall gnome-panel
```
then type in your password when prompted. This will reinstall the panels and hopefully fix your problems. If everything goes through without errors then restart by typing
```
sudo shutdown -r now
```

I had the same issue as the OP and this method fixed it for me.  Hardy 8.04.3 64-bit

I did notice however that 'gnome-panel' was not installed... when typing 'gnome-panel' nothing would happen.  I did notice in the repos that there is 'gnome-panel' and 'gnome-panel2'.  I just did

```
sudo apt-get install gnome-panel
```

After the reboot and logged in, I got some error messages about the trash-applet.  Everything but the "trash" seems to be working fine again.

---

### Post by drfox on 2009-07-22
Here's what you need to do to get your panels back:
Get a terminal session, either by logging on to a terminal session or by pressing Alt-F2 from your desktop and then typing "xterm"

Remove these folders:
.gconfd
.gconf
.gnome2
.gnome2_private
.config

by using the command: rm -r foldername

Once they are removed, reboot using the command: sudo shutdown -r now

Your panels will be back. 

HTH  Larry

---

### Post by goofy2909 on 2009-09-15
> **drfox said:**
> Here's what you need to do to get your panels back:
... 

HTH  Larry

 thanks a lot - you saved my day :) 
 works perfectly

---

