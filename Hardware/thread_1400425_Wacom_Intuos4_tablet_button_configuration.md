---
title: "Wacom Intuos4 tablet button configuration"
date: 2010-02-06
forum: Hardware
---

### Post by addiebk on 2010-02-06
I initially tried my Intuos4 tablet with Jaunty, which worked perfectly after following all of the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1120029](http://ubuntuforums.org/showthread.php?t=1120029)

After updating to Karmic, I found that my tablet worked out-of-the-box, something for which I am eternally grateful.  I cannot, however, figure out how to personalize the buttons on the tablet.

Running:
> wacomcpl
Yields the Wacom control panel, as it did for me in Jaunty, but with no options whatsoever-- there is nothing that I can edit in the window.

Furthermore, the command:
> xsetwacom set pad Button3 "core key C "
Produces the error:
> Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'pad'

I also tried
> xsetwacom set Button3 "core key C "
on the off-chance that the format was slightly different, and 'pad' was no longer needed, but this produced the error:
> Set: Unknown parameter 'core key C '

I am stumped.

---

### Post by Favux on 2010-02-06
Hi addiebk,

What output do you get with:
```
xinput --list
```
and
```
xsetwacom list
```
in a terminal?

---

### Post by slegrand on 2010-02-28
I am facing the same issue and I would be very grateful for some help.
This is what the above 2 commands yield for me.

```
simon@simon-ubuntu:~$ xinput --list
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
"stylus"        id=2    [XExtensionKeyboard]
        Type is Wacom Stylus                
        Num_keys is 248                     
        Min_keycode is 8                    
        Max_keycode is 255                  
        Num_buttons is 7                    
        Num_axes is 6                       
        Mode is Absolute                    
        Motion_buffer is 256                
        Axis 0 :                            
                Min_value is 0              
                Max_value is 60960          
                Resolution is 5080          
        Axis 1 :                            
                Min_value is 0              
                Max_value is 45720          
                Resolution is 5080          
        Axis 2 :                            
                Min_value is 0              
                Max_value is 1023           
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
                Min_value is -900           
                Max_value is 899            
                Resolution is 1             
"pad"   id=3    [XExtensionKeyboard]        
        Type is Wacom Pad                   
        Num_keys is 248                     
        Min_keycode is 8                    
        Max_keycode is 255                  
        Num_buttons is 15                   
        Num_axes is 6                       
        Mode is Relative                    
        Motion_buffer is 256                
        Axis 0 :                            
                Min_value is 0              
                Max_value is 60960          
                Resolution is 5080          
        Axis 1 :                            
                Min_value is 0              
                Max_value is 45720          
                Resolution is 5080          
        Axis 2 :                            
                Min_value is 0              
                Max_value is 1023           
                Resolution is 1             
        Axis 3 :                            
                Min_value is 0              
                Max_value is 4096           
                Resolution is 1             
        Axis 4 :                            
                Min_value is 0              
                Max_value is 4096           
                Resolution is 1             
        Axis 5 :                            
                Min_value is 0              
                Max_value is 1023           
                Resolution is 1             
"cursor"        id=4    [XExtensionKeyboard]
        Type is Wacom Cursor                
        Num_keys is 248                     
        Min_keycode is 8                    
        Max_keycode is 255                  
        Num_buttons is 7                    
        Num_axes is 6                       
        Mode is Relative                    
        Motion_buffer is 256                
        Axis 0 :                            
                Min_value is 0              
                Max_value is 60960          
                Resolution is 5080          
        Axis 1 :                            
                Min_value is 0              
                Max_value is 45720          
                Resolution is 5080          
        Axis 2 :                            
                Min_value is 0              
                Max_value is 1023           
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
"eraser"        id=5    [XExtensionKeyboard]
        Type is Wacom Eraser                
        Num_keys is 248                     
        Min_keycode is 8                    
        Max_keycode is 255                  
        Num_buttons is 7                    
        Num_axes is 6                       
        Mode is Absolute                    
        Motion_buffer is 256                
        Axis 0 :                            
                Min_value is 0              
                Max_value is 60960          
                Resolution is 5080          
        Axis 1 :                            
                Min_value is 0              
                Max_value is 45720          
                Resolution is 5080          
        Axis 2 :                            
                Min_value is 0              
                Max_value is 1023           
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
"NOVATEK USB Keyboard"  id=6    [XExtensionKeyboard]
        Type is KEYBOARD                            
        Num_keys is 248                             
        Min_keycode is 8                            
        Max_keycode is 255                          
        Num_buttons is 14                           
"NOVATEK USB Keyboard"  id=7    [XExtensionKeyboard]
        Type is KEYBOARD                            
        Num_keys is 248                             
        Min_keycode is 8                            
        Max_keycode is 255                          
"Power Button"  id=8    [XExtensionKeyboard]        
        Type is KEYBOARD                            
        Num_keys is 248                             
        Min_keycode is 8                            
        Max_keycode is 255                          
"Power Button"  id=9    [XExtensionKeyboard]        
        Type is KEYBOARD                            
        Num_keys is 248                             
        Min_keycode is 8                            
        Max_keycode is 255                          
"Macintosh mouse button emulation"      id=10   [XExtensionPointer]
        Type is MOUSE                                              
        Num_buttons is 5                                           
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
"Logitech USB-PS/2 Optical Mouse"       id=11   [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 7
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
simon@simon-ubuntu:~$ xsetwacom list
stylus           stylus
pad              pad
cursor           cursor
eraser           eraser
simon@simon-ubuntu:~$

```

---

### Post by slegrand on 2010-02-28
Well I just fixed my problem by manually creating an ~/.xinitrc file and pasting my old settings in there.

```
kate ~/.xinitrc
```
In kate paste the following
```
xsetwacom set pad StripRDn "Button 0"
xsetwacom set pad StripRUp "Button 0"
xsetwacom set pad StripLDn "Button 0"
xsetwacom set pad StripLUp "Button 0"
xsetwacom set pad Button8 "Button 0"
xsetwacom set pad Button7 "Button 0"
xsetwacom set pad Button6 "Button 0"
xsetwacom set pad Button5 "Button 5"
xsetwacom set pad Button4 "Button 4"
xsetwacom set pad Button3 "Button 3"
xsetwacom set pad Button2 "Button 2"
xsetwacom set pad Button1 "Button 1"
xsetwacom set stylus TPCButton "off"
xsetwacom set stylus mode "Absolute"
xsetwacom set stylus Button3 "Button 2"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
# run the primary system script. /etc/X11/xinit/xinitrc
```
Then save and run
```
sh ~/.xinitrc
```

---

### Post by addiebk on 2010-03-07
When I post those two commands in a terminal I get:

```
addie@ChocolateMousse:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
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
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"USB 2.0 Camera"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
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
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
"Wacom Intuos4 4x6 eraser"	id=10	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
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
"Wacom Intuos4 4x6 cursor"	id=11	[XExtensionKeyboard]
	Type is Wacom Cursor
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
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
"Wacom Intuos4 4x6 pad"	id=12	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 71
		Resolution is 1
"Wacom Intuos4 4x6"	id=13	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
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
		Min_value is -900
		Max_value is 899
		Resolution is 1
addie@ChocolateMousse:~$ xsetwacom list
addie@ChocolateMousse:~$
```

The second command didn't give anything back, and I don't know what to make of that.  :/

Manually remaking the xinitrc file did not do anything for me, either.> 

---

