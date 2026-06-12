---
title: "Ubuntu 16 with nvidia-415, system doesn't use the nvidia gpu"
date: 2019-03-23
forum: Hardware
---

### Post by torydebra on 2019-03-23
Hi,
I solved the issue few days ago [URL="https://ubuntuforums.org/showthread.php?t=2414581&p=13844153#post13844153"]https://ubuntuforums.org/showthread.php?t=2414581&p=13844153#post13844153
[/URL]But after recent system updates (kernel also I think) optirun gave me errors about a socket not found.

After some researches, I give up with bumblebee, it seems outdated and not developed anymore.
I purge nvidia and bumblebee, and install the recent nvidia driver from settings menu. I also assured from here [https://nvidia.custhelp.com/app/answers/detail/a_id/3142](https://nvidia.custhelp.com/app/answers/detail/a_id/3142) that my gpu (Geforce 840M, maxwell architecture) is supported by 410 driver series. I think it should be supported.

**ISSUES:**
The nvidia gpu is not used.
[B]
Some Outputs:[/B]

```
tori@Aspire-E15:~$ nvidia-settings

ERROR: Unable to load info from any available system
```

```
tori@Aspire-E15:~$ sudo prime-select query
unknown

```

I can correctly swicth to nvidia:
```
tori@Aspire-E15:~$ sudo prime-select nvidia
Info: the current GL alternatives in use are: ['mesa', 'mesa']
Info: the current EGL alternatives in use are: ['mesa-egl', 'nvidia-415']
Info: selecting nvidia-415 for the nvidia profile
update-alternatives: viene usato /usr/lib/nvidia-415/ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in modalità manuale
update-alternatives: viene usato /usr/lib/nvidia-415/ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in modalità manuale
update-alternatives: viene usato /usr/lib/nvidia-415/alt_ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modalità manuale
tori@Aspire-E15:~$ sudo prime-select query
nvidia

```

But, again, nvidia-setting fails:
```
tori@Aspire-E15:~$ sudo nvidia-settings 

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system


```

If I reboot, prime-select query returns unknown again.

**Other outputs:**
```
tori@Aspire-E15:~$ glxinfo 
name of display: :0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  35
  Current serial number in output stream:  36

```


[B]Trials:

[/B]Added ```
nvidia-drm.modeset=1
``` to line ```
GRUB_CMDLINE_LINUX_DEFAULT
``` in ```
/etc/default/grub
``` but nothing changed so I removed it.


Is there a solution?
Thanks

---

