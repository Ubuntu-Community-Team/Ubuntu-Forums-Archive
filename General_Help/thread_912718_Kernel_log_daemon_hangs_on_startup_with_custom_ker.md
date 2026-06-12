---
title: "Kernel log daemon hangs on startup with custom kernel config (2.6.26.3)"
date: 2008-09-07
forum: General Help
---

### Post by Neo_The_User on 2008-09-07
Hello! I am 15, kinda in-experienced so feel free to dumb things down for me. I have a problem with Ubuntu starting up on my computer. I download the kernel source (2.6.26.3) from kernel.org and decompress the tar file.

I do cp -vi /boot/config-`uname -r` .config in the terminal. works fine.

I turn off a huge load of stuff I don't need (laptop extras, wireless, bluetooth etc etc.) I am working on making a new kernel config file using xconfig so I can graphically optimize my kernel for my computer. I have done that many many times before except I am tired of after waiting an hour for the kernel to compile on my old slow K7 processor, then do sudo dpkg -i and install the 2.6.26.3 image and headers, edit my menu.lst and turn off quite and splash, reboot, then it says something like

"Starting kernel log daemon..."

It stays there for around 20 minutes so I go do something else like play video games or something, go back to my computer and it finally asks me for my username and password at the gnome login screen.

I am currently using the 2.6.24-19-generic kernel and it has no trouble with the kernel log daemon. Everything shows up as OK and works great so it isn't my system. I think its either the kernel source or my highly modified ubuntu stock config file with a lot of the options removed. I am going to share my config files / post the config file on pastebin.ca to help others help me.

My main question is, how can I tell the kernel to skip the kernel log daemon or at least make it load in half a second or so similar to the way my kernel originally was. If you need any additional information regarding this issue, I would be more than happy to share more information with you. Thank you so much for your time / support in advance!

---

### Post by Neo_The_User on 2008-09-07
I have plenty of spare time on my hands to follow suggestions (that aren't too ridiculously difficult) so if you have any ideas, I could really use them. I would highly appreciate any help from anybody.

---

### Post by Neo_The_User on 2008-09-07
I have uploaded my config file.

[http://pastebin.ca/1196478](http://pastebin.ca/1196478)

I saved the file as 26263.config in my home directory. I cd to the kernel source, type in make xconfig, click open at the top left, select the 26263.config file, saved the kernel config (not Save As I let it automatically pick the destination of where the config file goes since I do not know) in the terminal I type in make-kpkg clean then I type in

fakeroot make-kpkg --initrd --append-to-version=-k7 kernel-image kernel-headers

I wait. Then I type in sudo dpkg -i and drag the kernel image in the terminal first. Then I type in sudo dpkg -i and drag the headers in. Then I type in 

sudo gedit /boot/grub/menu.lst

I take out splash and quiet. I reboot my computer and it hangs at:

Starting kernel daemon

---

### Post by Washer on 2008-09-07
Try renaming the SXXklogd files in /etc/rc2.d/ to KXXklogd, that keeps it from starting.

or you could delete them if you're feeling adventurous, but I don't recommend it
```
sudo rm /etc/rc2.d/*klogd* 
```

15 yr olds recompiling their kernels *shakes head*

---

### Post by Neo_The_User on 2008-09-07
Should I do that command in the 2.6.26.3 kernel (wait 20 minutes on startup) or the 2.6.24-19-generic kernel?

---

### Post by Washer on 2008-09-07
You shouldn't do that command. Kernel version doesn't matter, they're files in your partition.

---

### Post by Neo_The_User on 2008-09-07
OK I will rename it instead. Thank you so much! I highly appreciate your help! I did gksudo nautilus and changed the S to a K and left the 11 alone. I will go reboot and see how it is. Thanks again.

---

