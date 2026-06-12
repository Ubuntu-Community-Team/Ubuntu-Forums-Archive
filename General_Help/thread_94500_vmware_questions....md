---
title: "vmware questions..."
date: 2005-11-24
forum: General Help
---

### Post by ubuntito on 2005-11-24
Hi folks!!

I've got two problems with vmware. The first one is that I've launched it as root one time and after that I can only start it as root or using sudo, Do you know how can I start it as a normal user once again?

The second one is that when I start vmware it changes the master volume and the PCM volume. How can I fix that?

Thanks for all!!

---

### Post by chaumurky on 2005-11-24
I just reinstalled my system and discovered this strange problem on my vmware install as well. I don't recall having to run vmware as root last time. The installed launcher in the gnome menu just runs 'vmware' and - of course, doesn't work. This is curious. It means I can't just go "vmware <my-virtual-machine>.vmx -x" without having to use gksudo. That was very handy.

---

### Post by chaumurky on 2005-11-24
OK run this line in a terminal:

```
sudo chown root.root /usr/bin/vmware && sudo chmod 755 /usr/bin/vmware && sudo chmod -R o+rX /usr/lib/vmware
``` Don't know what causes the problem in the first place though... :)

---

### Post by ubuntito on 2005-11-24
Thanks for your answer chaumurky, but this doesn't work. I still need to use gksudo to start vmware... If start vmware as a normal user, it displays this:

VMware Workstation Error:

Press "Enter" to continue...

Then I press enter and exits vmware. I think that some config files are owned by root, so I can't start it as a normal user...

thanks,

ubuntito

---

### Post by patrickfromspain on 2005-11-24
Hi. Can I get an evaluation version of vmware? A 30 day trial or something like this. I've looked around but I haven't found anything.

Thanx!

---

### Post by mlomker on 2005-11-24
[QUOTE=patrickfromspain]Hi. Can I get an evaluation version of vmware? A 30 day trial or something like this. I've looked around but I haven't found anything.
[/QUOTE]

[http://www.vmware.com/download/ws/eval.html](http://www.vmware.com/download/ws/eval.html)

---

### Post by patrickfromspain on 2005-11-24
thanks!

---

### Post by Aber_Adrian on 2005-11-24
[QUOTE=ubuntito]Thanks for your answer chaumurky, but this doesn't work. I still need to use gksudo to start vmware... If start vmware as a normal user, it displays this:

VMware Workstation Error:

Press "Enter" to continue...

Then I press enter and exits vmware. I think that some config files are owned by root, so I can't start it as a normal user...

thanks,

ubuntito[/QUOTE]

Have you tried a (sudo) chmod 777 on the directory where the virtual machine is installed? And a chmod 666 on the files within that directory?

Doing this of course assumes you trust everyone who has access to your computer, but it's the way I do it.

Adrian

---

### Post by ubuntito on 2005-11-25
Yes Adrian, It was the first thing that I tried. I'm sure that the directory where the virtual machine is installed is owned by my normal user. I also tried to change the owner of /etc/vmware.conf (I think) and it doesn't workl. So I'm still using gksudo...

Thanks,

ubuntito

---

### Post by mlomker on 2005-11-25
[QUOTE=ubuntito]So I'm still using gksudo...
[/QUOTE]

FWIW I tried to fix all of the file permissions when I first installed it but it never quite ran right.  I always run it sudo, myself.

---

