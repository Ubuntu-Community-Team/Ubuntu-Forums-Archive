---
title: "[SOLVED] Video Card change."
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by Norwal on 2006-01-30
:-k 

Hello,

I just change my video card from a ATI 9600 to a N6600. Now X will not start. My config file shows that the drivers for the ATI card are still installed.

How do I edit the file to install drivers for Nvida?

Is there an auto detect?  

Thanks

---

### Post by o_fortuna on 2006-01-30
[QUOTE=Norwal]:-k 

Hello,

I just change my video card from a ATI 9600 to a N6600. Now X will not start. My config file shows that the drivers for the ATI card are still installed.

How do I edit the file to install drivers for Nvida?

Is there an auto detect?  

Thanks[/QUOTE]
Since X won't start up, you'll be stuck at the command line. Try this:
```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
That last command should fix up X. Just restart the computer by pressing Ctrl-Alt-Delete, and X should start.

---

### Post by Norwal on 2006-01-30
Thx o_fortuna

The first two cmds worked.  But the third gives me the error message:
        
            command not found

I ran the first two cmds again ( even though I saw them working) and the fglrx drivers are gone and the nvidia ones are the most current.

any other suggestions?

---

### Post by morphodone on 2006-01-30
try this command

```
sudo nvidia-glx-config enable
```

---

### Post by Norwal on 2006-01-31
Thx morphodone

This cmd is recognized but I get an error telling me that the xorg.config file has been change and to edit manually if this is correct. I need to change the driver section from nv to nvidia.

My problem is the only edit cmd I know is gedit and that wouldn't work without X.

What cmd do I use to edit in console mode.

---

### Post by Norwal on 2006-01-31
\\:D/    \\:D/    \\:D/ 
Thanks for the help everyone.

The cmd I was looking for was "nano".

I'm up and running with all my bookmarks.  Now to get the 3D working.

Nor:D

---

### Post by morphodone on 2006-01-31
[QUOTE=Norwal]\\:D/    \\:D/    \\:D/ 
Thanks for the help everyone.

The cmd I was looking for was "nano".

I'm up and running with all my bookmarks.  Now to get the 3D working.

Nor:D[/QUOTE]

if you are using 'nvidia' as your driver then 3D is working ;) 

a sure sign that it is working is that big nVidia screen splash that appears
before the ubuntu desktop loads

---

