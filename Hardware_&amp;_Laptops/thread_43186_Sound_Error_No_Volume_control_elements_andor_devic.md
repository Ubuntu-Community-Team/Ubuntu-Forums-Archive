---
title: "Sound Error: No Volume control elements and/or device found!!!"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by newbieOh on 2005-06-21
Hello to all,

I am a newbie to Linux and also to Ubuntu "Hoary Hedgehog" latest version.

I have successfully installed Ubuntu and running on my old AMD K6-2 machine.

However, there is no sound when running application like CD Player...etc.

I tried to open Volume Control and I get the following error:
-------------->>>**No volume control elements and/or devices found.**

Other error is opening Volume Monitor, it will give this error:
-------------->>>**Cannot connect to sound daemon.**
-------------->>>**Please run 'esd' at a command prompt.**

I have tried the command 'esd' at the terminal window but it gives this error:
-------------->>>**/dev/dsp:No such file or directory**

**My ISA sound card is ESS ES1869 Plug and Play AudioDrive (ISA)**

Please can anybody guide me in the configuation of this sound device issue?
Thanks in advance.  :neutral: 
Regards...

---

### Post by filemanager on 2005-07-12
I have the exact same problem. I'm running amd64, I have a SB Live! 24-bit sound card (and can't figure out how to install ca0106). I also have AC97 onboard sound (which is currently enabled, as disabling it doesn't help and I don't want my sound to turn off in WinXP)

---

### Post by MyBuntu on 2007-01-21
Could Be You Don't Have The Privileges 

Go To Systems And Administration User Rights And Groups
Click On The User Privileges Tab And Enable/check "use Audio Devices"

Hope For The Best

---

### Post by MyBuntu on 2007-01-21
Comment On My Previous Post:

Make Sure You Log Out And Then Log In Again

That Should Work 

And Remove Any Headphone 
And Disable Mute Button

---

