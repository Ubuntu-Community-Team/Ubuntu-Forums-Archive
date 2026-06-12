---
title: "eeePC 4g Webcam difficulties"
date: 2008-10-15
forum: Hardware
---

### Post by moephan on 2008-10-15
Hello,

I installed eeeUbuntu on my 4g about a week ago. Previously I was running eeeXubuntu. Under eeeXubuntu the webcam worked fine. 

Under eeeUbuntu, the web cam works with luvcview. However, when I run Cheese, the web cam light comes on for a moment, then turns off. Then cheese displays the attached test pattern. 

When I try the web cam on Skype, when I click Test, nothing happens, but luvcview will not when Skype is in video test mode (indicating that the web cam is busy. However, the web cam light does not come on).

Any thoughts about how I could go about solving or trouble shooting this? I would like to use the web cam on both cheese and Skype.

Cheers, Rick

---

### Post by michaelkahl on 2008-10-15
I use Ubuntu Eee 8.04.1 on my 900 and the webcam doesn't work either.  From what I read the lastest kernel from array.org appears to fix this.  I think there is a hack to get it working on earlier versions of the kernel.

[Array]("http://array.org/ubuntu/")

[4G Hacks to load modules]("http://array.org/ubuntu/hacks.html?id=1&device=&dist=")

[900 Hacks to load modules]("http://array.org/ubuntu/hacks.html?id=2&device=&dist=")

After loading the hack my web cam works.

If you decide to try the hack at least backup your /etc/modules file.

```
sudo cp /etc/modules /etc/modules.bak
```

This way if something goes bad, you can boot in from a live disk and replace the file.  (use the below code in reference to where your Eee's SSD is mounted)

```
sudo cp /etc/modules.bak /etc/modules
```

Then reboot, but hopefully all will go well.  Also make sure your web cam is turned on in the bios.  May sound silly, but I've done it before too.

---

### Post by moephan on 2008-10-16
michaelkahl,

Thanks for the suggestion, but I'm already running that version of the kernel. It was installed when I installed eeeUbuntu. Also, the modules file was already set up properly.

Any suggestions (from anyone) on how I could start trouble shooting this? I checked the eeeUbuntu wiki, and Googled extensively, but I haven't been able to get started on tracking this down. 

TIA

Cheers, Rick

---

### Post by moephan on 2008-10-19
Just a quick update ... for whatever reason, the webcam in both cheese and skype is now working. I have no idea why. In cheese, the camera now turns off as it did before, but then turns on again and displays the video.

I haven't been able to pin down a change that I made that could have effected it, but there you go ...

Cheers, Rick

---

### Post by michaelkahl on 2008-10-30
I'm just glad you got it working.

---

