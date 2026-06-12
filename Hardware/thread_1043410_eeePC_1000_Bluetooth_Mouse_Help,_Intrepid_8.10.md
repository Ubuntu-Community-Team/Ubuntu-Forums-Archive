---
title: "eeePC 1000 Bluetooth Mouse Help, Intrepid 8.10"
date: 2009-01-18
forum: Hardware
---

### Post by physeetcosmo on 2009-01-18
Hello,

I am a newbie to Ubuntu. Could someone please help with bluetooth mouse setup? I have the array.org kernel installed for the eeepc which claims bluetooth support but I'm not sure if it works properly or not.

I can browse files on my phone, so I am assuming the bluetooth works.

My mouse is an IOGear GME228BW6, a simple three button w/ scroll wheel. It uses bluetooth interface. My mouse appeared in the "Setup New Device" window the first time I connected it. After a few minutes the mouse pointer moved around in a choppy manner and then stopped working.
The mouse has an 'auto power down' feature that requires the user to push any button to wake it up. Now, even after deleting the 'Known Paired Devices' from the Preferences page, my bluetooth "Setup New Device" doesn't detect the mouse.

Can anyone help me with commands/ ideas on how to debug this? Can I setup the bluetooth to auto reconnect to the mouse? My bluetooth is internal on the eeePC 1000, but it is controlled through the USB controller.

Thanks!:)

---

### Post by frenchrh on 2009-07-11
Same problem.

I have Ubuntu Netbook Release 9.04 on a ASUS Eee PC 1005HA and the IOgear bluetooth mouse.  and I can't see the bluetooth mouse in the setup new devices window.

any ideas?

---

### Post by tavern on 2009-09-27
I use Bluez for my bluetooth connections, i had to change the setting for "visibiltiy" to always visible for the mouse to work.

also ensure the computer's bluetooth is running before the mouse is turned on.

---

### Post by highflyer100 on 2009-09-27
[FONT=Verdana][SIZE=1]Hello, This is what I did to connect to my mouse in Jaunty.
Thanks to Eran Chinthaka, and Mad Max....[/SIZE][/FONT]

  	 	 	 	 	 	  [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*1. From terminal and type :*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000080][FONT=Verdana, sans-serif]*hcitool scan *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*You should see something like *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*Scanning ... *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*00:1D:D8:92:59:F6 Microsoft Bluetooth Notebook Mouse 5000 *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*Copy the hardware address found above.*[/FONT][/COLOR][/SIZE]
[SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*2. Go and edit hcid.conf , in Terminal type:*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000080][FONT=Verdana, sans-serif]*sudo gedit /etc/bluetooth/hcid.conf *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT] [SIZE=1]
[/SIZE] [/LEFT]
 [LEFT] [SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][COLOR=#dc2300]** Note ( A separate window will open in which you will do your edit. There may not be anything in this window....thats okay ) **[/COLOR][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*And put following at the end of that conf file. *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000080][FONT=Verdana, sans-serif]*device Hardware Address Here {name “Microsoft Bluetooth Notebook Mouse 5000”;}*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1]
[/SIZE] [/LEFT]
 [LEFT][SIZE=1][COLOR=#dc2300][FONT=Verdana, sans-serif]*example: device OO:1D:D8:92:37:DB {name “Microsoft Bluetooth Notebook Mouse”;}*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1]
[/SIZE] [/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*3. Save the file.*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*4. Restart the bluetooth system, in Terminal type:*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000080][FONT=Verdana, sans-serif]*sudo /etc/init.d/bluetooth restart *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*You should see some thing like *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]** Stopping bluetooth [ OK ] *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]** Starting bluetooth [ OK ] *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*5. Install the bluez-compat package from synaptic package manager.*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*6. Push the connect button on the mouse until the red/green light alternates. *[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*7. In Terminal type:  [COLOR=#000080]sudo hidd --search[/COLOR]*[/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif][/FONT][/COLOR][/SIZE][/LEFT]
 [LEFT][SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]*Search should start and connect to mouse!*[/FONT][/COLOR][/SIZE][/LEFT]

---

