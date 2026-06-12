---
title: "Logitech Mediaplay Cordless mouse in Ubuntu Intrepid Ibex"
date: 2009-01-18
forum: Hardware
---

### Post by rocketsquash on 2009-01-18
Hey, for those of who who wanna get ur Logitech mediaplay cordless mouse working with intrepid and amarok, follow this guide:

1. Download the Logitech Mediaplay cordless mouse drivers from [_[COLOR="Blue"]here[/COLOR]_]("http://daemon.prozone.org/%7Edavid/projects/lmpcm_usb/lmpcm_usb-0.5.7.tar.gz")

2. Untar the downloaded file
```
 tar zxf lmpcm_usb-0.5.7.tar.gz 
```

3. Go to the directory and install the drivers
```
 cd lmpcm_usb-0.5.7
 sudo make
 sudo make install
```

4. Change directory to /lib/modules/your-kernel-version

5. Copy and paste modules.dep to ur desktop just in case something goes wrong

6. sudo gedit /lib/modules/your-kernel-version/modules.dep

7. Remove *usbmouse* and *usbhid* entries and then save modules.dep 

8. Enter the following commands to get rid of the currently loaded generic modules and to load the new Logitech Mediaplay module:

```
 sudo rmmod usbmouse
 sudo rmmod usbhid
 sudo modprobe lmpcm_usb
```

9. My mouse didnt work once i executed these lines, so i removed the usb receiver and then my mouse worked again, with all the mediaplay buttons working!!!

10. So when u restart ur computer the mediaplay buttons wont work until u enter the code from step 8, which is quite a schlep everytime u boot up, so why not run these commands automatically upon startup?

11. To run the commands automatically upon startup, create a file *mouse.sh* in */home/your-username/* and paste the following code inside ur newly created file:

```
#!/bin/sh
sudo rmmod usbhid
sudo modprobe lmpcm_usb
```

12. Make sure this file executable: 

```
sudo chmod +x mouse.sh
```
or simply right click on the file, click properties, then click on the permissions tab, and then make sure the "Allow executing file as program" check-box is ticked.

13. Then to make this script run on startup, edit the file */etc/rc.local* in gedit as follows:

```
sudo gedit /etc/rc.local

``` and then include the following line above the exit 0:

```
/home/your-username/mouse.sh

```

14. Reboot ur machine and the script will automatically load and ul be able to use the mediaplay buttons on ur mouse! To get these to work in Amarok, just click on Settings -> Configure Global Shortcuts, and then simply assign ur mediaplay buttons to the appropriate function.

15. Enjoy!

---

### Post by dsnoeck on 2009-03-03
Hi rocketsquash,

and thanks for your tutorial. I can now user my MediaPlay Logitech mouse. But my external keyboard stop working. So in the module.dep files, I restored the two lines that contains *usbhid*. Now my keyboard and my mouse are working nice.

Cheers,
Damien

---

### Post by Ultimateswan on 2009-04-13
Thanks a lot ! =D>
I was looking for this trick !

Very simple and work great ! :D

For user who use other USB peripheral, watch out when you delete lines with usbhid. :D

---

### Post by martini1179 on 2009-12-16
I'd just like to point out that you can get all of your Mediaplay mouse's buttons working in a much more noob-friendly way by downloading Easystroke [[http://easystroke.sourceforge.net/]](http://easystroke.sourceforge.net/])

It's primarily a systemwide mouse gesture app, but it can also be used to assign different functions to individual buttons without messing with drivers. 

Assuming your keyboard has multimedia keys, it's a pretty straightforward process.


**INSTRUCTIONS**: 

1) After installing Easystroke to your PPA, open it. 

2) Go to your Preferences tab, click on the Additional Buttons dropdown arrow. 

3) Click add, and then add individual buttons by clicking them. 

4) Then, for each button you want to configure, go to the Actions tab and click Add Action. "Gesture" is the name of the action, for example play/pause, volume up, etc., depending on the key. 

5) For "Command," chose "Key." When it asks you to enter a Key Combination, simply hit the keyboard multimedia key that corresponds to the key on your mouse. Save it. 

When configuring each button, I'd do this one by one so that you remember which button is "Button 13," for example, under Additional Buttons in Step 3.

---

