---
title: "upgrade and touchpad is lost"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by raf-it on 2006-08-05
Yesterday i've done an upgrade but this morning when i've switch on my notebook, Hp omnibook Xe3, my touchpad don't work.
Now i've connected a mouse but i want my touchpad

what can i do?

---

### Post by franute on 2006-08-05
Disconnect your usb mouse and try with:
"sudo dpkg-reconfigure xserver-xorg"

---

### Post by raf-it on 2006-08-05
i've try but it ask me what kind of mouse i use and i can choose
imps/s or Explorerps/2

but i can't find touchpad or thinkpad

---

### Post by LuisC-SM on 2006-08-05
> **raf-it said:**
> Yesterday i've done an upgrade but this morning when i've switch on my notebook, Hp omnibook Xe3, my touchpad don't work.
Now i've connected a mouse but i want my touchpad

what can i do?

Hey... no offense but...

this is what i've been trying to do eversince i bought an optical minimouse and i've had headaches trying to disable the touchpad.

I have a toshiba satellite s284, just in case someone has any ideas on how to turn it off

Regards

PS Using Ubuntu Dapper

---

### Post by franute on 2006-08-05
> **raf-it said:**
> i've try but it ask me what kind of mouse i use and i can choose
imps/s or Explorerps/2

but i can't find touchpad or thinkpad

It works for me, I had the touchpad with a bad configuration (scroll didn't work) and it worked. Simply, do the dpkg-reconfigure with your usb-mouse disconnected and select the first option that appears on mouse selection (I think it's Imps/2) and 3buttons emulation (if you want it). It must configure the touchpad by itself. Anyway, you can always save your current xorg.conf file and restore it if you don't like the changes ;)

---

### Post by franute on 2006-08-05
> **LuisC-SM said:**
> Hey... no offense but...

this is what i've been trying to do eversince i bought an optical minimouse and i've had headaches trying to disable the touchpad.

I have a toshiba satellite s284, just in case someone has any ideas on how to turn it off

Regards

PS Using Ubuntu Dapper

I think that with dpkg-reconfigure, when you're selecting the mouse, it is only for an "external" mouse. It seems to configure the touchpad without asking. You can always try the "ugly" way to do things, try to comment the touchpad lines in your xorg.conf file (I hope you know it but you can comment a line with a "#" before every line you don't want to be "loaded" in a file like this). Then restart the Xserver with "sudo /etc/init.d/gdm restart" or "sudo /etc/init.d/kdm restart" in kubuntu.

---

### Post by LuisC-SM on 2006-08-05
Hi. 

tnx for your reply.

Commenting the synaptic touchpad lines in /etc/X11/xorg.conf only causes xserver to go down.

dpkg-reconfiguring xserver-xorg (in my case) gave me more options than first time configuration but, still cannot make the touchpad to be off (not even by BIOS conf).

However, this laptop, with these new kernel updates, has been getting so darn slow that even working just with firefox is getting into my nervs and I'm just about one or 2 weeks away to buy a new acer aspire 9800 :-({|= (I'll be asking for opinions in a new thread).

Anyways, thanks so much for your help :D 


Luis C. Suárez

---

### Post by TheWizzard on 2006-08-06
dapper does not recognise synaptics touchpads correctly. problems are very easy to solve if you follow the instructions here: 
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by LuisC-SM on 2006-08-07
> **TheWizzard said:**
> dapper does not recognise synaptics touchpads correctly. problems are very easy to solve if you follow the instructions here: 
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Hey, tnx a lot for the link.

It just worked like a charm :D

Regards.

Luis C. Suárez

---

### Post by Andcor on 2006-08-08
By the way, one of you asked if there were any way to turn the touchpad off, and there is, a quite good way in fact. 
noob_Lance have made a thread about turning the touchpad on and off in ubuntu and kubuntu, and it works like a charm.

Take a look, it is certainly worth the efford.

[http://ubuntuforums.org/showthread.php?t=143095]("http://ubuntuforums.org/showthread.php?t=143095")

---

### Post by LuisC-SM on 2006-08-08
> **Andcor said:**
> By the way, one of you asked if there were any way to turn the touchpad off, and there is, a quite good way in fact. 
noob_Lance have made a thread about turning the touchpad on and off in ubuntu and kubuntu, and it works like a charm.

Take a look, it is certainly worth the efford.

[http://ubuntuforums.org/showthread.php?t=143095]("http://ubuntuforums.org/showthread.php?t=143095")

Tnx Ancor.

My reply was precisly to thank "The Wizzard" for the link to the wikki provided above.

However, thanks again for your effort to help.

Regards.

Luis C. Suárez

PS. It's worthwhile to take a look to your provided link too.(It is jjust about the same).

---

