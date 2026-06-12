---
title: "touchpad disabling"
date: 2010-11-04
forum: Hardware
---

### Post by paito1 on 2010-11-04
hi.

i have a lenovo y530 and i have a problem with touchpad. if i use that, the left mouse is being locked..

i wanna to disable the touchpad, but in spite of i have uninstalled from synaptic, it s still up and having trouble. 

i ve tried like this ;

# xinput list

# xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 13 0

but giving invalid format 13 error.


how can i disable this touchpad ? 

thanx.

---

### Post by DanaLou on 2010-11-04
Hi! I had solved a similar problem on my new HP laptop; I read that you need to download a program from the Ubuntu Software Center (use keywords 'disable tapping'). Then after istalling, go to System > Preferences > Pointing Devices .. from there you should see your touchpad device; click on it, and tick the box labeled 'Disable Touchpad' under the general tab.

NOTE: This didn't work correctly for me at first; it disabled it until I started typing anything; I had to also go into System > Preferences > Mouse and then go to the touchpad tab, and un-tick the 'disable while typing' box. NOW it is fuly disabled.

</whew!>

---

