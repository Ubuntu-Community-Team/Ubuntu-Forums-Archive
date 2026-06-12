---
title: "ATI Graphic Card"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by slipk487 on 2006-03-28
how do i get my ATI Radeon 9250 graphic card to work because i can even to get ubuntu to start

---

### Post by TLE on 2006-03-29
Could you be a little more specific. Does it boot as it is supposed to but when the login screen is supposed to come you get an X error message ?

---

### Post by slipk487 on 2006-03-29
it doesnt get to the boot up screen

---

### Post by nazish on 2006-03-29
First let us graphical boot your computer.....
1.)
after you login enter the following command 
sudo vi /etc/X11/xorg.conf
after the file opens find the line which contains someting like** Driver **I think for your card the value in the double quote would be **"Ati"** change it to **"vesa"** by  changing it to vesa we mean that xorg should load the generic drivers, 
2.)
Run the command **startx** 

then follow the steps below

**1.)**
Install the xorg-driver-fglrx package from the Miscellaneous  Restricted                   graphics  section and run the following commands

     **Assuming that u know how to use Synaptic Package Manager and have all                       the repositories updated**

**2.) **
echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

---

### Post by slipk487 on 2006-03-29
dont really know how to use the Synaptic Package Manager  but i cant open it

---

### Post by TLE on 2006-03-29
Well, what have you already done, what kind of install ?
Did it ever start up?
Did you get any error masseges during install, do you ge any during boot. Please give as much information as you can about your problem.
EDIT.Ah sorry I missed the last posts

---

### Post by Jose Catre-Vandis on 2006-03-29
Can you confirm you can boot from Ubuntu CD to commence the install?

If not, have you checked that the CD is OK on another machine, and that it will boot that one? Have you set the bios on your install PC to boot from CD? If you boot up your PC without the CD in, what do you get? Any display?

Your PC should automatically startup in basic VGA mode, if you don't get this you might have a hardware problem so check all connections and that everything is well seated in place, inlcuding your graphics card.

nazish has covered things if you can get to login

---

### Post by sublime on 2006-03-29
you need to do a lot more research, reading and searching before you jump into linux.  read through the ati driver install threads.  your issue is that the driver X (the graphics server) is trying to use isnt compatible with your graphics card.  you need to go into the configuration file and edit it manually, or you can try to load the drivers via command line and wget.  if you dont understand anything im saying then you need to search search search and more search

---

### Post by slipk487 on 2006-04-01
i can get it to boot up with out the radeon card fine ive tried installing ubuntu with the radeon card and when it is done installing packegs the screen stays black but it should go to the boot screen and if i put it in after it is installed it will stay black insted of going to the boot screen and i dont know what to do about it

---

