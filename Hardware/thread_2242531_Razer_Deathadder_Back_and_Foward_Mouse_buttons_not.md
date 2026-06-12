---
title: "Razer Deathadder Back and Foward Mouse buttons not working, Xinput"
date: 2014-09-02
forum: Hardware
---

### Post by bmdahmen on 2014-09-02
I am on a relatively fresh install on my dekstop, and I can't get my back and forward mouse buttons to work with a Razer Deathadder. 

I have tried to plug the same mouse into my ubuntu laptop  (where all the mouse buttons work just fine )and ran
```
xinput get-button-map 15 
```  (where 15 was the Razer Razer Deathadder 2013 slave pointer)  

yielding me 
1 2 3 4 5 6 7 8 9 10 11 12 13
.

So I went back to my desktop and plugged the mouse back in and attempted to set the same maping with

```
xinput set-button-map 8 1 2 3 4 5 6 7 8 9 10 11 12 13
```

and I get nothing. I am exhausting my google pages very quickly. 

I have tried using external solutions like btnx(couldn't get it to install/isn't supported past 12.10), or easystroke (couldn't figure out how to map ) without much Luck

I have install xbindkeys, made a .xbindkeys rc and added  the following to it

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```

(Where Buttons 8 and 9 are the back and forward buttons respectively as tested with xinput test)


Any suggestions? I'm going crazy

EDIT: After fixing xinput settings, I would strongly suggest a restart. It might save you five hours. ****.

---

