---
title: "Wacom mouse problem"
date: 2009-05-02
forum: Hardware
---

### Post by K-buntu on 2009-05-02
The mouse on my Wacom Bamboo Fun tablet seems to frequently miss clicks, sometimes I have to click as many as 3 times for it to register. I don't have this problem when using the pen.
I'm using Kubuntu Jaunty, but I've also tried installing the Ubuntu desktop but with no difference.
Thanks for any help.

---

### Post by K-buntu on 2009-05-04
Nobody has a solution?
I think it might be that the system isn't polling the mouse state often enough, since it seems to register a click more often when I hold down the mouse button for a bit.
But I have no idea what to do about it. Any suggestions?

---

### Post by Favux on 2009-05-04
Hi K-buntu,

What version of Kubuntu are you using?  If you have Windows is there a clicking problem in Windows?  If so maybe the mouse needs cleaning?  Or there is some other hardware problem.

Have you calibrated your tablet with "wacomcpl" typed in a terminal?  If not that might clear it up.

I don't see anything in the HOW TO for clickforce with the mouse:
```
ClickForce    integer (1 - 21)         sets tip/eraser pressure threshold with clickforce scale

```
[http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)  or  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

### Post by K-buntu on 2009-05-04
Thanks for the reply, Favux.

I'm using a new install of Kubuntu 9.04 on its own partition, and before that I had a WUBI install of Ubuntu 8.10, which also had the same problem (although with 8.10 the mouse didn't work at all until I installed some extra libraries.)

It works just fine in Vista, so cleaning isn't the issue.

I just tried wacomcpl, and it just shows an empty list below "Select the device."
I also tried entering: "xsetwacom list dev" which strangely shows nothing as well.

---

### Post by Favux on 2009-05-04
Hi K-buntu,

Is the output of this blank?:
```
xsetwacom list
```

What is the output of?:
```
xinput --list
```

---

### Post by K-buntu on 2009-05-04
"xsetwacom list" produces nothing as well.

