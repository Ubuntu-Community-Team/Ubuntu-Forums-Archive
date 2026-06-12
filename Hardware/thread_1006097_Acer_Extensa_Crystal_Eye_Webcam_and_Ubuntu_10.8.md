---
title: "Acer Extensa Crystal Eye Webcam and Ubuntu 10.8"
date: 2008-12-08
forum: Hardware
---

### Post by J_Boi on 2008-12-08
I've got a Acer Extensa 4620z laptop running ubuntu-8.10-desktop-i386 and I've looked all around because I'm having trouble with my crystal eye webcam. The green light shows up when I run Ekiga, but I only get a green screen and no image. The mic works fine but the camera isn't. I've searched up and down on google and here and so far nothing. I've also tried the linux-uvc.tar.gz and this:
> Usage notes:

- download the files to your desktop
- extract the files (right-click the icon and click extract here (or something like that, I'm not sure since I have localized version))
- open console (ALT+F2 (to run a program) than enter "gnome-terminal" without the quotes)
- now go to your Desktop directory from console: "cd ~/Desktop" (without the quotes again, mind the capitalisation/case and notice that it might be called something else if you have a localized (non-english) version, type "ls" in console to check up - it will list all non-hidden directories and files there are)
- now go into the linux-uvc directory: "cd linux-uvc", or what ever it is called if you renamed it
- now enter the following commands:
Code:

./svn-version.sh
sudo make
sudo make install

It _should_ be installed now, unless you got some errors/mistakes in the proccess (or I wrote something wrong). Try restarting if it's not working. If it's not working after a restart, there's some problem. Possible causes might be: you have a diffrent webcam from mine, you don't have build-essential package installed (you can install it throught System -> Administration -> Synaptic), something else?

When I type ./svn-version.sh in terminal I get and error of permission denied.
Any help would be greatly appreciated.

---

### Post by J_Boi on 2008-12-12
Anybody??

---

### Post by krisstaar on 2008-12-16
I've got an Acer 5720z and had the same problem. My crystal Eye didn't work in either Ekiga, aMSN or Cheese...

I haven't found a firm solution but I found a workaround:
In Cheese, I changed the Resolution in Settings from 640 x 480 to 176 x 144. I was then able to retrive a low-res, pixelated image. Nonetheless, it's better than no image at all.

Hope this helps. O:)
I'd appreciate a notice if you come over a proper fix.

---

### Post by scunn77 on 2008-12-23
did you try entering "sudo ./svn-version.sh"  ?  I'm not exactly sure what you're trying to do based on your quote there, but if you don't have permission, you probably need to log in as super user (the 'sudo' part).  

I haven't tried Ekiga at all, though I did install Cheese on my 4620z and it worked  just fine (well, mostly - it's seems a little buggy).  I don't think you can use it for web-conferencing though - at least my version has very limited functionality.

---

