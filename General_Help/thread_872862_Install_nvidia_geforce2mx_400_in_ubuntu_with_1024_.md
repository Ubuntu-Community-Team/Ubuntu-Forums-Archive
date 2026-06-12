---
title: "Install nvidia geforce2mx 400 in ubuntu with 1024 x 768 resolution to activate compiz"
date: 2008-07-28
forum: General Help
---

### Post by CharlesTowers on 2008-07-28
The thing is like this. Since i installed ubuntu, xubuntu and kubuntu -i tried them all- I have the same issue; i could install the 3d acceleration but i always had 800 x 600 resolution only. And here is the trick to have 3d acceleration and an acceptable resolution: Yes, install the nvidia propietary drivers (this is for xubuntu) by going to:

 ---->applications ---> system ---> Hardware Drivers

Once in there, you'll have to enable the restricted drivers. 

When the job is done, the system will ask you to restart the system, but you'll have to do something before. Open a terminal, and type:

sudo apt-get install nvdidia-settings

Once the installation of this is ok, you can restart your computer.

The first thing you'll notice (Well if you have the same problem i used to have) is that your resolution has changed. Now don't panic, this is very easy to change.

Once you've logged, open a terminal and type: 

sudo nvidia-settings

then, type in your adminstrator password. The nvidia settings should now appear. Now go to the tab that says "nvidia x server display configuration"

once in there, choose your favorite resolution. The screen will flicker and the resolution must be changed. But that's not all. Now you have to press the button that says "save to x configuration file"

Now, to test everything is allright, press this combination of keys:

ctrl+alt+backspace

when you log again, you'll have the selected resolution and 3d acceleration enabled.

---

### Post by northern lights on 2008-07-28
> **CharlesTowers said:**
> sudo nvidia-settings
Please don't. In fact, _never_ run graphical apps with 'sudo'. If you must start a graphical app as superuser, run ```
gksu GRAPHICAL APP
```instead. See [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") for a reference.

Apart from that, you can open nvidia-settings, once installed, from "System > Administration > NVIDIA X Server Settings"

---

### Post by CharlesTowers on 2008-07-29
> **northern lights said:**
> Please don't. In fact, _never_ run graphical apps with 'sudo'. If you must start a graphical app as superuser, run ```
gksu GRAPHICAL APP
```instead. See [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") for a reference.

Apart from that, you can open nvidia-settings, once installed, from "System > Administration > NVIDIA X Server Settings"

I didn't knew that. Thanks for the advice. Hope this post help others, because i searched and couldn't fix my problem. By the way, why is it that you shouldn't run an application in graphical mode as a super user using the terminal?

---

### Post by northern lights on 2008-07-29
> **CharlesTowers said:**
> why is it that you shouldn't run an application in graphical mode as a super user using the terminal?
That's a misconception.
You certainly may run graphical apps as the superuser/root. Just not with 'sudo'.

'sudo' allows a normal user to gain root privileges to do administrative tasks. That's perfectly sufficient if you want to run a shell command that does not have a GUI. If however, you launch a graphical application with 'sudo' The application is launched with root rights but the user's preferences. Launching it with 'gksu' gives you the superuser's preferences also.

Launching graphical apps with 'sudo' may result in a mixup of rights and permissions which is not fun to fix.

---

