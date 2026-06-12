---
title: "nvidia driver 313 breaks display"
date: 2013-09-22
forum: Hardware
---

### Post by hc4cQTP on 2013-09-22
I wished to upgrade my video driver from 310 to 313. So, I went to "Software and Updates" and the "Additional Drivers" tab.
I then selected the 313 driver.

This broke my display. The system would boot, but when X started up, the display was black and unresponsive.
I was able to drop down to a console prompt, and I used the following commands to remove driver 313:
#dpkg --get-selections | grep nvidia
#apt-get remove nvidia-313-updates

This allowed me to get back to a GUI where I was able to select the original 310 drivers.

However, what now seems to be happening is that X and my window manager will start successfully approximately every other boot.
When it doesn't start correctly, if I do a hard reset (ouch), it will then start correctly.

When I check the "Additional Drivers" tab, it shows the nvidia 310 drivers selected.

I would appreciate your guidance in how to troubleshoot this.

Thanks!

---

### Post by hc4cQTP on 2013-09-22
Update: I found the answer here - 
[http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver](http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver)

I needed to do the following steps from a console:
1. sudo apt-get --purge remove nvidia-current
2. reboot
3. Run the following commands:
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
sudo apt-get install nvidia-current nvidia-settings
4. reboot

I didn't use the "--purge" flag the first time. Perhaps that was the difference.

---

