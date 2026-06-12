---
title: "Mount Phone as Drive via Bluetooth"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by TekNullOG on 2007-12-03
Does anyone know how to mount a phone via bluetooth as if it were a hard drive?

I would like to access the files and folders on my phone via Drag and Drop even when I don't have my cable.

Here are my specs if it may help:

- standard ubuntu 7.10 bluetooth drivers
- gnome-obex-server 0.9.1
- Nokia E70 phone

The main reason I want to try this is that I installed DivX on my phone via [http://mobile.divx.com/divx](http://mobile.divx.com/divx) and would like to transfer small videos to it to test it out. When I send a file with gnome-obex-server, i receive it like an sms in my phone. If the file is not recognized, I wont be able to open the message to remove its contents. Drag and drop would be so much easier.

I saw it mentioned in this post from 2005 and was worried that much had changed sinced and thought that there was probably an easier solution: [http://ubuntuforums.org/showthread.php?t=75978](http://ubuntuforums.org/showthread.php?t=75978)

Thanks in advance for any help you can give me.

---

### Post by jpkotta on 2007-12-04
Maybe this will work?  Fuse is awesome. 
[http://www.mulliner.org/bluetooth/btfs.php](http://www.mulliner.org/bluetooth/btfs.php)

 It has been said that in Unix everything is a file, but in Linux everything is a filesystem.

---

### Post by TekNullOG on 2007-12-04
thanks for your help.

I didn't find btfs with the package manager. The version from that page is 3 years old and I haven't found an updated version searching threw google.

I don't have a virtual machine installed so i hate to test things on my laptop in case I mess things up.

Any suggestions?

---

### Post by jpkotta on 2007-12-05
[http://www.siltala.net/2007/07/25/mounting-a-nokia-phone-a-little-bit-easier/](http://www.siltala.net/2007/07/25/mounting-a-nokia-phone-a-little-bit-easier/)

obexfs is in the repos.

Don't worry about messing things up.  Just keep track of the packages you needed to install to get something to work, then if you never get it going, you can uninstall them, no problem.  For things that need to be compiled, you can use checkinstall to make an ad-hoc package.

---

### Post by TekNullOG on 2007-12-06
Pretty cool! I will look into it when I get home tonight. This looks pretty simple.

Thanks for the help
I will try to post any results I get.

Cheers

---

