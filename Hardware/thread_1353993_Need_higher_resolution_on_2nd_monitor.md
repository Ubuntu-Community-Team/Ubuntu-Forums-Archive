---
title: "Need higher resolution on 2nd monitor"
date: 2009-12-13
forum: Hardware
---

### Post by msbohn on 2009-12-13
I've seen some posts on this but I was thinking all available screen resolutions would be made available in Ubuntu 9.10 just as it is in XP.  

Here is the appropriate terminal command results for my Dell Laptop with a 19" Dell LCD monitor attached.  The Dell LCD is limited to 1024x768 and I'd like to go to approx 11xx wide.  (Can't recall what the xx is w/o rebooting to XP - please don't make me do that :)  )

```
mark@mark-laptopXP:~$ lspci |grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
mark@mark-laptopXP:~$ xrandr
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 2048 x 768
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1024x768       75.0     60.0* 
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+1024+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
mark@mark-laptopXP:~$
```

Is this something that should be detected or do I need to go the complicate route described on another thread?

---

### Post by Thyago Lopes on 2009-12-13
I don't know much and, therefore, am not sure if I'll be able to help you. But do you have the ATI driver installed? And in the Video configuration window, does it recognize the second monitor?

---

### Post by msbohn on 2009-12-13
> **Thyago Lopes said:**
> I don't know much and, therefore, am not sure if I'll be able to help you. But do you have the ATI driver installed? And in the Video configuration window, does it recognize the second monitor?

How do I tell if the ATI driver is installed?

Yes, in the "Display Preferences" panel it shows my monitor but it doesn't list the full capabilities of the monitor resolutions, the highest it shows is 1024x768

---

### Post by Thyago Lopes on 2009-12-13
Go to System > Administration > Hardware Drivers (I think it's the name, my system is in other language)... see if the ATI driver is there and if it's installed.. if not, maybe, installing it could help.

---

### Post by msbohn on 2009-12-13
> **Thyago Lopes said:**
> Go to System > Administration > Hardware Drivers (I think it's the name, my system is in other language)... see if the ATI driver is there and if it's installed.. if not, maybe, installing it could help.

Yes, that is one of the first things I tried.  It only shows my wireless driver, nothing for ATI.

---

### Post by Thyago Lopes on 2009-12-13
> **msbohn said:**
> Yes, that is one of the first things I tried.  It only shows my wireless driver, nothing for ATI.

Uhn.. that's strange since you have a Radeon...
Type
```
lspci | grep VGA
```
and tell me what shows up?

---

### Post by msbohn on 2009-12-13
> **Thyago Lopes said:**
> Uhn.. that's strange since you have a Radeon...
Type
```
lspci | grep VGA
```
and tell me what shows up?
Take a look at my OP, it shows that output.

---

### Post by Thyago Lopes on 2009-12-13
Sorry, it's true... now I don't know.. I think the ATI driver could help, but since it's not being shown, and I don't know another way to install it (maybe Synaptic?), maybe someone could help you with configuring X the hard way... unfortunately, I don't know how to do that... :(

---

### Post by msbohn on 2009-12-15
I couldn't tell you how I did it but I got the resolution I was hoping for: 1280x1024.  I followed a few of the (seemingly hundreds) of threads on this resolution issue and somehow stumbled onto the right thing.  It had something to do with modifying the x???.conf file.  It looked all the world like I had a permissions problem doing what they said but when I logged out then back in, it worked!

Now if I can just luck into getting my wireless working, I'll be all set!

---

### Post by steveneddy on 2009-12-15
> **msbohn said:**
> I couldn't tell you how I did it but I got the resolution I was hoping for: 1280x1024.  I followed a few of the (seemingly hundreds) of threads on this resolution issue and somehow stumbled onto the right thing.  It had something to do with modifying the x???.conf file.  It looked all the world like I had a permissions problem doing what they said but when I logged out then back in, it worked!

Now if I can just luck into getting my wireless working, I'll be all set!

For the next person having this issue, once you make any changes to the **xorg.conf** file you must **restart X** for the changes to take effect.

to restart X:

Ctrl+Alt+Backspace

then log back in to see your new changes.

---

