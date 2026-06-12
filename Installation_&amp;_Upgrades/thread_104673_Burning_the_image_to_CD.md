---
title: "Burning the image to CD"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by StubornAH on 2005-12-16
Can I ask for help about Nero here?  It was my first time burning an image and I did it as data.  What is worse is I asked Nero SmartStart to create a bootable disk for me so that I could do the install.  I later found this website and read that I need to burn it as an image not as data.  However, I have a problem other than the fact that the install did not work.

The problem is that I booted off the Nero disk and was trying to install Ubuntu.  Well I guess I did something wrong and I got a new boot loader.  It appears to be German and I can't read it.  It also has taken over my system.  It appears when I turn the computer on and when I come out of hibernation.  I have tried pushing buttons as well as searching the BIOS but I can't get rid of it.  Can anyone help?  Thanks.

As for installing Ubuntu, my CD burner has a minimum of 8x and I guess you have to burn it at 1x for whatever stupid reason, so I just ordered the disks from shipit.  When installing now it always errors in the "Install Base" part.  Oh well, guess I will use a different distribution until the CD's arrive.

Thanks for the help.

Edit:  I suppose I should tell you that I am currently using WinXP Pro.  That just might be important :)

---

### Post by CaptainMorgan on 2005-12-16
I can't be of much help, but you got me wondering why exactly you have to burn at 1x. Is that for you personally? Or is this something I haven't yet... ?


good luck

---

### Post by aysiu on 2005-12-16
[QUOTE=StubornAH]Can I ask for help about Nero here?  It was my first time burning an image and I did it as data.  What is worse is I asked Nero SmartStart to create a bootable disk for me so that I could do the install.  I later found this website and read that I need to burn it as an image not as data.  However, I have a problem other than the fact that the install did not work.[/quote] This is what you're looking for:
[http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)

> 
The problem is that I booted off the Nero disk and was trying to install Ubuntu.  Well I guess I did something wrong and I got a new boot loader.  It appears to be German and I can't read it.  It also has taken over my system.  It appears when I turn the computer on and when I come out of hibernation.  I have tried pushing buttons as well as searching the BIOS but I can't get rid of it.  Can anyone help?  Thanks. That's weird. If you burned the ISO as data, it shouldn't have done anything when you booted to it. It shouldn't have booted at all.

> 
As for installing Ubuntu, my CD burner has a minimum of 8x and I guess you have to burn it at 1x for whatever stupid reason, so I just ordered the disks from shipit.  When installing now it always errors in the "Install Base" part.  Oh well, guess I will use a different distribution until the CD's arrive. 8x should be fine. The problem is that (for some strange reason) Ubuntu ISOs are delicate and corrupt easily (in my experience this is a uniquely Ubuntu phenomenon--I've never found my Mepis, Mandriva, SuSE, Damn Small or other Linux disks corrupted during download or burn). Burning at a slower speed makes it more likely that the ISO didn't get corrupted during the burn. 8x is fine. Just don't burn it at 48x or above.

As for your boot loader... do you have a Windows CD? There's a Windows utility called fixmbr.

---

### Post by StubornAH on 2005-12-16
I just downloaded Debian, burned it and got the same problem.  As for the boot from Nero, I created a bootable disk and put the Ubuntu image on it, that is why it booted.  I downloaded and burned Ubuntu twice and Debian once.  I got the 1x idea from a post on this forum about someone having this problem and it was said they had to burn at 1x.  I will look for my Windows CD.  Thanks for the help.

---

