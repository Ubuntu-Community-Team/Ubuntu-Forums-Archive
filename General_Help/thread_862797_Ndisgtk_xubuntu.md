---
title: "Ndisgtk xubuntu"
date: 2008-07-17
forum: General Help
---

### Post by SpenceMakesSense on 2008-07-17
How am I suppose to install ndisgtk if the file has dependencies issues and my only access to the internet is my other computer?

---

### Post by jonian_g on 2008-07-17
I think the package is in the xubuntu cdrom and the dependecies too.

If not then try this:

Go to Synaptic, check for installation the package you want and instead of clicking apply, go to the File menu and select generate download script.

But you have to do this on the computer you want to install the package to get all the dependencies. Then run the script (double click, execute in terminal) on a computer with internet access and all the packages will be downloaded in the folder the script is.

---

### Post by caljohnsmith on 2008-07-17
> **SpenceMakesSense said:**
> How am I suppose to install ndisgtk if the file has dependencies issues and my only access to the internet is my other computer?
The ndisgtk dependencies are ndiswrapper-utils-1.9 and ndiswrapper-common, if I remember correctly. They are both on the Live CD, so if you go to System > Admin/Prefs > Software Sources, you can add your Live CD as a source. Then you should be able to install the dependencies. 

Another approach is to go to packages.ubuntu.com, download the packages manually, transfer them to your computer, and then install them. If you need any more details let me know.

---

### Post by blazeboy84 on 2008-11-14
Hello, I am a total noob when it comes to Ubuntu. I installed my first ubuntu 8.10. However, I am unable to use the internet because I am missing some drivers for my internet adapter. So basically I need to use ndisgtk or something but I have no idea how to install it. I downloaded the files manually from the website packages but it says Error: Deoendency is not satisfiable:ndiswrapper-util or it says some other error. But how do i install the package by using the cd? (I downloaded the cd from the internet and put it on the disk myself). Please, I really need the help, thanks.

---

### Post by blazeboy84 on 2008-11-14
Okay, I inserted the disk and typed intall command in the terminal but after I get a message Media change: please insert the disk labeled "ubuntu 8.10 _Intrepid Ibix_ - release i386 in the drive /cdrom/ and press enter
I have the disk inside but it doesn't do anything...

---

