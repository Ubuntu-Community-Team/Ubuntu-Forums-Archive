---
title: "[SOLVED] Firewall?"
date: 2008-08-21
forum: General Help
---

### Post by Yezinki on 2008-08-21
Hi there,

Is there a firewall in Ubuntu Hardy Heron.........& if yes where........& how does  one configure it?

Thanks.

---

### Post by brian_p on 2008-08-21
> **Yezinki said:**
> Hi there,

Is there a firewall in Ubuntu Hardy Heron.........& if yes where........& how does  one configure it?

Thanks.

Yes - iptables, a kernel module. Yes - use ufw, it is already installed.

Considering I answered your question perhaps you might answer mine. Has searching these forums gone out of fashion?

---

### Post by tuxxy on 2008-08-21
Open a terminal and type

```
ufw
```

this will show you the usage command

---

### Post by Yezinki on 2008-08-21
> **brian_p said:**
> Yes - iptables, a kernel module. Yes - use ufw, it is already installed.

Considering I answered your question perhaps you might answer mine. Has searching these forums gone out of fashion?


Hi there,

Considering you answered ok (hopefully), searching is in fashion but not for newbies.

Regards!

---

### Post by Yezinki on 2008-08-21
> **tuxxy said:**
> Open a terminal and type

```
ufw
```

this will show you the usage command

Thanks alot..........

ubuntu@ubuntu-laptop:~$ ufw

Usage: ufw COMMAND

Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by WRDN on 2008-08-21
iptables, the firewall is already enabled by default, but ufw (Uncomplicated Firewall) is not, and is just a configuration layer. If you want to use a GUI, you may consider Firestarter (outdated).

---

### Post by brian_p on 2008-08-21
> **Yezinki said:**
> Hi there,

Considering you answered ok (hopefully), searching is in fashion but not for newbies.

Regards!

You're not alone! And my response is spot on. Which you could verify by ..... Guess what?

---

### Post by mb_webguy on 2008-08-21
The question is not does Ubuntu have a firewall, but rather do you need to use it.  You may want to check the "Security on Ubuntu" link in my signature before you start fiddling with the firewall settings.

---

### Post by Yezinki on 2008-08-21
Thanks mb_webguy,

You are one smart, genius, humble gentleman, having indepth knowledge about what you are talking about.

I appreciate what you have taught me in a few days with Ubuntu.

Regards!

---

### Post by Yezinki on 2008-08-21
At thhe moment how do you see my firewall status?

I prefer Kubuntu..........which versionnn should I install?

Thanks again!

---

### Post by WRDN on 2008-08-21
If you are using UFW, type:

```
sudo ufw status
```

If you use Firestarter, click System > Administration > Firestarter

The status is listed on the "Status" tab.

---

### Post by Yezinki on 2008-08-21
ubuntu@ubuntu-laptop:~$ sudo ufw status
[sudo] password for ubuntu: 
Firewall not loaded
ubuntu@ubuntu-laptop:~$

---

### Post by rampageoberon on 2008-08-21
So you have no rules enabled in ufw. By default ubuntu has no ports open so you should be quite secure unless you have installed any daemons/servers which will open up the associated ports.

---

### Post by Yezinki on 2008-08-22
It says Firewall not loaded, when I typed sudo ufw status in terminal.......is that normal?

---

### Post by adult swim on 2008-08-22
yes your firewall, iptables is on.  when it says that the firewall is not loaded, it means that iptables isnt currently being manipulated by ufw.  if you would like to use ufw to control your firewall (which is already on with ports closed by default) you can run sudo ufw enable.

---

### Post by Yezinki on 2008-08-22
Thanks adult swim,

Your reply was very concise & clear!

---

