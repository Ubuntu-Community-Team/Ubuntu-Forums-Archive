---
title: "Problem with detecting Intel Wireless-N 1030"
date: 2011-03-31
forum: Hardware
---

### Post by ablmf on 2011-03-31
I've got a new dell laptop with Intel Wireless-N 1030 adapter.  I'm pretty sure about this.

After install ubuntu, I found that this wireless adapter is not detected.

```

eth0      Link encap:Ethernet  HWaddr 14:fe:b5:9b:b9:ae  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::16fe:b5ff:fe9b:b9ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4847774 (4.8 MB)  TX bytes:881864 (881.8 KB)
          Interrupt:40 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

After Google this for a whole night, it seems the kernel I'm using is too old and 2.6.38 includes the newest driver.  However, after I successfully updated, nothing changed.  The current kernel:

```

2.6.34-020638-generic

```

Here's result of `lspci -v`

```

01:00.0 Network controller: Intel Corporation Device 008a (rev 34)
	Subsystem: Intel Corporation Device 5325
	Flags: fast devsel, IRQ 16
	Memory at d1600000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel modules: iwlagn

```

Any suggestion?

---

### Post by Knight of Cydonia on 2011-03-31
I think I'm having the exact same wireless card in my new Dell, Vostro 3750, and would REALLY appreciate some professional help here, I'm getting desperate (after two days of trying every online guide I could find), and considering ditching ubuntu, little point to an OS that I can't have internet access one (wired is not an option). :(

---

### Post by ablmf on 2011-03-31
> **Knight of Cydonia said:**
> I think I'm having the exact same wireless card in my new Dell, Vostro 3750, and would REALLY appreciate some professional help here, I'm getting desperate (after two days of trying every online guide I could find), and considering ditching ubuntu, little point to an OS that I can't have internet access one (wired is not an option). :(

If you are sure you have the same adapter, I've some good news for you.

Mine works!

Here's what I did :

1. Update kernel to 2.6.38 (I don't know if it's necessary, but try it)

[http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/](http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/)

2. Update everything by software update manager.

For me, everything works fine now!

---

### Post by Knight of Cydonia on 2011-03-31
Sadly that won't work for me, I have no immediate access to a wired connection, why can't I for once get ubuntu to give me wireless out of the box, this is the third laptop where I've had wireless issues on (none of the previous methods work).

---

### Post by andersonvom on 2011-04-02
> **ablmf said:**
> If you are sure you have the same adapter, I've some good news for you.

Mine works!

Here's what I did :

1. Update kernel to 2.6.38 (I don't know if it's necessary, but try it)

[http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/](http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/)

2. Update everything by software update manager.

For me, everything works fine now!

That worked perfectly! Thanks!

---

### Post by blimeyrob on 2011-04-07
Everyting works perfectly now. The Wireless and thevideo adaptor seems better now too!. Thanks heaps, spent all day trying to get the wireless to work and this took no time at all. You rock!

---

### Post by aeronutt on 2011-04-16
> **ablmf said:**
> If you are sure you have the same adapter, I've some good news for you.

Mine works!

Here's what I did :

1. Update kernel to 2.6.38 (I don't know if it's necessary, but try it)

[http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/](http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/)

2. Update everything by software update manager.

For me, everything works fine now!

I just purchased a dell vostro 3550 with an Intel 1030 network card, and I can't get wireless to work under either 10.04 or 10.10.  I tried the above:
  sudo add-apt-repository ppa:kernel-ppa/ppa
  sudo apt-get update
  sudo apt-get install linux-headers-2.6.38-1-generic linux-image-2.6.38-1-generic

But when I run apt-get install, it says that "...2.6.38..." is not available.

Help, i don't want to have to use windows!! :)

---

### Post by aeronutt on 2011-04-16
FYI, I downloaded the latest compiled kernals 2.6.38 from ubuntu (debs), and now wireless works. Touchpad is not recognized though.

---

### Post by zanuxzan on 2011-04-19
I recently purchased a Dell 15r (N5110) which has an Intel Centrino Wireless-N 1030.

I was able to get this working on Ubuntu Maverick Meerkat 10.10 by installing the following packages and then rebooting:

[LIST]
[*]linux-backports-modules-compat-wireless-2.6.37-maverick-generic-pae
[*]linux-backports-modules-compat-wireless-2.6.37-2.6.35-28-generic-pae
[/LIST]

Note that this didn't stop my touchpad from working, however I am yet to find a simple solution to get my touchpad scrolling functionality working.

---

### Post by aeronutt on 2011-04-19
Thanks for the info. I've tried about 5 different kernal loads on 10.10, and have yet to get all of the following 3 things working:

- wireless connection
- graphics support using fglrx
- scroll on mousepad

A bit frustrating...and actually, fglrx doesn't work with any of the combinations I've tried. So right now with 10.10, I have wireless working, but not fglrx and no pad scroll.

Using 11.04 beta, wireless and pad scroll work, but fglrx doesn't (known issue). And when I try fglrx, it fails to boot, even after I remove fglrx (under limited graphics mode). Here's to hoping that on final release of 11.04 in a few weeks, fglrx will be updated in time.

---

### Post by donalgodon on 2011-04-26
What is fglrx?

I just ordered this model specifically for Ubuntu use, so I'm hoping all goes well, but is there a specific driver issue yet unresolved?

BTW, whoever designed this model for Dell should be fired then shot.

Removing the logic board and display assembly to replace the hard drive?!

---

### Post by aeronutt on 2011-04-27
fglrx is a proprietary AMD driver for AMD Radeon graphics cards, which I have, but the driver doesn't work with my card, and ubuntu (yet). I've read that it's supposed to be updated  by 28 apr for 11.04 release. We'll see. 

Wireless and ethernet has been working under 11.04 beta for me (but I have tons of other problems with beta...so I'm not using that anymore).

For 10.10, I had to update the kernel to get wirless to work. So here's my most current usable Ubuntu for my laptop.(But this setup doesn't use the Radeon graphics card, and I don't believe it's using the Intel Sandy Bridge graphics that I have either.)

10.10 with the kernel version updated to 2.6.38-02063802-generic

Here are the most recent builds for 2.6.38 kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/)

---

### Post by donalgodon on 2011-04-27
So, you have this model but with Radeon Graphics? 

I just bought the standard Intel graphics, because I'm not a gamer, but does that mean that the Natty drivers don't support accelerated graphics on the Intel chip yet either?

Have you tried the daily builds to see if there was any improvement? 

I've noticed that .39 kernel is in RC4 at this point. If I can't get the daily build to work, I might take a stab at the RC.

As of this moment, we have 24 hours to wait for Natty!

Fingers crossed.

---

### Post by aeronutt on 2011-04-27
Yes, new Dell Vostro 3550 has an AMD Radeon HD 6630M  Graphic Card. Plus, the integrated graphics of the Intel Sandy Bridge i3 processor. From my experience and random searches on the web and forums, here's my understanding of where things are.

10.04 LTS: 
- nothing much works on my laptop. (But this is understandable with the newer technologies in my laptop.)

10.10: 
- neither my intel or AMD graphics is supported
- even surfing some web sites (flash, other) performance is terrible.
- Intel wireless-n 1030 card doesn't work with standard kernel, but does work when I install one of the kernels for Natty/11.04
- touchpad works, but isn't recognized as a touchpad , only as a generic mouse (eg no scroll).
- during boot, it often gets stuck in a "*ERROR* atombios stuck" loop...for 5-10 interactions at 5 seconds per iteration. But oddly, most of the time, finds its way out of that loop and boots successfully.

11.04 beta: 
- graphics performance is better than in 10.10. BUT, in beta, AMD proprietary driver for my Radeon does not work. So I'm unsure if 11.04 beta is: a) using intel graphics, b) using open driver for Radeon graphics, or c) graphics performance is ok simply from the i3 processor.
- wireless works out of the box (unlike 10.10)
- touchpad is not recognized as a touchpad, but... oddly...scroll works.
- Unity performance is 'not good' eg, typing into the application search-box is terrible, screen lags keyboard input by several seconds.
- and...this load is extremely unstable on my laptop. Fails to boot 9 out of 10 times. Gets hung at various random points in the boot process.

Here's what I've read looking forward.
- AMD proprietary driver for Radeon Graphics is supposed to be updated by 11.04 release date (tomorrow!). Here's to hoping it works for my Radeon HD 6630M.
- Sandy Bridge architecture may not be well supported until 11.10 release.

That's what I've read anyway.

As of right now, Windows 7 has far better management of Sandy-Bridge graphics and Radeon Graphics capabilities. The 2 work together, and the user can define which will be used depending on various things like: battery vs AC, application, etc.

Fingers also crossed that final release of Natty will 
- support AMD Radeon
- recognize my touchpad
- boot reliably
- somewhat support sandy bridge

Honestly, I'm not hopeful. I tried a daily build 2 days ago...and now can't boot into 11.04. But, I am patiently waiting.

---

### Post by Yellow Pasque on 2011-04-27
@aeronutt: Quite simply, you're screwed because of the hybrid graphics. You may be able to get the open-source radeon driver working with vga_switcheroo script, but it's not pretty.

Return the laptop if you can. In mean time, purge fglrx, as it's useless: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by donalgodon on 2011-04-27
That's why I bought the N5110 model only.

Is the standard Intel Sandy Bridge graphics chip supported fully at this point?

---

### Post by aeronutt on 2011-04-27
> **Temüjin said:**
> @aeronutt: Quite simply, you're screwed because of the hybrid graphics. You may be able to get the open-source radeon driver working with vga_switcheroo script, but it's not pretty.

Return the laptop if you can. In mean time, purge fglrx, as it's useless: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Well....that's not good news. Although I'm not screwed, I can use Windows. One would think this problem (dual graphics) is not a problem to be ignored with the trend of integrated graphics and continued need to have high-end graphics.

But I need clarification...using Linux and a setup like mine (integrated + discrete graphics), is there no way to get ONE of them working?

---

### Post by Yellow Pasque on 2011-04-27
You can get the Intel one working. It should work on 11.04 without any hacking (though you may get a better experience with the xorg-edgers PPA). Like I said, purge fglrx to get your default graphics setup back.

---

### Post by aeronutt on 2011-04-27
> **Temüjin said:**
> You can get the Intel one working. It should work on 11.04 without any hacking (though you may get a better experience with the xorg-edgers PPA). Like I said, purge fglrx to get your default graphics setup back.

Thanks much!  I'll probably keep the laptop, and if I need the performance of the AMD discrete graphics....just...gulp...log into Windows. (May also try playing with the vga-switcheroo..thanks for the link. I don't mind fiddling.)

---

### Post by donalgodon on 2011-04-27
Just got the n5110 today and I cant' get it to boot from a Natty live USB even after setting the BIOS to use it.

Strange.

---

### Post by aeronutt on 2011-04-27
FYI, I have the same problem with my vostro, natty won't boot from USB. But will from CD.

---

### Post by Yellow Pasque on 2011-04-27
For USB, you did add this to the boot line, right?:
```
cdrom-detect/try-usb=true
```

---

### Post by donalgodon on 2011-04-27
FWIW, the 5110 is working GREAT!

Literally everything works out of the box.

---

### Post by FredTheKat on 2012-01-26
When I execute this command: sudo apt-get install linux-headers-2.6.38-1-generic linux-image-2.6.38-1-generic
 
I get this error: E: couldn't find package linux-headers-2.6.38-1-generic 
 
I am completely new to Linux/Ubuntu. Why would a kernel update not be something that could be done from the Update Manager? My laptop is useless without a wireless network connection.
 
At this point, I'm just a button pushing monkey, knowing nothing about Ubuntu. I'll take the time to learn all the command line stuff, but for now I just need to get the thing working.

---

### Post by RahulChhabra on 2012-08-20
It worked.. It worked.. Yeepee :guitar:

---

