---
title: "New Samsung laser printer not printing"
date: 2011-04-01
forum: Hardware
---

### Post by reddleman79 on 2011-04-01
I would be grateful for any help getting my Samsung ML-1665 printing from my Lenovo B550 running Ubunto 10.10. All looks well when checking the printer queue but the printer just blinks when I send a print command from the open office application. I know the printer works because I installed it on my other computer which runs WinXP. Any suggestions? Thanks

---

### Post by dadman77 on 2011-04-01
You didn't mention how you are connecting to the printer. Is it a network or USB connection? I use a Samsung ML-1740 on 10.04 and serve it up to my home network via Samba, so I can print from Windows XP/Vista or Ubuntu. Maybe it's a driver issue, there are several available under Ubuntu.

---

### Post by reddleman79 on 2011-04-02
I am using a USB connection and the default driver which I was prompted to use during the setup. No error messages are given by the computer during the printing process.

---

### Post by AlexDudko on 2011-04-02
This printer is not working with default drivers. 
Look [here]("http://www.openprinting.org/printer/Samsung/Samsung-ML-1665") for some additional information.
You need **20070725085320093_UnifiedLinuxDriver.tar.gz** package to be installed to make it work. 
Since Linux drivers were removed from Samsung official web site simply google for it.

---

### Post by reddleman79 on 2011-04-11
Haven't tried that yet but did try more of the built in drivers and managed to get the printer to feed the paper through without any print on it. I think that willl have to be the next plan.

---

