---
title: "Video Card Driver Help"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by Fiki on 2007-08-05
I recently put together a computer with an Nvidia GeForce 8600 GT video card. I tried to install the ubuntu nvidia-glx driver through the synaptic package manager but it failed - I later realized this is because that driver does not support the 8600 GT. Is there any way to install a driver for this video card? I tried downloading the driver from the Nvidia website but I could not get out of Xserver to install it (I tried researching how to do it but no method worked, ctrl+alt+backspace logged me out but didnt get me out of X). I am also worried that the Nvidia website driver for linux won't support the 8600 GT either. Does anyone have any suggestions? I think I'm gonna cry.

Note: I'm using the latest version of Ubuntu Feisty

---

### Post by RevThain on 2007-08-05
I believe the answer is to install ENVY driver installer...

Problem is, the driver has a lot of dependencies that are not installed...

That solved my problem installing it.

---

### Post by RevThain on 2007-08-05
also... ENVY has dependencies as well, you can install those through adept package manager.

here is the link for ENVY:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by circuz_phreak on 2007-08-05
sudo /etc/init.d/gdm stop 

should exit x server completely, i believe you also have to be inside root to install the driver.  I'm in the same position but can't get anywhere untill i can mount my cd-rom drive.  I believe if you don't have the libc kernal headers you will have to download the package and use the cd you installed from, in order to finish the process of the libc package (which is where i get stuck, my cd rom isn't being read).  

sudo su -  (then enter password will give you root)

if all else fails boot in recovery mode so that way you are in command line as root, then to start x simply type "start x"

NVIDIA-Linux-x86-100.14.11-pkg1 is the current driver i THINK (not 100% sure), double check the website....and let me know if you find the right one (if the one i mentioned isn't it)....

Hope this helps.

p.s. don't forget, as root, you will have to navigate to the folder where your driver is installed....

---

### Post by Fiki on 2007-08-05
I tried Envy - I manually installed the latest Nvidia driver within Envy. When i rebooted Xserver didn't start and i got a blue screen error message that said it was not able to start. It said something about not detecting an Nvidia device compatible with the driver - it then gave me no access to terminal or any other means of input and at this point I have to re-install ubuntu (no big deal i didnt install anything else yet because i figured i would have to re-do it a dozen or so times in order to get the driver up and running). Got any ideas as to why this happened?

---

### Post by RevThain on 2007-08-05
After installing ubuntu, try immediately installing envy, and the driver... (any changes you made before trying envy could have caused a problem.)

Other than that, good luck, you'll find an answer, just hang in there. lol

I have found ubuntu to be quite finicky with nividia cards, but if you get it right, it works great.

---

