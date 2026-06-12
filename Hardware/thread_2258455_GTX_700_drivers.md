---
title: "GTX 700 drivers"
date: 2014-12-27
forum: Hardware
---

### Post by mr-voorhees on 2014-12-27
I'm running a Geforce GTX 700 series on Ubuntu 14.04. Just recently I  downloaded a game and tried to play it only for the error "opengl 4.0 or  later cannot be found. please make sure that your video card and driver  support OpenGL 4.0" I checked and (of course) video card does so i  figured it must be a problem with the driver.
I downloaded the driver from this site but when i opened it I got the  message "The file you opened has some invalid characters. If you  continue editing this file you could corrupt this document.
You can also choose another character encoding and try again." I've  tried both character encodings I have available, redownloading, and  restarting my computer but it still won't run, does anyone have any  suggestions? thanks

---

### Post by barkerson on 2014-12-28
You should instead of download drivers from nvidias website download them from ubuntus own drivers list.
Go to Applications(top left corner), System Tools, Preferences, and Additional drivers. There you should find drivers for your card, being able to use the desktop at all usually means the nouveau drivers are in use. If there are drivers listed you should choose the latest proprietary drivers, that should be fine.

If no drivers are listed you should follow the instructions [here]("http://ubuntuhandbook.org/index.php/2014/01/install-nvidia-driver-331-38-ubuntu/")
I could try to help you if you encounter any errors if you have to do this.

---

### Post by Yellow Pasque on 2014-12-28
Ubuntu is not doing a good job of keeping their nvidia drivers up to date. Easy way to install nvidia drivers for recent cards is to add a PPA like so:
```
sudo apt-add-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get install nvidia-346
```

---

