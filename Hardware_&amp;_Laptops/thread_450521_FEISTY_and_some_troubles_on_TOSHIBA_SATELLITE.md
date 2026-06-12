---
title: "FEISTY and some troubles on TOSHIBA SATELLITE"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by _deneb_ on 2007-05-21
Hi everybody,

I'm new and running Feisty on a Toshiba Satellite M40-284
Anyway, got three main problems at the moment :

1) When I SUSPEND the session there is NO WAY to wake the laptop up again! I mean, I can move the mouse, flipp the lid, press the power button or a key.. nothing happens! To use the computer again I have to remove the cell first! :P

2) I have no linux drivers for my devices.. and it's very annoying that I don't know how to deny the single or double-click with the touchpad. I mean.. I just wanna use the proper buttons, not the touchpad. How can I manage this?

3) The mouse sometimes doesn't work. It's a Microsoft (x_x) compact optical USB mouse and sometimes it stops working. No way to bring him to life again. The mouse it's new and it used to work on XP.

Any suggestions? Thx (^_^)
_deneb_

---

### Post by Psicolonia on 2007-05-21
I have no ideia but instead of removing the cell, press the power button for 10 seconds (should take less)

:) sorry... don't know hoe to solve thoso problems yet ;)

---

### Post by _deneb_ on 2007-05-21
> **Psicolonia said:**
> I have no ideia but instead of removing the cell, press the power button for 10 seconds (should take less)

:) sorry... don't know hoe to solve thoso problems yet ;)


hehe I know that pale... the fact is that if I press the power for 10 or 20 or 1000 seconds nothing would happen! :D It tries to shut down but I can't!! Really strange.. I kwno (xox)

_deneb_

---

### Post by stchman on 2007-05-21
> **_deneb_ said:**
> Hi everybody,

I'm new and running Feisty on a Toshiba Satellite M40-284
Anyway, got three main problems at the moment :

1) When I SUSPEND the session there is NO WAY to wake the laptop up again! I mean, I can move the mouse, flipp the lid, press the power button or a key.. nothing happens! To use the computer again I have to remove the cell first! :P

2) I have no linux drivers for my devices.. and it's very annoying that I don't know how to deny the single or double-click with the touchpad. I mean.. I just wanna use the proper buttons, not the touchpad. How can I manage this?

3) The mouse sometimes doesn't work. It's a Microsoft (x_x) compact optical USB mouse and sometimes it stops working. No way to bring him to life again. The mouse it's new and it used to work on XP.

Any suggestions? Thx (^_^)
_deneb_

My Toshiba laptop does the same thing.  I have come to the conclusion that Suspend or Hibernate do not work with Ubuntu and these laptops.  I just go in the Power Management section and don't ever let the laptop go into either of these modes.

I did not have to remove the battery, just hold down the power button for about 10 secs until the laptop shut off.

---

### Post by madscience on 2007-05-21
Has anyone tried adding ec_intr=0 to your kernel command line?  Supposedly it fixes the issue for some thinkpads.  I've gone back to Edgy on my M30 due to the same issues with suspend in Feisty...

---

### Post by calgarystevens on 2007-05-21
Suspend on my Toshiba A100 is working flawlessly now, after I switched to this type:

sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

and in lines that say:
elif [ -x "/sbin/s2ram" ] ; then
	    /sbin/s2ram -f       <--------Add the -f to force suspend
	   RET=$?
To go back to the old type of suspend -> sudo dpkg-divert --rename --remove /usr/sbin/pmi

That worked for me, it switches the default suspend version, and this one works fantastic for me. If you also have an ATI Xpress 200M these tips might be needed also, because of the finicky ATI drivers (never seemed to restore properly). Try these:

sudo gedit /etc/acpi/sleep.sh
On second line put: sudo chvt 1

sudo gedit /etc/acpi/lid.sh
On second line put: sudo chvt 1

sudo gedit /etc/acpi/resume.sh
On last line put: sudo chvt 7

sudo gedit /etc/default/acpi-support
Edit lines thusly:
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

Good luck, hope it works for you also ;)

---

### Post by _deneb_ on 2007-05-22
> **calgarystevens said:**
> Suspend on my Toshiba A100 is working flawlessly now, after I switched to this type:

sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

and in lines that say:
elif [ -x "/sbin/s2ram" ] ; then
	    /sbin/s2ram -f       <--------Add the -f to force suspend
	   RET=$?
To go back to the old type of suspend -> sudo dpkg-divert --rename --remove /usr/sbin/pmi

That worked for me, it switches the default suspend version, and this one works fantastic for me. If you also have an ATI Xpress 200M these tips might be needed also, because of the finicky ATI drivers (never seemed to restore properly). Try these:

sudo gedit /etc/acpi/sleep.sh
On second line put: sudo chvt 1

sudo gedit /etc/acpi/lid.sh
On second line put: sudo chvt 1

sudo gedit /etc/acpi/resume.sh
On last line put: sudo chvt 7

sudo gedit /etc/default/acpi-support
Edit lines thusly:
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

Good luck, hope it works for you also ;)


:( No way pal.. :(
I tried but nothing has changed. I do think is because of my ATI express because it's in the RESTRICTED DRIVERS list. The system suggested me to use another driver... now I'm switching to the ATI driver and see what happens..

cya
_deneb_

---

### Post by _deneb_ on 2007-05-22
I enabled the ATI driver in the Restricted Drivers and after a brief installation I tried to SUSPEND.
Now when I try to wake him up again, I see the mouse cursor appear and disappear continuosly on a BLACK screen. But nothing more

I checked the changes I made before the installation  and I saw that the acpi-support files has been restored. 
I made those changes again but then everything was as before.. and I couldn't see even the mouse coursor blinking anymore 

> **calgarystevens said:**
> 
sudo gedit /etc/default/acpi-support
Edit lines thusly:
MODULES_WHITELIST="fglrx" 
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true


:( what can I do.. ?? My VIDEO CARD is "RS400 [Radeon Xpress 200M]" 

_deneb_

---

### Post by calgarystevens on 2007-05-22
> **_deneb_ said:**
> 

:( what can I do.. ?? My VIDEO CARD is "RS400 [Radeon Xpress 200M]" 

_deneb_
I don't know what else to try, mine is the Radeon Xpress 200M also, and it took a bit of fiddling but it finally works perfect. Maybe I changed something I've forgotten. It's definitely not easy, but if you keep trying it can work, I'm convinced. It did on mine anyway. This is where I got my final fix for it, after I had done the editing of acpi-support etc with the pmi method of suspend that never did work for me: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)
Maybe something there will help hopefully.

---

### Post by _deneb_ on 2007-05-22
> **calgarystevens said:**
> I don't know what else to try, mine is the Radeon Xpress 200M also, and it took a bit of fiddling but it finally works perfect. Maybe I changed something I've forgotten. It's definitely not easy, but if you keep trying it can work, I'm convinced. It did on mine anyway. This is where I got my final fix for it, after I had done the editing of acpi-support etc with the pmi method of suspend that never did work for me: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)
Maybe something there will help hopefully.

Thx anyway.

I posted something in the page you mentioned. I hope they will answer
Byez

_deneb_

---

### Post by mbittleston on 2007-06-02
thanks for the hint, calgarystevens. tried it with toshiba satellite A105 but both with and without the /etc/acpi/... edits it does not work.

---

