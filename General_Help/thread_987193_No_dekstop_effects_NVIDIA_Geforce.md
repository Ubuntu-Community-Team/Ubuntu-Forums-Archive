---
title: "No dekstop effects NVIDIA Geforce"
date: 2008-11-19
forum: General Help
---

### Post by flashmxboy on 2008-11-19
Okay...

I am a bit newbie to ubuntu. I use ubuntu 8.10 and my graphics card is a NVIDIA Geforce 8600M GS. I am in a laptop btw.
I saw some funny videos on youtube about amazing effects in ubuntu and did some research about it.:) Then i tried to activate desktop effects and got a really annoying error:confused:. It says:

Desktop effects could not be enabled.

It says no more than that.:confused: So i thought out i needed some more info.
I downloaded and ran compiz check ([http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")).
This is the output i got:
```
ubuntu@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600M GS (rev a1)
 Driver in use:         nv
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: nv driver in use 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 
```

Can anyone please help me with this?

Thanks:KS

---

### Post by JuL.LeVi on 2008-11-19
hi flashmxboy,

Try this way,

- go to System --> Administration ---> Hardware Drivers
- carefully check the list. If Ubuntu 8.10 finds your graphic card, it must be shown up here. If so, just check the box, then active . Wait for moment , then Reboot

Hope this works 

P/S , and I also want to make sure that you don't use Ubuntu in a Virtual MAchine ( for example , created by VMware or Qemu ) 

JuL

---

### Post by eternalnewbee on 2008-11-19
> go to System --> Administration ---> Hardware Drivers
Add **Main Menu**, before System , to avoid confusion

---

### Post by flashmxboy on 2008-11-19
Thanks guys but no luck here:(

On the hardware drivers 2 drivers showed up...
I tried both but still the error:confused::

Desktop effects could not be enabled

Btw my compiz-config output is now:```
ubuntu@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600M GS (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

```

Im not running in a virtual machine. Real ubuntu:KS

---

### Post by eternalnewbee on 2008-11-19
OK. I found this link which might be helpful to you:
[http://packages.ubuntu.com/intrepid/i386/nvidia-glx-173/download](http://packages.ubuntu.com/intrepid/i386/nvidia-glx-173/download)
If you have problems understanding it, post here, and myself or another member will try our best to assist you.

---

### Post by flashmxboy on 2008-11-19
Hmm bad luck again:(
I installed the deb eternalnewbee linked to, and restarted my system. Then i tried to activate desktop effects but no luck. Again i got:

Desktop effects could not be enabled:mad:

Again i post my compiz-check output just in case it might help```
ubuntu@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600M GS (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

```

Thanks to anyone that helps me and anyone that wants to help:KS

---

### Post by Twitch6000 on 2008-11-19
Ok first can you please tell us if you are using ubuntu in a virtual machine like virtual box,vmware,or anything like that?

If so you will not be able to get 3D effects in a Virtual machine.

If not however try this, uninstall all the nvidia drivers you have already installed(I know I know weird).

Then logout and log back in(you don't need to fully restart).

Ok now go to hardware drivers and pick the nvidia driver that has recommended above it.

After that then restart or restart x server.

Now see if everything is working.

If not install envy and get the latest driver for your nvidia and then try again.


Note: Normally after installing the driver and restarting x server everything works >.>.

---

### Post by flashmxboy on 2008-11-20
Ok im not running under a virtual machine...

But when i install the driver that is recommended it still says

Desktop effects could not be enabled

And when i check in the hardware drivers again it says when i clik the driver i just installed it says:

A different version of this driver is in use

---

### Post by eternalnewbee on 2008-11-21
OK. The best site where you can help (my personal opinion) is here:
[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

---

