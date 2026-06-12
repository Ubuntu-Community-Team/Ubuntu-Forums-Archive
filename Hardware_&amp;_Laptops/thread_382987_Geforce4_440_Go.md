---
title: "Geforce4 440 Go"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by masterwont0n on 2007-03-12
Hey. I am new to Ubuntu. I just installed it (Edgy by the way) on my Dell Latitude C840 (duel booting XP) I have been trying to install accelerated nvidia drivers to get beryl to work but i keep getting problems. I have looked all over the internet and it seems like everyone that has the Geforce4 440 Go is having trouble with the drivers. Is there anybody out there that has gotten the 3d drivers and Beryl to work with this graphics card? if so could you tell me how you did it. I have tried every tutorial i have found on the internet. Any help would be greatly appreciated. Thanks.

---

### Post by Dr. Feltersnatch on 2007-03-13
Can you describe what kind of problems? I have an inspiron 8200 with the same video card and have gotten beryl to work successfully.

Check this out as well:
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by masterwont0n on 2007-03-13
Its my understanding (tell me if i am wrong, like i said i am new to linux) that i need to install an accelerated driver (the nivida, not the nv driver) i have tried many different ways to install it including Envy. when i do it with envy i get a black screen when ubuntu starts. i tried manually a couple different ways but most of the time i get an error on boot up that says the X server can not start. Once i got it to successfully install the nvidia drivers. It showed the NVIDIA logo on boot up but for some reason the desktop did not fill the screen and the right 1/4 of the screen was all vertical lines and the bottom 1/4 was a copy of the top 1/4 of the screen.

---

### Post by konungursvia on 2007-03-13
> **Dr. Feltersnatch said:**
> Can you describe what kind of problems? I have an inspiron 8200 with the same video card and have gotten beryl to work successfully.

Check this out as well:
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

Me too, I have the 8200 and am running "nvidia" with no problem, as I used "envy" to install the drivers and have the same video card as you two, and my Beryl is just fine.

---

### Post by jeza on 2007-03-15
I too experienced difficulties getting a gl desktop to function correctly on an nvidia Geforce4 440 Go. I've used many many different howtos and have tried the legacy and proprietry drivers and experienced the full boot up but no display that the Envy install seems to give others. The only way I got the drivers to function was to install the drivers through Automatix although I don't know which driver version this is. If anyone else is having difficulties with the nvidia geforce4 440 go I recommend giving this a go.

---

### Post by flusheDData on 2007-03-20
I own a Dell Inspiron 8200 laptop with NVIDIA GeForce4 440 Go and have lots of troubles trying to install an Nvidia driver.
My computer's graphic chipset is not listed in Nvidia's site as a legacy one but when I tried to install (compiling) the newest driver I got a black screen. Everythihg seems to work, I mean, I hear the gdm start sound but all black.
Another day I used the Automatix Bleeder way, but Beryl went not that well. The Genie-like effect was not smooth at all.
Then I tried the Envy way, but a black screen again.
Also I lost my Atheros wireless driver because of the restricted modules (which I have no idea how to manage. Adding "ath_pci" to the last line maybe?). As I was n ot sure I did a make clean, make and make install. Now I am as at the beginning. I have Internet but not accelerated graphics.
Anyway when I had the nvidia driver (the ubuntu's one for my kernel) my animated cursor (busy one) flickered a lot.
As you may see I am a newbie at English too. Excuses.
Best Regards,
Miguel

---

### Post by airtonix on 2007-03-21
the reason why you lost your wifi is probably not obvious....

but if you remember or maybe you didnt even have achance to see a message similar to this on the envy site

> if you install this driver you will be replacing your kernel....

so, a thought that comes to mind is you will need to recompile your wifi drivers for the new kernel...

could be wrong...and maybe you already thought of this...

---

### Post by skip27 on 2007-03-23
Try the 9631 drivers instead of the legacy 7184. This should eliminate any problems you're having, and it's what enabled me to use my Geforce4 440 Go 32MB to work with Beryl (although it's slow--you'll need a better graphics card).

---

### Post by flusheDData on 2007-03-27
> **airtonix said:**
> the reason why you lost your wifi is probably not obvious....

but if you remember or maybe you didnt even have achance to see a message similar to this on the envy site



so, a thought that comes to mind is you will need to recompile your wifi drivers for the new kernel...

could be wrong...and maybe you already thought of this...

You are right.
I compiled the nvidia kernel module and the madwifi wireless one and everything works perfectly.
BTW, the Nvidia's driver version I used for my Dell Inspiron 8200 is
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run)
No balck screen at all. And Beryl works without AIXGL nor XGL.
Thanks

---

