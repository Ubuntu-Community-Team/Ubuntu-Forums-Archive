---
title: "Convertion of .deb to rpm"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by spatil on 2009-04-03
I am unable to convert deb to .rpm

i am getting following error

Package build failed. Here's the log of the command (cd linux-image-2.6.24.2-custom-2.6.24.2-custom; rpmbuild -bb --target i386 linux-image-2.6.24.2-custom-2.6.24.2_custom-10.00.Custom.spec):
error: line 1: Tag takes single token only: Buildroot: /root/Desktop/Download/Images and src/linux-image-2.6.24.2-custom-2.6.24.2-custom
Building target platforms: i386
Building for target i386

Please help :cry:me how can i convert it to rpm

Thanks Iin advance

---

### Post by easybake on 2009-04-03
I don't know much about the errors you got but this might help:

You can use the program Alien to convert deb's to rpm's or vice-versa. Read more [here.]("http://www.linuxdocs.org/HOWTOs/RPM-for-Unix-HOWTO-8.html")

---

