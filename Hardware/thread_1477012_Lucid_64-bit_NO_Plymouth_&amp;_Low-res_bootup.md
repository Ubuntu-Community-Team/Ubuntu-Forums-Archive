---
title: "Lucid 64-bit: NO Plymouth &amp; Low-res bootup"
date: 2010-05-08
forum: Hardware
---

### Post by Godspell on 2010-05-08
Hi there folks,

I've recently installed Lucid 64-bit on my laptop, Acer Aspire 5542 with ATI Radeon HD 4200.

The first problem I have is Plymouth doesn't work at all. Just blank screen with cursor and then a login screen.

Another problem occured after updating GPU drivers. I didn't want to use drivers from "System > Preferences > Hardware Drivers" because they don't work well with Cairo dock.
So, I downloaded latest drivers from ATI website and used them. It's version 10.4 64-bit. Drivers work well and I don't have any major issue BUT the resolution whilst booting up is very low. The Ubuntu logo is really big and same for all the command lines appearing. It's exactly the same after logging out, everything just turned into low resolution.

So, these are the issues I'm having atm. If any of you have solutions, please let me know. I'm pretty desperate to sort'em out.

Thank you very much.

Regards,
GS

---

### Post by jicampbell on 2010-05-08
I have an HD 4500, And It's exactly the same problem with the start up. Disabling the Hardware Driver solves the issue, but it means my laptop's fan is on constantly, something I really don't want to be happening. So, I'm grinning and bearing it at the moment, seeing as it's only 10 seconds or so. Still, it would be nice to have it fixed!

---

### Post by Godspell on 2010-05-08
> **jicampbell said:**
> I have an HD 4500, And It's exactly the same problem with the start up. Disabling the Hardware Driver solves the issue, but it means my laptop's fan is on constantly, something I really don't want to be happening. So, I'm grinning and bearing it at the moment, seeing as it's only 10 seconds or so. Still, it would be nice to have it fixed!

Hiya mate,

What did you mean by "Disabling the Hardware Driver"? Is that the one from System > Preferences > Hardware Drivers??? Checked it myself and couldn't find anything :S
I don't use those drivers anyway so would happily off'em if it'll resolve the situation.
Please let me know and thanks for reply :)

Cheers and regards,
GS

---

### Post by jicampbell on 2010-05-08
Yeah it is (Well, System > Adminstration > Hardware Drivers). I fresh installed 10.04 the other week, and the Ubuntu logo + command line stuff was perfectly fine, and matched the resolution of my screen. However, like I said, the fan was on constantly. When I checked for Proprietary Drivers, there was one available for the graphics card, so I enabled it, and restarted. Sorted the fan out, but the startup screen had gone all low-res...

I am *very* new to Ubuntu, and only just finding my way around (hence the low post count!) but if your fan is fine, you may as well give disabling the graphics driver a go.

Extra Details (for you, or more experienced people who could [please!] help):

Laptop > Dell Studio 1555
Graphics Driver mentioned above > ATI/AMD proprietary FGLRX graphics driver

Any help would be greatly appreciated!

---

### Post by Godspell on 2010-05-09
Right, I still can't see Plymouth but the low resolution when booting up and shutting down issue, is sorted.
In case if you would like to know how I did it, here's the solution.

1. sudo apt-get install v86d
2. sudo apt-get install v86d hwinfo
3. sudo hwinfo --framebuffer
   This will generate a range of resolutions that are supported. 

4. gksu gedit /etc/default/grub
   This will bring up grub for you to edit

5. This is the line you have to find and REPLACE
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   with this
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
   
