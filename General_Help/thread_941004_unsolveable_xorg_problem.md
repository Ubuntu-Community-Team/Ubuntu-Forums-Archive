---
title: "unsolveable xorg problem"
date: 2008-10-07
forum: General Help
---

### Post by skydiver|goose on 2008-10-07
I'm running Hardy 8.04 64-bit on my Compaq Presario CQ50-107NR laptop, it has an NVIDIA GeForce 8-series video card, which is locked in 800x600.


Isn't included with the default install. I found this: [http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html) on the NVIDIA website. I've tried installing it from terminal, and from the root shell prompt when booting in recovery mode. Both times, it appears to and claims to have installed properly, but when I reboot after installation, I boot to a totally black screen and I have to reboot in recovery mode, reset x server to default, and then I'm back to square one.

Help please?

I don't wanna go back to being a Vista slave :(

-edit-
The restricted drivers do the same thing, black screen of nothingness upon reboot.

I've also tried nvidia-xconfig. same thing.

---

### Post by kabotage on 2008-10-07
try to install Envy. just follow the instructions. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by skydiver|goose on 2008-10-07
followed the install instructions verbatim, there's no "Envy" in Applications > System Tools, only the NVIDIA thing. Tried running it from terminal...

goose@goose-laptop:~$ sudo envyng -g
/usr/bin/envyng: line 11: cd: /usr/share/envy: No such file or directory
Traceback (most recent call last):
  File "/usr/share/envyng-gtk/envynggtk.py", line 736, in <module>
    os.chdir('/usr/share/envy')
OSError: [Errno 2] No such file or directory: '/usr/share/envy'

goose@goose-laptop:~$ sudo envyng -t
/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory

---

### Post by pietjanjaap on 2008-10-07
envy you find where you can install software, "synaptic package manager"

Try this:

With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this)
So install envy, then start envy and choose your videocard.

---

### Post by skydiver|goose on 2008-10-08
nope, envy failed, said it couldn't detect my hardware

---

### Post by kabotage on 2008-10-09
have you installed envy? 

using the terminal/console 

if your using ubuntu or xubuntu
```
sudo apt-get install envyng-gtk
```if your using Kubuntu, install EnvyNG-QT (which contains the QT4 interface). 

    ```
sudo apt-get install envyng-qt
```
Launch EnvyNG's GUI by selecting apps > system tools 
or
on terminal type
```
sudo envyng -g
```

---

### Post by oxman on 2008-10-11
> **skydiver|goose said:**
> I'm running Hardy 8.04 64-bit on my Compaq Presario CQ50-107NR laptop, it has an NVIDIA GeForce 8-series video card, which is locked in. 

Just a word of encouragement. I just purchased the hp dv6938 laptop with a 8 series nv. I did an update/upgrade, then selected envy for an install. Tah Dah! It worked. 

Have you done an update/upgrade via synaptic or apt-get CLI?

---

### Post by thunderheights on 2008-10-12
I have been unable to get any Linux distros installed on this laptop. Compaq Prsario CQ50_107NR.
I shrunk the C drive and created 30G of  unallocated space.
I can't get the ubuntu cd to go past busybox and type 'help'
for more commands.
I first left the new disk space unallocated and then tried to install it after using Gparted.
It's like the cd doesn't recognize my hard disk.
Any ideas?

---

### Post by eXonius on 2008-10-12
> **thunderheights said:**
> I have been unable to get any Linux distros installed on this laptop. Compaq Prsario CQ50_107NR.
I shrunk the C drive and created 30G of  unallocated space.
I can't get the ubuntu cd to go past busybox and type 'help'
for more commands.
I first left the new disk space unallocated and then tried to install it after using Gparted.
It's like the cd doesn't recognize my hard disk.
Any ideas?

I'm a bit confused, aren't you talking about a totally different problem than the one discussed above? 8-[

---

### Post by porchrat on 2008-10-12
> **thunderheights said:**
> I have been unable to get any Linux distros installed on this laptop. Compaq Prsario CQ50_107NR.
I shrunk the C drive and created 30G of  unallocated space.
I can't get the ubuntu cd to go past busybox and type 'help'
for more commands.
I first left the new disk space unallocated and then tried to install it after using Gparted.
It's like the cd doesn't recognize my hard disk.
Any ideas?

Dude don't hijack threads...make your own.

---

