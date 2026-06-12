---
title: "[SOLVED] Resolution just not right!  PLEASE HELP!"
date: 2008-05-31
forum: Hardware
---

### Post by whos2know on 2008-05-31
Hi, 

This morning I turned my computer on and as soon as the login screen came on, my screen resolution 1280x800.  To be honest this resolution is way too big on my eyes.  Also my icons and menus are out of reach.  (i have a 24 inch monitor)  I've had the restricted drivers turned off because it was the only way to be able to get higher resolution.  After this happen, I went ahead and turned on my restricted drivers, reset the computer... The resolution is the same but the screen is with the boundaries but I still cannot change my resolution higher.  I've change the monitor type and everything.  Any help would be great!! Thank you very much!!

I have a 

ATI 200M
Soyo 24" LCD Monitor
Ubuntu 8.04 Hardy

Bobby

---

### Post by ugm6hr on 2008-05-31
Assuming Hardy / 8.04:

Post output from:
```
sudo xrandr -q
```

---

### Post by whos2know on 2008-05-31
yes I'm using Hardy 8.04.  Also my monitor is 1920x1200 Native Resolution.  I forgot to add also that this monitor is my main monitor.  I am using a laptop but the screen doesn't work on it.  Here is my read out from sudo xrandr -q.

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1024x768       60.0  
   1024x480       60.0  
   848x480        60.0  
   800x600        60.0     56.0     47.0  
   720x576        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   640x350        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  

```

Thank you!!

---

### Post by AliTabuger7 on 2008-06-01
What video card do you have?

Do you have the right drivers for your video card?

If so, you can always try taking a look at /etc/xorg.conf (make sure you make backups).

---

### Post by whos2know on 2008-06-01
The video card I have is a Ati Radeon Express 200M.  The driver I am using is a restricted driver that Ubuntu installed after I check it.  I'm not sure if that would be the right one or not.  I a bit new at using Ubuntu so...any help would be great.... Thank you!!

Bobby

---

### Post by ugm6hr on 2008-06-01
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800

```

This suggests that your video card / monitor combo won't support a higher resolution.

Maybe unselect the ATI driver - go back to the generic - and reboot.

Other option is to try Envy...

---

### Post by whos2know on 2008-06-01
That is strange because I have been using a much higher resolution ever since I started to use Ubuntu and Windows I can get the higher with no problem.

When I go back to the generic driver ( which I was using until this happened ) it uses the same resolution but my desktop is outside my screen.  

I will try envy though.  I believe I used that before I upgraded to 8.04 last month.  Thank you.

Bobby

---

### Post by ugm6hr on 2008-06-01
> When I go back to the generic driver ( which I was using until this happened ) it uses the same resolution but my desktop is outside my screen.

Try that command again with the other driver to see what options it gives.

---

### Post by whos2know on 2008-06-15
Hi, just wanted to let everyone know, I installed ATI's drivers from ATI's website and works great!  Have my high resolution no problems!  Thanks for the help everyone! :)

Bobby

---

