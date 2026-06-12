---
title: "Reinstalling network manager"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Earl-Grey on 2009-11-08
[color=#FF0777]Is there a way of recovering deleted programs without connecting to the internet or using a live CD.

I foolishly deleted the Network Manager and now I can’t access the internet at tall. I don’t have a CD drive to use a live CD to reinstall it.

Is there a way of downloading the Network Manager in a form of a .exe file or something in Windows, save it to USB memory and reinstall it in Ubuntu?[/color]

---

### Post by iponeverything on 2009-11-08
> **Earl-Grey said:**
> [color=#FF0777]Is there a way of recovering deleted programs without connecting to the internet or using a live CD.

I foolishly deleted the Network Manager and now I can’t access the internet at tall. I don’t have a CD drive to use a live CD to reinstall it.

Is there a way of downloading the Network Manager in a form of a .exe file or something in Windows, save it to USB memory and reinstall it in Ubuntu?[/color]

from the prompt:

```

cd /var/cache/apt/archives
sudo dpkg -i network-manager-gnome*

```

---

### Post by Earl-Grey on 2009-11-08
> **iponeverything said:**
> from the prompt:

```

cd /var/cache/apt/archives
sudo dpkg -i network-manager-gnome*

```

[COLOR=#ff0777]
I can't believe that it is as simple as that. I will give it a go now, thank you.[/color]

---

### Post by Earl-Grey on 2009-11-08
[COLOR=#ff0777]I tried the code but no luck :-P

```
dpkg: error processing network-manager-gnome* (--install):

 cannot access archive: No such file or directory

Errors were encountered while processing:

 network-manager-gnome*


```I found this link [http://ns2.canonical.com/karmic/i386/network-manager/download](http://ns2.canonical.com/karmic/i386/network-manager/download) which has the Network Manager, and hopefully can get it to work.

Couldn't get it to work, as far as I know you can't get it to work by just downloading it, it has to be done through Ubuntu.

There are quite a lot of versions of the Network Manager and I might be downloading the wrong one, so I am going to try all of them. 

[/COLOR][network-manager]("http://ns2.canonical.com/karmic/i386/net/network-manager") (0.8~a~git.20091013t193206.679d548-0ubuntu1)network management framework daemon[network-manager-dev]("http://ns2.canonical.com/karmic/i386/net/network-manager-dev") (0.8~a~git.20091013t193206.679d548-0ubuntu1)network management framework (development files)[network-manager-gnome]("http://ns2.canonical.com/karmic/i386/net/network-manager-gnome") (0.8~a~git.20091014t134532.4033e62-0ubuntu1)network management framework (GNOME frontend)[network-manager-openconnect]("http://ns2.canonical.com/karmic/i386/net/network-manager-openconnect") (0.8~a~git.20090828t161429.dfe1b50-0ubuntu2) [**universe**]network management framework (Openconnect plugin)[network-manager-openvpn]("http://ns2.canonical.com/karmic/i386/net/network-manager-openvpn") (0.8~a~git.20091008t123607.7c184a9-0ubuntu1) [**universe**]network management framework (OpenVPN plugin)[network-manager-pptp]("http://ns2.canonical.com/karmic/i386/net/network-manager-pptp") (0.8~a~git.20091013t190309.0c39c37-0ubuntu1) [**universe**]network management framework (PPTP plugin)[network-manager-strongswan]("http://ns2.canonical.com/karmic/i386/net/network-manager-strongswan") (1.1.1-2ubuntu1) [**universe**]network management framework (strongSwan plugin)[network-manager-vpnc]("http://ns2.canonical.com/karmic/i386/net/network-manager-vpnc") (0.8~a~git.20091008t124012.f5b95a2-0ubuntu1) [**universe**]network management framework (VPNC plugin)

---

### Post by Earl-Grey on 2009-11-09
[COLOR=#ff0777]I got it to work by downloading the [network-manager-gnome]("http://ns2.canonical.com/karmic/i386/net/network-manager-gnome") file, saving it to my USB drive in Windows and then running the file in Ubuntu. Thank you to everybody who tried to help me :KS [/COLOR]

---

### Post by jdholman on 2010-01-23
This was a brutal, brutal error to fix.  On my wife's former-Vista-now-Ubuntu-Karmic laptop, I wanted to assign a fixed IP address for her wireless, but this doesn't work in NetworkManager without hacking the config files.

I read that this does work in wicd, so I installed that.  What I didn't know is that installing wicd uninstalls network-manager.  wicd didn't work for me, so I uninstalled it.

Now I had no network!!  No wicd _**and**_ no network-manager!!!  Trying to reinstall via Synaptic Manager using the live CD didn't work either.  What now!?!?

Luckily I had another PC with internet access, found this thread and was able to download network-manager and network-manager-gnome and reload from removable storage.

Here are more specific links in case anyone else needs to recover from this.

[http://ns2.canonical.com/karmic/i386/network-manager/download]("http://ns2.canonical.com/karmic/i386/network-manager/download")

[http://ns2.canonical.com/karmic/i386/network-manager-gnome/download]("http://ns2.canonical.com/karmic/i386/network-manager-gnome/download")

I know I blew this up myself, but I was surprised how difficult the recovery was of so critical an item.  At least I am working again.

Jim

---

### Post by akand074 on 2010-01-27
wrote in the wrong thread -_-' sorry!
[]("http://ns2.canonical.com/karmic/i386/net/network-manager-gnome")

---

### Post by colferma on 2010-04-05
many thanks for that jdholman, you saved my skin!

---

### Post by gatordude on 2010-05-23
JUst wanted to say thanks for your hard work on this. It helped me fix my problem after trying Wicd.

I also had errors when I tried the first fix. 
```
cd /var/cache/apt/archives
sudo dpkg -i network-manager-gnome*
```

I had to use the links provided by jdholman.
Just remember to install the packages in order. 
1. network manager 2. Network manager gnome.

Interestingly enough. Before I reinstalled the packages, Network Manager was still listed in my StartUp Preferences. The command line was set to "nm-applet --disable". I was foolish enough to think that changing disable to enable would fix it.
Now I have to get back to fixing my intranet issue.

---

### Post by jumbuck on 2010-06-26
A huge thanks from me as well , Jim. Your on my chrissy list to receive lotsa beer :-).

---

### Post by GlammaGeek on 2011-07-28
> **jdholman said:**
> This was a brutal, brutal error to fix.  On my wife's former-Vista-now-Ubuntu-Karmic laptop, I wanted to assign a fixed IP address for her wireless, but this doesn't work in NetworkManager without hacking the config files.

I read that this does work in wicd, so I installed that.  What I didn't know is that installing wicd uninstalls network-manager.  wicd didn't work for me, so I uninstalled it.

Now I had no network!!  No wicd _**and**_ no network-manager!!!  Trying to reinstall via Synaptic Manager using the live CD didn't work either.  What now!?!?

Luckily I had another PC with internet access, found this thread and was able to download network-manager and network-manager-gnome and reload from removable storage.

Here are more specific links in case anyone else needs to recover from this.

[http://ns2.canonical.com/karmic/i386/network-manager/download](http://ns2.canonical.com/karmic/i386/network-manager/download)

[http://ns2.canonical.com/karmic/i386/network-manager-gnome/download](http://ns2.canonical.com/karmic/i386/network-manager-gnome/download)

I know I blew this up myself, but I was surprised how difficult the recovery was of so critical an item.  At least I am working again.

Jim

I am about 4 months into a dual boot with Ubuntu 11.04 and Win 7 both x64 on both my Sony laptop and Hubby's desktop built my yours truly.  Apparently, after I removed the Wireless card from his desktop, it broke the network manager(s).  (THIS HAS GOT TO BE A BUG.) So, like an ID 10 T, what did I do?  Yep!  Remove the network managers.  Completely!  Then, when I followed all of the other advice and nothing worked, I became obsessed with fixing it before I could sleep.  Thank God I found this solution.

Thanks Jim!  

The links were dead!!! Arrgggghhhh!  So, in my obsession to fix the problem, I replaced the word "karmic" in your links with the word "natty".  That did the job!!  Again, because Hubby's system is x64, the links that worked were:

[http://ns2.canonical.com/natty/amd64/network-manager/download]("http://ns2.canonical.com/karmic/i386/network-manager/download")

[http://ns2.canonical.com/]("http://ns2.canonical.com/karmic/i386/network-manager-gnome/download")[natty/amd64]("http://ns2.canonical.com/karmic/i386/network-manager/download")[/network-manager-gnome/download]("http://ns2.canonical.com/karmic/i386/network-manager-gnome/download")

I didn't test it, but for those with 32-bit systems, I'd guess that if "amd64" was replaced with "i386" in the links above, it should work just as well.

Did I say THANK YOU?!!?  Now, I can get some sleep.  In about an hour or so...

---

