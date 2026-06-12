---
title: "Samsung SCX-4521F Scanner Help"
date: 2008-08-22
forum: Hardware
---

### Post by KingCandyCorn on 2008-08-22
I know that there are many threads out there about this topic but none of them seems to deal with quite the same issue or offer a solution that works.

I have Hardy Heron on my system with the above named printer attached.  Printing works fine.  I've got the latest version of the Samsung driver installed.  If I run sane-find-scanner it shows up no problem.  When I look in the Samsung driver it doesn't show any scanner device.  When I run xsane it can't find any scanner.  scanimage -L can't find a scanner either.

So, on the one hand, sane says it can see my usb scanner.  On the other, it says it can't.  I clearly don't know enough about the sane architecture to use that information in any useful way.

Anybody have any answers or advice on how to get the scanner recognized?

Thanks.

---

### Post by yahs on 2008-08-23
Hi, I'm a new user so bear with me.
I have a Samsung scx-4100 and the drivers are pretty much the same.
I read the thread HOWTO Install Samsung Unified Printer Driver by  tweedeldee and used the link [http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146). I had good and not so good results. I did get _everything_ running but then i crashed the system by messing about. I have an image file so i am trying to see what went where. I did a fresh install and I have printing and scanning but not OCR scanning (i did before). The instructions from vyvy worked pretty good but not perfect. I have my own adapted instructions but not sure about posting etc, but more than happy to help if I can.

---

### Post by KingCandyCorn on 2008-08-23
yahs,

Thanks for the reply.  That got things a little bit closer.  That bit on the linked page about uncommenting the four lines in the mountdevsubfs.sh script got it to the point where the scanner now shows up in the Samsung unified print driver configuration page.

I still can't get it to shop up for xsane or scanimage though.  Puzzling.  Actually, I think this is as far as I've ever been with this scanner in Ubuntu.  I had it scanning fine back when I was using OpenSuse 10.20.  When I first jumped to Ubuntu 7.10, I could only access the scanner via that Samsung driver's property page.  Luckily I can still do a scan that way, albeit very limited.  Still would like to figure out how to get it working with xsane though...

I do appreciate the pointer!

---

### Post by yahs on 2008-08-24
That's better news. I think the rest of it is to do with ownership and permissions. Gimp, Openoffice and Xsane should all allow scanning but it seems to be tempermental. At one stage I could only run xsane by using the terminal "sudo xsane" which ran after warning!. I don't think both scanimage and xsane are required but I ended up with both and as it happens that helped. I used applications to remove xsane and followed the section about ownership and permissions in the forum HOWTO Install Samsung Unified Printer by Tweedledee (points 8,9 10), had success with Gimp and openoffice, then reinstalled xsane and it now works. Can't as yet get gscan2pdf to work but who knows?. I intend to do a completely fresh build and install everything again from scratch to see what happens. Also as xsane opens with Wine I think the version of Wine you use is a factor. This one is 1.1.2, I think the older one didn't work as well. (I see that 1.1.3 is available but don't know if it stable). Good Luck

---

