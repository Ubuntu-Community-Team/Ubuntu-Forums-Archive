---
title: "apt-zip help in downloading pakages on windows"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-10-17
I am trying to use apt-zip to download updates for ubuntu from a windows system
 following this link:
[http://linuxbasics.org/tutorials/using/apt-zip](http://linuxbasics.org/tutorials/using/apt-zip)
i followed the "prepare the media" part  however i am stuck with the next step "Get the packages"

I have installed Wget from 
[http://gnuwin32.sourceforge.net/packages/wget.htm](http://gnuwin32.sourceforge.net/packages/wget.htm)
downloading the "Complete package, except sources" and "sources" 
but i need help how to run the fetch script on the media 
please  help!

---

### Post by mac9416 on 2009-10-17
I am not really familiar with how apt-zip works. I would suggest giving [Keryx]("http://keryxproject.org/") a try. It's not perfect, but it has a GUI and plenty of documentation. Good luck, and let me know how it goes!

---

### Post by richlyn9 on 2009-10-20
I tried this and it has worked perfectly however its a tedious and needs be done manually.

1.	In your Ubuntu machine open Synaptic, select the program you want to install, it will select the dependencies; then go to the synaptic main menu and choose Generate download script, this will create a text file in your home with the urls of all the .debs selected with the dependencies.

2. Copy the text file to your usb stick.

3. In the Windows machine open the text file and, copy and paste every url to download or just use a download manager and go for a cofee.

4. Copy the downloades packages to your usb stick.

5. Back in your ubuntu machine, go to Synaptic, in the main menu choose Add downloades packages and select the directory where are the downloaded .debs.

I also have given Keryx a try but have got stuck on the part where i have to create a project.
[http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)
I seem to be doing something wrong but since i know nothing about perl i cannot figure it out.


about apt-zip i tried it using wget on windows running a batch file with the following code:
C:\WINDOWS\wget -c [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-14-generic_2.6.27-14.41_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-14-generic_2.6.27-14.41_i386.deb)

since i have wget.exe in C:\WINDOWS\
but the error i get is:

D:\Documents and Settings\gz2z7m\My Documents>C:\WINDOWS\wget -c [http://us.archi](http://us.archi)
ve.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-14-generic_2.6.27-14.4
1_i386.deb
--2009-10-20 11:54:36--  [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/l](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/l)
inux-image-2.6.27-14-generic_2.6.27-14.41_i386.deb
Resolving us.archive.ubuntu.com... 91.189.88.40, 91.189.88.46, 91.189.88.45, ...

Connecting to us.archive.ubuntu.com|91.189.88.40|:80... failed: Connection timed
 out.
Connecting to us.archive.ubuntu.com|91.189.88.46|:80...

i am manually able to go to the url and download but theres somthing thats not right!

Any ideas?

---

### Post by EXCiD3 on 2009-10-20
You can use one of the default projects provided by keryx so that you don't have to create one yourself. It works much easier that way and should get everything you need.

---

### Post by richlyn9 on 2009-10-22
> **EXCiD3 said:**
> You can use one of the default projects provided by keryx so that you don't have to create one yourself. It works much easier that way and should get everything you need.
the existing project is for a differrent distro of ubuntu then what i have installed. will that have no problems? and today i plan to install the kramic RC.

---

### Post by richlyn9 on 2009-10-23
> **EXCiD3 said:**
> You can use one of the default projects provided by keryx so that you don't have to create one yourself. It works much easier that way and should get everything you need.
i also tried that default  projects provided
heres the result.


Downloading 12 file(s)
Downloading: [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.gz)
Failed: [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.gz)
Reason: [Errno socket error] (10060, 'Operation timed out')
Downloading: [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.gz)

---

### Post by EXCiD3 on 2009-10-23
The links are valid. Are you behind a firewall or anything? Also which distro are you using it on?

---

### Post by richlyn9 on 2009-10-23
> **EXCiD3 said:**
> The links are valid. Are you behind a firewall or anything? Also which distro are you using it on?
ya i have a firewall probably but when i enter the link manually in the browser i am able to get there without any troubles 
I am using 8.10 and am keen on 9.10 while the project is for juanty! and am trying the keryx on windows

---

### Post by EXCiD3 on 2009-10-24
Make sure the firewall allows Keryx through, that's what is causing it from downloading anything.

As for Karmic, you can create your own project on an install of it (or if you boot into the livecd and create the project there) and then you can use Keryx for Karmic as well.

---

### Post by richlyn9 on 2009-10-24
sure will,... thanks for the guidance.
i tried 9.10 on a mltiboot with a dedicated grub partition and am not able to boot anything.so need to fix that first!

---

