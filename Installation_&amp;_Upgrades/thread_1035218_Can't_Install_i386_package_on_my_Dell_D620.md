---
title: "Can't Install i386 package on my Dell D620?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by smaka5 on 2009-01-09
Hello,

I created a dual-boot system using Wubi so I could run Ubuntu 8.0.4 and Windows XP Pro on my Dell laptop D620. Up until yesterday I had not run into any issues installing new packages. I now need to do development on an embedded processor made by Atmel and need to install the board support package files.

All of the packages I need to install are type .deb and most have i386 in their name. I have tried to open them with the GDebi Package Installer and all packages that have i386 in the file name result in the error message:
"Error: Wrong architecture 'i386'". Then, I tried using the dpkg utility via Terminal and get a similar error message: "package architecture (i386) does not match system (amd64)".

Notes: 
1. My computer has a Intel Core2 processor & I have verified Ubuntu recognizes this fact via Terminal using the command: "cat /proc/cpuinfo"
2. My coworker has the same model laptop and has no issues with a copy of these files. However, he is using Vmware on his machine to run Ubuntu.

If anyone knows what I need to do to enable installation of these packages, it would be greatly appreciated.

---

### Post by oldos2er on 2009-01-09
You can try this: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by smaka5 on 2009-01-24
Thanks for the link oldos2er.

I attempted to follow the instructions in the link, but had no luck getting the complete package installed.

I did more research and discovered the "amd64" is generic for 64-bit processor architecture. When I used Wubi, the installation used the 64-bit version of Ubuntu - not sure whether I was given a choice or it just did it. Anyway, what I really needed was to have the 32-bit version of Ubuntu installed to be able to install the i386 package.

Thus, I opted to reinstall the 32-bit version of Ubuntu using Wubi. Luckily, I have just started using Ubuntu, so I didn't have a lot to back up or applications to find/reinstall.
Must say, the reinstallation of Ubuntu was easier than I thought - just placed the version of Ubuntu I needed into the directory where the Wubi executable was, then ran Wubi. Wubi did the uninstall of the 64-bit version, then installed the 32-bit version I needed.:)

---

