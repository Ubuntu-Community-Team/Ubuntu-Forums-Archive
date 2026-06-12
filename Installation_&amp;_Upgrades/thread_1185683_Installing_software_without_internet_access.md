---
title: "Installing software without internet access?"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by Ryzol on 2009-06-12
I would like to install some repository software on my 9.04 Ubuntu computer, however I can not get on the internet with it. I do have internet access through public Windows XP machines, and I can install software on those Windows machines. 

Is there any way I can download programs through the Windows machines and install them on my offline Ubuntu box?

---

### Post by stretch427 on 2009-06-12
Hey Ryzol, Check this link out [http://ubuntuforums.org/archive/index.php/t-7455.html](http://ubuntuforums.org/archive/index.php/t-7455.html) It looks like it might be what your looking for! 
Cheers!

---

### Post by cariboo on 2009-06-12
You can go to [packages.ubuntu.com]("http:///packages.ubuntu.com/") and download any package you want, remember you have to download the dependencies too.

---

### Post by blackxored on 2009-06-12
I know this is a workaround. But what if, besides trying the replies, take linux with you, on some removable device?
That's how I'm able to land anywhere :D

---

### Post by ByteJuggler on 2009-06-12
> **Ryzol said:**
> I would like to install some repository software on my 9.04 Ubuntu computer, however I can not get on the internet with it. I do have internet access through public Windows XP machines, and I can install software on those Windows machines. 

Is there any way I can download programs through the Windows machines and install them on my offline Ubuntu box?

I'm not sure what you mean "public Windows XP machines", do you mean public as in an internet cafe, or do you mean public as in they've got "public" IP addresses?  

In any case, you can activate "Internet Connection Sharing" on a Windows XP box with (e.g.) DSL internet access, and then use a crossover ethernet cable to directly connect the 2 network ports on the 2 computers.  The Ubuntu box will then receive its IP address from the Windows box and will be able to use the internet as normal, including downloading and installing packages.  Note: You need a crossover ethernet cable for this, a normal patch cable will not work.

---

### Post by aysiu on 2009-06-12
I haven't used it myself, but I've heard good things about APTOnCD:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Alternatively, you can boot up the Ubuntu live CD on the XP machines as a live session, remount the /var/cache/apt/archives directory to a thumb drive and then "install" the packages you want into the live session. Copy those .deb files from your thumb drive to your Ubuntu desktop and then ```
cd ~/Desktop
sudo dpkg -i *.deb
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal).

---

### Post by zenxi on 2009-06-12
you can also just download the debs from [http://www.getdeb.net/](http://www.getdeb.net/) and copy them to a pin drive or cd

---

### Post by aysiu on 2009-06-12
> **zenxi said:**
> you can also just download the debs from [http://www.getdeb.net/](http://www.getdeb.net/) and copy them to a pin drive or cd
Wouldn't you also have to track down and download all the dependencies as well?

---

