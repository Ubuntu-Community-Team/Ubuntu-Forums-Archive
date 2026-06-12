---
title: "Successful Canon MX922 All-In-One Scanner Operation od Network/WIFI"
date: 2018-03-30
forum: Hardware
---

### Post by kenj69 on 2018-03-30
(BTW, the title says "od" - it should read "on." I can't edit titles yet)

After much trial and error I can report the successful setup of the Canon PIXMA MX-920 series All-In-One scanner on network/wifi. I wanted to share my process with everyone.  3/30/2018

1. Terminal: "sane-find-scanner" command shows only SCSI, USB and parallel-port scanners. No network printers will show up using this command!

2. Terminal: "scanimage -L" command returns, device `pixma:MX920_192.168.0.30' is a CANON Canon PIXMA MX920 Series multi-function peripheral (at least mine does since installing the Canon printer). Best to assign a static IP address.

3. Using software center/package manager add 'sane' scanner graphical "backend." Also add sane-utils and libsane-extras.
Terminal: sudo apt install sane sane-utils libsane-extras

4. Add sane-git repository in order to recieve updates:
Terminal: sudo add-apt-repository ppa:reolfbensch/sane-git
Terminal: sudo apt-get updates

5. Install a scanner "frontend" application such as Xsane, Simplescan or similar.

6. Firewall, by default, blocks most incoming requests. To allow scanner traffic add 'Scanner' both directions on port 8612.
Ref: [https://www.systutorials.com/docs/linux/man/5-sane-pixma/](https://www.systutorials.com/docs/linux/man/5-sane-pixma/)

References (thank you to all resource owners!):
1. [https://ubuntuforums.org/showthread.php?t=2362915](https://ubuntuforums.org/showthread.php?t=2362915)
2. [https://help.ubuntu.com/community/sane](https://help.ubuntu.com/community/sane)
3. [http://www.sane-project.org/sane-frontends.html](http://www.sane-project.org/sane-frontends.html)

-=Ken=-

---

### Post by him610 on 2018-04-01
Hello kenj69,

While I do not have a Canon scanner; I have an Epson (USB) and a Brother (network) that have been installed for awhile. I am sure the folks in the Community that own Canon scanners and have had issues with the installation will appreciate your post.
Good job!

---

