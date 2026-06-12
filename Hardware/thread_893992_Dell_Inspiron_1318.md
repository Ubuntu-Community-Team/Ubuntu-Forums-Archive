---
title: "Dell Inspiron 1318"
date: 2008-08-18
forum: Hardware
---

### Post by BadLuckBrand on 2008-08-18
Hello all.  I just purchased a Dell Inspiron 1318, the one thats only available at WallyWorld.  

I installed Ubuntu Hardy, Ran the automatic updates, wifi is working beautifully, graphics are great (even spinning desktop cube is smooth), everything seems to work without needing any searching through forums to find a workaround.

The store price is $678 USD, I was lucky and got a display still in perfect condition for under $450.

I have not verified if bluetooth, memorycard reader, or the built in webcam work, but the dmesg seems to pick them up fine.

Having the graphics and wifi working without any tuning was amazing.

Just wanted to give a heads up for anyone who may have been looking at this model, works great with Ubuntu.

---

### Post by sevenincubus on 2008-09-28
How's volume control for you? I have this same laptop and its half volume on hardy is not as loud as vista's half volume. In fact I can barely hear anything at half volume. I've tried alsa 1.0.17 and its still the same. I think its just a volume increment problem because at 100% hardy and vista sound the same. I can confirm that bluetooth, webcam and memory card slot(SD,MMC only) work. For the internal mic to work I had to add this to /etc/modprobe.d/alsa-base:

```
options snd-hda-intel model=dell-bios
```

Other than that I am very satisfied with this laptop. One warning is that the T5750 processor does not support kvm. :( I plan on upgrading to the T8300.

---

### Post by balistardrake on 2008-09-28
I understand this is a month or so outdated, but I still hope there will be a reply.

Did you get it all working without any edits at all? Did you get it all to work only after the updates?

I recently purchased a dell inspiron 1318 and am trying to install ubuntu. However, after the install, I do not get wifi and the top and bottom panels do not stretch all the way. 

Any tips?

---

### Post by Cytomax on 2008-11-04
So hows the new 8.10 working on these laptops... is it just a 
simple put in the CD and everything works?
Thanks in Advance
Eddie

---

### Post by BiggRedd on 2008-11-15
I have been running 8.04 for almost 2 mo.  I had to use ndiswrapper for wifi and the sound levels are lower than with vista, but otherwise it's running Great!  I am tring to find a way to use an external monitor and turn the laptop screen off.  So far I can only use the external while my main screen is on.

---

### Post by analystscouch on 2008-11-16
Hi there,

Could BadLuckBrand and BiggRedd just confirm for me which wifi cards you are using?

I'm thinking of buying the 1318 and want to know if Wifi will work without NDISwrapper. BadLuck you seem to suggest it will, but BiggRedd you say it won't - i'm guessing you have different configs.

Thanks,
Nick

---

### Post by richaoj on 2008-12-03
I think that it depends on which card you choose.  I have the basic Dell a/b/g card and it worked just fine out of the box.  I had similar sound issues with the microphone/etc, but generally this laptop works great with ubuntu.

---

### Post by teamsuperoxide on 2009-04-01
Hi there, I've just installed 8.04 on my 1318 but can't get the WiFi to work. That said, I wasn't able to get it working in XP and therefore loaded Ubuntu....
I've run NDISwrapper but I'm not sure which drivers are for what....
Help....

---

### Post by ReyPorUnDia on 2009-04-22
Try to install or upgrade to 8.10, i did that on my 1318 and worked perfect with all the HW.
And about the sound...maybe it fixes when u upgrade.

---

### Post by dondabull on 2009-05-15
I installed ubuntu on my inspiron 1318 and noticed that my CD/DVD Rom drive could only read DVDs but not CDs.  Did anyone have same issues?  When I tied to open a CD I got an error message that no media was found or something like that.  Any ideas?

Thanks

---

### Post by dolphinsonar on 2010-05-16
Hi all,

This thread is old, so I am guessing you have fixed these issues or moved on, but the microphone not working can be fixed using this solution:

[http://ubuntuforums.org/showthread.php?p=9307284](http://ubuntuforums.org/showthread.php?p=9307284)

If you had problems with the wireless connection, upgrading to Lucid Lynx will fix that.  I am on a Dell Inspiron 1318 laptop, assuming this is the same computer today as it was when the first post was published...

---

