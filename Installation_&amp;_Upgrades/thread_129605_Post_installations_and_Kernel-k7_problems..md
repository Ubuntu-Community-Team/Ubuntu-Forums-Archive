---
title: "Post installations and Kernel-k7 problems."
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by Xecuter on 2006-02-14
Hi guys! I'm new here, so if i've posted in the wrong forum, let me know ;)

Well, i got tired of Windows, and desided to give Linux a chance. So i did, and i'm very impressed. Got Ubuntu two weeks ago.

Now i want to upgrade my kernel to k7. I got AMD socket A. So i start up terminal and type:
```
sudo apt-get install linux-k7
```
but it says "Package not found."
Why?

I've also tried to run Automatix go get the rest of the programs, but i don't have internet at my appartment so it doesn't work. How can i install Automatix without internet?

---

### Post by renzokuken on 2006-02-14
for the k7 kernel, it should just be in the repos. 

do a 
# sudo apt-get update

then try again.

if it still doesnt work then go into Synaptic Package Manager and check to see all the repositories are enabled. if not, enable them, update again then try the k7 install again.

---

### Post by Xecuter on 2006-02-15
Hey remember i haven't got internet. Doesn't all apt-get commmands get their packages from internet?

Anyway, it doesn't work. I can't enable all repositories because it searches for something on the net, and then it says "Error: Couldn't find http://***********" and so on.

---

### Post by Ocxic on 2006-02-15
linux-k7 is not the name of the actual package, try using the synaptic pakage manager it will be in there.

---

### Post by frodon on 2006-02-15
[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

Check also that you have enabled all the repositories : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by renzokuken on 2006-02-15
i may have misinterpreted you here Xecuter, but all synaptic/apt-get does is download the necessary files (in this case linux-k7) from the online repos and then installs them for you. the files are not pre-stored on your PC, they still have to be downloaded from the repos, so no it wont work with no net connection.

is that what u mean?

---

### Post by Xecuter on 2006-02-16
Yeah, but my question is: How do i get it to work?

Isn't it possible to download the package from school, onto my USB-disc?

I've also got the same problem whit the ATI driver.

---

### Post by renzokuken on 2006-02-16
ok, i see.....yes it is possible to do that. you just need to find out which repo the .deb files are in.

if you open the file /etc/apt/sources.list you will see the ftp/web addresses that Synaptic downloads from. 

[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

just have a rummage around in there and try to find the linux-k7 and the fglrx (for ATI) debs.

then put em on disc, get them home, and to install them simply type in a console

# sudo dpkg -i name_of_file.deb

simple as that

hopefully someone can point u in the correct place to find the debs u need

---

### Post by Xecuter on 2006-02-16
Ahh! Thanks man. I'll have a look around ;)

---

### Post by Xecuter on 2006-02-21
[http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) 
This is what source.list says the repositories should be. But I can only find 14kB big files in every folder. Is this right? How do I know what package to get? They're all named Package.bz2 or Package.gz. 

I've also downloaded som torrents which are supposed to contain all necessary files, but there's noone that seeds it, so I ain't getting it.

---

### Post by renzokuken on 2006-02-21
the debs are in the "pool" link.......

[http://no.archive.ubuntu.com/ubuntu/pool/](http://no.archive.ubuntu.com/ubuntu/pool/)

---

### Post by Xecuter on 2006-02-22
OK thanks. But there are alot of files here. If I want linux-k7, how do I know where to find it? Do i run "sudo apt-get install linux-k7" and read through there error report where to find it?

---

### Post by renzokuken on 2006-02-22
ok, i think i got it

go to [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/)

and get 
 linux-headers-2.6.12-10-k7_2.6.12-10.28_i386.deb
and
 linux-image-2.6.12-10-k7_2.6.12-10.28_i386.deb

then  # sudo dpkg -i whatever.deb

**I WOULD SERIOUSLY CONSULT A MODERATOR BEFORE DOING IT THIS WAY TO CHECK I HAVE GIVEN YOU THE RIGHT FILES, COS I'M NOT SURE IF I HAVE AND I WOULDNT WANT TO BE RESPONSIBLE FOR BREAKING YOUR SYSTEM**

---

### Post by StefanoCole on 2006-02-24
Xecuter, to install the k7 kernel you have to download the following debs:

- linux-image-2.6.12-9-k7_2.6.12-9.23_i386.deb from: [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/")

- linux-image-k7_2.6.12.16_i386.deb from: [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/")

- linux-k7_2.6.12.16_i386.deb from: [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/")

- linux-restricted-modules-2.6.12-9-k7_2.6.12.4-11_i386.deb from: [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.12/]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.12/")

- linux-restricted-modules-k7_2.6.12.16_i386.deb from: [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/")

Then install with dpkg or creating a local repository.
I advise you to preserve the original 386 kernel, so in case of problems you could always boot from it. 
linux-headers are not required (only if you intend to compile).

Stefano

---

### Post by Xecuter on 2006-02-24
Thanks:D
So I just type "sudo dpkg -i filename" in terminal on all the files and reboot? 

Will it automaticly preserve the 386 kernel, so I just choose it when boot?

---

### Post by StefanoCole on 2006-02-24
With "sudo dpkg -i filename" you have to install the packages in the correct order. For instance you have to install first linux-restricted-modules-2.6.12-9-k7_2.6.12.4-11_i386.deb and then linux-restricted-modules-k7_2.6.12.16_i386.deb. 
I am not sure about the correct order but it could be:

1. sudo dpkg -i linux-image-2.6.12-9-k7_2.6.12-9.23_i386.deb 
2. sudo dpkg -i linux-image-k7_2.6.12.16_i386.deb
3. sudo dpkg -i linux-restricted-modules-2.6.12-9-k7_2.6.12.4-11_i386.deb
4. sudo dpkg -i linux-restricted-modules-k7_2.6.12.16_i386.deb
5. sudo dpkg -i linux-k7_2.6.12.16_i386.deb

Try in this order. If doing dpkg of one package it says that the installation of another package is required first then install it accordingly. 

Otherwise, if you want to learn more, you could create a local repository for the 5 packages and use "apt" to install them. This link is useful: [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html")
in particular sections "How to use APT locally" and "The /etc/apt/sources.list file".

Once you have installed the packages just reboot. At this point GRUB should show you both the old 386 kernel and the new k7 kernel and you simply choose the one you want.

Let me know if everything went fine, Stefano

---

