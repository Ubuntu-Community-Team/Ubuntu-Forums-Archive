---
title: "ubuntu is running in low-graphics mode"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by watsonsun on 2009-10-10
Pse Help -- newbee
Ubuntu 9.04 was running beautifully for months.  Did an update and had all sorts of errors.  Thought that I could just reinstall the whole ubuntu desktop and get it going again -- wrong!!   After the new installation,  I got this message

ubuntu is running in low-graphics mode

EE GARTinit: unable to open /dev/agpgart (No such file or directory)
EE drm  drm Open failed
EE intel(O) dri  DRIScreeninit failed/  Disabling DRI
EE intel(O) Failed to allocate framebuffer.  Is your VideoRam set too low?
EE intel(O) Couldnt allocate video memory

My mouse also did not work.  Tried reinstalling a few times and got the same message.  When I accept the low resolution mode,  the screen appeared normal, but only occupied 4/5 th of the monitor.  Unfortunately without a mouse,  I do not know how to get the terminal working.

I tried reinstallation many times,  each time deleting the partition and recreating the partition.  But the same results.

Strange,  when I run ubuntu 9.04 from my CD, without installation,  everything is ok,  ie no resolution or mouse problems.

My system is on dual boot with Win 7

Would appreciate any help,  thanks

---

### Post by tommcd on 2009-10-10
To get to a virtual terminal hit: ctrl + alt + F2 and login.
See what modules are being loaded:
```
lsmod | less
```
Use the up and down arrow keys to scroll through the output.
I use intel video on my laptop. I have these drivers loaded (among many others):
**drm  agpgart  intel_agp**
Verify that those drivers are being loaded. If any are not listed then:
First hit the "q" key to exit from less. Then stop the X server :
```
sudo /etc/init.d/gdm stop
```
Then load any of those drivers that were not loaded:
```
sudo modprobe drm agpgart intel_agp
```
If you can't modprobe them all at once then modprobe them one at a time.
Then restart X:
```
sudo /etc/init.d/gdm start
```
It should take you to the Ubuntu login screen. If it doesn't then hit: ctrl + alt + F7. See if the video is ok.
If this works we can add those modules to your /etc/modules file so they load automatically at bootup.

---

### Post by watsonsun on 2009-10-10
Hi Tommcd

thanks for the direction.  
when I enterred 

lsmod | less,  I get the following
usb_storage
r8169
mii
fbcon
tileblit
font
bitblit
softcursor

I then typed 
**sudo modprobe** [B]drm  agpgart  intel_agp
[/B]I get
FATAL: Could not load /lib/modules/2.6.28-15-server/modules.dep: No such file or directory

Sorry for asking a foolish question.  What does this statement mean:
If you can't modprobe them all at once then modprobe them one at a time.
Am I supposed to type 
sudo manprobe r8169, mii, fbcon ...  ?

When I typed sudo /etc/init.d/gdm start
I get back to the low-graphics mode

I tried to start the by typing startx
I get 
FATAL: Could not load /lib/modules/2.6.28-15-server/modules.dep: No such file or directory
EE drm  drm Open failed
EE intel(O) dri  DRIScreeninit failed/  Disabling DRI
EE intel(O) Failed to allocate framebuffer.  Is your VideoRam set too low?
EE intel(O) Couldnt allocate video memory

Like what I mentioned earlier, when I run ubuntu 9.04 from the same CD, without installation,  everything is ok.  No problem with my screen

---

### Post by watsonsun on 2009-10-11
I fail to mention that when I type 
lsmod | less

the list that showed did not include
drm agpgart intell_agp 

I then typed 
sudo modprobe drm  agpgart intell_agp

I get 
FATAL: Could not load /lib/modules/2.6.28-15-server/modules.dep: No such file or directory

when I tried to do a listing on that directory,  I only get
2.6.28-11-generic.
there is no directory 2.6.28-15-server

Thanks

---

### Post by tommcd on 2009-10-11
When I said to modprobe them 1 at a time, I was referring to the 3 modules I listed in bold type: **drm agpgart intel_agp**. So to modprobe the 1 at a time it would be:
```

sudo modprobe drm
sudo modprobe agpgart
sudo modprobe intel_agp

```
So look for those 3 modules in the output of **lsmod**. If any of those 3 modules are not listed then modprobe them as I listed here.
I don't know why you are getting the:
```
FATAL: Could not load /lib/modules/2.6.28-15-server/modules.dep: No such file or directory

``` 
error. Did you install Ubuntu 9.04 from the server install CD or the minimal install CD or something?
Try modprobing the 3 drivers I listed after stopping the X server (sudo /etc/init.d/gdm stop, then restart the X server (sudo /etc/init.d/gdm start) as per my last post.
If that doesn't work, the only other thing I can suggest is to boot to recovery mode and choose the option **xfix fix the video** and then reboot and see if that fixes your desktop.

---

### Post by watsonsun on 2009-10-11
Silly me.  Will try your suggestion when I reach home and have access to my desktop.
sudo modprobe drm
sudo modprobe agpgart
sudo modprobe intel_agp

  I installed my desktop from a CD,  whose image I downloaded from the internet.  I have used this CD on my notebook and it installed very smoothly.  When I used this CD to run Ubuntu (from CD) without  installing on the desktop, it also worked smoothly.

I have tried installing about 3 times now, each time deleting and recreating the partition, and everytime, the same results, ie low - graphics mode.  Also it kept refering to this directory 2.6.28-15-server.  The only sub-directory that exist is 2.6.28-11-generic

Thanks very much for your help and patience.  Will get back to you with the results asap.

---

### Post by watsonsun on 2009-10-11
ok,  tried 

sudo modprobe drm
sudo modprobe agpgart
sudo modprobe intel_agp

got similar errors for all
FATAL: Could not load /lib/modules/2.6.28-15-server/modules.dep: No such file or directory
tried 
sudo apt-get install drm -  couldn't find package 
sudo apt-get install agpgard -  couldn't find package 
sudo apt-get install intel_agp -  couldn't find package 

Tried as instructed below was unsuccessful
'If that doesn't work, the only other thing I can suggest is to boot to recovery mode and choose the option **xfix fix the video** and then reboot and see if that fixes your desktop'

Still get low-graphics mode.

Can anyone tell me why it is looking for  2.6.28-15-server.  The only sub-directory that exist on my desktop is 2.6.28-11-generic.  Also my CD is Ubuntu 9.04 Desktop.  

I have reinstalled many times, using both the image for desktop and also for server,  but the same low-graphics result.

However,  if I run it direct from my CD, without installing,  there is no problem

Thanks to all.

---

### Post by watsonsun on 2009-10-12
I must apologise to commcd. After all his advise and hard work,  i found that the problem was created by me.  I initially installed and ran on Ubuntu 9.04 server.  however after a rogue update,  my system crashed.  I then deleted the partition and installed ubuntu 9.04 desktop.  As there were many previous installations shown in my startup screen,  i always assumed that the one on top was the latest.  However in this instance,  the top link was an old installation of my 9.04 server, which was deleted when I deleted my partition.  So when I tried to start my ubuntu with this link,  it was looking for the server directories  and I ended up getting the error
FATAL: Could not load /lib/modules/2.6.28-15-server/modules.dep: No such file or directory

When I clicked on the correct link, ie 9.04 desktop,  everything worked ok.

Once again thank you all and consider this thread closed

---

### Post by tommcd on 2009-10-13
No apology needed. Glad you got it fixed. I guess I was on the right track when I asked about Ubuntu server.

---

