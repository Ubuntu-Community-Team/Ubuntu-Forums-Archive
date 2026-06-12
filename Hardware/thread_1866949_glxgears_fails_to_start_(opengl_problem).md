---
title: "glxgears fails to start (opengl problem?)"
date: 2011-10-22
forum: Hardware
---

### Post by hoover67 on 2011-10-22
Hi folks,

I'm running 10.04 LTS on an older AMD board featuring an nvidia 6200 agp gpu. OpenGL used to work fine (mainly used for stellarium and of course, MineCraft), but all of a sudden opengl-apps fail to start: 

```

$ glxgears
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x3a00002
  Serial number of failed request:  37
  Current serial number in output stream:  37

```

The nvidia kernel module is loaded: 

```

$ lsmod | grep nvidia
nvidia              10382361  24 
agpgart                32011  2 nvidia,amd64_agp

```

and finally, nvidia settings shows the driver is active (also checked org.conf), using driver version 280.xx, but when I click on glx settings, nvidia-settings crashes: 

```

$ nvidia-settings 
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 282 error_code 3 request_code 138 minor_code 4)
 

```

which looks like what glxinfo spews forth: 


```
$ glxinfo
name of display: :0.0
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x3a00003
  Serial number of failed request:  32
  Current serial number in output stream:  32
```

Any ideas what could have gone wrong here or what else to check? 

The system has been freshly updated and rebooted, but sadly the error persists. 

All the best & thanks in advance, 

Uwe

---

### Post by hoover67 on 2011-10-22
Please disregard. I had forgotten I had previously installed the nvidia driver 280 manually, re-installing it using the run file fixed the missing opengl problem. Sorry for the confusion!

---

