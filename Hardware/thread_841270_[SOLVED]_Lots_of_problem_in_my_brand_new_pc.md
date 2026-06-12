---
title: "[SOLVED] Lots of problem in my brand new pc"
date: 2008-06-26
forum: Hardware
---

### Post by Cerberus108 on 2008-06-26
Hello, I have lots of annoying problems on my brand-new pc, and I am hoping someone will be able to help me... 

Here is my computer configuration:

CPU: AMD Phenom 9750 (AM2+ Quad-core)
Mainboard: ASUS M3A78-EH with AMD 780G chipset
VGA: ATI HD 3650 512MB
OS: UbuntuStudio 8.04 updated with hardy-proposed

I was very excited when I installed UbuntuStudio, hoping I'd play many games such Nexuiz, Warsow or other 3D apps like Blender. Yes, at the beginning it worked, but i experienced some delay with the cursor movements, so I decided to install the official ATI driver. Unfortunately, restarting X11, I got some strange errors, bonded (since I'm not English i don't know if it's the right word) with a "Signal 11" error... So, goodbye fglrx and 3D acceleration. For comfort of reading, I'm listing my problems: 
[LIST=1]
[*]As above, fglrx doesn't work and I don't know how to remove it (the ATI installer does not provide an uninstall feature)
[*]Even with atl2-source package installed, the system doesn't recognize my network adapter, although I have an eth0 device. Moreover, if I set eth0 in roaming mode, nm-applet won't show me the connection handshake animation, and it won't connect to the net.
[*]The frequency modifier gnome applet doesn't work, even with Cool'n'quiet enabled
[*]None of the processor sensors is recognized from the system
[*]Boot time, shutdown time, applications open time is IDENTICAL to my old pc's one... Very annoying, since my old CPU was an AMD Sempron solo core...
[*]By setting a domain in network-admin I get a "unable to resolve host" error when running sudo commands in terminal
[/LIST]

I hope someone will help me: it's frustrating to see Windows run perfectly and Ubuntu panting on the same computer.

Thanks in advance!

---

### Post by Odrodzona-Sarmacja on 2008-06-26
It looks to me like you need to boot in recovery mode and fix x-server. The file you are going to be interested when doing patching this problem is : "/etc/X11/xorg.conf". Also check in "/var/log/syslog" for any possible hints about this. Good luck!

---

### Post by Cerberus108 on 2008-06-26
Ok, nevermind about X11 issues, I restored order by installing Envy's ATI driver.. Anyways, remaining problems are still unsolved. Thank you in advance for any answer!

---

### Post by AFarris01 on 2008-08-06
Im sorry you're having so many issues with your machine under Ubuntu... and im sorry so few have been able to help you out so far to resolve these issues after so long, but hopefully i can do something for you.  I suppose I'll just go on down the line with your issues, and see what i can do:

1. I see that you've already fixed issue 1, so congrats!
2. open a terminal and run the command: 
       lspci
and paste the output here.  this will give more info about the devices installed on your computer, which will allow for more device-specific help to be given for the network adapter.
3. i believe that the frequency modifier app that you're referring to requires an additional package to be installed to make them work for some CPUs (which seems to be the case in your situation)...Unfortunately i dont remember the name of the package, and Im not at my Ubuntu box right now, but when i get home, i'll update with the name of the package.
4. by processor sensors, do you mean temperature sensors/voltage sensors, etc?  I've never really been one to overclock or anything, so Ive never been too terribly concerned with things like this, but i've seen a lot of people recommend an app called "gkrellm" as an answer to that.  to get it, make sure you're universe repository is enabled and search for it in synaptic, or punch this into a terminal:
     sudo apt-get gkrellm
5. The boot time of any OS is influenced most by what you are loading at start-up, rather than your hardware.  That said, there are a number of ways to speed up your booting process, some simple, like unchecking services you don't need from the Sessions manager (System>Preferences>Sessions  i believe), to less-simple, or quite complicated system tweaks (just as with tweaking whinedohs).  Personally, I've trimmed my boot time from push-button to login screen to 8 seconds (I don't dual boot or anything, so no grub menu :)) by following a few pretty nice guides i found online.  I have a link bookmarked at home to a pretty good ubuntu tweaking page that specifically targets streamlining the system boot and operation, but i cant find it here, so when i get home, ill post that link here too.  
6. Im not entirely clear on what you mean by this item, but i have a feeling that the issue is probably linked with your issue #2: seeing as how your system doesn't recognize the network adapter, this probably means that you don't have any internet access, which could explain the 'unable to resolve host' error.  but as i said, im not entirely clear on what exactly was happening, but if you could maybe give more details on that, it might be helpful.

i hope that you find (at least some of) this information helpful!

Andrew

---

### Post by Cerberus108 on 2008-08-24
Thank you for trying to help me, Andrew! (and sorry for my delay in answering). Fortunately, by doing a clean re-install of ubuntu, the second problem (the one related to the network) seems to be solved. Although, by installing and adequately configuring the "sensors" package I was able to have all MB sensors recognized. 

About the 5th and 6th, it seems helpless, so I won't mind. 

Anyways, thank you a lot for the interest!

---