The output of "xinput --list" is:
```
"Virtual core pointer"  id=0    [XPointer]
        Num_buttons is 32                 
        Num_axes is 2                     
        Mode is Relative                  
        Motion_buffer is 256              
        Axis 0 :                          
                Min_value is -1           
                Max_value is -1           
                Resolution is 0           
        Axis 1 :                          
                Min_value is -1           
                Max_value is -1           
                Resolution is 0           
"Virtual core keyboard" id=1    [XKeyboard]
        Num_keys is 248                    
        Min_keycode is 8                   
        Max_keycode is 255                 
"AT Translated Set 2 keyboard"  id=2    [XExtensionKeyboard]
        Num_keys is 248                                     
        Min_keycode is 8                                    
        Max_keycode is 255                                  
"Macintosh mouse button emulation"      id=3    [XExtensionPointer]
        Num_buttons is 32                                          
        Num_axes is 2                                              
        Mode is Relative                                           
        Motion_buffer is 256                                       
        Axis 0 :                                                   
                Min_value is -1                                    
                Max_value is -1                                    
                Resolution is 1                                    
        Axis 1 :                                                   
                Min_value is -1                                    
                Max_value is -1                                    
                Resolution is 1                                    
"Wacom BambooFun 4x5"   id=4    [XExtensionKeyboard]               
        Num_keys is 248                                            
        Min_keycode is 8                                           
        Max_keycode is 255                                         
        Num_buttons is 5                                           
        Num_axes is 6                                              
        Mode is Absolute                                           
        Motion_buffer is 256                                       
        Axis 0 :                                                   
                Min_value is 0                                     
                Max_value is 14760                                 
                Resolution is 2540                                 
        Axis 1 :                                                   
                Min_value is 0                                     
                Max_value is 9225                                  
                Resolution is 2540                                 
        Axis 2 :                                                   
                Min_value is 0                                     
                Max_value is 511                                   
                Resolution is 1                                    
        Axis 3 :                                                   
                Min_value is -64                                   
                Max_value is 63                                    
                Resolution is 1                                    
        Axis 4 :                                                   
                Min_value is -64                                   
                Max_value is 63                                    
                Resolution is 1                                    
        Axis 5 :                                                   
                Min_value is 0                                     
                Max_value is 1023                                  
                Resolution is 1                                    
"Wacom BambooFun 4x5 pad"       id=5    [XExtensionKeyboard]       
        Num_keys is 248                                            
        Min_keycode is 8                                           
        Max_keycode is 255                                         
        Num_buttons is 7                                           
        Num_axes is 6                                              
        Mode is Relative                                           
        Motion_buffer is 256                                       
        Axis 0 :                                                   
                Min_value is 0                                     
                Max_value is 14760                                 
                Resolution is 2540                                 
        Axis 1 :                                                   
                Min_value is 0                                     
                Max_value is 9225                                  
                Resolution is 2540                                 
        Axis 2 :                                                   
                Min_value is 0                                     
                Max_value is 511                                   
                Resolution is 1                                    
        Axis 3 :                                                   
                Min_value is 0                                     
                Max_value is 0                                     
                Resolution is 1                                    
        Axis 4 :                                                   
                Min_value is 0                                     
                Max_value is 0                                     
                Resolution is 1                                    
        Axis 5 :                                                   
                Min_value is 0                                     
                Max_value is 71                                    
                Resolution is 1                                    
"Wacom BambooFun 4x5 cursor"    id=6    [XExtensionKeyboard]       
        Num_keys is 248                                            
        Min_keycode is 8                                           
        Max_keycode is 255                                         
        Num_buttons is 5                                           
        Num_axes is 6                                              
        Mode is Relative                                           
        Motion_buffer is 256                                       
        Axis 0 :                                                   
                Min_value is 0                                     
                Max_value is 14760                                 
                Resolution is 2540                                 
        Axis 1 :                                                   
                Min_value is 0                                     
                Max_value is 9225                                  
                Resolution is 2540                                 
        Axis 2 :                                                   
                Min_value is 0                                     
                Max_value is 511                                   
                Resolution is 1                                    
        Axis 3 :                                                   
                Min_value is -900                                  
                Max_value is 899                                   
                Resolution is 1                                    
        Axis 4 :                                                   
                Min_value is -1023                                 
                Max_value is 1023                                  
                Resolution is 1                                    
        Axis 5 :                                                   
                Min_value is 0                                     
                Max_value is 1023                                  
                Resolution is 1                                    
"Wacom BambooFun 4x5 eraser"    id=7    [XExtensionKeyboard]       
        Num_keys is 248                                            
        Min_keycode is 8                                           
        Max_keycode is 255                                         
        Num_buttons is 5                                           
        Num_axes is 6                                              
        Mode is Absolute                                           
        Motion_buffer is 256                                       
        Axis 0 :                                                   
                Min_value is 0                                     
                Max_value is 14760                                 
                Resolution is 2540                                 
        Axis 1 :                                                   
                Min_value is 0                                     
                Max_value is 9225                                  
                Resolution is 2540                                 
        Axis 2 :                                                   
                Min_value is 0                                     
                Max_value is 511
                Resolution is 1
        Axis 3 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 4 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 5 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1

```

---

### Post by Favux on 2009-05-05
Hi K-buntu,

A fix may have come through recently, I'm not sure.  Run update manager and install any updates.  We're probably looking for any new udev rules or xorg-xserver.  Then try the commands again.  Otherwise we'll move on.

---

### Post by K-buntu on 2009-05-05
Just installed the updates. (I got an error message: "E: The package cache file is corrupted   E: _cache->open() failed, please report." after checking for updates (report where?) so i hit the check button again to redownload the list and didn't receive any errors that time. Perhaps it's just because I accidentally started the GNOME update manager instead of the KDE.)

I rebooted and then tried the commands again with the same result as last time.

One thing I forgot to mention earlier was that I'm running the amd64 version of Kubuntu, I don't know if that effects anything.

---

### Post by Favux on 2009-05-05
Hi K-buntu,

As far as I know AMD-64 doesn't affect anything.  KDE may have some effect, but I don't think so.  From your xinput --list:
stylus=Wacom BambooFun 4x5
eraser=Wacom BambooFun 4x5 eraser
cursor=Wacom BambooFun 4x5 cursor
pad=Wacom BambooFun 4x5 pad

