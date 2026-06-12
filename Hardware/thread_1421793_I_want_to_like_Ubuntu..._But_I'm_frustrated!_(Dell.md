---
title: "I want to like Ubuntu... But I'm frustrated! (Dell Laptop)"
date: 2010-03-04
forum: Hardware
---

### Post by Mickelonis on 2010-03-04
I have an old Dell Inspiron 8000 laptop and I think Ubuntu would be a great fit. I've always been curious about Linux (I am a Windows user), however I can't help but be completely frustrated in getting it to work properly.
 
Let's start with the video driver.... The max resolution I can get according to Ubuntu is 800x600, however that's a lot lower than native resolution.
 
My laptop is on this list: [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)
 
Seems like it should work to me... I'm friggin lost as to how to get proper resolutions from Ubuntu on this laptop....
 
When going to Dell.com to look for drivers, they offer a "Red Hat Linux 7.0" driver... Will this work for Ubuntu? If so, I have no idea how I can get it to work...
 
[http://support.dell.com/support/downloads/driverslist.aspx?os=LN70&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INS_PNT_P3CG_8000&hidos=WW1&hidlang=en&TabIndex=&scanSupported=True&scanConsent=False](http://support.dell.com/support/downloads/driverslist.aspx?os=LN70&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INS_PNT_P3CG_8000&hidos=WW1&hidlang=en&TabIndex=&scanSupported=True&scanConsent=False)
 
Can anyone please lend a hand? I am COMPLETELY lost....
 
Thanks!
 
-Pete

---

### Post by ghostborg on 2010-03-04
Try looking into what hardware drivers are available to you.

System=>Administration=>Hardware Drivers .Reboot.

If you are lucky to get that going then check
System=>Preferences=>Appearance then Visual Effects tab to enable
the special effects.

CompizConfig settings manager available in the Repository to fine tune
you Compiz settings.

Mediabuntu.org to get your DVD working with protected discs and some codecs.
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Also in your repository is ubuntu-restricted-extras .

---

### Post by b0b138 on 2010-03-04
You might want to try envyng. Its a little utility that will help download and install the right video drivers for ati and nvidia.  And since this is an older laptop with older hardware, im guessing support for it has been dropped from the newer video driver packages.

---

### Post by candtalan on 2010-07-15
I had some success with my 8000 - maybe this link will help
[http://ubuntuforums.org/showthread.php?t=1531644](http://ubuntuforums.org/showthread.php?t=1531644)

good luck

---

