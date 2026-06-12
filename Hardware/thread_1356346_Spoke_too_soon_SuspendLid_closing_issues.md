---
title: "Spoke too soon: Suspend/Lid closing issues"
date: 2009-12-16
forum: Hardware
---

### Post by BaroqueBloke on 2009-12-16
I posted earlier in the Cafe that My Macbook 1,1 miraculously started working perfectly today.  Well, I spoke too soon.  

I am running 9.10.  Complete install, no OSX remains on my laptop.  When I close the lid the backlight turns off but the computer stays running.  Then, after about 10-15 seconds the backlight turns back on.  Before, I could never get it to wake up from sleep after the lid had been closed and would have to reboot.  

????

This is my first Linux experience and so far I am enjoying it quite a bit.  I have learned more about computers through working out bugs in this then I ever thought I would.  
BUT, its not perfect yet.  And I will obsess about it until it is.   :D   

ANY help or suggestions will not go unappreciated here.  I have done a lot of googleing and forum surfing to try and get the bottom of this but with no success.  

Maybe one of you out there knows the answer.  


Cheers!

---

### Post by BaroqueBloke on 2009-12-16
I should note, also, that suspend seems to work fine so long as I execute from the shutoff menu.  The problem only occurs when I simply close the lid.  :confused:

---

### Post by tenfishsticks on 2009-12-16
Same problem here.  I have a eMachines E627, 64bit, with a FGLRX video card running Jaunty.  If I select suspend from the menu, all's well.  If I close the lid and try to wake it later, all I get is the black screen and a white cursor.

Did you every find a solution to this?

---

### Post by coffeecat on 2009-12-16
@BaroqueBloke, have you had a look in System > Preferences > Power Management to see what your settings are there? If that doesn't help, there's a dedicated Apple subforum:

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

... where you're more likely to find people with experience of Apple hardware.

@tenfishsticks, suspend problems are usually hardware-related, so your eMachines issue is unlikely to be related to the OP's problem with a Macbook. To show how the ymmv principle works with suspend, suspend with lid closure works just fine on both my Sony and Acer laptops, but a search of the forum will show people having problems with certain laptop types. The quality of ACPI implementation varies so enormously  that suspend is never going to work for everyone, despite the impressive efforts of the kernel developers.

If the Power Management settings don't help, you may be better off starting your own thread with eMachine in the title.

---

