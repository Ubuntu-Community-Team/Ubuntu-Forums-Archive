---
title: "Installing GFX driver NVIDIA"
date: 2008-08-27
forum: General Help
---

### Post by ^^rac on 2008-08-27
Hi guys!

Im still struggeling........hehehe
I got the correct driver. Dloaded it to the desktop. Its a .run file

I tried:

alt+ctrl+f2
Logged in
sudo killall gdm
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

I tried

alt+ctrl+f2
Logged in
sudo killall gdm
sh NVIDIA-Linux-x86-173.14.12-pkg1.run

In both instances, i got an error, 

sh: Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run


How do i do this?? Hehhehe, im using Ubuntu 8.0.4. I dloaded the file twice!

I tried Envy, did not work for me!

Thanks guys!

---

### Post by jerome1232 on 2008-08-27
That should get :)

edit: adjusted commands to not use sudo -i since that changes your pwd

```

ctrl-alt-f1
sudo apt-get install build-essential
sudo /etc/init.d/gdm stop
chmod +x NVIDIA-Linux-x86-173.14.12-pkg1.run
sudo ./NVIDIA-Linux-x86-173.14.12-pkg1.run -a
sudo /etc/init.d/gdm start
```

---

### Post by ^^rac on 2008-08-27
> **jerome1232 said:**
> That should get :)

```

ctrl-alt-f1
sudo -i
apt-get install build-essential
/etc/init.d/gdm stop
chmod +x NVIDIA-Linux-x86-173.14.12-pkg1.run
./NVIDIA-Linux-x86-173.14.12-pkg1.run -a
exit
sudo /etc/init.d/gdm start
```

Hi there!
Thanks alot, but when i get to chmod line, it says no such file or directory?

Must i copy the package to the root or summin?

---

### Post by jerome1232 on 2008-08-27
Well were is the downloaded file at? you would need to cd to the directory it's in.

Like if it's on you desktop then

```
cd Desktop
chmod ....
```

you can use ls to see files in the current directory and tab completion to type long names, like just type chmod +x NV[hit tab]

on second thought, sudo -i changes you to roots home directory so you are in a different spot, instead of using sudo -i, just prepend each command except the chmod one with sudo, I adjusted the commands

---

### Post by ^^rac on 2008-08-27
Hi i get into the gui...

But it gives me an error:
nvidia-installer must be run as root?

Any ideas

---

### Post by jerome1232 on 2008-08-27
Did you run it as root?

```
[COLOR="Red"]sudo[/COLOR] ./NVIDIA-Linux-x86-173.14.12-pkg1.run -a
```

---

### Post by ^^rac on 2008-08-27
> **jerome1232 said:**
> Did you run it as root?

```
[COLOR="Red"]sudo[/COLOR] ./NVIDIA-Linux-x86-173.14.12-pkg1.run -a
```


Hi there!! Thanks man!
I did everything you said, and it actually installed the driver....

But it does not work. It seems like there is no driver for 7300GT, during the installation, it wanted to dload a kernel etc, and could not find it...

Then it built its own kernel..

After reboot, i got the generic driver back to square one....

Do you think that there is no driver for this card??

Thanks man!
Youve been a great help!

---

### Post by jerome1232 on 2008-08-27
There is no precompiled binary that's normal, building you own driver is why I had you install build-essential for, at the end did you let it edit your xorg.conf? There is an option towards the end of the installer to do that, and if you didn't let it, it will default back to the generic drivers.

---

