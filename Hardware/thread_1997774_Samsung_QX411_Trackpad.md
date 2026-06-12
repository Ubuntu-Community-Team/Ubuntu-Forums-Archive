---
title: "Samsung QX411 Trackpad"
date: 2012-06-05
forum: Hardware
---

### Post by porky101 on 2012-06-05
I recently installed Ubuntu 12.04 LTS on my Samsung QX411-W02 laptop using WUBI and I am having issues with the trackpad.  Two-finger scrolling works, but the right click does not work and when I left click + drag (to move windows) it does not work.

Are there any additional drivers I can download for this?

---

### Post by sajanko on 2012-06-26
hi 
i also had a same problem before just copy and paste the command below in your terminal it should work..

sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot

    OR-

    Go to System>Preferences>Mouse and select "TouchPad" Tab and select 2 finger scrolling and 2 finger right click.

* Remember that to copy or paste text in the terminal you have to use CTRL+Shift+C and CTRL+Shift+V.

I used the code solution and lost the trackpad scrolling.

content from the link below



[http://ramonsuarez.com/how-to-install-ubuntu-in-a-samsung-900x3a-ult](http://ramonsuarez.com/how-to-install-ubuntu-in-a-samsung-900x3a-ult)

---

### Post by porky101 on 2012-06-26
Thanks!  It works!

I looked for a solution for so long and could not find one.  Thanks!

---