NOTE: I used 1024x768 because it's the maximum resolution my laptop can afford in bootup stage. You can use what's suitable for you. 24 is the colour depth.
   
   In the same file, look for the following line
   #GRUB_GFXMODE=640x480
   and replace it with
   GRUB_GFXMODE=1024x768 (again, use the resolution that's best for you)

6. gksu gedit /etc/initramfs-tools/modules
   This will open up modules in gedit for you to edit.
   At the end of the file, paste the following line
   uvesafb mode_option=1024x768-24 mtrr=3 scroll=ywrap (mind the resolution)

7. echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
8. sudo update-grub2
9. sudo update-initramfs -u

I'm using proprietary drivers version ATI Catalyst 10.4 and this fix has worked for me.
It's not my own idea and thus, followings are the sources.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by jicampbell on 2010-05-09
Nice one mate, I'll check it out when I get back from Uni. Thanks!  Btw, What is Plymouth?

---

### Post by Godspell on 2010-05-09
Hmm good question, actually. I've been complaining a lot for not getting Plymouth but I don't know much about it either lol
All I know is it's a graphical boot splash that was integrated to Ubuntu Lucid. So, upon upgrading or fresh installing it, users have nice pretty Graphical splash on BIOS bootup stage.
I've only seen one or two pictures and it looks pretty great.
That's all I know atm :)
Cheers.

Regards,
GS

---

### Post by TheStickleback on 2010-05-09
Hey man, this is still the same guy, I changed my account (I've sent a message asking to deactivate the other one, so its all good)...

Anyway, what you suggested worked! I ended up using 1280x800, and it looks slick again. Thanks for the links. :) Decided to leave the actual Grub2 screen as a lower resolution though.

So yeah, thanks again. I hope you get your Plymouth problem sorted!

See you around
Jonathan

(Btw, for any folk who are stumbling across this thread, [http://en.wikipedia.org/wiki/Display_resolution](http://en.wikipedia.org/wiki/Display_resolution) is a really helpful reference for all of the display ratios.)

---

### Post by Godspell on 2010-05-09
Hey man,

Glad it worked out :) Yeah, plymouth is a long story. I've got a funny feeling it's gonna take a while til it get sorted.
Thanks for the wiki link, cheers.
Anyway, take care. See ya around.

Regards,
GS

---

### Post by Andrew Golightly on 2010-05-14
thanks. Worked perfectly for me too.

I'm using the proprietary ATI graphics driver.

---

### Post by Godspell on 2010-05-30
Alright fellas,

It seems that plymouth has been working right before my eyes since I've applied the above mentioned solution.

I thought I was just changing the resolution of Ubuntu logo on startup, but in fact, that WAS a plymouth bootsplash! (how dumb was I lol)

Anyway, after finding out about it I also managed to installed all the plymouth themes available from Synaptic Package Manager and was able to change them one by one.

Just thought I'd share this with you. I can't remember the original author cause I've just been through loads of threads. So whoever it is out there, all credits to you and thank you.

Just go on Synaptic and search for plymouth, you'll find following themes.

plymouth-theme-spinfinity
(This one does not work for me. Just like the name it was taking infinity! and wouldn't go on login screen.)
plymouth-theme-solar
plymouth-theme-text
plymouth-theme-fade-in
plymouth-theme-glow

Install whichever ones you want. Solar is my favourite one, it's beautiful. 
After installing them, pop up the terminal and type this

```
sudo update-alternatives --config default.plymouth
```You'll see a selection of themes you just installed. Choose any one of them and press enter.
After that, type the following to update/apply it.

```
sudo update-initramfs -u
```Reboot and enjoy :)
It works like a charm for me so hopefully, it will also work for y'all.
Can't guarantee it'll work definitely, though.

Thanks and regards,
GS

---

### Post by ranger29 on 2010-06-15
Hey, just wanted to say thanks for the advice! spent waaaayy too long fiddling with this minor aspect of the Ubuntu experience, so i'm well chuffed to have it finally sorted! thanks alot!

---

### Post by Godspell on 2010-06-19
> **ranger29 said:**
> Hey, just wanted to say thanks for the advice! spent waaaayy too long fiddling with this minor aspect of the Ubuntu experience, so i'm well chuffed to have it finally sorted! thanks alot!

You're very welcome, mate. Credits to original uploaders, I guess.
All I did was searching on the Internet and piecing the solutions together.
Glad it worked out for you.

All the best and regards,
GS

---

### Post by tom957 on 2010-07-07
Thanks a bunch! This was the last thing to get sorted out.

---

