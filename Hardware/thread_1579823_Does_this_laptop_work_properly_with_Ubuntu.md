---
title: "Does this laptop work properly with Ubuntu?"
date: 2010-09-22
forum: Hardware
---

### Post by anchorschmidt on 2010-09-22
I recently had a bad experience with one of the lenovo laptops (thinkpad edge AMD chip) as it did not support wireless on Ubuntu. I tried the suggestions on the forum and they did not work. Now I am thinking of buying another lenovo laptop (U350)

[http://www.cyberport.de/notebook/notebooks/notebook-berater/1C31-12C/lenovo-ideapad-u350-m22eqge---subnotebookhit.html](http://www.cyberport.de/notebook/notebooks/notebook-berater/1C31-12C/lenovo-ideapad-u350-m22eqge---subnotebookhit.html)

In another thread that I read, it seemed that the wireless problem only existed on the laptops with the AMD chip. This one has an intel chip but all the same I would like to be sure. Can anyone confirm that Ubuntu works properly with this machine?
Thank you.

---

### Post by avongil on 2012-06-30
This is an old thread but I would like to comment on the U350.  
It&#347; fantastic, and a bargain now since they did not sell well.  

Works great with xubuntu 12.04. 
Everything seems to be working well.

A few things must be done:

1 - install laptop mode tools. It uses 15 watts , when laptop mode tools are installed it will use around 8. Battery last 4 or 8 hours depending on 8 cell or 4 cell.
with with powertop utility.  

Install tools:
sudo apt-get install laptop-mode-tools

Install power monitor:
sudo apt-get install powertop

One must modify USB auto suspend if you use a mouse.  The mouse will turn off in a few seconds and is very annoying. You may also just white list it instead. To do either edit the usb auto suspend config file.

gedit /etc/laptop-mode/conf.d/usb-autosuspend.conf

2 - The fan is a bit too loud. Some early U350s have had stickers placed between the heat sink and the processor. Mine did not but I took it apart and cleaned the fan and processor. It&#347; not so easy to take these apart so put aside 2 hours or so.

The fan speed can be tweaked with a bios update that was hacked by a user named  					 			 											 				 					 							 		 	 	 	 			 				 			 		 			[middleton]("https://forums.lenovo.com/t5/user/viewprofilepage/user-id/53489").  Thank you sir!  After installing this (requires windows so do this before installing ubuntu) 		 		 		 			 		 		 		 		 	 			 		 

[https://forums.lenovo.com/t5/IdeaPad-Y-U-V-and-Z-series/Ideapad-U350-Fan-Control-Speed/td-p/174840/page/6](https://forums.lenovo.com/t5/IdeaPad-Y-U-V-and-Z-series/Ideapad-U350-Fan-Control-Speed/td-p/174840/page/6)

 					 			 											 				 					 							 		 	 	 	 			 				 			 		 			[middleton]("http://forums.lenovo.com/t5/user/viewprofilepage/user-id/53489")

Rev 5 of BIOS:
		 		 		 			 		 		 		 		 	 			 		 
 							 															 		 			 				 			
 		
 	 
 				
 			 
			 		
			 			Here is the link to the latest version of my patch: [Download.]("http://www.mediafire.com/file/m8pm3kya57kbr63/04E0_04E0_04E0_04E0_04E0_Reduced_Fan_Speed_Lenovo_U350_BIOS_1CCN26WW.rar")
 Special version of BIOS:

**UPDATE: **I added CTRL-FN swap and disabled whitelist of wireless adapters. You can find this BIOS version [here.]("http://forums.lenovo.com/t5/IdeaPad-Y-U-B-V-and-Z-series/Ideapad-U350-Fan-Control-Speed/m-p/315340#M29688")
 			 			 				 			 		
 		 		 		 		 		 		 		 	 
 				 				 				 			 
			 		
		 	


---


Thats it, if you do these two things the U350 is quite an awesome and svelte laptop. 
XUbuntu 12.04 runs like a champ. I have not tested unity or gnome 3 or kde, but I suspect there will be no issues.

---

### Post by avongil on 2012-07-08
After the bios Update and an SSD, this laptop is virtually silent!
Camera and Audio in/out work perfectly.

Only ports left to test are the SD and HDMI, will update some time soon, but I suspect they work well.

---

### Post by avongil on 2012-07-15
Update:

Moved on to LXDE. 6W power consumption at idle vs 8.  Everything works well, including audio In after installing pulsaudio and its control panel.

I'm so much happier with LXDE!


sudo apt-get install pulseaudio pavucontrol

---

