---
title: "ETPS/2 Elantouch Touchpad not working"
date: 2014-12-07
forum: Hardware
---

### Post by backdoorbobby on 2014-12-07
Hello, everybody.
I bought an ASUS TP500L series laptop on Black Friday. I also purchased an SSD to replace the hard drive inside of it, and did so. I installed Windows 8 alongside Ubuntu on the drive and after downloading a few drivers on Windows 8, everything worked perfectly. The same with Ubuntu, but before and after installing drivers, the touchpad will not work. 
Here is the output of xinput 

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller    id=10    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Wireless Mouse            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard

I did find a few different posts on various websites about the same model having the same exact problem but none of them were provided a working solution. I'd be more than happy to provide any more information if anyone can find the problem.

---

### Post by area51pilot on 2014-12-16
> **backdoorbobby said:**
> Hello, everybody.
I bought an ASUS TP500L series laptop on Black Friday. I also purchased an SSD to replace the hard drive inside of it, and did so. I installed Windows 8 alongside Ubuntu on the drive and after downloading a few drivers on Windows 8, everything worked perfectly. The same with Ubuntu, but before and after installing drivers, the touchpad will not work. 
Here is the output of xinput 

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller    id=10    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Wireless Mouse            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard

I did find a few different posts on various websites about the same model having the same exact problem but none of them were provided a working solution. I'd be more than happy to provide any more information if anyone can find the problem.

Mine has the same issue, no Bluetooth either. I was only able to get the touchpad to work as a basic mouse (point/click ... no gestures or scrolling). Here are my posts: [https://answers.launchpad.net/ubuntu/+question/257520](https://answers.launchpad.net/ubuntu/+question/257520) & [https://answers.launchpad.net/ubuntu/+question/257523](https://answers.launchpad.net/ubuntu/+question/257523)   These issues still persist. Im on the latest kernel (3.18)

---

### Post by solo2 on 2015-03-01
[**[COLOR=#000000]solo2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1970621") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]  					 					 						First Cup of Ubuntu 					 					 						[IMG]http://ubuntuforums.org/images/rank_1.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateFeb 2015Beans1 					 					 				
 			 		
 	  	 		 		 		 		[h=2]Re: i8042 - Asus X450LN (R409) - touchpad is missing after suspend[/h] 		 				 				 					 				 		 			 				[INDENT] 					I Had same problem with Asus x501u....
saw this somewhere, so not taking credit if it works...
"There's a nice graphical tool that alows you to simply enable and disable the touchpad. 
You can install it by typing on a console:



sudo add-apt-repository ppa:atareao/atareao

sudo apt-get update

sudo apt-get install touchpad-indicator



   
 
You can try to enable it from the System Settings

 
   
You can try running from the console synclient TouchpadOff=0
        

sudo gedit /etc/rc.local Before the line exit 0 you will add the following lines

:

sudo modprobe -r psmouse

sudo modprobe psmouse proto=imps

Save the file and reboot the computer" 				[/INDENT]

---

