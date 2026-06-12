---
title: "Disable Wireless Network"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by ed_unique on 2008-01-26
How do I disable the wireless network in Ubuntu 7.10? Previously in Network Settings there were an activate and deactivate buttons but they seem to be gone now.

---

### Post by chewearn on 2008-01-26
First, you go into Network Settings, disable "roaming mode" for the adapter (in Properties), then you can uncheck the box next to the wireless interface to disable it.

---

### Post by ed_unique on 2008-01-26
A problem with that is that when I uncheck roaming mode the OK button is disabled.

---

### Post by chewearn on 2008-01-26
After unchecking roaming mode, select Static IP, and key in a correct static IP configuration (include the gateway).  Or select DHCP; then the OK button will be enabled.

---

### Post by MikeyXX on 2008-01-26
How I disable wireless, is I go to the top by the clock there is either a wireless signal strength or two monitors indicating your network status. If you right click this, there are two checkmarks. One beside "enable networking" and the other beside "enable wireless". I just uncheck the "enable wireless" when I don't want my wireless radio on. 

Works great for me when I have both wireless available but I choose to use the network cable.

Lemme know if that works. It seems to be quicker than these other methods but might not be what you want.

---

### Post by ed_unique on 2008-01-26
AstalaVista - Yes I can press the OK button if I type in a static network address. But when open the dialog again the roaming mode is checked again.

MikeyXX - You are propably right when the wireless network is connected. But since I have no wireless device to communicate with it is not and I only have a wired network connection at the clock. As I understand it the roaming mode means that the computer searches for a wireless network which is what I want to avoid.

---

### Post by chewearn on 2008-01-26
Disable roaming mode in the properties dialogbox (and click OK).

Then at the Network setting dialogbox (not the properties dialogbox), next to your wireless interface (in the list), unselect the checkbox.

---

### Post by ed_unique on 2008-01-26
SUCCESS! I added the line "blacklist ipw2200" to "/etc/modprobe.d/blacklist". But I whish they would put the deactivate button back. It was much easier.

---

### Post by MikeyXX on 2008-01-27
> **ed_unique said:**
> 

MikeyXX - You are propably right when the wireless network is connected. But since I have no wireless device to communicate with it is not and I only have a wired network connection at the clock. As I understand it the roaming mode means that the computer searches for a wireless network which is what I want to avoid.

If it's not connected, you should get a little grey computer with an "!" or something similiar. If you right click this, you'll still be offered to turn off wireless. Again, I do this when I'm at work where there is a wireless that I don't want to use (and haven't associated to it either).

Give it a go.

---

