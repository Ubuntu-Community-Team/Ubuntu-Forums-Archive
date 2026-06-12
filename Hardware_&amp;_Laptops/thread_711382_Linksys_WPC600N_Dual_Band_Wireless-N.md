---
title: "Linksys WPC600N Dual Band Wireless-N"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by zaipai on 2008-02-29
Ok, so I had this card for my P3 laptop, well Ubuntu did not detect it so I thought I would use NDiswrapper and use the XP drivers. I followed a post for using NDiswrapper with a different card. So I stream lined it and I hope this helps.

Steps:

1) connect ethernet cable...turn on computer...boot into ubuntu ...ensure internet is working

2) open synaptic package manager 
system-->Administration-->Synaptic Package Monitor

3)hit ctrl+f and search for ndiswrapper (make sure the search is set to 'description and name)

you should get 3 entries:
1)ndisgtk
2)ndiswrapper-common
3)ndiswrapper-utils-1.9

install all of them by ensuring all are checked off and hitting apply 
(not if the box is dark it is already installed)

4)Find some wireless drivers
-look for your card on the forums...find a link for wireless drivers...make sure they are for your card..Or do what I did and use the CD that came with the card, use ndisgtk to install the WindowsXP/2000 drivers.

-you need two files - a .inf as well as a .sys file - note that files for vista don't usually dont work in ubuntu

*** note I do not know what this does but it worked ****
5) Go to applications-->accessories-->terminal 

copy in the following
Code:
echo 'blacklist wpc600n' | sudo tee -a /etc/modprobe.d/blacklist

6) DO NOT FORGET THIS STEP - go back to terminal and copy paste in the following command:
Code:
sudo gedit /etc/modules

a new window (text file) will open...at the bottom there is a list of names...add ndiswrapper to this list (do not misspell) 
save file...reboot to ensure everything is working... TA DA your done
hit enter...leave the terminal running in the background for now..

While I am not exactly new to Linux I am not a hardcore user, so there maybe a better way to do this, but it worked for me. I don't know if WEP/WPA/WPA2 works but I believe it will.
 I will test later and post results. This should work for other wireless cards that don't show up. I should also mention I am using GeUbuntu and its really just Ubuntu 7.10 with Enlightenment window manager. However because its Ubuntu under the hood it should work in stock Ubuntu systems as well.... Good Luck

---

### Post by zaipai on 2008-02-29
I can verify it does work with WPA/WPA2 and WEP.. I just had to make sure WPASupplicant (its in the repositories, just use Synaptic Package manager in the under the Administration menu) was installed and showed up in gkndis (it did by default).

---

### Post by zaipai on 2008-03-07
One note.. I had to reinstall so I went with Ubuntu 7.10 and it just worked using just NDiswrapper and WPASup, I used Ndisgtk to install the XP driver that came on the CD..

---

### Post by quadm on 2008-06-01
I could not get this to work on hardy. have you tried it yet?

I definitely have it installed, and ndiswrapper definitely verifies when the card is inserted. However I am unable to connect or attempt to connect to any networks. I am not sure if nm-applet is the issue?

Have you tried this on hardy yet zaipai?

---

