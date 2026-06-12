---
title: "Nvidia Driver"
date: 2013-05-30
forum: Hardware
---

### Post by telleri on 2013-05-30
Hello dear developers.
 
Can you please provide the Nvidia driver 173.14.37 with the functioning adjustable nvidia-settings for precise pangolin and the following versions in the repository? For the graphics card NVIDIA GeForce FX 5500?

If that is so then, I ask for feedback.

 I come from Germany.

 Since my English is not good, I use the google translator.
In the German forum I was told I should try it here.
Please move my question in the right forum, I should be wrong here.

                        
Many thanks in advance.
Telleri

   
Many thanks in advance.
Telleri

---

### Post by papibe on 2013-05-30
Hi telleri. Welcome to the forum ):P

The driver you are looking for is available in the repositories as a meta package named 'nvidia-173'.

You can open the 'Software Center' and install it from there, or you can do it in the terminal by running:
```
sudo apt-get install nvidia-173
```
You may need to reboot in order to take effect.

Let us know how the installation goes.

Come here often, and have fun.
Regards.

---

### Post by telleri on 2013-05-31
Hi pabibe.

Wonderful, but I only have the problem that apparently an incompatible version of nvidia-settings will be offered with the driver 173.14.37.
Nvidia-settings because you can no longer set since the last security update from nvidia:
- X Server Color Correction
-Digital Vibrance
-Image Sharpening
So please be my offer to the developer to an adjustable driver 173.14.37 nvidia-settings with the repository.

---

### Post by Yellow Pasque on 2013-05-31
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1100994](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1100994)

---

