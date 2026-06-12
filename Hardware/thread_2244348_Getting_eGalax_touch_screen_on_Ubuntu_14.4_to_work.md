---
title: "Getting eGalax touch screen on Ubuntu 14.4 to work"
date: 2014-09-15
forum: Hardware
---

### Post by BartDG on 2014-09-15
Guys,

I'm a Linux newbie.  Worked with "that other OS" for 25 years, so I know my way around a computer.  <cough> :)

I've got a 15" touch screen ([This One)]("http://www.qnv.com/gestor/idioma/es/pdf/prod-513.pdf") I would like to get working with Ubuntu.  It basically uses an eGalax USB touch driver.  I've Googled around and found threads [like these]("http://ubuntuforums.org/showthread.php?t=1478877&page=4"), but unfortunately these solutions don't work anymore with the most recent Ubuntu version.  

The stupid part is Ubuntu sees the screen just fine.  It's just that I cannot get it to calibrate.  I've used "xinput_calibrator", but then the mouse gets stuck in the upper left corner and doesn't even move any more.  Nothing I've tried seems to be able to fix that.  I've found a Linux driver [here]("http://www.eeti.com.tw/LinuxDriverDownload.html"), but it's so incredibly cumbersome and complicated to install, I can't do it. (for one, it requires recompilation of the kernel :$ ).  I've also read something about an "evtouch" driver, but didn't succeed in installing it, let alone using it.

I DID get the screen calibrated and functional with my Raspberry Pi though, oddly enough.  I used raspbian and the "xinput_calibrator" command did the trick then.  I don't know why this doesn't work with Ubuntu 14.04 (or Mint 17, tried that as well)

The only thing left for me to do seems to either install Ubuntu 10.04 and use the fixes presented in the threads I've linked to above, OR buy a Windows licence, which I believe would be a crying shame.

Could somebody please help me?

Thanks!!

---

### Post by gtronick on 2015-05-22
Hi, i have the same problem on Kubuntu 14.04 x64, i have bought a LCD monitor from Neway, and it comes with eGalax touchscreen technology. I have tried with the driver included in the miniCD they provide, also, i have followed the guide but i can't make it to work. After the first touch, the pointer stucks on the upper left corner of the screen. I have also read about here: [https://docs.google.com/document/d/1G4oD6Y8vlyNHW6wJT89pxcjWHoETLLT-SEoAIW6_7Xc/pub](https://docs.google.com/document/d/1G4oD6Y8vlyNHW6wJT89pxcjWHoETLLT-SEoAIW6_7Xc/pub) and followed all steps without success. When i open the eGTouchU application, i can see the device connected to hidraw1, but the model and the version are unreachable. Hope somebody help us :(

---

### Post by gtronick on 2015-06-09
Well, after many time, we have not response. I keep fighting with this. I'm talking to the Neway company, who sell me the LCD with the eGalax touchscreen device incorporated into the main board. Their engineer is working with Cubieboard and Linux 3.0.1 and seems that the Touchscreen is fully working for him. But, as expected, this does not work for me, because the Linux 3.13.0-53 which i have installed, is many different to the Linux 3.0.1 Kernel. I hope, Neway and me, find a definitely solution for this. Just, keep fighting. ;)

---

### Post by Tyler_Wyant on 2015-07-06
I feel like I'm an experienced Linux user and I have tried installing my eGalax touch screen on Arch, Debian and now Ubuntu. Nothing seems to work. The drivers are out of date and xinput just puts me in a corner and I'm stuck there. If I don't calibrate it at default, my ups and downs are my rights and lefts, vice versa. If this was solved here it would really help me out also.

---

### Post by Tyler_Wyant on 2015-07-17
Here everyone This was released.
[https://docs.google.com/document/d/1G4oD6Y8vlyNHW6wJT89pxcjWHoETLLT-SEoAIW6_7Xc/pub](https://docs.google.com/document/d/1G4oD6Y8vlyNHW6wJT89pxcjWHoETLLT-SEoAIW6_7Xc/pub)

Wile doing this I had trouble with getting the service to start. If you have this problem try this. 
Go to the file that we moved into /usr/local/bin and right click it then click properties. It was there I able to make it executable by clicking the check box under the tab Permissions. Then it worked!

Tip from a nerd girl ~_^

---

