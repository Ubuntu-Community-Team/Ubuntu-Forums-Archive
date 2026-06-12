---
title: "glxgears broken when using ssh -X on 8.10"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by Fijitotev on 2009-03-17
Hello,

I am having trouble getting opengl to work on 8.10 (both 32bit and 64bit) when using ssh -X from another machine.

> LIBGL_DEBUG=verbose glxgears
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
Error: couldn't get an RGB, Double-buffered visual

> glxinfo
name of display: localhost:10.0
Error: couldn't find RGB GLX visual or fbconfig

glxgears works just fine when run directly on the machine, and even when logging in through "ssh -X localhost". Its only broken when logging in from another machine. This works OK on 8.04.

I have also tried on other 8.10 machines that have hardware acceleration graphics cards and it works OK, so I assume the problem lies somewhere in the swrast_dri.so driver.

Anybody seen this before? Am I missing some configuration or is this an openGL bug?

---

### Post by dummy.automata on 2009-04-25
I'm also getting the same problem. glxgears tunneling works perfectly from other computers but when  sshing  (-X or -Y) to ubuntu glxgears doesn't work. I have tried 8.10 and 9.04.

Could it be related to this old bug?
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/27459]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/27459")

```
jorge@vm-ubuntu:~$ glxinfo 
name of display: localhost:10.0
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
Error: couldn't find RGB GLX visual or fbconfig

jorge@vm-ubuntu:~$ glxgears 
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
Error: couldn't get an RGB, Double-buffered visual

```

---

### Post by elupus on 2009-07-30
I've posted a new report about a similar issue
 
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/384001](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/384001)

---

### Post by leigh123@linux on 2009-09-29
> **Fijitotev said:**
> Hello,

I am having trouble getting opengl to work on 8.10 (both 32bit and 64bit) **when using ssh -X from another machine**.

> LIBGL_DEBUG=verbose glxgears
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
Error: couldn't get an RGB, Double-buffered visual

> glxinfo
name of display: localhost:10.0
Error: couldn't find RGB GLX visual or fbconfig

glxgears works just fine when run directly on the machine, and even when logging in through "ssh -X localhost". Its only broken when logging in from another machine. This works OK on 8.04.

I have also tried on other 8.10 machines that have hardware acceleration graphics cards and it works OK, so I assume the problem lies somewhere in the swrast_dri.so driver.

Anybody seen this before? Am I missing some configuration or is this an openGL bug?

Try using the correct switch !

Have you tried using the -Y switch instead of -X ?

> -Y Enables trusted X11 forwarding. Trusted X11 forwardings are not
subjected to the X11 SECURITY extension controls.> 
-X Enables X11 forwarding. This can also be specified on a per-host
basis in a configuration file.

X11 forwarding should be enabled with caution. Users with the
ability to bypass file permissions on the remote host (for the
user’s X authorization database) can access the local X11 display
through the forwarded connection. An attacker may then be able
to perform activities such as keystroke monitoring.

For this reason, X11 forwarding is subjected to X11 SECURITY
extension restrictions by default. Please refer to the ssh -Y
option and the ForwardX11Trusted directive in ssh_config(5) for
more information.

---

### Post by kingtiger01 on 2010-02-04
> **leigh123@linux said:**
> Try using the correct switch !

Have you tried using the -Y switch instead of -X ?

I am having the same issue, but the Y switch doesnt make a difference.

(X server Lucid, X client Karmic Koala Beta 3(live-CD 8/09))

Standard X forwarding functions work, but any GLX calls(gl) results in the same problem... 

looks like a X issue rather than a glxgears/glxinfo issue.

time to create a thread relative then.

---

### Post by xkucf03 on 2010-04-02
After connecting to remote machine using SSH, try:
```
tux@remote:~$ export LIBGL_ALWAYS_INDIRECT=y
tux@remote:~$ glxgears
```it worked for me :-)

---

