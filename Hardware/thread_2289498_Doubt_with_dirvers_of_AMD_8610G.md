---
title: "Doubt with dirvers of AMD 8610G"
date: 2015-08-04
forum: Hardware
---

### Post by mfvpcrec on 2015-08-04
Hello everybody , i have a few questions about the drivers of AMD HD 8610G of HP Pavilion Notebook.

1)
I downloaded the drivers from AMD website and after install I made a test with glxgears...
The result is in average  2500 fps , but the cpu consumption is 77% for Glxgears and 30 % for Xorg ...
I don' t know if this behavior is normal or not this is my first doubt  

2)
If i make glxinfo I obtain
[FONT=monospace]```
[COLOR=#000000]
name of display: :0 [/COLOR]
display: :0  screen: 0 
[B]direct rendering: Yes 
[/B]server glx vendor string: ATI 
server glx version string: 1.4 
```

Ok Direct Rendering is yes but if I make glxinfo -i I obtain

[/FONT]```
 [FONT=monospace][COLOR=#000000]name of display: :0 [/COLOR]
display: :0  screen: 0 
**direct rendering: No (-i specified) **
server glx vendor string: ATI 
server glx version string: 1.4 
[/FONT]

```

Have got I a really direct rendering or not ? This is my second doubt.

I'm using Kubuntu 15.04

Thank you for all!

---

