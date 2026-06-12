---
title: "ubuntu slower than windows xp??"
date: 2009-01-21
forum: Hardware
---

### Post by elliottj85 on 2009-01-21
Hi,
I've been messing around with ubuntu for a couple of months now and theres still a couple of things I can't get to work.

My main problem is that programs that ran smoothly such as google earth, under windows, are now very slow and sluggish.

I'm using an old sony vaio pcg-fx602
ubuntu intrepid
the graphics card is an ati rage mobilty with 8mb

direct rendering is enabled but im only getting 200-300 fps in glxgears, someone with a similar card was up to about a thousand I believe.

could someone give me some very simple instructions to get my 3d abilities up to speed.

thank you!!!

---

### Post by chinakr on 2009-01-24
It must be a 3D driver's related problem.
Just wait for the new version of the 3D driver.

---

### Post by fland on 2009-01-24
> **chinakr said:**
> It must be a 3D driver's related problem.
Just wait for the new version of the 3D driver.
new driver for such old video? Good joke. About what is slower - ubuntu or XP I can say just that Ubuntu needs more RAM for running same number or programs at the same time then XP, but under Ubuntu we get more aesthetically pleasing set of effects and stable working.

---

### Post by jmate24 on 2009-01-24
shut of tracker and indexing. and the rest of the apps so that ubuntu can load faster and use less CPU and memory. But if you intend on using one of these apps then do not uncheck the box.

system>preferences>search and indexing, uncheck 'enable indexing' and 'enable watching' and check 'disable all indexing on battery' and 'disable initial index sweep while on battery'

then go to:

system>preferences>sessions and uncheck 'beagle search daemon', 'beagle search tool', 'blueproximity', 'bluetooth manager' (if you don't plan on using bluetooth or if your hardware does not support it), 'check for new hardware drivers' (if you don't have a nvidia video card and the installation of ubuntu went fine and you were able to load the X server and GDM), 'evolution alarm notifier' (if you don't plan on using evolution), 'gnome logon sound', 'gnome splash screen' (these are not really necessary), 'remote desktop', and if you are not visually, mentally, physically, or hearing impaired then uncheck 'visual assistance'

next:

system> administration> services and uncheck 'bluetooth device management', 'folder sharing service' (if you do not plan on using SAMBA or SMB), 'audio settings management' (if not already unchecked), 'bluetooth device management' (again if not using bluetooth or if your hardware does not support it), 'braille display management'(if you are not visually impaired (it should be unchecked already)), and 'cpu frequency manager'

then:
accessories>terminal
then type or copy & paste then press enter:
```
sudo apt-get install sensors* && sudo apt-get install libsensors4 && sudo apt-get install libsensors* && sudo apt-get install lm-sensors
```

finally go to:
system> administration> services and make sure that these are checked (enabled) 'hardware monitor (lm-sensors)' and 'hardware monitor (sensord)

next: right click on an empty space of the panel and chose 'add to panel'
then scroll down and find 'cpu freqency scaling montor' and click on it then click 'add' then scroll down a little more until you find 'hardware sensors monitor' and click on it then click 'add'

last of all: reboot if you want. i did not have to but i would recommend it.

jmate24

---

### Post by AlexBellisBrown on 2009-01-24
The only thing i notice that starts sloweris firefox, but once its started, shut, then started again, its much faster. Its only a matter of seconds, so it doesnt matter much. I heard on the "grape vine" that its not JUST the boot times they want to improve in 9.04, but everything else as well. Eg; Nautilus, Menus, Etc...

---

