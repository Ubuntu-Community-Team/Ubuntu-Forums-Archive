---
title: "EasyPen stuck in corner with 10.10"
date: 2010-11-22
forum: Hardware
---

### Post by abujenin on 2010-11-22
Completing set up of my new Genius EasyPen i405 is getting to hard for me. I followed the instructions, but may be there is a different set up for 10.10 (Maverick Meerkat)... remembered maverick means doing things differently! 
I followed: 
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
but it did not work well, so I tried: 
[http://ubuntuforums.org/showthread.php?t=1337260&highlight=Genius+EasyPen](http://ubuntuforums.org/showthread.php?t=1337260&highlight=Genius+EasyPen)

Yet still when I try using the EasyPen tablet, the courser just get stuck in the upper left corner. 

I had a Genius MousePen 8x6 working since about 9.04 or 9.10; but found it defective when decided to use it recently. So the old configuration of it my be corrupting EasyPen configuration. 

Attached are 
 /etc/hal/fdi/policy/99-x11-wizardpen.fdi
 /usr/share/X11/xorg.conf.d/70-wizardpen.conf

Appreciating your assistance and all the effort you put on FOSS; and giving an angry face :mad: to hardware manufacturers that do not support the open software community.

---

### Post by Favux on 2010-11-22
Hi abujenin,

You don't use the .fdi with Maverick.  If you made any changes to your xorg.conf for the EasyPen comment them out.

First try changing your 70-wizardpen.conf to:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
#    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
#    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
Reboot and see what happens.

---

### Post by abujenin on 2010-11-23
Thank you very much. EasyPen is now working fully across all the screen and with pressure sensing.
So I assume the calibration setting are stored in the .fdi file and not in the .conf file. 

Regards,

---

### Post by Favux on 2010-11-23
Hi abujenin,

Good!

No, there is no .fdi in Lucid or Maverick, HAL was removed.  I believe the WizardPen driver is getting the coordinates from a table it has or a table in the WizardPen kernel driver.

---

