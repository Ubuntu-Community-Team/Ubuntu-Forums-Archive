---
title: "DVD-RAM in Ubuntu 17.04 - working fine! Except plymouth interrupts booting ..."
date: 2017-09-20
forum: Hardware
---

### Post by dw1-4 on 2017-09-20
I solved the issue to get **DVD-RAM working in Ubuntu 16 and 17.04**. I want to report here. 

Question is: If I put an automated mount in fstab, why does plymouth fail? Reproducible on 2 very different machines: plymouth fails (no boot in GUI!) when having DVD-RAM in automount. 
Basis is Ubuntu 17.04 XFCE4.    More details in the end of the thread. 

**Here the good, working stuff: **

DVD-RAM is very old. Old and underestimated.  
DVD-RAM on Ubuntu Linux is easy. I use Ubuntu 17.04 and 16.10 with XFCE4 but that  does not matter at all. 

  Why DVD-RAM? Because it is more reliable and more stable archiving data. See Wikipedia for details on DVD-RAM. 


  However, DVD-RAM is rather an external drive than a DVD to write on.  

Not all drives can write and read. However, most modern Laptop and  Computer optical drives can. 

  Careful: DVD-RAM is slow by modern means. Don't force the mount and umount to break. 



  We have to format it as UDF file system. 
This is the appropriate FS  for the DVD-RAM (I do not quote the details here, use duckduckgo.com)

  Know your CD-Writer:  Mount a CD, with „mount“ watch out for the name. Like /dev/sr0. 

  Take the DVD-RAM out of the cartridge if necessary, put it in your drive and reboot.

  Prepare: 
  sudo apt-get install udftools
sudo apt-get install dvd+rw-tools
  Make a mount point: 

  sudo mkdir /mnt/dvdram0
  and adapt the user rights etc.  You need to adapt the rights again for the mounted DVD-RAM (different than vfat floppy or external drive). 
  Adapt the fstab:

  sudo vim /etc/fstab
  For automatic mount enter a new line like[INDENT]   /dev/sr0  /mnt/dvdram0  auto  user,users,rw,auto,exec,utf8 0  0
 [/INDENT]
The first auto may better be "udf". The second auto depends on you: Try noauto if the boot process hangs. 
  Format the DVD-RAM:

  sudo mkudffs --media-type=dvdram   /dev/sr0
  The default options for mkudffs probably match your needs.  Otherwise: man mkudffs !
  Mount the DVD-RAM:
  mount /dev/sr0
  should do it, otherwise use as sudo mount /dev/sr0. With the fstab entry it will be found. 
  When you ask your CLI now with mount it should answer something like:[INDENT]   /dev/sr0 on /mnt/dvdram0 type udf   (rw,nosuid,nodev,relatime,utf8,user=myname)
 [/INDENT]
Now again adapt the access rights for the mounted(!) drive: 

  sudo chown myname /mnt/dvdram0
sudo chmod u+rwx /mnt/dvdram0 
  Test your access rights:
  mkdir /mnt/dvdram0/mydirectory
  without sudo it should work. Otherwise check the rights. 
  Do a reboot now or restart all relevant services. 
  So now we have 
  
[LIST]
[*]installed the tools 
[*]prepared to mount 
[*]formatted the DVD-RAM 
[*]mounted it in the file system 
[*]adapted the user access 
[/LIST]
  It shall be available in the file manager like a normal drive. Watch out for /mnt/dvdram0 (and in Nemo create a bookmark).  

  Unmounting takes time because of write completion. It is done from CLI or try to find a way in your browser. 

  What did I forget? What was wromng?

-------- ---------- ---------- ---------------- ------------------------- --------- ----------- 


PROBLEM: 
This entry kills the boot process: 
fstab:  /dev/sr0    /mnt/dvdram0    auto    user,rw,users,noauto,exec,utf8 0 0 
 (locations exist, no typo).

Plymouth details: 
gdm3[2289]: [./ply-boot-client.c:183]                       ply_boot_client_connect:could not connect to /org/freedesktop/plymouthd: Connection refused
gdm3[2289]: [./ply-boot-client.c:184]                       ply_boot_client_connect:trying old fallback path /ply-boot-protocol
gdm3[2289]: [./ply-boot-client.c:190]                       ply_boot_client_connect:could not connect to /ply-boot-protocol: Connection refused
gdm3[2289]: [./plymouth.c:1121]                                          main:daemon not running

looks like the automount of some data DVD-RAM kills the plymouth by preventing plymouthd to start. 

WHY does plymouthd not start?? Any idea??

---

