---
title: "Screen flickering"
date: 2009-04-03
forum: Hardware
---

### Post by rang501 on 2009-04-03
I have a lenovo with nVidia 7300 Go GPU and  I'm using Jaunty (Kubuntu). 
Problem:
Screen flickers.

dmesg output (end):

```
[ 5583.363492] operapluginwrap[7524]: segfault at f37a8030 ip 00000000f70c59e0 sp 00000000ff8ca864 error 4 in libpthread-2.9.so[f70be000+15000]
[ 6039.225868] operapluginwrap[7767]: segfault at f5424030 ip 00000000f70689e0 sp 00000000ffe6e314 error 4 in libpthread-2.9.so[f7061000+15000]
[ 6043.343743] operapluginwrap[7774]: segfault at f542d030 ip 00000000f70719e0 sp 00000000ffb76304 error 4 in libpthread-2.9.so[f706a000+15000]
[10349.641389] NVRM: Xid (0001:00): 13, 0000 80016100 0000008a 00000404 00000000 00004000
[10534.280978] operapluginwrap[8677]: segfault at f53e2030 ip 00000000f70269e0 sp 00000000ffb2bac4 error 4 in libpthread-2.9.so[f701f000+15000]
```

I don't know, if this is related: in rare cases, screen flicker caused system crash.
Anyway, this flickering problem is common after using 180.xx drivers.

kwin: X Error (error: <unknown>[DAMAGE+0], request: XDamageDestroy[DAMAGE+2], resource: 0x1455aa5)

Does anyone have this kind on problem?

---

### Post by nimajiman on 2009-05-09
Yes I have a similar problem with screen flickering. It has never completely crashed on me but I find after using the computer for 20-30 mins it begins to flicker every couple of minutes. It's not enough to be a serious problem but is annoying as it's so constant.

Running 32bit Jaunty, graphics = Geforce GO 7600 256mb; running nvidia 180.44 drivers i think (?)

Not sure if there is a fix for this?

---

### Post by WakkiTabakki on 2009-05-11
+1
I've been running jaunty since its release and never had a problem. Today, out of nowhere(?) the same thing started to happen. First time it just froze up my comp for a couple of seconds and spontaneously rebooted. Then it kept happening every 10 minutes or so. Mostly I was able to switch to a VT, and when I switched back it was alright again.

I'm on a Thinkpad T61, Ubuntu AMD64 with an nVidia Quadro NVS 140M and nvidia 180.44 drivers.
It only seems to happen when 
(a) I have en external monitor connected via DVI, AND
(b) compiz is running (killing compiz from VT and starting metacity fixes the problem for me), AND
(c) firefox running. Actually, clicking a link seemed to triggre it at least 2 times (could ofcourse be a coincidence)

Edit:
Found this bug reported on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371472](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371472)
/N

---

### Post by firebadger on 2009-05-16
I'm having the same problem as the the first two posts, but not the previous post. That seems to be a different problem.

My computer typically starts to flicker (screen goes to black for a fraction of a second) after it has been up and running for a short while. The flickers happen at random intervals of a few seconds to a few minutes.

It is very annoying.

I'm on a Dell XPS M1710 with Nvidia graphics.

I also notice that it doesn't happen with the user account I used for work - thankfully. Makes me think it is some sort of settings issue, but I can't think what.

---

### Post by WakkiTabakki on 2009-05-18
Since upgrading to nVidia drivers 180.53 I've had no more of these problems.
I use this PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)


/N

---

