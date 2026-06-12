---
title: "ISA  Sound Card Issue"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by pluto1111 on 2006-10-25
I have the following sound card: CT 1750  - SB 16 MCD CSP and cannot get Ubuntu 6.06 to detect this card.  I tried the following with the following errors:
```
pluto@abit:~$ sudo modprobe snd-sb16
FATAL: Error inserting snd_sb16 (/lib/modules/2.6.15-27-386/kernel/sound/isa/sb/snd-sb16.ko): No such device
pluto@abit:~$ sudo modprobe sb
FATAL: Error inserting sb (/lib/modules/2.6.15-27-386/kernel/sound/oss/sb.ko): No such device
pluto@abit:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
pluto@abit:~$

```
Please help.

---

### Post by lloyd_b on 2006-10-25
I'm not sure, but I think you might be using the wrong module for that card.

Try "sudo modprobe sb-16-csp" instead and see if it works.

Lloyd B.

---

### Post by pluto1111 on 2006-10-25
Thanks for your help.  I tried entering "sudo modprobe sb-16-csp" and received the following error
```
"sudo modprobe sb-16-csp"
```

Any other suggestions?

By the way, how does one insert a picture with their post (i.e. the dog in the lloyd_b post)?

---

### Post by dannyboy79 on 2006-10-25
> **pluto1111 said:**
> Thanks for your help.  I tried entering "sudo modprobe sb-16-csp" and received the following error
```
"sudo modprobe sb-16-csp"
```

Any other suggestions?

By the way, how does one insert a picture with their post (i.e. the dog in the lloyd_b post)?

Reading your post, I don't see any error? What was the error when you did the modprobe command. Also, to include pic is simply, there is an icon along the top that says, insert image, just hold your cursor over each icon and wait for a description to come up and then click on the one that states, insert image. Oh, you might not have that option if you are clicking the farthest to the right icon, which is the quick reply option, for when you reply, you want to pick on the icon farthest to the left so that you get all the options when replying to threads, at least when you want all the options.

---

### Post by pluto1111 on 2006-10-25
> **dannyboy79 said:**
> Reading your post, I don't see any error? What was the error when you did the modprobe command. Also, to include pic is simply, there is an icon along the top that says, insert image, just hold your cursor over each icon and wait for a description to come up and then click on the one that states, insert image. Oh, you might not have that option if you are clicking the farthest to the right icon, which is the quick reply option, for when you reply, you want to pick on the icon farthest to the left so that you get all the options when replying to threads, at least when you want all the options.

Thanks for the help.  I see the "insert pic" icon, but that requests a url.  I want to have the image I inserted into my profile display next to my screen name.  

As for the error message, I copied the wrong line.  Here is the error I received.```
FATAL: Module sb_16_csp not found.

```

---

### Post by az on 2006-10-25
Is the device enabled in the BIOS and are you sure that is the correct chipset?

---

### Post by dannyboy79 on 2006-10-25
oh, you need to edit options under the link User CP which stands for User Control Panel, then scroll down and you'll see show avitar, show image, show something else, just check what you want. The error is telling you that you don't have that module so you can't probe it. You need to install it I think. I am a newbie so you'll need to ask someone else or gogle, install missing module. I just gogled it, and it apprears that the module is named sb16-cp not sb-16-cp so try, sudo modprobe sb16-cp instead.

---

### Post by pluto1111 on 2006-10-25
I'm pretty sure the device is enabled in the bios.  I used this sound card under Win98, and did not modify the bios when switching to Ubuntu.  As for the chip set, I opened the case and read this, "CT 1750  - SB 16 MCD CSP" directly from the card.

---

### Post by pluto1111 on 2006-10-25
> **dannyboy79 said:**
> oh, you need to edit options under the link User CP which stands for User Control Panel, then scroll down and you'll see show avitar, show image, show something else, just check what you want. The error is telling you that you don't have that module so you can't probe it. You need to install it I think. I am a newbie so you'll need to ask someone else or gogle, install missing module. I just gogled it, and it apprears that the module is named sb16-cp not sb-16-cp so try, sudo modprobe sb16-cp instead.
Thanks again for your help.  I tried sudo modprobe sb16-cp and received 
a similar error message ```
FATAL: Module sb16_cp not found.

```. At this point I'm considering just purchasing a PCI sound card.  How compatible are the newer (cheap) PCI cards with Ubuntu?

---

### Post by dannyboy79 on 2006-10-25
> **pluto1111 said:**
> Thanks again for your help.  I tried sudo modprobe sb16-cp and received 
a similar error message ```
FATAL: Module sb16_cp not found.

```. At this point I'm considering just purchasing a PCI sound card.  How compatible are the newer (cheap) PCI cards with Ubuntu?

