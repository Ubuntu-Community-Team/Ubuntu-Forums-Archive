---
title: "screen resolution"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by jvanoort05 on 2007-04-30
i have a laptop with a resolution of 1400*1050 and the Screen and Resolution Preferences manager will only let me choose 640*480, 800*600, or 1024*768. how do i change this to my screen resolotion because i have some wasted screen space that i need.

---

### Post by tanguyr on 2007-04-30
Hello,

Have you tried [this page from the wiki]("https://help.ubuntu.com/community/FixVideoResolutionHowto")?

/t

---

### Post by veloce on 2007-04-30
> **jvanoort05 said:**
> i have a laptop with a resolution of 1400*1050 and the Screen and Resolution Preferences manager will only let me choose 640*480, 800*600, or 1024*768. how do i change this to my screen resolotion because i have some wasted screen space that i need.

IF your video card is an intel (as mine is) then you need the utility "915resolution" - use your favourite package manager to install.  It installs in auto mode which works most of the time.  If it doesn't then you need to edit  it's defaults file.

---

### Post by jvanoort05 on 2007-05-05
I found out that reconfiguring the xserver with this command works.

 sudo dpkg-reconfigure xserver-xorg

if you use this command you get a screen that sets up the xserver. just go through these pages untill you get
 one on the screen resolution. just check off the one /s you need by pressing the space bar and then press enter. you will get a few more pages on refresh rate and just use the default value. then you will be asked if you want to write the settings to the hard drive. press yes if you want to save the settings. now reboot and your screen resolution should be back to normal.

---

### Post by quickwitt on 2007-05-05
> **jvanoort05 said:**
> I found out that reconfiguring the xserver with this command works.

 sudo dpkg-reconfigure xserver-xorg

if you use this command you get a screen that sets up the xserver. just go through these pages untill you get
 one on the screen resolution. just check off the one /s you need by pressing the space bar and then press enter. you will get a few more pages on refresh rate and just use the default value. then you will be asked if you want to write the settings to the hard drive. press yes if you want to save the settings. now reboot and your screen resolution should be back to normal.

I would be cautious using this method to configure X. If you don't know the exact specs of your hardware you can do more harm than good. What is your video card/chipset? That is the best place to start when asking a question.

---

