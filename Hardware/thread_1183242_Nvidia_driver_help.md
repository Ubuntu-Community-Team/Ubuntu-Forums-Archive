---
title: "Nvidia driver help"
date: 2009-06-09
forum: Hardware
---

### Post by rrvega on 2009-06-09
Been trying to update display drivers, I have a nvidia 8600gt with the restricted drivers enabled. I've downloaded the driver package from nvidia website, and put "sh NVIDIA-Linux-x86-185.18.14-pkg1.run" into the terminal like it says on the nvidia site. I get "sh: Can't open NVIDIA-Linux-x86-185.18.14-pkg1.run" in the terminal. Not sure what else to do after this as im pretty new to ubuntu/linux etc. 

Thanks in advance for any help :)

---

### Post by sloopveedub on 2009-06-09
I'm not expert myself, but I believe that you should make sure you are in the same directory as where the driver file is.  Also try putting sudo in front of the command and enter your password when prompted.

---

### Post by rrvega on 2009-06-09
yep def in the same directory, saved to desktop and thats were terminal starts of at. Tried the sudo thing and that returned "sudo: NVIDIA-Linux-x86-185.18.14-pkg1.run: command not found" 

Its probably not to important, everything seems to be running fine and dandy, but would still be nice to figure out why its not working or what im doing wrong.

---

### Post by Jive Turkey on 2009-06-09
you might need to make the driver package executable like so:
```
chmod 744 NVIDIA-Linux-x86-185.18.14-pkg1.run
```
I know they say to use 'sh' but you might try doing this instead:
```
sudo ./NVIDIA-Linux-x86-185.18.14-pkg1.run
```
I'm certain you will need 'sudo' or 'su' to install the driver.  Let us know how you get on, I've been thinking about trying a newer driver than the restricted one (for no particular reason).

---

### Post by rrvega on 2009-06-09
tried the chmod thing and got this ```
chmod: cannot access `NVIDIA-Linux-x86-185.18.14-pkg1.run': No such file or directory
```
Downloaded it again and tried and still didnt work. Starting to think theres something wrong with the thing im downloading. 

The file is definitly on the desktop, terminal is definitaly saying its on the desktop too.

---

### Post by pedja_portugalac on 2009-06-09
Right click on Nvidia driver and under permissions check the box allow executing file as program.

Log out from GDM, Ctrl-Alt-F1 to the first virtual console and login there. Run 
> sudo /etc/init.d/gdm stop
Change into a directory or place where your Nvidia driver is. 
> cd Desktop
Run:
> sudo ./NVIDIA-Linux-x86-185.18.14-pkg1.run
After installing, run
> sudo /etc/init.d/gdm start
to run GDM again.

---

### Post by pedja_portugalac on 2009-06-10
Sorry, I forget to tell you write the commands on a piece of paper before Ctrl-Alt-F1. Can you come back into GDM?

---

### Post by rrvega on 2009-06-10
it installed and all, and im able to get back into the gdm(asuming its the gui). I am having problems with the driver now though, so trying to uninstall it now lol.

Was an interesting activity though. Thanks for the help :)

---

### Post by bugginnick on 2009-07-14
If I may jump into this topic; I am having the same problems with running the file to no avail.  I have gone through the purging steps and still can't get it to run.  Is there something wrong with the file or am I retarded?  I am fairly new at all this, so please be gentle.;)

---

