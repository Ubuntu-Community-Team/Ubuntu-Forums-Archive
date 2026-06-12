---
title: "Hardwhare conflict!!! need help."
date: 2009-02-24
forum: Hardware
---

### Post by Javageek1212 on 2009-02-24
Hi I run ubuntu 8.10 with a Nvidia GeForce 8400 GS Verto.

I just installed ubuntu 8.10 and upgraded for 8.04 to 8.10...

I tryed installin the drivers from Add and Remove but when I rebooted they were indeed installed but they still did not let me go to Extra Effects.

Heck didnt even let me go to medium!

Any help on this would be great......

By the way the error when trying to enable desktop effects was "Desktop effects could not be enabled."

PS: already tried installing them through the Hardware program to....IT! did the same thing..

-Javageek1212

---

### Post by deepclutch on 2009-02-24
make sure 3D driver works:
open terminal and see the output of:
```
glxinfo |grep render
```

you may add this also to your /etc/X11/xorg.conf ,if you like! :
```
Section "Extensions"
        Option         "Composite" "Enable"
EndSection
```

---

### Post by Javageek1212 on 2009-02-24
I typed:

 glxinfo |grep render

And the output was:

direct rendering: Yes
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 

Do you wan me t try the other one to?

---

### Post by deepclutch on 2009-02-24
if you have nvidia's proprietary driver and harnesses installed ,it comes with a nifty tool "nvidia-xconfig" .you try this as:
"sudo nvidia-xconfig" -hopefully this will write a nvidia compatible /etc/X11/xorg.conf :)

---

### Post by hellsgator on 2009-02-24
Install Envy. Works just fine. ;)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Javageek1212 on 2009-02-24
Ok, this is what I got from typing "sudo nvidia-xconfig"
And then i got an error: :mad:

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



Ok.... 


I guess I will try Envy now......

---

### Post by hellsgator on 2009-02-24
Bummer, it does not work for 8.10. Sorry.

Did you install the hardware driver correctly or tried to reinstall it? And did you check for known issues?

Here, some bugs. Have fun reading. ;)

[http://search.conduit.com/ResultsExt.aspx?ctid=CT1361345&SearchSource=3&q=Using+X+configuration+file%3A+%22%2Fetc%2FX11%2Fxorg.conf%22.++WARNING%3A+No+Layout+specified%2C+constructing+implicit+layout+section+using+screen+%22Default+Screen%22.+++WARNING%3A+Unable+to+find+CorePointer+in+X+configuration%3B+attempting+to+add+new+CorePointer+section](http://search.conduit.com/ResultsExt.aspx?ctid=CT1361345&SearchSource=3&q=Using+X+configuration+file%3A+%22%2Fetc%2FX11%2Fxorg.conf%22.++WARNING%3A+No+Layout+specified%2C+constructing+implicit+layout+section+using+screen+%22Default+Screen%22.+++WARNING%3A+Unable+to+find+CorePointer+in+X+configuration%3B+attempting+to+add+new+CorePointer+section).

---

### Post by Javageek1212 on 2009-02-24
Alright um. yes I tried like 100 times lol and it didnt work

---

### Post by Javageek1212 on 2009-02-24
And to answer your question yes..

---

### Post by hellsgator on 2009-02-24
Clearly. ^^

---

### Post by Javageek1212 on 2009-02-24
Wel do you have any answers????????????

---

### Post by Javageek1212 on 2009-02-24
Can you help me though???

---

### Post by hellsgator on 2009-02-24
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Graphics_Card)

This might help a bit. I can not help directly, but i can point you in the right direction.

Linux is lot's of reading. ^^

---

### Post by Javageek1212 on 2009-03-11
I still cant I have found nothing...
I'm sorry for bugging you but I bought a really expensive graphics card 

AND I CAN'T EVEN USE IT!!!!!!

:(:(:(

---

### Post by Javageek1212 on 2009-03-11
I really need an answer

---

### Post by mhgsys on 2009-03-11
Hey, 
Seems to me you don't have the right driver installed. 
Have you tried.

System -> Administrator -> Hardware Driver.
Choose nvidia version 177, install and restart ubuntu

---

