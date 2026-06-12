---
title: "nvidia driver  failed to detect but detected via console login"
date: 2009-08-21
forum: Hardware
---

### Post by Ajat on 2009-08-21
I have Benq Joybook s41 which use GeForce 8600M GS,
after updating to linux kernel 2.6.13 ,  my kubuntu starts with low graphic mode. Then i reinstall the NVIDIA driver (185.18.31) via console login.

When i start my laptop, and boot to kubuntu, it says that i need to update the configuration, since my VGA is failed to be detected.. and the 4 options show (start with low graphic mode, reconfigure, troubleshoot, exit to console login)

the first 3 options, take me to login screen but with low graphic (can't use compiz )

while when i choose "exit to console login", it doesn't really take me to console (just for a few seconds), a gui login screen appears with high resolution, and smooth compiz run fine.

what happen? help me

thanks

---

### Post by Ajat on 2009-08-23
bump.

I found that my problem is related to glx module, since

```
$ sudo grep -n "^(EE)" /var/log/Xorg*log
```

gives

```

/var/log/Xorg.0.log:300:(EE) XKB: No components provided for device Virtual core keyboard
/var/log/Xorg.1.log:79:(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
/var/log/Xorg.1.log:81:(EE) Failed to load module "glx" (loader failed, 7)
/var/log/Xorg.1.log:1408:(EE) USB Optical Mouse: Read error: No such device
/var/log/Xorg.1.log:1425:(EE) USB Optical Mouse: Read error: No such device
/var/log/Xorg.failsafe.log:1331:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```



i have tried to modified my xorg.conf by adding
```
load glx
``` 
in the modules section (since it wasn't there at the beginning)

but it doesn't work.

running nvidia-xconfig DOES **NOT** solve the problem.

now every time i restart my computer, the "ubuntu running in low graphic" window always appear, and i need to chose "exit to console login" to get a 24 color depth login screen, and then everthing works fine (compiz, video). but it's annoying.

how could the driver is not there? 
i installed nvidia official driver for GeForce 8600M GS linux 32 bit, 185.18.31-pkg1 

it's been three days i have trying to solve this, but the problem still persists.

any help would be greatly appreciated.

Thanks.

---

### Post by pescez on 2009-11-15
i have this problem too. i think it did appear after i removed pulseaudio but i cannot be sure. to get the correct logins page i click on the cancel button of the low-graphics window to get the real KDM splash.
did you have any news? did it just solve automagically or you did something?

---

### Post by Ajat on 2009-11-17
if i remembered it correctly, i switch to GDM for while and then switch back to KDM ... there was something in my startup configuration, but i can't remember what it is..

---

