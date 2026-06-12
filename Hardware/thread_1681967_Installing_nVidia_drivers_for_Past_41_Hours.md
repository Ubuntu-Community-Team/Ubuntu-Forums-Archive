---
title: "Installing nVidia drivers for Past 41 Hours"
date: 2011-02-05
forum: Hardware
---

### Post by ahsan101 on 2011-02-05
Hi everyone, just another new to ubuntu migrated from Windows.... I enjoyed allot using it .... But what has caused headache is nVidia driver, i searched everything everywhere , tried each and every step told in all the forums, googled well but still have no success...

My nvidia card is Geforce4 Mx 440 , and the error it gives is "The Nouveau Kernel driver is currently in use..." , so i searched allot on how to stop it or remove it, i followed every step in these forums, but i have no success, i went in recovery mode also but no success, tried "sudo /etc/init.d/lxdm stop" , brought me into the Terminal from there still can't, blacklisted the nouveau kernel in /etc/modprobe.d/blacklist.conf , rebooted !! but still no success ... so i am posting here for someone to help me out :) and hopefully someone will do this :) ...Thanks in advance and thanks to Linux :) :p

---

### Post by sikander3786 on 2011-02-05
Welcome to the forums :-)

I hope you are running Ubuntu 10.10 Maverick and the Nvidia driver was broken. For a workaround, see here.

[http://ubuntulifeblog.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html](http://ubuntulifeblog.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html)

---

### Post by ahsan101 on 2011-02-05
Thank you for welcoming me... I have done the following, 

root@Game1:~$ sudo service lxdm stop

it brought me into the terminal..
then i entered

root@Game1:~$ sh NVIDIA.run -z

(-z to disable nouveau check)...

but alas i came up with another error, after compiling the kernel it says

Unable to load the kernel module 'nvidia.ko'...


:(

---

### Post by gradinaruvasile on 2011-02-05
Disable nouveau by adding it to the /etc/modprobe.d/blacklist.conf
Then install the appropiate driver for your card - 96.4319 from nvidias site.

---

### Post by ahsan101 on 2011-02-05
Well i have installed it successfully, using the following command,

sh NVIDIA.run -k $(uname -r) -z


but another problem :( it didn't gave me a display on rebooting.... then i came into the recovery mode and restored the backed-up configurations of the X, now when i am in X, when i point to System tools i have a new option there, NVIDIA X Server settings, but how do i know which am i running? Nvidia or the old one... i think its something like lspci | grep vga...

---

### Post by ahsan101 on 2011-02-05
> **gradinaruvasile said:**
> Disable nouveau by adding it to the /etc/modprobe.d/blacklist.conf
Then install the appropiate driver for your card - 96.4319 from nvidias site.

I have done that before, i have successfully installed it but it didn't gave me a display at reboot..  Now when i come to my System Profiler and Benchmark , i don't have OpenGL, it says Unknown next to the OpenGL.... :(

---

### Post by Sylos on 2011-02-05
Hello there.

Can you post the contents of your xorg.conf please. If the propoer NVIDIA driver has installed then we should be able to point to it rather than nouveau from the conf file.

```
gksudo gedit /etc/X11/xorg.conf
```

I believe that should bring it up. Dont save anything over it - just copy an paste the contents.

---

### Post by ahsan101 on 2011-02-05
> **Sylos said:**
> Hello there.

Can you post the contents of your xorg.conf please. If the propoer NVIDIA driver has installed then we should be able to point to it rather than nouveau from the conf file.

```
gksudo gedit /etc/X11/xorg.conf
```

I believe that should bring it up. Dont save anything over it - just copy an paste the contents.
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted


Gives me this error when i execute gksudo gedit /etc/X11/xorg.conf .

---

### Post by ahsan101 on 2011-02-05
Somehow i opened the xorg.conf file, but it is completely blank, i used xhost +SI:localuser:ahsan to open the xorg.conf . then i used your command but its blank file.

---

### Post by ahsan101 on 2011-02-05
This is all what i have in my X11 directory,


ahsan@Game1:/etc/X11$ ls -a
.                        rgb.txt                        Xreset.d
..                       X                              Xresources
app-defaults             xinit                          Xsession
cursors                  xkb                            Xsession.d
default-display-manager  xorg.conf-backup-110205140621  Xsession.options
fonts                    xorg.conf.failsafe             Xwrapper.config
openbox                  Xreset

---

### Post by Sylos on 2011-02-05
Aah yes - my apologies - by default no xorg.conf is created in the newer incarnations. 

Not to worry - if you create one it will still be used. Just a shame we have to create one for it.

I struggle to remember how to do one from scratch.

Lets try this....

```
gksudo nvidia-settings
```

This should open up the nvidia settings tool. If it does change a couple of settings from what they are to something else and then back again. Then click on the button to save to x (something like that). Hopefully this will save the basic info into the xorg.conf file.

Close the nvidia settings window and try to open the xorg.conf again.

---

### Post by ahsan101 on 2011-02-05
> **Sylos said:**
> Aah yes - my apologies - by default no xorg.conf is created in the newer incarnations. 

Not to worry - if you create one it will still be used. Just a shame we have to create one for it.

I struggle to remember how to do one from scratch.

Lets try this....

```
gksudo nvidia-settings
```

This should open up the nvidia settings tool. If it does change a couple of settings from what they are to something else and then back again. Then click on the button to save to x (something like that). Hopefully this will save the basic info into the xorg.conf file.

Close the nvidia settings window and try to open the xorg.conf again.
Got this


root@Game1:/home/ahsan# gksudo nvidia-settings
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted

---

### Post by Sylos on 2011-02-05
> **ahsan101 said:**
> Got this


root@Game1:/home/ahsan# gksudo nvidia-settings
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted

Sorry - That is above my station. I may be the "blind leading the blind" here.

I'll research and see if I can come up with any insights and post back with what I find.

---

### Post by Sylos on 2011-02-05
What OS version are you running?

---

### Post by Sylos on 2011-02-05
Did you definitely launch as sudo?

---

### Post by Sylos on 2011-02-09
If your still fighting with this I had another thought regarding the error you are getting.

Maybe the error is beause when you installed manually you didnt have the Glib stuff installed for it to build against - hence the error when trying to load the app.

You could try installing the build-essential packages first and then remove all the nvidia modules and reinstall them.

---

