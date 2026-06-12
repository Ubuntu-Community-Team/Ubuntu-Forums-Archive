---
title: "How to turn off camera pop up?"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by TheOtherLinuxFreak on 2007-12-19
how can I turn off the pop up that makes me import my photos. when I plug in my camera, the import photo dialog pops up and it trys to load the drivers but it cant. Then it freezes up and i have to use xkill to end it. then The camera is not mounted so I cant use Picasa to import the pictures. I don't want it to recognize the camera as a camera but recognize it as a flash drive. The camera is a panasonic DMC-LZ3. Or, does anyone know where to get drivers for this camera? 

Thanks for your help!

---

### Post by timcredible on 2007-12-19
the 'driver' is already there or it wouldn't be recognized.  the 'driver' is really just a text file with the vendor/make ID numbers that specify what the device is.  what's happening is that HAL (Hardware Abstraction Layer) is seeing your camera, it checks files for the matching vendor/make ID info, and the files say it's a camera, so in ubuntu the default action for a camera is to launch f-spot.  if you want it to be mounted the same as a flash drive, you're going to have to find out which file has the vendor/make ID match and change that file so that HAL mounts the camera as a removable media.  i tracked down these files once several years ago to add a camera that wasn't in the default database, but I don't remember where the files are, so you'll have to do some searching.  fwiw, why not just let f-spot or digikam load the pictures?

---

### Post by TheOtherLinuxFreak on 2007-12-19
when fspot loads the camera it freezes and when I use xkill to end the program, the camera is no longer mounted. also this is my parents pc and they want to use picasa.

EDIT:I fspot wasn't the program that tried to load the camera. I uninstalled fspot and now when I plug in my camera This pops up. (see attachment) That is what freezes and after I exit that with xkill, the disk is not mounted. how do I uninstall that?

---

### Post by TheOtherLinuxFreak on 2007-12-21
anyone?

---

