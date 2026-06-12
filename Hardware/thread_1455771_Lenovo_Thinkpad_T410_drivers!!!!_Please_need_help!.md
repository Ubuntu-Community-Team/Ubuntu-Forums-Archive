---
title: "Lenovo Thinkpad T410 drivers!!!! Please need help!!!"
date: 2010-04-16
forum: Hardware
---

### Post by cwillygs on 2010-04-16
Hey guys I just got a new thinkpad t410. i am a total newbie of ubuntu and linux. i installed ubuntu 9.04 on it and dont know what kind of drivers i need for it. where do i go to see if there is a list of missing drivers like in window's device manager. how do i get drivers? 

here is my hardware components:

              45M4817  	SBB INTELCI5-520M2.40GHZ,3MBL3	 	 	 	 
 	      45M3092  	VBB GENWIN7HOMEPREM64	 	 	 	 
 	      60Y5846  	SBB GEN WIN 7 HM PR 64 US ENG	 	 	 	 
 	      45M4797  	SBB 14.1WXGA TFTW/LEDBACKLIGHT	 	 	 	 
 	      45M4788  	SBB IN.GR.M.A.5700MHD-AMT,TPM	 	 	 	 
 	      42X6306  	VBB 2GBPC3-8500 1067MHZ1DIMM	 	 	 	 
 	      45M4839  	SBB KEYBOARDUS ENGLISH	 	 	 	 
 	      45M4801  	SBB ULNAV(T.POINT+TOUCHPAD)	 	 	 	 
 	      45M4834  	SBB CAMERA SUBCARD	 	 	 	 
 	      45M4823  	SBB 250GB HARDDISKDRIVE5400RPM	 	 	 	 
 	      45M4820  	SBB DVDREC8XMAXD.L.U.SLIMS.ATA	 	 	 	 
 	      45M4816  	SBB 9CELLLI-ION BATTERY	 	 	 	 
 	      41W1787  	SBB CPK NORTH AMERICA	 	 	 	 
 	      44C8733  	SBB THINKPAD B/G/N	 	 	 	 
 	      45M4874  	SBB LANG.PACK US ENGLISH

I am a total newbie and i have no programming experience. i would really appreciated if anybody could elaborate on their instructions and tips. thanks a lot! seems nothing is working for me on ubuntu.

---

### Post by anthony_barker on 2010-04-26
In ubuntu most of the drivers should be there out of the box with the exception o f your wifi drivers

update-pciids
# lspci | egrep -i 'network|atheros|wireless'


[http://www.thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)

Does the video work ok?

Thanks

---

### Post by jwbaker on 2010-04-26
Everything should work fine out of the box.  If it appears to work, it is working.  There are not buried land mines like Windows' lack of IDE DMA or anything like that.  If you don't notice any problems, I would leave it alone.

Edit: Ignore the link above.  Your WiFi is a Realtek, not Atheros
Edit #2: Oh, I just noticed you are running 9.04.  You may have problems.  Personally I would install 10.04.

---

