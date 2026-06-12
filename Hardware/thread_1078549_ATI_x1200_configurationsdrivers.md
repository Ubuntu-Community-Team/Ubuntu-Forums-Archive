---
title: "ATI x1200 configurations/drivers"
date: 2009-02-23
forum: Hardware
---

### Post by rdmike on 2009-02-23
Hi all,

New Ubuntu user here trying to get the graphics working correctly on my Gateway T-1628 notebook. I have an ATI x1200 video adapter and have been following the instructions listed [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") to get things working correctly.

I ran the get update and reboot commands without difficulty but the next command asks to verify that everything worked using this string;

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)


I pasted the info into a terminal and got the following response;

> michael@michael-laptop:~$ display: :0.0  screen: 0
bash: display:: command not found
michael@michael-laptop:~$ OpenGL vendor string: ATI Technologies Inc.
bash: OpenGL: command not found
michael@michael-laptop:~$ OpenGL renderer string: RADEON 9600 Generic
bash: OpenGL: command not found
michael@michael-laptop:~$ OpenGL version string: 2.0.5814 (8.25.18)
bash: syntax error near unexpected token `('


So, I'm kinda stick and would like some help please.

There are a couple of notes, at this site, with troubleshooting info but, to be honest, I'm a bit confused by them. If anyone can help walk me through this issue I'd certainly appreciate it. The whole purpose for me trying this is the default install, of ubuntu, will not allow me to play supertuxcart, for example, in full screen mode. It'll work in the default screen mode but flickers horribly.

Anyhoo, thanks in advance!

---

### Post by rdmike on 2009-02-25
Can anyone help? Pretty please?

---

### Post by rdmike on 2009-02-26
Bump

---

### Post by csurlee on 2009-02-26
Try installing envyNG

---

### Post by rdmike on 2009-02-27
That's what my ubuntu book said too but I cannot find it via the package manager

---

### Post by lvleph on 2009-03-01
```
http://albertomilone.com/nvidia_scripts1.html
```
I have the same computer. I have the graphics working using the restricted drivers. However, I have hibernate issues that I have not been able to solve.

---

### Post by rdmike on 2009-03-03
I can only assume then that Ubuntu and the ATI x1270 adapter aren't compatible; shame as I was starting to like Ubuntu.

---

### Post by lvleph on 2009-03-12
The recent update to xorg broke my graphics, but then I used envyng and it is working again.

---

