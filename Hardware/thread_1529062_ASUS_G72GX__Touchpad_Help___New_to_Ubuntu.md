---
title: "ASUS G72GX \ Touchpad Help \  New to Ubuntu"
date: 2010-07-11
forum: Hardware
---

### Post by Judges1979 on 2010-07-11
[LEFT]I am looking for someone or anyone for that matter that has a solution for my laptop.  I have been searching for the past 2 days trying most solutions.  Ubuntu works great using 10.04 64-bit.:D  Playing Wow with wine and doing more with this then I ever did Windows.  Problem seems to be that I can not disable my silly touch pad.  I have no reason to even use it due to I use an external mouse I would say about 99.5% of the time.  I do have a mouse disable button on my laptop but it only disables the touchpad for a few moments.  Anyone have any configuration help they can give or any thoughts.  New Guy happy for any and all help you can give.

Thanks in advance.

[/LEFT]

---

### Post by Judges1979 on 2010-07-12
Looks like I have solved my own issue.  Here is what I have done.

Under system -> Perferences -> Mouse

You have 3 tabs. (General, Accessibility, and Touchpad)
Select Touch pad make sure both boxes are unchecked Disable touchpad while typing and enable mouse clicks with touchpad again uncheck them.

Then goto Ubuntu software center and find the pkg Pointing Devices and install it.  From here I had rebooted not sure if really needed but what the heck...  

Once i rebooted you will go to Under system -> Perferences -> Pointing Devices.

Select SynPS/2 Synaptics Touchpad this is if you have another mouse already installed like I do.  From here select The General Tab and select touchpad off Guest mouse left unchecked and Enabled Palm Detection set both sliders to the left so Range:Narrow and Pressure:Low.  Closed the programs out and rebooted once more just for giggles.

And now I can use my button on my laptop to Enable and disable the touchpad when I please...  It was so nice writing this without worry of the touchpad.;)

I certainly hope this helps others like it has helped me.  I have detailed this out and tried it 3 times and rebooted 3 times and get the same results.  This might work for other Asus computers but  don't have any others to try.  Good Luck

---

### Post by jack frost on 2011-02-11
thanks for your post. I use a usb mouse and this  worked pefect for disabling the touchpad mouse.
 
> **Judges1979 said:**
> Looks like I have solved my own issue. Here is what I have done.
 
Under system -> Perferences -> Mouse
 
You have 3 tabs. (General, Accessibility, and Touchpad)
Select Touch pad make sure both boxes are unchecked Disable touchpad while typing and enable mouse clicks with touchpad again uncheck them.
 
Then goto Ubuntu software center and find the pkg Pointing Devices and install it. From here I had rebooted not sure if really needed but what the heck... 
 
Once i rebooted you will go to Under system -> Perferences -> Pointing Devices.
 
Select SynPS/2 Synaptics Touchpad this is if you have another mouse already installed like I do. From here select The General Tab and select touchpad off Guest mouse left unchecked and Enabled Palm Detection set both sliders to the left so Range:Narrow and Pressure:Low. Closed the programs out and rebooted once more just for giggles.
 
And now I can use my button on my laptop to Enable and disable the touchpad when I please... It was so nice writing this without worry of the touchpad.;)
 
I certainly hope this helps others like it has helped me. I have detailed this out and tried it 3 times and rebooted 3 times and get the same results. This might work for other Asus computers but don't have any others to try. Good Luck

---

