---
title: "Compiz DOA (8.04.1)"
date: 2008-09-17
forum: General Help
---

### Post by kg87 on 2008-09-17
I have a love/hate relationship with ubuntu. as soon as hardy was released i installed it, but then wiped it out :(, so i burned .1, and installed. Everything good (including wireless), ran all the updates..  but i've ran into a problem i've never had before

usually, I setup a startup script to restart Compiz (so it would work), but now i get this

```
george@george-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Its an Intel 495 vid chip, on Dell 6400m. 

Thanks in advance guys (or girls :))

---

### Post by kg87 on 2008-09-19
no one with any ideas?

By the way, Is there anywhere i can get the 8.04 iso **Without** the updates (or without x.xx.1)?

---

### Post by hijk867 on 2008-09-19
[&#32593;&#32476;&#30005;&#35805;](http://www.headcall-shop.com)&#25353;&#29031;&#20449;&#24687;&#20135;&#19994;&#37096;&#26032;&#30340;&#12298;&#30005;&#20449;&#19994;&#21153;&#20998;&#31867;&#30446;&#24405;&#12299;,&#23454;&#29616;PCTOPHONE,&#20855;&#26377;&#30495;&#27491;&#24847;&#20041;&#30340;IP&#30005;&#35805;&#12290;&#30446;&#21069;&#22269;&#20869;&#30340;[&#20813;&#36153;&#32593;&#32476;&#30005;&#35805;](http://www.orangetel.com.cn)&#36890;&#35805;&#36136;&#37327;&#37117;&#22312;&#19968;&#20010;&#27700;&#24179;&#19978;&#65292;&#20854;&#23454;&#32593;&#32476;&#30005;&#35805;&#30340;&#36890;&#35805;&#36136;&#37327;&#23436;&#20840;&#21487;&#20197;&#19982;&#20256;&#32479;&#30340;&#30005;&#35805;&#30456;&#23218;&#32654;&#30340;&#65281;

---

### Post by justinblat on 2008-09-19
Not that I've bad much better luck recently with Compiz, but I have run across a lost of posts talking about the initiate_edge issue.  I think this has to do with an unset value in a configuration file.  

You can try changing the value of that particular setting with gconf-editor from blank to [], and seeing if that gives you any better luck.  Or, you can modify the value through the Compiz Config Settings Manager, available via synaptic.  

Best of luck!

---

