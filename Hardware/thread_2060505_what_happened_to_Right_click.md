---
title: "what happened to Right click"
date: 2012-09-20
forum: Hardware
---

### Post by buddajah on 2012-09-20
Laptop = acer timeline U M5 481T-6670

Problem = no right click for click pad

mouse = Elantech 

tried :
1. [http://askubuntu.com/questions/151375/righ-click-doesnt-work-on-an-elantech-touchpad](http://askubuntu.com/questions/151375/righ-click-doesnt-work-on-an-elantech-touchpad)
2. [http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html](http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html)
3. [https://wiki.ubuntu.com/DebuggingTouchpadDetection#Enabling_right_button_click_for_clickpads_on_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/DebuggingTouchpadDetection#Enabling_right_button_click_for_clickpads_on_Ubuntu_12.04_LTS)
4. [https://wiki.ubuntu.com/DebuggingTouchpadDetection?action=AttachFile&do=view&target=enable-rightbutton.sh](https://wiki.ubuntu.com/DebuggingTouchpadDetection?action=AttachFile&do=view&target=enable-rightbutton.sh)

# xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                      	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=14	[slave  keyboard (3)]

# ./enable-rightbutton.sh 13|ETPS/2 Elantech Touchpad
-bash: ETPS/2: No such file or directory
property Synaptics Right Button Area doesn't exist, you need to specify its type and format


how do i make this work ?

---

### Post by buddajah on 2012-09-20
looks like there is a 2 finger tap gesture to mimic right click... i would still prefer a right click or an upper right corner tap (single finger) for a right click if someone can tell me how that can be done ?

---

