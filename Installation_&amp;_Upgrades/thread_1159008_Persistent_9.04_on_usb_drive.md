---
title: "Persistent 9.04 on usb drive"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by samtheozzy on 2009-05-14
Hi.  I was hoping to install a persistent state version of ubuntu on my 2gb flash drive.  I followed the instructions at [Pen Drive Linux]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/") but that ends up with a persistent live CD rather than an actual install of linux.  Also I would like to use my computer's RAM as the tmp file.  Are there any tutorials on how to achieve this?

---

### Post by kpkeerthi on 2009-05-14
[http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/"). Its for 8.04 but the general principle is the same for 9.04. I feel 2 GB might not be sufficient.

---

### Post by syst3m on 2009-05-14
Just do a normal full installation of the live cd, and when you get to the partition part choose full disk, selecting the usb drive. Also on the final step, choose the advance options and once again select the usb drive for the boot loader installation. The last thing you want is to be forced to have the usb drive in when you boot your other OS.

Hope this helps, it worked for me with 8.10.

---

### Post by lindsay7 on 2009-05-14
You could try downloading Unetbootin from Synaptic and install on your USB that way. If Unetbootin does not show 9.04, you can install it with Unetbootin using a live cd. It is easy and I think it will auto do a persistent setup.

---

### Post by timcredible on 2009-05-14
> **syst3m said:**
> just do a normal full installation of the live cd, and when you get to the partition part choose full disk, selecting the usb drive. Also on the final step, choose the advance options and once again select the usb drive for the boot loader installation. The last thing you want is to be forced to have the usb drive in when you boot your other os.

Hope this helps, it worked for me with 8.10.

+1

---

### Post by Mighty_Joe on 2009-05-14
> **lindsay7 said:**
> You could try downloading Unetbootin

Unetbootin does live cd install.  Not a full install like OP wants.
I used these instructions to [install ]("http://beastie.cs.ua.edu/cs150/usb-install.html") and [configure ]("http://beastie.cs.ua.edu/cs150/configuration.html") a full Ubuntu install including moving logging and Firefox cache to tmpfs (saves wear and tear and improves performance).  Since the instructions are for an academic exercise, there's some things you don't need to do (like set up vim).  
I've been using it for about a week on my HP/Compaq 8510p laptop and it runs great.  Even suspends and resumes (hibernate? not so much).
You will probably need a bigger flash drive.  The normal Ubuntu install is larger than 2gb.

---

### Post by samtheozzy on 2009-05-16
Thanks for the solid advice.  I'll give it a go.

---

### Post by theozzlives on 2009-05-16
You don't want ppersistence, but a full blown install. I did that but my 2 GB flash wasn't big enough so I used my 8 GB. I setup a seperate /home and a 1 GB swap.

I prolly did it the hard way, but I removed my HD so as to prevent messing up my existing install. It worked good.

---

### Post by Mighty_Joe on 2009-05-16
> **theozzlives said:**
> I setup a seperate /home and a 1 GB swap.


Note that the instructions that I linked to specifically say to use no swap partition.  There's two reasons:  First, USB flash drives are slow and using the swap partition will noticeably degrade performance.  Second, flash drives can [wear out]("http://en.wikipedia.org/wiki/Flash_memory#Memory_wear"), so using that drive for a high-traffic swap partition may lead to early drive death.
My laptop has 2GB of RAM, so I haven't seen any problems not having a swap partition.  If one has less RAM, one may run into problems if you exceed available memory.

---

### Post by samtheozzy on 2009-05-16
> **theozzlives said:**
> You don't want ppersistence, but a full blown install. I did that but my 2 GB flash wasn't big enough so I used my 8 GB. I setup a seperate /home and a 1 GB swap.

I prolly did it the hard way, but I removed my HD so as to prevent messing up my existing install. It worked good.

Just to confirm that theozzlives is right, 2gb is too small for an actual install of ubuntu 9.04.  4gb is the minimum.

---

