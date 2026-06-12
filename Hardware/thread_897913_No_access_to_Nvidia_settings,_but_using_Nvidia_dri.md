---
title: "No access to Nvidia settings, but using Nvidia drivers"
date: 2008-08-22
forum: Hardware
---

### Post by Xan63 on 2008-08-22
Hi,

I'm currently under Hardy 8.04, kernel 2.6.24-19-generic, and using Nvidia drivers 173.14.12 for my 8600GT. I installed them with Envy (after many issues with Compiz). 

I'd like to have a look on Nvidia-settings, but I've got the following message: 
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I've tried to do it, unsuccessfully. However, it seems that i'm using Nvidia drivers, because my compiz effects are running smoothly and I can see the Nvidia screen before login.

thanks by advance for your help!

---

### Post by tturrisi on 2008-08-22
Use synaptic to reinstall nvidia-settings.
run the program:
/usr/bin/nvidia-settings

---

### Post by Xan63 on 2008-08-22
I tried to remove completely nvidia-settings, kill gdm and restart, without effect.

I saw that nvidia-xconfig is not installed (there is just an executable remaining in /usr/bin); but as i'm trying to install it, it  tell me that 
nvidia-glx-new-dev-envy  & nvidia-glx-new-envy will be removed.

I fear it will hose my install of nvidia drivers by envy... 

What could I do? I just get the feeling to walk in a Moebius strip... :confused:

---

### Post by Xan63 on 2008-09-02
[EDIT]
Issue solved, I just removed xgl-server, reboot and I'm now able to access to nvidia-settings!

Thansk to Qba [here]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/#comment-8145")

:biggrin:

---

