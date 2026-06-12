---
title: "Nvidia Geforce 6200 driver install"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by seiferkai on 2006-08-12
can someone please tell me in laymans terms on how to install this?

NVIDIA-Linux-x86-1.0-8762-pkg1.run

they say do some sh code to extract but they dont say where, or how to do it for the beginners..

---

### Post by halfvolle melk on 2006-08-12
You could also grab the ones from the repo's. Open a terminal and run
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```
close all programs, press ctrl+alt+backspace and log in again.

edit:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by seiferkai on 2006-08-12
thanks that actually helped...

---

### Post by Andrew Pape on 2007-02-21
I also have run intro trouble installing the nVidia Geforce 6200 driver. When X Windows starts and I try to run the driver, with the command:

sh NVIDIA-Linux-x86-1.0-8762-pkg1.run

I get an error message like: "You appear to be running an x server, please close it". I've gone to a plain text console with CTRL-ALT-F1, but I get the same error, ie, that x windows is still running and needs to be closed.

I decided to boot in recovery mode so that x windows wouldn't start. This gave a different error message when I tried to install the driver: "You appear to be running in run level 1; this may cause problems... recommended that you quit installation now and switch to run level 3 ('telinit 3') before installing. Quit installation now yes/no?".

If I quit the installation and run telinit 3, I get back to the ubuntu screen and hence into x windows, which leaves me with the original problem. On the other hand, if I try to continue the installation, I get a message about the internet, and I cannot proceed because I don't have the internet working with Linux. (The internet only works with Windows because of my wireless hardware).

I have tried the command: sudo apt-get install nvidia-glx nvidia-kernel-common
as given in this thread, but that too has failed, giving me an error that "... the package is missing, has been obsoleted, or is only available from another source..."

Can someone please help me with installing the nVidia driver? I'm pretty new to Linux; I may have overlooked something obvious, so sorry if I have.

Regards,

Andrew.

---

### Post by Rinias on 2007-02-21
Hi,

If you are trying to get into init 3 (which is the system running on single user as opposed to init 5 which is mutliuser and what is starting your GUI) what you should do is start up you system normally into the graphical mode (yes, x has been started) but no need to login (even if you do, it shouldn't make any difference). Afterwards you switch over to TTY 1 (or 2 or 3 or whatever) with your Ctrl-Alt-F1 (or F2 or F3 or whatever- but less than 7). This should give you a login prompt. You need to login to the console and then do a sudo telinit 3 which should spit something out to the effect that the system is going into single user mode or to init 3 or whatever. 

I'm not sure of the code telinit - on other systems it's simply init (eg, init 3)... 

Afterwards you should be able to do a sudo sh ./NVIDIA-Linux-blah-blah.run from the directory where you have the file...

Hope this helps a bit,

Rinias

---

### Post by r4ik on 2007-02-21
Or just use Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by Rinias on 2007-02-21
> **r4ik said:**
> Or just use Envy 


I'd have to agree with that... Of course, it doesn't hurt to actually know how to do it ;)

But then again, I am a **Slacker** :)

Rinias

---

### Post by Andrew Pape on 2007-02-22
Hi Rinias,

thanks for the quick reply, but unfortunately I'm still stuck with installing the nVidia driver.

I followed your instructions:

".. This should give you a login prompt. You need to login to the console and then do a sudo telinit 3 which should spit something out to the effect that the system is going into single user mode or to init 3 or whatever."

After issuing the instruction above, for some reason I get no message on the console. Instead, I just get another prompt, and then when I proceed to run the driver, I get the same error message, ie that I'm still in x server mode and need to get out.
I have tried logging into the console both as my normal user name, and as root, but the effect has been the same.

>I'm not sure of the code telinit - on other systems it's simply init (eg, init 3)...

I tried "init 3" instead, but got the same result: just another prompt, as if the instruction did nothing.

>Or just use Envy

I checked out the Envy website, but it doesn't seem to be the best solution for me because it requires an internet connection. I do have one, but only in Windows. I think it'd be a problem to get my hardware to work with Linux. My modem router came with a Windows disc, although I admit I haven't checked for a Linux driver. Also, I'm using a wireless router, which should work for Linux as it uses TCP/IP, but the computer connection hardware seems to be made for Windows only. I'll look into that, but I think I've got a better chance of installing the nVidia driver, as I have it already, and I feel I just need a magic Linux command to get the driver working. I'm "envious" of those of you Linux users who have internet connections and can run Envy, as it sounds like a great program.

I'm new to ubuntu, so again I may have overlooked something. It seems that I'm getting stuck in x windows, and if I could just get out I might be okay to run the driver.

Any further help would be greatly appreciated.

Best regards,

Andrew.

---

### Post by Rinias on 2007-02-22
Ok...

There's actually a couple of solutions possible...

1 - Do a little searching to find out exactly which Ubuntu packages you need to install the nvidia driver (there should be an apt-get command that will tell you what you need to download without actually trying to download it... If I have some time I'll try to find it, though a little Googling should be easy enough... Or check out Envy, it has to have some way of knowing what to download and install). Find those packages, download them and then install them in Ubuntu.

2 - Haha, here's a rather strong/unorthodox (and NOT SUGGESTED) way to get your x-session to not start (to install the nVidia driver you don't actually need to be in init 3) :

- Log into your system (graphical login fine)
- Open up your favorite editor (gedit ? nano?) to edit the file /etc/X11/xorg.conf (you need to have super user permissions)
- In the section "Device" delete the Driver part (not the word driver, but whatever comes after it.... "nv" probably in your case)
- Save the file
- CTRL-ATL-Backspace to kill the x-server

What you should have now is a system that will try to start X11 but cannot because there is no driver. It should post a blue screen telling you that there were problems starting the x-server and that it will disable it for some time. Say "ok" or whatever is logical (sorry, but I don't remember exactly what the prompt says) and when it asks if you want to see further information, say "no."

Next you can ALT-F1 to flip over to TTY1 and login (logging in as a normal user is fine). Change the directory (with the cd command) to the one where you saved the NVIDIA driver file. Then issue :

sudo sh ./NVIDIA-blah-blah.run  

(I don't know what the blah-blah's are in your case, but if you type ./NV and then hit TAB it will most probably autocomplete the rest)

This *should* get you into the install program which *should* run. The program is going to compile the driver for your system. This is important to know because it means that you need at least the kernel headers installed to make this work... It also means that if you upgrade your kernel, your driver will "suddenly" not work anymore... Because it needs tbe compiled again...

I say that this second way is not suggested because a) it's a lot of work and it means more work in the future; and b) Ubuntu is made to use a package manager (apt - argueably one of if not te best package manager out there) and it's always best to work through the package manager rather than patch stuff up on your own (which means that apt has no idea that a package is installed...)

Good luck again ! Try to go with the first suggestion unless you are feeling very brave and want to get your hands dirty ;)

Rinias

PS - As for the telinit and init commands... The fact that you see a new prompt does not surprise me... I think that X11 is on TTY8 in Ubuntu (confirmation?) which means ALT-F8. If you try it again, then see if you can ALT-F8 to a graphical interface (you shouldn't be able to). You can also try ALT-F7, F6, F5 etc... I'd be very surprised if init 3 or telini 3 didn't work... You may just need to login again...

---

### Post by Andrew Pape on 2007-02-26
Hi Rinias,

I now have the video driver working properly. I found a thread re working in text mode, and that allowed me to proceed with my nvidia installation. I ran into further trouble, but decided to email the author of Envy. He pointed me to a web page containing instructions on how to install nvidia cards offline (recall I have no net connection with Linux). I went through some of the instructions, got a bit stuck, but then when I started x windows the problem seemed to be solved, ie I now have the high-res mode working with ubuntu. Thanks for your help and others in this thread for mentioning Envy. If anyone else reading this post has similar problems to me with nvidia cards, feel free to contact me and I'll give you a link to the offline installation instructions.

[EMAIL="andrew_pape@yahoo.com.au"]andrew_pape@yahoo.com.au[/EMAIL]

Cheers,

Andrew.

---

### Post by Rinias on 2007-02-26
Great news! 

So glad you got through it! After all that trouble it is great to see a pretty GUI, isn't it?

All the best, and I hope that the rest of Linux will suck you in rather than make you wonder why you ever tried it ;)

Good luck,

Riri

---

### Post by Derspankster on 2007-03-24
> **r4ik said:**
> Or just use Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

Not so sure I'd use Envy. I did and it broke the hell out of X

---

