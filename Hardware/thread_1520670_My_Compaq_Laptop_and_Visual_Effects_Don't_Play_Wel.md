---
title: "My Compaq Laptop and Visual Effects Don't Play Well Together !"
date: 2010-06-29
forum: Hardware
---

### Post by Windows Refugee on 2010-06-29
Despite running into various major problems with Intrepid, Jaunty and Karmic on my Compaq Presario 900 series laptop (2002 vintage), I decided to give Lucid a try.  

The fresh (dual boot with Grub) install of 10.04 LTS went without a hitch, but the resulting copy of Lucid was unusable because it was so slow.  "Laggy" doesn't begin to describe the situation.  I would type a few letters on the keyboard, and they wouldn't appear on the screen for five or ten seconds.  When I tried to close, move or minimize a window, it wouldn't react for a few seconds, and then could take a few more seconds before it completed the action.  It was completely unusable.

I took a look at the published system requirements, and while my laptop doesn't meet all of them (ie: recommended minimum 1 GB of RAM), my gut told me that it was SO slow, this wasn't simply a CPU that wasn't fast enough to run Ubuntu.  I mean, if Windows XP performs well on this machine, shouldn't I be able to run a Linux O/S ?

Because the performance problem was centered around very slow screen updates, I suspected a video driver issue.  But the solution (in my case) turned out to be changing a single system setting.  Under SYSTEM > PREFERENCES > APPEARANCE, I clicked on the "Visual Effects" tab, and selected "None" (it was set to "Normal").  Voila !  Performance problem solved.  Now, Lucid is performing wonderfully, and is very responsive.

Perhaps the graphics chip in my laptop just can't handle or does not support Ubuntu's (Debian's?) "visual effects".  While I realize that this is an older machine, my experience makes me wonder whether "NONE" should be the default initial setting for visual effects regardless of the hardware Ubuntu is being installed on, with the option to enable it left to the user.

Compaq Presario 906
AMD 1.5 GHz Athlon CPU
ATI Radeon graphics
512 MB RAM (shared with the video adapter)

---

### Post by edfast on 2011-05-13
Brilliant! I am running 0904 on the same type of machine and with the same specs. Love it, but had problems with 1004 so decided not to upgrade until I have upped the RAM. However, since you're apparently into tweaking vintage machines using Ubuntu, perhaps you can advise me on another issue. The presario 900 has wifi capabilities, but no device to turn them on mechanically, such as a proper switch, on-off-like. Instead, it uses the fn+F2 keystroke, and whereas all the other fn+Fx combinations seem to work ok under jaunty, this one unfortunately does not. My question is if you have some workaround or fix to solve this problem, or are you running wired?

---

### Post by Windows Refugee on 2011-05-14
> **edfast said:**
> Brilliant! I am running 0904 on the same type of machine and with the same specs. Love it, but had problems with 1004 so decided not to upgrade until I have upped the RAM. However, since you're apparently into tweaking vintage machines using Ubuntu, perhaps you can advise me on another issue. The presario 900 has wifi capabilities, but no device to turn them on mechanically, such as a proper switch, on-off-like. Instead, it uses the fn+F2 keystroke, and whereas all the other fn+Fx combinations seem to work ok under jaunty, this one unfortunately does not. My question is if you have some workaround or fix to solve this problem, or are you running wired?

My Compaq 906 laptop (actual model is "906US"), which I am using to post this reply, does NOT have built-in Wi-Fi.  I use either a PCMCIA Wi-Fi card or a USB-connected Wi-Wi adapter, depending on the situation.  Compaq DID offer a Wi-Fi option for this laptop, because there is a door built into one corner of the lid of the laptop, which can be removed and replaced with their "Wireless LAN W200" Wi-Fi adapter (which was 802.11b only, ie:11Mbps).  Under this removable panel in the lid, there is a small circuit board with what appears to be a proprietary USB connection for the Wi-Fi adapter.  I've done searches on the Web over the years, but have never found the Compaq Wi-Fi adapter that this laptop was designed to accept, but when I just searched again, I found what I believe is the Compaq Wi-Fi option for the Presario 900 (and several other Compaq laptops of that vintage ([See them here on eBay]("http://shop.ebay.com/?_nkw=compaq%20wireless%20W200&rvr_id=232340983331&clk_rvr_id=232340983331")).   Since I don't have built-in Wi-Fi, I can't respond directly to your question regarding turning your Wi-Fi on and off from within Ubuntu.  However, I would guess that Compaq provided a driver with your laptop, which listens for the FN + F2 keystroke to turn the Wi-Fi adapter on and off.  If such a thing even exists for Linux (don't know if it does), you would need to install software in Ubuntu to turn your Wi-Fi on and off.  If you can identify the Windows driver that Compaq supplies for your Wi-Fi adapter,  perhaps you could run it on Ubuntu using the WINE emulator ???  ([Here's the Compaq driver]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-27036-1&lc=en&dlc=en&cc=us&os=228&product=95668&sw_lang=") for the Compaq W200 adapter I previously mentioned. The description on Compaq's download page mentions the FN + F2 keystroke combination.)  I'm guessing (based on your post) that you are outside the United States so perhaps Compaq sold other machines in the Presario 900 series with different features, in other countries.

Regarding running Ubuntu on a Compaq 906US laptop, I just installed Ubuntu 11.04 (Natty Narwahl) on this machine, and the only major issue I came across was similar to the issue I had with Lucid (Ubuntu 10.04).  In Natty, I must choose "Ubuntu Classic (No effects)" on the taskbar at the bottom of the login screen.  Otherwise, it never brings up the Gnome desktop (but I can get to the terminal screen by pressing CTRL + ALT + F1) . This seems to be an issue with the "ATI Radeon Mobility U1" graphic adapter on this machine.  I don't know how much memory you have installed, (I'm running 512MB), so you may experience different results if you try installing Natty.

By the way if you decide to use an external Wi-Fi adapter on your Presario laptop, you might have to install a driver for it to work with Ubuntu.  I installed a great little utility called ndisgtk from within the Synaptic package manager.  Ndisgtk makes it very easy to install the necessary Wi-Fi card drivers (in my case, a Broadcom driver for my Motorola PCMCIA Wi-Fi card, and a SiS driver for my "eHome" USB Wi-Fi adapter).

---

