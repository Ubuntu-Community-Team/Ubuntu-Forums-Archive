---
title: "Intel q35 chipset family"
date: 2016-01-15
forum: Hardware
---

### Post by christopher_m3 on 2016-01-15
Hi,

When using anything but KUBUNTU I get this garbage on my screen its like multi colors and shapes in things As you see in the screenshot here: 

This is on Ubuntu 15.10 with Gnome 3.

[http://i886.photobucket.com/albums/ac69/CMAR606/Ubuntu%20Gnome%203/Screenshot%20from%202016-01-08%2023-25-46.png](http://i886.photobucket.com/albums/ac69/CMAR606/Ubuntu%20Gnome%203/Screenshot%20from%202016-01-08%2023-25-46.png)


Is there any way to stop this from happening so I can use Gnome 3 ? I kinda feel stuck if I can only use Unity or KDE DE. :( 

Its weird that those two DE works fine no issues but gnome 3 is a total different story. 


Here is my Graphics Card Info:  [http://i886.photobucket.com/albums/ac69/CMAR606/Ubuntu%20Gnome%203/Graphics%20Card%20Drivers.png](http://i886.photobucket.com/albums/ac69/CMAR606/Ubuntu%20Gnome%203/Graphics%20Card%20Drivers.png)



And no before anyone asks under additional drivers nothing came up but 1 thing that said UNKNOWN and wouldnt tell me anything more about it. 


Thanks,
Christopher

---

### Post by mörgæs on 2016-01-16
It's better if you find graphics card info and other specifications by running a command and posting the output. 

Anyway, for semi-old Intel graphics UXA acceleration often does the trick. If you click the Old Hardware link in my signature and search for UXA in the text you'll get to instructions.

---

### Post by christopher_m3 on 2016-01-16
I am booted into windows right now wonder what kinda command I can run to find out the full info of the display driver?

~$ lspci | grep -i vga

00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

ubuntu-gnome@ubuntu-gnome:~$

---

### Post by mörgæs on 2016-01-18
Thanks, please use terminal output next time. Google reads that (as opposed to a screen shot).

Did UXA help?

---

### Post by christopher_m3 on 2016-01-18
When I reinstall I will try that trick thanks :)

---

