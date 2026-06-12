---
title: "Upgraded to an FX 8350 now Ubuntu wont load up"
date: 2013-12-28
forum: Hardware
---

### Post by campcreekdude on 2013-12-28
I had an FX 4100 then all i did was a CPU upgrade to a FX 8350 and now ubuntu wont load.

i tried cleaning up packages in recovery after enabling networking in recovery mode.
Not working. 

I feel like Ubuntu is not good at upgrades. I had an issue on a different computer with a video card upgrade.
I didnt know what to do other than re-install it. SO what can I do?

---

### Post by JDorfler on 2013-12-28
This is odd.  I'm running an FX 8350 right now.  Have you checked your MoBo for updates?  If so, did you set your HDDs to boot in the exact same order as they were last time?

---

### Post by JDorfler on 2013-12-28
If you can get to at least the login I think if you hit Alt-F1 to get to the terminal.  If there, try
```
sudo aptitude reinstall linux-signed-generic
```

If aptitude isn't installed type
```
sudo apt-get install aptitude
```

Then enter
```
sudo aptitude reinstall linux-signed-generic
```

---

### Post by campcreekdude on 2013-12-28
I'll try it in a bit... thanks....... 

Edit:

It did not work. I loaded into recovery mode followed the instructions. (i enabled networking and write mode then keyed in the sudo). 

I cannot get to the input screen for password at all, before or after aptitude.

I have the latest BIOS.

---

### Post by JDorfler on 2013-12-29
Can you boot into a Live CD/DVD/Thumbdrive OS?

---

### Post by campcreekdude on 2013-12-29
Okay I have some more information.
I had my cosair link plugged in and that was causing my Windows XP install to have errors.
I have noticed before if I had a siatek gamepad plugged into my computer while Ubuntu Loads it would not load up.

Cosair Link is a fan/tempurature monitor for the H100i. Its probably not compatible with Ubuntu and most likely the cause for Ubuntu to not load.

What happens now when I try to enter Ubuntu after GRUB all that happens is a W and a wierd symbol in green after a purple screen.

So somehow I have to undue the damage that the Cosair Link did to my Ubuntu Install. I am pretty sure if I was not using the Cosair Link Ubuntu would probably load fine.

This is a different ball park now. I havent tried USB live stuff. I dont even know how to fix Ubuntu with any of that.

---

### Post by campcreekdude on 2013-12-30
Is there anyway to fix Ubuntu? I wish the CD download had some sort of Repair install.

---

### Post by campcreekdude on 2013-12-30
so i uninstalled my Graphics driver with sudo codes... and its booting now. I dont think it re-installed properly with generic amd drivers but its loaded and working. Typing from Ubuntu. Hopefully this works for a while now.

---

### Post by Bucky Ball on 2013-12-30
You may perhaps want to mark this thread as solved and post a new thread for any new issues (as they probably won't be related to the title of this thread). ;)

---

