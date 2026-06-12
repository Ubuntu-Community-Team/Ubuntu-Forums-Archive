---
title: "Issues with ATI Radeon HD 7870 Graphics Card (Tahiti LE)"
date: 2017-01-08
forum: Hardware
---

### Post by mikewalsh720 on 2017-01-08
Hi everyone, I am currently using a desktop that has a Sapphire Radeon HD 7870 XT which uses the Tahiti LE chipset. When I first installed Ubuntu 16.04 I was having issues, basically the installer would get to a certain point and I would get a very pixelated screen with multiple colors. I then ran the installation with -nomodeset which appeared to work. I have (3) monitors (2 hooked up via minidisplayport and 1 hooked up via DVI. So I continued on by installing AMDGPU-PRO. This caused errors upon restart, putting my system into a login loop. 

Fast forward, it seemed like the only way to get the card working properly and to be able to use multiple monitors I would have to use fglrx. So I installed a fresh copy of Ubuntu 14.04.05 and hoped for the best. Still had to install using -nomodeset, but each time I tried to use fglrx  I was running into the same login loop issue. It's funny that I had all 3 monitors showing the login screen at this point but upon entering my password the screen would turn black then I would be taken back to the login screen. I most recently tried the method in the following link  [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide") to only get the same loop issue at login :( 

Is there anyone who has been through this issue that would be able to help me out? Thanks!

---

### Post by QIII on 2017-01-08
Hello!

Because 14.04.5 has some of the same graphics components as 16.04, it is not likely that fglrx will work with it.  AMDGPU may not yet support your graphics adapter.  It probably will eventually, since it is a GCN 1.0 card.

14.04 or 14.04.1 would be better choices if you want to use fglrx.

---

### Post by mikewalsh720 on 2017-01-08
Did not think about that, you brought up a good point. Will try with an earlier version of 14.04! Thanks!

---

### Post by mikewalsh720 on 2017-01-09
SOLVED: Downgraded to 14.04.01 and ran the following in the terminal>  apt-get update
apt-get install fglrx fglrx-amdcccle fglrx-dev
sudo reboot 

Upon restart all three screens appeared to be mirrored but working, was able to login and use Catalyst Control Center to adjust the monitors to my liking. 

Thanks again!

---

