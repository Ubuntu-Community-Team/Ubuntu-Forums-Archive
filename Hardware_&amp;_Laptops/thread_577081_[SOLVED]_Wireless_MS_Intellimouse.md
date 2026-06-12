---
title: "[SOLVED] Wireless MS Intellimouse"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by measekite on 2007-10-15
**[COLOR=Red]FOUND SOLUTION[/COLOR]:  XEV NOW SHOWS EVENT FOR BUTTONS 6 AND 7 SIDE BUTTONS:**
**Microsoft Wireless Intellimouse Explorer 2 [COLOR=Red]Model 1007[/COLOR]**
[COLOR=Red]HERE IS THE XORG.CONF MOUSE SECTION ON FEISTY[/COLOR]

Section "InputDevice"
        Identifier       "Configured Mouse"
        Driver           "mouse"
        Option           "CorePointer"
        Option           "Device"               "/dev/input/mice"
        Option           "Protocol"             "ExplorerPS/2"
        Option           "Emulate3Buttons"      "[COLOR=Red]false[/COLOR]"
        Option           "Buttons"              "7"
        Option           "ZAxisMapping"         "4 5"
        Option           "ButtonMapping"        "[COLOR=Red]1 2 3 6 7[/COLOR]"  #Note btn 4 & 5 are not on this line
[B][COLOR=Red]
END SOLUTION[/COLOR][/B]



Situation:  Side Buttons do not work

Environment:
Feisty 7.04
[B]Microsoft Wireless Intellimouse Explorer 2 [COLOR=Red]Model 1007

[/COLOR][/B][COLOR=Red][COLOR=Black]I tried to do the same thing for my Computer 1 Logitech G7 combination and apply it to this situation for the MS Mouse.  The side buttons do not work.

I ran the command 
[/COLOR][/COLOR]```
sudo xev
```and ran tests.  Unlike my experience with the Logitech Mouse the Microsoft Mouse model 1007 returned the following events:

Left Button =1  Right Button = 3  Forward Scroll Wheel =4 Backward Scroll Wheel = 5

[COLOR=Red]Back Side Button = Nothing Returned
Forward Side Button = Nothing Returned
[/COLOR]
**Questions:**

[COLOR=Blue]Does this mean it cannot be done since there is n**o returned event**?

Am I missing something?

Has Anybody got this **exact** mouse working in Feisty?
[/COLOR]

---

### Post by linuxwizard on 2007-10-17
[https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons)

---

### Post by measekite on 2007-10-17
> **linuxwizard said:**
> [https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons)



One of the issues I am having is that when I run xev no event is returned when I click the side button.  Events are returned for Left, Right and Scroll Up and Down.

Therefore editing xorg in this way does not change anything.

When I configured my Logitech G7 events for the side button were returned and editing xorg made them work.

---

### Post by HossBud on 2007-10-21
Thanks so much for posting this information.  I cut and pasted it into my xorg.conf file and it worked perfectly!  I think I'm right on the edge of finally dumping Windows.

---

