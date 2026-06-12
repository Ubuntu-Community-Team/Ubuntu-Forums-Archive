---
title: "Ubuntu and Acer 4202 with Intel Duo"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by kingsidy on 2006-03-02
I recently purchased and Acer Travelmate 4202. I am about to install Dapper on it as a dual boot. And I was wonering whether there were any issues I should look out for. I know that the wireless adapter, an intel 3945 a/b/g, is not yet fully supported. Although I hear that some drivers were released a couple of weeks ago. If anybody got this working could you please detail how.

---

### Post by jdong on 2006-04-18
Please keep us up to date on how things work here. I am very interested myself in purchasing this laptop. Any comments about the laptop itself are well appreciated.

If it has the Intel GMA 950 graphics card, it may require the 915resolution / (955resolution?) hack to go up to 1280x800, because intel seemingly omitted higher resolution modes from the video BIOS.

The sound chipset is supposedly supported in Dapper. The kernel devs are working on integrating the ipw3945abg drivers into Dapper. They say it will be done for the Dapper release, but there is code reorganization that needs to happen.

Meanwhile, there are open-source (sort of) drivers from Intel via their ipw3945 sourceforge project. They should work ,but require some level of research and dedication to set up :)

---

### Post by nolongerlivecd on 2006-04-19
Just curious, and slightly OT, is it possible to tri-boot XP, Dapper and Breezy?

---

### Post by jdong on 2006-04-19
It it indeed possible to boot as many different Linux + windows installs as you can manage to partition :)

I believe the installer is also intelligent enough to provide appropriate grub entries for that, without additional tweaking.

A lot of us Dapper testing people do that during the earlier testing phases where breakages were very possible.

---

### Post by Tom^ on 2006-05-14
Hi, Kingsidy

I'm about to buy that same laptop and I was wondering have managed to get all the bits and pieces working? Does the wlan and sound work for you? How about hibernation? Is there something that you don't like in that laptop?

Thanks in advance for all info

---

### Post by vmark on 2006-05-14
I just bought this laptop yesterday and immediately set about getting Dapper set up. There were a few caveats, but I eventually worked them all out.

First was the laptop only displaying in 1024x768. This was fixed by installing 915resolution from the repository and adding the correct modes (1280x800) to the bios. I still have a strange problem with OpenGL. The KDE GL screensavers only seem to display in the top half of the screen. I have this same problem with an IBM thinkpad that has the i915 chipset. However, my friend with an Acer Aspire that has i945 like the TravelMate has his GL working right. I'm at a loss.

The second thing, of course, was the wireless. I was under the impression when I bought this that it was ipw2200, a little shocked to learn it was actually the even less supported ipw3945. I followed another thread on this forum for getting that driver installed. It requires installing the build chain and making the modules yourself for now. After I got it bringing up an eth1 using the manual instructions, following the "Install in your distribution" section of the ipw3945 INSTALL file got it setting up eth1 flawlessly on boot.

Then it was just a matter of installing KNetworkManager from the repository (and NetworkManager of course), it immediately showed me a list of all available wireless networks, I picked my router from the list, entered my WPA2 passphrase and I was in business.

I installed ksynaptic to get the touchpad fully working (tap with 2 fingers to middle click, horiz. and vert. scrolling zones, etc).

The only thing I don't have working at all that would be nice are the Acer hotkeys. Not a deal breaker for me, but any insight would be helpful.

---

### Post by vmark on 2006-05-18
Just an update, loading module 'acerhk' with parameter 'force_series=4000' causes the 4 hotkeys to start generating standard keypress events. Now I have them starting kopete, konqueror, konsole and locking the display.

just add
acerhk
to /etc/modules, and
options acerhk force_series=4000
to /etc/modprobe.d/options

Then create your keybindings in ~/.Xmodmap and load it at KDE start by putting a .sh script that does so in ~/.kde/env

In addition: I tried some OpenGL apps that weren't the KDE screensavers and they work perfectly. I wonder if they're compiled against the wrong GL library or something similar.

---

### Post by Firetech on 2006-07-10
OK, I realize I'm reviving a dead thread, but...

> **vmark said:**
> Then it was just a matter of installing KNetworkManager from the repository (and NetworkManager of course), it immediately showed me a list of all available wireless networks, I picked my router from the list, entered my WPA2 passphrase and I was in business.

Hmm, I couldn't get NetworkManager (and KNetworkManager) to find my ipw3945 (it only listed the wired interface, that wasn't connected). Did you do anything special to get it working? (I didn't touch any config files...)

---

### Post by Firetech on 2006-07-10
Ok, got it working by commenting out all interfaces except lo in /etc/network/interfaces. My WLAN without SSID-broadcast seems to be a bit of a problem though... Might have to revert to KWlan and wpa_supplicant. :/

---

