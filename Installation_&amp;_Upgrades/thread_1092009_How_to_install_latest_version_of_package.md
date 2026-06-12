---
title: "How to install latest version of package?"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Davepar on 2009-03-09
There is a critical fix in geotiff-bin_1.2.4-4_i386.deb that I need to install, but whenever I do "apt-get install geotiff-bin" it says that I have the latest version 1.2.4-3.

I'm fairly new to Ubuntu and Linux, so not sure what I'm doing wrong. Any help appreciated.

Thanks,
Dave

---

### Post by Neo_The_User on 2009-03-09
Try forcing it. Open up a terminal in Applications > Accessories and copy and paste the following commands in order. After the first command, press enter. Then copy the other command and press Enter. Then continue what you were doing. btw, this is the UNSAFE way to do it but if you insist, that's how.

```

wget http://mirrors.kernel.org/debian/pool/main/libg/libgeotiff-dfsg/geotiff-bin_1.2.4-4_i386.deb

sudo dpkg -i geotiff*

```

---

### Post by Davepar on 2009-03-10
Thank you very much. That worked great.

---

### Post by Neo_The_User on 2009-03-10
> **Davepar said:**
> Thank you very much. That worked great.

Heh no problem. Don't normally install apps using the debian repository though. Think of that as a one time only.

---

### Post by innactpro on 2009-03-10
What about other packages? I am trying to transition from windows To Ubuntu Studio. I do though want to stay with the LTS versions. When I try to install gimp through Add/Remove or Synaptic, only version 2.4.1, I believe it's .1, is available. I have found though that gimp 2.6.5 is available through Jaunty. I have tried adding the Jaunty repositories. Though I'm not sure I did that correctly, gimp 2.6.5 did show up in the Synaptic Package Manager. When trying to install the newer version of gimp, there was some sort of error. I don't remember what the error was. I even tried downloading and installing the package:
[http://packages.ubuntu.com/jaunty/graphics/gimp](http://packages.ubuntu.com/jaunty/graphics/gimp)

This kept having dependencies satisfaction issues. I kept downloading dependencies and installing them until I got to libxcb xlib0 I believe. Something like that. I was given the message informing me that an older version was already installed and could not be removed. When I tried removing it myself, it listed many other things that were going to be removed. Knowing this would very likely render Ubuntu useless on my computer I went ahead anyway. Of course I had to reinstall Ubuntu on the computer.

I tried downloading directly from gimp.org, but that needs to be compiled and that started getting a bit complicated. With the dependencies satisfaction issues I was having, I'm not even sure compiling that would work.

So any hints for getting Ubuntu to allow for the most recent versions of packages would be helpful. Would the previous solution work in this case? Or would something different need be done? Other than the previous solution obviously being specifically for the original problem.

Thanks.

---

### Post by Partyboi2 on 2009-03-10
> **innactpro said:**
> What about other packages? I am trying to transition from windows To Ubuntu Studio. I do though want to stay with the LTS versions. When I try to install gimp through Add/Remove or Synaptic, only version 2.4.1, I believe it's .1, is available. I have found though that gimp 2.6.5 is available through Jaunty. I have tried adding the Jaunty repositories. Though I'm not sure I did that correctly, gimp 2.6.5 did show up in the Synaptic Package Manager. When trying to install the newer version of gimp, there was some sort of error. I don't remember what the error was. I even tried downloading and installing the package:
[http://packages.ubuntu.com/jaunty/graphics/gimp](http://packages.ubuntu.com/jaunty/graphics/gimp)

This kept having dependencies satisfaction issues. I kept downloading dependencies and installing them until I got to libxcb xlib0 I believe. Something like that. I was given the message informing me that an older version was already installed and could not be removed. When I tried removing it myself, it listed many other things that were going to be removed. Knowing this would very likely render Ubuntu useless on my computer I went ahead anyway. Of course I had to reinstall Ubuntu on the computer.

I tried downloading directly from gimp.org, but that needs to be compiled and that started getting a bit complicated. With the dependencies satisfaction issues I was having, I'm not even sure compiling that would work.

So any hints for getting Ubuntu to allow for the most recent versions of packages would be helpful. Would the previous solution work in this case? Or would something different need be done? Other than the previous solution obviously being specifically for the original problem.

Thanks.
You should be able to go to [[COLOR=Blue]getdeb[/COLOR]]("http://www.getdeb.net/app/Gimp") and download gimp 2.6.5 deb for the version of ubuntu you are using. 
I would suggest removing the jaunty repo from your sources.list as this can cause breakages with the package managers.

---

### Post by innactpro on 2009-03-10
> **Partyboi2 said:**
> You should be able to go to [[COLOR=Blue]getdeb[/COLOR]]("http://www.getdeb.net/app/Gimp") and download gimp 2.6.5 deb for the version of ubuntu you are using. 
I would suggest removing the jaunty repo from your sources.list as this can cause breakages with the package managers.

I will give this a try. And after I reinstalled Ubuntu I haven't done anything with repos.

Thanks.

---

### Post by snowpine on 2009-03-10
Ubuntu is not a "rolling release" distro. This means that package versions are stable for each release--all you typically get is minor upgrades and bug fixes (for example, from 2.1.0 to 2.1.1 of a hypothetical package, but not 2.2). Generally speaking, you upgrade to newer packages in Ubuntu by dist-upgrading every six months.

If you need a newer version of a particular package (which is fine, lots of us do it), I really recommend learning how to use dpkg to install the specific .deb for that package. It is not really that hard, and dpkg is "smart" enough to alert you of any dependecy problems. I agree 100% with Partyboi; once you start adding repositories for Debian or Jaunty, things will get weird fast. :)

---

### Post by Neo_The_User on 2009-03-10
> **snowpine said:**
> Ubuntu is not a "rolling release" distro. This means that package versions are stable for each release--all you typically get is minor upgrades and bug fixes (for example, from 2.1.0 to 2.1.1 of a hypothetical package, but not 2.2). Generally speaking, you upgrade to newer packages in Ubuntu by dist-upgrading every six months.

If you need a newer version of a particular package (which is fine, lots of us do it), I really recommend learning how to use dpkg to install the specific .deb for that package. It is not really that hard, and dpkg is "smart" enough to alert you of any dependecy problems. I agree 100% with Partyboi; once you start adding repositories for Debian or Jaunty, things will get weird fast. :)

Not unless you know what you're doing. I transfered all the Xorg and X11 pakckages from 9.04 to 8.10. Don't do it though. I develop for Mesa so I kind of had to. I use 9.04 now though.

---

