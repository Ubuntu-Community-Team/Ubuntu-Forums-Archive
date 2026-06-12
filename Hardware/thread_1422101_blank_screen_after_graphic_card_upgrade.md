---
title: "blank screen after graphic card upgrade"
date: 2010-03-05
forum: Hardware
---

### Post by thegitksan on 2010-03-05
Good evening all. My trusty old ATI Radeon 9800 AGP 256 MB graphics card just bit the dust, and so I bought a replacement - an ATI Radeon 3650 AGP 512 Mb card. It is what is available for my:

Dell Dimension 8300
3GHz speed
4Gb RAM
Dual boot: WinXP & Hardy 8.04.3 LTS

I had problems getting the drivers properly installed for WinXP, eventually got it with a Hotfix from ATI/Sapphire. And now when I boot into Ubuntu, after some text messages, the screen goes blank and stays that way. I think very likely the drivers for the new card need to be installed and the old drivers uninstalled, but I don't know for sure.

I can get command line text mode to come onscreen, but nothing GUI. I had no choice in my order - ordinarily, I'd have uninstalled anything to do with the old card before installing the new one. However, the old card is kaput.

Any ideas for an approach for me?
---------------------------------------
Updated information:

I tried putting the LiveCD into the boot drive (8.04.1) to see if it would work, and it seems to work fine. I wonder if simply re-installing over top of the existing OS might work. I don't have anything important on the partition that I can remember. Alternatively, perhaps if I went for an upgraded version, that might also do the trick?

Does anyone know? I am wondering if reinstalling or upgrading might get the OS to recognize the new graphics card. Ideally, it would be done without losing everything I have on the partition right now, but I'd toss it if I had to.

Another thought - is there a utility that can help my OS figure it out on its own?

---

### Post by thegitksan on 2010-03-05
bump!
Hoping someone will read this request and reply back to me.
Tx, Russell

---

### Post by thegitksan on 2010-03-06
~bump~
Best regards,
Russell

---

### Post by thegitksan on 2010-03-06
~bump
Still trying to get a reply from somone for my problem.

---

### Post by agnes on 2010-03-06
See what I replied at [http://ubuntuforums.org/showthread.php?t=1422641]("http://ubuntuforums.org/showthread.php?t=1422641")

---

### Post by thegitksan on 2010-03-06
Okay, Agnes, that worked. My thanks to you for your keen eye. Here is exactly how it worked for me.

I used your "sudo apt-get ... etc" command, after booting into recovery mode and choosing to go to the command line. That worked very quickly, but gave no indication if my problem was gone or not.

Next, I did Ctrl-D to get back to the menu of choices. I chose to fix X Server, and it seemed to flicker quickly on the screen. And then I chose to boot normally, and after some more flickering, it all came back like normal.

Thank you. That was quick, painless, and very effective. My compliments to you.

Russell

---

### Post by agnes on 2010-03-08
Sorry, I read too fast and thought you already had tried to install the new driver in Ubuntu, and then came the blank screen. Glad the thread did work out for you anyway.

---

