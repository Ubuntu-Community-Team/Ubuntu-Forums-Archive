---
title: "Synaptic Package Manager"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by nicodemus314 on 2009-10-25
Hello,

My Synaptic Package Manager, during an upgrade and installation of various packages, stopped at Java 5.0 and froze. After it stopped responding, I attempted to reopen Synaptic Package Manager, and it called an error and asked me to run a manual dpkg --install -a. Having no luck at finding the folder containing or titled Synaptic Packages Manager, I tried executing a general dpkg --install -a, and it gave the response that:

dpkg: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more'

Please, if any of you are able, help me resolve this problem so I can re-enable my Synaptic Package Manager and Update Manager.

---

### Post by oldos2er on 2009-10-25
Have you tried ```
sudo dpkg --configure -a
```

---

### Post by nicodemus314 on 2009-10-25
Yes, tried that. It asked me to download Java SE Doc, place it in the /tmp folder as root.root. I wasn't sure what that meant, so I merely saved it to the desktop, extracted it into the /tmp folder, only it extracted as a folder named Doc. Then I reattempted to do as you suggested, but it still returned the same error response. The exact name of the file that I downloaded is jdk-6u10-docs.zip... the exact issue is that my downloader/installer programs are not working. Again, thanks for your assistance. :)

---

### Post by oldos2er on 2009-10-26
> **nicodemus314 said:**
> Yes, tried that. It asked me to download Java SE Doc, place it in the /tmp folder as root.root. 

  I'm at a loss to understand your problem. Could you possibly post a screenshot of the above error, or terminal output?

---

### Post by nicodemus314 on 2009-10-26
Here is a screenshot of the terminal response. Take a look, and let me know if you can figure through the problem. Much Thanks.

---

### Post by freecru on 2009-10-26
It would seem you should download those files to Desktop, chown them, then move them to /tmp, then do dpkg command again. Like so:

```
sudo chown root:root ~/Desktop/jdk-6u10-docs.zip
sudo cp ~/Desktop/jdk-6u10-docs.zip /tmp
sudo dpkg --configure -a
```Maybe this will settle the issue? Sorry, I've not seen this happen before on my machine so cannot help anymore.

EDIT: After some looking around I've found this: [http://ubuntuforums.org/showthread.php?t=1274005](http://ubuntuforums.org/showthread.php?t=1274005)

---

### Post by Wazz72 on 2009-10-27
Any Ideas on this one?
Synaptic crashed whilst installing, now Im stuck and Synaptic crashes whenever I try and run it.


warren@warren-desktop:~$ sudo dpkg --configure -a
[sudo] password for warren: 
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-16-server
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-16-server
dpkg: subprocess post-installation script returned error exit status 1
warren@warren-desktop:~$

---

