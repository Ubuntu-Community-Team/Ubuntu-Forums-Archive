---
title: "wacom bamboo sluggish action"
date: 2009-11-01
forum: Hardware
---

### Post by josvanr on 2009-11-01
I'm using a wacom bamboo graphic tablet with gimp. It kind of works, 
but its very sluggish and slow: a line drawn often seems to lag behind
the mouse pointer, slowly growing on the trail the pointer has 
followed. Actions with the pointer often freeze a few seconds. This 
often happens when moving the pointer to another window to click
a button there, or when the pencil is turned upside down to use the
eraser. Also, very often, the cursor does still move, but one is unable
to click a button or other widget for a few seconds. 

Any one know if this is a problem of the tablet (it was cheap) or a 
software problem? Any suggestions?

josvanr

---

### Post by Favux on 2009-11-01
Hi josvanr,

Educate me please.  Is it a serial tablet or are all Bamboos usb?

---

### Post by josvanr on 2009-11-02
its usb.... btw, i'm using 9.10 kubuntu

---

### Post by Favux on 2009-11-02
Hi josvanr,

OK.  I asked because there seems to be a problem with serial tablets in 64-bit 9.10.

Let's see what, in a terminal, this tells us.:
```
xinput --list
```

What model is your Wacom Bamboo?

---

### Post by josvanr on 2009-11-03
thanks for your assistance!

Model is MTE-450


here is the output of xinput --list:





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
"Video Bus"     id=2    [XExtensionKeyboard]
        Type is KEYBOARD                    
        Num_keys is 248                     
        Min_keycode is 8                    
        Max_keycode is 255                  
"Sleep Button"  id=3    [XExtensionKeyboard]
        Type is KEYBOARD                                                                                                    
        Num_keys is 248                                                                                                     
        Min_keycode is 8                                                                                                    
        Max_keycode is 255                                                                                                  
"Wacom Bamboo"  id=4    [XExtensionKeyboard]                                                                                
        Type is Wacom Stylus                                                                                                
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
"Wacom Bamboo pad"      id=5    [XExtensionKeyboard]                                                                        
        Type is Wacom Pad                                                                                                   
        Num_keys is 248                                                                                                     
        Min_keycode is 8                                                                                                    
        Max_keycode is 255                                                                                                  
        Num_buttons is 4                                                                                                    
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
"Wacom Bamboo cursor"   id=6    [XExtensionKeyboard]                                                                        
        Type is Wacom Cursor                                                                                                
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
"Wacom Bamboo eraser"   id=7    [XExtensionKeyboard]                                                                        
        Type is Wacom Eraser                                                                                                
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
"Power Button"  id=8    [XExtensionKeyboard]                                                                                
        Type is KEYBOARD                                                                                                    
        Num_keys is 248                                                                                                     
        Min_keycode is 8                                                                                                    
        Max_keycode is 255                                                                                                  
"USB2.0 1.3M UVC WebCam"        id=9    [XExtensionKeyboard]                                                                
        Type is KEYBOARD                                                                                                    
        Num_keys is 248                                                                                                     
        Min_keycode is 8                                                                                                    
        Max_keycode is 255                                                                                                  
"Asus Laptop extra buttons"     id=10   [XExtensionKeyboard]                                                                
        Type is KEYBOARD                                                                                                    
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"AT Translated Set 2 keyboard"  id=11   [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Macintosh mouse button emulation"      id=12   [XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"    id=13   [XExtensionPointer]
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

---

### Post by Favux on 2009-11-03
Hi josvanr,

Well your xinput looks ok.

Do you have the Wacom mouse (puck)?

In gimp if you have a usb mouse enabled as an extended input device why don't you try disabling it and see if that fixes things.

If you want to see if wacomcpl, the LWP's calibration and configuration gui gets you anywhere you could try changing your wacom.fdi to the one in [post #176 here]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by josvanr on 2009-11-14
hi, after some updates, I don't seem to be having the problems any more... 

btw, wacomcpl just gives me some empty form...


josvanr

---

### Post by Favux on 2009-11-14
Hi josvanr,

Good.  Glad the updates fixed it.

Sure wacomcpl is empty, the default .fdi isn't parsing the Wacom names correctly.  That's why I suggested the modified wacom.fdi.  But if your happy with your setup you can ignore it and wacomcpl.

---

