---
title: "SSH X Forwarding to Mac giving errors"
date: 2016-05-11
forum: Hardware
---

### Post by Elijah_Rockers on 2016-05-11
Hello Ubuntu Experts

    Running a Mac Pro, OS X El Capitan 10.11.4
    With ATI Radeon Graphics card, and XQuartz v 2.7.9
    
    I am able to run qdec and freeview perfectly fine on my machine. The     problem comes when I attempt to SSH into an Ubuntu 12.04 (Nvidia GeForce GTX 650) machine and use     these programs (it used to work fine, but I am wondering if     something in our configuration has changed now)
    
    I get the following errors after ssh into the Ubuntu machine.
    
    ```
[FONT=courier new][COLOR=#828282][myuser[/COLOR]@[COLOR=#828282]ubuntu-machine[/COLOR]:[COLOR=#ff3b1d]~[/COLOR][COLOR=#828282]][/COLOR] freeview
Xlib: extension "NV-GLX" missing on display "localhost:10.0". 
X Error: BadValue (integer parameter out of range for operation) 2
Extension:    150 (Uknown extension)
Minor opcode: 3 (Unknown request)
Resource id:  0x0
Abort         (core dumped)
            
[COLOR=#828282][myuser[/COLOR]@[COLOR=#828282]ubuntu-machine[/COLOR]:[COLOR=#ff3b1d]~[/COLOR][COLOR=#828282]][/COLOR] qdec
Xlib: extension "NV-GLX" missing on display "localhost:10.0".
X Error of failed request:  BadValue (integer parameter out of range for operation)
Major opcode of failed request:  150 (GLX)
Minor opcode of failed request:  3 (X_GLXCreateContext)
Value in failed request:  0x0
Serial number of failed request:  1504
Current serial number in output stream:  1505[/FONT]
```
        
        Based on my limited knowledge, It seems likely to be a problem         with X / SSH, and the graphics card, but I am unsure on how to         proceed from here. If anyone has any ideas on how to overcome         this, I would be incredibly grateful!
        
        The Ubuntu machine itself also has a monitor, and can run qdec         and freeview fine locally, with no problems. the issue seems to         happen over SSH. This feels like a driver issue maybe, but I am posting in hardware because I think the video people will be able to help me, and this is incredibly important for our workplace to resolve! :) Many thanks

The Mac recently updated XQuartz but I am not entirely sure if this problem was happening before the update or not.

---

