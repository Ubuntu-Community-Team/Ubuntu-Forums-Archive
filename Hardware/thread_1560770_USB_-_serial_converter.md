---
title: "USB - serial converter"
date: 2010-08-25
forum: Hardware
---

### Post by heviiguy on 2010-08-25
The only thing keeping me tethered to Windoze these days is the requirement to run a Java-based program which manages file transfers between my box and a proprietary piece of hardware used for my work. The transfers are done via a serial connection from the hardware to a USB converter.

Being a newb I haven't quite figured out how I'm going to load, let alone run, the java program on Ubutu. I've been told that this shouldn't be a problem. However, the manufacturer of my hardware (and author of the utilities program) indicated that I'll need a new USB-Serial driver that can be used within Linux. They don't have one!

Can anybody steer me in the direction of getting this up and running so that I can ditch my windoze partition and thus free-up space for the "real stuff"?

---

### Post by sgtGarcia on 2010-08-25
Most of USB->serial cables based on PL2303( this one is better than ftdi) have drives included in kernel as module.
For FTDI there is a lib: libftdi .

I can say that I have PL2303 based cable & its' working flawless.

---

### Post by heviiguy on 2010-08-25
Thanks Sarge.

I realize that I'm asking for a lot but, when you have a moment, can you (or perhaps somebody else) help me out in doing what I need to do with this? For example: 

[LIST]
[*]How do I load this?
[*]Where do I load it to?
[*]How can I make sure that it's appropriate for my Java-based utilities program?
[/LIST]
And most embarrassingly: 

[LIST]
[*]*How do I load/run the Java program on Lucid (it has a windoze installer) ?*
[/LIST]

---

### Post by sgtGarcia on 2010-08-25
You don't have to load anything. Just install libftdi in Synaptic Packet Manager.

**Installing.**

This is three way.

1st.
Try to treat this exe installer file as rar and extract it to whether You want - if its going to work You will have a directory with files & one of them will have extension like *.jar

If U have installed Sun Java then double clicking on it (the jar file) should start program or right click on file & choose Open with -> Sun Java Runtime

2nd 
Install program "Wine"
Next install Your program with double click.
Then You go to Your home folder press Ctrl+H , then navigate to
```
.wine/drive_c/ProgramFiles/
```
and there You look for directory with Your program & copy it to whether You want.

3rd
Install program "Wine"
Next install Your program with double click.
Download Java Runtime for Windows & install it with doubleclick.
Run Your program via Menu->Wine->Programs->Your program name. 

I can't assure You that any of this ways will work, You have to try them ( in that order preferably ).

Hope it helps You.

---

### Post by heviiguy on 2010-08-25
Thanks again, Sarge. I'll give it a shot!

---