Ok, you need to kind of use common sense here. I typo'd, you're chipset specifically states CT 1750 - SB 16 MCD CSP, so if I told you to modprobe sb16-cp, you should have asked yourself, why would he want me to modprobe sb16-cp when the chipset is sb16-csp? So, please do a sudo modprobe sb16-csp. Also, are htose the exact error messages that are coming up? why is it erroring with an underscore?  FATAL: Module sb16_cp not found instead of FATAL: Module sb16-cp not found? Not sure about that. It is in Ubuntu, i just verified it, snd-sb16-csp /usr/lib/alsa/modprobe-post-install snd-sb16-csp. Rerad over this page, [http://www.webservertalk.com/archive228-2005-1-875670.html](http://www.webservertalk.com/archive228-2005-1-875670.html), it tells you alot about sound drivers (modules) and how they are loaded, this guy is simply trying to load a different module than you but its the same in principle. 

Also, don't take what I said to heart, I am sorry, I am simply trying to help you help yourself. Some  stuff in linux is based on logic. He He

God luck

---

### Post by pluto1111 on 2006-10-25
Thanks for the help.  After I'm done licking my wounds, if I can muster up enough self-esteem, I might try to get this sound card to work!  :)  I sincerly do appreciate the help.

Thank you.

---

### Post by pluto1111 on 2006-10-25
> **dannyboy79 said:**
> Ok, you need to kind of use common sense here. I typo'd, you're chipset specifically states CT 1750 - SB 16 MCD CSP, so if I told you to modprobe sb16-cp, you should have asked yourself, why would he want me to modprobe sb16-cp when the chipset is sb16-csp? So, please do a sudo modprobe sb16-csp. Also, are htose the exact error messages that are coming up? why is it erroring with an underscore?  FATAL: Module sb16_cp not found instead of FATAL: Module sb16-cp not found? Not sure about that. It is in Ubuntu, i just verified it, snd-sb16-csp /usr/lib/alsa/modprobe-post-install snd-sb16-csp. Rerad over this page, [http://www.webservertalk.com/archive228-2005-1-875670.html](http://www.webservertalk.com/archive228-2005-1-875670.html), it tells you alot about sound drivers (modules) and how they are loaded, this guy is simply trying to load a different module than you but its the same in principle. 

Also, don't take what I said to heart, I am sorry, I am simply trying to help you help yourself. Some  stuff in linux is based on logic. He He

God luck


Regarding the error messgae, that is the exact error message I receive.  I too thought it was weird that the error reports with _ when I typed -.

---

### Post by pluto1111 on 2006-10-25
> **dannyboy79 said:**
> Ok, you need to kind of use common sense here. I typo'd, you're chipset specifically states CT 1750 - SB 16 MCD CSP, so if I told you to modprobe sb16-cp, you should have asked yourself, why would he want me to modprobe sb16-cp when the chipset is sb16-csp? So, please do a sudo modprobe sb16-csp. Also, are htose the exact error messages that are coming up? why is it erroring with an underscore?  FATAL: Module sb16_cp not found instead of FATAL: Module sb16-cp not found? Not sure about that. It is in Ubuntu, i just verified it, snd-sb16-csp /usr/lib/alsa/modprobe-post-install snd-sb16-csp. Rerad over this page, [http://www.webservertalk.com/archive228-2005-1-875670.html](http://www.webservertalk.com/archive228-2005-1-875670.html), it tells you alot about sound drivers (modules) and how they are loaded, this guy is simply trying to load a different module than you but its the same in principle. 

Also, don't take what I said to heart, I am sorry, I am simply trying to help you help yourself. Some  stuff in linux is based on logic. He He

God luck


I think I found the problem.  ```
bash: cd: alsa: No such file or directory

```

---

### Post by dannyboy79 on 2006-10-25
> **pluto1111 said:**
> I think I found the problem.  ```
bash: cd: alsa: No such file or directory

```

well, depending on where you were when you typed cd alsa, you are going to get that message. A better thing to have done would be to first do sudo find / -name alsa. When I did that this is what I get, 

/var/lib/alsa
/etc/apm/scripts.d/alsa
/etc/default/alsa
/usr/share/alsa
/usr/share/sounds/alsa

so, if I were you I wouldn't just assume that you don't have alsa installed since it is installed by default with ubuntu. It's all about whether or not the module is installed!

---

### Post by lloyd_b on 2006-10-25
A suggestion: Check to see if the module is present:

```
cd /lib/modules/{Kernel Version}/drivers/sound/isa/sb
ls
```

and see if there's a "snd-sb16-csp.ko".  On my machine, the value for {Kernel Version} is "2.6.17-10.generic" - yours may be slightly different.

Hmmmm That "snd" prefix......

Try this:

```
sudo modprobe snd-sb16-csp
```

I may have simply told you the wrong name...

Lloyd B.

---

### Post by pluto1111 on 2006-10-25
> **dannyboy79 said:**
> well, depending on where you were when you typed cd alsa, you are going to get that message. A better thing to have done would be to first do sudo find / -name alsa. When I did that this is what I get, 

/var/lib/alsa
/etc/apm/scripts.d/alsa
/etc/default/alsa
/usr/share/alsa
/usr/share/sounds/alsa

so, if I were you I wouldn't just assume that you don't have alsa installed since it is installed by default with ubuntu. It's all about whether or not the module is installed!

For your information, I'm new to Linux so I don't even know what alsa is; I'm just trying to get my sound card working.  While I do appreciate the help, I'm not happy with the condescending arrogance.  If you're interested in helping someone new to the Linux operating system, Great!  If your objective is to make others feel inferior because they know less then you, please don't bother responding to the requests for help.  Many people are hesitant to switch to Linux because of past issues with getting help (i.e. Read the ******* Manual).   Please try and follow the spirit of Ubuntu.

---

### Post by pluto1111 on 2006-10-25
> **lloyd_b said:**
> A suggestion: Check to see if the module is present:

```
cd /lib/modules/{Kernel Version}/drivers/sound/isa/sb
ls
```

and see if there's a "snd-sb16-csp.ko".  On my machine, the value for {Kernel Version} is "2.6.17-10.generic" - yours may be slightly different.

Hmmmm That "snd" prefix......

Try this:

```
sudo modprobe snd-sb16-csp
```

I may have simply told you the wrong name...

Lloyd B.

Ok.  I found the module.  It's located at 
/lib/modules/2.6.15-26-386/kernel/sound/isa/sb$.

This leads to another question though.  I have the following kernels listed
2.6.15-23-386  2.6.15-26-386  2.6.15-27-386

Should this be?  How do I know which kernel is being used?

---

### Post by lloyd_b on 2006-10-25
> This leads to another question though. I have the following kernels listed
2.6.15-23-386 2.6.15-26-386 2.6.15-27-386

Should this be? How do I know which kernel is being used

```
cat /proc/version
```

Will tell you (in detail) which kernel version is actually running.  It's not too unusual to have multiple kernel versions installed on the same machine, and typically each kernel version has it's own directory under "/lib/modules".  Unless you're short on disk space, I wouldn't worry too much about it.  

> Ok. I found the module. It's located at
/lib/modules/2.6.15-26-386/kernel/sound/isa/sb$.

Then "sudo modprobe" the module (leaving off the ".ko" part) and see what happens.

Lloyd B.

---

### Post by dannyboy79 on 2006-10-26
> **pluto1111 said:**
> For your information, I'm new to Linux so I don't even know what alsa is 

Well, then wouldn't you think you should know what you are talking about before saying stuff like, "I think I found the problem. bash: cd: alsa: No such file or directory"!!!! 

> **pluto1111 said:**
>  I'm just trying to get my sound card working.  While I do appreciate the help, I'm not happy with the condescending arrogance.  If you're interested in helping someone new to the Linux operating system, Great!  If your objective is to make others feel inferior because they know less then you, please don't bother responding to the requests for help.  Many people are hesitant to switch to Linux because of past issues with getting help (i.e. Read the ******* Manual).   Please try and follow the spirit of Ubuntu.

There was nothing arrogant about what I said, I was merely telling you that your statement, "I think I found the problem. bash: cd: alsa: No such file or directory" was completely false. I tried to understand why you received this message and explained why you would receive it since I figured you were a newbie. Hell, I'm a newbie, and being such I wouldn't just go off and start saying thigs that I have no idea about, see my point. So before making assumptions, since you know where that'll lead ya, ask someone, why does it say, "bash: cd: alsa: No such file or directory" instead of just stating your opinion or assumption since you yourself say your're a newbie. I was trying to help you but apparently by your statement you think you already know everything so I'll go help someone else.

---

### Post by pluto1111 on 2006-10-26
> **lloyd_b said:**
> ```
cat /proc/version
```

Will tell you (in detail) which kernel version is actually running.  It's not too unusual to have multiple kernel versions installed on the same machine, and typically each kernel version has it's own directory under "/lib/modules".  Unless you're short on disk space, I wouldn't worry too much about it.  



Then "sudo modprobe" the module (leaving off the ".ko" part) and see what happens.

Lloyd B.

Thank you for your help and the explanation on the multiple kernels.  I solved the problem with the sound card; I purchased a new PCI sound card and it works great!

---