Now hopefully you have a copy of your old .xinitrc and can just substitute the names.  Loic2's Wacom tablet thread has several examples and some include Bamboos.  Start with mallow's post #160 and read forward:  [http://ubuntuforums.org/showthread.php?t=967147&page=16](http://ubuntuforums.org/showthread.php?t=967147&page=16)

Until today I would have recommended rec's script which translates the HAL names to linuxwacom names before Xserver starts.  This has the advantage of saving you from renaming everything.  But in the last couple days two people have reported some problems with it.  Out of I suppose dozens and dozens who have installed it.  But still.  Plus for our tablet pc's we seemed to have figured out a .fdi that gets around the whole problem.  I'm not sure I understand why yet.  Apparently something to do with how we specify the tablet in the .fdi (a different point on the HAL device branch).  So I suppose it might be possible to come up with one for external graphics tablets.

And here is a sample custom_wacom.fdi from Loic2's Wacom.fdi wiki:  [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

Good luck!

---

### Post by K-buntu on 2009-05-05
Thanks for the help, Favux.

I don't have an .xinitrc file, should I create a new one?

I tried:
```
xsetwacom set "Wacom BambooFun 4x5 cursor" ClickForce 1
```
and:
```
xsetwacom set "Wacom BambooFun 4x5 cursor" ClickForce 21
```
as well as trying it on the "Wacom BambooFun 4x5 pad" device just in case, all with no change in the clicking behavior.


Perhaps I should go the .fdi route, the custom sample you showed me seems to be doing a text match on the device names, but since the stylus is named "Wacom BambooFun 4x5", how would you do a text match that differentiates it from the other devices?

---

### Post by Favux on 2009-05-05
Hi K-buntu,

As I mentioned cyberfish/gali98 just came up with a .fdi that gets around the whole names problem.  We didn't think that was possible, so it's changed our understanding of what's going on.  It was  a .fdi problem all along, apparently.  We can go back to configuring with wacomcpl like before with the new .fdi.

So I started to play around with their .fdi to see if I could extend it to an external Wacom graphics tablet.  I'll attach it.  This is a shot in the dark because I would probably need to see the output of your "lshal" to really have a chance.  In a terminal type:
```
lshal>lshal.txt
```
That should create a text file with your HAL output.  There should be a least one section with Wacom stuff in it, probably more.  Since the output is long it is tedious to comb through, I know because I've done it several times now.  Putting the output in a txt file makes it searchable with gedit.  I probably also need to look at the .fdi's in Loic2's thread and wiki.

If you were to try it replace the current 10-wacom .fdi in /usr/share/hal/fdi/policy/20thirdparty/ (after renaming it say 10-wacom.bak and saving it somewhere safe) with the new 10-wacom.fdi.

---

### Post by K-buntu on 2009-05-07
Thanks again Favux, sorry for the late reply.

Your shot in the dark worked :) all the devices are now showing up in wacomcpl. I tested reassigning the buttons on each device to make sure they're labelled properly, and it all seems to be in order.

However, the mouse only has parameters related to button assignment and acceleration, nothing about ClickForce or pressure sensitivity. So I'm pretty sure now that it has to do with the driver not polling the mouse as often as it does the pen.

---

### Post by Favux on 2009-05-07
Hi K-buntu,

Wow!  Talk about a lucky guess.

That makes sense and explains why the HOW TO doesn't have clickforce for the mouse.  If we knew enough about the linuxwacom driver it might be possible to alter the polling behavior.  So you could post on the LWP's general discussion site and see if Ping Cheng or someone can help.  The forum is here:  [http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-discuss)

---

### Post by Favux on 2009-05-17
Hi K-buntu,

A Bamboo user who seems pretty good at setting up his tablet has only these two entries for his Wacom mouse in the .xinitrc that wacomcpl generates:
```
xsetwacom set cursor Accel "1"
xsetwacom set cursor SpeedLevel "4"
```
I don't know if it will be useful to you but I thought I should pass it along.

---

