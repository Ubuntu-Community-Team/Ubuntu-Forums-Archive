---
title: "Upgrade from 8.10 to 9.04 caused  Crash"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Plasma_Snake on 2009-07-16
I recently upgraded from 8.10 to 9.04 on both of my machines, a Dell Studio 1555 and my Desktop. While on the laptop is smoothed out the rough edges of 8.10, on desktop it made the situation from bad to worse.
Earlier my Display was not being detected nor were the Ati drivers properly worked, even the restricted ones gave me a blank screen. I upgraded today from 8.10 and after the restart, when the login window is supposed to display, I get a garbled screen, the text is not garbled, the whole screen is garbled. Will post its pic soon.
I tried repairing the X-Server but of no use. My screen is a Samsung LCD TV and video input to it is provided by my HD4850. Any idea as to why is this happening?

---

### Post by dstew on 2009-07-16
Try booting in Recovery Mode and doing```
sudo apt-get remove xorg-driver-fglrx
```Maybe that will get you a working display, without any acceleration. Then upgrade Jaunty, and hopefully later kernels or drivers will work better.

---

### Post by Plasma_Snake on 2009-07-16
Take a look a the screenshot. The other thing I also noticed was that when this happens, the keyboard also goes unresponsive, no lights r lit, no keys work, the only way to escape is the manually switch off the system but shutting down the power.
[[IMG]http://img17.imageshack.us/img17/8408/17072009.th.jpg[/IMG]](http://img17.imageshack.us/i/17072009.jpg/)

---

### Post by Plasma_Snake on 2009-07-17
> **dstew said:**
> Try booting in Recovery Mode and doing```
sudo apt-get remove xorg-driver-fglrx
```Maybe that will get you a working display, without any acceleration. Then upgrade Jaunty, and hopefully later kernels or drivers will work better.
Umm where to write this command in Recovery mode? There are following entries there:

[LIST=1]
[*]resume  Resume normal boot
[*]clean  Try to make free space
[*]dpkg  Repair broken packages
[*]fsck File system check
[*]grub Update Grub bootloader
[*]netroot Drop to root shell prompt with networking
[*]root Drop to root shell prompt
[*]xfix Try to auto repair graphic problems
[/LIST]
I've tried option no. 3 6 and 7 and none works. Infact when I select 6 or 7, it says press Control-D to continue and when I do so it takes me back to the Recovery Menu.
The other problem that has popped now is with the laptop. Its Dell Studio 1555 and after the Jaunty update, none of the listed drivers produce sound output. Some even give errors.
Following r listed;
For Sound Playback of Sound Events,Movies and Music and Audio Confrencing-

[LIST=1]
[*]AutoDetect
[*]HDA Intel STAC92xx Analog (ALSA)
[*]HDA ATI HDMI ATI HDMI (ALSA)
[*]HDA Intel STAC92xx Analog (OSS)
[*]HDA Intel STAC92xx Analog (OSS)        These r double enteries existing by default, I messed wwith nothing here.
[*]ALSA- Advanced Linux Sound Architecture
[*]OSS- Open Sound System
[*]Pulse Audio Sound Service
[/LIST]
Out of these the 2nd and the 7th entry gives following error when selected and tested.
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

Can u also please tell me how to take screenshots in Ubuntu as PrntScrn key doesn't works and using Gimp leads to removal of focus from intended app thus disvowing the whole aim of taking the screenshot ?

[LEFT]
[/LEFT]

---

### Post by irv on 2009-07-17
I had the same problem awhile back. Here is what I did to make it work.
I ran:
```
apt-get remove xorg-driver-fglrx 
```

Rebooted and "WALA" I was back running in Ubuntu 9.04. Now to check it out and make sure everything else is working.

---

### Post by Plasma_Snake on 2009-07-17
What I'm asking is to where actually run this command in Recovery menu?

---

### Post by dstew on 2009-07-17
I think it's choice 6, root with networking. You enter it on a command line that should appear after you make that choice.

---

### Post by Plasma_Snake on 2009-07-18
OK, I ran that command and it did the trick. Now by default the max. res. that my screen supports(1360x768 ) is shown there but when I select it, the screen shifts to left. I can't manually adjust it as its an LCD TV and there is no option to do so, what can I do? I know installing ATi drivers do give the option to adjust screen but in this case since I've no drivers installed either so what to do besides installing the drivers and adjusting the res. from there? Moreover how to install those drivers?

---

### Post by irv on 2009-07-18
I take it you are using this for your main monitor? Is there an adjustment setting on the LCD TV it's self to move the display to the right or left? 
Under System>Administration>Device Driver is there a place where you can see your video driver? This is a place to start.

---

### Post by irv on 2009-07-18
One other thing you might try: There is a small book in PDF format on Ubuntu. Here is the link: [http://www.ubuntupocketguide.com/download_main.html]("http://www.ubuntupocketguide.com/download_main.html")
Download it and go to the section on Monitors and Graphics. Maybe something there you can try.

---

### Post by Plasma_Snake on 2009-07-18
While trying to install Skype, mentioned at this this [site]("http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/"), I messed up the repositories and package manager. How can I repair it or revert the changes?

---

### Post by irv on 2009-07-18
> **Plasma_Snake said:**
> While trying to install Skype, mentioned at this this [site]("http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/"), I messed up the repositories and package manager. How can I repair it or revert the changes?

Maybe you should start a new thread and explain exactly what you did. I am sure someone will help you out with this one.

---

