---
title: "Updates"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by jwh400 on 2006-01-26
I am new to Ubuntu and Linux in general but the installation went well and I've been using Breezey Badger for several days without a problem. I decided to download and install the updates that were noted in the system tray and after rebooting I'm getting a screen I wasn't before. This is on a Toshiba laptop and the screen begins with;

[COLOR="DarkRed"]Ubuntu 5.10 "Breezy Badger" Toshiba tty1[/COLOR]

[COLOR="DarkRed"]Toshiba login:[/COLOR]

 After entering my username and password it goes on to text about the system being free and where the individual files are stored.

[COLOR="DarkRed"]Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.[/COLOR]

The next part is where I'm stuck. 

[COLOR="DarkRed"]"username"@Toshiba:~$[/COLOR]

It's waiting for a command to the right of the $ but I don't know what to enter. Thanks for any help you can offer.

---

### Post by kaamos on 2006-01-26
This should open the login manager
```
sudo /etc/init.d/gdm restart
```
But it should be up and running already, so something might be wrong with your config. You could try this to reconfigure:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now try the first command again. If you are still out of luck, try
```
sudo dpkg-reconfigure xserver-xorg
```
to configure you graphic settings.

Hope this helps!

---

### Post by Ocxic on 2006-01-26
befor you do what kaamos said just try:  startx
at the prompt you get to see if it will start, that will tell you if something is wrong with x right away.

---

### Post by jwh400 on 2006-01-26
Thanks for the quick replies. startx did the trick although I didn't see your reply until I tried kaamos' tips. Those didn't work for me kaamos but at least I know the video card is configured properly now;) . Was there an update that has added this for each time you boot or was this just one of those oddities that happen?
Thanks again.:p

---

### Post by mishranurag on 2006-01-26
The exact same thing happened to me few days back too. I went ahead and installed KUBUNTU over it, and I can see the KUBUNTU login screen now. I still work in GNome but have lot of KDE crap installed, which I am scared to remove.

Anurag

---

