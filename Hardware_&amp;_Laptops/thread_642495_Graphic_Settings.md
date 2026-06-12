---
title: "Graphic Settings?"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by Eagleguy125 on 2007-12-16
When I boot up Ubuntu (7.10), I always get the warning message for Low Graphics Mode. So, every time, I configure Monitor 1 to be the Dell 773c that it is, running at 1280x1024 at 60Hz, and my graphics card as a Radeon (Specifically, a Diamond 1950x). Everything seems to be set up correctly. However, after briefly snapping to the correct resolution, I reach the Ubuntu login screen, and I can't help but notice that the system is giving me 800x600 pixels... I login, make it to the desktop, and can change the settings--Which require a logout to perform. However, because the OS is installed on an external hard drive, anything from a logout to a hibernation equals a shutdown. (Thank you Dell BIOS.) To cut a long story short, any changing of settings is reset. Perhaps I need to save them somewhere? The save function at the top of the menu requires a location to be given--But not amount of tinkering with that menu has let me save anything. I always get an error message telling me that the location I entered is invalid.

Note: Now that I've gone and written this post, I went to grab the error message from the Screens and Graphics admin menu, and the menu has changed a bit. Now, my monitor isn't *allowed* to be set over 800x600 (I run it on my XP Pro partition all the time at 1280x1024), and I apparently have not two, but three graphics devices. (The onboard, the video card, and whatever the new thing is.) Can somebody help me with this strange problem?

---

### Post by Orfintain on 2007-12-21
I have something similar going on.

Dell Inspiron 600m Radeon RV250 Mobility Fire GL 9000
Gusty 7.1

While the resolution worked fine on the live version once I installed and rebooted I can't get Linux out of ~800X600.
Accept during login and live editions...

---

### Post by CityofAsh on 2007-12-21
Distro: Gusty 7.1
Monitor: Samsung 22" 226bw
Max resolution: 1680 x 1050
Video: Nvidia 6 Series 6500

I am having the same exact problem. Saving the settings in the configuration doesn't matter. i just typed /home/'my user' and saved it there. all it allows you to do is load the settings you saved again.

I installed the latest Nvidia drivers. I reboot and get the low graphics mode and set up my monitor there. Once the welcome screen appears it is back to 800 x 600 resolution. Once i login to gnome i use sudo nvidia-settings and it gives me an error saying the drivers are not installed to run xorg-config and reboot. Once i do his i am back to step 1. I tried this both with the Nvidia Restricted Kernal Driver installed and uninstalled. 
Also after killing XDM and installing the Nvidia driver  i cannot just startx at terminal anymore. Have to reboot every time.

 I had a bad feeling about the Gusty distro upgrade.

Any ideas anyone?

~City

---

### Post by Orfintain on 2007-12-22
I figured out how to change my resolution but I still can't get any normal effects and I have to tell it what drivers to use ever reboot

---

### Post by Orfintain on 2007-12-28
@Eagleguy125  ...try useing fglrx drivers

I still have to set it at every boot up but at least i can function in normal resolution



also anyone who is haveing to do this are you haveing trouble VM ware?

---

