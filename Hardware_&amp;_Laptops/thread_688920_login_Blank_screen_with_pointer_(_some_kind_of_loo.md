---
title: "login Blank screen with pointer ( some kind of loop ) problem"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by eretron on 2008-02-05
Hello, first of all I have to say that I am newbie with linux and still learning a lot.

I have problem with gdm starting, boot goes ok but when gdm is started it stuck with black background and working pointer which I can move. It looks to me that some kind of loop is active. When I press Ctrl+Alt+F1 everything works fine. 

Also i can do Ctrl+Alt+Backspace, and after pressig it i can see for a couple of seconds that last line is 

Running local boot scripts (etc/rc.local )     [OK]   

after that black screen again with same pointer on it...


Ive tried

gdm stop 
dpkg-reconfigure  xserver-xorg

and I've tried to restore backed up xorg.conf file but I had no luck.

I alse searched google for hours and tried every solution that I could Find... stil nothing.

Also i was using intel driver from xserver config, I've tried to revert to VESA... but still...

I am using HP nx7300 laptop
Intel i945 graphic
512mb RAM....   
Ubuntu 7.10


If u need any additional info please ask..

Also forgive me for my bad English... its not my native language :D


Thanks in advance

---

### Post by eretron on 2008-02-05
Just wanted to add that Ctrl+c isn't helping also ...

---

### Post by minispalla on 2008-02-05
You might want to re-install Gnome  i had that problem a while back i think the command is ( can do it thru the CLI) sudo apt-get install ubuntu-desktop

see if that works

---

### Post by eretron on 2008-02-06
Thanks for the answer. 

I already tried that, but run into another proble. Networking is down so i cant download archives. Is there any command to enable networking.

Ive tried with this ( I read it on forum )

/etc/init.d/udev restart
i got intel_rng: FWH not detected

then

/etc/initd./module-init-tools restart
/etc/init.d/networking start

but still i cant ping anything 

If it helps im connected to internev via cable not wifi.

T.I.A

---

### Post by eretron on 2008-02-06
any ideas for connecting to the internet?

---

### Post by kesman on 2008-02-06
sudo ifdown eth0 && ifup eth0
would maybe work.
Could you check the Xorg-log for errors?
```

cat /var/log/Xorg.0.log | grep EE

```
and
```

cat /var/log/Xorg.0.log | grep WW

```
Maybe that'll help you.

---

### Post by eretron on 2008-02-06
OK I've managet to get internet. I have edited

/etc/network/interfaces

and added 

auto eth0
iface eth0 inet dhcp

and then /etc/init.d/networking restart

ill try with ubuntu-desktop reinstall now and post results.

---

### Post by eretron on 2008-02-06
OK I've reinstalled ubuntu-desktop, but its still the same

btw Xorg error log just have 1 line that says

(II) Loading extensions MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable

---

### Post by eretron on 2008-02-06
Ok update,

after reconfiguring xorg from VESA back to Intel driver

log says:

waiting for X server ti shut down
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
FreeFontPath: FPE "usr/share/fonts/X11/misc" refcount is 2, should ne 1; fixing

I remember that i was installing FreeFont for compiling other package the last time it bootet correctly so i guess that maybe it is a problem.

Is it maybe possible that this last line is causing problems, like the ubuntu is trying to fix problem but cant do that so it is trying and trying over and over again and causing this strane behaivor??

Thanks

---

### Post by eretron on 2008-02-06
oh, whatever i guess ill have to reinstal Ubuntu.

Thanks for all who helped.

---

